# Do I not like Ruby anymore?

[https://sgt.hootr.club/molten-matter/maybe-i-like-python-now/](https://sgt.hootr.club/molten-matter/maybe-i-like-python-now/)

这篇文章是一位程序员对其编程语言偏好的反思，特别是对 Ruby 和 Python 态度的转变。作者曾是 Ruby 的狂热爱好者，但最近在一家主要使用 Python 的公司工作后，开始重新审视 Python，并发现它有不少吸引人的地方。

*   **对 Ruby 的热爱与失望**：
    *   作者最初被 Ruby 吸引，因为它优雅、简洁、富有表现力，设计理念深受 Smalltalk 和 Lisp 影响。Ruby 中一切都是对象，允许通过 `send` 发送消息、使用 `method_missing` 动态定义方法等特性让作者着迷。
    *   然而，作者认为近年来 Ruby 并没有发生太大变化，缺乏像 Python 的类型提示那样的革命性新特性，这让他感到有些失望和疏远。

*   **对 Python 的旧怨**：
    *   作者最初不喜欢 Python，认为它不如 Ruby 优雅。例如，Python 的 `if` 是语句而非表达式，这迫使开发者先声明变量再在 `if` 块内修改它，这与函数式编程的不变性理念相悖。
    *   Python 的 `lambda` 功能受限，早期连 `print` 都是语句，无法在 `lambda` 内使用。

*   **态度的转变**：
    *   **TypeScript 的影响**：作者在前端开发中使用 TypeScript，体验到了强大的类型系统如何弥补语言本身的不足。这让他意识到，静态分析工具可以“原谅”语言的一些设计缺陷。
    *   **自身的变化**：接触 Rust 等语言后，作者对可变性等概念的看法也发生了改变。
    *   **Python 的进化**：Python 本身也发生了巨大变化，引入了类型提示、`match` 语句（模式匹配）、将 `print` 改为函数等。作者尤其欣赏类型提示，它不仅支持类型检查，还能被 Pydantic 等库用于数据验证和 FastAPI 等库用于简化 API 开发。Python 的关键字参数、命名空间等特性也让作者感到满意。

*   **结论**：
    *   作者认为，与其说是不再喜欢 Ruby，不如说是自己和 Python 都改变了，而 Ruby 的变化未能跟上他的期待。他开始怀念在其他语言中习以为常的功能（如类型提示、关键字参数），而这些在现代 Python 中都能找到。最终，作者以一种幽默的方式表达了对 Python 的认可，甚至愿意“奖励”它一块炸鸡。

#标签 #Python #Ruby #编程语言 #TypeScript #类型系统 #函数式编程 #语言设计 #开发者体验