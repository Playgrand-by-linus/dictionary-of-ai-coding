---
description: 一個或多個人在 session 期間跟 agent 一起工作的模式——即時審閱、導正方向、或協作。
aliases:
  - HITL
  - Human-in-the-loop (HITL)
---

一個或多個人在 [session](./Session.md) 期間跟 [agent](./Agent.md) 一起工作的模式——即時審閱、導正方向、或協作。人是在場、投入的，不只是為個別動作把關而已。

對照的是 [AFK](./AFK.md) 的做法，agent 無人看管地跑，你事後再評斷結果。Human-in-the-loop 的意思是在問題還便宜的時候就抓到它：你看到 agent 抓錯檔案、看錯需求、或走進死路，你用一句話就把它導正——而不是等到二十分鐘後才發現，一堆信心十足的工作全部疊在那個錯誤判斷上。Agent 不太會自己察覺方向偏了；沒人管的時候，它們傾向硬著頭皮往下做，而不是停下來問。

哪一種模式適合，要看工作內容。規格清楚、風險低、容易驗證的任務適合 AFK。模糊不清、不可逆、或者你很難審閱完成結果的任務——schema migration、棘手的設計決定、任何碰到 production 的事——適合留在 loop 裡。判斷的重點基本上是：走錯一步的代價有多高，你多晚才會發現。

有些工作天生就得留在 loop 裡，因為你的反應本身就是輸入。[Grilling](./Grilling.md) 一定要有你在場回答問題才成立；[prototyping](./Prototyping.md) 一定要有你在場對產出物做反應才成立。

留在 loop 裡要花你的注意力，而注意力是稀缺資源。用 agent 用得更好的一部分，就是把更多工作安全地移出 loop——靠計畫、[automated check](./Automated%20check.md)，還有最後的 [human review](./Human%20review.md)，取代全程盯著。

_使用情境：_

「這個放著 AFK 跑一整晚？」

「不要，這是 schema migration——留在 human-in-the-loop 裡跑。我要看每一步，如果它挑錯欄位來 backfill 我要能馬上導正。」
