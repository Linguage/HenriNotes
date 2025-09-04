# Agentic Browser Security: Indirect Prompt Injection in Perplexity Comet | Brave

**链接**: https://brave.com/blog/comet-prompt-injection/

**标签**: #AI安全 #浏览器安全 #提示注入 #隐私保护 #AI代理 #网络安全 #Brave #Perplexity

**概要**:
本文由Brave浏览器团队发布，揭示了在AI代理浏览器（如Perplexity的Comet和Brave的Leo）中存在的一种新型严重安全漏洞——间接提示注入（Indirect Prompt Injection）。传统Web安全机制（如同源策略）在AI代理浏览模式下面临失效风险。攻击者可在网页内容中隐藏恶意指令（如在社交媒体评论中），当用户使用AI助手的“总结页面”功能时，AI会将这些恶意指令与用户请求一同处理，并可能将其误认为是用户的命令去执行，例如访问用户的邮箱、读取OTP（一次性密码）并将其发送给攻击者，从而实现账户劫持。文章详细演示了这一攻击过程，并强调了AI代理浏览器需要全新的安全和隐私架构。Brave提出了几种可能的缓解策略，包括浏览器应区分用户指令和网页内容、模型应对任务进行用户对齐检查、以及将代理浏览模式与常规浏览隔离。研究旨在提升整个行业的AI代理浏览安全标准。
