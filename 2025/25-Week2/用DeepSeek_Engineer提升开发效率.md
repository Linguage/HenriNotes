用DeepSeek Engineer提升开发效率
- 原文标题：用DeepSeek打造你的超强代码助手
- 链接：[用DeepSeek打造你的超强代码助手](https://mp.weixin.qq.com/s/i-cQq9uv4ujNfGROnoPs2A)

- **文章类别**：博客

---

**内容整理**：

```markdown
├── 文章简介
│   ├── 作者：老码小张
│   ├── 发布时间：2025年01月01日 08:30
│   └── 地点：广东
├── DeepSeek Engineer介绍
│   ├── 定义：基于命令行的智能助手应用，可读文件、改文件、生成代码，基于DeepSeek API
│   └── 功能
│       ├── 快速读文件内容
│       ├── 自动改文件，生成差异表并自动应用修改
│       └── 智能代码生成，按指定格式和规则返回代码片段
├── 核心功能拆解
│   ├── 自动配置DeepSeek客户端
│   │   └── 通过.env文件配置API Key，自动连接到DeepSeek服务器
│   ├── 数据模型：使用Pydantic定义和管理，包括FileToCreate、FileToEdit、AssistantResponse
│   ├── 强大的系统Prompt，引导输出结构化的JSON数据，支持文件创建和编辑操作
│   ├── 常用Helper函数
│   │   ├── read_local_file：读取本地文件内容
│   │   ├── create_file：新建或覆盖文件
│   │   ├── show_diff_table：生成差异表展示文件修改前后对比
│   │   └── apply_diff_edit：应用代码片段级别的修改
│   └── 交互式会话
│       ├── 运行主程序进入命令行界面
│       ├── 可加载文件、提出需求，让助手生成代码或修改建议
├── 与其他工具对比
│   ├── 对比对象：GitHub Copilot、TabNine
│   ├── 对比维度及结果
│   │   ├── 文件内容读取：DeepSeek Engineer支持，其他两者不支持
│   │   ├── 文件修改和应用：DeepSeek Engineer支持，其他两者不支持
│   │   ├── JSON响应结构化：DeepSeek Engineer内置支持，其他两者不支持
│   │   ├── 离线使用：DeepSeek Engineer需联网，TabNine部分支持
│   │   └── 灵活性和可定制性：DeepSeek Engineer可配置Prompt，其他两者不支持
├── 快速上手指南
│   ├── 准备环境
│   │   ├── 安装依赖：pip install -r requirements.txt
│   │   └── 配置API Key：创建.env文件写入Key
│   ├── 启动工具：运行python3 main.py
│   ├── 体验功能
│   │   ├── 加载文件：/add your_file.py
│   │   └── 提出需求，生成代码或修改建议
│   └── 探索更多用法：修改配置，自定义连接方式
└── 引用链接
    └── DeepSeek Engineer项目地址：https://github.com/bravekingzhang/deepseek-engineer
```

### 对比
以下是文章中提到的DeepSeek Engineer与其他工具对比的表格化输出：

| 功能        | DeepSeek Engineer | GitHub Copilot | TabNine |
| --------- | ----------------- | -------------- | ------- |
| 文件内容读取    | ✅ 支持              | ❌ 不支持          | ❌ 不支持   |
| 文件修改和应用   | ✅ 支持              | ❌ 不支持          | ❌ 不支持   |
| JSON响应结构化 | ✅ 内置支持            | ❌ 不支持          | ❌ 不支持   |
| 离线使用      | ❌ 需要联网            | ❌ 需要联网         | ✅ 部分支持  |
| 灵活性和可定制性  | ✅ 可配置Prompt       | ❌ 不支持          | ❌ 不支持   |
