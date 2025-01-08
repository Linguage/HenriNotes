开发者必备的CLI/TUI工具
- 原文标题：Essential CLI/TUI Tools for Developers
- 链接：[https://itnext.io/essential-cli-tui-tools-for-developers-7e78f0cd27db](https://itnext.io/essential-cli-tui-tools-for-developers-7e78f0cd27db)

- **文章类别**：博客

---
**内容整理**： 

这篇文章由Alex Pliutau撰写，主要介绍了一些开发者在日常工作中可以使用的命令行界面（CLI）和文本用户界面（TUI）工具。这些工具可以提高开发者的工作效率，或为开发过程增添乐趣。文章按照不同的功能对工具进行了分类，以下是详细整理：

| **类别**         | **工具及链接**                                                 | **描述**                                              |
| -------------- | --------------------------------------------------------- | --------------------------------------------------- |
| **Kubernetes** | [k9s](https://github.com/derailed/k9s)                    | 提供一个终端用户界面，用于与Kubernetes集群交互，便于导航和管理应用。             |
|                | [ktop](https://github.com/vladimirvivien/ktop)            | 类似于Unix/Linux的top工具，显示Kubernetes集群中节点、Pods等的有用指标信息。 |
|                | [kubectx](https://github.com/ahmetb/kubectx)              | 快速切换kubectl上下文（集群）。                                 |
|                | [kdash](https://github.com/kdash-rs/kdash)                | 一个简单快速的Kubernetes仪表板。                               |
|                | [kubescape](https://github.com/kubescape/kubescape)       | Kubernetes安全平台，提供全面的安全覆盖。                           |
| **容器**         | [ctop](https://github.com/bcicen/ctop)                    | 提供多个容器的实时指标概览。                                      |
|                | [lazydocker](https://github.com/jesseduffield/lazydocker) | 一个简单的终端UI，用于Docker和docker-compose。                  |
|                | [dive](https://github.com/wagoodman/dive)                 | 用于探索Docker镜像每一层的工具。                                 |
| **文件/文本**      | [jq](https://github.com/jqlang/jq)                        | 命令行JSON处理器。                                         |
|                | [bat](https://github.com/sharkdp/bat)                     | 增强版的cat命令，支持语法高亮和git集成。                             |
|                | [ripgrep](https://github.com/BurntSushi/ripgrep)          | 递归搜索目录中的正则表达式模式。                                    |
|                | [rsync](https://github.com/RsyncProject/rsync)            | 快速且极其灵活的文件复制工具。                                     |
| **Git**        | [lazygit](https://github.com/jesseduffield/lazygit)       | 简单的终端UI，用于git命令。                                    |
|                | [gitui](https://github.com/extrawurst/gitui)              | 快速的终端UI，用于git。                                      |
| **开发**         | [ATAC](https://github.com/Julien-cpsn/ATAC)               | 终端中的简单API客户端。                                       |
|                | [vegeta](https://github.com/tsenart/vegeta)               | HTTP负载测试工具和库。                                       |
|                | [httpie](https://github.com/httpie/cli)                   | 现代用户友好的命令行HTTP客户端。                                  |
| **网络**         | [dog](https://github.com/ogham/dog)                       | 命令行DNS客户端。                                          |
|                | [gping](https://github.com/orf/gping)                     | 可视化的ping工具。                                         |
| **工作站**        | [tmux](https://github.com/tmux/tmux/wiki)                 | 终端复用器，允许多个终端在一个屏幕上创建和控制。                            |
|                | [zellij](https://github.com/zellij-org/zellij)            | 一个集成了多种功能的终端工作区。                                    |
|                | [btop](https://github.com/aristocratos/btop)              | 资源监控工具，显示处理器、内存、磁盘、网络和进程的使用情况。                      |
|                | [chezmoi](https://github.com/twpayne/chezmoi)             | 安全地管理多个机器上的dotfiles。                                |


### 结论
文章总结了多种CLI/TUI工具，强调了它们在现代开发中的重要性，并推荐了作者个人使用的Ghostty终端。整体来看，这些工具能够显著提高开发者的工作效率，值得开发者们尝试和使用。
