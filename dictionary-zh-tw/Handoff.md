---
description: 把 agent 的 context 從一個 session 傳到另一個，沒有回頭路——傳遞機制不只一種，artifact、compaction 等等。
---

把 [agent](./Agent.md) 的 [context](./Context.md) 從一個 [session](./Session.md) 傳到另一個。傳遞機制不只一種——寫成文件的 [handoff artifact](./Handoff%20artifact.md)、記憶體裡的摘要（[compaction](./Compaction.md)），還有其他做法。這跟 [clearing](./Clearing.md)（完全不傳遞）不一樣。理由各式各樣：切換角色（規劃者換成實作者）、啟動一次 [AFK](./AFK.md) 執行、分散成多個平行 session，或是騰出 [context window](./Context%20window.md) 的空間。

接收端的 session 從零 context 開始——[model](./Model.md) 是 [stateless](./Stateless.md) 的，舊 session 裡的東西，新 session 一樣都看不到。下一個 session 需要的東西，都得明確地傳過去；剩下的就全部沒了。「沒有回頭路」是塑造這個傳遞方式的限制條件：新 session 沒辦法回頭問舊 session 當初是什麼意思，所以傳過去的內容必須自己就站得住腳。

| 機制             | 形式                                     | 特性                                                            |
| ---------------- | ---------------------------------------- | --------------------------------------------------------------- |
| Handoff artifact | [Environment](./Environment.md) 裡的檔案 | 可以在任何東西依賴它之前先讀過、修正；能被多個 session 重複使用 |
| Compaction       | Context window 裡的摘要                  | 自動且便宜；比較難檢查；只餵給下一個 session                    |

一次糟糕的 handoff，看得見的失敗徵狀是舊事重提：新 session 把舊 session 已經拍板的決定又重新打開來討論，因為傳遞下來的內容只記了決定了什麼，沒記為什麼。要評斷一次 handoff 好不好，就看一個零 context 的 session 拿到它能做出什麼。

_使用情境：_

「規劃的 session 越來越吃重了——要不要就這樣硬撐下去？」

「做一次 handoff。把決定寫進文件，clear 掉，然後在一個全新的 session 裡開始實作，從那份文件讀起。」
