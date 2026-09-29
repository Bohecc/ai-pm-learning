# 02 01 Token Embedding Transformer 与 Attention

## 学习目标

- 理解 LLM 生成回答的基本链路。
- 区分 Token、Embedding、Transformer 和 Attention 的职责。
- 知道这些概念的边界，不把技术类比误当作严格事实。

## 1. LLM 最核心的生成机制

大语言模型（LLM）的直接生成机制可以概括为：

> 根据已经看到的内容，计算下一个最可能出现的 Token 的概率，并逐步生成回答。

它不是数据库，也不是搜索引擎。它会利用训练中学到的语言模式生成连贯内容，因此可能生成没有可靠依据的错误信息。

## 2. Token

Token 是模型处理文本的基本单位。它不等于字数，也不完全等于单词数；具体切分方式取决于模型使用的分词器。

Token 会影响：

- 上下文窗口容量；
- 输入和输出成本；
- 响应速度与生成时长。

## 3. Embedding

Embedding 是把 Token 或其他内容转换成数字向量表示，使模型能够进行计算。

在 LLM 内部，Embedding 的第一作用是将 Token 转为可处理的数字表示。

在知识库/RAG 中，Embedding 还有另一种常见用途：将用户问题和资料片段转换成可比较的向量，用于寻找语义相近的资料。

这两种用途相关，但不要混为“Embedding 就是检索”。

## 4. Transformer

Transformer 是许多现代 LLM 使用的一类神经网络架构。它的核心作用是处理多个 Token 之间的上下文关系。

生成式 LLM 在预测下一个 Token 时，不能查看未来尚未生成的内容；但它可以利用已经出现的多个 Token 建立关系，而不仅依赖紧挨着的前一个词。

## 5. Attention

Attention 是 Transformer 中的重要计算机制。通俗理解：处理当前 Token 时，模型会动态衡量它与上下文中其他 Token 的关联强弱。

例如：

> 小王把书放在桌上，因为它太重了。

模型需要判断“它”更可能指向“书”而非“桌子”。Attention 有助于建立这类上下文关联。

注意：Attention 是数学计算机制，不等于人类真正的注意、意识或理解；也不能单独将 Attention 权重当成可靠的因果解释。

## 6. 一条可复述的基础链路

> 文本先被切分为 Token；每个 Token 被转换成数字向量 Embedding；Transformer 利用 Attention 等机制处理 Token 之间的上下文关系；模型据此计算下一个 Token 的概率分布，生成一个 Token 后重复该过程，最终形成回答。

## 产品意义

- 模型输出流畅，不等于事实正确。
- 输入越长，会消耗更多 Token，通常带来更高成本和更长延迟。
- 长上下文并不是万能记忆，仍需要检索、筛选和评测。

## 小测试

1. Token 和字数是否完全相等？它影响哪些产品问题？
2. Embedding 在 LLM 输入处理中与 RAG 检索中分别起什么作用？
3. Transformer 与 Attention 的关系是什么？
4. 请复述 LLM 的基础生成链路。

## 参考答案

1. 不完全相等；影响上下文容量、成本和速度。
2. 前者将 Token 表示为数字向量；后者帮助比较问题和资料的语义相似度。
3. Transformer 处理上下文关系；Attention 动态衡量当前 Token 与其他 Token 的关联强弱。
4. 见本节第 6 部分。

## 验收标准

- [ ] 能区分 Token、Embedding、Transformer、Attention。
- [ ] 不把 LLM 误认为数据库或搜索引擎。
- [ ] 能用自己的话复述基础生成链路。

