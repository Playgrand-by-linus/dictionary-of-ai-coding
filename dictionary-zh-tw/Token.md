---
description: model 讀寫的最小單位。大致跟一個詞差不多大，但不完全一樣。context window 大小、成本、延遲都是用 token 計算的。
---

[model](./Model.md) 讀寫的最小單位。大致跟一個詞差不多大，但不完全一樣——常見的詞是一個 token，罕見或很長的詞會被拆成好幾個。[context window](./Context%20window.md) 大小、成本、延遲全都是用 token 計算的。

文字要透過 tokenizer 才會變成 token：一份在 [training](./Training.md) 之前就學好的、有好幾萬個片段的固定詞表，會把任何輸入拆成一串詞表項目。model 從來看不到字元或詞——每一段文字進去之前都會先被轉成 token，而 [next-token prediction](./Next-token%20prediction.md) 出來的時候，也是一次產生一個 token。

概略來說，一個 token 大約是四分之三個英文單字，所以一千個 token 大概是 750 個字。程式碼比較難預測：常見的關鍵字跟慣用寫法會被切得很緊湊，而產生出來的識別字、雜湊值、base64 區塊、壓縮過的輸出，每個「詞」都會被拆成很多 token。規律是：在 tokenizer 訓練材料裡常出現的文字，會得到又短又有效率的編碼；沒出現過的，就會被剁成很多小塊。像 `a3f9c2e1` 這種雜湊值從來沒在任何地方出現過，所以會被拆成一堆 token，而 `function` 是一個 token。這就是為什麼一個看起來很小、卻塞滿不尋常字串的檔案，可以佔掉 context window 出乎意料大的一部分。

token 是其他一切度量的單位。成本是按 token 算的——provider 會分開計費 [input token](./Input%20tokens.md) 跟 [output token](./Output%20tokens.md)。速度是每秒幾個 token，因為輸出是一次生成一個 token。而 context window 是固定數量的 token，所以你檔案的 token 數決定了能塞進去多少。

_避免使用：_「word」——token 的邊界跟詞的邊界對不上，而且真正重要的單位是「每秒幾個 token」跟「每一塊錢幾個 token」。

_使用情境：_

「這個 prompt 會有多大？」

「拿去跑一次 tokenizer——schema 本身很精簡，但 JSON 的 key 很怪，會被拆成比你想像中更多的 token。」
