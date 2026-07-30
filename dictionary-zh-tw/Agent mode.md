---
description: 一種預設組合，把 permission mode 跟注入 system prompt 的行為指示綁在一起。可以在 session 中途切換。
aliases:
  - plan mode
  - accept-edits
  - bypass permissions
  - YOLO mode
---

一種預設組合，決定 [agent](./Agent.md) 在執行時怎麼運作——把一個 [permission mode](./Permission%20mode.md) 跟注入 [system prompt](./System%20prompt.md) 的行為指示綁在一起。例如：預設模式會在有風險的呼叫上詢問；**plan mode** 會封鎖編輯、引導 agent 去做研究；**accept-edits** 模式會自動核准編輯；**bypass permissions** 模式（口語上叫 **YOLO mode**）會自動核准所有事情。可以在 [session](./Session.md) 中途切換。

把兩者綁在一起，正是 mode 跟單純的權限設定不一樣的地方。Permission mode 只是一道閘門：它決定哪些 [tool call](./Tool%20call.md) 能通過。光有閘門會做出一種 agent：牠想編輯卻不能——牠提出寫入請求，被擋下來，再試別的辦法。注入的指示把那個「想」拿掉了：plan mode 不只是封鎖編輯，它還告訴 agent 現在是規劃階段，所以 agent 會去讀、去問、去提案，而不是硬頂著閘門。閘門跟引導的方向是一致的。

實務上，你會隨著任務過程中信任程度的變化去切換 mode。同一個任務可以經過好幾種 mode：做法還在成形時用 plan mode，最早幾筆細膩的編輯用預設的詢問模式，agent 表現出牠理解這個變更之後換成 accept-edits，[AFK](./AFK.md) 在 [sandbox](./Sandbox.md) 裡跑的時候用 bypass。切換 mode 不用付出任何代價：對話會從原本的地方繼續，只是換了新的權限跟新的指示。如果你發現自己每個提示都不看就核准，代表 mode 設得比你實際的信任程度還緊；如果你一直在拒絕編輯，代表設得太鬆了。

\_廠商用詞：\_Claude Code 把這些叫做「permission mode」，Codex 叫做「approval mode」——兩者都早於行為綁定這個做法。

_使用情境：_

「它一直在改檔案，我只是想要一份計畫。」

「切到 plan mode——它會封鎖寫入，停在研究階段。」

「那之後的 AFK 跑法呢？」

「Bypass mode，但只能在 sandbox 裡面用。」
