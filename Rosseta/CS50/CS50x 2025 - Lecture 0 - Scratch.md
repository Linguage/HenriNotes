
[视频链接](https://www.youtube.com/watch?v=2WtPyqwTLKM)

---
## 内容提要


这个视频是哈佛大学 CS50 课程的入门讲座，主要围绕计算机科学的基础概念和编程入门展开。以下是视频的主题内容、框架与主要知识点：

**主题内容:**

* **计算机科学入门介绍:** 包括课程概述、讲师个人经历分享、课程目标和学习方法。
* **计算机科学基础概念:** 讲解计算机如何表示信息（数字、字符、颜色、图像、视频、声音），以及算法和编程的基本原理。
* **编程语言入门 (Scratch):** 通过图形化编程语言 Scratch 介绍编程的基本概念，例如函数、循环、条件语句、变量、事件等。
* **通过项目实例学习编程:** 使用 Oscartime 和 Ivy's Hardest Game 两个游戏项目实例，讲解如何将编程概念应用于实际项目中，并强调逐步迭代开发的重要性。

**框架:**

1. **引言 (Introduction):** 课程介绍和激励。
2. **计算机科学基础 (Computer Science Fundamentals):**
    *   问题解决 (Problem Solving)
    *   信息表示 (Representation of Information)
    *   算法 (Algorithms)
3. **编程入门 (Programming Introduction):**
    *   伪代码 (Pseudocode)
    *   Scratch 编程语言
    *   项目实例分析 (Project Examples)
4. **总结 (Conclusion):** 课程展望和鼓励。

**主要知识点:**

*   **问题解决:** 计算机科学的核心是问题解决，将问题转化为输入，通过算法处理，产生输出（解决方案）。
*   **信息表示:**
    *   **一进制 (Unary):** 使用单个符号（如手指）进行计数，基数为 1。
    *   **二进制 (Binary):** 计算机内部使用二进制（基数为 2），只有 0 和 1 两个数字，通过晶体管的开关状态来表示。
    *   **位 (Bit) 和 字节 (Byte):** 位是最小的二进制单位，一个字节通常包含 8 个比特。
    *   **ASCII:** 美国信息交换标准代码，使用 7 或 8 位二进制数表示英文字母、数字和标点符号。
    *   **Unicode:**  一种更全面的字符编码标准，可以使用多个字节表示更多语言的字符和表情符号。
    *   **RGB:**  红绿蓝颜色模型，通过三种颜色的不同强度组合来表示各种颜色，通常每个颜色分量使用一个字节。
    *   **图像、视频和声音的表示:**  图像由像素组成，每个像素的颜色可以用 RGB 表示；视频是一系列静态图像（帧）的快速播放；声音可以通过频率、音量和持续时间等参数来表示。
*   **算法:** 解决问题的步骤说明，强调精确性和步骤性。
*   **伪代码:**  用自然语言描述算法步骤，不需要严格遵循特定编程语言的语法。
*   **编程概念:**
    *   **函数 (Functions):** 执行特定任务的代码块，可以接受输入（参数）并产生输出（返回值或副作用）。
    *   **条件语句 (Conditionals):**  根据布尔表达式（真/假）的结果来决定执行不同的代码分支 (if, else if, else)。
    *   **循环 (Loops):**  重复执行一段代码，直到满足特定条件 (forever, repeat)。
    *   **变量 (Variables):**  存储数据的容器，可以在程序中多次使用。
    *   **事件 (Events):**  程序中发生的动作或事件，例如鼠标点击、键盘按键等，可以触发特定的代码执行。
    *   **抽象 (Abstraction):**  隐藏复杂性，将复杂的细节封装在简单的接口后面，例如自定义函数。
*   **Scratch 编程:**
    *   **图形化编程界面:**  通过拖放拼图块来编写代码，避免了复杂的语法。
    *   **精灵 (Sprites):**  程序中的角色或对象。
    *   **脚本 (Scripts):**  控制精灵行为的代码块序列。
    *   **舞台 (Stage):**  程序运行的可视化区域。
*   **项目开发:**
    *   **迭代开发:**  从小处着手，逐步添加功能，不断测试和改进。
    *   **代码复用:**  通过创建自定义函数来避免重复代码，提高效率和可维护性。

**总结:**

CS50 课程旨在介绍计算机科学的基本原理和编程的艺术，强调问题解决能力和计算思维的培养。通过 Scratch 这种图形化编程语言，即使没有编程经验的学生也能快速入门，并逐步过渡到更高级的编程语言。课程通过实际项目案例，帮助学生理解编程概念的应用，并鼓励学生进行创造性探索。

---
## 视频脚本-中文

**00:00:00 - 开场**

[音乐播放中]
这里是 CS50

**00:01:15 - 这里是 CS50**

DAVID MALAN: 好的。这里是 CS50，哈佛大学计算机科学与编程艺术导论课程。我叫 David Malan，几年前我自己也上过这门课，但我差点就没上。那是我大学的第一年，我和我的室友们住在马修斯大厅，对这里熟悉的人可能知道。

[欢呼声] 好的，马修斯。实际上，当时我们值得一提的是，我们的房间恰好是马特·达蒙三年前住的。就从那说起。但在我的第一年，我真的没有勇气踏入这个教室，更不用说计算机科学了。事实上，对我来说，计算机科学，特别是 CS50，是一门让人望而却步的课程。我算是比较熟悉电脑的，但我肯定算不上那些对电脑特别精通的人。

所以我在第一年的时候回避了它。相反，我实际上选了很多政府学课程。事实上，在高中时，我真的很喜欢历史。我喜欢我在高中最后一年上的宪法课。所以我想，好吧，如果这是我在高中喜欢的，如果这是我的舒适区，那这可能就是我在大学应该做的。因此，在大学的第一年，一年半的时间里，我基本上把政府学作为我的专业。但到了大二，当我搬到马瑟楼住的时候。

好吧，没有马瑟楼的。当我住在马瑟楼的时候，我记得大概是那年九月开学的第一周，我和几个朋友一起去上了一门叫做 CS50 的课。老实说，当我踏进那个教室的那一刻，当时的教授是一位著名的计算机科学家，名叫 Brian Kernighan，现在在普林斯顿大学。我当时就被迷住了。实际上，之后每周五晚上，当发布习题集的时候，我都会在晚上 7:00、8:00 坐下来开始做作业。

这并不是我们特别推荐的做法。但对我来说，这就像一个信号，哇，我好像找到了我的使命。我在校园里找到了我的同学。当然，并不是每个人都会这样。我们当然不期望你在上了一门计算机科学课后就一定会或可能会想上其他的计算机科学课。但是计算机科学，特别是 CS50，最强大的地方在于它与更广阔的世界息息相关，无论你是在艺术、人文、社会科学、自然科学还是其他领域，这些概念和实用的编程技能都非常适用，你将带着这些技能从这门课毕业。

这一路上会充满挑战，的确，我当年也付出了很多时间，即使我当时也觉得很有挑战性。这里有一张照片，是麻省理工学院一个非常有名的“恶作剧”，可以说，就在这条路上，它传达了这样一个信息：从麻省理工学院获得教育就像试图从消防水管中喝水。也就是说，会有很多信息，很多新的东西，你肯定不可能在一周中的任何一天第一次就全部吸收。

但最终，正是通过这种挑战，投入时间，在课程结束时，回报才会更高。而且，你将带着对计算机科学和编程的更好理解走出这门课，更重要的是，你将学会如何自学新技术和其他知识。在接下来的三个多月里，我们将有助教、课程助理和我本人在你身边，指导你学习课程材料。但本学期结束时的目标是摘掉这些辅助轮，让你具备自学课堂之外新思想的能力。

不过，请放心，大多数 CS50 学生以前从未上过 CS 课程，事实上，根据教学大纲，这门课最终重要的不是你相对于同学的最终水平，而是你相对于开始时的自己的最终水平。而你的开始就是今天。所以，考虑一下你对计算的熟悉程度或不熟悉程度，更不用说计算机科学和编程了，特别是如果你以前从未在课堂上探索过这两者，并考虑一下几个月后你的变化，这将真正描述你走了多远。

这才是最重要的，而不是你现在左右、前后方的同学知道多少。话虽如此，请允许我再补充一些灵感。这是我 1996 年 CS50 第一次作业的照片，我想提请大家注意的是，尽管这是一个我们下周将要学习的所谓的“hello world”程序，它几乎是你用 C 语言编写的最短、最简单的程序。但我的第一次作业还是被扣了两分，也就是说，我们都会在前进的道路上犯错。但目标将是学习并享受这个过程。

最后，像我一样，你也将自豪地拿着你的 CS50 T恤毕业，这也是我们的传统。说到这里，CS50 还有很多其他的传统，无论是在校内还是校外。特别是，我们在 CS50 中不仅努力提供你可能需要的学术支持结构，而且还提供集体共享的社区体验。也就是说，在几天后，我们将正式开始 CS50 益智日，这不仅是一个与朋友们聚会、享用披萨、赢取奖品和解决各种逻辑谜题的机会，更是为了传达一个信息，即计算机科学本身不是关于编程，不是关于 C，不是关于 Python，不是关于编程语言本身，而是关于问题解决，更重要的是与你在这门课或其他地方身边的其他聪明人合作解决问题。

事实上，在学期快结束的时候，我们会通过 CS50 黑客马拉松来巩固这一点，这将是一个通宵的机会，让你深入研究你自己的最终项目，这是本课程的顶点，之后是 CS50 展览会，这将是一个面向全校学生、教职员工的展览，展示你自己的最终项目，无论你决定在本学期结束前创建的是你自己的网络应用程序、移动应用程序还是其他任何东西。事实上，最终的目标，特别是最终项目，是为你自己、为你的同学、为参观者创造一些我们甚至没有教你如何做的东西。这实际上将表明你已经走在正确的道路上并且准备好了。为此，我们想通过这个简短的视频让你了解 CS50 的过去，如果可以调暗灯光的话，它描绘了这里和未来的所有等待。

[视频回放] [音乐播放中]

[结束回放] DAVID MALAN: 好的，欢迎加入 CS50 和计算机科学本身。

**00:08:35 - 计算机科学**

那么什么是计算机科学呢？简单地说，它是对信息的研究。比如，你如何表示它，以及如何处理它。但更重要的是，我们将在这门课中教你计算思维。也就是说，将计算机科学的思想应用于我们在课堂上感兴趣的问题和你在课后感兴趣的问题。

所以归根结底，计算机科学实际上是关于问题解决的，因此具有广泛的适用性。说到问题解决，我们的意思很简单。事实上，我们可以用这个思维导图来概括它。这就是问题解决。你有一些问题要解决，也就是你想解决的输入。当然，问题解决的目标是实际产生一个解决方案。所以在这个模型中，输出就是解决方案。

有趣的部分最终将在于你如何处理输入并将其转化为输出，从而解决问题。但在我们这样做之前，我们都必须就如何表示这些输入和输出达成一致，特别是如果我们想以标准化的全球方式使用计算机，无论是笔记本电脑、台式机、手机还是现在大多数其他类型的电子设备。那么我们该怎么做呢？嗯，世界上有不同的方式来表示信息。

**00:09:44 - 一进制**

例如，如果我要用老式的方法点名，也许在一个较小的房间里，我可能会用 1、2、3、4、5、6、7 等等，只用我的手指来数人数。这实际上被称为一进制记数法，在数学上也被称为以一为基数，因为在这个模型中，你实际上是用手指作为数字。

但有一个小问题。你用一只手能数到多高？如果你使用的进制不是一进制，那么五是不正确的。

所以如果你只使用一进制并只数 1、2、3、4、5，那显然是正确的。但我敢说我可以用我的手想出更多的模式，这使我能够不用第二只手或一双脚就能数到比 5 更高的数字。

事实上，也许对于那些更熟悉的人来说，你实际上可以用一只手数到多高呢？所以 31，信不信由你，实际上是正确的答案。但为什么呢？嗯，在这里，我最初很简单地开始了。1、2、3、4、5。我只是把所有的手指加起来，数了总数。

但如果我更聪明一点，并考虑到手指竖起的模式呢？所以也许这仍然是零。这是一。但现在也许我们普遍同意这是二。即使这只是我的食指。也许我们都同意这是三，竖起了两个手指。

也许我们同意这是经常冒犯性的，只竖起一个中指，但这将是四。这可能是五。这可能是六。这可能是七。如果我继续以这种方式排列我的手指——请允许我剧透一下——这实际上将是 31。但再说一遍，为什么呢？但这里的区别在于，我们不再使用一进制或

**00:11:28 - 二进制**

数学家所说的以一为基数，而是以二为基数。因为如果我们不仅考虑到我使用的手指总数，而且考虑到每个手指是放下还是竖起，因此处于两种可能的状态。放下，竖起，A，B，黑，白，无论你想如何区分这两种状态，你现在操作的就是所谓的以二为基数，也许更熟悉的是，即使你本身不是计算机专业人士，这就是所谓的二进制系统。

而且很可能，即使你根本不是计算机科学专业的人，你可能也普遍知道计算机只能理解或说出什么字母表呢？所以是一和零，零和一，也就是所谓的二进制系统。实际上，这里有一个值得注意的术语。当你使用零和一，当然，总共是两个数字，你有所谓的二进制数字——bi 暗示二，这意味着有两种可能性，零或一。

如果我们去掉其中一些字母，然后把这两个短语连在一起，这里就有一个技术术语，那就是比特。一个比特就是一个二进制数字，也就是说它是一个零或一。当然，这与你和我所知的十进制系统形成对比。Dec 暗示 10，因为在现实世界中，你和我每天都使用零到九，这是 10 种可能性。

计算机只使用零和一，也就是说，使用两个比特来表示信息。那么我们如何表示这些信息呢，特别是当我们最终使用的确实是计算机和电子设备时？嗯，如果我想表示零，我实际上可以把它想象成类似于物理世界。

也许我有一个灯泡，它通过一个开关来控制它的熄灭或点亮。所以你可以把一个二进制数字零想象成一个熄灭的灯泡。相比之下，如果你把数字世界中的一想象成是两种可能性中的第二种，你可以在人类或模拟世界，物理世界中，把它想象成一个点亮的灯泡。事实上，你的 Mac、PC、安卓手机、iPhone 的内部都有数百万个被称为晶体管的微小光开关，它们可以被打开或关闭，打开或关闭。

从本质上讲，你可以使用这些晶体管来存储信息，因为如果你想存储零，你就把其中一个开关关掉。如果你想存储一，你就把其中一个开关打开。当然，这就引出了一个问题，我们如何计数到比零或一更高的数字呢？嗯，我们似乎需要使用更多的东西，而不仅仅是也许一个比特，一个灯泡。所以如果我们想计数到比零或一更高的数字，例如，我们为什么不这样做呢？所以为了我有一些地方可以放这些东西，让我从舞台上借一些我们实际的物理灯泡。现在让我在舞台上用三个比特，三个光开关，三个晶体管，无论你最熟悉哪个比喻，这就是计算机表示零的方式，因为它们都熄灭了。

所以它是关，关，关。但如果计算机想计数到一，我们可以天真地这样做。我们可以把它打开。如果计算机想表示二，我们可以这样做。如果计算机想表示三，我们可以这样做。但我有点把自己逼到了墙角，没有尽可能巧妙地使用这些灯泡，因为目前我只数到了三。所以如果我想数到四，到五，到六，我将需要越来越多的灯泡。

我们能不能更聪明一点呢？嗯，再说一遍，其他更熟悉的人，这里的剧透是什么？使用二进制的零和一，我总共可以用三个灯泡数到多高？

在后面？是的。所以这里的答案是七。如果你也在想，人们是如何算出 31 和 7 的？这就是我们这里的目标。所以让我这样做。让我把所有这些都再次关掉，这样我的三个灯泡或开关就又表示零了。第一个很简单。这就是计算机表示数字一的方式。

它将是开，关，关。但是，计算机将如何表示二呢？嗯，就像我提出的手指例子一样。让我们这样做。让我们把这个关掉，把这个打开。这就是计算机表示二的方式。通过说关，开，关。

换句话说，010 将是在数字上发音的方式。如果我想表示三呢？这就是我在手指上用两个手指做到的。嗯，我要把这个打开。这是三。现在，对于那些不太熟悉的人来说，这将是不明显的。现在这就是我表示数字四的方式。

这就是我表示五的方式。这就是我表示六的方式。根据剧透，这就是我表示七的方式。所以也许刚刚我做了什么或者为什么我选择了这些模式，这可能非常不明显。但我敢说，如果你在脑海中倒带，或者稍后在视频中倒带，你会发现我实际上向你展示了八种不同的灯泡模式。

第一个是关，关，关。最后一个是开，开，开。然后它们之间总共有另外六个。等等，为什么是七？嗯，如果你从零开始计数，并且我声称有八种可能性，你只能从零数到七，我们很快就会看到。那么这些模式是如何产生的，我们的计算机实际上在做什么呢？嗯，它实际上在做一些类似这样的事情，就像在十进制中一样。

所以在人类世界中，你和我非常习惯于使用以 10 为基数，从零到九，也就是十进制。那么，作为人类，我们是如何本能地使用它的呢？嗯，屏幕上这个明显的数字是什么？123。但为什么是 123 呢？多年来，你并没有真正思考过为什么屏幕上的这个符号或数字模式，一，二，三，在数学上表示这个你显然知道是 123 的数字。

但如果你倒带到小学，很可能，像我一样，你被教导最右边的数字是个位，第二个数字是十位，这个数字是百位，等等。所以即使我们没有人必须明确地做这个数学运算，你所做的就是 100 乘以 1 加上 10 乘以 2 加上 1 乘以 3，这给你 100 加 20 加 3。哦，这就是为什么它是 123，因为这些数字按这个顺序具有这种意义。左边的数字比右边的数字具有更大的权重。

那么我们能从中得到什么呢？嗯，让我们首先把它概括为任意的三位数。所以数字，数字，数字。个位，十位，百位。但其中有一些数学运算，而且它并不是特别复杂。这些实际上是 10 的幂。所以 10 的 0 次方，10 的 1 次方，10 的 2 次方，这就是你的十进制系统。

因为这个值中的基数是 10，这是因为每个占位符都有 10 种可能性，从零到九。但在二进制世界中，在计算机的世界中，它们只有零和一，为什么呢？因为它们在物理上只有晶体管。非常非常小的灯泡，可以关闭或打开。如果你只有两个数字可以使用，那么 10 进制当然应该变成 2 进制。

现在如果我们在这里做一些数学运算，2 的 0 次方，2 的 1 次方，2 的 2 次方，你就得到了个位，二位，四位。如果我们继续 8，16，32，64，128 等等，它是 2 的幂而不是 10 的幂。但这意味着计算机以与你和我从小到大完全相同的方式表示信息，但它们可用的数字更少，所以这些列需要以不同的方式加权。

所以我们仍然可以从零一直数到无穷大。那么这意味着什么呢？嗯，这里我们在屏幕上有三个比特，000。如果我们现在要在心理上或在纸上把它转换成十进制，我们该怎么做呢？嗯，4 乘以 0 加上 2 乘以 0 加上 1 乘以 0。这给了我们你和我所知的数学数字零。

那是三个灯泡。关，关，关。好吧，如果我们在最右边打开一个灯泡呢？这个二进制数 001 表示什么十进制数呢？只是一，因为它是 4 乘以 0，2 乘以 0，1 乘以 1。这就是事情变得更有趣的地方，即使在灯泡形式或甚至物理手形式中不明显。二进制中的 010 在十进制中是什么？

二，因为它是 2 乘以 1，就是这样。二进制中的 011 当然现在是三。这现在是四。这现在是五。这现在是六和七。开，开，开或 111 是我们可以用这三个比特数的最高值。好的。那么计算机如何直观地计数到八呢？你可能需要做什么呢？

你需要添加一个比特。所以你需要另一个灯泡，另一个开关。你需要更多的内存，可以说，使用你可能熟悉的术语。所以事实上，如果我们把所有这些都改成零，但我们给自己增加一个比特，总共四个，那一定是第八位，因为这里只是 2 的又一个幂。所以 1000 是十进制数八。

在二进制中你不说 1,000。你实际上说 1000。但这就是你和我所知的数字八。你可以不断地向上，向上，向上。那么计算机如何使用 Excel 或任何类型的数字处理软件计数到非常高的数字并跟踪非常大的数字呢？计算机只是向它投入越来越多的晶体管，越来越多的比特来计数到越来越高。然而，事实证明，一个比特，三个比特，甚至四个比特在实践中并不是那么有用，因为你只能数到七，或者可能是 15 或 31。

所以更常见的是，众所周知，使用一个字节的比特。对于那些熟悉的人来说，一个字节中有多少个比特？所以它只是八个。为什么是八个？它只是比一个或两个或三个或其他数字更有用。顺便说一句，它恰好是 2 的幂，这在电子学上也很有用。所以一个字节就是 8 个比特。

这里是我刚才脱口而出的那些列。这是计算机在十进制中表示零的方式，但使用八个二进制数字或比特。小知识。再说一遍，这不是计算机科学的重点，但它有助于了解这些值的下限和上限。如果这是零，那么用 8 个比特或 1 个字节你能数到多高？

是的。所以它实际上是 255。所以如果我把所有这些零都改成一，然后做一些快速的心算或计算器数学运算，128 加上 64 加上 32，16，8，4，2 和 1 实际上会给我总共 255。再加上 0，这给了我总共 256 种可能性。所以这只是为了说明——这也不是我们会经常做的数学运算，但你会经常在计算机世界和编程世界中看到 2 的幂，像 255，256 这样的数字。为什么呢？因为这些是系统倾向于使用的常见度量单位。

所以让我在这里暂停一下，看看在二进制、零和一、晶体管等方面，有什么问题或困惑我们可以澄清的吗？哦，非常好的问题。为什么比特只是开或关，而不是通过调整电压来实现 0%、50%、100% 呢？所以你对电压的推断实际上是正确的。这通常是计算机所做的。

也许它们使用接近 0 伏的电压来表示 0，也许使用接近 5 伏的电压来表示 1。事实证明，在计算机中做极端的事情真的很容易。如果你开始分割电压范围，对于那些还记得任何电力知识的人来说，要精确就变得越来越难。如果你把事情弄得有点模糊，你可能会把零误认为是一或二或三。所以事实证明，使用二进制系统更简单。

但确实存在被称为三进制计算机的计算机，它们实际上使用三个值，零、一和二，当然，这介于二进制和十进制之间。但你可以做不同的事情。它只是简单的开和关。举个例子，我不想真的戏剧性地关掉我的电脑，但如果我拔掉电源插头，那可能是关，实际上就是零。把它插回去，那就是一。

这其中有一种简洁和简单。还有什么问题或困惑我们可以澄清的吗？没有？好的。所以如果你暂时同意，好的，只使用零和一，

**00:23:58 - ASCII**

我们可以表示从零开始的任何数字，让我建议我们用我们的电脑、口袋里的设备、台式机和笔记本电脑做一些更有用的事情，比如表示字母，为了谷歌文档、微软 Word 或我们可能想写的任何类型的文本。所以现在知道计算机只包含或只使用零和一，因此只包含像晶体管这样的硬件，你如何在计算机内部表示像英语中的大写字母 A 这样的东西呢？当然，它不再是一个数字了。

我们能做什么呢？是的？观众：我们可以使用字母表，然后使用数字。DAVID MALAN：好的，是的。所以我们可以取英语中的字母 A 到 Z，我们可以给每个字母分配一个数字。老实说，这不仅是正确的答案，而且实际上是唯一的答案。

因为归根结底，如果你只有零和一可用，这就是解决这个问题的全部潜在方案。所以事实证明，是的，大写字母 A，几年前，一群人决定用这种零和一的模式来表示。01000001。

现在，经过训练，你可以做一些快速的二进制数学运算，哪个十进制数显然是用来表示大写字母 A 的？所以是 65，因为那是 64 加 1 再加 1 乘以 1 等于 65。B 是什么？事实证明是 66。C 是什么？67。所以他们从那以后就保持简单了。

如果 A 是零或者 A 是一，那可能会很好。但不，我们只能用 65 代替。但之后的一切都是非常可预测的。事实上，对于小写字母，还有一整套其他的数字，比如小写字母 A 恰好是 97，小写字母 B 恰好是 98，等等。但再说一遍，这就像是 CS 的冷知识。但这里重要的是，从 65 到 66 到 67 等等，它们确实是连续的。这是我们将能够利用的东西，不仅仅是字母 A。

这是什么系统？这是你自己提出的什么映射？它是 ASCII，美国信息交换标准代码。事实上，几年前是一群美国人提出了这个系统。不幸的是，当时，他们只分配了 7 个比特，最终总共 8 个比特来表示字母，包括大写和小写，键盘上的数字，以及标点符号。

所以根据我们刚才的对话，如果这个房间里的美国人，可以说，总共只使用了 8 个比特，那么在这个故事中，我们能用计算机表示多少个不同的字符呢？所以只有 255 个，如果我们再次从零开始计数，技术上是 256 个。这还不足以表示所有的人类语言，但至少足以表示英语，以及其他一些语言。

所以这里，例如，是一个 ASCII 映射表。果然，如果我们放大这一列，65 是大写字母 A，66 是大写字母 B，点点点，72 是 H，73 是 I，等等。所以至少所有这些英文字母都有一个标准化的映射。好吧，假设你收到一封电子邮件或一条短信，或者像一个包含这种零和一模式的谷歌文档。所以 01001000 等等等等。

所以 3 个字节。三组 8 个比特。也就是说 3 个字节，每个字节在 ASCII 中表示一个字母。你收到了什么信息？好吧，这次我来做数学运算，这样我们就不用做了。假设你真正收到的是十进制的 72、73、33。

你刚刚收到了什么信息？如果你还记得前面的图表的话。事实上，答案是“嗨”。为什么呢？因为 H 是 72，I 是 73。等等，33。

所以这是 H。这是 I。33，如果我们突出显示它，恰好是一个感叹号。所以这就是底层发生的事情，可以说，当你今天收到一条短信，上面真的用大写字母和一个感叹号写着“嗨！”时，你的手机至少收到了三个字节，每个字节表示字母表中的一个字母。你的电脑正在快速地进行心算，以找出这些数字到底是什么，然后在某种意义上，在它的记忆中查找所谓的 ASCII 表，你应该在屏幕上实际看到哪个字母。

所以如果你要显示这条信息，你确实会看到它是英文的，而不是那些数字等价物。那么我们还能怎么利用这个呢？嗯，这又是那个图表。也许只是为了改变一下，也许让我这里轻松一点，我们为什么不试着拼写其他的东西呢？这次是一个不同的三个字母的单词，但也许需要八个志愿者。

我们能得到一个字节的志愿者吗？作为交换，我可以给你们一些压力球作为奖励。你只需要愿意走上舞台并出现在互联网上。所以，是的。一，二。三，四怎么样？五，六，七怎么样？

八怎么样？上来吧。为我们的志愿者鼓掌。是的。[掌声] 好的。所以我要让你们每个人做的就是按特定的顺序表示一个比特。所以如果你们想，按任何顺序，在这里排成一排，面向观众。过来吧。好的。

我们将让你们代表——好吧，我们得看看谁最终在哪里。往这边挪一点。这边，这边。好的。所以你将是个位，拿着它。二位。

三。四位。八位。16、32、64 和 128。如果可以的话，请你们稍微压缩一下。所以这些人中的每一个都代表一个特定位置的比特。

让我们这样说。如果你只是不舒服地站在那里，没有任何举手，我们假设你代表一个零，很简单。但是，如果你的手举起来了，观众应该假设你代表一个一。因此，我们将拼出一个三个字母的单词，在每一轮中，你要么保持原样，要么举手。但首先，让我们先认识一下我们这里的一些志愿者，从一号位置开始，如果你想说出你的名字，也许你来自哪里和/或学习什么。

观众：嗨。我叫布鲁克。我来自印第安纳州，我正在学习生物学和计算机科学。DAVID MALAN：好的。欢迎。观众：嗨，我是贝卡。我来自马里兰州，华盛顿特区附近，我正在学习电气工程。

DAVID MALAN：欢迎。观众：嗨，我是艾迪生。我来自马里兰州。我正在学习工程学。观众：嗨。我是莎伦。我来自卢旺达，我正在学习 CS 和数学。DAVID MALAN：欢迎。观众：嗨，我是格蕾丝。

我来自阿拉巴马州，我正在学习电气工程。DAVID MALAN：欢迎。观众：嗨，我是安吉丽娜。我来自马里兰州。而且，我住在马修斯。DAVID MALAN：好的。马修斯。好的。[掌声]

观众：我正在学习应用数学和经济学，以及环境科学和公共政策。DAVID MALAN：欢迎。观众：我是欧文·贝尔斯，我来自弗吉尼亚州的农村，我正在学习 CS。DAVID MALAN：好的，欢迎。还有？

观众：我叫马克斯。我来自伦敦。我也住在马修斯，我正在学习计算机科学和神经科学。谢谢。DAVID MALAN：也欢迎你。如果你也想知道为什么我在开始时戴着这些眼镜——现在在互联网上非常常见的是这些 POV 视频。所以事实证明，这些雷朋眼镜实际上可以录制视频片段，我们有几个，我们想把它们提供给几个志愿者。如果有人想为这里的每个人记录他们的观点。弗拉德会在这里帮助确保它们正在录制。

第二个志愿者。是的，二号。好的。所以当弗拉德把那些设置好后，在你们的纸的背面，你们有接下来三轮的说明。每一轮代表一个字母。这其中的观众参与部分是实际进行心算，以找出这些志愿者代表的数字。

所以继续执行第一轮，要么保持你的手放下，要么适当地举起它。好的。我们的志愿者在这里代表什么数字？观众：66。DAVID MALAN：66，因为我们有一个 64 加一个 2。那它映射到哪个 ASCII 字母呢？

观众：B。DAVID MALAN：B 是第一个字母。好的，放下手。第二轮，开始。难一点了。现在代表什么？观众：79。

DAVID MALAN：我开始听到了。79 实际上是正确的。79，因为我们有一个 64 和一个 8 和 4 和 2 和一个 1。所以如果是 79，我们就有了 ASCII 字母 O。所以我们得到了 BO，最后，第三轮。

开始。我们有 01010111。这是什么数字？观众：87。DAVID MALAN：87。它拼出了哪个字母？观众：W。

DAVID MALAN：W。它拼出了哪个单词？观众：Bow。DAVID MALAN：不是“bow”。如果可以的话，鞠个躬。好的。为我们的志愿者鼓掌。[掌声] 从这边下来，拿一个 CS50 压力球。

谢谢我们的志愿者。所以这只是为了说明我们现在已经同意了如何表示从零开始的数字。我们已经同意了如何表示字母。但至少是用 ASCII 表示字母，事实上，这些不仅仅是装饰。实际上，这是课程结束时的一个小知识。如果你上来领取你自己的 CS50 压力球，事实证明这里有 64 个灯泡在舞台的底部。如果你把它们分成 8 个字节或单个——

**00:33:42 - Unicode**

8 个比特或单个字节块，有一个由 8 个字母组成的单词，今天恰好是用这个 ASCII 图表拼出来的。所以今天的谜题是，这个单词到底是什么。但是，当然，如果你只有 8 个比特，你只能表示 256 个字符，这听起来对英语来说已经足够了，而且确实如此。零到九，A 到 B，大写和小写，大写和小写，以及标点符号。但是世界上还有很多其他的人类语言，它们有其他的字符。

例如，我们不仅有我们在美国英语键盘上看到的英文字母表。我们还有重音字符，我们还有各种亚洲语言，它们有更多的字形。我们需要超过 256 个可能的字符。所以现在计算机不仅仅使用 7 个甚至 8 个比特。它们可能对某些字母使用 8 个比特，比如所有的英文字母。它们可能对某些其他语言使用 16 个比特。

甚至可能是 24 或 32 个比特。有趣的是，如果你有 32 个比特——我们在舞台上有更多的比特。如果你有 32 个比特，你实际上可以表示多达 40 亿个可能的字符，这是相当多的。没有双关的意思。那么我们还能表示什么呢？嗯，这个系统的目标，不仅仅是 ASCII，还有一种叫做 Unicode 的更新的标准，是为了向后兼容 ASCII。所以人们保留了所有其他的数字，65、66、67 等等，但他们添加了一个表示的超集，可能是 16、24 或 32 个比特。

目标是能够以数字方式表示所有过去、现在和未来的人类语言，甚至通过象形图，比如笑脸之类的东西，甚至是超越人类语言的人、地点、事物和情感。事实上，很可能在过去的几分钟或几小时内，你们中的大多数人都使用过这些表情符号中的一个或多个，这些象形图，事实证明它们只是键盘上的字符。

你可能需要按一个特殊的按钮来调出那种形式的键盘，但这些只是这里的字符。所以这些表情符号之所以大受欢迎，有很多原因，其中之一就是，天哪，我们要用 40 亿个可能的零和一的模式做什么呢？我们可以开始玩得开心，并表示英语和人类语言之外的东西。现在，顺便说一句，当涉及到 Unicode 时，事实证明 Unicode 几年前标准化了这个 32 个零和一的模式来表示其中一个表情符号。所以表情符号倾向于使用更多的比特。

有人知道这是什么十进制数吗？这不是一个有趣的数学练习。剧透是 4,036,991,106 是实际上表示目前世界上最受欢迎的表情符号的十进制数。有人想猜猜这个数字代表什么表情符号吗？

观众：心。DAVID MALAN：心？心？不，但它实际上是这个所谓的“喜极而泣的脸”。所以也许想想你发送这个表情符号的频率。即使它显然是屏幕上的一张图片，当然，它实际上更像是一种字体，因为在底层，它实际上只是计算机存储的零和一的模式或十进制数。但是计算机，无论是 Mac OS 还是 Windows 还是 iOS 还是 Android，都知道将该模式显示为这里的这张图片。但是图片可能会因硬件而异。

为什么呢？因为像谷歌、微软、Meta 和其他公司都有自己的艺术家作为员工，这些艺术家对“喜极而泣的脸”等描述的解释不同。所以你们中那些使用安卓手机的人实际上看到的“喜极而泣的脸”看起来有点像这样。例如，如果你在手机上安装了 Telegram，它甚至比那更有动画效果。这是使用相同零和一模式的表情符号。所以不同的艺术家以不同的方式呈现这些表情符号，但它们都只是模式。现在，对于所有其他的答案，除了刚才喊出的一个答案之外，这是根据 Unicode 的几年前最受欢迎的表情符号的云图，其中表情符号的大小表示它的相对受欢迎程度。所以心，我确实在这里听到了，它确实也是最受欢迎的表情符号之一。

问题？观众：为什么某些表情符号会显示 [听不清]？DAVID MALAN：哦，非常好的问题。为什么某些表情符号不能在一个设备或另一个设备上显示呢？这取决于软件的更新程度。

几乎每年，Unicode 联盟背后的人类都会发布新的表情符号。也就是说，他们决定这个其他的模式将代表这个新的表情符号，这个其他的模式将代表这个新的表情符号。除非你把你的手机、笔记本电脑更新到最新的软件，并且该设备或软件的制造商也通过聘请艺术家以他们自己的字体、他们自己的风格绘制这些图片来进行更新，否则你通常只会看到一个空的黑色方块，或者可能只是一个黑白的心形，而不是更丰富多彩的东西。实际上只是占位符，因为，这就像你没有安装正确的字体，或者实际上，你安装了该字体的旧版本。但它已经成为一种年度传统，每年都会发布新的和更多的表情符号，

**00:38:45 - 颜色**

这是这些更新包含越来越多的内容的原因之一。是的？

观众：你如何在字节中表示颜色？

DAVID MALAN：这是一个很好的引子。你如何在字节中表示颜色呢？嗯，你使用 RGB，这恰好是，巧合的是，下一张幻灯片。

所以让我们再次回顾一下。我们知道如何表示字母。我们知道如何表示数字。我们甚至可以表示表情符号。但从技术上讲，这些表情符号在屏幕上当然是由颜色组成的，比如那个笑脸上的大量黄色？那么，计算机如何只使用零和一来表示颜色呢？嗯，按照惯例，它们通常使用一个缩写为 RGB 的系统。红色、绿色、蓝色。这就是说，计算机，为了在屏幕上表示一个点——

也许是这个，这个，这个——将分配一些比特数或一些字节数来表示那个点的颜色，也就是所谓的像素。你实际上可以在你的手机甚至你的电视或显示器上看到像素。如果你靠得很近，特别是如果它是一个较旧的显示器，你可以看到微小的正方形。每个正方形都有一些比特告诉设备使用什么颜色。特别是，这些设备通常总共使用三个数字，三个字节。

也就是说每个像素 24 个比特。他们这样做。如果你要使用这三个数字在屏幕上表示一个点，这里只是为了说明，这是 72、73、33，在短信、电子邮件、谷歌文档的上下文中，当然，它在文本上表示“嗨”。如果计算机使用相同的零和一模式，即相同的十进制数字模式来表示屏幕上的颜色呢？如果你正在使用 Photoshop 打开图像，这是相关的。因此，使用了解颜色、图像而不仅仅是文本的不同软件。好吧，这意味着您希望屏幕上的那个点具有中等量的红色、中等量的绿色和少量蓝色。为什么我说中等和小量？

好吧，再说一遍，如果这些数字中的每一个都使用 8 位或 1 个字节，正如我们发现的那样，我们可以计算的最高值是 255。所以我在做平均。所以 255 中的 72 对我来说感觉像是中等量的红色。33 感觉是相对较少的蓝色。但是，如果现在计算机将这些波长的光组合起来，即中等量的红色、中等量的绿色、少量蓝色，您将获得单个点的颜色代码。

有没有人想猜猜这三种颜色大致代表什么颜色？

观众：白色。观众：紫色。

DAVID MALAN：不是白色，不是紫色。

观众：棕色。

DAVID MALAN：不是棕色。

观众：黄色。

DAVID MALAN：实际上，答案是黄色。

因此，它在一个像素中大致表示这种黄色阴影。也就是说，如果我们回顾一下任何这些表情符号，它们同样由零和一的模式表示，但是您和我作为人类将它们视为屏幕上的图像——让我实际上继续放大并进一步放大到一个这样的样本表情符号。当您放大到足够大或将手机靠近您的脸时，您实际上可以看到所有这些被称为像素的小点，所有的小方块。鉴于这么多像素是黄色的，也就是说三个字节的模式 72、73、33 用于表示此像素。

另外 3 个相同的字节用于表示此像素、此像素、此像素等等。所以现在，如果您在手机或相机上拍摄了数码照片，您可能通常从今天的互联网和硬件中了解到一张照片是 1 兆字节、10 兆字节，具体取决于它的分辨率？

好吧，兆字节意味着数百万字节。这些照片或您正在拍摄或下载的这些图像中，所有这些字节都在哪里？它们对应于屏幕上的每一个像素。

**00:42:27 - 表示**

至少有三个字节用于表示每个点。顺便说一句，这是一个善意的谎言，因为现在有花哨的压缩软件可以使用少于那么多字节。但总的来说，这就是所有这些字节，数百万字节的来源。那么对于我们如何表示颜色这个问题，这个答案如何呢？谢谢。因此，如果我们现在同意有这种方式，也许还有其他方式来表示颜色，那么，我们如何表示的不仅仅是图像，还有视频呢？

嗯，视频曾经，或者说电影，被称为电影图片。带运动的电影图片。这是为什么呢？好吧，这类似于成长。如果您曾经玩过这些图画书中的一本——事实上，现在有模因使这些再次流行起来，为什么您在单独的纸张上有一堆图像。

如果您足够快地翻阅它们，您的人类思维和眼睛会将其视为实际的运动，即使您只是看到图像、图像、图像、图像、图像、图像。但它太快了，所以看起来像运动。这就是您屏幕上的视频的全部内容。这就是您电视上电影的全部内容。它实际上并不是连续运动。

它可能是每秒 30 帧或图像，可能是每秒 24 帧或图像。也就是说，我们知道如何表示数字，我们知道如何表示字母，我们知道如何表示颜色，从而表示图像。现在我们免费获得了视频，因为它们只是更多相同的东西。使用越来越多的那些模式。

为什么视频这么大？为什么它们要下载千兆字节，数十亿字节？因为有太多该死的图像。在这些类型的视频中，每秒有 30 多张图像。也许最后，只是为了完善我们的多媒体，您如何表示声音？也许是房间里的音乐家。如何仅使用零和一，就能表示像音乐一样悦耳的东西呢？像数字一样模拟的东西。是的？

观众：所以每个数字都对应一个频率。

DAVID MALAN：是的。因此，我们存储在计算机中的每个数字都可以对应某个频率，这与声音或音符的音高有直接关系。例如，在钢琴和许多其他乐器的世界中，您有 A、B、C，也许您还有升号和降号。我们可以像几年前的 ASCII 人一样同意，为了表示音符 A，让我们使用这种模式，音符 A 升，让我们使用这种模式等等。

但也许仅音高或仅频率是不够的。也许我们需要那个数字，但也许需要第二个数字来表示音量，这是您敲击钢琴键的数字等效值。也许第三个数字表示您按住琴键的时间。所以也许是音高、音量和持续时间，有点像 RGB，我们可以使用三个字节来表示某个片段中的每个音符。

如果我们想跟踪计算机应该演奏什么乐器来发出那种音乐，好吧，也许那只是第四个字节或其他东西。也就是说，归根结底，我们所拥有的只是这些零和一可以用来解决问题。所以现在，关于表示信息就是这些了。

我们有我们的数字，我们有我们的字母，我们有我们的颜色和图像，我们的视频，现在还有声音。关于计算机如何仅使用零和一表示那些输入和输出，还有什么问题吗？是的，在中间。观众：计算机将其作为输入。DAVID MALAN：正确。所以计算机在最后将零和一作为输入，并输出零和一。然而，正如我们将在这门课中学到的，通过编写软件，通过编写理解那些零和一的代码，我们将享受到的不仅仅是字面上的零和一，我们将看到 A、B、C，我们将看到颜色，我们将看到视频，我们将听到声音，只要我们编写代码来解释那些零和一。事实上，值得注意的是，我现在一直用于示例的相同模式，72、73、33，计算机如何知道？

那是消息“嗨”吗？那是黄色吗？它是单独视频中的一个点吗？这取决于上下文。简而言之，如果您使用 Excel 或计算器程序打开零和一的模式，那么该软件很可能会将这三个字节解释为数字，当然。

但是，如果您在短信程序、谷歌文档、微软 Word 中打开相同的模式，相同的模式将被解释为字母序列。相反，如果您打开 Photoshop，相同的模式，您可能会看到一个恰好是黄色的点。相反，一旦您自己成为一名程序员或更优秀的程序员，您将能够用代码编写您希望计算机如何处理这些零和一的模式。

您基本上可以告诉计算机，使用它来存储数字或字母或颜色或其他东西。这是程序员自己在最后拥有的能力。关于用比特表示事物的其他问题？没有？好的。所以最后，在这个黑匣子的中间，可以说，

**00:47:20 - 算法**

是解决问题的秘诀，它将这些输入转换为输出，将这些问题转换为解决方案。那么什么是算法呢？它实际上只是解决某些问题的分步说明。事实上，我想起了我在 CS50 中第一次从 Brian Kernighan 教授那里学到这一点。

幸运的是，我刚刚参加了我的 25 周年同学聚会，在那里我们提取了 1996 年的一些视频片段。所以我们实际上很幸运地拥有了 25 年前我自己参加 CS50 的前几分钟。但那时和今天的教训从根本上来说是相同的。事实上，重要的是不仅要正确地表达自己，而且要精确地表达自己，正如我们今天将要探讨的那样。这就是 Brian Kernighan 教授，他在多年前通过在课堂上刮胡子，非常难忘地向我们和我的同学们介绍了算法。

如果我们可以为 Brian 调暗灯光。[视频回放] - 我们将在这门课中讨论的另一件事是算法的概念。算法是如何做某事的非常精确的描述。这里的关键词是精确。

它必须非常、非常、非常、非常精确。我要做的任务是我要修剪我的胡子，它已经失控了。[掌声]

我带来了各种各样的东西，人们可以用它们来修剪胡子。[笑声] [掌声]

[结束回放] DAVID MALAN：可以说，我没有多少胡子。但我确实有这项被称为电话簿的其他技术。当然，这些电话簿中有很多信息。碰巧特别存储了数字和字母。

对于那些不熟悉的人来说，它们存储了从 A 到 Z 的人名（英文），并且每个人的名字都与一个数字相关联。所以即使你从来没有机会实际使用这种设备，事实证明它几乎等同于你的 iOS 手机或你的安卓手机上的通讯录或地址簿应用程序。为什么呢？因为如果你打开你的通讯录，当然，你会看到一些熟悉的名字，按名字或姓氏的字母顺序排列。

如果你点击其中任何一个名字，你就会联系到你可能想打电话或发短信的人。这里显示的是约翰·哈佛的电话号码，加 1-949-468-2750，你可以在闲暇时拨打或发短信。但这是约翰·哈佛，他在数字电话簿中途。好吧，事实证明，在物理电话簿中，我们可能会使用一种算法，即逐步说明，以查找约翰·哈佛，这与 iOS、Android、Mac OS、Windows 或其他操作系统本身使用的方式几乎相同。所以，当我在寻找约翰·哈佛时，名字以 J 开头，我可以从电话簿的开头开始，逐页地寻找约翰·哈佛。

如果他在那里，我可以打电话。这是一种算法。它确实是循序渐进的，但那是一个错误。翻了几页。但这个算法正确吗？一步一步，假设我在注意。

所以是的，如果约翰·哈佛在这里，一旦我到达 J 部分，我最终会找到他。现在，这有点乏味。这将需要一段时间。几十页，几百页。所以也许我可以做一些更聪明的事情，就像小学时那样，2、4、6、50:55
8、10、12、14、16 等等，速度快一倍。这个算法正确吗？

所以不正确，但为什么呢？观众：你可能会错过它。

DAVID MALAN：我可能会错过他，对吧？我可能会不走运，真的，有 50/50 的概率，因为约翰·哈佛可能被夹在两页之间。现在，这个算法并不是完全失败的。

也许我能做的就是，如果我过了 J 区到了 K 区，我可以至少回过头来看一页，以确保我没有错过约翰·哈佛。所以我仍然可以以两倍的速度前进，再加上一个额外的步骤，以确保我没有搞砸。所以第一个算法可能需要与电话簿中的页数一样多的步骤。所以如果这本电话簿有 1000 页，在最坏的情况下，如果我不是在找约翰·哈佛，而是在找一个名字以 Z 开头的人，可能需要我 1000 页才能到达那里。第二个算法，快一倍。实际上，它可能需要我 500 加一步才能到达那里，因为我一次翻两页，所以只要我确实修复了那个错误。但是我们过去所做的，以及你的手机现在正在做的，尽管是数字化的，是大致翻到电话簿的中间，向下看并意识到，哦，我不小心翻到了 M 区，所以是电话簿的一半。但是我现在对约翰·哈佛了解了什么呢？

他在左边还是右边？所以他显然在左边，因为 J 在 M 之前。所以我可以做的，以及你的电脑在比喻上所做的，就是把问题分成两半，把一半的问题扔掉，现在我们仍然面临着同样的基本问题，但它只有一半大。

所以我突然从 1000 页变成了 500 页。将此与其他两个进行比较，1000 页，999，998，与 1000 页，998，996，994。那仍然很慢。我只用这个算法的一步就从 1000 页变成了 500 页。我下一步该怎么做？我大致翻到这里的中间。哦，我翻得有点太远了。我现在在 E 区。

那么约翰·哈佛现在在左边还是右边呢？所以他在右边。所以我可以再次把问题分成两半，把左半部分扔掉，现在知道约翰·哈佛按字母顺序一定在这里。我可以一遍又一遍地划分、划分、划分和征服这个问题，通过使用向左或向右的启发式方法。我敢说，如果我做得正确，我最终会只剩下一页，约翰·哈佛的号码实际上就在那一页上。或者他根本不在电话簿里。那么第三个也是最后一个算法最多可能需要多少步呢？

不是一千。它甚至不是 500 或 501。你能把一千页分成两半多少次，一次又一次，大致是多少次？观众：我想说九次。

DAVID MALAN：所以是 9 次，10 次。

所以通常是 10 次左右。这里有一点四舍五入，因为它不是 2 的完美幂，但大约是 10 次。这从根本上来说比这两种算法都好，因为我从一千页到 500 页到 250 页到 125 页等等，实际上把问题一次又一次地减半。所以我们实际上可以更直观地欣赏和看到这一点。

这是我们将在本学期后面讨论的事情之一，当我们谈到不仅要编写正确的代码，而且还要讨论你的代码是否设计良好？它是否比你以前的代码更好？它是否比别人的代码更好？它是否比其他一些产品更好？如果你对算法及其质量进行了更多的思考，你或许可以最大限度地减少解决问题所需的时间，但同样是正确的。

所以如果我们在这里有一个简单的 xy 图，在 y 轴或垂直轴上是以任何度量单位（秒、页数，无论你想怎么计算）表示的解决时间。在水平轴或 x 轴上是以例如页数表示的问题大小。所以这将意味着电话簿中有零页。这将意味着电话簿中有很多页。这将意味着没有解决时间。这将意味着大量的解决时间。那么，这三种算法之间的关系是什么呢？

嗯，第一个基本上是一条直线，斜率为 1。如果电话簿中有 n 页，我们将这里的斜率描述为第一个算法的斜率基本上是 1 比 1，逐页逐页地翻。也就是说，如果明年我们要在电话簿中再增加一页，第一个算法将多花一步。但第二个算法肯定更好。它肯定更快，但它仍然是一条直线。

所以它平均需要大约 n 除以 2 步，因为你只需要翻阅一半的电话簿，因为你一次翻两页，而不是在最坏的情况下翻阅整本电话簿，如果某人的名字是 Z，则需要翻阅每一页。所以如果我们实际比较这些——让我画一些虚线。假设电话簿中有这么多页。如果你只是画这条垂直的白线，使用第一个算法将花费这么多时间（红色），但使用第二个算法将花费一半的时间（黄色），因为你实际上一次翻两页。

但第三个也是最后一个算法是一个完全不同的形状。相反，它看起来有点像这样。它看起来越来越平坦。它总是在增加。它永远不会完全变平。

但它作为电话簿大小的函数增长得慢得多。对于那些还记得对数的人来说，这将被描述为以 2 为底的 n 的对数。事实上，这就是数学的来源。以 2 为底的 1000 的对数总共大约是 10，即使你需要一个计算器来确认。但这种形状是根本不同的。

为什么呢？好吧，假设我们所在的剑桥和街对面的奥尔斯顿镇明年将他们的两本电话簿合并。他们从每本 1000 页变成了一本 2000 页的电话簿。第一个算法实际上将花费两倍的步骤或页数。第二个算法将花费一半或多 50%，因为你一次翻两页。但第三个算法几乎不会错过任何一个节拍。为什么呢？因为如果这里是 1000 页，那里是 2000 页，从绿线的形状推断，它在垂直轴上不会比其他两个高多少。

所以更具体地说，如果明年你有一本 2000 页的电话簿，使用第三个也是最后一个算法，你需要多走几步呢？只需一步，因为你将把一本 2000 页的电话簿分成一本 1000 页的电话簿，然后你就回到了原来的故事。这就是学习算法的力量。这就是学习计算机科学和学习如何编程的力量，能够驾驭大数据。

谷歌大小的东西，人工智能训练数据集大小的东西，使用越来越好、越来越聪明的算法，这些算法执行得更快，因此不仅使软件更具竞争力，而且使你和我这样的人在使用该软件时更易于使用和更受青睐。因此，当涉及到作为程序员实现算法时，

**00:57:34 - 伪代码**

作为计算机科学家，您真正要做的就是采用这些算法，这些算法可以用英语概念性地表达，就像我们刚才所做的那样，但实际上只是将它们转换为代码，无论是 C 还是 C++ 还是 Python 还是 R 还是 Ruby 还是世界上存在的任何其他语言。但是现在，让我们考虑如何使用仍然是字面上的英语但伪代码的东西来实现该算法。

根据 Kernighan 教授的建议，某些内容仍然是正确的，但精确且有限，也就是说，使用您自己的英语方言，并简洁地说出您的意思。编写伪代码没有一种方法。它不是某种正式的语言。我只是要将我直观地执行的步骤转换为如下所示的分步说明。

第一步，我所做的几乎就是拿起电话簿。第二步，我所做的几乎就是打开电话簿的中间部分以进行第三种算法。第三步，查看页面。第四步，如果人在页面上，那么，第五步，打电话给人。

如果事实证明并非如此，则第六步，否则如果该人在书中的较早位置，则打开到该书左半部分的中间，然后返回到第三行。然后，否则如果该人在书中的较后位置，则打开到该书右半部分的中间，然后再次转到第三行。否则，还有第四种也是最后一种情况。如果像约翰哈佛这样的人不在页面上，不在较早的位置，也不在较后的位置，我们需要考虑的第四种情况是什么？他根本不在那里。

否则我们应该做一些具体的事情，比如退出。现在，顺便说一句，这个房间里的每个人可能都遇到过这些愚蠢的技术支持问题之一，即您的手机或笔记本电脑或台式电脑突然死机，或者它可能无缘无故地自发重启。很可能是因为不是你，而是其他一些人犯了错误。他们可能在微软或苹果或谷歌或其他地方工作时编写了代码，而他们实际上并没有预料到，哦，现实世界中可能会发生第四种情况。但是如果没有代码告诉计算机在这种第四种也是最后一种情况下该做什么，谁知道计算机会做什么呢？它可能默认重启。它可能默认冻结。这只是一个暗示，即软件中将要出现的错误，即软件中的错误。

但是，尽管这只是一种编写此代码（也称为伪代码）的方法，但我们今天将使用一些突出的特征。一，有这些动词，这些动作。从今以后，作为有抱负的计算机科学家或程序员，我们将开始用越来越专业的术语来称呼这些。这些是函数。

函数是一个动作或动词。它就像计算机可以为您执行的一小部分任务。那么这些就是此处的伪代码中的函数。但是这里还有其他类型的代码。

这里有这些东西。If else if else if else。这些是我们将开始称为条件语句的示例。这些是众所周知的道路上的岔路口，也许你走这条路，也许你走那条路，但你要根据一个问题来决定走哪条路。

你提出的问题就是我们将从技术上称为以数学家布尔命名的布尔表达式。布尔表达式是一个答案为是或否、真或假、黑或白、一或零的问题。有两种可能性，并且这里暗示了底层的二进制。布尔表达式会告诉你，是或否，你应该沿着这条路走下去。请注意，这里重要的是缩进的结果很重要。

请注意，在第四行，当我第一次问这个人是否在页面上时，可以说，只有当答案是“是”或“真”时，我才应该按照其缩进执行第五行，只有当这个人实际上在书中的较早位置时，我才应该打开到该书左半部分的中间并返回到第三行。因此，伪代码和许多编程语言中的缩进具有逻辑意义。它告诉你是否要做某事。但是这里还有另一个结构。

回到。回到，这实际上让我回到第三行，可能会一次又一次地回去，从而创建某种循环或我们将通常称为循环的东西。因此，即使在这个相对简单的现实世界算法中，我们也拥有我们将要在这门课中编写的大多数计算机程序的这四个基本特征，并且您可能会在这门课之外编写，我们现在有一些技术术语来描述它们。但需要注意的是，第 8 行和第 11 行，尽管它们说回到第三行，回到第三行，你可能会认为你有冒着我们所说的无限循环的风险，你实际上永远陷入了一个循环，如果在某个时候你想关掉你的电脑，即使它仍在工作，这听起来并不像一件好事。但这些不会导致无限循环。

为什么？每次我们回到第三行时，在这个特定的算法中发生了什么，保证我们最终将停止回到第三行？

观众：这个人在页面上，你打电话给它。

DAVID MALAN：完全正确。如果这个人在页面上，我们将打电话给他们，或者我们将退出。

但更重要的是，因为我们不断地划分和征服问题，在这种情况下，将电话簿减半，将电话簿减半，最终我们将用完电话簿，在这种情况下，约翰·哈佛要么在那一页上，要么不在那一页上，我们将打电话或我们将退出。所以我们会及时看到。事实上，请允许我保证。很可能在某个时候你会编写代码，这些代码似乎可以控制你的电脑，它正在做某事，做某事，做某事，而且它实际上不再对你做出响应。这只是因为一个错误，一个所谓的错误，你自己总是会无意中添加到你的代码中。

但我们将向您展示终止它或摆脱这些情况的方法。事实上，我们将在今天课程休息后不久，探索的不仅仅是这些概念，还有一些您可以使用它们来解决真实且非常直观和音频问题的方法。但现在，让我们至少将它与近几个月来，过去几年中一直非常贴切的东西联系起来，即

**01:03:32 - 人工智能**

人工智能，这也是我们将在课程结束时回到的一个话题，让您了解每个人都在谈论的人工智能世界与我们将要通过编写代码在接下来的几周内构建的内容之间的联系。例如，如果您尝试实现一个聊天机器人，它只是回答问题并与您进行对话，您可以使用伪代码来做到这一点，正如我们很快将看到的那样，您也可以使用 C、Python 和许多其他语言。在实现聊天机器人时，该伪代码可能如下所示。您可以告诉聊天机器人，如果学生对您说“你好”，则回复“你好”。正如前面所述，缩进意味着这是有条件的。

否则，如果学生对您说“再见”，则对学生说“再见”。否则，如果学生问您“你好吗”，则说“我很好”。因此，您可以枚举一个又一个问题，并处理所有这些条件可能性。但是事情很快就会升级，尤其是使用当今的工具，例如 ChatGPT。作为程序员，我们真的有能力编写另一个条件语句，例如“否则如果学生问为什么二进制中的 111 是十进制中的 7”——这有点暗示了，天哪，这个人可以向聊天机器人提出无数个问题。我们真的必须编写无数个条件语句吗？

那是不可能的。没有足够的时间，也没有足够的代码行可用。人工智能肯定需要能够解决其中的一些问题。因此，这不是您实现人工智能的方式，而是您通常如何实现像聊天机器人这样的人工智能，您通常会根据大量数据对其进行训练。

您为其提供大量输入、大量输入、训练数据，并让它弄清楚它应该如何回答某些问题。这归结为大量的概率、大量的统计数据，现在也称为大型语言模型，如果我们真的深入了解一下，实际上通常是用受生物学世界启发的所谓神经网络来实现的，我们人类拥有所有这些神经元来传输电信号，以便我的大脑告诉我的手以这种方式、这种方式和其他方式移动。因此，计算机科学家在过去多年来一直在做的事情是使用字面上的零和一、图形或网络、神经网络在软件中实现，这些神经网络看起来有点像这样，其中每个圆圈代表一个神经元，每个箭头代表它们之间的通路，并为这些网络提供大量数据作为输入，例如整个互联网、所有维基百科、它可能作为输入的所有书籍。

然后，根据这里这个单一的最终神经元，这个神经网络的目标是产生一个问题的答案。也许很简单，比如“是”、“否”，或者可能是 111 问题或“你好吗”或“再见”或“你好”之类的答案。这些神经网络所做的就是使用统计和概率，并尝试输出对所提出的这个问题的最有可能的答案，并且真的希望它是正确的。OpenAI 或谷歌或微软的程序员并没有试图预测我们可能提出的每一个问题，不仅是用英语，而且是用其他语言。

所以你可能想知道为什么舞台上有一只 8 英尺高的鸭子。所以 CS50 自己的人工智能所扮演的角色实际上是一只橡皮鸭，因为事实证明，在编程圈子里——这在 CS50 很久以前就是如此——人们经常建议学生和有抱负的程序员在你的桌子上放一只真正的橡皮鸭。这个想法是，在没有朋友、家人、同事、可以回答你的技术问题的助教的情况下，如果你在晚上独自一人在马瑟的房间里，你可以和鸭子说话，也许关上门，向鸭子提出你的问题，或者更重要的是，向鸭子解释你遇到的困惑。

仅仅是谈论问题，从逻辑上解释你正在尝试做什么，你实际上在做什么，以及错误实际上是什么，总是会产生那种众所周知的灵光一现，你会意识到，哦，我是个白痴。我从自己的话中听到了我哪里出错了。即使这只鸭子永远不会对你说任何话，但仅此而已，橡皮鸭调试或橡皮鸭往往是一种有价值的编程技术，信不信由你。但多亏了这些大型语言模型，我们不仅拥有了实体的鸭子，还拥有了虚拟的鸭子。因此，您将在本课程中可以使用像 ChatGPT 之类的工具，这些工具根据政策是不允许的。使用 ChatGPT 之类的工具是不合理的。

但您被允许并鼓励使用 CS50 自己的人工智能工具，这些工具类似于那些工具，但了解 CS50 的一些知识，并渴望表现得像一个好的助教，引导您找到解决方案，而不是直接向您提供某些内容。因此，这是一个将在整个课程中通过此 URL 提供的工具。CS50.ai。它还将嵌入到您即将遇到的编程环境中，该环境称为 Visual Studio Code，它是基于云的版本。鸭子也将生活在该环境中，并会不时出现在舞台上，也就是说，我们将不仅讨论，而且将在整个课程中使用这种被称为人工智能的东西。

但这是我们下周将开始编写的代码。不幸的是，这里的这段代码是用一种叫做 C 的语言编写的。这本质上就是我在 25 年前丢了两分的程序。不可否认，它看起来确实很神秘。这就是为什么我们今天将重点关注的不是这段代码的样子，也不是这段代码被转换成的零和一，以便您的计算机可以理解您希望它执行的操作的输入。我们将专注于一个更直观的化身。

但我知道到目前为止，这已经很多了。所以让我们在这里休息五分钟，当我们五分钟后回来时，我们将进行一些实际的编程。所以五分钟后见。好的。所以现在是时候用实际的代码来解决一些实际的问题了，

**01:09:21 - Scratch**

虽然是以一种有趣、直观和音频的方式。但回想一下我们之前结束的地方是这里。从下周开始，您将编写最终看起来像这样的代码，但谢天谢地，您不会编写零和一，包括我自己在内，没有正常人能够一眼就理解所有这些零和一。

我们可以拿出一些纸和笔，也许可以非常乏味地弄清楚它。但这正是重点。计算机只能理解这些东西，但作为程序员，我们今天将开始编写的是更高级别的代码。事实上，这将是——这在计算机科学中将是频繁的，我们操作的抽象级别不同。

最低级别，最细微的，就像计算机理解的零和一。在这门课中，关于零和一就到此为止。希望您至少已经理解了为什么零和一可以用三元组和字节来表示越来越高的数字。但现在让我们同意计算机可以做到这一点。

让我们从这个细节中抽象出来，专注于比零和一更高级别的语言，即像这样的语言。所以这是我当年学习的第一个编程语言的一个例子，根据那个家庭作业，它是一种叫做 C 的语言。它是一种较旧的语言，但它仍然是当今最流行、无处不在的语言之一，因为它速度非常快，并且特别擅长使设备快速运行。对于我们的教学而言，C 的价值不在于您可能在硅谷和其他此类工作中会大量使用 C，而在于它将提供一个概念基础，在此基础上我们将介绍其他语言，例如 Python，可以说，它是更新和改进的，它通过抽象掉我们将在未来几天首先关注的一些内容，为您提供了更多免费的开箱即用功能。

因此，最终，您应该更好地理解像 Python、JavaScript 和 SQL 这样的语言，因为您对像 C 这样的语言有基本的了解。但这对于第一天来说太多了。你们中的许多人会认为这对于第二周来说也太多了。但实际上，C 只是看起来有点吓人，因为所有这些该死的标点符号和语法，分号、括号、双引号、大括号等等。

我同意。这在智力上是无趣的，学习编程早期面临的许多挑战是，您只是没有我或一些助教可能拥有的肌肉记忆，不知道什么符号应该放在哪里。但这会随着时间和练习而来，我保证。然而，我们今天要做的是扔掉所有那些在智力上无趣的细节，真正专注于思想。

你们中的一些人可能在这里感到很自在，因为如果您在初中时玩过一种叫做 Scratch 的编程语言，您当时可能只是为了在课堂上或课外玩得开心，制作游戏、动画、互动艺术。至少在初中时，您可能没有用它来考虑和探索编程语言本身。但是 Scratch 的美妙之处在于，它是麻省理工学院几年前发明的图形化编程语言，您可以通过拖放拼图块（也称为块）来编程，而不是使用键盘，如果这样做在逻辑上是合理的，这些块将卡在一起。您不必处理括号、双引号、分号和所有这些，至少在下周之前是这样。但是 Scratch 的好处在于，在本周之后，以及在所谓的习题集零（您将使用 Scratch 的第一个作业）之后，您将拥有一个思维模型，通过该模型，您也将更容易掌握所有后续的语法。所以让我们看看如何通过首先制作最简单的程序来开始用 Scratch 编程。您可以在 scratch.mit.edu 上执行此操作。

您现在不必这样做。习题集零将引导您完成所有这些步骤。但是我在 scratch.mit.edu 上所做的正是其中的默认网页。这是在单击 Scratch 中的“创建”按钮之后，它将允许我创建我的第一个程序。但首先，介绍一下用户界面，以及最终可用的内容。好吧，在 Scratch 环境中，我们将看到屏幕的几个不同区域。一，我们在左侧有这个拼图块的调色板。

蓝色的与运动有关，紫色的与外观有关，粉红色的与声音有关，等等。因此，块的颜色只是粗略地分类了该块的用途。我们将能够通过从左到右拖放来使用那些拼图块。在屏幕中间的右侧这里，是我将要编写实际程序的地方。

这是我将拖放这些拼图块、将它们锁在一起并实际编写代码的地方。我要编码什么呢？嗯，我将控制一个或多个精灵。就像在熟悉的游戏世界中一样，精灵就像您可能在屏幕上看到的角色。Scratch 世界中的默认角色实际上是一只看起来像这样的猫。

如果在这个例子中，我只有一只猫，我就可以通过让猫在右上角的小世界中向上、向下、向左、向右移动、旋转或做其他事情来让那只猫做一些事情。但是如果您想引入一只狗或一只鸟或任何数量的其他自定义角色，您只需添加更多精灵，它们就会在同一个世界中获得自己的位置。至于如何考虑这个世界中的运动，它实际上非常熟悉，尽管它暂时变得有点数字化了。

如果 Scratch 现在在屏幕中间，猫在 0, 0 处，如果您考虑 x, y 坐标或经度纬度。如果您将猫一直向上移动，这仍然是 x 等于 0，但它将是 y 180。180 是什么？垂直方向上 180 个像素或屏幕上的点。这是底部屏幕上的负 180 个像素。相比之下，如果您向左和向右移动，您的 x 值可能会改变。

负 240，但 y 是 0，或者正 240，y 也是 0。但在大多数情况下，您不需要知道或关心猫的像素坐标是什么。作为程序员，您通常最关心的只是您是否希望猫相对向上、向下、向左或向右移动，并让麻省理工学院在大多数情况下计算出移动这个东西的数学原理。好的。

所以让我们继续介绍这些程序中的第一个，通过做一些非常简单的事情，就像我们在 C 中所做的那样，但是通过如下编写代码来更简单一些。我要回到 scratch.mit.edu。按照之前的说明，我已经点击了“创建”按钮。如果我点击左侧这里的黄色块类别——我将放大——我们将看到一大堆黄色的拼图块。

**01:16:15 - 你好，世界**

也许你将在 Scratch 中编写代码时最常用的一个，仅仅是第一周，实际上是当点击绿色标志时。为什么？好吧，如果我们回到右上角的猫的世界，请注意，在猫的矩形世界上方，不仅有一个用于开始的绿色标志，还有一个用于停止的红色停止标志。所以让我们这样做。让我继续点击并拖动。

当点击绿色标志时，将其拖动到中间的任何位置并松开。现在我要转到外观，看起来这里有一大堆紫色的拼图块。我要选择一些简单的东西，比如“说‘你好’” ，拖动它。请注意，如果我靠得足够近，它会想要磁性地卡在一起。所以我就这样做，它就完成了。

这个带有文本的白色椭圆形表示这是“说”拼图块的输入。如果我想更常规地说“你好，世界”，我实际上可以手动更改输入的内容。事实上，根据传说，这是用 C 语言编写的第一个程序，现在在大多数语言中都是如此，包括在 Brian Kernighan 的书中。“你好，世界”通常是大多数程序员编写的第一个程序。所以这就是程序的内容。

让我继续在这里缩小。让我转到右侧并点击绿色标志，也许令人兴奋，也许令人失望，我们现在编写了一个程序，它非常简单地说“你好，世界”。现在让我们暂时让它更具技术性。我一直称之为的这个拼图块是什么？它实际上是一个类似的——

它是我们之前伪代码中思想的一个化身。上次在我的伪代码中，我们如何称呼那些动作和动词？观众：[听不清]。DAVID MALAN：函数。没错。所以这些紫色的拼图块实际上是函数，正如我们所看到的，一些函数接受输入，比如“你好，世界”。毕竟，Scratch 如何知道该说什么呢？

你必须向猫提供输入，也就是说函数确实可以像这样接受输入。在这种情况下是一个输入，但我们还将看到传入更多输入的机会。然而，猫在右上角的屏幕上所做的视觉效果通常被称为副作用。有时当你调用一个函数时，它会在视觉上做一些事情。

在这种情况下，您会看到一个卡通语音泡泡，上面写着“你好，世界”。这就是这个函数的副作用。因此，如果我们现在想将其映射到我们的输入和输出世界，并查看此副作用在哪里，这就是我在课程开始时提出的范式，简而言之，这就是计算机科学，它将成为我们实际上在整个课程中使用的框架，无论语言如何——无论语言如何演变。

那么这个特定程序的输入是什么呢？嗯，这个白色的椭圆形，“你好，世界”是我的输入。算法，解决某个问题的分步说明，是用代码实现的，这种语言叫做 Scratch，通过这个紫色的拼图块。根据此输入，该函数的输出是副作用，即猫确实在屏幕上的语音泡泡中直观地说出了“你好，世界”。

因此，我们今天开始使用的完全相同的范式控制着这只猫在这里的确切工作方式。好吧，让我们实际上回到这个程序，让它比那更有趣一点。让我继续点击红色的停止标志。

**01:19:00 - 你好，你**

让我实际上使用一种不同类型的拼图块，另一个函数做一些不同的事情。首先，我要去掉“说”块。所以我不仅要把它拉开，我还要把它拖到左边的任何地方，然后放手，它会自动删除自己。或者我可以右键单击或按住 Control 键单击，然后从一个小菜单中，我也可以明确地说删除。我现在要做的是在“侦测”下，这是一个浅蓝色的拼图块——这里有一大堆，但我将专注于这个。“询问某事并等待”。默认文本是“你叫什么名字？”

这没关系。但因为它是一个白色的椭圆形，如果我想更改问题，我可以手动更改输入。我要把它拖到这里。它会磁性地吸附在一起。我对这个问题没有意见。

但我该怎么回答呢？好吧，让我们这样做。我可以再次转到“外观”。我可以再抓取一个“说”块，让它吸附进去，我可以说“你好，大卫”。

但这将是我有意或无意中犯的许多错误中的第一个。让我点击绿色标志。Scratch 现在就像在 Web 浏览器中一样，提示我输入一些内容。所以让我继续输入我的名字。

大卫。回车。瞧。它起作用了。“你好，大卫。”不过，我有点作弊，对吧？

因为如果我缩小，停止，然后再次播放。让我在这里输入朱莉娅的名字，回车，它仍然说“你好，大卫”。所以这并没有真正实现我想要的想法。好的，那我该如何解决这个问题呢？嗯，似乎这一次我想要的不仅仅是一个副作用。

我想使用人类输入的值。为此，我们需要函数的另一个特性，即它们不仅有时会产生副作用，即视觉上发生一些事情。有些函数可以返回一个值，一个所谓的回传值，这将允许您实际重用人类输入的任何内容。

因此，回传值是被虚拟地传递给您的东西，您可以将其存储在称为变量的东西中，例如数学中的 x、y 和 z，并且您通常可以重用它一次或多次。所以让我实际提请大家注意，在左侧，不仅有蓝色的拼图块，“询问‘你叫什么名字？’并等待”，而且请注意，它下面有一个特殊的拼图块，这个蓝色的椭圆形叫做“答案”，它代表了计算机科学家所说的回传值。

因此，麻省理工学院将其捆绑在一起，并排放在一起，以明确其中一块与其他块相关。这意味着我可以这样做。我可以拖动这个椭圆形，并将这个椭圆形用作“说”函数的输入。

现在，请注意它的大小不同，但形状正确，所以没关系。Scratch 会增大或缩小东西以适应。但这也不太正确。让我继续这样做。让我继续停止，点击绿色标志。我将再次输入我的名字。D-A-V-I-D。回车。这有点奇怪或粗鲁。

就像，我至少想要一个“你好”，但它只是在屏幕上说“大卫”。好的，我可以解决这个问题。让我用红色的停止标志停止。让我暂时把它们分开。我可以把它放在中间，但它们暂时没有逻辑连接。

让我回到“外观”。让我抓取一个“说”块，第二个，让我继续说，只是为了语法正确，“你好，空格”。然后我将重新连接这个。

所以目前它看起来像我想要的，我想要一个“你好，”，然后根据人类输入的任何内容打印出回传值。所以让我缩小。让我点击绿色标志。再说一遍，“你叫什么名字？” D-A-V-I-D。并观察猫的副作用。

回车。它仍然没有正确地问候我。没有“你好”。万一它太快了，让我们再做一次。绿色标志。D-A-V-I-D。回车。它粗鲁地只说我的名字，这很奇怪。但是，这里的错误是什么呢？它更微妙一些。

为什么？是的？观众：它只是快速地过去了。

DAVID MALAN：是的。在这种情况下，它只是太快地过去了“说”命令或“说”函数。我的 Mac、你的 PC、你的手机，它就是这么快。两者都在发生，但对我的人眼来说太快了，甚至没有注意到。

所以我们可以通过多种方式解决这个问题。实际上，我可以使用完全不同的拼图块。事实上，麻省理工学院有点预料到了这一点。请注意，“外观”中的第一个拼图块是“说‘你好’”持续特定的秒数，您可以指定消息和秒数，因此是两个输入，现在也称为函数的参数。

函数的输入现在只是一个参数。这可以在这里解决问题。也许我可以更明确地这样做。我可以转到“事件”，向下滚动一点，然后——抱歉，在“控制”中是橙色的，我可以抓取一个“等待”块，然后我可以把它插入中间。这实际上可能会有所帮助。所以我可以点击绿色标志。

D-A-V-I-D。回车。“你好，大卫。”我可以更改时间以使其更自然。但是，如果我想让猫一口气说“你好，大卫”怎么办？好吧，为此，我需要使用如下所示的稍微不同的技术。让我继续去掉“等待”。让我去掉第二个“说”块，并用停止标志停止猫。

让我转到这里的“运算”，让我巧妙地抓住这个。“连接”块在底部。默认情况下，它使用“苹果”和“香蕉”作为占位符，但那些是白色的椭圆形，所以我可以更改它们。让我把这个拖到“说”函数的白色椭圆形上，然后放手，它会吸附并填充。让我继续在这里输入“你好，空格”，而不是“苹果”。

我应该用什么代替“香蕉”呢？

观众：答案。

DAVID MALAN：是的。所以这将是“答案”回传值——回传值。所以让我再次转到“侦测”。让我再拖动它的一个副本。

你可以一次又一次地使用它们。它们不会消失。我想把“答案”拖到“香蕉”上，以便“连接”的第二个输入实际上是“询问”块的输出，就像那样。它会吸附到位。

所以现在如果我继续并再次点击绿色标志。D-A-V-I-D。回车。现在我们在美学上拥有了我关心的行为。但除了美学之外，这里的目标实际上是再次将其映射到我们将看到的相同范式。

此示例的算法、输出和输入如下。“说”块的输入是“你叫什么名字？”当然，用代码实现该算法的函数是“询问并等待”块。然而，“询问”块的输出不是一些视觉上的副作用。它是一个名为“答案”的回传值，就像一个变量，一个像数学中的 x、y 和 z 一样的特殊变量。

但在这个例子中，我们在编程中通常用实际的单词来描述变量，而不仅仅是字母。但是“说”块的这个输出，我想腾出空间来将其作为第二个参数传递给“说”块。所以让我们这样做。让我们退一步，现在建议对于我刚刚使用的“连接”块。

它接受两个输入，“你好，空格”和“答案”。所讨论的函数确实是“连接”块。此函数的输出最好是“你好，大卫”。我想对“连接”块的输出做什么？

好吧，让我清除屏幕。让我把它移过来，因为现在“连接”块的输出将立即成为“说”块的输入，以便现在在这个多步骤过程中，输出是“你好，大卫”的副作用。因此，我将这些块嵌套在一起的事实是非常有意的。如果我在这里放大，请注意“你好”和“答案”位于“连接”之上，“连接”位于“说”块之上。如果你回想一下高中数学，这就像你有括号，你必须先做括号里面的事情，然后再做括号外面的事情。

这是相同的想法，但我只是在视觉上将它们堆叠起来。但是输出可以变成输入，这取决于函数在那里期望什么。让我在这里暂停一下，看看是否对不是猫在做什么，而是猫如何做这件事有任何疑问。

当前有什么问题吗？好的。好吧，让我们让猫更像猫，然后这样做。

**01:27:02 - 喵**

让我扔掉所有的“说”块，然后放手。让我在左下角介绍一个 Scratch 的不错的功能，其中还有这些扩展，它们倾向于使用云，互联网，为你提供更多功能。事实上，我要点击这里这个扩展，文本转语音。如果我点击它，我突然在底部获得了一个全新的块类别。文本转语音。它们恰好是绿色的。但这里的好处是我现在实际上可以让猫说一些可听见的东西。所以让我把“朗读”块拖到这里，而不是“说”块。

我不希望它只说“你好”。让我停止它。所以让我回到“运算”。让我再抓取一个“连接”块，因为我把另一个扔掉了。让我把“苹果”改成“你好，空格”。

让我转到“侦测”。让我把“答案”拖到“香蕉”上。现在让我点击绿色标志，让我输入我的名字，D-A-V-I-D。过一会儿我会按回车键。电脑：你好，大卫。

DAVID MALAN：好的。它不完全像猫，但它是合成的。

但事实证明，在这些文本转语音块下，还有一些其他的。例如，“将声音设置为女低音”似乎是默认设置。但让我们改变一下。所以请注意，有些拼图块不仅仅需要白色的椭圆形。它们甚至可能有下拉菜单。

因此，创建该拼图块的人提前决定了该输入的可用选项是什么。所以我要把它改成“吱吱声”，这听起来——或者实际上“小猫”听起来更贴切。让我缩小，点击绿色标志，输入我的名字。

D-A-V-I-D。回车。电脑：喵，喵。

DAVID MALAN：这很有趣。

所以似乎无论我输入什么都无关紧要。那么“DAVID MALAN”怎么样？电脑：喵，喵，喵。

DAVID MALAN：所以它似乎会根据我输入的短语的长度按比例发出喵叫声。如果我把“小猫”改成“巨人”，它很快就会变得有点令人毛骨悚然。让我继续并点击播放。D-A-V-I-D。回车。

电脑：你好，大卫。

DAVID MALAN：所以你可以以非常非学术的方式开始享受其中的乐趣，但只是玩弄这些不同的输入和输出。但让我们实际上让猫做一些更像猫的事情，实际上是喵叫，而不是说任何话。所以让我把所有这些都扔掉。现在让我转到“声音”。让我拖动“播放声音直到结束”。

请注意，在这里的下拉菜单中，默认情况下，你只能得到猫的声音。你可以录制你自己的声音。有一个完整的狗、鸟和各种声音库，你可以导入到程序中。我会用猫来保持简单。让我点击绿色标志。

电脑：喵。

DAVID MALAN：好的。所以猫叫了一声。如果我想让猫再叫一声，我可以这样做。

电脑：喵。

DAVID MALAN：如果我想让猫叫第三声，我可以再次点击播放。

电脑：喵。

DAVID MALAN：所以这有点乏味，如果玩这个游戏，我必须不断点击按钮，不断点击按钮，才能让猫以这种方式保持虚拟的活力。

所以也许我希望这种情况一次又一次地发生。好吧，让我这样做。让我拖放。或者我可以右键单击或按住 Control 键单击，然后一个小菜单会让我复制粘贴或复制块。但我会继续拖放。让我们这样做。电脑：喵。喵。喵。

DAVID MALAN：猫有点饿了，不开心。

所以让我们放慢速度，让它再次变得可爱。所以让我转到“控制”。让我抓住其中一个“等待一秒钟”，然后我把它放在这里。另一个。让我把它放在这里。

再次点击播放。电脑：喵。喵。

DAVID MALAN：更可爱了。不那么饿了。

当然。但是，如果我的目标是让猫叫三声，那么这个程序现在可以说是正确的。但是现在，即使你以前从未编程过，也要批评这个程序。它设计得不好，尽管它是正确的。

换句话说，它可以更好。你觉得怎么样？是的？

观众：循环。

DAVID MALAN：所以使用循环。为什么呢？既然它能正常工作，你为什么鼓励我使用循环呢？

观众：绘制起来更容易。

DAVID MALAN：是的。总而言之，使用循环更容易，因为我可以在一个地方明确指定我希望它循环多少次。此外，坦率地说，任何时候你在代码中复制和粘贴某些东西，或者一遍又一遍地拖动相同的东西，你很可能在做一些愚蠢的事情。为什么呢？因为你在不必要地重复自己。这有点极端，但假设我想稍后更改此程序，以便猫在两次喵叫之间暂停两秒钟。好吧，显然我可以在这里输入 2。

但是如果我忘记了呢？假设这个程序不是五个或六个拼图块。假设它是 50 或 60 或 500 或 600。最终，我或与我一起工作的同事会搞砸。他们会在一个地方更改一个值，忘记在另一个地方更改它。

那么你为什么要招致犯错的可能性呢？只需简化事情，这样你只需在一个地方更改输入即可。那么我该怎么做呢？让我缩小。让我把大部分重复的内容扔掉，只留下“播放”和“等待”函数。

现在，我也在“控制”下，抓取其中一个。例如，我可以按如下方式重复。让我抓取一个“重复”。我将不得不分两部分移动它们。所以我要把它移下来。它太小了，但它会增长以适应正确的形状。

然后让我把它重新连接到这里。让我把默认的 10 改成 3。现在我想我已经完全按照你所鼓励的那样做了，那就是简化。我现在点击播放。

电脑：喵。喵。

DAVID MALAN：现在和。

电脑：喵。

DAVID MALAN：是的。所以仍然是正确的，但可以说是设计得更好。我现在可以保持简单，只在一个地方更改内容，它将继续工作。但我认为这现在变得有点乏味了。

**01:32:21 - 抽象**

就像，我为什么要实现喵叫的想法呢？麻省理工学院如果只为我们实现一个喵叫的拼图块不是更好吗？因为整个主题都是围绕一只猫展开的。为什么没有喵叫的拼图块呢？为什么我需要经历所有这些复杂性来构建该功能呢？好吧，Scratch 的好处以及编程语言的普遍好处在于，你通常可以发明你自己的拼图块，你自己的函数，然后使用和重用它们。所以让我继续这样做。我将转到这里粉红色的“我的块”。

我将继续点击“制作块”，我将看到这个界面。我将把这个块称为“喵”，因为显然麻省理工学院忘记为我们实现它了。我将继续并立即点击“确定”。现在你将看到两件事。

一，在屏幕上，我得到了这个占位符粉红色块，上面写着“定义喵如下”。因此，我附加到该“定义”块底部的任何内容都将定义喵叫的含义。

在左上角，请注意我在“我的块”下有什么。我现在有一个名为“喵”的粉红色拼图块，它是一个新函数，它将执行该代码块告诉猫执行的任何操作。那么我想在这里做什么呢？好吧，我现在要保持简单。我要移动“播放声音喵直到结束”并等待两秒钟。虽然让我们把它改回一秒钟以加快进度。现在让我把“喵”拼图块拖到我的循环中，这样，现在它会做什么呢？它会喵叫三次。

只是为了戏剧化，眼不见心不烦。让我，出于非技术原因，把它一直拖到屏幕底部，然后向上滚动，只是为了在视觉上说明现在喵叫存在。这是我们可以抽象掉的实现细节，不必关心它是如何存在的，因为我现在在更高的概念层面上知道，如果我想要喵叫，我只需使用“喵”拼图块，而我或其他人已经处理了如何实现喵叫。

所以现在让我继续并点击播放。

电脑：喵。喵。喵。

DAVID MALAN：好的，所以是完全相同的代码，但可以说设计得更好，因为我现在给自己提供了可重用的代码，这样我就不必复制粘贴那几个块了。我可以一次又一次地使用“喵”。但让我们做一个改进。

让我实际上向下滚动到我确实实现了这个的地方。让我按住 Control 键单击或右键单击它，让我编辑我刚才创建的粉红色块，因为我想练习我一直在宣扬的关于输入的内容。所以我不希望这个函数只被称为“喵”。我希望这个函数也接受一个输入，为了与我们之前使用的 n 保持一致，n 在计算机科学中通常表示数字，让我喵叫 n 次。

只是为了让这个拼图块对程序员更友好，让我添加一个文本标签，除了使这个函数从左到右以更友好的英语方式阅读之外，它没有任何技术意义。“喵叫 n 次”。让我点击“确定”。现在请注意，底部的东西已经改变了，它不仅被称为“喵”，还明确提到了 n，这是一个圆圈，这正是我们在它被称为“答案”时看到的变量形状。

但这并不是一个回传值。这又是我们将要称之为参数的东西，即函数的输入。所以让我这样做。我要把它移回顶部，这样我就可以在一个地方看到所有东西，我要做一个修改，因为我现在 的目标是制作一个经过改进的喵叫版本，它实际上考虑了我希望猫喵叫多少次。因此，我不会在“当点击绿色标志时”下的我自己的程序中使用循环，我要暂时分离它。我要把它移开。我要把这段代码移到这里，然后我要把它重新连接到这里。

所以暂时只关注左侧，“喵”现在被定义为重复三次以下两个函数。“播放声音”和“等待”。但这不太正确。我想去掉三。那我该怎么办呢？

因为我刚才自己创建了这个“喵”函数的输入，所以我实际上可以把它的一个副本拖到右边，也就是把三改成一般的 n。所以现在我有一个叫做“喵”的函数，它会喵叫任意次数。现在的好处是，我的实际程序是由那个绿色标志控制的，我可以输入三，我可以输入 10，我可以输入 100，它都会工作。从今以后，我可以再次戏剧性地向下滚动它，这样我们就不再知道或关心它了。现在我的程序是一行代码，其中喵叫的概念已经通过定义我自己的函数或自定义块被抽象掉了。那么，关于这个想法，这个创建你自己的函数来隐藏实现细节的原则，一旦你解决了问题，有什么问题吗？因此，你不想再考虑同样的问题了。这就是编程的美妙之处，通常情况下。

关于我们刚刚在这里做了什么，有什么问题吗？没有？好的。好吧，让我们这样做。现在让我们在代码中让它更具互动性。

**01:37:23 - 条件语句**

让我转到这个绿色标志。让我向下滚动，扔掉所有这些辛苦的工作，我们在课程网站上提供了所有这些程序的副本，如果你想更慢地回顾它们，可以一步一步地查看。让我们这样做。在“控制”下，事实证明还有其他循环方式。

有一个“无限循环”块，它会永远做某事。所以在“无限循环”块中，有一些地方可以放置一些其他的代码。我将移动到这里的“控制”部分，并抓取其中一个“如果”块，所以是这些条件语句之一。

让我们把它插入这里。现在注意“如果”，然后有这个类似梯形的占位符，它可能会适合什么？“如果”是一个条件语句。“无限循环”是一个循环。

“说”等等是函数。我们使用的另一个关键术语是什么？所以是一个布尔表达式。我们需要在这里放置一个“是”、“否”或“真”、“假”的问题。那么这些是什么呢？好吧，我已经使用 Scratch 多年了，所以在“侦测”下，这里有一个这样的形状。“碰到鼠标指针？”，问号。

问号实际上唤起了布尔表达式是“是”、“否”的整个概念。它太大了，无法适应，但它是正确的形状。所以让我拖动它。放手。它会增长以填充。现在让我转到“声音”。

让我抓住“播放声音喵直到结束”，并把它放在条件语句中，这样我刚刚在这里实现了什么样的程序呢？可以说？当我点击绿色标志时，这个程序会做什么？

嗯，目前什么都不会。观众：没有碰到猫。

DAVID MALAN：但我没有碰到猫。所以如果我把鼠标指针移到猫身上。

电脑：喵。

DAVID MALAN：再来一次。

电脑：喵。

DAVID MALAN：再来一次。

电脑：喵。

DAVID MALAN：这有点像是在实现抚摸猫的想法，如果你愿意的话，因为我一直在等待、等待、等待。鼠标指针是否接触到那个精灵，接触到那只猫？

只有当是的时候，才会播放声音“喵”直到结束。但现在我们可以让事情变得更有趣。让我停止这个，让我做一些完全不同的事情。让我把所有这些辛苦的工作都扔掉。

让我转到“扩展”。让我转到“视频侦测”，因为很多笔记本电脑，包括我自己的，现在都有一个小的网络摄像头。让我批准在那里使用它。你可以在画面中看到我。让我这样做。让我拖动其中一个“当运动超过某个度量时”。

通过反复试验，我发现 50 往往效果很好。让我走出画面，在旁边编程。如果我去“播放声音喵直到结束”，请注意，这是使用“当点击绿色标志时”的替代方案。

这是一类不断等待我们所说的事件的块。事件只是屏幕上可能发生的某些事情，点击、拖动、鼠标移动等等。所以让我缩小这里。现在，如果我能做到这一点——开始了。

不，太慢了。还是太慢了。等等，我点击播放了吗？让我们看看。再试一次。

电脑：喵。

DAVID MALAN：开始了。好的。50 显然有点太高了。所以让我们把它调低一点。10.

电脑：喵。

DAVID MALAN：好的，好吧。

电脑：喵。

DAVID MALAN：开始了。

电脑：喵。

DAVID MALAN：开始了。

电脑：喵。

DAVID MALAN：好的，所以我们现在更实际地实现了抚摸猫的想法。

电脑：喵。喵。

DAVID MALAN：哦，该死的。好的。

电脑：喵。喵。喵。

DAVID MALAN：好的。所以这是一个错误。现在——这是麻省理工学院的错。所以它没有响应红色的停止标志而停止。所以在有疑问时你会怎么做呢？最极端的情况，你重新启动。现在，我只是要关闭窗口。

好的。所以现在我们已经看到了我们在伪代码中看到的所有这些原语，但在这个图形化编程语言中得到了体现，而且，再次强调，没有括号、分号、双引号和所有我们很快将介绍的标点符号。但现在，我们已经有了机制，我们可以做一些非常有趣的事情。

**01:41:14 - 奥斯卡时间**

所以事实上，我想，本着回顾过去的精神，我想打开我实际上学习时写的第一个程序——我交叉注册了麻省理工学院的一门课程，并参加了一门向有抱负的教师介绍 Scratch 的课程。我实现了这个名为“奥斯卡时间”的程序，这是一个使用我小时候喜欢的歌曲的游戏，它允许你把垃圾拖到垃圾桶里。但是为了让它栩栩如生，也许是为了换取一个压力球，我能找一个勇敢的志愿者上来控制这个键盘吗？我看到你最热情地举手了。是的，下来吧。

非常高兴。[掌声] 过一会儿，我们确实要休会了。但现在的目标是要通过一个比上一个稍微困难一点的迷宫，不过，我们先让你向你前面的同学们介绍一下你自己。

观众：大家好。我是埃里克。我来自费城，我也来自霍利斯大厅。[欢呼声] 

DAVID MALAN：只有一个人来自霍利斯。好的。欢迎。好的。埃里克，请到这里来拿键盘。

一旦你点击绿色标志，它也将是关于上、下、左、右的。如果我们可以调大音乐的话。[MC Hammer 的“U Can't Touch This”] 你不能碰这个 

DAVID MALAN：所以请注意，黑色的墙壁比上次复杂了一点。但目标是到达最右边的精灵并触摸它，这时你将进入下一个级别。

当然，下一个级别有耶鲁在来回移动。你已经进入了第三个级别。但现在有两个耶鲁。所以另一个精灵正在以稍微不同的方向随机移动。三个耶鲁。

下一个级别。麻省理工学院加入了。

很好。墙壁现在消失了。普林斯顿加入了。

很好。两个普林斯顿。好的。新的生命。

好的，又一条命。很好。很好。哦。

很好。倒数第二个级别。三个普林斯顿。最后一个级别。

是的！恭喜。[掌声] 谢谢。好的。那么，这就是 CS50。欢迎加入。现在供应蛋糕。

[音乐播放中]

---
## 视频脚本-英文

