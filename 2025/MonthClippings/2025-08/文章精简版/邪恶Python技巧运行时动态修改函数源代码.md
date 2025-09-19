# Wicked Python trickery - dynamically patch a Python function's source code at runtime

## 链接
https://ericmjl.github.io/blog/2025/8/23/wicked-python-trickery-dynamically-patch-a-python-functions-source-code-at-runtime/

## 概要
这篇文章介绍了作者 Eric J. Ma 发现的一个强大但危险的 Python 技巧：在运行时动态地更改 Python 函数的源代码。该技巧利用 `compile` 和 `exec` 函数，能够将字符串形式的函数定义编译成字节码并在特定的命名空间中执行，从而替换掉原有的函数实现。
作者最初是为了改进其 LLM 代理框架 LlamaBot 中的 `AgentBot` 而探索此方法。原有的 `AgentBot` 将工具选择、执行和用户响应生成混合在一个循环中，难以分离关注点。更重要的是，其原有的代码执行工具将生成的代码隔离在 Docker 容器中，虽然安全，但无法访问当前 Python 环境中的变量，限制了实用性。
基于此，作者开发了新的 `ToolBot`，它只负责工具选择，不负责执行。其中一个最强大的工具是 `write_and_execute_code`，它允许 LLM 生成 Python 函数代码，并在调用时通过 `compile` 和 `exec` 在当前运行时环境中（通过传入 `globals()` 字典）编译和执行该代码。这使得生成的代码能够直接访问和操作当前环境中的所有变量、数据和函数，极大地增强了 LLM 代理的能力，例如可以直接操作用户环境中的数据框（DataFrame）进行数据分析和可视化。
文章强调，虽然这个技巧为构建更强大的 LLM 代理（如结合 Marimo 实现生成式 UI）和动态编程打开了可能性，但它也带来了严重的安全风险。与沙箱化执行相比，直接在运行时环境中执行 LLM 生成的代码要危险得多，恶意代码可能对本地机器和外部世界造成巨大损害。作者承认目前尚未实现代码净化，并计划未来使用如 Restricted Python 等技术来增强安全性。作者总结道，这个技巧让他认识到 Python 运行时的可塑性、LLM 代理设计中系统设计的重要性，以及通过 LLM 进行自学的价值。

## 标签
#Python #编程技巧 #动态编程 #LLM #AI代理 #LlamaBot #ToolBot #代码执行 #安全 #元编程