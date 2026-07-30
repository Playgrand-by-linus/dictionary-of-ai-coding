---
description: 由另一個 agent 透過 tool call 產生的 agent。在自己的 session 裡執行，回報單一 tool result。不能再產生 subagent。
---

由另一個 [agent](./Agent.md) 透過 [tool call](./Tool%20call.md) 產生的 agent。在自己的 [session](./Session.md) 裡執行，有自己的 [context window](./Context%20window.md)，並回報單一 [tool result](./Tool%20result.md)。跟 [handoff](./Handoff.md) 不同——parent 明確期待一個回傳結果；handoff 沒有回傳路徑。**不能再產生 subagent**——這棵樹只有一層深。Subagent 存在的目的是隔離 [context](./Context.md)，不是拿來組出階層架構。

重點是把吵雜的工作擋在 parent 的 context 之外。一次大範圍搜尋，或一趟很長的讀檔過程，會產生好幾頁的 tool result，其中大多數只在找到答案之前那一刻有用。在 parent 裡面跑，這些東西就會一直留在 parent 的 context 裡，跟著剩下的 session。在 subagent 裡面跑，雜訊就填滿一個用完即丟的 window，只有最後的報告會進到 parent 的 context。這份報告是 [secondary source](./Secondary%20source.md)：parent 拿到的是 subagent 對它找到什麼的說法，不是原始結果，所以報告裡沒提到的東西，對 parent 來說就是看不見的。

Subagent 也可以同時執行——parent 可以一次對好幾個獨立的工作分頭展開。

_使用情境：_

「grep 的結果快把我的 context 塞爆了。」

「叫一個 subagent 去做搜尋——雜訊會燒在它自己的 context window 裡，最後只回報你真正需要的那兩個檔案路徑。」
