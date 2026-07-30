---
description: "Agent experience：environment 為了讓 agent 做好工作而準備得多充分——checks、架構，以及空出來的 context。"
aliases:
  - Agent experience
---

Agent experience——[environment](./Environment.md) 為了讓 [agent](./Agent.md) 在一個 codebase 裡做好工作，準備得有多充分。這是對應 [DX](./DX.md) 的 agent 版本。當同一個 agent 在一個 repo 表現很好、在另一個 repo 表現很糟——用的是同一個 [model](./Model.md)、同一個 [harness](./Harness.md)——差別通常就在 AX。直覺上會怪 model 或改寫 prompt；但真正該修的地方通常是那個 repo 本身。

好的 AX 有三個主要面向：

| 面向             | 好的 AX 長什麼樣子                                                                                                                                                                                                   |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Automated checks | 快、確定性的 [automated check](./Automated%20check.md)——型別、測試、lint——讓 agent 不需要人介入就能自己修正                                                                                                          |
| 架構             | 一個 agent 不用讀完全部就能摸清楚的 codebase：結構可預期、大量行為藏在小的介面後面、名字看得出東西在做什麼                                                                                                           |
| 空出來的 context | [AGENTS.md](./AGENTS.md.md)、[skill](./Skill.md)、[tool](./Tool.md) 都保持精簡，讓 [context window](./Context%20window.md) 大部分都能留給眼前的任務，agent 才能待在 [smart zone](./Smart%20zone.md) 裡，而不是被淹沒 |

AX 跟 DX 有重疊——好的 checks 跟乾淨的架構對兩邊都有幫助——但兩者也會分岔。人可以忍受口耳相傳的知識、慢的 CI、「這個去問 Sarah」，agent 不行。Agent 也用不到 IDE 的提示或漂亮的儀表板；牠們需要的是失敗訊息以文字形式出現在 [tool result](./Tool%20result.md) 裡。一個 codebase 可以 DX 很好但 AX 很差。

*避免使用：*把 AX 當成 DX 的同義詞——這兩群受眾需要投入不同的東西。

_使用情境：_

「Agent 在 API repo 寫出來的程式碼很棒，在前端 repo 寫出來的卻是垃圾。」

「API repo 有嚴格的型別跟快速的測試套件，前端 repo 兩者都沒有，還掛了四十個一直載入的 skill。這是 AX 的落差，不是 model 的問題。」
