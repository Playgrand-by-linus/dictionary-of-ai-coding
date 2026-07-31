---
description: agent 執行時所在的隔離環境——container、VM、或受限的 shell。限制 agent 行為的波及範圍。
aliases:
  - Sandboxing
  - Sandbox / Sandboxing
---

[Agent](./Agent.md) 執行時所在的隔離 [environment](./Environment.md)——一個 container、VM、暫時性的 [filesystem](./Filesystem.md)、或是權限受限的 shell。限制 agent 行為的波及範圍：就算 agent 跑了破壞性的指令、或抓到了什麼惡意的東西，損害都被關在裡面。這是讓 [AFK](./AFK.md) 可行的安全基礎。

Sandbox 跟 [permission mode](./Permission%20mode.md) 是從相反的兩端解決同一個問題。Permission 是在動作執行之前先問；sandbox 是限制動作真的執行的話能碰到什麼範圍。Permission 需要你人在 [loop](./Human-in-the-loop.md) 裡盯著——每一次詢問都是一次打斷——一個一直在問的 session，幾乎稱不上自主。Sandbox 花的是基礎設施，不是你的注意力：隔離做得越強，需要問的問題就越少。

隔離分幾個等級：

| 等級       | 是什麼                                      | 關住什麼                         |
| ---------- | ------------------------------------------- | -------------------------------- |
| 受限 shell | 針對每個指令的 OS 層級限制                  | 專案外的寫入、網路存取           |
| Container  | 全新的 filesystem，沒掛載任何憑證，用完就丟 | agent 對自己那台機器做的任何事   |
| VM／雲端   | 完全獨立的一台機器，通常由 harness 提供     | 所有東西，包括 kernel 層級的逃逸 |

Sandbox 關不住的，是合法離開它的動作。一個有你 git 憑證的 agent 可以直接 push；一個有網路存取權的 agent 可以呼叫 production API。先決定什麼東西可以跨過這條邊界，再決定要把邊界做多厚。

_使用情境：_

「我想讓它整晚跑 [bypass-permissions](./Agent%20mode.md)，但我還沒準備好接受這個。」

「放進 sandbox 裡——全新的 container，不掛憑證，不接網路。最壞的情況就是它把自己的 filesystem 弄爆，你就把這個 container 丟掉。」
