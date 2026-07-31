---
description: provider 透過 prefix cache 從先前的請求裡快取下來的 input tokens，計費費率低很多。
---

[Provider](./Model%20provider.md) 從先前一次 [model provider request](./Model%20provider%20request.md) 快取下來的 [input tokens](./Input%20tokens.md)，不用重新處理。當連續幾次請求共用同一個前綴時，provider 會透過它的 [prefix cache](./Prefix%20cache.md) 重複利用先前的運算結果，並把被快取的那部分用低很多的費率計費。這是讓長 [session](./Session.md) 負擔得起的關鍵機制——沒有它，每個 [turn](./Turn.md) 都得重新支付整段歷史的費用。

會這樣，是因為 session 計費的方式。[Model](./Model.md) 是 [stateless](./Stateless.md) 的，所以每一次請求都要把整段對話——[system prompt](./System%20prompt.md)、每一則訊息、每一個 [tool result](./Tool%20result.md)——當成 input tokens 重新送一次。到了第五十個 turn，每次請求都帶著五十個 turn 的歷史，如果全部都用全額費率計費，每次都要付一次。快取改變了這個算法：provider 已經在一模一樣的前綴裡處理過的 token，會以 cache tokens 計費，費率通常是 input 費率的十分之一或更低。在一個長 session 裡，你送出去的大部分都是 cache tokens，帳單才不會失控。

一個例子可以說明什麼時候會被快取、什麼時候不會。每個字母代表一段對話內容；每次請求都送出目前為止的整段對話：

| 這次請求送出 | 被快取的部分 | 以全額費率計費的部分 | 原因                                          |
| ------------ | ------------ | -------------------- | --------------------------------------------- |
| `AB`         | 無           | `AB`                 | 第一次請求——沒有東西可以比對                  |
| `ABC`        | `AB`         | `C`                  | `AB` 剛好是上一次請求的前綴，完全吻合         |
| `ABCD`       | `ABC`        | `D`                  | 前綴仍然完整                                  |
| `AXCD`       | `A`          | `XCD`                | 有個編輯把 `B` 改成了 `X`；比對從那裡開始失敗 |

這個快取的脆弱之處很具體：它比對的是完全一致的前綴。只要對話裡更早的地方有任何變動——[harness](./Harness.md) 重新排列了內容、時間戳記更新了、某個檔案的呈現方式變了——快取就會從那個點開始失效，之後的所有內容都會用全額 input 費率計費。快取也會在閒置幾分鐘後過期，所以一個暫停很久之後恢復的 session，會需要把歷史重新支付一次費用。當一個 session 的花費無緣無故暴增時，去用量報表裡比較 cache tokens 跟 input tokens——快取壞掉的話，會先在那裡看得出來。

_使用情境：_

「長 session 的成本高得嚇人——一次重構就花了八塊美金。」

「查一下 cache tokens。如果 harness 在每個 turn 之間重新排列了 system prompt 或檔案順序，前綴就會斷掉，每次請求都會用全額 input 費率計費。」
