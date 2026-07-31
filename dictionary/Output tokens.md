---
description: model 生成回來的 tokens。計費比 input tokens 高，因為產生它們要花更多運算。
---

[Model](./Model.md) 生成回來的 [tokens](./Token.md)。計費比 [input tokens](./Input%20tokens.md) 高——通常大約是五倍——因為產生它們要花更多運算。

model 寫出來的每一樣東西都算數：你讀到的文字、它寫出的程式碼、[tool call](./Tool%20call.md)，還有它回答之前做的任何 extended thinking。最後這一項常讓人意外——推理用的 tokens 算作 output，就算 [harness](./Harness.md) 通常不會把它們顯示給你看，把 [effort](./Effort.md) 調高也會花掉更多這種 tokens。

Output tokens 也決定了 [session](./Session.md) 的節奏。model 讀 input 讀得很快，但生成 output 是一次一個 token，所以當一個 [turn](./Turn.md) 感覺很慢的時候，幾乎都是 output 正在被寫出來，不是 input 正在被讀。等很久，通常代表接下來會是一個很長的答案。

_使用情境：_

「這次重構的 session 一直在燒 credit，明明 input 很小。」

「Agent 在整檔重寫，不是在打補丁。Output tokens 大概是 input 費率的五倍——讓它改成輸出 diff，帳單就會降下來。」
