---
description: 文件裡指向另一份文件的提及，讓 agent 只在任務需要時，才把它拉進 context。
---

文件裡的一句話，指向另一份文件，讓 [agent](./Agent.md) 只在任務需要時，才把它拉進 [context window](./Context%20window.md)。[Progressive disclosure](./Progressive%20disclosure.md) 就是靠這個單位組成的。

用 pointer（而不是把內容整個內嵌進去）的理由是成本。一個 pointer 在 context window 裡只占一行。它背後的文件可能有好幾千個 [token](./Token.md)，但這些 token 在 agent 真的去跟隨這個 pointer 之前，完全不花錢。把一份 2,000 token 的執行手冊直接寫進 [AGENTS.md](./AGENTS.md.md)，每一個 [session](./Session.md) 都要付這個成本；換成「部署流程：見 `internal/deploy.md`」，就只有真的要部署的 session 才會載入它。任務對上的時候，agent 會用一次 [tool call](./Tool%20call.md) 去跟隨這個 pointer。

一個 pointer 要能發揮作用，需要兩個部分：一個穩定的路徑，以及足夠的描述，讓 agent 知道跟隨它值不值得。只有一個路徑、沒有描述的 pointer，agent 沒有理由去跟隨；「見 `internal/deploy.md`」，完全不提裡面是什麼，需要它的 session 也會直接跳過。把這句話寫成符合任務出現方式的樣子：「release、deploy 或 rollback——先讀 `internal/deploy.md`」。

仔細看的話，pointer 到處都是：AGENTS.md 裡的一行字、[skill](./Skill.md) 的描述（harness 會載入描述，skill 本體則等在後面）、目錄清單裡的檔名、文件之間的連結。

Pointer 也可以把一份 [secondary source](./Secondary%20source.md) 連回它衍生自的 [primary source](./Primary%20source.md)——像是 compaction 摘要裡標出原始 transcript 的出處，或是一份文件標出它描述的原始檔案。這讓 secondary source 的失真變得可以補救：當摘要證明不夠用時，agent 可以跟隨這個 pointer 去讀原始資料，而不是只能用摘要留下來的內容硬撐。

_避免使用：_「reference」——太乾，沒有傳達出跟隨它會把更多 context 拉進來這件事。「portal」——太花俏。

_使用情境：_

「AGENTS.md 越來越肥大了。」

「裡面大部分應該是 context pointer，不是內容本身。把一直都要用到的規則留在裡面；部署手冊跟風格指南拆成 skill，只留一個 context pointer 在後面。」
