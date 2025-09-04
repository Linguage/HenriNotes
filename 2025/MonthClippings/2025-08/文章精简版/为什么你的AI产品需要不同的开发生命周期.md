# Why your AI product needs a different development lifecycle

## 文章概要

这篇文章由 Aishwarya Naresh Reganti 和 Kiriti Badam 撰写，他们基于在 OpenAI、Google、Amazon、Databricks 和 Kumo 等公司领导超过 50 个 AI 实施项目的经验，提出了一种专门为 AI 产品开发设计的新框架：**连续校准/连续开发（CC/CD）**。

文章首先指出了传统软件开发与 AI 产品开发的根本区别：
1.  **AI 产品的本质是非确定性的**：传统软件的输入和输出通常是可预测的，而 AI 系统的输出基于模式而非固定规则，即使是相同的输入也可能产生不同的结果。同时，用户与 AI 系统的交互（如开放式提示）也远比点击按钮更难预测和验证。
2.  **AI 产品需要在“代理性”（Agency）和“控制力”（Control）之间进行权衡**：AI 系统被设计为能代表用户执行任务（即具备代理性），但给予系统更多代理性就意味着放弃部分控制力。过早赋予系统高代理性（如自动执行操作）而未充分测试其错误处理机制，会导致系统失控、用户信任丧失和调试困难。

正是由于忽视了这些差异，许多团队经历了从令人印象深刻的演示到无法扩展或维持的系统的痛苦转变。

为了解决这些问题，作者提出了 **CC/CD 框架**，它是对传统 CI/CD（持续集成/持续部署）的改编，专为处理非确定性行为和需要逐步获得代理权的系统而设计。

**CC/CD 框架包含两个相互交织的循环**：
*   **连续开发（Continuous Development, CD）**：这个阶段侧重于系统的设计和构建。
    1.  **界定能力范围和整理数据（Scope capability and curate data）**：不是按功能划分版本，而是按系统拥有的代理性和愿意放弃的控制力来划分版本。从高控制、低代理的特性开始（如仅建议，不自动执行），逐步增加代理性。同时，构建一个“参考数据集”来定义预期行为，用于后续评估。
    2.  **搭建应用（Set up application）**：基于第一步的范围搭建最简单的可用版本。重点是使其可测量和可迭代（如记录用户输入、系统输出和用户交互），并确保在必要时能无缝地将控制权交还给人类（称为“控制权交接”）。
    3.  **设计评估指标（Design evals）**：定义评估指标（Evals）来衡量系统是否按预期工作。“Evals”类似于传统软件的测试，但专门针对 AI 系统的模糊性和任务相关性。它们用于评估系统在非确定性任务上的表现（如路由准确率、检索质量），并在部署前提供信号。
*   **连续校准（Continuous Calibration, CC）**：系统部署上线后进入此阶段，通过观察真实世界的行为来学习和改进。
    1.  **运行评估（Run evals）**：利用部署后收集的真实用户交互数据，运行在 CD 阶段设计的评估指标。
    2.  **分析行为并发现错误模式（Analyze behavior and spot error patterns）**：手动审查数据，特别是评估指标较弱的部分，找出重复出现的错误模式。
    3.  **应用修复（Apply fixes）**：基于发现的错误模式，有针对性地修改系统（如调整提示、更换模型、改进检索等），然后重新评估。这个过程可能需要迭代多次。同时，也可能需要根据实际用户行为修订评估指标本身。

整个 CC/CD 流程是一个循环迭代的“飞轮”。每一次循环，系统都会积累经验，赢得更多的代理性，变得更加稳健和可信。作者通过一个客户服务自动化系统的例子（从简单的工单路由到最终的自动解决问题），生动地展示了如何运用 CC/CD 框架分阶段、渐进式地构建 AI 产品。

文章最后将 AI 系统的开发比作引导一位新队友，强调需要从小事做起，观察、建立信任，再逐步扩大其职责范围。CC/CD 框架的核心是判断力，它帮助开发者决定何时发布、如何保护用户、何时交还控制权以及如何定义“足够好”。

总而言之，这篇文章为 AI 产品经理和开发者提供了一套系统性的方法论，以应对 AI 产品开发的独特挑战，帮助他们构建更安全、更可靠、更值得信赖的 AI 产品。

## 文章标签

#AI产品 #AI开发 #产品框架 #CCCD #非确定性 #代理性 #控制力 #评估指标 #产品生命周期 #AI工程化

## 文章链接

[https://www.lennysnewsletter.com/p/why-your-ai-product-needs-a-different?utm_source=post-email-title&publication_id=10845&post_id=170720848&utm_campaign=email-post-title&isFreemail=true&r=5dvur6&triedRedirect=true](https://www.lennysnewsletter.com/p/why-your-ai-product-needs-a-different?utm_source=post-email-title&publication_id=10845&post_id=170720848&utm_campaign=email-post-title&isFreemail=true&r=5dvur6&triedRedirect=true)