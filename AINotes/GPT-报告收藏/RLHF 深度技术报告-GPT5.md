You: 

大型语言模型（LLM）的训练一般包含预训练、SFT（监督微调）、RLHF（人类反馈强化学习）三个阶段。请广泛深入调研分析RLHF的教程和文章、论文等，使用通俗易懂的语言，帮我输出一份技术报告，面向软件开发者和产品经理等，使得我们能够快速理解大语言模型训练的过程，配合一些图表和视频，不少于三万字

ChatGPT: 

已思考 1m 38s

已思考 58s

文档已创建

已思考 19s

已把一份系统化的《RLHF 技术报告（面向开发者与产品经理）》放到右侧画布，便于阅读、二次编辑与后续版本沉淀。报告聚焦方法理解与工程落地（含：方法全景、数据与标注、奖励模型与PPO/GRPO要点、DPO/SimPO/ORPO/KTO/RRHF/IPO 对比、评测与门控、治理与常见坑、可复用清单与术语表）。同时，我为报告配了可下载的图表，方便插入到你的文档或演示里：

-   下载：RLHF Training Pipeline（schematic）
    
-   下载：偏好对齐方法时间轴（代表性）
    
-   下载：方法景观对比（训练环路复杂度 × 标注成本·示意）
    

> 说明：以上图仅为工程沟通示意，数轴位置为启发式，建议结合你们的实际数据与约束校正。

---

# 参考资料与视频（精选，可直接用作延伸阅读清单）

## 里程碑论文与方法

