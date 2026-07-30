---
description: 兩個 token 之間的配對——有意義的配對彼此的影響力比不相關的配對大。一個 N 個 token 的 context 大約有 N² 組這種配對。
---

在預測每一個 [token](./Token.md) 的時候，[model](./Model.md) 會把 [context](./Context.md) 裡其他每一個 token 都納入考量——有些考量得多，有些幾乎不考量。兩個 token 之間的配對就是一組 **attention relationship**，而有意義的配對（例如「她」跟「Sarah」，或是一次 `getUser()` 呼叫跟它的 `function getUser` 定義）彼此的影響力，比不相關的配對大。一個有 N 個 token 的 context，大約會有 N² 量級的關係。

這些配對，正是 model 表面上「理解」的來源。當它解析一個代名詞時，是因為「她」跟「Sarah」之間的 attention relationship 很強。當它用對的參數呼叫一個函式時，靠的是呼叫點跟它先前讀過的定義之間的關係在起作用。這一切都不是查表得來的——是每一次 [model provider request](./Model%20provider%20request.md) 裡，針對每一對關係重新算出來的。

N² 這個數字值得好好想一下，因為它成長的速度比直覺快很多：

| Context 大小  | 配對數量 (~N²) |
| ------------- | -------------- |
| 1,000 token   | 約 100 萬      |
| 10,000 token  | 約 1 億        |
| 100,000 token | 約 100 億      |

每一組配對，實際上還會被算不只一次。Model 有多個 attention head——頂尖 model 確切的數量沒有公開，但五十到一百個是合理的猜測——而每個 head 都會各自算一次每一組關係。所以上表裡的每一組配對，都要在每個 head 上重複算一次。這是非常龐大的配對數量。

在任何一次任務裡，真正重要的關係只佔其中一小部分。你的指示跟它所管轄的程式碼之間的配對，就是少數幾組真正算數的關係之一；剩下大部分都是雜訊。而這兩種數量成長的速度不一樣：真正重要的關係大致維持不變，配對總數卻隨著 context 大小呈平方成長。在 1,000 個 token 時，你關心的那組配對是一百萬分之一；到了 100,000 個 token，變成一百億分之一。這就是 [attention budget](./Attention%20budget.md) 背後的算術，而 [attention degradation](./Attention%20degradation.md) 就是當真正重要的關係分到太薄的一份時的感覺。

_使用情境：_

「它一直搞混 diff 裡的兩個 `user` 符號——聽起來我們是在 [dumb zone](./Smart%20zone.md) 裡。」

「對，每個呼叫點跟它宣告之間的 attention relationship 在互相干擾——token 形狀一樣，綁定的東西不一樣。把其中一個改名，配對就會變清楚。」
