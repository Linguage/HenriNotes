# 机械辅助证明讲座

Terence Tao

**讲座总结：**
Terence Tao在他的讲座中探讨了数学中机器证明的发展，特别是正式证明助手如Lean的使用，以及大型语言模型如GPT在数学领域的潜在应用。他强调了正式证明的重要性，并讨论了如何通过合作和将复杂问题分解为小块来提高证明过程的效率。他还提到了机器学习在发现数学联系和生成猜想方面的潜力，尽管目前的技术水平还不能完全替代传统的数学直觉和证明方法。

**提问环节回答：**
1. **关于正式证明的可读性问题：**
   - Terence Tao指出，虽然存在一些证明（如布尔P问题）人类不太可能阅读，但我们可以通过分析计算机生成的证明来提取人类可理解的证明。他认为这不是一个可怕的事情，因为我们已经在很多数学领域依赖于大型数值计算。

2. **关于直觉在证明中的作用和自动化的可能性：**
   - 他提到，尽管大型语言模型可以生成看似直觉的想法，但它们在区分好主意和坏主意方面表现不佳。目前，AI还无法自动化证明的直觉部分，除非在AI技术上有重大突破。

3. **关于蓝图的需求：**
   - 蓝图是为了帮助人类组织和协调大型项目，将复杂问题分解为易于管理的小部分。这不是为了计算机，而是为了人类能够更有效地合作。

## 主持人

你好，我是AMS的主席Briana C，很高兴欢迎你们参加这次座谈会讲座。这是AMS会议中最古老的讲座系列，始于1895年。第一次座谈会讲座发生在1896年的西北大学，那是我的母校，所以我不得不提一下。我们的演讲者名单包括了许多数学界的名人，如Burkoff、Morse、Fyon Tari Chon、Milner、Smil、Nurgate和Tate等。今天，我们也很荣幸有Terence Tao作为我们的演讲者，他在数学界有着举足轻重的地位，不仅因为他的学术成就，还因为他在科学和技术领域的贡献。

Terence Tao，你可能不需要介绍，因为他在《纽约时报》的填字游戏中出现过。我不想通过列举他所获得的奖项来占用他的时间，但我可以给出他成就的简短列表。他在2006年获得了菲尔兹奖，是皇家学会、澳大利亚科学院、美国艺术与科学学院和国家科学院的会员。他有超过350篇出版物，这意味着他几年来几乎没有睡觉。他的研究涵盖了从纯数学到应用数学的广泛领域。他也是总统科学和技术顾问委员会的成员，指导了20多名博士生。


## 讲座正文

好的，谢谢Briana。我很高兴能在这里参加JMM并得到这次讲座。这总是令人愉快的，能够在旧金山做这次演讲。那么，我们谈论的是一个我认为真正令人兴奋的发展，它将塑造我们的未来，这是过去几年里许多技术的发展，它们使得机器和计算机能够帮助我们更有效地进行数学研究。

现在，这对一些人来说可能并不新鲜，因为我们实际上已经使用机器和计算机进行数学研究好几个世纪了。我在这里使用“机器”和“计算机”这两个词时，它们有轻微的区别。当我们谈论机器辅助数学和计算机辅助数学时，它们实际上是同义词。但最初它们并不是，因为计算机过去是人类。

然后是机械的，最后是电子的。例如，计算机最早的用途之一是建立表格。比如纳皮尔等人建立的对数表，基本上是由大量的人力计算机建造的。这些是计算机辅助数学最早的一些例子。表格今天仍然非常重要。我的意思是，不再是对数表了，但是大量的实验数学是基于创建大量的有趣事物的表格，尤其是在数论领域。

所以，例如，著名的高斯和Legendre建立了质数表，并用它来推测质数定理，这当然现在是一个定理。同样，在60年代，Bswen D等人创建了大量的关于鹿的排名等的大数据表，这是BSD猜想形式化的一个关键输入。也许数学中最大的表格是OIS在线百科全书数学序列。这是一个包含数十万个整数序列的数据库，每天我认为数学家们都会发现意想不到的联系，或者重新发现现有的联系。

我自己也使用OIS，如果我知道有一个公式但我记不起来，我可以计算前五个元素，通常都能找到。最近，人们开始使用大型数学对象数据库作为神经网络的训练数据。我稍后会给你们一个例子。所以这是使用计算机的一种非常古老和传统的方式。另一个重要的用途当然是在数值计算或科学计算中，这也是一个非常古老的主题。可以说第一个大型科学计算是在20年代，当时Len被要求为荷兰新堤坝的建设建模流体流动。所以她组建了一个人力计算机团队来模拟会发生什么。

这是浮点运算首次引入的地方，当然我们现在使用科学计算来模拟PDEs，解决大型方程组系统。当然，我们使用它们来进行计算机代数包，如Magma、Maple、Sage等。如果你要做一个大的数值积分或代数，你知道计算机基等等，我们现在都在数学的各个领域中常规地做这些事情。当然，数值计算有时是不准确的，有舍入误差和其他可能的问题。但是有方法可以使计算更严格，例如，而不是使用浮点运算，如果你使用区间运算，如果你用误差范围表示数字，一个下界和一个上界，你保持这些界限，像实数一样有限或无限位置。那么你可以避免错误，至少原则上是这样，只是可能会使运行时间更长。最近，有更先进的代数包，不仅仅是你在Sage或Mathematica中得到的标准东西。

这些被称为SAT求解器、可满足性求解器或满足模理论求解器SMT。所以SAT求解器给你的是，你输入一组语句，一堆命题P1、P2、P3等等，你说P1和P2或P3是真，P3和P4不是P5，其中一个是真的。它们会尝试看看是否有解决方案。许多问题可以表述为一个SAT问题。所以如果你有一个通用的SAT求解器，你可以潜在地只是把它输入到这样一个程序中，为你解决问题。然后有这些更复杂的变体SMT求解器，你还输入代数定律，你知道你有一些变量，你假设这些变量遵循某些定律，你问能否从你已经有的定律中推导出一个新定律。所以这些是非常强大的，不幸的是SAT可解性是一个NP完全问题。一旦你有成百上千的这些命题，实际上解决这些问题变得非常困难。但它们仍然非常有用。

这是一个典型的SAT求解器应用的例子。几年前，有一个著名的问题在Koric中被称为布尔P问题。毕达哥拉斯三元组问题，问题是你取自然数，并将它们分成两个颜色类别，红色和蓝色，你问是否总是有一种颜色类别包含一个毕达哥拉斯三元组，三个数字a、b和c，使得a² + b² = c²。结果发现我们没有人类对这一陈述的证明，但我们现在知道这是真的，因为一个SAT求解器。所以有一个大规模的计算表明，如果你只到7824，你不能这样做。有一种方法可以将数字从1到7824分成两类，没有一个类别包含毕达哥拉斯三元组，但一旦你上升到7825，无论如何你做，两个类别中总有一个必须有一个毕达哥拉斯三元组。原则上这是一个有限的计算，因为只有两种到七二五的不同方式来计算不同的分区，所以你可以检查每一个，但这是计算上不可行的。但是有了SAT求解器，你可以重新表述这个问题作为一个三可满足性问题。这不仅仅是运行求解器，你必须优化它等等，但确实可以解决这个问题。它给你一个证书，给你一个证明，实际上，这是当时世界上最长的证明。首先，它花了四年的CPU时间来生成，是一个200TB的证明，虽然它是可压缩的，我认为它仍然是有史以来第二大的证明。

但我认为这仍然是使用计算机的一种更传统的方式。但我认为令人兴奋的是，我们有很多新的方式可以使用计算机来做数学。当然，有一些无聊的方式，比如我们使用计算机发电子邮件和写LaTeX，我指的是这些，但有一些新的模式，它们通常有些许特定的应用，但我发现真正有趣的是它们可以潜在地结合在一起。它们的结合可能是通用的，我们中的许多人都可以使用，所以这三件新事物，首先是机器学习算法，如果你有问题，如果你有很多数据。你可以设置一些专门的牛顿网络来训练它，它可以为你生成计数器示例，尝试生成连接，人们开始在各种数学领域使用这个。我稍后会给你一些例子。

所以这是一个发展，也许最引人注目的发展是大型语言模型，如GPT。这些是非常通用的模型，可以理解自然语言。到目前为止，它们还没有直接用于数学，我相信你们中的许多人已经尝试过与GPT交谈，要求它解决你最喜欢的数学问题。它会给出一些看似合理的废话，一般来说，但正确使用时，我认为它们确实提供了很多潜力。我的意思是，我偶尔发现这些模型可以是有用的。我最初没有想到的证明技术，或者建议相关主题或文献，它们实际上最有用于次要任务。所以对于实际进行数学研究，它们还没有真正证明自己，但对于编写代码或组织参考文献等更常规任务。这些LMS非常有用，但第三种新技术，已经存在了二十年，但直到现在才开始准备好投入使用，是这些正式证明助手。

这些是设计用来验证电子设备的语言，但它们也可以验证数学证明，关键是它们可以验证大型语言模型的输出，它们可以弥补LLMs原则上的最大缺陷。它们允许新的数学方法，特别是它们可以允许真正的大规模合作，没有这些正式证明助手我们真的做不到。它们还可以生成数据，这些数据可以用于其他两种技术。我将分别讨论这三件事，但它们开始尝试将它们结合起来，但它们仍然有点原型阶段。