-   **InstructGPT（RLHF 三段式）**：提出以人类偏好训练奖励模型，并在 KL 约束下用 PPO 微调策略；文中也写明了 KL 系数与预训练损失项的作用。[arXiv](https://arxiv.org/abs/2203.02155?utm_source=chatgpt.com)
    
-   **Anthropic HH-RLHF（有害性/有用性）**：大规模偏好数据与 RLHF 训练，观察到 RL 奖励与相对初始策略的 KL 距离平方根近似线性关系。
    
-   **Constitutional AI / RLAIF**：以原则（“宪法”）为准则，用 AI 反馈替代部分人类标注，降低暴露有害样本的成本。[arXiv](https://arxiv.org/abs/2212.08073?utm_source=chatgpt.com)[www-cdn.anthropic.com](https://www-cdn.anthropic.com/7512771452629584566b6303311496c262da1006/Anthropic_ConstitutionalAI_v2.pdf?utm_source=chatgpt.com)
    
-   **RLAIF vs. RLHF（系统比较）**：在若干任务上，AI 反馈可达到接近人类反馈的效果，并提出直接从 LLM 获取奖励信号的 d-RLAIF。[arXiv](https://arxiv.org/abs/2309.00267?utm_source=chatgpt.com)[OpenReview](https://openreview.net/forum?id=AAxIs3D2ZZ&utm_source=chatgpt.com)
    
-   **DPO（Direct Preference Optimization）**：把“最大化人类偏好奖励”的 RL 问题重参数化为简单的分类/对比损失，无需在线 RL 与显式奖励模型。[arXiv](https://arxiv.org/abs/2305.18290?utm_source=chatgpt.com)[OpenReview](https://openreview.net/pdf?id=HPuSIXJaa9&utm_source=chatgpt.com)
    
-   **SimPO**：引入平均 log 概率作为隐式奖励并加入 margin，往往不需要参考模型，报告中在多个评测上优于 DPO。[arXiv](https://arxiv.org/abs/2405.14734?utm_source=chatgpt.com)[NeurIPS](https://neurips.cc/virtual/2024/poster/96741?utm_source=chatgpt.com)
    
-   **ORPO**：单模型的“偏好+惩罚”目标（无需参考模型），在 EMNLP 2024 发表。[arXiv](https://arxiv.org/abs/2403.07691?utm_source=chatgpt.com)[ACL Anthology](https://aclanthology.org/2024.emnlp-main.626/?utm_source=chatgpt.com)
    
-   **KTO（Kahneman-Tversky Optimization）**：将人类前景理论引入对齐目标，强调损失厌恶等心理特征。[arXiv+1](https://arxiv.org/abs/2402.01306?utm_source=chatgpt.com)
    
-   **RRHF**：基于多候选排序的偏好对齐，训练稳定但依赖候选质量。[arXiv](https://arxiv.org/abs/2304.05302?utm_source=chatgpt.com)[OpenReview](https://openreview.net/pdf?id=EdIGMCHk4l&utm_source=chatgpt.com)
    
-   **IPO（Implicit Preference Optimization）**：把生成式 LLM 作为偏好分类器以自举方式获得偏好并做 DPO-式训练（2025）。[arXiv](https://arxiv.org/abs/2502.16182?utm_source=chatgpt.com)[ACL Anthology](https://aclanthology.org/2025.acl-long.954/?utm_source=chatgpt.com)
    
-   **早期根基**：Christiano 等“从人类偏好中进行深度强化学习”（2017），为后续 RLHF 奠基；OpenAI 在摘要任务上率先展示“人类反馈 → 更好摘要”。
    

## 理论、实现细节与稳定性

-   **PPO/GRPO 与 KL 约束**：InstructGPT 附录与 GRPO 工作；实践上需把控 KL 区间、价值基线与长度归一。
    
-   **奖励过优化（Reward Hacking）与标尺失真**：奖励模型/直接对齐算法在过度优化时可能与“真偏好”脱节，应配合人评与早停。
    
-   **密集化奖励与稳定性**：将注意力引导的 token 级奖励用于 PPO，缓解训练不稳与信用分配。
    
-   **“规则化奖励”以细化安全行为**：以可操作的规则分解安全目标，生成更细粒度的拒答/道歉/替代建议风格。
    

## 数据、评测与工具

-   **公开偏好数据**：Anthropic HH-RLHF、Stanford SHP（385K 偏好）。
    
-   **奖励模型评测**：RewardBench（论文+代码与榜单）。
    
-   **对话/偏好评测**：MT-Bench & Chatbot Arena、AlpacaEval 2（长度控制胜率）。
    
-   **开源训练栈**：Hugging Face TRL（SFT/RM/PPO/GRPO/DPO 全链路）；配套 RLHF 博文与课程。[Hugging Face+1](https://huggingface.co/docs/trl/en/index?utm_source=chatgpt.com)
    

## 教程与视频（适合产品/工程团队共学）

-   **DeepLearning.AI — RLHF 短课**（概念→实操→SxS 评测），另有开放课程章节。
    
-   **OpenAI Instruction-following（概览）** 与 **Learning to Summarize with Human Feedback（任务化示例）**。
    
-   **Stanford CS25 系列（含对齐/开源模型分享）**。
    
-   **RLHF 书籍（Nathan Lambert）**：系统性讲解偏好数据、奖励模型与优化。
    
-   **最新工程综述（推理与 RL）**：强化学习用于“推理型后训练”的近况与趋势。
    

---

## 你会在报告里看到什么（要点速览）

-   **两条主路线**如何取舍：\*\*SFT+（DPO/SimPO/ORPO）\*\*的快速上线范式 vs. **RM+PPO/GRPO**的精细化可控；并给出资源/目标导向的选型树。
    
-   **数据闭环**：提示池设计、SFT 演示与失败修复、偏好对构造与质检、RLAIF 冷启动与“人审抽检”纠偏。
    
-   **训练与稳定性**：KL 约束区间、长度归一/密集奖励、早停与“奖励过优化”监控。
    
-   **评测与门控**：自动基准 + Golden Set + 人评抽检 + 线上观测（拒答率/长度偏置/幻觉/越狱/引用占比）。
    
-   **常见坑**：长度偏置、过拒、奖励过优化、分布移位、LLM-as-Judge 偏差……给出逐条缓解策略。
    

---

## 想继续深化？我可以直接在画布里为你补充

-   适配你们业务的 **Rubric 模板**、**偏好标注规范** 与 **安全拒答话术库**；
    
-   把以上图表扩成 **海报/讲义版**（含备注与空位示例）；
    
-   输出 **评测清单与看板指标字典**（可直接交给数据/平台侧落地）。
    

如果你希望我把这份报告扩写成“白皮书级”的长篇（例如加入更详尽的案例、更多对比表、可交付的评测脚本与标注文档），也可以直接告诉我你们的目标域与上线时间线，我会在当前文档上继续铺开。

——

*注：画布内不附带外链引用，以上正文为你核查与深入阅读所用的高质量来源。*

You: 

好的，基于以上内容和分析，帮我输出一个更为详细和完整的深入研究报告，把握重点核心内容，使用通俗易懂的语言，不少于三万字

ChatGPT: 

我可以为你进一步撰写更为详细的 RLHF 深度研究报告。为了确保内容完全满足你的预期，能否请你补充以下信息：

1.  报告主要用途是对内培训、对外发表，还是用于技术评审？
    
2.  是否有特定领域或行业（如医疗、金融、政务、教育、客服等）希望着重分析 RLHF 的应用？
    
3.  是否希望包含开源代码、工程框架、具体标注模板、评测脚本等“可落地工具”？
    
4.  是否希望扩展篇幅至 3–5 个章节的子专题报告（如 PPO/GRPO 稳定性、红队与拒答策略、RLAIF 的风险与使用建议等）？
    

补充这些信息后我将启动深度调研与撰写流程，为你组织一份结构合理、重点突出、含图表引用且风格清晰的 RLHF 长篇技术报告。

You: 

报告主要用途是面向软件开发者和产品经理的技术分享，没有特定领域或行业，主要分享核心的原理和实现方案，不需要过于细节，不受限于结构，而是聚焦于让读者更好的理解内容，掌握内容；期望附加内容：如图表（可导出）、视频资源推荐、术语表等。使用通俗易懂的语言，不少于三万字

ChatGPT: 

明白了，我将为你撰写一份面向软件开发者与产品经理的 RLHF 深度技术报告。内容将聚焦核心原理与主流实现方法，使用通俗语言帮助读者理解并掌握偏好对齐的关键概念与应用流程，涵盖：

-   全流程概览与方法演进；
    
-   各类方法（RLHF/PPO/DPO/SimPO/ORPO/KTO/RRHF/RLAIF/Constitutional AI）的核心机制与对比；
    
-   数据构建、训练流程、评测指标与上线治理策略；
    
-   图表插图（可导出）、术语解释、视频/教程推荐等扩展资源；
    
-   篇幅将达到或超过三万字。
    

我会尽快完成调研并撰写，完成后第一时间通知你审阅。

# RLHF 深度技术报告

## 引言 (Introduction)

强化学习从人类反馈（**RLHF**，Reinforcement Learning from Human Feedback）是近年来大模型对齐（Alignment）的核心方法，被广泛应用于诸如 InstructGPT 和 ChatGPT 等先进语言模型的训练[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=next%20important%20topic%20is%20how,unstable%20or%20hard%20to%20tune)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Feedback%20,that%20of%20complex%20human%20values)。简单来说，RLHF 让模型在学习模仿海量人类文本的基础上，引入人类偏好作为新的优化目标，使模型的回答更符合人类期望[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=OpenAI%2C%20may%20have%20seemed%20like,learned%20to%20truly%20serve%20humanity)。相比仅用纯粹的**监督学习**（Supervised Learning）或人为设计的指标来训练模型，RLHF 更直接地**以人类反馈作为模型的学习信号**，从而在生成文本时更好地满足用户的需求和价值观[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Writing%20a%20loss%20function%20to,of%20Reinforcement%20Learning%20from%20Human)[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=text%20patterns%20but%20really%20bad,learned%20to%20truly%20serve%20humanity)。

RLHF 的出现源于一个现实问题：语言模型通过预测下一个词语可以学会流畅地“模仿”人类语言模式，但未必能**理解人类真正想要什么**。早期的大模型往往输出大量无关、有害或风格不当的内容，即使它们在形式上看似正确[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=OpenAI%2C%20may%20have%20seemed%20like,learned%20to%20truly%20serve%20humanity)。为了解决这一**模型对齐**问题，OpenAI 团队在 2017 年提出了“从人类偏好中深度强化学习”的概念，把**人工偏好**直接融入训练循环[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=They%20created%20a%20smartly%20working,loop%2C%20with%203%20steps)。这一方法起初用于游戏代理（让人类比较游戏片段，教会 AI 玩游戏[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=In%20RLHF%2C%20two%20different%20models,responses%2C%20written%20by%20human%20annotators)[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=The%20reward%20model%20is%20then,r_%7B%5Ctheta)），随后拓展到让语言模型学习摘要、对话等任务中的人类偏好[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=text%20patterns%20but%20really%20bad,learned%20to%20truly%20serve%20humanity)。在 2022 年，OpenAI 成功将 RLHF 应用到 GPT-3 模型上，诞生了 InstructGPT，并在此基础上打造了 ChatGPT，大幅提升了模型回答的有用性、礼貌性和安全性[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=RLHF%27s%20most%20recent%20success%20was,to%20explain%20RLHF%20for%20us)。可以说，RLHF 是让 AI 真正“为人所用”的转折点[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=stuck,learned%20to%20truly%20serve%20humanity)。

对于没有学术背景的软件从业者和产品经理而言，理解 RLHF 的**原理机制**与**工程实现**有助于把握当今 AI 模型调优的关键思路。本报告将通过通俗易懂的语言，全面介绍 RLHF 的背景动机、训练流程、数据标注要求、以及近年来围绕 RLHF 的各种改进技术路径。我们将重点讨论各类偏好对齐方法（如 PPO、DPO、RLAIF、KTO 等）的**原理和对比**，并解析一些**工程细节**和实践策略。最后，我们还将讨论模型上线后的**评测与迭代**，即如何持续收集反馈优化模型。希望本报告能帮助您从宏观上把握 RLHF 及相关技术，让模型调优变得更加直观和工程可行。

*（注：文中专业术语和缩写会在附录的术语表中中英对照解释，以方便阅读。）*

## 背景与动机 (Background and Motivation)

随着大规模预训练语言模型（LLM）的发展，人们发现仅靠传统的训练目标（如下一个词预测）很难让模型输出真正**有用**或**符合人类偏好**的内容[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Writing%20a%20loss%20function%20to,of%20Reinforcement%20Learning%20from%20Human)。例如，在预训练语料中，既有高质量的信息，也充斥着偏见、不相关甚至有害的文本。模型学到的只是“如何像人一样写作”，而不是“什么是人类喜欢的答案”[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=OpenAI%2C%20may%20have%20seemed%20like,learned%20to%20truly%20serve%20humanity)。这导致未对齐的模型往往**答非所问**、输出冗长空洞的回答，甚至可能生成不安全或有攻击性的内容[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=text%20patterns%20but%20really%20bad,learned%20to%20truly%20serve%20humanity)。

为此，研究者尝试引入**人类的价值判断**来指导模型学习。其中一个里程碑是 2017 年的论文《从人类偏好中深度强化学习》(Deep RL from Human Preferences)，证明了通过让人类比较模型行为的好坏并据此训练奖励函数，可以比直接用预定义分数（如游戏得分）更好地训练出符合人意的智能体papers.neurips.cc[reddit.com](https://www.reddit.com/r/reinforcementlearning/comments/13hwfho/opendilab_awesome_paper_collection_rl_with_human/#:~:text=Initially%2C%20in%20the%202017%20research,to%20introduce%20human%20feedback)。这一思想应用于语言模型，就是让人类去**比较不同回答的优劣**，并用这些比较结果来调整模型，使其更倾向于人类偏好的答案[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=They%20created%20a%20smartly%20working,loop%2C%20with%203%20steps)。

OpenAI 在 2022 年发布的 InstructGPT 模型正式将这一流程应用于大规模语言模型调优。他们通过**人工标注反馈**，让 GPT-3 模型学会什么样的回答更受人类青睐，从而极大提升了模型输出的相关性和有益性[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=RLHF%27s%20most%20recent%20success%20was,to%20explain%20RLHF%20for%20us)。InstructGPT 和后续的 ChatGPT 成功展示了 RLHF 的威力：模型不再只是“随机聊天”或“文不对题”，而是**尽可能对用户的问题给出有帮助且合乎礼仪的回答**[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=Feedback%20,unstable%20or%20hard%20to%20tune)[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=OpenAI%2C%20may%20have%20seemed%20like,learned%20to%20truly%20serve%20humanity)。这背后的动机在于，让 AI 模型按照**人类的意图**行事，而不仅仅是基于训练语料的统计规律。

总结而言，RLHF 诞生的主要动因有：

-   **对齐人类价值观**：将人类对输出的喜好作为训练信号，使模型更符合人类在有用性、真实、无害等方面的期望[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=text%20patterns%20but%20really%20bad,learned%20to%20truly%20serve%20humanity)。
    
-   **弥补损失函数不足**：传统语言模型的损失函数（如困惑度）无法充分衡量回答质量，而直接使用人类反馈可绕过设计复杂指标的难题[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Writing%20a%20loss%20function%20to,of%20Reinforcement%20Learning%20from%20Human)。
    
-   **改进用户体验**：通过RLHF，模型回答变得更加精准、有礼貌和安全，从而提升人机交互的质量[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Feedback%20,that%20of%20complex%20human%20values)。
    
-   **解决奖励设计难题**：相比手工设计奖励（如 BLEU/ROUGE 等指标），人类偏好是更直接的“终极指标”，可以指导模型朝着真正让用户满意的方向优化[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Writing%20a%20loss%20function%20to,of%20Reinforcement%20Learning%20from%20Human)。
    

总之，RLHF 的出现标志着模型训练范式从**模仿学习**向**偏好驱动学习**的转变，把**人**纳入了 AI 优化闭环，从而开启了让 AI 真正满足人类需求的新篇章。

## RLHF 方法机制 (Method and Mechanism of RLHF)

RLHF 的训练流程涉及**多个阶段、多个模型**，看起来较为复杂。下面我们将分步骤解释这一过程，并辅以直观图示，帮助理解 RLHF 是如何将人类反馈融入模型训练的。

### 3.1 RLHF 典型流程 (Typical RLHF Pipeline)

一个标准的 RLHF 训练由三步组成[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=preferences,process%20into%20three%20core%20steps)：

1.  **步骤1：有监督微调（SFT）** – 首先，对预训练语言模型进行**有监督微调**。开发者收集一批高质量的**指令-回答**示例（通常由人工编写），然后训练模型根据指令生成适当的回答。这个阶段让模型具备基本的指令遵循能力，提升初始性能[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=Similarly%20to%20the%20reward%20model%2C,trained%20model.%5B%2014)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=As%20a%20starting%20point%20RLHF,powered%20products)。一般来说，只需要对预训练模型进行少量 epochs 的微调即可，否则模型可能过拟合于微调数据[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=The%20first%20step%20in%20its,more%20than%20that%20causes%20overfitting)。
    
2.  **步骤2：奖励模型训练（RM Training）** – 接下来，引入**奖励模型**（Reward Model）。奖励模型的作用是**根据人类偏好为模型输出打分**[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Generating%20a%20reward%20model%20,later%20in%20the%20RLHF%20process)。为了训练奖励模型，需要收集**偏好数据**：具体做法是让人工标注者针对同一提示（prompt），比较两到多个模型输出，选出他们认为更好的回答[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=,to%20train%20a%20reward%20function)。有了足够的比较数据后，将其转换为**训练集**来微调一个预训练模型，使其输入一个（prompt, 回答）对后输出一个分数，表示该回答被人类偏好的程度[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=The%20reward%20model%20is%20then,r_%7B%5Ctheta)[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=,l)。常用的方法是让奖励模型对比较对中的胜者输出比败者更高的分值，并使用交叉熵损失训练（即 Bradley-Terry 模型）[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=following%20cross,r_%7B%5Ctheta%20%7D%28x%2Cy_%7Bl%7D%29%7D%7D%7D%5Cright)。经过训练的奖励模型可以近似模拟人类的偏好判断[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=)。下图形象展示了这一过程：
    

*图1：奖励模型训练流程示意图。首先由初始模型对同一提示生成多种回答，人工标注者对这些回答进行偏好排序或比较，然后用这些偏好数据来训练一个奖励模型，使其能够输出反映人类喜好的评分[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=The%20reward%20function%20is%20where,KL%29%20divergence)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=probability%20distributions%20from%20the%20RL,KL%20divergence%20is%20approximated%20via)。*

3.  **步骤3：强化学习微调（RL Fine-tuning）** – 最后，也是核心的一步，将上一步得到的奖励模型作为“评分指南”，对**策略模型**（也就是我们希望最终得到的对话模型）进行强化学习训练[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=reinforcement%20learning%20%20%28RL%29%20policy,responses%2C%20written%20by%20human%20annotators)[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=The%20key%20is%20to%20understand,can%20be%20applied%20to%20it)。具体做法通常采用**策略梯度**方法，最常见的是**近端策略优化（PPO）**算法[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=The%20most%20widespread%20RL%20algorithm,preventing%20large%20shifts%20in%20behavior)。简单而言，我们让当前策略模型针对提示生成回答，然后用奖励模型对回答打分，得到一个**奖励值**；同时，我们设置一个机制避免模型偏离初始行为分布太远（通常通过和初始SFT模型的输出做 KL 散度惩罚）[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=probability%20distributions%20from%20the%20RL,KL%20divergence%20is%20approximated%20via)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=papers%20from%20OpenAI%2C%20Anthropic%2C%20and,explained%20by%20John%20Schulman)。综合奖励模型分数 $r\_{\\theta}$ 和 KL 惩罚 $r\_{KL}$ 后，形成最终的奖励信号 $r = r\_{\\theta} - \\lambda \\cdot r\_{KL}$[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=papers%20from%20OpenAI%2C%20Anthropic%2C%20and,explained%20by%20John%20Schulman)。PPO 算法会根据这个奖励信号调整策略模型的参数，使其产生更高奖励的输出[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=with%20the%20original%20prompt%2C%20that,useful%20to%20make%20sure%20the)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=sampling%20from%20both%20distributions%20,is%20r%3Dr%20%CE%B8%E2%88%92%CE%BB%20r%20KL)。训练过程中，策略模型会不断尝试新的回答方式，逐步被优化成\*\*迎合奖励模型（即人类偏好）\*\*的方向。下图展示了 RL 阶段的工作原理：
    

*图2：RLHF 中的强化学习微调阶段。在每次训练迭代中，策略模型（Policy）根据提示 $x$ 生成回答 $y$，奖励模型对 $y$ 打分得到 $r\_{\\theta}$，同时计算策略模型输出与参考模型输出分布的 KL 距离作为惩罚 $r\_{KL}$[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=probability%20distributions%20from%20the%20RL,KL%20divergence%20is%20approximated%20via)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=sampling%20from%20both%20distributions%20,is%20r%3Dr%20%CE%B8%E2%88%92%CE%BB%20r%20KL)。综合得到的最终奖励 $r = r\_{\\theta} - \\lambda r\_{KL}$ 用于更新策略模型参数[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=papers%20from%20OpenAI%2C%20Anthropic%2C%20and,explained%20by%20John%20Schulman)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=sampling%20from%20both%20distributions%20,is%20r%3Dr%20%CE%B8%E2%88%92%CE%BB%20r%20KL)。KL 惩罚限制模型不要偏离初始模型太多，以免出现语无伦次的“奖励黑客”式输出[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=between%20these%20sequences%20of%20distributions,is%20r%3Dr%20%CE%B8%E2%88%92%CE%BB%20r%20KL)。*

上述三个步骤完成后，我们就得到了一个经过 RLHF 调优的模型。需要注意，在实际应用中，**SFT 模型**通常作为**策略模型的参考基线**存在，并不参与 RL 阶段参数更新，只用于计算 KL 惩罚和提供初始策略[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Image)。整个流程也可以迭代进行：模型上线后收集真实用户的反馈，再用于更新奖励模型和策略模型，从而不断提升性能[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Optionally%2C%20RLHF%20can%20continue%20from,complex%20and%20open%20research%20question)。不过大多数研究和开源实现目前只执行一次离线的 RLHF 循环，持续在线迭代仍是前沿探索领域[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Optionally%2C%20RLHF%20can%20continue%20from,complex%20and%20open%20research%20question)。

### 3.2 RLHF 工程实现 (Engineering Implementation)

在工程上，实现 RLHF 需要处理多个模型和数据管道，但幸好现在已有一些开源工具和实践经验：

-   **多模型管理**：RLHF 涉及**策略模型**（policy）、**奖励模型**（reward model）和有时单独的**价值函数模型**（value model，用于估计状态的期望回报）。有些实现将价值函数和策略合并在同一模型不同头上，有些使用单独网络。比如 OpenAI 的 PPO 实现使用**策略-价值双头模型**，而 DeepSeek 的新方法（见后文 GRPO）则完全省去了价值网络[reddit.com](https://www.reddit.com/r/LLMDevs/comments/1ibhpqw/how_was_deepseekr1_built_for_dummies/#:~:text=How%20was%20DeepSeek,3)[together.ai](https://www.together.ai/deepseek#:~:text=DeepSeek%20Models%20Family%20,advantage%20estimation%20to%20cut)。在代码层面，需要能够同时加载、保存和更新这些模型。
    
-   **训练库**：Hugging Face 提供了开源的 **TRL**（Transformer Reinforcement Learning）库，以及其衍生项目 TRLX，可用于RLHF训练[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=The%20first%20code%20released%20to,OpenAI%20in%20TensorFlow%20in%202019)。这些库封装了 PPO 等算法，对接 Transformers 模型，支持多 GPU 分布式训练。使用这些库可以避免从零编写 RL 训练循环。除了Hugging Face，OpenAI早在2019年就开源过一个 TensorFlow 实现，近期也有如 **RL4LMs** 等学术代码提供更多算法支持[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=The%20first%20code%20released%20to,OpenAI%20in%20TensorFlow%20in%202019)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=TRL%20is%20designed%20to%20fine,with%20experience%20at%20this%20scale)。工程上通常采用**混合精度**和**低阶微调**（如 LoRA）来降低大模型训练的内存和算力需求[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=policy,scaling%20up%20to%20the%20new)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=parameter%20model%20is%20prohibitively%20expensive,more%20on%20that%20later)。
    
-   **数据管道**：需要准备两类数据：一是用于**SFT微调**的高质量指令-回答数据，二是用于**奖励模型**的成对比较数据。前者可来自公开的指令数据集（如 OpenAI 提供的人类撰写示例）或靠模型自生成后人工筛选调整。后者获取难度更高，一般需要众包标注或专业团队。工程上常采用**人机对话界面**让标注员与模型交互并比较输出，从而收集偏好数据[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=model%20is%20then%20customarily%20trained,responses%2C%20written%20by%20human%20annotators)[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=The%20reward%20model%20is%20then,r_%7B%5Ctheta)。在数据存储格式上，许多实现将比较数据存成 `{prompt, chosen_response, rejected_response}` 的JSON，这也是 TRL/TRLX 读取的格式[docs.axolotl.ai](https://docs.axolotl.ai/docs/rlhf.html#:~:text=DPO)[docs.axolotl.ai](https://docs.axolotl.ai/docs/rlhf.html#:~:text=)。有些场景下也将多次交互序列存为对话格式。
    
-   **超参数调优**：PPO 训练过程中有不少超参数，如学习率、截断区间 ε、奖励归因方法、KL 惩罚系数等。经验表明，**KL 惩罚系数**的选择非常关键：若太小，模型可能学会投机取巧“骗”奖励模型（输出胡言乱语但奖励高）；太大则训练收敛缓慢[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=papers%20from%20OpenAI%2C%20Anthropic%2C%20and,explained%20by%20John%20Schulman)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=between%20these%20sequences%20of%20distributions,is%20r%3Dr%20%CE%B8%E2%88%92%CE%BB%20r%20KL)。OpenAI 在 InstructGPT 训练中通过在 PPO 更新中混入少量监督学习梯度，进一步稳定训练[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=KL)。工程上通常需要多次实验调整超参数，有条件的话也会对奖励模型的**胜率精度**等指标进行监控，确保策略改进真的是奖励模型评价提高而非过拟合。
    
-   **多GPU并行**：大模型的 RL 训练非常耗算力。一个 trick 是利用并行化生成样本。比如 DeepMind 曾用过 A2C（同步 Actor-Critic）让多个并行模型收集数据[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Finally%2C%20the%20update%20rule%20is,has%20not%20been%20reproduced%20externally)。近期有项目尝试结合 **vLLM** 加速生成[docs.axolotl.ai](https://docs.axolotl.ai/docs/rlhf.html#:~:text=GRPO)。工程上可以将**策略模型推理**和**梯度更新**解耦，由多个生成 worker 提供经验轨迹，再集中更新策略。
    

需要强调的是，RLHF 的工程实现难点不在于 RL 算法本身（PPO 等已有成熟实现[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=research%20problem,more%20on%20that%20later)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=research%20problem,more%20on%20that%20later)），而在于如何稳健地**结合大模型的训练**。由于LLM参数量巨大，稍有不慎就可能导致策略坍塌（输出崩溃）或者训练不收敛[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=Feedback%20,unstable%20or%20hard%20to%20tune)[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=The%20most%20widespread%20RL%20algorithm,preventing%20large%20shifts%20in%20behavior)。因此实践中往往需要反复实验，以及结合**经验法则**（例如每次PPO update后策略与初始策略KL差异保持在一定范围内）来确保训练过程稳定[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=papers%20from%20OpenAI%2C%20Anthropic%2C%20and,explained%20by%20John%20Schulman)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=between%20these%20sequences%20of%20distributions,is%20r%3Dr%20%CE%B8%E2%88%92%CE%BB%20r%20KL)。总的来说，RLHF工程实现目前已经有一些开源范例和工具，但仍需要开发者具备对 RL 基本概念和大模型训练特性的理解，才能有效地调试和收敛模型。

## 数据与标注 (Data and Annotation)

RLHF 的成功高度依赖于**高质量的人类反馈数据**。这一部分我们探讨构建 RLHF 数据集时的要点，包括数据类型、收集方法和质量控制。

**1\. 偏好数据的形式**：RLHF 使用的反馈数据主要有两种形式：**成对比较数据**和**打分数据**[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=,to%20each%20response%2C%20reflecting%20how)。成对比较是指给定同一提示下模型的两条不同回答，让人类选择哪一条更好[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=,to%20train%20a%20reward%20function)。这是当前最常用的格式，因为比较相对简单、可靠，而且可用于 Bradley-Terry 等模型训练奖励函数[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=following%20cross,r_%7B%5Ctheta%20%7D%28x%2Cy_%7Bl%7D%29%7D%7D%7D%5Cright)。打分数据是指让人类直接为单个回答打一个分（如 1-5 星或百分制）。打分更直观但不同人标准可能不一致，一般需要较严格的标注准则。也有用**排序数据**（一次排列多个回答从好到坏），但常可拆解为多次两两比较来处理[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=,to%20each%20response%2C%20reflecting%20how)。目前行业普遍采用\*\*两两比较（Preference Pairs）\*\*收集偏好[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=,to%20each%20response%2C%20reflecting%20how)，因为标注者任务简单且能提供清晰的相对偏好信号。

**2\. 收集方法**：获取偏好数据往往通过**人工标注**平台。常见做法包括：在 Mechanical Turk 等众包平台发布任务，让标注者阅读模型输出并选择更好的；或者自建标注团队，使用专门的UI（如类似于ChatGPT的聊天界面）让标注员与模型多轮互动后对每轮回复作出偏好判断[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=model%20is%20then%20customarily%20trained,responses%2C%20written%20by%20human%20annotators)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=Preference%20data%20and%20where%20to,find%20it)。Anthropic 在 HH-RLHF 数据集中就是提供上下文和两种助手回复，要求标注者选出更有帮助/无害的那个[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=they%20devised%20this%20method%20in,the%20concept%20of%20Constitutional%20AI)。OpenAI 则利用其 API 用户提供的对话作为提示，生成多个GPT-3回答后请人比较好坏[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=The%20training%20dataset%20of%20prompt,model%20to%20generate%20new%20text)。无论哪种方法，都需要为标注者提供**明确的评价标准**，如从助益性、真实性、礼貌度、无害性等维度考虑答案优劣，并权衡哪些维度更重要。Anthropic 的做法是让标注者同时考虑 Helpful（有用）和 Harmless（无害）两个标准，并综合给出偏好[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=they%20devised%20this%20method%20in,the%20concept%20of%20Constitutional%20AI)。

**3\. 数据规模**：RLHF 对数据量的需求没有预训练那么夸张，但依然需要相当数量的偏好样本才能训练出良好的奖励模型和最终策略。OpenAI 在 InstructGPT 中使用了大约上万条人工比较数据[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=model%20is%20then%20customarily%20trained,responses%2C%20written%20by%20human%20annotators)[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=The%20first%20step%20in%20its,more%20than%20that%20causes%20overfitting)。Anthropic 的HH数据集公开了大约16万对比较[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=they%20devised%20this%20method%20in,the%20concept%20of%20Constitutional%20AI)。一般而言，每个新任务/领域都需要上千到上万条偏好数据来覆盖多样的情境和输出差异[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=In%20previous%20posts%2C%20we%20started,Play%20Fine)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=alternative%2C%20Direct%20Preference%20Optimization%20,11%20and%20fifth%20blog%20posts)。数据量不足可能导致奖励模型评价不准确，从而影响策略优化效果。值得注意的是，**偏好数据扩展有一定困难**：人工标注耗时费钱，一般比单纯收集监督问答数据更昂贵，因为需要人类仔细比较理解多种输出。因此近来一些研究在探索如何用较少偏好数据达到好的效果（如后面提到的 DPO 等方法），或者使用 AI 代替人收集反馈（RLAIF）。

