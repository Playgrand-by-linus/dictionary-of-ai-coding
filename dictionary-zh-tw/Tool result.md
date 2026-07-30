---
description: harness 執行完一次 tool call 之後回傳的東西——檔案內容、輸出，或錯誤訊息。agent 對 environment 唯一的視角。
---

[harness](./Harness.md) 執行完一次 [tool call](./Tool%20call.md) 之後回傳的東西——檔案內容、指令輸出、錯誤訊息。[agent](./Agent.md) 對 [environment](./Environment.md) 唯一的視角。會在*下一次* [model provider request](./Model%20provider%20request.md) 裡送回給 [model](./Model.md)，由 model 決定要拿它怎麼辦。tool call 跟 tool result 是同一次交換的兩端，都發生在同一個 [turn](./Turn.md) 裡。

tool result 的生命週期：

| 步驟 | 誰      | 發生什麼事                                                     |
| ---- | ------- | -------------------------------------------------------------- |
| 1    | Harness | 執行這個 tool call——跑指令、讀檔案                             |
| 2    | Harness | 把結果記下來：輸出、內容，或錯誤                               |
| 3    | Harness | 把它當成一則訊息附加進 [context](./Context.md)                 |
| 4    | Harness | 在下一次 model provider request 裡把整個 context 送給 provider |
| 5    | Model   | 讀這個結果，並決定：再發一次 tool call，還是給出最終答案       |

這個結果會在 context 裡留到 [session](./Session.md) 結束。tool result 通常佔掉 coding session context 裡的大部分：每一次讀檔、每一次跑測試、每一次搜尋都是完整落地，而且早就沒用了還繼續佔著 [token](./Token.md)。幾個大的結果——一份很囉唆的測試紀錄、一個整份讀進來的產生檔案——就能比對話本身更快把 session 推向 [context window](./Context%20window.md) 的邊緣。

因為 model 看到的就只有這個結果，它沒有辦法回頭去檢查 environment 本身。如果輸出被截斷了、指令悄悄地失敗了，或是 harness 回傳的是錯誤訊息而不是內容，model 就是拿它被給的東西去推理。當 agent 對你系統的理解看起來不對，該去查的就是 tool result：逐字稿裡某個地方，有一個結果講的東西跟你知道的事實不一樣。

_使用情境：_

「它在推理這個檔案的時候，好像把它當成是空的。」

「tool result 回來的是權限被拒，不是檔案內容。model 只看到那串錯誤訊息——它沒有別的辦法看到這個檔案。」