现在，我认为使用所有这些技术，并将它们与计算机代数系统和SAT求解器结合成一个集成的软件包，可能会非常强大和系统化。让我们从证明助手开始。计算机辅助证明并不新鲜。著名的四色定理在1976年部分由计算机证明，尽管在当时，按现代标准，我们不会称之为完全形式化的证明。1976年的证明是一个长篇文档，包含许多子声明，其中很多是手工验证的，很多是由电子计算机和人力计算机验证的。我认为其中一位作者的女儿不得不检查500个图形，确认它们都具有这个放电属性，实际上证明中还有很多小错误。在证明中，这些都是可修正的，但它确实不符合今天计算机验证证明的标准。

第一个证明，好吧，它花了20年时间。对于一个替代证明的四色定理进行了验证，这个证明更接近于完全形式化，大约有10到15页的人类可读论证。然后它归结为一个非常具体的计算，你可以用任何你喜欢的编程语言运行计算机程序来验证它，所以它是一个计算机可验证的证明。但它仍然不是一个正式证明，就像它没有用专门设计只输出正确证明的形式化证明语言编写一样，这不得不等到21世纪初。当时，W和G实际上在一种早期的证明助手语言中形式化了整个四色定理，所以现在我们知道四色定理是正确的。好吧，假设你信任C编译器。

另一个著名的机器辅助证明，最初是人类证明，但最终由计算机验证，是关于球填充猜想的证明。球填充猜想是关于如何在平面上有效地打包单位球体的声明。有一种自然的方式来堆积单位球体，就像你在杂货店看到的橘子堆叠方式一样。它被称为六角紧密堆积，还有一种具有相同密度的对偶堆积，称为立方紧密堆积，它们有一个确定的密度π/32。这被猜测是最密集的堆积。这是一个非常难以证明的陈述，所以这是一个在无限多变量中的优化问题，你知道每个球体都有不同的定位，所以有无限数量的球体。你试图证明涉及无限数量的变量的不等式，解决无限数量的约束。所以它并不立即适用于计算机验证。但在50年代，人们意识到可能可以通过某种蛮力计算来实现这一点。于是Toth提出了以下范式。

每次你堆积球体，它都会伴随一个von Neumann细胞，这是一个多面体，其中所有点都比球体中心更接近。这将空间划分为所有这些小多面体，这些不同细胞的体积之间有各种关系。你知道，你只能将一定数量的球体打包在参考球体旁边。这创造了所有这些约束，所以希望的是，如果你能收集足够的不等式。相邻von Neumann细胞的体积，也许每个这样的不等式系统原则上给你一个堆积密度的上界。如果你得到足够多的不等式，也许你可以得到最佳界限。所以人们尝试了这种方法很多年，包括一些错误的尝试。但他们没有能够使这种方法工作。但是Thomas Hales和他的合作者能够适应这种方法，使其在1994-1998年的一系列论文中工作。但他们不得不修改策略很多，所以他们没有使用von Neumann分解，而是使用了一个更复杂的分解。

他们不得不定义一个新的评分函数，而不是体积，但基本上策略是相同的。他能够证明大量相邻多面体的线性不等式。然后只是使用线性规划就能得到一个界限，并且通过正确的评分和正确的划分选择，它就是最佳界限。这是一个非常灵活的方法，因为你有很多方式可以做划分，你有很多方式可以做评分，但它实际上是太灵活了。这里有Hales的合作者Samuel Ferguson的一句引用，他说他们每次遇到解决最小化问题的困难时，就可以调整评分函数来适应困难。这个函数变得越来越复杂，但每次改变我们都可以减少几个月或几年的工作。这种不断的调整在我的同事中并不受欢迎。每次我在会议上展示我的工作进展时，我都在使用不同的最小化函数，更糟糕的是这个函数与早期论文中的不兼容，这需要回去修补早期的论文。所以证明基本上是一团糟。他们最终在1998年完成了它，并且能够从线性规划计算中得出球填充猜想。最初是手工完成的，但随着复杂性的增加，别无选择，只能更多地依赖计算机。所以当证明公布时，证明是由250页的笔记和大量的程序和数据组成的，它非常难以审查。花了四年时间由一个12人的评审小组来审查这篇论文，即便如此，小组只有99%的确定性证明的正确性。他们不能确定计算是否正确，因为原则上都是可行的，但就像你必须自己实现所有这些不同的计算机计算一样。但最终它被接受了，但显然有一个很大的星号，关于这是否真的是一个有效的证明有很多争议。

所以这是第一次真正高调使用正式证明助手，因为这是一个结果，人们对其正确性有严重的怀疑。所以他们在2003年由Hales发起了一个项目，将这个庞大的证明以完全形式化的方式写下来，以便标准证明助手可以验证它。他估计这将需要20年时间，他聚集了21个合作者，实际上只花了11年。但最终他们做到了，他们首先创建了一个蓝图，一个人类可读的证明版本，将事情分解成非常小的步骤，然后逐步形式化每个步骤。最终完成了，然后他们发表了一篇关于形式化的论文，只在2017年出现，所以这是大约20年前的形式化的最新水平。像这样，可以形式化大型复杂的结果，但需要巨大的努力，不是你会例行公事的事情。

有一个更近期的类似精神的努力，由Peter Scholze发起，他称之为液态张量实验。Scholze引入了一种叫做凝聚数学的理论，这真的远离了我的专业领域，但基本上，某些类型的数学，你想在各种类别中工作。比如拓扑群和拓扑向量空间的类别，问题是它们不是服从的类别，它们没有一个好的核或像函数空间这样的好东西。但它们不服从，所以Scholze提出了用一个更花哨的版本替换所有这些标准类别，称为凝聚类别。然后希望你可以使用更强大的代数来处理拓扑结构或分析结构，比如B空间，但为了使理论工作。有一个特定的消失定理，我在这里写了，但我不能向你解释，所以有一个特定的类别，涉及P双曲空间的群，必须消失，这个消失定理是必要的，以便其余的理论实际上是有用的。

如果你想应用到功能分析，特别是，Scholze在一篇博客文章中说，你知道我在2019年大部分时间都在痴迷于证明这个定理。几乎要疯了，最后我们能够把论证写在纸上，但我认为没有人敢看过细节，我仍然有一些挥之不去的疑虑。有了这个希望，有了这个定理，Scholze希望凝聚公式可以成功地应用于功能分析。或者是假的，99%的确定是不够的，因为这是最基础的重要性，他说我认为这可能是我最重要的定理。实际上，这真的是一个大声明，嗯，它最好是正确的，所以这是另一个案例，人们非常希望证明能够形式化。所以他公开在互联网上寻求帮助，用现代证明助手语言C Lean来形式化这个证明。所以，Lean基于这样一个理念，它有一个巨大的数学定理库，就像F FAL微积分或群的分类。许多基础数学定理已经在这个大库中形式化了，理念只是继续在这个库上构建，并用额外的项目添加到它。但其中一个问题是，你需要的许多基本工具，比如同调代数和拓扑理论，实际上还不在库中。所以他们实际上必须首先建立这个理论的基础，并在库中形式化它，但基本上是在一年内完成了一个关键的子定理的形式化。然后在大约一年后完成了整个项目的形式化。

除了让Peter确信一切都是正确的之外，还有一些其他的好处。首先，在形式化过程中发现了证明中的一些较小错误，但它们被修正了。还有一些小的简化。有一个重大的简化实际上发生了。原来的证明使用了一些非常复杂的东西，我不想称之为Breen-Deligne解析，但在形式化过程中，他们发现有一个更弱版本的这个理论，足以形式化这个应用。但这实际上是一个重大发现，因为这个更弱的理论也可能攻击一些其他问题，Breen-Deligne解析不适合的问题。现在数学库在支持同调代数理论和许多其他方面做得更好，这有助于其他形式化项目变得更容易。

我对几个月前对这种形式化感兴趣，所以，像开普勒实验一样，你不能直接将论文从档案中转移到Lean中。我们发现，首先创建一个中间文档真的很有帮助。这是人类可读证明和正式证明之间的一个中间文档，我们称之为蓝图。它看起来像人类的证明，并且是用LaTeX的一个版本编写的。但是，证明中的每个步骤都与Lean中的引理相关联，所以它非常紧密地集成在一起。它有一个非常好的特征，它可以创建依赖图。你可以看到你可以看到哪些部分的证明已经被形式化，哪些还没有，以及哪些依赖于哪些。实际上，它给写论文的过程提供了很多结构。你知道，我们现在手工做这些事情，没有太多的帮助。

Scholze说，写蓝图的过程真的帮助他更好地理解了证明。实际上，人们也采取了相反的方式，有一些软件可以将看起来像计算机代码的正式证明转换回人类可读的证明。这里有一个原型软件。这里有一个拓扑学中的定理，如果一个函数在密集集上连续，并且有一些额外的属性，那么它就是全局连续的。证明最初是在Lean中编写的，然后自动转换为人类可读的证明，但再次，你可以在每一步展开和收缩。如果有一步你想要更多解释，你可以双击它，它会展开并给出所有的论证。你可以点击证明中的任何一点。它会告诉你当前的假设是什么，你正在尝试证明什么，你可以给出很多结构。我认为最终，教科书，这可能是一个好格式。比如说，对于本科生的教科书，有一些难以理解的分析或拓扑学的证明，以一种你真正可以深入了解的方式编写，而不是以静态的方式。但你可以一直钻到基础公理，如果你想要的。

好的，关于这些形式化项目的一件事值得注意的是，它们允许大规模合作。你知道，在其他科学领域，人们与20人、500人、5000人合作，但在数学中，我们还没有真正以这种方式合作。部分原因是，如果你想与20人合作，如果你不认识这20人，并且不完全信任他们做的是正确的数学，那么这将非常困难。因为每个人都必须检查每个人的贡献。但是有了证明系统，证明系统提供了正式保证。所以你可以真正与你从未见过的数百人合作，你不需要信任他们，因为他们上传代码。Lean编译器验证了，是的，这确实解决了他们声称的问题，然后你可以接受它，或者它没有。

