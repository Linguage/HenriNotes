深入解析大模型LLMs的Token及其成本流向
- 原文标题：一文说清楚什么是大模型LLMs的Token,全面了解钱的流向
- 链接：[一文说清楚什么是大模型LLMs的Token,全面了解钱的流向](https://mp.weixin.qq.com/s?__biz=MzI4MjE1Nzc2MQ==&mid=2649035008&idx=1&sn=a2e92d4f3beadcc1d86f6f8a2313580d&scene=21#wechat_redirect)

- **文章类别**：博客

---
**内容整理**： 

本文主要介绍了大语言模型（LLMs）中的Token概念及其在OpenAI API中的成本流向。文章通过多个实例详细解释了Token的生成方式、特殊情况以及中英文Token处理的差异。

### OpenAI API Token的报价
文章首先列出了OpenAI不同模型的Input和Output价格，具体如下表所示：

| 模型          | Input价格       | Output价格      |
|---------------|-----------------|-----------------|
| gpt-4o        | $0.00250 / 1K tokens | $0.01000 / 1K tokens |
| gpt-4o-mini   | $0.000150 / 1K tokens | $0.000600 / 1K tokens |
| gpt-4-turbo   | $0.0100 / 1K tokens  | $0.0300 / 1K tokens  |
| gpt-3.5-turbo-1106 | $0.0010 / 1K tokens | $0.0020 / 1K tokens |

### 什么是Token
文章指出，大语言模型（LLM）并非简单地预测下一个单词，而是预测下一个Token。Token可以被视为单词的片段，通过分词器将句子拆分为一个个Token，从而降低字典规模，提高模型训练和推断的效率。例如，句子"Learning new things is fun!"中的每个单词都被转换为一个Token。通常，1个Token约等于4个字符（英语）或四分之三个单词，100个Token约等于75个单词。

### Token的特殊情况
文章还讨论了Token的一些特殊情况，包括：

- **相同单词的Token不一样**：两个看似相同的单词可能根据它们在文本中的结构生成不同的Token。例如，"red"和"Red"（首字母大写且带有前导空格）会生成不同的Token。
- **一个单词拆成多个Token**：某些单词可能会被拆分成多个Token。例如，"lollipop"可能会被拆分为"l"、"oll"、"ipop"三个Token。这会影响语言模型对单词的理解和处理。

### 中文Token的生成方式
现代LLM通常采用基于子词单元的Token化方式，如BPE（Byte Pair Encoding）或SentencePiece。BPE将文本切分为子词单元，并按频率统计对子词进行合并；SentencePiece则将所有输入文本视为一个字节流，包括空格和标点符号。BPE类似于搭积木，先拆开再按频率合并；SentencePiece则像切蛋糕，从整体出发找到切分点。

### GPT系列大模型处理中文Token举例
GPT系列模型使用BPE分词。对于中文文本，BPE通常以单字为基础单元，再逐步合并常见的子词单元。例如，输入"我爱中国"，分词结果可能是["我", "爱", "中", "国"]或["我", "爱", "中国"]。BPE会优先选择词频更高的子词。如果训练语料中“中国”作为一个整体出现得更频繁，那么BPE会将其视为一个整体；否则会分解为“中”和“国”。

### 结论
文章通过具体实例和详细解释，帮助读者全面理解了大语言模型中的Token概念及其在OpenAI API中的成本流向。了解Token的生成方式和特殊情况对于开发者在使用大语言模型时优化性能和控制成本具有重要意义。