Anthropic API 引入引用功能：提升 AI 输出的可验证性和可信度  
- 原文标题：Introducing Citations on the Anthropic API  
- 链接：[https://www.anthropic.com/news/introducing-citations-api](https://www.anthropic.com/news/introducing-citations-api)  

- **文章类别**：新闻报道  

---

**内容整理**：

# Anthropic API 引入引用功能：提升 AI 输出的可验证性和可信度

## 文章框架

```markdown

├── 引言
│   ├── 功能介绍：Citations 功能上线
│   └── 可用平台：Anthropic API 和 Google Cloud 的 Vertex AI
├── 核心功能：通过引用提升可信度
│   ├── 传统方法的局限性
│   └── Citations 的优势：自动引用，提升准确性
├── 应用场景
│   ├── 文档总结
│   ├── 复杂问答
│   └── 客户支持
├── 工作原理
│   ├── 文档处理：分块处理
│   └── 引用生成：基于上下文和查询生成引用
├── 定价模式
│   ├── 标准基于令牌的定价
│   └── 输出引用文本不收费
├── 客户案例
│   ├── Thomson Reuters：法律和税务知识平台 CoCounsel
│   └── Endex：金融领域自主代理
└── 使用指南
    ├── 支持的模型：Claude 3.5 Sonnet 和 Claude 3.5 Haiku
    └── 文档链接
```

## 文章要点

### 引言
- Anthropic 推出了 Citations 功能，允许 Claude 在生成回答时引用源文档中的具体句子和段落。
- Citations 功能已在 Anthropic API 和 Google Cloud 的 Vertex AI 上全面推出。

### 核心功能：通过引用提升可信度
- **传统方法的局限性**：开发者以往依赖复杂的提示词来让 Claude 包含源信息，但这种方法效果不稳定，且需要大量时间进行提示词工程和测试。
- **Citations 的优势**：用户可以将源文档添加到上下文窗口中，Claude 会自动在输出中引用这些文档中的内容，内部评估显示其引用能力比大多数自定义实现更优，召回准确率提升高达 15%。

### 应用场景
- **文档总结**：生成长文档（如案例文件）的简洁总结，每个关键点都链接回原始来源。
- **复杂问答**：在大量文档（如财务报表）中提供详细答案，每个回答元素都追溯到相关文本的具体部分。
- **客户支持**：创建支持系统，通过引用多个产品手册、常见问题解答和支持工单来回答复杂查询。

### 工作原理
- **文档处理**：启用 Citations 功能后，API 会将用户提供的源文档（PDF 和纯文本文件）分块为句子，然后将这些分块的句子与用户提供的上下文和查询一起传递给模型。
- **引用生成**：Claude 分析查询并生成包含精确引用的回答，引用的文本会参考源文档，以减少“幻觉”现象。

### 定价模式
- Citations 使用标准的基于令牌的定价模型。虽然处理文档可能需要额外的输入令牌，但用户无需为返回引用文本本身的输出令牌付费。

### 客户案例
- **Thomson Reuters**：使用 Claude 为其法律和税务知识平台 CoCounsel 提供支持，Citations 功能使其更容易构建、维护和部署引用和链接到原始来源的能力，增强了 AI 生成内容的信任度。
- **Endex**：使用 Claude 为金融公司提供自主代理，Citations 功能将源“幻觉”和格式问题从 10% 降至 0%，并将每条回答中的引用数量增加了 20%，提高了复杂多阶段金融研究的准确性。

### 使用指南
- Citations 功能现已支持新的 Claude 3.5 Sonnet 和 Claude 3.5 Haiku 模型，用户可以通过 [Anthropic 文档](https://docs.anthropic.com/en/docs/build-with-claude/citations)了解如何开始使用。

## 文章标签
#Anthropic ， #Citations ， #AI可信度 ， #API功能