所以我自己也体验到了这一点，因为我几个月前对形式化产生了兴趣。所以我最近证明了一个组合定理。与Tim Gowers、Ben Green和Freddy Manners一起，它被称为Polom-Froissart猜想。确切的猜想并不重要。这是一个组合学中的猜想，你有一个小的有限向量空间的子集，你想证明它非常接近一个子群的余集。这是一个在讨论会上高度追求的领域，所以我们有一篇30-33页的论文，最近证明了这一点。幸运的是，我们认为这是一个很好的候选者来进行形式化。所以我在一个专门讨论Lean的互联网论坛上寻求帮助。然后大约有20-30人加入了进来，实际上只花了三周时间就形式化了。所以形式化项目所需的时间正在大幅减少。特别是，形式化这个项目所需的时间大约与我们最初写论文的时间相同。当我们提交论文时，我们能够作为一个注释，证明实际上已经被形式化了。所以，正如我所说，它使用了一个叫做蓝图的东西，将证明分成了很多小部分。所以它创建了这个漂亮的小浮点图。这是项目早期阶段的图表图片。所以底部有一个叫做pfr的节点，只有前面的人才能看见，那是我们试图证明的最终定理。在截图的时候，这个节点是白色的，这意味着它还没有被证明，甚至还没有被正确陈述。所以在你证明定理之前，你必须首先陈述它，然后你必须做出定义等等。蓝色是已经被定义但尚未证明的事情。绿色是已经被证明的事情。所以在任何时候，有些气泡是白色的，有些是蓝色的，有些结果依赖于其他结果。所以形式化的进行方式是，不同的人只是抓住了一个准备被形式化的节点，因为也许所有依赖于它的结果都已经形式化了，他们只是形式化了那一个步骤。独立于其他人。你不需要太多协调。我的意思是，我们在互联网论坛上协调，但每个小节点都非常明确。有一个非常精确的定义和一个非常精确的要证明的东西，我们只需要证明，我们真的不在乎证明是什么。所以，是的，所以人们只是分别挑选这些小声明，并且随着时间的推移，它就像这样折叠起来。这是典型的证明步骤的样子。这是Rouer距离是非负的证明。这是Lean中的代码。它看起来有点像数学，但实际上一旦你熟悉了语法，它实际上就像阅读LaTeX。第一次阅读LaTeX，它看起来像一堆混乱的符号。但每一行实际上都对应着数学英语的一个句子。例如，第一行，如果你想证明这个距离是正的，证明两倍的距离是正的就足够了。所以你用两倍的距离来工作，因为结果有一个引理限制了两倍的距离。所以，是的，每一行实际上都相当符合我们对数学证明的思考方式。

好的，所以幸运的是，证明没有审查任何主要问题。有一些小问题，但非常非常小。我们也需要再次添加到数学库中。我们使用的数学库中没有Shannon熵，现在有了。关于形式化的一件事是，它仍然需要比写证明更长的时间，但可能大约是10倍。这很不幸，如果形式化写证明比写证明更快。那将是转折点，然后我认为很多人都会转向，因为得到正确性的保证。所以我们还没有到那一步。但它绝对比以前快得多，但有一件事我们注意到，实际上，虽然写证明仍然需要很长时间。如果你想修改证明，改变一些参数，使它更好一点，那么在正式设置中可以更快地完成。这比用纸证明要快得多，因为用纸证明，如果你改变了所有的小参数等等，你可能会犯一些错误。然后你得回去，这很烦人。但在正式证明中修改现有的证明比从头开始创建一个要容易得多。例如，我们证明中出现了一个12次方的常数。几天后，有人发布了一个改进的论证。将12改进到11，我们能够在几天内适应正式证明。是的，因为你可以使用合作，我认为这个过程是可扩展的。最近，Kevin Buzzard发起了一个为期五年的项目，目标是形式化FLT的证明。这是一个相当大的目标。因为有很多子部分根本没有正式证明。所以我认为这将是一个雄心勃勃的项目，但我认为现在是可行的。五年前做不到，但现在我认为是可能的。

好的，所以这是四个更多的证明。另一个。好的，好的，好的，我可能实际上需要加快一点速度，好的，所以机器学习使用新网络在不同的数学领域变得更加普遍。我想我会跳过这个，所以机器学习的一个应用是在PDE中构建各种问题候选的近似解。

例如，在流体方程中有一个著名的问题，你知道Navier-Stokes方程在有限时间内是否会破裂，油方程在有限时间内是否会破裂。Navier-Stokes方程仍然是一个挑战，但油方程最近取得了很多进展，人们开始构建近似自相似解。油方程，这些自相似解有一些星号，但星号正在慢慢被移除。证明策略之一是首先构建一个近似的自相似解，看起来即将破裂，然后使用严格的微分理论将其完善为实际的破裂解。而机器学习已经证明在生成这些近似解方面非常有用，但我会因为时间原因跳过这部分。我最喜欢的机器学习应用于数学的例子是关于结理论的。这是一个近期的工作，结是数学中一个非常古老的主题。在结的研究中，你研究的一个基本事物是结的不变性。你可以赋予结一些取决于结的拓扑或几何的统计数据。例如，有一种叫做签名的组合不变量，还有著名的琼斯多项式、HOMFLY多项式，这些都是结理论中的重要不变量。然后我们可以谈论结的补空间的体积和其他几何不变量。所以有大量的结数据库，你可以生成数以百万计的结，并计算所有这些不变量。但它们来自数学的不同领域，一些结的不变量来自组合学，一些来自代数，一些来自低维拓扑，它们之间的关系并不明显。但数学家所做的是，他们在这些大型结数据库上训练了一个神经网络，并研究了结的超不变性和签名，这是组合不变量。他们发现网络可以从超不变性预测签名，准确率高达99%。他们使用一半的数据来训练模型，然后用另一半数据来测试。所以他们发现，结的签名必须是超不变性的函数，或者至少与超不变性非常密切相关。但是神经网络的问题在于，它们给出了一个函数关系，至少是一个推测的函数关系，但这是一个极其复杂的函数。它是数百个非线性函数的组合，它不会给你任何关于关系是什么的洞察，它只是显示了存在某种联系。但有可能进行一些分析，他们实际上尝试了一些非常基础的事情，叫做敏感性分析。这个神经网络给出了一个函数，基本上他们输入了20个超不变性作为输入，签名作为输出。所以它基本上是一个从20个变量到整数的函数。他们决定做的是，一旦有了这个函数，他们就测试了函数对每个输入的敏感性。他们只是改变了20个变量中的一个，看看输出会发生什么。他们发现，只有3个变量实际上对函数有重要影响。其他17个变量基本上不相关。所以他们专注于这三个变量，并开始绘制这两个或三个变量的签名作为函数的图表。使用颜色等，他们开始看到模式，并能够使用这些模式来推测各种不等式和关系。结果他们推测出的第一个不等式是错误的，他们可以使用神经网络和数据集来确认这一点。但经过一些来回，他们最终确定了一个正确的关于这些不变量和签名的不等式。然后他们能够找到他们推测的不等式的严格证明。所以这是一个非常好的使用机器学习工具来指明方向的例子。但然后回到传统的数学方法来证明事物。

当然，现在最引人注目的发展是大型语言模型，比如GPT。有时它们工作得非常好。这里有一个GPT-4的例子，这是OpenAI最先进的大型语言模型。它实际上解决了一个国际数学奥林匹克竞赛中的问题。这个问题是一个函数的B功能性方程，你能解决这个函数吗？它给出了一个完全正确的证明。现在这是一个非常挑选的例子，我认为他们在这篇论文中尝试了所有最近的国际数学奥林匹克竞赛问题。他们能够解决大约1%的问题。众所周知，它甚至在基础算术上也很糟糕。如果你让它计算7乘以4加上8乘以8。它会给出错误的答案，它会给出120，然后它会继续保持下去。如果你在解释过程中指出它们犯了一个错误。并说我很抱歉，之前的计算是错误的。这些大型语言模型让我想起了一些基础薄弱的本科生。如果你在办公时间问他们在黑板上解决问题，他们会尽力尝试，但有时它们工作得非常好。但通常它们非常非常不可靠。但是有很多有趣的最近实验，你可以将这些语言模型与更可靠的工具结合起来。进行数学计算。例如，GPT现在有了Wolfram Alpha的插件，所以如果你让GPT做一些算术计算。它知道最好不要自己尝试，它会将任务外包给Wolfram Alpha。然后有一些更近期的例子，人们正在将这些语言模型与证明助手结合起来。比如Lean。如果你要求它证明一个陈述，证明两个开集的并集是开的。如果你要求一个原始的大型语言模型。它会给出一个看起来像证明的陈述，但证明中有很多小逻辑错误。但你可以让Lean编译。如果有编译错误，它会将错误发送回最后一个GPT，并要求它更正并创建一个反馈循环。实际上，它可以被用来解决大约本科数学作业水平的问题。通过这种技术，如果它有效，我当然有时它会卡住并放弃。因为它永远无法让Lean编译器接受这个论点，但它开始取得一些进展。正如我所说，我发现它作为一个缪斯工具非常有用。就像当你刚开始一个项目时，我最近试图证明一个组合恒等式。我有一些想法，我想使用一些特殊情况的代数工作。但没有什么效果。我向GPT寻求了一些建议，它给了我一些我已经考虑过的建议，加上一些要么完全无效要么错误的建议。但它确实告诉我，你应该使用生成函数。我应该已经知道了，但在那个时候，它逃过了我。但有了这个提示，我能够让它工作。所以你知道，作为一个检查你的思维过程的人，它是有用的。它仍然不太好，但它有潜力使用。有一个我现在越来越多使用的另一个工具。它被集成到一个叫做VS Code的东西中，这是一个编写代码的编辑器，但它也可以用LaTeX编写。有一个叫做GitHub Copilot的人工智能动力自动完成工具，你输入你的代码或LaTeX，根据你已经输入的所有文本。它会建议一个新的可能的句子来生成。所以它可以非常有用，用于编写代码。你写下三行代码，它就帮你写第四行，有时完全正确，有时不完全正确，有时完全是垃圾。但是你可以接受它，它可以节省很多时间，特别是当你做一些非常机械的代码时，你在重复某些东西。它适用于LaTeX。我最近写了一篇LaTeX博客文章，试图估计一个积分。我将积分分成三部分。我说第一部分我可以通过这种技术估计，我写下了如何使用这种技术的估计方法，然后GitHub Copilot建议如何估计第二项。实际上，它提供了一个完全正确的论证，它只是我已有论证的一个修改版本。所以它非常擅长修改你已经输入的文本，并且它正在慢慢被集成到证明助手中，比如Lean。所以，对于一些简单的证明步骤，我们可以让很多AI来帮助我们完成。你知道，在正式的论文证明中，并不是所有的步骤都那么显而易见或明显正确。我认为，随着证明自动化变得更加容易和扩展得更好，我们可能会看到AI在这方面发挥更大的作用。最终，我们可能能够以一种全新的方式进行数学研究，我们现在无法做到的方式。我的意思是，我们现在一次证明一个定理，然后证明另一个定理。最终，我们可能会自动化地探索整个定理空间，探索数以百万计的不同陈述，哪些是真的，哪些显然是错误的，并且能够探索它们自己的几何结构。我认为，我们将看到许多不同的方式去做数学，我们将看到许多不同的方式去建立联系，这些领域我们目前不会。这将使合作变得更容易，工作在数学的不同领域。特别是，你可以使用这些工具来将所有这些任务分解成小块，这些大型复杂项目，加上大型语言模型实际上会变得非常擅长于让人类了解任何数量的先进主题。

