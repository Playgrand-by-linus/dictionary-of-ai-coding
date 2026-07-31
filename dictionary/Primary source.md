---
description: 原始的東西本身——程式碼、逐字紀錄、原始資料。完整且具權威性，但載入 context 的成本很高。
---

一個真相來源的原始形式——程式碼本身、對話的逐字紀錄、原始的 log、實際的 API 回應。不是對這件事的描述；是這件事本身。是 [secondary source](./Secondary%20source.md) 的對應概念。

如果你想知道你的 codebase 到底在做什麼，程式碼就是 primary source。文件、架構圖、README，全都是對它的描述——寫的當下是準的，之後就各自照自己的步調過時。當一個 [agent](./Agent.md) 很有自信地講出一句關於你專案的錯誤陳述時，該問的問題是它參考的是哪個來源：讀了文件的 agent，會繼承文件的過時；讀了程式碼的 agent，讀到的是當下的事實。

讓 primary source 沒辦法變成預設選項的，是它的成本。把它整個載進 [context window](./Context%20window.md) 很貴——完整的檔案、完整的逐字紀錄，每一個 [token](./Token.md) 都被算成 [input](./Input%20tokens.md)、都在跟別的東西搶 [attention budget](./Attention%20budget.md)。付出這個成本換來的是完整性：沒有人事先照著自己對「什麼重要」的判斷去篩選過。上個月寫的摘要，不可能包含今天才發現重要的那個細節；primary source 卻還留著。

當精確度很重要的時候，就去找 primary source——確切的函式簽章、實際發生的錯誤、真正丟出例外的那一行。管理 [context](./Context.md) 有很大一部分，就是在決定什麼時候值得付這個成本去讀 primary source，什麼時候 secondary source 就夠用了。

_使用情境：_

「Agent 說 retry 邏輯是指數退避，但我看著它一直狂打那個 endpoint。」

「它是從設計文件裡讀到的。讓它去看實際的 retry 模組——行為攸關的時候，就用 primary source。」
