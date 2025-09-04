---
title: "The AI Ethics Brief #171: The Contradictions Defining AI's Future"
source: "https://brief.montrealethics.ai/p/the-ai-ethics-brief-171-the-contradictions?utm_source=post-email-title&publication_id=29999&post_id=170160724&utm_campaign=email-post-title&isFreemail=true&r=50w2ld&triedRedirect=true&utm_medium=email"
author:
  - "[[Montreal AI Ethics Institute]]"
published: 2025-08-19
created: 2025-08-26
description: "OpenAI's strategic reversals, why some philosophers say \"ChatGPT is bullshit,\" and the battle between protection and privacy."
tags:
  - "clippings"
---
### OpenAI's strategic reversals, why some philosophers say "ChatGPT is bullshit," and the battle between protection and privacy.

*Welcome to **The AI Ethics Brief**, a bi-weekly publication by the Montreal AI Ethics Institute. We publish **every other Tuesday at 10 AM ET.** Follow MAIEI on [Bluesky](https://bsky.app/profile/mtlaiethics.bsky.social) and [LinkedIn.](https://www.linkedin.com/company/mtlaiethics)*

❤️ [Support Our Work.](https://montrealethics.ai/donate/)

---

### 📌 Editor’s Note

---

#### In this Edition (TL;DR)

- **One Question We're Pondering:** Are we witnessing the beginning of the end for large language models as we know them? We examine GPT-5's mixed reception, NVIDIA and Georgia Tech researchers arguing for smaller specialized models, and University of Glasgow philosophers' peer-reviewed argument that "ChatGPT is bullshit," revealing fundamental questions about AI's relationship with truth.
- **OpenAI Returns to Open Source:** We analyze OpenAI's first open-source models since GPT-2, examining the strategic contradiction of releasing capable models anyone can modify after years of justifying closed development for safety, with energy efficiency insights from Hugging Face researcher Sasha Luccioni.
- **YouTube's AI Age Verification:** We explore the platform's new machine learning technology that predicts user age to block inappropriate content, examining the tension between child protection and privacy rights.
- **AI Copyright Battles Continue:** Our *AI Policy Corner* with GRAIL at Purdue University examines the U.S. Copyright Office’s evolving guidance on works containing AI-generated material, including its January 2025 report and over 1,000 works containing some level of AI-generated material. Building on our coverage in [Brief #168](https://brief.montrealethics.ai/i/166771550/beyond-fair-use-how-ai-copyright-battles-are-fragmenting-culture) on court rulings on fair use and [Brief #169](https://brief.montrealethics.ai/i/167704348/from-opt-out-to-compensation-the-next-phase-of-ai-web-governance) on Cloudflare’s data governance shift, this development highlights how [copyright](https://chatgptiseatingtheworld.com/2025/08/13/updated-map-of-us-copyright-lawsuits-v-ai-companies-aug-12-2025/) has become the central arena where courts, infrastructure providers, and regulators are negotiating the future of cultural production in the age of generative AI.
- **Can Chatbots Replace Human Mental Health Support?** Sabia Irfan examines the growing use of AI chatbots for mental health support, highlighting both accessibility benefits and concerns about emotional over-reliance and clinical oversight.

**What connects these stories:** The contradictions at the heart of AI development—between closed and open systems, revolutionary promises and incremental progress, protecting users while respecting privacy—revealing an industry grappling with its own stated values.

**Brief #171 Banner Image Credit:** *Behaviour Power* by Bart Fish & Power Tools of AI, featured in [Better Images of AI,](https://betterimagesofai.org/images?artist=BartFish&title=BehaviourPower) licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).

---

### 🔎 One Question We’re Pondering:

---

![](https://substackcdn.com/image/fetch/$s_!bBvf!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F58100851-1e64-428a-8ba3-6aaa803c6ea9_1456x137.webp)

#### Are we witnessing the beginning of the end for large language models as we know them?

The release of [OpenAI's GPT-5](https://techcrunch.com/2025/08/07/openais-gpt-5-is-here/) on August 7 earlier this month was supposed to mark another triumphant milestone in our era of perpetual AI improvement. CEO Sam Altman hyped it as offering ["PhD-level intelligence"](https://openai.com/index/introducing-gpt-5/) and positioned it as a significant leap forward. Yet the reception has been notably mixed, with [thousands of users on Reddit](https://www.tomsguide.com/ai/chatgpt/chatgpt-5-users-are-not-impressed-heres-why-it-feels-like-a-downgrade) calling it ["horrible"](https://medium.com/data-science-in-your-pocket/gpt-5-openais-worst-release-yet-421558ad89f4) and ["underwhelming."](https://garymarcus.substack.com/p/gpt-5-overdue-overhyped-and-underwhelming)

Critics have noted that it provides shorter, less nuanced responses while [limiting user access](https://finance.yahoo.com/news/openai-gpt-5-met-mixed-212741623.html) to previously available models. Ironically, some of these complaints may stem from OpenAI's efforts to reduce what they call "sycophancy," the tendency for AI systems to be excessively agreeable, flattering, or validating rather than providing honest, balanced responses. While OpenAI claims this makes GPT-5 more truthful, many users are experiencing it as a loss of the warmth and personality they valued in earlier versions.

This lukewarm reception comes at a fascinating inflection point. While we chase ever-larger models, researchers at NVIDIA and Georgia Tech are making the case that we're heading in the wrong direction entirely. Their preprint paper ["Small Language Models are the Future of Agentic AI"](https://arxiv.org/abs/2506.02153) argues that for most practical applications—especially the repetitive, specialized tasks that AI agents actually perform—smaller, more efficient models are not just adequate but superior.

Which brings us to a more fundamental question about the nature of these systems altogether. In their peer-reviewed paper ["ChatGPT is bullshit"](https://doi.org/10.1007/s10676-024-09775-5) published in *Ethics and Information Technology*, philosophers Michael Townsen Hicks, James Humphries, and Joe Slater at the University of Glasgow build on Harry Frankfurt's influential work *[On Bullshit](https://en.wikipedia.org/wiki/On_Bullshit)* to argue that large language models aren't trying to convey truth at all, they're designed to produce convincing-sounding text regardless of accuracy.

Unlike lying, which requires intent to deceive, or what the industry euphemistically calls ["AI hallucinations,"](https://techcrunch.com/2025/05/22/anthropic-ceo-claims-ai-models-hallucinate-less-than-humans/) this represents something more concerning: systematic indifference to truth itself. As the authors put it, these systems "cannot themselves be concerned with truth" and are fundamentally "indifferent to the truth of their outputs." This matters because framing AI errors as mere "hallucinations" suggests the systems are trying but failing to perceive reality correctly, when in fact, they're not designed to care about accuracy at all.

Perhaps the mixed reviews of GPT-5 aren't a bug but a feature, a sign that we're finally recognizing these tools for what they actually are: sophisticated text generators optimized for plausibility rather than truth, whose utility may be better served by smaller, specialized models rather than ever-larger general-purpose ones.

---

Please share your thoughts with the MAIEI community:

---

### 🚨 Here’s Our Take on What Happened Recently

---

![](https://substackcdn.com/image/fetch/$s_!bBvf!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F58100851-1e64-428a-8ba3-6aaa803c6ea9_1456x137.webp)

#### OpenAI Returns to Open Source with GPT-OSS Release

OpenAI released [GPT-OSS](https://openai.com/index/introducing-gpt-oss/), their first open-source models since GPT-2 in 2019. The release includes multiple model sizes designed to be [energy-efficient](https://huggingface.co/blog/sasha/gpt-oss-energy) and capable of running on consumer hardware, [available for download on Hugging Face](https://huggingface.co/openai/gpt-oss-120b). This marks a significant shift for a company that has moved increasingly toward [closed, proprietary systems since GPT-3](https://venturebeat.com/ai/openai-returns-to-open-source-roots-with-new-models-gpt-oss-120b-and-gpt-oss-20b/). The announcement of GPT-OSS on August 5 came in the same week as GPT-5's launch on August 7.

##### 📌 MAIEI’s Take and Why It Matters:

This release represents a notable contradiction in OpenAI's strategy. For years, the company justified keeping powerful models closed by citing [safety concerns](https://openai.com/safety/), yet here they're releasing capable models that anyone can download and modify.

The timing alongside GPT-5's mixed reception suggests this reflects competitive pressures rather than strategic planning. As companies like [Meta](https://ai.meta.com/llama/) and [Mistral](https://mistral.ai/news/mistral-small-3-1) push open-source alternatives, OpenAI appears to be recognizing that maintaining relevance in an increasingly open ecosystem may matter more than controlling access to powerful models.

More significantly, this aligns with growing arguments that [smaller, specialized models may be the future](https://arxiv.org/abs/2506.02153). GPT-OSS represents OpenAI acknowledging that not every use case requires flagship models, potentially signalling a more nuanced approach where different model sizes serve different needs.

Beyond strategic considerations, the environmental implications are significant. As Hugging Face researcher Sasha Luccioni demonstrates in [her analysis](https://huggingface.co/blog/sasha/gpt-oss-energy), GPT-OSS models consume substantially less energy while maintaining competitive performance. The cumulative impact of millions of users running models locally rather than through energy-intensive cloud infrastructure could be considerable.

If OpenAI is comfortable releasing these models openly, it raises questions about whether their previous arguments for closed development were primarily about safety or about maintaining competitive advantage. As the industry faces mounting pressures around [energy consumption](https://fortune.com/2025/08/14/data-centers-china-grid-us-infrastructure/), [shifting policy priorities,](https://www.lawfaremedia.org/article/liberal-democracies-are-retreating-from-ai-safety) and [evolving regulatory frameworks,](https://www.techpolicy.press/one-year-on-eu-ai-act-collides-with-new-political-reality/) GPT-OSS suggests that openness may become less of an ideological choice and more of a business necessity.

---

![](https://substackcdn.com/image/fetch/$s_!bBvf!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F58100851-1e64-428a-8ba3-6aaa803c6ea9_1456x137.webp)

#### YouTube’s AI-Powered Age Verification: An Invasion of Privacy or a Mechanism to Protect Children?

YouTube began testing [machine learning age-verification technology](https://apnews.com/article/youtube-video-age-verification-system-1ce99a7089b33e88dc76e49945ded186) on a subset of American users this past week. The technology will predict a user’s age according to several factors, including [video preferences and the account creation date](https://blog.youtube/news-and-events/extending-our-built-in-protections-to-more-teens-on-youtube/). If the user is inferred to be under the age of 18, they will be blocked access to content deemed inappropriate, receive well-being reminders, and not be sent targeted ads. In the event of incorrect age estimation, users may prove they are an adult by providing their credit card or a government ID. If the trial is successful, this technology, which has already been implemented in other markets, will expand throughout the United States.

##### 📌 MAIEI’s Take and Why It Matters:

YouTube’s age verification measures are only one example of a global trend. For instance, earlier this summer, the United States Supreme Court [ruled in favour](https://apnews.com/article/supreme-court-porn-age-verification-texas-12a73197796fe8c4bef0d888259543cf) of a Texas law requiring identification to view sexually explicit material with the aim of protecting children from viewing such content. Moreover, the European Commission is entering a pilot phase of testing [online age verification measures](https://digital-strategy.ec.europa.eu/en/policies/eu-age-verification) that will be compatible with new [European Union Digital Identity Wallets](https://digital-strategy.ec.europa.eu/en/policies/eudi-regulation).

These measures are highly controversial. They raise digital privacy concerns in an era of increased government surveillance and potentially [infringe on internet free speech](https://www.aclu.org/press-releases/fsc-paxton-age-verification). Data breaches are also a serious concern, such as in the UK, where many sites are utilizing third-party platforms to meet the age verification requirements of the [Online Safety Act](https://www.eff.org/deeplinks/2025/08/no-uks-online-safety-act-doesnt-make-children-safer-online). YouTube and many third-party verification platforms pledge that [data is tightly secured](https://www.clrn.org/how-do-you-confirm-your-age-on-youtube/?utm_source=chatgpt.com) to protect against leaks. However, such measures are often inefficient. For instance, the privacy of [72,000 images on Tea](https://www.nytimes.com/2025/07/26/us/tea-safety-dating-app-hack.html) (a controversial women-only app through which users share safety information and perspectives on potential male partners) was compromised, many of which were gender verification images that were supposed to be deleted quickly after verification.

On the other hand, such regulations are important to protect the well-being of children, preventing them from viewing sexually explicit, [violent, and otherwise harmful content](https://services.google.com/fh/files/misc/vibe-expansion-gtm-casestudy.pdf), in addition to guarding against predatory advertising methods. Platforms such as YouTube have a history of hosting material aimed at exploiting minors. A famous example of this phenomenon is the [Elsagate scandal](https://en.wikipedia.org/wiki/Elsagate), through which platforms utilized “educational” themes and popular children’s characters from Disney and Nick Jr. to slip lewd and explicit content through the filtering mechanisms of YouTube Kids. For instance, a video with the [stated purpose of facilitating the “learning and development of children!”](https://www.nytimes.com/2017/11/04/business/media/youtube-kids-paw-patrol.html) depicts Paw Patrol characters in a strip club.

Age verification is a difficult issue as it puts two important values head-to-head: digital privacy and protecting children from harm. Promising advancements such as [Zero Knowledge Proof (ZKP) technology adopted by Google](https://www.theblock.co/post/352865/google-wallet-integrates-zk-proofs-a-tech-incubated-by-crypto-industry) and potentially [EU Digital Identity Wallets](https://eu-digital-identity-wallet.github.io/eudi-doc-architecture-and-reference-framework/2.4.0/discussion-topics/g-zero-knowledge-proof/) may serve as future solutions, but it is very difficult to fully protect one’s privacy online. Moving forward, effective solutions must balance protecting user privacy with safeguarding children from harm.

---

**Did we miss anything? Let us know in the comments below.**

---

### 💭 Insights & Perspectives:

---

![](https://substackcdn.com/image/fetch/$s_!bBvf!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F58100851-1e64-428a-8ba3-6aaa803c6ea9_1456x137.webp)

#### AI Policy Corner: U.S. Copyright Guidance on Works Created with AI

This edition of our produced in partnership with the [Governance and Responsible AI Lab (GRAIL)](https://cla.purdue.edu/academic/polsci/research/labs/grail/index.html) at Purdue University, explores how the U.S. Copyright Office’s 2023 guidance on works containing AI-generated material is shaping the legal landscape. The piece focuses on the human authorship requirement, clarifying that only work reflecting a human’s original creative input is eligible for protection. It also outlines the threshold for “sufficient human authorship,” noting that prompt-based generation typically does not qualify. A follow-up report issued in January 2025 reaffirms that existing copyright law remains flexible enough to apply to generative AI, while emphasizing the need for discernible human contribution. Since the guidance was issued, the Office has registered over 1,000 works containing some level of AI-generated material, reflecting how its evolving interpretation is being tested in practice and shaping ongoing debates around authorship, ownership, and creative accountability.

> *To dive deeper, **[read the full article here](https://montrealethics.ai/ai-policy-corner-u-s-copyright-guidance-on-works-created-with-ai/)**[.](https://montrealethics.ai/ai-policy-corner-u-s-copyright-guidance-on-works-created-with-ai/)*

#### Can Chatbots Replace Human Mental Health Support?

In this op-ed, Sabia Irfan examines the growing use of AI chatbots for mental health support, highlighting a 2025 survey in which nearly half of Americans reported using large language models for psychological support, with 75 percent seeking help for anxiety and nearly 60 percent for depression. This marks a dramatic shift from a 2021 survey by Woebot, which found that only 22 percent of adults had used a mental health chatbot, though 47 percent expressed willingness to try one. While these tools offer accessible, non-judgmental support, Irfan raises concerns about emotional over-reliance, lack of clinical oversight, and the risks of unsafe responses, including a recent case involving Character.ai. The piece also highlights recent legislation in Illinois that restricts the use of AI in mental health services, highlighting the need for clearer boundaries, stronger safeguards, and professional involvement in the development of AI therapeutic tools.

> *To dive deeper, **[read the full article here](https://montrealethics.ai/can-chatbots-replace-human-mental-health-support/)**[.](https://montrealethics.ai/can-chatbots-replace-human-mental-health-support/)*

---

### ❤️ Support Our Work

---

![](https://substackcdn.com/image/fetch/$s_!bzIU!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F093f61c1-be66-46ac-b3d2-b5477e121c7f_2000x293.png)

Please help us keep ***The AI Ethics Brief*** free and accessible for everyone by becoming a paid subscriber on Substack or making a donation at **[montrealethics.ai/donate](https://montrealethics.ai/donate).** Your support sustains our mission of democratizing AI ethics literacy and honours **[Abhishek Gupta’s](https://montrealethics.ai/open-letter-moving-forward-together/)** legacy.

For corporate partnerships or larger contributions, please contact us at **[support@montrealethics.ai](https://brief.montrealethics.ai/p/)**

---

### ✅ Take Action:

---

Have an article, research paper, or news item we should feature? **Leave us a comment below** — we’d love to hear from you!