You: 

```

### 深入浅出：SFT（监督微调）快速导读

基于原文（王宸）内容，按主题整理为便于非 AI 岗位技术人员（开发、产品等）阅读的 Markdown 摘要与要点。

---

## 1. 为什么会有 SFT？
- 大模型训练通常包含三阶段：预训练 → SFT（监督微调）→ RLHF（人类反馈强化学习）。
- 预训练：获得通用语言能力。  
- SFT：用监督数据提升在特定领域/任务上的表现。  
- RLHF：对齐人类偏好、加强安全与价值观约束。

---

## 2. SFT 与预训练的区别
- 目标：预训练学“通用能力”，SFT学“特定能力/行为”。  
- 数据：预训练用海量无标注语料；SFT用有标注的指令-回应对。  
- 学习范式：预训练自监督、SFT有监督（按 token 计算 loss）。

---

## 3. SFT 与 RLHF 的区别
- 目的不同：SFT提升任务能力；RLHF对齐人类偏好并处理有害/敏感内容。  
- 技术不同：SFT=监督学习（行为克隆）；RLHF=强化学习（奖励模型、PPO 等）。  
- 反馈：SFT主要正向示范；RLHF可提供排序/负反馈，纠正错误倾向。  
- 优化粒度：SFT按 token 优化；RLHF可基于完整输出序列优化。

---

## 4. SFT 与 RAG 的区别
- SFT：通过微调把知识内化到模型参数里。  
- RAG（检索增强生成）：在推理时实时检索外部知识并拼接到提示中，知识可动态更新。  
- 权衡：SFT延迟低、风格连贯但知识静态且可能遗忘；RAG易更新、减少幻觉但推理更复杂、有检索开销。两者可结合。

---

## 5. SFT 与继续预训练（Continue Pre‑train）
- Continue Pre‑train：在原预训练之后，用大量未标注、聚焦领域的语料继续无监督训练，通常在 SFT 之前。  
- 用途：当基础模型对目标领域几乎没接触时（极端差异），先做增量预训练再 SFT。  
- 数据量：增量预训练 >> SFT，通常成本很高，99% 情况不必。

---

## 6. SFT 与 In‑Context Learning（ICL）
- ICL：在推理时通过示例（prompt）让模型临时“学习”任务，不改变参数。  
- SFT：在训练时更新参数，使模型永久掌握任务。  
- 适用：ICL适合快速试验或零样本场景；SFT适合长期稳定部署。

---

## 7. SFT 与 LoRA / PEFT 的关系
- 传统 SFT 多指全参数微调（Full FT）。  
- PEFT（参数高效微调）：只训练少量参数或附加模块，包含 LoRA、Prefix Tuning、Adapter 等。  
- 优劣：全微调上限高但资源消耗大；PEFT 显存/成本小，性能接近但在极致场景可能略逊一筹。

---

## 8. SFT 的分类维度
- 按任务：对话、问答、分类、生成、相似度判断等。  
- 按微调方式：全参数微调、PEFT（LoRA/Adapter/Prefix）、部分层解冻等。

---

## 9. SFT 的前提条件（三要素）
1. 基座模型（base 或 chat；多数情况下推荐 chat 版）。  
2. 微调数据（格式、质量、数量、COT 等设计）。  
3. 微调环境（硬件 GPU、软件框架、工具链，如 DeepSpeed、Accelerate、Transformers、Unsloth、LLaMA‑Factory 等）。

---

## 10. 如何选择基座模型
- 优先考虑 chat 模型（已具备指令遵循能力），除非有特殊需求用 base。  
- 模型大小根据任务与资源权衡：单一窄任务可选小模型；复杂推理/通用场景选大模型。  
- 注意模型许可与量化版本的适配（量化模型通常不做全参数微调）。

---

## 11. SFT 训练数据集如何构建
- 常见格式：Alpaca（单轮指令 JSON）、ShareGPT（多轮对话）。  
- 包含 COT（思维链）可提升推理能力，但会增加输出长度。  
- 数据来源：人工标注、模型辅助生成（+人工审核）、检索增强生成。  
- 数据质量关键：多样性、一致性、无矛盾、格式统一、Instructions 明确。95% 时间常用于数据收集与清洗。

---

## 12. 需要多少数据？
- 视任务而定，常见范围 2k–100k。实践中“一万条优质样本”常被证明能带来显著效果（LIMA、InstructGPT 等案例）。

---

## 13. 如何评估微调数据质量？
- 指令多样性、答案准确性、一致性、噪声率、任务覆盖面与难度分布。  
- 自动+人工复核相结合，抽样审核，避免相互矛盾示范。

---

## 14. 硬件与资源要求（要点）
- 显存占用受模型参数、优化器状态、激活值影响，经验约为参数量的若干倍（需具体估算）。  
- 老 GPU（如 V100）对一些新算子/精度（BF16、FlashAttention）支持有限。  
- PEFT/LoRA 可显著降低显存需求；量化模型（GPTQ）微调需谨慎，不建议全参数微调。

---

## 15. SFT 训练过程常见现象
- 训练 loss 通常下降；验证 loss 在某点后可能回升（过拟合）。  
- 大模型在第 1~2 个 epoch 即可学到大量训练集内容，过拟合风险高，常只跑 1–3 个 epoch。  
- 若多次训练仍学不会某些 case，可能是模型能力/容量限制。

---

## 16. 超参数与调参要点
- 学习率：一般取预训练 lr 的 ~0.1 倍，小模型可用更大 lr，大模型需更小 lr；使用 warmup + 衰减。  
- Epoch：1–3（与数据量成反比）。  
- Batch：依显存设定，可用梯度累积（16/32/64 等）。  
- 正则化、weight decay、dropout、梯度裁剪等可用于缓解过拟合。  
- 逐次只改少量超参，先用小试验验证趋势。

---

## 17. 如何评价 SFT 后模型效果
- 主观评估：功能达成度、响应质量、风格一致性（人工打分/盲测）。  
- 客观评估：训练/验证 loss、任务专用指标（Accuracy、ROUGE、BLEU 等）、基准测试（MMLU、TruthfulQA 等）。  
- 灰度上线 + 线上监控（用户反馈、错误案例）非常重要。

---

## 18. SFT 可能带来的问题与缓解
- 通用能力下降（遗忘）：通过数据混合（加入通用样本）、更小 lr 或 PEFT 缓解。  
- 过拟合与幻觉：严格审核数据、使用 PEFT、加入拒答示例、结合 RAG 减少无凭证编造。  
- 风格单一或创造力下降：在训练数据中保留风格多样性或在使用时通过 prompt 控制。  
- 数据偏差：多元化采样与审核。

---

## 19. 推理速度与 token 成本估算
- 延迟近似：Time ≈ b + k × x  
    - b：首 token 时间（与 prompt 长度相关）  
    - k：每 token 时间（与模型大小/硬件相关）  
    - x：生成 token 数量  
- 控制策略：缩短 prompt、限制输出长度、避免冗长 COT（若对延迟敏感）。

---

## 20. 什么是 SFT Packing？
- 将多个短样本拼接为一个长序列以减少 padding 浪费，提高 GPU 利用率。  
- 优点：训练效率提升；缺点：可能影响短样本拟合、多轮对话逻辑、样本独立性。是否使用需权衡数据类型与目标。

---

## 21. 一句话概括 SFT 原理
- 预训练与 SFT 都是 next‑token 预测：预训练是自监督学“能写”，SFT是用人工示范学“怎么写”。SFT本质是把希望的行为“刻”到模型参数里（有时学到的是记忆而非泛化）。

---

## 22. 代码/实践要点（速览）
- Tokenizer 与模型必须匹配；若扩词表需 resize embeddings。  
- 开启“思考模式”须在 tokenizer/template 中启用并在训练数据中包含相应格式。  
- 推理示例（简化）：

	```py
	from transformers import AutoTokenizer, AutoModelForCausalLM
	model_path = "./Mistral-7B-Instruct"
	tokenizer = AutoTokenizer.from_pretrained(model_path, trust_remote_code=True)
	model = AutoModelForCausalLM.from_pretrained(model_path, torch_dtype="auto", device_map="auto")
	input_ids = tokenizer("Hello, world!", return_tensors="pt").input_ids.to(model.device)
	outputs = model.generate(input_ids, max_length=50)
	print(tokenizer.decode(outputs[0], skip_special_tokens=True))
	```

- 训练常用方式：Hugging Face `Trainer` 或 TRL 的 `SFTTrainer`。注意设置 `eos_token`、`gradient_accumulation_steps`、`fp16/bf16` 等参数。

---

若需，我可以把上述每个部分扩展为更详细的“非 AI 岗位可读”章节（含图表、示例场景与决策建议），或生成一份 PPT 大纲供汇报使用。

```



ChatGPT: 

为了更深入地调研和分析SFT内容，并向开发者、产品经理等非AI岗位的技术人员通俗易懂地分享重点内容，是否有具体的期望输出形式？例如：

1.  是否需要图表、流程图等可视化帮助理解？
    
2.  希望以什么形式呈现内容？比如总结性文章、PPT结构草稿、技术指南等？
    
3.  是否希望对比不同模型或具体应用案例？
    
4.  是否希望涵盖代码层面操作指南？
    

请告知你的具体需求，这将帮助我更高效地完成调研任务。

You: 

需要图表、流程图等可视化帮助理解；以总结性文章进行呈现；希望对比不同模型或具体应用案例；不希望涵盖代码层面操作指南。 请尽可能广泛和深入调研SFT，使用通俗易懂的语言，体系化的总结输出，配合图表和视频等资料，不少于三万字

ChatGPT: 

明白了。我将深入调研监督微调（SFT）的原理、实践方法、技术演进、与其他技术的对比（如RAG、LoRA、PEFT等），并结合实际案例和模型应用场景，整理成一篇体系化的总结性文章。

文章将以通俗语言讲解面向开发者和产品经理的SFT核心知识，包含图表、流程图和参考视频资源等，重点帮助非AI岗位人员建立对SFT的全面理解。

我会在整理完调研内容后尽快与你分享初稿。

# 深入浅出解读 SFT：大型语言模型的监督微调详解

大型语言模型（LLM）的训练一般包含**预训练**、**SFT（监督微调）**、\*\*RLHF（人类反馈强化学习）\*\*三个阶段[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=Image%3A%203%20phases%20of%20ChatGPT,outperforms%20SFT%20alone)。预训练让模型具备广泛的通用语言能力，SFT通过有监督的数据进一步让模型掌握特定领域或任务，RLHF则使模型的回答更符合人类偏好和价值观，对敏感内容进行约束。本文将围绕 SFT 展开深入研究和分析，用通俗易懂的语言为非 AI 岗位的技术人员（如开发者、产品经理等）系统讲解 SFT 的核心概念、方法和实践要点。

## 什么是 SFT？为什么需要 SFT？

**SFT（Supervised Fine-Tuning）**指在一个已经预训练好的大模型基础上，使用人工标注的高质量**监督数据**进行微调训练，以提升模型在特定任务或领域的能力[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=Supervised%20Fine)[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=Image%3A%20Supervised%20Fine)。预训练模型虽然知识面广，但在回答具体指令时往往**不够精确**或不够贴合人类需求[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=Pre,world%20applications)。SFT 就像给一位经过通识教育的学生进行专业辅导，通过示范正确的问答例子，**教会模型按照我们希望的方式回应**[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=Pretraining%20optimizes%20for%20completion,following%20could%20be%20valid%20completion)[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=How%20to%20do%20that%3F%20We,the%20model%20clones%20this%20behavior)。简单来说，**预训练**让模型“读遍群书”，而**SFT**则手把手“教”模型在某个具体场景下如何回答问题。

在没有 SFT 的情况下，一个纯预训练的模型（例如 GPT-3 基础模型）在面对用户问句时，可能会**续写**出与问句相关的内容，而不一定直接给出答案[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=Pretraining%20optimizes%20for%20completion,following%20could%20be%20valid%20completion)。通过 SFT，我们为模型提供了大量\*\*（提示，回应）**对示例（demonstrations），让模型学会**“遵循指令”**的行为，将预训练模型从单纯的续写优化为**直接回答用户问题\*\*[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=How%20to%20do%20that%3F%20We,the%20model%20clones%20this%20behavior)。例如，预训练模型面对\*\*“如何做披萨？”\*\*这样的提问，可能继续补充上下文或反问，而经过指令微调（SFT）后，它会直接给出制作披萨的步骤[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=Pretraining%20optimizes%20for%20completion,following%20could%20be%20valid%20completion)。

SFT 的重要性在于：**预训练模型的通用能力需要通过微调来桥接实际应用**[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=Pre,world%20applications)。预训练提供了**广度**，SFT 提供**深度**，在特定领域内提升模型的准确性、一致性和专业性[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=%2A%20Domain%20Specialization%3A%C2%A0Makes%20general,support%2C%20legal%20advisories%2C%20and%20financial)。对于企业来说，SFT 可以让通用 LLM 转变为**行业专家**——例如将一个通用模型微调成法律助理模型，喂以成千上万的法律问答范例，使其语言风格和术语都贴合法律场景[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=For%20example%2C%20if%20an%20LLM,specific%20expertise)。

总之，**没有 SFT，大模型就难以胜任特定业务场景**。SFT 使模型**快速适应**新任务，比起让人标注大规模奖励函数数据（RLHF）或让用户自己反复 prompt 调整，SFT 更直接有效，是构建实用对话AI必不可少的一步[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=learning.%20,legal%20advisories%2C%20and%20financial%20reporting)。

## SFT 与预训练的区别

**预训练**和\*\*微调（SFT）\*\*的目标与方式截然不同[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=Supervised%20Fine)：

-   **目标不同**：预训练旨在学习**通用语言能力**，通常在海量网络文本上通过自监督任务（如下一个词预测）训练模型；SFT 的目标则是让模型在**特定任务/领域**上表现更好[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=Supervised%20Fine)。预训练后的模型相当于“通才”，而SFT培养“专才”[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=%2A%20Domain%20Specialization%3A%C2%A0Makes%20general,support%2C%20legal%20advisories%2C%20and%20financial)。
    
-   **数据不同**：预训练使用的多是**无标注的大规模语料**，模型通过预测下一个token来自主学习语言统计模式。而 SFT 使用**人工标注的高质量数据**，数据格式通常是指令和正确回应对，直接告诉模型“遇到这样的指令，理想回应是什么”[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=How%20to%20do%20that%3F%20We,the%20model%20clones%20this%20behavior)。因此 SFT 数据更**小而精**：数量远小于预训练语料，但质量要求高，内容贴近应用场景。
    
-   **训练方式不同**：预训练是**自监督学习**，用上下文预测下文，**反馈粒度**在token级别；SFT 属于**有监督学习**，有明确的输入和期望输出，仍然通过最小化交叉熵损失来调整模型，使模型产出的每个token更接近标注答案[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=%2A%20Training%20data%3A%20high,approximately%2088%2C000%20pairs)。简而言之，预训练让模型\*\*“预测下一个词”**，SFT 则让模型**“模仿范例答案”\*\*[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=How%20to%20do%20that%3F%20We,the%20model%20clones%20this%20behavior)。
    
-   **效果不同**：预训练后模型具备语言理解和生成的基础能力，但直接应用时往往**缺少指令遵循**和**任务专精**能力[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=Pretraining%20optimizes%20for%20completion,following%20could%20be%20valid%20completion)。SFT 让模型能**按照人类指令**办事，比如学会遵循 prompt 格式、在医疗问答中使用专业措辞等。实践证明，一个经SFT微调的小模型（如 InstructGPT 的13亿参数版本）在指令任务上的表现甚至**优于**未微调的大模型（1750亿GPT-3）[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=To%20train%20a%20model%20to,approach%20produces%20much%20superior%20results)[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=finetune%20InstructGPT)。这充分说明了 SFT 的价值：用较少的参数和数据，通过定向微调即可实现**质的飞跃**。
    

总结来说，预训练解决模型\*\*“能不能理解和生成语言”**的问题，SFT解决模型**“愿不愿、会不会按照特定要求生成合适内容”\*\*的问题。预训练造就了一个博闻强记的“通识全才”，SFT 则培养出胜任特定工作的“专才”。

## SFT 与 RLHF 的区别

SFT 和 RLHF 都属于预训练后的**模型微调阶段**，但目的和方法上有明显区别：

-   **训练目标不同**：**SFT**主要是提高模型在**特定任务上的能力**，教模型给出任务期望的正确回答。而**RLHF**（Reinforcement Learning from Human Feedback，人类反馈强化学习）的核心目标是让模型输出更符合**人类偏好和价值观**，特别是在有潜在**有害内容**的话题上对模型进行约束[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=an%20example%20of%20a%20language%3F%E2%80%9D%2C,)[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=Reinforcement%20Learning%20from%20Human%20Feedback,in%20LLMs)。SFT 加强模型在某领域的**表达能力**，RLHF 则引导模型在**价值观对齐**方面表现得更好[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=model%E2%80%99s%20response%20is%20%E2%80%9CJava%E2%80%9D%2C%20the,)。例如，SFT 可能让模型更擅长医学问答，而 RLHF 则确保模型避免给出不道德或有害的建议。经过 RLHF，模型在宗教、政治、伦理等敏感问题上的回答会更加谨慎、符合人类普遍认可的准则。
    
