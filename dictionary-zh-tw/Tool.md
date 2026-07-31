---
description: harness 開放給 agent 呼叫的函式——Read、Write、Bash、Search。agent 感知並操作 environment 的方式。
---

[harness](./Harness.md) 開放給 [agent](./Agent.md) 呼叫的函式——Read、Write、Bash、Search。tool 是 agent 感知並操作 [environment](./Environment.md) 的方式：除了透過 [tool result](./Tool%20result.md)，agent 沒辦法看到 environment；除了透過 [tool call](./Tool%20call.md)，agent 也沒辦法改變它。每一次 tool call 都要多花一次 [model provider request](./Model%20provider%20request.md)，因為結果得先送回 model，它才能決定下一步要做什麼。

大多數 coding agent 內建的 tool：

| Tool   | 作用                                              |
| ------ | ------------------------------------------------- |
| Read   | 把檔案內容當成 tool result 回傳                   |
| Write  | 在 [filesystem](./Filesystem.md) 裡新增或編輯檔案 |
| Bash   | 執行一個 shell 指令並回傳輸出                     |
| Search | 在整個 codebase 裡找出符合某個模式的檔案或文字    |

一個 tool 由三件事定義：名稱、一段描述它做什麼的說明，以及它參數的 schema。harness 會在每一次請求裡把這些定義送給 [model](./Model.md)，而 model 選 tool 的方式，跟它產生其他所有東西一樣——靠寫 [token](./Token.md)，在這裡就是一個附帶參數的結構化呼叫。model 從來不會自己執行任何東西；harness 讀這個呼叫、執行對應的函式，再把結果送回去。

tool 清單決定了 agent 能做什麼。一個能力很強的 model，配上很窄的 tool 集合，出來就是一個能力很窄的 agent：它會把所有事都硬塞進手上有的那幾個 tool，這也是為什麼 agent 這麼依賴 Bash——一個 shell 就是一個能碰到系統裡大部分東西的 tool。要乾淨俐落地給 agent 加上某個能力，就替它加一個 tool；[MCP](./MCP.md) 是從 harness 外部接入 tool 的標準做法。

tool 的定義在每一次請求裡都會佔掉 [context](./Context.md)，所以一個很大的 tool 集合，在任何 tool 被呼叫之前就已經有固定的成本——而且很多描述相似的 tool 放在一起，只會讓 model 更難挑對該用哪一個。

_使用情境：_

「agent 可以直接查詢 staging 嗎？」

「在 harness 裡加一個 `psql` tool，限定在 staging 上唯讀。沒有對應的 tool，agent 對 filesystem 之外的東西完全看不到。」
