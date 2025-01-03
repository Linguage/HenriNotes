如何在本地运行大型语言模型（LLMs）
- **原文标题**：How I run LLMs locally
- **链接**：[How I run LLMs locally - Abishek Muthian](https://abishekmuthian.com/how-i-run-llms-locally/)

- **文章类别**：博客文章

---
**内容整理**：
Abishek Muthian在其个人博客上分享了他如何在本地运行大型语言模型（LLMs）的经验。以下是文章的详细内容整理：

### 引言
Abishek Muthian应一位HN用户的要求，记录了他如何在本地运行LLMs，并在此分享给所有人。他首先感谢了那些无名艺术家、编码者和作家，他们的工作往往是LLMs训练的基础，却常常没有得到应有的认可或补偿。

### 开始
- **资源推荐**：Abishek推荐了r/LocalLLaMA subreddit和Ollama blog作为开始运行LLMs的资源。

### 硬件要求
- **个人设备**：Abishek使用的是一台装有Linux操作系统的笔记本电脑，配备有i9处理器（32线程）、4090 GPU（16GB显存）和96GB RAM。他指出，较小的模型可以在旧的GPU或CPU上运行，尽管速度较慢且可能出现更多错误。

### 工具
- **Ollama**：一个中间件，提供Python和JavaScript库，用于运行LLMs，Abishek在Docker中使用它。
- **Open WebUI**：一个前端界面，提供熟悉的聊天界面，支持文本和图像输入，并与Ollama后端通信，将输出流回用户。
- **llamafile**：一个包含LLM的单执行文件，是开始使用本地LLMs的最简单的方式，但Abishek遇到了与dGPU卸载相关的问题。
- **图像和视频生成**：Abishek使用AUTOMATIC1111进行需要定制的图像生成，Fooocus用于简单的图像生成，ComfyUI用于具有图像生成的复杂工作流自动化。
- **代码补全**：在VSCode中使用Continue。
- **笔记查询**：在Obsidian中使用Smart Connections查询笔记。

### 模型
- **模型来源**：Abishek使用Ollama模型页面下载最新的LLMs，并使用RSS在Thunderbird上跟踪模型更新。他还使用CivitAI下载特定风格的图像生成模型。
- **模型选择**：基于性能/大小选择LLMs，当前选择的LLMs会因LLMs的快速发展而频繁变化。

### 更新
- **Docker容器更新**：使用WatchTower更新Docker容器。
- **模型更新**：在Open Web UI内更新模型。

### 微调和量化
- **个人情况**：Abishek尚未在机器上微调或量化任何模型，因为他的Intel CPU可能存在制造缺陷，不想在训练过程中长时间承受高温。

### 结论
- **本地运行LLMs的优势**：本地运行LLMs使Abishek能够完全控制自己的数据并降低响应延迟。他强调，没有开源项目和免费模型以及训练这些模型所依据的数据的原始所有者，这一切都不可能实现。
- **更新承诺**：Abishek承诺将随着使用更新的工具/模型更新这篇文章。

文章最后，Abishek还提供了他的Newsletter订阅链接，邀请读者订阅以获取他关于健康、产品开发、编程、软件工程、DIY、安全、哲学等领域的高质量内容。