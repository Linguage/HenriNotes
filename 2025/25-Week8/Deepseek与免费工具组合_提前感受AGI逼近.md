Deepseek与免费工具组合：提前感受AGI逼近  
  原文标题：一秒超神：Deepseek + 这两个免费工具！提前感受 AGI 逼近  
  链接：[原文链接](https://mp.weixin.qq.com/s/PuHwfJk3EZv8eR4y10EAvQ)  

- **文章类别**：博客  

---

**文章框架**：  
```
├── 引言：介绍Deepseek与免费工具组合的强大功能
│   ├── 场景举例：AI自动写邮件、查找重复文件等
│   └── 工具组合：VS code + Cline插件 + Deepseek API
├── VS code介绍
│   ├── 官方网站
│   └── 插件生态系统
├── Cline插件
│   ├── 功能特点
│   └── 支持的模型与API
├── Deepseek与替代方案
│   ├── Deepseek官网API
│   ├── 火山引擎API
│   │   ├── 注册链接与邀请码
│   │   ├── 配置步骤
│   └── 其他替代API
├── MCP协议与插件服务
│   ├── MCP协议简介
│   ├── Smithery.ai服务
│   └── Awesome MCP Server GitHub库
└── 结语：推荐使用与交流
```

**内容整理**：  

文章介绍了如何通过组合使用Deepseek和两个免费工具（VS code和Cline插件）来实现强大的AI功能，提前感受AGI（通用人工智能）的逼近。以下是详细内容整理：

1. **引言**  
   文章开篇通过列举几个场景，展示了AI工具的强大潜力，例如：
   - 让AI自动打开浏览器写邮件并发送；  
   - 查找并删除电脑中的重复文件；  
   - 抓取网页内容并翻译成双语文档；  
   - 读取本地Obsidian笔记并改写为适合小红书或X平台的风格发布。  
   这些功能并非遥不可及，而是可以通过以下工具组合实现：VS code + Cline插件 + Deepseek API。

2. **VS code介绍**  
   - VS code是微软出品的开源代码编辑器，网址为：[https://code.visualstudio.com/](https://code.visualstudio.com/)。  
   - 它是目前最流行的AI编程工具基础，许多工具如Cursor、Windsurf、Trae等都是基于VS code二次开发的。  
   - 如果不想订阅付费工具，或者希望灵活自定义，文章推荐使用VS code上的Cline插件。

3. **Cline插件**  
   - Cline是目前最好用的AI编程工具之一，在Open Router的日排行、周排行和月排行中，Cline都是调用模型最多的工具。  
   - 它支持Ollama本地部署的模型，也支持云端主流大模型和OpenAI兼容协议，因此可以调用硅基流动、火山引擎或自行中转的LLM API。  
   - 安装方法：下载并安装VS Code后，点击左侧插件图标，搜索“Cline”并安装。

4. **Deepseek与替代方案**  
   - 如果Deepseek官网的API不稳定，可以使用其他三方Host API，如火山引擎、硅基流动、Openrouter、TogetherAI等。  
   - 火山引擎最近有活动，注册送几十万Token，文章提供了邀请码（3CT2B6KQ）和注册链接：[火山引擎注册链接](https://www.volcengine.com/experience/ark?utm_term=202502dsinvite&ac=DSASUQY5&rc=3CT2B6KQ)。  
   - 配置火山引擎API的步骤：  
     1. 在线推理→创建推理接入点，创建API key和模型ID。  
     2. 复制Base URL、Model ID和API Key。  
     3. 打开Cline插件，填写上述获取的信息。

5. **MCP协议与插件服务**  
   - 大模型虽然强大，但如果不联网或缺乏外部数据，实用性会大打折扣。例如，大模型无法回答“今天北京天气”这样的问题。  
   - Anthropic公司推出了一套MCP（Model Calling Protocol）协议，允许LLM调用和安装插件。  
   - 文章推荐了一个提供MCP服务的网站：[Smithery.ai](https://smithery.ai/)，用户只需复制安装命令即可为LLM添加网页搜索、数据库操作、本地文件编辑等功能。  
   - 另一个资源是GitHub库：[Awesome MCP Server](https://github.com/appcypher/awesome-mcp-servers?tab=readme-ov-file)，其中包含了常见的插件，对个人用户来说，搜索和笔记类插件非常实用。

6. **结语**  
   文章最后强烈推荐这套工具组合，鼓励读者体验后分享有趣的应用场景。

**文章标签**：  
#Deepseek ， #VScode ， #Cline ， #AGI