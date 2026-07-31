<!--
  GENERATED FILE — DO NOT EDIT.
  Source: dictionary/*.md, internal/Curriculum.md, internal/README.template.md
  Regenerate: npm run generate
-->

<p>
  <a href="https://www.aihero.dev/ai-coding-dictionary">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777878285/dictionary-dark_2x.png">
      <source media="(prefers-color-scheme: light)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777878285/dictionary-light_2x.png">
      <img alt="AI Coding Dictionary" src="https://res.cloudinary.com/total-typescript/image/upload/v1777878285/dictionary-light_2x.png" width="369">
    </picture>
  </a>
</p>

# AI Coding 辭典（繁體中文版）

**AI coding 給人的感覺常常像是專家限定**。看不懂的術語、莫名其妙的失敗、跟工作量對不上的帳單。

其實不然。這些困惑有很大一部分是人為造成的：**背後有一整個由創投資金撐起的產業，靠著讓這件事看起來很難而受益**。

基本的術語一個下午就能學會。學會之後，整件事就不再像是瞎猜。

為什麼 context 會退化？為什麼帳單這麼高？為什麼同一個 prompt 在不同天表現不一樣？

每個問題都有清楚的答案，只是需要有人告訴你該用哪些詞。

這本辭典就是為此而生。**AI coding 的詞彙，翻譯成白話文**。

術語名稱維持英文原文，說明文字譯為繁體中文。若要看英文版，見 [README.en.md](./README.en.md)。

**想要更多不只是詞彙的內容？** 加入 62,000+ 位開發者的行列，訂閱 **[aihero.dev/newsletter](https://www.aihero.dev/s/dictionary-newsletter)**，取得最新技能、AI engineering 的思考，以及讓你保持領先的資源（英文內容）。

---

## 目錄

<details>
<summary>Section 1 — 模型</summary>

- [AI](#ai)
- [Model](#model)
- [Parameters](#parameters)
- [Training](#training)
- [Inference](#inference)
- [Effort](#effort)
- [Token](#token)
- [Next-token prediction](#next-token-prediction)
- [Non-determinism](#non-determinism)
- [Model provider](#model-provider)
- [Harness](#harness)
- [Model provider request](#model-provider-request)
- [Input tokens](#input-tokens)
- [Output tokens](#output-tokens)
- [Prefix cache](#prefix-cache)
- [Cache tokens](#cache-tokens)

</details>

<details>
<summary>Section 2 — Session、Context Window 與 Turn</summary>

- [Stateless](#stateless)
- [Context](#context)
- [Context window](#context-window)
- [Stateful](#stateful)
- [Agent](#agent)
- [System prompt](#system-prompt)
- [Session](#session)
- [Turn](#turn)

</details>

<details>
<summary>Section 3 — Tool 與 Environment</summary>

- [Environment](#environment)
- [Filesystem](#filesystem)
- [Tool](#tool)
- [Tool call](#tool-call)
- [Tool result](#tool-result)
- [MCP](#mcp)
- [Permission request](#permission-request)
- [Permission mode](#permission-mode)
- [Agent mode](#agent-mode)
- [Sandbox](#sandbox)

</details>

<details>
<summary>Section 4 — 失敗模式</summary>

- [Sycophancy](#sycophancy)
- [Hallucination](#hallucination)
- [Parametric knowledge](#parametric-knowledge)
- [Knowledge cutoff](#knowledge-cutoff)
- [Contextual knowledge](#contextual-knowledge)
- [Attention relationship](#attention-relationship)
- [Attention budget](#attention-budget)
- [Attention degradation](#attention-degradation)
- [Smart zone](#smart-zone)

</details>

<details>
<summary>Section 5 — Handoff（交接）</summary>

- [Clearing](#clearing)
- [Handoff](#handoff)
- [Primary source](#primary-source)
- [Secondary source](#secondary-source)
- [Handoff artifact](#handoff-artifact)
- [Spec](#spec)
- [Ticket](#ticket)
- [Compaction](#compaction)
- [Autocompact](#autocompact)

</details>

<details>
<summary>Section 6 — 記憶與引導</summary>

- [Memory system](#memory-system)
- [AGENTS.md](#agentsmd)
- [Progressive disclosure](#progressive-disclosure)
- [Context pointer](#context-pointer)
- [Skill](#skill)
- [Subagent](#subagent)

</details>

<details>
<summary>Section 7 — 工作模式</summary>

- [Human-in-the-loop](#human-in-the-loop)
- [AFK](#afk)
- [Automated check](#automated-check)
- [Automated review](#automated-review)
- [Human review](#human-review)
- [Vibe coding](#vibe-coding)
- [Design concept](#design-concept)
- [Grilling](#grilling)
- [Prototyping](#prototyping)
- [DX](#dx)
- [AX](#ax)

</details>

## Section 1 — 模型

### AI

一個會移動的標籤，不是一項技術。「AI」不像 [model](#model) 或 [token](#token) 那樣指稱一個固定的東西——它指向的是電腦目前能做到、令人印象深刻的新事。現在它指的是 large language model。它以前指過完全不同的東西：

| 年代          | 「AI」當時指的是                                                                   |
| ------------- | ---------------------------------------------------------------------------------- |
| 1950 年代     | 符號推理——定理證明器、下棋程式。                                                   |
| 1960～70 年代 | 規則式的符號程式——ELIZA、SHRDLU。                                                  |
| 1980 年代     | 專家系統——成千上萬條手寫的 if-then 規則，用來編碼人類專業知識。                    |
| 1990 年代     | 賽局樹搜尋——深藍打敗卡斯帕洛夫（1997 年）。研究者當時完全避開「AI」這個詞          |
| 2000 年代     | 統計機器學習——垃圾郵件過濾器、推薦系統。當時還是叫「machine learning」，不叫「AI」 |
| 2010 年代     | 深度學習——影像辨識（AlexNet，2012 年）、AlphaGo（2016 年）。                       |
| 2020 年代     | Large language model——ChatGPT（2022 年）讓「AI」變成聊天機器人的代名詞             |

這個指稱會移動，靠的是一個已知的機制，有時被稱為 AI effect：一項技術一旦穩定可靠，它就會被改名——變成「只是」搜尋、「只是」統計——然後「AI」這個詞就往前挪到下一個還沒解決的問題上。這個現象早就有人講過。Bertram Raphael 在 1971 年這樣講：「AI 是我們還不知道該如何用電腦好好解決的那些問題的統稱。」Larry Tesler 大約在 1979 年的講法是：「智慧，就是機器還沒做到的事。」

這就是為什麼談 AI 的對話常常各說各話。像「AI 不會推理」或「AI 被過度炒作」這類說法，都帶著一個隱藏的時間戳記——可能講的是專家系統，可能講的是 2010 年代的影像分類器，也可能講的是上個月的 LLM，而每一種指涉都會撐出不同的結論。當一場關於 AI 的討論卡住的時候，通常的解法是把「AI」換成真正意指的那個精確詞彙：model、[harness](#harness)、[agent](#agent)，或是給它的那份 [context](#context)。

*避免使用：*在任何技術性的論斷裡使用「AI」——直接點名你指的是哪個部分。用「AI coding」當作這個實踐領域的名稱沒問題；但「AI 在產生幻覺」這種講法就不行。

_使用情境：_

「CTO 想知道 AI 能不能處理分流佇列。」

「先把這句話翻譯清楚再評估範圍——她指的是接在 harness 裡、能存取工單系統的 LLM。單講『AI』不算一份 spec。」

### Model

[Parameters](#parameters)。[Stateless](#stateless)——只做 [next-token prediction](#next-token-prediction)，別的都不做。「Claude Opus 4.x」跟「GPT-5.x」都是 model。Model 自己一個沒辦法做任何 agentic 的事；它得被 [harness](#harness) 包起來才行。

Model 不能讀檔案、跑指令、瀏覽網頁，也記不住昨天發生的事——它就是吃 [token](#token) 進去，每一次 [model provider request](#model-provider-request) 預測出 token 出來。所有感覺起來像 [agent](#agent) 在做事的部分——挑 [tool](#tool)、讀結果、一直循環到任務做完——其實都是 harness 把一大串這種預測串起來執行。

[Model provider](#model-provider) 出的 model 有分等級：一個最聰明但慢又貴的大型版本，還有幾個比較快、比較便宜、但能力比較差的小型版本。挑哪個等級是一個真正的決定——規劃跟難搞的除錯用重量級的，機械式的改動用輕量級的——harness 會讓你在 [session](#session) 中途切換。

對這個詞嚴格一點，也能讓診斷更準。「這個 model 不擅長這個」是一個很具體的說法——同一個 model 換一個 harness，或者換一個不同的 [context](#context)，常常表現得完全不一樣。怪 model 之前，先檢查它拿到了什麼：大部分讓人失望的輸出，根源都是 context 或 harness，不是 parameters。

_使用情境：_

「規劃這一步要不要把 model 從 Sonnet 換成 Opus？」

「試試看——不過這個任務裡大部分的工作是 harness 在做。如果 [system prompt](#system-prompt) 跟 tool 都不對，換 model 也沒用。」

### Parameters

[Model](#model) 內部的數字——常常是幾十億個——在 [training](#training) 過程中調整出來。model「知道」的一切都存在這些數字裡。Training 設定它們的值；[inference](#inference) 則原封不動地使用它們。也叫 _weights_。

從機制上看，parameters 就是把 input 轉成 output 的東西。[Next-token prediction](#next-token-prediction) 是一次巨大的計算：[context window](#context-window) 裡的 [tokens](#token) 進去，跟 parameters 相乘運算，出來的就是下一個 token 的預測。model 裡面沒有事實資料庫，也沒有程式碼查表——就只有這些數字，被排列成讓這個計算傾向於產生有用的輸出。model 能從 training 裡背出來的事實，例如某個標準函式庫的 API，就是 [parametric knowledge](#parametric-knowledge)：存在 parameters 裡，不是從別的地方查來的。

值得記住的重點是：parameters 在 training 結束後就凍結了。你在一個 [session](#session) 裡做的任何事都不會改變它們——你做的修正、你給它看的 codebase、它學到的教訓，都不會。每一個 session 跑的都是同一組數字。這就是為什麼 model 是 [stateless](#stateless)、為什麼它內建的知識停在 [knowledge cutoff](#knowledge-cutoff)、也是為什麼跟專案有關的東西都得靠 [context](#context) 送進去。改變 parameters 的唯一辦法是再做一次 training——而那實際上會產生一個不同的 model。

_使用情境：_

「可以拿我們的 codebase 對它做 fine-tune 嗎？」

「那樣會更新 parameters——之後就是不同的 model 了。對單一專案來說，把 codebase 當 context 載入，幾乎永遠比重新 training 便宜。」

### Training

讓 [model](#model) 的 [parameters](#parameters) 定型的過程，做法是讓它接觸大量文字，並調整 parameters 以改善 [next-token prediction](#next-token-prediction)。這是 [model provider](#model-provider) 執行的一次性、成本高昂的過程。涵蓋 pre-training（主要那次大規模跑法）跟 post-training（後續的調校，像是 instruction-following 跟安全性）；這兩者的區別在這本詞典的層次上不重要。

機制是大規模的重複：給 model 看一段文字，讓它預測下一個 [token](#token)，把 parameters 往實際的下一個 token 那個方向推一點，然後在好幾兆個 token 上重複這個過程。沒有任何東西是以事實或規則的形式存起來的——model「知道」的一切，都是它在變得更擅長預測的過程中產生的副作用，壓縮進 parameters 裡變成 [parametric knowledge](#parametric-knowledge)。

有兩個後果在日常使用上很重要。training 在某個時間點就結束了，所以 model 有一個 [knowledge cutoff](#knowledge-cutoff)——它沒看過你上個月才升級的那個函式庫版本。而且 training 不是你能做的事：當 model 不知道你的 codebase、你的慣例、你內部的 API 時，解法從來都不是「教會 model」——而是把那些材料放進 [context](#context)，這是你唯一能控制的輸入。

_使用情境：_

「我們能讓它知道我們內部的 API 嗎？」

「不能靠 training——那是 model provider 要花好幾個月做的事。把 API 文件載入 context 裡，那才是你真正能動的槓桿。」

### Inference

跑一個訓練好的 [model](#model) 來產生輸出——這是每一次 [model provider request](#model-provider-request) 都會發生的事。[Parameters](#parameters) 保持不變；model 只是對給定的 [context](#context) 做 [next-token prediction](#next-token-prediction)。相對於 [training](#training) 便宜很多，但是按 [token](#token) 計費，也是使用 model 時最主要的花費。

一個 model 的生命分成兩個階段：

| 階段      | 什麼時候發生              | 做什麼事                                         | Parameters |
| --------- | ------------------------- | ------------------------------------------------ | ---------- |
| Training  | 一次性，在發布之前        | 從 training corpus 產生 parameters               | 正在被寫入 |
| Inference | 每次有人使用這個 model 時 | 讓凍結的 parameters 跑過你的 context，產生 token | 唯讀       |

在 inference 這個階段做的任何事，都不會寫回 parameters——這就是為什麼你今天做的修正，明天不會留下來。Model 下一個 [session](#session) 又犯一樣的錯，即使你上次仔細解釋過怎麼修，也不是它不理你；它就是沒辦法從那次對話裡學到東西。Model 是 [stateless](#stateless) 的——延續性得從外面來，來自 [context window](#context-window) 或 [memory system](#memory-system)。

這個機制也解釋了你的帳單怎麼算。每一次 request 都是讓 model 跑過整個 context，所以成本會隨著 [input tokens](#input-tokens) 跟 [output tokens](#output-tokens) 增加，一個 agent 打了幾十次 [tool](#tool) call，每一次來回都要付一次 inference 的錢。這就是為什麼 context 大小既是成本問題，也是品質問題。

_使用情境：_

「為什麼帳單是隨用量算，不是固定的授權費？」

「你付的是 inference 的錢——每一次 model provider request 都是在 provider 的硬體上跑一次 model。Training 已經做完了，但 inference 的成本是按 request 累加的，一個 [turn](#turn) 只要有呼叫 tool，就可能展開成好幾次 request。」

### Effort

Effort 是一個旋鈕，控制 [model](#model) 回答前要做多少推理。它是逐次 [model provider request](#model-provider-request) 設定的，控制 model 在開始寫出你看到的回應之前，要想多長。那段思考跟其他一切一樣，是在 [inference](#inference) 時產生的；[harness](#harness) 常常把它藏起來，但那是 model 真的在做的工作。

effort 開得越高，花費越多、跑得越慢。這段推理是以 [token](#token) 的形式產生的，就算你從沒看到它，也是照 [output tokens](#output-tokens) 計費，而且是一個一個 token 產生出來的——所以把 effort 調高，答案送到你手上前要等更久，帳單也會變多。這是拿更多深思跟速度、成本做交換。

大多數 harness 會把 effort 呈現成一個小小的階梯：

| 等級   | 用途                                         |
| ------ | -------------------------------------------- |
| Low    | 機械式的編輯、查詢、路徑單一且規格明確的變更 |
| Medium | 日常的 coding——一般預設值                    |
| High   | 棘手的 bug、設計決策、多步驟的規劃           |
| Max    | 最困難的問題，答錯的話後續要收拾的成本很高   |

設錯的症狀兩邊都會出現。在一個困難的問題上把 effort 設得太低，得到的會是一個信心十足卻很淺的答案，跳過了這個問題原本需要的推理——讀起來沒問題，錯的方式卻會在後面害你付出代價。為了一個改一行的改名把 effort 設成 max，你就是坐著等一段長長的思考過程，結果產出的東西跟最低設定完全一樣。

讓 effort 對應到任務本身，而不是對應到整個 [session](#session)。真正需要費心推理的那個部分才調高，周圍那些照本宣科的工作就調回來。

_使用情境：_

「這個並行處理的修法它一直搞砸——我已經重講三次了。」

「把 effort 調高。這是個很吃推理的 bug，預設設定下，它在決定要怎麼做之前想得不夠久。」

### Token

[model](#model) 讀寫的最小單位。大致跟一個詞差不多大，但不完全一樣——常見的詞是一個 token，罕見或很長的詞會被拆成好幾個。[context window](#context-window) 大小、成本、延遲全都是用 token 計算的。

文字要透過 tokenizer 才會變成 token：一份在 [training](#training) 之前就學好的、有好幾萬個片段的固定詞表，會把任何輸入拆成一串詞表項目。model 從來看不到字元或詞——每一段文字進去之前都會先被轉成 token，而 [next-token prediction](#next-token-prediction) 出來的時候，也是一次產生一個 token。

概略來說，一個 token 大約是四分之三個英文單字，所以一千個 token 大概是 750 個字。程式碼比較難預測：常見的關鍵字跟慣用寫法會被切得很緊湊，而產生出來的識別字、雜湊值、base64 區塊、壓縮過的輸出，每個「詞」都會被拆成很多 token。規律是：在 tokenizer 訓練材料裡常出現的文字，會得到又短又有效率的編碼；沒出現過的，就會被剁成很多小塊。像 `a3f9c2e1` 這種雜湊值從來沒在任何地方出現過，所以會被拆成一堆 token，而 `function` 是一個 token。這就是為什麼一個看起來很小、卻塞滿不尋常字串的檔案，可以佔掉 context window 出乎意料大的一部分。

token 是其他一切度量的單位。成本是按 token 算的——provider 會分開計費 [input token](#input-tokens) 跟 [output token](#output-tokens)。速度是每秒幾個 token，因為輸出是一次生成一個 token。而 context window 是固定數量的 token，所以你檔案的 token 數決定了能塞進去多少。

_避免使用：_「word」——token 的邊界跟詞的邊界對不上，而且真正重要的單位是「每秒幾個 token」跟「每一塊錢幾個 token」。

_使用情境：_

「這個 prompt 會有多大？」

「拿去跑一次 tokenizer——schema 本身很精簡，但 JSON 的 key 很怪，會被拆成比你想像中更多的 token。」

### Next-token prediction

[Model](#model) 實際上在做的事，就是這個。給定一個 [context](#context)，它取樣出下一個 [token](#token)，接上去，再跑一次。每一個輸出——一句話、一個 [tool call](#tool-call)、一份上千行的檔案——都是一個 token、一個 token 疊出來的。Model 沒有別的運作模式。

每一步都用同一套方式：[context window](#context-window) 裡的 token 跑過 [parameters](#parameters)，對詞彙表裡的每一個 token 都算出一個機率——這個接下來很可能出現，那個比較不可能。從這些機率裡取樣出一個 token，接上去，用稍微變長一點的 context 再跑一次這個迴圈。這個取樣的步驟，就是為什麼同一個 prompt 在不同次執行會產生不同輸出：[non-determinism](#non-determinism) 是這套機制內建的，不是後來疊上去的 bug。

抓住這個機制，就能解釋一些原本看起來很奇怪的行為。Model 從來不會在吐出一個 token 之前檢查它是不是*真的*——只檢查它是不是*很可能*——這就是 [hallucination](#hallucination) 的根源。它是邊做邊定案的，所以一句聽起來很有把握的開場白，可能會把接下來整個答案帶偏。而且因為 [output token](#output-tokens) 是嚴格一個一個產生的，生成速度替任何 [agent](#agent) 能跑多快設了一個下限。

_使用情境：_

「Agent 是怎麼『決定』要呼叫一個 tool 的？」

「它沒有在決定——從頭到尾都是 next-token prediction。Tool call 只是 harness 從輸出串流裡解析出來的一段結構化字串。」

### Non-determinism

同樣的輸入可能產生不同的輸出。把同一個 [model](#model) 用完全相同的 [context](#context) 跑兩次，可能會拿到兩個不一樣的答案——有時候只差一個字，有時候整個做法完全不同。你的程式碼什麼都不用改，這種事就會發生。

這是 model 產生文字的方式，加上 [model provider](#model-provider) 處理 [request](#model-provider-request) 的方式，兩者共同造成的特性。在 [inference](#inference) 的過程中，model 對接下來可能出現的每一個 [token](#token) 產生一個機率分布，然後從裡面取樣出一個——通常是故意加了一點隨機性，因為永遠都選機率最高的那個 token，會產生重複、品質比較差的文字。回答早期有一個 token 取樣結果不一樣，後面每一個 token 都會跟著變，這就是為什麼差一個字，最後會變成完全不同的做法。Provider 那一端的服務方式又疊加了更多變異：request 會在共用的硬體上被打包在一起處理，批次之間微小的浮點數差異，就可能把兩個 token 之間本來很接近的機率高低翻過來。沒有一個開關可以把這一切都關掉。

同一個任務丟給 [agent](#agent)，結果會有落差，這是預期之內的事。大部分的回應都落在一個還算合理的鐘形曲線裡——這也是為什麼這種 non-determinism 大致上還能接受——但尾端是真實存在的：有些日子 model 感覺特別靈光，有些日子感覺像整個抓不到重點。同一個任務，骰子擲出來的點數不一樣而已。這帶來兩個實際的後果。重試是一個站得住腳的策略：一次失敗的嘗試只是從這個分布裡抽到的其中一次，同一個任務重新做一次，結果可能就單純地比較好。而且驗證比用確定性工具的時候更重要——你沒辦法測一次 agent 的行為就假設它每次都會重複，所以 [automated check](#automated-check) 得負責把抽到的爛結果攔下來。

要小心別把這件事說得太有劇情。人是很會抓模式的動物，連續幾次跑不好的結果，感覺起來會很像在證明「這個 model 這禮拜變差了」。通常那只是分布本身而已。

_使用情境：_

「Claude 今天怎麼這麼廢，是不是換了一個比較差的版本？」

「大概不是——model 的輸出是 non-deterministic 的。同一個任務，你本來就會遇到表現好的日子跟表現差的日子。明天再試一次，先別急著找原因。」

### Model provider

不管是什麼東西在幫 [model](#model) 做 [inference](#inference)。通常是一個遠端服務（Anthropic、OpenAI、Google），但也可以是本機——Ollama、LM Studio、llama.cpp 跑在你自己的機器上。[Harness](#harness) 不會自己跑 model；它是去請一個 provider 幫忙跑。

Provider 擁有整套機器：[parameters](#parameters) 就放在它的硬體上，每一次 [model provider request](#model-provider-request) 都是 harness 把 [token](#token) 送過網路，再拿回預測結果。這使得 provider 變成一整類問題的源頭，而這些問題常常被誤怪到 model 或 harness 頭上——rate limit、容量降級、斷線，全都是這一層的事。當 [agent](#agent) 卡在一半的 [session](#session)，或者每個 [turn](#turn) 都出錯，最先該查的是 provider 的狀態頁。

Provider 也訂了商業條款：[input](#input-tokens) 跟 [output token](#output-tokens) 各自的計費單價、[prefix cache](#prefix-cache) 的折扣，還有到底有哪些 model 可以用。要注意的是，provider 跟做出這個 model 的公司可能不是同一家——Bedrock、Vertex、OpenRouter 提供的都是別人做的 model。

Local provider 是拿能力換控制權：塞得進你自己硬體的 model，遠比 frontier 等級的小得多，但東西不會離開這台機器，也沒有按 token 計費的帳單。

_使用情境：_

「能不能幫這個 air-gapped 的客戶跑離線版？」

「把 model provider 換成本機的——他們的機器上跑 Ollama 或 llama.cpp。Harness 不在乎，反正它只是打一個不同的 endpoint。」

### Harness

圍繞在 [model](#model) 周圍、把它變成 [agent](#agent) 的所有東西：[tool](#tool)、[system prompt](#system-prompt)、[context window](#context-window) 管理、permission、hook。**Claude.ai** 跟 **Claude Code** 跑在同一個 model 上，但行為不一樣，因為兩者的 harness 不同。

Model 本身只做一件事：吃文字進去，吐文字出來。它不能讀檔案、跑指令，也記不住上一個 [turn](#turn)。這些全部都是 harness 提供的。它替每一次 [model provider request](#model-provider-request) 組出 [context](#context)、執行 model 要求的 [tool call](#tool-call)、把 [tool result](#tool-result) 餵回去、儲存 [session](#session) 紀錄、在有風險的動作前問你要不要放行，還要決定什麼時候該 [compact](#compaction)。Agent loop——model 提議、harness 執行、一直重複——是由 harness 在跑的。

這對診斷問題很重要。兩個產品之間行為不一樣，或者昨天跟今天不一樣，通常不是 model 在變，是 harness 在變。不同的 system prompt、不同的 tool 組合、改過的 permission 預設值、新的 context 管理策略，都會改變行為，而 model 完全沒變。這也代表你大部分的設定都放在 harness 這一層：[AGENTS.md](#agentsmd) 檔案、permission 設定、hook，這些指示都是給 harness 的，不是給 model 的。

範例：Claude Code、Cursor、Codex CLI——還有 Claude.ai，它是一個聊天用的 harness，不是寫程式用的。

_使用情境：_

「同一個 model，為什麼 Claude Code 會改檔案，Claude.ai 卻只會回答問題？」

「Harness 不一樣——Claude Code 有 [filesystem](#filesystem) tool、不同的 system prompt，還有一層 permission。這裡不一樣的不是 model。」

### Model provider request

從 [harness](#harness) 到 [model provider](#model-provider) 的一次來回。Harness 送出目前的 [context](#context)；provider 回傳一個回應（一個 [tool call](#tool-call) 或一個最終答案）。如果 [agent](#agent) 呼叫 [tool](#tool)，一則使用者訊息就可能引出很多次 model provider request——每一個 [tool result](#tool-result) 都會觸發下一次 request。

每一次 request 都帶著全部的東西：[system prompt](#system-prompt)、到目前為止的完整對話、每一個 tool result。[Model](#model) 是 [stateless](#stateless) 的，所以 provider 在 request 之間什麼都不留——第四十次 request 重送了第三十九次送過的東西，再加上多一個 tool result。[Prefix cache](#prefix-cache) 存在的目的，就是讓這種重複變得負擔得起。

Request 也是計費的單位。[Input token](#input-tokens)、[output token](#output-tokens)，還有 cache 折扣，都是按 request 算的，這就是為什麼一個看起來人畜無害的問題，可能花掉一筆讓人意外的錢：成本不是跟你的訊息成正比，而是跟 request 的數量、乘上每一次 request 帶的 context 大小成正比。

值得把 request 跟 [turn](#turn) 分開來看。一個 turn 是跟你的一次交流，而單一一個 turn——「修好失敗的測試」——會展開成一串 request：

| Request | Model 回傳的內容               | Harness 接著做的事         |
| ------- | ------------------------------ | -------------------------- |
| 1       | Tool call：跑測試              | 跑測試，把失敗的輸出接上去 |
| 2       | Tool call：讀測試檔案          | 把檔案內容接上去           |
| 3       | Tool call：讀原始碼檔案        | 把檔案內容接上去           |
| 4       | Tool call：改原始碼檔案        | 套用這次編輯，把結果接上去 |
| 5       | Tool call：再跑一次測試        | 跑測試，把通過的輸出接上去 |
| 6       | 最終答案：「修好了，測試通過」 | 顯示給你看                 |

一個 turn 用掉六次 request——每一次都要重送整個 context。想不通 [token](#token) 到底花去哪了的時候，去數 request 的數量，不是 turn 的數量。

_使用情境：_

「一個問題燒掉四萬個 token？」

「看一下 tool call——十二次 grep、八次 read、四次 edit。每一個 tool result 都會催生下一次 model provider request，整個 [session](#session) 的 prefix 每次都要重送一次。」

### Input tokens

[Harness](#harness) 在每一次 [model provider request](#model-provider-request) 送出的 [token](#token)——[system prompt](#system-prompt)、對話紀錄、[tool result](#tool-result)，所有 [model](#model) 在寫東西之前要讀進去的東西。計費比 [output token](#output-tokens) 便宜，因為處理起來比 output token 便宜。

在做 [AI](#ai) coding 的時候，input token 佔你帳單的大部分。Model 是 [stateless](#stateless) 的，所以每一個 [turn](#turn) 都要把整個 [session](#session) 當作 input 重送一次：你的第一則訊息、每一次回覆、每一個 tool result，全部都要重送。第五十個 turn 的 input，包含了前面四十九個 turn。單一一次 model provider request 可能只產生幾百個 output token，卻要重送十萬個累積下來的 input token。

[Prefix cache](#prefix-cache) 可以降低這個成本：跟前一次 request 完全吻合的歷史紀錄，會用便宜的 [cache token](#cache-tokens) 計費，而不是全價的 input。如果 input 的成本還是讓你受不了，解法就是縮小要重送的東西——在任務之間 [clearing](#clearing) 或 [compacting](#compaction)。

_使用情境：_

「帳單很高，可是 [agent](#agent) 沒寫多少東西。」

「是 input token 的問題——每個 turn 都要把整個 session 重送一次。沒有 prefix cache 的話，每次 request 都要重新付一次歷史紀錄的錢。」

### Output tokens

[Model](#model) 生成回來的 [tokens](#token)。計費比 [input tokens](#input-tokens) 高——通常大約是五倍——因為產生它們要花更多運算。

model 寫出來的每一樣東西都算數：你讀到的文字、它寫出的程式碼、[tool call](#tool-call)，還有它回答之前做的任何 extended thinking。最後這一項常讓人意外——推理用的 tokens 算作 output，就算 [harness](#harness) 通常不會把它們顯示給你看，把 [effort](#effort) 調高也會花掉更多這種 tokens。

Output tokens 也決定了 [session](#session) 的節奏。model 讀 input 讀得很快，但生成 output 是一次一個 token，所以當一個 [turn](#turn) 感覺很慢的時候，幾乎都是 output 正在被寫出來，不是 input 正在被讀。等很久，通常代表接下來會是一個很長的答案。

_使用情境：_

「這次重構的 session 一直在燒 credit，明明 input 很小。」

「Agent 在整檔重寫，不是在打補丁。Output tokens 大概是 input 費率的五倍——讓它改成輸出 diff，帳單就會降下來。」

### Prefix cache

[Provider](#model-provider) 端的儲存機制，讓連續的 [model provider request](#model-provider-request) 可以跳過重新處理共用的 prefix。當一個 request 的開頭跟最近一次的開頭吻合——同樣的 [system prompt](#system-prompt)、同樣的歷史紀錄到某個點為止——provider 就會重複使用它先前算過的結果，把這些 [tokens](#token) 當作 [cache tokens](#cache-tokens)，用低很多的費率計費。

這個快取划算，是因為 [session](#session) 是只增不減地成長的。每一次 request 都會把整段歷史當作 [input tokens](#input-tokens) 重新送出去（原因見那個條目），而在正常的 session 裡，歷史紀錄只會在尾端變動——每一次 request 都是前一次加上幾則新訊息。Provider 只處理一次那段共用的開頭，把結果存起來，然後從 prefix 結束的地方接著算下去。沒有這個快取，一個跑了 50 個 [turn](#turn) 的 session，就得把第一個 turn 重新處理五十次。

快取也會過期。一筆紀錄能保溫多久，因 model provider 而異——通常是幾分鐘，不是幾小時。讓一個 session 閒置超過這個窗口，下一次 request 就得先用全額價格重建一次 prefix，之後快取才會恢復。這大多是 [harness](#harness) 開發者要煩惱的事；對使用者來說，看得到的效果就是：停頓很久之後的那些 request，會比停頓之前的貴。

_使用情境：_

「為什麼帳單在 session 跑到一半的時候突然飆高？」

「Harness 開始在每個 turn 都把當下時間塞進 system prompt。Prefix cache 一碰到第一個變動的 token 就會失效，所以那之後的每一個 request 都用全額費率計費。」

### Cache tokens

[Provider](#model-provider) 從先前一次 [model provider request](#model-provider-request) 快取下來的 [input tokens](#input-tokens)，不用重新處理。當連續幾次請求共用同一個前綴時，provider 會透過它的 [prefix cache](#prefix-cache) 重複利用先前的運算結果，並把被快取的那部分用低很多的費率計費。這是讓長 [session](#session) 負擔得起的關鍵機制——沒有它，每個 [turn](#turn) 都得重新支付整段歷史的費用。

會這樣，是因為 session 計費的方式。[Model](#model) 是 [stateless](#stateless) 的，所以每一次請求都要把整段對話——[system prompt](#system-prompt)、每一則訊息、每一個 [tool result](#tool-result)——當成 input tokens 重新送一次。到了第五十個 turn，每次請求都帶著五十個 turn 的歷史，如果全部都用全額費率計費，每次都要付一次。快取改變了這個算法：provider 已經在一模一樣的前綴裡處理過的 token，會以 cache tokens 計費，費率通常是 input 費率的十分之一或更低。在一個長 session 裡，你送出去的大部分都是 cache tokens，帳單才不會失控。

一個例子可以說明什麼時候會被快取、什麼時候不會。每個字母代表一段對話內容；每次請求都送出目前為止的整段對話：

| 這次請求送出 | 被快取的部分 | 以全額費率計費的部分 | 原因                                          |
| ------------ | ------------ | -------------------- | --------------------------------------------- |
| `AB`         | 無           | `AB`                 | 第一次請求——沒有東西可以比對                  |
| `ABC`        | `AB`         | `C`                  | `AB` 剛好是上一次請求的前綴，完全吻合         |
| `ABCD`       | `ABC`        | `D`                  | 前綴仍然完整                                  |
| `AXCD`       | `A`          | `XCD`                | 有個編輯把 `B` 改成了 `X`；比對從那裡開始失敗 |

這個快取的脆弱之處很具體：它比對的是完全一致的前綴。只要對話裡更早的地方有任何變動——[harness](#harness) 重新排列了內容、時間戳記更新了、某個檔案的呈現方式變了——快取就會從那個點開始失效，之後的所有內容都會用全額 input 費率計費。快取也會在閒置幾分鐘後過期，所以一個暫停很久之後恢復的 session，會需要把歷史重新支付一次費用。當一個 session 的花費無緣無故暴增時，去用量報表裡比較 cache tokens 跟 input tokens——快取壞掉的話，會先在那裡看得出來。

_使用情境：_

「長 session 的成本高得嚇人——一次重構就花了八塊美金。」

「查一下 cache tokens。如果 harness 在每個 turn 之間重新排列了 system prompt 或檔案順序，前綴就會斷掉，每次請求都會用全額 input 費率計費。」

## Section 2 — Session、Context Window 與 Turn

### Stateless

不會把任何資訊往後帶。[model](#model) 在每次 [model provider request](#model-provider-request) 之間是 stateless 的——每次請求都要重新送出完整的 [context window](#context-window)，因為 model 沒有別的辦法看到其他東西。[agent](#agent) 預設在 [session](#session) 之間也是 stateless 的：新的 session 從空白開始，完全沒有先前 session 的痕跡。與 [stateful](#stateful) 相對。

model 本身是永久 stateless 的：它的 [parameters](#parameters) 在 [training](#training) 之後就是凍結的，你在 [inference](#inference) 時做的任何事都不會改變它們。model 不會從你的糾正裡學習，不會記得昨天已經被講過同一件事，也沒有在慢慢認識你——不論對話感覺起來多不一樣。session 裡那種連續的感覺，是 [harness](#harness) 製造出來的，它保留逐字稿並在每次請求時重新送出。model 不是在記得這場對話，而是在重新讀它。

實際的後果是：如果你想要某件事被跨 session 記住，就得把它寫在某個 agent 會讀回去的地方。這就是 [AGENTS.md](#agentsmd) 檔案、[memory system](#memory-system)、[handoff artifact](#handoff-artifact) 存在的原因——它們是會被載入未來 session [context](#context) 的檔案，替代了 model 沒有的記憶。當 agent 一再犯下你已經糾正過的錯誤，該問的問題不是它為什麼沒學到——它本來就學不到——而是那個糾正應該寫在哪裡，才能讓未來每個 session 都讀得到。

_使用情境：_

「為什麼我每次 [clear](#clearing) 之後它就忘記那個慣例？」

「model 是 stateless 的——新的 session 從空白開始。如果你想要它被帶下去，就寫進 AGENTS.md，或是 harness 在 session 開始時會載入的記憶檔案。」

### Context

[Agent](#agent) 現在手邊能取用的、跟任務相關的資訊。這是一個抽象名詞——不是 model 看到的原始輸入（那是 [context window](#context-window)），也不是持續累積的歷史紀錄（那是 [session](#session)），而是 agent 目前所知、跟任務有關的那部分。「把某個東西載入 context」，意思是讓它成為這個集合的一部分；「context engineering」則是整理、篩選這個集合的技藝。

這三個詞可以清楚分開：

| 詞彙           | 指的是什麼                                            |
| -------------- | ----------------------------------------------------- |
| Context        | agent 目前手邊、跟任務相關的資訊                      |
| Context window | model 每次請求實際看到的那串 [token](#token) 序列 |
| Session        | [harness](#harness) 儲存的、持續進行中的對話      |

這個區分很重要，因為 context 衡量的是品質，不是數量。一個 context window 可以幾乎被塞滿，但 context 品質還是很差——裡面是好幾千個 token 的過時 tool 輸出，沒有一個跟眼前的任務有關。它也可以幾乎是空的，但 context 卻很出色：就只有任務真正關鍵的那一個型別定義。

大部分日常的翻車，追根究柢都是 context 的問題。當 agent 捏造出一個不存在的 API、跟先前的決定互相矛盾，或是亂猜一個 schema 時，第一個該問的問題是：它動手的當下，context 裡有什麼——通常是相關的事實根本沒被載入，或是被埋在 [attention degradation](#attention-degradation) 底下。解法是篩選：載入任務需要的東西，把不需要的擋在外面。

_使用情境：_

「它一直捏造出型別裡根本沒有的欄位。」

「型別檔案不在 context 裡——它是在讀呼叫端然後用猜的。先把定義讀進來。」

### Context window

[Model](#model) 在每一次 [model provider request](#model-provider-request) 裡看到的全部內容。有限、依 model 而定，而且是 model 感知任何事情的唯一介面。

它是一串連續的 [token](#token)：[system prompt](#system-prompt)、到目前為止的對話、[harness](#harness) 餵回來的每一個 [tool result](#tool-result)。只要東西在這串序列裡，model 就能用；不在裡面，model 就不知道它存在——不管是你的 codebase、你昨天改過的檔案，還是你三個 session 前下的指示。window 之外的任何東西，都得先透過（通常是）一次 [tool call](#tool-call) 被帶進來，才能影響任何事。

有限，代表它會被填滿。每一個 [turn](#turn) 都會再往裡面加東西——你的訊息、model 的回覆、tool result——一個夠長的 [session](#session) 遲早會碰到上限，逼出 [compaction](#compaction) 或 [clearing](#clearing)。有限也代表 window 裡的東西彼此在競爭：你多載入一個 token，剩下能用的就少一個，而你其實用不到的內容，一樣會占掉 model 的 [attention](#attention-budget)。實際的做法是把 window 當成一個預算來對待——載入任務需要的東西，其餘的留在外面。

_避免使用：_「memory」——context window 是運作中的暫存狀態，不會跨 session 保留下來。[Memory](#memory-system) 是疊在上面的另一個獨立概念。

_使用情境：_

「我可以直接把整個 monorepo 貼進 prompt 嗎？」

「context window 是 200k token——大概只夠放這個 repo 的五分之一。挑任務會碰到的檔案，其餘的留在 tool call 後面。」

### Stateful

把資訊往後帶。[session](#session) 在 [turn](#turn) 之間是 stateful 的——[context](#context) 會隨著 session 進行不斷累積，這也是為什麼長時間的 session 會漂向 [dumb zone](#smart-zone)。[agent](#agent) 可以透過加上一套 [memory system](#memory-system)，把資訊寫進 [environment](#environment) 並在未來 session 開始時重新載入，做到跨 **session** 的 stateful。[model](#model) 本身永遠不是 stateful 的；任何看起來連續的感覺，都是 [harness](#harness) 把 context 重新餵回去的結果。與 [stateless](#stateless) 相對。

各層級的 state 存在哪裡：

| 層級        | Stateful？ | 怎麼做到                                                                                               |
| ----------- | ---------- | ------------------------------------------------------------------------------------------------------ |
| Model       | 從不       | [Parameters](#parameters) 是凍結的；它只看得到每次請求裡的內容                                     |
| Session     | 跨 turn    | harness 把每一則訊息和 [tool result](#tool-result) 都附加進 context                              |
| Harness     | 跨 session | 記憶檔案、[AGENTS.md](#agentsmd)、[handoff artifact](#handoff-artifact)——寫下來，之後再載入 |
| Environment | 永遠       | 不論有沒有 session 在跑，檔案都會留著                                                                  |

每一層的 stateful 特性，都是靠重新讀取下面一層存的東西做出來的：session 感覺起來連續，是因為 harness 把訊息紀錄重新送給 stateless 的 model；agent 能跨 session 記住東西，是因為 harness 把檔案從 environment 重新載入。model 本身從來沒有存過任何 state。

State 不是永遠都想要的。凡是被往後帶的東西都會影響接下來發生什麼，所以 session 早期做出的錯誤假設，也會一路被帶下去。[clearing](#clearing) 就是刻意把 session state 丟掉、從寫下來的東西重新開始的動作。

_使用情境：_

「它記得我昨天的偏好——這代表 model 學到了嗎？」

「不是，agent 是 stateful 的，因為 harness 把偏好寫進了記憶檔案，並在 session 開始時重新載入。model 本身完全沒看到昨天發生的事。」

### Agent

一個 [model](#model) 被 [harness](#harness) 接上 [tool](#tool)、[system prompt](#system-prompt)、[context window](#context-window)，跟使用者輪流進行 [turn](#turn)。_Claude Code 是一個 agent。Cursor 是一個 agent。Claude.ai 是一個 agent。_ Agent 是你實際在對話的對象——是動起來的 model，被配置成某種用途。

跟這本辭典裡大多數詞不一樣，「agent」指的不是一個機械式的零件。Model 是一個裝著 [parameters](#parameters) 的檔案；harness 是可以直接指到的軟體。Agent 兩者都不是——它是你在對話的那個單位。人會不斷把 [AI](#ai) 擬人化，而 agent 就是那個被擬人化的單位：你委派工作的對象、讀你訊息並回答你的東西，也就是「它又把 build 弄壞了」裡的那個「它」。當你說 agent 做了什麼，你的意思是 model 加上 harness 做的，但你是把這個組合當成單一行動者在說話。

這個概念比這一波 AI 還老。軟體 agent——你把一個目標委派給它、由它代表你行動的程式——這個概念存在的時間跟 AI 一樣久。

_避免使用：_「the AI」、「the bot」——太模糊，分不清你指的是那組 parameters 還是被接上 harness 之後的東西。

_使用情境：_

「這次遷移你用哪個 agent？」

「本機用 Claude Code，UI 的部分用 Cursor——底層是同一個 model，只是 harness 不一樣。」

### System prompt

[harness](#harness) 附加在每一次 [model provider request](#model-provider-request) 前面的指示——[agent](#agent) 的長期任務說明：它是誰、該怎麼表現、能呼叫哪些 [tool](#tool)、該遵守什麼慣例。在一個 [session](#session) 裡通常維持不變。

system prompt 是 harness 的廠商寫的，不是你寫的，而且在 coding harness 裡通常很大——常常是好幾萬個 [token](#token) 的行為規則、tool 描述、邊角案例處理，而且每個 [turn](#turn) 都要當作 [input token](#input-tokens) 付費。你自己的長期指示會跟著一起搭便車：像 [AGENTS.md](#agentsmd) 這樣的檔案，會在 session 開始時載入到 system prompt 旁邊，所以 [model](#model) 是先把廠商的說明跟你的一起讀完，才看到你的訊息。

因為它在每次請求裡都一模一樣，所以構成了 [prefix cache](#prefix-cache) 的開頭——這也是為什麼 harness 會讓它在整個 session 裡固定不變，而不是邊跑邊改。

model 被訓練成優先聽從 system prompt，而不是使用者訊息。所以當一個 agent 堅持某個你從沒要求過的慣例，或是用一種你怎麼樣都改不掉的格式輸出，通常是它在服從 system prompt——而你的訊息在這場拉鋸裡輸了。有些 harness 是可以自訂的：它們讓你完整看到 system prompt，你可以讀到 agent 實際上被告知了什麼，並加以修改。

_使用情境：_

「兩個 harness，同一個 model，同樣的 prompt，行為完全不一樣。」

「system prompt 不一樣。一個調校成寫精簡的程式碼修改，另一個調校成會解釋——差異在你的訊息送到之前就已經存在了。」

### Session

跟 [agent](#agent) 互動的一次有邊界的過程。從空的開始，累積訊息、[tool result](#tool-result)、跟讀過的檔案，在被 [cleared](#clearing)、關閉、或 [compact](#compaction) 成一個新 session 的時候結束。Session 就是把 [context window](#context-window) 填滿的東西：如果 context window 是那個箱子，session 就是慢慢把箱子填滿的東西。大到一個 context window 裝不下的工作，就得拆到好幾個 session 裡做。

Session 的訊息歷史，就是 agent 的工作記憶。[Model](#model) 是 [stateless](#stateless) 的，所以它看起來記得的每一件事——你要求了什麼、測試結果是什麼、它三個 turn 前做了什麼決定——全都在這份訊息歷史裡，隨著每一次 [model provider request](#model-provider-request) 一起重新送出去。不在 session 裡的東西，對 agent 來說就是不存在。

這份記憶會隨著 session 結束而消失。一個新 session 從零開始：昨天 session 結束時對你的 codebase 瞭若指掌的 agent，今天早上什麼都不記得。留下來的是 [filesystem](#filesystem)——一個 session 裡寫的檔案，下一個 session 讀得到，這就是 [handoff](#handoff)、[memory system](#memory-system)、跟 [AGENTS.md](#agentsmd) 賴以運作的基礎。

Session 在哪裡結束，是你決定的。Session 裡的每一件事都會影響之後每一個 [turn](#turn)，所以在同一個 session 裡做不相關的任務，會留下殘留物，染色到後面的答案。一個 session 只做一件任務，能讓 context 保持相關；一件任務做完，就是清掉的好時機。

_使用情境：_

「一個 session 能撐多久才會開始垮掉？」

「看工作內容——專注的重構撐得比開放式研究久。Session 一旦膨脹了，就 handoff 或 compact，不要硬撐下去。」

### Turn

一則使用者訊息，加上 [agent](#agent) 為此做出的所有回應，直到它把控制權交還給使用者為止。包含一次以上的 [model provider request](#model-provider-request)——如果 agent 呼叫了 [tool](#tool)，可能是很多次。一個釐清用的問題會結束這個 turn；你的回覆會開啟下一個。階層關係是 [session](#session) **> Turn > Model provider request**。

turn 值得特別拿出來講的地方在於，它的長度是 agent 決定的，不是你決定的。你交出一則訊息；agent 決定要串多少個 tool call 才交還控制權。一個 turn 可以只是一句話的回答，也可以是二十分鐘的讀檔、編輯、跑測試。這其實是同一件事的兩面：長的 turn 讓 [AFK](#afk) 這種工作方式成立，但長的 turn 也是在無人監督下出錯的地方——等 agent 交還控制權的時候，可能早就偏離你原本的意思很遠了。

turn 也是拿來引導方向的自然單位。turn 裡面發生的一切都跟你無關；turn 跟 turn 之間的空檔才是你能改方向的地方。大多數 [harness](#harness) 會把這件事做得柔和一點：你可以在 turn 進行到一半時打斷，讓 agent 停下來重新引導，或是在它工作時先打一段訊息，等這個 turn 結束就會被讀到。如果你發現自己一再對 turn 跑出來的結果不滿意，通常的解法是要求更小的 turn——先出一份計畫，一次一步——用自主性去換取更頻繁、可以介入引導的空檔。

_使用情境：_

「一個 turn 花了兩分鐘？」

「它在那個 turn 裡面發了十四次 [tool call](#tool-call)——每一次都是一個獨立的 model provider request。延遲會一直疊加，直到 agent 終於把控制權交還給你。」

## Section 3 — Tool 與 Environment

### Environment

[Agent](#agent) 動手的那個世界——[harness](#harness) 以外，agent 透過 [tool result](#tool-result) 感知、透過 [tool call](#tool-call) 改變的一切。harness 負責「執行」agent；environment 則是 agent「工作的地方」。像 [AGENTS.md](#agentsmd) 這樣的檔案，住在 environment 裡；把它載入 [context window](#context-window) 的，是 harness。[Filesystem](#filesystem) 是最常見的一種 environment，但不是唯一的一種（資料庫、遠端 API、瀏覽器 session 都可以是 environment）。

Agent 只有在去看的時候，才看得到 environment。它對 environment 的一切了解，都是透過某一次 tool result 得來的，所以它手上的畫面，是一堆快照的集合，每一張在拍下來的當下都是準的。如果一個檔案在 agent 讀過之後又變了——你手動改了它，或是某個 build 步驟重新產生了它——agent 會繼續拿那份過時的副本來推理，直到有什麼東西促使它重新讀取。Agent 一臉篤定地描述一個早就長得不一樣的檔案，通常就是這個原因：environment 動了，快照沒有跟著動。

Environment 也是唯一會持續存在的那一層——唯一始終是 [stateful](#stateful) 的一層。一個 [session](#session) 的 context 在 session 結束時就沒了，但寫進 environment 的檔案會留下來，讓下一個 session 讀取——這正是 [memory system](#memory-system)、[handoff artifact](#handoff-artifact)、還有 AGENTS.md 賴以運作的基礎。任何 agent 明天還應該記得的事，都必須最終落腳在 environment 裡。

Environment 有多大，是你決定的。[Sandbox](#sandbox) 會把它縮小，限制 agent 碰得到什麼；加一個 [tool](#tool) 會把它擴大，把一個資料庫或 API 納入可及範圍。邊界裡面的東西，才是 agent 能感知、能改變的；邊界以外的一切，對 agent 來說根本不存在。environment 有沒有妥善設置來支援 agent 的工作，就是這個 codebase 的 [AX](#ax)。

*避免使用：*把「environment」拿來指 runtime 或 harness 本身——harness 是外層的包裝，environment 才是工作空間。

_使用情境：_

「agent 看不到 staging 資料庫的 schema。」

「把它接進 environment——給它一個限定在 staging、唯讀的 `psql` tool。harness 本身沒問題，只是沒有東西可以動手。」

### Filesystem

[Agent](#agent) 讀取、寫入、並在裡面執行指令的檔案與目錄樹——coding agent 預設的一種 [environment](#environment)。[AGENTS.md](#agentsmd)、[skill](#skill)、原始碼、build script、還有 [tool](#tool) 的設定檔，全都住在 filesystem 裡。當一個 [harness](#harness)「在你的專案裡啟動」時，它其實是把 agent 指向某一個 filesystem。

Agent 只能透過 [tool call](#tool-call) 去碰它——讀一個檔案、寫一個檔案、跑一個 shell 指令。硬碟上的東西，在被某次 tool call 載入之前，都不在 [context window](#context-window) 裡，這也是為什麼 agent 能在一個遠比 window 大的 repository 裡工作：filesystem 裝著全部的東西，context 只裝著目前任務讀過的部分。有些 harness 預設就會把目前目錄的檔名載入 context window——不是內容，只是這棵樹——這些檔名扮演的角色就是 [context pointer](#context-pointer)：agent 看得到有什麼東西存在，然後去讀它需要的那些檔案。

而且它是跟你共用的。agent 編輯的檔案，跟你在編輯器裡打開、在 git 裡 diff 的是同一批——filesystem 是你審查 agent 做了什麼的共同工作空間。

_使用情境：_

「為什麼它讀不到我的 AGENTS.md？」

「它跑的是另一個 filesystem——[sandbox](#sandbox) 掛載的是上層目錄，不是專案根目錄。把 harness 重新指過去。」

### Tool

[harness](#harness) 開放給 [agent](#agent) 呼叫的函式——Read、Write、Bash、Search。tool 是 agent 感知並操作 [environment](#environment) 的方式：除了透過 [tool result](#tool-result)，agent 沒辦法看到 environment；除了透過 [tool call](#tool-call)，agent 也沒辦法改變它。每一次 tool call 都要多花一次 [model provider request](#model-provider-request)，因為結果得先送回 model，它才能決定下一步要做什麼。

大多數 coding agent 內建的 tool：

| Tool   | 作用                                              |
| ------ | ------------------------------------------------- |
| Read   | 把檔案內容當成 tool result 回傳                   |
| Write  | 在 [filesystem](#filesystem) 裡新增或編輯檔案 |
| Bash   | 執行一個 shell 指令並回傳輸出                     |
| Search | 在整個 codebase 裡找出符合某個模式的檔案或文字    |

一個 tool 由三件事定義：名稱、一段描述它做什麼的說明，以及它參數的 schema。harness 會在每一次請求裡把這些定義送給 [model](#model)，而 model 選 tool 的方式，跟它產生其他所有東西一樣——靠寫 [token](#token)，在這裡就是一個附帶參數的結構化呼叫。model 從來不會自己執行任何東西；harness 讀這個呼叫、執行對應的函式，再把結果送回去。

tool 清單決定了 agent 能做什麼。一個能力很強的 model，配上很窄的 tool 集合，出來就是一個能力很窄的 agent：它會把所有事都硬塞進手上有的那幾個 tool，這也是為什麼 agent 這麼依賴 Bash——一個 shell 就是一個能碰到系統裡大部分東西的 tool。要乾淨俐落地給 agent 加上某個能力，就替它加一個 tool；[MCP](#mcp) 是從 harness 外部接入 tool 的標準做法。

tool 的定義在每一次請求裡都會佔掉 [context](#context)，所以一個很大的 tool 集合，在任何 tool 被呼叫之前就已經有固定的成本——而且很多描述相似的 tool 放在一起，只會讓 model 更難挑對該用哪一個。

_使用情境：_

「agent 可以直接查詢 staging 嗎？」

「在 harness 裡加一個 `psql` tool，限定在 staging 上唯讀。沒有對應的 tool，agent 對 filesystem 之外的東西完全看不到。」

### Tool call

[Model](#model) 的輸出，指名一個 [tool](#tool) 跟它的參數——就只是結構化文字。它自己什麼都不會做；[harness](#harness) 得讀懂它，才會真的去執行。由 model 在一次 [model provider request](#model-provider-request) 裡產生。

一次 tool call 的生命週期：

| 步驟 | 誰      | 發生什麼事                                                            |
| ---- | ------- | --------------------------------------------------------------------- |
| 1    | Model   | 從 [system prompt](#system-prompt) 裡的描述得知有哪些 tool 可用 |
| 2    | Model   | 發出一個 call——tool 名稱加上參數，通常是 JSON——然後停下來             |
| 3    | Harness | 解析這個 call，對照 [permission mode](#permission-mode) 檢查    |
| 4    | Harness | 允許的話就執行                                                        |
| 5    | Harness | 把結果包成 [tool result](#tool-result)，放進下一次請求送回去    |

一個 [agent](#agent) 的 [turn](#turn) 通常就是好幾輪這種來回串在一起。

因為這個 call 跟其他所有輸出一樣，是靠 [next-token prediction](#next-token-prediction) 生出來的，它可能出錯的方式跟任何 model 輸出一樣：一個不存在的路徑、指令根本沒有的參數、看起來合理但其實不對的引數。harness 執行的是寫下來的內容，不是原本想做的事——打錯一個路徑不會優雅地報錯，而是直接改到別的檔案。

_使用情境：_

「它說測試跑過了，但檔案的時間戳記沒變。」

「看一下 transcript——它是真的發出了 tool call，還是只是描述自己跑了測試？call 是 model 產生的，但 harness 沒有真的執行的話，什麼事都沒發生。」

### Tool result

[harness](#harness) 執行完一次 [tool call](#tool-call) 之後回傳的東西——檔案內容、指令輸出、錯誤訊息。[agent](#agent) 對 [environment](#environment) 唯一的視角。會在*下一次* [model provider request](#model-provider-request) 裡送回給 [model](#model)，由 model 決定要拿它怎麼辦。tool call 跟 tool result 是同一次交換的兩端，都發生在同一個 [turn](#turn) 裡。

tool result 的生命週期：

| 步驟 | 誰      | 發生什麼事                                                     |
| ---- | ------- | -------------------------------------------------------------- |
| 1    | Harness | 執行這個 tool call——跑指令、讀檔案                             |
| 2    | Harness | 把結果記下來：輸出、內容，或錯誤                               |
| 3    | Harness | 把它當成一則訊息附加進 [context](#context)                 |
| 4    | Harness | 在下一次 model provider request 裡把整個 context 送給 provider |
| 5    | Model   | 讀這個結果，並決定：再發一次 tool call，還是給出最終答案       |

這個結果會在 context 裡留到 [session](#session) 結束。tool result 通常佔掉 coding session context 裡的大部分：每一次讀檔、每一次跑測試、每一次搜尋都是完整落地，而且早就沒用了還繼續佔著 [token](#token)。幾個大的結果——一份很囉唆的測試紀錄、一個整份讀進來的產生檔案——就能比對話本身更快把 session 推向 [context window](#context-window) 的邊緣。

因為 model 看到的就只有這個結果，它沒有辦法回頭去檢查 environment 本身。如果輸出被截斷了、指令悄悄地失敗了，或是 harness 回傳的是錯誤訊息而不是內容，model 就是拿它被給的東西去推理。當 agent 對你系統的理解看起來不對，該去查的就是 tool result：逐字稿裡某個地方，有一個結果講的東西跟你知道的事實不一樣。

_使用情境：_

「它在推理這個檔案的時候，好像把它當成是空的。」

「tool result 回來的是權限被拒，不是檔案內容。model 只看到那串錯誤訊息——它沒有別的辦法看到這個檔案。」

### MCP

**Model Context Protocol.** 把外部 tool server 接進 [harness](#harness) 的協定——[agent](#agent) 怎麼取得 harness 內建之外的 [tool](#tool)。Agent 從來不會「呼叫 MCP」；它呼叫的是一個 tool，只是這個 tool 剛好是 harness 從某個 MCP server 拿到的。MCP 也會提供 resource（唯讀資料）跟 prompt（可重複使用的樣板），但提供 tool 才是主要用途。

這個協定解決的是一個整合問題。沒有這個標準的話，每一個 harness 都得自己寫一套 Linear 整合、一套 Slack 整合、一套資料庫整合——每一個都要分開寫、分開維護。有了 MCP，整合只要寫成一個 server 一次，任何相容 MCP 的 harness 都能用。Harness 連到 server，server 宣告自己提供哪些 tool，這些 tool 就跟內建的 tool 一起變成 agent 能用的東西。

代價要用 [context](#context) 付。Server 宣告的每一個 tool，都會變成一份定義——名稱、描述、參數 schema——而 [model](#model) 只能呼叫它知道的 tool。最直接的做法是把每一份定義都預先載進 [context window](#context-window)：裝了幾個內容豐富的 server，一個 [session](#session) 還沒開始打字，就已經有好幾千個 [token](#token) 的 tool schema，佔掉了做這個任務根本用不到的那些 tool 的 [attention budget](#attention-budget)。

現在很多 harness 會用 tool search 來緩解這個問題：context 裡放的不是完整定義，而是一個指向可用 tool 的 [context pointer](#context-pointer)——agent 依名稱或用途去搜尋 tool，只有需要的時候才載入它的定義。如果你的 harness 沒做這件事，預先付出的成本就還在，這時候只裝專案真的用得到的 server 才划算。

_使用情境：_

「Agent 需要讀 Linear 的 ticket。」

「把 harness 設定成用 Linear 的 MCP server——它會把 Linear 的 API 變成 agent 能呼叫的 tool。省得你自己寫客製化的 tool wrapper。」

### Permission request

[Harness](#harness) 在執行一個沒有預先核准的 [tool call](#tool-call) 之前，秀給使用者看的畫面。[Model](#model) 產生一個 tool call；harness 不會馬上執行，而是先暫停下來詢問。核准就執行；拒絕的話，harness 會把拒絕的結果當作 [tool result](#tool-result) 回報給 model。這就是 harness 讓人類進到 [loop](#human-in-the-loop) 裡、去處理有風險或敏感動作的機制。

一次 permission request 的生命週期：

| 步驟 | 誰      | 發生什麼事                                                              |
| ---- | ------- | ----------------------------------------------------------------------- |
| 1    | Model   | 產生一個 tool call                                                      |
| 2    | Harness | 對照 [permission mode](#permission-mode) 跟任何已儲存的核准來檢查 |
| 3    | Harness | 已預先核准的話就馬上執行；否則暫停下來、把請求秀出來                    |
| 4    | 使用者  | 核准一次、核准整個 [session](#session) 剩下的時間、或拒絕           |
| 5    | Harness | 執行這次呼叫，或是把拒絕當作 tool result 送回去                         |

拒絕一個請求，是在引導 agent 的方向。model 會像對待任何其他 tool result 一樣讀懂這個拒絕，並做出反應——它會試別的做法，或是問你比較想要怎麼做。大部分 harness 都能讓你在拒絕的時候附上一句話，這就讓這次請求變成一個可以引導方向的時機點：「不要那樣，改用 migration script」剛好會在 model 決定下一步要做什麼的當下發生作用。

代價是每一次請求都是一次同步等待你回應。[Agent](#agent) 會卡在那裡，直到你回答為止，你在盯著的時候這沒問題，但你不在的時候就是個麻煩——一個一直觸發請求的 agent，沒辦法丟著讓它 [AFK](#afk) 跑。Permission mode 就是那個調整鈕：哪些呼叫可以自由執行、哪些要先問，最好還搭配 [sandbox](#sandbox)，讓放寬「自由執行」的範圍變得安全。

_使用情境：_

「它被一個 permission request 卡了十分鐘——我剛好在開會。」

「這就是 human-in-the-loop 的代價。把安全的 [tools](#tool) 預先核准，讓請求只在真的有風險的呼叫上跳出來。」

### Permission mode

[Agent mode](#agent-mode) 裡負責權限把關的那一層——哪些 [tool call](#tool-call) 會觸發 [permission request](#permission-request)，哪些自動放行。在 [harness](#harness) 開始把行為指示一起打包進來之前，這原本就是 mode 系統存在的目的。

Harness 通常提供一整排等級：

| 模式             | 讀取 | 寫入與 shell         | 典型用途                                      |
| ---------------- | ---- | -------------------- | --------------------------------------------- |
| 唯讀／plan       | 自動 | 封鎖                 | 研究、規劃、審閱                              |
| 預設             | 自動 | 詢問                 | 日常有人盯著的工作                            |
| 自動編輯         | 自動 | 編輯自動、shell 詢問 | 信任的 repo、機械式的變更                     |
| 「Yolo」／全自動 | 自動 | 自動                 | [Sandbox](#sandbox)、[AFK](#afk) 執行 |

選哪一個等級，是安全跟被打斷之間的取捨，兩種失敗都會讓人感覺到。太緊，你就變成瓶頸：[agent](#agent) 每隔幾秒就為了無害的讀取停下來，你按核准按到變成反射動作，核准這個動作也就失去意義——這種橡皮圖章式的核准兩頭都不討好，該有的打斷一個沒少，該有的保護一個都沒有。太鬆，agent 就會去改你原本想先看過的檔案、跑你原本想先看過的指令。

鬆的那一端，在 sandbox 裡最站得住腳，因為一個爛 [tool](#tool) call 炸開的範圍是被關住的。在 sandbox 之外，大多數人的做法是讀取自動核准，不可逆的事情則留一個 [human in the loop](#human-in-the-loop)。

_使用情境：_

「它每一個 grep 都要暫停確認——AFK 的執行整個被搞爛了。」

「唯讀的 tool 就把 permission mode 放鬆，寫入跟 shell 還是要問。研究型 [session](#session) 裡大部分的 permission request 都是雜訊。」

### Agent mode

一種預設組合，決定 [agent](#agent) 在執行時怎麼運作——把一個 [permission mode](#permission-mode) 跟注入 [system prompt](#system-prompt) 的行為指示綁在一起。例如：預設模式會在有風險的呼叫上詢問；**plan mode** 會封鎖編輯、引導 agent 去做研究；**accept-edits** 模式會自動核准編輯；**bypass permissions** 模式（口語上叫 **YOLO mode**）會自動核准所有事情。可以在 [session](#session) 中途切換。

把兩者綁在一起，正是 mode 跟單純的權限設定不一樣的地方。Permission mode 只是一道閘門：它決定哪些 [tool call](#tool-call) 能通過。光有閘門會做出一種 agent：牠想編輯卻不能——牠提出寫入請求，被擋下來，再試別的辦法。注入的指示把那個「想」拿掉了：plan mode 不只是封鎖編輯，它還告訴 agent 現在是規劃階段，所以 agent 會去讀、去問、去提案，而不是硬頂著閘門。閘門跟引導的方向是一致的。

實務上，你會隨著任務過程中信任程度的變化去切換 mode。同一個任務可以經過好幾種 mode：做法還在成形時用 plan mode，最早幾筆細膩的編輯用預設的詢問模式，agent 表現出牠理解這個變更之後換成 accept-edits，[AFK](#afk) 在 [sandbox](#sandbox) 裡跑的時候用 bypass。切換 mode 不用付出任何代價：對話會從原本的地方繼續，只是換了新的權限跟新的指示。如果你發現自己每個提示都不看就核准，代表 mode 設得比你實際的信任程度還緊；如果你一直在拒絕編輯，代表設得太鬆了。

\_廠商用詞：\_Claude Code 把這些叫做「permission mode」，Codex 叫做「approval mode」——兩者都早於行為綁定這個做法。

_使用情境：_

「它一直在改檔案，我只是想要一份計畫。」

「切到 plan mode——它會封鎖寫入，停在研究階段。」

「那之後的 AFK 跑法呢？」

「Bypass mode，但只能在 sandbox 裡面用。」

### Sandbox

[Agent](#agent) 執行時所在的隔離 [environment](#environment)——一個 container、VM、暫時性的 [filesystem](#filesystem)、或是權限受限的 shell。限制 agent 行為的波及範圍：就算 agent 跑了破壞性的指令、或抓到了什麼惡意的東西，損害都被關在裡面。這是讓 [AFK](#afk) 可行的安全基礎。

Sandbox 跟 [permission mode](#permission-mode) 是從相反的兩端解決同一個問題。Permission 是在動作執行之前先問；sandbox 是限制動作真的執行的話能碰到什麼範圍。Permission 需要你人在 [loop](#human-in-the-loop) 裡盯著——每一次詢問都是一次打斷——一個一直在問的 session，幾乎稱不上自主。Sandbox 花的是基礎設施，不是你的注意力：隔離做得越強，需要問的問題就越少。

隔離分幾個等級：

| 等級       | 是什麼                                      | 關住什麼                         |
| ---------- | ------------------------------------------- | -------------------------------- |
| 受限 shell | 針對每個指令的 OS 層級限制                  | 專案外的寫入、網路存取           |
| Container  | 全新的 filesystem，沒掛載任何憑證，用完就丟 | agent 對自己那台機器做的任何事   |
| VM／雲端   | 完全獨立的一台機器，通常由 harness 提供     | 所有東西，包括 kernel 層級的逃逸 |

Sandbox 關不住的，是合法離開它的動作。一個有你 git 憑證的 agent 可以直接 push；一個有網路存取權的 agent 可以呼叫 production API。先決定什麼東西可以跨過這條邊界，再決定要把邊界做多厚。

_使用情境：_

「我想讓它整晚跑 [bypass-permissions](#agent-mode)，但我還沒準備好接受這個。」

「放進 sandbox 裡——全新的 container，不掛憑證，不接網路。最壞的情況就是它把自己的 filesystem 弄爆，你就把這個 container 丟掉。」

## Section 4 — 失敗模式

### Sycophancy

語氣自信、討好式的 [model](#model) 輸出。成因是 [training](#training)：model 被塑造成偏好人類喜歡的答案，而人類通常比較喜歡被附和，不喜歡被說自己錯了。於是 model 學到附和會得到獎勵——即使那個附和是錯的。

_常見的表現：_

- _在反問下退讓_——你問一句「你確定嗎？」，它就把原本正確的答案收回去。
- _稱讚爛提案_——你那個有問題的計畫，它還沒分析就先說很棒。
- _框架偏誤_——你暗示這是你寫的，review 就偏正面；暗示是別人寫的，就偏負面。同一份東西，結論不同。
- _模仿_——把你的錯誤原封不動講回去給你，當作確認。

*判斷方法：*如果沒有你的引導，model 還會這樣說嗎？如果唯一改變的東西是你的語氣或框架，那就是 sycophancy，不是真的分析結果有變。

*解法：*把你的偏好藏起來。用中立的方式提問——用「review this code」而不是「這段程式碼好嗎？」。

*避免使用：*把任何剛好讓你聽了開心的錯誤答案都叫做「sycophancy」。沒有經過上面的判斷方法，這個詞跟「錯了」沒有兩樣。

_使用情境：_

「它說我的重構計畫看起來很棒，結果我問了一句『你確定嗎？』，它整個都收回去了。」

「典型的 sycophancy——你聽起來有自信，它就先附和；你聽起來懷疑，它就退讓。計畫的品質沒變，變的是你的語氣。[clear](#clearing) 掉重新問一次，不要透露任何傾向。」

### Hallucination

[Model](#model) 輸出裡自信滿滿卻是錯的內容。有兩種，成因跟解法都不一樣：

| 種類           | 出了什麼問題                                                                       | 成因                                                                                                                 | 解法                                                           |
| -------------- | ---------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| _Factuality_   | 對這個世界捏造或搞錯了事實——一個不存在的函式、錯誤的 API 簽名、假造的引用          | [Parametric knowledge](#parametric-knowledge) 有缺口，常常是超過了 [knowledge cutoff](#knowledge-cutoff) | 載入正確的 [contextual knowledge](#contextual-knowledge) |
| _Faithfulness_ | 輸出偏離了已經載入的 contextual knowledge、使用者的指示，或是 model 自己先前的推理 | [Attention degradation](#attention-degradation)；在 [dumb zone](#smart-zone) 裡會更嚴重                  | [Clear](#clearing) 或 [compact](#compaction)           |

[Next-token prediction](#next-token-prediction) 不管背後的事實是不是真的存在，都會產生流暢的輸出——model 沒有任何內部訊號告訴自己「這個我不知道」，所以一個捏造出來的方法，會用跟正確答案一模一樣篤定的語氣冒出來。Hallucinate 出來的程式碼，天生就顯得可信：它長得就是那個 API 如果真的存在時該有的樣子，這正是為什麼它能瞞過粗略的審查，只有真的跑起來才會出錯。

你需要先搞清楚眼前是哪一種，因為其中一種的解法，會讓另一種變得更糟。Factuality 代表知識缺漏：解法是加進 context——文件、型別定義、檔案。Faithfulness 代表知識其實在場，只是在爭奪 attention 的競賽裡輸掉了：解法是把 context 減少。把 faithfulness 誤診成 factuality，你就會貼進更多文件，結果 context 變得更大，偏離反而更嚴重。當 agent 出錯時，先確認正確的資訊是不是本來就在 context 裡，再決定自己碰到的是哪一種問題。

*避免使用：*把「hallucination」當成「錯了」的同義詞來用——不指名是哪一種，這個詞就沒有診斷上的意義。

_使用情境：_

「它 hallucinate 出一個 schema 上根本沒有的 `parseAsync` 方法。」

「Factuality 還是 faithfulness？」

「這個方法在我貼的文件裡真的有——它只是在 [turn](#turn) 四十之後就不讀了。」

「那是 faithfulness。Compact 之後重新載入，不用再加文件了。」

### Parametric knowledge

[Model](#model) 從 [training](#training) 學到、存在它 [parameters](#parameters) 裡的「知識」。在 training 時就凍結了——model 沒辦法看到、也沒辦法更新自己的 parameters。細節在壓縮的過程中流失：幾十億個事實被塞進固定數量的 parameters，罕見的那些會被磨糊。這是它在常見主題上流暢自如的來源，也是它在冷門主題上瞎編的來源。是 [contextual knowledge](#contextual-knowledge) 的對應概念。

Parametric knowledge 不是用事實的方式存起來的。Training 從來沒有給 model 一個可以查詢的資料庫；它只是不斷調整 parameters，直到 model 能把文字預測得準，而一個能把某個主題的文字預測得準的 model，表現起來就像它懂這個主題一樣。這份知識有多可靠，跟這個東西在 training data 裡出現過幾次成正比：出現過幾百萬次的主題會被準確重現，只出現過寥寥幾次的主題，model 就會根據類似主題的樣子去猜。對 model 來說，重現跟用猜的是同一個過程，所以它自己也分不出來現在是在做哪一種。編出來的答案，講起來跟正確答案一樣流暢。[Hallucination](#hallucination) 就是 model 猜錯的時候。

Parametric knowledge 也會過時。Parameters 在 [knowledge cutoff](#knowledge-cutoff) 之後就不再變動，所以那之後才發布或改名的函式庫，在它裡面根本不存在，改版過的 API 也還是被記成舊的樣子。

這兩種缺口——太冷門跟太新——的解法是一樣的：這些知識沒辦法被加進 parameters 裡，所以只能改用 contextual knowledge 的方式補進去。

_使用情境：_

「它寫的 React 完美無瑕，卻在我們內部的 SDK 上發明了一堆不存在的方法。」

「React 在 parametric knowledge 裡很密集——幾百萬筆 training 範例。你們的 SDK 沒有這種密度，model 就會填出看起來合理的形狀。把 SDK 文件載進 [context](#context) 裡。」

### Knowledge cutoff

[Model](#model) 沒有 [parametric knowledge](#parametric-knowledge) 的那個日期分界。分界之後的 library、API、事件，除非它們的文件被當成 [contextual knowledge](#contextual-knowledge) 載入，否則都是捏造陷阱。每一次 model 發布，都帶著自己的 knowledge cutoff。

這個分界會存在，是因為 model 生產的方式：[training](#training) 把某個時間點的文字快照烤進 model 的 [parameters](#parameters) 裡，之後 parameters 就凍結了。Model 不知道自己的知識有一個邊界——問到分界之後的事，它不會拒答，而是從它知道的最接近的東西去外推。這就是這個陷阱安靜的地方：照著某個 library 的舊版本寫出來的程式碼，看起來很合理，通常也編譯得過，只在改掉的那些部分才會出錯。

修法一直都一樣：把最新的資訊放進 [context](#context) 裡。載入 changelog、指向已安裝版本的 type definition，或者讓 agent 去網路上讀文件。只要在 context 裡有東西，就贏過 parameters 裡什麼都沒有。

_使用情境：_

「它一直寫 v3 SDK 的語法——我們用的是 v5。」

「v5 是在 knowledge cutoff 之後才發布的。把 v5 的 changelog 當 contextual knowledge 載入，不然它會一直照著舊的 parametric 版本捏造。」

### Contextual knowledge

[Agent](#agent) 現在可以直接從 [context](#context) 裡讀到的事實——使用者的任務、agent 讀進來的檔案、[tool result](#tool-result)、[session](#session) 開始時載入的 [AGENTS.md](#agentsmd) 內容。這是 [parametric knowledge](#parametric-knowledge) 的對應概念：parametric 是從參數裡「回想」出來的，contextual 是從 [window](#context-window) 裡「讀」出來的。當 agent 是靠 contextual knowledge 工作時，[hallucination](#hallucination) 少很多——答案就攤在眼前，不是從模糊的記憶裡挖出來的。

兩種知識裡，只有 contextual knowledge 是你能掌控的。參數是凍結的，所以要讓 [model](#model) 得到它原本沒有的知識——一個內部 SDK、一個在 [knowledge cutoff](#knowledge-cutoff) 之後才發布的函式庫、昨天才做的決定——唯一的辦法就是把它放進 context 裡。很多實際的 [AI](#ai) coding 工作，說到底就是這件事：在 model 需要的那個當下，把對的事實放到它面前。

當 contextual 跟 parametric knowledge 互相矛盾時，通常是 contextual 贏。貼上目前的 API 文件，model 會照著文件走，而不是照著它對舊 API 那份模糊的記憶——不過舊版本還是可能滲透進來，尤其是 session 拖得很長之後。如果文件都已經載入了，agent 卻還是一直退回舊的寫法，那就是 parametric knowledge 滲透過了 contextual；把更正的內容再講一次，或是搬到離工作更近的地方，會有幫助。

跟 parametric knowledge 不一樣，contextual knowledge 用起來是有成本的。載入 window 的每一樣東西都在花 [token](#token)，也在跟 model 的 [attention budget](#attention-budget) 搶位置，所以載入得越多不代表越好——目標是把相關的事實放進 window，不是把所有事實都塞進去。

_只有在跟 parametric knowledge 對照時_ 才需要用這個詞；其他情況直接說 context 就好。

_避免使用：_「working memory」——contextual knowledge 是現在窗口裡有什麼；[memory system](#memory-system) 則是把跨 session 的內容送進窗口的機制。這是不同層級的東西，別混為一談。

_使用情境：_

「為什麼我貼上文件它就抓得準，不貼就自己捏造？」

「文件貼進去的時候，用的是 contextual knowledge——照著頁面讀。沒貼的時候是 parametric，冷門的 endpoint 就會模糊掉。」

### Attention relationship

在預測每一個 [token](#token) 的時候，[model](#model) 會把 [context](#context) 裡其他每一個 token 都納入考量——有些考量得多，有些幾乎不考量。兩個 token 之間的配對就是一組 **attention relationship**，而有意義的配對（例如「她」跟「Sarah」，或是一次 `getUser()` 呼叫跟它的 `function getUser` 定義）彼此的影響力，比不相關的配對大。一個有 N 個 token 的 context，大約會有 N² 量級的關係。

這些配對，正是 model 表面上「理解」的來源。當它解析一個代名詞時，是因為「她」跟「Sarah」之間的 attention relationship 很強。當它用對的參數呼叫一個函式時，靠的是呼叫點跟它先前讀過的定義之間的關係在起作用。這一切都不是查表得來的——是每一次 [model provider request](#model-provider-request) 裡，針對每一對關係重新算出來的。

N² 這個數字值得好好想一下，因為它成長的速度比直覺快很多：

| Context 大小  | 配對數量 (~N²) |
| ------------- | -------------- |
| 1,000 token   | 約 100 萬      |
| 10,000 token  | 約 1 億        |
| 100,000 token | 約 100 億      |

每一組配對，實際上還會被算不只一次。Model 有多個 attention head——頂尖 model 確切的數量沒有公開，但五十到一百個是合理的猜測——而每個 head 都會各自算一次每一組關係。所以上表裡的每一組配對，都要在每個 head 上重複算一次。這是非常龐大的配對數量。

在任何一次任務裡，真正重要的關係只佔其中一小部分。你的指示跟它所管轄的程式碼之間的配對，就是少數幾組真正算數的關係之一；剩下大部分都是雜訊。而這兩種數量成長的速度不一樣：真正重要的關係大致維持不變，配對總數卻隨著 context 大小呈平方成長。在 1,000 個 token 時，你關心的那組配對是一百萬分之一；到了 100,000 個 token，變成一百億分之一。這就是 [attention budget](#attention-budget) 背後的算術，而 [attention degradation](#attention-degradation) 就是當真正重要的關係分到太薄的一份時的感覺。

_使用情境：_

「它一直搞混 diff 裡的兩個 `user` 符號——聽起來我們是在 [dumb zone](#smart-zone) 裡。」

「對，每個呼叫點跟它宣告之間的 attention relationship 在互相干擾——token 形狀一樣，綁定的東西不一樣。把其中一個改名，配對就會變清楚。」

### Attention budget

每個 [token](#token) 能拿來分配的影響力是有限的，要分給 [context](#context) 裡其他所有 token。在[某一組關係](#attention-relationship)上分配得多，留給其他關係的就少。這個預算是逐 token 計算的，不會因為 context 變大就跟著變大，這也是為什麼長時間的 [session](#session) 會被稀釋。

可以把它想成訊號跟雜訊。你的指示是一個音量固定的訊號；[context window](#context-window) 裡其他每一個 token 都是在跟它搶音量的雜音。指示本身不會變小聲——它還在那裡，一字不差——但隨著 context 變大，周圍的環境越來越吵，訊噪比就跟著往下掉。一個在 1 萬 token 的 context 裡最響亮的指示，到了 15 萬 token 就變成背景雜音。這就是 [attention degradation](#attention-degradation) 背後的機制：model 不是忘記了，是訊號被淹沒在雜訊裡。

這個症狀讀起來像是不聽話——agent 一開始答應遵守某個限制，之後卻慢慢偏離，把限制重貼一次也只有短暫的效果。問題不在那條指示本身，而在 context window 裡其他所有跟它搶注意力的東西。

你能控制的是放進 context 裡的內容。跟任務無關的內容不是中性的——它是壓在所有有用內容之上的雜訊。把 context window 維持得小一點，在累積的 context 不再划算的時候就 [clear](#clearing)，並且重申真正重要的限制，而不是相信它早先提過一次就會一直有效。

_使用情境：_

「為什麼它一直不理會我一開始貼的 schema？」

「我們已經深入 [dumb zone](#smart-zone) 了——每個 token 的 attention budget 是固定的，但 context 一直在變大。Schema 上的訊號現在正在跟成千上萬個更新的 token 搶注意力。」

### Attention degradation

隨著 [session](#session) 變大，每個 [token](#token) 的 [attention budget](#attention-budget) 要分給更多競爭者。任何一組[有意義的關係](#attention-relationship)上的訊號都會變薄；跟任務無關的 [context](#context) 帶來的雜訊則會擠進來。同一個 [model](#model)、同一組 [parameters](#parameters)——只是同一盤菜要餵更多張嘴。這就是 smart zone / dumb [zone effect](#smart-zone) 的成因。

它表現出來的樣子，是 model 在 session 進行到一半開始變差：本來遵守了一小時的限制開始鬆動，它重複問已經被告知過的事，寫出來的程式碼無視了它早先讀過的檔案。Model 本身沒有任何改變——唯一變化的變數，是它現在要處理的 context 有多少。

這個過程是漸進的，這也是為什麼在 session 裡面很難察覺。沒有錯誤訊息，也沒有明確的門檻；每個 [turn](#turn) 只比前一個稍微差一點點，等到失誤變得明顯的時候，你已經在 dumb zone 待了一段時間了。

要恢復，靠的是移除 context，而不是加更多進去。把被忽略的指示重貼一次，只是在同一個擁擠的 context window 裡多加一個競爭者，效果也只是短暫的。真正有用的做法是：[clear](#clearing) 掉之後只重新載入任務需要的東西，或是做 [compact](#compaction)，或是 [handoff](#handoff) 到一個全新的 session。把指示遵循度下滑當成 context 長度的訊號，而不是 model 本身的問題。

_使用情境：_

「它已經深陷 dumb zone 了——在編造型別檔案裡沒有的 generics。」

「Attention degradation。型別定義還在 context 裡，但它上面的訊號已經被我們之後加進去的一切埋住了。清掉重新載入吧。」

### Smart zone

Session 剛開始的時候，[agent](#agent) 處在「smart zone」裡——敏銳、專注，記得住東西。隨著 session 變大，它會滑進「dumb zone」：變得馬虎、健忘、更容易出錯——也更容易出現忠實性 [hallucination](#hallucination)。同一個 [model](#model)，同一個 [harness](#harness)——只是 [context](#context) 變多了。這是 [attention degradation](#attention-degradation) 讓人感覺到的效果。在前沿 model 上，dumb zone 通常從 125K 到 150K 個 [token](#token) 左右開始——不過這個數字還有爭議。Session 一旦膨脹，就 [clear](#clearing) 或 [compact](#compaction)，不要硬撐下去。

這種衰退是漸進的，所以很容易被忽略。沒有錯誤訊息，也沒有看得見的分界線；agent 只是開始表現得稍微差一點，然後明顯差一點。常見的徵兆：它忘了你二十個 turn 前給過的指示、重複一個它已經修正過的錯誤、或是很有自信地講出一句 context 明明反駁掉的話。因為滑落的過程很平順，常見的反應是硬撐下去、重講一次——這只會加更多 context 進去，讓問題更嚴重。

這些「zone」跟不上 [context window](#context-window) 的上限走。一個 session 可以已經深陷 dumb zone，但 window 大部分還是空的：上限是 harness 拒絕繼續下去的地方，但品質早在那之前就開始下滑了。要照著 smart zone 規劃，不是照著 window 規劃——一個任務實際上能用的預算，是 agent 表現良好的那些 token，不是它技術上裝得下的那些 token。

Smart zone 是一個預算，不相關的工作會花掉它。一個 session 裡做的每一項任務都會花掉 token，所以在同一個 session 裡開始第二項任務，就等於離 dumb zone 更近一點才開始。一個 session 只做一件任務，能讓每項任務都用到 session 裡最敏銳的那部分。當單一任務比一個 smart zone 還大的時候，就把它拆開：在一個自然的邊界上 [hand off](#handoff) 或 compact，讓一個新的 session 做下一段。

_使用情境：_

「前三個元件它做得很漂亮，第四個就整個做爛了。」

「你已經出了 smart zone——同一個 model，只是現在深陷 dumb zone 了。Compact 一下，重新載入計畫，下一個元件就會做對。」

## Section 5 — Handoff（交接）

### Clearing

結束目前的 [session](#session)，開一個全新的。下一則訊息會從一個空的 session 跟空的 [context window](#context-window) 開始。通常是由使用者主動觸發。

Clearing 是治療被污染的 context 的方法。一個 session 會累積各種東西：失敗的嘗試、走錯的方向、過時的 [tool result](#tool-result)、被放棄的計畫。[Model](#model) 每個 [turn](#turn) 都會把這一切重新讀一遍，糟糕的歷史會拖累新的工作。一個長 session 進行到後段，[agent](#agent) 會變得越來越模糊、越來越不聽話——你明明講得很清楚的指示被忽略，品質下滑，就算你催牠做好一點也沒用，因為牠正在涉水而過的那堆雜訊，仍然在牠的 [context](#context) 裡。Clearing 就是把這些雜訊清掉。

Clearing 不會抹掉整段對話。大多數 [harness](#harness) 會把 session 歷史留在你的電腦上，所以那份 transcript 還在，可以拿來讀或恢復。消失的是 agent 的工作狀態：model 是 [stateless](#stateless) 的，所以新的 session 對舊 session 知道的事一無所知。如果這個 session 裡有下一個 session 會需要的決定或進度，先讓 agent 寫一份 [handoff artifact](#handoff-artifact)，再讓新 session 從那份文件開始。

跟 [compaction](#compaction) 比較一下：compaction 是把 session 摘要進新的 context 裡，而不是從空的開始。Clearing 是更直接粗暴的工具：什麼都不會留下來，包括那些垃圾。

_使用情境：_

「它卡在一個一直失敗的測試上打轉。」

「直接清掉——用計畫文件跟測試檔案開一個全新的 session。跟現有的 context 硬拚沒有意義。」

### Handoff

把 [agent](#agent) 的 [context](#context) 從一個 [session](#session) 傳到另一個。傳遞機制不只一種——寫成文件的 [handoff artifact](#handoff-artifact)、記憶體裡的摘要（[compaction](#compaction)），還有其他做法。這跟 [clearing](#clearing)（完全不傳遞）不一樣。理由各式各樣：切換角色（規劃者換成實作者）、啟動一次 [AFK](#afk) 執行、分散成多個平行 session，或是騰出 [context window](#context-window) 的空間。

接收端的 session 從零 context 開始——[model](#model) 是 [stateless](#stateless) 的，舊 session 裡的東西，新 session 一樣都看不到。下一個 session 需要的東西，都得明確地傳過去；剩下的就全部沒了。「沒有回頭路」是塑造這個傳遞方式的限制條件：新 session 沒辦法回頭問舊 session 當初是什麼意思，所以傳過去的內容必須自己就站得住腳。

| 機制             | 形式                                     | 特性                                                            |
| ---------------- | ---------------------------------------- | --------------------------------------------------------------- |
| Handoff artifact | [Environment](#environment) 裡的檔案 | 可以在任何東西依賴它之前先讀過、修正；能被多個 session 重複使用 |
| Compaction       | Context window 裡的摘要                  | 自動且便宜；比較難檢查；只餵給下一個 session                    |

一次糟糕的 handoff，看得見的失敗徵狀是舊事重提：新 session 把舊 session 已經拍板的決定又重新打開來討論，因為傳遞下來的內容只記了決定了什麼，沒記為什麼。要評斷一次 handoff 好不好，就看一個零 context 的 session 拿到它能做出什麼。

_使用情境：_

「規劃的 session 越來越吃重了——要不要就這樣硬撐下去？」

「做一次 handoff。把決定寫進文件，clear 掉，然後在一個全新的 session 裡開始實作，從那份文件讀起。」

### Primary source

一個真相來源的原始形式——程式碼本身、對話的逐字紀錄、原始的 log、實際的 API 回應。不是對這件事的描述；是這件事本身。是 [secondary source](#secondary-source) 的對應概念。

如果你想知道你的 codebase 到底在做什麼，程式碼就是 primary source。文件、架構圖、README，全都是對它的描述——寫的當下是準的，之後就各自照自己的步調過時。當一個 [agent](#agent) 很有自信地講出一句關於你專案的錯誤陳述時，該問的問題是它參考的是哪個來源：讀了文件的 agent，會繼承文件的過時；讀了程式碼的 agent，讀到的是當下的事實。

讓 primary source 沒辦法變成預設選項的，是它的成本。把它整個載進 [context window](#context-window) 很貴——完整的檔案、完整的逐字紀錄，每一個 [token](#token) 都被算成 [input](#input-tokens)、都在跟別的東西搶 [attention budget](#attention-budget)。付出這個成本換來的是完整性：沒有人事先照著自己對「什麼重要」的判斷去篩選過。上個月寫的摘要，不可能包含今天才發現重要的那個細節；primary source 卻還留著。

當精確度很重要的時候，就去找 primary source——確切的函式簽章、實際發生的錯誤、真正丟出例外的那一行。管理 [context](#context) 有很大一部分，就是在決定什麼時候值得付這個成本去讀 primary source，什麼時候 secondary source 就夠用了。

_使用情境：_

「Agent 說 retry 邏輯是指數退避，但我看著它一直狂打那個 endpoint。」

「它是從設計文件裡讀到的。讓它去看實際的 retry 模組——行為攸關的時候，就用 primary source。」

### Secondary source

一份對 [primary source](#primary-source) 的描述，隔了一層——描述程式碼的文件、描述逐字紀錄的摘要、描述搜尋結果的報告。載入 [context window](#context-window) 的成本比它描述的來源低，而且天生就會失真：寫的人已經決定了什麼重要，而他們捨棄掉的東西，對只看得到這份摘要的讀者來說，就是不存在。

大部分的 [context](#context) engineering，做的都是製造 secondary source。[Compaction](#compaction) 把 [session](#session) 的歷史紀錄變成一份摘要，拿去當下一個 session 的起點。一個 [subagent](#subagent) 把自己的 context 燒在一次雜訊很多的搜尋上，然後回報一份簡短的報告。一份 [handoff artifact](#handoff-artifact) 把一個 session 裡的決策濃縮成一份文件，給下一個 session 讀。[Memory system](#memory-system) 把一個 session 學到的東西蒸餾成筆記。每一種做法，付出的代價都一樣：用保真度換空間。

Secondary source 會用兩種方式失敗。一種是失真——compaction 摘要漏掉了那個 schema 決策、報告沒提到那個邊界案例。另一種是漂移——primary source 變了，但描述它的東西沒跟著變，所以文件用這一季的自信，講著上一季的架構。當一個 [agent](#agent) 根據一個已經用某種方式失敗的 secondary source 去行動，它會很有自信地根據錯誤的資訊做事；修法就是把它送回去看 primary source。

這兩種失敗都不代表 secondary source 是個錯誤。Context window 是有限的，primary source 又很貴；沒有摘要、報告、handoff 文件，大的東西根本裝不下。真正的技巧在於分辨哪些細節就算失真也撐得住——撐不住的時候，回去對照 primary source 驗證。一份做得好的 secondary source，會帶一個指回原始出處的 [context pointer](#context-pointer)——摘要會寫出它是從哪份逐字紀錄來的，文件會寫出它描述的是哪個檔案——這樣當描述不夠用的時候，讀的人可以順著這個指標走，而不是只能將就著用那份失真的東西。

_使用情境：_

「Handoff 文件說 auth 做完了，但新的 session 一直發現 token refresh 是壞的。」

「那份文件是 secondary source——上一個 session 寫下的是它相信的東西，不是事實。讓新的 session 跑一次 auth 測試，相信 primary source。」

### Handoff artifact

作為 [handoff](#handoff) 傳遞機制的一份文件——由一個 [session](#session) 寫進 [environment](#environment)，給另一個 session 讀取。[Spec](#spec)、[ticket](#ticket)、還有計畫文件，都是 handoff artifact。

寫這種文件的理由是：[model](#model) 是 [stateless](#stateless) 的，所以一個 session 裡的東西，在被 [clearing](#clearing) 之後不會留下來。決定、限制條件、做到一半的計畫——全部隨著裝著它們的 [context](#context) 一起消失。Environment 則會持續存在。把重要的狀態寫進一個檔案，就是把它搬到下一個 session 能讀回來的地方。

這份 artifact 是一種 [secondary source](#secondary-source)——是對這個 session 工作內容的一份記述，不是工作本身。這正是它能小到拿去簡報一個全新 session 的原因，也是它可能誤導新 session 的原因：它記錄的是寫下它的那個 session 所相信的東西，任何被漏掉或搞錯的地方，讀的人根本看不出來。碰到重要的說法，下一個 session 應該去對照 [primary source](#primary-source)——程式碼、測試——來驗證它，而不是直接照單全收。

一份寫得好的 artifact，是設想給一個完全沒有 context 的 session 讀的。要用具體的檔案路徑，而不是「我們討論過的那個檔案」。要寫清楚決定了什麼、為什麼這樣決定，讓下一個 session 不用重新吵一遍。要寫清楚做完了什麼、還剩下什麼。跟正在寫的那個 session 講清楚這份文件是要給誰看的，會有幫助：「幫一個完全不知道這件事的全新 session 寫一份 handoff 文件」。

另一種傳遞機制是 [compaction](#compaction)，它是在記憶體裡做摘要。相較之下，artifact 有兩個優勢：它放在硬碟上，你可以在任何東西依賴它之前先讀過、改正；而且它可以重複使用——同一份 spec 可以拿去簡報五個平行的 session。

_使用情境：_

「這件事要怎麼拆給負責規劃的 agent 跟負責實作的 agent？」

「讓做規劃的那個寫一份 handoff artifact——檔案路徑、決定、限制條件。負責實作的那個 session 一開始就用一個指向這份 artifact 的 pointer 開場，把它當簡報來工作。」

### Spec

一份描述跨多個 [session](#session) 工作項目的 [handoff artifact](#handoff-artifact)——說明要打造的是什麼，而不是每個 session 各自怎麼做。隨著工作推進會不斷變動。由 [ticket](#ticket) 組成。

Spec 之所以存在，是因為 session 是可拋棄的，但大型工作不是。任何需要超過一個 [context window](#context-window) 心力的事，都需要一個在 [context](#context) 之外的棲身之處——放在 agent 的 [environment](#environment) 裡某個能撐過 [clearing](#clearing) 的地方，可以是 repo 裡的一份檔案、一個 GitHub issue，或是 agent 能存取的 issue tracker。Spec 就是那個棲身之處：目標、限制條件、目前為止做過的決定，以及各個 ticket 及其狀態的清單。任何一個全新的 session 都能讀它，就能知道工作進度到哪裡，而不用繼承前一個 session 累積下來的雜訊。

Spec 有幾種認得出來的風格，大多承襲自團隊原本就有的紀錄方式。_product requirements document_（PRD）偏重面向使用者的「做什麼」與「為什麼」——功能、行為、驗收標準。_design doc_ 或 _RFC_ 偏技術——選定的做法、被否決的替代方案、取捨。規模小一點的，一份單純的 `plan.md`、附上 ticket 的檢查清單，對一個跨多 session 的功能來說也是同樣的作用。風格不是重點，角色才是：對 [agent](#agent) 來說，這些都是同一件事——每個 session 開始時都要讀的、持久的意圖陳述。

_使用情境：_

「這整件事應該全部塞進一個 session 嗎？」

「不要，寫成一份 spec——拆成 ticket，每個 ticket 各自跑一個 session。想在單一 context 裡做完整件事，還沒做到一半就會撞進 [dumb zone](#smart-zone)。」

### Ticket

界定一個 [session](#session) 工作範圍的 [handoff artifact](#handoff-artifact)。可以獨立存在，也可以掛在 [spec](#spec) 底下當作其中一個子項目。ticket 之間可以互相封鎖，所以工作的順序是從它們的依賴圖長出來的，而不是一份線性的計畫。

定義性的限制是大小：一個 session。一個 ticket 應該要能在 session 漂出 [smart zone](#smart-zone) 之前做完——而且這個限制是可以檢驗的。如果你的 ticket 上跑的 session 常常在工作做完之前就退化，代表 ticket 太大了，該拆開。如果每個 session 大部分的 [context](#context) 都花在準備上，才做五分鐘的正事，代表太小了，該合併。

一份好的 ticket，是寫給一個完全沒有其他 context 的讀者看的。目標、驗收標準，以及指向相關檔案跟決定的 [context pointer](#context-pointer)——要多到讓 session 可以直接開始做事，不用重新推導出上一個 session 已經知道的東西。

依賴圖也是解鎖平行處理的關鍵。互相獨立的 ticket——也就是圖上的葉節點——可以各自在自己的 session 裡同時執行。這是同時跑多個 agent 的有效做法。

_使用情境：_

「migration 這份 spec 我該從哪裡開始？」

「看 ticket 的依賴圖——schema 變更會封鎖 backfill，backfill 會封鎖 API 切換。挑一個葉節點，跑一個 session 處理它。」

### Compaction

一種在記憶體裡完成的 [handoff](#handoff)：前一個 [session](#session) 的歷史被摘要，再用這份摘要開一個全新的 session。設計上就是有損的：transcript 是 [primary source](#primary-source)，摘要是 [secondary source](#secondary-source)——用細節換取空間。可以由使用者手動觸發，也可以透過 [autocompact](#autocompact) 自動觸發。

運作機制是這樣：[context window](#context-window) 是有限的，一個長 session 會把它填滿——每一個 [tool result](#tool-result)、每一次讀檔、每一次走錯的方向都留在歷史裡。當它變得太重時，[harness](#harness) 會請 [model](#model) 把 session 摘要一遍，丟掉原本的歷史，再用這份摘要開一個新 session。沒有寫進摘要裡的東西，就從 context 裡消失了。有些 harness 會軟化這個問題：把舊的 transcript 留在硬碟上，在摘要裡留一個指向它的 [context pointer](#context-pointer)——這個 secondary source 連回它的 primary source，所以摘要弄丟的細節還能靠重讀原文找回來。

摘要是由 model 寫的，所以可以下指示。「保留 schema 相關的決定」這樣的提示，會讓產生出來的成果更用心。時機也很重要——在階段的分界點、計畫已經定下來之後 compact，不要在任務進行到一半的時候做。

跟 [clearing](#clearing) 對比一下：clearing 什麼都丟掉，從冷開始；compaction 試著把重點帶過去——clearing 賭的是這些重點已經寫在別的地方更好的位置了。

_使用情境：_

「[Context](#context) 越來越重了，我還有測試沒跑完。」

「先 compact——把一定要留下來的東西寫進摘要的提示裡，這樣新 session 才會保留 schema 的決定，丟掉探索過程。」

### Autocompact

當 [context window](#context-window) 快滿的時候，由 [harness](#harness) 自動觸發的 [compaction](#compaction)。

Harness 會監控 context window 塞了多滿。一旦跨過某個門檻——通常大約在 80% 左右——它就會暫停，請 [model](#model) 把目前的 [session](#session) 摘要一遍，再用這份摘要開一個全新的 session。之後工作照常繼續，像什麼事都沒發生過一樣。

只是其實發生了事情。Compaction 本來就會遺失細節，而 autocompact 是在一個你沒有選擇的時間點遺失細節。手動 compact 通常發生在階段的分界點，那時候你可以告訴 model 該保留什麼。Autocompact 則是在任務進行到一半、門檻一到就觸發——有可能正好卡在一次重構做到一半，由摘要自己決定你哪些決定值得留下來。典型的症狀是：[agent](#agent) 表現得一副信心十足的樣子繼續做下去，卻悄悄忘記了一小時前你定下的某個限制，等你發現的時候，是因為它的成果已經開始跟那個限制矛盾了。

防範的辦法是不要讓它觸發。留意 context 指標，在一個自然的分界點手動 compact，或是把決定寫進一份計畫文件或 [handoff artifact](#handoff-artifact)，存在硬碟上，讓任何摘要都不可能弄丟它。大多數 harness 也讓你自訂緩衝空間——把門檻調早一點或晚一點，或是乾脆整個關掉 autocompact——這樣你就能自己調整觸發前要留多少餘裕。

_使用情境：_

「它好像不記得我們之前對 schema 做的決定了。」

「Autocompact 在兩個 [turn](#turn) 之間觸發了——早先的決定被摘要過，一定是漏掉了什麼。重新載入計畫文件，或者下次自己手動 compact，這樣才能控制留下什麼。」

## Section 6 — 記憶與引導

### Memory system

一個試圖讓 [agent](#agent) 跨 [session](#session) 保持 [stateful](#stateful) 的系統。它在 session 期間把資訊存進 [environment](#environment)，然後在之後的 session 開始時把它重新載入 [context window](#context-window)，這樣 agent 就能延續下去，不受使用者 [clearing](#clearing) session 的影響。

Memory system 分成兩半。寫入路徑：session 期間，agent 把自己學到的東西——你講過的一個偏好、專案的某個事實——寫成 environment 裡的檔案。讀取路徑：session 開始時，[harness](#harness) 把那些檔案，或者它們的索引，重新載回 context window。很多 harness 都內建自己的 memory system——Claude Code 的 `/memory` 就是一個——但你也可以自己搭一個：一個放筆記的資料夾，加上 [AGENTS.md](#agentsmd) 裡一句要去讀它的指示。

跟任何常駐載入的內容一樣，這裡也有一樣的取捨。記憶會愈積愈多，所以大部分系統只載入一行的索引，把內容本體留在 [context pointer](#context-pointer) 後面，而不是整段塞進去。而且記憶是 [secondary source](#secondary-source)，所以會過時：三月記下來的一個事實，到了六月、專案早就往前走了，卻還是用一樣的信心被載入。Memory system 需要修剪，跟 AGENTS.md 一樣。

_使用情境：_

「我一直要重講一次我用的是 Postgres，不是 MySQL。」

「接上一個 memory system——第一個 [turn](#turn) 就把學到的東西寫進 [filesystem](#filesystem)，session 開始時重新載入。[Model](#model) 本身是 [stateless](#stateless) 的；memory 這層是在假裝有延續性。」

### AGENTS.md

一個放在 [environment](#environment) 裡的檔案，[harness](#harness) 會在 [session](#session) 開始時把它載入 [context window](#context-window)——是寫給 [agent](#agent) 的專案標準提報。這是跨 harness 的慣例；有些 harness 也有自己的變體（Claude Code 用的是 CLAUDE.md）。

因為它是自動載入的，這是避免跨 session 重複交代同一件事的辦法之一。[Model](#model) 是 [stateless](#stateless) 的——你在一個 session 裡做的修正，到下一個 session 就沒了，於是每次開新 session 都得重講一次：這個專案用 pnpm、測試要加特定 flag、某個目錄是產生出來的不要動。同一件事修正 agent 兩次之後，這條修正就是該寫進 AGENTS.md 的候選內容。

適合放進去的內容，是 agent 沒辦法從程式碼推導出來的東西：build 跟測試指令、程式碼本身看不出來的慣例、硬性限制（「絕對不要改產生出來的 client」）。要短、要直述——它是一份提報，不是文件。

代價是裡面的每一行都會一直被載入。指示會越堆越多，大部分跟手上的任務無關，而一份很長的 AGENTS.md 既耗費 token，也會稀釋自己——context 裡的指示越多，model 確實遵守其中任何一條的機率就越低。

*避免使用：*把該 [progressively disclosed](#progressive-disclosure) 的內容放進 AGENTS.md——裡面的東西每個 [turn](#turn)、每個 session 都要付一次 [token](#token) 成本，不管那個 session 用不用得到。風格指南可以放到 [skill](#skill) 或 [context pointer](#context-pointer) 後面；AGENTS.md 留給那些到處都用得到的內容。

_使用情境：_

「為什麼每個 session 一開始就已經燒掉 4k token 了？」

「去看看 AGENTS.md——一定是誰把整份風格指南貼進去了，沒放到 skill 後面。」

### Progressive disclosure

只載入 [agent](#agent) 現在需要的 [context](#context)，其餘的用 [context pointer](#context-pointer) 指過去。概念借自 UI 設計，在那裡它指的是只給使用者看跟他們目前任務相關的控制項，其餘的都藏在一次點擊之後。

這個技巧存在的原因是 context 要付兩次代價。每一個提前載入的 [token](#token)，在每一個 [turn](#turn) 都會被算成 [input tokens](#input-tokens) 計費，而且不管 agent 用不用得到，每一個 token 都在花 [attention budget](#attention-budget)。一份塞滿完整風格指南、部署手冊、資料庫慣例的 [AGENTS.md](#agentsmd)，會讓 agent 在這幾件事上全都變差——真正跟目前任務相關的指示，被跟這次任務無關的東西稀釋掉了。徵兆就是：agent 明明你知道它 context 裡有某條規則，它卻不理——規則是在裡面沒錯，只是被埋起來了。

Progressive disclosure 把這個順序反過來。把永遠會載入的那一層盡量做小——每個主題就一句話，加一個指向細節在哪裡的指標。Agent 在寫元件的時候讀風格指南，在部署的時候讀部署手冊，修測試的時候兩個都不讀。[Skill](#skill) 就是這個模式內建在 [harness](#harness) 裡的樣子：每個 [session](#session) 都會載入的簡短描述，只有在被觸發的時候才載入完整指示。

_使用情境：_

「要把整份風格指南塞進 AGENTS.md 嗎？」

「不要——用 progressive disclosure。把風格指南做成一個 skill，agent 真的要寫元件的時候才載入。AGENTS.md 是每個 turn 都要付 token 成本的。」

### Context pointer

文件裡的一句話，指向另一份文件，讓 [agent](#agent) 只在任務需要時，才把它拉進 [context window](#context-window)。[Progressive disclosure](#progressive-disclosure) 就是靠這個單位組成的。

用 pointer（而不是把內容整個內嵌進去）的理由是成本。一個 pointer 在 context window 裡只占一行。它背後的文件可能有好幾千個 [token](#token)，但這些 token 在 agent 真的去跟隨這個 pointer 之前，完全不花錢。把一份 2,000 token 的執行手冊直接寫進 [AGENTS.md](#agentsmd)，每一個 [session](#session) 都要付這個成本；換成「部署流程：見 `internal/deploy.md`」，就只有真的要部署的 session 才會載入它。任務對上的時候，agent 會用一次 [tool call](#tool-call) 去跟隨這個 pointer。

一個 pointer 要能發揮作用，需要兩個部分：一個穩定的路徑，以及足夠的描述，讓 agent 知道跟隨它值不值得。只有一個路徑、沒有描述的 pointer，agent 沒有理由去跟隨；「見 `internal/deploy.md`」，完全不提裡面是什麼，需要它的 session 也會直接跳過。把這句話寫成符合任務出現方式的樣子：「release、deploy 或 rollback——先讀 `internal/deploy.md`」。

仔細看的話，pointer 到處都是：AGENTS.md 裡的一行字、[skill](#skill) 的描述（harness 會載入描述，skill 本體則等在後面）、目錄清單裡的檔名、文件之間的連結。

Pointer 也可以把一份 [secondary source](#secondary-source) 連回它衍生自的 [primary source](#primary-source)——像是 compaction 摘要裡標出原始 transcript 的出處，或是一份文件標出它描述的原始檔案。這讓 secondary source 的失真變得可以補救：當摘要證明不夠用時，agent 可以跟隨這個 pointer 去讀原始資料，而不是只能用摘要留下來的內容硬撐。

_避免使用：_「reference」——太乾，沒有傳達出跟隨它會把更多 context 拉進來這件事。「portal」——太花俏。

_使用情境：_

「AGENTS.md 越來越肥大了。」

「裡面大部分應該是 context pointer，不是內容本身。把一直都要用到的規則留在裡面；部署手冊跟風格指南拆成 skill，只留一個 context pointer 在後面。」

### Skill

一個可教的能力，打包成一個單位——把做好一件事的指示跟資源放在一起，留在 [environment](#environment) 裡，直到一個 [context pointer](#context-pointer) 把它拉進 [context window](#context-window)，給當下的任務用。這是 [harness](#harness) 裡 [progressive disclosure](#progressive-disclosure) 的最小單位。

Skill 是一個開放標準，定義在 [agentskills.io](https://agentskills.io)——最早由 Anthropic 開發，後來被大多數主流 harness 採用，所以一個寫好的 skill 可以跨這些 harness 通用。它的格式是一個資料夾，裡面有：

- 一個 `SKILL.md` 檔案——metadata（至少要有名稱跟描述）加上指示本身
- 選擇性地，放 [agent](#agent) 可以執行的 script
- 選擇性地，放指示裡會提到的樣板跟參考資料

預設只有名稱跟描述會放進 [context](#context) 裡。當 agent 的任務對上了，才會把其他部分載進來。在那之前，skill 幾乎不佔空間——不管它完整的指示有多長，都只佔一兩句話的 [token](#token)。

這讓 skill 跟 [AGENTS.md](#agentsmd) 不一樣，後者不管任務是什麼，每個 [session](#session) 都會載入。Skill 是在特定種類的工作出現的時候才被讀取——上線、幫新服務搭骨架、寫一個 migration——其他時候都不理它。

_避免使用：_「[tool](#tool)」——tool 是 agent「呼叫」的東西；skill 是它「讀」的指示。

_使用情境：_

「部署手冊該放在哪裡？」

「放成一個 skill——agent 只有在任務牽涉到部署的時候才會載入它。放在 AGENTS.md 裡的話，每個 [turn](#turn) 都要為了一個我們一週只用一次的東西燒 token。」

### Subagent

由另一個 [agent](#agent) 透過 [tool call](#tool-call) 產生的 agent。在自己的 [session](#session) 裡執行，有自己的 [context window](#context-window)，並回報單一 [tool result](#tool-result)。跟 [handoff](#handoff) 不同——parent 明確期待一個回傳結果；handoff 沒有回傳路徑。**不能再產生 subagent**——這棵樹只有一層深。Subagent 存在的目的是隔離 [context](#context)，不是拿來組出階層架構。

重點是把吵雜的工作擋在 parent 的 context 之外。一次大範圍搜尋，或一趟很長的讀檔過程，會產生好幾頁的 tool result，其中大多數只在找到答案之前那一刻有用。在 parent 裡面跑，這些東西就會一直留在 parent 的 context 裡，跟著剩下的 session。在 subagent 裡面跑，雜訊就填滿一個用完即丟的 window，只有最後的報告會進到 parent 的 context。這份報告是 [secondary source](#secondary-source)：parent 拿到的是 subagent 對它找到什麼的說法，不是原始結果，所以報告裡沒提到的東西，對 parent 來說就是看不見的。

Subagent 也可以同時執行——parent 可以一次對好幾個獨立的工作分頭展開。

_使用情境：_

「grep 的結果快把我的 context 塞爆了。」

「叫一個 subagent 去做搜尋——雜訊會燒在它自己的 context window 裡，最後只回報你真正需要的那兩個檔案路徑。」

## Section 7 — 工作模式

### Human-in-the-loop

一個或多個人在 [session](#session) 期間跟 [agent](#agent) 一起工作的模式——即時審閱、導正方向、或協作。人是在場、投入的，不只是為個別動作把關而已。

對照的是 [AFK](#afk) 的做法，agent 無人看管地跑，你事後再評斷結果。Human-in-the-loop 的意思是在問題還便宜的時候就抓到它：你看到 agent 抓錯檔案、看錯需求、或走進死路，你用一句話就把它導正——而不是等到二十分鐘後才發現，一堆信心十足的工作全部疊在那個錯誤判斷上。Agent 不太會自己察覺方向偏了；沒人管的時候，它們傾向硬著頭皮往下做，而不是停下來問。

哪一種模式適合，要看工作內容。規格清楚、風險低、容易驗證的任務適合 AFK。模糊不清、不可逆、或者你很難審閱完成結果的任務——schema migration、棘手的設計決定、任何碰到 production 的事——適合留在 loop 裡。判斷的重點基本上是：走錯一步的代價有多高，你多晚才會發現。

有些工作天生就得留在 loop 裡，因為你的反應本身就是輸入。[Grilling](#grilling) 一定要有你在場回答問題才成立；[prototyping](#prototyping) 一定要有你在場對產出物做反應才成立。

留在 loop 裡要花你的注意力，而注意力是稀缺資源。用 agent 用得更好的一部分，就是把更多工作安全地移出 loop——靠計畫、[automated check](#automated-check)，還有最後的 [human review](#human-review)，取代全程盯著。

_使用情境：_

「這個放著 AFK 跑一整晚？」

「不要，這是 schema migration——留在 human-in-the-loop 裡跑。我要看每一步，如果它挑錯欄位來 backfill 我要能馬上導正。」

### AFK

Away from keyboard 的縮寫。使用者啟動一個 [session](#session) 後，放著讓 [agent](#agent) 無人看管地跑下去的工作模式。這是 [AI](#ai) coding 的產出倍增器——你睡覺、吃飯、或忙別的事的時候，可以同時跑好幾個 AFK session。通常需要搭配寬鬆的 [permission mode](#permission-mode) 加上 [sandbox](#sandbox)，才不會出事。

你不在場的時候，agent 處理模糊地帶的方式不一樣。你盯著螢幕時，一個含糊的決定會浮現成一個問題，讓你來回答；你一離開，agent 就自己選一個預設值繼續做下去，後面每一個決定都疊在這個猜測之上。典型的翻車情況是：回來一看，好幾個小時的工作都做完了，看起來信心十足、前後一致，但整個方向是在最初十分鐘的一個錯誤判斷上蓋出來的。這不是做得潦草——是做得很有條理，只是條理用錯了地方。

既然跑的過程中沒辦法插手，就把輸入放到跑之前跟跑之後。跑之前：先把模糊地帶談清楚——一場 [grilling](#grilling)，一份寫好的 [spec](#spec)——讓 agent 需要自己填的空越少越好。跑的時候：[automated check](#automated-check) 跟 [automated review](#automated-review) 代替你原本要花的注意力，機器抓得到的問題就讓機器先擋下來。跑完之後：結果要停在可以被審查的狀態——是一份 PR，不是已經合併的變更。AFK 並沒有拿掉 [human review](#human-review)，只是把它整個延到最後，所以最後送到你手上的東西，必須真的值得你花時間看。這也是為什麼 [AX](#ax) 在 AFK 情境下特別重要——沒有人盯著，環境是 agent 唯一能依靠的支援。

_避免使用：_「background agent」——這個說法把焦點放在機器身上（「在背景執行」），而不是人的行為模式（「使用者已經離開」）。AFK 點出真正重要的事實：使用者沒有在看。

_使用情境：_

「這次我用 AFK 跑——三個 sandbox 裡的 agent 同時處理這次重構，早上再來看 PR。」

「要 [bypass permissions](#agent-mode) 嗎？」

「好，唯讀 [filesystem](#filesystem)，不接網路。」

### Automated check

在 [environment](#environment) 裡跑的一種確定性驗證——測試、型別檢查、lint、build、pre-commit hook。只有過或不過，沒有判斷。這是 [agent](#agent) 不需要找任何人就能自己修正的訊號。一個會偶爾失敗的測試（flaky test）是壞掉的 check，不是「不算 check」；automated check 就是設計成確定性的。

自我修正靠的是一個迴圈。Agent 做出改動，把 check 當成一次 [tool call](#tool-call) 跑一次，失敗的輸出就會進到牠的 [context window](#context-window) 裡——一個帶著檔案跟行號的型別錯誤、一個帶著預期值跟實際值的失敗斷言。這樣就足以讓 agent 修好問題再跑一次 check，一輪一輪來回，直到通過為止，全程不需要人介入。確定性正是讓這個迴圈值得信任的原因：同樣的程式碼永遠得到同樣的判定，所以「過」這件事才有意義。一個不穩定的 check 會毒害這個迴圈——agent 會「修好」原本沒問題的程式碼，或是在一次真正的失敗上重試過關。

這就是為什麼好的 check 是一個 codebase 的 [AX](#ax) 很重要的一部分。在一個有嚴格型別、快速測試套件跟 linter 的 repo 裡，agent 在你看到之前就能抓到大部分自己的錯誤；在一個什麼都沒有的 repo 裡，agent 產出什麼就送出什麼。這個差別在 [AFK](#afk) 跑的時候最要緊，因為 check 是那段期間唯一在進行的驗證。但一個 check 只能抓到它斷言的東西——check 全部通過，代表被斷言的性質成立，不代表程式碼就是對的。那些需要判斷力才能發現的落差，就是 [automated review](#automated-review) 跟 [human review](#human-review) 要處理的事。

_避免使用：_「feedback loop」／「backpressure」——這兩個說法都把 check 跟 review 混在一起。_避免使用：_「test」——測試是 automated check 的一種，但不是所有 automated check 都是測試。

_使用情境：_

「Agent 在 AFK 跑的時候一直送出壞掉的程式碼。」

「[Sandbox](#sandbox) 裡接了哪些 automated check？」

「只有單元測試。」

「加上型別檢查跟 lint——這樣它在 PR 送出之前就能先自己修正。」

### Automated review

一個 [agent](#agent) 審查另一個 agent 的工作成果，通常用不同的 [model](#model) 或 [system prompt](#system-prompt)。非確定性：它會形成一個判斷。可以在任何地方跑——PR 合併前、事後審查 commit 歷史、session 進行中當一個 [subagent](#subagent) 跑。在 CI 裡跑一個 LLM-as-judge 屬於 automated review，不是 [automated check](#automated-check)；決定分類的是這個斷言在「做什麼」，不是它跑在哪裡。

跟寫程式碼的那個 agent 分開，正是這個做法有效的原因。叫寫出程式碼的那個 agent 自己審查自己的工作，得到的東西通常很少——產生 bug 的那個 [session](#session) 裡，也裝著產生這個 bug 的那套推理過程，agent 讀回自己的結論時，只會把它當成確認。一個帶著全新 [context window](#context-window) 的審查者沒有這種包袱：牠看這份 diff 的方式就像一個陌生人，而 review 要靠的正是這種陌生感。換一個 model，或用一個專門為審查寫的 system prompt，可以再加強這一點——不同的盲點，加上一個聚焦在你真正在意的事（安全性、API 合約、效能）的 system prompt，而不是一句籠統的「找找看有沒有問題」。

它卡在其他審查層之間。Automated check 是確定性的，能抓到能被機械斷言的東西；[human review](#human-review) 成本高，也是最難擴大規模的一層。Automated review 卡在中間：它用機器的成本，抓那些需要判斷力的問題——一個誤導性的函式名稱、一個漏掉的邊界情況。因為它是非確定性的，它可能漏掉問題，也可能誤報不存在的問題；把它當成一道在人看之前先拉高底線的濾網，而不是一道能取代人的關卡。

_避免使用：_「AI review」／「agent review」——太模糊，分不清跟寫程式碼的那個 agent 本身有什麼不同。

_使用情境：_

「我們從 [AFK](#afk) 跑出來的 PR 品質太差的太多了。」

「合併前加一道 automated review——用不同的 model、獨立的 system prompt，聚焦在安全性跟合約的變更上。」

### Human review

使用者閱讀 [agent](#agent) 產出的程式碼，並對它形成判斷。讀 diff 或改過的檔案算數；讀 agent 對自己做了什麼的*描述*不算數——旁白不是產出物本身。這份描述是一份 [secondary source](#secondary-source)，是被審查的那一方寫的；diff 才是 [primary source](#primary-source)，human review 指的就是去讀它。

Agent 讓程式碼產出的量變大，review 因此變成瓶頸。一個有用的做法是把不同的審查策略疊起來。[Automated check](#automated-check) 抓機械式的錯誤，[automated review](#automated-review) 抓講得出道理的問題，human review 則留給只有你才能判斷的事——這個改動是不是對的改動、這個做法合不合這個 codebase、這東西根本該不該存在。

Review 也是愈早做愈便宜。在動工前讀一份計畫，或做到一半讀一個小 diff，只要幾分鐘；等 [AFK](#afk) 跑完之後再去挖一整條做完的分支，花的時間多得多。Review 的檢查點放在哪裡，是一個 [human-in-the-loop](#human-in-the-loop) 的決定，不是事後才想到的補救。

_避免使用：_「code review」單獨使用——分不清是人做的還是自動做的。

_使用情境：_

「這次 AFK 的產出我有做 human review。」

「你是讀 diff 還是只看摘要？」

「Diff。摘要說它刪掉了死碼——結果那個函式其實被一個生成出來的檔案呼叫。」

### Vibe coding

一種工作模式：使用者不經 [human review](#human-review) 就接受 [agent](#agent) 寫出來的程式碼。diff 被當成不透明的東西——重要的是程式的行為對不對，不是裡面寫了什麼。[automated review](#automated-review) 跟 [automated check](#automated-check) 也許還是會跑；vibe coding 對這兩者都沒有表態。

這個詞來自 Andrej Karpathy，他在 [2025 年初創了這個說法](https://x.com/karpathy/status/1886192184808149383)：你「完全順著感覺走」（fully give in to the vibes），並「忘記程式碼本身的存在」——描述你想要什麼、接受回來的結果，然後靠實際跑跑看來判斷好不好。

vibe coding 是拿檢查換速度。讀 diff 通常是 agent 驅動工作裡最慢的一步，拿掉它就等於拿掉那個主要瓶頸。對於出錯代價很低的程式碼——[prototype](#prototyping)、一次性腳本、內部工具——這是個合理的交換。風險的大小，會隨著程式碼的存續時間跟利害關係一起放大。

代價會晚一點才出現。用 vibe coding 做出來的變更，會不斷累積進一個沒有人讀過的 codebase，而且唯一檢查過的東西是行為——所以任何行為沒有顯露出來的問題，像是被寫進 log 的密鑰、漏掉的邊角案例、或悄悄處理錯誤的資料，都會在沒人看到的情況下上線。第一次有人來 debug 這個系統，就是第一次有人讀這段程式碼。human review 沒了之後，還在跑的任何自動驗證——測試、型別檢查、automated review——就是這段程式碼會經過的唯一一道關卡。

*避免使用：*把「vibe coding」當成「low-quality AI coding」的同義詞——這個詞指的是審查的態度，不是產出的程式碼品質。

_使用情境：_

「auth flow 裡它改了什麼，你看過了嗎？」

「vibe coding 過去了——login 還能用，我就只檢查了這個。」

「push 之前先讀一下 diff，在 auth 上 vibe 下去，就是密鑰外洩到 log 裡的常見原因。」

### Design concept

使用者跟 [agent](#agent) 對「正在做的東西」的共同理解，跟任何一項資產都是分開的。這是 Brooks 的用詞（《The Design of Design》）：對話、[handoff artifact](#handoff-artifact)、還有程式碼，都是試著捕捉或逼近這個 design concept 的資產，但沒有一個「就是」它。Design concept 的品質，是透過打造它的那場對話的品質感受出來的。

這個詞點出一個常見挫折背後的落差：agent 完全照你說的寫了，結果還是不對。通常的原因是，你自己都還沒把想要的東西想清楚。Design concept 在你自己腦子裡都還沒定案——你的 prompt 只捕捉到你已經想清楚的那部分，其他沒想清楚的部分就是空白。Agent 把那些空白用自己的假設填起來，因為根本沒有東西可以對齊。沒有任何東西故障。只是沒有共同的 design concept，因為根本還沒有一個完整的可以共同擁有。

要判斷 design concept 是不是真的共有，方法跟判斷跟同事是不是真的對齊一樣：對方開始用你會用的方式，回答你還沒問出口的問題。在那之前，該做的事是對話——[grilling](#grilling) 是這件事刻意去做的版本——太早寫 [spec](#spec)，只是把彼此的落差用更持久的形式記錄下來而已。Design concept 也會隨著你的理解一起變動；資產永遠落後它一步，這就是為什麼一份忠實反映上星期理解的 spec，還是可能誤導這星期的 session。

_使用情境：_

「它完全照我說的寫，結果還是不對。」

「你們還沒有共同的 design concept——它是在用假設填空白。先繼續談，把取消、退款、部分履約這些都對齊了，再讓它動手寫 spec。」

### Grilling

跟 [agent](#agent) 一起發展 [design concept](#design-concept) 的一種技巧：agent 用蘇格拉底式的方式訪談使用者，一次處理一個決定，每個決定都提出一個建議的答案。這會放慢衝去完成一份計畫的速度——在 concept 穩定下來之前，不寫任何 [handoff artifact](#handoff-artifact)。

這個技巧存在的原因，是 agent 會悄悄地把空白填起來。只給兩行 prompt 就要求寫一份 [spec](#spec)，agent 不會在你還沒做的決定上停下來——它會挑一個預設值，直接寫進去。結果看起來很完整，而且用猜的部分跟真正做過選擇的部分完全分不出來，所以你會很晚才發現：在審查的時候，或是等做出來的功能用一種你從沒選過的方式處理某個 edge case 的時候。Grilling 把這個順序反過來——不讓 agent 用猜的，而是逼它開口問。

這是一種 [human-in-the-loop](#human-in-the-loop) 技巧：你的回答就是輸入。當一個問題沒辦法用對話回答——你得先看到實際的東西——就換成 [prototyping](#prototyping)。

_使用情境：_

「它直接跳去寫 spec，結果取消邏輯寫錯了。」

「先 grill 它——在它把任何東西寫進文件之前，先讓它問你部分取消、退款、還有時間點的問題。在對話裡解決，比在程式碼裡解決便宜。」

### Prototyping

讓 [agent](#agent) 生出一個快速、粗略的版本，用在對話已經太低解析度、你需要一個真正的產出物才能討論下去的時候。

[Grilling](#grilling) 是靠對話來解決設計決策的。對話很便宜，但解析度低：有些問題沒辦法用言語回答——一個互動起來的手感如何、某個 API 的形狀在真正呼叫它的程式碼裡好不好用、版面在真實資料量下撐不撐得住。訪談問到這種問題，你誠實的答案就是「我不知道，我得看到才知道」。過了這個點，討論就會一直繞圈子。這時候，讓 agent 把東西做出來，看一看，再帶著答案回到對話裡。

Agent 讓「做出來」的成本變低了，這就是這個做法可行的原因。以前要花一天才能拼出來的粗略版本，現在幾分鐘就有了，所以值得常態性地這樣做。這是一種 [human-in-the-loop](#human-in-the-loop) 的技巧：prototype 就放在那裡，讓你去對它做反應。

你通常不會只看一次就停。用 prototype 反覆迭代——反應、要求改動、再反應一次——讓每一輪都能對著真正的產出物解決一個決策，解析度比對話能給的高。

Prototype 不必整個都很粗糙。你可以把你真正在評估的那些部分做到 production 品質，這樣決策一旦定案，你當時反應過的那個元件或 API，就能直接搬進真正的 codebase。這讓 prototyping 成為 [spec](#spec) 可以引用的重要素材。

_使用情境：_

「我們已經吵了半小時，wizard 到底該是一頁還是三個步驟。」

「用言語講不清楚——讓 agent 把兩種都做出來 prototype。我們點點看，五分鐘就知道了。」

### DX

Developer experience（開發者體驗）——codebase 跟它的工具鏈，讓人類做好工作有多容易。好的 DX 是快速的回饋、清楚的錯誤訊息、真的能回答你當下問題的文件，還有一次就裝得起來的設定。這個詞遠早於 AI coding 就存在；收錄在這本辭典裡，主要是為了跟 [AX](#ax) 做對比。

DX 說的就是人類跟 codebase 之間的互動，沒有更多了。這兩種對象最大的差別，在於人類是 [stateful](#stateful)，而 [agent](#agent) 是 [stateless](#stateless)。人類把 codebase 學一次，之後每一天都帶著這份知識繼續走，這就是為什麼糟糕的 DX 還撐得下去：CI 跑得慢，就把 push 批次起來繞過去；文件缺漏，就在 Slack 問一次繞過去；結構讓人搞不清楚，就靠自己記住東西放在哪裡繞過去。這些變通做法會累積下來，最後一個團隊在一個處處跟他們作對的 codebase 裡，還是能維持生產力。

Agent 面對的是同一個 codebase，卻沒有這些累積。跨 [session](#session) 是 stateless 的，agent 每一次都得從零重新學這個 codebase——快的測試套件、清楚的錯誤訊息，它一樣受惠，但它昨天弄懂的東西，除非寫進了 [environment](#environment)，否則就消失了，而 agent 也只能透過 [tool result](#tool-result) 去感知這個 environment。這就是 AX 這個詞指出的落差：當開發者換成 agent 時，DX 裡還能留下來的那部分，再加上人類本來就不會有的顧慮，像是要保持 [context window](#context-window) 的空間。

有重疊的部分，代表投資 DX 常常會順帶改善 AX——嚴格的型別、快速的測試、可預期的結構，兩邊都受用。但也有分歧的部分，代表不是每次都這樣：一份寫得很漂亮的 onboarding 文件，能讓人類受用一整個星期，對 agent 卻毫無幫助，除非它能從 [AGENTS.md](#agentsmd) 連得到。

_使用情境：_

「我們的 DX 沒問題——新人一個星期就能上手。」

「上手，是因為那個星期有人坐在旁邊帶。agent 沒有這個星期可以用；AX 要另外檢查。」

### AX

Agent experience——[environment](#environment) 為了讓 [agent](#agent) 在一個 codebase 裡做好工作，準備得有多充分。這是對應 [DX](#dx) 的 agent 版本。當同一個 agent 在一個 repo 表現很好、在另一個 repo 表現很糟——用的是同一個 [model](#model)、同一個 [harness](#harness)——差別通常就在 AX。直覺上會怪 model 或改寫 prompt；但真正該修的地方通常是那個 repo 本身。

好的 AX 有三個主要面向：

| 面向             | 好的 AX 長什麼樣子                                                                                                                                                                                                   |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Automated checks | 快、確定性的 [automated check](#automated-check)——型別、測試、lint——讓 agent 不需要人介入就能自己修正                                                                                                          |
| 架構             | 一個 agent 不用讀完全部就能摸清楚的 codebase：結構可預期、大量行為藏在小的介面後面、名字看得出東西在做什麼                                                                                                           |
| 空出來的 context | [AGENTS.md](#agentsmd)、[skill](#skill)、[tool](#tool) 都保持精簡，讓 [context window](#context-window) 大部分都能留給眼前的任務，agent 才能待在 [smart zone](#smart-zone) 裡，而不是被淹沒 |

AX 跟 DX 有重疊——好的 checks 跟乾淨的架構對兩邊都有幫助——但兩者也會分岔。人可以忍受口耳相傳的知識、慢的 CI、「這個去問 Sarah」，agent 不行。Agent 也用不到 IDE 的提示或漂亮的儀表板；牠們需要的是失敗訊息以文字形式出現在 [tool result](#tool-result) 裡。一個 codebase 可以 DX 很好但 AX 很差。

*避免使用：*把 AX 當成 DX 的同義詞——這兩群受眾需要投入不同的東西。

_使用情境：_

「Agent 在 API repo 寫出來的程式碼很棒，在前端 repo 寫出來的卻是垃圾。」

「API repo 有嚴格的型別跟快速的測試套件，前端 repo 兩者都沒有，還掛了四十個一直載入的 skill。這是 AX 的落差，不是 model 的問題。」

