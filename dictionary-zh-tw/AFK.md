---
description: 使用者啟動一個 session 後放著讓 agent 無人看管地跑下去的工作模式（away from keyboard 的縮寫）。
aliases:
  - away from keyboard
  - 離開鍵盤
---

Away from keyboard 的縮寫。使用者啟動一個 [session](./Session.md) 後，放著讓 [agent](./Agent.md) 無人看管地跑下去的工作模式。這是 [AI](./AI.md) coding 的產出倍增器——你睡覺、吃飯、或忙別的事的時候，可以同時跑好幾個 AFK session。通常需要搭配寬鬆的 [permission mode](./Permission%20mode.md) 加上 [sandbox](./Sandbox.md)，才不會出事。

你不在場的時候，agent 處理模糊地帶的方式不一樣。你盯著螢幕時，一個含糊的決定會浮現成一個問題，讓你來回答；你一離開，agent 就自己選一個預設值繼續做下去，後面每一個決定都疊在這個猜測之上。典型的翻車情況是：回來一看，好幾個小時的工作都做完了，看起來信心十足、前後一致，但整個方向是在最初十分鐘的一個錯誤判斷上蓋出來的。這不是做得潦草——是做得很有條理，只是條理用錯了地方。

既然跑的過程中沒辦法插手，就把輸入放到跑之前跟跑之後。跑之前：先把模糊地帶談清楚——一場 [grilling](./Grilling.md)，一份寫好的 [spec](./Spec.md)——讓 agent 需要自己填的空越少越好。跑的時候：[automated check](./Automated%20check.md) 跟 [automated review](./Automated%20review.md) 代替你原本要花的注意力，機器抓得到的問題就讓機器先擋下來。跑完之後：結果要停在可以被審查的狀態——是一份 PR，不是已經合併的變更。AFK 並沒有拿掉 [human review](./Human%20review.md)，只是把它整個延到最後，所以最後送到你手上的東西，必須真的值得你花時間看。這也是為什麼 [AX](./AX.md) 在 AFK 情境下特別重要——沒有人盯著，環境是 agent 唯一能依靠的支援。

_避免使用：_「background agent」——這個說法把焦點放在機器身上（「在背景執行」），而不是人的行為模式（「使用者已經離開」）。AFK 點出真正重要的事實：使用者沒有在看。

_使用情境：_

「這次我用 AFK 跑——三個 sandbox 裡的 agent 同時處理這次重構，早上再來看 PR。」

「要 [bypass permissions](./Agent%20mode.md) 嗎？」

「好，唯讀 [filesystem](./Filesystem.md)，不接網路。」
