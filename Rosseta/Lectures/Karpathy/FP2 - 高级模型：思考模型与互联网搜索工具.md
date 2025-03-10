
# 高级模型：思考模型与互联网搜索工具

## 解锁LLM的深层推理能力：思考模型(ReasoningModels)的崛起

现在，我们将进入一个更为高级的LLM领域：思考模型(ReasoningModels)。在之前的视频中，我们已经了解了语言模型的训练过程，包括预训练和后训练两个主要阶段。而思考模型的出现，则标志着LLM训练技术迈向了一个新的台阶，它引入了第三个关键阶段：强化学习(ReinforcementLearning)。

强化学习的引入，为LLM带来了质的飞跃。在这个阶段，模型不再仅仅是被动地学习语言规律和知识，而是开始主动地学习如何进行推理和思考。可以将强化学习阶段，比喻为模型在大量类似于教科书中的练习题的问题上进行刻意练习。这些练习题，通常涵盖了大量的数学问题、代码问题以及其他需要复杂推理的问题。在强化学习的过程中，模型通过不断地尝试不同的解题策略，并根据反馈信号(例如，答案是否正确)进行自我优化，最终学习到一系列能够引导其获得良好结果的思考策略。

当你仔细观察这些思考策略时，你会惊讶地发现，它们非常类似于人类在解决复杂问题时所进行的内心独白。模型会尝试不同的想法，它会回溯到之前的步骤，它会重新审视假设，它会进行逐步的逻辑推演，它会进行试错，它会进行反思，等等。这些思考过程，与人类的思维活动惊人地相似。

值得注意的是，很多这些思考策略，都很难作为人类标注员进行硬编码，因为我们并不清楚最佳的思考过程应该是什么样的。只有在强化学习的环境中，模型才能自由地尝试各种不同的方法，并通过大量的试错，自主地找到最适合自身知识和能力的思考过程。因此，强化学习阶段，被认为是训练这些模型的第三个关键阶段，也是近年来LLM技术领域的一个重大突破。

**DeepSeek的先驱探索：强化学习驱动推理能力提升**

我们在之前的视频中，曾经介绍过DeepSeek团队发表的一篇重要论文，这篇论文是最早公开讨论思考模型训练技术的文献之一。他们在这篇论文中，详细阐述了如何通过强化学习来激励LLM中的推理能力。这篇论文，正是我们在之前的视频中看到的，关于通过强化学习提升LLM推理能力的开创性研究。

**“思考气泡”：模型内部的额外思考过程**

现在，我们需要对我们之前用来卡通化地描述LLM的图景进行稍微的调整。基本上，我们可以将LLM的“表情符号”升级一下，让它现在拥有这个可选的“思考气泡”。当你使用一个思考模型时，它会在模型内部进行额外的思考过程。您正在使用的模型，是经过强化学习进行了额外调整的模型。

在质量上，思考模型与非思考模型相比，意味着什么呢？在质量上，最显著的区别在于，思考模型会进行更多的思考。您可以期望的是，使用思考模型，您将获得更高的准确性，尤其是在数学、代码以及其他需要大量思考的问题上。对于一些非常简单的问题，思考模型可能实际上不会带来明显的收益，但在处理真正深入、难度较高的问题时，思考模型的优势就会凸显出来。但需要注意的是，使用思考模型，您为此付出的代价是，模型会进行思考，这有时可能需要几分钟。因为模型在思考的过程中，会发出大量的tokens，您必须耐心等待，因为模型正在进行思考，就像人类在思考一样。但是，当您面对非常困难的问题时，这种思考过程，可能会转化为更高的准确性，最终帮助您找到正确的答案。

### 思考模型实战：梯度检查编程难题的解决

