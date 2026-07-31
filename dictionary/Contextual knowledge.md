---
description: agent 現在可以直接從 context 讀到的事實，是 parametric knowledge 的對應概念。
---

[Agent](./Agent.md) 現在可以直接從 [context](./Context.md) 裡讀到的事實——使用者的任務、agent 讀進來的檔案、[tool result](./Tool%20result.md)、[session](./Session.md) 開始時載入的 [AGENTS.md](./AGENTS.md.md) 內容。這是 [parametric knowledge](./Parametric%20knowledge.md) 的對應概念：parametric 是從參數裡「回想」出來的，contextual 是從 [window](./Context%20window.md) 裡「讀」出來的。當 agent 是靠 contextual knowledge 工作時，[hallucination](./Hallucination.md) 少很多——答案就攤在眼前，不是從模糊的記憶裡挖出來的。

兩種知識裡，只有 contextual knowledge 是你能掌控的。參數是凍結的，所以要讓 [model](./Model.md) 得到它原本沒有的知識——一個內部 SDK、一個在 [knowledge cutoff](./Knowledge%20cutoff.md) 之後才發布的函式庫、昨天才做的決定——唯一的辦法就是把它放進 context 裡。很多實際的 [AI](./AI.md) coding 工作，說到底就是這件事：在 model 需要的那個當下，把對的事實放到它面前。

當 contextual 跟 parametric knowledge 互相矛盾時，通常是 contextual 贏。貼上目前的 API 文件，model 會照著文件走，而不是照著它對舊 API 那份模糊的記憶——不過舊版本還是可能滲透進來，尤其是 session 拖得很長之後。如果文件都已經載入了，agent 卻還是一直退回舊的寫法，那就是 parametric knowledge 滲透過了 contextual；把更正的內容再講一次，或是搬到離工作更近的地方，會有幫助。

跟 parametric knowledge 不一樣，contextual knowledge 用起來是有成本的。載入 window 的每一樣東西都在花 [token](./Token.md)，也在跟 model 的 [attention budget](./Attention%20budget.md) 搶位置，所以載入得越多不代表越好——目標是把相關的事實放進 window，不是把所有事實都塞進去。

_只有在跟 parametric knowledge 對照時_ 才需要用這個詞；其他情況直接說 context 就好。

_避免使用：_「working memory」——contextual knowledge 是現在窗口裡有什麼；[memory system](./Memory%20system.md) 則是把跨 session 的內容送進窗口的機制。這是不同層級的東西，別混為一談。

_使用情境：_

「為什麼我貼上文件它就抓得準，不貼就自己捏造？」

「文件貼進去的時候，用的是 contextual knowledge——照著頁面讀。沒貼的時候是 parametric，冷門的 endpoint 就會模糊掉。」
