数据处理引擎革新企业AI基础设施

  

**概述**

  

本文介绍了加州初创公司 DataPelago 推出的数据处理引擎 Nucleus。Nucleus 能显著提升 AI 和分析领域的数据处理速度，甚至在 Nvidia 自家硬件上超越了 Nvidia 的 cuDF 库。Nucleus 不仅性能卓越，还具备硬件中立性，能够兼容多种硬件环境，打破了传统 GPU 软件的性能天花板。文章分析了 Nucleus 的技术突破、对企业和行业的影响，以及未来 AI 基础设施的发展趋势。

  

**GPU****数据处理的现状与挑战**

- 多年来，企业依赖 GPU（图形处理单元）来处理日益增长的数据量，利用其并行计算能力推动 AI 和分析工作负载。无论是生成式 AI 模型、推荐引擎还是分析仪表盘，都离不开高效的数据处理库来准备、连接和转换海量数据集。
- 然而，行业面临一个隐性难题：硬件不断进步，但软件栈却难以充分发挥硬件潜力。许多传统数据处理库最初为 CPU 优化，导致 GPU 的内存带宽和计算吞吐量未被充分利用。数据在 CPU 与 GPU 之间频繁传输时，性能优势也会大打折扣。
- Nvidia 于 2018 年推出了 cuDF（GPU 加速 DataFrame 库），作为其开源 RAPIDS 套件的一部分。cuDF 成为数据操作的行业标准，显著提升了速度和 GPU 利用率。
- 但 cuDF 也有局限：它需要 Nvidia GPU、充足的显存和 CUDA 支持，限制了硬件环境的选择。cuDF 成为行业的性能上限，虽能加速 AI 和分析流程，但受限于 GPU 架构的特性。

  

**Nucleus****引擎的技术突破与性能表现**

- DataPelago 推出的 Nucleus 数据处理引擎，号称突破了 cuDF 的性能瓶颈。Nucleus 构建于 Nvidia 硬件之上，但在基准测试中表现远超 cuDF：在哈希连接（hash join）操作上快 38.6 倍，排序快 8 倍，过滤和投影快 10 倍（注：均为官方测试数据）。
- DataPelago CEO Rajan Goyal 指出，要充分发挥 GPU 优势，数据处理引擎必须既利用硬件强项，又弥补其短板，这需要为数据工作负载量身定制新算法。
- Nucleus 的性能提升不仅是技术炫技，更有实际意义。云端 GPU 昂贵，企业需最大化每一计算周期。更快的数据处理意味着更低的云成本和更快的洞察速度。Nucleus 设计为可在任何硬件上运行，支持任意数据类型，并能无缝集成现有框架，无需更改客户应用。
- Goyal 强调：“我们可以直接嵌入开发者现有环境。”这意味着企业无需大规模更换基础设施即可享受性能提升。
- Nucleus 的基准测试在标准公有云服务器上进行，涵盖入门级 Tesla T4 和高端 H100 GPU，模拟真实场景：数据从 CPU 传输到 GPU，处理后再返回主机。测试中，Nucleus 与 cuDF 在核心 AI 和分析操作上正面较量，均使用同一数据集和测试工具。
- Nucleus 通过重构执行层，支持复杂工作负载，包括内核融合（kernel fusion）、原生多列支持和对变长数据（如字符串）的优化处理。虽然 Nucleus 仍运行在 Nvidia CUDA 框架和 GPU 上，但其性能却高于 Nvidia 自家技术。
- DataPelago 总裁 JG Chirapurath 表示，Nucleus 能让企业“从现有硬件投资中获得更高性能”，并强调企业更倾向于在现有基础上升级，而非彻底更换系统。
- Goyal 认为，cuDF 与 Nvidia GPU 生态深度绑定，导致厂商锁定（vendor lock-in），限制了硬件灵活性和开放创新。Nucleus 则设计为兼容任何硬件（不仅限于 GPU），支持任意数据类型和查询引擎，旨在提升所有硬件的性能上限。其内置智能可自动将数据操作映射到最合适的硬件，并动态重配置任务以最大化性能。

  

**企业****AI****基础设施的硬件中立新趋势**

- 如果 DataPelago 的方法被广泛采纳，企业在构建 AI 基础设施时可能会优先考虑通用性和效率，而非单一厂商生态。分析师指出，基准测试结果在实际生产环境中未必完全复现，且硬件格局若快速变化也存在风险。
- Forrester 高级分析师 Alvin Nguyen 认为，Nucleus 对希望避免厂商锁定的企业有吸引力。但随着 AMD 推出针对数据中心 GPU 的 CUDA 转译工具，真正的优势在于能同时支持 CPU 和 FPGA（现场可编程门阵列）。目前有大量开发者熟悉 Nvidia 生态，转向其他平台短期内需投入更多资源。
- Nguyen 还指出，基于 Transformer 的工作负载（如大型基础模型训练）进展已不如往年，推理（inferencing）开始超过训练成为主流，GPU 的原始算力不再是唯一驱动力。更均衡地看待软件层是明智之举。
- 投资者已开始布局。DataPelago 获得 Eclipse、Qualcomm Ventures 和 Taiwania Capital 的种子及 A 轮融资共 4700 万美元，并聘请行业资深人士 JG Chirapurath 担任总裁。CEO Goyal 曾在 Cisco 和 Oracle 工作，后创办 DataPelago。
- 多年来，AI 行业关注芯片短缺和 GPU 性能竞赛。Nucleus 指向另一种竞争模式：最大性能提升来自软件而非硬件，未来战场或将从芯片制造转向算法创新。AI 基础设施的未来，或许不在于造更大的芯片，而在于重新思考如何利用现有硬件。
- Chirapurath 表示：“硬件中立不仅是技术能力，更是战略差异化。企业希望基础设施投资能在技术演进中持续保值。”他的长期愿景是将 DataPelago 打造成通用数据处理基础，加速未来十年 AI 和分析创新，让原本不可能的应用变得经济可行。

  

**框架与心智模型**

- **硬件中立性（****Hardware Neutrality****）**：Nucleus 的设计理念是兼容多种硬件（GPU、CPU、FPGA），不依赖单一厂商生态，避免厂商锁定。这一框架强调基础设施的灵活性和可持续性，使企业能根据技术发展自由选择硬件。
- **软件优先（****Software Over Silicon****）**：文章提出，未来 AI 基础设施的性能提升将更多依赖于软件创新而非硬件升级。企业应关注算法和数据处理引擎的优化，而不是一味追求更强的芯片。
- **无缝集成（****Seamless Integration****）**：Nucleus 能直接嵌入现有开发环境，无需大规模更换系统。这一心智模型强调技术升级的低门槛和高兼容性，降低企业转型成本。
- **动态任务分配（****Dynamic Task Allocation****）**：Nucleus 内置智能，可自动将数据操作分配到最合适的硬件，并根据实际情况动态调整任务配置，最大化性能。这一框架体现了智能化和自动化在现代数据处理中的重要性。
- **性能上限突破（****Breaking Performance Ceilings****）**：Nucleus 通过新算法和架构设计，突破了传统 GPU 数据处理的性能瓶颈，为企业带来数量级的效率提升。这一心智模型鼓励技术团队不断挑战现有极限，寻求创新突破。

  

**基本信息**

- Title: This startup claims it just outran Nvidia on its own turf
- Author: Harry McCracken
- Date: August 21, 2025
- URL: https://www.fastcompany.com/91389650/this-startup-claims-it-just-outran-nvidia-on-its-own-turf