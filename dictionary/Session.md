---
description: 跟 agent 互動的一次有邊界的過程。從空的開始累積，在被清除、關閉、或 compact 成新 session 時結束。
---

跟 [agent](./Agent.md) 互動的一次有邊界的過程。從空的開始，累積訊息、[tool result](./Tool%20result.md)、跟讀過的檔案，在被 [cleared](./Clearing.md)、關閉、或 [compact](./Compaction.md) 成一個新 session 的時候結束。Session 就是把 [context window](./Context%20window.md) 填滿的東西：如果 context window 是那個箱子，session 就是慢慢把箱子填滿的東西。大到一個 context window 裝不下的工作，就得拆到好幾個 session 裡做。

Session 的訊息歷史，就是 agent 的工作記憶。[Model](./Model.md) 是 [stateless](./Stateless.md) 的，所以它看起來記得的每一件事——你要求了什麼、測試結果是什麼、它三個 turn 前做了什麼決定——全都在這份訊息歷史裡，隨著每一次 [model provider request](./Model%20provider%20request.md) 一起重新送出去。不在 session 裡的東西，對 agent 來說就是不存在。

這份記憶會隨著 session 結束而消失。一個新 session 從零開始：昨天 session 結束時對你的 codebase 瞭若指掌的 agent，今天早上什麼都不記得。留下來的是 [filesystem](./Filesystem.md)——一個 session 裡寫的檔案，下一個 session 讀得到，這就是 [handoff](./Handoff.md)、[memory system](./Memory%20system.md)、跟 [AGENTS.md](./AGENTS.md.md) 賴以運作的基礎。

Session 在哪裡結束，是你決定的。Session 裡的每一件事都會影響之後每一個 [turn](./Turn.md)，所以在同一個 session 裡做不相關的任務，會留下殘留物，染色到後面的答案。一個 session 只做一件任務，能讓 context 保持相關；一件任務做完，就是清掉的好時機。

_使用情境：_

「一個 session 能撐多久才會開始垮掉？」

「看工作內容——專注的重構撐得比開放式研究久。Session 一旦膨脹了，就 handoff 或 compact，不要硬撐下去。」
