---
description: model 的輸出，指名一個 tool 跟它的參數——就只是結構化文字。harness 得讀懂它才會真的去執行。
---

[Model](./Model.md) 的輸出，指名一個 [tool](./Tool.md) 跟它的參數——就只是結構化文字。它自己什麼都不會做；[harness](./Harness.md) 得讀懂它，才會真的去執行。由 model 在一次 [model provider request](./Model%20provider%20request.md) 裡產生。

一次 tool call 的生命週期：

| 步驟 | 誰      | 發生什麼事                                                            |
| ---- | ------- | --------------------------------------------------------------------- |
| 1    | Model   | 從 [system prompt](./System%20prompt.md) 裡的描述得知有哪些 tool 可用 |
| 2    | Model   | 發出一個 call——tool 名稱加上參數，通常是 JSON——然後停下來             |
| 3    | Harness | 解析這個 call，對照 [permission mode](./Permission%20mode.md) 檢查    |
| 4    | Harness | 允許的話就執行                                                        |
| 5    | Harness | 把結果包成 [tool result](./Tool%20result.md)，放進下一次請求送回去    |

一個 [agent](./Agent.md) 的 [turn](./Turn.md) 通常就是好幾輪這種來回串在一起。

因為這個 call 跟其他所有輸出一樣，是靠 [next-token prediction](./Next-token%20prediction.md) 生出來的，它可能出錯的方式跟任何 model 輸出一樣：一個不存在的路徑、指令根本沒有的參數、看起來合理但其實不對的引數。harness 執行的是寫下來的內容，不是原本想做的事——打錯一個路徑不會優雅地報錯，而是直接改到別的檔案。

_使用情境：_

「它說測試跑過了，但檔案的時間戳記沒變。」

「看一下 transcript——它是真的發出了 tool call，還是只是描述自己跑了測試？call 是 model 產生的，但 harness 沒有真的執行的話，什麼事都沒發生。」
