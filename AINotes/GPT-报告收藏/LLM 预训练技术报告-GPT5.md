You: 

> 大型语言模型（LLM）的训练一般包含预训练、SFT（监督微调）、RLHF（人类反馈强化学习）三个阶段。请广泛深入调研分析预训练的教程和文章、论文等，使用通俗易懂的语言，帮我输出一份技术报告，面向软件开发者和产品经理等，使得我们能够快速理解大语言模型训练的过程，配合一些图表和视频，不少于三万字

ChatGPT: 

已思考 3m 35s

文档已创建

已思考 21s

我已把完整的《LLM预训练（Pre-training）技术报告》放到侧边文档里（见右侧“LLM预训练技术报告（开发者与产品经理版）”）。这是一份系统、工程视角为主的长文：覆盖数据治理与去重、分词与词表、模型结构（RMSNorm/SwiGLU/RoPE/Flash-Attention/MQA）、优化与并行（ZeRO、FSDP、Megatron-LM、GSPMD）、Chinchilla/Kaplan 规模化法则、实践路线（1B→7B）、评估与合规清单等，并附有可复刻的图表示意与配置模板。

下面给你一份“精选参考资料与可直接观看的视频清单”（与文档互补），方便你进一步深挖或对照实现。

# 精选参考与延伸阅读（按主题）

**Transformer 与规模化法则**

