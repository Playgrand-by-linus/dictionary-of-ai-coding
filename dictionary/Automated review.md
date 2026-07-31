---
description: "一個 agent 在審查另一個 agent 的工作成果，通常用不同的 model 或 system prompt。非確定性：它會形成一個判斷。"
---

一個 [agent](./Agent.md) 審查另一個 agent 的工作成果，通常用不同的 [model](./Model.md) 或 [system prompt](./System%20prompt.md)。非確定性：它會形成一個判斷。可以在任何地方跑——PR 合併前、事後審查 commit 歷史、session 進行中當一個 [subagent](./Subagent.md) 跑。在 CI 裡跑一個 LLM-as-judge 屬於 automated review，不是 [automated check](./Automated%20check.md)；決定分類的是這個斷言在「做什麼」，不是它跑在哪裡。

跟寫程式碼的那個 agent 分開，正是這個做法有效的原因。叫寫出程式碼的那個 agent 自己審查自己的工作，得到的東西通常很少——產生 bug 的那個 [session](./Session.md) 裡，也裝著產生這個 bug 的那套推理過程，agent 讀回自己的結論時，只會把它當成確認。一個帶著全新 [context window](./Context%20window.md) 的審查者沒有這種包袱：牠看這份 diff 的方式就像一個陌生人，而 review 要靠的正是這種陌生感。換一個 model，或用一個專門為審查寫的 system prompt，可以再加強這一點——不同的盲點，加上一個聚焦在你真正在意的事（安全性、API 合約、效能）的 system prompt，而不是一句籠統的「找找看有沒有問題」。

它卡在其他審查層之間。Automated check 是確定性的，能抓到能被機械斷言的東西；[human review](./Human%20review.md) 成本高，也是最難擴大規模的一層。Automated review 卡在中間：它用機器的成本，抓那些需要判斷力的問題——一個誤導性的函式名稱、一個漏掉的邊界情況。因為它是非確定性的，它可能漏掉問題，也可能誤報不存在的問題；把它當成一道在人看之前先拉高底線的濾網，而不是一道能取代人的關卡。

_避免使用：_「AI review」／「agent review」——太模糊，分不清跟寫程式碼的那個 agent 本身有什麼不同。

_使用情境：_

「我們從 [AFK](./AFK.md) 跑出來的 PR 品質太差的太多了。」

「合併前加一道 automated review——用不同的 model、獨立的 system prompt，聚焦在安全性跟合約的變更上。」
