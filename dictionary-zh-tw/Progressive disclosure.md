---
description: 只載入 agent 現在需要的 context，其餘的用 context pointer 指過去。概念借自 UI 設計。
---

只載入 [agent](./Agent.md) 現在需要的 [context](./Context.md)，其餘的用 [context pointer](./Context%20pointer.md) 指過去。概念借自 UI 設計，在那裡它指的是只給使用者看跟他們目前任務相關的控制項，其餘的都藏在一次點擊之後。

這個技巧存在的原因是 context 要付兩次代價。每一個提前載入的 [token](./Token.md)，在每一個 [turn](./Turn.md) 都會被算成 [input tokens](./Input%20tokens.md) 計費，而且不管 agent 用不用得到，每一個 token 都在花 [attention budget](./Attention%20budget.md)。一份塞滿完整風格指南、部署手冊、資料庫慣例的 [AGENTS.md](./AGENTS.md.md)，會讓 agent 在這幾件事上全都變差——真正跟目前任務相關的指示，被跟這次任務無關的東西稀釋掉了。徵兆就是：agent 明明你知道它 context 裡有某條規則，它卻不理——規則是在裡面沒錯，只是被埋起來了。

Progressive disclosure 把這個順序反過來。把永遠會載入的那一層盡量做小——每個主題就一句話，加一個指向細節在哪裡的指標。Agent 在寫元件的時候讀風格指南，在部署的時候讀部署手冊，修測試的時候兩個都不讀。[Skill](./Skill.md) 就是這個模式內建在 [harness](./Harness.md) 裡的樣子：每個 [session](./Session.md) 都會載入的簡短描述，只有在被觸發的時候才載入完整指示。

_使用情境：_

「要把整份風格指南塞進 AGENTS.md 嗎？」

「不要——用 progressive disclosure。把風格指南做成一個 skill，agent 真的要寫元件的時候才載入。AGENTS.md 是每個 turn 都要付 token 成本的。」