好的，我们还没有完全到达那里。如果例如，证明形式化仍然需要大约10到20倍的时间来形式化一个证明，而不是手工完成。但它正在下降，我看不出为什么这个比例不能最终降到1以下。最终，我们可能会解释我们所有的证明给GPT，GPT会生成Lean和所有这些东西，我们会问问题，当我们不清楚的时候，然后它会生成证明，并同时检查我们的工作。所以我认为这些都是未来的事情。好的，所以谢谢大家的聆听，这很棒。我认为我们还有几分钟可以回答几个简短的问题。是的，这里有一个麦克风。是的，我们可以使用这些麦克风，还是我们在观众中叫人？是的，太好了。我看不到麦克风从这里，所以叫到的人可以问问题，好吗？当然，没问题。所以，有些人对AI辅助数学证明的进步提出了一个预测。我们可能会进入一个时期，新的定理被正式验证，但我们还没有技术将其转化为人类容易理解的形式。你看到这会是一个问题吗？嗯，这已经发生了。例如，这个布尔P问题。没有人真正会去读那个证明。所以我认为这并不可怕。我们知道，我们已经在很多数学领域依赖大型数值计算。当然，我们仍然希望有人类可理解的证明，但正如布尔P定理的例子所示，你可以从不可理解的计算机证明中分析，并从中提取出人类可理解的证明。所以我认为这将是我们未来做数学的一种方式。澄清计算机系统证明，使它们对人类可理解。谢谢。我可以问你那边的问题吗？我的问题是有点推测性的，但我想征求你的意见。关于人类直觉在未来的作用，因为我们谈论的很多是将人类直觉的形式化成为正式的数学。我想知道你是否会认为在不久的将来，证明的直觉部分，也就是想出证明想法的部分，可以自动化吗？不是在不久的将来。正如我说的，这些大型语言模型可以生成看起来像直觉的东西。但在非常低的层面上，证明一两步证明时，我们可以使用这些证明助手来挑选出好的直觉，并丢弃坏的。但大型语言模型现在非常糟糕的是试图区分好主意和坏主意。它们只是生成想法。所以除非在AI上有另一个突破，否则我不认为这会在不久的将来发生。

好的，我们再从这边拿一个问题。

我很好奇关于蓝图的需求。是因为系统还不知道足够的定义，还是因为证明空间太大，或者是两者的结合？

不，这是为了人类组织起来。如果你想协调20个人在同一项目上工作，没有人像许多在这些项目上工作的人那样理解整个证明。所以你需要一些结构来将其分解成真正小的部分，对于个人来说确实是自包含的。所以这是为了将一个复杂的问题分解成许多容易处理的部分。就像现代工业中的分工一样。

好的，我邀请所有其他等待提问的人加入我们在204房间的讨论。让我们感谢Terry的精彩演讲。




