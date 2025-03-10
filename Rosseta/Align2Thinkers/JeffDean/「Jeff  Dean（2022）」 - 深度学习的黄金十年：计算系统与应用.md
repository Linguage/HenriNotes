

## 导读

现在是2025年，距离人工智能领域经历又一次巨大飞跃已经过去了两年多。自2022年末起，我们见证了**大语言模型**（LLMs）以前所未有的速度发展，深刻地改变了我们对人工智能的认知和应用方式。在这个背景下，重新审视2022年春季由Google高级研究员Jeffrey Dean撰写的论文《深度学习的黄金十年：计算系统与应用》有着一些特别体验。

这篇文章发表于大语言模型革命的黎明之前，它出色地总结了**2010年代深度学习的辉煌成就**，并对未来的发展方向做出了展望。在2022年，深度学习已经深刻地影响了计算机视觉、语音识别、自然语言处理等多个领域，正如Dean在文章中详细阐述的那样，这十年是名副其实的“黄金十年”。

**文章的核心内容可以概括为：**

*   **深度学习复兴的原因：** Dean深入分析了深度学习在过去十年取得突破的关键因素，包括计算硬件的飞速发展（GPU、TPU等专用加速器）、开源软件框架的普及（TensorFlow、PyTorch等）、以及研究社区的蓬勃发展。
*   **应用领域的爆炸式增长：** 文章细致地描绘了深度学习在各个领域的广泛应用，从神经科学、分子生物学、医疗健康，到环境保护、机器人技术、以及创造力工具等，展现了深度学习强大的通用性和解决问题的能力。
*   **对未来方向的展望：** Dean在文章的结尾，前瞻性地提出了未来机器学习发展的一些关键趋势，例如稀疏激活模型、自动化机器学习（AutoML）、多任务学习等方向。他还强调了负责任的AI开发的重要性。

**在2025年重读这篇文章的意义在于：**

1.  **理解LLM浪潮的历史背景：**  虽然文章没有直接预测到今天大语言模型的爆发，但它清晰地描绘了深度学习在过去十年的积累和沉淀，正是这些基础性的进步为LLM的快速发展奠定了坚实的基础。我们可以从文章中看到，对**更大模型、更强算力、更易用工具**的追求，早已是深度学习发展的主旋律，而LLM正是这一趋势的极致体现。
2.  **验证文章的前瞻性：**  令人惊叹的是，即使在今天看来，文章中提出的许多未来方向仍然具有高度的预见性。 例如，Dean 讨论的**稀疏激活模型**，与当前MoE（Mixture of Experts，混合专家）架构的大型模型有着异曲同工之妙，而**AutoML** 的发展也为高效构建和优化LLM提供了思路。 这表明，即使技术发展日新月异，一些根本性的研究方向和挑战仍然是长期存在的。
3.  **反思深度学习的本质：**  尽管大语言模型在2025年占据了人工智能领域的中心舞台，但Dean的文章提醒我们，深度学习的应用远不止于语言。  文章中列举的**广泛应用领域**，例如在科学发现、医疗健康、环境保护等方面的潜力，在LLM时代依然重要，甚至可能因为LLM的进步而得到进一步的释放。  我们不应将目光仅仅局限于语言模型本身，而应该思考如何利用深度学习这一强大的工具，解决更广泛、更复杂的世界性难题。
4.  **强调负责任AI的重要性：**  Dean在文章末尾强调的“负责任的AI开发”在今天看来更加具有现实意义。 大语言模型的强大能力也带来了潜在的风险，例如偏见、滥用、信息安全等问题。  这篇文章提醒我们，在追求技术进步的同时，必须时刻关注伦理和社会责任，确保人工智能技术能够真正造福人类。

总结来说，《深度学习的黄金十年》这篇文章，在2025年这个大语言模型蓬勃发展的时代，依然具有重要的阅读价值。 它不仅帮助我们回顾和理解深度学习的过去，也为我们展望和思考人工智能的未来提供了宝贵的视角。  它提醒我们，技术的进步是一个持续积累的过程，而对基础原理的深刻理解和对未来趋势的前瞻性思考，是把握人工智能发展方向的关键。


### **文章框架**

```
├── 引言
│   ├── 深度学习的崛起与应用
│   └── 本文关注点
├── 深度学习的发展历程
│   ├── 早期人工智能的探索
│   └── 神经网络的复兴
├── 硬件与软件的进步
│   ├── 专用硬件的出现
│   └── 开源软件框架的推动
├── 深度学习的应用领域
│   ├── 科学领域
│   │   ├── 神经科学
│   │   ├── 分子生物学
│   │   └── 气候与环境
│   ├── 医疗健康
│   ├── 机器人技术
│   ├── 可访问性
│   ├── 个性化学习
│   └── 计算机辅助创造力
├── 机器学习的未来方向
│   ├── 稀疏激活模型
│   ├── 自动化机器学习（AutoML）
│   ├── 多任务学习与迁移学习
│   └── 责任制人工智能开发
└── 结论
```



# 深度学习的黄金十年：计算系统与应用

