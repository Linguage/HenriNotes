Git 使用指南
    
- 原文标题：The guide to Git I never had.. 🩺 Doctors have stethoscopes.
    
- 链接：[The guide to Git I never had](https://medium.com/@jake.page91/the-guide-to-git-i-never-had-a89048d4703a)
    
- **文章类别**：博客文章
    

---

**内容整理**：

### 文章框架与要点

markdown复制

```markdown
├── 引言
│   ├── Git的重要性
│   └── 目标
├── Git的基础概念
│   ├── 分支（Branches）
│   ├── 提交（Commits）
│   ├── 标签（Tags）
│   ├── HEAD
│   ├── 阶段（Stages）
│   │   ├── 工作目录（Working directory）
│   │   ├── 暂存区（Staging area）
│   │   ├── 本地仓库（Local repository）
│   │   └── 远程仓库（Remote repository）
├── Git的基本操作
│   ├── 初始化仓库（git init）
│   ├── 设置凭证（Credentials set up）
│   ├── 分支操作（Working with branches）
│   ├── 提交操作（Working with commits）
│   ├── 操作历史（Manipulating History）
│   │   ├── 变基（Rebasing）
│   │   ├── 合并（Merging）
│   │   ├── 压缩提交（Squashing）
│   │   └── 拣选提交（Cherry-picking）
├── 高级Git命令
│   ├── 签名提交（Signing commits）
│   ├── Git reflog
│   ├── 交互式变基（Interactive rebase）
├── Git协作
│   ├── 源仓库与上游仓库（Origin vs Upstream）
│   ├── 解决冲突（Conflicts）
│   ├── 流行的Git工作流（Popular Git workflows）
│   │   ├── 功能分支工作流（Feature Branch Workflow）
│   │   ├── Gitflow工作流（Gitflow Workflow）
│   │   ├── Forking工作流（Forking Workflow）
│   │   ├── Pull Request工作流（Pull Request Workflow）
│   │   └── 主干开发（Trunk-Based Development）
├── Git备忘单（Cheatsheet）
├── 额外工具与资源（Bonus! Some Git tools and resources to make your life easier）
```

### 文章标签：

#Git #版本控制 #编程 #开发工具

---

**内容整理**：

### 引言

#### Git的重要性

- Git 是开发者日常工作中不可或缺的工具之一。
    
- 掌握 Git 的功能和特性是开发者最好的投资之一。
    

#### 目标

- 本文旨在提供一个 Git 基础指南，帮助读者更好地理解和使用 Git。
    

### Git的基础概念

#### 分支（Branches）

- 分支代表同时进行的工作流，允许开发者在同一个项目中并行处理多个功能或修复。
    

#### 提交（Commits）

- 提交是代码更新的包，记录了项目在特定时间点的代码快照。
    
- 每个提交都有一个唯一的加密哈希值。
    

#### 标签（Tags）

- 标签用于标记项目开发中的重要里程碑，如发布版本或重要提交。
    

#### HEAD

- HEAD 指向当前检出的分支的最新提交。
    

#### 阶段（Stages）

- **工作目录（Working directory）**：本地机器上当前文件的状态。
    
- **暂存区（Staging area）**：准备提交的更改区域。
    
- **本地仓库（Local repository）**：本地存储的提交历史。
    
- **远程仓库（Remote repository）**：共享和协作的集中存储位置。
    

### Git的基本操作

#### 初始化仓库（git init）

- 将一个本地文件夹初始化为 Git 仓库。
    

#### 设置凭证（Credentials set up）

- 配置 Git 凭证以避免每次推送或拉取时输入用户名和密码。
    

#### 分支操作（Working with branches）

- 创建、切换和查看分支的命令。
    

#### 提交操作（Working with commits）

- 提交更改、修改最近一次提交、遵循提交信息规范。
    

#### 操作历史（Manipulating History）

- **变基（Rebasing）**：重写提交历史。
    
- **合并（Merging）**：生成新的合并提交，保留分支历史。
    
- **压缩提交（Squashing）**：将多个提交压缩为一个。
    
- **拣选提交（Cherry-picking）**：选择性地将某个提交应用到另一个分支。
    

### 高级Git命令

#### 签名提交（Signing commits）

- 使用 GPG 密钥对提交进行签名，以验证提交的真实性和完整性。
    

#### Git reflog

- 用于恢复丢失的提交或分支，调试和排除故障，撤销错误操作。
    

#### 交互式变基（Interactive rebase）

- 允许交互式地重写提交历史，修改、重新排序、合并或删除提交。
    

### Git协作

#### 源仓库与上游仓库（Origin vs Upstream）

- **源仓库（Origin）**：默认的远程仓库。
    
- **上游仓库（Upstream）**：原始仓库，用于保持与原项目的同步。
    

#### 解决冲突（Conflicts）

- 合并或变基时检测到冲突，手动解决冲突并保存更改。
    

#### 流行的Git工作流（Popular Git workflows）

- **功能分支工作流（Feature Branch Workflow）**：每个新功能或修复在独立分支上开发，完成后合并到主分支。
    
- **Gitflow工作流（Gitflow Workflow）**：严格的分支模型，适用于有计划发布和长期维护的项目。
    
- **Forking工作流（Forking Workflow）**：每个开发者克隆主仓库，在自己的分叉上进行开发，然后通过拉取请求合并。
    
- **Pull Request工作流（Pull Request Workflow）**：开发者在主仓库中创建功能分支，通过拉取请求进行代码审查和协作。
    
- **主干开发（Trunk-Based Development）**：开发者直接在主分支上工作，频繁提交小的更改。
    

### Git备忘单（Cheatsheet）

- 常用 Git 命令的备忘单。
    

### 额外工具与资源（Bonus! Some Git tools and resources to make your life easier）

- 交互式变基工具、彩色增量差异查看工具、交互式 Git 分支练习平台等。
    

---

以上是对文章《The guide to Git I never had.. 🩺 Doctors have stethoscopes.》的详细整理与笔记。