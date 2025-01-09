N-Gram模型与自然语言处理入门
- 原文标题：入门GPT（一）| N-Gram 带你了解自然语言处理（1）
- 链接：[文章链接](https://mp.weixin.qq.com/s/itcpsLv6x-4Thk9B2-BtTQ)

- **文章类别**：博客

---

**内容整理**：

本文是一篇关于自然语言处理（NLP）入门知识的博客文章，主要介绍了N-Gram模型的基本概念、定义、实现过程、优缺点以及应用场景，并简要提及了GPT模型与N-Gram模型的关系。以下是文章的详细内容梳理：

### N-Gram模型与自然语言处理入门

#### 1. N-Gram模型的重要性
文章指出，理解N-Gram模型是学习概率语言模型的基础，也是深入理解现代语言模型（如GPT）的重要前奏。GPT的核心思想正是对N-Gram思想的深度拓展和优化。因此，学习N-Gram模型是迈向GPT的第一步。

#### 2. GPT模型简介
- **GPT（Generative pre-trained transformer）**：基于transformer的生成式预训练模型，是一个人工智能语言模型系列。
- **ChatGPT**：由OpenAI开发的聊天机器人/生成式预训练transformer模型。

#### 3. N-Gram模型的基本概念
- **定义**：N-Gram模型通过将文本分割成连续的N个词的组合（即N-Gram），来近似地描述词序列的联合概率。第N个词出现的概率依赖于它前面的N-1个词的词序列。
- **基本思想**：利用有限的上下文信息（N-1个词）来近似地预测下一个词的概率。

#### 4. N-Gram模型的定义
- **Unigram（一元组）**：1个词为一组，假设每个词的出现概率互不相关，只与当前单词本身有关。
- **Bigram（二元组）**：2个词为一组，假设每个词只依赖于它前面的一个词（n-1）。
- **Trigram（三元组）**：3个词为一组，假设每个词只依赖于它前面的两个词（n-1）。

#### 5. N-Gram模型的实现
- **条件概率估计**：通过训练语料中的频率统计近似得到条件概率。
  - **公式**：\[ P(w_i | w_{i-1}, w_{i-2}, \ldots, w_{i-n+1}) \approx \frac{C(w_{i-n+1}, w_{i-n+2}, \ldots, w_i)}{C(w_{i-n+1}, w_{i-n+2}, \ldots, w_{i-1})} \]
  - **解释**：分子是词对在语料中的共现次数，分母是前缀的出现次数。

#### 6. N-Gram模型的构建过程
1. **文本分割**：将给定的文本分割成连续的N个词的组合（N-Gram）。
2. **统计词频**：统计每个N-Gram在文本中出现的次数。
3. **计算条件概率**：利用条件概率公式计算给定前N-1个词时，下一个词出现的概率。
4. **预测与生成**：使用这些概率来预测文本中下一个词出现的可能性，多次迭代可以生成整个句子。

#### 7. “词”的定义
- **英文**：可以指单词、字符或子词（Subword）。
- **中文**：可以指词、短语或字。
- **子词分词算法**：将单词切分成更小的部分，以便更好地处理未登录词、拼写错误和词汇变化等问题。例如，英文单词"embedding"可以切分为["em", “bed”, “ding”]。

#### 8. 优点
1. **简单高效**：易于实现，计算成本低。
2. **广泛适用**：可用于分词、文本生成等NLP任务。
3. **灵活性**：可以根据任务调整n的大小以平衡复杂度和性能。

#### 9. 缺点
1. **数据稀疏性**：对于较大的n，数据中的某些N-Gram可能没有出现过，导致概率为零。
2. **上下文局限**：只能捕获有限长度的上下文，不能理解长距离依赖关系。
3. **维度增长**：随着n增大，存储n-gram的参数数量会显著增加。

#### 10. 应用场景
1. **拼写检查**：根据上下文判断一个单词是否拼写正确。
2. **机器翻译**：利用目标语言的N-Gram模型生成更流畅的翻译结果。
3. **文本生成**：用训练好的N-Gram模型生成新的句子。

#### 11. 参考资料
- [一文说清楚什么是大模型LLMs的Token,全面了解钱的流向](https://mp.weixin.qq.com/s?__biz=MzI4MjE1Nzc2MQ==&mid=2649035008&idx=1&sn=a2e92d4f3beadcc1d86f6f8a2313580d&scene=21#wechat_redirect)
- [GPT图解大模型是怎么构建的](https://mp.weixin.qq.com/s?__biz=MzI4MjE1Nzc2MQ==&mid=2649035008&idx=1&sn=a2e92d4f3beadcc1d86f6f8a2313580d&scene=21#wechat_redirect)

#### 12. 往日文章推荐
- [LangChain实战 | OutputParser：让大模型输出从 “鸡肋” 变 “瑰宝” 的关键！](https://mp.weixin.qq.com/s?__biz=MzI4MjE1Nzc2MQ==&mid=2649036728&idx=1&sn=1414a16017e7ad12255171147e0c788f&scene=21#wechat_redirect)
- [国产之光，DeepSeek V3大模型既便宜又好用，惊艳世界AI圈](https://mp.weixin.qq.com/s?__biz=MzI4MjE1Nzc2MQ==&mid=2649036762&idx=1&sn=f2a1744bc0fe16165e65a976d5ba888d&scene=21#wechat_redirect)
- [从0到1开发AI Agent（七）| Plan-and-Execute 如何解决AI复杂任务](https://mp.weixin.qq.com/s?__biz=MzI4MjE1Nzc2MQ==&mid=2649036387&idx=1&sn=d42f6914d7a0ffb171e9eeb18f82de23&scene=21#wechat_redirect)