- 作者： **[Jeffrey Dean](https://research.google/people/jeff/)**
- 时间：2022年春季
- 原文链接：[A Golden Decade of Deep Learning: Computing Systems & Applications  ]([https://www.amacad.org/publication/daedalus/golden-decade-deep-learning-computing-systems-applications](https://www.amacad.org/publication/daedalus/golden-decade-deep-learning-computing-systems-applications))

> 在过去的十年里，由于通过深度学习实现的神经网络的复兴，人工智能领域取得了巨大的进步。 这有助于提高计算机观察、聆听和理解周围世界的能力，从而导致人工智能在许多科学领域和人类努力的其他领域的应用取得显著进展。 在本文中，我将探讨取得这些进展的原因，包括旨在加速机器学习的计算硬件的进步与开源软件框架的出现的融合，这些框架极大地扩展了能够有效使用机器学习的人群。 我还对过去十年中机器学习应用的一些领域进行了广泛的概述。 最后，我概述了人工智能进一步发展的一些可能方向。



自从计算的最早期以来，人类就梦想着能够创造出“思考机器”。 人工智能领域是在1956年由John McCarthy在达特茅斯学院组织的一次研讨会上创立的，一群数学家和科学家聚集在一起，目的是“找出如何让机器使用语言、形成抽象和概念、解决现在只属于人类的问题，并改进它们自己。”[1] 研讨会的参与者乐观地认为，几个月专注的努力将在这些问题上取得真正的进展。

事实证明，几个月的时间表过于乐观。 在接下来的五十年里，各种创建人工智能系统的方法应运而生，又逐渐没落，包括基于逻辑的系统、基于规则的专家系统和神经网络。[2] 涉及对关于世界的逻辑规则进行编码并使用这些规则的方法被证明是无效的。 将数百万条人类知识手工整理成机器可读的形式（以Cyc项目为最突出的例子）被证明是一项非常劳动密集型的任务，并没有在使机器自主学习方面取得重大进展。[3] 从真实的生物神经网络中汲取灵感的人工神经网络，在这段时间里似乎是一种很有前途的方法，但最终在20世纪90年代失宠。 虽然它们能够在玩具规模的问题上产生令人印象深刻的结果，但它们无法在当时在现实世界的问题上产生有趣的结果。 作为1990年的一名本科生，我对神经网络很着迷，觉得它们似乎是创造智能机器的正确抽象，并且确信我们只需要更强大的计算能力，就能让更大的神经网络来处理更大、更有趣的问题。 我做了一篇关于神经网络并行训练的本科毕业论文，确信如果我们能够使用64个处理器而不是一个处理器来训练一个神经网络，那么神经网络就可以解决更有趣的任务。[4] 然而，事实证明，相对于1990年的计算机，我们需要大约一百万倍的计算能力，而不是64倍，才能让神经网络在具有挑战性的问题上开始取得令人印象深刻的进展！ 然而，从2008年左右开始，由于摩尔定律，我们开始拥有如此强大的计算机，神经网络开始复兴，并成为创建能够观察、聆听、理解和学习的计算机的最有希望的方式（同时将这种方法重新命名为“深度学习”）。

从2011年左右到写作时（2021年）的十年间，1956年达特茅斯研讨会上提出的目标取得了显著进展，机器学习（ML）和人工智能现在正在许多领域取得全面进展，为新型计算体验和交互创造了机会，并极大地扩展了世界上可以解决的问题集。 本文重点关注三个方面：推动这一进展的计算硬件和软件系统；过去十年中机器学习的一些令人兴奋的应用示例；以及我们如何创建更强大的机器学习系统，以真正实现创建智能机器的目标。


## 人工智能的软硬件

与通用计算机代码（例如您每天使用文字处理器或Web浏览器时可能使用的软件）不同，深度学习算法通常由少量线性代数运算的不同组合方式构成：矩阵乘法、向量点积和类似运算。 由于这种运算词汇的限制，可以构建专门支持这些类型计算的计算机或加速器芯片。 与必须运行各种算法的通用中央处理器（CPU）相比，这种专业化实现了新的效率和设计选择。

在21世纪初，少数研究人员开始研究使用图形处理单元（GPU）来实现深度学习算法。 虽然最初设计用于渲染图形，但研究人员发现这些设备也非常适合深度学习算法，因为与CPU相比，它们具有相对较高的浮点计算速率。 2004年，计算机科学家Kyoung-Su Oh和Keechul Jung展示了使用GPU的神经网络算法近20倍的改进。[5] 2008年，计算机科学家Rajat Raina及其同事展示了在某些无监督学习算法中，使用GPU与最佳的基于CPU的实现相比，加速高达72.6倍。[6]

随着神经网络在GPU上的训练在各种计算机视觉竞赛中胜过其他方法，这些早期的成就不断积累。[7] 随着深度学习方法在图像识别、语音识别和语言理解方面开始显示出显著的改进，并且随着计算密集型模型（在更大的数据集上训练）不断展示出改进的结果，机器学习领域真正起飞了。[8] 计算机系统设计师开始研究如何将深度学习模型扩展到更具计算密集性的高度。 一种早期的方法是使用大规模分布式系统来训练单个深度学习模型。 谷歌研究人员开发了DistBelief框架，这是一个软件系统，可以使用大规模分布式系统来训练单个神经网络。[9] 使用DistBelief，研究人员能够训练一个无监督神经网络模型，该模型比以前的神经网络大两个数量级。 该模型是在YouTube视频中的大量随机帧上训练的，并且具有大型网络和足够的计算和训练数据，它表明模型中的个体人工神经元（神经网络的构建块）将学习识别高级概念，如人脸或猫，尽管除了原始图像的像素之外，从未向它们提供任何关于这些概念的信息。[10]

这些成功促使系统设计师设计出比GPU更适合和匹配深度学习算法需求的计算设备。 为了构建专用硬件，深度学习算法有两个非常好的特性。 首先，它们对精度降低非常宽容。 与许多需要32位或64位浮点表示来保证计算的数值稳定性的数值算法不同，深度学习算法在训练（神经网络从观察中学习的过程）期间通常可以使用16位浮点表示，在推理（神经网络从输入生成预测或其他输出的过程）期间可以使用8位甚至4位整数定点表示。 与使用更高精度乘法器相比，使用降低的精度可以在相同的芯片面积中放置更多的乘法电路，这意味着芯片每秒可以执行更多的计算。 其次，深度学习算法所需的计算几乎完全由稠密矩阵或向量上的不同线性代数运算序列组成，例如矩阵乘法或向量点积。 这导致了这样一种观点，即制造专门用于低精度线性代数计算的芯片和系统可以在每美元性能和每瓦特性能方面带来巨大的好处。 谷歌的第一个张量处理单元（TPUv1）是这种早期芯片，它针对深度学习推理的8位整数计算，并在速度和每瓦特性能方面比当时的CPU和GPU提高了一到两个数量级。[11] 这些芯片的部署使谷歌能够在语音识别准确率、语言翻译和图像分类系统方面取得显著改进。 后来的TPU系统由定制芯片以及通过高速定制网络将许多这些芯片连接在一起的更大规模系统组成，形成pod，这是一种专为训练深度学习模型而设计的大型超级计算机。[12] 像NVIDIA这样的GPU制造商开始针对较低精度的深度学习计算调整后来的设计，并且大量风险投资支持的初创公司涌现出来，构建各种深度学习加速器芯片，其中Graph-Core、Cerebras、SambaNova和Nervana是一些最著名的。

除了GPU和其他面向ML的硬件的兴起之外，研究人员还开发了开源软件框架，使得表达深度学习模型和计算变得容易。 这些软件框架仍然是关键的推动因素。 今天，开源框架帮助广泛的研究人员、工程师和其他人推动深度学习研究，并将深度学习应用于极其广泛的问题领域（其中许多将在下面讨论）。 一些最早的框架，如2003年开始开发的Torch，从早期的数学工具（如MatLab和NumPy）中汲取了灵感。[13] 2010年开发的Theano是一个早期的面向深度学习的框架，包括自动符号微分。[14] 自动微分是一个有用的工具，它极大地简化了许多基于梯度的机器学习算法的表达，例如随机梯度下降（一种通过比较实际输出和期望输出并在误差梯度的方向上对模型参数进行微小调整来纠正输出中的错误的技术）。 DistBelief和Caffe是2010年代初期开发的框架，强调规模和性能。[15]

TensorFlow是一个允许表达机器学习计算的框架。[16] 它由谷歌于2015年开发并开源，结合了早期框架（如Theano和DistBelief）的思想。[17] TensorFlow旨在针对各种系统，并允许ML计算在台式计算机、移动电话、数据中心的大规模分布式环境和Web浏览器上运行，并针对各种计算设备，包括CPU、GPU和TPU。 该系统已被下载超过五千万次，是世界上最受欢迎的开源软件包之一。 它使世界各地的个人和大小组织能够广泛使用机器学习。

PyTorch于2016年发布，因其使用Python轻松表达各种研究思想而受到研究人员的欢迎。[18] JAX于2018年发布，是一个流行的开源Python库，结合了复杂的自动微分和底层的XLA编译器，XLA编译器也被TensorFlow用于将机器学习计算有效地映射到各种不同类型的硬件上。[19]

像TensorFlow和PyTorch这样的开源机器学习库和工具的重要性怎么强调都不为过。 它们使研究人员能够快速尝试想法并在这些框架之上表达它们。 随着世界各地的研究人员和工程师更容易地在彼此的工作基础上进行构建，整个领域的进步速度加快了！


## 研究爆炸 

由于研究进展、GPU和TPU等面向ML的硬件的计算能力不断增长，以及TensorFlow和PyTorch等开源机器学习工具的广泛采用，机器学习及其应用领域的研究成果急剧增加。 一个强有力的指标是发布到arXiv（一个流行的论文预印本托管服务）的机器学习相关类别的论文数量，2018年发布的论文预印本数量是2009年的32倍以上（增长率超过每两年翻一番）。[20] 现在，每天有超过100篇研究论文发布到arXiv的机器学习相关子主题领域，并且这种增长没有放缓的迹象。

## 应用爆炸

计算能力的变革性增长、机器学习的软件和硬件系统的进步以及机器学习研究的激增，都导致了机器学习在许多科学和工程领域的应用激增。 通过与气候科学和医疗保健等关键领域的专家合作，机器学习研究人员正在帮助解决可以造福社会和促进人类进步的重要问题。 我们确实生活在一个激动人心的时代。

神经科学是机器学习加速科学进步的一个重要领域。 2020年，研究人员研究了果蝇的大脑，以更多地了解人类大脑的工作原理。 他们构建了一个连接组，一个果蝇整个大脑突触分辨率水平的连接图。[21] 但是如果没有机器学习和我们现在拥有的计算能力，这将需要很多年。 例如，在20世纪70年代，研究人员花了大约十年的时间才煞费苦心地绘制出蠕虫大脑中的大约三百个神经元。 相比之下，果蝇的大脑有十万个神经元，而小鼠的大脑（机器学习辅助连接组学的下一个目标）有大约七千万个神经元。 人脑包含大约850亿个神经元，每个神经元大约有一千个连接。 幸运的是，基于深度学习的计算机视觉的进步现在使得加速这个以前庞大的过程成为可能。 而且今天，由于机器学习，您可以使用交互式3-D模型自行探索果蝇的大脑！[22]

**分子生物学。** 机器学习还可以帮助我们更多地了解我们的基因组成，并最终更有效地解决基于基因的疾病。 这些新技术使科学家能够通过更准确的模拟、估计和数据分析，更快地探索潜在实验的范围。 一种开源工具DeepVariant可以使用卷积神经网络更准确地处理来自DNA测序仪（其中包含因读取遗传序列的物理过程而引入的错误）的原始信息，并对其进行分析，以更准确地识别序列中相对于参考基因组数据的真实遗传变异。 一旦识别出遗传变异，深度学习还可以帮助分析遗传序列，以更好地了解导致特定健康或其他结果的单个或多个DNA突变的遗传特征。 例如，由Dana-Farber癌症研究所领导的一项研究将2,367名癌症患者队列中导致前列腺癌和黑色素瘤的遗传变异的诊断率提高了14%。[23]

**医疗保健。** 机器学习还提供了新的方法来帮助检测和诊断疾病。 例如，当应用于医学图像时，计算机视觉可以帮助医生比医生自己更快、更准确地诊断许多严重疾病。

一个令人印象深刻的例子是深度神经网络能够正确诊断糖尿病视网膜病变，通常与人类眼科医生相当。 这种眼部疾病是可预防失明的增长最快的原因（预计到2040年将影响6.42亿人）。

深度学习系统还可以帮助检测肺癌，其效果与训练有素的放射科医生相当或更好。 乳腺癌、皮肤病和其他疾病也是如此。[24] 在病历上应用序列预测可以帮助临床医生确定慢性疾病的可能诊断和风险水平。[25]

今天的深度学习技术也使我们能够更准确地了解疾病是如何传播的，从而使我们有更好的预防机会。 机器学习帮助我们对复杂的事件进行建模，例如全球COVID-19大流行，这需要全面的流行病学数据集、开发新型的可解释模型以及基于代理的模拟器来为公共卫生应对措施提供信息。[26]

**天气、环境和气候变化。** 气候变化是当前人类面临的最大挑战之一。 机器学习可以帮助我们更好地了解天气和我们的环境，特别是预测或预报日常天气和气候灾害。

对于天气和降水预报，计算密集型的基于物理的模型，如美国国家海洋和大气管理局的高分辨率快速刷新（HRRR）长期以来一直占据主导地位。[27] 然而，基于机器学习的预测系统可以在较短的时间尺度上比HRRR预测得更准确，具有更好的空间分辨率和更快的预测计算。[28]

对于洪水预报，神经网络可以对世界各地的河流系统进行建模（一种称为HydroNets的技术），从而产生更准确的水位预测。[29] 利用这项技术，当局可以更快地向印度和孟加拉国超过2亿人发送洪水警报。[30]

机器学习还可以帮助我们更好地分析卫星图像。 我们可以在自然灾害发生后快速评估损失（即使事先的卫星图像有限），了解野火的影响和范围，并改善生态和野生动物监测。[31]

**机器人技术。** 现实世界是混乱的，充满了意想不到的障碍、滑倒和破损。 这使得创建能够在厨房、办公室和道路等混乱的现实环境中成功运行的机器人非常具有挑战性（工业机器人已经在世界上产生了重大影响，在工厂装配线等更受控制的环境中运行）。 为了对现实世界的物理任务进行硬编码或编程，研究人员需要预测机器人可能遇到的所有可能情况。 机器学习通过强化学习、人类演示和自然语言指令等技术的组合，有效地训练机器人在现实环境中有效运行。 机器学习还允许一种更灵活、适应性更强的方法，在这种方法中，机器人可以学习参与抓取或行走任务的最佳方式，而不是被锁定在硬编码的假设中。

一些有趣的研究技术包括自动强化学习与远程机器人导航相结合，教机器人遵循自然语言指令（以多种语言！），以及应用零样本模仿学习框架来帮助机器人在模拟和真实环境中更好地导航。[32]

**无障碍。** 认为我们能够看到美丽的图像、听到最喜欢的歌曲或与亲人交谈的能力是理所当然的。 然而，超过十亿人无法以这些方式进入世界。 机器学习通过将这些信号（视觉、听觉、语音）转换为具有无障碍需求的人可以很好地管理的信号，从而改善无障碍性，从而更好地进入周围的世界。 一些应用示例包括语音转文本转录、某人参与对话时的实时转录以及可以帮助视障用户识别周围环境的应用程序。[33]

**个性化学习。** 机器学习还可以用于创建有助于个性化学习的工具和应用程序。 其好处将是深远的，最初的例子包括幼儿阅读辅导，例如Google Read Along（以前称为Bolo），它正在帮助世界各地的儿童学习以各种不同的语言阅读，[34] 以及像Socratic这样的机器学习工具，可以通过向孩子们提供直观的解释和关于他们在各种学科（如数学、化学和文学）中遇到的概念的更详细信息来帮助孩子们学习。[35] 以语音识别、逼真的语音输出和语言理解为后盾的个性化学习有可能改善全世界的教育成果。

**计算机辅助创造力。** 深度学习算法显示出以复杂和创造性的方式转换图像的惊人能力，使我们能够轻松地创建莫奈风格的宇宙飞船或爱德华·蒙克风格的金门大桥。[36] 通过一种艺术风格转换算法（由机器学习研究员Leon Gatys及其同事开发），神经网络可以获取真实世界的图像和绘画的图像，并自动以画家的风格渲染真实世界的图像。 OpenAI的DALL·E使用户能够使用文本描述图像（“鳄梨形状的扶手椅”或“白色床旁边有床头柜，床头柜旁边有鱼缸的阁楼卧室”），并生成具有自然语言描述所表达的属性的图像，为艺术家和其他创作者制作复杂的工具，以快速创建他们脑海中的图像。[37]

机器学习驱动的工具也正在帮助音乐家以他们以前从未有过的方式进行创作。[38] 超越“技术”，这些新的计算用途可以帮助任何人创建新的和独特的声音、节奏、旋律，甚至是全新的乐器。

不难想象未来的工具可以通过与我们的计算助手进行交互式交谈，以交互方式帮助人们创建我们心理意象的惊人表示——“给我画一片海滩......不，我希望是夜晚......有满月......还有一只母长颈鹿和一只小长颈鹿在一位冲浪者旁边从水里出来”——。

**重要组成部分。** 联邦学习是一种强大的机器学习方法，它可以保护用户隐私，同时利用许多不同的客户端（如移动设备或组织）来协作训练模型，同时保持训练数据分散。[39] 这使得在大规模学习系统中具有卓越隐私属性的方法成为可能。[40]

研究人员通过开发自适应学习算法、在联邦环境中模拟集中式算法的技术、互补密码协议的重大改进等，继续推动联邦学习的最新技术。[41]

**Transformer。** 自该领域开始以来，语言一直是开发人工智能的核心，因为语言的使用和理解在我们的日常生活中无处不在。 因为语言处理符号，所以它自然而然地促使人工智能采用符号方法。 但是多年来，人工智能研究人员已经意识到，更多的统计或基于模式的方法会产生更好的实际用途。 正确类型的深度学习可以非常有效地表示和操纵分层结构用于各种现实世界的任务，从语言之间的翻译到图像标记。 来自谷歌和其他地方的许多关于这个领域的工作现在都依赖于Transformer，这是一种最初为语言问题开发的特殊类型的神经网络模型（但越来越多的证据表明它们对图像、视频、语音、蛋白质折叠和各种其他领域也很有用）。[42]

在科学环境中，有几个有趣的Transformer使用示例，例如在蛋白质序列上进行训练以找到编码有意义的生物学属性的表示、通过语言建模生成蛋白质、用于生物医学数据文本挖掘的bio-BERT（具有预训练模型和训练代码）、科学文本的嵌入（带代码）以及医学问题解答。[43] 计算机科学家Maithra Raghu和Eric Schmidt对深度学习用于科学发现的方式进行了全面回顾。[44]

**用于计算机系统的机器学习。** 研究人员还将机器学习应用于核心计算机科学和计算机系统问题本身。 对于机器学习和计算基础设施研究来说，这是一个令人兴奋的良性循环，因为它可以加速我们应用于其他领域的整个技术范围。 事实上，这一趋势正在催生全新的会议，例如MLSys。[45] 基于学习的方法甚至被应用于数据库索引、学习排序算法、编译器优化、图优化和内存分配。[46]

## 机器学习的未来

在ML研究社区中正在发生一些有趣的研究线索，如果将它们结合起来可能会更有趣。

首先，关于稀疏激活模型的工作，例如稀疏门控混合专家模型，展示了如何构建非常大容量的模型，其中对于任何给定的示例，只有一部分模型被“激活”（例如，在2,048个专家中只有两到三个专家）。[47] 这种模型中的路由函数与不同的专家同时联合训练，以便路由函数了解哪些专家擅长哪些类型的示例，并且专家同时学习专门针对它们所获得的示例流的特征。 这与当今大多数ML模型形成对比，在这些模型中，整个模型都会针对每个示例被激活。 研究科学家Ashish Vaswani及其同事表明，这种方法同时在训练效率方面提高了大约9倍，在推理效率方面提高了大约2.5倍，并且更准确（对于语言翻译任务，准确率提高了+1 BLEU点，这是一个相对较大的改进）。[48]

其次，关于自动化机器学习（AutoML）的工作，其中诸如神经架构搜索或进化架构搜索之类的技术可以自动学习有效的结构和机器学习模型的其他方面或组件，以优化给定任务的准确性，通常涉及运行许多自动实验，每个实验都可能涉及大量的计算。[49]

第三，在少数到几十个相关任务的中等规模上进行多任务训练，或者从在大量数据上训练的用于相关任务的模型进行迁移学习，然后在新任务的少量数据上进行微调，已被证明在各种问题中非常有效。[50] 到目前为止，多任务机器学习的大多数使用通常是在单一模态的背景下（例如所有视觉任务或所有文本任务），尽管一些作者也考虑了多模态设置。[51]

一个特别有趣的研究方向将这三个趋势结合起来，在一个运行在大规模ML加速器硬件上的系统中，目标是训练一个可以执行数千或数百万个任务的单一模型。 这样的模型可能由许多不同结构的不同组件组成，示例之间的数据流在逐个示例的基础上是相对动态的。 该模型可能会使用诸如稀疏门控混合专家和学习路由之类的技术，以拥有一个非常大容量的模型，[52] 但其中给定的任务或示例仅稀疏地激活系统中组件的一小部分（因此每个训练示例或推理的计算成本和功耗要低得多）。 一个有趣的研究方向是针对不同的示例使用动态和自适应的计算量，以便“简单”示例使用的计算量远少于“困难”示例（这是当今机器学习模型中相对不寻常的属性）。 图1描绘了这样一个系统。

每个组件本身可能正在运行一些类似AutoML的架构搜索，以便使组件的结构适应于被路由到该组件的数据类型。[53] 新任务可以在有用时利用在其他任务上训练的组件。 希望通过非常大规模的多任务学习、共享组件和学习路由，该模型可以非常快速地学习以高精度完成新任务，每个新任务的示例相对较少（因为该模型能够利用它在完成其他相关任务时已经开发的专业知识和内部表示）。

构建一个可以处理数百万个任务并且可以自动学习成功完成新任务的单一机器学习系统，是人工智能和计算机系统工程领域的一个真正巨大的挑战。 它将需要许多领域的专业知识和进步，包括机器学习算法、责任人工智能主题（如公平性和可解释性）、分布式系统和计算机体系结构，以便通过构建一个可以泛化以独立解决机器学习的所有应用领域的新任务的系统来推动人工智能领域的发展。






*图1  多任务、稀疏激活的机器学习模型*


> 注：此图描绘了一个大型、稀疏激活的多任务模型的设计。模型中的每个框代表一个组件。任务的模型通过将组件拼接在一起来开发，可以使用人类指定的连接模式或自动学习的连接性。每个组件可能正在运行一个小型架构搜索，以适应正在路由到它的数据类型，并且路由决策使组件决定哪些下游组件最适合基于观察到的行为的特定任务或示例。 来源：作者的图表，包括Barret Zoph和Quoc V. Le，“使用强化学习进行神经架构搜索”，arXiv（2016），图7，15，https://arxiv.org/abs/1611.01578。

**负责任的AI开发。** 虽然人工智能有能力在生活的许多方面帮助我们，但所有研究人员和从业者都应确保这些方法得到负责任的开发——仔细审查偏见、公平、隐私和其他社会考虑因素，了解这些工具的行为方式以及它们可能如何影响他人——并努力适当地解决这些考虑因素。

记录一套明确的原则来指导负责任的开发也很重要。 2018年，谷歌发布了一套人工智能原则，用于指导该公司的人工智能工作和使用。[54] 人工智能原则列出了重要的考虑领域，包括机器学习系统中的偏见、安全、公平、问责制、透明度和隐私等问题。 近年来，其他组织和政府也效仿了这种模式，发布了自己的人工智能使用原则。 很高兴看到更多的组织发布了自己的指导方针，我希望这种趋势将继续下去，直到它不再是一种趋势，而是所有机器学习研究和开发的标准。


## 结论

2010年代确实是深度学习研究和进步的黄金十年。 在这十年中，该领域在1956年创建人工智能领域的研讨会提出的一些最困难的问题领域取得了巨大进展。 机器变得能够以早期研究人员所希望的方式观察、聆听和理解语言。 这些核心领域的成功推动了许多科学领域的巨大进步，使我们的智能手机变得更加智能，并且当我们继续在创建更复杂和强大的深度学习模型方面取得进展时，通常会让我们大开眼界，这些模型可以帮助我们处理日常生活。 我们面前的未来是，由于令人难以置信的强大机器学习系统提供的帮助，我们都将变得更有创造力和能力。 我迫不及待地想看看未来会发生什么！

### 作者注

Alison Carroll、Heather Struntz 和 Phyllis Bendell 协助编辑了这份手稿，并就如何呈现大部分材料提出了许多有益的建议。

### 关于作者

**Jeffrey Dean**，自 2016 年起成为美国艺术与科学院院士，是 Google 公司的高级研究员 (Google Senior Fellow) 兼 Google Research 高级副总裁；也是斯坦福大学以人为本人工智能研究所的杰出研究员 (Distinguished Fellow)。他曾在 *Communications of the ACM*、《ACM计算机系统汇刊》( *ACM Transactions on Computer Systems*) 和《计算语言学协会汇刊》(*Transactions of the Association for Computational Linguistics*) 等期刊上发表过文章。他的研究论文可以在 Google Scholar 上找到：https://scholar.google.com/citations?user=NMS69lQAAAAJ


### 参考文献

1.   [Dartmouth Workshop](https://en.wikipedia.org/wiki/Dartmouth_workshop), Wikipedia, last updated October 7, 2021.
2.   [History of Artificial Intelligence](https://en.wikipedia.org/wiki/History_of_artificial_intelligence), Wikipedia, last updated December 2, 2021.
3.   [Cyc](https://en.wikipedia.org/wiki/Cyc), Wikipedia, last updated October 21, 2021.
4.   Jeffrey Dean, [Parallel Implementations of Neural Network Training: Two Back-Propagation Approaches](https://drive.google.com/file/d/1I1fs4sczbCaACzA9XwxR3DiuXVtqmejL/view) (senior thesis, University of Minnesota, 1990).
5.   Kyoung-Su Oh and Keechul Jung, [GPU Implementation of Neural Networks](https://www.sciencedirect.com/science/article/abs/pii/S0031320304000524), *Pattern Recognition* 37 (6) (2004).
6.   Rajat Raina, Anand Madhavan, and Andrew Y. Ng, [Large-Scale Deep Unsupervised Learning Using Graphics Processors](http://robotics.stanford.edu/~ang/papers/icml09-LargeScaleUnsupervisedDeepLearningGPU.pdf), in *Proceedings of the 26th International Conference on Machine Learning* (Princeton, N.J.: International Machine Learning Society, 2009).
7.   Jürgen Schmidhuber, [History of Computer Vision Contests Won by Deep CNNs on GPU](https://people.idsia.ch/~juergen/computer-vision-contests-won-by-gpu-cnns.html), AI Blog, 2017, last updated 2021.
8.   Alex Krizhevsky, Ilya Sutskever, and Geoffrey E. Hinton, [ImageNet Classification with Deep Convolution Neural Networks](https://papers.nips.cc/paper/2012/file/c399862d3b9d6b76c8436e924a68c45b-Paper.pdf), in *Advances in Neural Information Processing Systems 25 (NIPS 2012),* ed. F. Pereira, C. J. C. Burges, L. Bottou, and K. Q. Weinberger (Neural Information Processing Systems Foundation, 2012); Geoffrey Hinton, Li Deng, Dong Yu, et al., [Deep Neural Networks for Acoustic Modeling in Speech Recognition: The Shared Views of Four Research Groups](https://ieeexplore.ieee.org/document/6296526), *IEEE Signal Processing Magazine* 29 (6) (2012); Tomas Mikolov, Kai Chen, Greg Corrado, and Jeffrey Dean, [Efficient Estimation of Word Representations in Vector Space](https://arxiv.org/abs/1301.3781), arXiv (2013); and Ilya Sutskever, Oriol Vinyals, and Quoc V. Le, [Sequence to Sequence Learning with Neural Networks](https://arxiv.org/abs/1409.3215), arXiv (2014).
9.   Jeffrey Dean, Greg S. Corrado, Rajat Monga, et al., [Large Scale Distributed Deep Networks](https://static.googleusercontent.com/media/research.google.com/en//archive/large_deep_networks_nips2012.pdf) (Mountain View, Calif.: Google, Inc., 2012).
10.   Quoc V. Le, Marc’Aurelio Ranzato, Rajat Monga, et al., [Building High-Level Features Using Large Scale Unsupervised Learning](https://static.googleusercontent.com/media/research.google.com/en//archive/unsupervised_icml2012.pdf), in *Proceedings of the 29th International Conference on Machine Learning* (Princeton, N.J.: International Machine Learning Society, 2012).
11.   Norman P. Jouppi, Cliff Young, Nishant Patil, et al., [In-Datacenter Performance Analysis of a Tensor Processing Unit](https://dl.acm.org/doi/10.1145/3079856.3080246), in *ISCA ‘17: Proceedings of the 44th Annual International Symposium on Computer Architecture* (New York: Association for Computing Machinery, 2017).
12.   Norman P. Jouppi, Doe Hyun Yoon, George Kurian, et al., [A Domain-Specific Supercomputer for Training Deep Neural Networks](https://cacm.acm.org/magazines/2020/7/245702-a-domain-specific-supercomputer-for-training-deep-neural-networks/fulltext), *Communications of the ACM* 63 (7) (2020).
13.   Ronan Collobert, Samy Bengio, and Johnny Mariéthoz, [Torch: A Modular Machine Learning Software Library](https://infoscience.epfl.ch/record/82802/files/rr02-46.pdf), IDIAP Research Report 02-46 (Martigny, Switzerland: Dalle Molle Institute for Perceptual Artificial Intelligence, 2002).
14.   James Bergstra, Oliver Breuleux, Frédéric Bastien, et al., “Theano: A CPU and GPU Math Compiler in Python,” in *Proceedings of the 9th Python in Science Conference (SciPy 2010)* (Austin: Python in Science Conference, 2010).
15.  Dean et al., “Large Scale Distributed Deep Networks”; and [Caffe](https://caffe.berkeleyvision.org/), Berkeley Artificial Intelligence Research.
16.  [TensorFlow](https://www.tensorflow.org/).
17. [TensorFlow: A System for Large-Scale Machine Learning](https://www.usenix.org/conference/osdi16/technical-sessions/presentation/abadi), Usenix.
18. Adam Paszke, Sam Gross, Francisco Massa, et al., [PyTorch: An Imperative Style, High-Performance Deep Learning Library](https://arxiv.org/abs/1912.01703), arXiv (2019).
19. Matthew Johnson, Peter Hawkins, Jake Vanderplas, et al., [Jax](http://github.com/google/jax), GitHub, last updated December 15, 2021; and [XLA: Optimizing Compiler for Machine Learning](https://www.tensorflow.org/xla), TensorFlow, last updated December 2, 2021.
20. [Machine Learning](https://arxiv.org/list/cs.LG/recent), arXiv.
21. Michal Januszewski, [Releasing the Drosophila Hemibrain Connectome–The Largest Synapse-Resolution Map of Brain Connectivity](https://ai.googleblog.com/2020/01/releasing-drosophila-hemibrain.html), Google AI Blog, January 22, 2020.
22. Janelia FlyEM Hemibrain Dataset Information, [Hemibrain Neuroglancer Demo](https://tinyurl.com/25cjs3uk).
23. Saud H. AlDubayan, Jake R. Conway, Sabrina Y. Camp, et al., [Detection of Pathogenic Variants with Germline Genetic Testing Using Deep Learning vs. Standard Methods in Patients with Prostate Cancer and Melanoma](https://jamanetwork.com/journals/jama/article-abstract/2772962?guestAccessKey=39889aad-2894-4380-b869-5704ed2f9f6b), *JAMA* 324 (19) (2020).
24. Shravya Shetty and Daniel Tse, [Using AI to Improve Breast Cancer Screening](https://blog.google/technology/health/improving-breast-cancer-screening/), The Keyword, January 1, 2020; and Yuan Liu, Ayush Jain, Clara Eng, et al., [A Deep Learning System for Differential Diagnosis of Skin Diseases](https://www.nature.com/articles/s41591-020-0842-3), *Nature Medicine* 26 (2020).
25. Alvin Rajkomar and Eyal Oren, [Deep Learning for Electronic Health Records](https://ai.googleblog.com/2018/05/deep-learning-for-electronic-health.html), Google AI Blog, May 8, 2018.
26. [Covid-19-open-data](https://github.com/GoogleCloudPlatform/covid-19-open-data), GitHub, updated December 1, 2021; Sercan Arik, Chun-Liang Li, Jinsung Yoon, et al., [Interpretable Sequence Learning for Covid-19 Forecasting](https://research.google/pubs/pub49500/), in *Advances in Neural Information Processing Systems 33 (NeurIPS 2020)*, ed. H. Larochelle, M. Ranzato, R. Hadsell, et al. (Neural Information Processing Systems Foundation, 2020); and [Agent-based-epidemic-sim](https://github.com/google-research/agent-based-epidemic-sim), GitHub, updated September 28, 2021.
27. [The High-Resolution Rapid Refresh (HRRR)](https://rapidrefresh.noaa.gov/hrrr/), Global Systems Laboratory, U.S. Department of Commerce.
28. Jason Hickey, [Using Machine Learning to ‘Nowcast’ Precipitation in High Resolution](https://ai.googleblog.com/2020/01/using-machine-learning-to-nowcast.html), Google AI Blog, January 13, 2020.
29. Sella Nevo, [The Technology Behind Our Recent Improvements in Flood Forecasting](https://ai.googleblog.com/2020/09/the-technology-behind-our-recent.html), Google AI Blog, September 3, 2020.
30. Yossi Matias, [A Big Step for Flood Forecasts in India and Bangladesh](https://blog.google/technology/ai/flood-forecasts-india-bangladesh/), The Keyword, September 1, 2020.
31. Joseph Xu and Pranav Khaitan, [Machine Learning-Based Damage Assessment for Disaster Relief](https://ai.googleblog.com/2020/06/machine-learning-based-damage.html), Google AI Blog, June 16, 2020; Jihyeon Lee, Joseph Z. Xu, Kihyuk Sohn, et al., [Assessing Post-Disaster Damage from Satellite Imagery Using Semi-Supervised Learning Techniques](https://arxiv.org/abs/2011.14004), arXiv (2011); Yossi Matias, [Mapping Wildfires with the Power of Satellite Data](https://blog.google/products/search/mapping-wildfires-with-satellite-data/), The Keyword, August 20, 2020; and Sara Beery and Jonathan Huang, [Leveraging Temporal Context for Object Detection](https://ai.googleblog.com/2020/06/leveraging-temporal-context-for-object.html), Google AI Blog, June 26, 2020.
32. Aleksandra Faust and Anthony Francis, [Long-Range Robotic Navigation via Automated Reinforcement Learning](https://ai.googleblog.com/2019/02/long-range-robotic-navigation-via.html), Google AI Blog, February 28, 2019; Corey Lynch and Pierre Sermanet, [Language Conditioned Imitation Learning over Unstructured Data](https://language-play.github.io/) (2020); and Xinlei Pan, Tingnan Zhang, Brian Ichter, et al., [Zero-Shot Imitation Learning from Demonstrations for Legged Robot Visual Navigation](https://research.google/pubs/pub48968/), *ICRA* (2020).
33. Julie Cattiau, [How AI Can Improve Products for People with Impaired Speech](https://www.blog.google/outreach-initiatives/accessibility/impaired-speech-recognition/), The Keyword, May 7, 2019; Sagar Savla, [Real-Time Continuous Transcription with Live Transcribe](https://ai.googleblog.com/2019/02/real-time-continuous-transcription-with.html), Google AI Blog, February 4, 2019; and [Lookout by Google](https://play.google.com/store/apps/details?id=com.google.android.apps.accessibility.reveal), Google Play.
34. Avni Shah, [Making Learning to Read Accessible and Fun with Bolo](https://www.blog.google/technology/ai/bolo-literacy/), The Keyword, September 9, 2019.
35. Shreyans Bhansali, [When Students Get Stuck, Socratic Can Help](https://www.blog.google/outreach-initiatives/education/socratic-by-google/), The Keyword, August 15, 2019.
36. Leon A. Gatys, Alexander S. Ecker, and Matthias Bethge, [A Neural Algorithm of Artistic Style](https://arxiv.org/abs/1508.06576), arXiv (2015); and Vincent Dumoulin, Jonathon Shlens, and Manjunath Kudlur, [Supercharging Style Transfer](https://ai.googleblog.com/2016/10/supercharging-style-transfer.html), Google AI Blog, October 26, 2016.
37. [DALL·E: Creating Images from Text](https://openai.com/blog/dall-e/), OpenAI.
38. [Magenta](https://research.google/teams/brain/magenta/), Google Research Team.
39. Jakub Konečný, Brendan McMahan, and Daniel Ramage, [Federated Optimization: Distributed Optimization beyond the Datacenter](https://arxiv.org/abs/1511.03575), arXiv (2015).
40. Keith Bonawitz, Hubert Eichner, Wolfgang Grieskamp, et al., [Towards Federated Learning at Scale: System Design](https://arxiv.org/abs/1902.01046), arXiv (2019). For a less technical description on how the technology works, you can also check out this online comic description: [Federated Learning: Building Better Products with On-Device Data and Privacy by Default](https://federated.withgoogle.com/), Google AI.
41. Sashank Reddi, Zachary Charles, Manzil Zaheer, et al., [Adaptive Federated Optimization](https://arxiv.org/abs/2003.00295), arXiv (2020); Sai Praneeth Karimireddy, Martin Jaggi, Satyen Kale, et al., [Mime: Mimicking Centralized Stochastic Algorithms in Federated Learning](https://arxiv.org/abs/2008.03606), arXiv (2020); and James Bell, K. A. Bonawitz, Adrià Gascón, et al., [Cryptology ePrint Archive: Report 2020/704](https://eprint.iacr.org/2020/704), in *CCS ’20: Proceedings of the 2020 ACM SIGSAC Conference on Computer and Communications Security* (New York: Association for Computing Machinery, 2020).
42. Ashish Vaswani, Noam Shazeer, Niki Parmar, et al., [Attention Is All You Need](https://arxiv.org/abs/1706.03762), arXiv (2017); Jakob Uszkoreit, [Transformer: A Novel Neural Network Architecture for Language Understanding](https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html), Google AI Blog, August 31, 2017; Neil Houlsby and Dirk Weissenborn, [Transformers for Image Recognition at Scale](https://ai.googleblog.com/2020/12/transformers-for-image-recognition-at.html), Google AI Blog, December 3, 2020; Dirk Weissenborn, Oscar Täckström, and Jakob Uszkoreit, [Scaling Autoregressive Video Models](https://arxiv.org/abs/1906.02634), arXiv (2019); Anmol Gulati, James Qin, Chung-Cheng Chiu, et al., [Conformer: Convolution-Augmented Transformer for Speech Recognition](https://arxiv.org/abs/2005.08100), arXiv (2020); and AlphaFold Team, [AlphaFold: A Solution to a 50-Year-Old Grand Challenge in Biology](https://deepmind.com/blog/article/alphafold-a-solution-to-a-50-year-old-grand-challenge-in-biology), DeepMind, November 30, 2020.
43. Kyle Lo, Iz Beltagy, Arman Cohan, et al., [Scibert](https://github.com/allenai/scibert), GitHub, last updated June 14, 2020.
44. Maithra Raghu and Eric Schmidt, [A Survey of Deep Learning for Scientific Discovery](https://arxiv.org/abs/2003.11755), arXiv (2020).
45. [MLSys–2020](https://mlsys.org/), Fifth Conference on Machine Learning and Systems, Santa Clara, California, April 11–14, 2020.
46. Tim Kraska, Alex Beutel, Ed H. Chi, et al., [The Case for Learned Index Structures](https://arxiv.org/abs/1712.01208), arXiv (2017); Ani Kristo, Kapil Vaidya, Ugur Çetintemel, et al., [The Case for a Learned Sorting Algorithm](https://dl.acm.org/doi/abs/10.1145/3318464.3389752), in *SIGMOD ’20: Proceedings of the 2020 ACM SIGMOD International Conference on Management of Data* (New York: Association for Computing Machinery, 2020); Samuel J. Kaufman, Phitchaya Mangpo Phothilimthana, Yanqi Zhou, et al., [A Learned Performance Model for Tensor Processing Units](https://arxiv.org/abs/2008.01040), arXiv (2020); Yanqi Zhou and Sudip Roy, [End-to-End, Transferable Deep RL for Graph Optimization](https://ai.googleblog.com/2020/12/end-to-end-transferable-deep-rl-for.html), Google AI Blog, December 17, 2020; and Martin Maas, David G. Andersen, Michael Isard, et al., [Learning-Based Memory Allocation for C++ Server Workloads](https://research.google/pubs/pub49008/), *Proceedings of the 25th ACM International Conference on Architectural Support for Programming Languages and Operating Systems (ASPLOS)* (New York: Association for Computing Machinery, 2020).
47. Vaswani et al., “Attention Is All You Need.”
48. Ibid., Table 4.
49. Barret Zoph and Quoc V. Le, [Neural Architecture Search with Reinforcement Learning](https://arxiv.org/abs/1611.01578), arXiv (2016); Hieu Pham, Melody Guan, Barret Zoph, et al., [Efficient Neural Architecture Search via Parameters Sharing](http://proceedings.mlr.press/v80/pham18a.html), *Proceedings of Machine Learning Research* 80 (2018); Adam Gaier and David Ha, [Weight Agnostic Neural Networks](https://arxiv.org/abs/1906.04358), arXiv (2019); and Esteban Real, Sherry Moore, Andrew Selle, et al., [Large-Scale Evolution of Image Classifiers](https://arxiv.org/abs/1703.01041), arXiv (2017).
50. Jacob Devlin, Ming-Wei Chang, Kenton Lee, and Kristina Toutanova, [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805), arXiv (2018).
51. Carl Doersch and Andrew Zisserman, [Multi-Task Self-Supervised Visual Learning](https://arxiv.org/abs/1708.07860), arXiv (2017); and Sebastian Ruder, [An Overview of Multi-Task Learning in Deep Neural Networks](https://arxiv.org/abs/1706.05098), arXiv (2017).
52. Vaswani et al., “Attention Is All You Need.”
53. Pham et al., “Efficient Neural Architecture Search via Parameters Sharing.”
54. [Artificial Intelligence at Google: Our Principles](https://ai.google/principles/), Google AI.