为了更具体地说明思考模型的价值，让我们来看一些实际的例子。这是一个具体的例子，发生在我最近被一个编程问题困扰的时候。当时，我遇到了一个叫做梯度检查的问题，这个梯度检查失败了，但我不知道为什么。我将模型我的代码复制粘贴到了ChatGPT中。代码的细节并不重要，但这基本上是关于一个多层感知器的优化的代码。细节并不重要，重要的是，这是一堆我写的存在bug的代码，因为我的梯度检查无法正常工作。我当时只是在寻求ChatGPT的建议，希望能找到解决问题的线索。

我最初使用的是GPT-4模型，这是OpenAI最强大的模型之一，但没有开启思考模式。在这种模式下，GPT-4只是给出了一些它认为是问题所在，或者我应该仔细检查的地方，但实际上并没有真正解决问题。它给我的所有建议，都没有触及问题的核心，模型并没有真正帮我找到bug的根源。它只是泛泛地告诉我应该如何调试代码等等。

但后来，我做了一个关键的改变。在ChatGPT界面的下拉菜单中，我切换到了一个思考模型。对于OpenAI来说，所有以“O”开头的模型，都属于思考模型。例如，O1Mini、O3Mini、O3MiniHigh和O1Promode，都是思考模型。OpenAI在命名模型方面做得不太好，但事实就是这样。在模型描述中，它们可能会使用一些类似“使用高级推理”或“擅长代码和逻辑”之类的话语，来暗示这些模型是思考模型。但实际上，这些模型基本上都是通过强化学习进行调整的。因为我每月支付200美元订阅了ChatGPTPro服务，所以我可以访问OPromode，这是最擅长推理的模型。如果您没有Pro订阅，您可能需要尝试一些其他的思考模型，例如O1Mini或O3Mini，这取决于您的定价层级。

当我将同一个提示，完全相同的代码，输入给O1Pro模型(这是OpenAI最擅长推理的模型，需要每月支付200美元才能使用)时，奇迹发生了。O1Pro模型在收到我的提示后，继续思考了大约1分钟，它在模型内部经历了一系列复杂的思考过程。OpenAI并没有完全向你展示确切的思考过程，他们只是给出了一些思考的简要总结。但从这些总结中，我们可以看到，模型仔细地思考了一段时间代码，然后它实际上给出了正确的解决方案。它注意到代码中存在参数不匹配的问题，并指出了我是如何打包和解包这些参数的错误之处。O1Pro模型真正地解决了我的问题。

### 多模型对比：思考模型vs.非思考模型

为了更全面地评估思考模型的效果，我尝试将完全相同的提示，相同的代码，也输入给其他一些LLM。例如，Claude。我将相同的问题输入给Claude，令人惊讶的是，Claude实际上也注意到了正确的问题，并成功地解决了它。更令人意外的是，我当时使用的是Claude3.5Sonnet模型，而Sonnet并非一个思考模型。据我所知，Claude3.5Sonnet不是一个思考模型，而且据我所知，Anthropic目前没有部署思考模型。当然，当您观看这个视频时，情况可能会有所改变，Anthropic可能会推出新的思考模型。但即使没有思考模型的加持，Claude3.5Sonnet仍然成功地解决了问题。

当我访问Gemini时，我也问了它同样的问题，Gemini也解决了问题。尽管我本可以尝试使用Gemini的思考模型，但在这个问题上，似乎没有必要。我也将问题输入给了Grok，在这种情况下，我使用的是Grok3模型，Grok3也解决了一堆问题之后的问题。所以，Grok3也成功地解决了问题。

最后，我访问了perplexity.ai。我个人很喜欢perplexity的一个重要原因是，当您访问perplexity的模型下拉菜单时，它们托管的模型之一正是DeepSeekR1。DeepSeekR1，正是具有DeepSeek团队研发的推理能力的模型，也就是我们在之前提到的DeepSeek论文中所描述的模型。Perplexity只是托管了DeepSeekR1模型，并使其非常容易使用。我将代码复制粘贴到perplexity中，并运行了它。Perplexity的界面渲染效果可能不太理想，但在页面的下方，您可以看到模型的原始思想，即使您可能需要展开它们才能看到完整的内容。但您可以看到，模型逐步地“思考”了这个问题。例如，它首先意识到用户在梯度检查方面遇到了问题，然后它尝试了一堆不同的方法，但都没有奏效。然后，它突然意识到，“但是等等，当他们累积梯度时，他们做的事情是不正确的。”于是，它开始检查参数打包的顺序，因为问题很可能出在这里。最终，DeepSeekR1模型注意到了问题所在，并明确指出，“这是一个关键的错误。”整个思考过程，有点像模型在一步一步地“思考”，您必须等待几分钟，才能看到最终的结果，但最终，DeepSeekR1也提出了正确的答案。