**4\. 质量控制**：偏好标注存在**主观性**和**一致性**问题[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=comparisons%20%28A%20,would%20be%20the%20pointwise%20scores)。不同标注者可能偏好不同风格，甚至同一人不同时刻判断也可能不一致。因此数据采集需注重质量控制。例如，可以给同一比较任务安排多个标注者，取多数票以减少随机误差[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=comparisons%20%28A%20,would%20be%20the%20pointwise%20scores)。还可在任务中穿插**黄金标准**（预先知道正确偏好的样本）来检测剔除不认真或标准不符的标注者。Anthropic 在数据说明中提到，他们给定了明确准则，例如回答是否真的有用、有没有回避用户问题、有没有潜在伤害等作为判断依据。对于打分数据，往往要求标注者接受培训以提高评分的一致性。总之，需要尽量减小偏好数据中的噪声，因为奖励模型对任何系统偏差都会**敏感过拟合**，从而误导强化学习阶段（比如如果标注者过度奖赏啰嗦的回答，策略模型就会倾向产出不必要的长篇内容）。

**5\. 公开数据集**：随着 RLHF 热度攀升，也出现了一些**公开偏好数据集**和**挑战**。如 OpenAI 的 Summarize from Feedback 数据集，用于让模型学摘要，包含人类对摘要好坏的标注[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=,to%20train%20a%20reward%20function)。Anthropic 开源了 Helpful-Harmless 数据集（HH-RLHF），包括多轮对话场景下助手机器人的回答偏好。还有 OpenAssistant 等开源社区收集的人类反馈数据。这些数据集为没有资源组织大规模标注的团队提供了宝贵资源。然而不同数据集的侧重点可能不同，用别处的数据来对齐自己产品的价值观时要谨慎。例如Anthropic的Constitutional AI数据主要针对有害内容的偏好，而一般客服助手还需注重有用性/准确性等。工程上经常会**混合使用**开源偏好数据和少量自己领域的偏好数据，以既利用大规模通用数据，又包含特定场景的标注。

**6\. 偏好数据与提示数据的结合**：除了比较数据本身，RLHF 还需要**提示集（prompts）**来引导模型生成回答进行优化[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=Similarly%20to%20the%20reward%20model%2C,trained%20model.%5B%2014)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=The%20reward%20function%20is%20where,KL%29%20divergence)。这些提示可以来自用户实际问题、社区问答汇总，或者人工设计的任务。好的提示集应具有**多样性**和**代表性**，覆盖模型应用的各种话题和难度问题。Anthropic 的策略是先用人工与模型对话产生很多问题，然后筛选清洗。OpenAI 则部分利用真实用户API的查询。提示分布若过于单一，会导致模型在未见过的场景下泛化不佳[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=,challenging%20with%20limited%20preference%20data)。因此在数据准备阶段，既要有高质量的回答比较，也要确保提示多元。常见做法是先准备一个 prompts 列表，然后让模型生成回答交由人比对。后续强化学习时，也从这些 prompts 出发采样场景。这样可以保证训练和评价都在相似分布上。

总之，数据是 RLHF 的基础，其获取难度和重要性丝毫不亚于算法本身。**“巧妇难为无米之炊”**，如果没有充足且高质量的人类反馈，RLHF 再高级的算法也无法奏效[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=comparisons%20%28A%20,would%20be%20the%20pointwise%20scores)。因此，在实际项目中，一定要充分投入对数据/标注的设计和打磨。这通常包括：制定明确的标注规范、对标注者进行培训考核、采用重复标注和黄金集监控质量、积极收集覆盖产品重要场景的提示，并在过程中持续和标注团队沟通以统一标准。只有这样才能确保奖励模型学到的是**真实可靠**的偏好信号，为策略优化打下良好基础。

## 偏好对齐的技术路径对比 (Preference Alignment Methods and Variants)

传统的 RLHF 管线（SFT + 奖励模型 + PPO微调）已经证明有效，但也存在一些**局限**：例如训练流程复杂、需要同时维护多个模型，RL 训练不稳定且调参困难，偏好数据需求量大等[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=In%20previous%20posts%2C%20we%20started,Play%20Fine)[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=Feedback%20,unstable%20or%20hard%20to%20tune)。因此，近年业界和学界提出了多种改进策略，试图简化或替代 RLHF 的部分环节。在本节中，我们将介绍几种常见的**模型偏好对齐技术**，包括经典的 PPO 方法以及各种新近出现的替代算法。这些方法有的仍属于 RL 范式的改进，有的则完全舍弃了 RL 但依然能达到类似效果。

### 5.1 Proximal Policy Optimization (PPO) – 近端策略优化

**PPO** 是 OpenAI 于2017年提出的一种强化学习策略优化算法，也是目前 RLHF 中最常用的 RL 方法[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=The%20most%20widespread%20RL%20algorithm,preventing%20large%20shifts%20in%20behavior)。它之所以被广泛采用，原因在于 PPO 通过对策略更新幅度的限制，实现了**稳定高效**的策略训练[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=In%202017%2C%20researchers%20at%20Open,%E2%80%99)[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=It%E2%80%99s%20important%20to%20know%20these,before%20understanding%20DeepSeek%E2%80%99s%20GRPO%20implementation)。PPO 的思想核心是在每次基于梯度更新策略时，限制新旧策略的差异不要太大（通过剪切或者KL惩罚），从而防止策略崩溃[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=PPO%20%E2%80%94%20Clip%20relies%20on,through%20them%20one%20by%20one)[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=Advantage%20in%20PPO%20Clip)。这非常契合 RLHF 的需求——我们希望模型逐步对齐人类偏好，但又不能一步走太猛导致输出质量急剧恶化[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=The%20most%20widespread%20RL%20algorithm,preventing%20large%20shifts%20in%20behavior)。

在 RLHF 场景下，PPO 的实现通常如下：策略模型（LM）产生新回答，计算相对于参考模型的概率比 $r=\\frac{\\pi\_{\\theta}(y|x)}{\\pi\_{\\text{ref}}(y|x)}$，结合奖励模型分数形成目标，然后采用 PPO 的**剪切目标函数**限制 $r$ 不偏离 1 太多[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=PPO%20%E2%80%94%20Clip%20relies%20on,through%20them%20one%20by%20one)。也就是说，如果新策略和旧策略输出概率差别过大，损失函数会进行裁剪惩罚，鼓励策略变动在“小步范围”内[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=PPO%20%E2%80%94%20Clip%20relies%20on,through%20them%20one%20by%20one)。这种做法相当于**信任域策略优化**，避免一次更新导致输出分布与参考模型偏差太远。正如 PPO 论文标题所述，它试图回答：“如何在利用当前数据尽可能大地更新策略的同时，又不走过头导致性能崩塌？”[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=In%202017%2C%20researchers%20at%20Open,%E2%80%99)。

PPO 在 RLHF 中的效果得到了验证。OpenAI 表示他们选择 PPO 是因为它相对成熟，易于扩展到大模型的分布式训练[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=research%20problem,more%20on%20that%20later)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=research%20problem,more%20on%20that%20later)。在 ChatGPT 的训练中，PPO + KL 控制被证明能较好地平衡“追求奖励模型高分”和“保持输出合理”[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=probability%20distributions%20from%20the%20RL,KL%20divergence%20is%20approximated%20via)[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=papers%20from%20OpenAI%2C%20Anthropic%2C%20and,explained%20by%20John%20Schulman)。当然，PPO 也有一些参数需要调，比如截断范围 ε 和 KL 系数等，需要仔细调节以取得最佳效果[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=papers%20from%20OpenAI%2C%20Anthropic%2C%20and,explained%20by%20John%20Schulman)。总之，作为**RLHF的基准算法**，PPO 为后续各种变体提供了基础框架，也常被用来对比新方法的表现[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=The%20last%20result%20worth%20mentioning,in%20our%20previous%20blog%20posts)。

值得一提的是，一些教程和资料对 PPO 在 RLHF 中的应用有直观解释：比如 Turing Post 提到，PPO 会用奖励模型给输出打分，同时用参考模型计算 KL 惩罚（防止输出分布漂移），然后基于“优势函数”来更新策略[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=The%20most%20widespread%20RL%20algorithm,preventing%20large%20shifts%20in%20behavior)。优势函数衡量某输出比预期好多少，PPO 利用这个信号指导模型改进[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=The%20most%20widespread%20RL%20algorithm,preventing%20large%20shifts%20in%20behavior)。这一过程类似教师指导学生：既表扬（高分奖励）好的变化，也纠正（KL限制）偏离原知识太多的改动[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=Typically%2C%20RLHF%20and%20DPO%20use,the%20regularization%20doesn%27t%20sufficiently%20make)。因此 PPO 实现了一种**稳健的强化微调**，让大模型逐步贴近人类喜好而不失控。

### 5.2 Direct Preference Optimization (DPO) – 直接偏好优化

**DPO**（直接偏好优化）是 Stanford 等机构在2023年提出的一种**无需显式强化学习**的偏好对齐方法[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=In%20previous%20posts%2C%20we%20started,Play%20Fine)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Direct%20Preference%20Optimization)。它的核心思想是：**直接基于偏好数据优化策略模型**，跳过单独训练奖励模型和复杂的RL过程[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=Nevertheless%2C%20RLHF%20is%20complex%20and,Play%20Fine)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Direct%20Preference%20Optimization)。DPO 提供了一个闭-form的目标函数，使我们可以用类似**监督学习**的方式来融入人类比较偏好[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=At%20the%20core%20of%20DPO,expressed%20in%20a%20closed%20form)。

具体来说，DPO 从经典 RLHF 中的奖励函数推导出了策略的解析形式，发现可以通过最大化**偏好概率的对数比**来更新模型[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=At%20the%20core%20of%20DPO,expressed%20in%20a%20closed%20form)。DPO 的损失函数源自这样一个设想：如果我们有一个参考策略 $\\pi\_{\\text{ref}}$（通常就是SFT模型），以及当前策略 $\\pi\_{\\theta}$，我们希望对于每对比较 $(y\_w, y\_l)$ 满足：

$$
\log \frac{\pi_{\theta}(y_w|x)}{\pi_{\theta}(y_l|x)} = \text{some function of human preference}。
$$

经典 RLHF 通过训练奖励模型 $r(x,y)$ 来逼近这种关系，再PPO优化。而 DPO 则证明，可以直接以\*\*$\\log$ 概率比**作为优化目标，使得模型自己去匹配偏好顺序[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=Preference%20Optimization%20%28DPO%29%C2%A0,hypothesize%20that%20this%20discrepancy%20between)[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=data%2C%20eliminating%20the%20need%20for,may%20lead%20to%20suboptimal%20performance)。换言之，DPO 等价于把**奖励模型融入策略模型\*\*内部，用策略的 logit 差值来表示对偏好的信心[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=This%20is%20achieved%20through%20a,expressed%20in%20a%20closed%20form)。

训练时，DPO 方法会固定参考模型 $\\pi\_{\\text{ref}}$，只学习 $\\pi\_{\\theta}$，目标是让胜选回答的概率相对提高[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=data%2C%20eliminating%20the%20need%20for,may%20lead%20to%20suboptimal%20performance)。其推导结果表明，**策略的优化可以转换为一个逻辑斯蒂回归损失**，把比较偏好当作标签即可训练[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=policy%20models%2C%20enabling%20them%20to,simplifies%20the%20training%20process%20significantly)。这样完全避免了独立训练一个奖励网络，以及后续的PPO循环[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Experiments%20have%20shown%20that%20DPO,while%20enjoying%20several%20key%20advantages)。

DPO 的优势在于：

-   **简化流程**：不需要维护额外的奖励模型和价值模型，训练更简单稳定[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Experiments%20have%20shown%20that%20DPO,while%20enjoying%20several%20key%20advantages)。
    
