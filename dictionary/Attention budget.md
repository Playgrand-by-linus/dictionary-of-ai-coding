---
description: 每個 token 能分配出去的影響力是有限的，要分給 context 裡其他所有 token。是逐 token 算的，不會因為 context 變大就跟著變大。
---

每個 [token](./Token.md) 能拿來分配的影響力是有限的，要分給 [context](./Context.md) 裡其他所有 token。在[某一組關係](./Attention%20relationship.md)上分配得多，留給其他關係的就少。這個預算是逐 token 計算的，不會因為 context 變大就跟著變大，這也是為什麼長時間的 [session](./Session.md) 會被稀釋。

可以把它想成訊號跟雜訊。你的指示是一個音量固定的訊號；[context window](./Context%20window.md) 裡其他每一個 token 都是在跟它搶音量的雜音。指示本身不會變小聲——它還在那裡，一字不差——但隨著 context 變大，周圍的環境越來越吵，訊噪比就跟著往下掉。一個在 1 萬 token 的 context 裡最響亮的指示，到了 15 萬 token 就變成背景雜音。這就是 [attention degradation](./Attention%20degradation.md) 背後的機制：model 不是忘記了，是訊號被淹沒在雜訊裡。

這個症狀讀起來像是不聽話——agent 一開始答應遵守某個限制，之後卻慢慢偏離，把限制重貼一次也只有短暫的效果。問題不在那條指示本身，而在 context window 裡其他所有跟它搶注意力的東西。

你能控制的是放進 context 裡的內容。跟任務無關的內容不是中性的——它是壓在所有有用內容之上的雜訊。把 context window 維持得小一點，在累積的 context 不再划算的時候就 [clear](./Clearing.md)，並且重申真正重要的限制，而不是相信它早先提過一次就會一直有效。

_使用情境：_

「為什麼它一直不理會我一開始貼的 schema？」

「我們已經深入 [dumb zone](./Smart%20zone.md) 了——每個 token 的 attention budget 是固定的，但 context 一直在變大。Schema 上的訊號現在正在跟成千上萬個更新的 token 搶注意力。」