0:02
hello hello
0:08
hello good afternoon I'm Briana C I'm president of the AMS and it's my pleasure to welcome you to the
0:15
colloquium lectures these are the oldest lectures at the meetings of the AMS the
0:21
first meeting was held in 1895 the second in 1896 where the first
0:27
colloquium lectures actually took place and those were at Northwestern University and since that's my home
0:32
institution I can't help but mention that the list of speakers is a veritable
0:38
who's who in mathematics including burkoff Morse fyon tari Chon Milner smil nurg
0:49
Tate and the list of people I've left off is well equally prestigious to those
0:55
that I included and amongst them was also our speakers today's um adviser
1:00
Stein Ilia Stein so with that I'll turn to the introduction of Terry tow Terry may
1:09
be somebody who doesn't need introduction after all he's been in a crossroad puzzle as a clue in the New
1:15
York Times Crosser puzzle I don't want to um use up all his
1:21
time by listing the awards he's won but I could um I'll give you just a short list of the highlights of the fields
1:28
medal in 2006 MacArthur Fellowship he's a fellow of the Royal Society the
1:33
Australian Academy of Sciences the American Academy of Arts and Science and a member of the National Academy of Science and of course he's a fellow of
1:40
the AMS most important of those distinctions um he has over 350
1:46
Publications meaning he hasn't slept in a few years um and this includes
1:51
numerous highly influential texts and he has more than 50 collaborators and maybe
1:57
that's when I counted last week so I don't know maybe this week think there's more he's also one of the broadest
2:02
researchers in mathematics covering interests from Pure to applied um and I
2:09
won't list all of the all of the subjects but it's this not only research
2:15
he also serves the profession in numerous ways and starting in 2021 took on a very substantial role he was
2:22
appointed by President Biden as a member of the president's Council of advisers on science and
2:28
technology so he's Force he's mentored over 20 PhD students um and I could go
2:33
on and on so I've known Terry for a while uh since about
2:39
2004 or five when we first met um but one of my Fondest Memories of him was at
2:46
a party um that I was a co-host for in 2008 it was the election night and Terry
2:53
was sitting in the corner November 2008 on his computer on some website that was
2:59
giving uh election returns announcing the States before the TV was it was
3:04
really impressive and uh it's just one of my f Fondest Memories anyway I won't
3:09
keep you any long it's any longer it's my pleasure to introduce [Applause]
3:23
Terry all right thank you very much Brina I'm uh very happy to be here at this JMM to get this lecture it's always
3:30
nice to be up in San Francisco um so are we talking about um what I think is really exciting
3:37
development um in mathematics it's going to shape our future um which is really
3:42
the uh um the development over the last few years of lots of Technologies to have to to make uh machines and
3:49
computers um um help us do math um much more effectively um now this some to
3:57
some ense this is not new um we haveed used both machines and computers and I I use the terms slightly differently um
4:04
we've used both actually for centuries really um you know nowadays computers and machines when we talk machine
4:10
assisted mathematics and computer assisted mathematics they're sort of synonymous um initially they weren't because computers used to be human um
4:17
and then they were mechanical and then finally electronic um so for example you know
4:23
maybe one of the earliest use of computers uh was to build tables you know so for example um the log tables of
4:28
napia and so forth were basically built by lots and lots of human computers um and those are earliest
4:35
examples of somehow computer assisted mathematics um and tables are still really important today um I mean not so
4:41
much the log tables anymore um but you know a lot of what we call experimental
4:46
mathematics uh is based on creating lots and lots of large tables of of interesting things um especially in
4:53
number Theory um so for example famously the genre and gaus um built tables of prime numbers um and and they use that
5:00
to conjecture the prim number theorem which is of course now a theorem um and similarly in the 60s B swen D um um
5:08
created lots and lots of big tables of the deers and their ranks and so forth and this was a a key input in for
5:16
formalizing the famous BSD conjecture and maybe the biggest table of all in mathematics is the ois online
5:22
encyclopedia mathal sequences um so it's a datase of hundreds of thousands of of integer sequences and every day I think
5:30
mathematicians discover unexpected connections um or maybe ReDiscover an existing connection you know I myself
5:36
used o ois you know if if there's a if there's a a quantity which I know there's a formula for but I can't
5:42
remember it you know I can just compute the first five elements put in the Oris I can usually find it um and most
5:49
recently uh people are starting to use large databases of of of mathematical objects as training data for neural
5:55
networks and so I'll give you an example of that later so that's one very um storied and
6:02
and and antique way of using um uh computers in mathematics um the other
6:09
big use of course is in numerics or scientific Computing uh and that's also um a very old subject um arguably the
6:16
first big scientific computation was in the 20s uh when Len uh was asked to to
6:23
model the fluid flow for the construction of a new Dyke in the in the Netherlands um and so she assembled a
6:29
team of human computers basically to model what would happen to uh um to the
6:34
water flow and so forth uh it's notable for the introduction he's almost the first place where where floating Point
6:39
arithmetic was was introduced and of course we use scientific Computing nowadays to to model pdes to solve large
6:47
system of equations um and of course we uh we use them for computer algebra packages you know magma Maple sage and
6:54
so forth um yeah you want to to do a big um you know numerical integration or or
7:00
or or algebraic you know computer glob a basis whatever um you know we routinely do this now all across
7:07
mathematics um of course the numerics are sometimes inaccurate you know there are roundoff errors um and and other
7:14
possible um um problems but there are ways to make the uh the computation more rigorous for example instead of floating
7:20
Point arithmetic if you use interval arithmetic um if you represent numbers by error ranges um a lower and upper
7:25
bound um and and you keep those bounds like Ral numbers like finite position
7:31
like infinite position uh then you can um uh then you can avoid errors at least
7:36
in in principle uh at the cost maybe of um of making the runtime
7:42
longer um more recently there are more advanced um um algebra packages than
7:49
just sort of the standard things you get in um in Sage or or Mathematica um the
7:55
these things called sat solvers satisfiability solvers or satisfy satisfi modular Theory solvers smt
8:01
solvers um so what they so a SAT solver gives is you feeded a host statement um
8:07
a bunch of of propositions P1 P2 P3 and so forth and you say that P1 and P2 or P3 is true P3 and P4 and not P5 one of
8:16
them is true so forth and it will try to to see if there's a solution or not um and many problems can be phrased as a
8:22
SAT problem so if you have a general purpose sat Sil uh you can potentially uh just feed it into into such a
8:29
um um such a program and solve the problem for you uh then there are these more sophisticated variant smt solvers
8:35
where you also feed uh laws of algebra or you know so you have some some variables and you um uh you assume that
8:44
there certain laws of the the these these variables obey certain laws and you ask can you deduce a new law from
8:49
from the laws you already have um so those are um potenti is very powerful
8:54
and unfortunately sat solvability is an NP complete problem um and uh you know once you get hundreds and hundreds of
9:00
these of these propositions it becomes very hard to actually solve these uh um these problems but still um they are
9:06
very useful uh here's a typical application of a sa silver um so a few
9:12
years ago um uh there was this um famous problem in koric called the Boolean um P
9:18
Pythagorean triples problem and so the problem is this you you take the natural numbers and you color them into two two color classes red and red and blue and
9:25
you ask uh is it always the case that one of these um color classes contains a Pythagorean triple three numbers a b and
9:32
c such as a squ plus b squ c squ um and it turns out to be uh we don't have like
9:39
a human proof of the statement but we we know it's true now because of a SAT Sol
9:44
um so there was a massive computation that says that um you can if you only go
9:50
up to 7,8 824 then you can't do this there is a way to partition the numbers from 1 to
9:56
7824 into two classes neither of which contain a pth Pythagorean triple but once you go up to 7825 um no matter how
10:03
you do it you must always get um one of the two color classes must have a path pathan trouble um in principle this is a
10:10
finite computation because there's only two to seven two two five different ways to to compute um uh different partitions
10:18
and so you can just check each one but that is computationally unfeasible um but with a sat over uh you can rephrase
10:24
this problem as as a three satisfiability problem um and uh uh it it's it's not just a matter of running
10:31
the solver you have to optimize it and so forth but it is possible to actually solve this problem um and it gives you a certificate it gives you a proof um and
10:37
actually uh this is uh at the time it was actually the the world's longest proof um the the proof certificate uh
10:45
first of all it took four CPU years to generate and it's a 200 200 terabyte proof although although it is
10:51
compressible um I think it is still the second largest proof ever generated okay so that's uh but this I
10:59
still consider so a more classical way of using using U computers um but what I think is is um
11:07
exciting is that there are a lot of new ways um that we can use computers um to
11:14
um to do mathematics of course there's s of the boring ways you know we use computers to do emails and and write latch and so forth like gu I don't mean
11:21
that um but um there are S three new new modalities um which um indiv usually
11:29
they still have somewhat Niche applications um but what what I find really interesting is that they can potentially be combined together um and
11:36
the combination of them it could be something general purpose that actually a lot of us could use so the three sort of uh new things
11:45
um so the first is s of machine learning algorithms where you have a problem um and if you have a lot of data for that
11:51
problem you can set some sort of specialized newon Network to train it on the data and it can generate counter
11:56
examples for you try to generate connections um and and so people are beginning to use this in all kinds of fields mathematics I'll give you some
12:01
examples later um so that's um that's one um development um maybe the most
12:09
high-profile development is large language models like chat GPT um these are very general purpose models that can
12:15
understand natural language um to date uh they have not been directly Ed for so
12:20
much mathematics I'm sure many of you have tried talking to GPT asking you to solve your favorite favorite math problem and it will give you some sort
12:26
of plausible looking nonsense um General um but um when used correctly um
12:34
I think they do offer a lot of potential I mean I um I have I have found occasionally that these models can be
12:40
useful for suggesting proof techniques that I I wasn't initially um um um
12:46
thinking of or to suggest related topics or literature in um um they're actually
12:51
most useful for sort of uh secondary tasks okay so for actually doing math research they still have they still haven't really proved themselves but for
12:58
doing things like like like writing code or or or organizing biblography you know like a lot of the other um more routine
13:05
tasks that we do actually these LMS are very useful um but the third um um new
13:12
technology which uh was been around for for two decades but has only Now sort of becoming ready for prime time um are
13:18
these formal proof assistants uh which are languages designed to verify um uh
13:24
or to verify um many of them design to verify Electronics but they can also ver ify mathematical proofs
13:31
um um and crucially they can also verify the output of large language models which they can they can complement they
13:36
can fix the the biggest defect in in principle of of the llms um and um they
13:45
allow new types of ways to do mathematics um in particular they can allow really large scale collaborations which we really can't do without these
13:51
formal proof assistance um and they can also generate data uh which can be used for the the other two uh uh uh the other
13:59
two technologies so I will talk about each of these three things separately um but
14:04
um what but and they haven't there's beginning to be experiments to combine them together um but they're still kind
14:11
of prototypes right now but um I think the paradig of using all of them and also combining with um the computer
14:18
algebra systems and the sap solvers into one integrated package uh it could really be quite um a powerful methodical
14:25
assistant okay so let's talk I think I my first slide begin with proof assistance
14:30
um so um proof assist the um computer assistant proofs are not new um famously
14:37
the full color theorem in 1976 was was proven partly by computer um although at the time it was um by modern standards
14:44
we would not call it a fully formalized um proof the 1976 proof um the proof uh
14:51
was this long document uh with lots and lots of of of sub claims which uh were
14:56
ver like a lot of them were verified by by by by hand and a lot of them were verified by both electronic computers
15:02
and human computers and I think one of the author's daughters actually had to go through 500 graphs and check they all
15:07
had this discharging property um and actually it had a lot of mistakes too um
15:13
so there there's a lot of minor errors um in in the in the proof they're all correctable um but it was it it it
15:19
really U will not meet the standards today of of a of of a proof of a computer verified
15:26
proof um the first proof okay in so it took 30 20 years um for an alternative
15:33
proof the Four Color theorem to be verified and this proof uh is closer to being completely formal so it it it's
15:40
about 10 15 pages of human readable argument and then it reduces to this very specific computation which you can
15:46
run you anyone can just run um um a computer program in whatever language they like to verify it um so it was a
15:53
computer verifiable proof um but it still wasn't a formal proof in like it wasn't written in a formal proof
16:00
language which was designed to only output correct um correct proofs um and
16:05
that had to wait until uh the early 2000s um when w and G here actually formalized the entire for color theorem
16:11
in one of the early proof assistant languages in this case um so you know I mean now we know
16:18
with 100% certainty that the Four Color Fus is correct uh well modulo you know um you know trusting the compiler of C
16:25
okay but um all right
16:31
um another famous um machine assist of proof well actually initially human
16:36
proof but eventually computer um verified was the proof of the cap conjecture so uh the cap conjecture is a
16:43
statement about how efficient you can pack unit spheres in the plane um and so
16:48
there's a natural way to to to stack unit spheres and is the way that you see oranges stacked in in in in the grocery
16:53
store uh it's called the the hexagonal close packing and there's also a dual packing with the same density called the cubic close packing um and they have a
17:01
certain density Pi 32 and this was conjectured to be the densest packing um
17:07
so this is an annoyingly hard statement to prove um so
17:13
um you know it's it's an optimization problem in infinitely many variables you know so there there's each each sphere
17:20
has a different location and so and there's infinite number of spheres so um you know you're trying to to prove an
17:25
inequality involving an infinite number of uh of variables involving a solving infinite number of constraints um so it
17:32
doesn't immediately lend itself to commuter verification um but even in the 50s um
17:39
it was realized that possibly this could be done by some sort of Brute Force computation um and so Toth proposed the
17:46
following Paradigm um so every time you're SE packing um it comes with what's called aoid decomposition so uh
17:53
every sphere comes with a vono cell which is this polytope of all the points that are closer to the center of of that
17:58
of that sphere than to all the other spheres and this partitions um space into all these little polyhedra these
18:04
volary cells um and um there are various relationships between the volumes of these different cells um you know
18:10
there's only so many spheres that you can pack next to one one reference sphere and this creates with all these kind of constraints um and so the Hope
18:18
was that if you could gather enough inequalities between um adjacent vono
18:23
cells um the volumes of adjacent vono cells maybe um every such system inequalities in principle gives you um
18:31
an upper bound on the density of of a SE packing um and in principle if if you get enough of of these inequalities
18:36
maybe you you could actually get the optimal bound of of the2 um so people tried um this approach for many many
18:43
years and including some uh false uh attempts uh but uh this they were not
18:50
able to actually make this approach work um but uh Thomas hailes and then
18:55
later with a collaborator was able to adapt this approach to make it work in a series of papers from
19:01
9498 um but they had to modify the strategy quite a lot so instead of of using uh the vono decomposition there
19:08
was a more complicated decomposition that was used and instead of using volume they had to Define this this new
19:13
score function attached to each polyhedron but basically the the strategy was the same um and he was able
19:20
to prove lots and lots of linear inequalities between the scores of adjacent polyedra uh and then just using
19:27
linear programming was able to then get a bound and uh with the right choice of score and the right choice of partition
19:33
it was uh it was the optimal bound um it's a very flexible method um
19:39
because you lots of ways you can do the partition and lots of ways that you can do the score but it it was actually the
19:45
problem that it was too flexible so here's a quote from from hailes says that Samuel Ferguson who was H's
19:51
collaborator and I realized every time we encounter difficulty solving the minimization problem we could adjust a scoring function to SC the difficulty
19:56
the function became more complicated but with each change we could cut months or years from our work this this incessant
20:02
fiddling was unpopular with with my colleagues every time I presented my work in progress as a the conference I was using I was minimizing a different
20:08
function even worse the function was mly incompatible what what it in earlier papers and this required going back and patching the earlier papers um so the
20:15
proof was uh was a mess basically um they did eventually finish it in 98 and
20:23
they able to derive the capital conjecture from a linear programming computation from a very complic optimization program um initially it was
20:31
done by hand but um with the increased complexity there was no choice but to make it more more computer assisted um
20:38
so when the proof was announced uh the proof had uh yeah it was a combination of of 250 pages of notes and lots and
20:45
lots of gigabytes of programs and data uh and it it was famously hard to referee uh it took four years for anal
20:51
to referee the paper with a panel of 12 referees and even then the panel only 99% certain of the correctness of the
20:57
proof and they couldn't certain ify the corrections the the um the the calculations because I mean um in
21:04
principle like it was all doable but like you know the ref have to S Implement all these different computer
21:10
calculations themselves uh but it was eventually accepted um but clearly there was this
21:16
big asterisk there's a lot of controversy about whether this was really a valid proof and so this this was one of the the first really
21:23
high-profile uses of um formal proof assistance because this was a result in
21:29
which there was serious doubt about the correctness um so they created uh so har
21:35
in 2003 uh initiated a project to write down this massive proof in a completely
21:41
formalized way so that a standard proof assistant could verify it um he estimated it will take 20 years to to
21:47
make this work um it uh and so with he had he gathered 21 collaborators it
21:53
actually only took 11 years um but uh
21:58
yeah eventually what they did was that they they first created a blueprint you know so a human readable version of the
22:04
proof breaking things up into very very small steps and then they formalized each step bit by bit um and it was it
22:09
was finally done and then there was a yeah so they and they they published a paper about the formalization and that only appear in
22:16
2017 so this was sort of the state-ofthe-art of formalization you know as of say 20 years ago you know
22:22
like it was possible to formalize Big complicated results but it took enormous amounts of effort
22:29
um you know not something which uh you would uh do routinely um there was a more recent
22:36
effort in a similar Spirit uh by Peter schulzer he called it the liquid tensor experiment so uh schulzer introduced
22:43
this this theory of condensed mathematics which is uh all right this is really far from my own area of
22:49
expertise but um basically there are certain problems with uh uh so certain
22:55
types of mathematics you want to work in various categories like categories of topological obedient groups and and topological Vector spaces and uh there's
23:01
a problem that they're not obedient categories but they don't they don't have a good notion of Kernel CERN or
23:06
things don't work out properly um so he proposed replacing all L of these standard categories uh with a more fancy
23:13
version called a condensed um condensed category uh which has better category theoretic properties um and so the hope
23:20
then that you can use a lot more High powerered algebra to attack uh to to handle um things of topological
23:26
structure or analytical structure like function spaces for example B spaces um but in order for the theory to work
23:34
there's a certain Vanishing theorem which uh I've written there oops uh but I cannot explain to you oops uh okay so
23:42
there's a certain category uh um groups and there's certain X group
23:48
involving P bino spaces that has to vanish um and U this Vanishing theorem
23:54
is needed in order for all of the rest of the theory to actually be useful um if you want to apply to to to fun to
24:01
functional analysis in particular um and so schulzer what a blog post about this is said you know I
24:07
spent much of 2019 obsessed with the proof this theorem almost going getting crazy over it in the end we were able to
24:12
get an argument pin down on paper but but I think no one else has ever dared to look at the details of this and still I still have some lingering doubts um
24:20
with this hope um with this theorem the the the hope that the condensed formulas can can be fruitfully applied to
24:26
functionalis stands or fals being 99% sure is not enough because this the is of the most um most fundamental um
24:33
importance um he says I think this may be most my most important the on the date which is a really big claim
24:39
actually uh better be sure it's correct so this was another case where um there
24:45
was a great desire to to formalize the proof um so he asked publicly on the
24:51
internet for help um to formalize this in a modern proof ofis language C lean
24:57
um um and so uh again about 20 people I think um joined this project to help out
25:03
um and it it uh so so lean is based on uh um it has this philosophy where um it
25:11
has this single huge library of mathematical theorems like the F FAL calculus or the classification fin in
25:17
groups like like a lot of the basic theorems of of mathematics are already formalized in this big library and the idea is to just keep building on this
25:24
library and adding to it with additional projects um but um one of the the problems uh that
25:31
shorts are face was that a lot of the uh tools that basic tools that you needed like homological algebra Chief Theory
25:37
and topos Theory weren't actually in the library yet so actually part of what they had to do was actually set up the foundations of of that theory and
25:43
formalize it in the library first but it basically was done in about two years uh in in one year they
25:50
formalized a key sub theorem um and then uh and then the whole thing was was formalized about a year
25:56
afterwards um it um it did have some in addition to
26:02
sort of making uh reassuring Peter that it was it was everything was was correct uh there was some some um uh other minor
26:09
benefits so first of all there were actually a few minor errors in the proof that were discovered in the formalization progress um but but uh uh
26:15
but they could fixed uh also some small simplifications uh there was one big simplification actually um so they uh um
26:24
the original proof used something very complicated which I also don't want stand called the Breen delene resolution
26:29
uh but in the course of formalizing it you know it was too hard to actually formalize this this Theory but they
26:35
found that there was a weaker version of this Theory which was good enough to formalize this application but this was actually a major Discovery because this
26:41
weaker Theory could also potentially attack some other problems that that the bring to the resolution is is is not
26:48
well suited for and now the math library is is much much better in in uh it has a
26:54
lot of of uh support for for homological Al she Theory and and lots of other things which which helped other U
27:00
formalization projects become easier um I got interested in um this formalization a few months ago um so
27:09
hang on um I should say um like with the Kepler experiment so the um you don't
27:15
just directly transfer um a a paper from you know the archive or something into
27:21
um inter lean um what we found is is that um it really helps to create first an intermediate document so halfway
27:27
between a human readable proof and um a formal proof uh which we call a
27:32
blueprint um so it it it looks like a human proof and is written in a version
27:38
of latch um but like each each step in the proof is linked to a Lemma in lean
27:44
um and so it's very tightly integrated um and it has a very nice um uh there's
27:49
a very nice feature uh it can create a dependency graphs which I'll show you an example L you can you can see which parts of the proof have been formalized
27:55
which ones are not and what depends on what um and it actually it it uh it gives a lot of structure to the process
28:01
of writing a paper which you know right now we do by hand without sort of much uh much assistance really
28:08
um yeah Scher said that the process of writing the blueprint really helped him understand the proof a lot better
28:15
um um and actually people have been also going the other way um there's also
28:20
software that takes formal proofs which are written in something that looks like computer code and turns them back into human readable proofs um here is um a
28:29
prototype software so there's a there's a theorem and topology um okay you I
28:35
think it's a if a function is continuous on a dense set and there's there's some extra extra properties then it's it
28:41
continuous extends to a continuous function globally um and the proof is written uh was written first in lean but
28:48
then it was automatically converted into a human proof human readable proof but again where every step you can expand
28:54
and contract like if there's a step you want you want to explain more you can double click it and it will expand out give all the justification and you can
29:00
click at any given point in the proof and it will tell you what the hypotheses are currently what you're trying to prove and you can give a lot of
29:06
structure um I think eventually um textbooks uh this is this maybe a good
29:12
format say for undergraduate textbooks to have you know um proofs of say you know tricky films and Analysis or
29:17
something written in in a way where um you know in a not in a static way but where you can you can really um you know
29:24
drill down all the way down to the to the basic axioms if you wanted to
29:30
okay um one thing I mean one thing notable about these um formalization
29:37
projects is that they allow mive collaborations you know so you know in other Sciences people collaborate with
29:43
20 people 500 people you know 5,000 people um but in mathematics still we
29:49
don't really collaborate in um in really large groups you know five is kind of the maximum usually um and part of it is
29:57
that you know you know if you want to collaborate with 20 people if you don't already know these 20 people and you don't completely trust that they're
30:03
doing correct mathematics you know it's uh it's it's it's it's very difficult because you have everyone has to check
30:09
everyone else everyone else's contribution um but with a proof ass system the proof system provides a
30:14
formal guarantee um and so you can really collaborate with 20 hundreds of people that you've never met before and
30:21
you don't need to to to to trust them um because they upload code and and um the
30:28
the the lean compiler verifies yes this actually solves the problem they claimed and then you can accept it or or it
30:34
doesn't um so I I experienced this myself because I got interested in formalization a few months ago um so I'd
30:41
recently proven um a combinatorial theorem um with Tim GS Ben green and and Freddy manners um it sold something
30:48
called the polom F Ria conjecture um the precise conjecture is not important uh
30:53
talk it's a conject in combinatorics you have a subset of a of a fin Vector space of of small doubling uh and you want to
30:59
show that it is it is very close to actually being a co- set of a subgroup um this was a segement that uh was um in
31:07
at Comm talks that was highly sought after um so we had a 30 33-page paper um
31:13
recently proving this um mostly self-contained fortunately so we thought I thought it was a good candidate for uh
31:20
for formalization so I asked on an internet Forum specializing lean for
31:25
help to formalize it and then again like 20 30 people uh joined in and and it
31:30
actually only took three weeks to formalize so the the time taken to formalize these projects is going down
31:35
quite a bit um um so in particular um the time take to formalize this this
31:42
this project was roughly about the same same time it took for us to write the paper in the first place um and by the
31:47
time we submitted the paper we're able to put as as a as a note that it was actually the proof is actually been
31:52
formalized um so as I said it it uses this thing called a blueprint which splits up the proof into lots and lots
31:58
of little pieces um and um and so it creates this this this nice little float
32:03
this little dependency graph so um this is a picture of the graph at an early stage of the project um so there is no
32:09
down the bottom called pfr maybe only the people in the front can see it that's the final theorem that we're trying to prove um at the time of of of
32:16
the screenshot this was white which means that it had not been um proved but not even even being stated properly so
32:22
so in fact even before you prove the theorem you have to First State it uh and and then you have to make definitions and so forth um blue are
32:29
things that have been have been defined but not yet proven and green have been things that have been proven um and so
32:36
um at any state of um any point in time some bubbles are white some bubbles are blue and and some results depend on some
32:42
others um and so people so the way the uh the formalization proceeded was that different people just grabbed a node
32:49
that was ready to be formalized because maybe all the all the previous results all the results that it depended on were formalized and they just formalized that
32:56
one step independent of everybody else um and you didn't really need to coordinate um too much I mean we we we
33:03
did coordinate um uh on an internet Forum um but um each little node is
33:09
completely specified there's a very precise definition and a very precise thing to prove and uh we just need the
33:14
proof and um it we really don't care exactly what the proof is I mean it has
33:19
to be not massively long but um so yeah so people just picked up individual claims like here's one very simple claim
33:26
is there's a certain functional called rouer distance D and it had there's a very simple claim that it was non
33:32
negative uh and this turns out to have a three-line proof assuming some previous um some previous facts that would uh um
33:41
that were also um on the blueprint and so people just sort of picked up these things separately and and and and over
33:47
time it it just folded up this is what a typical step in the Pro looks like this is the proof that this rer distance is
33:52
non negative this is the code and lean it doesn't it it looks kind of a little bit like mathematics um but it
33:59
it U it is actually if you um once you famili the syntax actually reads it's
34:05
like reading latch first time you read latch it looks like a whole bunch of mess of symbols but um this um it's
34:10
actually it's um every line corresponds to a sentence in mathematical English for example the
34:16
first line if you want to prove that this distance is positive it suffices to prove that twice the distance is positive um so you work with twice the
34:21
distance because it turns out there's another Lema that bounds twice the distance um so yeah every step actually
34:28
it corresponds reasonably well to to uh U the way we think about ma mathematical
34:36
proofs yeah so uh yeah fortunately the proof uh didn't review any major issues
34:42
there some some types but very very minor picked up um uh and we also um
34:48
there were some things we need again we needed to to add to the math Library there was a um the math Library we used
34:54
Shannon entropy and shannan entropy was not in the math library now it is um one thing about about formalization
35:00
is that it still takes longer to formalize proofs than um than to write them um but and maybe about 10 times
35:07
longer I would say um which is unfortunate if it was faster if it was
35:12
faster to formalize to write from proofs formally than um um than to write my
35:17
hand I think then that will be a Tipping Point and then I think a lot of us would would switch over just because to get
35:23
the guarantee of correctness um so we're not there yet it is definitely getting a lot faster than it was before um but one
35:30
thing we we noticed is that actually um while it still takes a long time to write a proof if you want to modify a
35:36
proof to change some parameters and make it and just and make it a little bit better um that can be done much quicker
35:42
in the formal setting than in the um than with paper prooof because uh with paper prooof if you change all your
35:48
little parameters and so forth you likely make all some mistakes and you go back and and it's it's it's a very annoying process but but it's actually
35:55
much easier to to modify an existing formal proof than to create it one from scratch for example we were able there's
36:01
a constant 12 exponent that appeared in our proof um a few days afterwards someone um posted a an improvement the
36:10
argument that improved 12 to 11 and in a few days we able to adapt the formal proof to to do that as
36:16
well um yeah and because you can collaborate um I think the process is
36:21
scalable um there's there was just uh just recently Kevin buzzer for example launched fiveyear project the aim is to
36:28
formalize F last the the proof um and that is quite a a big goal because there
36:33
are lots and lots of sub portions that have that have had no formal proof at all um so that I think will be quite an
36:41
ambitious project but I think it's now doable it it wasn't doable five years ago but but now I think it
36:47
is um okay so that's four more proofs um another
36:53
um okay um okay okay I might actually have to speed up a little okay so
36:59
um all right so uh machine learning has uh using new networks has become also uh
37:05
more more um common place in in different areas of mathematics um I think I'll skip over this one so um one
37:11
place where is being used is in pde to construct um candidate approximate solutions for various problems so like
37:18
uh so there's a famous problem in in fluid equations you know do the nav St equations bu in finite time do the oil equations bu in finite time um Navia
37:26
stes is still Challen in but oil there's been a lot of progress recently um that people have been starting to construct
37:31
selfsimilar solutions to the oiler equations with some asterisks but the asteris are slowly being removed um and
37:37
one of the strategies of proof is to First construct an approximate solution approximately self-similar solution that
37:43
that that that looks like is going to blow up and then use some rigorous peration Theory to um to perur that to an actually um blowing up solution um
37:51
and machine and machine learning has turned out to be be to be useful to actually generate these approximate Solutions um but I'm going to skip that
37:58
for lack of time um I'll tell you um my favorite application of um machine learning to to
38:05
mathematics is a not Theory um so this is a recent work um so knots are a very
38:11
old subject in mathematics um and there's lots and lots of one of the fundamental things you study in Nots is
38:17
not invariance so there there's various statistics you can you can um study you can assign to a knot which depends on
38:24
the topology of the knot or the geometry of the knot um so there something called the signature which is a combinatorial
38:30
invariant um these famous polins like the Jonas polinomial hly polinomial uh then these things called hyperbolic
38:36
invariance the complement of a knot is often hyperbolic space um and then you can talk about the and the volume of
38:42
that space and some other geometric invariant and so there are these massive databases of knots um you can you can
38:47
generate millions of knots and you can compute all these invariant um but they come from very different areas of
38:53
mathematics you know so some kns some not inv variants come from comor X some come from operate algebra some come from
38:59
from from hypo geometry and it's not obvious how they related um but um what these
39:08
mathematicians did was that they they they trained a new network on this big database of knots and they studied the
39:13
hyperbolic invariance and the signature which is the comorian invariant and they found that the uh you could train the
39:19
network to predict the signature from the hyp variant with like 99% accuracy
39:24
um so they they they used like half the data to train the set and then half the data to test the set to test the new
39:31
network um and so um what this um told them is that there must be some
39:37
connection the signature of a knot is must somehow be a function or at least very closely related to a function of
39:42
hypol variance but um the problem with neon Nets is that they they give you a function a functional relationship at
39:49
least a conjectural function but it's this massively complicated function it's it's you compos hundreds and hundreds of
39:55
of of of of nonlinear functions together and it doesn't give you any insight as as to what the relationship is it just
40:00
shows you that there is a connection but it's possible to do some analysis um so
40:06
they actually tried a very basic thing which happened to work uh it's what's called aeny analysis so this new network
40:12
gave them this function basically they fed in 20 hyperbolic invariances as
40:18
input and the signature as output so it's basically a function from article 20 to to the inages I think um and what
40:24
they decided doing is that once say this function they just tested how sensitive the function was to each of its inputs so they they they just varied one one of
40:31
the 20 variables and they saw what happened to to the output and what they found was that only three of the 20
40:37
variables were actually important um that only three of them had a significant influence on the function the other 17 were were basically not
40:43
relevant at all um and so they focused on those three variables and they they started plotting um um this function
40:50
just restricted to those three variables um and that's just low enough to mention that you can eyeball the relationships
40:56
you know so they started plotting uh the signatures as a function of you know two or three of of these variables and using
41:02
color and so forth and they started seeing patterns and um they could use these patterns to conjecture various
41:08
inequalities and various relationships um it turns out that the first few uh inequalities they conjectured were were
41:14
false um and they um they could use the the neet and the data set to to confirm
41:21
this um but um with a bit of back and forth they were able to eventually settle upon a correct conjecture
41:27
relating the uh these invariants to the um um to the signature and it it wasn't
41:33
the invariance that they expected um um so yeah it was it was these um yeah they
41:39
were expecting the hyperic volume for example to be really important it to not not be relevant at all um but um but
41:46
once they found the right variables and the right concu inquality uh it suggested the proof and then they were
41:51
able to actually find um a rigorous proof of the inequality that they conjectured um so it was a very nice
41:57
back and forth between using the machine learning um machine learning tool to suggest uh um the way forward but then
42:04
going back to sort of traditional mathematics to uh to prove things okay so of course the most
42:11
high-profile um uh development these days has been um large language models like like GPT um
42:19
and sometimes they work really really well um so so here is an example of gp4 which is open A's most advanced lar
42:25
language model actually solving a problem from the IMO in mathematical LM and so it's a
42:31
question you know there's a function that OB functional equation can you can you can you prove a can you solve solve
42:37
for the function and it actually happens to give a completely correct proof um
42:43
now this is an extremely cherry-picked example um I think they they tried uh from this paper they they they tried all
42:49
the the recent IMO problems and they could solve like 1% of the problems of this method um you know famously it's
42:55
bad even at basic arithmetic um you know you there's a you ask it to solve 7 * 4
43:01
plus 8 * 8 and it'll give you the wrong answer it gives you 120 and then it will keep going say and I'll explain why and
43:07
during the course of of the explanation it it will actually make a mistake uh and uh yeah and then you then you point
43:15
out that that they made a mistake and say I'm sorry the previous incorrect um I mean these these L LS they remind me a
43:22
lot of you know if if you have sort of a somewhat weak undergraduate student in office hours and you ask problem at the
43:28
Blackboard with no with no uh um AIDS you know it will he or she will try try
43:34
their best you know and try J something looks like a proof but um yeah they they don't really have a good way of of of
43:41
correcting themselves um so you know sometimes they they work really well but often they're very very
43:48
unreliable um but there's lots of interesting recent experiments um where
43:54
you can couple these language model models to other much more reliable tools to do mathematics um so for example GPT
44:00
now comes with plugins for wol from alpha so now if you tell um ask wol um
44:06
GPT to do an arithmetic calculation it knows better than to try to do it itself it will Outsource it to wol Alpha
44:13
um um then there's a there are more recent examples where um people are coupling um these L language models to
44:21
um approve ver like lean so you know you ask it to to prove a statement you know
44:26
prove that the union of two open set is open um if you ask a raw large language
44:31
model it will give you a statement that a proof that looks like a proof but there's lots of little logical errors in
44:37
the proof but but you can force it output in in lean get lean to compile and if there's a compilation error it
44:43
will send back the error to the last L AO and have to correct it and create a feedback loop um and it can actually be
44:50
used to solve um roughly sort of undergraduate math homework level problems um by by the this technique
44:56
with you know but now with 100% guarantee of accuracy um if it works I mean of course sometimes it would just
45:01
get stuck and give up because it can never get the lean compiler to to to to to accept the argument but um it is
45:10
beginning to um uh to make some to make some Headway um as I said before I do
45:16
find uh it it can be useful um as a muse kind of like like if you're just
45:22
starting on a project um I I recently was trying to to um uh to prove some
45:29
comor identity um and I was thinking of using I I was I had some ideas in mind I
45:34
was going to use as some astics work with some special cases um but nothing was working and I asked GPT for some
45:41
suggestions and it gave me some suggestions I was already thinking of um plus some suggestions that were either
45:47
completely vacuous or or or or wrong um but it did tell me that you should probably use generating functions um
45:53
which I should have known uh but but at at the time you know it it it escaped me and and just with you know with that
45:59
hint I was able to to uh um to actually get um get the to work um so you know I
46:07
mean as as just kind of a someone to double check your your your your your thought process um it is sort of useful
46:14
still not great but it is it is uh it has some potential use um there was
46:19
another tool which I I do like and I I use more and more now um um it's
46:25
integrated into something called vs code which is an Editor to write code but it can also use for latch something called
46:31
GitHub co-pilot um it's basically an AI power autocomplete and uh you um you type in
46:38
your code or your latch whatever and based on all the text that you've already written it will suggest a
46:43
possible new sentence to generate um and so it it can be very useful for code you
46:49
you you write down three lines of code andt just the fourth and it's sometimes you get exactly right sometimes it's not exactly right sometimes it's complete
46:54
rubbish but um um but then you can you can accept it and can it can save a lot of time especially you're doing some
47:00
very menial code where you're repeating um something over and over again um it works for latch um I wrote um a latch
47:08
blog post actually recently where I was trying to estimate an integral and I broke up the integral into three pieces and said okay the first piece I can
47:14
estimate by by this technique and I wrote down how to estimate this technique and then this copil just suggested how to how to estimate the
47:21
second term and actually a completely correct argument it was just it was a modification of of of of what I already written so it's very good at just
47:27
modifying text that that has that you you've already um um appeared um and um
47:35
it's it's slowly being integrated into into proof assistance like lean um so to
47:41
the point where sort of one line proofs two line proofs we can kind of get the AI to fill in for us you know the kind of steps that that correspond like you
47:47
know this is obvious or clearly this is true in in a paper proof we um I mean not all of them but we can get to the
47:53
point where air can feel in um a lot of them that will make crew formalization a lot faster um so there's a lot of potential
48:01
it we're still it's a lot of these Technologies are very very close to prime time but you know not quite yeah
48:08
it's still like you know took me a month to learn lean and so forth um this is still they're still not completely usable out of the box but um but they
48:15
are they are beginning to be more and more useful and in surprising areas you know you wouldn't have expected they not Theory to be to to to benefit from these
48:22
tools but but they do um they can't solve math problem on their own uh except maybe undergraduate level
48:28
homework questions maybe it's the current level um but as an assistant um I think they can be very very useful um
48:35
they can generate conjectures they can uncover connections that that we um you wouldn't normally guess
48:41
um once proof automation becomes uh easier um and and and scales better we
48:47
can we may be able to do completely new types of mathematics that we we we don't do right now you know right now we um
48:56
you know we prove the one at a time I mean we're still kind of you know cross Crossman you know we take one one theorem and we prove it and we take
49:01
another theor and we prove it you know eventually you could aut make theor Prov like exploring an entire theorem space
49:07
you know of of of you know of millions of different statements and which ones are true which ones are obviously false
49:14
and you could you could explore the geometry of of of of the themselves um I think this there's a we're going to see
49:20
a lot of different ways to do mathematics um and and we're going to see a lot different ways to to make
49:26
connections in fields that that uh that that we uh don't currently and it' be a
49:31
lot easier to collaborate and work in in different areas of mathematics
49:36
um um yeah especially because you can use these tools to sort of compartmentalize um all these tasks all
49:44
these big complicated projects into small pieces and plus also these large language large language models actually
49:49
will become very good at at at uh at getting humans up to speed on on on any number of of of advanced path
49:56
topics okay um oops yeah um it's but yeah I can it's
50:03
still not quite there yet um I would say um if for example Pro formalization it still takes about 10 to 20 times longer
50:10
to formalize a proof than than to do it by hand but it's dropping um and I see no reason why this this ratio Cannot
50:16
drop below one um eventually it will become faster to to you know eventually
50:22
we may just explain all our proofs to to GPT and GPT will generate you know it will ask questions whenever we're
50:28
unclear but then it will just generate the lch and the lean and stuff for us um and we you know and EV eventually and
50:34
and you know and and and check our work at the same time um so I think this this
50:39
this is this is all in the future um all right so thanks for
50:54
listening great thank you that was lovely I think
51:00
we have a couple minutes for a few short
51:13
questions is there a
51:23
microphone yeah there will also be a Q&A next door in 204 for a few minutes after
51:30
when when this is over are we using these mics or are we calling on people in the audience yes uh that's great I
51:37
can't see the mic from here um so the person I called on can ask the question okay sure so um one one
51:44
prediction that some people have banded about uh about advances with um AI assisted um theor provs is that we might
51:51
enter a period where there's a proliferation of um proves that for new theorems that are formally verifiable
51:58
but which we don't yet have the technology to translate into forms that are easily comprehensible by humans do
52:03
you see this being an issue um well it already happens you know for example this this this this Boolean um um pagon
52:11
tripl theorem you no human will ever read that proof um so I mean I think
52:17
it's it's actually not that scary I mean you know we we we rely on big numerical computations already in a lot of H
52:24
mathematics of course we would still want to uh to have a human understandable proof but as as the not
52:31
ex not the example shows you can take incomprehensible computer proof and still analyze it um and and extract out
52:38
from it um a human proof so I think that would be one of the ways we do mathematics in the future is to is to is
52:44
to clarify computer system proofs and make them human understandable thank you
52:50
can I ask you over there to ask your question uh my question is
52:56
kind of speculative but I wanted to ask your opinion on the rule of human intuition going forward with this
53:03
because what a lot of what we talked about is formalization of human intuition into formal mathematics I was
53:09
wondering if you think that intuitive part of coming up with the idea for the proof itself could be automated in the
53:15
near future um not in the near future um as I
53:20
said these L models can generate things that that resemble intuition but it's there it has a lot of garbage um at the
53:28
very low level of of of proving like one or two steps in a proof uh we can use these these proof assistance to to to um
53:36
um to sort of um only pick out the good intuition and discard discard the bad
53:42
one but what large CLS are terrible at right now is trying to is is is differentiating good ideas from bad
53:48
ideas they just generate ideas um so unless it's another breakthrough in AI I
53:53
don't think this is going to happen anytime okay we'll take one more question from this side so I was curious about the
54:00
need for blueprints is it that the system doesn't know enough definitions
54:05
yet or is the proof space too big some combination thereof no uh it's it's more
54:11
of an organization to for the humans okay if you want to coordinate 20 people uh to work on the same project um no one
54:18
person like many of the people who work on on these projects they don't understand the whole proof um so you
54:23
need some structure to to SP it up into really small pieces um really Atomic pieces that are selfcontained for for
54:30
individual people to work on so it's it's it's it's it's it's not for the computer the computer can can compile anything um it's it's for the humans to
54:37
to break up a complicated problem into lots of of Easy Pieces um kind of like how divisional label Works in in like
54:43
modern Industries like factories okay I'm going to invite all the other people waiting to ask
54:49
questions to join us in room 204 briefly and let's thank Terry for a lovely talk