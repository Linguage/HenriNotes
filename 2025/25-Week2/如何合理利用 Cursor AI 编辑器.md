如何合理利用 Cursor AI 编辑器  
  原文标题：Cursor 弃之可惜，食之无味？  
  链接：https://baoyu.io/blog/cursor-use-or-discard

- **文章类别**：博客

---

**内容整理**：

这篇文章讨论了如何合理使用 Cursor 这类 AI 编辑器，以及人们对其的不同态度和使用方法。文章通过具体的例子和建议，帮助读者更好地理解如何在编程中利用 AI 工具。

### 背景与态度
- **用户态度**：对于使用 Cursor 这类 AI 编辑器，用户的态度有三种：
  - **非常依赖**：觉得非常好用，离不开它。
  - **完全不用**：要么嫌贵，要么认为会产生依赖心理，不利于技术成长。
  - **想用但觉得不好用**：认为“弃之可惜，食之无味”。

### 具体案例
- **网友 Tang 的分享**：
  - **担忧**：Tang 主要写后端代码，担心 AI 生成的代码在计算金额等关键部分出错，不放心直接使用。
  - **解决方案**：
    - **使用 Git 管理版本**：每次使用 Cursor 之前先 Commit，以便清晰跟踪和 Review AI 的变更。
    - **代码 Review**：像团队协作时一样，对 AI 生成的代码进行 Review，确保安全。
    - **单一任务**：每次任务尽量单一，便于 Review。
    - **AI 写测试代码**：利用 AI 擅长的测试代码生成能力，通过大量自动化测试覆盖各种场景，确保代码质量。

### 其他观点
- **同学的使用情况**：
  - **不使用原因**：需要实现的金融逻辑 AI 没有训练过，使用效果不佳。
  - **解决方案**：通过在提示词中详细描述规则，配合 AI 生成符合规则的代码，并辅以充足的测试代码.

### 结论与建议
- **AI 的局限性**：现阶段 AI 确实有其局限性，没有网上吹嘘的那么厉害。
- **合理利用**：不建议因为期望与现实的落差而放弃使用 AI，而是要找到适合的使用场景，发挥其优势。
- **积极态度**：如果认定 AI 能提升效率，遇到困难应想办法克服，而不是找借口不去用它.