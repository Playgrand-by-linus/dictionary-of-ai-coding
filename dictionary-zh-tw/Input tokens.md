---
description: harness 在每一次 model provider request 送出的 token。計費比 output token 便宜。
---

[Harness](./Harness.md) 在每一次 [model provider request](./Model%20provider%20request.md) 送出的 [token](./Token.md)——[system prompt](./System%20prompt.md)、對話紀錄、[tool result](./Tool%20result.md)，所有 [model](./Model.md) 在寫東西之前要讀進去的東西。計費比 [output token](./Output%20tokens.md) 便宜，因為處理起來比 output token 便宜。

在做 [AI](./AI.md) coding 的時候，input token 佔你帳單的大部分。Model 是 [stateless](./Stateless.md) 的，所以每一個 [turn](./Turn.md) 都要把整個 [session](./Session.md) 當作 input 重送一次：你的第一則訊息、每一次回覆、每一個 tool result，全部都要重送。第五十個 turn 的 input，包含了前面四十九個 turn。單一一次 model provider request 可能只產生幾百個 output token，卻要重送十萬個累積下來的 input token。

[Prefix cache](./Prefix%20cache.md) 可以降低這個成本：跟前一次 request 完全吻合的歷史紀錄，會用便宜的 [cache token](./Cache%20tokens.md) 計費，而不是全價的 input。如果 input 的成本還是讓你受不了，解法就是縮小要重送的東西——在任務之間 [clearing](./Clearing.md) 或 [compacting](./Compaction.md)。

_使用情境：_

「帳單很高，可是 [agent](./Agent.md) 沒寫多少東西。」

「是 input token 的問題——每個 turn 都要把整個 session 重送一次。沒有 prefix cache 的話，每次 request 都要重新付一次歷史紀錄的錢。」
