---
description: agent mode 裡負責權限把關的那一層——哪些 tool call 會觸發 permission request，哪些自動放行。
---

[Agent mode](./Agent%20mode.md) 裡負責權限把關的那一層——哪些 [tool call](./Tool%20call.md) 會觸發 [permission request](./Permission%20request.md)，哪些自動放行。在 [harness](./Harness.md) 開始把行為指示一起打包進來之前，這原本就是 mode 系統存在的目的。

Harness 通常提供一整排等級：

| 模式             | 讀取 | 寫入與 shell         | 典型用途                                      |
| ---------------- | ---- | -------------------- | --------------------------------------------- |
| 唯讀／plan       | 自動 | 封鎖                 | 研究、規劃、審閱                              |
| 預設             | 自動 | 詢問                 | 日常有人盯著的工作                            |
| 自動編輯         | 自動 | 編輯自動、shell 詢問 | 信任的 repo、機械式的變更                     |
| 「Yolo」／全自動 | 自動 | 自動                 | [Sandbox](./Sandbox.md)、[AFK](./AFK.md) 執行 |

選哪一個等級，是安全跟被打斷之間的取捨，兩種失敗都會讓人感覺到。太緊，你就變成瓶頸：[agent](./Agent.md) 每隔幾秒就為了無害的讀取停下來，你按核准按到變成反射動作，核准這個動作也就失去意義——這種橡皮圖章式的核准兩頭都不討好，該有的打斷一個沒少，該有的保護一個都沒有。太鬆，agent 就會去改你原本想先看過的檔案、跑你原本想先看過的指令。

鬆的那一端，在 sandbox 裡最站得住腳，因為一個爛 [tool](./Tool.md) call 炸開的範圍是被關住的。在 sandbox 之外，大多數人的做法是讀取自動核准，不可逆的事情則留一個 [human in the loop](./Human-in-the-loop.md)。

_使用情境：_

「它每一個 grep 都要暫停確認——AFK 的執行整個被搞爛了。」

「唯讀的 tool 就把 permission mode 放鬆，寫入跟 shell 還是要問。研究型 [session](./Session.md) 裡大部分的 permission request 都是雜訊。」
