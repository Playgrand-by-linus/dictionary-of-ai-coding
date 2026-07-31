---
description: "一種發展 design concept 的技巧：agent 用蘇格拉底式的方式，一次一個決定地訪談使用者。"
---

跟 [agent](./Agent.md) 一起發展 [design concept](./Design%20concept.md) 的一種技巧：agent 用蘇格拉底式的方式訪談使用者，一次處理一個決定，每個決定都提出一個建議的答案。這會放慢衝去完成一份計畫的速度——在 concept 穩定下來之前，不寫任何 [handoff artifact](./Handoff%20artifact.md)。

這個技巧存在的原因，是 agent 會悄悄地把空白填起來。只給兩行 prompt 就要求寫一份 [spec](./Spec.md)，agent 不會在你還沒做的決定上停下來——它會挑一個預設值，直接寫進去。結果看起來很完整，而且用猜的部分跟真正做過選擇的部分完全分不出來，所以你會很晚才發現：在審查的時候，或是等做出來的功能用一種你從沒選過的方式處理某個 edge case 的時候。Grilling 把這個順序反過來——不讓 agent 用猜的，而是逼它開口問。

這是一種 [human-in-the-loop](./Human-in-the-loop.md) 技巧：你的回答就是輸入。當一個問題沒辦法用對話回答——你得先看到實際的東西——就換成 [prototyping](./Prototyping.md)。

_使用情境：_

「它直接跳去寫 spec，結果取消邏輯寫錯了。」

「先 grill 它——在它把任何東西寫進文件之前，先讓它問你部分取消、退款、還有時間點的問題。在對話裡解決，比在程式碼裡解決便宜。」
