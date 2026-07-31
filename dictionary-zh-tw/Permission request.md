---
description: harness 在執行一個沒有預先核准的 tool call 之前，秀給使用者看的畫面。是讓人類進到 loop 裡的機制。
---

[Harness](./Harness.md) 在執行一個沒有預先核准的 [tool call](./Tool%20call.md) 之前，秀給使用者看的畫面。[Model](./Model.md) 產生一個 tool call；harness 不會馬上執行，而是先暫停下來詢問。核准就執行；拒絕的話，harness 會把拒絕的結果當作 [tool result](./Tool%20result.md) 回報給 model。這就是 harness 讓人類進到 [loop](./Human-in-the-loop.md) 裡、去處理有風險或敏感動作的機制。

一次 permission request 的生命週期：

| 步驟 | 誰      | 發生什麼事                                                              |
| ---- | ------- | ----------------------------------------------------------------------- |
| 1    | Model   | 產生一個 tool call                                                      |
| 2    | Harness | 對照 [permission mode](./Permission%20mode.md) 跟任何已儲存的核准來檢查 |
| 3    | Harness | 已預先核准的話就馬上執行；否則暫停下來、把請求秀出來                    |
| 4    | 使用者  | 核准一次、核准整個 [session](./Session.md) 剩下的時間、或拒絕           |
| 5    | Harness | 執行這次呼叫，或是把拒絕當作 tool result 送回去                         |

拒絕一個請求，是在引導 agent 的方向。model 會像對待任何其他 tool result 一樣讀懂這個拒絕，並做出反應——它會試別的做法，或是問你比較想要怎麼做。大部分 harness 都能讓你在拒絕的時候附上一句話，這就讓這次請求變成一個可以引導方向的時機點：「不要那樣，改用 migration script」剛好會在 model 決定下一步要做什麼的當下發生作用。

代價是每一次請求都是一次同步等待你回應。[Agent](./Agent.md) 會卡在那裡，直到你回答為止，你在盯著的時候這沒問題，但你不在的時候就是個麻煩——一個一直觸發請求的 agent，沒辦法丟著讓它 [AFK](./AFK.md) 跑。Permission mode 就是那個調整鈕：哪些呼叫可以自由執行、哪些要先問，最好還搭配 [sandbox](./Sandbox.md)，讓放寬「自由執行」的範圍變得安全。

_使用情境：_

「它被一個 permission request 卡了十分鐘——我剛好在開會。」

「這就是 human-in-the-loop 的代價。把安全的 [tools](./Tool.md) 預先核准，讓請求只在真的有風險的呼叫上跳出來。」
