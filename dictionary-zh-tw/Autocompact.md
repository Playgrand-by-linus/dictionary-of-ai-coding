---
description: 當 context window 快滿的時候，由 harness 自動觸發的 compaction。
---

當 [context window](./Context%20window.md) 快滿的時候，由 [harness](./Harness.md) 自動觸發的 [compaction](./Compaction.md)。

Harness 會監控 context window 塞了多滿。一旦跨過某個門檻——通常大約在 80% 左右——它就會暫停，請 [model](./Model.md) 把目前的 [session](./Session.md) 摘要一遍，再用這份摘要開一個全新的 session。之後工作照常繼續，像什麼事都沒發生過一樣。

只是其實發生了事情。Compaction 本來就會遺失細節，而 autocompact 是在一個你沒有選擇的時間點遺失細節。手動 compact 通常發生在階段的分界點，那時候你可以告訴 model 該保留什麼。Autocompact 則是在任務進行到一半、門檻一到就觸發——有可能正好卡在一次重構做到一半，由摘要自己決定你哪些決定值得留下來。典型的症狀是：[agent](./Agent.md) 表現得一副信心十足的樣子繼續做下去，卻悄悄忘記了一小時前你定下的某個限制，等你發現的時候，是因為它的成果已經開始跟那個限制矛盾了。

防範的辦法是不要讓它觸發。留意 context 指標，在一個自然的分界點手動 compact，或是把決定寫進一份計畫文件或 [handoff artifact](./Handoff%20artifact.md)，存在硬碟上，讓任何摘要都不可能弄丟它。大多數 harness 也讓你自訂緩衝空間——把門檻調早一點或晚一點，或是乾脆整個關掉 autocompact——這樣你就能自己調整觸發前要留多少餘裕。

_使用情境：_

「它好像不記得我們之前對 schema 做的決定了。」

「Autocompact 在兩個 [turn](./Turn.md) 之間觸發了——早先的決定被摘要過，一定是漏掉了什麼。重新載入計畫文件，或者下次自己手動 compact，這樣才能控制留下什麼。」
