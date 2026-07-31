---
description: 一個試圖讓 agent 跨 session 保持 stateful 的系統，做法是寫進 environment，再於 session 開始時重新載入。
---

一個試圖讓 [agent](./Agent.md) 跨 [session](./Session.md) 保持 [stateful](./Stateful.md) 的系統。它在 session 期間把資訊存進 [environment](./Environment.md)，然後在之後的 session 開始時把它重新載入 [context window](./Context%20window.md)，這樣 agent 就能延續下去，不受使用者 [clearing](./Clearing.md) session 的影響。

Memory system 分成兩半。寫入路徑：session 期間，agent 把自己學到的東西——你講過的一個偏好、專案的某個事實——寫成 environment 裡的檔案。讀取路徑：session 開始時，[harness](./Harness.md) 把那些檔案，或者它們的索引，重新載回 context window。很多 harness 都內建自己的 memory system——Claude Code 的 `/memory` 就是一個——但你也可以自己搭一個：一個放筆記的資料夾，加上 [AGENTS.md](./AGENTS.md.md) 裡一句要去讀它的指示。

跟任何常駐載入的內容一樣，這裡也有一樣的取捨。記憶會愈積愈多，所以大部分系統只載入一行的索引，把內容本體留在 [context pointer](./Context%20pointer.md) 後面，而不是整段塞進去。而且記憶是 [secondary source](./Secondary%20source.md)，所以會過時：三月記下來的一個事實，到了六月、專案早就往前走了，卻還是用一樣的信心被載入。Memory system 需要修剪，跟 AGENTS.md 一樣。

_使用情境：_

「我一直要重講一次我用的是 Postgres，不是 MySQL。」

「接上一個 memory system——第一個 [turn](./Turn.md) 就把學到的東西寫進 [filesystem](./Filesystem.md)，session 開始時重新載入。[Model](./Model.md) 本身是 [stateless](./Stateless.md) 的；memory 這層是在假裝有延續性。」
