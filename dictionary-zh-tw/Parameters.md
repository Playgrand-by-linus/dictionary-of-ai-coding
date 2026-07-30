---
description: model 內部的數字——常常是幾十億個——在 training 過程中調整出來。model 知道的一切都存在裡面，也叫 weights。
---

[Model](./Model.md) 內部的數字——常常是幾十億個——在 [training](./Training.md) 過程中調整出來。model「知道」的一切都存在這些數字裡。Training 設定它們的值；[inference](./Inference.md) 則原封不動地使用它們。也叫 _weights_。

從機制上看，parameters 就是把 input 轉成 output 的東西。[Next-token prediction](./Next-token%20prediction.md) 是一次巨大的計算：[context window](./Context%20window.md) 裡的 [tokens](./Token.md) 進去，跟 parameters 相乘運算，出來的就是下一個 token 的預測。model 裡面沒有事實資料庫，也沒有程式碼查表——就只有這些數字，被排列成讓這個計算傾向於產生有用的輸出。model 能從 training 裡背出來的事實，例如某個標準函式庫的 API，就是 [parametric knowledge](./Parametric%20knowledge.md)：存在 parameters 裡，不是從別的地方查來的。

值得記住的重點是：parameters 在 training 結束後就凍結了。你在一個 [session](./Session.md) 裡做的任何事都不會改變它們——你做的修正、你給它看的 codebase、它學到的教訓，都不會。每一個 session 跑的都是同一組數字。這就是為什麼 model 是 [stateless](./Stateless.md)、為什麼它內建的知識停在 [knowledge cutoff](./Knowledge%20cutoff.md)、也是為什麼跟專案有關的東西都得靠 [context](./Context.md) 送進去。改變 parameters 的唯一辦法是再做一次 training——而那實際上會產生一個不同的 model。

_使用情境：_

「可以拿我們的 codebase 對它做 fine-tune 嗎？」

「那樣會更新 parameters——之後就是不同的 model 了。對單一專案來說，把 codebase 當 context 載入，幾乎永遠比重新 training 便宜。」
