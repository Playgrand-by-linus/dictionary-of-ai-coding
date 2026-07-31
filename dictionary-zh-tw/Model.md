---
description: Parameters。Stateless——只做 next-token prediction，別的都不做。自己一個沒辦法做任何 agentic 的事。
---

[Parameters](./Parameters.md)。[Stateless](./Stateless.md)——只做 [next-token prediction](./Next-token%20prediction.md)，別的都不做。「Claude Opus 4.x」跟「GPT-5.x」都是 model。Model 自己一個沒辦法做任何 agentic 的事；它得被 [harness](./Harness.md) 包起來才行。

Model 不能讀檔案、跑指令、瀏覽網頁，也記不住昨天發生的事——它就是吃 [token](./Token.md) 進去，每一次 [model provider request](./Model%20provider%20request.md) 預測出 token 出來。所有感覺起來像 [agent](./Agent.md) 在做事的部分——挑 [tool](./Tool.md)、讀結果、一直循環到任務做完——其實都是 harness 把一大串這種預測串起來執行。

[Model provider](./Model%20provider.md) 出的 model 有分等級：一個最聰明但慢又貴的大型版本，還有幾個比較快、比較便宜、但能力比較差的小型版本。挑哪個等級是一個真正的決定——規劃跟難搞的除錯用重量級的，機械式的改動用輕量級的——harness 會讓你在 [session](./Session.md) 中途切換。

對這個詞嚴格一點，也能讓診斷更準。「這個 model 不擅長這個」是一個很具體的說法——同一個 model 換一個 harness，或者換一個不同的 [context](./Context.md)，常常表現得完全不一樣。怪 model 之前，先檢查它拿到了什麼：大部分讓人失望的輸出，根源都是 context 或 harness，不是 parameters。

_使用情境：_

「規劃這一步要不要把 model 從 Sonnet 換成 Opus？」

「試試看——不過這個任務裡大部分的工作是 harness 在做。如果 [system prompt](./System%20prompt.md) 跟 tool 都不對，換 model 也沒用。」
