


<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" class="logo" width="120"/>

# 如何编写 claude.md 文件？

编写 `CLAUDE.md` 文件是充分利用 Claude Code 的一项关键实践。可以将其看作是专门为人工智能代理[^1][^3]准备的一套指令或项目指南。通过提供关于项目的清晰、结构化的信息，您可以帮助 Claude 理解上下文、遵循约定，并更准确、高效地执行任务[^1]。

### `CLAUDE.md` 的核心目的

`CLAUDE.md` 是一个特殊的 Markdown 文件，每当您在代码仓库中启动会话时，Claude Code 都会自动读取并将其纳入上下文[^1]。它的主要功能是记录：

*   **项目背景**：项目的目的、技术栈和架构[^7]。
*   **关键命令**：用于构建、代码检查和测试项目的 Shell 命令[^1][^2]。
*   **编码规范**：风格指南、命名约定和必需的格式[^1][^5]。
*   **工作流程**：关于测试、创建拉取请求或处理 Git 分支的说明[^1]。
*   **仓库特定怪癖**：项目特有的任何异常行为或设置要求[^1]。

### 如何创建和使用 `CLAUDE.md`

您可以通过多种方式和在不同位置创建 `CLAUDE.md` 文件：

1.  **自动初始化**：最简单的方法是在您的项目目录中运行 `/init` 命令[^2][^6]。Claude 会分析您的代码库——查看像 `package.json` 这样的文件，甚至其他工具（如 Cursor 或 GitHub Copilot）的规则——并为您生成一个具有良好起点的 `CLAUDE.md` 文件[^5]。
2.  **手动创建**：您可以手动创建该文件。将其放置在以下任一位置最为有效[^1]：
    *   **项目根目录**：最常见的位置。将此文件检入 Git 可以让整个团队受益于相同的指令[^1]。
    *   **父目录或子目录**：对于单体仓库（monorepos）很有用，根目录的 `CLAUDE.md` 可以提供通用规则，而子目录文件可以添加更具体的上下文[^1]。
    *   **主文件夹**：位于 `~/.claude/CLAUDE.md` 的文件将全局偏好设置应用于您所有的 Claude Code 会话[^1]。

### 您的 `CLAUDE.md` 文件中应包含哪些内容

一个好的 `CLAUDE.md` 文件应该是简洁、易于人类阅读且结构清晰的[^1]。考虑包含以下部分：

*   **仓库概览**：项目目的和目标的简要总结[^7]。
*   **技术栈**：使用的主要语言、框架和库[^7]。
*   **常用命令**：开发、测试和构建所需的基本命令列表。这可以避免 Claude 费力查找它们[^1][^2]。
*   **代码风格和约定**：关于格式化、导入/导出语法、命名约定和错误处理的说明[^1][^5]。明确表达您的偏好。
*   **测试说明**：如何运行整个测试套件，更重要的是，如何运行单个测试以获得更好的性能[^1][^5]。
*   **工作流程和 Git 规则**：分支命名、提交信息格式（例如，约定式提交 Conventional Commits）和拉取请求流程的指南[^1]。
*   **个性化**：您甚至可以包含关于 Claude 应如何与您互动的说明，例如用昵称称呼您[^4]。

### 编写最佳实践

像对待任何重要的提示（prompt）一样对待您的 `CLAUDE.md`。持续优化它以获得更好的结果[^1]。

*   **具体且可操作**：不要写“测试代码”，而应写“使用 `npm run test:unit` 运行单元测试”[^1]。
*   **使用结构**：使用 Markdown 标题、列表和代码块来组织文件，使其易于人类和 AI 解析[^1]。
*   **提供示例**：对于像提交信息格式这样的规则，提供一个清晰的良好提交信息示例[^7]。
*   **迭代和调整**：如果 Claude 没有遵循某条指令，尝试换种说法。您可以使用“重要”（IMPORTANT）或“必须”（YOU MUST）等词语来强调，以提高遵循度[^1]。您还可以在会话期间使用 `#` 键快速向文件添加新指令[^1]。

### 示例 `CLAUDE.md`

这是一个结合了多项最佳实践的 `CLAUDE.md` 文件示例：

```markdown
# CLAUDE.md - Claude Code 站点指南

此文件为 Claude Code 在此代码仓库中工作时提供指导[^5]。

## 1. 仓库概览

此代码仓库包含一个使用 Jekyll 和 Minimal Mistakes 主题构建的个人博客，托管在 GitHub Pages 上[^7]。

## 2. 关键命令

- **本地开发**：`bundle exec jekyll serve`[^7]
- **运行测试**：`ci.sh`[^7]
- **代码检查**：`npm run lint`

## 3. 代码风格与约定

- **模块语法**：您必须使用 ES 模块 (`import`/`export`) 语法，而不是 CommonJS (`require`)[^1]。
- **导入**：尽可能解构导入（例如：`import { foo } from 'bar'`）[^1]。
- **样式**：所有样式均通过位于 `_sass/` 目录中的 SCSS 文件完成[^7]。

## 4. 工作流程

- **测试**：进行更改时，出于性能考虑，优先运行单个测试，而不是整个测试套件[^1]。
- **新博文**：在 `_posts/` 文件夹中创建新博文，使用 `YYYY-MM-DD-标题.md` 格式[^7]。
- **Git 提交**：所有提交信息必须遵循约定式提交（Conventional Commits）规范。
  - **示例**：`feat: 为头部添加暗黑模式切换按钮`

## 5. 个人备注

- 如果遇到困难，请停下来寻求帮助。我的名字是 Harp Dog[^4]。
```

<div style="text-align: center">⁂</div>

[^1]: https://www.anthropic.com/engineering/claude-code-best-practices
[^2]: https://docs.anthropic.com/en/docs/claude-code/tutorials
[^3]: https://www.reddit.com/r/ClaudeAI/comments/1k5slll/anthropics_guide_to_claude_code_best_practices/
[^4]: https://harper.blog/2025/05/08/basic-claude-code/
[^5]: https://kirshatrov.com/posts/claude-code-internals
[^6]: https://www.datacamp.com/tutorial/claude-code
[^7]: https://craigmbooth.com/CLAUDE/
[^8]: https://github.com/hesreallyhim/awesome-claude-code
[^9]: https://github.com/basicmachines-co/basic-memory/blob/main/CLAUDE.md