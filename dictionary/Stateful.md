---
description: 把資訊往後帶。session 在 turn 之間是 stateful 的；agent 可以透過 memory system 在 session 之間做到 stateful。
---

把資訊往後帶。[session](./Session.md) 在 [turn](./Turn.md) 之間是 stateful 的——[context](./Context.md) 會隨著 session 進行不斷累積，這也是為什麼長時間的 session 會漂向 [dumb zone](./Smart%20zone.md)。[agent](./Agent.md) 可以透過加上一套 [memory system](./Memory%20system.md)，把資訊寫進 [environment](./Environment.md) 並在未來 session 開始時重新載入，做到跨 **session** 的 stateful。[model](./Model.md) 本身永遠不是 stateful 的；任何看起來連續的感覺，都是 [harness](./Harness.md) 把 context 重新餵回去的結果。與 [stateless](./Stateless.md) 相對。

各層級的 state 存在哪裡：

| 層級        | Stateful？ | 怎麼做到                                                                                               |
| ----------- | ---------- | ------------------------------------------------------------------------------------------------------ |
| Model       | 從不       | [Parameters](./Parameters.md) 是凍結的；它只看得到每次請求裡的內容                                     |
| Session     | 跨 turn    | harness 把每一則訊息和 [tool result](./Tool%20result.md) 都附加進 context                              |
| Harness     | 跨 session | 記憶檔案、[AGENTS.md](./AGENTS.md.md)、[handoff artifact](./Handoff%20artifact.md)——寫下來，之後再載入 |
| Environment | 永遠       | 不論有沒有 session 在跑，檔案都會留著                                                                  |

每一層的 stateful 特性，都是靠重新讀取下面一層存的東西做出來的：session 感覺起來連續，是因為 harness 把訊息紀錄重新送給 stateless 的 model；agent 能跨 session 記住東西，是因為 harness 把檔案從 environment 重新載入。model 本身從來沒有存過任何 state。

State 不是永遠都想要的。凡是被往後帶的東西都會影響接下來發生什麼，所以 session 早期做出的錯誤假設，也會一路被帶下去。[clearing](./Clearing.md) 就是刻意把 session state 丟掉、從寫下來的東西重新開始的動作。

_使用情境：_

「它記得我昨天的偏好——這代表 model 學到了嗎？」

「不是，agent 是 stateful 的，因為 harness 把偏好寫進了記憶檔案，並在 session 開始時重新載入。model 本身完全沒看到昨天發生的事。」
