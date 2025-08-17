为什么选择 Clojure

  

**概述**

  

本文作者回顾了自己五十年来使用过的众多编程语言，最终认为 Lisp，尤其是 Clojure，是最简洁、最优雅、最易用的编程语言。作者认为 Clojure 的“表达经济性”远超其他语言，极简的语法让开发者能够用更少的代码、更少的精力，清晰直接地表达问题和解决方案。作者通过对比 Java、C++ 等主流语言，详细阐述了 Clojure 的优势，并回应了常见的质疑，最终得出结论：Clojure 的极简语法不仅适合小型项目，更适合构建大型系统，是未来编程语言的标准。

  

**语言演变与个人经历**

- 作者拥有丰富的编程经验，曾使用过汇编、Java、Fortran、COBOL、PL/1、C、Pascal、C++、Lua、Smalltalk、Logo 等几十种语言，涵盖静态类型、动态类型、无类型、栈式、逻辑式等多种范式。
- 在长达五十年的编程生涯中，作者逐步形成了对编程语言的深刻理解。最初并不喜欢 Lisp，认为其诸如 ‎⁠CAR⁠、‎⁠CDR⁠、‎⁠CADDADDR⁠ 等语法过于学术化，缺乏实际价值。
- 十年前，作者接触到《SICP》（Structure and Interpretation of Computer Programs，计算机程序的构造和解释），随后又发现了 Clojure——一种运行在 Java 生态上的 Lisp 方言，且摒弃了传统 Lisp 的繁琐语法。
- 作者并非一开始就被 Clojure吸引，经历了数年摸索和挫折后，才逐渐体会到 Clojure 的简洁和优雅。最终，作者认为 Clojure 是自己用过的最容易、最优雅、最不干扰思路的语言，且优势非常明显。

  

**Clojure** **的核心优势：表达经济性**

- 作者列举了选择 Clojure 的唯一理由：“表达经济性”（Economy of Expression）。
- Clojure 代码更简洁，字符更少，开发时间更短，思维负担更轻。
- 这种简洁源于 Clojure 极少的语法和语法规则。作者强调：“Clojure 几乎没有语法或语法规则。”
- 通过示例代码，作者展示了 Clojure 的语法极简：`(println (take 25 (map #(* % %) (range))))`

  

- ‎⁠(⁠ 表示开始一个列表
- ‎⁠)⁠ 表示结束最近的未闭合列表
- 名称即函数名
- ‎⁠*⁠ 是乘法函数
- ‎⁠#⁠ 表示后面的列表是一个匿名函数
- ‎⁠%⁠ 表示匿名函数的第一个参数

- 作者指出，这段代码已经涵盖了 Clojure 80% 的语法。进一步举例：

```clojure
(defn square [x] (* x x))

(println (take 25 (map square (range))))
```


  

- ‎⁠defn⁠ 用于定义新函数
- ‎⁠[]⁠ 表示向量（类似数组），用于定义参数列表
- 通过自定义 ‎⁠square⁠ 函数，代码更易读

- 作者强调，Clojure 的语法极简，开发者可以用更少的代码表达复杂问题，减少了“语法体操”。

  

**与主流语言的对比**

- 作者将 Clojure 与 Java 进行对比，展示了同样功能的 Java 代码：
- 
```java
 public class SquaresOfIntegers {

  public static void main(String[] args) {

    for (int i=0; i<25; i++)

      System.out.println(i*i);

  }

}
```


  

- Java 代码冗长，语法复杂，仅涵盖了 Java 5% 的语法。
- Clojure 代码则极为简洁，语法覆盖面广，表达直接。
- 作者曾是 C++ 程序员，喜欢复杂语法，转向 Java 时感到“平淡”，但转向 Clojure 后彻底改变了看法。
- 作者原以为大型系统需要复杂语法，实际发现 Clojure 的极简语法更适合构建大型系统，开发效率和可维护性远超 Java、C++。

  

**常见质疑与回应**

- **括号太多？**

- 作者用 Java 和 Clojure 的函数调用对比，指出括号数量并无本质区别。Clojure 括号多是因为函数嵌套，若不喜欢可用“threading macros”（线程宏）简化。

- **性能问题？**

- Clojure 并不慢。虽然不是 C 或汇编，但绝大多数软件无需纳秒级性能。作者用 Clojure 构建过实时 GUI 游戏，性能完全满足需求。

- **与** **JavaScript** **的兼容？**

- ClojureScript 可编译为 JavaScript，在浏览器中运行良好，性能甚至优于原生模式。

- **动态类型问题？**

- 可通过测试和 ‎⁠clojure/spec⁠ 库进行类型约束和动态检查，实现“设计契约”风格的开发。
- 作者认为类型声明会增加语法复杂度，降低表达经济性。
- 对于偏好静态类型的开发者，作者建议各取所需。

- **IDE** **支持？**

- IntelliJ + Cursive 插件支持良好，大多数 Clojure 开发者使用 Emacs。

- **重构能力？**

- IntelliJ + Cursive 提供部分重构功能，尚未支持“Extract Method”（提取方法）。

- **与** **Java** **的互操作？**

- Clojure 可直接调用 Java，Java 也能调用 Clojure，互操作性无障碍。

- **开发者来源？**

- Clojure 语法简单，易于培养新开发者。建议直接用 Clojure 构建新系统，几周即可上手，几个月后会有更深体会。

- **新语言层出不穷？**

- 作者认为新语言大多是旧语言拼凑，缺乏革命性创新。Clojure 的极简语法更具吸引力。

- **其他极简语法语言？**

- Forth、Smalltalk 也有极简语法，但各有“包袱”。Forth 是逆波兰栈式语言，表达经济性不足。Smalltalk 虽优雅，但基于“镜像”（image），难以普及。Lisp 历史更悠久，始于 1957 年，至今仍在发展，且是“拒绝消亡”的语言。
- 作者认为未来属于函数式编程，而 Lisp 天生函数式。

  

**框架与心智模型（Framework & Mindset）**

- **表达经济性为核心原则**：选择编程语言时，优先考虑表达经济性，即用最少的语法和代码表达最复杂的逻辑。
- **极简语法带来高效开发**：极简语法不仅适合小型项目，更适合大型系统开发。减少语法负担，提升开发效率和可维护性。
- **函数式编程为未来趋势**：Lisp/Clojure 的函数式特性契合未来软件开发的主流方向。
- **动态类型与测试结合**：通过测试和规范库（如 clojure/spec），动态类型同样可以实现高质量、可维护的代码。
- **工具与生态兼容性**：选择合适的开发工具（如 IntelliJ+Cursive、Emacs），充分利用 Clojure 与 Java 生态的互操作性。
- **持续学习与迭代**：新语言层出不穷，但核心思想不变。开发者应持续学习，关注语言的本质创新而非表面语法变化。

  

**基本信息**

- Title: Why Clojure
- Author: Uncle Bob（Robert C. Martin）
- URL: https://blog.cleancoder.com/uncle-bob/2019/08/22/WhyClojure.html