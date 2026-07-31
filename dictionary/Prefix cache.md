---
description: provider 端的儲存機制，讓連續的 request 可以跳過重新處理共用的 prefix，那些 token 用比較低的費率計費。
---

[Provider](./Model%20provider.md) 端的儲存機制，讓連續的 [model provider request](./Model%20provider%20request.md) 可以跳過重新處理共用的 prefix。當一個 request 的開頭跟最近一次的開頭吻合——同樣的 [system prompt](./System%20prompt.md)、同樣的歷史紀錄到某個點為止——provider 就會重複使用它先前算過的結果，把這些 [tokens](./Token.md) 當作 [cache tokens](./Cache%20tokens.md)，用低很多的費率計費。

這個快取划算，是因為 [session](./Session.md) 是只增不減地成長的。每一次 request 都會把整段歷史當作 [input tokens](./Input%20tokens.md) 重新送出去（原因見那個條目），而在正常的 session 裡，歷史紀錄只會在尾端變動——每一次 request 都是前一次加上幾則新訊息。Provider 只處理一次那段共用的開頭，把結果存起來，然後從 prefix 結束的地方接著算下去。沒有這個快取，一個跑了 50 個 [turn](./Turn.md) 的 session，就得把第一個 turn 重新處理五十次。

快取也會過期。一筆紀錄能保溫多久，因 model provider 而異——通常是幾分鐘，不是幾小時。讓一個 session 閒置超過這個窗口，下一次 request 就得先用全額價格重建一次 prefix，之後快取才會恢復。這大多是 [harness](./Harness.md) 開發者要煩惱的事；對使用者來說，看得到的效果就是：停頓很久之後的那些 request，會比停頓之前的貴。

_使用情境：_

「為什麼帳單在 session 跑到一半的時候突然飆高？」

「Harness 開始在每個 turn 都把當下時間塞進 system prompt。Prefix cache 一碰到第一個變動的 token 就會失效，所以那之後的每一個 request 都用全額費率計費。」
