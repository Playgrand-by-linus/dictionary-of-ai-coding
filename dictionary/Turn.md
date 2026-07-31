---
description: 一則使用者訊息，加上 agent 為此做出的所有回應，直到它把控制權交還使用者為止。包含一次以上的 provider request。
---

一則使用者訊息，加上 [agent](./Agent.md) 為此做出的所有回應，直到它把控制權交還給使用者為止。包含一次以上的 [model provider request](./Model%20provider%20request.md)——如果 agent 呼叫了 [tool](./Tool.md)，可能是很多次。一個釐清用的問題會結束這個 turn；你的回覆會開啟下一個。階層關係是 [session](./Session.md) **> Turn > Model provider request**。

turn 值得特別拿出來講的地方在於，它的長度是 agent 決定的，不是你決定的。你交出一則訊息；agent 決定要串多少個 tool call 才交還控制權。一個 turn 可以只是一句話的回答，也可以是二十分鐘的讀檔、編輯、跑測試。這其實是同一件事的兩面：長的 turn 讓 [AFK](./AFK.md) 這種工作方式成立，但長的 turn 也是在無人監督下出錯的地方——等 agent 交還控制權的時候，可能早就偏離你原本的意思很遠了。

turn 也是拿來引導方向的自然單位。turn 裡面發生的一切都跟你無關；turn 跟 turn 之間的空檔才是你能改方向的地方。大多數 [harness](./Harness.md) 會把這件事做得柔和一點：你可以在 turn 進行到一半時打斷，讓 agent 停下來重新引導，或是在它工作時先打一段訊息，等這個 turn 結束就會被讀到。如果你發現自己一再對 turn 跑出來的結果不滿意，通常的解法是要求更小的 turn——先出一份計畫，一次一步——用自主性去換取更頻繁、可以介入引導的空檔。

_使用情境：_

「一個 turn 花了兩分鐘？」

「它在那個 turn 裡面發了十四次 [tool call](./Tool%20call.md)——每一次都是一個獨立的 model provider request。延遲會一直疊加，直到 agent 終於把控制權交還給你。」