### 思考模型：难题求解的利器，并非万能药

长话短说，我希望通过这些例子，向您展示什么呢？我想向您展示的是，存在一类我们称之为“思考模型”的模型。所有不同的LLM提供商，可能会提供思考模型，也可能不提供思考模型。这些思考模型，对于解决数学和代码等难题，最有效。在这些特定场景下，思考模型可以显著提高您获得正确答案的准确性。但在许多其他场景下，例如，如果您只是要求旅行建议或类似的简单问题，您可能不会从思考模型中受益。没有必要为了获得旅行建议，而等待一分钟，让模型“思考”您可能想去的地方。

对我自己而言，我通常会首先尝试非思考模型，因为它们的响应速度非常快。但当我在使用非思考模型后，怀疑模型的响应可能不如它本可以达到的那么好，并且我想给模型一个机会，让它思考更长的时间，我会切换到一个思考模型。具体选择哪种模型，取决于您有什么可用的模型。

例如，当您访问Grok时，当您开始与Grok的新对话时，在您提出问题的界面，例如，您输入“你好”这样的简单问候语，您会看到一个“思考”(Reasoning)的选项。让模型花时间。如果您希望使用思考模型，您可以打开“思考”选项，然后点击“开始”。当您点击“思考”时，Grok在底层会自动切换到思考模型。所有不同的LLM提供商，都会提供一些选项，让您选择是否希望模型进行思考，或者是否可以只使用以前的非思考模型。

## 互联网搜索工具：获取最新信息的关键

好的，现在我想继续讨论下一个非常重要的工具：互联网搜索工具。到目前为止，我们与语言模型的交互，仅仅是通过文本进行的。我们所谈论的语言模型，再次强调，就是一个存储在文件夹中的“zip文件”，它是惰性的、封闭的，没有工具，它仅仅是一个可以发出tokens的神经网络。

我们现在想要做的是，超越这一点，我们想让模型能够使用一堆工具，从而扩展其能力边界。其中最有用的工具之一，无疑是互联网搜索。接下来，让我们深入探讨，如何让模型使用互联网搜索。

### 互联网搜索的应用场景：获取最新剧集信息

为了更好地说明互联网搜索工具的应用价值，我再次使用我个人生活中的具体例子。几天前，我正在观看《白莲花》(TheWhiteLotus)第三季。我看了第一集，非常喜欢这部电视剧。看完之后，我很好奇第二集什么时候播出。在没有LLM的“旧世界”中，您可以想象，您可能会打开谷歌或类似的搜索引擎，然后输入“《白莲花》第三季新剧集”这样的关键词，然后开始点击搜索结果中的链接，也许会打开其中的几个网页，对吧？您开始在网页中搜索相关信息，试图弄清楚第二集的播出时间。有时候您很幸运，可能会直接找到一个播出时间表。但很多时候，您可能会被各种疯狂的广告干扰，网页上充斥着大量的随机信息，整个搜索体验并不愉快，效率也不高。

所以，如果一个模型能够为您做这种搜索，自动访问所有相关的网页，然后获取所有这些网页的内容，并将这些内容“塞进”上下文窗口，然后基于这些网页内容，直接给您响应，那岂不是非常棒吗？这正是我们现在要实现的目标。

### 互联网搜索的工作原理：特殊Token与上下文增强

