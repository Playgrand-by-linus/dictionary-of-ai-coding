---
description: Model 實際上在做的事。從 context 取樣出下一個 token，接上去，再跑一次。它唯一的運作模式。
---

[Model](./Model.md) 實際上在做的事，就是這個。給定一個 [context](./Context.md)，它取樣出下一個 [token](./Token.md)，接上去，再跑一次。每一個輸出——一句話、一個 [tool call](./Tool%20call.md)、一份上千行的檔案——都是一個 token、一個 token 疊出來的。Model 沒有別的運作模式。

每一步都用同一套方式：[context window](./Context%20window.md) 裡的 token 跑過 [parameters](./Parameters.md)，對詞彙表裡的每一個 token 都算出一個機率——這個接下來很可能出現，那個比較不可能。從這些機率裡取樣出一個 token，接上去，用稍微變長一點的 context 再跑一次這個迴圈。這個取樣的步驟，就是為什麼同一個 prompt 在不同次執行會產生不同輸出：[non-determinism](./Non-determinism.md) 是這套機制內建的，不是後來疊上去的 bug。

抓住這個機制，就能解釋一些原本看起來很奇怪的行為。Model 從來不會在吐出一個 token 之前檢查它是不是*真的*——只檢查它是不是*很可能*——這就是 [hallucination](./Hallucination.md) 的根源。它是邊做邊定案的，所以一句聽起來很有把握的開場白，可能會把接下來整個答案帶偏。而且因為 [output token](./Output%20tokens.md) 是嚴格一個一個產生的，生成速度替任何 [agent](./Agent.md) 能跑多快設了一個下限。

_使用情境：_

「Agent 是怎麼『決定』要呼叫一個 tool 的？」

「它沒有在決定——從頭到尾都是 next-token prediction。Tool call 只是 harness 從輸出串流裡解析出來的一段結構化字串。」
