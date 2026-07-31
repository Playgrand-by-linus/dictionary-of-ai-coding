---
description: harness 到 model provider 之間的一次來回。Harness 送出 context，provider 回傳一個回應。
---

從 [harness](./Harness.md) 到 [model provider](./Model%20provider.md) 的一次來回。Harness 送出目前的 [context](./Context.md)；provider 回傳一個回應（一個 [tool call](./Tool%20call.md) 或一個最終答案）。如果 [agent](./Agent.md) 呼叫 [tool](./Tool.md)，一則使用者訊息就可能引出很多次 model provider request——每一個 [tool result](./Tool%20result.md) 都會觸發下一次 request。

每一次 request 都帶著全部的東西：[system prompt](./System%20prompt.md)、到目前為止的完整對話、每一個 tool result。[Model](./Model.md) 是 [stateless](./Stateless.md) 的，所以 provider 在 request 之間什麼都不留——第四十次 request 重送了第三十九次送過的東西，再加上多一個 tool result。[Prefix cache](./Prefix%20cache.md) 存在的目的，就是讓這種重複變得負擔得起。

Request 也是計費的單位。[Input token](./Input%20tokens.md)、[output token](./Output%20tokens.md)，還有 cache 折扣，都是按 request 算的，這就是為什麼一個看起來人畜無害的問題，可能花掉一筆讓人意外的錢：成本不是跟你的訊息成正比，而是跟 request 的數量、乘上每一次 request 帶的 context 大小成正比。

值得把 request 跟 [turn](./Turn.md) 分開來看。一個 turn 是跟你的一次交流，而單一一個 turn——「修好失敗的測試」——會展開成一串 request：

| Request | Model 回傳的內容               | Harness 接著做的事         |
| ------- | ------------------------------ | -------------------------- |
| 1       | Tool call：跑測試              | 跑測試，把失敗的輸出接上去 |
| 2       | Tool call：讀測試檔案          | 把檔案內容接上去           |
| 3       | Tool call：讀原始碼檔案        | 把檔案內容接上去           |
| 4       | Tool call：改原始碼檔案        | 套用這次編輯，把結果接上去 |
| 5       | Tool call：再跑一次測試        | 跑測試，把通過的輸出接上去 |
| 6       | 最終答案：「修好了，測試通過」 | 顯示給你看                 |

一個 turn 用掉六次 request——每一次都要重送整個 context。想不通 [token](./Token.md) 到底花去哪了的時候，去數 request 的數量，不是 turn 的數量。

_使用情境：_

「一個問題燒掉四萬個 token？」

「看一下 tool call——十二次 grep、八次 read、四次 edit。每一個 tool result 都會催生下一次 model provider request，整個 [session](./Session.md) 的 prefix 每次都要重送一次。」