基本上，我们引入了一种机制，一种方法，让模型能够发出一个特殊的token，这个token，代表着“搜索互联网”的指令。当模型发出“搜索互联网”的token时，ChatGPT应用程序，或者您正在使用的任何LLM应用程序，都会停止从模型中采样tokens，它会获取模型给它的查询关键词，然后真正地去执行互联网搜索。在搜索过程中，应用程序会访问相关的网页，获取所有网页的文本内容，并将所有这些文本内容都放入上下文窗口中。

这样一来，我们就为模型引入了一个强大的互联网搜索工具，这个工具本身，也可以向我们的上下文窗口贡献tokens。在这种情况下，它会贡献大量的互联网网页的文本内容，也许是10个甚至更多的网页，它会将这些网页的文本内容拼接在一起，这可能会包含来自这些网页的数千个tokens，就像我们自己手动打开这些网页并查看它们的内容一样。然后，在应用程序将所有这些网页的文本内容插入到上下文窗口之后，模型会重新获得控制权，它会参考上下文窗口中的所有信息，并结合您的原始问题，即“《白莲花》第三季什么时候播出？”，从网页内容中提取答案，给出正确的响应。

请特别注意，这是一个非常好的例子，说明了为什么我们需要互联网搜索。如果没有互联网搜索工具，模型根本没有机会给我们正确的答案，因为正如我之前提到的，这个模型是在几个月前训练的，当时《白莲花》第三季的播出时间表可能还未确定。所以，《白莲花》第三季什么时候播出，很可能不是模型自身知识的一部分，也不在模型的“zip文件”中，因为这很可能是一个最近几周才最终确定的信息。因此，模型必须进行互联网搜索，才能学习到这个最新的知识。它从网页中学习，就像您和我没有LLM帮助时所做的那样。然后，一旦相关信息被加载到上下文窗口中，模型就可以参考这些信息，并回答我们的问题。

请再次记住，上下文窗口是这个对话的“工作记忆”。所以，一旦我们加载了网页文章，一旦所有这些网页，将它们的文本内容想象成被复制粘贴到上下文窗口中，现在，这些信息就存在于模型的“工作记忆”中，模型实际上可以回答这些问题，因为它可以在上下文窗口中找到答案。

### PerplexityAI与ChatGPT“搜索网络”功能

长话短说，不要手动执行这种繁琐的搜索工作，而是使用像perplexity这样的工具。perplexity.ai提供了一个非常优秀的、用于进行互联网搜索的LLM。我认为PerplexityAI是第一个令人信服地实现这一功能的应用程序。最近，ChatGPT也引入了一个“搜索”按钮，上面写着“搜索网络”(Searchtheweb)。我们将在稍后的内容中详细介绍这个功能。

现在，当您想查询“《白莲花》第三季的新剧集什么时候播出？”这样的问题时，您可以直接向支持互联网搜索的LLM提问。您不必再手动完成繁琐的搜索工作，我们只需要按下回车键，模型就会自动访问相关的网页，它会自动创建所有必要的搜索查询，然后为您提供最终的答案。所以，互联网搜索工具为您做了大量的工作，大大提高了信息获取的效率。而且，通常情况下，LLM在给出答案的同时，还会提供引文，标明信息来源。通过这些引文，您实际上可以自己访问这些网页，验证信息的真实性，确保这些答案不是来自模型的幻觉。您可以仔细检查答案是否真的正确，因为从理论上来说，互联网搜索工具并不能100%保证答案的绝对正确性，它只是可能会或可能不会工作。

如果我们接受使用互联网搜索工具这种方式，我们也可以访问ChatGPT，提出同样的问题。但现在，当我们提出这个问题时，如果没有实际选择“搜索”选项，我实际上不太确定模型会做什么。在某些情况下，模型可能会错误地认为这是最近的知识，并且它可能“自认为”知道答案，从而没有进行互联网搜索，直接给出一个可能不准确的答案。在另一些情况下，模型可能会正确地判断出这需要进行互联网搜索。为了确保模型进行互联网搜索，在某些情况下，我们可能需要明确地声明我们想要进行搜索。在我个人的使用习惯中，如果我知道我所查询的信息模型很可能不知道，我就会主动选择“搜索”选项，以确保模型进行互联网搜索。但让我们先看看，不主动选择“搜索”选项，看看ChatGPT会发生什么。

