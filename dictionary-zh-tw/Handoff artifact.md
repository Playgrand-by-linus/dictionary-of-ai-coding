---
description: 作為 handoff 傳遞機制的文件——由一個 session 寫下，給另一個 session 讀取。
---

作為 [handoff](./Handoff.md) 傳遞機制的一份文件——由一個 [session](./Session.md) 寫進 [environment](./Environment.md)，給另一個 session 讀取。[Spec](./Spec.md)、[ticket](./Ticket.md)、還有計畫文件，都是 handoff artifact。

寫這種文件的理由是：[model](./Model.md) 是 [stateless](./Stateless.md) 的，所以一個 session 裡的東西，在被 [clearing](./Clearing.md) 之後不會留下來。決定、限制條件、做到一半的計畫——全部隨著裝著它們的 [context](./Context.md) 一起消失。Environment 則會持續存在。把重要的狀態寫進一個檔案，就是把它搬到下一個 session 能讀回來的地方。

這份 artifact 是一種 [secondary source](./Secondary%20source.md)——是對這個 session 工作內容的一份記述，不是工作本身。這正是它能小到拿去簡報一個全新 session 的原因，也是它可能誤導新 session 的原因：它記錄的是寫下它的那個 session 所相信的東西，任何被漏掉或搞錯的地方，讀的人根本看不出來。碰到重要的說法，下一個 session 應該去對照 [primary source](./Primary%20source.md)——程式碼、測試——來驗證它，而不是直接照單全收。

一份寫得好的 artifact，是設想給一個完全沒有 context 的 session 讀的。要用具體的檔案路徑，而不是「我們討論過的那個檔案」。要寫清楚決定了什麼、為什麼這樣決定，讓下一個 session 不用重新吵一遍。要寫清楚做完了什麼、還剩下什麼。跟正在寫的那個 session 講清楚這份文件是要給誰看的，會有幫助：「幫一個完全不知道這件事的全新 session 寫一份 handoff 文件」。

另一種傳遞機制是 [compaction](./Compaction.md)，它是在記憶體裡做摘要。相較之下，artifact 有兩個優勢：它放在硬碟上，你可以在任何東西依賴它之前先讀過、改正；而且它可以重複使用——同一份 spec 可以拿去簡報五個平行的 session。

_使用情境：_

「這件事要怎麼拆給負責規劃的 agent 跟負責實作的 agent？」

「讓做規劃的那個寫一份 handoff artifact——檔案路徑、決定、限制條件。負責實作的那個 session 一開始就用一個指向這份 artifact 的 pointer 開場，把它當簡報來工作。」
