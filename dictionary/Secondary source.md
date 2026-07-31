---
description: 對 primary source 隔了一層的描述——摘要、文件、compaction 摘要。載入成本低，但天生就會失真。
---

一份對 [primary source](./Primary%20source.md) 的描述，隔了一層——描述程式碼的文件、描述逐字紀錄的摘要、描述搜尋結果的報告。載入 [context window](./Context%20window.md) 的成本比它描述的來源低，而且天生就會失真：寫的人已經決定了什麼重要，而他們捨棄掉的東西，對只看得到這份摘要的讀者來說，就是不存在。

大部分的 [context](./Context.md) engineering，做的都是製造 secondary source。[Compaction](./Compaction.md) 把 [session](./Session.md) 的歷史紀錄變成一份摘要，拿去當下一個 session 的起點。一個 [subagent](./Subagent.md) 把自己的 context 燒在一次雜訊很多的搜尋上，然後回報一份簡短的報告。一份 [handoff artifact](./Handoff%20artifact.md) 把一個 session 裡的決策濃縮成一份文件，給下一個 session 讀。[Memory system](./Memory%20system.md) 把一個 session 學到的東西蒸餾成筆記。每一種做法，付出的代價都一樣：用保真度換空間。

Secondary source 會用兩種方式失敗。一種是失真——compaction 摘要漏掉了那個 schema 決策、報告沒提到那個邊界案例。另一種是漂移——primary source 變了，但描述它的東西沒跟著變，所以文件用這一季的自信，講著上一季的架構。當一個 [agent](./Agent.md) 根據一個已經用某種方式失敗的 secondary source 去行動，它會很有自信地根據錯誤的資訊做事；修法就是把它送回去看 primary source。

這兩種失敗都不代表 secondary source 是個錯誤。Context window 是有限的，primary source 又很貴；沒有摘要、報告、handoff 文件，大的東西根本裝不下。真正的技巧在於分辨哪些細節就算失真也撐得住——撐不住的時候，回去對照 primary source 驗證。一份做得好的 secondary source，會帶一個指回原始出處的 [context pointer](./Context%20pointer.md)——摘要會寫出它是從哪份逐字紀錄來的，文件會寫出它描述的是哪個檔案——這樣當描述不夠用的時候，讀的人可以順著這個指標走，而不是只能將就著用那份失真的東西。

_使用情境：_

「Handoff 文件說 auth 做完了，但新的 session 一直發現 token refresh 是壞的。」

「那份文件是 secondary source——上一個 session 寫下的是它相信的東西，不是事實。讓新的 session 跑一次 auth 測試，相信 primary source。」