-   **稳定性**：因为本质上是一个**离线优化**（Offline Optimization）问题，不存在PPO那种训练时策略分布不断变化的问题[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Experiments%20have%20shown%20that%20DPO,while%20enjoying%20several%20key%20advantages)。实验表明 DPO 在训练稳定性上优于PPO[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Experiments%20have%20shown%20that%20DPO,while%20enjoying%20several%20key%20advantages)。
    
-   **高效利用数据**：DPO 直接用偏好对优化策略，相当于充分利用了比较数据的信息，无需额外采样环境反馈[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Direct%20Preference%20Optimization)。一些研究者认为 DPO 更**样本高效**，因为每条比较直接贡献损失，没经过奖励模型拟合的损耗[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=Nevertheless%2C%20RLHF%20is%20complex%20and,Play%20Fine)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Direct%20Preference%20Optimization)。
    

实践中，DPO 已被许多开源模型采用。例如，Llama-2 和 Mistral 的一些对话版本就使用了 DPO 方法进行偏好对齐，被证明能取得与 RLHF 相当的性能[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=DPO%20is%20a%20simpler%20and,such%20as%20Llama%20and%20Mistral)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=popular%20choice%20and%20has%20been,such%20as%20Llama%20and%20Mistral)。Argilla 的博文指出，DPO 已成为许多模型的首选，因为它**简单且稳定**[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Direct%20Preference%20Optimization)。当然，DPO 也有局限：它仍需要大量偏好数据来拟合策略，如果比较数据稀少，效果会受影响[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=importance%20of%20having%20high,Play%20Fine)。此外，DPO 假设偏好比较可以转化为全局一致的分数，这在偏好不满足传递性时可能不完美[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=comparisons%20%28A%20,would%20be%20the%20pointwise%20scores)。

整体而言，DPO 是对 RLHF 的一大简化和创新。它展示了\*\*“没有RL也能学偏好”\*\*的可能性，证明通过巧妙的目标设计，可以用标准的语言模型微调过程来完成偏好对齐[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=At%20the%20core%20of%20DPO,expressed%20in%20a%20closed%20form)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=policy%20models%2C%20enabling%20them%20to,simplifies%20the%20training%20process%20significantly)。这为资源有限的团队提供了更容易实现的选项，也为后续其它偏好优化算法铺平了道路。

### 5.3 Simplified Preference Optimization (SimPO) – 简单偏好优化

**SimPO**（简单偏好优化）是 2024 年 Princeton 等机构提出的最新方法，它在 DPO 基础上进一步改进，强调让**奖励计算更贴合生成模型的度量**[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=In%20this%20new%20post%2C%20we,world%2C%20and%20the%20LLM%20behavior)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=Generally%2C%20once%20we%20have%20applied,that%20guides%20the%20generation%20model)。SimPO 名字中的 “Simple” 意味着其设计尽量**简化**且**直观**：**不用参考模型**，直接用模型自身的平均对数概率作为奖励，并加一个目标间距的超参数[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=learning%20from%20human%20feedback%20,and%20its%20latest%20variants%20across)[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=approach,We%20evaluated%20on%20extensive%20instruction)。

SimPO 和 DPO 的差异主要在**奖励函数**的定义上。DPO 的隐式奖励是策略与参考策略的 log 比值，而 SimPO 则直接使用**模型生成回答的平均 log 概率**作为隐式奖励[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=learning%20from%20human%20feedback%20,and%20its%20latest%20variants%20across)[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=approach,We%20evaluated%20on%20extensive%20instruction)。这样做的好处是：生成模型在推理时追求的是最大化自身概率（即提高答复的置信度），而 SimPO 用同样的度量来评价偏好对齐，使**训练目标和推理度量天然一致**[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=reward%20is%20formulated%20using%20the,may%20lead%20to%20suboptimal%20performance)[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=this%20reward%20formulation%20is%20not,may%20lead%20to%20suboptimal%20performance)。相比之下，DPO 的奖励用到了参考模型，会引入一个与实际生成无关的对比参照，SimPO 则完全**自洽**地只考虑当前模型[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=Nevertheless%2C%20RLHF%20is%20complex%20and,Play%20Fine)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=Optimization%C2%A0%28IPO%29%C2%A0and%20Kahneman,language%20models%20by%20learning%20from)。

除了奖励定义，SimPO 还引入了一个\*\*“目标奖励间隔”**（target reward margin）的概念[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=formulation%20better%20aligns%20with%20model,Our%20results%20demonstrate%20that%20SimPO)。这相当于希望模型在胜过另一回答时，不仅概率稍高，而且**高出一定幅度\*\*，从而增强胜者和败者的区分度[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=formulation%20better%20aligns%20with%20model,Our%20results%20demonstrate%20that%20SimPO)。这个间隔超参数鼓励模型进一步拉开优劣回答的概率差距，提高偏好对齐的**准确性**[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=existing%20preference%20DPO%20for%20each,of%20SimPO%20compared%20to%20DPO)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=the%20AlpacaEval%202%20LC%20win,of%20SimPO%20compared%20to%20DPO)。

实验结果显示，SimPO 在多项偏好基准上**优于 DPO**，包括 AlpacaEval 和 Arena 对话评测等[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=The%20results%20are%20straightforward%20when,of%20SimPO%20compared%20to%20DPO)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=existing%20preference%20DPO%20for%20each,of%20SimPO%20compared%20to%20DPO)。例如，在 AlpacaEval 2 上，SimPO 比 DPO 提升了约 3.8 到 6.4 个胜率点，在更难的 Arena-Hard 基准上提升了 1.2 到 7.5 点[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=The%20results%20are%20straightforward%20when,of%20SimPO%20compared%20to%20DPO)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=existing%20preference%20DPO%20for%20each,of%20SimPO%20compared%20to%20DPO)。这些一致的提升表明 SimPO 确实在对齐效果和稳定性上更胜一筹[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=The%20results%20are%20straightforward%20when,of%20SimPO%20compared%20to%20DPO)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=existing%20preference%20DPO%20for%20each,of%20SimPO%20compared%20to%20DPO)。更重要的是，SimPO 在诸多对比方法中也表现突出，一般只被它的一个变体 R-DPO 略微赶上，其余如 ORPO、IPO、KTO 等大多不及 DPO，而 SimPO 则全面领先[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=The%20last%20result%20worth%20mentioning,in%20our%20previous%20blog%20posts)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=We%20see%20in%20bold%20that,DPO)。因此 SimPO 被认为是目前**最有效的离线偏好优化方法之一**[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=The%20last%20result%20worth%20mentioning,in%20our%20previous%20blog%20posts)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=We%20see%20in%20bold%20that,DPO)。

需要说明的是，SimPO 虽然效果亮眼，但其成功的**理论原因**尚不完全清楚[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=One%20last%20thought%20on%20this,for%20such%20acknowledgement%20and%20transparency)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=authors,for%20such%20acknowledgement%20and%20transparency)。作者指出，为什么简单地改用平均对数概率当奖励就如此有效，背后缺乏严谨证明[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=One%20last%20thought%20on%20this,for%20such%20acknowledgement%20and%20transparency)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=authors,for%20such%20acknowledgement%20and%20transparency)。目前推测是因为这样做让**训练和生成的一致性**更好，使模型学到的偏好真正反映在生成概率里[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=In%20this%20new%20post%2C%20we,world%2C%20and%20the%20LLM%20behavior)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=Generally%2C%20once%20we%20have%20applied,that%20guides%20the%20generation%20model)。另一个需要手动调节的因素是前述“奖励间隔”超参数，不同设置下效果会变化，这提示我们缺乏理论指导去设定最佳值[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=One%20concrete%20argument%20regarding%20the,test%20this%20kind%20of%20outcome)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=One%20concrete%20argument%20regarding%20the,test%20this%20kind%20of%20outcome)。此外，SimPO 目前主要验证了在助理模型帮助/有害维度上的效果，对模型**安全性**和**诚实性**等方面是否也成立还有待测试[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=One%20concrete%20argument%20regarding%20the,test%20this%20kind%20of%20outcome)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=manually%2C%20and%20further%20research%20should,test%20this%20kind%20of%20outcome)。

总之，SimPO 体现了一种**更直接、贴近模型本身**的偏好优化思路。它去掉了参考模型，减轻了算力和内存需求[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=learning%20from%20human%20feedback%20,and%20its%20latest%20variants%20across)[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=approach,We%20evaluated%20on%20extensive%20instruction)，又通过对称的奖励定义提升了对齐度[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=reward%20is%20formulated%20using%20the,may%20lead%20to%20suboptimal%20performance)[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=this%20reward%20formulation%20is%20not,may%20lead%20to%20suboptimal%20performance)。SimPO 的成功激励研究者去思考偏好优化中一些习以为常做法（如引入参考模型）的必要性，探索更简单有效的替代方案。

### 5.4 Odds Ratio Preference Optimization (ORPO) – 比值偏好优化

**ORPO**（Odds Ratio Preference Optimization）是2023年提出的一种**单阶段**偏好优化方法，其目标是**将指令微调和偏好对齐合并为一个过程**[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-8/#:~:text=ORPO%20combines%20instruction%20tuning%20and,free%20and%20computationally%20more%20efficient)。传统RLHF流程需要先SFT再偏好优化，而 ORPO 希望训练一个模型直接**既符合监督数据又符合偏好数据**，从而避免多阶段训练的开销[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-8/#:~:text=ORPO%20combines%20instruction%20tuning%20and,free%20and%20computationally%20more%20efficient)。ORPO 名称中的 “Odds Ratio” 暗示它使用了**胜算比**（odd ratio）的概念来构造目标函数，使得参考模型不再需要[arxiv.org](https://arxiv.org/html/2403.07691v2#:~:text=ORPO%3A%20Monolithic%20Preference%20Optimization%20without,and%20DPO%20in%20two)。

简单来说，ORPO 的训练损失融合了**监督学习损失**和**偏好损失**。它假设我们有一批指令-理想响应的数据（比如SFT数据），以及一批比较偏好数据。ORPO 通过最大化**所选响应与被拒响应概率之比**，同时对齐指令数据上的交叉熵损失，从而达到一箭双雕[arxiv.org](https://arxiv.org/html/2403.07691v2#:~:text=ORPO%3A%20Monolithic%20Preference%20Optimization%20without,and%20DPO%20in%20two)。因为采用了**比值形式**，ORPO 不需要参考模型基线，直接在最终模型上优化，使得模型既学会忠实地遵循指令，又在有偏好比较的地方更倾向人类偏好的输出[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-8/#:~:text=ORPO%20combines%20instruction%20tuning%20and,free%20and%20computationally%20more%20efficient)。这为训练节省了一轮参考模型推理的开销，也减少了代码复杂度。

Argilla 的团队评价 ORPO **简化了对齐过程**，因为参考模型的移除让训练更高效[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-8/#:~:text=ORPO%20combines%20instruction%20tuning%20and,free%20and%20computationally%20more%20efficient)。ORPO 的论文指出，在同等数据下，ORPO 模型可以**胜过**“SFT + DPO”两阶段方法的效果，同时训练成本更低[arxiv.org](https://arxiv.org/html/2403.07691v2#:~:text=ORPO%3A%20Monolithic%20Preference%20Optimization%20without,and%20DPO%20in%20two)。这说明直接联合优化并不会互相干扰，反而可能带来正向增益。

需要注意 ORPO 的应用场景：它尤其适合**从头（base模型）直接微调**的情况。如果我们有一个预训练模型，没有足够资源先SFT再RLHF，那么直接用 ORPO 算法在混合了监督信号和偏好信号的数据上训练，就能一步得到一个对齐模型[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-8/#:~:text=ORPO%20combines%20instruction%20tuning%20and,free%20and%20computationally%20more%20efficient)。Hugging Face 的博客示例曾演示过用 ORPO 微调 Llama-3 8B 模型，结果相当不错[huggingface.co](https://huggingface.co/blog/mlabonne/orpo-llama-3#:~:text=Fine,the%20LLM%20Course%20on)。

ORPO 的出现体现了这样一个趋势：**训练范式的合并**。与其拆分多个阶段分别优化模型，不如设计一个统一的目标，同时吸收各种信号。这样做的挑战是要平衡不同目标，比如偏好优化倾向于让模型探索多样输出、提升强项，而监督信号要求模型模仿具体答案。如果处理不好，模型可能顾此失彼。但 ORPO 的成功案例表明，至少在偏好对齐任务上，这种平衡是可行的，而且能带来训练效率和效果的双赢[arxiv.org](https://arxiv.org/html/2403.07691v2#:~:text=ORPO%3A%20Monolithic%20Preference%20Optimization%20without,and%20DPO%20in%20two)。

### 5.5 Identity Preference Optimization (IPO) – 恒等偏好优化

**IPO**（Identity Preference Optimization）是 DeepMind 团队提出的一种改进 DPO 的方法，主要为了解决 DPO 可能出现的**过拟合**和**正则不充分**问题[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=Identity%20preference%20optimization%20%28IPO%29,noise%20in%20the%20preference%20data)[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=In%20summary%2C%20IPO%20can%20control,and%20the%20KL%20term%20fails)。其思路是在 DPO 的优化目标中加入**额外的正则化项**，并对偏好概率分布做一个恒等（identity）映射处理，使得当偏好数据几乎确定（接近0或1概率）时，模型不会疯狂放大输出差异[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=Identity%20preference%20optimization%20%28IPO%29,noise%20in%20the%20preference%20data)[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=In%20summary%2C%20IPO%20can%20control,and%20the%20KL%20term%20fails)。

简单来说，DPO 中假设可以用 Bradley-Terry 模型将比较偏好转换为点值奖励，但当偏好非常确定（比如某回答几乎总被选为胜者）时，这种点值模型会给出非常极端的奖励，从而削弱 KL 正则的作用[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=logit,problem%20later%20in%20this%20post)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=On%20one%20hand%2C%20the%20researchers,and%20the%20potential%20for%20overfitting)。IPO 则引入一个\*\*$\\Psi$ 函数**对偏好概率做变换，使得不会出现特别极端的值[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=Foremost%2C%20IPO%20first%20applies%20a,by%20heavily%20skewing%20the%20preference)[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=over%20a%20human%20preference%20dataset,stage%20by%20the%20following%20objective)。具体的实现是用**Logit 函数\*\* $\\Psi(q) = \\log(\\frac{q}{1-q})$ 来平滑原始偏好 $q$[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=Foremost%2C%20IPO%20first%20applies%20a,by%20heavily%20skewing%20the%20preference)。然后在优化目标中，加上一个额外的**二次损失**衡量策略模型给出的 log 概率差与 $\\Psi(q)$ 之差的平方[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=%7B%5Cdisplaystyle%20p%5E%7B,given%20%7D%7Dx%5C%7D%5D%7D%20en.wikipedia.org)[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=Image%3A%20,1%7D%5D%5E%7B2%7D%5Cend%7Baligned)。直观理解，这就像是在强制策略模型的 logit 差距（相当于隐式奖励）不要偏离某个范围，以免过度迎合偏好数据。

IPO 名称中的“Identity”来源于其论文提出了一个更广义的 $\\Psi$-PO 框架，其中 $\\Psi$ 是任意变换函数，而**选择恒等函数**（Identity）就是 IPO 特例[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=To%20better%20understand%20how%20these,by%20adjusting%20the%20training%20process)[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=over%20a%20human%20preference%20dataset,stage%20by%20the%20following%20objective)。DeepMind 的分析显示，IPO 的这种正则让模型在偏好数据接近确定时仍保持一定的**谨慎**，避免偏执地放大某些概率差，从而**缓解过拟合**[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=In%20summary%2C%20IPO%20can%20control,and%20the%20KL%20term%20fails)。毕竟，人类偏好数据本身可能有噪声或不一致，如果模型当真百分百相信偏好数据而完全舍弃原模型分布，可能会学到奇怪的偏差。IPO 则通过这个二次惩罚项，确保模型**始终被拉向参考模型**一些，不会因为偏好数据而走极端[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=%5BI%28y%2Cy%27%29%5D%3Dp_)。

实验表明，IPO 尤其在偏好数据**近乎确定**（如某回答几乎总赢）情况下有效地防止了策略退化[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=In%20summary%2C%20IPO%20can%20control,and%20the%20KL%20term%20fails)。它也被视为对 DPO 的一种**正则化增强**，从理论上统一了 RLHF 和 DPO 等目标为 $\\Psi$PO 框架[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=On%20one%20hand%2C%20the%20researchers,and%20the%20potential%20for%20overfitting)。Hippocampus 的综述提到，IPO 使用了**有界函数**来聚合偏好，从而保证即使偏好概率趋近0或1，KL 正则仍然有效[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=maintain%20fluency)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Identity,overfitting%20to%20the%20preference%20dataset)。这提高了模型泛化能力，因为模型不会死记硬背偏好数据的每个细节，而是在参考模型基础上适度调整[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=In%20summary%2C%20IPO%20can%20control,and%20the%20KL%20term%20fails)。

需要注意的是，IPO 仍然属于离线偏好优化方法的一种改进，其实现类似 DPO，只是目标函数多了一项，所以训练流程并没有比 DPO 复杂多少[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=,TRL%20to%20access%20this%20feature)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=On%20one%20side%2C%20they%20noted,and%20maximizes%20it%20to)。Hugging Face 的 TRL 库也已支持 IPO 损失，只需切换一下损失函数即可使用这种正则[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=,TRL%20to%20access%20this%20feature)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=integrated%20into%20the%20DPO%20trainer,TRL%20to%20access%20this%20feature)。

总的来说，IPO 针对 DPO 的薄弱环节（对确定性偏好过拟合）提出了解决方案，使偏好优化更健壮、更具理论保证[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=Identity%20preference%20optimization%20%28IPO%29,noise%20in%20the%20preference%20data)。在实际应用中，如果发现模型偏好对齐时容易在训练数据上表现**过分自信**而对新样本**泛化不佳**，IPO 提供了一种可能的补救思路。

### 5.6 Kahneman-Tversky Optimization (KTO) – 卡尼曼-特沃斯基优化

**KTO**（Kahneman-Tversky Optimization）是受行为经济学的**前景理论**（Prospect Theory）启发而提出的一种偏好对齐算法[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=Kahneman,not%20maximize%20the%20expected%20value)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Kahneman,where%20preference%20data%20is%20limited)。其名字来源于前景理论的提出者 Daniel Kahneman 和 Amos Tversky。KTO 的核心在于，它认为人类在决策时往往**不追求简单的期望值最大化**，而是对**损失和收益**赋予不同的心理权重[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=Kahneman,not%20maximize%20the%20expected%20value)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=KTO%20leverages%20the%20concept%20of,observed%20in%20other%20tested%20methods)。因此在偏好对齐中，KTO 引入了所谓\*\*“人类感知损益”的损失函数\*\*，希望模型能贴合人类这种非线性偏好模式[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=In%20general%2C%20KTO%20seeks%20to,by%20the%20general%20HALO%20objective)。

