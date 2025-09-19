中文标题：Smol AI  创始人 swyx 加入 Devin AI 的思考与选择

概述  
本文作者 swyx，原 Smol AI 创始人，宣布加入 Cognition Labs（Devin AI 的开发团队），并详细梳理了做出这一选择的核心逻辑，包括 AI 编码代理（Agent）与 AGI 路线的判断、Cognition“Devin”项目的独特优势、团队背景、商业模式、以及自己的个人成长与心路历程。文中通过对行业现状的梳理和多角度分析，深刻阐述了 Code AGI（代码领域人工智能）的发展趋势以及 Cognition 在技术与商业上的战略地位。

主题梳理

1. 短代码时间线与长 AGI 路线
    

- 作者认为并非所有 AI 赛道的价值都一样。将 AI 的发展拆分为“代码 AGI”与“通用 AGI”（AGI, Artificial General Intelligence, 通用人工智能），最重要的是代码领域的 AGI 实现会比通用 AGI 更快实现，同时能捕获 AGI 80% 的商业价值（“Pareto principle of AGI is simply to just do code AI now rather than later”）。
    
- 代码是“可验证领域”（verifiable domain），能非常直接地检验 AI 的实际效果。并且开发代码 AI 的团队可直接“自用（dogfood）”，在实际工作中迭代提升。行业众多头部，包括 OpenAI、Anthropic、DeepSeek、Reflection 等都在这一方向加速投入。
    
- “Code AGI” 不仅是 AGI 实现路径的核心部分，也是拉动大模型推理能力进步的重要推动剂。
    

2. Agent Labs vs Model Labs（代理实验室与模型实验室的博弈）
    

- 过去十年，AI 人才和资源聚集在 Model Labs（大模型实验室），以“预训练-扩展-推理”为范式，希望通过规模、算力取得突破。即便如此，接下来创新概率更高的反而是 Agent Labs——产品优先（product-first），专注于真实用户需求、快速落地并反哺数据与环境理解。
    
- Agent Labs 能够帮助不再跟得上 LLM（大语言模型）进展节奏的企业，适配应用和场域需求，把“前沿能力”铺向更广市场；在商业模式上快速找到高价值场景，用服务粘合上下游。
    
- 作者坦言“Agent Lab”定义仍有待完善，但特定 agent 工程可以持续在范式迁移中实现“生存”，优秀的团队能够搭建具有不断适配能力的技术栈和工具链，快速沿着技术和市场前沿推进。
    

3. 细节中的 Devin（Devin is in the Details）
    

- Cognition 的 Devin、Cascade 等产品与“LLM in a Loop”模式相比，最大的区别是工程和集成的“最后 10%”，这个部分看似琐碎但极易被工程师低估。
    
- 从企业集成到 UI 打磨，从 Marketplace 插件（如 Datadog、Sentry、Figma、Stripe 等）到长期积累的大客户场景适配，Devin 不断在打磨供企业实际落地所需的产品表面和深度。
    
- Windsurf（Cognition 近期收购的 IDE 产品）现已服务数十万开发者，团队着重于极致的产品打磨、与企业合规和安全的对接，确保团队能够应对从初创到大型企业的需求变化。
    
- 这种“面向产品的深度集成”是大多数 Model Labs 缺乏兴趣甚至不屑于做的，成为 Cognition 的核心支点。
    

4. 同步/异步范式的主导权（Owning the Sync/Async Spectrum）
    

- AI 代码工具可根据“AI 软件开发生命周期（SDLC）”“软件角色画像（personas）”以及“自主性等级（autonomy sliders）”等分不同赛道，不同路径上都有潜力公司，但如何切分市场抓住资源最优地定位自身，是 Cognition 令人印象深刻之处。
    
- Cognition 通过快速收购 Windsurf（异步代理 IDE）实现业务面扩展。在同步代理和异步代理两种模式的平衡方面具备先天优势，并可以借助 Slack、GitHub 等现有工具做深度整合。
    