好的，ChatGPT正在搜索网络，然后它打印出答案，并且提供了引文。所以，在这个例子中，模型实际上自己检测到它需要搜索网络，因为它理解新剧集播出时间是一种最近的信息，模型自身可能不具备这种最新的知识。所以，ChatGPT自动进行了互联网搜索，并给出了答案。或者，如果我创建一个新的对话，我也可以主动选择“搜索”选项，因为我知道我需要搜索，然后输入我的问题，ChatGPT就会做同样的事情，搜索网络，并给出搜索结果。

所以，基本上，当您使用这些LLM时，请留意互联网搜索这个功能。例如，Grok...抱歉，让我们尝试没有选择“搜索”的Grok。好的，Grok模型也进行了一些搜索，它知道它需要搜索，并给出了答案。

基本上，让我们看看Claude做了什么。您看，Claude实际上有搜索工具可用。但是，Claude给出的答案是，“截至我在2024年4月的最后一次更新。”这里的“最后一次更新”，指的就是模型进行预训练的时间。所以，Claude只是说，截至我的最后一次更新，也就是2024年4月的知识截止日期，《白莲花》第三季已经被宣布了，但它不知道新剧集的具体播出时间。这意味着，Claude没有将互联网搜索集成作为一个选项，它不会通过互联网搜索来获取最新的播出时间信息，也不会给您答案。我预计Anthropic(Claude的开发者)可能正在积极地进行互联网搜索功能的集成。但至少在目前，Claude可能还不具备互联网搜索功能。

让我们尝试Gemini，让我们看看Gemini怎么说。“不幸的是，还没有《白莲花》第三季的官方发布日期。”Gemini2.0pro实验版无法访问互联网搜索，也不知道新剧集的播出时间。我们可以尝试一些其他的Gemini模型，比如2.0flash，让我试试那个模型。好的，Gemini2.0flash似乎知道新剧集的播出时间，但它没有给出引文，没有标明信息来源。哦，等等，好的，在那里，我们得到了来源和相关内容。所以我们看到Gemini2.0flash实际上有互联网搜索工具。但我猜测Gemini2.0pro(这是他们拥有的最强大的模型)实际上没有访问互联网搜索的权限。在这里，Gemini实际上明确地告诉我们，“2.0pro实验版缺乏对实时信息的访问，以及一些Gemini功能。”所以，这个模型没有完全与互联网搜索连接。

### 互联网搜索应用场景拓展：从剧集信息到股票动态

长话短说，我们可以让模型为我们执行谷歌搜索，自动访问网页，直接将信息拉入上下文窗口，并快速回答问题。这是一个非常非常酷的功能，但不同的模型，不同的应用程序，对这个功能的集成程度有所不同。所以您必须注意这一点。有时模型会自动检测到它们需要进行搜索，有时您最好明确地告诉模型您希望它进行搜索。

当我在使用GPT-4时，如果我知道我所查询的问题需要进行互联网搜索才能获得答案，我可能会主动勾选“搜索”选项。所以，这就是互联网搜索工具。

我想再向您展示几个我在自己的工作中如何使用搜索工具的例子。我使用了哪些类型的查询呢？对我来说，很容易做到这一点，因为通常对于这些需要互联网搜索的场景，我出于习惯会直接去perplexity，即使ChatGPT现在也可以做这些事情，可能还有许多其他服务也可以。但我碰巧使用perplexity进行这些类型的搜索查询。

每当我期望通过执行类似于谷歌搜索，并访问一些排名靠前的链接来获得答案，并且答案很可能就藏在那些排名靠前的链接中的某个地方时，每当出现这种情况时，我都会毫不犹豫地使用搜索工具，我会直接去perplexity。