-   Attention Is All You Need（Transformer 原始论文）. [arXiv](https://arxiv.org/abs/1706.03762?utm_source=chatgpt.com)
    
-   Scaling Laws for Neural Language Models（Kaplan 等）. [arXiv](https://arxiv.org/abs/2001.08361?utm_source=chatgpt.com)
    
-   Training Compute-Optimal LLMs（Chinchilla；提出“算力最优”与数据-参数配平思想）. [arXiv](https://arxiv.org/abs/2203.15556?utm_source=chatgpt.com)
    
-   训练计算估算与“6×P×D FLOPs”简法（含更体系化推导/教材式说明）。
    

**分词与词表**

-   SentencePiece：语言无关的子词分词框架（BPE/Unigram）。 [arXiv](https://arxiv.org/abs/1808.06226?utm_source=chatgpt.com)
    
-   BPE 在神经机器翻译中的应用（Sennrich 等，BPE 里程碑文章）。
    

**预训练关键结构与内核优化**

-   RoFormer：Rotary Position Embedding（RoPE）. [arXiv](https://arxiv.org/abs/1608.03983?utm_source=chatgpt.com)
    
-   RMSNorm：Root Mean Square Layer Normalization. [arXiv](https://arxiv.org/pdf/1412.6980?utm_source=chatgpt.com)
    
-   SwiGLU：GLU 变体提升 Transformer 表现.
    
-   FlashAttention：精确且高效的注意力计算（内核级优化基础）。
    
-   多查询/分组查询注意力（解码加速，“一写头即可”）。
    
-   ALiBi（长序列外推的相对偏置思路）。
    

**优化与训练日程**

-   Adam（通用）、AdamW（解耦权重衰减）、余弦退火与预热（SGDR）。 [arXiv+2arXiv+2](https://arxiv.org/abs/2002.05202?utm_source=chatgpt.com)
    

**开放语料与数据治理**

-   C4（从 Common Crawl 清洗；T5 语料），CCNet（网页清洗管线）。
    
-   The Pile（多源大规模开放语料）。
    
-   RefinedWeb（大规模“去渣提纯”的网页文本）。
    
-   RedPajama（对标 GPT 家族的开源复现数据配方）。
    
-   FineWeb/FineWeb-Edu 与 DataTrove（Hugging Face 的现代开放数据与全流程工具）。
    
-   近重检测与去重的经典方法（MinHash/SimHash/LSH 等）。
    

**系统与并行（工程落地）**

-   Megatron-LM（张量/流水并行的经典实现与论文）。
    
-   DeepSpeed ZeRO（分片优化器/状态，配大批训练）。
    
-   PyTorch FSDP（官方文档/教程与工程经验论文）。
    
-   GSPMD（XLA 自动并行；TPU 体系）。
    

**代表性开放模型与论文（可对照“现代配方”）**

-   Llama 3（405B/70B/8B；现代化结构与数据治理）。
    
-   OLMo/OLMo 2（完整公开训练数据 Dolma、代码、日志与检查点；科研可复现范式）。
    
-   Dolma 数据集总览与仓库。
    

**Chinchilla“20 tokens / 参数”经验比值的一手/综述来源**

-   DeepMind 原论文 & 独立解读/复现（Databricks、Epoch、后续研究）。
    

# 入门到进阶：可直接观看的视频（精选）

-   Tri Dao 系列（FlashAttention / 内核与长序列）：斯坦福 MLSys Seminar、FA2/FA3 分享。
    
-   DeepSpeed/ZeRO 与大模型分布式训练实务（官方/社区培訓）。
    
-   Karpathy「从零手写 GPT / 深入浅出 LLM」系列（理解预训练与解码器-only主线极佳）。
    

---

如果你想把这份技术报告**导出为 Markdown、PDF 或幻灯片**，或者希望我**把其中某一节（比如“数据治理与去重”或“并行与系统工程”）扩写成可执行操作手册**，直接告诉我你偏好的格式和重点，我会一次性整理好给你。

You: 

> 好的，基于以上内容和分析，帮我输出一个更为详细和完整的深入研究报告，把握重点核心内容，使用通俗易懂的语言，不少于三万字

ChatGPT: 

为了确保深入研究报告能够完全满足你的需求，我想确认以下几个点：

1.  **语言风格与对象**：是否仍希望以通俗易懂的中文撰写，面向软件开发者和产品经理？
    
2.  **重点内容维度**：请确认是否希望我们保留原文中的结构，例如：数据治理、模型结构、训练优化、系统并行、典型案例等？是否希望加入更多：
    
    -   最新研究成果与趋势（例如 Mamba、Smoe、长上下文建模）？
        
    -   工程实践建议与实用对比（不同框架、平台优劣）？
        
    -   法务/安全/合规风险深度探讨？
        
3.  **是否期望附加内容**：如图表（可导出）、视频资源推荐、术语表、学习路径图等？
    

请你确认或补充这些内容，我将据此启动详细研究。

You: 

> 仍希望以通俗易懂的中文撰写，面向软件开发者和产品经理；不受限于结构，而是聚焦于让读者更好的理解内容，掌握内容；期望附加内容：如图表（可导出）、视频资源推荐、术语表等。使用通俗易懂的语言，不少于三万字

ChatGPT: 

好的，我将为你撰写一份不少于三万字的中文深入研究报告，全面介绍大语言模型的预训练阶段，重点使用通俗易懂的语言，面向软件开发者和产品经理群体，帮助读者真正理解和掌握核心概念与工程实践。

报告将融合：

-   最新研究成果与技术趋势
    
-   工程实践案例和对比分析
    
-   可导出图表、术语表、推荐视频等扩展内容
    

完成后，我会通知你进行查阅与反馈。

# 大语言模型预训练阶段深入研究报告

*图1：大型语言模型的完整训练流程分为三个阶段，预训练产生基础模型，然后经由有监督微调（SFT）和人类反馈强化学习（RLHF）逐步对齐人类需求[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=1,giving%20it%20a%20smiley%20face)[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=You%20can%20skip%20any%20of,steps%20gives%20the%20best%20performance)。预训练模型好比一个从互联网大量语料中“野生长成”的怪兽，富含海量知识但缺乏规范；SFT阶段用高质量数据将其驯化得“社会可接受”；RLHF则进一步“加上笑脸”，使模型行为更符合用户期望[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=1,giving%20it%20a%20smiley%20face)。*

## 引言：预训练的定义与整体流程

大型语言模型（LLM）的**预训练（Pre-training）**是指在海量未标注文本语料上对模型进行自监督训练，以学习语言的统计规律和知识[qiankunli.github.io](https://qiankunli.github.io/2023/12/18/llm_post_training.html#:~:text=%E9%A2%84%E8%AE%AD%E7%BB%83%E6%A8%A1%E5%9E%8B%E6%98%AF%E4%B8%80%E4%B8%AA%E6%9C%AA%E5%8A%A0%E6%8E%A7%E5%88%B6%E7%9A%84%E2%80%9C%E6%80%AA%E7%89%A9%E2%80%9D%EF%BC%8C%E5%9B%A0%E4%B8%BA%E5%85%B6%E8%AE%AD%E7%BB%83%E6%95%B0%E6%8D%AE%E6%9D%A5%E6%BA%90%E4%BA%8E%E5%AF%B9%E4%BA%92%E8%81%94%E7%BD%91%E5%86%85%E5%AE%B9%E7%9A%84%E6%97%A0%E5%B7%AE%E5%88%AB%E6%8A%93%E5%8F%96%EF%BC%8C%E5%85%B6%E4%B8%AD%E5%8F%AF%E8%83%BD%E5%8C%85%E6%8B%AC%E7%82%B9%E5%87%BB%E8%AF%B1%E5%AF%BC%E3%80%81%E9%94%99%E8%AF%AF%E4%BF%A1%E6%81%AF%E3%80%81%E6%94%BF%E6%B2%BB%E7%85%BD%E5%8A%A8%E3%80%81%E9%98%B4%E8%B0%8B%E8%AE%BA%E6%88%96%E9%92%88%E5%AF%B9%E7%89%B9%E5%AE%9A%E4%BA%BA%E7%BE%A4%E7%9A%84%E6%94%BB%E5%87%BB%E7%AD%89%E5%86%85%E5%AE%B9%E3%80%82%202,Tuning%EF%BC%8C%E7%9B%91%E7%9D%A3%E5%BE%AE%E8%B0%83)。预训练阶段通常耗费了整个模型训练流程中**绝大部分的计算资源**，例如在 OpenAI 的 InstructGPT 模型中，预训练就占据了约 98% 的总体算力和数据投入[qiankunli.github.io](https://qiankunli.github.io/2023/12/18/llm_post_training.html#:~:text=%EF%BC%89%E9%98%B6%E6%AE%B5%E3%80%82%E7%84%B6%E8%80%8C%EF%BC%8C%E4%BB%8E%E5%AE%9E%E8%AF%81%E7%9A%84%E8%A7%92%E5%BA%A6%E6%9D%A5%E7%9C%8B%EF%BC%8C%E5%B0%86%E8%BF%99%E4%B8%89%E4%B8%AA%E6%AD%A5%E9%AA%A4%E7%BB%93%E5%90%88%E8%B5%B7%E6%9D%A5%E5%8F%AF%E4%BB%A5%E8%8E%B7%E5%BE%97%E6%9C%80%E4%BD%B3%E6%80%A7%E8%83%BD%E3%80%82%E9%A2%84%E8%AE%AD%E7%BB%83%E6%98%AF%E8%B5%84%E6%BA%90%E6%B6%88%E8%80%97%E6%9C%80%E5%A4%A7%E7%9A%84%E9%98%B6%E6%AE%B5%E3%80%82%E5%AF%B9%E4%BA%8EInstructGPT%E6%A8%A1%E5%9E%8B%EF%BC%8C%E9%A2%84%E8%AE%AD%E7%BB%83%E9%98%B6%E6%AE%B5%E5%8D%A0%E6%8D%AE%E4%BA%86%E6%95%B4%E4%BD%93%E8%AE%A1%E7%AE%97%E5%92%8C%E6%95%B0%E6%8D%AE%20%E8%B5%84%E6%BA%90%E7%9A%8498)。预训练完成后，模型会进入后续的微调阶段，包括\*\*有监督微调（SFT）**和**基于人类反馈的强化学习（RLHF）\*\*等，用较小但高质量的数据进一步定制模型行为，使其更加符合人类指令和价值观[qiankunli.github.io](https://qiankunli.github.io/2023/12/18/llm_post_training.html#:~:text=%E9%A2%84%E8%AE%AD%E7%BB%83%E6%A8%A1%E5%9E%8B%E6%98%AF%E4%B8%80%E4%B8%AA%E6%9C%AA%E5%8A%A0%E6%8E%A7%E5%88%B6%E7%9A%84%E2%80%9C%E6%80%AA%E7%89%A9%E2%80%9D%EF%BC%8C%E5%9B%A0%E4%B8%BA%E5%85%B6%E8%AE%AD%E7%BB%83%E6%95%B0%E6%8D%AE%E6%9D%A5%E6%BA%90%E4%BA%8E%E5%AF%B9%E4%BA%92%E8%81%94%E7%BD%91%E5%86%85%E5%AE%B9%E7%9A%84%E6%97%A0%E5%B7%AE%E5%88%AB%E6%8A%93%E5%8F%96%EF%BC%8C%E5%85%B6%E4%B8%AD%E5%8F%AF%E8%83%BD%E5%8C%85%E6%8B%AC%E7%82%B9%E5%87%BB%E8%AF%B1%E5%AF%BC%E3%80%81%E9%94%99%E8%AF%AF%E4%BF%A1%E6%81%AF%E3%80%81%E6%94%BF%E6%B2%BB%E7%85%BD%E5%8A%A8%E3%80%81%E9%98%B4%E8%B0%8B%E8%AE%BA%E6%88%96%E9%92%88%E5%AF%B9%E7%89%B9%E5%AE%9A%E4%BA%BA%E7%BE%A4%E7%9A%84%E6%94%BB%E5%87%BB%E7%AD%89%E5%86%85%E5%AE%B9%E3%80%82%202,Tuning%EF%BC%8C%E7%9B%91%E7%9D%A3%E5%BE%AE%E8%B0%83)。

如图1所示，LLM 的开发一般分为三个阶段[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=1,giving%20it%20a%20smiley%20face)：

1.  **预训练阶段** – 模型在海量互联网语料上自监督训练，掌握广泛的通用知识和语言能力。此时模型犹如一个“未加控制的野兽”，因其语料未经严格筛选，可能包含点击诱饵、错误信息、阴谋论或仇恨言论等内容[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=1,giving%20it%20a%20smiley%20face)。预训练阶段赋予模型基本的“阅读理解”能力和对语言模式的**背景知识**[qiankunli.github.io](https://qiankunli.github.io/2023/12/18/llm_post_training.html#:~:text=%E9%A2%84%E8%AE%AD%E7%BB%83%E6%A8%A1%E5%9E%8B%E6%98%AF%E4%B8%80%E4%B8%AA%E6%9C%AA%E5%8A%A0%E6%8E%A7%E5%88%B6%E7%9A%84%E2%80%9C%E6%80%AA%E7%89%A9%E2%80%9D%EF%BC%8C%E5%9B%A0%E4%B8%BA%E5%85%B6%E8%AE%AD%E7%BB%83%E6%95%B0%E6%8D%AE%E6%9D%A5%E6%BA%90%E4%BA%8E%E5%AF%B9%E4%BA%92%E8%81%94%E7%BD%91%E5%86%85%E5%AE%B9%E7%9A%84%E6%97%A0%E5%B7%AE%E5%88%AB%E6%8A%93%E5%8F%96%EF%BC%8C%E5%85%B6%E4%B8%AD%E5%8F%AF%E8%83%BD%E5%8C%85%E6%8B%AC%E7%82%B9%E5%87%BB%E8%AF%B1%E5%AF%BC%E3%80%81%E9%94%99%E8%AF%AF%E4%BF%A1%E6%81%AF%E3%80%81%E6%94%BF%E6%B2%BB%E7%85%BD%E5%8A%A8%E3%80%81%E9%98%B4%E8%B0%8B%E8%AE%BA%E6%88%96%E9%92%88%E5%AF%B9%E7%89%B9%E5%AE%9A%E4%BA%BA%E7%BE%A4%E7%9A%84%E6%94%BB%E5%87%BB%E7%AD%89%E5%86%85%E5%AE%B9%E3%80%82%202,Tuning%EF%BC%8C%E7%9B%91%E7%9D%A3%E5%BE%AE%E8%B0%83)。
    
2.  **有监督微调（SFT）阶段** – 使用人工整理的高质量问答对话、专业文本（如百科、问答社区）或人工标注数据，对预训练模型进行微调。通过监督学习，这一步**解锁**了模型在预训练中潜藏但未充分表达的能力[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=1,giving%20it%20a%20smiley%20face)。经过SFT微调后，模型从“野兽”转变为在社会规范内可接受的助手[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=1,giving%20it%20a%20smiley%20face)。
    
3.  **人类反馈强化学习（RLHF）阶段** – 在此阶段，引入人类偏好对模型进行强化训练，使其行为更贴近用户期待。例如通过让模型生成多个回答并由人类排名优劣，训练一个奖励模型，然后用策略优化（如PPO算法）微调模型[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=You%20can%20skip%20any%20of,steps%20gives%20the%20best%20performance)。RLHF使模型在保持能力的同时更加**有用、无害**，好比给驯服的怪兽带上了微笑面具[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=1,giving%20it%20a%20smiley%20face)。
    

需要注意，这三阶段并非绝对独立，有时可以省略其中一步直接进行下一步（例如直接在预训练模型上执行RLHF）但实践证明依次完成预训练→SFT→RLHF效果最佳[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=You%20can%20skip%20any%20of,steps%20gives%20the%20best%20performance)。预训练阶段奠定了模型的基础能力和知识面，而微调和对齐阶段则**激活**并定向这些能力，使模型最终成为实用的对话或任务助手[qiankunli.github.io](https://qiankunli.github.io/2023/12/18/llm_post_training.html#:~:text=%EF%BC%89%E9%98%B6%E6%AE%B5%E3%80%82%E7%84%B6%E8%80%8C%EF%BC%8C%E4%BB%8E%E5%AE%9E%E8%AF%81%E7%9A%84%E8%A7%92%E5%BA%A6%E6%9D%A5%E7%9C%8B%EF%BC%8C%E5%B0%86%E8%BF%99%E4%B8%89%E4%B8%AA%E6%AD%A5%E9%AA%A4%E7%BB%93%E5%90%88%E8%B5%B7%E6%9D%A5%E5%8F%AF%E4%BB%A5%E8%8E%B7%E5%BE%97%E6%9C%80%E4%BD%B3%E6%80%A7%E8%83%BD%E3%80%82%E9%A2%84%E8%AE%AD%E7%BB%83%E6%98%AF%E8%B5%84%E6%BA%90%E6%B6%88%E8%80%97%E6%9C%80%E5%A4%A7%E7%9A%84%E9%98%B6%E6%AE%B5%E3%80%82%E5%AF%B9%E4%BA%8EInstructGPT%E6%A8%A1%E5%9E%8B%EF%BC%8C%E9%A2%84%E8%AE%AD%E7%BB%83%E9%98%B6%E6%AE%B5%E5%8D%A0%E6%8D%AE%E4%BA%86%E6%95%B4%E4%BD%93%E8%AE%A1%E7%AE%97%E5%92%8C%E6%95%B0%E6%8D%AE%20%E8%B5%84%E6%BA%90%E7%9A%8498)。

总之，**预训练**是大模型构建的基石。它通过在海量文本上学习**下一个词预测**等任务，让模型获得广博的语言知识和表示能力，为后续的小规模高质量微调做好准备[qiankunli.github.io](https://qiankunli.github.io/2023/12/18/llm_post_training.html#:~:text=%E9%A2%84%E8%AE%AD%E7%BB%83%E6%A8%A1%E5%9E%8B%E6%98%AF%E4%B8%80%E4%B8%AA%E6%9C%AA%E5%8A%A0%E6%8E%A7%E5%88%B6%E7%9A%84%E2%80%9C%E6%80%AA%E7%89%A9%E2%80%9D%EF%BC%8C%E5%9B%A0%E4%B8%BA%E5%85%B6%E8%AE%AD%E7%BB%83%E6%95%B0%E6%8D%AE%E6%9D%A5%E6%BA%90%E4%BA%8E%E5%AF%B9%E4%BA%92%E8%81%94%E7%BD%91%E5%86%85%E5%AE%B9%E7%9A%84%E6%97%A0%E5%B7%AE%E5%88%AB%E6%8A%93%E5%8F%96%EF%BC%8C%E5%85%B6%E4%B8%AD%E5%8F%AF%E8%83%BD%E5%8C%85%E6%8B%AC%E7%82%B9%E5%87%BB%E8%AF%B1%E5%AF%BC%E3%80%81%E9%94%99%E8%AF%AF%E4%BF%A1%E6%81%AF%E3%80%81%E6%94%BF%E6%B2%BB%E7%85%BD%E5%8A%A8%E3%80%81%E9%98%B4%E8%B0%8B%E8%AE%BA%E6%88%96%E9%92%88%E5%AF%B9%E7%89%B9%E5%AE%9A%E4%BA%BA%E7%BE%A4%E7%9A%84%E6%94%BB%E5%87%BB%E7%AD%89%E5%86%85%E5%AE%B9%E3%80%82%202,Tuning%EF%BC%8C%E7%9B%91%E7%9D%A3%E5%BE%AE%E8%B0%83)。在以下章节中，我们将深入探讨预训练阶段涉及的核心方法、工程实践与关键决策，包括预训练的训练目标、数据治理、模型架构、分词器设计、优化策略、并行训练、评估指标，以及典型模型案例和实践建议，帮助读者全面理解这一过程的方方面面。

## 预训练任务目标与范式

在预训练阶段，模型通过**自监督任务**来学习语言规律，即利用海量未经人工标注的文本本身构造训练信号。常见的预训练目标有以下两大范式[blog.csdn.net](https://blog.csdn.net/weixin_43014882/article/details/142364523#:~:text=%E2%80%8C%E8%87%AA%E5%9B%9E%E5%BD%92%E6%A8%A1%E5%9E%8B%E5%92%8C%E6%8E%A9%E7%A0%81%E6%A8%A1%E5%9E%8B%E6%98%AF%E4%B8%A4%E7%A7%8D%E4%B8%8D%E5%90%8C%E7%9A%84%E9%A2%84%E8%AE%AD%E7%BB%83%E6%96%B9%E6%B3%95%EF%BC%8C%E5%AE%83%E4%BB%AC%E5%9C%A8%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E8%AE%AD%E7%BB%83%E4%B8%AD%E5%90%84%E6%9C%89%E4%BC%98%E5%8A%BF%E3%80%82%E2%80%8C)[blog.csdn.net](https://blog.csdn.net/weixin_43014882/article/details/142364523#:~:text=%E8%BF%99%E4%B8%A4%E7%A7%8D%E6%96%B9%E6%B3%95%E5%90%84%E6%9C%89%E7%89%B9%E7%82%B9%EF%BC%8C%E8%87%AA%E5%9B%9E%E5%BD%92%E6%A8%A1%E5%9E%8B%E6%9B%B4%E9%80%82%E5%90%88%E4%BA%8E%E7%94%9F%E6%88%90%E5%BC%8F%E4%BB%BB%E5%8A%A1%EF%BC%8C%E8%83%BD%E5%A4%9F%E7%94%9F%E6%88%90%E8%BF%9E%E8%B4%AF%E7%9A%84%E6%96%87%E6%9C%AC%EF%BC%8C%E8%80%8C%E6%8E%A9%E7%A0%81%E6%A8%A1%E5%9E%8B%E5%88%99%E6%9B%B4%E9%80%82%E5%90%88%E4%BA%8E%E7%90%86%E8%A7%A3%E5%BC%8F%E4%BB%BB%E5%8A%A1%EF%BC%8C%E8%83%BD%E5%A4%9F%E6%9B%B4%E5%A5%BD%E5%9C%B0%E7%90%86%E8%A7%A3%E4%B8%8A%E4%B8%8B%E6%96%87%E4%BF%A1%E6%81%AF%E3%80%82%E5%9C%A8%E5%AE%9E%E9%99%85%E5%BA%94%E7%94%A8%E4%B8%AD%EF%BC%8C%E8%BF%99%E4%B8%A4%E7%A7%8D%E6%96%B9%E6%B3%95%E7%BB%8F%E5%B8%B8%E7%BB%93%E5%90%88%20%E4%BD%BF%E7%94%A8%EF%BC%8C%E4%BB%A5%E5%85%85%E5%88%86%E5%88%A9%E7%94%A8%E5%AE%83%E4%BB%AC%E7%9A%84%E4%BC%98%E5%8A%BF%EF%BC%8C%E6%8F%90%E9%AB%98%E6%A8%A1%E5%9E%8B%E7%9A%84%E6%80%A7%E8%83%BD%E2%80%8C2%E3%80%82)：

-   **自回归语言建模（Causal LM）**：模型按从前到后的顺序，**根据已经看到的上下文预测下一个词**。典型如 GPT 系列模型，输入一个文本序列，模型需要依次预测每个位置的下一个单词[blog.csdn.net](https://blog.csdn.net/weixin_43014882/article/details/142364523#:~:text=%E2%80%8C%E8%87%AA%E5%9B%9E%E5%BD%92%E6%A8%A1%E5%9E%8B%E5%92%8C%E6%8E%A9%E7%A0%81%E6%A8%A1%E5%9E%8B%E6%98%AF%E4%B8%A4%E7%A7%8D%E4%B8%8D%E5%90%8C%E7%9A%84%E9%A2%84%E8%AE%AD%E7%BB%83%E6%96%B9%E6%B3%95%EF%BC%8C%E5%AE%83%E4%BB%AC%E5%9C%A8%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E8%AE%AD%E7%BB%83%E4%B8%AD%E5%90%84%E6%9C%89%E4%BC%98%E5%8A%BF%E3%80%82%E2%80%8C)。通过这种方式，模型学会了生成连贯文本的能力，因为训练过程即模拟了文本续写。自回归预训练使模型能够从大规模语料中学习语言模式和语义，为下游任务提供扎实基础[blog.csdn.net](https://blog.csdn.net/weixin_43014882/article/details/142364523#:~:text=%E2%80%8C%E8%87%AA%E5%9B%9E%E5%BD%92%E6%A8%A1%E5%9E%8B%E5%92%8C%E6%8E%A9%E7%A0%81%E6%A8%A1%E5%9E%8B%E6%98%AF%E4%B8%A4%E7%A7%8D%E4%B8%8D%E5%90%8C%E7%9A%84%E9%A2%84%E8%AE%AD%E7%BB%83%E6%96%B9%E6%B3%95%EF%BC%8C%E5%AE%83%E4%BB%AC%E5%9C%A8%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E8%AE%AD%E7%BB%83%E4%B8%AD%E5%90%84%E6%9C%89%E4%BC%98%E5%8A%BF%E3%80%82%E2%80%8C)。这类模型由于只能利用过去的词预测未来词，特别擅长**生成**任务，能够持续地创作文本。
    
-   **掩码语言建模（Masked LM）**：模型随机将输入序列中的部分单词遮掩，然后**根据上下文预测这些被遮掩的词**[blog.csdn.net](https://blog.csdn.net/weixin_43014882/article/details/142364523#:~:text=%E2%80%8C%E6%8E%A9%E7%A0%81%E6%A8%A1%E5%9E%8B%E2%80%8C%EF%BC%8C%E5%A6%82BERT%EF%BC%8C%E9%80%9A%E8%BF%87%E5%AF%B9%E5%8F%A5%E5%AD%90%E4%B8%AD%E7%9A%84%E9%9A%8F%E6%9C%BA%E5%8D%95%E8%AF%8D%E8%BF%9B%E8%A1%8C%E6%8E%A9%E7%A0%81%EF%BC%8C%E5%B9%B6%E8%AE%AD%E7%BB%83%E6%A8%A1%E5%9E%8B%E6%A0%B9%E6%8D%AE%E5%91%A8%E5%9B%B4%E4%B8%8A%E4%B8%8B%E6%96%87%E9%A2%84%E6%B5%8B%E6%8E%A9%E7%A0%81%E5%8D%95%E8%AF%8D%E3%80%82%E8%BF%99%E7%A7%8D%E6%96%B9%E6%B3%95%E6%9C%89%E5%8A%A9%E4%BA%8E%E6%A8%A1%E5%9E%8B%E7%90%86%E8%A7%A3%E5%8F%8C%E5%90%91%E4%B8%8A%E4%B8%8B%E6%96%87%EF%BC%8C%E4%BB%8E%E8%80%8C%E6%9B%B4%E5%A5%BD%E5%9C%B0%E7%90%86%E8%A7%A3%E5%92%8C%E7%94%9F%E6%88%90%E6%96%87%E6%9C%AC%E3%80%82%E6%8E%A9%E7%A0%81%20%E8%AF%AD%E8%A8%80%E5%BB%BA%E6%A8%A1%EF%BC%88MLM%EF%BC%89%E5%AF%B9%E5%8F%A5%E5%AD%90%E4%B8%AD%E7%9A%84%E9%9A%8F%E6%9C%BA%E5%8D%95%E8%AF%8D%E8%BF%9B%E8%A1%8C%E6%8E%A9%E7%A0%81%EF%BC%8C%E5%B9%B6%E8%AE%AD%E7%BB%83%E6%A8%A1%E5%9E%8B%E6%A0%B9%E6%8D%AE%E5%91%A8%E5%9B%B4%E4%B8%8A%E4%B8%8B%E6%96%87%E9%A2%84%E6%B5%8B%E6%8E%A9%E7%A0%81%E5%8D%95%E8%AF%8D%E3%80%82%E8%BF%99%E6%9C%89%E5%8A%A9%E4%BA%8E%E6%A8%A1%E5%9E%8B%E7%90%86%E8%A7%A3%E5%8F%8C%E5%90%91%E4%B8%8A%E4%B8%8B%E6%96%87%EF%BC%8C%E4%BD%BF%E5%85%B6%E8%83%BD%E5%A4%9F%E4%BB%8E%E5%A4%A7%E5%9E%8B%E8%AF%AD%E6%96%99%E5%BA%93%E4%B8%AD%E5%AD%A6%E4%B9%A0%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%BC%8F%E5%92%8C%E8%AF%AD%E4%B9%89%EF%BC%8C%E4%B8%BA%E7%89%B9%E5%AE%9A%20%E4%BB%BB%E5%8A%A1%E7%9A%84%E5%BE%AE%E8%B0%83%E6%8F%90%E4%BE%9B%E4%BA%86%E5%9D%9A%E5%AE%9E%E7%9A%84%E5%9F%BA%E7%A1%80%E2%80%8C1%E3%80%82)。典型如 BERT 模型，会随机遮盖15%左右的词，让模型填空。这种方法使模型同时利用左、右双向上下文来理解词语意义，对**理解**类任务更有利[blog.csdn.net](https://blog.csdn.net/weixin_43014882/article/details/142364523#:~:text=%E2%80%8C%E6%8E%A9%E7%A0%81%E6%A8%A1%E5%9E%8B%E2%80%8C%EF%BC%8C%E5%A6%82BERT%EF%BC%8C%E9%80%9A%E8%BF%87%E5%AF%B9%E5%8F%A5%E5%AD%90%E4%B8%AD%E7%9A%84%E9%9A%8F%E6%9C%BA%E5%8D%95%E8%AF%8D%E8%BF%9B%E8%A1%8C%E6%8E%A9%E7%A0%81%EF%BC%8C%E5%B9%B6%E8%AE%AD%E7%BB%83%E6%A8%A1%E5%9E%8B%E6%A0%B9%E6%8D%AE%E5%91%A8%E5%9B%B4%E4%B8%8A%E4%B8%8B%E6%96%87%E9%A2%84%E6%B5%8B%E6%8E%A9%E7%A0%81%E5%8D%95%E8%AF%8D%E3%80%82%E8%BF%99%E7%A7%8D%E6%96%B9%E6%B3%95%E6%9C%89%E5%8A%A9%E4%BA%8E%E6%A8%A1%E5%9E%8B%E7%90%86%E8%A7%A3%E5%8F%8C%E5%90%91%E4%B8%8A%E4%B8%8B%E6%96%87%EF%BC%8C%E4%BB%8E%E8%80%8C%E6%9B%B4%E5%A5%BD%E5%9C%B0%E7%90%86%E8%A7%A3%E5%92%8C%E7%94%9F%E6%88%90%E6%96%87%E6%9C%AC%E3%80%82%E6%8E%A9%E7%A0%81%20%E8%AF%AD%E8%A8%80%E5%BB%BA%E6%A8%A1%EF%BC%88MLM%EF%BC%89%E5%AF%B9%E5%8F%A5%E5%AD%90%E4%B8%AD%E7%9A%84%E9%9A%8F%E6%9C%BA%E5%8D%95%E8%AF%8D%E8%BF%9B%E8%A1%8C%E6%8E%A9%E7%A0%81%EF%BC%8C%E5%B9%B6%E8%AE%AD%E7%BB%83%E6%A8%A1%E5%9E%8B%E6%A0%B9%E6%8D%AE%E5%91%A8%E5%9B%B4%E4%B8%8A%E4%B8%8B%E6%96%87%E9%A2%84%E6%B5%8B%E6%8E%A9%E7%A0%81%E5%8D%95%E8%AF%8D%E3%80%82%E8%BF%99%E6%9C%89%E5%8A%A9%E4%BA%8E%E6%A8%A1%E5%9E%8B%E7%90%86%E8%A7%A3%E5%8F%8C%E5%90%91%E4%B8%8A%E4%B8%8B%E6%96%87%EF%BC%8C%E4%BD%BF%E5%85%B6%E8%83%BD%E5%A4%9F%E4%BB%8E%E5%A4%A7%E5%9E%8B%E8%AF%AD%E6%96%99%E5%BA%93%E4%B8%AD%E5%AD%A6%E4%B9%A0%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%BC%8F%E5%92%8C%E8%AF%AD%E4%B9%89%EF%BC%8C%E4%B8%BA%E7%89%B9%E5%AE%9A%20%E4%BB%BB%E5%8A%A1%E7%9A%84%E5%BE%AE%E8%B0%83%E6%8F%90%E4%BE%9B%E4%BA%86%E5%9D%9A%E5%AE%9E%E7%9A%84%E5%9F%BA%E7%A1%80%E2%80%8C1%E3%80%82)。通过掩码预测，模型学到如何结合上下文推断局部缺失信息，从而更好地学习词语间的双向依赖关系。掩码语言模型预训练生成的模型在问答、分类等需要理解全局语义的任务上表现突出。
    

两种预训练范式各有千秋：**自回归模型更适合生成任务**，能够流畅地产生连贯文本；**掩码模型更擅长理解任务**，对上下文关系的把握更精准[blog.csdn.net](https://blog.csdn.net/weixin_43014882/article/details/142364523#:~:text=%E4%BB%BB%E5%8A%A1%E7%9A%84%E5%BE%AE%E8%B0%83%E6%8F%90%E4%BE%9B%E4%BA%86%E5%9D%9A%E5%AE%9E%E7%9A%84%E5%9F%BA%E7%A1%80%E2%80%8C1%E3%80%82)。实际研发中，这两种方法也有融合应用的尝试，以兼顾生成和理解能力。例如，T5模型采用了一种\*\*“填空式序列到序列”**的预训练目标，即随机遮盖 spans 再让模型恢复，被视为掩码和自回归的结合；又如**XLNet\*\*提出随机排列序列来结合双向上下文的自回归建模。这些变种旨在综合两类范式之长。

需要强调的是，无论采用哪种预训练任务，目标都是让模型学会对语言形式和语义的建模。在预训练结束时，模型并没有针对任何特定下游任务进行优化，但它学到了“如何续写文本”或“如何补全文本”的一般技能。在随后微调时，我们可以根据具体任务（问答、翻译等）来**调整模型参数**，快速迁移预训练中学到的语言表示能力。

综上，预训练阶段常用的**自回归**与**掩码建模**分别对应了**生成**与**理解**两大类任务需求[blog.csdn.net](https://blog.csdn.net/weixin_43014882/article/details/142364523#:~:text=%E4%BB%BB%E5%8A%A1%E7%9A%84%E5%BE%AE%E8%B0%83%E6%8F%90%E4%BE%9B%E4%BA%86%E5%9D%9A%E5%AE%9E%E7%9A%84%E5%9F%BA%E7%A1%80%E2%80%8C1%E3%80%82)。针对应用场景选择合适的预训练目标十分关键：若模型主要用于生成对话或文章，可优先采用自回归预训练；若更注重阅读理解、分类等任务，则掩码模型的双向语境建模会更有效。此外，也可以根据需要混合多种目标，充分利用不同任务范式的优势来提升模型性能[blog.csdn.net](https://blog.csdn.net/weixin_43014882/article/details/142364523#:~:text=%E4%BB%BB%E5%8A%A1%E7%9A%84%E5%BE%AE%E8%B0%83%E6%8F%90%E4%BE%9B%E4%BA%86%E5%9D%9A%E5%AE%9E%E7%9A%84%E5%9F%BA%E7%A1%80%E2%80%8C1%E3%80%82)。

## 训练语料的数据治理

预训练成败在很大程度上取决于训练**语料数据**的质量和规模。因此，在预训练前对数据进行精心的治理至关重要[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Progress%20in%20natural%20language%20processing,on%20model%20size%20first%20and)[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=massive%20web%20crawls%20which%20can,pipelines%20and%20reduce%20the%20need)。数据治理涵盖语料来源选择、清洗与过滤、去重以及采样策略等方面，目的是构建一个**海量且高质量**的训练语料库。

**1\. 数据来源与组成**：主流LLM的预训练数据通常由多种来源混合而成，以确保广覆盖和多样性[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=challenging%20by%20the%20fact%20LLMs,intensive%3A%20typically%2C%20each%20source%20requires)[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Training%20Data)。常见的数据来源包括：

-   **通用网络爬取数据**：最大头的是互联网抓取的开放域文本，如**Common Crawl**项目提供的海量网页快照。网络语料数量极其庞大（粗略估计原始Common Crawl文本可达百万亿字符级别），是预训练的主要燃料[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=This%20joint%20scaling%20paradigm%20raises,2023)。例如 GPT-3 的训练语料约60%来自经过过滤的Common Crawl网页文本[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=%E2%96%A0%20GPT,level)；Meta的 LLaMA 使用了5次不同时间的Common Crawl数据，占其语料的67%[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Training%20Data)。网络数据涵盖新闻、博客、论坛等多种内容，丰富但良莠不齐，需要严格过滤。
    
-   **高质量的精选语料**：为了弥补纯网络数据质量参差的不足，训练集中往往会加入一些人工挑选的“精品”语料[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=challenging%20by%20the%20fact%20LLMs,intensive%3A%20typically%2C%20each%20source%20requires)。如**维基百科**文本、权威百科全书，**书籍语料**（小说、非小说书籍）、**学术论文**（ArXiv文章）、**技术文档**（如编程代码、软件手册）、**问答社区**（StackOverflow、Quora 等）等。这类语料质量高、信息密度大，虽然数量相对有限，但有助于模型习得更可靠的知识。以 LLaMA 为例，其1.4万亿标记的训练集中，大约4.5%来自维基百科、4.5%来自公开图书语料，2.5%来自ArXiv论文，2%来自StackExchange问答[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Wikipedia%20%5B4.5)[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=ArXiv%20%5B2.5)。这些高质量数据提高了模型的知识准确性和专业性。
    
-   **源代码语料**：一些LLM（尤其是通用模型）也会包括编程代码数据（如GitHub开源项目）[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=GitHub%20%5B4.5)。代码具有格式和结构信息，训练在代码上可以提高模型的精确性和逻辑能力。LLaMA的语料中约4.5%来自GitHub开源代码（仅限开源许可项目，并过滤无效内容）[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=GitHub%20%5B4.5)。包含代码还能赋予模型一定的编程和工具使用能力。
    

各来源数据在训练集中的占比需要平衡。通常**网络爬取数据占大头**（例如LLaMA中将近70%是预处理后的Common Crawl[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Training%20Data)），**精品数据占小头**。但是这小部分精品对提升模型效果往往功不可没[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=challenging%20by%20the%20fact%20LLMs,intensive%3A%20typically%2C%20each%20source%20requires)。如GPT-3使用了大量书籍、百科等（其语料40%非网络数据），据称这是其优于纯Common Crawl模型的重要原因之一[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=challenging%20by%20the%20fact%20LLMs,intensive%3A%20typically%2C%20each%20source%20requires)。

**2\. 数据清洗与过滤**：由于抓取的原始网络文本充满杂讯和不良内容，必须通过**严格的清洗**来保证训练数据质量[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=massive%20web%20crawls%20which%20can,pipelines%20and%20reduce%20the%20need)。典型的清洗与过滤措施包括：

-   **格式和内容筛选**：移除页面中的HTML标签、脚本、导航等模板内容，仅提取主正文（常用工具如 *jusText* 或 *trafilatura* 提取正文[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=curated%20dataFuzzy%3A%20MinHash%20%28%E2%88%BC%2026,natural%20language%20processing%20is%20increasingly)[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=massive%20web%20crawls%20which%20can,pipelines%20and%20reduce%20the%20need)）。过滤掉过短或乱码文本，确保每条数据有合理的句子结构和词汇量[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=deduplication%20and%20language%20identification%20steps%3A,and%20sentences%20in%20a%20webpage)。剔除含有过多非自然语言字符的内容（比如自动日志、代码片段在非代码语料中）[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=GitHub%20%5B4.5)。对于多语言爬取，还要用语言识别模型过滤出目标语言[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Five%20CommonCrawl%20dumps%2C%20ranging%20from,classified%20as%20references%20are%20discarded)（如LLaMA针对英文训练，用fastText检测语言后丢弃非英语页面[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Five%20CommonCrawl%20dumps%2C%20ranging%20from,classified%20as%20references%20are%20discarded)）。
    
-   **质量评分与规则**：很多预处理管线会为网页文本打一个质量分。比如LLaMA在Common Crawl预处理时训练了一个分类器来识别“像百科引用的页面”，只有被判为类似百科参考文献的页面才保留[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=pages%2C%20and%20filters%20low,classified%20as%20references%20are%20discarded)。C4数据集则用了启发式规则（如检查标点占比、单词和句子长度等）过滤低质量内容[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=During%20exploratory%20experiments%2C%20it%20was,and%20sentences%20in%20a%20webpage)。这些步骤旨在去除**自动生成、广告、色情、极端偏见**等不良文本，保留相对中立和有信息量的内容[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=quality%20of%20this%20data%20has,we%20propose%20to%20explore%20how)。OpenAI在GPT-3数据处理中训练了一个**内容过滤模型**，专门筛除质量差的网页，只保留类似书籍、维基等高质量来源[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=%E2%96%A0%20GPT,level)。
    
-   **敏感内容剔除**：为了安全和合规，会用黑名单或分类器过滤违法或极度不恰当内容。例如**NSFW词汇过滤**（不雅词、淫秽内容）[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=C4%20%E2%88%BC%20360GT%20Public%20100,Content%20filter%20trained%20on%20known)、**暴恐仇恨检测**，以及**隐私信息**（如身份证号、电话号码）检测等。Falcon的RefinedWeb语料明确使用了不良URL黑名单和NSFW词表过滤[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=C4%20%E2%88%BC%20360GT%20Public%20100,Content%20filter%20trained%20on%20known)[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=REFINEDWEB%20%E2%88%BC%205%2C%20000GT%20Public,removed%29%201.%20Introduction)。这样做既是道德要求，也是减少模型日后产生有害输出的必要步骤。
    

经过上述清洗过滤，虽然会损失相当比例的数据，但能显著提升剩余语料的信噪比。例如C4数据集对Common Crawl做质量过滤和脏文本删除，最终只保留了原始抓取的10%左右内容用于训练[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Dataset%20Size%20Availability%20Web%20CC,for%20results%20in%20this%20paper)。这些精炼后的数据在实验中被证明优于未经过滤的数据训练的模型[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=massive%20web%20crawls%20which%20can,pipelines%20and%20reduce%20the%20need)。

**3\. 数据去重（Deduplication）**：大规模爬取文本中存在大量**重复**（如版权书籍在不同网站出现多次，或相同文章被转载），如果不去重，模型可能多次看到完全一样的句子甚至段落。这会导致不必要的过拟合和对高频内容的记忆，还可能使模型**直接记住训练例子**，产生版权或隐私泄露风险[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=had%20argued%20that%20scaling%20should,no%20less%20than%203%2C500%20billion)[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=quality%20of%20this%20data%20has,we%20propose%20to%20explore%20how)。因此，对预训练语料进行去重处理是业界共识。

去重可分为**精确去重**和**模糊去重**两种方式：

-   *精确去重*：将文本切分成一定长度的片段（如句子或n连句[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Dataset%20Size%20Availability%20Web%20CC,for%20results%20in%20this%20paper)），对这些片段计算精确匹配，移除重复出现的部分。比如RefinedWeb对每条文本做**行级和文档级**精确去重，剔除了约50%的内容[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=document%20and%20line,removed%29%201.%20Introduction)。The Pile数据集也在去重时对每个样本计算MinHash签名实现近似匹配，去除了26%重复[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=%E2%96%A0%20GPT,level)。
    
-   *模糊去重*：利用哈希或MinHash等技术检测近似重复（即内容相似但不完全相同的文本）。GPT-3的语料用MinHash做模糊去重，约删除了10%的重复内容[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=%E2%96%A0%20GPT,level)。模糊去重可以发现改写或格式不同但实质重复的文本，进一步净化数据。
    

去重的尺度也需拿捏：过严可能把共同短语也滤掉，影响正常语言多样性；过松则重复仍然大量存在。通常做法是在句子或段落级别进行，高层去重（确保同一篇文章不会重复出现），同时允许常见短句在不同文章中保留。

值得一提的是，LAION团队在Falcon模型的数据集上提出的**RefinedWeb**策略，结合**严格的过滤**和**前所未有规模的去重**，构建了一个5万亿字符的高质量英文网页语料[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Table%201,removed)[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=REFINEDWEB%20%E2%88%BC%205%2C%20000GT%20Public,removed%29%201.%20Introduction)。他们的结果表明，**仅靠精炼的网络数据**（不含额外书籍或百科）也能训练出性能媲美甚至超过混合语料模型的LLM[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Contributions,1%2F7B%20parameters%20LLMs%20trained%20on)。这挑战了以往认为“网络数据不如人工精选语料”的看法[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=massive%20web%20crawls%20which%20can,pipelines%20and%20reduce%20the%20need)[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Contributions,1%2F7B%20parameters%20LLMs%20trained%20on)。RefinedWeb通过在**5万亿标记**的海量网页中应用强力去重和过滤，极大提高了数据质量，使Falcon等模型取得了优异的零样本基准表现[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Contributions,1%2F7B%20parameters%20LLMs%20trained%20on)。

**4\. 采样与数据混合策略**：在构建好语料库后，还需设计训练时的数据采样策略。如果数据来自不同源，可能采用**混合比例**（mixing ratios）控制每种源的呈现频率。常见策略包括：

-   **固定比例采样**：按照预先设定的比例混合各语料源。例如LLaMA就是严格按67%网络、15%C4、4.5%代码/书/维基等比例构建训练数据[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Training%20Data)[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Wikipedia%20%5B4.5)。这种策略简单直接，但需合理设定比例以免模型过度偏向某类语料。
    
-   **温度采样**：有些方案根据数据源重要性或质量设定一个温度，对高质量数据多采样、低质量少采样。例如EleutherAI的GPT-Neo训练使用过一种temperature-based mixing，对不同来源按质量指数调整抽取概率。
    
-   **分阶段课程学习**：先让模型训练若干步骤在较容易或干净的数据上，再逐步加入复杂或噪声更大的数据。这类似课程学习，对模型更友好。但LLM预训练中不常见此法，因为多数情况是同时混合训练。
    

此外，还需要决定**epoch数**（遍历语料的次数）。通常LLM的预训练数据量极大，往往**只训练1个epoch或更少**，即大部分数据模型只看一遍[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Overall%2C%20the%20entire%20training%20dataset,which%20perform%20approximately%20two%20epochs)。这与普通小数据训练多epoch不同。像LLaMA对绝大多数语料仅训练一次，但对少数高质量数据（维基和书）进行了约2次遍历[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Overall%2C%20the%20entire%20training%20dataset,which%20perform%20approximately%20two%20epochs)。这样确保模型充分利用珍贵的数据源。

综上，数据治理贯穿预训练准备的始终。从**多样来源的汇集**，到**严格清洗过滤**，再到**谨慎去重**和**科学采样**，每一步都影响最终模型的质量和行为。良好的数据治理可以在相同模型规模下**大幅提升**模型的效果[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=quality%20of%20this%20data%20has,we%20propose%20to%20explore%20how)[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Contributions,1%2F7B%20parameters%20LLMs%20trained%20on)。反之，若语料掺杂太多噪声和偏差，模型可能学到有害或无用的模式，给后续对齐带来负担。因此，投入时间精力打造一个干净、多元、平衡的预训练语料库，是训练出优秀LLM的关键基础。

## 模型架构选择与创新

预训练阶段采用怎样的**模型架构**，直接决定了模型的表达能力、训练难度以及推理效率。近年来，大语言模型几乎清一色地基于**Transformer架构**，但具体的结构选择和改进细节上仍有许多关键决策，包括使用编码器-解码器还是纯解码器、位置编码方案、激活函数以及高效注意力实现等。

**1\. Transformer解码器 vs 编码器-解码器**：当前主流LLM大多采用**Transformer解码器（decoder-only）**架构，例如GPT系列、LLaMA等[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=Phase%201)。解码器是单向自回归的，每层包含**带掩码的自注意力**和前馈网络，用于生成下一个词。这种架构天然适合文本生成任务，也是对话模型的首选。相比之下，**编码器-解码器**架构（如T5、BART）在预训练时需要双倍的参数（有独立的编码和解码器）并以完整序列到序列方式训练，更多用于需要输入输出对的任务（翻译、摘要）。对于通用LLM的预训练，decoder-only结构更简洁高效，且证明了卓越性能。因此绝大多数大模型预训练都选用**Transformer Decoder**堆叠。例如GPT-3使用96层解码Transformer；LLaMA-65B用80层解码器，每层有多头注意力和MLP子层[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Architecture)[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=The%20ReLU%20non,of%204d%20as%20in%20PaLM)。编码器-解码器在一些需要编码语义的场景有优势，但由于其生成流程相对复杂，在ChatGPT这类对话模型中并不常用。

**2\. 网络深度与宽度**：架构的一个核心参数是**层数**和**隐藏维度**。选择时往往遵循缩放律和平衡经验：更多层（深度）提高模型抽象能力，较宽的隐藏层和多头数（宽度）提供更多表示容量。像GPT-3（175B）选用了96层、每层隐藏状态12288维、Attention头数96、FFN层扩大4倍[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。而较小模型（如GPT-2 1.5B参数）用了48层、每层1600维。Chinchilla研究提出，在给定计算预算下，参数数量与训练token数应均衡增长[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。因此**模型大小（层数和维度）应与可用数据规模匹配**。如果数据不够，多增加层数效果有限，反而不如缩小模型多训些数据[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。这一洞见我们在稍后会详细讨论（见“Chinchilla定律”部分）。总之，架构设计时需结合算力预算，挑选合适的深度和宽度来充分利用数据又不过度浪费计算。

**3\. 正则和稳定性技巧**：深层Transformer在训练中容易出现梯度不稳定等问题，近年来一些架构层面的改进被证明能显著提升稳定性和效果：

-   **Pre-Norm vs Post-Norm**：Transformer最初在每个子层输出后使用Layer Norm，而GPT-2之后有研究改为在子层输入前规范化（Pre-LN）。实践发现**预归一化**可以使深层网络训练更稳定。GPT-3和LLaMA均采用了**RMSNorm的预归一化**，即每个Attention或MLP子层前用RMSNorm处理输入而非后归一化[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=The%20network%20is%20based%20on,in%20different%20models%20are%20leveraged)。这减少了梯度信号随层数衰减的问题，提高了收敛速度[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=The%20network%20is%20based%20on,in%20different%20models%20are%20leveraged)。
    
-   **激活函数改进**：经典Transformer用GELU激活，但PaLM等发现**SwiGLU**（一种门控Linear Units变体）略有提升[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=normalized%20,normalizing%20the%20output)。LLaMA也引入了SwiGLU并将FFN隐层维度从4倍隐藏降为$\\frac{2}{3}\\times4$倍（即约2.67倍）以减少参数[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=normalized%20,normalizing%20the%20output)。选择激活函数需在表现和效率间权衡，目前GELU、ReLU、SwiGLU各有使用，但SwiGLU在大模型中逐渐流行[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=normalized%20,normalizing%20the%20output)。
    
-   **位置编码方案**：Transformer需要为序列位置提供表示。早期使用固定的正弦位置编码，后来**相对位置编码**（Transformer-XL、T5等）和**旋转位置编码RoPE**成为趋势。[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Rotary%20Embeddings%20)LLaMA等采用了**RoPE（Rotary Position Embeddings）**，在每层Attention中通过对Q,K向量的分段旋转实现位置编码[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Rotary%20Embeddings%20)。RoPE的优点是**可推广性**强，允许模型在推理时处理超出训练长度的长序列，且保持相对位置关系[hub.baai.ac.cn](https://hub.baai.ac.cn/view/29979#:~:text=,CV%E5%90%84%E5%A4%A7%E6%96%B9%E5%90%91%E4%B8%93%E6%A0%8F%E4%B8%8E%E5%90%84%E4%B8%AA%E9%83%A8%E7%BD%B2%E6%A1%86%E6%9E%B6%E6%9C%80%E5%85%A8%E6%95%99%E7%A8%8B%E6%95%B4%E7%90%86)[hub.baai.ac.cn](https://hub.baai.ac.cn/view/29979#:~:text=%E5%A4%87%E6%B3%A8%EF%BC%9A%E4%BB%80%E4%B9%88%E6%98%AF%E5%A4%A7%E6%A8%A1%E5%9E%8B%E5%A4%96%E6%8E%A8%E6%80%A7%EF%BC%9F)。实验证明RoPE比绝对位置编码能让模型更好**外推**到更长文本，在LLaMA、ChatGLM、Baichuan等众多大模型中被广泛采用[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/667864459#:~:text=%E6%97%8B%E8%BD%AC%E4%BD%8D%E7%BD%AE%E7%BC%96%E7%A0%81RoPE%20,)[hub.baai.ac.cn](https://hub.baai.ac.cn/view/29979#:~:text=,CV%E5%90%84%E5%A4%A7%E6%96%B9%E5%90%91%E4%B8%93%E6%A0%8F%E4%B8%8E%E5%90%84%E4%B8%AA%E9%83%A8%E7%BD%B2%E6%A1%86%E6%9E%B6%E6%9C%80%E5%85%A8%E6%95%99%E7%A8%8B%E6%95%B4%E7%90%86)。相比之下，传统正余弦编码固定长度，不具备这种灵活性，因而逐渐被RoPE或ALiBi等方案取代。
    
-   **多头注意力的优化**：注意力机制是Transformer的核心，但其$O(n^2)$时空复杂度对长序列训练极为不利。为此，出现了许多高效注意力实现，如**FlashAttention**。FlashAttention通过融合多步计算并使用GPU高速显存，实现**准确Attention的内存访问优化**[hopsworks.ai](https://www.hopsworks.ai/dictionary/flash-attention#:~:text=Why%20is%20Flash%20Attention%20important%3F)[hopsworks.ai](https://www.hopsworks.ai/dictionary/flash-attention#:~:text=By%20strategically%20minimizing%20the%20back,memory%20usage%2C%20enabling%20scalable%20solutions)。它将Q/K/V一次性读入片上SRAM，分块计算Softmax，从而减少反复的数据搬运[hopsworks.ai](https://www.hopsworks.ai/dictionary/flash-attention#:~:text=By%20improving%20the%20efficiency%20of,bandwidth%20memory%20and%20processing%20units)[hopsworks.ai](https://www.hopsworks.ai/dictionary/flash-attention#:~:text=By%20strategically%20minimizing%20the%20back,memory%20usage%2C%20enabling%20scalable%20solutions)。这一改进显著加快了注意力计算，**训练速度提高3-5倍**，单卡A100可达每秒225万亿次浮点运算（约占理论峰值72%），且无需激活重计算节省显存[github.com](https://github.com/Dao-AILab/flash-attention#:~:text=We%20have%20released%20the%20full,don%27t%20need%20any%20activation%20checkpointing)。FlashAttention等技术让训练长上下文的大模型成为可能，在实际工程中已被广泛采用。例如新版的Transformers库和Megatron-LM都整合了FlashAttention，使得在1k甚至2k以上序列长度训练仍能高效运行。对于架构设计者而言，引入这些**注意力优化内核**是提升预训练效率的关键工程手段之一[github.com](https://github.com/Dao-AILab/flash-attention#:~:text=We%20have%20released%20the%20full,don%27t%20need%20any%20activation%20checkpointing)[hopsworks.ai](https://www.hopsworks.ai/dictionary/flash-attention#:~:text=Why%20is%20Flash%20Attention%20important%3F)。
    

除了上述方面，架构选择还涉及诸如**参数初始化**（如DeepScale启发的Scaled Init）、**归一化种类**（LayerNorm vs RMSNorm vs DeepNorm）、**残差路径设计**（是否有FeedForward残差）等细节优化。这些改进大多旨在**稳定深层网络训练**或**提高计算利用率**，逐步形成了如今LLM的标准架构。例如，GPT-3使用的Pre-LN + 大内积矩阵优化，如今在开源LLaMA等模型中也成了标配[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=The%20network%20is%20based%20on,in%20different%20models%20are%20leveraged)。可以说，大模型架构在Transformer基干上不断演进，集成了业界大量**经验教训**和**创新成果**。

总而言之，预训练模型架构需在**能力**与**可训练性**间取得平衡：既要有足够深度和复杂性容纳海量知识，又要通过合理的改进确保在大算力下稳定收敛。选择decoder-only还是encoder-decoder、定位编码方案、新型注意力算法，这些决策都深刻影响预训练效率和效果。时至今日，**Transformer解码器 + RoPE + FlashAttention + PreNorm**几乎成为大模型的“配置标配”，这是无数实验比较后形成的最佳实践[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Rotary%20Embeddings%20)[github.com](https://github.com/Dao-AILab/flash-attention#:~:text=We%20have%20released%20the%20full,don%27t%20need%20any%20activation%20checkpointing)。未来，随着研究推进，我们可能看到如Mixture-of-Experts（MoE）稀疏化、多查询注意力等更复杂的架构融入预训练，以进一步提升模型能力或降低计算成本。

## 分词器设计：BPE、Unigram 与多语言兼容

在将文本输入模型之前，必须经过**分词（Tokenization）**步骤将字符串切分成基本单元（token）。分词器的设计对预训练影响深远：它决定了模型词汇表和序列长度，也关系到不同语言的适用性。LLM常用的分词算法主要有**BPE（Byte Pair Encoding）**、**WordPiece**和**Unigram语言模型**三种[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%E4%BA%8C%E3%80%81BPE%EF%BC%88Byte%20Pair%20Encoding%EF%BC%89)[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。下面分别介绍它们的原理和特点，并讨论多语种场景下的分词挑战。

**1\. Byte Pair Encoding (BPE)**[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%E4%BA%8C%E3%80%81BPE%EF%BC%88Byte%20Pair%20Encoding%EF%BC%89)：BPE是一种基于字符频率的**贪心合并**算法[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=BPE%20%E6%98%AF%E4%B8%80%E7%A7%8D%E5%9F%BA%E4%BA%8E%E9%A2%91%E7%8E%87%E7%9A%84%E8%B4%AA%E5%BF%83%E5%90%88%E5%B9%B6%E7%AE%97%E6%B3%95%E3%80%82)。初始词汇表以单字符为单位，不断将最频繁相邻字符对合并成新符号，迭代进行直到达到预定词表大小[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=BPE%20%E6%98%AF%E4%B8%80%E7%A7%8D%E5%9F%BA%E4%BA%8E%E9%A2%91%E7%8E%87%E7%9A%84%E8%B4%AA%E5%BF%83%E5%90%88%E5%B9%B6%E7%AE%97%E6%B3%95%E3%80%82)。例如在中文语料`"天气真好天气真好"`中，BPE会首先将频繁共现的`“天”`和`“气”`合并为新符号`“天气”`，再将`“真”`和`“好”`合并为`“真好”`，最终把句子切成\[`天气`, `真好`, `天气`, `真好`\][blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。BPE的特点是**分词结果唯一**（贪心合并保证确定性）[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)、训练实现简单且速度快[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。它倾向于将常见高频词组合压缩为一个token，从而减少序列长度[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。GPT系列、RoBERTa以及通用的大模型如旷视的Qwen都采用了BPE分词[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。BPE的劣势是对低频或未见过的词可能切得过碎，但整体上它在英文等空格分词语言中表现良好，并已成为工业界应用最广的算法之一。

**2\. WordPiece**[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%E4%B8%89%E3%80%81WordPiece)：WordPiece与BPE类似，也是不停合并子词来扩充词表，但它的合并标准不是简单频次，而是**基于语言模型概率的提升**[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。具体而言，WordPiece每轮尝试一个可能的合并，选择使模型对训练语料的对数似然增加最多的合并项加入词表[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=WordPiece%20%E7%B1%BB%E4%BC%BC%20BPE%EF%BC%8C%E4%BD%86%E5%90%88%E5%B9%B6%E7%AD%96%E7%95%A5%E4%B8%8D%E6%98%AF%E5%9F%BA%E4%BA%8E%E9%A2%91%E7%8E%87%EF%BC%8C%E8%80%8C%E6%98%AF%E5%9F%BA%E4%BA%8E%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E7%9A%84%E4%BC%BC%E7%84%B6%E6%8F%90%E5%8D%87%E3%80%82)。这种方法更“**语言感知**”，因为它考虑了子词组合对整体概率的影响，而非仅频率[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%2A%20%E5%90%88%E5%B9%B6%E6%9B%B4%E2%80%9C%E8%AF%AD%E8%A8%80%E6%84%9F%E7%9F%A5%E2%80%9D%EF%BC%8C%E4%BD%86%E8%AE%AD%E7%BB%83%E6%85%A2%E3%80%82%20%2A%20%E4%BD%BF%E7%94%A8%E7%89%B9%E6%AE%8A%E7%AC%A6%E5%8F%B7%E8%A1%A8%E7%A4%BA%E5%AD%90%E8%AF%8D%E6%8B%BC%E6%8E%A5%EF%BC%88%E5%A6%82%20%E2%80%9C,%E6%9B%B4%E9%80%82%E5%90%88%E8%8B%B1%E6%96%87%E5%9C%BA%E6%99%AF%E3%80%82)。然而计算代价更高，训练较慢[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%2A%20%E5%90%88%E5%B9%B6%E6%9B%B4%E2%80%9C%E8%AF%AD%E8%A8%80%E6%84%9F%E7%9F%A5%E2%80%9D%EF%BC%8C%E4%BD%86%E8%AE%AD%E7%BB%83%E6%85%A2%E3%80%82%20%2A%20%E4%BD%BF%E7%94%A8%E7%89%B9%E6%AE%8A%E7%AC%A6%E5%8F%B7%E8%A1%A8%E7%A4%BA%E5%AD%90%E8%AF%8D%E6%8B%BC%E6%8E%A5%EF%BC%88%E5%A6%82%20%E2%80%9C,%E6%9B%B4%E9%80%82%E5%90%88%E8%8B%B1%E6%96%87%E5%9C%BA%E6%99%AF%E3%80%82)。WordPiece还常使用特殊连接标记（如`##`）表示后续子词[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%2A%20%E5%90%88%E5%B9%B6%E6%9B%B4%E2%80%9C%E8%AF%AD%E8%A8%80%E6%84%9F%E7%9F%A5%E2%80%9D%EF%BC%8C%E4%BD%86%E8%AE%AD%E7%BB%83%E6%85%A2%E3%80%82%20%2A%20%E4%BD%BF%E7%94%A8%E7%89%B9%E6%AE%8A%E7%AC%A6%E5%8F%B7%E8%A1%A8%E7%A4%BA%E5%AD%90%E8%AF%8D%E6%8B%BC%E6%8E%A5%EF%BC%88%E5%A6%82%20%E2%80%9C,%E6%9B%B4%E9%80%82%E5%90%88%E8%8B%B1%E6%96%87%E5%9C%BA%E6%99%AF%E3%80%82)。例如单词 "unhappiness" 可能被切成 `["un", "##happi", "##ness"]`[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。WordPiece最著名的应用是 Google 的 BERT 模型及其衍生（如DistilBERT）[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。由于其统计方式更贴合语言，WordPiece在英文场景下效果良好，对拼写变化敏感的场景（如词形变化）能更好处理。但相比BPE实现稍复杂，且对于中文等连续书写的语言，WordPiece没有明显优势。

**3\. Unigram Language Model**[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%E5%9B%9B%E3%80%81Unigram%20Language%20Model)：Unigram算法思路完全不同。它**不基于合并**，而是假设一个大型初始词表，然后不断**剪枝**掉不好的子词，最终得到最优词表[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。具体过程是：首先枚举所有可能的子词（例如将句子任意切分得到大量候选），初始化每个子词一个概率，然后用EM算法训练子词概率分布[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=1,%E5%89%AA%E6%9E%9D%E6%8E%89%E4%BD%8E%E6%A6%82%E7%8E%87%E5%AD%90%E8%AF%8D%EF%BC%8C%E4%BF%9D%E7%95%99%E8%AF%8D%E8%A1%A8%E3%80%82)。接着迭代地移除对整体概率贡献最小的子词，直至词表达到目标大小[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=1,%E5%89%AA%E6%9E%9D%E6%8E%89%E4%BD%8E%E6%A6%82%E7%8E%87%E5%AD%90%E8%AF%8D%EF%BC%8C%E4%BF%9D%E7%95%99%E8%AF%8D%E8%A1%A8%E3%80%82)。Unigram的特点是**灵活性高**，因为多种切分路径都有概率，只要概率不为零就可能存在[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)；因此同一文本**切分不唯一**，一定程度上提高了鲁棒性[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。Unigram被认为**特别适合多语言**或小语种场景[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)，因其初始词表大且保留多样碎片，能覆盖不同语言的多种组合。Google的 SentencePiece 工具实现的 Unigram 分词在 T5、mT5、ByT5、UL2 等模型中采用[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。例如对于中文“今天真高兴”，Unigram可能的切分有 `["今天","真","高兴"]` 或 `["今","天","真","高","兴"]` 等多种路径，最终选择概率最高的那一种作为输出[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%E8%AF%AD%E6%96%99%EF%BC%9A%60)。Unigram算法能自适应找到最优子词集合，在跨语言任务中表现出色，不过其实现和理解比BPE稍复杂。

上述三种算法各有优劣，可以从词表稳定性、多语言支持等角度比较[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%E7%89%B9%E6%80%A7%20BPE%20WordPiece%20Unigram%20%E5%90%88%E5%B9%B6%E7%AD%96%E7%95%A5,%E8%BE%83%E5%A4%8D%E6%9D%82%20%E5%B8%B8%E8%A7%81%E5%BA%94%E7%94%A8%E6%A8%A1%E5%9E%8B%20GPT%2FQwen%20BERT%20T5%2FmT5%2FUL2)（见表1）。**BPE**合并基于字符频率，切分唯一，支持多语言中等，简洁快速，适用于英文及训练资源充足场景[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%E5%90%88%E5%B9%B6%E7%AD%96%E7%95%A5%20%E5%AD%97%E7%AC%A6%E9%A2%91%E7%8E%87%20%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E6%8F%90%E5%8D%87%20%E6%A6%82%E7%8E%87%E5%89%AA%E6%9E%9D%20%E6%8B%86%E5%88%86%E5%94%AF%E4%B8%80%E6%80%A7%E2%9C%85,%E8%BE%83%E5%A4%8D%E6%9D%82%20%E5%B8%B8%E8%A7%81%E5%BA%94%E7%94%A8%E6%A8%A1%E5%9E%8B%20GPT%2FQwen%20BERT%20T5%2FmT5%2FUL2)。**WordPiece**考虑语言模型增益，切分唯一，多语言支持较弱，适合主要处理英文的模型如BERT[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%E5%90%88%E5%B9%B6%E7%AD%96%E7%95%A5%20%E5%AD%97%E7%AC%A6%E9%A2%91%E7%8E%87%20%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E6%8F%90%E5%8D%87%20%E6%A6%82%E7%8E%87%E5%89%AA%E6%9E%9D%20%E6%8B%86%E5%88%86%E5%94%AF%E4%B8%80%E6%80%A7%E2%9C%85,%E8%BE%83%E5%A4%8D%E6%9D%82%20%E5%B8%B8%E8%A7%81%E5%BA%94%E7%94%A8%E6%A8%A1%E5%9E%8B%20GPT%2FQwen%20BERT%20T5%2FmT5%2FUL2)。**Unigram**通过概率剪枝，切分不唯一，多语言支持强，适合需要覆盖多种语言或词形复杂的情况，如T5/mT5等[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%E5%90%88%E5%B9%B6%E7%AD%96%E7%95%A5%20%E5%AD%97%E7%AC%A6%E9%A2%91%E7%8E%87%20%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E6%8F%90%E5%8D%87%20%E6%A6%82%E7%8E%87%E5%89%AA%E6%9E%9D%20%E6%8B%86%E5%88%86%E5%94%AF%E4%B8%80%E6%80%A7%E2%9C%85,%E8%BE%83%E5%A4%8D%E6%9D%82%20%E5%B8%B8%E8%A7%81%E5%BA%94%E7%94%A8%E6%A8%A1%E5%9E%8B%20GPT%2FQwen%20BERT%20T5%2FmT5%2FUL2)。

*表1：主流分词算法对比[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=%E7%89%B9%E6%80%A7%20BPE%20WordPiece%20Unigram%20%E5%90%88%E5%B9%B6%E7%AD%96%E7%95%A5,%E8%BE%83%E5%A4%8D%E6%9D%82%20%E5%B8%B8%E8%A7%81%E5%BA%94%E7%94%A8%E6%A8%A1%E5%9E%8B%20GPT%2FQwen%20BERT%20T5%2FmT5%2FUL2)。BPE简单高效，但对多语言略显不足；WordPiece效果好但语言局限明显；Unigram灵活鲁棒，尤其胜任多语种任务。*

在**多语种LLM**中，分词器设计尤为关键。由于不同语言有不同的字母和词汇，理想情况下需要覆盖所有语言的常用词。通常做法是构建一个**多语种词表**，将多语言语料混合训练分词器。例如 mBERT 的WordPiece词表涵盖了100多种语言字符。但一个挑战是：固定词表大小下，语言越多，每种语言平均能分配的词汇越少，可能导致高频词被过度拆分，影响表现。因此，多语言LLM常使用**较大词表**（如GPT-3词表5万个主要英文，但XLM-R用了25万个覆盖100语言）。也有策略是在词表中保留各语种的一些特有token，以提高兼容性。另外，像Unigram这类方法对多语言天然有优势，可以在剪枝时平衡各语言概率，确保弱势语言也有必要的子词。实践中如 mT5 就采用Unigram分词，并使用**字节回退**（Byte-fallback）机制保证任何未收录字符都能以UTF-8字节形式编码，这样即使遇到训练中没见过的稀有语言字符，模型也能处理[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Tokenizer)。

总之，**选择合适的分词方案**需要考虑模型用途和语言范围。如果主要针对英文或少数语言，BPE/WordPiece已足够并能与已有模型对齐；若是多语言通用模型，Unigram往往表现更佳[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。另外还要综合**词表大小**、**字符集**、**是否区分大小写**等设置。一个精心设计的分词器能显著提升模型效率（较短的序列）和性能（避免过度碎片化导致的上下文不连贯）。反之，糟糕的分词可能让模型浪费容量去学习字符拼接，或者对罕见词泛化不佳。因此，分词器虽是预处理环节，却是预训练工程的基础模块之一，值得投入设计和优化。

## 优化策略与训练技巧

在预训练如此庞大模型的过程中，采用正确的**优化方法和训练技巧**对于高效收敛、稳定训练以及充分利用算力至关重要。本节我们讨论大模型预训练常用的优化算法、学习率调度、数值精度、梯度裁剪等实践经验。

**1\. 优化器选择**：现代LLM预训练几乎都使用变种的自适应优化器，以应对深层网络和稀疏梯度。**AdamW**是当前事实上的标准优化器[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。它是Adam（带一阶二阶动量估计）的改进版，引入**权重衰减**修正（不对梯度一二阶矩估计应用L2正则，而直接对权重衰减）[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。AdamW在稳定训练和防止过拟合方面表现出色。OpenAI的GPT系列、Google的Transformer模型等均采用AdamW。相比之下，简单SGD在如此高维问题上难以收敛，而AdaGrad等会导致学习率过快降低。另有一些优化器被尝试，如**LAMB/Distributed LAMB**（在大批量下调节Adam学习率）、**Adafactor**（Transformer-XL中用来省内存的一种Adam变体）等，但它们未成为主流。总的来说，**AdamW + 合理的学习率计划**目前仍是预训练的首选优化方案。

**2\. 学习率调度**：预训练通常迭代几十万到上百万步，一个适当的学习率调度策略对成功至关重要[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=,both%3F%20Compute%20blows%20up%20quickly)。常用的方法是**Warmup + 退火**：先在训练初期经过一段**warmup**（如几千步）将学习率线性从0增大到目标峰值，然后进入主训练阶段按一定曲线逐渐衰减学习率。衰减策略有**线性下降**、**余弦退火**、**多段阶梯**等。GPT-3使用了**线性衰减到0**策略：warmup 375M样本后（相当于约几千步），学习率达到$10^{-4}$，随后在260B样本内线性降至0[lifearchitect.ai](https://lifearchitect.ai/chinchilla/#:~:text=LifeArchitect,So%2C%20we%20need)。一些Google模型则偏好**余弦退火**，学习率沿余弦曲线缓慢降低至minimum。例如BERT采用1e-4起始，1万步warmup，然后1e-4 -> 0余弦下降。Warmup可避免初始大梯度破坏网络稳定，而退火确保后期充分收敛、降低震荡。大模型训练通常warmup比例相对很小（几百到几千步），但**必要**。此外，使用**AdamW**时注意要调节$\\beta\_1,\\beta\_2$（如0.9/0.95，0.98/0.999等），以及**eps**以稳定计算。总体经验是：**先快速升到较大学习率**以充分学习表示，然后**缓慢降学习率**来精细调参数，让损失渐进收敛。

**3\. 混合精度训练**：LLM预训练涉及海量矩阵运算，**混合精度**是必不可少的加速技巧。常用方案是**FP16混合精度**或更新的**bfloat16精度**。混合精度的原理是在保持模型主参数FP32存储的同时，用半精度（FP16/BF16）进行矩阵乘加等计算，并在可能溢出的步骤使用Loss Scaling等确保数值稳定。NVIDIA的AMP库已成熟运用于PyTorch、TensorFlow中，能自动将大部分操作降为FP16。混合精度通常带来**2~3倍**的加速并减少一半显存占用，而对最终模型精度几乎无影响。Google TPU上则倾向于使用**bfloat16**（具有更大范围，不需要Loss Scale），如PaLM训练就是全程bfloat16。现代GPU也支持bfloat16，因此很多框架提供选项。总之，**不使用混合精度就训练不了LLM**——无论存储还是算力都不允许。目前甚至出现**FP8**精度的研究，但在预训练中尚未普及。实践中推荐优先用bfloat16（更省心），若环境不支持则用AMP自动混合精度。确保精度时要监控Loss Scale是否发生溢出调整，以及关键张量保留FP32精度（如累积梯度、优化器状态）。

**4\. 梯度累积与批量大小**：受限于显存，大模型单卡可能只能放下很小的batch。这时常用**梯度累积**（Gradient Accumulation）技术：让模型在多次小批次前向后，累积梯度再一起更新。这相当于模拟一个更大批量。适当的有效批量（比如总和达到几千甚至上万）有助于稳定训练。GPT-3训练使用了Minibatch 2048 tokens/卡，累计到总批大小 3.2M tokens 再更新[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Medium%20medium,3)。如此巨大批量需要配合调整学习率（LAMB优化器就是为大批量设计）。一般经验，大模型预训练**总批量越大越好**，能充分利用并行度且梯度估计更准确，但要调低学习率避免振荡。实践中可根据GPU数和显存选择一个“per GPU batch”，再通过累积达到理想global batch。需要警惕的是，过大batch可能降低泛化，故而一些研究采用**学习率复合**（Linear Scaling Rule）或**启发式调参**来平衡。

**5\. 梯度裁剪**：为防止偶发梯度过大导致训练发散，通常会启用**梯度裁剪（Gradient Clipping）**。比较常用的是**基于全局范数裁剪**：当一次反向传播得到的所有梯度的$L2$范数超过预设阈值时，将其等比缩放，使范数等于阈值。比如阈值设为1，这样就防止参数更新过猛。GPT-3训练中也使用了梯度裁剪（阈值0.03）来稳定训练[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Medium%20medium,3)。梯度裁剪对防止罕见的梯度爆炸特别有效，在混合精度下也能缓解溢出。一般阈值需要根据模型和batch大小实验设定，小模型可用1，大模型通常更小（因为梯度规模大）。总的来说，**Gradient Clipping几乎是大模型训练的标配**，它提供了训练稳定性的一个保障。

**6\. 正则化和Dropout**：预训练因为数据极其丰富，通常不需要强正则避免过拟合，但还是会应用一些基本正则手段。**Weight Decay**通过AdamW自然地实现，一般设一个较小值（如0.01），帮助限制模型权重规模[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。**Dropout**在LLM中可以使用但比例往往较低（如0.1或0.0X），因为太大会损失容量。GPT-3并未显式提及使用Dropout，而Transformers论文中常用0.1。总的来说，预训练阶段模型远未拟合数据，因此正则项作用有限，反而需要模型尽可能记忆知识。所以正则化只需**适度**，过多会降低收敛速率和最终性能。

除上述要点外，还有一些训练技巧如**数据并行下的梯度同步延迟**（考虑LAMB/局部更新）、**学习率热重启**（cosine restart，如果遇到plateau）、**Mixed Precision下的动态loss scaling**等等。在此不一一展开。总体而言，大模型预训练的优化策略已经较为成熟：**AdamW优化 + 适当学习率调度 + 混合精度 + 梯度裁剪**被证明是一套可靠方案，可以在众多开源实现中借鉴使用[github.com](https://github.com/Dao-AILab/flash-attention#:~:text=We%20have%20released%20the%20full,don%27t%20need%20any%20activation%20checkpointing)[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。研究者在实践中应着重监控训练过程（如损失曲线、梯度范数、学习率）并根据需要调整这些策略参数，以确保模型以稳定的速度朝着最优方向收敛。

## 并行策略与系统工程

预训练LLM通常需要**数百亿乃至上千亿**参数，单机单卡远无法胜任训练和存储需求。因此必须采用**分布式并行训练**策略，将计算和模型拆分到多GPU/TPU上协同完成。常见的并行范式包括**数据并行**、\*\*模型并行（张量并行和流水线并行）\*\*以及一些内存优化并行（如ZeRO、FSDP）等[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Data%20parallelism)[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Model%20parallelism)。本节解释这些并行方法及典型组合。

**1\. 数据并行（Data Parallelism, DP）**[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Data%20parallelism)：数据并行是最朴素的并行方式，将**训练数据划分**给不同GPU，每个GPU各自拥有一份完整模型副本，处理不同的minibatch样本[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Data%20parallelism%20evenly%20distributes%20data,GPU%20are%20synchronized%20and%20combined)。每一步计算后，各GPU的梯度在**同步**阶段进行聚合平均，然后所有模型副本更新相同的参数[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=DataParallel%20supports%20distributed%20training%20on,single%20machine%20with%20multiple%20GPUs)[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=DistributedDataParallel%20supports%20distributed%20training%20across,multiple%20machines%20with%20multiple%20GPUs)。这样相当于按GPU数扩充了有效批量。数据并行的优势是实现简单、可线性扩展GPU数降低训练时间[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=end%2C%20the%20results%20from%20each,GPU%20are%20synchronized%20and%20combined)。PyTorch的`DistributedDataParallel (DDP)`就是标准的数据并行实现，可扩展到多机[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=DistributedDataParallel)。需要注意通信开销：每步反向传播后需要在GPU间交换梯度，但DDP通过环形All-Reduce算法和bucketing等优化降低了通信成本[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=2,pass)。数据并行对模型代码改动很少，因此成为**分布式训练的主力**。其缺点是每GPU需存一份完整模型，当模型巨大会受内存限制。同时通信在大GPU数时可能成为瓶颈。不过总体而言，如果模型能放入单卡，则数据并行是首选策略。

**2\. 模型并行（Model Parallelism）**：当模型本身太大单卡放不下时，就要切分模型结构，让不同部分由不同GPU保存和计算[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Model%20parallelism%20distributes%20a%20model,layer%20to%20the%20first%20layer)。模型并行的典型形式有：

-   **层间并行（流水线并行, Pipeline Parallelism）**[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Pipeline%20parallelism)：将模型的层按顺序分成若干块，各块部署在不同GPU。前向时数据流经GPU0的层组，再传递到GPU1…依次类推[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Model%20parallelism%20distributes%20a%20model,layer%20to%20the%20first%20layer)；反向传播则反方向传递梯度。这如同生产流水线。为了减少各设备空闲等待，可将一个mini-batch拆成多份微批次流水，通过流水线并行处理[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Pipeline%20parallelism%20is%20conceptually%20very,a%20mini%20batch%20of%20data)。例如2张卡、4层模型，每卡2层：microbatch1经GPU0层计算后立刻传GPU1处理，同时GPU0接收microbatch2计算其层……从而各卡交替工作[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Pipeline%20parallelism%20is%20conceptually%20very,a%20mini%20batch%20of%20data)。流水线并行**提高了设备利用率**，减少纯顺序执行的等待时间[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Pipeline%20parallelism)。但流水线最终仍需等待最后一个微批完成反传，存在“填充”开销，且实现较复杂，需要手工将模型拆段和管理缓存[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=batch%20of%20data)。PyTorch的`Pipe`、DeepSpeed Pipeline等提供了辅助工具。Pipeline并行主要解决**深度模型跨卡**问题。
    
-   **层内并行（张量并行, Tensor Parallelism）**[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Tensor%20parallelism)：将单个神经网络层的参数和计算拆分到多GPU。例如对于一个全连接层的权重矩阵，可以按行或列切分成几块，分别存储在不同GPU上[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Tensor%20parallelism%20distributes%20large%20tensor,to%20reconstruct%20the%20final%20result)。前向计算时，各GPU只处理自己那部分矩阵乘，结果在必要时汇总。这允许**同一层的计算由多卡并行完成**，从而突破单卡显存限制[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Tensor%20parallelism%20distributes%20large%20tensor,to%20reconstruct%20the%20final%20result)。常用的张量并行方式有：切分多头注意力的头（每GPU计算部分head）、切分FFN的中间维度等等。Megatron-LM实现了针对Transformer的张量并行：可以设置几卡并行Attention和FFN[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Tensor%20parallelism%20distributes%20large%20tensor,to%20reconstruct%20the%20final%20result)。张量并行的优势是对模型代码改动小（框架可封装底层通信），且**通信模式简单高效**（多数是在计算前后做All-Gather或Reduce-Scatter）。它的缺点是GPU间需要频繁同步计算结果，通信量随着并行度增加而上升。另外张量并行要求各并行分支计算量均衡，不然快的卡仍需等待最慢的卡完成。
    

**3\. 混合并行（Hybrid / 3D Parallelism）**：实际大规模训练常结合以上多种并行以充分利用资源[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=ZeRO%20data%20parallelism%2C%20pipeline%20parallelism%2C,3D%20parallelism)。最常见的是**数据并行 + 模型并行**的组合，有时再加流水线，被称为“3D并行”[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=ZeRO%20data%20parallelism%2C%20pipeline%20parallelism%2C,3D%20parallelism)。例如Megatron-LM里，一个64 GPU的集群可以先按8GPU做张量并行（每个层8卡并行），再这基础上8组间做流水线并行（每组算模型一段），最后8组一起做数据并行。这实现了参数、计算、数据多层次拆分，使得即使千亿参数模型也能在有限显存GPU上训练[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Data%2C%20pipeline%20and%20model%20parallelism,optimize%20memory%20and%20compute%20efficiency)[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Compute%20efficiency%20is%20enabled%20by,with%20the%20other%20pipeline%20stages)。Microsoft DeepSpeed也提出3D并行方案，将数据、张量、流水线融合[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=ZeRO%20data%20parallelism%2C%20pipeline%20parallelism%2C,3D%20parallelism)。这些杂交并行需要精心划分并行维度和通信，但做得好可极大提升**计算效率**和**内存利用率**[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Memory%20efficiency%20is%20achieved%20by,the%20model%2C%20optimizer%2C%20and%20activations)。近年来谷歌的GSPMD提出了一种通用并行编译框架，用户只需对张量加少量注解，编译器即可自动混合实现各种并行[research.google](https://research.google/blog/general-and-scalable-parallelization-for-neural-networks/#:~:text=simply%20needs%20to%20add%20a,and%20enables%20easy%20porting%20of)[research.google](https://research.google/blog/general-and-scalable-parallelization-for-neural-networks/#:~:text=parallelism%20algorithms%20appropriate%20for%20different,split%20into%20smaller%2C%20parallel%20operators)。例如在Transformer中标注哪几个张量如何切分，GSPMD就能产出结合数据、张量、流水线的并行执行方案[research.google](https://research.google/blog/general-and-scalable-parallelization-for-neural-networks/#:~:text=simply%20needs%20to%20add%20a,and%20enables%20easy%20porting%20of)[research.google](https://research.google/blog/general-and-scalable-parallelization-for-neural-networks/#:~:text=The%20separation%20of%20model%20programming,implementation%20with%20previous%20smaller%20models)。GSPMD已在TensorFlow/XLA和JAX中应用，让开发者几乎像写单机代码一样训练超大模型[research.google](https://research.google/blog/general-and-scalable-parallelization-for-neural-networks/#:~:text=parallelization,a%20mathematically%20equivalent%2C%20parallelized%20computation)[research.google](https://research.google/blog/general-and-scalable-parallelization-for-neural-networks/#:~:text=The%20separation%20of%20model%20programming,implementation%20with%20previous%20smaller%20models)。这种自动并行代表未来方向，但目前主流开源实现还是以手工混合Parallel为主。

**4\. 内存优化并行 (ZeRO / FSDP)**：除了算力并行，**内存瓶颈**也是大模型训练难点。特别是数据并行会在每GPU上保存一份完整模型、优化器状态，占用巨量内存。为此，Microsoft提出了**ZeRO (Zero Redundancy Optimizer)**技术，通过在数据并行进程间**分摊存储**模型参数、梯度和优化器状态，实现近乎线性省内存[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Zero%20Redundancy%20Optimizer%20is%20a,There%20are%20three%20ZeRO%20stages)。ZeRO分三级：Stage 1分摊优化器状态（如动量、二阶矩）；Stage 2再分摊梯度张量；Stage 3甚至分摊模型参数本身，每块参数只存在于一个进程，其它需要用时再通信调度[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=reduce%20memory%20usage,three%20ZeRO%20stages)。ZeRO-3基本达到每GPU只存模型一部分，多个GPU合起来才有完整模型，**内存冗余降到零**[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Zero%20Redundancy%20Optimizer%20is%20a,There%20are%20three%20ZeRO%20stages)。PyTorch后来整合了类似思想推出**FSDP（Fully Sharded Data Parallel）**[pytorch.org](https://pytorch.org/blog/introducing-pytorch-fully-sharded-data-parallel-api/#:~:text=PyTorch%20Distributed%20data%20parallelism%20is,the%20simplicity%20of%20data%20parallelism)。FSDP本质就是ZeRO-3：将模型参数、梯度、优化器状态全部均匀切片到各GPU，正向计算前再gather需要的参数碎片，计算完后立即scatter回去，释放显存[pytorch.org](https://pytorch.org/blog/introducing-pytorch-fully-sharded-data-parallel-api/#:~:text=How%20FSDP%20Works)[pytorch.org](https://pytorch.org/blog/introducing-pytorch-fully-sharded-data-parallel-api/#:~:text=Figure%201)。这样，单卡显存要求大幅降低，使训练**万亿参数**模型成为可能（Facebook曾用FSDP训练1万亿参数模型，单卡只要放下1/数千的参数）[pytorch.org](https://pytorch.org/blog/introducing-pytorch-fully-sharded-data-parallel-api/#:~:text=Scaling%20tests%20of%20PyTorch%20FSDP,when%20CPU%20offloading%20was%20enabled)。FSDP在PyTorch 1.11+中已经成熟，可以一键包裹模型使用[pytorch.org](https://pytorch.org/blog/introducing-pytorch-fully-sharded-data-parallel-api/#:~:text=With%20PyTorch%201,APIs%20and%20additional%20performance%20improvements)。它还能结合CPU Offload，把暂时不用的碎片转移到CPU内存进一步节省[pytorch.org](https://pytorch.org/blog/introducing-pytorch-fully-sharded-data-parallel-api/#:~:text=Figure%201)。ZeRO和FSDP的代价是增加了一些通信和参数调度开销，但实践证明在大模型场景下这点开销相对于能训练更大模型而言值得接受。如今绝大多数超大模型训练（如开源的GPT-neoX、Bloom等）都使用DeepSpeed ZeRO或PyTorch FSDP来突破单机内存限制[pytorch.org](https://pytorch.org/blog/introducing-pytorch-fully-sharded-data-parallel-api/#:~:text=PyTorch%20Distributed%20data%20parallelism%20is,the%20simplicity%20of%20data%20parallelism)[pytorch.org](https://pytorch.org/blog/introducing-pytorch-fully-sharded-data-parallel-api/#:~:text=How%20FSDP%20Works)。

综上，**并行训练**是大模型训练的核心工程问题之一。开发者需要根据模型规模和集群条件选择适当的并行组合：如果模型小于单卡显存且节点通信较慢，可主要用数据并行扩展；如果模型太大放不下，就必须引入模型并行（张量或流水线）来拆分；如仍不够，还需要ZeRO/FSDP等进一步碎片化内存。理想情况下，我们希望并行策略对研发者透明（如GSPMD自动划分[research.google](https://research.google/blog/general-and-scalable-parallelization-for-neural-networks/#:~:text=simply%20needs%20to%20add%20a,and%20enables%20easy%20porting%20of)），但目前往往需要调优来达到效率最优。例如，Megatron-LM作者提到，达到最佳性能可能需要同时使用数据、张量、流水线3种并行，而且各自GPU拓扑要精心匹配NVLink/NVSwitch结构[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=largest%20model%20layer%20doesn%E2%80%99t%20fit,PipelineParallel%2C%20TensorParallel%2C%20DataParallel)[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Data%2C%20pipeline%20and%20model%20parallelism,optimize%20memory%20and%20compute%20efficiency)。

一个成功的案例是NVIDIA在2020年发布的**Megatron-Turing NLG 530B**模型训练：他们用了**8-way张量并行**+**8-stage流水线**，共64 GPU 一组进行模型并行，再在此基础上进行数据并行跨16组，总计1024 GPU协同[uvadlc-notebooks.readthedocs.io](https://uvadlc-notebooks.readthedocs.io/en/latest/tutorial_notebooks/scaling/JAX/3d_parallelism.html#:~:text=Part%205%3A%20Language%20Modeling%20with,models%20like%20large%20language)。同时搭配了DeepSpeed ZeRO Stage 2优化内存。最终实现了规模达5300亿参数的训练[uvadlc-notebooks.readthedocs.io](https://uvadlc-notebooks.readthedocs.io/en/latest/tutorial_notebooks/scaling/JAX/3d_parallelism.html#:~:text=Part%205%3A%20Language%20Modeling%20with,models%20like%20large%20language)。由此可见，善用组合并行才能充分发挥大型硬件集群的威力。

总而言之，并行策略是将庞大训练任务拆解的艺术。随着模型和数据规模的爆炸性增长，高效的并行技术变得愈发重要。从**横向扩展**（数据并行）到**纵向切分**（模型并行）再到**巧用存储**（ZeRO/FSDP），这些手段相辅相成，共同支撑起LLM的训练工程。未来，我们期待更智能的并行编译和调度，让开发者无需手工划分就能在大规模集群上顺畅训练上万亿参数的模型。

## 预训练阶段的评估指标与验证

在耗费巨量资源进行预训练时，我们需要持续监控和评估模型表现，以判断训练是否顺利进行、何时收敛，以及模型已掌握的能力。预训练阶段的评估与微调后的任务评估有所不同，主要依赖**固有指标**（如困惑度）和少量**零样本任务**测试。下面介绍常用的评估指标和机制：

**1\. 困惑度（Perplexity, PPL）**[blog.csdn.net](https://blog.csdn.net/qq_36485259/article/details/136617494#:~:text=%E6%98%AF%E8%87%AA%E7%84%B6%E8%AF%AD%E8%A8%80%E5%A4%84%E7%90%86%EF%BC%88NLP%EF%BC%89%E4%B8%AD%E5%B8%B8%E7%94%A8%E7%9A%84%E4%B8%80%E7%A7%8D%E8%AF%84%E4%BC%B0%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E7%9A%84%E6%8C%87%E6%A0%87%E3%80%82%E5%AE%83%E8%A1%A1%E9%87%8F%E7%9A%84%E6%98%AF%E6%A8%A1%E5%9E%8B%E5%AF%B9%E6%B5%8B%E8%AF%95%E6%95%B0%E6%8D%AE%E7%9A%84%E9%A2%84%E6%B5%8B%E8%83%BD%E5%8A%9B%EF%BC%8C%E5%8D%B3%E6%A8%A1%E5%9E%8B%E5%AF%B9%E6%B5%8B%E8%AF%95%E9%9B%86%E4%B8%AD%E5%8D%95%E8%AF%8D%E5%BA%8F%E5%88%97%E5%87%BA%E7%8E%B0%E6%A6%82%E7%8E%87%E7%9A%84%E9%A2%84%E6%B5%8B%E5%87%86%E7%A1%AE%E5%BA%A6%E3%80%82%E5%9B%B0%E6%83%91%E5%BA%A6%E8%B6%8A%E4%BD%8E%EF%BC%8C%E8%A1%A8%E7%A4%BA%E6%A8%A1%E5%9E%8B%E5%AF%B9%20%E6%95%B0%E6%8D%AE%E7%9A%84%E9%A2%84%E6%B5%8B%E8%B6%8A%E5%87%86%E7%A1%AE%E3%80%82)：困惑度是语言模型好坏的经典指标，反映模型对测试文本的预测不确定性[blog.csdn.net](https://blog.csdn.net/qq_36485259/article/details/136617494#:~:text=%E6%98%AF%E8%87%AA%E7%84%B6%E8%AF%AD%E8%A8%80%E5%A4%84%E7%90%86%EF%BC%88NLP%EF%BC%89%E4%B8%AD%E5%B8%B8%E7%94%A8%E7%9A%84%E4%B8%80%E7%A7%8D%E8%AF%84%E4%BC%B0%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E7%9A%84%E6%8C%87%E6%A0%87%E3%80%82%E5%AE%83%E8%A1%A1%E9%87%8F%E7%9A%84%E6%98%AF%E6%A8%A1%E5%9E%8B%E5%AF%B9%E6%B5%8B%E8%AF%95%E6%95%B0%E6%8D%AE%E7%9A%84%E9%A2%84%E6%B5%8B%E8%83%BD%E5%8A%9B%EF%BC%8C%E5%8D%B3%E6%A8%A1%E5%9E%8B%E5%AF%B9%E6%B5%8B%E8%AF%95%E9%9B%86%E4%B8%AD%E5%8D%95%E8%AF%8D%E5%BA%8F%E5%88%97%E5%87%BA%E7%8E%B0%E6%A6%82%E7%8E%87%E7%9A%84%E9%A2%84%E6%B5%8B%E5%87%86%E7%A1%AE%E5%BA%A6%E3%80%82%E5%9B%B0%E6%83%91%E5%BA%A6%E8%B6%8A%E4%BD%8E%EF%BC%8C%E8%A1%A8%E7%A4%BA%E6%A8%A1%E5%9E%8B%E5%AF%B9%20%E6%95%B0%E6%8D%AE%E7%9A%84%E9%A2%84%E6%B5%8B%E8%B6%8A%E5%87%86%E7%A1%AE%E3%80%82)。形式上，给定模型参数$\\theta$和一段由$N$个词$w\_1...w\_N$组成的测试文本$W$，困惑度定义为$PPL(W) = \\exp{!-\\frac{1}{N}\\sum\_{i=1}^N \\log P\_\\theta(w\_i \\mid w\_{<i})}$[blog.csdn.net](https://blog.csdn.net/qq_36485259/article/details/136617494#:~:text=%E5%9B%B0%E6%83%91%E5%BA%A6%E9%80%9A%E5%B8%B8%E5%AE%9A%E4%B9%89%E4%B8%BA%E6%B5%8B%E8%AF%95%E9%9B%86%E4%B8%8A%E7%9A%84%E4%BA%A4%E5%8F%89%E7%86%B5%E7%9A%84%E6%8C%87%E6%95%B0%E3%80%82%E5%AF%B9%E4%BA%8E%E4%B8%80%E4%B8%AA%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%EF%BC%8C%E5%A6%82%E6%9E%9C%E7%BB%99%E5%AE%9A%E4%B8%80%E4%B8%AA%E9%95%BF%E5%BA%A6%E4%B8%BA%20NN%20N%20%E7%9A%84%E8%AF%8D%E5%BA%8F%E5%88%97%20W%3Dw1%2Cw2%2C%E2%80%A6%2CwNW%3Dw_1%2Cw_2%2C,W%3Dw%201%2Cw%202%2C%E2%80%A6%2Cw%20N%EF%BC%8C%E5%85%B6%E5%9B%B0%E6%83%91%E5%BA%A6%E5%8F%AF%E4%BB%A5%E8%A1%A8%E7%A4%BA%E4%B8%BA%EF%BC%9A)。它等价于测试集上交叉熵损失的指数[blog.csdn.net](https://blog.csdn.net/qq_36485259/article/details/136617494#:~:text=%E5%9B%B0%E6%83%91%E5%BA%A6%E9%80%9A%E5%B8%B8%E5%AE%9A%E4%B9%89%E4%B8%BA%E6%B5%8B%E8%AF%95%E9%9B%86%E4%B8%8A%E7%9A%84%E4%BA%A4%E5%8F%89%E7%86%B5%E7%9A%84%E6%8C%87%E6%95%B0%E3%80%82%E5%AF%B9%E4%BA%8E%E4%B8%80%E4%B8%AA%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%EF%BC%8C%E5%A6%82%E6%9E%9C%E7%BB%99%E5%AE%9A%E4%B8%80%E4%B8%AA%E9%95%BF%E5%BA%A6%E4%B8%BA%20NN%20N%20%E7%9A%84%E8%AF%8D%E5%BA%8F%E5%88%97%20W%3Dw1%2Cw2%2C%E2%80%A6%2CwNW%3Dw_1%2Cw_2%2C,W%3Dw%201%2Cw%202%2C%E2%80%A6%2Cw%20N%EF%BC%8C%E5%85%B6%E5%9B%B0%E6%83%91%E5%BA%A6%E5%8F%AF%E4%BB%A5%E8%A1%A8%E7%A4%BA%E4%B8%BA%EF%BC%9A)。直观地，困惑度可以理解为模型在每个位置上平均有多少等可能的选项——越小表示模型越确信正确词是什么[blog.csdn.net](https://blog.csdn.net/qq_36485259/article/details/136617494#:~:text=%E6%98%AF%E8%87%AA%E7%84%B6%E8%AF%AD%E8%A8%80%E5%A4%84%E7%90%86%EF%BC%88NLP%EF%BC%89%E4%B8%AD%E5%B8%B8%E7%94%A8%E7%9A%84%E4%B8%80%E7%A7%8D%E8%AF%84%E4%BC%B0%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E7%9A%84%E6%8C%87%E6%A0%87%E3%80%82%E5%AE%83%E8%A1%A1%E9%87%8F%E7%9A%84%E6%98%AF%E6%A8%A1%E5%9E%8B%E5%AF%B9%E6%B5%8B%E8%AF%95%E6%95%B0%E6%8D%AE%E7%9A%84%E9%A2%84%E6%B5%8B%E8%83%BD%E5%8A%9B%EF%BC%8C%E5%8D%B3%E6%A8%A1%E5%9E%8B%E5%AF%B9%E6%B5%8B%E8%AF%95%E9%9B%86%E4%B8%AD%E5%8D%95%E8%AF%8D%E5%BA%8F%E5%88%97%E5%87%BA%E7%8E%B0%E6%A6%82%E7%8E%87%E7%9A%84%E9%A2%84%E6%B5%8B%E5%87%86%E7%A1%AE%E5%BA%A6%E3%80%82%E5%9B%B0%E6%83%91%E5%BA%A6%E8%B6%8A%E4%BD%8E%EF%BC%8C%E8%A1%A8%E7%A4%BA%E6%A8%A1%E5%9E%8B%E5%AF%B9%20%E6%95%B0%E6%8D%AE%E7%9A%84%E9%A2%84%E6%B5%8B%E8%B6%8A%E5%87%86%E7%A1%AE%E3%80%82)[blog.csdn.net](https://blog.csdn.net/qq_36485259/article/details/136617494#:~:text=%E5%BD%93%E6%88%91%E4%BB%AC%E8%AF%B4%E6%A8%A1%E5%9E%8B%E5%AF%B9%E6%B5%8B%E8%AF%95%E9%9B%86%E4%B8%AD%E5%8D%95%E8%AF%8D%E5%BA%8F%E5%88%97%E7%9A%84%E9%A2%84%E6%B5%8B%E5%B9%B3%E5%9D%87%E6%AF%8F%E4%B8%AA%E4%BD%8D%E7%BD%AE%E7%9A%84%E4%B8%8D%E7%A1%AE%E5%AE%9A%E6%80%A7%E7%9B%B8%E5%BD%93%E4%BA%8E%E4%BA%8C%E8%BF%9B%E5%88%B6%E9%80%89%E6%8B%A9%E4%B8%AD%E7%9A%84%202)。例如，一个完美模型看到文本会非常确定下一个词（困惑度接近1），而糟糕的模型则接近随机猜测（困惑度接近词表大小）。在预训练中，我们通常计算**验证集**的困惑度随训练进度的曲线。验证集是一小部分未参与训练的语料，其困惑度持续下降意味着模型在泛化提升。当困惑度趋于平稳时（下降缓慢），通常表示接近收敛。困惑度低也往往预示模型在下游任务上会有更好表现（尽管不是绝对）。因此，监控困惑度是预训练中的**核心诊断**：它提供一个量化指标来比较不同模型（困惑度低者语言建模能力强）[blog.csdn.net](https://blog.csdn.net/qq_39610915/article/details/116225356#:~:text=NLP%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E7%82%B9%EF%BC%9A%E5%9B%B0%E6%83%91%E5%BA%A6%EF%BC%88Perplexity%EF%BC%89%20,)。需要注意，不同语料和不同语言的困惑度不直接可比，通常同一验证集下比较或看下降比率。

**2\. 学习曲线与收敛验证**：训练过程中绘制的**loss/困惑度曲线**可以揭示训练动态。理想情况下，训练损失和验证损失都会平滑下降。如果观察到验证损失下降趋缓甚至上升，可能出现了**过拟合**。不过在海量数据和参数下，过拟合较少发生于预训练初期，更多是**欠拟合**风险：如曲线长期平台期，可能学习率太低或模型容量不足。常用做法是如果验证困惑度在长时间内不再改善，就考虑**提前停止**训练，节省算力。还有一个重要曲线是**训练loss对数线性图**，DeepMind研究指出语言模型的损失随计算量（FLOPs）呈现幂律下降关系[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Progress%20in%20natural%20language%20processing,on%20model%20size%20first%20and)[medium.com](https://medium.com/@kiran.phd.0102/maximizing-language-model-training-efficiency-insights-from-chinchilla-paper-training-ccbbb173940#:~:text=Approach%202%3A%20Exploring%20IsoFLOP%20Profiles)。监控是否遵循预期的幂律能判断训练是否有效率。比如Chinchilla论文通过多次训练运行拟合出loss关于训练量和模型大小的公式，当实际loss高于预测值太多，就说明训练未达最优，需要调整策略[medium.com](https://medium.com/@kiran.phd.0102/maximizing-language-model-training-efficiency-insights-from-chinchilla-paper-training-ccbbb173940#:~:text=The%20crux%20was%20fitting%20power,prior%20analyses%2C%20emphasizing%20its%20potential)[medium.com](https://medium.com/@kiran.phd.0102/maximizing-language-model-training-efficiency-insights-from-chinchilla-paper-training-ccbbb173940#:~:text=Figure%202%3A%20IsoFLOP%20Curves)。另外，可以在训练中周期性测试**few-shot学习曲线**：取少数下游任务（如关闭形式的语言理解题）评估模型零样本或少样本下的准确率，看是否随训练提升。这些曲线可以作为停训或调参的参考。

**3\. 零样本评估（Zero-Shot Evaluation）**：在预训练完成或中期检查时，常会直接让模型在未微调的情况下尝试一些下游任务，以粗略评估其通用能力[lakera.ai](https://www.lakera.ai/blog/large-language-model-evaluation#:~:text=Tools%20www,questions%20not%20explicitly%20represented)。零样本评估即不给模型任何额外训练，只提供任务说明或样例，直接看模型输出。例如：

-   **完形填空（Cloze）**：给模型一段句子让其补全空缺，以测试语言理解。例如LAMBADA数据集要求根据长上下文预测最后一个词，预训练模型可以直接测该任务的准确率。一个强的预训练模型在LAMBADA上零样本准确率会很高，GPT-3达到了76%[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=The%20result%20of%20the%20pretraining,Stability%20AI)（相比随机猜低得多）。
    
-   **下游选择题**：如HellaSwag、PIQA等常识推理选择题，可以提供问题和选项，让模型生成哪个是正确答案（通过log概率最高判断）。这无需微调也可测出模型的常识水平。Chinchilla模型被报告在零样本常识任务上明显优于同等计算的大模型[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=%2A%20LLaMA,benchmarks%20despite%20being%20much%20smaller)。
    
-   **翻译、问答**：给一个句子前加指令"Translate to French:"看模型产出，或者直接问一个常识问答，看未微调模型能否回答。这类测试可衡量模型的**Few-shot能力**：因为预训练模型未专门学翻译，但它见过多语文本，可能具备一定翻译本领。
    

Zero-shot评估的意义在于：预训练模型虽然不是为特定任务优化，但**涌现**出了一系列能力，可以不经微调直接完成简单任务[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=Phase%201)。例如GPT-3展示的现象——未微调的175B模型在TriviaQA问答、自然语言推理等多项任务上逼近有监督SOTA[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=%2A%20LLaMA,benchmarks%20despite%20being%20much%20smaller)[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=%2A%20LLaMA,despite%20being%205%E2%80%9310%20times%20smaller)。这证明了足够规模的预训练模型自发学到了很多语义、常识和推理知识。因而研究者会在预训练结束时对模型进行一系列基准测试，如**MMLU（多学科知识问答）**、**BoolQ**、**WiC**等，统计零样本准确率或F1，以与以往模型比较[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=%2A%20LLaMA,benchmarks%20despite%20being%20much%20smaller)。例如LLaMA-13B在多个零样本基准上就超越了GPT-3 175B[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=%2A%20LLaMA,benchmarks%20despite%20being%20much%20smaller)，这说明预训练策略更优导致了更高的知识效率。

需要强调，零样本评估**并非完美**指标：模型可能通过微调极大改善某任务表现，但零样本不突出；反之，有的能力零样本显现却难以通过RLHF提升。因此，它只是预训练阶段的一个参考。近年来还有学者提出更系统的预训练评测，如EleutherAI的**Language Model Evaluation Harness**集合了几十种NLP任务，方便对新模型跑零样本和少样本测试[github.com](https://github.com/EleutherAI/lm-evaluation-harness#:~:text=This%20project%20provides%20a%20unified,number%20of%20different%20evaluation%20tasks)。斯坦福的**HELM**框架也提供统一测评报告。不过在预训练阶段，我们往往聚焦**困惑度**等固有指标来指导训练过程，而将全面任务评测留到模型完成训练之后进行。

**4\. 验证机制**：为确保预训练过程中模型没有出现意外退化或崩溃，需要建立一些验证机制。除了前述定量指标外，还可有人为检查模型输出。比如定期抽取模型生成的一段文本，人工主观评估流畅度、内容合理性。如果发现训练到某步后输出质量突然变差，可能暗示训练问题（如数据错误注入、优化器异常）。大型训练通常也会记录**检查点（checkpoint）**，便于出问题时回滚。同时可在不同step的checkpoint上运行零样本评估，看性能曲线。如果性能不再提升甚至下降，说明可能过拟合或Learning Rate过大导致泛化变差，此时可考虑提早终止或调整学习率策略。

还有一个简单的验证技巧是**比较前后两版模型对同一问题的回答**。预训练中期，可以问模型一些知识性问题，记录答案。训练结束再问一次，看是否明显改进。这虽非严格评估，但能直观反映模型学到了什么新知识（例如早期回答错误的问题后来答对了）。

总的来说，预训练评估围绕\*\*“模型学会了语言吗”**这个核心展开，偏重**概率式指标**和**一般能力\*\*检测，而不像微调那样针对特定任务精调指标。困惑度提供了基础衡量，其降低意味着模型越来越擅长预测语言[blog.csdn.net](https://blog.csdn.net/qq_36485259/article/details/136617494#:~:text=%E6%98%AF%E8%87%AA%E7%84%B6%E8%AF%AD%E8%A8%80%E5%A4%84%E7%90%86%EF%BC%88NLP%EF%BC%89%E4%B8%AD%E5%B8%B8%E7%94%A8%E7%9A%84%E4%B8%80%E7%A7%8D%E8%AF%84%E4%BC%B0%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E7%9A%84%E6%8C%87%E6%A0%87%E3%80%82%E5%AE%83%E8%A1%A1%E9%87%8F%E7%9A%84%E6%98%AF%E6%A8%A1%E5%9E%8B%E5%AF%B9%E6%B5%8B%E8%AF%95%E6%95%B0%E6%8D%AE%E7%9A%84%E9%A2%84%E6%B5%8B%E8%83%BD%E5%8A%9B%EF%BC%8C%E5%8D%B3%E6%A8%A1%E5%9E%8B%E5%AF%B9%E6%B5%8B%E8%AF%95%E9%9B%86%E4%B8%AD%E5%8D%95%E8%AF%8D%E5%BA%8F%E5%88%97%E5%87%BA%E7%8E%B0%E6%A6%82%E7%8E%87%E7%9A%84%E9%A2%84%E6%B5%8B%E5%87%86%E7%A1%AE%E5%BA%A6%E3%80%82%E5%9B%B0%E6%83%91%E5%BA%A6%E8%B6%8A%E4%BD%8E%EF%BC%8C%E8%A1%A8%E7%A4%BA%E6%A8%A1%E5%9E%8B%E5%AF%B9%20%E6%95%B0%E6%8D%AE%E7%9A%84%E9%A2%84%E6%B5%8B%E8%B6%8A%E5%87%86%E7%A1%AE%E3%80%82)。而零样本任务测试揭示模型内部蕴含的多方面技能。通过结合这些评估，我们可以：1）监控训练进展和收敛；2）在不同模型配置间进行客观比较；3）初步了解模型潜力所在，为后续微调方向提供依据。

举例来说，DeepMind在训练70亿参数Chinchilla模型时，观察到其验证困惑度相对更大的Gopher模型大幅降低[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Progress%20in%20natural%20language%20processing,on%20model%20size%20first%20and)，且Chinchilla在58项任务中有51项零样本表现优于Gopher[arxiv.org](https://arxiv.org/pdf/2203.15556#:~:text=%5BPDF%5D%20Training%20Compute,does%20Chinchilla%20outperform%20its)。这充分证明了Chinchilla预训练策略的优越性。这样的比较不需要Chinchilla经过专门微调，就能以客观评测结果体现。

最后值得一提的是，随着模型规模增长，出现了一些\*\*“涌现能力（Emergent Abilities）”\*\*：在较小模型上完全不起作用的任务，超过某一规模门槛的模型突然能解决。预训练评估已经发现例如模型达到几十亿参数后，才能零样本解简单数学题或编写代码。这提醒我们，对预训练模型能力的认识需要不断更新，**规模本身也是性能的一个维度**。评估时应照顾不同大小模型的特点，不能以偏概全。

总之，在漫长的预训练过程中，持续的评估是不可或缺的。它帮助我们确保模型**沿着正确方向**学习，并在结束时对模型的**通用能力**有一个初步量化。后续的SFT和RLHF虽然能大幅提升模型在人机对话等方面的质量，但都是建立在一个高困惑度低、知识储备丰富的预训练模型之上的。因此，我们可以说：**预训练评估指标是模型“大脑”开发的体检报告**，决定了这个大脑底子有多好、需要在哪些方面加强。只要预训练评估表现优异，后面的微调才能“事半功倍”地将其打造成真正智能的助手。

## 典型开源模型与前沿研究

近年来，大语言模型领域诞生了许多具有里程碑意义的模型和研究工作。通过分析这些**典型模型**的预训练策略和创新，我们可以更直观地理解预训练阶段的重要决策和发展趋势。下面选取几个代表性的模型和项目，介绍其预训练要点：

-   **GPT 系列（OpenAI）**：GPT 是“Generative Pre-trained Transformer”的缩写，标志着通用自回归预训练范式的崛起。GPT-1（2018年）体量不大但证明了预训练-微调范式的有效性。GPT-2（2019年，15亿参数）采用大规模WebText语料预训练，展示出惊人的文本生成能力，首次引发大众关注。GPT-3（2020年，1750亿参数）将参数规模提升两个数量级，使用了当时空前的45TB文本（约3000亿Token）进行预训练[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=,3%20has%20175%20billion%20parameters)[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=3%EF%B8%8F%E2%83%A3%20The%20GPT)。其数据混合了Common Crawl、百科、书籍和网页问答等，并使用了混合精度、模型并行等技术克服算力限制[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=3%EF%B8%8F%E2%83%A3%20The%20GPT)。GPT-3的训练突出贡献在于**few-shot学习**能力：无需梯度更新，凭提示就能执行复杂任务。这直接来自预训练规模+泛化的成果。OpenAI后来没有公开GPT-3的权重，但通过论文分享了方法。GPT-3预训练的一个发现是它其实“**训练不足**”：只用300B token，而Chinchilla理论指出应有1400B token才匹配175B参数[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。这为后续优化提供了思路。总体而言，GPT系列引领了**纯解码Transformer + 超大规模数据**的预训练风潮，是之后模型的蓝本。ChatGPT和GPT-4虽然未公开细节，但可以推测预训练仍延续GPT-3思路，可能规模更大、数据更多元，并融入代码等新语料。
    
-   **Chinchilla（DeepMind）**：Chinchilla是DeepMind在2022年提出的一个具有划时代意义的概念验证模型，大小约70亿参数[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。它的特殊之处在于**训练策略的突破**：根据新的“**计算最优**”理论，Chinchilla用和Gopher（280B参数）相同的计算预算，选择了较小模型但训练了**4倍的token**（即1.4万亿token），结果性能全面超越了Gopher[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Medium%20medium,3)。这一结果证明了Hoffmann等提出的经验定律：给定算力，**应适当缩小模型、扩增训练数据**来达到最佳效果[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=,model%20trained%20on%20less%20data)[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。Chinchilla在MMLU百科问答基准上比Gopher平均高7.6%准确率[arxiv.org](https://arxiv.org/pdf/2203.15556#:~:text=%5BPDF%5D%20Training%20Compute,in%20addition%20to%20performing)，在多数任务上胜过更大模型，这震撼了业界。Chinchilla的预训练在架构上无特殊新颖（与Gopher类似的Transformer），关键是**数据量**。为了支撑1.4T tokens，他们扩充了语料（包括更多网络文本等）。Chinchilla成功后，许多后来的模型开始遵循它的compute-optimal原则，如OpenAI据传在GPT-4中也采用更长训练来充分训练模型。Chinchilla的出现，也让社区反思此前“只堆参数不增数据”的做法，推动了数据集获取和清洗的研究热潮（RefinedWeb正是在此背景下出现[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Progress%20in%20natural%20language%20processing,on%20model%20size%20first%20and)[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=massive%20web%20crawls%20which%20can,pipelines%20and%20reduce%20the%20need)）。总之，Chinchilla代表了**预训练规模效益**的新拐点：不是一味更大模型，而是**更高效地利用算力**。它让我们看到，小模型只要预训练到位，也能有大智慧。
    
-   **LLaMA 系列（Meta）**：LLaMA是Meta AI于2023年推出的系列基础模型，有7B、13B、33B、65B等规模，在学术界和开源社区引起巨大反响。它们的**预训练策略**体现了近年来最佳实践的集合。LLaMA使用仅公开数据训练，却达到了甚至超过封闭模型（如GPT-3）的性能[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=%2A%20LLaMA,benchmarks%20despite%20being%20much%20smaller)。其关键因素包括：1）**海量多样数据**：1.4万亿tokens来自多源高质语料[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Training%20Data)[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=Wikipedia%20%5B4.5)（67% CommonCrawl精滤版，15% C4，4.5% GitHub代码，4.5%维基百科，4.5%图书，2.5%ArXiv，2%StackExchange）。这些数据组合充分且相对干净。2）**平衡的模型尺寸**：65B参数模型匹配1.4T数据，遵循Chinchilla建议，果然表现优异[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=%2A%20LLaMA,benchmarks%20despite%20being%20much%20smaller)。3）**尖端架构**：采用RoPE位置编码、SwiGLU激活、RMSNorm预归一化等最新架构改进[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=The%20network%20is%20based%20on,in%20different%20models%20are%20leveraged)[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=The%20ReLU%20non,of%204d%20as%20in%20PaLM)。4）**高效实现**：使用FlashAttention、高性能GPU集群使预训练得以在合理时间内完成。LLaMA最初未公开权重给大众（仅供学术），但之后意外泄露，使得开源社区有机会在此基础上微调出大量衍生模型（如Alpaca、Vicuna等）。LLaMA的成功证明了：即便在没有额外人类标注数据的情况下，仅靠强大的预训练也能得到**功能强大的通用语言模型**，而其参数量远小于GPT-3却性能更好。这强调了数据和策略的重要性。后续Meta又发布了LLaMA-2，增加了对话微调部分，但其预训练仍延续LLaMA-1方法。因此学习LLaMA有助于了解**开源条件下如何构建一流LLM**。
    
-   **Falcon & RefinedWeb（TII UAE）**：Falcon是阿联酋TII机构在2023年发布的开源大模型（7B和40B参数），曾登上开放模型性能榜首。其预训练最大的特色在于**使用纯网络数据RefinedWeb**却达到了媲美混合语料模型的效果[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=We%20introduce%20REFINEDWEB%2C%20a%20high,web%20data%20alone%20can)[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Contributions,1%2F7B%20parameters%20LLMs%20trained%20on)。RefinedWeb数据集包含约5万亿token的英文网页文本[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Contributions,1%2F7B%20parameters%20LLMs%20trained%20on)。TII团队通过大规模抓取84次Common Crawl，共提取上百万篇文章，然后应用严格的过滤规则（NSFW剔除、不良URL黑名单等）和**全局去重**（包括MinHash模糊去重），最终整理出质量远高于原始抓取的数据子集[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=C4%20%E2%88%BC%20360GT%20Public%20100,Content%20filter%20trained%20on%20known)[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=REFINEDWEB%20%E2%88%BC%205%2C%20000GT%20Public,removed%29%201.%20Introduction)。这一数据比OpenAI的Web文本规模大得多，并经过精炼。Falcon-40B用这份数据训练，从零样本评测看，其英语能力超过了同时期很多混合数据的模型（如Meta的OPT）[huggingface.co](https://huggingface.co/datasets/tiiuae/falcon-refinedweb#:~:text=Falcon%20RefinedWeb%20is%20a%20massive,By%201.0%20license)。这证明了**海量网页数据只要清洗到位，照样能产出高性能模型**[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=massive%20web%20crawls%20which%20can,pipelines%20and%20reduce%20the%20need)[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Contributions,1%2F7B%20parameters%20LLMs%20trained%20on)。Falcon项目对开源社区贡献在于提供了RefinedWeb 1.0版本数据（600B token可下载）[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=Contributions,1%2F7B%20parameters%20LLMs%20trained%20on)和训练细节，使他人可以复现或改进。它也让大家重新重视互联网作为宝库——毕竟精品语料有限，但Web可不断获取，只要策略得当，就能“以量取胜”。Falcon模型架构与GPT类似，也采用了FlashAttention等优化，是当前开源世界一个重要里程碑。
    
-   **OLMo 项目（AI2）**：OLMo是Allen AI提出的“Open Language Model”计划，旨在打造一个**从数据到代码全开放**的大模型训练框架[allenai.org](https://allenai.org/olmo#:~:text=OLMo%20is%20Ai2%E2%80%99s%20first%20O,details%20in%20our%20technical%20report)[allenai.org](https://allenai.org/olmo#:~:text=OLMo%20is%20fully%20open)。它的意义不仅在于模型本身，更在于开放研究。OLMo项目开发了**Dolma**数据集（一套开源的大模型预训练语料），并训练了7B、13B等开源模型[allenai.org](https://allenai.org/olmo#:~:text=OLMo%202%2032B)[allenai.org](https://allenai.org/olmo#:~:text=OLMo%202%20)。他们的理念是：开放权重不够，还要开放数据和训练过程，让学术界也能深入研究LLM[allenai.org](https://allenai.org/olmo#:~:text=OLMo%20is%20fully%20open)。OLMo-2系列模型在2024年发布了32B参数版本，声称达到甚至超过GPT-3.5的学术基准表现[allenai.org](https://allenai.org/olmo#:~:text=OLMo%202%2032B%20is%20the,skill%20academic%20benchmarks)。关键是他们用**6万亿token**进行了充分预训练，同时提供了训练代码、超参配置、中间checkpoint等供社区检验[allenai.org](https://allenai.org/olmo#:~:text=open%20and%20accessible%20training%20data%2C,are%20in%20our%20technical%20report)[allenai.org](https://allenai.org/olmo#:~:text=to%206T%20tokens%20and%20post,skill%20academic%20benchmarks)。OLMo证明，**开源协作**可以打造高性能模型，透明度并不会损害竞争力。这一项目还特别注重**评估和安全**，他们开放了评测套件，方便社区复现他们报告的结果[allenai.org](https://allenai.org/olmo#:~:text=Evaluation)。OLMo对预训练领域的启示是：当行业巨头日益封闭自研时，仍有机构致力于开源开放，推动**科学研究**而非商业黑箱。通过OLMo，我们可以获取宝贵的一手训练经验（如处理某些数据分布的方法、训练大模型的故障排除等），这些都是平时闭源模型里学不到的。
    

以上例举的项目各有亮点：GPT系列体现了**规模提升**带来的范式转变，Chinchilla强调**高效利用算力**的重要，LLaMA展示了**数据与架构优化**的惊人效果，Falcon则聚焦**超大规模开放数据**的潜力，OLMo代表**开放科研**的路线。它们共同描绘了大模型预训练的发展脉络。

除了这些，值得一提的还有如**Google PaLM**（540B参数，用路径分解注意力等提升训练）、**微软的MT-NLG**（530B参数，与NVIDIA合作，着重3D并行）、**EleutherAI GPT-NeoX和Pythia**（开源仿GPT-3模型，提供不同规模checkpoint用于研究可伸缩性）等。这些项目无不在预训练方法上有所探索：例如PaLM引入**SwiGLU激活**[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=normalized%20,normalizing%20the%20output)，并尝试混合语料；Pythia提供了随规模不同的模型系列以研究**缩放规律**。

另一方面，**RefinedWeb、RedPajama、SlimPajama**等开放数据集项目，大大推动了数据治理技术。RedPajama复制了LLaMA的1.2T token数据配方[together.ai](https://www.together.ai/blog/redpajama#:~:text=,2%20trillion%20tokens)并开源，为后来者省去了大量收集整理工作；SlimPajama在此基础上**再去重30%**，得到627B高质数据，测试发现模型性能更佳[cerebras.ai](https://www.cerebras.ai/blog/slimpajama-a-627b-token-cleaned-and-deduplicated-version-of-redpajama#:~:text=SlimPajama%3A%20A%20627B%20token%2C%20cleaned,%282023%29)。这些都在验证一个理念：**数据质量几乎同等重要于模型架构**。

总之，通过典型模型案例我们看到，大模型预训练领域在过去几年取得了长足进展。一方面模型规模不断攀升，另一方面人们对如何\*\*“有效训练”**大型模型的理解也更深入了。从早期朴素地扩大模型、增加数据，到如今精打细算地安排参数与数据量、巧用并行和优化器，再到未来也许探索**多模态预训练\*\*（图文并举）或**知识注入**（结合知识图谱）等，每一步都源于前人的经验和新研究的指引。学习这些里程碑项目，可以帮助从业者少走弯路，站在巨人的肩膀上设计新的模型。

## 实践建议：构建1B–7B模型的落地路径

对于希望在实际项目中训练一个规模约数亿到几十亿参数的大语言模型的团队（如企业研发或学术实验室），在有限资源下如何**落地预训练**是一项艰巨但可行的任务。本节结合前文理念，给出一些实践层面的建议和关键决策指南，帮助开发者规划从无到有训练一个1B–7B参数模型的路径。

**1\. 明确需求，确定规模**：首先评估模型的应用场景和可用资源。如果目标是训练一个专用领域模型（如医疗问答）且后续仍需微调，那么**不必一味追求参数量**，几亿到十亿参数可能就足够，重点应放在领域数据质量上。若希望模型具备较通用能力，7B左右参数是当前小团队可考虑的上限（7B模型如LLaMA-7B在许多任务已有不错表现）。切忌好高骛远——模型参数翻倍，训练难度和成本远超线性增加。在资源有限的情况下，**宁愿模型小一点，数据训足一点**，这符合Chinchilla原则[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=,model%20trained%20on%20less%20data)[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。举例来说，与其训练个10B参数但只能喂500亿token，不如训练5B参数用1000亿token，后者效果可能更好而成本更低。

**2\. 数据准备和领域平衡**：尽量利用开源数据集来构建预训练语料。比如英文模型可直接使用 **Pile**（800GB多来源数据）、**RedPajama**（1.2T token模拟LLaMA数据）等[together.ai](https://www.together.ai/blog/redpajama#:~:text=,2%20trillion%20tokens)。这些数据已经过较好清洗，拿来即用能省很多功夫。如果有领域需求，则应收集该领域额外数据（如医学论文等）并与通用数据按比例混合。建议确保**多样性**：包括书籍、百科、对话、网页文章、代码等，以丰富模型知识面。同时要做基本清洗去重，删除明显杂质和重复。对于中文等非空格语言，需做好分句、去除噪声字符工作。**不要忽视数据质量**：许多小团队训练的模型表现不佳往往不是模型结构问题，而是数据混杂垃圾过多。花2周时间清洗数据，收益可能抵得上你多算几十亿步训练。对于7B以下模型，训练数据量以 **百亿 Token 级** 为宜（例如50B～200B），可根据算力调整。按照Chinchilla经验，假设你打算训练6B参数模型，理想数据量在6B×20=120B token左右[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。当然并非硬性，需要看实际可得数据，如果数据不足，可以多跑几遍（2-3个epoch）也是策略，但要小心过拟合高频内容。

**3\. 模型架构选择**：建议尽量**跟随业界已有成熟架构**，不要在复杂模型设计上过多纠结。对于大多数应用，**Transformer Decoder架构**是最稳妥选择，方便做对话生成等任务。可以直接参考开源实现如GPT-2、GPT-NeoX或LLaMA的配置。决定层数和隐藏维度时，可参照类似规模的知名模型：如想训练7B模型，可借鉴LLaMA-7B（32层、每层隐维4096，16头）配置，这些参数是有依据调好的。**嵌入维度**通常等于隐藏维度，**FFN维度**4倍或略减小。**位置编码**方面，强烈推荐使用**RoPE**或**ALiBi**等相对位置方案，以便以后扩展长上下文[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/667864459#:~:text=%E6%97%8B%E8%BD%AC%E4%BD%8D%E7%BD%AE%E7%BC%96%E7%A0%81RoPE%20,)。很多开源库（Transformers等）都已支持RoPE，只需几行代码调用。**归一化**建议用Pre-LayerNorm或RMSNorm，确保深层稳定[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=The%20network%20is%20based%20on,in%20different%20models%20are%20leveraged)。**激活函数**可用经典的GELU或SiLU，如果想更进一步可尝试SwiGLU并调低FFN放大倍数来节约参数[medium.com](https://medium.com/dair-ai/papers-explained-55-llama-c4f302809d6b#:~:text=normalized%20,normalizing%20the%20output)。这些改动在开源实现中基本都有例子。**分词器**方面，英文模型直接用开源GPT-2的BPE或EleutherAI GPT-NeoX的词表都行（无需重新训练分词器）；多语言模型可以用XLM-R或mBERT的词表。如果要训中文，可考虑结合字和BPE的方案（保持中文字符自身作为基本单元）。总之，在架构上**尽量复用社区已有的方案**能减少风险——比如索性用HuggingFace的`GPT2LMHeadModel`类定义模型，改改层数宽度，就能省却自己实现Transformer可能踩的坑。

**4\. 基础设施与并行**：需要准备足够的GPU算力。以7B模型为例，全精度参数约14GB，FP16约7GB。训练200B tokens若batch总长为1M tokens（假设使用128 GPU每卡8192 tokens），按每token前向反向2048浮点操作估计，共需约4.1e20 FLOPs。即使有128块A100（312 TFLOPs每卡），也需要约4.1e20/(128\*3.12e14) ≈ 8.3e3秒 ≈ 2.3小时？这显然不现实，因为实际每卡利用率不到100%，且我们忽略了很多常数。实际经验，训练7B模型数百亿token通常需要几星期到数月，具体取决于GPU数和优化程度。因此，一定要用**分布式并行**：单机8卡显然不够。可以考虑云上租用多机GPU实例，如4机×8卡共32 GPU，或者更多。使用DeepSpeed或Horovod之类框架简化多机并行实现。**首先**尝试使用Data Parallel（DDP）+ **ZeRO**。DeepSpeed的ZeRO-Offload甚至允许边训练边把部分数据放CPU，如果GPU内存紧张。但更推荐用PyTorch FSDP，它很适合7B级模型，让多机每卡只存局部参数[pytorch.org](https://pytorch.org/blog/introducing-pytorch-fully-sharded-data-parallel-api/#:~:text=How%20FSDP%20Works)。调试FSDP需要一些经验，但社区有许多教程脚本可借鉴。如果通信良好，还可考虑Megatron-LM的张量并行，将Attention和FFN在两卡上并行计算，能加速但实现稍复杂。在起步阶段，**简化目标**：能让模型跑通并收敛即可，不必强求把每滴算力榨干。所以32卡以内规模，用纯数据并行 + ZeRO即可胜任7B模型训练（就是慢些）。等验证有效后，再投入更多资源进行优化和全量训练。

**5\. 优化和训练超参**：使用前面章节建议的**AdamW优化器**。一个经验设置：$\\beta\_1=0.9,\\ \\beta\_2=0.95,\\ \\text{eps}=1e-8$，Weight Decay设0.1或0.01。学习率可按线性随全局批大小缩放：如总batch 0.5M tokens，学习率1e-4左右较常见。**Warmup**前1%-2%训练步骤，将学习率从0线性增至最大。然后采用**余弦退火**将学习率降至末期的10%水平。建议训练过程中多关注验证困惑度曲线，根据其走势微调学习率策略。**Mixed Precision**必须开启（O2级别混合精度或直接用bfloat16）。**梯度裁剪**在7B模型上设阈值1.0通常OK。**有效批量**越大越稳健，如资源允许尽量累计较大batch。如果发现损失曲线抖动，可增大batch或减小学习率。**训练时长**可以先跑一个小模型确定大致Epoch数：比如先训练1.3亿参数模型1个epoch看验证loss降幅，再推测7B需要几个epoch达到类似困惑度水平。一般几乎不需要多epoch，因为数据超多，多过1遍收益递减明显。不妨以困惑度降不动为准停止，而非固定epoch。

**6\. 中期评估与问题诊断**：在漫长训练中，建议每隔一定步数保存checkpoint，并对模型做简要评估（如验证困惑度，甚至几个零样本任务）。如果发现损失不降或发散，要及时**回滚**最近正常的checkpoint，调低学习率再试。常见问题及对策：训练初期loss爆Nan——多半混合精度下某步梯度太大导致溢出，可降低Loss Scale或更积极裁剪梯度。训练中后期loss突然大幅升高——可能学习率过高或数据分布突变（检查是否某些数据块格式异常），可缩学习率观察。GPU显存不足——考虑降低batch或层并行、启用ZeRO Stage 2/3。通信瓶颈——确保网络带宽，必要时减少并行度或使用梯度压缩。通过持续监控日志和评估指标，可以在第一时间发现异常并修正，从而避免浪费大量算力在坏配置上。

**7\. 微调与应用衔接**：预训练完成后，通常需要一个**下游微调**来让模型执行具体任务（如对话、分类等）。因此在预训练最后，可以直接准备好一些微调数据，用保存的最终模型权重跑下一阶段SFT。这里推荐实践者采用流行的**LoRA**或**QLoRA**等参数高效微调技术，以节省显存和算力。在对话场景下，可利用开源指令数据集（如Alpaca、OIG等）对模型进行指导微调，使其具备聊天能力。若有RLHF需求，则可先训练一个奖励模型然后PPO微调。需要注意，预训练模型对不恰当内容毫无约束，微调需特别考虑**安全和价值观**对齐，必要时过滤或惩罚某些输出倾向。这些属于部署前的“后训练”步骤，不在预训练阶段深入展开。但预训练时可以有意识地**降低有害内容占比**（通过过滤数据），这会减轻后续对齐难度。

**8\. 法务与合规**：构建自主模型也需考虑数据和模型的法律风险。应确保预训练语料来源合法（如公开的维基、开源协议文本、公共领域书籍等）。避免使用明显受版权保护且未授权的数据，或者对这些部分做模糊处理以无法还原。如果模型可能输出受版权保护的段落，要有过滤措施。同样要尊重用户隐私，训练数据中如含个人敏感信息需剔除。国内开发者需遵循相关监管规定，确保模型输出不违反伦理和政策要求。**在落地前做好评估、过滤和免责声明**，以免发布后出现法律纠纷。

概括来说，中小规模团队训练LLM应采取“**拿来主义+针对优化**”的思路：充分利用现有开源成果（数据、代码、模型配置），避免重复造轮子，同时根据自身需求做重点调整（比如加入特定领域数据，或者微调模型结构以减少参数）。切记控制野心，从易到难逐步验证：可以先训练个几千万参数的小模型跑通流程，再按比例放大到目标规模，以免大型号一上来遇到问题难以定位。

通过以上路径，一个有经验的10人团队，借助几十张GPU和几个月时间，是有可能训练出性能接近ChatGPT早期版本的对话模型的（例如业界一些7B开源对话模型已能在许多问答上媲美GPT-3.5）。当然，仍需正视：训练LLM需要**持续投入**，后续优化、维护也是挑战。但一旦掌握方法，自研模型将在数据掌控、定制灵活性上为团队带来独特价值。

## 法务、安全与合规考量

在大模型从研发到部署的生命周期中，**法律合规**和**安全伦理**问题不容忽视。这些考量既涉及预训练阶段的数据处理，也贯穿模型上线后的使用监管。下面分别讨论预训练数据法律风险、模型输出安全，以及上线前后的合规措施。

**1\. 数据版权与合法使用**：预训练往往收集互联网海量文本，但其中很多内容可能受版权保护。使用受版权文本训练AI模型在法律上是否算侵权，目前各国法规和判例尚不统一[mccarter.com](https://www.mccarter.com/insights/court-sets-new-limits-on-use-of-copyrighted-materials-to-train-ai-models/#:~:text=,at%20least%20in%20some)[arl.org](https://www.arl.org/blog/training-generative-ai-models-on-copyrighted-works-is-fair-use/#:~:text=Training%20Generative%20AI%20Models%20on,applying%20the%20US%20Copyright)。在美国，近期有法院倾向认为使用完整作品训练可能属于合理使用的一种（transformative use），但尚无最高法院定论[mccarter.com](https://www.mccarter.com/insights/court-sets-new-limits-on-use-of-copyrighted-materials-to-train-ai-models/#:~:text=Court%20Sets%20New%20Limits%20on,at%20least%20in%20some)。欧盟等地法律更严格，未经许可抓取数据可能违法。为降低风险，**数据治理**时应尽量使用**开放版权**或**公共领域**的内容[edtechfactotum.com](https://edtechfactotum.com/a-llm-training-dataset-made-up-of-only-open-or-public-domain-content/#:~:text=A%20LLM%20training%20dataset%20made,Common%20Corpus)。例如Wikipedia、政府出版物、开源项目代码（遵守其许可证）等。对于不可避免含有版权的部分，应避免模型过度记忆整段内容，以免日后输出一字不差地复现。技术上可以通过**训练数据去重**和**惩罚高频片段**来减小模型背诵原文的倾向[arxiv.org](https://arxiv.org/pdf/2306.01116#:~:text=massive%20web%20crawls%20which%20can,pipelines%20and%20reduce%20the%20need)。另外，保留好数据来源记录以便应对版权质询也很重要。如果模型将来商用，更需要审慎：有的授权协议（如CC-BY-NC）限制商业使用，训练数据中若含这些内容，严格讲模型也不能用于商业。总的来说，**敬畏知识产权**是必要的，获取数据时遵守robots协议、使用API受限内容也可能违反服务条款，所以务必在数据来源选择上多花心思，争取拿到授权或者采用清洗后“无法还原”的方式使用。

**2\. 个人隐私与敏感信息**：互联网语料可能包含大量个人敏感信息，如姓名、电话、住址、邮箱、社交ID等。模型若学习并能输出这些真实信息，将带来**隐私泄露**风险。例如，有研究发现GPT-2会背出训练数据中的某些社保号码。为避免此问题，预训练前应该对数据中可能的**PII（个人可识别信息）**做模糊处理或删除[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=1,giving%20it%20a%20smiley%20face)。比如用正则检测电话、邮箱格式并掩盖，或者干脆过滤掉涉及私人内容的文本段落。OpenAI据报道在GPT-4训练时就剔除了许多含个人数据的片段。对于人名等，完全去除不切实际，但可以限制模型对罕见名字的记忆——一招是对训练目标进行修改，使模型降低生成那些序列的概率。这方面仍属前沿研究。上线后，还应有**提示词过滤**机制，防止用户刻意诱导模型说出隐私数据（如“我的银行账号是多少”这类应禁止回答）。此外，不少国家对使用个人数据训练AI有规定，如GDPR要求知情同意、可删除等，目前LLM很难逐条落实（模型参数不可直接逆推出谁的数据）。为安全起见，最好避免使用涉及真人用户的私密对话或资料进行预训练，除非已做匿名化处理并征得许可。

**3\. 有害内容与偏见**：预训练数据中的不良内容会导致模型产生**有害言论**或偏见。模型未对齐前，会重复网上的**仇恨言论**、**色情暴力**细节、**极端政治宣传**等，这是重大安全风险[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=1,giving%20it%20a%20smiley%20face)。因此，预训练数据治理要严格**过滤**上述内容类别（见前文数据清洗部分）。但即便过滤，模型仍可能学到潜藏的偏见（比如性别和种族刻板印象），因为很多语料中隐含偏见。完全根除很困难，只能在后续微调中通过**对齐**和**安全微调**来纠正。所以在预训练完成后，一般会针对安全性再训练模型，比如OpenAI对InstructGPT进行“拒绝有害请求”的微调，Anthropic则引入“HHH准则”（有用、诚实、无害）过滤输出[huggingface.co](https://huggingface.co/blog/zh/rlhf#:~:text=Feedback)。开发者上线前应准备一套**内容审核**策略，包括人工标注和模型判别相结合，拦截模型输出中的不当内容。理想情况下，应该训练一个**安全过滤模型**，作为最终输出的把关人（OpenAI就使用Moderation模型在输出端过滤）。如果资源不足，也应集成关键词过滤、正则模式匹配等基础手段。

**4\. 模型使用政策**：在模型开放给用户使用时，须制定明确的**使用条款和政策**。例如OpenAI要求不得将ChatGPT用于违法用途、不得尝试提取私人数据等。作为模型提供方，需要在法律上做出适当的**免责声明**：模型生成内容不代表官方立场，不保证正确性，不可用于医疗法律建议等。这些声明有助于减轻模型输出错误造成的责任。不过不同司法区域对AI输出责任认定尚无共识，开发者仍需尽最大努力**降低危害**。最好在系统层面添加使用限制，比如对每次对话长度、敏感话题频率设限，检测到可能有法律风险的问题就拒绝回答。同时监控用户交互日志，若发现滥用模型去生成违规内容，应予以警告或封禁。简而言之，**在技术上和法律上都设立防线**，以免模型被用来大规模生成谣言、诈骗信息或侵权材料。

**5\. 合规认证与审查**：不同国家/地区开始出台针对生成式AI的监管要求。例如欧盟AI法案草案将大模型归为高风险系统，要满足数据治理、技术文档、透明度等义务。中国也发布了《生成式人工智能服务管理办法》，要求提供者对训练数据合法性负责，并对输出进行标识和审核。作为模型开发者，需要**跟进当地法规**，提前准备合规措施。可能需要留存训练数据来源清单、模型版本更新记录等，以备监管审查。上线前可能需要送交权威部门测评（如网络安全、无害化评估等）。这些流程要预留时间。**模型水印**技术可以在输出中嵌入某种统计特征，方便识别内容是否AI生成，这也是合规方向。OpenAI等都在研究将水印作为大模型输出标识的手段。如果政策要求，模型提供方应考虑实现类似功能，至少在某些特定应用场景加水印，便于后续追责和控制。

**6\. 开源发布的法律责任**：如果选择开源模型权重或供公众API服务，要意识到**责任转移**问题。开源后别人用模型干坏事，原作者通常不承担直接法律责任，但可能有声誉风险。因此很多组织在开源模型时附带**责任使用许可**（Responsible Use License），规定不得用于危害社会、歧视等。比如LLaMA-2要求商用用户遵守一定许可。虽然这些条款在法律上约束力有限，但表达了作者立场。另外开源时通常附上**模型卡（Model Card）**，详细说明训练数据、可能的问题和用途限制，尽到告知义务。作为开发者，应该尽可能在文档中提及模型的已知局限和风险，这既是专业态度，也能在事后免责有所依据。

总的来说，**大模型开发者需要从一开始就将安全和合规纳入流程**，而非等模型做好了再补救。从数据选择、训练策略到成品输出，都要考虑如何减少对现实世界可能的不良影响。可以组建一个跨职能的小组，包括工程师、法律顾问、伦理研究人员，共同制定AI使用准则并审核模型行为。例如Anthropic有“宪法AI”思路，在RLHF中融入一套人权和价值观原则。国内企业如百度、阿里在大模型上线前也都经过严格安全评估，多轮调整。

最后，**用户教育**也是合规的重要环节。向用户明确提示模型有可能出错，不能完全信赖；引导用户举报有害输出。这样通过厂商和用户两端的努力，才能形成模型安全使用的生态闭环。

**结语**：法律和伦理问题贯穿LLM生命周期，是技术不可分割的一部分。一个成功的大模型，不仅体现在语言能力上，也体现在安全可控上。在追求模型性能的同时，开发者有责任确保模型遵循法律法规和道德规范，为用户带来正面价值而非风险。只有这样，大模型技术才能被公众和监管所接受，取得长远的成功。

## 术语表

| **术语** | **解释** |
| --- | --- |
| 大语言模型（LLM） | 参数规模通常以亿计或以上的语言模型，基于大量文本语料训练，能够执行文本生成、理解等多种语言任务。 |
| 预训练（Pre-training） | 利用海量未标注文本数据对模型进行自监督训练的阶段，让模型学习通用语言知识，为后续微调打基础。 |
| 微调（Fine-tuning） | 在预训练模型的基础上，使用较小的特定任务数据进一步训练模型，使其适应具体应用。包括有监督微调（SFT）和强化学习微调（RLHF）等。 |
| SFT（有监督微调） | Supervised Fine-Tuning，通常指用人工标注的指令-响应数据对预训练模型进行监督训练，使其更好遵循指令要求。 |
| RLHF（人类反馈强化学习） | Reinforcement Learning from Human Feedback，通过人类偏好（如人工反馈的奖励模型）来进一步调整模型参数，使模型输出符合人类期望和价值观。 |
| 自回归模型（Causal LM） | 以预测下一个词为训练目标的语言模型，按从左到右顺序生成文本。GPT系列即属此类。 |
| 掩码语言模型（Masked LM） | 以预测被掩盖词为目标的双向语言模型，如BERT。通过随机mask部分词让模型填空来训练。 |
| 困惑度（Perplexity） | 衡量语言模型对测试数据预测不确定性的指标，数值等于模型预测下一个词时平均可能的选项数，越小表示模型预测越准确[blog.csdn.net](https://blog.csdn.net/qq_36485259/article/details/136617494#:~:text=%E6%98%AF%E8%87%AA%E7%84%B6%E8%AF%AD%E8%A8%80%E5%A4%84%E7%90%86%EF%BC%88NLP%EF%BC%89%E4%B8%AD%E5%B8%B8%E7%94%A8%E7%9A%84%E4%B8%80%E7%A7%8D%E8%AF%84%E4%BC%B0%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E7%9A%84%E6%8C%87%E6%A0%87%E3%80%82%E5%AE%83%E8%A1%A1%E9%87%8F%E7%9A%84%E6%98%AF%E6%A8%A1%E5%9E%8B%E5%AF%B9%E6%B5%8B%E8%AF%95%E6%95%B0%E6%8D%AE%E7%9A%84%E9%A2%84%E6%B5%8B%E8%83%BD%E5%8A%9B%EF%BC%8C%E5%8D%B3%E6%A8%A1%E5%9E%8B%E5%AF%B9%E6%B5%8B%E8%AF%95%E9%9B%86%E4%B8%AD%E5%8D%95%E8%AF%8D%E5%BA%8F%E5%88%97%E5%87%BA%E7%8E%B0%E6%A6%82%E7%8E%87%E7%9A%84%E9%A2%84%E6%B5%8B%E5%87%86%E7%A1%AE%E5%BA%A6%E3%80%82%E5%9B%B0%E6%83%91%E5%BA%A6%E8%B6%8A%E4%BD%8E%EF%BC%8C%E8%A1%A8%E7%A4%BA%E6%A8%A1%E5%9E%8B%E5%AF%B9%20%E6%95%B0%E6%8D%AE%E7%9A%84%E9%A2%84%E6%B5%8B%E8%B6%8A%E5%87%86%E7%A1%AE%E3%80%82)。 |
| Transformer | 目前主流的神经网络架构，基于自注意力机制。由编码器和解码器两部分构成，但LLM多用解码器结构。 |
| 解码器（Decoder） | Transformer解码器，对自回归语言建模来说，每层包括带mask的自注意力和前馈网络，用于根据已生成内容生成下文。 |
| 编码器-解码器架构 | Transformer的一种结构，编码器读取输入序列，解码器生成输出序列并可关注编码器输出。多用于翻译等序列到序列任务。 |
| BPE 分词 | Byte Pair Encoding，将文本字符根据频率迭代合并来构造子词词汇表的分词算法[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=BPE%20%E6%98%AF%E4%B8%80%E7%A7%8D%E5%9F%BA%E4%BA%8E%E9%A2%91%E7%8E%87%E7%9A%84%E8%B4%AA%E5%BF%83%E5%90%88%E5%B9%B6%E7%AE%97%E6%B3%95%E3%80%82)。 |
| WordPiece | 基于语言模型概率增益挑选合并操作的分词算法，BERT所用[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。 |
| Unigram 分词 | 基于概率模型的分词算法，通过假设大词表并迭代剪枝得到最佳子词集[blog.csdn.net](https://blog.csdn.net/guoguozgw/article/details/148311714#:~:text=)。SentencePiece提供实现。 |
| AdamW 优化器 | 带权重衰减修正的Adam优化器，几乎是大模型训练的标准优化算法[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。 |
| 混合精度 | Mixed Precision，将部分计算用FP16或bfloat16进行以加速和节省内存的训练技术。 |
| 学习率调度 | Learning rate schedule，随训练进程调整学习率的策略，如线性warmup+余弦退火等，用于稳定和加速收敛[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=,both%3F%20Compute%20blows%20up%20quickly)。 |
| 梯度累积 | Gradient Accumulation，在更新前累积多次小批次梯度，相当于增大有效批量以稳定训练的技术。 |
| 梯度裁剪 | Gradient Clipping，当梯度过大时进行裁剪（如按阈值缩放），防止训练发散的一种正则手段。 |
| 数据并行 | Data Parallelism，每个GPU持有模型副本，处理不同数据子集，期间同步梯度，实现扩展训练的并行方式[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Data%20parallelism%20evenly%20distributes%20data,GPU%20are%20synchronized%20and%20combined)。 |
| 模型并行 | Model Parallelism，将模型切分到多GPU上执行的并行方式，典型包括张量并行和流水线并行等[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Model%20parallelism%20distributes%20a%20model,layer%20to%20the%20first%20layer)[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Pipeline%20parallelism)。 |
| 张量并行 | Tensor Parallelism，将单个层的矩阵计算拆分到多GPU并行完成[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Tensor%20parallelism%20distributes%20large%20tensor,to%20reconstruct%20the%20final%20result)。 |
| 流水线并行 | Pipeline Parallelism，将模型层划分为多阶段，各GPU依序处理不同阶段，实现批处理流水线式的并行[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=Pipeline%20parallelism)。 |
| ZeRO 技术 | Zero Redundancy Optimizer，由DeepSpeed提出的分摊优化器状态和梯度的并行方法，Stage 3可将模型各分片存不同GPU以降低内存占用[huggingface.co](https://huggingface.co/docs/transformers/en/perf_train_gpu_many#:~:text=reduce%20memory%20usage,three%20ZeRO%20stages)。 |
| FSDP | Fully Sharded Data Parallel，PyTorch实现的完全碎片化数据并行，相当于ZeRO Stage 3，将模型参数/梯度/状态切分到各GPU[pytorch.org](https://pytorch.org/blog/introducing-pytorch-fully-sharded-data-parallel-api/#:~:text=How%20FSDP%20Works)。 |
| GSPMD | General and Scalable Parallelization for ML，由Google提出的自动并行编译框架，通过对张量标注切分策略，XLA编译器自动生成混合并行执行计划[research.google](https://research.google/blog/general-and-scalable-parallelization-for-neural-networks/#:~:text=simply%20needs%20to%20add%20a,and%20enables%20easy%20porting%20of)。 |
| RoPE | Rotary Position Embedding，旋转位置编码，一种将绝对位置转化为相对角度信息的编码方式，允许模型泛化到更长序列[hub.baai.ac.cn](https://hub.baai.ac.cn/view/29979#:~:text=,CV%E5%90%84%E5%A4%A7%E6%96%B9%E5%90%91%E4%B8%93%E6%A0%8F%E4%B8%8E%E5%90%84%E4%B8%AA%E9%83%A8%E7%BD%B2%E6%A1%86%E6%9E%B6%E6%9C%80%E5%85%A8%E6%95%99%E7%A8%8B%E6%95%B4%E7%90%86)[hub.baai.ac.cn](https://hub.baai.ac.cn/view/29979#:~:text=%E5%A4%87%E6%B3%A8%EF%BC%9A%E4%BB%80%E4%B9%88%E6%98%AF%E5%A4%A7%E6%A8%A1%E5%9E%8B%E5%A4%96%E6%8E%A8%E6%80%A7%EF%BC%9F)。 |
| FlashAttention | 闪电注意力，一种 IO优化的准确注意力算法，实现了更高的显存利用和计算速度，可大幅加速注意力计算[github.com](https://github.com/Dao-AILab/flash-attention#:~:text=We%20have%20released%20the%20full,don%27t%20need%20any%20activation%20checkpointing)[hopsworks.ai](https://www.hopsworks.ai/dictionary/flash-attention#:~:text=By%20improving%20the%20efficiency%20of,bandwidth%20memory%20and%20processing%20units)。 |
| Chinchilla 定律 | DeepMind提出的计算最优法则：在给定计算量下，模型参数和训练token应同时按约1:20比例增大才最优[medium.com](https://medium.com/codetodeploy/scaling-laws-in-llms-why-bigger-isnt-always-better-the-chinchilla-lesson-960c67755dbd#:~:text=Example%3A%20If%20you%20have%20compute,3)。即模型缩小+数据增多 often 优于 模型变大+数据不足。 |
| Few-Shot 学习 | 少样本学习，大模型无需梯度微调，只通过提供1到几条示例，就能在新任务上给出不错结果的能力。GPT-3展示了强大的few-shot能力。 |
| Emergent Ability | 涌现能力，模型规模达到某阈值后突然出现的质变能力，小模型完全不具备，如算术推理、多步骤推理等。 |
| PII | Personally Identifiable Information，个人可识别信息，如姓名、身份证号、电话等。处理这些数据需注意隐私合规。 |
| 模型水印 | 在模型生成内容中嵌入特定统计特征或标记的方法，用于识别文本是否由模型生成。 |

## 推荐阅读与学习资源

大语言模型预训练涉及众多概念和技巧，下列视频和资料有助于进一步学习：

-   **Andrew Ng 深度学习专项：大型语言模型预训练** – Andrew Ng在DeepLearning.AI的一段课程内容，深入浅出讲解预训练原理（Bilibili中字版：【2†】）。
    
-   **Andrej Karpathy 2023 最新LLM讲座** – 特斯拉前AI主管Karpathy的公开课视频《Let's build GPT》，涵盖Transformer、预训练、微调等（YouTube英文：【5†】| B站中字剪辑：【7†】）。
    
-   **Hugging Face 官方博客系列** – *Illustrating RLHF* 等博文详细阐述预训练到RLHF的流程，并有中文翻译[huggingface.co](https://huggingface.co/blog/zh/rlhf#:~:text=OpenAI%20%E6%8E%A8%E5%87%BA%E7%9A%84%20ChatGPT%20%E5%AF%B9%E8%AF%9D%E6%A8%A1%E5%9E%8B%E6%8E%80%E8%B5%B7%E4%BA%86%E6%96%B0%E7%9A%84%20AI,%EF%BC%8C%E5%8D%B3%E4%BB%A5%E5%BC%BA%E5%8C%96%E5%AD%A6%E4%B9%A0%E6%96%B9%E5%BC%8F%E4%BE%9D%E6%8D%AE%E4%BA%BA%E7%B1%BB%E5%8F%8D%E9%A6%88%E4%BC%98%E5%8C%96%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E3%80%82)[huggingface.co](https://huggingface.co/blog/zh/rlhf#:~:text=RLHF%20%E6%8A%80%E6%9C%AF%E5%88%86%E8%A7%A3)。适合了解整个大模型训练三部曲。
    
-   **深度拆解GPT-3架构（英语）** – 博客 *The GPT-3 Architecture, on a Napkin*[dugas.ch](https://dugas.ch/artificial_curiosity/GPT_architecture.html#:~:text=The%20GPT,3%20architecture)用通俗比喻和示意图解释GPT-3模型结构，对理解大模型组件很有帮助。
    
-   **《动手学大模型》教程** – Datawhale开源的中文教材，从零实践LLaMA2，包括预训练、微调全流程（GitHub项目：[madacode.com](https://madacode.com/2023/04/26/%E8%BF%88%E5%90%91%E5%A4%9A%E6%A8%A1%E6%80%81%E5%A4%A7%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B-%E8%A7%86%E9%A2%91%E8%AF%AD%E8%A8%80%E9%A2%84%E8%AE%AD%E7%BB%83%E7%9A%84%E5%85%AC%E5%BC%80%E6%95%B0%E6%8D%AE/#:~:text=%E8%BF%88%E5%90%91%E5%A4%9A%E6%A8%A1%E6%80%81%E5%A4%A7%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E2%80%93%E8%A7%86%E9%A2%91%E8%AF%AD%E8%A8%80%E9%A2%84%E8%AE%AD%E7%BB%83%E7%9A%84%E5%85%AC%E5%BC%80%E6%95%B0%E6%8D%AE%E9%9B%86%20,%E5%9B%A0%E6%AD%A4%EF%BC%8CWebVid%E6%95%B0%E6%8D%AE%E9%9B%86%E6%9B%B4%E9%80%82%E5%90%88%E4%BA%8E%E8%A7%86%E9%A2%91%E8%AF%AD%E8%A8%80%E7%9A%84%E9%A2%84%E8%AE%AD%E7%BB%83%E4%BB%BB%E5%8A%A1%EF%BC%8C%E4%BB%A5%E5%AD%A6%E4%B9%A0%E5%BC%80%E6%94%BE%E9%A2%86%E5%9F%9F%E7%9A%84%E8%B7%A8%E6%A8%A1%E5%BC%8F%E8%A1%A8%E5%BE%81%E3%80%82)）。
    
-   **OpenAI GPT-4 技术报告** – 尽管细节有限，但附录讨论了一些数据过滤、安全措施，提供了工业界在预训练数据上的考量视角（OpenAI, 2023）。
    
-   **Stanford CS324 课程 (2022)** – 专门讨论大模型（基础模型）的大学课程，录像和课件公开，涵盖预训练方法、社会影响等（课程网站可搜索）。
    
-   **《TorchScale: Transformers for Scale》论文** – Meta AI 2022年发布的论文，整理了很多大模型训练trick（如DeepNorm，FlashAttention前身等），帮助理解大规模训练稳定性的改进方法。
    
-   **BERT 和 GPT 原始论文** – 《Attention is All You Need》(Transformer架构), 《BERT: Pre-training of Deep Bidirectional Transformers》, 《Language Models are Unsupervised Multitask Learners》(GPT-3技术报告) 等原始论文，可以深入了解预训练目标和效果。
    

读者可根据自身背景和兴趣选择以上资源。对于产品经理，建议优先看浅显的视频和博客获取直观认识；对于工程师，则可深入论文和代码实践教程以掌握实现细节。预训练技术日新月异，保持关注最新研究（如学术会议论文、顶尖实验室博客）也很重要。

---

通过本报告的系统讲解，我们认识到大语言模型的预训练绝非“烧钱堆数据”这么简单。其中有大量精妙的方法论和工程实践：从训练目标的选择、语料的精心打磨，到模型结构的一步步改良，以及优化策略和并行技术的融合创新。这些共同造就了如今功能强大的LLM。在未来，我们可以预见预训练将在更多模态（如图像、音频）和知识融合方面继续拓展。而无论技术如何演进，**掌握预训练的核心原理**将帮助开发者举一反三，不断训练出更高效、更安全、更符合人类期望的AI模型。希望本报告为读者打下坚实基础，激发出新的实践灵感，在大模型时代创造出属于自己的杰出成果。


