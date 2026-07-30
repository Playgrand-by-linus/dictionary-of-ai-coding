---
description: agent 現在手邊能取用、跟任務相關的資訊——agent 目前所知、且與任務有關的那部分。
---

[Agent](./Agent.md) 現在手邊能取用的、跟任務相關的資訊。這是一個抽象名詞——不是 model 看到的原始輸入（那是 [context window](./Context%20window.md)），也不是持續累積的歷史紀錄（那是 [session](./Session.md)），而是 agent 目前所知、跟任務有關的那部分。「把某個東西載入 context」，意思是讓它成為這個集合的一部分；「context engineering」則是整理、篩選這個集合的技藝。

這三個詞可以清楚分開：

| 詞彙           | 指的是什麼                                            |
| -------------- | ----------------------------------------------------- |
| Context        | agent 目前手邊、跟任務相關的資訊                      |
| Context window | model 每次請求實際看到的那串 [token](./Token.md) 序列 |
| Session        | [harness](./Harness.md) 儲存的、持續進行中的對話      |

這個區分很重要，因為 context 衡量的是品質，不是數量。一個 context window 可以幾乎被塞滿，但 context 品質還是很差——裡面是好幾千個 token 的過時 tool 輸出，沒有一個跟眼前的任務有關。它也可以幾乎是空的，但 context 卻很出色：就只有任務真正關鍵的那一個型別定義。

大部分日常的翻車，追根究柢都是 context 的問題。當 agent 捏造出一個不存在的 API、跟先前的決定互相矛盾，或是亂猜一個 schema 時，第一個該問的問題是：它動手的當下，context 裡有什麼——通常是相關的事實根本沒被載入，或是被埋在 [attention degradation](./Attention%20degradation.md) 底下。解法是篩選：載入任務需要的東西，把不需要的擋在外面。

_使用情境：_

「它一直捏造出型別裡根本沒有的欄位。」

「型別檔案不在 context 裡——它是在讀呼叫端然後用猜的。先把定義讀進來。」