- 作者强调自己更偏好异步工具，“Slack is the killer agent UI”（Slack 是理想的代理人用户界面），对 remote 与开放式合作场景高度适配，对推进团队协作与自动化有长远价值。
    
- 虽然云+本地一体化的开发环境还未完全标准化，但 Cognition 已在行业率先布局这两端，形成壁垒。
    

5. 商业模式：企业计费与个人“低价位”策略
    

- Cognition 採行企业“用量计价”（usage based for enterprise）与个人“低价”并行的商业模式，先用 $500/month 向企业收固定月费，同时根据 Agent Compute Unit（代理算力单位）弹性扩张，让企业用多少算多少，符合大客户需求。
    
- 个人开发者则可以 $20/month 的低价按需使用，迅速拉新扩量，同时企业收入留足可持续现金流，模型可随用户增长自适应扩展。
    
- 2024/9—2025/6，Devin ARR 从 $1M 增长到 $73M，总净消耗低于 $20M，商业增长与效率同步。合并后企业客户几乎无重叠，带来爆发式增长。
    
- 大型企业客户包括高盛、花旗、戴尔、思科等，企业用户需求极度复杂，推动 Cognition 在行业多维度积累 know-how，带来高复购和扩容率。
    

6. 团队构成与文化
    

- Cognition 团队成员背景极为多元，既有 IOI 金牌得主，也充满创业和销售高手，讲求“彻底透明+高度连接”的文化，优先激励团队内部竞争与合作。
    
- 团队不仅技术过硬，更擅长“极致细节管理”——无论是日常的小 UI Bug Fix 还是大型企业迁移项目，都能全身心投入且找到乐趣。
    
- 作者个人在决定加入 Cognition 时，团队氛围与实际参与公司战略制定让他印象极为深刻，认为团队氛围和“Fully Connected”的工作方式（全员高度交流，减少层级）是 Cognition 最宝贵的无形资产之一。
    

框架与心智模型（Framework & Mindset）

- 代码 AGI 的因果模型：  
    做好“可验证领域”的产品（如软件开发自动化）能极大提升 LLM 推理、归纳能力，实现螺旋式“反馈—优化—再提升”循环。  
    而在开发 AI 代理时，从工程集成细节着手，比单纯拼建模能力更重要。因此，拥有产品研发、场景落地、业务集成的一体化能力，是构建良性发展的关键。
    
- Agent Labs 的演化：  
    与传统 Model Lab 靠烧钱买算力、做“模型再造”不同，Agent Lab（如 Cognition）以“产品为首”，发现真实市场需求，用实际用户场景不断打磨技术栈、集成、合规流程。  
    代理工程师生态也已形成类“产品递归”——即通过产品自我修复与不断集成响应外部反馈，快速迭代甚至引领行业范式迁移。
    
- 同步/异步协同范式：  
    AI 软件工程的未来不止于 IDE 自动化，而是覆盖“同步交互”（本地编辑、Pair Programming）与“异步工作流”（如 Slack 协作、远程代码审阅、任务队列分发）。代理要在这两个极端之间游刃有余，适应更多真实企业协作与分布式开发场景。
    
- 商业模式创新与策略：  
    通过企业用量+个人低价的双轨策略，Cognition 实现了“用大客户托底利润、用大众用户扩展体量”的稳健商业模型，并用强企业辅导能力，保持团队小而美、客户满意度和续费率高，带来网络效应和口碑雪球效应。
    
- 团队心智：  
    Cognition 以“Competitive Programmers（不仅是竞赛背景，更强调团队全面竞争力）”为文化支柱，鼓励内部多向交流和持续创新，快速适应市场反馈，推崇个人连接、透明、敏捷。这一团队模型能最大化吸收不同类型人才、激发创新和执行力。
    

基本信息  
Title：Cognition: The Devin is in the Details  
Author：swyx  
URL：[https://www.swyx.io/cognition](https://www.swyx.io/cognition)

1. [https://www.swyx.io/cognition](https://www.swyx.io/cognition)