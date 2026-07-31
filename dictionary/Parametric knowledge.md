---
description: model 從 training 學到、存在 parameters 裡的知識。在 training 時就凍結了，是 contextual knowledge 的對應概念。
---

[Model](./Model.md) 從 [training](./Training.md) 學到、存在它 [parameters](./Parameters.md) 裡的「知識」。在 training 時就凍結了——model 沒辦法看到、也沒辦法更新自己的 parameters。細節在壓縮的過程中流失：幾十億個事實被塞進固定數量的 parameters，罕見的那些會被磨糊。這是它在常見主題上流暢自如的來源，也是它在冷門主題上瞎編的來源。是 [contextual knowledge](./Contextual%20knowledge.md) 的對應概念。

Parametric knowledge 不是用事實的方式存起來的。Training 從來沒有給 model 一個可以查詢的資料庫；它只是不斷調整 parameters，直到 model 能把文字預測得準，而一個能把某個主題的文字預測得準的 model，表現起來就像它懂這個主題一樣。這份知識有多可靠，跟這個東西在 training data 裡出現過幾次成正比：出現過幾百萬次的主題會被準確重現，只出現過寥寥幾次的主題，model 就會根據類似主題的樣子去猜。對 model 來說，重現跟用猜的是同一個過程，所以它自己也分不出來現在是在做哪一種。編出來的答案，講起來跟正確答案一樣流暢。[Hallucination](./Hallucination.md) 就是 model 猜錯的時候。

Parametric knowledge 也會過時。Parameters 在 [knowledge cutoff](./Knowledge%20cutoff.md) 之後就不再變動，所以那之後才發布或改名的函式庫，在它裡面根本不存在，改版過的 API 也還是被記成舊的樣子。

這兩種缺口——太冷門跟太新——的解法是一樣的：這些知識沒辦法被加進 parameters 裡，所以只能改用 contextual knowledge 的方式補進去。

_使用情境：_

「它寫的 React 完美無瑕，卻在我們內部的 SDK 上發明了一堆不存在的方法。」

「React 在 parametric knowledge 裡很密集——幾百萬筆 training 範例。你們的 SDK 沒有這種密度，model 就會填出看起來合理的形狀。把 SDK 文件載進 [context](./Context.md) 裡。」
