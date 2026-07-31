---
description: 界定一個 session 工作範圍的 handoff artifact。可以獨立存在，也可以掛在 spec 底下。能封鎖或被同層級的 ticket 封鎖。
---

界定一個 [session](./Session.md) 工作範圍的 [handoff artifact](./Handoff%20artifact.md)。可以獨立存在，也可以掛在 [spec](./Spec.md) 底下當作其中一個子項目。ticket 之間可以互相封鎖，所以工作的順序是從它們的依賴圖長出來的，而不是一份線性的計畫。

定義性的限制是大小：一個 session。一個 ticket 應該要能在 session 漂出 [smart zone](./Smart%20zone.md) 之前做完——而且這個限制是可以檢驗的。如果你的 ticket 上跑的 session 常常在工作做完之前就退化，代表 ticket 太大了，該拆開。如果每個 session 大部分的 [context](./Context.md) 都花在準備上，才做五分鐘的正事，代表太小了，該合併。

一份好的 ticket，是寫給一個完全沒有其他 context 的讀者看的。目標、驗收標準，以及指向相關檔案跟決定的 [context pointer](./Context%20pointer.md)——要多到讓 session 可以直接開始做事，不用重新推導出上一個 session 已經知道的東西。

依賴圖也是解鎖平行處理的關鍵。互相獨立的 ticket——也就是圖上的葉節點——可以各自在自己的 session 裡同時執行。這是同時跑多個 agent 的有效做法。

_使用情境：_

「migration 這份 spec 我該從哪裡開始？」

「看 ticket 的依賴圖——schema 變更會封鎖 backfill，backfill 會封鎖 API 切換。挑一個葉節點，跑一個 session 處理它。」
