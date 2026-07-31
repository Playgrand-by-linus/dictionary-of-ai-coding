---
description: "自信滿滿卻是錯的 model 輸出。分兩種：factuality（捏造事實）跟 faithfulness（偏離已載入的 context）。"
---

[Model](./Model.md) 輸出裡自信滿滿卻是錯的內容。有兩種，成因跟解法都不一樣：

| 種類           | 出了什麼問題                                                                       | 成因                                                                                                                 | 解法                                                           |
| -------------- | ---------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| _Factuality_   | 對這個世界捏造或搞錯了事實——一個不存在的函式、錯誤的 API 簽名、假造的引用          | [Parametric knowledge](./Parametric%20knowledge.md) 有缺口，常常是超過了 [knowledge cutoff](./Knowledge%20cutoff.md) | 載入正確的 [contextual knowledge](./Contextual%20knowledge.md) |
| _Faithfulness_ | 輸出偏離了已經載入的 contextual knowledge、使用者的指示，或是 model 自己先前的推理 | [Attention degradation](./Attention%20degradation.md)；在 [dumb zone](./Smart%20zone.md) 裡會更嚴重                  | [Clear](./Clearing.md) 或 [compact](./Compaction.md)           |

[Next-token prediction](./Next-token%20prediction.md) 不管背後的事實是不是真的存在，都會產生流暢的輸出——model 沒有任何內部訊號告訴自己「這個我不知道」，所以一個捏造出來的方法，會用跟正確答案一模一樣篤定的語氣冒出來。Hallucinate 出來的程式碼，天生就顯得可信：它長得就是那個 API 如果真的存在時該有的樣子，這正是為什麼它能瞞過粗略的審查，只有真的跑起來才會出錯。

你需要先搞清楚眼前是哪一種，因為其中一種的解法，會讓另一種變得更糟。Factuality 代表知識缺漏：解法是加進 context——文件、型別定義、檔案。Faithfulness 代表知識其實在場，只是在爭奪 attention 的競賽裡輸掉了：解法是把 context 減少。把 faithfulness 誤診成 factuality，你就會貼進更多文件，結果 context 變得更大，偏離反而更嚴重。當 agent 出錯時，先確認正確的資訊是不是本來就在 context 裡，再決定自己碰到的是哪一種問題。

*避免使用：*把「hallucination」當成「錯了」的同義詞來用——不指名是哪一種，這個詞就沒有診斷上的意義。

_使用情境：_

「它 hallucinate 出一個 schema 上根本沒有的 `parseAsync` 方法。」

「Factuality 還是 faithfulness？」

「這個方法在我貼的文件裡真的有——它只是在 [turn](./Turn.md) 四十之後就不讀了。」

「那是 faithfulness。Compact 之後重新載入，不用再加文件了。」
