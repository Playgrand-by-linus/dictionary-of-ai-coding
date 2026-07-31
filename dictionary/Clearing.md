---
description: 結束目前的 session，開一個全新的。下一則訊息會從一個空的 session 跟空的 context window 開始。
---

結束目前的 [session](./Session.md)，開一個全新的。下一則訊息會從一個空的 session 跟空的 [context window](./Context%20window.md) 開始。通常是由使用者主動觸發。

Clearing 是治療被污染的 context 的方法。一個 session 會累積各種東西：失敗的嘗試、走錯的方向、過時的 [tool result](./Tool%20result.md)、被放棄的計畫。[Model](./Model.md) 每個 [turn](./Turn.md) 都會把這一切重新讀一遍，糟糕的歷史會拖累新的工作。一個長 session 進行到後段，[agent](./Agent.md) 會變得越來越模糊、越來越不聽話——你明明講得很清楚的指示被忽略，品質下滑，就算你催牠做好一點也沒用，因為牠正在涉水而過的那堆雜訊，仍然在牠的 [context](./Context.md) 裡。Clearing 就是把這些雜訊清掉。

Clearing 不會抹掉整段對話。大多數 [harness](./Harness.md) 會把 session 歷史留在你的電腦上，所以那份 transcript 還在，可以拿來讀或恢復。消失的是 agent 的工作狀態：model 是 [stateless](./Stateless.md) 的，所以新的 session 對舊 session 知道的事一無所知。如果這個 session 裡有下一個 session 會需要的決定或進度，先讓 agent 寫一份 [handoff artifact](./Handoff%20artifact.md)，再讓新 session 從那份文件開始。

跟 [compaction](./Compaction.md) 比較一下：compaction 是把 session 摘要進新的 context 裡，而不是從空的開始。Clearing 是更直接粗暴的工具：什麼都不會留下來，包括那些垃圾。

_使用情境：_

「它卡在一個一直失敗的測試上打轉。」

「直接清掉——用計畫文件跟測試檔案開一個全新的 session。跟現有的 context 硬拚沒有意義。」
