---
description: 圍繞在 model 周圍、把它變成 agent 的所有東西：tool、system prompt、context window 管理、permission、hook。
---

圍繞在 [model](./Model.md) 周圍、把它變成 [agent](./Agent.md) 的所有東西：[tool](./Tool.md)、[system prompt](./System%20prompt.md)、[context window](./Context%20window.md) 管理、permission、hook。**Claude.ai** 跟 **Claude Code** 跑在同一個 model 上，但行為不一樣，因為兩者的 harness 不同。

Model 本身只做一件事：吃文字進去，吐文字出來。它不能讀檔案、跑指令，也記不住上一個 [turn](./Turn.md)。這些全部都是 harness 提供的。它替每一次 [model provider request](./Model%20provider%20request.md) 組出 [context](./Context.md)、執行 model 要求的 [tool call](./Tool%20call.md)、把 [tool result](./Tool%20result.md) 餵回去、儲存 [session](./Session.md) 紀錄、在有風險的動作前問你要不要放行，還要決定什麼時候該 [compact](./Compaction.md)。Agent loop——model 提議、harness 執行、一直重複——是由 harness 在跑的。

這對診斷問題很重要。兩個產品之間行為不一樣，或者昨天跟今天不一樣，通常不是 model 在變，是 harness 在變。不同的 system prompt、不同的 tool 組合、改過的 permission 預設值、新的 context 管理策略，都會改變行為，而 model 完全沒變。這也代表你大部分的設定都放在 harness 這一層：[AGENTS.md](./AGENTS.md.md) 檔案、permission 設定、hook，這些指示都是給 harness 的，不是給 model 的。

範例：Claude Code、Cursor、Codex CLI——還有 Claude.ai，它是一個聊天用的 harness，不是寫程式用的。

_使用情境：_

「同一個 model，為什麼 Claude Code 會改檔案，Claude.ai 卻只會回答問題？」

「Harness 不一樣——Claude Code 有 [filesystem](./Filesystem.md) tool、不同的 system prompt，還有一層 permission。這裡不一樣的不是 model。」
