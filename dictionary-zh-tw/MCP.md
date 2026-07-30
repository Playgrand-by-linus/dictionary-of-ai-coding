---
description: 把外部 tool server 接進 harness 的協定——agent 怎麼取得 harness 內建之外的 tool。
---

**Model Context Protocol.** 把外部 tool server 接進 [harness](./Harness.md) 的協定——[agent](./Agent.md) 怎麼取得 harness 內建之外的 [tool](./Tool.md)。Agent 從來不會「呼叫 MCP」；它呼叫的是一個 tool，只是這個 tool 剛好是 harness 從某個 MCP server 拿到的。MCP 也會提供 resource（唯讀資料）跟 prompt（可重複使用的樣板），但提供 tool 才是主要用途。

這個協定解決的是一個整合問題。沒有這個標準的話，每一個 harness 都得自己寫一套 Linear 整合、一套 Slack 整合、一套資料庫整合——每一個都要分開寫、分開維護。有了 MCP，整合只要寫成一個 server 一次，任何相容 MCP 的 harness 都能用。Harness 連到 server，server 宣告自己提供哪些 tool，這些 tool 就跟內建的 tool 一起變成 agent 能用的東西。

代價要用 [context](./Context.md) 付。Server 宣告的每一個 tool，都會變成一份定義——名稱、描述、參數 schema——而 [model](./Model.md) 只能呼叫它知道的 tool。最直接的做法是把每一份定義都預先載進 [context window](./Context%20window.md)：裝了幾個內容豐富的 server，一個 [session](./Session.md) 還沒開始打字，就已經有好幾千個 [token](./Token.md) 的 tool schema，佔掉了做這個任務根本用不到的那些 tool 的 [attention budget](./Attention%20budget.md)。

現在很多 harness 會用 tool search 來緩解這個問題：context 裡放的不是完整定義，而是一個指向可用 tool 的 [context pointer](./Context%20pointer.md)——agent 依名稱或用途去搜尋 tool，只有需要的時候才載入它的定義。如果你的 harness 沒做這件事，預先付出的成本就還在，這時候只裝專案真的用得到的 server 才划算。

_使用情境：_

「Agent 需要讀 Linear 的 ticket。」

「把 harness 設定成用 Linear 的 MCP server——它會把 Linear 的 API 變成 agent 能呼叫的 tool。省得你自己寫客製化的 tool wrapper。」
