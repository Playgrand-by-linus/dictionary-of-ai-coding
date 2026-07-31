---
description: 不會把任何資訊往後帶。model 在每次請求之間是 stateless 的；agent 預設在 session 之間也是 stateless 的。
---

不會把任何資訊往後帶。[model](./Model.md) 在每次 [model provider request](./Model%20provider%20request.md) 之間是 stateless 的——每次請求都要重新送出完整的 [context window](./Context%20window.md)，因為 model 沒有別的辦法看到其他東西。[agent](./Agent.md) 預設在 [session](./Session.md) 之間也是 stateless 的：新的 session 從空白開始，完全沒有先前 session 的痕跡。與 [stateful](./Stateful.md) 相對。

model 本身是永久 stateless 的：它的 [parameters](./Parameters.md) 在 [training](./Training.md) 之後就是凍結的，你在 [inference](./Inference.md) 時做的任何事都不會改變它們。model 不會從你的糾正裡學習，不會記得昨天已經被講過同一件事，也沒有在慢慢認識你——不論對話感覺起來多不一樣。session 裡那種連續的感覺，是 [harness](./Harness.md) 製造出來的，它保留逐字稿並在每次請求時重新送出。model 不是在記得這場對話，而是在重新讀它。

實際的後果是：如果你想要某件事被跨 session 記住，就得把它寫在某個 agent 會讀回去的地方。這就是 [AGENTS.md](./AGENTS.md.md) 檔案、[memory system](./Memory%20system.md)、[handoff artifact](./Handoff%20artifact.md) 存在的原因——它們是會被載入未來 session [context](./Context.md) 的檔案，替代了 model 沒有的記憶。當 agent 一再犯下你已經糾正過的錯誤，該問的問題不是它為什麼沒學到——它本來就學不到——而是那個糾正應該寫在哪裡，才能讓未來每個 session 都讀得到。

_使用情境：_

「為什麼我每次 [clear](./Clearing.md) 之後它就忘記那個慣例？」

「model 是 stateless 的——新的 session 從空白開始。如果你想要它被帶下去，就寫進 AGENTS.md，或是 harness 在 session 開始時會載入的記憶檔案。」
