---
description: 控制 model 回答前要做多少推理的旋鈕。effort 開得越高，花的 output token 越多，難題答對的機會也越高。
aliases:
  - Reasoning effort
  - Thinking effort
---

Effort 是一個旋鈕，控制 [model](./Model.md) 回答前要做多少推理。它是逐次 [model provider request](./Model%20provider%20request.md) 設定的，控制 model 在開始寫出你看到的回應之前，要想多長。那段思考跟其他一切一樣，是在 [inference](./Inference.md) 時產生的；[harness](./Harness.md) 常常把它藏起來，但那是 model 真的在做的工作。

effort 開得越高，花費越多、跑得越慢。這段推理是以 [token](./Token.md) 的形式產生的，就算你從沒看到它，也是照 [output tokens](./Output%20tokens.md) 計費，而且是一個一個 token 產生出來的——所以把 effort 調高，答案送到你手上前要等更久，帳單也會變多。這是拿更多深思跟速度、成本做交換。

大多數 harness 會把 effort 呈現成一個小小的階梯：

| 等級   | 用途                                         |
| ------ | -------------------------------------------- |
| Low    | 機械式的編輯、查詢、路徑單一且規格明確的變更 |
| Medium | 日常的 coding——一般預設值                    |
| High   | 棘手的 bug、設計決策、多步驟的規劃           |
| Max    | 最困難的問題，答錯的話後續要收拾的成本很高   |

設錯的症狀兩邊都會出現。在一個困難的問題上把 effort 設得太低，得到的會是一個信心十足卻很淺的答案，跳過了這個問題原本需要的推理——讀起來沒問題，錯的方式卻會在後面害你付出代價。為了一個改一行的改名把 effort 設成 max，你就是坐著等一段長長的思考過程，結果產出的東西跟最低設定完全一樣。

讓 effort 對應到任務本身，而不是對應到整個 [session](./Session.md)。真正需要費心推理的那個部分才調高，周圍那些照本宣科的工作就調回來。

_使用情境：_

「這個並行處理的修法它一直搞砸——我已經重講三次了。」

「把 effort 調高。這是個很吃推理的 bug，預設設定下，它在決定要怎麼做之前想得不夠久。」
