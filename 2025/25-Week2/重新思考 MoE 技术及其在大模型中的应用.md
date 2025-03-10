重新思考 MoE 技术及其在大模型中的应用
- 原文标题：重新思考 MoE
- 链接：[重新思考 MoE](https://mp.weixin.qq.com/s/p7C9zXZRY5iE0Q-d8GRkaQ) 

- **文章类别**：博客文章

---

## 内容整理

### 文章框架

```
├── 引言
│   ├── 作者对 MoE 的初步点评回顾
│   └── 内部世界模型的概念阐述
├── GShard MoE 架构
│   ├── 架构目标与组成
│   ├── 计算分区与模型扩展
│   └── 架构示意图与优势
├── DeepSeek MoE 架构
│   ├── 架构潜力与问题分析
│   ├── 细粒度专家分段策略
│   └── 共享专家隔离策略
├── DeepSeek-V3 架构
│   ├── 架构创新与优势
│   ├── MLA 与负载均衡策略
│   └── 性能表现
├── RPC-Attention
│   ├── 核 PCA 框架与自注意力推导
│   └── RPC-Attention 的鲁棒性
├── 去噪混合专家 MoDE
│   ├── MoDE 架构与策略
│   ├── 计算效率与泛化能力
│   └── 训练与推理优化
└── MoE 本质探讨
    ├── 采样策略视角
    └── LLM 认知框架关联
```

### 详细内容

#### 引言
- 作者回顾了之前对 MoE（Mixture of Experts 混合专家技术）的点评，指出如果 MoE 大模型组合模式不能在内部世界模型上做到对齐和互换，其输出将是一个人格分裂的结果。
- 内部世界模型指的是麻省理工学者讲的“现实的共享统计模型”，也等同于作者所说的“以概率为表征的丰富范畴”，模型越大越丰富越准确。

#### GShard MoE 架构
- **架构目标与组成**：GShard 由一组轻量级标注 API 和对 XLA 编译器的扩展组成，目标是提高海量训练数据和计算资源下的模型质量，节约计算成本、降低编程难度，在并行设备上高效实现。
- **计算分区与模型扩展**：自动进行大规模计算分区，通过在模型代码中使用轻量级的分片注释来扩展 Transformer，能够支持的参数量达到万亿级。利用条件计算来扩展模型，权衡了可扩展性与成本，缓解了扩展大型神经网络对特定模型框架或工具的需求。
- **架构示意图与优势**：MoE Transformer 编码器层扩展示意图包括标准 Transformer、每隔一层的前馈层替换为 MoE 层、MoE 层在多个设备之间进行分片等。该架构在训练过程中可保持实用性和样本效率，还能提高现实世界应用的质量。

#### DeepSeek MoE 架构
- **架构潜力与问题分析**：MoE 架构潜力很大，依赖于“专家”的专精度，即每个专家获得非重叠且集中的知识。现有的 MoE 架构如 GShard 表现出知识混杂和知识冗余两个潜在问题，阻碍专精，导致无法达到理论上限性能。
- **细粒度专家分段策略**：在保持参数数量不变的情况下，通过拆分 FFN 中间隐藏维度将专家细分为更细粒度。相应地，在保持计算成本恒定的情况下，激活更多的细粒度专家，以实现更灵活和适应性更强的激活专家组合。细粒度专家分段使得多样化的知识能够更加精细地分解，并更精确地学习到不同的专家中，每个专家将保持更高水平的专精。
- **共享专家隔离策略**：将某些专家隔离出来，作为共享专家始终激活，旨在捕获并整合跨不同上下文的共享知识。通过将共享知识压缩到选出的共享专家中，将减少其他路由专家之间的冗余，提高参数效率，确保每个路由专家通过聚焦于特定领域保持专精。

#### DeepSeek-V3 架构
- **架构创新与优势**：DeepSeekMoE 架构创新为训练一个参数高效的 MoE 语言模型提供了机会，其中每个专家都具备高度专精。这一架构的优势在 DeepSeek V2 LLM 中得到了强有力的验证。DeepSeek V3 延用它来实现高效推理和经济训练，在千卡集群上高效实现 6710 亿总参数，每个 token 激活 370 亿参数。
- **MLA 与负载均衡策略**：DeepSeek-V3 采用了 MLA（Multi-head Latent Attention），并开创了一种无辅助损失的负载均衡策略，设置了多 token 预测训练目标，超越了其他开源模型，并且在性能上与领先的闭源模型相媲美。
- **性能表现**：DeepSeek 在架构上的锐意创新，不仅实现了作者强调的“内部世界模型上做到对齐和互换”，还机巧地平衡了训练和推理的算力资源，取得了重大的效能优势。

#### RPC-Attention
- **核 PCA 框架与自注意力推导**：通过引入核主成分分析（kernel PCA）推导出自注意力，展示了自注意力如何将查询向量投影到其关键矩阵在特征空间中的主成分轴上，并推导出自注意力中值矩阵的确切公式。
- **RPC-Attention 的鲁棒性**：借助该核 PCA 框架，学者提出了具有鲁棒主成分的注意力（RPC-Attention），对数据污染具有韧性鲁棒性。作者认为可以进一步平衡模型的效能。

#### 去噪混合专家 MoDE
- **MoDE 架构与策略**：卡尔斯鲁厄理工和麻省理工学院的学者们提出了 MoDE，一种混合专家（MoE）扩散策略。MoDE 使用噪声调节路由和自注意力机制，仅计算和集成每个噪声级别的必要专家，减少延迟和计算成本，实现各种噪声水平下更有效地去噪。
- **计算效率与泛化能力**：MoDE 超越了当前基于 Transformer 的最先进扩散策略，同时通过稀疏专家和噪声条件路由实现参数高效扩展，通过专家缓存将激活参数减少 40%，并将推理成本降低 90%。甚至在零样本泛化任务中优于所有基线，并表现出强大的泛化能力。
- **训练与推理优化**：训练 MoDE 后，路由器被噪声条件化，使得在推理之前可以预先计算每个噪声水平下使用的专家。这使得可以去除路由器，只保留选定的专家，从而显著提高网络效率。MoDE 与具有相同参数量的密集型 Transformer 模型的计算效率比较显示，得益于路由缓存和稀疏专家设计，MoDE 展示了更高的效率，FLOP 计数更低，推理速度更快。

#### MoE 本质探讨
- **采样策略视角**：MoE 里的“专家”是一种拟人的形象化的说法，如果全文替换成“特定范畴”，读者会发现 MoE 其实本质上是基于某种人类先验“知识”或“策略”的“跨范畴采样”：“在外部感官输入下（被提示置于某种上下文），大模型内部将限定在相应的高维语言概率空间的子空间内推理；推理是在子空间中采样，类比时跨范畴采样”。
- **LLM 认知框架关联**：作者在 LLM 认知框架中所讲的采样与变分推理，而这个 LLM 认知框架，是基于 Friston 大脑的知觉原理的合理推演。目前 MoE 可以理解为一种分布式采样策略，可以 GShard 硬编码，或进一步 DeepSeekMoE 细分，也可以如 MoDE 基于噪声更灵活调节策略，亦或引入某种优化器（类似 SQL 优化器），并最终依赖推理的 scaling law 涌现出策略。