-   **技术范式不同**：**SFT 使用监督学习**——给定输入直接优化输出与示范答案的匹配度（交叉熵损失最小化），属于**行为克隆**（behavior cloning）[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=How%20to%20do%20that%3F%20We,the%20model%20clones%20this%20behavior)；**RLHF 使用强化学习**，核心是引入一个**奖励模型**评价模型输出的好坏，然后通过策略优化（如PPO算法）调整模型策略，使之倾向于产出高分的回答[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=Unlike%20Supervised%20Fine,The%20process%20typically%20involves)[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=3,that%20align%20with%20human%20preferences)。监督学习的性能上限通常受限于教师示范的数据质量（模型至多学到示范者水平），而强化学习可以通过**探索和反馈**有机会**超越训练示范**[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=%3E%20%20%20,supposed%20to%20help%20with%20hallucination)。正如机器学习专家所言：“监督学习的上限是老师水平，而强化学习通过试错有机会超越老师。” 另外，SFT 的优化目标是每个 token 的预测准确性，**每个token的贡献相同**；RLHF 则是基于整个输出序列的质量给奖励，能针对**完整回答**进行优化调整[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=an%20example%20of%20a%20language%3F%E2%80%9D%2C,)。因此 RLHF 可以微调模型的**整体输出风格和符合度**，弥补纯监督学习的不足。
    
-   **反馈信号不同**：SFT 训练时模型只看到**正向示范**，也就是正确答案示例，没有明确告诉模型\*\*“不该怎么答”**[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=an%20example%20of%20a%20language%3F%E2%80%9D%2C,)。模型可能会**错把训练中没见过的不良回答也当作可接受输出\*\*。而 RLHF 引入了**人类偏好反馈**，既有正向也有负向的：人类标注者对模型不同回答进行**排序比较**，从而让模型知道哪些回答**更好**，哪些**更差**[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=%3E%20%20%20,supposed%20to%20help%20with%20hallucination)。通过这种**惩罚机制**，RLHF 能有效修正模型在 SFT 阶段学到的一些错误倾向，让模型**避免不受欢迎的回答**[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=an%20example%20of%20a%20language%3F%E2%80%9D%2C,)。可以说，SFT 给模型“打气”，RLHF 给模型“纠错”。在实际应用中，两者常配合使用：SFT 先把模型\*\*“扶上正轨”**，RLHF 再**“精益求精”\*\*调整模型行为，更贴合人类偏好[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=Image%3A%203%20phases%20of%20ChatGPT,outperforms%20SFT%20alone)[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=The%20idea%3A%20what%20if%20we,RLHF%20consists%20of%20two%20parts)。
    
-   **效果侧重不同**：SFT 增强模型**任务表现**，而 RLHF 增强模型**交互品质**。经过 SFT，模型在特定任务上的准确率和专业度提高，但可能仍存在胡乱回答或价值观偏差的问题。RLHF 则通过人类反馈**显著减少模型不恰当或低质回答**[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=tailored%20for%20different%20applications%2C%20models,generated%20content)[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=1,learning%20demands%20substantial%20computing%20resources)。例如，ChatGPT 和 Anthropic Claude 等模型正是通过 SFT 打好基础，再通过 RLHF 获得更好的**连贯性、礼貌性和安全性**[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=For%20example%2C%20ChatGPT%20and%20Claude,prone%20to%20generating%20harmful%20responses)[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=Reinforcement%20Learning%20from%20Human%20Feedback,preferences%20rather%20than%20static%20datasets)。
    

简单来说，**SFT 让模型“学会做事”，RLHF 让模型“做好人”**。在大模型训练管线中，通常**先 SFT 后 RLHF**[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=Image%3A%203%20phases%20of%20ChatGPT,outperforms%20SFT%20alone)：SFT 产出一个行为还不错的模型，然后 RLHF 再进一步调整模型策略，使其成为一个既能完成任务又让人满意的对话助手。两者相辅相成，共同造就了如今强大的对话模型[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=Image%3A%203%20phases%20of%20ChatGPT,outperforms%20SFT%20alone)。

  
*图：大语言模型训练流程。预训练阶段获得基础模型，经过 SFT 监督微调得到较擅长特定任务的模型，再通过 RLHF 使模型与人类偏好对齐，产出最终的对齐模型。*

## SFT 与 RAG 的区别

