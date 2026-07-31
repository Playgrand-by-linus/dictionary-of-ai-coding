---
description: 一種工作模式：使用者不做 human review 就接受 agent 寫出來的程式碼。diff 被當成不透明的黑盒子。
---

一種工作模式：使用者不經 [human review](./Human%20review.md) 就接受 [agent](./Agent.md) 寫出來的程式碼。diff 被當成不透明的東西——重要的是程式的行為對不對，不是裡面寫了什麼。[automated review](./Automated%20review.md) 跟 [automated check](./Automated%20check.md) 也許還是會跑；vibe coding 對這兩者都沒有表態。

這個詞來自 Andrej Karpathy，他在 [2025 年初創了這個說法](https://x.com/karpathy/status/1886192184808149383)：你「完全順著感覺走」（fully give in to the vibes），並「忘記程式碼本身的存在」——描述你想要什麼、接受回來的結果，然後靠實際跑跑看來判斷好不好。

vibe coding 是拿檢查換速度。讀 diff 通常是 agent 驅動工作裡最慢的一步，拿掉它就等於拿掉那個主要瓶頸。對於出錯代價很低的程式碼——[prototype](./Prototyping.md)、一次性腳本、內部工具——這是個合理的交換。風險的大小，會隨著程式碼的存續時間跟利害關係一起放大。

代價會晚一點才出現。用 vibe coding 做出來的變更，會不斷累積進一個沒有人讀過的 codebase，而且唯一檢查過的東西是行為——所以任何行為沒有顯露出來的問題，像是被寫進 log 的密鑰、漏掉的邊角案例、或悄悄處理錯誤的資料，都會在沒人看到的情況下上線。第一次有人來 debug 這個系統，就是第一次有人讀這段程式碼。human review 沒了之後，還在跑的任何自動驗證——測試、型別檢查、automated review——就是這段程式碼會經過的唯一一道關卡。

*避免使用：*把「vibe coding」當成「low-quality AI coding」的同義詞——這個詞指的是審查的態度，不是產出的程式碼品質。

_使用情境：_

「auth flow 裡它改了什麼，你看過了嗎？」

「vibe coding 過去了——login 還能用，我就只檢查了這個。」

「push 之前先讀一下 diff，在 auth 上 vibe 下去，就是密鑰外洩到 log 裡的常見原因。」
