---
description: 一個可教的能力，打包成一個單位——放在 environment 裡，直到 context pointer 把它拉進當下任務要用的 context window。
---

一個可教的能力，打包成一個單位——把做好一件事的指示跟資源放在一起，留在 [environment](./Environment.md) 裡，直到一個 [context pointer](./Context%20pointer.md) 把它拉進 [context window](./Context%20window.md)，給當下的任務用。這是 [harness](./Harness.md) 裡 [progressive disclosure](./Progressive%20disclosure.md) 的最小單位。

Skill 是一個開放標準，定義在 [agentskills.io](https://agentskills.io)——最早由 Anthropic 開發，後來被大多數主流 harness 採用，所以一個寫好的 skill 可以跨這些 harness 通用。它的格式是一個資料夾，裡面有：

- 一個 `SKILL.md` 檔案——metadata（至少要有名稱跟描述）加上指示本身
- 選擇性地，放 [agent](./Agent.md) 可以執行的 script
- 選擇性地，放指示裡會提到的樣板跟參考資料

預設只有名稱跟描述會放進 [context](./Context.md) 裡。當 agent 的任務對上了，才會把其他部分載進來。在那之前，skill 幾乎不佔空間——不管它完整的指示有多長，都只佔一兩句話的 [token](./Token.md)。

這讓 skill 跟 [AGENTS.md](./AGENTS.md.md) 不一樣，後者不管任務是什麼，每個 [session](./Session.md) 都會載入。Skill 是在特定種類的工作出現的時候才被讀取——上線、幫新服務搭骨架、寫一個 migration——其他時候都不理它。

_避免使用：_「[tool](./Tool.md)」——tool 是 agent「呼叫」的東西；skill 是它「讀」的指示。

_使用情境：_

「部署手冊該放在哪裡？」

「放成一個 skill——agent 只有在任務牽涉到部署的時候才會載入它。放在 AGENTS.md 裡的話，每個 [turn](./Turn.md) 都要為了一個我們一週只用一次的東西燒 token。」
