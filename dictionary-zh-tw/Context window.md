---
description: model 在每一次 model provider request 裡看到的全部內容——有限、依 model 而定，是 model 唯一能感知的介面。
---

[Model](./Model.md) 在每一次 [model provider request](./Model%20provider%20request.md) 裡看到的全部內容。有限、依 model 而定，而且是 model 感知任何事情的唯一介面。

它是一串連續的 [token](./Token.md)：[system prompt](./System%20prompt.md)、到目前為止的對話、[harness](./Harness.md) 餵回來的每一個 [tool result](./Tool%20result.md)。只要東西在這串序列裡，model 就能用；不在裡面，model 就不知道它存在——不管是你的 codebase、你昨天改過的檔案，還是你三個 session 前下的指示。window 之外的任何東西，都得先透過（通常是）一次 [tool call](./Tool%20call.md) 被帶進來，才能影響任何事。

有限，代表它會被填滿。每一個 [turn](./Turn.md) 都會再往裡面加東西——你的訊息、model 的回覆、tool result——一個夠長的 [session](./Session.md) 遲早會碰到上限，逼出 [compaction](./Compaction.md) 或 [clearing](./Clearing.md)。有限也代表 window 裡的東西彼此在競爭：你多載入一個 token，剩下能用的就少一個，而你其實用不到的內容，一樣會占掉 model 的 [attention](./Attention%20budget.md)。實際的做法是把 window 當成一個預算來對待——載入任務需要的東西，其餘的留在外面。

_避免使用：_「memory」——context window 是運作中的暫存狀態，不會跨 session 保留下來。[Memory](./Memory%20system.md) 是疊在上面的另一個獨立概念。

_使用情境：_

「我可以直接把整個 monorepo 貼進 prompt 嗎？」

「context window 是 200k token——大概只夠放這個 repo 的五分之一。挑任務會碰到的檔案，其餘的留在 tool call 後面。」
