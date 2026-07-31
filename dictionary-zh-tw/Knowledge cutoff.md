---
description: model 沒有 parametric knowledge 的日期分界。分界之後的 library 跟 API，不載入文件的話就是捏造陷阱。
---

[Model](./Model.md) 沒有 [parametric knowledge](./Parametric%20knowledge.md) 的那個日期分界。分界之後的 library、API、事件，除非它們的文件被當成 [contextual knowledge](./Contextual%20knowledge.md) 載入，否則都是捏造陷阱。每一次 model 發布，都帶著自己的 knowledge cutoff。

這個分界會存在，是因為 model 生產的方式：[training](./Training.md) 把某個時間點的文字快照烤進 model 的 [parameters](./Parameters.md) 裡，之後 parameters 就凍結了。Model 不知道自己的知識有一個邊界——問到分界之後的事，它不會拒答，而是從它知道的最接近的東西去外推。這就是這個陷阱安靜的地方：照著某個 library 的舊版本寫出來的程式碼，看起來很合理，通常也編譯得過，只在改掉的那些部分才會出錯。

修法一直都一樣：把最新的資訊放進 [context](./Context.md) 裡。載入 changelog、指向已安裝版本的 type definition，或者讓 agent 去網路上讀文件。只要在 context 裡有東西，就贏過 parameters 裡什麼都沒有。

_使用情境：_

「它一直寫 v3 SDK 的語法——我們用的是 v5。」

「v5 是在 knowledge cutoff 之後才發布的。把 v5 的 changelog 當 contextual knowledge 載入，不然它會一直照著舊的 parametric 版本捏造。」
