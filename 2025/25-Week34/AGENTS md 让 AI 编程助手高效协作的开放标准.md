AGENTS.md 让 AI 编程助手高效协作的开放标准

  

**概述**

  

AGENTS.md 是一种专为 AI 编程助手设计的开放文档格式，旨在为项目提供清晰、可预测的上下文和操作指令。它类似于 README，但专注于服务 AI 代理，帮助它们理解项目结构、开发流程和代码规范。AGENTS.md 已被超过 2 万个开源项目采用，成为连接人类开发者与 AI 编程助手的桥梁。通过将针对 AI 的详细说明与面向人的 README 分离，AGENTS.md 让项目文档更简洁，同时为 AI 代理提供所需的全部信息，提升协作效率和自动化能力。

  

**AGENTS.md** **的设计理念与作用**

- AGENTS.md 的核心定位是“为 AI 代理服务的 README”，它为 AI 编程助手提供专属的、结构化的指令和上下文信息。
- 传统的 README.md 文件主要面向人类开发者，内容包括项目简介、快速上手、贡献指南等。而 AGENTS.md 则补充了 AI 代理所需的额外细节，如构建步骤、测试流程、代码规范等，这些内容往往会让 README 变得冗长或对人类贡献者不够友好。
- 通过将 AI 相关说明单独放在 AGENTS.md 文件中，项目文档可以保持简洁，且 AI 代理能在一个固定位置获取所有必要信息。
- AGENTS.md 采用开放、通用的 Markdown 格式，无需专有工具或平台，任何项目都可以轻松集成和维护。
- 该标准已被 OpenAI Codex、Amp、Jules（Google）、Cursor、Factory、RooCode 等主流 AI 编程工具支持，形成了广泛的生态兼容性。

  

**AGENTS.md** **的内容结构与编写方法**

- AGENTS.md 文件通常放置在项目根目录，内容根据项目需求灵活组织，常见结构包括：

- 项目概览（Project overview）：简要介绍项目目标、主要功能和架构。
- 构建与测试命令（Build and test commands）：详细列出安装依赖、启动开发环境、运行测试等操作命令。例如：
```
# AGENTS.md
## Setup commands
- Install deps: `pnpm install`
- Start dev server: `pnpm dev`
- Run tests: `pnpm test`

```


- 代码风格指南（Code style guidelines）：说明代码书写规范，如 TypeScript 严格模式、单引号、无分号、优先使用函数式模式等。
- 测试说明（Testing instructions）：包括 CI 流程、测试命令、如何修复错误、添加或更新测试用例等。例如：
```markdown
## Testing instructions

- Find the CI plan in the .github/workflows folder.

- Run `pnpm turbo run test --filter <project_name>` to run every check defined for that package.

- From the package root you can just call `pnpm test`. The commit should pass all tests before you merge.

- To focus on one step, add the Vitest pattern: `pnpm vitest run -t "<test name>"`

- Fix any test or type errors until the whole suite is green.

- After moving files or changing imports, run `pnpm lint --filter <project_name>` to be sure ESLint and TypeScript rules still pass.

- Add or update tests for the code you change, even if nobody asked.
```



- PR 说明（PR instructions）：如提交标题格式、必须运行的检查命令等。
- 安全注意事项（Security considerations）、数据集说明、部署流程等也可根据项目实际情况补充。

- 对于大型 monorepo 项目，可以在每个子包目录下单独添加 AGENTS.md 文件，AI 代理会自动读取距离目标文件最近的 AGENTS.md，实现分层、定制化的指令分发。例如 OpenAI 主仓库目前有 88 个 AGENTS.md 文件。
- AGENTS.md 文件内容完全自定义，无强制字段，AI 代理会解析你提供的所有文本。若指令冲突，距离被编辑文件最近的 AGENTS.md 优先，用户的聊天指令则最高优先级。

  

**AGENTS.md** **的生态兼容性与应用案例**

- AGENTS.md 已被众多主流 AI 编程工具和平台支持，包括：

- Codex（OpenAI）：通用 CLI 工具，支持 Rust 项目。
- Amp：AI 编程助手。
- Jules（Google）：AI 编程工具。
- Cursor：AI 驱动的 IDE。
- Factory、RooCode 等。

- 典型应用场景包括：

- openai/codex：Rust 项目，集成 AGENTS.md 提供 AI 代理操作指令。
- apache/airflow：Python 项目，自动化工作流编排。
- temporalio/sdk-java：Java 项目，代码定义的工作流编排。
- PlutoLang/Pluto：C++ 项目，Lua 语言扩展。

- 超过 2 万个开源项目已采用 AGENTS.md，形成了丰富的实践案例和社区支持。

  

**框架与心智模型**

- AGENTS.md 的核心框架是“为 AI 代理提供结构化、可预测的操作指令”，其心智模型包括：

- 明确分离人类与 AI 代理的文档需求，分别用 README 和 AGENTS.md 管理。
- 采用开放、标准化的 Markdown 格式，降低集成门槛，提升可维护性。
- 支持分层、定制化指令分发，适应大型 monorepo 项目结构。
- 指令优先级清晰：最近的 AGENTS.md > 全局 AGENTS.md > 用户聊天指令。
- AGENTS.md 是“活文档”，可随时更新，适应项目演进。
- 迁移现有文档只需重命名并创建符号链接，无需复杂操作。

- 该框架鼓励开发者将所有希望 AI 代理知晓的信息（如构建、测试、代码规范、安全注意事项等）集中在 AGENTS.md，提升自动化协作和项目可维护性。

  

**基本信息**

- Title：AGENTS.md
- Author：AGENTS.md 社区项目
- Date：不详（持续更新中）
- URL：https://agents.md/