具体而言，KTO 定义了一类新的**人类感知损失（HALO）**：对于一个 (prompt, response) 对，令 $r\_{\\theta}(x,y)$ 表示模型的打分（可以理解为奖励模型输出），KTO 设计一个**价值函数 $v(\\cdot)$ 来转换 $r\_{\\theta}$**[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=In%20general%2C%20KTO%20seeks%20to,by%20the%20general%20HALO%20objective)。这个价值函数体现了人类对增量收益/损失的敏感度——通常在人类决策中，**损失带来的痛苦大于等额收益带来的快乐**，且有一个参考点[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=KTO%20leverages%20the%20concept%20of,observed%20in%20other%20tested%20methods)。KTO 把**参考点**设为对某 query 来说模型输出的一般水平（例如所有可能输出的期望值），然后计算当前输出相对于参考点的“收益”或“损失”[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=In%20general%2C%20KTO%20seeks%20to,by%20the%20general%20HALO%20objective)。再通过 $v$ 函数将这种相对差异映射成人类主观价值。最终，KTO 的优化目标是**最大化这种主观价值的期望**[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=In%20general%2C%20KTO%20seeks%20to,by%20the%20general%20HALO%20objective)。

更直观一点，KTO 不直接用人类偏好概率来算损失，而是用**带权重的增益函数**。例如，如果一个回答比参考好一点，普通方法可能给它线性+1的奖励，但 KTO 可能给>+1的“主观价值”（如果人倾向于追求增益）；反之，一个回答比参考差一点，KTO 可能给予-2的价值惩罚（因为人们厌恶损失）[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=KTO%20leverages%20the%20concept%20of,observed%20in%20other%20tested%20methods)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=gains%20or%20losses%20relative%20to,based%20methods%20like)。这样一来，模型在训练时会更避免产生让人强烈反感的输出（因为惩罚更大），同时对于稍好的改进可能相对奖励略小（因为人对收益敏感度低于对损失）[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=KTO%20leverages%20the%20concept%20of,observed%20in%20other%20tested%20methods)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=gains%20or%20losses%20relative%20to,based%20methods%20like)。

KTO 的一大优点是，它**不需要成对偏好比较数据**，只需二元标签（好/不好）即可训练[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Kahneman,where%20preference%20data%20is%20limited)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=the%20utility%20of%20model%20outputs,where%20preference%20data%20is%20limited)。因为前景理论本质上处理的是单一样本的价值增益，所以我们只需一个回答是可接受或不可接受的标记即可。这大大简化了数据需求，适合在**只有用户点赞/踩反馈**的场景使用[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=the%20utility%20of%20model%20outputs,where%20preference%20data%20is%20limited)。DeepMind 的实验表明，KTO 在只用正负反馈的数据情况下，也能达到与 DPO 等需要精细比较数据的算法相当甚至更好的效果[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=KTO%20leverages%20the%20concept%20of,observed%20in%20other%20tested%20methods)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=is%20greater%20than%20the%20pleasure,observed%20in%20other%20tested%20methods)。而且 KTO 甚至在**无监督微调**（无SFT）的模型上直接优化也能奏效[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=is%20greater%20than%20the%20pleasure,observed%20in%20other%20tested%20methods)——这是其他方法未能做到的。

KTO 将行为经济学引入 AI 对齐领域，是一个颇具想象力的尝试。它提醒我们，人类偏好不一定符合简单的概率模型或期望最大化原则，考虑**人类决策的心理偏差**可能会得到更合适的对齐方式[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=Kahneman,not%20maximize%20the%20expected%20value)。KTO 目前还算新颖，应用案例不多，但如果您所在领域有大量简单的二分类反馈（比如用户是否满意的打分），KTO 可能是一条值得探索的路线。

### 5.7 Rank Responses to Human Feedback (RRHF) – 回答排序对齐方法

**RRHF**（有时也称为 Reward-Rank Hindsight Fine-tuning）是一种于2023年提出的无需传统RL的对齐范式[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=%E2%80%93%20very%20interesting%20variations%20of,to%20what%20human%20alignment%20is)[github.com](https://github.com/opendilab/awesome-RLHF#:~:text=Awesome%20RLHF%20,with%20Human%20Feedback%20without%20tears)。它的思路是：**让模型一次性生成多个回答，并学会对这些回答排序，使其概率分布与人类偏好排序相符**[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=In%20contrast%2C%20we%20propose%20a,We%20evaluate%20RRHF)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=probabilities%20and%20learns%20to%20align,Harmless%20dataset%2C%20demonstrating%20comparable%20alignment)。可以理解为，把原本分步的“生成 -> 人工选择 -> 优化”过程改为**单步的排序学习**。

RRHF 的具体实现通常如下：对于每个提示，模型（或模型+一些其他来源）生成N个不同的回答[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=In%20contrast%2C%20we%20propose%20a,We%20evaluate%20RRHF)。然后通过人工或其他方式得到这N个回答的偏好排序（或打分）。接着，定义模型的一个评分函数，例如使用**对数概率**$\\log P\_{\\theta}(y\_i|x)$作为原始得分[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=In%20contrast%2C%20we%20propose%20a,We%20evaluate%20RRHF)。RRHF 的目标是调整模型参数，使得这些原始得分的**相对大小**与人类偏好排序一致[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=In%20contrast%2C%20we%20propose%20a,We%20evaluate%20RRHF)。通常用**排序损失**来训练，例如 listwise 的 Softmax Cross-Entropy 或 pairwise 的对比损失，使得模型倾向于赋予人类偏好高的回答更大的概率[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=In%20contrast%2C%20we%20propose%20a,We%20evaluate%20RRHF)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=probabilities%20and%20learns%20to%20align,Harmless%20dataset%2C%20demonstrating%20comparable%20alignment)。

这样，RRHF 等于是在做一个**排序学习**（Learning to Rank）的任务[openreview.net](https://openreview.net/pdf?id=EdIGMCHk4l#:~:text=,robustly%20without%20complex%20hyperparameter%20tuning)。它所需的模型只有**1~2个**：可能只需调整主模型，或者额外用一个辅助模型提供候选答案[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=including%20the%20model%20responses%20from,language%20models%20with%20human%20preferences)。不像 RLHF/PPO 需要策略、价值、奖励三模型齐备。正因如此，RRHF 实现起来更简单，超参数也更少[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=including%20the%20model%20responses%20from,Additionally%2C%20RRHF%20can%20be)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=during%20tuning%20and%20can%20efficiently,We%20evaluate%20RRHF)。作者形容，相比 PPO，RRHF **没有复杂的超参调节**，也不会因为值函数不准导致训练不稳定[dl.acm.org](https://dl.acm.org/doi/10.5555/3666122.3666604#:~:text=RRHF%3A%20rank%20responses%20to%20align,preferences%20robustly%20without%20complex)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=including%20the%20model%20responses%20from,Additionally%2C%20RRHF%20can%20be)。

RRHF 的一个关键优势是，它**可以利用来自不同来源的样本**[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=In%20contrast%2C%20we%20propose%20a,We%20evaluate%20RRHF)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=probabilities%20and%20learns%20to%20align,Harmless%20dataset%2C%20demonstrating%20comparable%20alignment)。例如，一部分回答可以来自当前模型自身，一部分来自更强的外部模型（如 GPT-4），还有一部分甚至是人写的参考答案。RRHF 能将这些杂糅的回答放在一起进行排序学习。这种灵活性很有吸引力，因为我们可以充分利用外部强大模型产生的大量示例作为对比，让较小的模型进行学习\*\*“向更好的看齐”\*\*[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=In%20contrast%2C%20we%20propose%20a,We%20evaluate%20RRHF)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=probabilities%20and%20learns%20to%20align,Harmless%20dataset%2C%20demonstrating%20comparable%20alignment)。

实验上，RRHF 在 OpenAI 的Helpful/Harmless数据集上达到了跟 PPO 相当的效果，无需复杂的 RL 过程[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=considered%20an%20extension%20of%20SFT,Extensive)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=on%20the%20Helpful%20and%20Harmless,available%20at%20%2017%20this)。另外有研究发现，RRHF 的性能高度取决于提供的候选响应的质量：如果候选集中包含高质量回答，模型就能学到更多[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=considered%20an%20extension%20of%20SFT,Extensive)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=on%20the%20Helpful%20and%20Harmless,available%20at%20%2017%20this)。这意味着RRHF本质上是一个\*\*“best-of-n学习者”\*\*，它擅长从n个候选中挑最好的[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=considered%20an%20extension%20of%20SFT,Extensive)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=on%20the%20Helpful%20and%20Harmless,available%20at%20%2017%20this)。因此提升候选回答的覆盖面和质量，对RRHF效果很重要。

RRHF 可以被看作是 SFT 和排名监督的一种融合，与其说是 RL，不如说是**排序版的有监督细调**[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=including%20the%20model%20responses%20from,We%20evaluate%20RRHF)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=during%20tuning%20and%20can%20efficiently,We%20evaluate%20RRHF)。它避免了策略不稳定、值模型偏差这些难题，对工程友好。这一思路对那些想实现RLHF效果但被RL复杂性劝退的团队很有吸引力：用几行 Ranking Loss 替代上千行 RL 代码，就能让模型对齐人类偏好。这也是 RRHF 作者所说的“无需眼泪（without tears）”的缘由[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=,this%20version%2C%20v3)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=sensitive%20to%20hyperparameters%20and%20requires,language%20models%20with%20human%20preferences)。

### 5.8 Group Relative Policy Optimization (GRPO) – 分组相对策略优化

