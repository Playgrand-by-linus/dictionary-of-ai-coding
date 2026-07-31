---
description: 在 environment 裡跑的一種確定性驗證——測試、型別檢查、lint、build、pre-commit hook。只有過或不過，沒有判斷。
---

在 [environment](./Environment.md) 裡跑的一種確定性驗證——測試、型別檢查、lint、build、pre-commit hook。只有過或不過，沒有判斷。這是 [agent](./Agent.md) 不需要找任何人就能自己修正的訊號。一個會偶爾失敗的測試（flaky test）是壞掉的 check，不是「不算 check」；automated check 就是設計成確定性的。

自我修正靠的是一個迴圈。Agent 做出改動，把 check 當成一次 [tool call](./Tool%20call.md) 跑一次，失敗的輸出就會進到牠的 [context window](./Context%20window.md) 裡——一個帶著檔案跟行號的型別錯誤、一個帶著預期值跟實際值的失敗斷言。這樣就足以讓 agent 修好問題再跑一次 check，一輪一輪來回，直到通過為止，全程不需要人介入。確定性正是讓這個迴圈值得信任的原因：同樣的程式碼永遠得到同樣的判定，所以「過」這件事才有意義。一個不穩定的 check 會毒害這個迴圈——agent 會「修好」原本沒問題的程式碼，或是在一次真正的失敗上重試過關。

這就是為什麼好的 check 是一個 codebase 的 [AX](./AX.md) 很重要的一部分。在一個有嚴格型別、快速測試套件跟 linter 的 repo 裡，agent 在你看到之前就能抓到大部分自己的錯誤；在一個什麼都沒有的 repo 裡，agent 產出什麼就送出什麼。這個差別在 [AFK](./AFK.md) 跑的時候最要緊，因為 check 是那段期間唯一在進行的驗證。但一個 check 只能抓到它斷言的東西——check 全部通過，代表被斷言的性質成立，不代表程式碼就是對的。那些需要判斷力才能發現的落差，就是 [automated review](./Automated%20review.md) 跟 [human review](./Human%20review.md) 要處理的事。

_避免使用：_「feedback loop」／「backpressure」——這兩個說法都把 check 跟 review 混在一起。_避免使用：_「test」——測試是 automated check 的一種，但不是所有 automated check 都是測試。

_使用情境：_

「Agent 在 AFK 跑的時候一直送出壞掉的程式碼。」

「[Sandbox](./Sandbox.md) 裡接了哪些 automated check？」

「只有單元測試。」

「加上型別檢查跟 lint——這樣它在 PR 送出之前就能先自己修正。」
