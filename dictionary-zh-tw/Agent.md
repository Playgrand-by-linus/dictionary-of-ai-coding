---
description: 一個被 harness 接上 tool、system prompt 跟 context window 的 model，跟使用者輪流對話。是動起來的 model。
---

一個 [model](./Model.md) 被 [harness](./Harness.md) 接上 [tool](./Tool.md)、[system prompt](./System%20prompt.md)、[context window](./Context%20window.md)，跟使用者輪流進行 [turn](./Turn.md)。_Claude Code 是一個 agent。Cursor 是一個 agent。Claude.ai 是一個 agent。_ Agent 是你實際在對話的對象——是動起來的 model，被配置成某種用途。

跟這本辭典裡大多數詞不一樣，「agent」指的不是一個機械式的零件。Model 是一個裝著 [parameters](./Parameters.md) 的檔案；harness 是可以直接指到的軟體。Agent 兩者都不是——它是你在對話的那個單位。人會不斷把 [AI](./AI.md) 擬人化，而 agent 就是那個被擬人化的單位：你委派工作的對象、讀你訊息並回答你的東西，也就是「它又把 build 弄壞了」裡的那個「它」。當你說 agent 做了什麼，你的意思是 model 加上 harness 做的，但你是把這個組合當成單一行動者在說話。

這個概念比這一波 AI 還老。軟體 agent——你把一個目標委派給它、由它代表你行動的程式——這個概念存在的時間跟 AI 一樣久。

_避免使用：_「the AI」、「the bot」——太模糊，分不清你指的是那組 parameters 還是被接上 harness 之後的東西。

_使用情境：_

「這次遷移你用哪個 agent？」

「本機用 Claude Code，UI 的部分用 Cursor——底層是同一個 model，只是 harness 不一樣。」
