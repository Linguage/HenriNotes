# Python创始人Guido van Rossum与开源传奇

## 概述

本纪录片回顾了Python编程语言从上世纪90年代初在荷兰阿姆斯特丹的一个科研所诞生，到成长为全球最受欢迎的编程语言的全过程。主线聚焦于Guido van Rossum（吉多·范罗苏姆）等核心人物的经历，剖析Python的设计理念、社区文化、开放源代码的波折、中途险些夭折的危机，以及它如何推动人工智能、数据科学和互联网企业蓬勃发展。纪录片最终总结，Python之所以能改变世界，除了简单优雅的语言本身，更源于一个包容、共享、富有乐趣和责任感的社区。

---

## Python的诞生与演化

- Python的起点离不开早期业界对“简洁易学”编程语言的渴望。Guido van Rossum最初在荷兰CWI研究所参与了ABC项目，旨在面向非专业技术人员（如艺术家等）普及编程知识。ABC虽然创新，却因传播局限（需邮寄软盘，缺乏网络）和管理层原因未能推广成功。但这段经历让Guido深刻体会到现有语言的繁琐和高门槛。
    
- 随后，Guido投身到Amoeba系统（分布式操作系统）的开发工作。他发现C语言不利于快速开发实用工具，ABC又过于抽象，无法高效与操作系统底层对接。他设想要做一门兼具脚本语言便利和底层交互能力的新语言，既要好学、好用，又要可扩展、兼容实际需求。Perl虽当时流行，但缺乏一致性和学习曲线陡峭，给了Python登场的机会。
    
- 1989年圣诞期间，Guido用“休假项目”的心态，综合ABC和自己反思，着手创造Python。他沿用ABC用缩进（indentation）控制语句分组（成为Python最鲜明特色之一），剔除不适合的部分，快速迭代开发。Python名字来源于Monty Python（英国喜剧团体），寓意编程应当有趣。
    

---

## 开源发布和社区壮大

- Python在CWI获得开源许可后，通过Usenet（早期网络公告板）分发出去。整个流程颇为繁琐，需要将代码压缩、编码、分片、多步复原。但很快，全球开发者通过电子邮件和Usenet反馈，推动语言迭代。“可读性强”“易用”成了Python最早的口碑。
    
- 1994年，在美国NIST举办的首届Python研讨会，20多位用户线下面对面交流，为Python社区奠定基调。创始社区推动了“所有人都欢迎，谁有点子谁先试”的文化。Python由此从科研、NASA等极客圈辐射到更广泛应用。
    
- 之后，Guido受邀加入美国CNRI机构，进一步专注于Python开发与维护。这一站让Python.org等基础设施诞生，并诞生了软件界著名的“BDFL”（Benevolent Dictator For Life，终身仁慈独裁者）称号，Guido成了最终技术决策者——不设冗余组织，倡导自由创新，一人拍板。
    
- Python开源许可和治理结构的独立性，保证了它不会被任何一家公司“把持”，始终为社区用户服务。Python Software Foundation（PSF）也在此背景下成立，成为推动Python发展的重要基金会。
    

---

## 核心理念与“Zen of Python”

- Python注重可读性、简洁性与实用主义。Tim Peters (Python早期贡献者) 以幽默诗歌方式总结Python哲学的“Zen of Python”（Python之禅），其中包括：
    
    - Beautiful is better than ugly.（优美胜于丑陋。）
        
    - Simple is better than complex.（简单优于复杂。）
        
    - Readability counts.（可读性很重要。）
        
    - Errors should never pass silently.（错误决不能悄无声息地掩盖。）
        
    - There should be one—and preferably only one—obvious way to do it.（应有一种，并且最好只有一种明显的办法。）
        

这些理念深深影响了后续Python功能设计、库开发乃至社区交流氛围，也让Python特别适合科学计算、AI等高度合作透明的领域。

---

## 应用扩展与数次危机

- Python之所以能持续强劲增长，是因为每一波技术浪潮——从Web开发（如Dropbox，YouTube等采用）、数据科学（Anaconda等分发包让科研用户门槛降低）、AI/ML（TensorFlow、PyTorch等主要API都用Python）——都选择了Python作为核心接口。
    
- 但Python的发展并非一帆风顺。最典型是Python 2到Python 3的大规模迁移：“破坏性升级”带来社区分裂，新特性（如所有字符串默认Unicode、二进制前缀等）让大量老项目面临重写。社区产生激烈争议（包括知名贡献者公开批评），大公司如Dropbox、Instagram（后者9-10个月迁移全站代码）示范带动，才促成逐步迁移（防止割裂与停滞）。
    
- 迁移期间，为兼容维护开发双线并行，社区发明如lib2to3、Six等迁移工具。Python 3.4、3.5后，随着新特性的吸引力提升，社区最终完成统一。深刻教训是：影响力越大、代码资产越多，技术变革阻力越强，语言治理也需要更加民主、透明。
    

---

## 社区包容力与多元实践

- Python社区刻意推动多元化与包容性。例如，PyCon会议女性演讲者比例逐年提升，从最初的1%跃升到33%-40%。PyLadies、Mentorship计划等组织培养了Mariatta Wijaya等女性核心开发者，孕育出一批新一代维护者和布道者。
    
- 包容性不仅体现在性别、年龄，更侧重于给初学者、非专业开发者、科学家、数据分析师提供平等、友善、开放的沟通氛围。Guido本人长期担任导师角色，主动招纳、培训女性与边缘群体，壮大社区影响力。
    

---

## 框架&心智模型（Framework & Mindset）

- Python治理模型：先由个人掌舵（BDFL），后过渡为五人“转型指导委员会”——一方面维持创新灵活、快速响应；一方面通过PEP（Python Enhancement Proposal，Python增强提案）机制，民主、透明决策核心变革。每一次重大决策，都可以留下详细文档，被社区充分讨论、历史可追溯。
    
- 语言进化哲学：
    
    - **拒绝对‘向后兼容’的教条执守**：Python从不承诺“永远不变”，而是不断吸纳需求变化，拥抱生态多样性。每一次演变都侧重实际问题、反复实践、开放讨论。
        
    - **实践驱动**：重点关注“实际需求”和“可用解决方案”，而非为创新而创新。典型如数据科学、AI等兴起时社区迅速拥抱新方向。
        
    - **社区主导、自下而上**：草根治理、利益相关者轮换、去中心化权力分布，使Python能够适应不同阶段的需求，迭代优化组织结构。
        
    - **包容失败、鼓励冒险**：Python遭遇过项目夭折（ABC、BeOpen等），数次关键节点靠社区自发拯救。失败和危机都成了之后成长的踏板。
        
- **核心心态**：
    
    - **开放、共享、可持续**：Python的开放源代码、开源社区、开放治理成为软件发展的范本，也让其成为学术界、工业界的桥梁。
        
    - **持续进化、应对变化**：无论技术、生态还是组织治理，都强调持续“变化”才是唯一不变的事物。不断渗透各行各业，实现普及与创新的兼顾。
        

---

## 基本信息

- Title: Python: The Documentary | An origin story
    
- Author: CultRepo（前身Honeypot）制作团队，核心人物Guido van Rossum等
    
- URL: [https://www.youtube.com/watch?v=GfH4QL4VqJ0](https://www.youtube.com/watch?v=GfH4QL4VqJ0)
    

1. [https://www.youtube.com/watch?v=GfH4QL4VqJ0](https://www.youtube.com/watch?v=GfH4QL4VqJ0)