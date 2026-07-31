---
description: 讓 model 的 parameters 定型的過程，做法是讓它接觸大量文字，並不斷調整以改善 next-token prediction。
---

讓 [model](./Model.md) 的 [parameters](./Parameters.md) 定型的過程，做法是讓它接觸大量文字，並調整 parameters 以改善 [next-token prediction](./Next-token%20prediction.md)。這是 [model provider](./Model%20provider.md) 執行的一次性、成本高昂的過程。涵蓋 pre-training（主要那次大規模跑法）跟 post-training（後續的調校，像是 instruction-following 跟安全性）；這兩者的區別在這本詞典的層次上不重要。

機制是大規模的重複：給 model 看一段文字，讓它預測下一個 [token](./Token.md)，把 parameters 往實際的下一個 token 那個方向推一點，然後在好幾兆個 token 上重複這個過程。沒有任何東西是以事實或規則的形式存起來的——model「知道」的一切，都是它在變得更擅長預測的過程中產生的副作用，壓縮進 parameters 裡變成 [parametric knowledge](./Parametric%20knowledge.md)。

有兩個後果在日常使用上很重要。training 在某個時間點就結束了，所以 model 有一個 [knowledge cutoff](./Knowledge%20cutoff.md)——它沒看過你上個月才升級的那個函式庫版本。而且 training 不是你能做的事：當 model 不知道你的 codebase、你的慣例、你內部的 API 時，解法從來都不是「教會 model」——而是把那些材料放進 [context](./Context.md)，這是你唯一能控制的輸入。

_使用情境：_

「我們能讓它知道我們內部的 API 嗎？」

「不能靠 training——那是 model provider 要花好幾個月做的事。把 API 文件載入 context 裡，那才是你真正能動的槓桿。」
