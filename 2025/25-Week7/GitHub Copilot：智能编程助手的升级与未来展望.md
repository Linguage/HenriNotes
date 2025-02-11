GitHub Copilot：智能编程助手的升级与未来展望  
- 原文标题：GitHub Copilot: The agent awakens  
- 链接：https://github.blog/news-insights/product-news/github-copilot-the-agent-awakens/  

- **文章类别**：博客  

---

**内容整理**：

### 文章框架
```
├── 引言
│   ├── GitHub Copilot的初衷与目标
│   └── 2025年2月的升级内容概述
├── Agent模式预览
│   ├── Agent模式的功能
│   ├── 示例：构建马拉松训练Web应用
│   └── 如何启用Agent模式
├── Copilot Edits正式发布
│   ├── Copilot Edits的功能与优势
│   ├── 双模型架构
│   └── 用户体验与反馈
├── Project Padawan：SWE代理的未来展望
│   ├── SWE代理的定义与功能
│   ├── Project Padawan的工作原理
│   └── 对开发流程的影响
└── 结语
    ├── 未来展望
    └── 用户参与与反馈
```

### 文章内容

#### 引言
GitHub Copilot自2021年推出以来，旨在通过AI辅助编程帮助开发者更高效地编写代码。它不是取代开发者，而是作为“副驾驶”协助完成任务。2025年2月，GitHub Copilot进行了重大升级，引入了Agent模式，并宣布Copilot Edits正式发布。

#### Agent模式预览
Agent模式是GitHub Copilot的一项新功能，能够自动迭代代码、识别错误并自动修复。它还可以建议终端命令并请求用户执行，分析运行时错误并自我修复。Agent模式不仅处理用户请求的任务，还能推断出未明确说明但必要的子任务，并自动完成它们。

- **示例**：GitHub Copilot可以自动构建一个用于跟踪马拉松训练的Web应用，包括生成代码、修复错误并提出终端命令。
- **启用方法**：用户需要下载VS Code Insiders，并在GitHub Copilot Chat中启用Agent模式设置。

#### Copilot Edits正式发布
Copilot Edits结合了聊天和内联聊天的优势，允许用户通过自然语言指定文件编辑需求，并在多个文件中进行内联更改。它利用双模型架构，包括基础语言模型和推测解码端点，以提高编辑效率和准确性。

- **功能与优势**：
  - 用户可以在VS Code中直接接受或拒绝建议的更改。
  - 支持多种语言模型，包括OpenAI的GPT-4o、Anthropic的Claude 3.5 Sonnet和Google的Gemini 2.0 Flash。
  - 支持语音交互，使编程体验更加自然流畅。
- **用户体验**：用户可以在编辑代码时保持流畅的工作流程，同时通过Copilot Edits进行快速迭代。

#### Project Padawan：SWE代理的未来展望
Project Padawan是GitHub Copilot的未来版本，将允许用户直接将问题分配给Copilot，生成经过测试的拉取请求，并与人类审查者协作解决反馈。它将通过安全的云沙盒环境自动处理任务，包括克隆仓库、设置环境、分析代码、编辑文件和运行测试。

- **工作原理**：Copilot会自动启动一个安全的云沙盒环境，异步克隆仓库、设置环境、分析代码、编辑文件，并运行测试。它还会考虑问题或拉取请求中的讨论以及仓库中的自定义指令。
- **对开发流程的影响**：开发者可以将更多时间用于高价值工作，而将重复性任务交给Copilot处理。

#### 结语
GitHub Copilot的升级将改变开发者的工作方式，使编程更加高效和自然。Agent模式和Copilot Edits的推出，以及Project Padawan的未来展望，都表明GitHub致力于通过AI技术提升开发体验。用户可以通过VS Code Insiders和GitHub Copilot Chat的预发布版本体验这些新功能，并提供反馈。

### 文章标签
#GitHubCopilot ， #AgentMode ， #CopilotEdits ， #AIProgrammingAssistant