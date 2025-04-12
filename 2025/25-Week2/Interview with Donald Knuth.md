与高德纳的访谈：开源、多核架构与编程哲学  

- 原文链接：[Interview with Donald Knuth](https://www.informit.com/articles/article.aspx?p=1193856)

---

### 对高德纳的采访

**日期：** 2008 年 4 月 25 日


安德鲁·宾斯托克与高德纳就开源的成功、多核架构的问题、对文学编程缺乏兴趣的失望、可重用代码的威胁以及关于通过一次编译赢得编程比赛的都市传说进行了交谈。

**安德鲁·宾斯托克：** 您是开源革命的先驱之一，尽管您没有被广泛地誉为如此。您之前曾说过，您将 TeX 作为开源发布，因为当时存在专有实现的问题，并且邀请对代码进行更正——这两者都是当今开源项目的关键驱动因素。自那时以来，您对开源的成功感到惊讶吗？

**高德纳：** 开源代码的成功可能是过去几十年来计算机领域唯一没有让我感到惊讶的事情。但它仍然没有发挥出全部潜力；我相信，随着经济越来越多地从产品转向服务，以及越来越多的志愿者出现来改进代码，开源程序将开始完全占据主导地位。

例如，开源代码可以生成数千个二进制文件，这些二进制文件可以完美地调整到个人用户的配置，而商业软件通常只有几个版本。通用的二进制可执行文件必须包含低效的“同步”指令之类的内容，这些指令对于许多安装来说完全不合适；当源代码高度可配置时，这种浪费就会消失。这应该是开源的一个巨大胜利。

然而，我认为有些程序，例如 Adobe Photoshop，将始终优于竞争对手，例如 Gimp——出于某种原因，我真的不知道为什么！如果我相信它是由最好的程序员制作的，我很乐意为真正好的软件支付高价。

不过请记住，我对经济问题的看法非常值得怀疑，因为我只是一位教育家和科学家。我对市场几乎一无所知。

**安德鲁：** 有一个故事说，您曾经在斯坦福大学（我相信）参加了一个编程比赛，您提交了获胜的条目，该条目在一次编译后就正确运行了。这个故事是真的吗？同样，今天的开发人员经常通过编写小的代码增量，然后立即编译和创建并运行单元测试来构建程序。您对这种软件开发方法有什么看法？

**高德纳：** 你听到的故事是典型的传说，它只基于一小部分事实。事情的真相是这样的：约翰·麦卡锡在 1971 年决定举办一个阵亡将士纪念日编程比赛。除了我之外，所有参赛者都在他位于斯坦福上方山丘的 AI 实验室工作，使用 WAITS 分时系统；我则在主校区，那里我唯一可用的计算机是一台大型机，我必须在上面打孔卡片并以批处理模式提交它们进行处理。我使用了沃思的 ALGOL W 系统（Pascal 的前身）。我的程序第一次没有运行成功，但幸运的是，我可以使用埃德·萨特斯韦特的优秀 ALGOL W 离线调试系统，所以我只需要运行两次。与此同时，使用 WAITS 的人们无法获得足够的机器周期，因为他们的机器超载了。（我想使用那种“现代”方法的第二名选手在我用老式方法提交获胜条目后大约一个小时才进来。）这不是一场公平的比赛。

至于你的实际问题，只有当我感觉自己在完全陌生的环境中摸索并需要有关什么有效和什么无效的反馈时，立即编译和“单元测试”的想法才会吸引我。否则，大量时间会浪费在我根本不需要执行甚至不需要考虑的活动上。没有什么需要“模拟”的。

**安德鲁：** 开发人员，尤其是客户端开发人员面临的一个新问题是改变他们的思维方式，以线程方式编写程序。由于廉价多核 PC 的出现，这种担忧肯定会要求许多算法针对多线程或至少是线程安全的进行重新设计。到目前为止，您为《计算机程序设计艺术》(TAOCP) 第 4 卷发布的大部分内容似乎都没有涉及这个方面。您是否期望在即将到来的工作中进入并发和并行编程的问题，特别是考虑到它似乎与您当前正在研究的组合主题自然契合？

**高德纳：** 组合算法领域非常广阔，我将很幸运地将其顺序方面的内容打包成三到四个实体卷，而且我认为顺序方法永远不会变得不重要。相反，并行技术的半衰期非常短，因为硬件变化很快，每台新机器都需要一种稍微不同的方法。所以我很久以前就决定坚持我最了解的东西。其他人比我更了解并行机；程序员应该听从他们的意见，而不是我的意见，以获取有关如何处理同时性的指导。

**安德鲁：** 多核处理器的供应商对将开发人员转移到这种模式的困难表示沮丧。作为一名前教授，您对这种过渡以及如何实现这种过渡有什么看法？这是适当的工具问题，例如语言中对并发的更好的本机支持，还是执行框架的问题？还是有其他解决方案？

**高德纳：** 我不想完全回避你的问题。我可能还不如就个人对当前多核架构趋势的不满发表一些激烈的言论。对我来说，这看起来或多或少像是硬件设计人员已经江郎才尽，他们正试图通过为我们提供仅在少数关键基准测试中运行速度更快的机器，将摩尔定律未来消亡的责任推给软件编写者！如果整个多线程的想法结果是一场失败，比本应如此出色的“安腾”方法更糟糕——直到事实证明所希望的编译器基本上不可能编写出来，我一点也不会感到惊讶。

让我这样说吧：在过去的 50 年里，我编写了超过一千个程序，其中许多程序都很大。我想不出这其中有哪五个程序会因并行性或多线程而得到明显增强。当然，例如，多处理器对 TeX 没有帮助。[1]

您认识多少程序员对这些有希望的未来机器充满热情？我几乎听不到来自软件人员的悲伤，尽管我们部门的硬件人员向我保证我错了。

我知道存在并行性的重要应用——渲染图形、破解代码、扫描图像、模拟物理和生物过程等。但是所有这些应用程序都需要专用代码和特殊用途技术，这些技术每隔几年就需要进行重大更改。

即使我对这些方法有足够的了解，可以在 TAOCP 中写出它们，我的时间也会在很大程度上被浪费，因为很快就没有人有理由阅读那些部分了。（同样，当我准备第 3 卷的第三版时，我计划删除关于如何在磁带上排序的大部分材料。这些东西曾经是整个软件领域最热门的话题之一，但现在当这本书被印刷时，它在很大程度上浪费了纸张。）

我今天使用的机器有双处理器。只有当我同时运行两个独立的作业时，我才能同时使用它们；这很好，但每周只会发生几分钟。如果我有四个处理器，或八个或更多，考虑到我所做的工作类型，我仍然不会有任何好转——即使我几乎每天都在使用我的计算机。那么，我为什么要对硬件供应商承诺的未来如此高兴呢？他们认为会有一种神奇的子弹来加速我这种类型的工作；我认为这是一个白日梦。（不——这是一个错误的比喻！“管道”实际上对我有用，但线程不行。也许我想要的词是“泡沫”。）

从相反的角度来看，我确实承认网络浏览可能会随着多核而变得更好。然而，我一直在谈论我的技术工作，而不是娱乐。我还承认，既然硬件设计人员在顺序计算方面开始碰壁，我对于他们应该提供什么来代替多核并没有很多好主意。（但我的 MMIX 设计包含几个想法，这些想法将大大提高当前令我最担心的程序类型的性能——代价是与传统的 x86 程序不兼容。）

**安德鲁：** 您的少数几个没有被广泛社区接受的项目之一是文学编程。您对为什么文学编程没有流行起来有什么看法？回顾过去，关于文学编程，您有什么不同的做法吗？

**高德纳：** 文学编程是一件非常私人的事情。我认为它很棒，但这很可能是因为我是一个非常奇怪的人。它有成千上万的粉丝，但没有数百万。

根据我的经验，使用文学编程创建的软件被证明比以更传统的方式开发的软件要好得多。然而，普通软件通常还可以——我会给它一个 C 级（或者可能是 C++），但不是 F 级；因此，传统方法一直伴随着我们。由于它们被广大程序员社区所理解，大多数人没有改变的强烈动机，就像我没有学习世界语的动力一样，即使它可能比英语、德语、法语和俄语更可取（如果每个人都转换的话）。

乔恩·本特利可能一语中的，当时他曾经被问到为什么文学编程没有席卷整个世界。他观察到，世界上有一小部分人擅长编程，还有一小部分人擅长写作；显然，我要求每个人都同时属于这两个子集。

然而，对我来说，文学编程当然是 TeX 项目中最重要的东西。自 1980 年代以来，它不仅使我能够比以往更快、更可靠地编写和维护程序，并且是我最大的快乐来源之一——它实际上有时是不可或缺的。我的一些主要程序，例如 MMIX 元模拟器，不可能使用我听说过的任何其他方法来编写。这种复杂性对于我有限的大脑来说简直太令人生畏了；如果没有文学编程，整个事业就会惨败。

如果人们确实发现了使用新奇的多线程机器的好方法，我希望这一发现来自那些经常使用文学编程的人。文学编程是您提升到普通水平的成就所需要的。但我不相信把想法强加给任何人。如果文学编程不是你的风格，请忘记它，做你喜欢的事情。如果除了我之外没有人喜欢它，就让它死去吧。

从积极的方面来看，我很高兴地发现，当我如今使用现成的 Linux 时，CWEB 的约定在预装软件（例如 Makefile）中已经是标准设备。

**安德鲁：** 在第 1 卷的 Fascicle 1 中，您重新介绍了 MMIX 计算机，它是对古老的 MIX 机器的 64 位升级，多年来计算机科学专业的学生已经熟悉了它。您之前在 MMIXware 中非常详细地描述了 MMIX。我读过这两本书的部分内容，但无法判断 Fascicle 是否更新或更改了 MMIXware 中出现的任何内容，或者它是否是一个纯粹的概要。您能澄清一下吗？

**高德纳：** 第 1 卷 Fascicle 1 是程序员的入门介绍，其中包括有指导意义的练习等内容。MMIXware 一书是一本详细的参考手册，有点简洁和枯燥，加上一堆文学程序，描述了原型软件供人们构建。这两本书定义了相同的计算机（一旦将 MMIXware 的勘误表从我的网站中纳入）。对于 TAOCP 的大多数读者来说，第一个 fascicle 包含关于 MMIX 的所有他们需要或想要知道的内容。

然而，我应该指出，MMIX 不是一台单独的机器；它是一种架构，具有几乎无限多种实现，具体取决于功能单元的不同选择、不同的管道配置、不同的多指令发射方法、不同的分支预测方法、不同的缓存大小、不同的缓存替换策略、不同的总线速度等。“更便宜”版本的硬件可以用软件模拟一些指令和/或寄存器。等等。这是一个测试平台，所有这些都可以用我的元模拟器进行模拟，即使高级版本在未来五年内无法有效地构建（然后我们可以通过将元模拟器规格再提高一个档次来要求进一步的进步）。

假设您想知道五个独立的乘法器单元和/或三路指令发射是否会加速给定的 MMIX 程序。或者，指令和/或数据缓存可以做得更大或更小或更具关联性。只需启动元模拟器，看看会发生什么。

**安德鲁：** 我怀疑您没有对 MMIXAL 进行单元测试，您能否告诉我您是如何确保您的代码在各种条件和输入下都能正常工作的？如果您有一个关于验证的特定工作程序，您能否描述一下？

**高德纳：** TAOCP 中机器语言代码的大多数示例出现在第 1-3 卷中；到了第 4 卷，如此低级别的细节在很大程度上是不必要的，我们可以在更高的抽象级别上安全地工作。因此，在准备第 4 卷的开头部分时，我只需要编写十几个 MMIX 程序，而且它们几乎都是玩具程序——没有什么实质性的内容。对于像这样的小事，我只是使用非正式的验证方法，基于我为这本书写下的理论，以及网上随时可用的 MMIXAL 汇编程序和 MMIX 模拟器（并在 MMIXware 一书中详细描述）。

该模拟器包括调试功能，就像我在前面提到的埃德·萨特斯韦特的 ALGOL W 系统中发现非常有用的功能一样。在使用这些工具检查程序后，我总是感到非常自信。

**安德鲁：** 尽管 TeX 是多年前制定的，但它仍然蓬勃发展，主要是作为 LaTeX 的基础。虽然 TeX 已应您的要求有效地冻结，但如果您有时间和带宽，是否有您想要更改或添加的功能？如果有，您会添加/更改哪些主要项目？

**高德纳：** 我相信对 TeX 的更改弊大于利。想要其他功能的其他人正在创建他们自己的系统，我一直鼓励进一步开发——除了没有人应该给他们的程序起与我的程序相同的名字。我想对 TeX 和 Metafont 以及所有影响依赖于我工作的现有文档的细微之处承担永久责任，例如 Computer Modern 字体中字符的精确尺寸。

**安德鲁：** 软件开发中很少讨论的一个方面是如何在全新的领域中进行软件设计工作。当您开始使用 TeX 时，您就面临着这个问题：您无法获得任何现有技术作为源代码，而且这是一个您不是专家的领域。您是如何进行设计的，您花了多长时间才开始进入编码部分？

**高德纳：** 这是另一个好问题！我在我的书《文学编程》的第 10 章以及我的书《数字排版》的第 1 章和第 2 章中详细讨论了答案。我认为任何真正对这个话题感兴趣的人都会喜欢阅读这些章节。（另请参阅《数字排版》第 24 章和第 25 章，了解我在 1977 年对 TeX 的初始设计的完整第一稿和第二稿。）

**安德鲁：** 关于 TeX 的书籍和程序本身都清楚地表明了限制内存使用的担忧——这是那个时代系统的一个重要问题。今天，程序中对内存使用的担忧更多地与缓存大小有关。作为一名在软件中设计过处理器的人，缓存感知和缓存无关算法的问题肯定已经出现在您的雷达屏幕上。算法设计中处理器缓存的作用是否是您期望在您即将到来的工作中涵盖的内容，即使是间接的？

**高德纳：** 我之前提到过 MMIX 为多种缓存提供了一个测试平台。而且它是一台软件实现的机器，因此我们可以进行即使在一百年后也可以重复的实验。当然，第 1-3 卷的下一版将讨论各种基本算法相对于不同缓存参数的行为。

到目前为止，在第 4 卷中，我统计了大约十几个对缓存内存和缓存友好方法的引用（更不用说“备忘录缓存”了，这是软件中一个不同但相关的想法）。

**安德鲁：** 您今天使用什么工具集来编写 TAOCP？您使用 TeX 吗？LaTeX？CWEB？文字处理器？您使用什么进行编码？

**高德纳：** 我的一般工作方式是先用铅笔和纸写下所有内容，坐在一个大废纸篓旁边。然后我使用 Emacs 将文本输入到我的机器中，使用 TeX 的约定。我使用 tex、dvips 和 gv 来查看结果，这些结果现在几乎可以立即出现在我的屏幕上。我用 Mathematica 检查我的数学。

我使用 CWEB 对讨论的每个算法进行编程（以便我可以彻底理解它），它与 GDB 调试器配合得非常好。我使用 MetaPost（或者在极少数情况下，在 Mac 上使用 Adobe Photoshop 或 Illustrator）制作插图。我有一些自制的工具，比如我自己的 Emacs 中用于 TeX 和 CWEB 的拼写检查器。我为 Emacs 设计了自己的位图字体，因为我讨厌 ASCII 撇号和左引号变成相互独立的符号，这些符号在视觉上不再匹配。我有特殊的 Emacs 模式来帮助我对文件中的所有数万篇论文和笔记进行分类，还有特殊的 Emacs 键盘快捷键，使写书有点像弹奏风琴。我更喜欢 rxvt 而不是 xterm 进行终端输入。自去年 12 月以来，我一直在使用一个名为 backupfs 的文件备份系统，它完美地满足了我对每个文件的每日状态进行存档的需求。

根据我机器上的当前目录，今年到目前为止，我已经编写了 68 个不同的 CWEB 程序。2007 年大约有 100 个，2006 年有 90 个，2005 年有 100 个，2004 年有 90 个，等等。此外，CWEB 有一个极其方便的“更改文件”机制，我可以用它快速创建多个版本和主题变体；到目前为止，在 2008 年，我已经对这 68 个主题进行了 73 种变体。（有些变体很短，只有几个字节；有些变体有 5KB 或更多。有些 CWEB 程序相当大，比如我在 1 月份完成的 55 页的 BDD 包。）因此，您可以看到文学编程在我的生活中有多么重要。

我目前在独立的笔记本电脑上使用 Ubuntu Linux——它没有互联网连接。我偶尔会在这个机器和我用于网络冲浪和图形的 Mac 之间携带闪存驱动器；但我只相信 Linux 的传家宝。顺便说一句，对于 Linux，我更喜欢经典 FVWM 可以获得的键盘焦点，而不是其他人似乎更喜欢的 GNOME 和 KDE 环境。各有所爱。

**安德鲁：** 您在 TAOCP 第 4 卷 Fascicle 0 的序言中指出，第 4 卷肯定会包含三卷，并且可能更多。从文本中可以清楚地看出，您真的很喜欢写这个主题。鉴于此，您对 TAOCP 网站上发布的第 5 卷将在 2015 年问世的说明有多大信心？

**高德纳：** 如果您查看 Wayback Machine 以了解该网页的早期版本，您会发现 2015 年这个数字并不是恒定的。

您当然是对的，我在写这篇材料时玩得很开心，因为我不断遇到一些迷人的事实，这些事实根本不能遗漏——即使我有一半以上的笔记没有进入最终版本。

精确的时间估计是不可能的，因为我无法确定，直到深入到每个部分，我的文件中有多少内容将是真正基本的，以及有多少内容与我的书无关或太高级。最近的许多文献都是学术上的你追我赶，我对这些文献的兴趣有限；如今的作者经常引入一些深奥的方法，这些方法只有在问题规模超过宇宙中的质子数时才会优于更简单的技术。此类算法永远不可能在真正的计算机应用程序中发挥重要作用。我阅读了数百篇此类论文，看看它们是否可能包含程序员的金块，但其中大多数最终都被忽视了。

从调度的角度来看，我目前所知道的只是，我必须在某一天消化我 45 年来一直在收集和归档的大量材料。我通过以批处理模式工作来获得重要时间：我不会深入阅读一篇论文，直到我可以在同一周内处理同一主题的数十篇其他论文。当我终于准备好阅读关于某个主题收集的内容时，我可能会发现我可以快速前进，因为对于我的目的来说，其中大部分内容都非常容易被遗忘。另一方面，我可能会发现它是基本的，值得花几周的时间研究；然后我必须编辑我的网站并将 2015 年这个数字推向无穷大。

**安德鲁：** 2006 年底，您被诊断出患有前列腺癌。您现在身体如何？

**高德纳：** 当然，癌症将是一个严重的问题。我有优秀的医生。目前，我觉得自己和以往一样健康，已经 70 岁了。当我写 TAOCP 以及当我写 TAOCP 草稿之前的文学程序时，文字自由流动。我早上醒来时会想到一些让我高兴的想法，其中一些想法在我当天晚些时候将它们输入到我的计算机时仍然让我高兴。

另一方面，我愿意把自己交给上帝，就我在癌症、心脏病或衰老或任何疾病发作之前还能做多少而言。如果我明天意外死亡，我没有理由抱怨，因为我的生活得到了难以置信的祝福。相反，只要我能够写计算机科学方面的内容，我就打算尽我所能组织和阐述自 1962 年以来我收集和记录的数万篇技术论文。

**安德鲁：** 在您的网站上，您提到 Peoples Archive 最近制作了一系列视频，在这些视频中，您回顾了您的过去生活。在第 93 部分“给年轻人的建议”中，您建议人们不要仅仅因为某事很时髦就去做。正如我们所熟知的，软件开发与其他任何学科一样容易受到时尚的影响。您能否举一些目前流行的例子，开发人员不应该仅仅因为它们当前很流行或因为它们当前就是这样做的而采用它们？您是否愿意指出软件开发之外的此类重要示例？

**高德纳：** 嗯。这个问题几乎是自相矛盾的，因为我基本上是在建议年轻人听从自己而不是听从他人，而我就是其他人之一。几乎每一个你想效仿的人的传记都会说，他或她做了许多违背当时的“传统智慧”的事情。

尽管如此，我还是讨厌回避你的问题，尽管我也讨厌冒犯别人的感情——因为软件方法论一直类似于宗教。需要注意的是，没有任何理由应该关心像我这样的计算机科学家/数学家对软件开发的意见，我只想说，几乎所有我听说过的与“极限编程”一词相关的每件事听起来都像是完全错误的做法……只有一个例外。例外是在团队中工作并阅读彼此的代码的想法。这个想法至关重要，它甚至可能掩盖了所有令我震惊的极限编程的可怕方面。

我还必须承认，我对可重用代码的时尚抱有强烈的偏见。对我来说，“可重新编辑的代码”比一个不可触碰的黑匣子或工具包要好得多。关于这一点，我可以滔滔不绝。如果您完全相信可重用代码很棒，我可能无论如何都无法动摇您，但您永远无法说服我可重用代码主要不是一种威胁。

这是您很可能打算问的一个问题：为什么新书被称为第 4 卷 Fascicle 0，而不是第 4 卷 Fascicle 1？答案是计算机程序员会理解我还没有准备好在 TAOCP 第 4 卷的真正起点开始编写它，因为我们知道程序的初始化不能在程序本身成形之前编写。所以我在 2005 年从第 4 卷 Fascicle 2 开始，之后是 Fascicle 3 和 4。（想想星球大战，它从第 4 集开始。）

最后，我被激发去写早期的部分，但我很快意识到介绍部分需要包含比单个 fascicle 中容纳的更多的内容。因此，记住迪克斯特拉的格言，计数应该从 0 开始，我决定从 Fascicle 0 开始第 4 卷。请期待今年晚些时候的第 4 卷 Fascicle 1。

#### 脚注
[1] 我的同事昆勒·奥卢科顿指出，如果 TeX 的使用成为一个主要的瓶颈，以至于人们拥有十几个处理器并且真的需要极大地加快他们的排版速度，那么可以开发一个使用“推测”来同时排版十几个章节的超并行版本的 TeX：每个章节都可以在假设前几章没有做任何奇怪的事情来扰乱默认逻辑的情况下进行排版。如果该假设失败，我们可以退回到一次做一个章节的正常方法；但在大多数情况下，当只调用正常的排版时，处理速度确实会快 12 倍。关心速度的用户可以调整他们的行为并以有纪律的方式使用 TeX。

安德鲁·宾斯托克是 Pacific Data Works 的首席分析师。他是 SD Times 的专栏作家和 InfoWorld 杂志的高级特约编辑。可以在以下网址找到他的博客：http://binstock.blogspot.com。



---
## 要点回顾

本文是一篇对计算机科学家高德纳（Donald Knuth）的访谈实录，由安德鲁·宾斯托克（Andrew Binstock）进行采访。访谈主要围绕开源软件的成功、多核架构的问题、编程哲学以及高德纳个人的一些观点和经历展开。以下是访谈的主要内容整理：

### 开源软件
- **高德纳对开源的看法**：高德纳认为开源软件的成功并不令他感到惊讶，因为开源项目能够根据用户的特定配置生成数千个二进制文件，而商业软件通常只有几个版本。开源软件的可配置性使其在某些方面具有优势。
- **开源的未来**：高德纳预测，随着经济从产品向服务的转变以及更多志愿者的参与，开源软件将逐渐占据主导地位。

### 多核架构
- **高德纳对多核架构的批评**：高德纳对当前多核架构的趋势表示不满，认为硬件设计者似乎已经没有新的想法，而是将摩尔定律的终结责任推给软件开发者，通过提供在某些基准测试上速度更快的机器来应对。
- **多核架构的局限性**：高德纳指出，他所编写的大量程序中，几乎没有几个会因为并行处理或多线程而得到显著提升。他认为多核架构对于大多数应用程序来说并不是必需的，甚至可能是一种失败的尝试。

### 编程哲学
- **对即时编译和单元测试的看法**：高德纳对即时编译和单元测试的方法持保留态度，他认为这些方法在探索未知环境时可能有用，但在其他情况下可能会浪费大量时间。
- **对可重用代码的看法**：高德纳对可重用代码持批评态度，他认为“可编辑代码”比不可触碰的黑盒或工具包要好得多。他认为可重用代码在很多情况下是一种威胁。

### 个人经历与观点
- **关于“一次编译成功”的传说**：高德纳澄清了关于他在斯坦福大学的一次编程比赛中一次编译成功的传说，实际上他使用了两次运行才成功。
- **对编程竞赛的看法**：高德纳认为编程竞赛并不是一个公平的竞赛，因为不同的参赛者使用不同的计算机系统和工具。
- **对编程教育的看法**：高德纳认为编程教育应该更加注重理解算法和程序的原理，而不是仅仅追求快速编写代码。

### 其他话题
- **对“文学编程”的看法**：高德纳是“文学编程”的倡导者，他认为这种编程方式能够提高软件的质量和可维护性。尽管“文学编程”并没有被广泛接受，但高德纳仍然认为它是一种非常重要的编程方法。
- **对MMIX计算机的看法**：MMIX是高德纳设计的一种计算机架构，他通过MMIX来研究和测试不同的计算机设计和算法。他认为MMIX是一个很好的测试平台，可以用于研究各种计算机性能问题。

### 结论
高德纳在访谈中分享了他对开源软件、多核架构、编程哲学以及个人经历的深刻见解。他的观点不仅反映了他对计算机科学的深刻理解，也展示了他对当前技术趋势的批判性思考。尽管高德纳的一些观点可能与主流观点不同，但他的见解无疑为计算机科学的发展提供了重要的参考和启示。


## 原文

### Interview with Donald Knuth

Date: Apr 25, 2008

[Return to the article](https://www.informit.com/articles/article.aspx?p=1193856)

Andrew Binstock and Donald Knuth converse on the success of open source, the problem with multicore architecture, the disappointing lack of interest in literate programming, the menace of reusable code, and that urban legend about winning a programming contest with a single compilation.

**Andrew Binstock: You are one of the fathers of the open-source revolution, even if you aren’t widely heralded as such. You previously have stated that you released** [TeX](http://en.wikipedia.org/wiki/TeX) **as open source because of the problem of proprietary implementations at the time, and to invite corrections to the code—both of which are key drivers for open-source projects today. Have you been surprised by the success of open source since that time?**

Donald Knuth: The success of open source code is perhaps the only thing in the computer field that _hasn’t_ surprised me during the past several decades. But it still hasn’t reached its full potential; I believe that open-source programs will begin to be completely dominant as the economy moves more and more from products towards services, and as more and more volunteers arise to improve the code.

For example, open-source code can produce thousands of binaries, tuned perfectly to the configurations of individual users, whereas commercial software usually will exist in only a few versions. A generic binary executable file must include things like inefficient "sync" instructions that are totally inappropriate for many installations; such wastage goes away when the source code is highly configurable. This should be a huge win for open source.

Yet I think that a few programs, such as Adobe Photoshop, will always be superior to competitors like the Gimp—for some reason, I really don’t know why! I’m quite willing to pay good money for really good software, if I believe that it has been produced by the best programmers.

Remember, though, that my opinion on economic questions is highly suspect, since I’m just an educator and scientist. I understand almost nothing about the marketplace.

**Andrew: A story states that you once entered a programming contest at Stanford (I believe) and you submitted the winning entry, which worked correctly after a _single_ compilation. Is this story true? In that vein, today’s developers frequently build programs writing small code increments followed by immediate compilation and the creation and running of unit tests. What are your thoughts on this approach to software development?**

Donald: The story you heard is typical of legends that are based on only a small kernel of truth. Here’s what actually happened: [John McCarthy](http://en.wikipedia.org/wiki/John_McCarthy_%28computer_scientist%29) decided in 1971 to have a Memorial Day Programming Race. All of the contestants except me worked at his AI Lab up in the hills above Stanford, using the WAITS time-sharing system; I was down on the main campus, where the only computer available to me was a mainframe for which I had to punch cards and submit them for processing in batch mode. I used Wirth’s [ALGOL W](http://en.wikipedia.org/wiki/Algol_W) system (the predecessor of Pascal). My program _didn’t_ work the first time, but fortunately I could use Ed Satterthwaite’s excellent offline debugging system for ALGOL W, so I needed only two runs. Meanwhile, the folks using WAITS couldn’t get enough machine cycles because their machine was so overloaded. (I think that the second-place finisher, using that "modern" approach, came in about an hour after I had submitted the winning entry with old-fangled methods.) It wasn’t a fair contest.

As to your real question, the idea of immediate compilation and "unit tests" appeals to me only rarely, when I’m feeling my way in a totally unknown environment and need feedback about what works and what doesn’t. Otherwise, lots of time is wasted on activities that I simply never need to perform or even think about. Nothing needs to be "mocked up."

**Andrew: One of the emerging problems for developers, especially client-side developers, is changing their thinking to write programs in terms of threads. This concern, driven by the advent of inexpensive multicore PCs, surely will require that many algorithms be recast for multithreading, or at least to be thread-safe. So far, much of the work you’ve published for Volume 4 of** [The Art of Computer Programming](http://www.informit.com/store/product.aspx?isbn=0201485419) **(_TAOCP_) doesn’t seem to touch on this dimension. Do you expect to enter into problems of concurrency and parallel programming in upcoming work, especially since it would seem to be a natural fit with the combinatorial topics you’re currently working on?**

Donald: The field of combinatorial algorithms is so vast that I’ll be lucky to pack its _sequential_ aspects into three or four physical volumes, and I don’t think the sequential methods are ever going to be unimportant. Conversely, the half-life of parallel techniques is very short, because hardware changes rapidly and each new machine needs a somewhat different approach. So I decided long ago to stick to what I know best. Other people understand parallel machines much better than I do; programmers should listen to them, not me, for guidance on how to deal with simultaneity.

**Andrew: Vendors of multicore processors have expressed frustration at the difficulty of moving developers to this model. As a former professor, what thoughts do you have on this transition and how to make it happen? Is it a question of proper tools, such as better native support for concurrency in languages, or of execution frameworks? Or are there other solutions?**

Donald: I don’t want to duck your question entirely. I might as well flame a bit about my personal unhappiness with the current trend toward multicore architecture. To me, it looks more or less like the hardware designers have run out of ideas, and that they’re trying to pass the blame for the future demise of Moore’s Law to the software writers by giving us machines that work faster only on a few key benchmarks! I won’t be surprised at all if the whole multithreading idea turns out to be a flop, worse than the "[Itanium](http://en.wikipedia.org/wiki/Itanium)" approach that was supposed to be so terrific—until it turned out that the wished-for compilers were basically impossible to write.

Let me put it this way: During the past 50 years, I’ve written well over a thousand programs, many of which have substantial size. I can’t think of even _five_ of those programs that would have been enhanced noticeably by parallelism or multithreading. Surely, for example, multiple processors are no help to TeX.[1]

How many programmers do you know who are enthusiastic about these promised machines of the future? I hear almost nothing but grief from software people, although the hardware folks in our department assure me that I’m wrong.

I know that important applications for parallelism exist—rendering graphics, breaking codes, scanning images, simulating physical and biological processes, etc. But all these applications require dedicated code and special-purpose techniques, which will need to be changed substantially every few years.

Even if I knew enough about such methods to write about them in _TAOCP_, my time would be largely wasted, because soon there would be little reason for anybody to read those parts. (Similarly, when I prepare the third edition of [Volume 3](http://www.informit.com/store/product.aspx?isbn=0201896850) I plan to rip out much of the material about how to sort on magnetic tapes. That stuff was once one of the hottest topics in the whole software field, but now it largely wastes paper when the book is printed.)

The machine I use today has dual processors. I get to use them both only when I’m running two independent jobs at the same time; that’s nice, but it happens only a few minutes every week. If I had four processors, or eight, or more, I still wouldn’t be any better off, considering the kind of work I do—even though I’m using my computer almost every day during most of the day. So why should I be so happy about the future that hardware vendors promise? They think a magic bullet will come along to make multicores speed up my kind of work; I think it’s a pipe dream. (No—that’s the wrong metaphor! "Pipelines" actually work for me, but threads don’t. Maybe the word I want is "bubble.")

From the opposite point of view, I do grant that web browsing probably will get better with multicores. I’ve been talking about my technical work, however, not recreation. I also admit that I haven’t got many bright ideas about what I wish hardware designers would provide instead of multicores, now that they’ve begun to hit a wall with respect to sequential computation. (But my [MMIX](http://www-cs-faculty.stanford.edu/~knuth/mmix.html) design contains several ideas that would substantially improve the current performance of the kinds of programs that concern me most—at the cost of incompatibility with legacy x86 programs.)

**Andrew: One of the few projects of yours that hasn’t been embraced by a widespread community is** [literate programming](http://www.literateprogramming.com/)**. What are your thoughts about why literate programming didn’t catch on? And is there anything you’d have done differently in retrospect regarding literate programming?**

Donald: Literate programming is a very personal thing. I think it’s terrific, but that might well be because I’m a very strange person. It has tens of thousands of fans, but not millions.

In my experience, software created with literate programming has turned out to be significantly better than software developed in more traditional ways. Yet ordinary software is usually okay—I’d give it a grade of C (or maybe C++), but not F; hence, the traditional methods stay with us. Since they’re understood by a vast community of programmers, most people have no big incentive to change, just as I’m not motivated to learn Esperanto even though it might be preferable to English and German and French and Russian (if everybody switched).

[Jon Bentley](http://en.wikipedia.org/wiki/Jon_Bentley) probably hit the nail on the head when he once was asked why literate programming hasn’t taken the whole world by storm. He observed that a small percentage of the world’s population is good at programming, and a small percentage is good at writing; apparently I am asking everybody to be in both subsets.

Yet to me, literate programming is certainly the most important thing that came out of the TeX project. Not only has it enabled me to write and maintain programs faster and more reliably than ever before, and been one of my greatest sources of joy since the 1980s—it has actually been _indispensable_ at times. Some of my major programs, such as the MMIX meta-simulator, could not have been written with any other methodology that I’ve ever heard of. The complexity was simply too daunting for my limited brain to handle; without literate programming, the whole enterprise would have flopped miserably.

If people do discover nice ways to use the newfangled multithreaded machines, I would expect the discovery to come from people who routinely use literate programming. Literate programming is what you need to rise above the ordinary level of achievement. But I don’t believe in forcing ideas on anybody. If literate programming isn’t your style, please forget it and do what you like. If nobody likes it but me, let it die.

On a positive note, I’ve been pleased to discover that the conventions of CWEB are already standard equipment within preinstalled software such as Makefiles, when I get off-the-shelf Linux these days.

**Andrew: In** [Fascicle 1 of Volume 1](http://www.informit.com/store/product.aspx?isbn=0201853922)**, you reintroduced the MMIX computer, which is the 64-bit upgrade to the venerable MIX machine comp-sci students have come to know over many years. You previously described MMIX in great detail in** [MMIXware](http://www-cs-faculty.stanford.edu/~knuth/mmixware.html)**. I’ve read portions of both books, but can’t tell whether the Fascicle updates or changes anything that appeared in MMIXware, or whether it’s a pure synopsis. Could you clarify?**

Donald: Volume 1 Fascicle 1 is a programmer’s introduction, which includes instructive exercises and such things. The MMIXware book is a detailed reference manual, somewhat terse and dry, plus a bunch of literate programs that describe prototype software for people to build upon. Both books define the same computer (once the errata to MMIXware are incorporated from my website). For most readers of _TAOCP_, the first fascicle contains everything about MMIX that they’ll ever need or want to know.

I should point out, however, that MMIX isn’t a single machine; it’s an architecture with almost unlimited varieties of implementations, depending on different choices of functional units, different pipeline configurations, different approaches to multiple-instruction-issue, different ways to do branch prediction, different cache sizes, different strategies for cache replacement, different bus speeds, etc. Some instructions and/or registers can be emulated with software on "cheaper" versions of the hardware. And so on. It’s a test bed, all simulatable with my meta-simulator, even though advanced versions would be impossible to build effectively until another five years go by (and then we could ask for even further advances just by advancing the meta-simulator specs another notch).

Suppose you want to know if five separate multiplier units and/or three-way instruction issuing would speed up a given MMIX program. Or maybe the instruction and/or data cache could be made larger or smaller or more associative. Just fire up the meta-simulator and see what happens.

**Andrew: As I suspect you don’t use unit testing with MMIXAL, could you step me through how you go about making sure that your code works correctly under a wide variety of conditions and inputs? If you have a specific work routine around verification, could you describe it?**

Donald: Most examples of machine language code in _TAOCP_ appear in Volumes 1-3; by the time we get to Volume 4, such low-level detail is largely unnecessary and we can work safely at a higher level of abstraction. Thus, I’ve needed to write only a dozen or so MMIX programs while preparing the opening parts of Volume 4, and they’re all pretty much toy programs—nothing substantial. For little things like that, I just use informal verification methods, based on the theory that I’ve written up for the book, together with the MMIXAL assembler and MMIX simulator that are readily available on the Net (and described in full detail in the MMIXware book).

That simulator includes debugging features like the ones I found so useful in Ed Satterthwaite’s system for ALGOL W, mentioned earlier. I always feel quite confident after checking a program with those tools.

**Andrew: Despite its formulation many years ago, TeX is still thriving, primarily as the foundation for** [LaTeX](http://en.wikipedia.org/wiki/LaTeX)**. While TeX has been effectively frozen at your request, are there features that you would want to change or add to it, if you had the time and bandwidth? If so, what are the major items you add/change?**

Donald: I believe changes to TeX would cause much more harm than good. Other people who want other features are creating their own systems, and I’ve always encouraged further development—except that nobody should give their program the same name as mine. I want to take permanent responsibility for TeX and [Metafont](http://en.wikipedia.org/wiki/Metafont), and for all the nitty-gritty things that affect existing documents that rely on my work, such as the precise dimensions of characters in the Computer Modern fonts.

**Andrew: One of the little-discussed aspects of software development is how to do design work on software in a completely new domain. You were faced with this issue when you undertook TeX: No prior art was available to you as source code, and it was a domain in which you weren’t an expert. How did you approach the design, and how long did it take before you were comfortable entering into the coding portion?**

Donald: That’s another good question! I’ve discussed the answer in great detail in Chapter 10 of my book [Literate Programming](http://www.amazon.com/Literate-Programming-Center-Language-Information/dp/0937073806/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1208825413&sr=1-1), together with Chapters 1 and 2 of my book [Digital Typography](http://www.amazon.com/Digital-Typography-Center-Language-Information/dp/1575860104/ref=sr_1_1?ie=UTF8&s=books&qid=1208825453&sr=1-1). I think that anybody who is really interested in this topic will enjoy reading those chapters. (See also _Digital Typography_ Chapters 24 and 25 for the complete first and second drafts of my initial design of TeX in 1977.)

**Andrew: The books on TeX and the program itself show a clear concern for limiting memory usage—an important problem for systems of that era. Today, the concern for memory usage in programs has more to do with cache sizes. As someone who has designed a processor in software, the issues of cache-aware and** [cache-oblivious algorithms](http://en.wikipedia.org/wiki/Cache-oblivious_algorithm) **surely must have crossed your radar screen. Is the role of processor caches on algorithm design something that you expect to cover, even if indirectly, in your upcoming work?**

Donald: I mentioned earlier that MMIX provides a test bed for many varieties of cache. And it’s a software-implemented machine, so we can perform experiments that will be repeatable even a hundred years from now. Certainly the next editions of Volumes 1-3 will discuss the behavior of various basic algorithms with respect to different cache parameters.

In Volume 4 so far, I count about a dozen references to cache memory and cache-friendly approaches (not to mention a "memo cache," which is a different but related idea in software).

**Andrew: What set of tools do you use today for writing _TAOCP_? Do you use TeX? LaTeX? CWEB? Word processor? And what do you use for the coding?**

Donald: My general working style is to write everything first with pencil and paper, sitting beside a big wastebasket. Then I use Emacs to enter the text into my machine, using the conventions of TeX. I use tex, dvips, and gv to see the results, which appear on my screen almost instantaneously these days. I check my math with Mathematica.

I program every algorithm that’s discussed (so that I can thoroughly understand it) using CWEB, which works splendidly with the GDB debugger. I make the illustrations with [MetaPost](http://en.wikipedia.org/wiki/METAPOST) (or, in rare cases, on a Mac with Adobe Photoshop or Illustrator). I have some homemade tools, like my own spell-checker for TeX and CWEB within Emacs. I designed my own bitmap font for use with Emacs, because I hate the way the ASCII apostrophe and the left open quote have morphed into independent symbols that no longer match each other visually. I have special Emacs modes to help me classify all the tens of thousands of papers and notes in my files, and special Emacs keyboard shortcuts that make bookwriting a little bit like playing an organ. I prefer [rxvt](http://en.wikipedia.org/wiki/Rxvt) to xterm for terminal input. Since last December, I’ve been using a file backup system called [backupfs](http://sourceforge.net/projects/backupfs), which meets my need beautifully to archive the daily state of every file.

According to the current directories on my machine, I’ve written 68 different CWEB programs so far this year. There were about 100 in 2007, 90 in 2006, 100 in 2005, 90 in 2004, etc. Furthermore, CWEB has an extremely convenient "change file" mechanism, with which I can rapidly create multiple versions and variations on a theme; so far in 2008 I’ve made 73 variations on those 68 themes. (Some of the variations are quite short, only a few bytes; others are 5KB or more. Some of the CWEB programs are quite substantial, like the 55-page BDD package that I completed in January.) Thus, you can see how important literate programming is in my life.

I currently use [Ubuntu Linux](http://www.ubuntu.com/), on a standalone laptop—it has no Internet connection. I occasionally carry flash memory drives between this machine and the Macs that I use for network surfing and graphics; but I trust my family jewels only to Linux. Incidentally, with Linux I much prefer the keyboard focus that I can get with classic [FVWM](http://en.wikipedia.org/wiki/FVWM) to the GNOME and KDE environments that other people seem to like better. To each their own.

**Andrew: You state in the preface of** [Fascicle 0 of Volume 4](http://www.informit.com/store/product.aspx?isbn=0321534964) **of _TAOCP_ that Volume 4 surely will comprise three volumes and possibly more. It’s clear from the text that you’re really enjoying writing on this topic. Given that, what is your confidence in the note posted on the _TAOCP_ website that Volume 5 will see light of day by 2015?**

Donald: If you check the Wayback Machine for previous incarnations of that web page, you will see that the number 2015 has not been constant.

You’re certainly correct that I’m having a ball writing up this material, because I keep running into fascinating facts that simply can’t be left out—even though more than half of my notes don’t make the final cut.

Precise time estimates are impossible, because I can’t tell until getting deep into each section how much of the stuff in my files is going to be really fundamental and how much of it is going to be irrelevant to my book or too advanced. A lot of the recent literature is academic one-upmanship of limited interest to me; authors these days often introduce arcane methods that outperform the simpler techniques only when the problem size exceeds the number of protons in the universe. Such algorithms could never be important in a real computer application. I read hundreds of such papers to see if they might contain nuggets for programmers, but most of them wind up getting short shrift.

From a scheduling standpoint, all I know at present is that I must someday digest a huge amount of material that I’ve been collecting and filing for 45 years. I gain important time by working in batch mode: I don’t read a paper in depth until I can deal with dozens of others on the same topic during the same week. When I finally am ready to read what has been collected about a topic, I might find out that I can zoom ahead because most of it is eminently forgettable for my purposes. On the other hand, I might discover that it’s fundamental and deserves weeks of study; then I’d have to edit my website and push that number 2015 closer to infinity.

**Andrew: In late 2006, you were diagnosed with prostate cancer. How is your health today?**

Donald: Naturally, the cancer will be a serious concern. I have superb doctors. At the moment I feel as healthy as ever, modulo being 70 years old. Words flow freely as I write _TAOCP_ and as I write the literate programs that precede drafts of _TAOCP_. I wake up in the morning with ideas that please me, and some of those ideas actually please me also later in the day when I’ve entered them into my computer.

On the other hand, I willingly put myself in God’s hands with respect to how much more I’ll be able to do before cancer or heart disease or senility or whatever strikes. If I should unexpectedly die tomorrow, I’ll have no reason to complain, because my life has been incredibly blessed. Conversely, as long as I’m able to write about computer science, I intend to do my best to organize and expound upon the tens of thousands of technical papers that I’ve collected and made notes on since 1962.

**Andrew: On your website, you mention that the** [Peoples Archive](http://www.peoplesarchive.com/home.jsp) **recently made a series of videos in which you reflect on your past life. In segment 93, "Advice to Young People," you advise that people shouldn’t do something simply because it’s trendy. As we know all too well, software development is as subject to fads as any other discipline. Can you give some examples that are currently in vogue, which developers shouldn’t adopt simply because they’re currently popular or because that’s the way they’re currently done? Would you care to identify important examples of this outside of software development?**

Donald: Hmm. That question is almost contradictory, because I’m basically advising young people to listen to themselves rather than to others, and I’m one of the others. Almost every biography of every person whom you would like to emulate will say that he or she did many things against the "conventional wisdom" of the day.

Still, I hate to duck your questions even though I also hate to offend other people’s sensibilities—given that software methodology has always been akin to religion. With the caveat that there’s no reason anybody should care about the opinions of a computer scientist/mathematician like me regarding software development, let me just say that almost everything I’ve ever heard associated with the term "[extreme programming](http://en.wikipedia.org/wiki/Extreme_programming)" sounds like exactly the wrong way to go...with one exception. The exception is the idea of working in teams and reading each other’s code. That idea is crucial, and it might even mask out all the terrible aspects of extreme programming that alarm me.

I also must confess to a strong bias against the fashion for reusable code. To me, "re-editable code" is much, much better than an untouchable black box or toolkit. I could go on and on about this. If you’re totally convinced that reusable code is wonderful, I probably won’t be able to sway you anyway, but you’ll never convince me that reusable code isn’t mostly a menace.

Here’s a question that you may well have meant to ask: Why is the new book called Volume 4 Fascicle 0, instead of Volume 4 Fascicle 1? The answer is that computer programmers will understand that I wasn’t ready to begin writing Volume 4 of _TAOCP_ at its true beginning point, because we know that the initialization of a program can’t be written until the program itself takes shape. So I started in 2005 with Volume 4 Fascicle 2, after which came Fascicles 3 and 4. (Think of _Star Wars_, which began with Episode 4.)

Finally I was psyched up to write the early parts, but I soon realized that the introductory sections needed to include much more stuff than would fit into a single fascicle. Therefore, remembering [Dijkstra](http://en.wikipedia.org/wiki/Edsger_W._Dijkstra)’s dictum that counting should begin at 0, I decided to launch Volume 4 with Fascicle 0. Look for Volume 4 Fascicle 1 later this year.

#### Footnote

[1] My colleague [Kunle Olukotun](http://ogun.stanford.edu/~kunle/) points out that, if the usage of TeX became a major bottleneck so that people had a dozen processors and really needed to speed up their typesetting terrifically, a super-parallel version of TeX could be developed that uses "speculation" to typeset a dozen chapters at once: Each chapter could be typeset under the assumption that the previous chapters don’t do anything strange to mess up the default logic. If that assumption fails, we can fall back on the normal method of doing a chapter at a time; but in the majority of cases, when only normal typesetting was being invoked, the processing would indeed go 12 times faster. Users who cared about speed could adapt their behavior and use TeX in a disciplined way.

_Andrew Binstock is the principal analyst at_ [Pacific Data Works](http://www.pacificdataworks.com/aboutus.html)_. He is a columnist for_ [SD Times](http://www.sdtimes.com/) _and senior contributing editor for_ [InfoWorld](http://www.infoworld.com/) _magazine. His blog can be found at:_ [http://binstock.blogspot.com](http://binstock.blogspot.com/)_._

