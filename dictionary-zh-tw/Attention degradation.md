---
description: 隨著 session 變大，每個 token 的 attention budget 要分給更多競爭者；有意義的關係上的訊號就變薄。
---

隨著 [session](./Session.md) 變大，每個 [token](./Token.md) 的 [attention budget](./Attention%20budget.md) 要分給更多競爭者。任何一組[有意義的關係](./Attention%20relationship.md)上的訊號都會變薄；跟任務無關的 [context](./Context.md) 帶來的雜訊則會擠進來。同一個 [model](./Model.md)、同一組 [parameters](./Parameters.md)——只是同一盤菜要餵更多張嘴。這就是 smart zone / dumb [zone effect](./Smart%20zone.md) 的成因。

它表現出來的樣子，是 model 在 session 進行到一半開始變差：本來遵守了一小時的限制開始鬆動，它重複問已經被告知過的事，寫出來的程式碼無視了它早先讀過的檔案。Model 本身沒有任何改變——唯一變化的變數，是它現在要處理的 context 有多少。

這個過程是漸進的，這也是為什麼在 session 裡面很難察覺。沒有錯誤訊息，也沒有明確的門檻；每個 [turn](./Turn.md) 只比前一個稍微差一點點，等到失誤變得明顯的時候，你已經在 dumb zone 待了一段時間了。

要恢復，靠的是移除 context，而不是加更多進去。把被忽略的指示重貼一次，只是在同一個擁擠的 context window 裡多加一個競爭者，效果也只是短暫的。真正有用的做法是：[clear](./Clearing.md) 掉之後只重新載入任務需要的東西，或是做 [compact](./Compaction.md)，或是 [handoff](./Handoff.md) 到一個全新的 session。把指示遵循度下滑當成 context 長度的訊號，而不是 model 本身的問題。

_使用情境：_

「它已經深陷 dumb zone 了——在編造型別檔案裡沒有的 generics。」

「Attention degradation。型別定義還在 context 裡，但它上面的訊號已經被我們之後加進去的一切埋住了。清掉重新載入吧。」
