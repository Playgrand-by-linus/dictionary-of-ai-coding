---
description: Session 剛開始時 agent 敏銳又專注。隨著 session 變大，它會滑進 dumb zone：變得馬虎、健忘、更容易出錯。
aliases:
  - Dumb zone
  - Smart zone / Dumb zone
---

Session 剛開始的時候，[agent](./Agent.md) 處在「smart zone」裡——敏銳、專注，記得住東西。隨著 session 變大，它會滑進「dumb zone」：變得馬虎、健忘、更容易出錯——也更容易出現忠實性 [hallucination](./Hallucination.md)。同一個 [model](./Model.md)，同一個 [harness](./Harness.md)——只是 [context](./Context.md) 變多了。這是 [attention degradation](./Attention%20degradation.md) 讓人感覺到的效果。在前沿 model 上，dumb zone 通常從 125K 到 150K 個 [token](./Token.md) 左右開始——不過這個數字還有爭議。Session 一旦膨脹，就 [clear](./Clearing.md) 或 [compact](./Compaction.md)，不要硬撐下去。

這種衰退是漸進的，所以很容易被忽略。沒有錯誤訊息，也沒有看得見的分界線；agent 只是開始表現得稍微差一點，然後明顯差一點。常見的徵兆：它忘了你二十個 turn 前給過的指示、重複一個它已經修正過的錯誤、或是很有自信地講出一句 context 明明反駁掉的話。因為滑落的過程很平順，常見的反應是硬撐下去、重講一次——這只會加更多 context 進去，讓問題更嚴重。

這些「zone」跟不上 [context window](./Context%20window.md) 的上限走。一個 session 可以已經深陷 dumb zone，但 window 大部分還是空的：上限是 harness 拒絕繼續下去的地方，但品質早在那之前就開始下滑了。要照著 smart zone 規劃，不是照著 window 規劃——一個任務實際上能用的預算，是 agent 表現良好的那些 token，不是它技術上裝得下的那些 token。

Smart zone 是一個預算，不相關的工作會花掉它。一個 session 裡做的每一項任務都會花掉 token，所以在同一個 session 裡開始第二項任務，就等於離 dumb zone 更近一點才開始。一個 session 只做一件任務，能讓每項任務都用到 session 裡最敏銳的那部分。當單一任務比一個 smart zone 還大的時候，就把它拆開：在一個自然的邊界上 [hand off](./Handoff.md) 或 compact，讓一個新的 session 做下一段。

_使用情境：_

「前三個元件它做得很漂亮，第四個就整個做爛了。」

「你已經出了 smart zone——同一個 model，只是現在深陷 dumb zone 了。Compact 一下，重新載入計畫，下一個元件就會做對。」
