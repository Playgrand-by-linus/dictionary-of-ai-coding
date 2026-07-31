---
description: agent 動手的那個世界——harness 以外，agent 透過 tool result 感知、透過 tool call 改變的一切。
---

[Agent](./Agent.md) 動手的那個世界——[harness](./Harness.md) 以外，agent 透過 [tool result](./Tool%20result.md) 感知、透過 [tool call](./Tool%20call.md) 改變的一切。harness 負責「執行」agent；environment 則是 agent「工作的地方」。像 [AGENTS.md](./AGENTS.md.md) 這樣的檔案，住在 environment 裡；把它載入 [context window](./Context%20window.md) 的，是 harness。[Filesystem](./Filesystem.md) 是最常見的一種 environment，但不是唯一的一種（資料庫、遠端 API、瀏覽器 session 都可以是 environment）。

Agent 只有在去看的時候，才看得到 environment。它對 environment 的一切了解，都是透過某一次 tool result 得來的，所以它手上的畫面，是一堆快照的集合，每一張在拍下來的當下都是準的。如果一個檔案在 agent 讀過之後又變了——你手動改了它，或是某個 build 步驟重新產生了它——agent 會繼續拿那份過時的副本來推理，直到有什麼東西促使它重新讀取。Agent 一臉篤定地描述一個早就長得不一樣的檔案，通常就是這個原因：environment 動了，快照沒有跟著動。

Environment 也是唯一會持續存在的那一層——唯一始終是 [stateful](./Stateful.md) 的一層。一個 [session](./Session.md) 的 context 在 session 結束時就沒了，但寫進 environment 的檔案會留下來，讓下一個 session 讀取——這正是 [memory system](./Memory%20system.md)、[handoff artifact](./Handoff%20artifact.md)、還有 AGENTS.md 賴以運作的基礎。任何 agent 明天還應該記得的事，都必須最終落腳在 environment 裡。

Environment 有多大，是你決定的。[Sandbox](./Sandbox.md) 會把它縮小，限制 agent 碰得到什麼；加一個 [tool](./Tool.md) 會把它擴大，把一個資料庫或 API 納入可及範圍。邊界裡面的東西，才是 agent 能感知、能改變的；邊界以外的一切，對 agent 來說根本不存在。environment 有沒有妥善設置來支援 agent 的工作，就是這個 codebase 的 [AX](./AX.md)。

*避免使用：*把「environment」拿來指 runtime 或 harness 本身——harness 是外層的包裝，environment 才是工作空間。

_使用情境：_

「agent 看不到 staging 資料庫的 schema。」

「把它接進 environment——給它一個限定在 staging、唯讀的 `psql` tool。harness 本身沒問題，只是沒有東西可以動手。」
