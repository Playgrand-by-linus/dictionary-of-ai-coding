---
description: 跑一個訓練好的 model 來產生輸出——每一次 model provider request 都會發生這件事。Parameters 保持不變。
---

跑一個訓練好的 [model](./Model.md) 來產生輸出——這是每一次 [model provider request](./Model%20provider%20request.md) 都會發生的事。[Parameters](./Parameters.md) 保持不變；model 只是對給定的 [context](./Context.md) 做 [next-token prediction](./Next-token%20prediction.md)。相對於 [training](./Training.md) 便宜很多，但是按 [token](./Token.md) 計費，也是使用 model 時最主要的花費。

一個 model 的生命分成兩個階段：

| 階段      | 什麼時候發生              | 做什麼事                                         | Parameters |
| --------- | ------------------------- | ------------------------------------------------ | ---------- |
| Training  | 一次性，在發布之前        | 從 training corpus 產生 parameters               | 正在被寫入 |
| Inference | 每次有人使用這個 model 時 | 讓凍結的 parameters 跑過你的 context，產生 token | 唯讀       |

在 inference 這個階段做的任何事，都不會寫回 parameters——這就是為什麼你今天做的修正，明天不會留下來。Model 下一個 [session](./Session.md) 又犯一樣的錯，即使你上次仔細解釋過怎麼修，也不是它不理你；它就是沒辦法從那次對話裡學到東西。Model 是 [stateless](./Stateless.md) 的——延續性得從外面來，來自 [context window](./Context%20window.md) 或 [memory system](./Memory%20system.md)。

這個機制也解釋了你的帳單怎麼算。每一次 request 都是讓 model 跑過整個 context，所以成本會隨著 [input tokens](./Input%20tokens.md) 跟 [output tokens](./Output%20tokens.md) 增加，一個 agent 打了幾十次 [tool](./Tool.md) call，每一次來回都要付一次 inference 的錢。這就是為什麼 context 大小既是成本問題，也是品質問題。

_使用情境：_

「為什麼帳單是隨用量算，不是固定的授權費？」

「你付的是 inference 的錢——每一次 model provider request 都是在 provider 的硬體上跑一次 model。Training 已經做完了，但 inference 的成本是按 request 累加的，一個 [turn](./Turn.md) 只要有呼叫 tool，就可能展開成好幾次 request。」