\*\*RAG（Retrieval-Augmented Generation，检索增强生成）\*\*是一种利用外部知识库提升模型表现的方法，它与 SFT 的思路截然不同[ibm.com](https://www.ibm.com/think/topics/rag-vs-fine-tuning#:~:text=What%E2%80%99s%20the%20difference%20between%20RAG,tuning)：

-   **能力来源不同**：SFT 通过**模型参数的微调**，直接把特定领域的知识和技能内化到模型的权重中[ibm.com](https://www.ibm.com/think/topics/rag-vs-fine-tuning#:~:text=The%20difference%20between%20RAG%20and,the%20enterprise%20that%20uses%20it)[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=Fine,answering%20benchmarks)。也就是说，SFT 后模型本身就\*\*“学会了”**领域知识，回答无需外援。而 RAG 则假定模型本身**不具备**该领域的全部知识，但可以借助**检索系统**获取相关信息再作答[ibm.com](https://www.ibm.com/think/topics/rag-vs-fine-tuning#:~:text=What%E2%80%99s%20the%20difference%20between%20RAG,tuning)。RAG 的工作机制是在模型推理时，**实时检索**外部数据库或文档，将相关内容与用户问题一起送入模型，以此生成更准确的回答[ibm.com](https://www.ibm.com/think/topics/rag-vs-fine-tuning#:~:text=RAG%20is%20an%20LLM%20optimization,touchpoints%2C%20both%20internal%20and%20external)[ibm.com](https://www.ibm.com/think/topics/rag-vs-fine-tuning#:~:text=Retrieval%20augmented%20generation%20works%20by,more%20relevant%20responses)。因此，RAG 更像是给模型外挂了一个**知识库查询助手\*\*，而不是改变模型内部参数[ibm.com](https://www.ibm.com/think/topics/rag-vs-fine-tuning#:~:text=The%20difference%20between%20RAG%20and,the%20enterprise%20that%20uses%20it)。
    
-   **知识新鲜度**：RAG 的一大优势是能够利用**最新的、动态更新**的数据。当知识领域更新频繁时，RAG 模型可以立刻检索到最新资料并纳入回答[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=RAG%20pulls%20information%20from%20an,during%20its%20last%20training%20session)[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=Consider%20asking%20an%20AI%20about,sensitive%20applications)。相比之下，SFT 后的模型**知识固定在训练时**，如果领域出现新知识，模型**不会自动获取**，需要重新微调才能掌握[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=RAG%20pulls%20information%20from%20an,during%20its%20last%20training%20session)。例如，假如有人问“上周发布的某软件有什么新功能？”，基于 SFT 的模型（除非训练数据包含这个信息）可能回答不了或张冠李戴，而 RAG 模型可以从公司知识库检索上周更新文档，进而给出准确答复[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=Consider%20asking%20an%20AI%20about,sensitive%20applications)。因此，在**数据时效性**要求高的场景（如实时资讯、法规更新等），RAG 更具优势。
    
-   **实现复杂度**：SFT 的实现需要完整的模型训练管线，有GPU训练基础和高质量标注数据，对中小型团队而言可能**门槛较高**。RAG 则侧重构建**检索管道**：需要建立文档数据库、索引、向量检索，并编写将检索结果融入 prompt 的代码[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=The%20work%20involved%20in%20implementing,or%20updating%20data%20becomes%20straightforward)[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=parameter,choosing%20hyperparameters%20and%20preventing%20overfitting)。相对来说，**SFT 在训练阶段成本高**（需要大量算力和人力标注数据），但模型部署后推理**简单快速**（只是正常生成，不额外查数据库）[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=The%20cost%20structures%20also%20differ,or%20more%20complex%20to%20scale)；而 RAG **训练阶段成本低**（无需微调或只做少量调优），但**推理阶段每次都要检索**，引入额外的查询开销和系统复杂度[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=The%20cost%20structures%20also%20differ,or%20more%20complex%20to%20scale)。在服务多个不同领域/客户时，SFT 可能需要**训练多套模型**分别覆盖（开销巨大），而 RAG 则可以用**同一个通用模型**配不同知识库，应对不同领域查询[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=When%20scaling%20across%20multiple%20domains,tuned%20LLMs%20for%20each%20customer)。
    
-   **性能与输出风格**：**微调模型**倾向于给出**连贯一致**且贴合训练风格的回答。例如，微调后的法律问答模型不仅内容准确，还会保持法律措辞和专业语气。而 RAG 模型的回答内容依赖检索结果，往往在事实准确性上**更有保障**（因为可引用文档原文），但语言风格上可能略显**生硬或不够专业贴切**[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=Fine,tuning)[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=Fine,tuning)。微调模型对领域**内部知识**掌握深入（如法律模型深知法条之间关系），因此在回答复杂问题时能**融会贯通**输出高度相关的内容[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=Fine,answering%20benchmarks)[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=For%20complex%20questions%2C%20a%20fine,the%20other%20via%20knowledge%20lookup)；RAG 则更擅长提供**具体事实**（如准确数据、引用条文），减少无依据的臆测，从而**降低幻觉**（编造错误事实）的发生[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=RAG%20tends%20to%20improve%20factual,can%20lead%20to%20poor%20answers)。实践表明，如果**准确性**是第一要求（如客服必须引用最新政策），RAG 更有利[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=RAG%20tends%20to%20improve%20factual,can%20lead%20to%20poor%20answers)；如果要求**回答格式、语气统一**且适应性强，微调模型更适合[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=Fine,tuning)[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=model%20has%20been%20explicitly%20trained,tuning)。
    
-   **泛化与遗忘**：微调会让模型**高度适应**特定领域，但代价是可能**遗忘**部分通用能力，模型对于其他未微调领域的问题表现下降，这被称为“灾难性遗忘”[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=,labeled%20datasets%20can%20be%20time)。RAG 因为没有更改模型内部表征，模型的通用能力**不受损**，它仍保留预训练时掌握的广泛知识。同时，由于 RAG 使用**外部数据支撑**回答，对于超出知识库范围的问题，它更倾向于说“无相关信息”，**幻觉倾向更低**[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=RAG%20tends%20to%20improve%20factual,can%20lead%20to%20poor%20answers)。相比之下，微调模型有时会在未见过的新问题上**编造答案**（因为它只能凭已有参数硬凑一个回复）。通过 RAG，可以**部分避免**这种幻觉，因为模型有真实文本依据[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=RAG%20tends%20to%20improve%20factual,can%20lead%20to%20poor%20answers)。
    

总的来说，**SFT 和 RAG 各有所长**。如果需要模型**内化**专业知识、**低延迟**地执行特定任务，且知识更新不频繁，SFT 是理想方案，能打造**离线独立**的模型。但若需求涉及**动态更新**的信息或大量**私有知识**无法全部用微调覆盖，RAG 是有效选择，它保留了大模型的**通用性**，又通过外部知识扩展模型的**即时准确性**[ibm.com](https://www.ibm.com/think/topics/rag-vs-fine-tuning#:~:text=RAG%20plugs%20an%20LLM%20into,be%20able%20to%20without%20it)。在实际应用中，两者也可以结合：例如先对模型基本能力进行SFT，再通过RAG接入实时数据库，使模型既有良好对话能力又不会因知识陈旧而出错。

## SFT 与继续预训练（Continue Pre-training）的区别

有时预训练模型的能力范围与应用场景有较大差距，这种情况下除了 SFT，还有一种思路是**继续预训练**（增量预训练，Continual Pre-Training）。两者区别如下：

-   **目的不同**：**继续预训练**是指在原始预训练之后，使用额外的大规模未标注语料对模型再训练一段时间，以**弥补模型在某些领域语料上的不足**。这个过程还是无监督的 next-token 训练，只不过语料更聚焦特定领域或风格。它的动机是：当基础模型对目标领域几乎没有涉猎时，直接微调可能效果欠佳，可以先通过继续预训练让模型\*\*“补课”**，获得该领域的背景知识。**SFT** 则是直接用标注数据教模型完成任务。如果说 continue-pretrain 是**扩充模型知识面\*\*，SFT 则是**精雕模型输出行为**。例如，一个基础模型主要训练于英文文本，现在要在医学领域回答问题，如果直接SFT可能发现模型缺少医学术语知识，这时可以先用大量医学文献对模型做一次继续预训练，再进行SFT 微调，这样效果更好。需要注意，**99%的场景下通常不需要增量预训练**，只有当**基础模型和目标领域差异极大**时（比如模型从没见过编程代码，而你要它生成代码），才考虑这一步。
    
-   **顺序不同**：**继续预训练**一般发生在**预训练之后、SFT 之前**。训练流程上看，是先完成原始预训练，然后如果需要，加载预训练模型，投入新的未标注语料继续训练若干步，得到“增量预训练模型”；接着再用有监督数据进行SFT，最后 RLHF 对齐。它相当于预训练的**补充延续**。而 SFT 则始终是在**预训练停止后**进行，有明确的监督信号。如果把大模型开发看作先“打地基”（预训练），再“盖房子”（SFT），那么 continue-pretrain 算是在盖房子前发现地基某块区域不够稳，又**加固打桩**了一次，然后再盖房。
    
-   **数据量与成本**：**增量预训练**所需数据量一般**介于**原始预训练和SFT之间——可能需要数十亿词甚至更多，远多于SFT所需的数据（通常SFT几千到几万样本），但又少于初始预训练的海量数据。因为需要较长时间的无监督训练，所以增量预训练的算力开销也很大，通常只有资源非常充足时才会采用。在绝大多数（>99%）应用中，如果基础模型不是严重偏离目标领域，团队会倾向直接SFT，而不额外进行如此昂贵的 continue-pretrain 步骤。
    

总而言之，**继续预训练是为了解决模型知识覆盖不足的问题**，它本质上仍是在学“是什么”，扩展模型的通识；而 **SFT 是解决模型能力与任务不匹配的问题**，是在学“怎么做”，强调特定任务的执行。举个比喻，如果要让一个通用语言模型成为法律专家，continue-pretrain 是让它**狂读海量法律文献**（无监督，但阅读吸收），SFT 则是让它**跟随律师导师学习问答案例**（有监督，习得解决问题的方法）。通常我们更关注SFT，因为它直接优化任务效果；只有当模型连基本领域背景都没有时，才会补上一段继续预训练作为前置步骤。

## SFT 与 In-Context Learning 的区别

**In-Context Learning（上下文学习）**是指在不改变模型参数的情况下，通过在输入 prompt 中提供一到多个示例，让模型**依靠上下文**来**推断任务模式**并输出答案[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=At%20a%20high%20level%2C%20the,process%20has%20two%20phases)。这个概念在 GPT-3 论文中提出，惊人的发现是大模型可以通过几个示例就表现出一定的**零样本/小样本学习**能力，而**无需梯度更新**模型参数[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=At%20a%20high%20level%2C%20the,process%20has%20two%20phases)。

SFT 与 In-Context Learning 的区别可以概括为：

-   **是否更新模型参数**：**SFT 要更新模型的权重**。每次微调训练，都通过反向传播调整参数，使模型**永久性**地记住新任务的解法。而 **In-Context Learning 完全不调模型参数**[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=At%20a%20high%20level%2C%20the,process%20has%20two%20phases)，模型只是临时地在 prompt 中读取示例，并在**推理过程中**利用这些示例来调整输出。换言之，SFT 是让模型\*\*“再训练一次”**，而 ICL 只是让模型**“临时参考例子”\*\*。
    
-   **示范提供方式**：SFT 时，示范（训练样本）在**训练阶段**提供，属于模型的学习部分；ICL 时，示例在**推理阶段**作为 prompt 的一部分提供，相当于用户在问题前给几个范例。比如，要让模型执行翻译任务，SFT 方法是准备大量（句子，翻译）对进行训练；ICL 方法是直接在 prompt 中写几句英文及其法语翻译，然后让模型翻译下一个给定英文句子。后者模型参数没变，但因为 prompt 里有例子，模型能**根据上下文模式**给出翻译[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=1,via%20cached%20keys%2Fvalues)。
    
-   **泛化能力与持续性**：SFT 一旦完成，模型参数固化，模型在微调任务上**长期有效**，下次使用无需再次提供示例。ICL 则属于一次性发挥，每次回答**都需要**重新提供示例，模型并没有真正“学到”，只是利用其强大的**模式匹配能力**临时完成任务。而且ICL效果很大程度取决于提供示例的质量和格式，稍有变化模型可能无法领会。
    
-   **适用场景**：ICL 适合快速尝试模型在新任务上的能力，不需要训练，**零成本**获得一定效果，但当任务复杂或要求稳定输出时，ICL 难以媲美SFT。SFT 需要付出训练成本，但换来模型对任务**深刻且稳定**的掌握。例如，在产品原型阶段，可以用ICL试试模型能否根据几个例子学会特殊格式回复；而产品正式上线前，通常会通过SFT微调模型确保输出满足要求（比如遵循严格格式或政策）。
    

简而言之，**SFT 是“内化学习”**，模型参数发生改变；**ICL 是“外在提示”**，模型参数不变，通过上下文发挥已有能力。ICL 仰赖模型的**即学即用**本领，而SFT是真正**教会**模型新东西。两者也能结合：我们可以先SFT微调模型具备指令遵循能力，再通过ICL在prompt中给它几个具体案例，使它在新领域也能应付自如。这种灵活运用让LLM更加实用。

## SFT 与 LoRA/PEFT 的区别

在微调大模型时，**并不一定要调整全部参数**。为降低计算/存储需求，社区提出了多种\*\*参数高效微调（PEFT）\*\*方法，代表包括 **LoRA**、Prefix Tuning、Adapter 等。理解它们与传统SFT的区别很重要：

-   **全参数微调 vs. 参数高效微调**：**传统SFT**通常指**全参数微调**（Full Fine-Tuning），即训练过程中模型所有权重均参与更新[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=Full%20fine,layers%2C%20are%20updated%20during%20training)[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=However%2C%20this%20method%20has%20some,is%20small%20or%20lacks%20diversity)。它的优点是理论上性能上限最高，因为模型可以充分调整每一层适应新任务[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=The%20primary%20advantage%20of%20full,trained%20model)。但缺点也明显：对硬件要求高（需要存储和更新完整模型参数），训练慢且**容易过拟合**或“遗忘”原有能力[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=However%2C%20this%20method%20has%20some,is%20small%20or%20lacks%20diversity)。**PEFT** 方法则**冻结大部分模型参数**，只训练极少部分额外参数或附加模块，从而降低资源需求[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=Low,the%20layers%20of%20the%20model)[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=Instead%2C%20a%20low,be%20updated%2C%20leading%20to%20a)。例如 LoRA（Low-Rank Adaptation）在模型的每个线性层新引入两个小的低秩矩阵，仅训练这部分参数，其余权重保持不变[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=Low,the%20layers%20of%20the%20model)[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=Instead%2C%20a%20low,be%20updated%2C%20leading%20to%20a)。这样显著减少了需要优化的参数量，在相同硬件上就能微调更大的模型或更长序列[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=Instead%2C%20a%20low,memory%20usage%20and%20computational%20cost)。
    
-   **内存和算力消耗**：全参数微调需要GPU同时存储模型的**原始权重、梯度以及优化器状态**，对大模型而言显存占用极大（经验上大致是参数量的十几倍显存需求）[massedcompute.com](https://massedcompute.com/faq-answers/?question=Can%20I%20run%20BF16%20models%20on%20a%20Tesla%20V100%20GPU?#:~:text=Compute%20massedcompute,Talk%20to%20our%20Experts)。PEFT 方法只训练少量参数，显存占用和计算成本大幅降低[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=Instead%2C%20a%20low,memory%20usage%20and%20computational%20cost)。LoRA 论文中指出，他们只训练不到0.1%的参数，就能达到和全量微调接近的效果。这对于**资源有限**的团队非常有吸引力：例如你有一个130亿参数模型，直接微调或许需要数十GB显存，而用LoRA只需几GB即可完成训练。
    
-   **性能差异**：由于PEFT没有调优模型的所有权重，所以在一些复杂任务上**性能上限可能略低**于全参数微调[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=dramatic%20reduction%20in%20memory%20usage,and%20computational%20cost)。尤其是任务需要模型对数据**深度理解**并做出微妙调整时，LoRA 等低秩近似可能**无法捕捉所有细节**[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=dramatic%20reduction%20in%20memory%20usage,and%20computational%20cost)。学术研究也发现，LoRA模型在某些情况下虽性能接近全微调模型，但如果严格追求极致表现，全微调仍有优势[news.ycombinator.com](https://news.ycombinator.com/item?id=42085665#:~:text=LoRA%20vs.%20Full%20Fine,of%20existing%20training%20is%20detrimental)。不过对于许多应用而言，LoRA 等PEFT带来的效率提升远超性能上的些许差距，被认为是**性价比极高**的方案。特别是在要保持模型原有能力（避免灾难性遗忘）方面，LoRA 冻结大部分参数反而是一种**正则化**，可以减缓模型忘记预训练知识[arxiv.org](https://arxiv.org/html/2410.21228v1#:~:text=LoRA%20vs%20Full%20Fine,2024%29%20and)。有研究指出 LoRA 微调相比全微调**遗忘更少**，保留了更多通识能力[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=as%20full%20fine,rank)。
    
-   **典型方法**：**PEFT** 是参数高效微调方法的统称，其中包括：
    
    -   **LoRA**：如上所述，引入低秩矩阵近似权重更新[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=Low,the%20layers%20of%20the%20model)。它只在训练时存在，推理时可以将这低秩更新合并回原权重，对推理速度无影响。LoRA 的优点是极大降低了显存和计算需求[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=Instead%2C%20a%20low,memory%20usage%20and%20computational%20cost)，缺点是低秩限制下性能略逊全微调[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=dramatic%20reduction%20in%20memory%20usage,and%20computational%20cost)。
        
    -   **Prefix Tuning**（前缀微调）：在每层Transformer的输入添加一小段可训练的伪token embedding，模型参数不变，只训练这部分前缀。这个方法也很省参数，只是在每次推理也需要附加这段前缀提示。
        
    -   **Adapter Tuning**：在模型的每一层插入小型适配器网络（如两层全连接层），仅训练这些Adapter的参数[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=To%20summarize%20the%20differences%20between,can%20consider%20the%20following%20factors)。Adapter方法过去在计算机视觉、NLP中很流行，也可以大幅减少待训练参数量。
        
    -   **部分层解冻**：另一种思路是**冻结大部分层，只微调少数几层**（如顶层或者某几层中间层）。这种方法在实践中用得相对少，因为找到最佳的解冻层组合不易，一般效果不如LoRA等专门设计的方法。
        
-   **使用现状**：大公司在追求最佳效果时，更多采用**全参数微调**（只要资源允许）[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=The%20primary%20advantage%20of%20full,trained%20model)。全参数微调能够充分发挥模型潜力，在数据充足时通常表现更佳[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=The%20primary%20advantage%20of%20full,trained%20model)。然而在模型极大的情况下（数百亿参数以上），或快速验证/小规模调优时，LoRA/PEFT 方案非常实用。开源社区里，不少低资源爱好者用 LoRA 来 fine-tune 7B、13B 模型实现了诸多有趣应用，因为他们没有能力训练全参数的庞然大物。需要提及的是，有些一线实践者反馈，在一些严肃产品场景，他们较少使用LoRA，倾向直接全模型微调获取最高精度（可能因为他们有充裕的算力，以及全微调易管理单一模型版本）。但对于大多数开发者来说，PEFT 提供了**降维打击**的利器，让微调LLM的门槛大大降低。
    

总结来说，**SFT泛指“微调”动作本身**，通常默认全参数微调，而 **LoRA/PEFT 是实现微调的一种技巧**，核心思想是\*\*“少调参数，多省资源”**。全参数微调追求极致性能，PEFT 方法权衡性能损耗来换取训练成本降低。在实践中，应根据**场景需求**和**资源限制\*\*选择方案：如果要求顶尖效果且有足够 GPU 内存，优先全参数微调；如果资源有限或仅需适度提升，LoRA 等PEFT是不二选择。

## SFT 可以有哪些类型？

SFT 可以按照不同维度进行分类，常见的分类方式包括：

**1\. 按任务类型划分**：根据要微调完成的任务不同，SFT 可用于各种任务，包括但不限于：

-   **对话/问答类**：让模型在多轮对话中扮演助手角色，回答用户各种问题。这类SFT数据通常格式为Instruction-Response形式，人们也称之为**指令微调**。例如 GPT-3.5/4 的SFT数据就是大量用户指令及正确回答对。
    
-   **分类任务**：输入一段文本，让模型输出分类标签。这时SFT数据就是很多标注了类别的文本，让模型学会预测标签。比如情感分类（Positive/Negative）。
    
-   **文本生成任务**：如摘要生成、机器翻译、代码生成等，SFT 数据是输入文本和期望输出的对，模型据此学习生成策略。
    
-   **相似度判定/排序任务**：如给出两个句子判断是否语义相似，或给出查询和文档判断相关性。SFT 可以微调模型最后输出embedding用于相似度计算，或者直接让模型输出评分/判定结果。
    

无论任务如何，SFT 的本质都是**给定输入，监督模型输出期望结果**，区别只在具体应用场景和数据格式上稍有不同。一个经过对话任务SFT的模型，往往具有良好的**聊天与指令遵循**能力；而经过分类任务SFT的模型，则像一个**分类器**一样表现。

**2\. 按模型参数调整范围划分**：可以分为：

-   **全参数微调**：即前面介绍的**传统SFT**方式，训练中所有模型参数都会更新。很多大型科技公司采用此法，因为有足够计算资源且追求最高精度。
    
-   **PEFT 微调**：即利用**LoRA、Adapter**等参数高效方法，只训练一小部分参数。开源社区不少项目使用PEFT，让个人笔记本也能微调7B模型。
    
-   **部分参数微调**：即**部分层冻结**、部分层训练的方法。目前工业界用得较少，可以看作全参数微调和PEFT间的折中尝试。比如有论文只微调Transformer最后几层，或只微调嵌入层和LN层等。不过由于效果和通用性不突出，此法并未广泛流行。
    

需要注意，业界在谈“SFT”时，有时默认指**全模型SFT**。但在学术/开源实现里，会明确说明微调方法，例如“我们对XX模型进行了LoRA微调（PEFT的一种）”，或者“进行了全参数SFT”。**SFT强调的是目的（微调模型能力）**，而**LoRA/PEFT强调的是手段（少调参数）**。两者概念层面有交叉，从分类维度看并非对立：LoRA微调也是一种SFT，只不过不是full SFT 而是参数高效SFT。

## SFT 的前提条件和准备工作

要成功进行 SFT 微调，需要满足几个基本前提条件：**基座模型**、**微调数据**、**微调环境**。

**1\. 基座模型的选择**：首先需要选定一个**预训练好的基础模型**作为微调起点。一般我们会：

-   **从权威来源获取预训练模型**：可以从 ModelScope、HuggingFace 等平台下载经过良好预训练的 LLM（如Llama2、BLOOM等）。确保模型的**架构和尺寸**适合任务和可用算力。
    
-   **Base模型 vs. Chat模型**：很多模型发布时有两类版本：基础版（base）和对话版（chat）。**Base模型**是纯预训练的，没有经过任何指令微调；**Chat模型**通常是在base模型上已经进行了一轮指令SFT，具备基本的对话和指令遵循能力（有时也可能包含RLHF阶段）[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=%2A%20%E6%8C%81%E7%BB%AD%E9%A2%84%E8%AE%AD%E7%BB%83%28Continual%20Pre,%E8%AE%AD%E7%BB%83%E8%B5%84%E6%BA%90)。对于二次开发来说，**通常优先选择 chat 模型作为SFT基座**，因为它已经能理解指令、遵守一定人类偏好，在此基础上再做领域微调效果更好、更省事[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=%2A%20%E6%8C%81%E7%BB%AD%E9%A2%84%E8%AE%AD%E7%BB%83%28Continual%20Pre,%E8%AE%AD%E7%BB%83%E8%B5%84%E6%BA%90)。直接用base模型微调虽然也可行，但你要首先“教会”模型听懂指令格式，会浪费很多精力在基础对齐上。当然，如果你的任务不需要对话能力，或你有非常充足的数据从头教一个base模型，也是可以的。
    
-   **大模型 vs. 小模型**：基座模型参数量有大有小（如从7B到70B不等）。**并不是越大越好**，要根据应用场景和资源抉择。**单一专门任务**，小模型经过良好微调可能已经足够，反而更高效部署；而**需要复杂推理或广泛能力**的场景，大模型表现会更优。比如做一个简单客服问答，用7B模型微调也许就够；但做一个通用AI助手，可能需要几十B的模型做底座才能保证全面智能。
    
-   **模型量化版本**：ModelScope等平台常提供三类模型：①原始预训练模型（fp16精度）；②已微调的chat模型（fp16）；③在chat模型基础上的**量化模型**（如int8或int4）[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,%E6%96%B0%E6%8A%80%E6%9C%AF)。量化模型是将大模型权重用更低比特表示（如8bit、4bit）以节省显存，但会损失一些精度。对于微调，**一般使用全精度（fp16）模型**作为基座，避免量化误差干扰训练。如果显存不够也可尝试在量化模型上套用 LoRA 等微调，但需要注意混合精度的问题（后面会讲）。
    

**2\. 微调数据的准备**：高质量的**微调训练数据集**是 SFT 的生命线，通常需要考虑：

-   **数据格式**：根据微调任务的不同，设计合适的输入/输出格式。通常LLM的SFT数据会采用**对话格式**或**指令-响应格式**。现在比较通用的两种格式：**Alpaca格式**（Stanford Alpaca项目使用的JSON，每条包含 instruction、input、output 字段）和 **ShareGPT 格式**（源自ShareGPT的多人对话记录，包含多轮上下文）[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,T2Q%EF%BC%9A%E9%9A%90%E5%90%AB%E6%8E%A8%E7%90%86%E6%8F%90%E5%8F%96%E6%B3%95)。Alpaca格式简洁，适合单轮指令微调；ShareGPT格式保留了对话中的来回过程，更复杂，适合训练多轮对话能力。选择格式时，要看**基座模型**需要的输入格式（如是否要求系统提示、角色标签等）并**统一格式**。一个技巧是**将所有训练样本整理为统一的JSON结构**，包括统一的markdown用法、统一的缩进等，确保模型学到一致规范的输出风格（有实践者提到要统一所有JSON数据的格式，比如是否带markdown，缩进空格数等，以免模型输出时格式混乱）。
    
-   **包含思维链（CoT）**：CoT（Chain-of-Thought）数据指在答案中包含模型的**思考过程**。在数学、逻辑推理等任务中，加入思维链示例有助于模型学会**逐步推理**[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=%E6%95%B0%E5%AD%A6reasoning%E4%B8%8A%E6%98%AF%E6%9C%89%20%E4%B8%89%E7%A7%8D%E5%BD%A2%E5%BC%8F%20%E5%8F%AF%E6%98%BE%E8%91%97%E6%8F%90%E9%AB%98%E6%95%88%E6%9E%9C%E6%A8%A1%E5%9E%8B%20reasoning%20%E8%83%BD%E5%8A%9B)。CoT 数据通常包括：问题、思考过程、最后答案三部分。在 SFT 数据中，可以将**思考过程**作为回答的一部分，让模型模仿先思考再得出答案的模式。常见做法是在最后一轮对话前由模型展示思考（这有时称为启用“思考模式”）。不过增加CoT会明显增大输出token数量，从而**减慢推理速度**，需要在效果和性能间平衡[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=%2A%20Prefill%20is%20a%20one,the%20prefill%20overhead%20might%20dominate)（很多人明知CoT有效但生产环境少用，就是因为**生成的token太多影响速度**）。可以**针对需要推理的子任务**准备CoT数据，而非所有数据都带思维链，以兼顾性能。
    
-   **数据来源**：微调数据可以**人工构造**或**人工+模型协作构造**。人工编写能保障质量但成本高；常见策略是先用大模型产生初步回答，再由人类审核修改，生成高质量数据（有人将这称为**人类和大模型协同**标注）。另外还可以用**RAG**方式：对一些问题让模型检索资料，再组织答案，这样得到的问答对事实准确率高，也可以纳入SFT数据集。无论来源如何，关键是要**尽可能多样化**：**丰富 prompt 的类型和表达方式**，甚至有意加入一些噪声prompt以增强模型鲁棒性（抗噪能力）。例如同一请求可以有不同说法，“帮我总结上文” vs “请概括以上内容要点”。提升多样性可以防止模型**局限于套路**。
    
-   **数据质量与清洗**：获取高质量的微调数据是SFT中最费时也最重要的工作。业内经验是：开发者**95%以上的时间**可能都花在**数据收集、分析、清洗**上，而非模型训练本身。一定要**反复清洗数据**，确保没有冲突、错误、格式不统一的样本。不少实践者有惨痛教训：“尝试各种办法模型效果都上不去，最后老老实实用规则+人工把数据一条条清洗，模型才终于稳定”——尤其对复杂推理任务，如果数据里答案有矛盾点，模型很容易**学疯**（学到冲突信息导致输出混乱）。所以宁缺毋滥，保证每条示例都是**正确且一致**的。具体措施如：剔除错误标注，统一单位和格式，去除不雅或敏感内容等等。
    
-   **Instruction 和 Input**：对话/指令数据通常分 Instruction（系统/用户指令）和 Input（用户具体内容）。实践中**一定要给出 Instruction 部分**，明确告诉模型扮演的角色或任务。例如Instruction写：“你是百科问答助手”，Input是用户的问题。哪怕有时没有额外context输入，Input可以留空，但 Instruction 不要省略，这样模型知道“我是在执行一个指令，需要输出答案”。否则模型可能无法判断自己身份而回答风格不统一。总之，**数据要让模型明确角色和任务**，这会让微调效果更理想。
    

**3\. 微调环境的搭建**：指进行 SFT 训练所需的**硬件、软件、工具**等配置：

-   **硬件**：主要是**GPU**。大模型微调对显存要求高（尤其全参数微调）。经验上，所需显存约为模型参数量的**10-12倍**[massedcompute.com](https://massedcompute.com/faq-answers/?question=Can%20I%20run%20BF16%20models%20on%20a%20Tesla%20V100%20GPU?#:~:text=Compute%20massedcompute,Talk%20to%20our%20Experts)。例如微调一个10亿参数模型，大概需要12GB左右显存才能跑通完整训练过程（包括模型权重、梯度、优化器状态等占用）。多GPU可以**并行加速**或**分布模型**。如果GPU显存不足，可以考虑**梯度累积**、**混合精度**甚至**模型并行**等方案来勉强训练，但速度和稳定性会受影响。另外，不同GPU架构的能力也不同：例如NVIDIA V100不支持**bfloat16（BF16）**精度（这是安培A100引入的新数据格式）[reddit.com](https://www.reddit.com/r/MachineLearning/comments/vndtn8/d_mixed_precision_training_difference_between/#:~:text=,TPU%20supports%20BF16%20since)；也早期版本的 FlashAttention 算法（高效Attention实现）不支持 V100 这类老架构[discuss.huggingface.co](https://discuss.huggingface.co/t/load-phi-3-small-on-nvidia-tesla-v100-flash-attention/99360#:~:text=v100%20is%20Volta%20generation%20GPU,have%20Ampere%20or%20later)。因此在配置环境时，要根据你的GPU型号调整一些**训练参数**（如将默认bf16改为fp16/fp32）。还有的模型发布时用了一些Hopper架构新特性（FP8等），老GPU上可能跑不了，需要关闭或修改配置。总之**硬件环境**包含：GPU型号/数量、CPU、内存、存储IO、操作系统和驱动（CUDA等），都要兼容。
    
-   **软件和工具**：主流的大模型微调工具链包括：
    
    -   **深度学习框架**：如 PyTorch（最常用）或 TensorFlow。PyTorch 在Transformer领域应用更广。
        
    -   **分布式训练库**：如 **Megatron-LM**（英伟达的LLM训练框架）、**DeepSpeed**（微软开发，可高效并行和内存优化）、**Accelerate**（HuggingFace的轻量级多GPU库）等。它们能将模型和数据切分到多卡上，实现**并行训练**，突破单卡显存限制。比如 DeepSpeed 的 ZeRO技术可以把优化器状态平均分布到多GPU，从而训练更大模型[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=%2A%203.%20Model%20Mixture,RLHF%20%E4%BA%BA%E7%B1%BB%E5%8F%8D%E9%A6%88%E5%BC%BA%E5%8C%96%E5%AD%A6%E4%B9%A0)。
        
    -   **开源微调工具**：如 **Hugging Face Transformers**库自带 Trainer，方便地微调成千上万种预训练模型；**LLaMA-Factory**（一个开源平台，号称提供开箱即用的大模型微调环境）；**Unsloth**（开源LLM微调工具，优化了计算步骤和GPU kernel，据称可显著提升训练速度并减少显存占用[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/24442583307#:~:text=%E5%9C%A8%E5%86%85%E5%AD%98%E4%BD%BF%E7%94%A8%E6%96%B9%E9%9D%A2%EF%BC%8CUnsloth%20%E6%AF%94%E4%BC%A0%E7%BB%9F%E7%9A%84%E5%BE%AE%E8%B0%83%E6%96%B9%E6%B3%95%E5%87%8F%E5%B0%91%E4%BA%8670%25%20,%E5%B9%BF%E6%B3%9B%E7%9A%84)）。在实际应用中，可以根据熟悉程度选择工具。例如很多人直接用 Transformers + Trainer/Accelerate，优点是生态成熟、模型和数据读取方便；而追求极致性能的可能会选 DeepSpeed 或自研程序。
        
    -   **框架版本依赖**：务必注意不同库和模型代码对**Python、CUDA、PyTorch版本**等的要求，避免版本冲突导致训练失败。比如一些新模型的代码需要PyTorch2.x，否则跑不通。
        
    -   **其他**：数据处理需要 pandas 或自编脚本，将原始数据转换为模型所需格式；训练监控可以用 TensorBoard 等查看loss曲线；如果做混合精度需要 NVIDIA Apex 等库。
        

总之，在SFT开始前，要**下载并加载好基础模型**、**准备好训练数据**、**配置好运行环境**。可以写一个简单的**验证脚本**确保模型能正常forward，数据能正确tokenize无错误。只有地基打稳，才能开始大展拳脚训练模型。

## 如何选择 SFT 的基座模型？

基座模型（微调起点模型）的选择对SFT成败有重大影响，主要考虑以下几个问题：

**（1）Base 模型 vs. Chat 模型**：前面提到过，一般推荐用**Chat模型**作为微调起点。Chat模型往往是官方已经用指令数据做过一轮SFT的版本，具备基本的**指令遵循和对话上下文能力**[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=%2A%20%E6%8C%81%E7%BB%AD%E9%A2%84%E8%AE%AD%E7%BB%83%28Continual%20Pre,%E8%AE%AD%E7%BB%83%E8%B5%84%E6%BA%90)。它相当于已经“上过训练营”的模型，知道看到`"用户:"`提问该怎么答，懂得格式例如不随意超出角色等。拿这样一个模型再进行垂直领域微调，可以**事半功倍**。反之，如果用 Base 模型（未指令调优的）作为起点，你的SFT数据得先教它听懂用户指令。例如很多Base模型一开始并不会在回答里避免第一人称、或者它可能继续问用户问题而非直接回答，因为预训练目标不是对话。如果SFT数据量足够大，其实也能从零训练出对话能力，但这等于把别人已经做过的工作重做一遍，**浪费数据**。因此除非有特殊原因（比如chat模型授权限制，或你想探索不同风格），大多数情况**直接用chat模型**更省心。

**（2）模型规模的权衡**：大模型（如30B、70B参数）相比小模型（7B、13B）有更强的表达和推理能力，但训练和推理成本也高。选择多大的基座模型，取决于**任务复杂度**和**部署限制**：

-   如果你的应用只是**单一窄任务**，例如分类评论正负面，或者做一个特定领域的问答，小模型经过微调完全可能达到满意效果，而且响应速度快部署成本低。此时用一个数百亿参数模型有些大材小用，不必要的容量还可能带来幻觉或不稳定。
    
-   如果应用需要模型具备**通用对话能力、多种技能**，或者要求**推理多步**得出结论（如复杂数学），大模型的优势会明显体现。比如OpenAI的GPT-4据称是上千亿参数，能应付非常开放的对话和创意任务，这是小模型难以企及的。
    
-   资源方面也要考虑：有多少GPU，可以负担多大模型。一般要保证模型能放进显存并留有训练余量，否则训练会频繁内存溢出。
    

总之策略是：**够用就好**。能用小模型解决问题，就没必要用大模型增加开发和运维负担；但如果小模型无法胜任需求，就要选更大的模型甚至多种模型 ensemble。很多团队会先用小模型实验，如果效果不理想再逐步升级模型规模。

**（3）模型版本和发布源**：如今模型库里，每种模型常有**不同版本**，要仔细分辨：

-   官方或权威机构发布的模型一般分raw/base、指令微调(chat)版、量化版等[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,%E6%96%B0%E6%8A%80%E6%9C%AF)。尽量选择**原版模型**做SFT（不要用已SFT过其它数据的模型作为基座，除非确定无冲突），否则可能产生**数据冲突**（模型已学过的行为与你的新数据不一致，会干扰训练）。当然，如果两批数据是互补关系也问题不大。
    
-   看**模型许可**。有的预训练模型允许商用，有的不允许。后续产品化时模型基座许可需合规。如果原始模型不能商用，但你SFT出一个商用服务，这是不被允许的。
    
-   确认**模型架构**与微调框架兼容。比如有些模型使用了特殊推理代码（trust\_remote\_code=True那种），用 Trainer 训练时要传相应参数。基座模型一般要包含**分词器**，确保编码解码一致。
    
-   注意**模型量化**：如果选用了量化版本模型作为基座，前面提到尽量走LoRA等PEFT路线，而不要尝试全参数更新，因为量化模型很多权重信息丢失，不适合反向传播更新。同时要确认微调过程中计算精度匹配，比如GPUs通常对FP16支持好，对int4不一定支持训练。所以**强烈建议**微调基座用全精度模型，以免不必要麻烦。
    

选择好了合适的基座模型，相当于站在一个合适的起点。一个预训练良好又契合你任务的基座，会让SFT事半功倍；反之如果基座差（预训练质量低）或者不匹配，可能要用微调来弥补基础能力的不足，难度就高多了。

## SFT 训练数据集如何构建？

构建 SFT 训练集需要**对症下药**，针对不同模型和任务，设计合适的数据格式和获取方法：

**（1）数据格式与内容**：正如前文所述，SFT 数据通常是**指令-输出对**。具体格式上，现在比较通用的是 **Alpaca 风格 JSON** 或 **ShareGPT 多轮对话**。[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,T2Q%EF%BC%9A%E9%9A%90%E5%90%AB%E6%8E%A8%E7%90%86%E6%8F%90%E5%8F%96%E6%B3%95)两者各有适用场景：

-   **单轮指令微调**：推荐 Alpaca 格式，每条数据有 `"instruction"`（用户要求）、`"input"`（可选额外输入）、`"output"`（期望回答）。大部分基础能力微调使用这种，因为它简单直接。如果不涉及多轮上下文，可以将所有需要教模型的任务都表述为这种 (指令 → 答复 ) 模式。
    
-   **多轮上下文对话微调**：如果想让模型学会长对话、多轮记忆，就采用ShareGPT风格的数据，即一整段对话历史。常见做法是把用户和助手的每轮发言依次列出，让模型学习在已有多轮基础上回复下一句。这种数据关心**上下文逻辑和衔接**，如长对话中的指代、省略处理等。训练长对话能力很重要，但这类数据编写更困难。
    
-   有的项目还会混合格式，比如大部分单轮，少部分多轮，或者构造成类似 ChatML 格式（OpenAI对话格式）。**关键是所有数据格式尽量统一**，尤其是给定的 system prompt 风格、换行/标记符号等。因为训练中出现的格式模型都会记忆，一致性越高，模型输出越不会乱用格式。
    

**（2）数据获取方法**：主要有 **人工标注** 和 **人工+模型配合生成**：

-   **纯人工**：由领域专家或标注员根据任务需求撰写大量高质量的 Q&A 对。优点是质量可控、贴合需求；缺点是耗时费力，规模有限。一般用于要求特别高的场景（如法律、医疗等敏感领域需要专家标注）。
    
-   **大模型辅助**：利用现有强大模型（如GPT-4）来生成部分指令及答案，再人工审核修改。比如 Stanford Alpaca 项目就是用OpenAI模型生成了5万条指令及答案。这种方式**高效**但要小心质量：初始模型可能引入一些风格或错误，需要**人工把关**。另外还有**基于检索的生成**：对于知识型问答，可以检索资料然后组织答案，这样得到的数据真实可靠，人工再润色格式即可。
    
-   **扩充多样性**：无论哪种来源，都要注意**丰富任务类型和表述**。正如有经验者说的，要想尽各种办法扩充 prompt 的多样性，包括语气、用词、长短等等[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/24442583307#:~:text=%E5%9C%A8%E5%86%85%E5%AD%98%E4%BD%BF%E7%94%A8%E6%96%B9%E9%9D%A2%EF%BC%8CUnsloth%20%E6%AF%94%E4%BC%A0%E7%BB%9F%E7%9A%84%E5%BE%AE%E8%B0%83%E6%96%B9%E6%B3%95%E5%87%8F%E5%B0%91%E4%BA%8670%25%20,%E5%B9%BF%E6%B3%9B%E7%9A%84)。甚至可以**刻意加入扰动**：如在指令里添加拼写错误、口语化表达，训练模型对噪声鲁棒。这些都能避免模型训练后只能识别一种固定问法。
    
-   **统一标准**：将收集的原始数据进行**格式清洗**。如前所述，统一JSON格式，统一是否含markdown、换行风格等[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/24442583307#:~:text=%E5%9C%A8%E5%86%85%E5%AD%98%E4%BD%BF%E7%94%A8%E6%96%B9%E9%9D%A2%EF%BC%8CUnsloth%20%E6%AF%94%E4%BC%A0%E7%BB%9F%E7%9A%84%E5%BE%AE%E8%B0%83%E6%96%B9%E6%B3%95%E5%87%8F%E5%B0%91%E4%BA%8670%25%20,%E5%B9%BF%E6%B3%9B%E7%9A%84)。这一点很容易被忽视但很重要。否则模型可能学到不统一的输出格式（忽而有markdown格式忽而没有）。
    

**（3）数据质量评估**：拿到初步数据集后，要评估其质量，包括：

-   **样本多样性**：涵盖足够广的场景。要检查有没有某些问法/类型高度重复，而另一些情况完全没覆盖。如果单一模式太多，模型会过拟合固定回答模板，缺乏适应性。
    
-   **答案正确性**：确保每个示范答案都是**事实正确、逻辑自洽**的。特别在知识型问答数据里，答案要核实是否准确。错误示范比没示范更糟，会把模型带沟里。
    
-   **回答风格一致性**：如果期望模型有统一的语气/格式（如礼貌地称呼用户、回答分条列点等），那示范答案应该尽量都遵循这些规则。否则模型学到矛盾风格，会产生不稳定输出。
    
-   **无冲突**：检查有没有两条数据的指令类似但答案不同的情况（除了客观允许的多样答案外）。如果有，要修正统一，否则模型可能无所适从。比如一条教它“如何处理坏心情”回答“去跑步”，另一条类似问题回答“静坐冥想”，模型可能混乱。可以通过人为丰富答案让模型知道多种解法，但要确保**不直接矛盾**且在上下文区分条件。
    

可以说，**优质的微调数据胜过大量的平庸数据**。有研究表明，在指令微调中，与其追求数量不如打磨质量，一万条高质量样本往往足矣[anote-ai.medium.com](https://anote-ai.medium.com/lima-less-is-more-for-alignment-21e0db831e66#:~:text=LIMA%3A%20Less%20Is%20More%20for,carefully%20curated%20prompts%20and%20responses)。Meta 的 **LIMA** 项目更是用仅1000条精心挑选的问答对，把65B模型对齐到接近GPT-4水平[anote-ai.medium.com](https://anote-ai.medium.com/lima-less-is-more-for-alignment-21e0db831e66#:~:text=LIMA%3A%20Less%20Is%20More%20for,carefully%20curated%20prompts%20and%20responses)。因此在时间有限时，把精力放在提高数据质量而非盲目扩充数量，是明智的选择[anote-ai.medium.com](https://anote-ai.medium.com/lima-less-is-more-for-alignment-21e0db831e66#:~:text=LIMA%3A%20Less%20Is%20More%20for,carefully%20curated%20prompts%20and%20responses)。

**（4）数据量需求**：SFT需要多少数据呢？这没有一概而论的答案，但一般来说：

-   小规模微调几千条数据就能看到明显效果提升。OpenAI 的 InstructGPT 微调阶段用了大约**1.3万组**指令数据[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=%2A%20Training%20data%3A%20high,approximately%2088%2C000%20pairs)，已经让模型从GPT-3变得听话很多。
    
-   常见的开源指令微调数据集规模在**几千到几万**。如 Alpaca 52k、人类反馈对话数据10万级别等。
    
-   **任务难度**影响需求：简单任务（如分类）可能一两千样本就够，复杂开放对话可能要上万。也可以采用**课程学习**策略：先用几千基本问答SFT，再逐步增加难度数据继续SFT。
    
-   **LIMA思想**：【“少即是多”】。一篇论文指出，只需约一万条优质指令样本，就能达到很好的效果[anote-ai.medium.com](https://anote-ai.medium.com/lima-less-is-more-for-alignment-21e0db831e66#:~:text=LIMA%3A%20Less%20Is%20More%20for,carefully%20curated%20prompts%20and%20responses)。与其搞几十万低质数据，不如精心挑选打磨一万条。这理念越来越被接受。
    
-   如果有子任务分布，可以**按需分配数据**：重要场景多给些数据，次要场景少给或不单独给。这涉及数据配比，复杂度高的任务数据可以适当多一些。
    

综合来说，**2千到10万条**都是可能的数据量范围，要视具体任务分析。宁可数据少而精，也不要多而杂。“一万优质样本即可达成理想效果”并非夸张，而是有实践支持的观点[anote-ai.medium.com](https://anote-ai.medium.com/lima-less-is-more-for-alignment-21e0db831e66#:~:text=LIMA%3A%20Less%20Is%20More%20for,carefully%20curated%20prompts%20and%20responses)。

## 如何评估 SFT 训练数据集的质量？

拿到一个SFT数据集，我们可以从多个维度来评估质量，确保在训练前清洗完善。关键指标包括：

-   **指令多样性**：检查 prompt 部分是否涵盖足够广的语言风格、领域和难度。有无过多重复或模板化的问句？高质量数据集应包括各种各样的问题，从直白提问到复杂长句、从常见任务到边缘场景。可以计算指令的词汇多样性、长度分布等来量化。
    
-   **任务覆盖面**：如果模型要胜任多种功能，数据应反映所有这些功能。例如一个通用助手需要既有闲聊对话数据，又有知识问答、推理题、编程题等。每类任务的数据量是否合理？有没有某些任务完全没教？这需要领域专家评估和统计分析相结合。
    
-   **答案质量**：评估答案是否**正确、有用**。这可能需要人工抽样检查或者借助现有强模型辅助。错误答案、含糊其辞的答案都应移除或修正。此外答案是否符合预期格式（如需要条列就要条列清楚）也属质量指标。
    
-   **一致性**：看整个数据集的回答风格是否一致。如前所述，有无前后矛盾或风格冲突。过于发散的风格会让模型输出不稳定。可以建立**风格指南**，按照指南检查每条数据。例如要求回答一律使用礼貌语气，那凡是不礼貌的样本就不合格。
    
-   **噪音**：剔除无关或有害内容。预训练数据中常有噪音，但SFT数据应该尽量干净。确保没有脏话、人身攻击、隐私信息等。如果SFT目的是对齐安全策略，更要严格筛除违规内容。
    
-   **覆盖难度**：题目难易度是否梯度合理。假如全部都是很简单的问题，模型训练后遇到稍难的就不行。所以应有一定比例的高难度数据。但也不能全是超难题，否则模型可能学不会或过拟合难题模式。
    

评估这些指标需要**自动+人工**结合。自动方面可以写脚本计算长度分布、重复率等；人工方面需要对样本进行详细review。大型数据集可以抽样评估。很多团队引入**标注审核流程**，分多轮审核清洗数据，不断提升质量。

最简单的客观指标之一是训练完成后模型的**loss曲线**：如果训练loss降得很低但验证loss很高，可能数据有问题（模型过拟合）。当然这是训练后反馈。训练前评估主要靠人工经验。

一句话：**好钢用在刀刃上**，优质数据集能让模型如虎添翼，而劣质数据可能让模型学歪甚至性能下降。数据质量评估和清洗是确保SFT成功的关键步骤，万万不可省略。

## SFT 对硬件和资源有什么要求？

大模型 SFT 对计算资源要求较高，这里讨论主要的硬件考虑：

**（1）显存占用**：训练过程中显存主要消耗在**模型参数、副本、优化器状态、梯度和激活值**上。其中模型参数和优化器状态（例如Adam会存二阶矩估计）往往需要原始模型参数量的数倍内存。经验法则：**所需显存 ≈ 模型参数量的 10~12 倍**[massedcompute.com](https://massedcompute.com/faq-answers/?question=Can%20I%20run%20BF16%20models%20on%20a%20Tesla%20V100%20GPU?#:~:text=Compute%20massedcompute,Talk%20to%20our%20Experts)。例如，10亿参数模型大概需要12GB显存才能全程训练（FP16精度情况下）。因此：

-   一个70亿参数模型理论上需要约80~100GB显存才能全参数微调（如果使用Adam优化器）。这通常需要8张以上高端GPU协同才能满足。
    
-   可以使用**优化策略**降低显存，如DeepSpeed ZeRO将优化器状态分摊、Gradient Checkpointing节省激活等，但这些通常以增加训练时间为代价。
    
-   **FP16 vs BF16**：NVIDIA Ampere 架构(如A100)开始支持bfloat16，这种格式对内存与FP16相当，但对某些运算更稳定。**V100及以前**不支持bf16，只支持FP16[reddit.com](https://www.reddit.com/r/MachineLearning/comments/vndtn8/d_mixed_precision_training_difference_between/#:~:text=,TPU%20supports%20BF16%20since)。在这些GPU上需要将bf16设置改为FP16或FP32，才能正常训练[massedcompute.com](https://massedcompute.com/faq-answers/?question=Can%20I%20run%20BF16%20models%20on%20a%20Tesla%20V100%20GPU?#:~:text=Compute%20massedcompute,Talk%20to%20our%20Experts)。另外**Flash Attention**（高效注意力算子）在V100上早期也不支持[discuss.huggingface.co](https://discuss.huggingface.co/t/load-phi-3-small-on-nvidia-tesla-v100-flash-attention/99360#:~:text=v100%20is%20Volta%20generation%20GPU,have%20Ampere%20or%20later)（因为V100架构sm7.0当时flash-attn没有实现），需要相应调整或使用兼容版本。总之，不同GPU有不同限制，需要对症配置。
    
-   **显存监控**：训练前最好用小批量跑一下，看每GPU占用。显存临界时可以调小batch，或使用梯度累积来在更小batch下模拟大batch。
    

**（2）GPU算力**：除了显存，计算性能也影响训练速度。SFT通常不会像预训练那样跑几个月，但根据数据量和模型大小也可能需要几小时到几天。多GPU并行可以线性加速，但要注意通信开销是否成为瓶颈。使用NVLink高速互联的GPU群组会更好。还要关注**GPU算力的精度支持**：如**V100**的Tensor Core对FP16有加速（理论上120 TFLOPS）[reddit.com](https://www.reddit.com/r/LocalLLaMA/comments/1fzkxfa/how_many_years_does_the_v100_have_left/#:~:text=Reddit%20www,doesn%27t%20support%20bfloat16%20and%20FlashAttention), 而A100对于BF16也有类似加速。如果使用FP32训练速度会慢非常多，不建议。

**（3）存储和CPU**：数据读取、预处理由CPU和存储负责。如果训练数据很大，要确保**I/O**跟得上，不要GPU等数据。可以使用**内存映射**或LMDB等加速读取。CPU核数够用也能在加载和tokenize时更快。特别训练多GPU时，数据分发不能成为瓶颈。NVMe SSD比HDD好很多。

**（4）框架依赖**：底层驱动和库也属于“环境”。CUDA版本需要和框架匹配，NCCL库用于多GPU通信。注意**flash-attn**、**bitsandbytes**（用于8bit optimizer或者GPTQ加载）等库版本对GPU架构的要求。例如flash-attn不同版本支持GPU架构不同，要安装对版本。**NVIDIA驱动**也得跟CUDA匹配，不然后面框架调kernel会出错。

**（5）PEFT和量化**：如果使用 LoRA 等PEFT，对硬件要求会降低：因为冻结大部分参数，仅训练 LoRA 层，如7B模型LoRA甚至**单张16GB GPU**就能训。这是PEFT受欢迎的原因之一。但也需注意：

-   LoRA 训练完后保存的 checkpoint 通常只包含 LoRA 引入的权重（例如低秩矩阵），文件很小。**推理时**需要将它们和原模型**合并**才能得到完整模型权重。或者通过加载base模型再加载LoRA层方式实现。测试部署前别忘了这步，不然模型实际没应用那些微调。
    
-   **GPTQ 量化模型微调**：GPTQ是一种4bit量化方案，有人会先加载一个4bit量化模型再套LoRA训练（称为QLoRA）。实践中**不建议对量化模型做全参数微调**，因为量化是有损过程，回传梯度容易不稳定。配合LoRA等PEFT是可行的，但要确保类型匹配：如 GPTQ模型权重是int4+FP16混合，LoRA层是FP16，如果直接合并在一起会有困难[reddit.com](https://www.reddit.com/r/LocalLLaMA/comments/1fzkxfa/how_many_years_does_the_v100_have_left/#:~:text=Reddit%20www,doesn%27t%20support%20bfloat16%20and%20FlashAttention)。当前实现一般是在推理时对int4权重解码，然后应用LoRA偏移。所以如果可以，**尽量使用原始FP16模型微调**，除非内存实在不允许才选择QLoRA方案。
    

**（6）其他硬件**：除了GPU：

-   **CPU RAM**：加载模型和数据需要内存。7B模型fp16需要~14GB内存加载，30B要60GB左右内存。加上数据集（特别如果大量加载到内存）也要预估。内存不足会造成交换，严重拖慢训练。
    
-   **网络**：如果用多机分布式训练，机器间网络带宽和延迟很关键。InfiniBand高带宽网络常用于多机GPU训练，否则参数同步会拖慢甚至无法完成。
    
-   **电源散热**：长时间高负载训练对机器硬件压力大，注意散热、防止过热降频等。
    

总之，准备进行SFT，**硬件资源评估**是第一步。需要多少GPU、能不能并行、能不能放下模型，提前计算好。若资源不够，要么缩小模型/批量，要么采用PEFT/低精度来降低需求。将资源要求和实际可用硬件平衡好，训练才能顺利进行。

## SFT 训练过程是什么样的？

当所有准备就绪开始训练后，可以关注训练过程中模型的损失曲线和一些典型现象：

**（1）损失曲线变化**：通常会在训练中监控**训练集loss**和**验证集loss**随迭代的变化。典型情况：

-   **训练loss**通常从初始较高值迅速下降，在前若干 step 降幅最大，然后逐渐趋于平稳甚至有轻微震荡[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=SFT%20packing%20%E6%8C%87%E8%AE%AD%E7%BB%83sft%E8%BF%87%E7%A8%8B%E4%B8%AD%EF%BC%8C%E5%B0%86%20%E5%A4%9A%E4%B8%AAsft%E6%95%B0%E6%8D%AEpack%E5%88%B0%E4%B8%80%E4%B8%AA%E6%A0%B7%E6%9C%AC%E5%86%85%20%E8%BF%9B%E8%A1%8C%E8%AE%AD%E7%BB%83)。
    
-   **验证loss**则先下降，到达某个最低点后可能开始上升[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=)。验证loss上升通常意味着模型开始过拟合训练集了，即**泛化性能变差**。所以在验证loss最低点附近停止训练或使用该epoch模型作为最终模型，是比较稳妥的。
    
-   训练中后期，可能出现**训练loss继续下降、验证loss上升**的明显分叉（过拟合征兆）。此时模型在训练集已经学得很好，但对未见数据表现变差。过拟合往往由于数据量不足或模型容量过大。可以通过**正则化、提前停止**等手段缓解。
    
-   具体数值上，SFT任务的loss一般会降到**1.x甚至0.x**（取决于token化方式和答案长度）。如果loss长时间停留在高位不降，说明模型没学会，这时需要检查学习率、数据问题等。
    

  
*图：示意 SFT 训练中训练集损失和验证集损失的典型变化趋势。前期二者都快速下降；在约第2轮迭代(Epoch 2)后，训练损失持续下降而验证损失开始回升，表明出现过拟合。实际曲线噪声会更大，但总体趋势类似。*

**（2）Epoch vs. 过拟合**：很多经验者提到一个现象：SFT训练到**第2个epoch左右**，验证loss往往就达到最低点，之后模型开始记忆训练数据导致验证loss上升[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=)。这是因为LLM参数量极大，**在第1个epoch**通常就已经把训练集大致记住了，第二遍再训练时训练loss会急剧下降，而验证loss不降反升。这意味着**过拟合在SFT中很容易发生**，通常不需要太多epoch。一些实践者甚至只跑**1个epoch**就停，以避免过拟合。当然这也依数据量而定，如果数据很少，一个epoch等于把每条都见过一次，那大模型可能已经记住不少了。

**（3）学不会 vs. 模型容量**：如果你尝试增加epoch，比如训练集反复训了10遍，但仍有某些case模型输出不对，那可能意味着**模型能力的限制**。正如有人调侃：“训10个epoch某些例子还不会，那说明模型能力就到这了”[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,packing%E7%9A%84%E6%96%B9%E5%BC%8F%E4%BC%9A%E5%BD%B1%E5%93%8D%E6%A8%A1%E5%9E%8B%E7%BB%AD%E5%86%99%E7%9A%84%E6%95%88%E6%9E%9C%EF%BC%8C%E5%9B%A0%E6%AD%A4%E4%BC%9A%E5%BD%B1%E5%93%8D%E4%B8%80%E4%BA%9Bbenchmark%E6%95%88%E6%9E%9C%E3%80%82%E4%BD%86%E5%9C%A8%E5%A4%A7%E6%89%B9%E9%87%8F%E6%95%B0%E6%8D%AE%E4%B8%8A%E6%98%AF%E6%97%A0%E6%8D%9F%E6%B3%9B%E5%8C%96%E6%95%88%E6%9E%9C%E7%9A%84%E3%80%82)。LLM毕竟参数有限，不是所有逻辑都能学会。如果验证集中一直错的那些样本，哪怕训练集类似样本也见过，模型依然错，那往往无论再训几遍都难以纠正。这时应考虑换更大模型或换策略（比如用思维链提示）。

**（4）学习率Warmup**：训练loss初期快速下降还有一点需要注意：很多训练配置会使用**学习率预热（warmup）**。即开始若干步逐渐提高学习率到目标值，再继续训练。Warmup目的是避免一开始大梯度破坏模型已有知识。采用warmup后，头几百步loss下降速度可能稍缓，然后加速下降。没有warmup时可能loss一开始跳降但偶尔震荡。总之，前期loss曲线可能有warmup造成的非线性，要了解配置对曲线的影响。

**（5）不收敛的情况**：如果发现loss在合理时间后不下降甚至发散，说明训练存在问题，可能是：

-   学习率过高：模型更新幅度太大，损失震荡甚至增大。这时尝试减小learning rate，或采用更小初始学习率热身。
    
-   数据不匹配：比如喂给模型格式完全不同的数据，会导致loss异常高且不降。这种情况要检查数据预处理是否正确。
    
-   实现Bug：常见如DataLoader没乱序、每个epoch重复相同顺序数据；或者多GPU时同步问题。需要仔细debug。
    
-   模型层不更新：如果用了PEFT，要确保 LoRA 等模块的参数 `requires_grad=True`。有时加载模型需要 `model.gradient_checkpointing_enable()` 等，不然模型算梯度时有问题。
    
-   优化器问题：比如全精度训练时显存不够，梯度被截断等。这些要结合具体log判断。
    

**（6）过拟合后的表现**：当验证loss升高，模型进入过拟合阶段，实际效果上会**倾向于重复训练集回答**而缺乏灵活性。还可能出现所谓**幻觉**问题变多，因为模型在训练集问题上学得太死板，面对新问题要么生搬硬套训练集答案，要么编造。如果检测到过拟合，应该**及时停止训练**并回滚模型到过拟合前的checkpoint。

概括来说，SFT 训练和一般深度学习训练类似，可以通过loss曲线观测学习动态。和普通任务不同的是，LLM非常容易过拟合，因为模型太大而数据相对有限。所以训练往往**不需要太多epoch**。最理想的是借助一个验证集（开发集）来决定**提前停止**（Early Stopping）时机：当验证loss连续若干评估上升，就停止并选最低点的模型作为最终模型[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=)。如果没有验证集，可以根据经验选择在第1~2个epoch保存的模型。有时候甚至第0.5个epoch（半个epoch）模型效果就已经不错了。

最后提一点，损失并不能完全代表最终应用效果。模型的语言输出质量需要用主观和其他指标评估。但loss曲线是训练阶段最直观的指标，密切关注它能帮助我们及时调整训练。

## SFT 过程中如何调整超参数？

成功的微调离不开对训练**超参数**的恰当设置和调整。以下是几个关键超参数及调参技巧：

**（1）学习率（Learning Rate）**：这是影响训练收敛和效果的头号因素。一般经验：

-   SFT初始学习率可设为**预训练阶段学习率的1/10**左右。因为预训练时常用较高lr以快速学习通用模式，而微调需要更小步伐以免破坏已有知识。
    
-   **模型参数量越大**，宜采用**越小的学习率**。大模型参数敏感，lr过大会导致输出震荡甚至严重损坏原有语言流畅性。小模型则可以尝试稍大lr迅速收敛。
    
-   可以采用**学习率预热**（warmup）和**衰减**策略。通常warmup几百步到峰值，然后线性或余弦衰减学习率有助于稳定收敛。
    
-   如果发现训练loss不下降或验证性能下降很快，可能lr过大，需要降低。很多人训练时会从一个lr开始试，如果过拟合严重就下调再训一次。**降低学习率**在一定程度上确实可以缓解过拟合，因为每步更新幅度小了，模型不会快速记住细节[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,packing%E7%9A%84%E6%96%B9%E5%BC%8F%E4%BC%9A%E5%BD%B1%E5%93%8D%E6%A8%A1%E5%9E%8B%E7%BB%AD%E5%86%99%E7%9A%84%E6%95%88%E6%9E%9C%EF%BC%8C%E5%9B%A0%E6%AD%A4%E4%BC%9A%E5%BD%B1%E5%93%8D%E4%B8%80%E4%BA%9Bbenchmark%E6%95%88%E6%9E%9C%E3%80%82%E4%BD%86%E5%9C%A8%E5%A4%A7%E6%89%B9%E9%87%8F%E6%95%B0%E6%8D%AE%E4%B8%8A%E6%98%AF%E6%97%A0%E6%8D%9F%E6%B3%9B%E5%8C%96%E6%95%88%E6%9E%9C%E7%9A%84%E3%80%82)。
    

**（2）批次大小（Batch Size）**：Batch越大，梯度估计越稳定，但也越占显存。可以采用**梯度累积**（Gradient Accumulation）的方法，实现\*\*“用小批多步累积成大批”**[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=%E4%BB%8Ecomplexity%E8%A7%92%E5%BA%A6%EF%BC%8C%E5%AF%B9%E4%BA%8Eprompt%E7%9B%B4%E6%8E%A5%E8%BF%9B%E8%A1%8C%E9%9A%BE%E5%BA%A6%E7%9A%84%E5%8D%87%E7%BA%A7%EF%BC%8C%E6%89%80%E4%BB%A5%E5%8D%B3%E4%BD%BF%E5%9C%A8%E5%90%8C%E4%B8%80%E4%B8%AA%E8%AF%AD%E6%84%8F%E7%A9%BA%E9%97%B4%E7%9A%84prompt%E4%B9%9F%E4%BC%9A%E5%8F%98%E5%BE%97diverse%E3%80%82%E6%AF%94%E8%BE%83%E8%91%97%E5%90%8D%E7%9A%84%E6%98%AFWizard%20%E6%96%B9%E6%B3%95%EF%BC%8C%E9%80%9A%E8%BF%87GPT4%E8%BF%9B%E8%A1%8Cprompt%E9%9A%BE%E5%BA%A6%E5%8D%87%E7%BA%A7%EF%BC%8C%E7%84%B6%E5%90%8E%E6%9E%84%E6%88%90complexity%E4%B8%B0%E5%AF%8C%E7%9A%84prompt%E3%80%82%20,3%20Answer%E7%9A%84%E8%B4%A8%E9%87%8F%EF%BC%9AAnswer%E7%9A%84%E8%B4%A8%E9%87%8F%E5%8C%85%E6%8B%AC%E5%86%85%E5%AE%B9%E5%92%8C%E6%A0%BC%E5%BC%8F%E4%B8%A4%E6%96%B9%E9%9D%A2%EF%BC%8C%E4%B8%80%E6%96%B9%E9%9D%A2%E5%86%85%E5%AE%B9%E7%9A%84%E6%AD%A3%E7%A1%AE%E6%80%A7%E9%9C%80%E8%A6%81%E5%BE%97%E5%88%B0%E4%BF%9D%E8%AF%81%EF%BC%8C%E4%B8%80%E6%96%B9%E9%9D%A2%E5%86%85%E5%AE%B9%E7%9A%84%E6%A0%BC%E5%BC%8F%E4%B9%9F%E5%BE%88%E9%87%8D%E8%A6%81%EF%BC%8C%E7%BB%86%E8%8A%82%E4%B8%B0%E5%AF%8C%EF%BC%8C%E9%80%BB%E8%BE%91%E7%BC%9C%E5%AF%86%E7%9A%84answe)。例如显存只能放下8条样本，那累积4步再更新，相当于32条样本的有效batch。适当的batch可以加速训练和提高效果。一般**越大的batch\*\*对结果越有利（尤其在预训练中很重要），但SFT数据本来就不算特别多，所以不用太过追求超大batch，保证loss平稳下降就行。可以尝试的累积步数有16、32、64等，看显存和效果调节[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=%E4%BB%8Ecomplexity%E8%A7%92%E5%BA%A6%EF%BC%8C%E5%AF%B9%E4%BA%8Eprompt%E7%9B%B4%E6%8E%A5%E8%BF%9B%E8%A1%8C%E9%9A%BE%E5%BA%A6%E7%9A%84%E5%8D%87%E7%BA%A7%EF%BC%8C%E6%89%80%E4%BB%A5%E5%8D%B3%E4%BD%BF%E5%9C%A8%E5%90%8C%E4%B8%80%E4%B8%AA%E8%AF%AD%E6%84%8F%E7%A9%BA%E9%97%B4%E7%9A%84prompt%E4%B9%9F%E4%BC%9A%E5%8F%98%E5%BE%97diverse%E3%80%82%E6%AF%94%E8%BE%83%E8%91%97%E5%90%8D%E7%9A%84%E6%98%AFWizard%20%E6%96%B9%E6%B3%95%EF%BC%8C%E9%80%9A%E8%BF%87GPT4%E8%BF%9B%E8%A1%8Cprompt%E9%9A%BE%E5%BA%A6%E5%8D%87%E7%BA%A7%EF%BC%8C%E7%84%B6%E5%90%8E%E6%9E%84%E6%88%90complexity%E4%B8%B0%E5%AF%8C%E7%9A%84prompt%E3%80%82%20,3%20Answer%E7%9A%84%E8%B4%A8%E9%87%8F%EF%BC%9AAnswer%E7%9A%84%E8%B4%A8%E9%87%8F%E5%8C%85%E6%8B%AC%E5%86%85%E5%AE%B9%E5%92%8C%E6%A0%BC%E5%BC%8F%E4%B8%A4%E6%96%B9%E9%9D%A2%EF%BC%8C%E4%B8%80%E6%96%B9%E9%9D%A2%E5%86%85%E5%AE%B9%E7%9A%84%E6%AD%A3%E7%A1%AE%E6%80%A7%E9%9C%80%E8%A6%81%E5%BE%97%E5%88%B0%E4%BF%9D%E8%AF%81%EF%BC%8C%E4%B8%80%E6%96%B9%E9%9D%A2%E5%86%85%E5%AE%B9%E7%9A%84%E6%A0%BC%E5%BC%8F%E4%B9%9F%E5%BE%88%E9%87%8D%E8%A6%81%EF%BC%8C%E7%BB%86%E8%8A%82%E4%B8%B0%E5%AF%8C%EF%BC%8C%E9%80%BB%E8%BE%91%E7%BC%9C%E5%AF%86%E7%9A%84answe)。

**（3）Epoch 数**：前面提过，SFT往往用**1到3个epoch**就够。**数据量越大**，需要的epoch越少。极端来说如果有10万数据，1个epoch模型就学得不错了，再多可能开始过拟合。而数据少（如2000条），或许可以训到3~5个epoch才过拟合。总之 epoch 是和数据量成反比的。调参时可以先取一个稍大的epoch上限，然后每个epoch评估验证loss，观察何时开始上升，即停训。很多人喜欢2个epoch左右保存最优模型。

**（4）正则化**：SFT有时也需要正则化手段来防止过拟合。常用有：

-   **Dropout**：在模型训练中随机丢弃部分神经元。Transformer结构里本身有dropout，在SFT可以调高或调低dropout率。如过拟合严重可考虑**适当增大 dropout**。不过大模型训练dropout影响较小，一般预训练时怎么设SFT就沿用即可。
    
-   **权重衰减（L2正则）**：通过给优化器设置weight\_decay，对模型权重增加一个L2损失项。SFT时这个值不宜太大，否则会抑制模型学习。通常用一个很小的weight\_decay或者干脆0。
    
-   **梯度裁剪**：以防止偶尔梯度爆炸导致更新过大，一般设置一个最大梯度范数，如1.0或0.5。
    

**（5）检查点选择**：训练过程中可以设置定期保存checkpoint，如每隔若干steps保存一次。最终选择哪个checkpoint作为成品模型，需要考量**欠拟合 vs 过拟合**。理想是基于验证集指标选。若无验证集，可以根据经验：通常**在过拟合前刚开始的点**性能最佳。例如如果发现第2个epoch过后模型开始过拟合，那第2个epoch结束或略早的checkpoint可能是最好模型。还有些人采用**平均权重**的方法（SWAD之类），不过较少用于LLM微调。

**（6）学习率调度**：可以尝试不同**lr\_scheduler**策略：线性衰减、余弦退火、多步下降等[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=%E4%BB%8Ecomplexity%E8%A7%92%E5%BA%A6%EF%BC%8C%E5%AF%B9%E4%BA%8Eprompt%E7%9B%B4%E6%8E%A5%E8%BF%9B%E8%A1%8C%E9%9A%BE%E5%BA%A6%E7%9A%84%E5%8D%87%E7%BA%A7%EF%BC%8C%E6%89%80%E4%BB%A5%E5%8D%B3%E4%BD%BF%E5%9C%A8%E5%90%8C%E4%B8%80%E4%B8%AA%E8%AF%AD%E6%84%8F%E7%A9%BA%E9%97%B4%E7%9A%84prompt%E4%B9%9F%E4%BC%9A%E5%8F%98%E5%BE%97diverse%E3%80%82%E6%AF%94%E8%BE%83%E8%91%97%E5%90%8D%E7%9A%84%E6%98%AFWizard%20%E6%96%B9%E6%B3%95%EF%BC%8C%E9%80%9A%E8%BF%87GPT4%E8%BF%9B%E8%A1%8Cprompt%E9%9A%BE%E5%BA%A6%E5%8D%87%E7%BA%A7%EF%BC%8C%E7%84%B6%E5%90%8E%E6%9E%84%E6%88%90complexity%E4%B8%B0%E5%AF%8C%E7%9A%84prompt%E3%80%82%20,3%20Answer%E7%9A%84%E8%B4%A8%E9%87%8F%EF%BC%9AAnswer%E7%9A%84%E8%B4%A8%E9%87%8F%E5%8C%85%E6%8B%AC%E5%86%85%E5%AE%B9%E5%92%8C%E6%A0%BC%E5%BC%8F%E4%B8%A4%E6%96%B9%E9%9D%A2%EF%BC%8C%E4%B8%80%E6%96%B9%E9%9D%A2%E5%86%85%E5%AE%B9%E7%9A%84%E6%AD%A3%E7%A1%AE%E6%80%A7%E9%9C%80%E8%A6%81%E5%BE%97%E5%88%B0%E4%BF%9D%E8%AF%81%EF%BC%8C%E4%B8%80%E6%96%B9%E9%9D%A2%E5%86%85%E5%AE%B9%E7%9A%84%E6%A0%BC%E5%BC%8F%E4%B9%9F%E5%BE%88%E9%87%8D%E8%A6%81%EF%BC%8C%E7%BB%86%E8%8A%82%E4%B8%B0%E5%AF%8C%EF%BC%8C%E9%80%BB%E8%BE%91%E7%BC%9C%E5%AF%86%E7%9A%84answe)。线性衰减到0是一种稳定方案。余弦调度让lr前期大幅下降后期平稳，可能更好保持模型状态。具体哪个好需要实验。对大模型微调，很多人直接用线性warmup+线性衰减比较保险。

**（7）混合精度**：使用 FP16/BF16 训练需要注意loss缩放（PyTorch会自动GradScaler）。一般SFT没有预训练那么长，不太遇到数值溢出，但也要确保loss不要出现NaN。如果出现NaN，可以降低初始lr或禁用grad scaler试试。此外 BF16在新GPU上用，可以免去手动loss scale。

**（8）分层微调**：一种更高级的调参是**不同层用不同学习率**（layer-wise LR decay）。就是让模型高层lr大，底层lr小，避免底层embedding被大改动。这对预训练很重要，对微调也可尝试。如果SFT发现模型倾向遗忘基础知识，可以考虑冻结embedding或前几层，仅调后面层。但这样要有一定经验和实验支持，普通情况下不需用到。

总之，**调参的核心思想是：以尽可能小的改动达成足够的学习**。SFT希望模型学会新任务但又不破坏原有能力，所以lr、epoch都不能太激进。常规配置比如：“lr=1e-4，batch=32（或累积达到32），epoch=2，warmup=100 steps，线性decay到0”是比较常见的起点。如果发现**欠拟合**（表现为训练loss都还高，验证loss也高，模型明显没学会），可以**增加epoch或lr**；如果**过拟合**（训练loss低但验证loss升），就**减少epoch**或**降低lr**，也可以尝试**数据增强**。每个任务不同，调参需要一些反复试验，结合loss曲线和实际输出质量来判断。

### 实例：一些超参数常用值

-   微调ChatGPT等指令遵循模型：lr通常1e-5到2e-5（模型大），小模型可用1e-4。
    
-   epoch通常2。如果数据>1万条，可能1 epoch就够。数据<5000条，可尝试3-5 epoch但留意过拟合。
    
-   batch按显存最大来，小模型32-64，大模型8-16，然后用accumulation扩充。
    
-   warmup步骤=总训练steps的 2%~5%是一种设置，也有人固定100或500步warmup。
    
-   LR scheduler很多人用**cosine退火**到一定最小值（如0），表现平稳，也容易配置。
    

**Tips**：调参最好**一次只改一两个**超参数，观察影响，再决定下步。这跟普通机器学习调参类似。可以先粗调确定量级，再细调微优化。例如先二分法找到合适lr范围，再在范围内grid search微调。由于LLM训练成本高，能跑的实验有限，所以要有经验指导和监控判断，必要时借助**小规模试验**（比如用小一号模型或截断数据测试一轮）验证趋势。

## 如何评价 SFT 后模型的效果？

当 SFT 训练完成后，需要评价模型的表现。这通常包含**客观指标**和**主观评估**两方面：

**（1）主观评估**：根据实际产品需求，检验模型是否达到预期：

-   **功能达成度**：模型能否正确执行任务？例如如果微调目标是对话，拿一组代表性聊天测试模型是否礼貌、有用；如果是分类器，就看它对样例分类是否准确。
    
-   **响应品质**：人工与模型交互，主观判断回答是否流畅、合理、有无明显错误或不当内容。通常由项目团队或标注员对一批测试问答进行打分或写评语。可以设定一些**评价标准**（如相关性、准确性、简洁性、多样性等）给每项打分，综合衡量。
    
-   **与预期行为比较**：列出微调希望达到的**目标**，比如“对于敏感话题要拒答”，“对于事实型问题引用准确信息”等，然后实际测试这些点看模型是否达标。如果某些方面不达标，就分析训练数据是否覆盖，或者需要额外调整（可能通过RLHF再调）。
    

主观评估非常重要，尤其在**对话系统**中，人们更看重模型回答是否让人满意。这部分需要评估者对任务有深刻理解，也可以对比微调前后的模型差异，看SFT带来了哪些改进。

**（2）客观指标**：虽然语言任务有些指标很难量化，但我们仍有一些客观手段：

-   **Loss曲线**：最基本的是看**训练和验证loss**。训练loss下降表明模型成功学习了模式。验证loss若有，也可以作为泛化性能参考。通常我们希望最终验证loss相比微调前明显降低。若验证loss降幅很小，说明SFT效果有限；降幅大但后来升高，说明过拟合，需要折中选择checkpoint。
    
-   **任务特定指标**：如果SFT任务有明确评价指标，就可以计算。如**准确率**（用于分类任务）、**BLEU/ROUGE**（用于翻译/摘要任务）等。如果有标准答案，可以计算**准确率、召回率、F1**等。对话系统可以有人机对话然后看**用户满意度**调查之类，不过这又回到主观评估了。
    
-   **基准测试（Benchmark）**：在开源领域，经常会在一些公共数据集上评测模型，如TruthfulQA、MMLU、HellaSwag等NLP任务，看微调模型的成绩。这有助于了解模型综合能力是否下降或提升。例如有报告指出，SFT 虽让模型在特定领域进步，但通用知识问答成绩可能下降[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=,labeled%20datasets%20can%20be%20time)。通过benchmark比较，可以量化这种**能力漂移**。
    
-   **模型输出长度、速率**：一些指标如**平均输出长度**，**重复率**等可以自动计算。如果微调目标包含这些要求（如不要啰嗦重复），就能对比微调前后这些指标变化。
    

**（3）AB测试**：如果可能，可以让多人对**微调前 vs. 微调后**模型的回答做盲测对比，统计胜率。这类似OpenAI做InstructGPT时，用人类评价新模型回答相对于旧模型的优选率[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=Empirically%2C%20RLHF%20improves%20performance%20significantly,2022)。比如给若干相同问题，让微调模型和未微调模型回答，然后请评审员选择哪个更好。如果微调有效，应该有较高比例的回答被认为优于原模型[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=To%20train%20a%20model%20to,approach%20produces%20much%20superior%20results)。

**（4）上线监控**：最终还是要看模型在真实环境中的表现。可以灰度上线SFT模型一段时间，观察**用户反馈**和**错误案例**，比如看用户是否对答案满意度提升，模型是否犯新的错误。通过收集这些实际交互数据，再决定是否需要进一步微调或调整策略。

需要注意，**SFT模型不可能完美**。评估的目的是确认它是否**达到了可以接受的水平**。主观和客观结合可以较全面地把握：客观指标保证模型在已有数据上的表现，而主观评估关注模型对未知问题的处理。两者都达标，才能认为微调成功。

如果评估发现问题，比如模型虽然在领域问题上很棒但对通识问题变差，这时就要考虑怎么优化：可能需要在训练数据中加入一定比例的通用指令数据，以免模型遗忘通识（即**数据配比**技巧）；或者采用PEFT来减少对原模型的改动幅度等等。

最后，评估也是一个**循环过程**的一环：评估->发现不足->改进数据/参数->再训练->再评估，直到满意为止。所以要有持续评测的机制，尤其在模型上线后也持续监控，保证模型质量稳中有升。

## SFT 带来哪些潜在问题？如何避免？

尽管 SFT 能提升特定能力，但也会产生一些**不良后果**需要注意：

**（1）通用能力下降**：模型在微调领域表现提升的同时，可能**遗忘**部分预训练学到的通用知识和技能[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=%2A%20Limited%20Generalization%3A%C2%A0Once%20fine,labeled%20datasets%20can%20be%20time)。这就是\*\*“大模型遗忘”**问题，又称**“对齐税”**（alignment tax）：为了让模型对齐人类要求，可能牺牲了一些原本的能力。例如，一个聊天AI微调后更安全了，但创造力下降了；又如微调成金融问答专家后，它可能无法再正确回答医学问题。这个现象在SFT和RLHF后都观察到。**如何缓解**？一个常用方法是**混合训练数据\*\*：在SFT数据集中**加入一部分通用数据**或原预训练任务的数据，让模型在学习新任务时也复习旧知识。比如对一个医学QA模型SFT时，加一些日常闲聊问答的数据，以保持它的闲聊能力。或者微调训练末期，来一点原始网络语料让它记起之前知识。这类似**多任务学习**防止单一任务学偏。当然，加通用数据要慎重拿捏比例，太多会削弱主要任务效果。另一个思路是采用**较小学习率**或**PEFT**，不让模型权重大幅变化，这样基础能力保留更多[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=as%20full%20fine,rank)。

**（2）过拟合与幻觉**：SFT数据通常量不大，而且内容相对集中，模型极易过拟合训练集。过拟合不仅体现在验证loss升高，还体现在模型倾向于**照搬训练集回答**或者在类似问题上**编造**（幻觉）[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=)。例如训练集中某问题答案有个小错误，模型微调后可能把这个错误学得很牢，一遇到相关问题就重复这个谬误。这就会产生我们常说的**幻觉**（Hallucination）：模型信心满满地输出与事实矛盾的内容。**避免方法**：

-   **严格数据审核**，保证训练答案里没有错误或自相矛盾的信息。如果发现模型老在某知识上出错，去看训练数据是否提供了错误示范或者根本没提供正确示范。
    
-   **使用PEFT**或**正则**降低模型对训练集的记忆强度。如果全参数微调导致幻觉增多，可以尝试 LoRA 方式，这样模型保留原知识，不会一股脑用新小数据覆盖全部权重，幻觉可能减少[arxiv.org](https://arxiv.org/html/2410.21228v1#:~:text=LoRA%20vs%20Full%20Fine,2024%29%20and)。
    
-   **加入检索或工具**：这个是模型应用层面的。对于容易幻觉的领域（如实时信息）可以在SFT基础上再集成RAG，让模型别靠记忆瞎猜。或者教模型使用计算工具（通过在SFT数据加入要求它不会算就调用计算器的示例）。
    
-   **惩罚不确定输出**：在RLHF阶段往往会引入机制让模型学会说“我不确定”“我不知道”。纯SFT阶段模型不会拒答，这也是幻觉产生因素。可以**在数据中加入少量拒答示例**，对于模型不该乱答的问题给出“抱歉我无法提供信息”的正确输出，引导模型遇到不懂的学会拒绝。
    

**（3）模型输出多样性降低**：SFT倾向让模型**背训练答案**，因此回答可能变死板。不微调的大模型可能给出五花八门的表述，而微调后统一成一种腔调。比如未经调教的GPT-3回答可以有创造性的扮演角色，SFT对齐后都变成客服式口吻。这在一些场景下算副作用，如何缓解？可以在训练数据中**提供风格多样的示例**，鼓励模型保留一定创造性。另外也可在使用时通过**Prompt技巧**让模型输出丰富些，比如提示“换个说法回答”。

**（4）数据偏差引入**：SFT数据如果偏向某种观点、群体，模型可能学到相应偏见。比如训练数据里某类用户总是刁难AI，那模型可能对某些问题误判为攻击而反应过激。**避免**的方法是**多元化数据**，并对内容偏见做检查。也可以在RLHF阶段专门让人检查模型有无歧视性输出等。

**（5）计算性能影响**：SFT后模型体积通常不变，但如果加入了思维链等，**推理时可能更慢**，因为模型倾向于先输出一大段推理过程再答。这其实不是模型内在性能变差，而是**输出token变多**。应对方法可以是在使用时通过prompt或参数约束控制模型简明回答。另外SFT模型往往**更遵守格式**，所以有时推理可以更快结束（因为遇到特定stop符号就停止）。但总的来说，SFT对推理速度的负面影响不大，可通过调节**max tokens**等参数控制[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=%2A%20Prefill%20is%20a%20one,the%20prefill%20overhead%20might%20dominate)。

归纳来说，**SFT是一把双刃剑**：强化特定能力可能带来其他方面能力的削弱。我们需要通过精心的训练方案和数据设计，将负面效应降到最低。训练中多观察，多用多样化的验证场景测试模型，就是为了及时发现这些副作用。如果发现，通常可以通过**调整数据集**组成或**改变微调策略**来补救。例如有团队在微调末期再用少量原始任务数据fine-tune一下模型，起到\*\*“复习旧知识”\*\*的作用，缓解遗忘。在开发闭环中不断权衡取舍，才能获得性能和安全性均衡的模型。

## 如何评估 SFT 模型的推理速度？

SFT模型在推理（Inference）阶段的性能也值得关注。一般来说，微调不会改变模型架构，因此**单步计算的复杂度不变**，但SFT可能影响输出token的数目和生成方式，从而影响**整体响应时间**。

一个简单模型：**生成总耗时 ≈ T<sub>prefill</sub> + T<sub>decode</sub>**。其中 T<sub>prefill</sub> 是处理提示（prompt）的时间，T<sub>decode</sub> 是逐字生成输出的时间。更具体地，有经验之谈：**模型的预测延迟近似可以理解为 `b + k * x`**[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=%2A%20Prefill%20is%20a%20one,the%20prefill%20overhead%20might%20dominate)：

-   `b` 是**首个token的耗时**，包括处理整个prompt和输出第一个字的时间。这个通常是最耗时的，一旦首token出得慢，后面整体延迟也高。`b` 跟prompt长度密切相关[docs.nvidia.com](https://docs.nvidia.com/nim/benchmarking/llm/latest/metrics.html#:~:text=Time%20to%20first%20token%20generally,prompt%2C%20the%20larger%20the%20TTFT)——prompt越长，首token时间越久，因为模型需要把prompt全部“看”一遍形成初始缓存。
    
-   `k` 是**每个后续token的耗时**，相对稳定，大致取决于模型大小、硬件性能。一般大模型k大，小模型k小。`x` 则是**生成token的总数量**。
    
-   `b` 通常是 `k` 的十几倍或更多[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=%2A%20Prefill%20is%20a%20one,the%20prefill%20overhead%20might%20dominate)。也就是说，光是输出第一个字，模型可能花费相当于后面十几个字的计算。这是因为首token需要计算prompt全长的Transformer层，而后续token借助**KV-cache**（键值缓存）机制，每生成一个新token只需计算新增的一步，而前面已有的不用重复算[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=%2A%20Prefill%20is%20a%20one,the%20prefill%20overhead%20might%20dominate)。
    

因此，**推理总时间大致正比于 prompt长度 + 生成长度**。这意味着：

-   **长prompt**（比如用户提供了上千字符的上下文）会显著增加首token延迟。如果应用场景prompt长，要考虑使用**检索+精简**等策略减少进入模型的文本长度。
    
-   **输出长度**直接线性增加时间。**CoT**方法让模型\*\*“想一步写一步”\*\*输出大量推理文字，当然能提高准确率，但也使得生成的token数成倍上升，速度变慢[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=%2A%20Prefill%20is%20a%20one,the%20prefill%20overhead%20might%20dominate)。这也是为什么大家知道CoT效果好却很矛盾——生成100字的逐步推理再给答案，和直接输出一句答案相比，速度慢了许多。对于有严格延迟要求的应用，就很少允许CoT式超长回答。
    
-   **批处理**：如果一次推理并行处理多个请求（batch推理），那么可以摊薄一定的开销，但过大batch也会降低单条速度。这是服务部署层面的优化，不展开。
    

SFT本身怎么影响这些呢？

-   SFT后的模型更遵循格式，或许会**更早地输出终止符**（EOS）。比如训练数据教模型回答完毕要输出`<|endoftext|>`，模型学会及时结束，不会胡乱自说自话，这可以减少无谓的token生成。但前提是你在推理设置了合适的**停止条件**，否则模型可能还是继续。
    
-   如果SFT数据包含大量**冗长解释**（如都给出了详细过程），模型也倾向于长回答。这会增加输出长度x。可以通过**调整temperature或提示**让它简洁一点。
    
-   SFT不会改变模型基本推理效率，但**使用PEFT**可能略有影响（因为多了一些矩阵计算合并），不过这个几乎可以忽略，相比整体计算量九牛一毛。
    

为了**量化**推理速度，可以测算**Token per second**指标：比如每秒模型输出多少token。也可记录**Time to First Token (TTFT)**和**Time per Token**[developer.nvidia.com](https://developer.nvidia.com/blog/llm-benchmarking-fundamental-concepts/#:~:text=Diagram%20showing%20LLM%20metrics%20including,TPOT)。TTFT对应上文的b，每个token时间对应k。监控这些指标可帮助优化服务。

一个值得注意的技巧是**KV Cache**：Transformer在生成时会缓存前面步骤的Key/Value投影向量，后续生成利用缓存大幅减少计算[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=Key)[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=Latency%20vs)。现代LLM实现都会自动用cache，所以一般后续token计算量是固定的，不随上下文长度增加。**但是**第一步算cache的时间随上下文线性增加[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=Latency%20vs)。因此对**超长上下文**（几千token）的问题，如果需要提升速度，可以考虑**模型裁剪**或者**检索摘要**以减少输入长度。

还有一点，**并行解码** vs. **顺序解码**：由于生成是自回归的，无法全并行。可以做的是使用**多线程/多进程**处理不同请求。但对单一请求，没法并行出token。这是语言模型的基本限制。不过像**Speculative Decoding**等算法可以用一个小模型并发预测以加速，但这些属于研究前沿。

总结来说，SFT模型推理时间基本与原模型一致，**主要关心输入输出token数量**。我们用公式**Time ≈ b + k\*x**来估算延迟[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=%2A%20Prefill%20is%20a%20one,the%20prefill%20overhead%20might%20dominate)。所以要加快响应：

-   控制prompt长度（必要时简化用户输入或索引所需部分）。
    
-   控制输出长度（可通过**max\_length**参数或引导模型简洁回答）。
    
-   使用更快的模型架构或硬件（这不是SFT范畴，但像采用INT8量化模型推理也能提速，只是要注意和LoRA结合的问题前述）。
    
-   批处理多个请求如果流量大，也能提高**吞吐**（不是单条延迟，但优化服务器整体TPS）。
    

最后，可以写个脚本测试SFT模型在一些典型输入下的响应时间，和微调前作比较，确保微调没有导致意外的效率问题。通常只要微调没乱改模型结构，**差别主要来自文本长度**。因此精心设计交互，达到**效率与效果的平衡**是应用层该考虑的事。

## 什么是 SFT Packing？

在准备SFT训练数据时，有一个技巧叫 **SFT Packing**。它指在训练时将**多个独立的SFT样本**拼接在**同一个序列**里进行训练[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=SFT%20packing%20%E6%8C%87%E8%AE%AD%E7%BB%83sft%E8%BF%87%E7%A8%8B%E4%B8%AD%EF%BC%8C%E5%B0%86%20%E5%A4%9A%E4%B8%AAsft%E6%95%B0%E6%8D%AEpack%E5%88%B0%E4%B8%80%E4%B8%AA%E6%A0%B7%E6%9C%AC%E5%86%85%20%E8%BF%9B%E8%A1%8C%E8%AE%AD%E7%BB%83)。简单说，就是\*\*“打包训练”**：本来一条训练样本可能只占用几十个token，如果每条分别训练，计算时需要padding到batch中最长长度，造成大量填充浪费。Packing 做法是把几条短样本**首尾相连\*\*组成一个长序列作为一个训练样本，这样显卡算一个长序列就涵盖了原本多个短对话，有效利用每个token的计算[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=SFT%20packing%20%E6%8C%87%E8%AE%AD%E7%BB%83sft%E8%BF%87%E7%A8%8B%E4%B8%AD%EF%BC%8C%E5%B0%86%20%E5%A4%9A%E4%B8%AAsft%E6%95%B0%E6%8D%AEpack%E5%88%B0%E4%B8%80%E4%B8%AA%E6%A0%B7%E6%9C%AC%E5%86%85%20%E8%BF%9B%E8%A1%8C%E8%AE%AD%E7%BB%83)。

**SFT Packing 的优点**：主要是**提高GPU利用率，减少padding浪费**[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=SFT%20packing%20%E6%8C%87%E8%AE%AD%E7%BB%83sft%E8%BF%87%E7%A8%8B%E4%B8%AD%EF%BC%8C%E5%B0%86%20%E5%A4%9A%E4%B8%AAsft%E6%95%B0%E6%8D%AEpack%E5%88%B0%E4%B8%80%E4%B8%AA%E6%A0%B7%E6%9C%AC%E5%86%85%20%E8%BF%9B%E8%A1%8C%E8%AE%AD%E7%BB%83)。对于大量短对话的数据集，使用Packing可以显著提高“有效训练token/总计算token”的比例，进而加快训练进程。因为Transformer的并行操作按序列最大长度来，padding token也是白算的。如果不packing，一个batch里可能只有少部分样本长度接近max，其余都在pad。而packing让大部分计算token都是实际数据。实验表明，在小样本短序列场景，Packing可以提升训练速度，可能**更快收敛**（每步覆盖样本数更多）。

**Packing的实现**：通常需要对数据进行**离线预处理**，将若干段对话concat起来，中间用特殊分隔符隔开（如 `<|endoftext|>` 表示一句话结束）。还需相应调整**attention mask**让模型不会跨样本attend[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,block%20diagonal%20attention%2C%20%E6%AF%8F%E4%B8%AAtoken%E4%BB%85%E4%BB%85%E5%8E%BBattention%E8%87%AA%E5%B7%B1%E7%9A%84%E9%97%AE%E9%A2%98%E5%86%85%E7%9A%84token%E3%80%82%E4%BD%86%E4%B8%80%E8%88%AC%E4%B8%9A%E5%8A%A1%E4%B8%AD%E4%BC%9A%E7%9B%B4%E6%8E%A5%E5%B0%86%E5%85%B6%E7%9B%B8%E8%BF%9E%E6%8E%A5%EF%BC%8C%E7%84%B6%E5%90%8E%E8%BF%9B%E8%A1%8C%E9%A2%84%E6%B5%8B%EF%BC%8C%E8%99%BD%E7%84%B6%E8%BF%99%E6%A0%B7%E4%BC%9A%E5%BC%95%E5%85%A5%E4%B8%80%E4%BA%9B%E5%99%AA%E9%9F%B3%EF%BC%8C%E4%BD%86%E5%A5%BD%E5%83%8F%E7%9B%B8%E5%AF%B9%E4%BA%8E%E9%9D%9Esft%20packing%E6%96%B9%E5%BC%8F%E7%9A%84%E6%95%B4%E4%BD%93%E7%9A%84%E6%95%88%E6%9E%9C%E6%8D%9F%E5%A4%B1%E4%B8%8D%E5%A4%A7%E3%80%82%E8%BF%99%E4%B8%AA%E5%8F%AF%E8%83%BD%E6%98%AF%E5%9B%A0%E4%B8%BApretrain%E7%9A%84%E6%97%B6%E5%80%99%E6%A8%A1%E5%9E%8B%E4%B9%9F%E6%98%AF%E8%BF%99%E4%B9%88%E8%AE%AD%E7%BB%83%E7%9A%84%E3%80%82)。有的实现甚至使用**Block Diagonal Attention**技术，让模型注意力矩阵在不同样本间为0，完全隔离样本[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,block%20diagonal%20attention%2C%20%E6%AF%8F%E4%B8%AAtoken%E4%BB%85%E4%BB%85%E5%8E%BBattention%E8%87%AA%E5%B7%B1%E7%9A%84%E9%97%AE%E9%A2%98%E5%86%85%E7%9A%84token%E3%80%82%E4%BD%86%E4%B8%80%E8%88%AC%E4%B8%9A%E5%8A%A1%E4%B8%AD%E4%BC%9A%E7%9B%B4%E6%8E%A5%E5%B0%86%E5%85%B6%E7%9B%B8%E8%BF%9E%E6%8E%A5%EF%BC%8C%E7%84%B6%E5%90%8E%E8%BF%9B%E8%A1%8C%E9%A2%84%E6%B5%8B%EF%BC%8C%E8%99%BD%E7%84%B6%E8%BF%99%E6%A0%B7%E4%BC%9A%E5%BC%95%E5%85%A5%E4%B8%80%E4%BA%9B%E5%99%AA%E9%9F%B3%EF%BC%8C%E4%BD%86%E5%A5%BD%E5%83%8F%E7%9B%B8%E5%AF%B9%E4%BA%8E%E9%9D%9Esft%20packing%E6%96%B9%E5%BC%8F%E7%9A%84%E6%95%B4%E4%BD%93%E7%9A%84%E6%95%88%E6%9E%9C%E6%8D%9F%E5%A4%B1%E4%B8%8D%E5%A4%A7%E3%80%82%E8%BF%99%E4%B8%AA%E5%8F%AF%E8%83%BD%E6%98%AF%E5%9B%A0%E4%B8%BApretrain%E7%9A%84%E6%97%B6%E5%80%99%E6%A8%A1%E5%9E%8B%E4%B9%9F%E6%98%AF%E8%BF%99%E4%B9%88%E8%AE%AD%E7%BB%83%E7%9A%84%E3%80%82)。如果不做复杂处理，直接简单拼接，其实Transformer自带的序列建模可能隐含也能学到每段开头结尾，但会引入一点**噪声**：模型可能模糊两个拼接问答的界限。不过实践发现，如果加上合理分隔符，这点噪声对最后效果影响不大，**因为预训练时模型就经常读长文本，包括拼接的内容**[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,block%20diagonal%20attention%2C%20%E6%AF%8F%E4%B8%AAtoken%E4%BB%85%E4%BB%85%E5%8E%BBattention%E8%87%AA%E5%B7%B1%E7%9A%84%E9%97%AE%E9%A2%98%E5%86%85%E7%9A%84token%E3%80%82%E4%BD%86%E4%B8%80%E8%88%AC%E4%B8%9A%E5%8A%A1%E4%B8%AD%E4%BC%9A%E7%9B%B4%E6%8E%A5%E5%B0%86%E5%85%B6%E7%9B%B8%E8%BF%9E%E6%8E%A5%EF%BC%8C%E7%84%B6%E5%90%8E%E8%BF%9B%E8%A1%8C%E9%A2%84%E6%B5%8B%EF%BC%8C%E8%99%BD%E7%84%B6%E8%BF%99%E6%A0%B7%E4%BC%9A%E5%BC%95%E5%85%A5%E4%B8%80%E4%BA%9B%E5%99%AA%E9%9F%B3%EF%BC%8C%E4%BD%86%E5%A5%BD%E5%83%8F%E7%9B%B8%E5%AF%B9%E4%BA%8E%E9%9D%9Esft%20packing%E6%96%B9%E5%BC%8F%E7%9A%84%E6%95%B4%E4%BD%93%E7%9A%84%E6%95%88%E6%9E%9C%E6%8D%9F%E5%A4%B1%E4%B8%8D%E5%A4%A7%E3%80%82%E8%BF%99%E4%B8%AA%E5%8F%AF%E8%83%BD%E6%98%AF%E5%9B%A0%E4%B8%BApretrain%E7%9A%84%E6%97%B6%E5%80%99%E6%A8%A1%E5%9E%8B%E4%B9%9F%E6%98%AF%E8%BF%99%E4%B9%88%E8%AE%AD%E7%BB%83%E7%9A%84%E3%80%82)。

**Packing 的缺点**：它对**样本独立性要求高**，不适用于多轮对话这种**上下文有强依赖**的情况[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=SFT%20packing%20%E6%8C%87%E8%AE%AD%E7%BB%83sft%E8%BF%87%E7%A8%8B%E4%B8%AD%EF%BC%8C%E5%B0%86%20%E5%A4%9A%E4%B8%AAsft%E6%95%B0%E6%8D%AEpack%E5%88%B0%E4%B8%80%E4%B8%AA%E6%A0%B7%E6%9C%AC%E5%86%85%20%E8%BF%9B%E8%A1%8C%E8%AE%AD%E7%BB%83)。例如多轮对话数据如果被拆开组合，模型可能混淆前后轮次关系。另外packing会导致**短样本的梯度被稀释**：比如原本一个batch有一条很短的问答，它梯度占据整个batch，现在packing把它跟别的拼一起，它的loss只占整个loss一部分，更新方向更多被别的长样本主导。这可能**削弱模型对某些短QA的记忆**[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=)。有研究者指出，packing后模型对**那些难的短query**拟合能力变弱了，因为原本短query独占一个batch梯度很大，现在被摊薄[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=)。不过他们也发现，这种拟合能力降低**未必意味着泛化变差**，可能模型不会过度记忆那个短例子反而泛化更好[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,packing%E7%9A%84%E6%96%B9%E5%BC%8F%E4%BC%9A%E5%BD%B1%E5%93%8D%E6%A8%A1%E5%9E%8B%E7%BB%AD%E5%86%99%E7%9A%84%E6%95%88%E6%9E%9C%EF%BC%8C%E5%9B%A0%E6%AD%A4%E4%BC%9A%E5%BD%B1%E5%93%8D%E4%B8%80%E4%BA%9Bbenchmark%E6%95%88%E6%9E%9C%E3%80%82%E4%BD%86%E5%9C%A8%E5%A4%A7%E6%89%B9%E9%87%8F%E6%95%B0%E6%8D%AE%E4%B8%8A%E6%98%AF%E6%97%A0%E6%8D%9F%E6%B3%9B%E5%8C%96%E6%95%88%E6%9E%9C%E7%9A%84%E3%80%82)。

**是否使用 Packing**：要具体权衡：

-   如果你的数据都是**单轮简短指令**且量大，用Packing基本无害且能加速，可考虑使用。
    
-   如果有**很多多轮对话**或**需要严格order**的场景，最好对每条对话单独训练，不要packing混杂，避免逻辑串扰。
    
-   在数据量较小时，packing可能反而有损效果[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,packing%E7%9A%84%E6%96%B9%E5%BC%8F%E4%BC%9A%E5%BD%B1%E5%93%8D%E6%A8%A1%E5%9E%8B%E7%BB%AD%E5%86%99%E7%9A%84%E6%95%88%E6%9E%9C%EF%BC%8C%E5%9B%A0%E6%AD%A4%E4%BC%9A%E5%BD%B1%E5%93%8D%E4%B8%80%E4%BA%9Bbenchmark%E6%95%88%E6%9E%9C%E3%80%82%E4%BD%86%E5%9C%A8%E5%A4%A7%E6%89%B9%E9%87%8F%E6%95%B0%E6%8D%AE%E4%B8%8A%E6%98%AF%E6%97%A0%E6%8D%9F%E6%B3%9B%E5%8C%96%E6%95%88%E6%9E%9C%E7%9A%84%E3%80%82)。因为本来希望模型充分拟合每条，但packing降低了单条权重。数据量大时，这无所谓，因为模型样本看得多自然泛化。
    
-   业界有些经验认为，一般**不使用 packing**更稳妥，尤其如果对最终效果追求极致而训练时间可接受，就宁可浪费一些padding算力。
    

可以把Packing看成一种**工程优化**手段，如果训练时间很紧张，用packing能较快得到一个还不错的模型。如果追求最佳效果，愿意多花算力，也可以不用packing确保每条数据足够关注。也有折中方案，比如把数据按长度分桶，不同bucket分别pad（所谓Smart Batching），这样短的跟短的一起，长的跟长的，不需要packing也减少了pad浪费。

总结：**SFT Packing = 拼单**，让GPU一口气算好几单生意。当然拼多了服务质量可能稍降。所以到底拼不拼，要看你的吞吐需求和对模型质量的要求程度。

## 一句话形容 SFT 的原理？

用一句通俗的话来说，SFT 就像**给大模型“背书”**。预训练时模型通过自监督学会了语言模型本领（next token prediction），SFT 则在有监督信号下做同样的 next token prediction，只不过这里每个 token 都有“老师范例”告诉它正确答案[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=How%20to%20do%20that%3F%20We,the%20model%20clones%20this%20behavior)。从反馈粒度看，两者都是按 token 级别反馈，只是预训练的“正确答案”由上下文自洽给出，SFT 的“正确答案”来自人工标注。所以**预训练学的是广博，SFT学的是针对**。SFT 过程中模型主要是在**记忆**训练提供的问答映射——所以一般不会存在“完全学不会”，顶多是“学得不通泛”。换言之，如果某问题在训练集中或类似形式出现过，模型几乎必然会**牢牢记住并复现**答案；但若出现跟训练差异很大的问题，它就难以举一反三（这需要更高级的RLHF或推理能力）。

也有人用类比说：**预训练是模型读书自学，SFT是老师带着做题**。预训练后模型掌握了很多知识，但可能不知如何应用；SFT拿出一些题目手把手教，模型就会套用所学去答类似的问题。因为老师批改只告诉它哪种答案是好的，没有告诉它不好的（那是RLHF做的事），所以SFT模型难免**不知避错**，只会**尽量模仿正确**。整体来说，SFT 是在模型脑中刻下**特定领域的问答“映射表”**。所以效果很大程度取决于训练集覆盖的问答对。如果问到了**训练中没覆盖**或者**答案冲突**的问题，模型可能就懵或者乱答，这就是SFT的局限。

一句话总结SFT原理：**“预训练是让模型预测下一个词，自学成才；SFT是在预训练模型基础上，用人工答案逐词监督，让模型学会按照特定任务要求来预测下一个词。”**两者形式类似（都是下一个词预测），但因为引入了**人类监督信号**，SFT能显著改善模型在特定任务上的行为。

## SFT 实践中的一些细节和案例

（本节根据提供的代码片段和常见实践总结，尽量不用具体代码而用描述。）

**模型与分词器匹配**：进行SFT时务必要确保**tokenizer和model是一致的**[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,T2Q%EF%BC%9A%E9%9A%90%E5%90%AB%E6%8E%A8%E7%90%86%E6%8F%90%E5%8F%96%E6%B3%95)。不同模型哪怕架构类似，如果用了不同的词表，token含义会不同。通常从预训练模型仓库加载Tokenizer，再加载对应模型。如果擅自换tokenizer可能导致乱码输出。微调时如果需要扩充词表（例如加入专业术语），也应在加载后通过`tokenizer.add_tokens`并让模型embedding层resize对应大小。

**思考模式**：一些大模型支持特殊的“思考模式”开关，如 Qwen-3 有一个 `enable_thinking` 参数。启用后，模型会在回答时输出推理过程（可能带特殊标记）[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,%E6%95%B0%E6%8D%AE%E6%95%88%E7%8E%87%E7%A0%94%E7%A9%B6)。这通常需要在tokenizer应用对话模板时设置。例如 `tokenizer.apply_chat_template(..., enable_thinking=True)` 会让prompt格式要求模型先输出`<思考>`内容。这在Chain-of-thought训练或分析模型内部逻辑时有用。**不过**，默认用户产品中不会启用，因为思考内容往往杂乱且冗长。这个功能更多是给开发者调试或研究用途。要用好它，需要SFT数据本身包含相应格式的思考链，不然模型不知道怎么输出。

**模型加载和推理**：基于Transformers库，一般加载微调后的模型用 `AutoModelForCausalLM.from_pretrained` 和对应的 `AutoTokenizer`[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,T2Q%EF%BC%9A%E9%9A%90%E5%90%AB%E6%8E%A8%E7%90%86%E6%8F%90%E5%8F%96%E6%B3%95)。推理（生成）可以用 `model.generate` 方法：传入编码后的input\_ids，设置`max_length`等参数，模型会返回输出ids序列，然后用tokenizer解码为文本[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,T2Q%EF%BC%9A%E9%9A%90%E5%90%AB%E6%8E%A8%E7%90%86%E6%8F%90%E5%8F%96%E6%B3%95)。要注意给生成函数加上 `stop_token` 或者在Tokenizer中定义好 `eos_token`（如 `tokenizer.eos_token = '</s>'` 等）[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,T2Q%EF%BC%9A%E9%9A%90%E5%90%AB%E6%8E%A8%E7%90%86%E6%8F%90%E5%8F%96%E6%B3%95)。否则模型可能一直生成下去直到达到max\_length。通常模型在SFT数据里已经学会遇到某些符号停止，比如 `</s>` 或 `\nHuman:` 这样的role提示。只要设置对了`eos_token_id`，`generate`函数遇到它会停止[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,T2Q%EF%BC%9A%E9%9A%90%E5%90%AB%E6%8E%A8%E7%90%86%E6%8F%90%E5%8F%96%E6%B3%95)。

**训练代码实现**：SFT训练常用两种方式：HuggingFace Trainer 或 TRL库的SFTTrainer：

-   **使用 Trainer**：需要准备好 `TrainingArguments`（包括输出目录、epoch数、batch大小、学习率、评估策略等）[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,T2Q%EF%BC%9A%E9%9A%90%E5%90%AB%E6%8E%A8%E7%90%86%E6%8F%90%E5%8F%96%E6%B3%95)。然后用 `Trainer(model, args, train_dataset, eval_dataset, tokenizer)` 初始化并调用 `train()`[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,T2Q%EF%BC%9A%E9%9A%90%E5%90%AB%E6%8E%A8%E7%90%86%E6%8F%90%E5%8F%96%E6%B3%95)。Trainer 会自动处理常见流程（梯度累积、多GPU、保存checkpoint等）。其日志会打印loss，每隔logging\_steps会输出。
    
-   **使用 TRL SFTTrainer**：这是为RLHF任务准备的，也可以用于纯SFT。配置类似但可以直接支持一些对话格式处理等。如果不需要RL相关功能，用普通Trainer足够了。
    

**训练细节**：如Gradient Checkpointing（梯度检查点）可以在TrainingArguments打开，它能减少显存但降低一点速。`save_steps`和`eval_steps`可以设定保存/评估频率。小心`save_total_limit`防止硬盘爆满。还有 `fp16=True` 或 `bf16=True` 来自动混合精度训练（前提GPU支持bf16）。HuggingFace Trainer这些参数都很丰富，要根据硬件尝试合适组合。

**EOS符号**：再次强调，**一定要确保 tokenizer.eos\_token 定义正确**[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=,T2Q%EF%BC%9A%E9%9A%90%E5%90%AB%E6%8E%A8%E7%90%86%E6%8F%90%E5%8F%96%E6%B3%95)。很多开源模型用 `</s>` 或 `<|endoftext|>` 作为结束符。如果微调数据没有显式在答案末尾加EOS，也没关系，但为了安全，可以在训练数据处理时给每条答案结尾加上终止符。这样模型学习结束符，推理时就会自己停或在适当时输出EOS。如果没有EOS，模型可能“停不下来”。另外在generate时可以手动设置 `stop_sequence`参数（在一些接口中，如HuggingFace pipelines可以传stop tokens）。总结就是，要么**训练**时给模型灌输何时停的概念，要么**推理**时外部强制停，否则模型有时会无穷扯下去。

**可视化和调试**：训练过程中可以记录loss曲线，用 TensorBoard 或 Matplotlib 看【21†】。如发现loss波动异常，可打印部分样本检查梯度，或对比embedding层是否正常更新。另外可以每隔一段时间让模型生成几个测试问题看输出是否朝着正确方向变化。

**图表和流程图**：在理解SFT概念时，可借助一些可视化来帮助。如之前插入的大流程图概要了预训练-SFT-RLHF的关系，还有损失曲线图体现过拟合拐点等等。这些示意图对于非AI从业者理解抽象概念很有帮助。对于代码层面操作，这里就不深入给出流程图，以免偏离重点。

**具体应用案例**：最后，以一个简化案例结尾：假设我们有一个基础模型，想让它成为数学解题助手。我们准备了一批包含问题、逐步推理、最终答案的示例进行SFT微调。微调后模型在用户提问数学题时，会先输出推理过程再给答案。评估时发现模型确实学会了这种格式，但有时推理过程算错。为减少错误，我们又加入了一些正确推理示例并略微降低学习率再训，模型稳定了不少。这说明SFT是个不断迭代改进的过程。应用中，我们可以权衡要不要让模型显式推理：如果不要，就在prompt或数据中取消思维链格式即可，让模型直接输出答案以节省时间。这些都取决于产品对准确率和时延的要求。SFT 给了我们**定制模型行为**的强大手段，但也需要我们**精雕细琢数据和参数**，才能塑造出理想的AI助手。

以上内容全面概括了SFT的方方面面，从概念原理到实操注意事项，希望对开发者和产品经理们理解**监督微调**在大模型中的作用有所帮助。在实际项目中，SFT常与预训练、RLHF配合出现，共同打造出功能强大又贴近人意的AI模型。通过合理应用SFT，我们可以让通用大模型快速适应垂直场景，发挥出更大价值。**监督微调**，这把让AI听话懂事的钥匙，正越来越成为大模型落地的标配技能。祝愿大家用好这把钥匙，打开AI应用的大门！[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=struggle%20with%20questions%20outside%20its,especially%20for%20highly%20specialized%20fields)[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=,especially%20for%20highly%20specialized%20fields)

**参考文献：**

1.  NudgeBee博客 – *《SFT vs RLHF vs RL: Key Differences in Fine-Tuning LLMs》*[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=Image%3A%20Supervised%20Fine)[blogs.nudgebee.com](https://blogs.nudgebee.com/supervised-fine-tuning-vs-rlhf-vs-rl-differences-and-role-in-llms/#:~:text=,labeled%20datasets%20can%20be%20time)
    
2.  Huyen Chip – \*《RLHF: Reinforcement Learning from Human Feedback》\*博文[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=Pretraining%20optimizes%20for%20completion,following%20could%20be%20valid%20completion)[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=%3E%20%20%20,supposed%20to%20help%20with%20hallucination)
    
3.  IBM Cloud – \*《RAG vs. Fine-Tuning》\*文章[ibm.com](https://www.ibm.com/think/topics/rag-vs-fine-tuning#:~:text=What%E2%80%99s%20the%20difference%20between%20RAG,tuning)[ibm.com](https://www.ibm.com/think/topics/rag-vs-fine-tuning#:~:text=RAG%20plugs%20an%20LLM%20into,be%20able%20to%20without%20it)
    
4.  Monte Carlo Data – *《RAG vs Fine Tuning: How to Choose the Right Method》*[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=RAG%20tends%20to%20improve%20factual,can%20lead%20to%20poor%20answers)[montecarlodata.com](https://www.montecarlodata.com/blog-rag-vs-fine-tuning/#:~:text=RAG%20pulls%20information%20from%20an,during%20its%20last%20training%20session)
    
5.  HuggingFace – \*《Illustrating RLHF》\*博文[huyenchip.com](https://huyenchip.com/2023/05/02/rlhf.html#:~:text=an%20example%20of%20a%20language%3F%E2%80%9D%2C,)
    
6.  Lathashree H. – *《Understanding the LLM’s inference》* (Medium文章)[lathashreeh.medium.com](https://lathashreeh.medium.com/understanding-the-llms-inference-36a767f98a83#:~:text=%2A%20Prefill%20is%20a%20one,the%20prefill%20overhead%20might%20dominate)
    
7.  Garanti BBVA Teknoloji – *《Full Fine-Tuning, LoRA, qLoRA Comparison》*[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=dramatic%20reduction%20in%20memory%20usage,and%20computational%20cost)[medium.com](https://medium.com/garantibbva-teknoloji/full-fine-tuning-lora-and-qlora-a-comparison-of-techniques-in-model-optimization-89038d36865f#:~:text=Instead%2C%20a%20low,memory%20usage%20and%20computational%20cost)
    
8.  Meta AI – *《LIMA: Less Is More for Alignment》* (arXiv 2023)[anote-ai.medium.com](https://anote-ai.medium.com/lima-less-is-more-for-alignment-21e0db831e66#:~:text=LIMA%3A%20Less%20Is%20More%20for,carefully%20curated%20prompts%20and%20responses)
    
9.  鹤啸九天 – \*《LLM 大模型训练之路》\*博客[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=SFT%20packing%20%E6%8C%87%E8%AE%AD%E7%BB%83sft%E8%BF%87%E7%A8%8B%E4%B8%AD%EF%BC%8C%E5%B0%86%20%E5%A4%9A%E4%B8%AAsft%E6%95%B0%E6%8D%AEpack%E5%88%B0%E4%B8%80%E4%B8%AA%E6%A0%B7%E6%9C%AC%E5%86%85%20%E8%BF%9B%E8%A1%8C%E8%AE%AD%E7%BB%83)[wqw547243068.github.io](https://wqw547243068.github.io/llm_train#:~:text=)
    

![](https://www.google.com/s2/favicons?domain=https://lathashreeh.medium.com&sz=32)

![](https://www.google.com/s2/favicons?domain=https://www.montecarlodata.com&sz=32)

![](https://www.google.com/s2/favicons?domain=https://www.ibm.com&sz=32)

![](https://www.google.com/s2/favicons?domain=https://blogs.nudgebee.com&sz=32)

![](https://www.google.com/s2/favicons?domain=https://huyenchip.com&sz=32)

源