---
description: harness 在 session 開始時載入 context window 的檔案，放在 environment 裡——寫給 agent 的專案標準提報。
---

一個放在 [environment](./Environment.md) 裡的檔案，[harness](./Harness.md) 會在 [session](./Session.md) 開始時把它載入 [context window](./Context%20window.md)——是寫給 [agent](./Agent.md) 的專案標準提報。這是跨 harness 的慣例；有些 harness 也有自己的變體（Claude Code 用的是 CLAUDE.md）。

因為它是自動載入的，這是避免跨 session 重複交代同一件事的辦法之一。[Model](./Model.md) 是 [stateless](./Stateless.md) 的——你在一個 session 裡做的修正，到下一個 session 就沒了，於是每次開新 session 都得重講一次：這個專案用 pnpm、測試要加特定 flag、某個目錄是產生出來的不要動。同一件事修正 agent 兩次之後，這條修正就是該寫進 AGENTS.md 的候選內容。

適合放進去的內容，是 agent 沒辦法從程式碼推導出來的東西：build 跟測試指令、程式碼本身看不出來的慣例、硬性限制（「絕對不要改產生出來的 client」）。要短、要直述——它是一份提報，不是文件。

代價是裡面的每一行都會一直被載入。指示會越堆越多，大部分跟手上的任務無關，而一份很長的 AGENTS.md 既耗費 token，也會稀釋自己——context 裡的指示越多，model 確實遵守其中任何一條的機率就越低。

*避免使用：*把該 [progressively disclosed](./Progressive%20disclosure.md) 的內容放進 AGENTS.md——裡面的東西每個 [turn](./Turn.md)、每個 session 都要付一次 [token](./Token.md) 成本，不管那個 session 用不用得到。風格指南可以放到 [skill](./Skill.md) 或 [context pointer](./Context%20pointer.md) 後面；AGENTS.md 留給那些到處都用得到的內容。

_使用情境：_

「為什麼每個 session 一開始就已經燒掉 4k token 了？」

「去看看 AGENTS.md——一定是誰把整份風格指南貼進去了，沒放到 skill 後面。」
