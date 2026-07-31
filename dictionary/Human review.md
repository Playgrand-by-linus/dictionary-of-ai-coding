---
description: 使用者閱讀 agent 產出的程式碼並形成判斷。讀 diff 算數，讀摘要不算數。
---

使用者閱讀 [agent](./Agent.md) 產出的程式碼，並對它形成判斷。讀 diff 或改過的檔案算數；讀 agent 對自己做了什麼的*描述*不算數——旁白不是產出物本身。這份描述是一份 [secondary source](./Secondary%20source.md)，是被審查的那一方寫的；diff 才是 [primary source](./Primary%20source.md)，human review 指的就是去讀它。

Agent 讓程式碼產出的量變大，review 因此變成瓶頸。一個有用的做法是把不同的審查策略疊起來。[Automated check](./Automated%20check.md) 抓機械式的錯誤，[automated review](./Automated%20review.md) 抓講得出道理的問題，human review 則留給只有你才能判斷的事——這個改動是不是對的改動、這個做法合不合這個 codebase、這東西根本該不該存在。

Review 也是愈早做愈便宜。在動工前讀一份計畫，或做到一半讀一個小 diff，只要幾分鐘；等 [AFK](./AFK.md) 跑完之後再去挖一整條做完的分支，花的時間多得多。Review 的檢查點放在哪裡，是一個 [human-in-the-loop](./Human-in-the-loop.md) 的決定，不是事後才想到的補救。

_避免使用：_「code review」單獨使用——分不清是人做的還是自動做的。

_使用情境：_

「這次 AFK 的產出我有做 human review。」

「你是讀 diff 還是只看摘要？」

「Diff。摘要說它刪掉了死碼——結果那個函式其實被一個生成出來的檔案呼叫。」
