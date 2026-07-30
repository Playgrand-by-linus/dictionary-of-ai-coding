---
description: "Developer experience（開發者體驗）：codebase 跟工具鏈讓人類做好工作有多容易——文件、回饋速度、錯誤訊息。"
aliases:
  - Developer experience
  - 開發者體驗
---

Developer experience（開發者體驗）——codebase 跟它的工具鏈，讓人類做好工作有多容易。好的 DX 是快速的回饋、清楚的錯誤訊息、真的能回答你當下問題的文件，還有一次就裝得起來的設定。這個詞遠早於 AI coding 就存在；收錄在這本辭典裡，主要是為了跟 [AX](./AX.md) 做對比。

DX 說的就是人類跟 codebase 之間的互動，沒有更多了。這兩種對象最大的差別，在於人類是 [stateful](./Stateful.md)，而 [agent](./Agent.md) 是 [stateless](./Stateless.md)。人類把 codebase 學一次，之後每一天都帶著這份知識繼續走，這就是為什麼糟糕的 DX 還撐得下去：CI 跑得慢，就把 push 批次起來繞過去；文件缺漏，就在 Slack 問一次繞過去；結構讓人搞不清楚，就靠自己記住東西放在哪裡繞過去。這些變通做法會累積下來，最後一個團隊在一個處處跟他們作對的 codebase 裡，還是能維持生產力。

Agent 面對的是同一個 codebase，卻沒有這些累積。跨 [session](./Session.md) 是 stateless 的，agent 每一次都得從零重新學這個 codebase——快的測試套件、清楚的錯誤訊息，它一樣受惠，但它昨天弄懂的東西，除非寫進了 [environment](./Environment.md)，否則就消失了，而 agent 也只能透過 [tool result](./Tool%20result.md) 去感知這個 environment。這就是 AX 這個詞指出的落差：當開發者換成 agent 時，DX 裡還能留下來的那部分，再加上人類本來就不會有的顧慮，像是要保持 [context window](./Context%20window.md) 的空間。

有重疊的部分，代表投資 DX 常常會順帶改善 AX——嚴格的型別、快速的測試、可預期的結構，兩邊都受用。但也有分歧的部分，代表不是每次都這樣：一份寫得很漂亮的 onboarding 文件，能讓人類受用一整個星期，對 agent 卻毫無幫助，除非它能從 [AGENTS.md](./AGENTS.md.md) 連得到。

_使用情境：_

「我們的 DX 沒問題——新人一個星期就能上手。」

「上手，是因為那個星期有人坐在旁邊帶。agent 沒有這個星期可以用；AX 要另外檢查。」