这里有一些我常用的互联网搜索查询的例子：

>“今天市场开市吗？”(Isthemarketopentoday?)

例如，在一些特殊的日子，例如节假日，市场可能会休市，我不太确定今天是否开市。所以，perplexity理解当前的时间，它会进行搜索，并快速找出今天是总统日，市场是关闭的。*

>“《白莲花》第三季在哪里拍摄的？”(WhereisWhiteLotusseason3beingfilmed?)

同样，我不确定模型是否会在其知识库中知道这一点，这有点小众。可能互联网上关于它的提及没有那么多。而且这也是最近的信息，所以我不期望模型默认知道。因此，这种问题非常适合使用搜索工具来解决。

>“Vercel是否提供PostgreSQL数据库？”(DoesVercelofferPostgreSQLdatabases?)

这是一个很好的例子，因为这类信息会随着时间而变化。Vercel(一家云计算公司)的产品可能会随着时间推移而发生变化，我想要获取最新的信息。每当我想了解什么是最新的，或者有什么变化时，我都喜欢使用搜索工具，所以我直接去perplexity。

>“苹果明天发布什么？有什么传言？”(WhatisAppleannouncingtomorrow?Whataretherumors?)

同样，这属于最近发生的事件，信息更新速度很快，非常适合使用互联网搜索工具。

>“《单身即地狱》第四季的演员在哪里？”(WhereisthecastofSingle’sInfernoseason4?)

必须知道！这又是一个很好的例子，因为它属于非常新的信息，互联网上可能刚刚出现相关的信息。

>“为什么Palantir的股票会上涨？是什么推动了这种热情？”(WhyisPalantirstockup?What'sdrivingtheenthusiasm?)

股票价格的波动，市场情绪的变化，都是实时更新的信息，模型自身的知识库无法及时反映这些变化，因此，互联网搜索工具是获取这类信息的最佳途径。

>“《文明6》什么时候发布？”(WhenwasCivilization6released?)

确实。这是一个需要互联网搜索才能获取答案的问题。

>“BrianJohnson有没有谈论过他使用的牙膏？”(HasBrianJohnsontalkedaboutwhattoothpasteheuses?)

我很好奇。基本上我很喜欢Brian所做的事情。这个问题有两个特点：第一，它有点深奥，我不太确定互联网上是否大规模存在关于BrianJohnson使用牙膏的信息，并且这些信息是否会成为模型知识的一部分；第二，个人使用的牙膏品牌可能会随着时间而变化，所以我想知道他最近使用什么牙膏。因此，这非常适合使用搜索工具来解决。

>“去越南旅行安全吗？”(IsitsafetotraveltoVietnam?)

旅行安全状况可能会随着时间而变化，受到各种因素的影响，例如国际关系、地区冲突、自然灾害等等。因此，查询旅行安全信息，需要获取最新的信息，互联网搜索工具是理想的选择。

>“我在Twitter上看到了一堆关于USAID的东西，我想知道是怎么回事。”(IsawabunchofthingsaboutUSAIDonTwitterandwantedtoknowwhatwasgoingon.)

我在Twitter上看到了一些趋势性的信息，我很好奇究竟发生了什么。所以我搜索了USAID，然后您可以以各种方式深入了解相关信息。这里的用例类似于我看到一些趋势，我很好奇发生了什么。所以，我经常只是快速搜索发生了什么，然后让模型给我一个关于大致发生了什么的要点，因为很多单独的推文或帖子可能没有完整的上下文，信息碎片化，难以理解全貌。通过互联网搜索，模型可以将来自不同来源的信息整合起来，提供一个更全面、更清晰的概括。

### 互联网搜索：信息获取的强大助手

这些例子，只是我如何使用搜索工具的一些缩影。总而言之，每当您需要获取最新的信息，查询特定领域或小众知识，了解变化信息或趋势动态时，互联网搜索工具都将是您强大的助手，帮助您快速、高效地获取所需的信息。

