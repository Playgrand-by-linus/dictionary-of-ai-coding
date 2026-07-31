---
description: agent 讀取、寫入、並在裡面執行指令的檔案與目錄樹——coding agent 預設的 environment。
---

[Agent](./Agent.md) 讀取、寫入、並在裡面執行指令的檔案與目錄樹——coding agent 預設的一種 [environment](./Environment.md)。[AGENTS.md](./AGENTS.md.md)、[skill](./Skill.md)、原始碼、build script、還有 [tool](./Tool.md) 的設定檔，全都住在 filesystem 裡。當一個 [harness](./Harness.md)「在你的專案裡啟動」時，它其實是把 agent 指向某一個 filesystem。

Agent 只能透過 [tool call](./Tool%20call.md) 去碰它——讀一個檔案、寫一個檔案、跑一個 shell 指令。硬碟上的東西，在被某次 tool call 載入之前，都不在 [context window](./Context%20window.md) 裡，這也是為什麼 agent 能在一個遠比 window 大的 repository 裡工作：filesystem 裝著全部的東西，context 只裝著目前任務讀過的部分。有些 harness 預設就會把目前目錄的檔名載入 context window——不是內容，只是這棵樹——這些檔名扮演的角色就是 [context pointer](./Context%20pointer.md)：agent 看得到有什麼東西存在，然後去讀它需要的那些檔案。

而且它是跟你共用的。agent 編輯的檔案，跟你在編輯器裡打開、在 git 裡 diff 的是同一批——filesystem 是你審查 agent 做了什麼的共同工作空間。

_使用情境：_

「為什麼它讀不到我的 AGENTS.md？」

「它跑的是另一個 filesystem——[sandbox](./Sandbox.md) 掛載的是上層目錄，不是專案根目錄。把 harness 重新指過去。」
