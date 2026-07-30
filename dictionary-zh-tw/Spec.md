---
description: 描述跨多個 session 之工作項目的 handoff artifact——說明要打造的是什麼，而非每個 session 怎麼分工。由 ticket 組成。
---

一份描述跨多個 [session](./Session.md) 工作項目的 [handoff artifact](./Handoff%20artifact.md)——說明要打造的是什麼，而不是每個 session 各自怎麼做。隨著工作推進會不斷變動。由 [ticket](./Ticket.md) 組成。

Spec 之所以存在，是因為 session 是可拋棄的，但大型工作不是。任何需要超過一個 [context window](./Context%20window.md) 心力的事，都需要一個在 [context](./Context.md) 之外的棲身之處——放在 agent 的 [environment](./Environment.md) 裡某個能撐過 [clearing](./Clearing.md) 的地方，可以是 repo 裡的一份檔案、一個 GitHub issue，或是 agent 能存取的 issue tracker。Spec 就是那個棲身之處：目標、限制條件、目前為止做過的決定，以及各個 ticket 及其狀態的清單。任何一個全新的 session 都能讀它，就能知道工作進度到哪裡，而不用繼承前一個 session 累積下來的雜訊。

Spec 有幾種認得出來的風格，大多承襲自團隊原本就有的紀錄方式。_product requirements document_（PRD）偏重面向使用者的「做什麼」與「為什麼」——功能、行為、驗收標準。_design doc_ 或 _RFC_ 偏技術——選定的做法、被否決的替代方案、取捨。規模小一點的，一份單純的 `plan.md`、附上 ticket 的檢查清單，對一個跨多 session 的功能來說也是同樣的作用。風格不是重點，角色才是：對 [agent](./Agent.md) 來說，這些都是同一件事——每個 session 開始時都要讀的、持久的意圖陳述。

_使用情境：_

「這整件事應該全部塞進一個 session 嗎？」

「不要，寫成一份 spec——拆成 ticket，每個 ticket 各自跑一個 session。想在單一 context 裡做完整件事，還沒做到一半就會撞進 [dumb zone](./Smart%20zone.md)。」