**GRPO**（Group Relative Policy Optimization）是一种**强化学习算法**改进，最初由开源项目 DeepSeek 在2024年应用于大模型训练[yugeten.github.io](https://yugeten.github.io/posts/2025/01/ppogrpo/#:~:text=DeepSeek%20also%20make%20the%20RLHF,a%20separate%20critic%20model)[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=DeepSeek,ago%20in%20the%20DeepSeekMath%20paper)。GRPO 针对标准 PPO 存在的一个问题：需要训练**单独的价值网络**来估计优势，这增加了训练不稳定性和计算量[reddit.com](https://www.reddit.com/r/LLMDevs/comments/1ibhpqw/how_was_deepseekr1_built_for_dummies/#:~:text=How%20was%20DeepSeek,3)[together.ai](https://www.together.ai/deepseek#:~:text=DeepSeek%20Models%20Family%20,advantage%20estimation%20to%20cut)。GRPO 的创新之处在于**去掉了单独的价值函数**，转而利用**分组的相对优势估计**来进行策略更新[reddit.com](https://www.reddit.com/r/LLMDevs/comments/1ibhpqw/how_was_deepseekr1_built_for_dummies/#:~:text=DeepSeek%20uses%20GRPO%2C%20a%20pure,3)[together.ai](https://www.together.ai/deepseek#:~:text=%2A%20,GRPO)。

具体来说，GRPO 会让模型针对同一提示一次生成**多条不同的回答**，将这些回答视为一个**分组**。然后根据奖励模型或其他评估方法，对该组回答计算出每个的得分，并据此算出它们相对于组内平均水平的优势（advantage）[reddit.com](https://www.reddit.com/r/LLMDevs/comments/1ibhpqw/how_was_deepseekr1_built_for_dummies/#:~:text=How%20was%20DeepSeek,3)[together.ai](https://www.together.ai/deepseek#:~:text=%2A%20,GRPO)。这样，无需训练价值网络，我们也可以知道某个回答比“组平均”好还是坏多少。之后，GRPO 使用这些相对优势来更新策略参数。

举例说明：假设每次从策略模型针对提示采样3个回答，奖励模型打分分别为 A:0.8, B:0.5, C:0.2。那么组平均得分约0.5，回答A高于平均0.3，被视为正优势；C低于平均0.3，是负优势；B近乎平均略高。PPO 需要价值网络预测这些优势，而 GRPO 直接由**组内比较**得到[together.ai](https://www.together.ai/deepseek#:~:text=%2A%20,GRPO)。然后GRPO更新策略时让产生A的概率上升，让C的概率下降，程度按优势大小。由于每组内部自身提供了基准，\*\*不需要另一个模型预测“基线”\*\*了。

GRPO 的好处在于：**计算量减少**（少了价值网络的前向和训练）以及**训练稳定**。价值网络往往难精确预测大模型每个输出的真实期望回报，误差会影响策略更新。而 GRPO 取巧地利用了**一次生成的多样性**作为参考，不受长远不确定性的影响[reddit.com](https://www.reddit.com/r/LLMDevs/comments/1ibhpqw/how_was_deepseekr1_built_for_dummies/#:~:text=How%20was%20DeepSeek,3)[together.ai](https://www.together.ai/deepseek#:~:text=%2A%20,GRPO)。Together 的官方说明指出，GRPO **通过组内相对优势估计，降低了计算要求，同时保持训练稳定性**[yugeten.github.io](https://yugeten.github.io/posts/2025/01/ppogrpo/#:~:text=DeepSeek%20also%20make%20the%20RLHF,a%20separate%20critic%20model)[together.ai](https://www.together.ai/deepseek#:~:text=%2A%20,GRPO)。

DeepSeek 团队在其 R1 模型训练中使用 GRPO 取得了成功。他们甚至**完全跳过了有监督微调**这一步，直接用纯 RL（GRPO）训练模型，从而赋予模型很强的推理和自我改进能力[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=that%20has%20led%20to%20better,time%20compute)[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=Why%20is%20RL%20important%20in,the%20context%20of%20LLMs)。这被认为是首次在无SFT的情况下，通过RL实现大型语言模型的强推理（emergent reasoning）能力[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=Reinforcement%20Learning,evolution)[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=environment%20and%20receive%20feedback)。GRPO 在其中功不可没，它让纯RL大模型训练成为可能，因为去掉价值网络减轻了许多不稳定因素[together.ai](https://www.together.ai/deepseek#:~:text=training%20stability)[together.ai](https://www.together.ai/deepseek#:~:text=%2A%20,GRPO)。

总而言之，GRPO 可以被视为对 PPO 的一种结构优化：用\*\*“群体智慧”**替代**“单独先知”\*\*（价值函数）。对于多轮生成且想提升效率的 RLHF 训练来说，这是一条很有潜力的方向。例如，我们可以让模型针对每个 prompt 一次输出k个回答，组内排序判优，再进行策略更新，而不是每次只输出一个回答依赖价值模型评估。GRPO 已在开源社区引起关注，如果您追求更高的 RLHF 训练效率或考虑纯RL方案，值得进一步研究这一方法。

**小结：** 本节介绍了多种 RLHF 相关的偏好对齐技术，归纳如下：

-   **PPO**：经典的策略梯度算法，借助KL惩罚稳定更新，是RLHF基石[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=The%20most%20widespread%20RL%20algorithm,preventing%20large%20shifts%20in%20behavior)。
    
-   **DPO**：抛弃显式RL，直接用比较数据优化策略，简化流程且效果稳健[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Direct%20Preference%20Optimization)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Experiments%20have%20shown%20that%20DPO,while%20enjoying%20several%20key%20advantages)。
    
-   **SimPO**：对DPO改进，用模型自身log概率当奖励，更直观高效，当前表现领先[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=The%20results%20are%20straightforward%20when,of%20SimPO%20compared%20to%20DPO)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=The%20last%20result%20worth%20mentioning,in%20our%20previous%20blog%20posts)。
    
-   **ORPO**：将SFT和偏好优化合一，单阶段训练，无需参考模型[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-8/#:~:text=ORPO%20combines%20instruction%20tuning%20and,free%20and%20computationally%20more%20efficient)[arxiv.org](https://arxiv.org/html/2403.07691v2#:~:text=ORPO%3A%20Monolithic%20Preference%20Optimization%20without,and%20DPO%20in%20two)。
    
-   **IPO**：对DPO正则化，防止过拟合偏好数据，处理确定性偏好的鲁棒方案[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=Identity%20preference%20optimization%20%28IPO%29,noise%20in%20the%20preference%20data)[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=In%20summary%2C%20IPO%20can%20control,and%20the%20KL%20term%20fails)。
    
-   **KTO**：引入行为经济学损失，支持二元反馈，用前景理论建模人类价值[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Kahneman,where%20preference%20data%20is%20limited)[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=KTO%20leverages%20the%20concept%20of,observed%20in%20other%20tested%20methods)。
    
-   **RRHF**：多答排序学习，不用PPO，直接学模型概率与人类排序一致，易实现超参少[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=In%20contrast%2C%20we%20propose%20a,We%20evaluate%20RRHF)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=including%20the%20model%20responses%20from,Additionally%2C%20RRHF%20can%20be)。
    
-   **GRPO**：替换PPO的更新机制，组内优势估计，无需值网络，适合大模型纯RL训练[together.ai](https://www.together.ai/deepseek#:~:text=%2A%20,GRPO)[together.ai](https://www.together.ai/deepseek#:~:text=training%20stability)。
    

不同方法各有侧重：有的着眼于**简化工程**（如DPO/SimPO/RRHF），有的聚焦于**理论完善**（如IPO/KTO），有的提升**性能与稳定**（如SimPO/GRPO），还有的优化**资源利用**（如ORPO 单阶段、GRPO 无值网）。在实际应用中，选择哪种方法应根据团队资源、数据情况、模型规模等因素：如果有大量比较数据且可承受复杂训练，可用经典RLHF/PPO；如数据有限或需快速实现，可考虑DPO/SimPO；如只有用户正负反馈，KTO 是选项；追求低成本实现，RRHF 很有吸引力；而如想探索更高性能的RL训练，GRPO 等创新也值得关注。

## 辅助机制与增强策略 (Auxiliary Mechanisms and Enhancements)

除了上文讨论的直接偏好优化算法外，还有一些**辅助机制**可以与 RLHF 或其替代方法配合使用，以进一步改进模型行为。这些机制有的用于**降低对人工标注的依赖**，有的用于**改进模型的价值观对齐**，也有的用于**提高训练评价效率**。本节介绍几种目前备受关注的辅助技术，包括从 AI 获取反馈、使用大模型作为评审、以及 Anthropic 提出的宪法式 AI 等。

### 6.1 Reinforcement Learning from AI Feedback (RLAIF) – 来自AI反馈的强化学习

**RLAIF**（Reinforcement Learning from AI Feedback）指利用**人工智能模型**而非人工来提供反馈信号，完成类似 RLHF 的训练流程[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=For%20this%20one%2C%20we%E2%80%99d%20like,labelled%20data)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=Building%20on%20top%20of%20Anthropic%2C,making%20this%20process%20less%20complex)。它的动机非常直接：RLHF 受限于昂贵且稀缺的人类标注，如果能用一个强大的 AI 模型来代替人给出偏好评价，那么可以**极大扩展**反馈数据量、降低成本[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=Feedback%20,labelled%20data)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=Building%20on%20top%20of%20Anthropic%2C,making%20this%20process%20less%20complex)。早在 2022 年，Anthropic 的**宪法式 AI**理念就已包含了让 AI 根据一套原则来评判和改写模型输出的雏形（详见下节）[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=they%20devised%20this%20method%20in,the%20concept%20of%20Constitutional%20AI)。但真正明确对比 RLAIF 和 RLHF 的是 2023 年 Google Research 的工作[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=Building%20on%20top%20of%20Anthropic%2C,making%20this%20process%20less%20complex)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=that%20directly%20prompting%20the%20LLM,making%20this%20process%20less%20complex)。

RLAIF 的实现需要一个**反馈模型**（AI Labeler），通常选择比目标模型更强大或更可靠的大模型来承担。例如，用 GPT-4 来评价一个较小模型的回答优劣。具体流程可能是：给定一个 prompt 和两份候选回答，我们让 AI 反馈模型根据预先设定的准则（如准确、礼貌、无害等）输出一个**评分或偏好判断**[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=Contrary%20to%20RLHF%2C%20this%20approach,preference%2C%20between%200%20and%201)。这样每对回答得到一个0到1之间的偏好分数[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=Contrary%20to%20RLHF%2C%20this%20approach,preference%2C%20between%200%20and%201)。以这些 AI 生成的“软标签”为数据，训练奖励模型（或有时**直接跳过奖励模型**，详述见下）[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=After%20labelling%20the%20preferences%20through,assign%20rewards%20to%20model%20responses)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=policy%20model%2C%20using%20the%20RM,assign%20rewards%20to%20model%20responses)。后续就跟 RLHF 相同，用这个奖励信号做强化学习更新策略。

RLAIF 最初在 Anthropic 的宪法AI中用于**无害性对齐**：他们用一组原则（宪法）指导一个辅助模型去评判对话中的有害程度并提供改进意见[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=they%20devised%20this%20method%20in,the%20concept%20of%20Constitutional%20AI)。只用很少的人类定义规则（宪法）和几乎全程 AI 自己反馈，他们训练出了一个在安全性上很强的助手模型[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=they%20devised%20this%20method%20in,the%20concept%20of%20Constitutional%20AI)。Google 的研究进一步**直接比较**了 RLAIF 与 RLHF，在摘要、生成人机对话有益性、无害性等任务上发现，RLAIF 训练的策略模型在这些维度上**等于或优于** RLHF 模型[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=Building%20on%20top%20of%20Anthropic%2C,making%20this%20process%20less%20complex)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=RLAIF%20vs%20RLHF)。例如，他们报告 RLAIF 和 RLHF 政策在人工评价中旗鼓相当，偏好于它们的比例接近，而都显著好过仅监督模型[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=RLAIF%20vs%20RLHF)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=current%20results%20in%20the%20state,than%20getting%20equivalent%20human%20annotations)。重要的是，RLAIF 的成本估计只有人工标注的约十分之一[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=RLAIF%20vs%20RLHF)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=current%20results%20in%20the%20state,than%20getting%20equivalent%20human%20annotations)。

RLAIF 有两种常见实现模式：

-   **蒸馏式（Distilled）**：即**两阶段**。先用 AI 模型给大量比较生成软标签（可能是胜率或评分分布），然后训练一个奖励模型拟合这些标签，再进行强化学习[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=After%20labelling%20the%20preferences%20through,assign%20rewards%20to%20model%20responses)。这类似RLHF，只是将“人”换成了“AI”。
    
-   **直接式（Direct）**：**单阶段**。直接将AI模型的评分用作策略更新的奖励，不训练单独奖励模型[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=policy%20model%2C%20using%20the%20RM,assign%20rewards%20to%20model%20responses)。例如提示 GPT-4 给每个回答一个1-10的打分，取其Softmax归一化为概率，再线性变换到-1到1作为即时奖励[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=However%2C%20an%20alternative%20method%20that,used%20as%20a%20reward%20directly)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=policy%20model%2C%20using%20the%20RM,assign%20rewards%20to%20model%20responses)。然后策略模型就直接根据这个信号做RL优化。
    

两者各有利弊：蒸馏式更稳定，因为奖励模型平滑了反馈，但多了一步训练；直接式无中间人、速度快，但AI打分的噪声直接影响策略，需要大模型评估非常可靠。Google 论文探讨了这两种方案，也称直接用 AI 评分为**d-RLAIF（direct RLAIF）**[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=After%20labelling%20the%20preferences%20through,assign%20rewards%20to%20model%20responses)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=policy%20model%2C%20using%20the%20RM,assign%20rewards%20to%20model%20responses)。实验证明 d-RLAIF 也能工作，不过需要对评分做适当处理归一，才能当作RL奖励[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=policy%20model%2C%20using%20the%20RM,assign%20rewards%20to%20model%20responses)。

RLAIF 的**优势**显然是规模和成本：我们可以让强模型批量生成成千上万条反馈，而不可能雇佣同等规模的人来标注[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=RLAIF%20vs%20RLHF)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=current%20results%20in%20the%20state,than%20getting%20equivalent%20human%20annotations)。并且 AI 反馈一致性更高，不会像人那样标准不一[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=they%20devised%20this%20method%20in,the%20concept%20of%20Constitutional%20AI)。RLAIF 也能**避免人接触有害内容**：在对齐有害性时，可用AI来识别不良输出，减少人类审阅毒性内容的风险[queirozf.com](https://queirozf.com/entries/paper-summary-constitutional-ai#:~:text=Paper%20Summary%3A%20Constitutional%20AI%20,harmlessness%2C%20without%20being%20overly%20evasive)。**劣势**则在于：AI 模型的偏好不一定等同于真实人类偏好，它可能引入自己的偏见或盲点（例如GPT-4评判可能过于严苛或在某些价值上与普罗大众不同）。因此 RLAIF 的效果很大程度取决于所选**反馈模型的质量**[arxiv.org](https://arxiv.org/abs/2309.00267#:~:text=RLAIF%20vs,the%20scalability%20limitations%20of%20RLHF)。如果反馈模型本身对齐不足，可能把坏的倾向放大给学生模型。此外，过于依赖单一AI来源也可能**趋同**——模型只学会迎合那个AI的审美，而非广泛人类喜好。

综合考虑，RLAIF 是解决 RLHF 可扩展性的重要方案。当构建一个模型产品时，如果人力有限或希望加速迭代，可以先用现有强模型进行 RLAIF 调优，然后再做少量人工评估校正。这一思路目前已经得到相当验证，有望在未来成为行业标准流程之一（特别是在模型不断自改进的方向上）。

*图3：将 RLHF（下）与 RLAIF（上）进行对比的示意图[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=ImageA%20diagram%20depicting%20RLAIF%2C%20on,From%20Lee%20et%20al%2C%202023)。可以看到两者流程类似，区别在于 RLAIF 用 AI Labeler 生成偏好数据，而 RLHF 用人工标注者提供反馈。研究发现 RLAIF 在多个任务上性能媲美 RLHF，但代价显著降低[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=Building%20on%20top%20of%20Anthropic%2C,making%20this%20process%20less%20complex)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=RLAIF%20vs%20RLHF)。*

### 6.2 Large LM as a Judge (LLM-as-Judge) – 大模型评审机制

**“LLM-as-Judge”** 指的是利用大型语言模型充当**评审**或**裁判**的角色，对候选输出进行评价、打分甚至选择，从而指导另一个模型的训练或评估。这其实是 RLAIF 思路的一种具体实现形式，但值得单独阐述，因为它在**模型评测**和**数据生成**等方面有多种应用。

在训练角度，LLM-as-Judge 可用于：

