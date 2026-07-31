---
description: harness 附加在每一次 model provider request 前面的指示——agent 的長期任務說明。在一個 session 裡通常維持不變。
---

[harness](./Harness.md) 附加在每一次 [model provider request](./Model%20provider%20request.md) 前面的指示——[agent](./Agent.md) 的長期任務說明：它是誰、該怎麼表現、能呼叫哪些 [tool](./Tool.md)、該遵守什麼慣例。在一個 [session](./Session.md) 裡通常維持不變。

system prompt 是 harness 的廠商寫的，不是你寫的，而且在 coding harness 裡通常很大——常常是好幾萬個 [token](./Token.md) 的行為規則、tool 描述、邊角案例處理，而且每個 [turn](./Turn.md) 都要當作 [input token](./Input%20tokens.md) 付費。你自己的長期指示會跟著一起搭便車：像 [AGENTS.md](./AGENTS.md.md) 這樣的檔案，會在 session 開始時載入到 system prompt 旁邊，所以 [model](./Model.md) 是先把廠商的說明跟你的一起讀完，才看到你的訊息。

因為它在每次請求裡都一模一樣，所以構成了 [prefix cache](./Prefix%20cache.md) 的開頭——這也是為什麼 harness 會讓它在整個 session 裡固定不變，而不是邊跑邊改。

model 被訓練成優先聽從 system prompt，而不是使用者訊息。所以當一個 agent 堅持某個你從沒要求過的慣例，或是用一種你怎麼樣都改不掉的格式輸出，通常是它在服從 system prompt——而你的訊息在這場拉鋸裡輸了。有些 harness 是可以自訂的：它們讓你完整看到 system prompt，你可以讀到 agent 實際上被告知了什麼，並加以修改。

_使用情境：_

「兩個 harness，同一個 model，同樣的 prompt，行為完全不一樣。」

「system prompt 不一樣。一個調校成寫精簡的程式碼修改，另一個調校成會解釋——差異在你的訊息送到之前就已經存在了。」
