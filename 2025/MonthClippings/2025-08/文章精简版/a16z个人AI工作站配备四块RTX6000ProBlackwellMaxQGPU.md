# Building a16z’s Personal AI Workstation with four NVIDIA RTX 6000 Pro Blackwell Max-Q GPUs

**链接**: https://a16z.com/building-a16zs-personal-ai-workstation-with-four-nvidia-rtx-6000-pro-blackwell-max-q-gpus/

**标签**: #AI硬件 #GPU #工作站 #RTX6000 #Blackwell #AI计算 #本地AI #a16z #深度学习 #硬件构建

**概要**:
本文介绍了由a16z（Andreessen Horowitz）构建的一款高性能个人AI工作站。该工作站的核心是4块全新的NVIDIA RTX 6000 Pro Blackwell Max-Q GPU，每块GPU拥有96GB显存，总显存高达384GB。其设计旨在为研究人员、开发者和工程师提供本地化的强大AI计算能力，以应对基础模型、多模态AI和大型数据集带来的挑战，同时避免云服务的延迟、设置开销和隐私问题。工作站配置包括：AMD Ryzen Threadripper PRO 7975WX CPU（32核64线程）、256GB ECC DDR5内存、8TB PCIe 5.0 NVMe SSD存储（RAID 0配置理论读取速度可达59.6GB/s）、1650W金牌电源，并配备Baseboard Management Controller (BMC)用于远程管理。其关键优势在于每块GPU都独占完整的PCIe 5.0 x16通道，确保最大带宽；支持未来的NVIDIA GPUDirect Storage (GDS)技术以实现数据直接流式传输至显存；且功耗峰值仅为1650W，可使用标准家用电路。该工作站适用于训练和微调参数高达数百亿的大型语言模型、运行密集的多模态推理、实验模型并行计算等场景，是数据中心级算力与桌面级可访问性之间的良好平衡。