-   **偏好数据合成**：用强模型（如 GPT-4）自动生成对两种输出的偏好判断，从而构造偏好数据集[medium.com](https://medium.com/@prajnaaiwisdom/rlaif-vs-rlhf-whats-the-difference-and-why-it-matters-8e515aa374b6#:~:text=How%20RLAIF%20Works,AI%20feedback%20model%20evaluates)。例如，让 GPT-4 看两个回答，直接要求它输出“更好的回答是A还是B”，这样得到一个AI偏好标签，可用于训练较弱模型的奖励模型或策略。
    
-   **即时奖励**：在 RL 环境中，将LLM评审整合为环境的一部分。比如在对话生成时，每轮由一个预先冻结的GPT-4对当前回复打分作为奖励给策略模型。这类似前述的 direct RLAIF。OpenAI 的一项研究就使用 GPT-4 作为代理评估模型输出是否遵守对话规则[arxiv.org](https://arxiv.org/abs/2309.00267#:~:text=RLAIF%20vs,the%20scalability%20limitations%20of%20RLHF)。
    
-   **序列筛选**：生成多个候选回答后，用 LLM Judge 选出最优一个作为最终输出（这在推理阶段属于推理增强策略，称为 **“Generative Reranking”** 等）。
    

LLM-as-Judge 在模型**评测**上也广泛使用。由于人工评测慢且贵，许多研究改为用 GPT-4 等模型自动评估新模型与基准模型在对话质量上的优劣。例如 Vicuna、Llama2 等模型的论文都采用 GPT-4 来打分模型对话，与 ChatGPT对比胜率[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=substantially%20increasing%20response%20length,nlp%2FSimPO)。这些自动评测往往与人类评价有较高相关，被认为是目前可行的评测替代方案。所以 LLM-as-Judge 既可以**帮助训练**也可以**帮助测试**。

LLM-as-Judge 的优势显而易见：**强大的 LLM 具有对语言任务的深刻理解**，有时甚至比普通人还挑剔和一致。例如 GPT-4 可以根据一些隐含标准进行非常详细的比较（如考虑逻辑、事实性、语气等）[medium.com](https://medium.com/@prajnaaiwisdom/rlaif-vs-rlhf-whats-the-difference-and-why-it-matters-8e515aa374b6#:~:text=How%20RLAIF%20Works,AI%20feedback%20model%20evaluates)。这有助于模型对齐更细致的要求。并且大模型评审者可以7\*24小时工作，容易扩展。不足之处主要在于：**大模型的评判标准需要人来设定**。要让 GPT-4 当裁判，你得提示它用什么标准，是注重准确还是礼貌？不同提示会导致评审结果不同。因此仍需人类高层设定**准则**。另外，有时大模型会存在“偏爱某种风格输出”等自身偏见，需要注意平衡（例如 GPT-4 是否偏好啰嗦的礼貌回答？这要验证）。

总的来说，LLM-as-Judge 是 RLAIF 思想的具体产物，已经在诸多开源项目中得到应用。对开发者来说，可以考虑引入一个强大的开源或商用模型作为\*\*“质量把关者”\*\*：无论是在生成训练数据时过滤不良样本，还是在强化训练中提供反馈信号，抑或在上线前评测模型与前代版本的差异，都能发挥作用。当然，要注意监控这种自动反馈的可靠性，理想情况下还是应辅以少量人工检查校准。

### 6.3 Constitutional AI – 宪法式 AI 自我反馈

**Constitutional AI**（宪法 AI）是Anthropic在2022年提出的一种对齐方法，旨在**无需人工标注有害内容**的情况下，让模型学会遵循一系列人类价值原则[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=they%20devised%20this%20method%20in,the%20concept%20of%20Constitutional%20AI)。可以将其视为RLAIF在安全性/价值观对齐方向的一种应用：通过一套预设的“AI 宪法”（即原则清单），让模型自己批判和改进输出[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=they%20devised%20this%20method%20in,the%20concept%20of%20Constitutional%20AI)。

Constitutional AI 的流程通常如下：

1.  **制定宪法**：人工撰写一组原则，比如“不提供非法建议”“尊重用户”“不歧视”等。这些原则就是模型需要遵循的“价值观”。
    
2.  **AI 自我反馈**：训练包含两个阶段：先让模型产生初步回答，然后让模型的另一个实例根据宪法原则审视该回答是否违反了某条原则，或者能否更完善[rlhfbook.com](https://rlhfbook.com/c/13-cai.html#:~:text=By%20employing%20a%20human,generate%20artificial%20preference%20and)。这个自我审视的模型会生成一个反馈（可能是指出问题，或直接给出改进建议）。
    
3.  **改进输出**：模型接着根据反馈修改原回答，使之更符合宪法原则。这样得到了改进版回答。
    
4.  **训练**：用这些有初稿和修改稿的对话对模型进行微调，使其学会**自动产生符合宪法的最终回答**。在Anthropic实现中，甚至对模型引入RL，使其在无人工参与下通过自辩论方式优化。
    

这个过程中，唯一人工参与的是写宪法，而不需要标注大量具体案例的好坏[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=they%20devised%20this%20method%20in,the%20concept%20of%20Constitutional%20AI)。Anthropic 发现，这样训练出的模型在**有害内容**方面比传统RLHF更可控，因为原则明确，模型不会被训练数据中潜在偏见所影响[fanpu.io](https://fanpu.io/summaries/2024-07-23-constitutional-ai-harmlessness-from-ai-feedback/#:~:text=Constitutional%20AI%3A%20Harmlessness%20from%20AI,a%20clear%20outline%20of)。例如，他们报告Claude模型在对抗性测试中拒绝有害请求的比例更高，相比只用人类反馈的数据，提高了安全性能[arxiv.org](https://arxiv.org/html/2504.04918v1#:~:text=Constitution%20or%20Collapse%3F%20Exploring%20Constitutional,8)。同时，因为宪法公开透明，模型的行为准则清晰可解释，而 RLHF 的内在规则是隐含在数据里的，不容易解释[fanpu.io](https://fanpu.io/summaries/2024-07-23-constitutional-ai-harmlessness-from-ai-feedback/#:~:text=Constitutional%20AI%3A%20Harmlessness%20from%20AI,a%20clear%20outline%20of)。

Constitutional AI 的优势是：**省去了大量人工标注违规案例**。特别是对于有害性对齐，以往需要人工标注各种不良对话来惩罚模型，这既慢又让人接触坏内容。而宪法AI只需写一遍规则，让模型自己生成无数例子自己纠正，效率高且保护人类不受毒害[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=they%20devised%20this%20method%20in,the%20concept%20of%20Constitutional%20AI)。缺点在于：宪法原则的制定仍很考究，需要**全面细致**且**没有歧义**。如果规则有漏洞，模型可能钻空子（比如规则没说不能骂人，那模型可能学会骂人？当然实际规则会包括这一条）。另外模型对原则的理解和执行也非完美，可能会出现**过度顺从**（如宁可不回答正当问题也怕触犯原则）或**错误理解**原则的情况，需要多轮迭代完善规则[arxiv.org](https://arxiv.org/html/2504.04918v1#:~:text=Constitution%20or%20Collapse%3F%20Exploring%20Constitutional,8)。

目前，宪法式AI已被Anthropic用于训练其Claude系列模型，并公开了一些效果评估[arxiv.org](https://arxiv.org/html/2504.04918v1#:~:text=3,8)。其他组织也开始尝试类似方法，如Stanford Alpaca 的一个扩展项目，也引入规则让模型自己审阅输出安全性。宪法AI并非对RLHF的完全替代，反而可以**配合**RLHF使用：先用宪法AI处理安全/价值观，再用RLHF处理有用性等指标，这样组合能提升模型整体的对齐程度。

总而言之，Constitutional AI 提供了一种**人类高层指导 + AI自我监督**的范式，让模型在固定价值框架内自行改进。对于安全关键的领域，这是一种非常有前景的方法，也让我们看到了**减少人工干预**的新思路。

### 6.4 上线评测与迭代优化 (Evaluation and Iterative Improvement)

模型训练完成并上线后，工作并未结束。**持续的评测**和**迭代优化**对于保持模型性能和对齐程度非常重要。本节最后，我们简要讨论在模型部署后可以采取的一些措施，包括自动化评测、用户反馈收集以及模型的定期更新策略。

**1\. 自动评测工具**：在缺乏大规模人工评测的情况下，利用**LLM-as-Judge**（上一节讨论）来对模型输出进行打分对比是常用做法。可以建立一个评测集，包含代表性的问题，让当前模型和以前版本模型（或竞争模型）回答，然后用 GPT-4 或类似模型评价哪个好[turing.com](https://www.turing.com/resources/rlaif-in-llms#:~:text=Training%20www,generated%20feedback%20to%20train%20LLMs)。例如，使用 GPT-4 按照“是否正确回答问题、语言是否得体、内容是否有害”等多维度打分。这种方法能较快定位模型在升级中的改进或退化之处。虽然绝对可信度不如真人，但大量实验显示 GPT-4 等评估结果与人类有较高相关性[arxiv.org](https://arxiv.org/abs/2309.00267#:~:text=RLAIF%20vs,the%20scalability%20limitations%20of%20RLHF)。为了安全评测，也可设计**自动红队**：让模型大量生成边界案例，再用规则或AI判定模型表现。这种stress test有助于发现在训练集未覆盖到的弱点。

**2\. 用户反馈收集**：一旦模型上线，我们可以通过应用界面收集**真实用户的反馈**。常见做法是在应用中提供反馈按钮或评分，让用户报告不满意的答案或者点赞好的答案。这些反馈数据非常宝贵，可用来构建更贴近实际使用的数据集。例如，把用户低分的 Q&A 对整理出来，人工分析原因后补充进下次训练数据。更进一步的，甚至可以尝试**在线RLHF**：将用户反馈实时转为奖励信号，不断更新模型（这需要谨慎，当前研究还少）。但短期至少可以**批次迭代**：每隔一段时间汇总用户反馈，进行一次类似 RLHF 或 DPO 的再训练。这种循环让模型逐步适应真实用户需求，而不仅仅满足实验室中的指标[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Optionally%2C%20RLHF%20can%20continue%20from,complex%20and%20open%20research%20question)。

**3\. 模型监控**：持续监控模型的输出也是迭代优化的重要部分。可以针对不同模块建立**指标**，如有用性指标（问题回答是否完整）、准确性指标（事实是否正确，可用检索校对）以及安全性指标（有无敏感内容）。通过定期采样模型回答并分析指标，可以在无用户举报前发现潜在问题。现有一些工具和研究用于**自动检测**模型输出的事实错误或有害内容，可集成到监控管道中。当发现指标劣化时，可能意味着需要新一轮偏好对齐或微调。

**4\. 快速回滚和AB测试**：在部署新模型前，最好进行**AB测试**：将部分用户请求分配给新模型，观察满意度、会话长度、问题解决率等与旧模型的对比。如果新模型有显著退步之处，应仔细分析原因（可能某次RLHF过度优化导致损失知识等），然后决定是否推送。即使上线后，也应保持可以**快速回滚**到旧模型的能力，以防出现不可接受的问题。很多产品在模型更新上采取渐进策略，小流量验证后再全面切换。

**5\. 模型融合与Ensembling**：有时一个模型难以完美胜任所有内容，可以考虑**多模型组合**。例如，引入一个专门的**过滤模型**，在主模型回答给用户前，先由过滤模型检测不良内容，必要时拦截或替换回答（OpenAI 有类似Moderation机制）。又或者对一些高风险领域的问题转由更严格的模型回答。这些也属于上线后的优化手段，使系统更稳健。

总之，上线并不意味着对齐工作的结束，而是进入了**真实世界反馈循环**的新阶段。正如 RLHF 可以理解为模型与人类的一种互动训练，上线后用户与模型的每一次交互，都是新的学习机会[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Optionally%2C%20RLHF%20can%20continue%20from,complex%20and%20open%20research%20question)。通过良好的评测和反馈机制，我们可以不断**校准模型**，逐步接近理想状态。这种持续优化理念也契合 Anthropic 所提出的“Iterated Online RLHF”愿景，即模型和人类共同进化，不断刷新对齐水平[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Optionally%2C%20RLHF%20can%20continue%20from,complex%20and%20open%20research%20question)。

## 结论 (Conclusion)

在本报告中，我们深入探讨了 RLHF 及其相关的各种技术路径。从 RLHF 的背景动机到其分步训练流程，我们了解到**将人类反馈融入模型训练**如何显著改善模型对人类偏好的贴合度。RLHF 的经典实现（SFT + 奖励模型 + PPO）已成功应用于 ChatGPT 等系统，证明了其价值[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Feedback%20,that%20of%20complex%20human%20values)。与此同时，我们也看到了 RLHF 所面临的挑战：数据昂贵、训练复杂、容易不稳定等[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-6/#:~:text=In%20previous%20posts%2C%20we%20started,Play%20Fine)。因此，业界探索出了许多替代或改进方法，例如 DPO、SimPO 这样的**离线偏好优化**，用更简单直观的方式实现了与 RLHF 相当的效果[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=DPO%20is%20a%20simpler%20and,such%20as%20Llama%20and%20Mistral)[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=The%20results%20are%20straightforward%20when,of%20SimPO%20compared%20to%20DPO)。还有 ORPO、IPO、KTO 等算法从不同角度完善了偏好对齐的理论和实用性，让我们有机会根据具体需求选择最合适的方法组合。

我们也讨论了若干**辅助机制**，如 RLAIF 和 Constitutional AI 等，展示了**减少人工参与、扩大反馈来源**的新方向[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=Building%20on%20top%20of%20Anthropic%2C,making%20this%20process%20less%20complex)[fanpu.io](https://fanpu.io/summaries/2024-07-23-constitutional-ai-harmlessness-from-ai-feedback/#:~:text=Constitutional%20AI%3A%20Harmlessness%20from%20AI,a%20clear%20outline%20of)。这些方法在未来可能和经典 RLHF 相辅相成，共同构建一个多层次的模型对齐方案。例如，可以设想先用大量 AI 自我反馈预训练模型价值观，再用少量人工反馈精调用户偏好，最后上线后结合用户反馈持续优化的闭环。

对于软件开发者和产品经理来说，理解 RLHF 及其衍生技术有助于做出明智的决策：在模型开发中**平衡数据、人力与效果**。如果资源有限，也许选择 DPO 或 RRHF 这样的路线更实际；如果注重安全和价值观，对宪法式AI的投入就非常必要。在工程实现时，善用开源工具（TRL库等）和已有数据，也是快速推进项目的要诀[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=The%20first%20code%20released%20to,OpenAI%20in%20TensorFlow%20in%202019)。同时不能忽视上线后的评测迭代，通过用户反馈形成“人机共训”的良性循环，才能让模型保持长期的高质量服务。

AI 模型的偏好对齐是一个跨领域的挑战，需要机器学习、人工智能伦理、人机交互等方面的协同。RLHF 只是一个开端，未来可能出现更高效、更人性化的对齐技术。但无论方法如何演变，其核心始终是**让 AI 更好地为人服务**。希望本报告提供的全面视角，能帮助您在实践中灵活运用这些技术，为所在行业打造既强大又安全可靠的 AI 应用。

## 推荐学习资源 (Recommended Learning Resources)

深入理解 RLHF 及相关技术，不仅可以阅读文档和论文，观看教学视频也是很好的学习方式。以下是一些优质的视频资源：

-   **《从人类反馈中进行强化学习 (RLHF)》课程 – 吴恩达 (Andrew Ng)**：DeepLearning.AI 出品的短课程（中英双语字幕）[bilibili.com](https://www.bilibili.com/video/BV1R94y1P7QX/#:~:text=139)。共6讲，涵盖 RLHF 工作原理、所需数据集、用 TensorFlow 在 Llama-2 上实践 RLHF 微调等[bilibili.com](https://www.bilibili.com/video/BV1R94y1P7QX/#:~:text=https%3A%2F%2Fwww.deeplearning.ai%2Fshort,Side%20%28SxS%29%E2%80%9D%E6%96%B9%E6%B3%95%EF%BC%8C%E8%AF%84%E4%BC%B0%E7%BB%8F%E8%BF%87%E5%BE%AE%E8%B0%83%E7%9A%84LLM%E4%B8%8E%E5%8E%9F%E5%A7%8B%E5%9F%BA%E7%A1%80%E6%A8%A1%E5%9E%8B%E7%9A%84%E5%B7%AE%E5%BC%82%E3%80%82)[bilibili.com](https://www.bilibili.com/video/BV1R94y1P7QX/#:~:text=%EF%BC%88RLHF%EF%BC%89%E7%9B%AE%E5%89%8D%E6%98%AF%E4%BD%BFLLM%E4%B8%8E%E4%BA%BA%E7%B1%BB%E7%9A%84%E4%BB%B7%E5%80%BC%E8%A7%82%E5%92%8C%E5%81%8F%E5%A5%BD%E4%BF%9D%E6%8C%81%E4%B8%80%E8%87%B4%E7%9A%84%E4%B8%BB%E8%A6%81%E6%96%B9%E6%B3%95%E3%80%82RLHF%E4%B9%9F%E7%94%A8%E4%BA%8E%E8%BF%9B%E4%B8%80%E6%AD%A5%E8%B0%83%E6%95%B4%E5%9F%BA%E6%9C%ACLLM%E4%BB%A5%E4%BD%BF%E5%85%B6%E4%B8%8E%E6%82%A8%E7%9A%84%E7%94%A8%E4%BE%8B%E4%B8%AD%E7%89%B9%E5%AE%9A%E7%9A%84%E4%BB%B7%E5%80%BC%E8%A7%82%E5%92%8C%E5%81%8F%E5%A5%BD%E4%BF%9D%E6%8C%81%E4%B8%80%E8%87%B4%E3%80%82%20%E5%9C%A8%E8%BF%99%E9%97%A8%E8%AF%BE%E7%A8%8B%E4%B8%AD%EF%BC%8C%E6%82%A8%E5%B0%86%E8%8E%B7%E5%BE%97%E5%AF%B9RLHF%E8%AE%AD%E7%BB%83%E8%BF%87%E7%A8%8B%E7%9A%84%E6%A6%82%E5%BF%B5%E6%80%A7%E7%90%86%E8%A7%A3%EF%BC%8C%E7%84%B6%E5%90%8E%E5%AE%9E%E8%B7%B5%E5%BA%94%E7%94%A8RLHF%E6%9D%A5%E8%B0%83%E6%95%B4LLM%E3%80%82%E6%82%A8%E5%B0%86%E4%BC%9A%EF%BC%9A%20%E6%8E%A2%E7%B4%A2%E5%9C%A8RLHF%E8%AE%AD%E7%BB%83%E4%B8%AD%E4%BD%BF%E7%94%A8%E7%9A%84%E4%B8%A4%E4%B8%AA%E6%95%B0%E6%8D%AE%E9%9B%86%EF%BC%9A%E2%80%9C%E5%81%8F%E5%A5%BD%E2%80%9D%E5%92%8C%E2%80%9C%E6%8F%90%E7%A4%BA%E2%80%9D%E6%95%B0%E6%8D%AE%E9%9B%86%E3%80%82%20%E4%BD%BF%E7%94%A8%E5%BC%80%E6%BA%90%E7%9A%84Google%20Cloud,Side%20%28SxS%29%E2%80%9D%E6%96%B9%E6%B3%95%EF%BC%8C%E8%AF%84%E4%BC%B0%E7%BB%8F%E8%BF%87%E5%BE%AE%E8%B0%83%E7%9A%84LLM%E4%B8%8E%E5%8E%9F%E5%A7%8B%E5%9F%BA%E7%A1%80%E6%A8%A1%E5%9E%8B%E7%9A%84%E5%B7%AE%E5%BC%82%E3%80%82)。非常适合有一定机器学习基础的开发者入门 RLHF。
    
-   **RLHF 原理与 PPO 讲解 – ChatGPT 系列 by 李rumor**：B站上“笨蛋李大河”的视频[bilibili.com](https://www.bilibili.com/video/BV13r42177Hk/#:~:text=%E7%90%86%E8%A7%A3%E5%A4%A7%E6%A8%A1%E5%9E%8B%E8%AE%AD%E7%BB%83%E7%9A%84%E5%87%A0%E4%B8%AA%E9%98%B6%E6%AE%B5%20Pretraining%EF%BC%8CSFT%EF%BC%8CRLHF)（ChatGPT 原理剖析系列第2篇），深入浅出地解释了 RLHF 管线，特别是 PPO 如何在 ChatGPT 中应用[youtube.com](https://www.youtube.com/watch?v=qf2zcev7mHQ#:~:text=%E5%BC%BA%E5%8C%96%E5%AD%A6%E4%B9%A0RLHF%E4%B8%8EPPO%EF%BC%81%20ChatGPT%20%E7%B3%BB%E5%88%97%E7%AC%AC02%E7%AF%87,)。对强化学习背景薄弱的听众也很友好。
    
-   **RLHF 代码实战 from scratch**：B站UP主“蓝斯诺特”发布的5集系列[bilibili.com](https://www.bilibili.com/video/BV13r42177Hk/#:~:text=1)[bilibili.com](https://www.bilibili.com/video/BV13r42177Hk/#:~:text=05%3A36)，带领观众从零实现RLHF流程，包括Actor模型训练、Critic模型（奖励模型）训练以及最终PPO微调步骤[bilibili.com](https://www.bilibili.com/video/BV13r42177Hk/#:~:text=1)[bilibili.com](https://www.bilibili.com/video/BV13r42177Hk/#:~:text=4)。该系列附有GitHub代码[bilibili.com](https://www.bilibili.com/video/BV13r42177Hk/#:~:text=1147)适合想实践的工程师。
    
-   **“RLHF & DPO Explained (In Simple Terms!)” – YouTube**：简明对比 RLHF 和 DPO 的英文视频[youtube.com](https://www.youtube.com/watch?v=nSrj1J6ODoM#:~:text=RLHF%20%26%20DPO%20Explained%20,I%20provide%20a%20high)。博主用非数学方式解释了两者区别，适合快速了解DPO为何物以及相较RLHF的优势[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Direct%20Preference%20Optimization)。
    
-   **Hugging Face 直播课程: Fine-tuning LLMs on Human Feedback**：Hugging Face 官网上的直播录屏[youtube.com](https://www.youtube.com/watch?v=bbVoDXoPrPM#:~:text=Fine,Learn%20more)。介绍如何使用 TRL 库对 LLM 做RLHF和DPO微调，包含实际代码演示[github.com](https://github.com/ranzeet013/RLHF-CustomData#:~:text=Reinforcement%20Learning%20from%20Human%20Feedback,the%20model%20to%20generate)。对于计划自己动手复现的人很有帮助。
    
-   **深度强化学习在大模型中的应用 – YouTube (台湾中文)**：生成式AI导论课程的相关章节[youtube.com](https://www.youtube.com/watch?v=v12IKvF6Cj8#:~:text=%E7%94%9F%E6%88%90%E5%BC%8FAI%E5%B0%8E%E8%AB%962024%20%E7%AC%AC8%E8%AC%9B%EF%BC%9A%E5%A4%A7%E5%9E%8B%E8%AA%9E%E8%A8%80%E6%A8%A1%E5%9E%8B%E4%BF%AE%E7%B7%B4%E5%8F%B2%20,14%3A50%20%E6%95%99)。讲解了RLHF在大型语言模型调优的地位，以及OpenAI在GPT系列中引入RLHF的实践。繁体中文讲解，对中文观众也友好。
    

以上资源有的偏理论讲解，有的偏实战代码，建议根据自己的侧重选择观看。在学习过程中，推荐对照本报告内容，加深对关键概念的理解。

## 专业术语词汇表 (Glossary of Terms)

最后附上本报告涉及的主要专业术语和缩写列表，并提供对应的英文全称及简要说明：

-   **RLHF（Reinforcement Learning from Human Feedback）**：从人类反馈中强化学习。指利用人类提供的偏好反馈对模型进行强化学习训练的方法[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Feedback%20,that%20of%20complex%20human%20values)。ChatGPT 等模型成功应用了 RLHF 来对齐人类偏好。
    
-   **LLM（Large Language Model）**：大型语言模型。通常指具有上亿甚至千亿参数的语言模型，如GPT-4、Llama等。LLM 能基于大规模语料预训练，具备强大的自然语言生成和理解能力。
    
-   **SFT（Supervised Fine-Tuning）**：有监督微调。对预训练模型进一步在人工标注的高质量问答对、对话等数据上进行的微调，使模型具备基本的指令遵循或任务执行能力[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=As%20a%20starting%20point%20RLHF,powered%20products)。RLHF 中通常先经过SFT再进行强化学习微调。
    
-   **Reward Model（奖励模型）**：在RLHF中训练的模型，输入(prompt, 回答)对，输出一个分数以评估该回答的质量或人类偏好程度[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=The%20reward%20model%20is%20then,r_%7B%5Ctheta)。奖励模型通常通过人类偏好比较数据训练得到[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=following%20cross,r_%7B%5Ctheta%20%7D%28x%2Cy_%7Bl%7D%29%7D%7D%7D%5Cright)。
    
-   **Policy Model（策略模型）**：在RLHF中指最终我们优化的模型（通常就是LLM本身）。强化学习视角下，它将回答视为行动，目标是学到一个策略使得行动获得高奖励[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=The%20key%20is%20to%20understand,can%20be%20applied%20to%20it)。
    
-   **PPO（Proximal Policy Optimization）**：近端策略优化。OpenAI提出的策略梯度RL算法，通过限制每次参数更新幅度来稳定训练[medium.com](https://medium.com/yugen-ai-technology-blog/understanding-the-math-behind-grpo-deepseek-r1-zero-9fb15e103a0a#:~:text=PPO%20%E2%80%94%20Clip%20relies%20on,through%20them%20one%20by%20one)。PPO被广泛用于RLHF的策略模型微调[turingpost.com](https://www.turingpost.com/p/rlhfvariants#:~:text=The%20most%20widespread%20RL%20algorithm,preventing%20large%20shifts%20in%20behavior)。
    
-   **KL散度（KL Divergence）**：Kullback-Leibler散度，一种衡量两个概率分布差异的指标。RLHF中常用KL散度来约束策略模型不要偏离初始模型输出分布太多[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=papers%20from%20OpenAI%2C%20Anthropic%2C%20and,explained%20by%20John%20Schulman)。
    
-   **DPO（Direct Preference Optimization）**：直接偏好优化。无需显式训练奖励模型和进行RL，通过重新参数化将偏好比较直接融入策略优化的一种方法[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=At%20the%20core%20of%20DPO,expressed%20in%20a%20closed%20form)。简化了RLHF流程，常用于对齐。
    
-   **SimPO（Simple Preference Optimization）**：简单偏好优化。DPO的改进版，用模型自身的平均log概率作为奖励信号且无需参考模型[ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2405.14734#:~:text=learning%20from%20human%20feedback%20,and%20its%20latest%20variants%20across)。在实验中比DPO有更好效果[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-11/#:~:text=The%20results%20are%20straightforward%20when,of%20SimPO%20compared%20to%20DPO)。
    
-   **ORPO（Odds Ratio Preference Optimization）**：胜算比偏好优化。将指令微调和偏好优化合并的单阶段方法，不需要参考模型[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-8/#:~:text=ORPO%20combines%20instruction%20tuning%20and,free%20and%20computationally%20more%20efficient)。通过最大化胜出回答与败北回答概率比来训练模型。
    
-   **IPO（Identity Preference Optimization）**：恒等偏好优化。对DPO目标加入正则项，防止偏好数据过拟合的一种改进[en.wikipedia.org](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback#:~:text=In%20summary%2C%20IPO%20can%20control,and%20the%20KL%20term%20fails)。通过对偏好概率作恒等(logit)变换平滑，增强模型鲁棒性。
    
-   **KTO（Kahneman-Tversky Optimization）**：卡尼曼-特沃斯基优化。利用前景理论的人类决策模型来优化LLM的直接偏好对齐方法[hippocampus-garden.com](https://hippocampus-garden.com/preference_optimization/#:~:text=Kahneman,where%20preference%20data%20is%20limited)。只需正负反馈标签即可训练，对损失和收益赋不同权重。
    
-   **RRHF（Rank Responses with Human Feedback）**：通过排序对齐模型。一次生成多个响应，用人类或AI偏好对它们排序，并训练模型的概率分布匹配该排序[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=In%20contrast%2C%20we%20propose%20a,We%20evaluate%20RRHF)。一种无需PPO的对齐新范式。
    
-   **GRPO（Group Relative Policy Optimization）**：分组相对策略优化。DeepSeek提出的RL算法，组内比较优势替代单独价值网络[together.ai](https://www.together.ai/deepseek#:~:text=%2A%20,GRPO)。一次生成多个输出，利用它们之间的相对好坏来更新策略。
    
-   **RLAIF（Reinforcement Learning from AI Feedback）**：从AI反馈中强化学习。使用AI模型（如GPT-4）代替人类提供偏好信号来训练LLM的方法[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=Building%20on%20top%20of%20Anthropic%2C,making%20this%20process%20less%20complex)。大幅降低人工成本，性能接近RLHF。
    
-   **LLM-as-Judge**：大模型作为裁判。指利用强大的语言模型来评估或比较其他模型输出，从而提供反馈信号或进行自动评测。在RLAIF和模型评测中广泛应用[medium.com](https://medium.com/@prajnaaiwisdom/rlaif-vs-rlhf-whats-the-difference-and-why-it-matters-8e515aa374b6#:~:text=How%20RLAIF%20Works,AI%20feedback%20model%20evaluates)。
    
-   **Constitutional AI（宪法式AI）**：Anthropic提出的用一组预定义原则（宪法）让AI自我评判和改进输出的方法[argilla.io](https://argilla.io/blog/mantisnlp-rlhf-part-4/#:~:text=they%20devised%20this%20method%20in,the%20concept%20of%20Constitutional%20AI)。减少人工标注参与，主要用于有害内容对齐和价值观引导。
    

以上术语涵盖了报告中的重点概念，希望通过中英文对照和解释能帮助读者巩固理解。在实际工作中，与团队沟通或阅读相关资料时，这些词汇会经常出现，掌握其含义将非常有益。[huggingface.co](https://huggingface.co/blog/rlhf#:~:text=Feedback%20,that%20of%20complex%20human%20values)[arxiv.org](https://arxiv.org/abs/2304.05302#:~:text=In%20contrast%2C%20we%20propose%20a,We%20evaluate%20RRHF)

![](https://www.google.com/s2/favicons?domain=https://www.reddit.com&sz=32)

![](https://www.google.com/s2/favicons?domain=http://papers.neurips.cc&sz=32)

![](https://www.google.com/s2/favicons?domain=https://en.wikipedia.org&sz=32)

![](https://www.google.com/s2/favicons?domain=https://huggingface.co&sz=32)

![](https://www.google.com/s2/favicons?domain=https://www.turingpost.com&sz=32)

源