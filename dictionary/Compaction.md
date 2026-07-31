---
description: "一種在記憶體裡完成的 handoff：前一個 session 的歷史被摘要,再用摘要開一個全新的 session。有損——用細節換取空間。"
---

一種在記憶體裡完成的 [handoff](./Handoff.md)：前一個 [session](./Session.md) 的歷史被摘要，再用這份摘要開一個全新的 session。設計上就是有損的：transcript 是 [primary source](./Primary%20source.md)，摘要是 [secondary source](./Secondary%20source.md)——用細節換取空間。可以由使用者手動觸發，也可以透過 [autocompact](./Autocompact.md) 自動觸發。

運作機制是這樣：[context window](./Context%20window.md) 是有限的，一個長 session 會把它填滿——每一個 [tool result](./Tool%20result.md)、每一次讀檔、每一次走錯的方向都留在歷史裡。當它變得太重時，[harness](./Harness.md) 會請 [model](./Model.md) 把 session 摘要一遍，丟掉原本的歷史，再用這份摘要開一個新 session。沒有寫進摘要裡的東西，就從 context 裡消失了。有些 harness 會軟化這個問題：把舊的 transcript 留在硬碟上，在摘要裡留一個指向它的 [context pointer](./Context%20pointer.md)——這個 secondary source 連回它的 primary source，所以摘要弄丟的細節還能靠重讀原文找回來。

摘要是由 model 寫的，所以可以下指示。「保留 schema 相關的決定」這樣的提示，會讓產生出來的成果更用心。時機也很重要——在階段的分界點、計畫已經定下來之後 compact，不要在任務進行到一半的時候做。

跟 [clearing](./Clearing.md) 對比一下：clearing 什麼都丟掉，從冷開始；compaction 試著把重點帶過去——clearing 賭的是這些重點已經寫在別的地方更好的位置了。

_使用情境：_

「[Context](./Context.md) 越來越重了，我還有測試沒跑完。」

「先 compact——把一定要留下來的東西寫進摘要的提示裡，這樣新 session 才會保留 schema 的決定，丟掉探索過程。」
