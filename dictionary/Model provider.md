---
description: 提供 model 做 inference 的服務。通常是遠端（Anthropic、OpenAI、Google），但也可以是本機（Ollama、llama.cpp）。
---

不管是什麼東西在幫 [model](./Model.md) 做 [inference](./Inference.md)。通常是一個遠端服務（Anthropic、OpenAI、Google），但也可以是本機——Ollama、LM Studio、llama.cpp 跑在你自己的機器上。[Harness](./Harness.md) 不會自己跑 model；它是去請一個 provider 幫忙跑。

Provider 擁有整套機器：[parameters](./Parameters.md) 就放在它的硬體上，每一次 [model provider request](./Model%20provider%20request.md) 都是 harness 把 [token](./Token.md) 送過網路，再拿回預測結果。這使得 provider 變成一整類問題的源頭，而這些問題常常被誤怪到 model 或 harness 頭上——rate limit、容量降級、斷線，全都是這一層的事。當 [agent](./Agent.md) 卡在一半的 [session](./Session.md)，或者每個 [turn](./Turn.md) 都出錯，最先該查的是 provider 的狀態頁。

Provider 也訂了商業條款：[input](./Input%20tokens.md) 跟 [output token](./Output%20tokens.md) 各自的計費單價、[prefix cache](./Prefix%20cache.md) 的折扣，還有到底有哪些 model 可以用。要注意的是，provider 跟做出這個 model 的公司可能不是同一家——Bedrock、Vertex、OpenRouter 提供的都是別人做的 model。

Local provider 是拿能力換控制權：塞得進你自己硬體的 model，遠比 frontier 等級的小得多，但東西不會離開這台機器，也沒有按 token 計費的帳單。

_使用情境：_

「能不能幫這個 air-gapped 的客戶跑離線版？」

「把 model provider 換成本機的——他們的機器上跑 Ollama 或 llama.cpp。Harness 不在乎，反正它只是打一個不同的 endpoint。」
