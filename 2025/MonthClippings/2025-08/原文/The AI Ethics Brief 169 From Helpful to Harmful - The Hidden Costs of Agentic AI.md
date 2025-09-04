---
title: "The AI Ethics Brief #169: From Helpful to Harmful - The Hidden Costs of Agentic AI"
source: "https://brief.montrealethics.ai/p/the-ai-ethics-brief-169-from-helpful?utm_source=post-email-title&publication_id=29999&post_id=167704348&utm_campaign=email-post-title&isFreemail=true&r=50w2ld&triedRedirect=true"
author:
  - "[[Montreal AI Ethics Institute]]"
published: 2025-07-22
created: 2025-08-26
description: "Exploring agentic AI's privacy risks alongside web governance shifts, healthcare automation challenges, and the global AI literacy crisis."
tags:
  - "clippings"
---
### Exploring agentic AI's privacy risks alongside web governance shifts, healthcare automation challenges, and the global AI literacy crisis.

*Welcome to **The AI Ethics Brief**, a bi-weekly publication by the Montreal AI Ethics Institute. We publish **every other Tuesday at 10 AM ET.** Follow MAIEI on [Bluesky](https://bsky.app/profile/mtlaiethics.bsky.social) and [LinkedIn.](https://www.linkedin.com/company/mtlaiethics)*

❤️ [Support Our Work.](https://montrealethics.ai/donate/)

---

### 📌 Editor’s Note

---

#### In this Edition (TL;DR)

- We explore how **agentic AI systems** are breaking down digital privacy boundaries by requiring unprecedented access across apps and platforms, creating what Signal's president calls a "profound" threat to user autonomy while conflating automated task completion with meaningful human choice.
- **Cloudflare's "Content Independence Day" announcement** marks a pivotal shift from opt-out to compensation models for AI training data, defaulting to blocked access for new domains and potentially reshaping how AI companies acquire training content.
- The **UK’s** **NHS AI-enabled healthcare transformation** promises to make every doctor's AI assistant a reality, but automation failures like the Post Office Horizon scandal highlight the risks of rushing AI deployment in critical systems without adequate testing, transparency, and accountability measures.
- In our **AI Policy Corner** series with the **Governance and Responsible AI Lab (GRAIL)** at Purdue University, we examine **Japan's AI Promotion Act**, which represents a strategic bet on light-touch regulation to become "the most AI-friendly country in the world" through voluntary compliance rather than punitive enforcement.
- A **KPMG-University of Melbourne study reveals Canada's alarming AI literacy gap**, ranking 44th out of 47 countries in AI knowledge and training, highlighting the urgent need for coordinated institutional responses and dedicated public AI literacy infrastructure across the country.

**Brief #169 Banner Image Credit:***Web of Influence I* by Elise Racine, featured in *The Bigger Picture*, licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/). View the work on *Better Images of AI* [here](https://betterimagesofai.org/images?artist=EliseRacine&title=WebofInfluenceI).

---

### 🔎 One Question We’re Pondering:

---

![](https://substackcdn.com/image/fetch/$s_!bBvf!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F58100851-1e64-428a-8ba3-6aaa803c6ea9_1456x137.webp)

#### Are we trading away human agency in the name of convenience, and if so, how do we recalibrate our relationship with the technologies that mediate our lives?

Recent developments point to the convergence of several trends: the expansion of agentic AI systems, the integration of AI into enforcement infrastructure, and a shifting understanding of human autonomy in digital environments. As discussed in *[Brief #168](https://brief.montrealethics.ai/i/166771550/are-civil-liberties-at-risk-when-algorithmic-surveillance-becomes-the-new-playbook-for-immigration-enforcement)*[,](https://brief.montrealethics.ai/i/166771550/are-civil-liberties-at-risk-when-algorithmic-surveillance-becomes-the-new-playbook-for-immigration-enforcement) the growing use of algorithmic surveillance in immigration enforcement highlights how these trajectories are beginning to intersect. Together, they raise urgent questions about how technologies built for convenience are quietly reinforcing systems of monitoring and control.

At SXSW, Signal President [Meredith Whittaker](https://techcrunch.com/2025/03/07/signal-president-meredith-whittaker-calls-out-agentic-ai-as-having-profound-security-and-privacy-issues/) warned that so-called agentic AI systems pose “profound” security and privacy concerns. Designed to [perform tasks on a user’s behalf,](https://www.cnbc.com/2025/05/16/ai-travel-agents-planning-future-trip-far-beyond-assistant-status.html) such as booking tickets, messaging contacts, or updating calendars, these systems require elevated permissions across various apps, web browsers, calendars, and communication platforms. Whittaker described this as breaking the **“blood-brain barrier”** between apps and operating systems, creating a seamless but opaque data pipeline between intimate digital behaviours and remote cloud servers.

Implemented at scale, these systems would fundamentally reshape digital privacy boundaries. Agentic systems must access, summarize, and act upon a user’s data, including credit card information, messages, and location history, often with root-level permissions, which can potentially undermine both user consent and platform integrity. Whittaker noted that these operations are unlikely to remain fully on-device and will increasingly rely on cloud processing, creating systemic vulnerabilities to surveillance and data misuse.

[Vilas Dhar,](https://www.politico.com/newsletters/digital-future-daily/2025/07/11/5-questions-for-vilas-dhar-00448529) president and trustee of the Patrick J. McGovern Foundation, adds crucial nuance to this picture. He argues that ["agentic" systems lack genuine human agency,](https://www.politico.com/newsletters/digital-future-daily/2025/07/11/5-questions-for-vilas-dhar-00448529) which involves compassion, kindness, empathy, and protection of our vision for a just world. We've conflated automated task completion with meaningful human choice and expression.

Research from [Stanford’s Institute for Human-Centred AI](https://hai.stanford.edu/news/what-workers-really-want-from-artificial-intelligence) reinforces this concern. Their recent study on worker-AI interaction found that most people prefer AI systems that augment human control, rather than replace it. Workers consistently expressed a desire for AI tools that assist with mundane tasks while preserving decisional autonomy. This preference sharply contrasts with the current deployment path of agentic systems, which often sidestep user input in favour of end-to-end automation.

Taken together, these developments highlight a systemic risk: that technologies positioned as helpful and efficient are simultaneously creating a data substrate that can be co-opted for surveillance and control. In parallel, [enforcement agencies are expanding predictive monitoring programs,](https://brief.montrealethics.ai/i/166771550/are-civil-liberties-at-risk-when-algorithmic-surveillance-becomes-the-new-playbook-for-immigration-enforcement) using social media sentiment, geolocation data, blockchain activity, and communication metadata to identify risk patterns. These two trajectories, agentic AI and predictive enforcement, are not isolated. They are deeply interoperable.

Each interaction with an AI assistant generates behavioural data, which can be used to train future surveillance models. Each API permission granted to a digital agent expands its reach across personal and institutional systems. Without strong data minimization safeguards, algorithmic transparency, and constraints on cross-system integration, the infrastructure built for convenience may serve broader systems of control.

**Preserving meaningful human agency will require technical, legal, and civic interventions:**

1. Adopting privacy-focused defaults and granular consent models.
2. Demanding greater transparency on what agentic systems access and how that data is stored or shared.
3. Supporting legislation that limits interoperability between commercial AI agents and government surveillance systems.

The core challenge involves the kinds of futures we are encoding through architecture. Preserving human agency requires intentionality about the systems we build and the values they reflect.

---

Please share your thoughts with the MAIEI community:

---

### 🚨 Here’s Our Take on What Happened Recently

---

![](https://substackcdn.com/image/fetch/$s_!bBvf!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F58100851-1e64-428a-8ba3-6aaa803c6ea9_1456x137.webp)

#### From Opt-Out to Compensation: The Next Phase of AI Web Governance

[Cloudflare’s July 1, 2025](https://blog.cloudflare.com/content-independence-day-no-ai-crawl-without-compensation/) announcement marks a pivotal shift in the governance of AI access to web content. Often described as the backbone of the modern internet, Cloudflare routes traffic for approximately 20 percent of global web activity. Its decision to block AI bots by default for all new customer domains establishes the first infrastructure-level barrier to automated data extraction.

Framed as [“Content Independence Day,”](https://blog.cloudflare.com/content-independence-day-no-ai-crawl-without-compensation/) the update signals Cloudflare’s intent to move beyond opt-out protections to actively support content licensing models. Whereas the company’s [July 3, 2024 release](https://blog.cloudflare.com/declaring-your-aindependence-block-ai-bots-scrapers-and-crawlers-with-a-single-click/) introduced a one-click tool to block AI bots and scrapers from accessing websites, this new approach envisions a future where content used for AI training is not only protected by default but also compensated directly.

##### 📌 MAIEI’s Take and Why It Matters:

Cloudflare’s policy evolution reflects broader tensions around the economics of AI development. Over the past year, legal and technical debates have converged on the question of how generative models acquire and use training data. As covered in *[Brief #168](https://brief.montrealethics.ai/i/166771550/beyond-fair-use-how-ai-copyright-battles-are-fragmenting-culture)*[,](https://brief.montrealethics.ai/i/166771550/beyond-fair-use-how-ai-copyright-battles-are-fragmenting-culture) U.S. courts have largely upheld the [fair use doctrine](https://fortune.com/2025/06/24/ai-training-is-fair-use-federal-judge-rules-anthropic-copyright-case/) in favour of AI companies, even in cases involving unauthorized content scraping. At the same time, institutions such as the U.S. Copyright Office have experienced significant internal disruption, including the controversial dismissal of its director. These events illustrate the uncertain governance landscape surrounding cultural data in the AI era.

[Saanya Ojha,](https://www.linkedin.com/posts/saanyaojha_yesterday-the-open-internet-got-its-first-activity-7346245331686182914-Xmyl?utm_source=share&utm_medium=member_desktop&rcm=ACoAAADXkdEBkyLWLG_-rtxI2ZGcARnTiGQv6lw) a partner at Bain Capital Ventures, notes that Cloudflare’s new stance [reframes the structure of participation](https://saanyaojha.substack.com/p/the-internet-just-flipped-its-default) in the AI ecosystem, redefining the balance of power between AI companies and the open web.

> **From open to closed.  
> From assumed permission to enforced consent.  
> From passive scraping to active negotiation.**

This shift signals a broader reckoning with the economics of data. Rather than treating content scraping as a neutral technical act, Cloudflare reframes it as a form of uncompensated extraction. By offering web services that default to non-consent, Cloudflare has quietly laid the groundwork for a content licensing infrastructure that prioritizes alignment over automation.

This reframing has direct implications for the future of copyright, consent, and AI development. If the open web adopts similar policies, AI companies building these systems may be forced to negotiate access, pay licensing fees, or build new data partnerships. This could benefit content creators who have long been excluded from the value chains of AI innovation. It also introduces new tensions. Fragmentation across platforms and inconsistent implementation may produce further disparities in whose content is represented in training data and whose is not.

While Cloudflare’s update does not resolve questions of copyright ownership or authorship, it introduces a technical intervention that can shift the incentive landscape. The ability to block AI scraping by default is a step toward more equitable negotiation, but it remains one piece of a broader debate about how cultural data is sourced, protected, and monetized.

Together with recent legal decisions, these changes reveal a digital ecosystem in a state of flux. As AI-generated content becomes more pervasive and indistinguishable from human work, the architecture of consent and the norms of participation are being rewritten in real-time. Cloudflare’s decision, Ojha’s framing, and the evolving role of copyright enforcement all point to the same conclusion: the governance of AI is inseparable from the governance of information itself.

---

![](https://substackcdn.com/image/fetch/$s_!bBvf!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F58100851-1e64-428a-8ba3-6aaa803c6ea9_1456x137.webp)

#### NHS Deploys AI Early Warning System in Maternity Care, But the Bigger Picture Raises Critical Questions

Last month, the [UK's National Health Service (NHS) announced the deployment of an AI early warning system](https://www.theguardian.com/society/2025/jun/30/nhs-will-use-ai-in-warning-system-to-catch-potential-safety-scandals-early) in maternity care, set to launch in November 2025. This system will monitor near real-time hospital data to detect anomalies such as elevated rates of stillbirths, brain injury, or neonatal death, and trigger rapid inspections when necessary. The rollout follows years of reports [citing failures in maternity care delivery](https://www.theguardian.com/society/2022/mar/26/shropshire-maternity-scandal-300-babies-died-or-left-brain-damaged-says-report) across NHS trusts.

The announcement coincides with the UK’s [Fit for the Future – 10 Year Health Plan for England,](https://assets.publishing.service.gov.uk/media/68760ad755c4bd0544dcae33/fit-for-the-future-10-year-health-plan-for-england.pdf) which outlines the digital transformation of NHS services, *“ [making AI every nurse’s and doctor’s trusted assistant,](https://www.gov.uk/government/publications/10-year-health-plan-for-england-fit-for-the-future/fit-for-the-future-10-year-health-plan-for-england-executive-summary#powering-transformation-innovation-to-drive-healthcare-reform:~:text=make%20AI%20every%20nurse%E2%80%99s%20and%20doctor%E2%80%99s%20trusted%20assistant%2C%20saving%20them%20time%20and%20supporting%20them%20in%20decision%20making) saving them time and supporting them in decision making.”*

Key pillars include:

- **Clinical Applications**: AI for diagnostics, decision support, drug discovery, and predictive care
- **Administrative AI**: Scribes, care plan generation, smart hospitals, and single patient records
- **Patient-Facing Tools**: Wearables, triage bots, remote assessments, and 24/7 AI health assistants

The goal is for all NHS hospitals to become “AI-enabled” within the plan’s timeframe, supported by a new [Health Data Research Service (HDRS)](https://www.hdruk.ac.uk/news/a-defining-moment-government-announces-a-health-data-research-service/) and large-scale genomic initiatives, making it the [most AI-enabled care system in the world](https://www.gov.uk/government/publications/10-year-health-plan-for-england-fit-for-the-future/fit-for-the-future-10-year-health-plan-for-england-executive-summary#powering-transformation-innovation-to-drive-healthcare-reform:~:text=preventative%2C%20chronic%20and%20post%2Dacute%20NHS%20treatment%20by%202035).

##### 📌 MAIEI’s Take and Why It Matters:

While AI has the potential to improve patient outcomes and reduce clinician burden, the risks are significant if systems are poorly designed or deployed without transparency and accountability.

**1\. Bias and False Positives/Negatives**

AI systems can replicate and amplify systemic biases. As highlighted in [Brief #102,](https://brief.montrealethics.ai/i/57654525/research-summaries) the U.S. tool [ImpactPro disproportionately misclassified Black patients as lower risk,](https://montrealethics.ai/ai-bias-in-healthcare-using-impactpro-as-a-case-study-for-healthcare-practitioners-duties-to-engage-in-anti-bias-measures/) due to flawed proxies in training data. In the NHS context, false negatives in triage could delay care, while false positives may overwhelm staff and distress patients unnecessarily. Healthcare workers may also develop [automation bias,](https://www.forbes.com/sites/brycehoffman/2024/03/10/automation-bias-what-it-is-and-how-to-overcome-it/) overrelying on AI recommendations even when clinical judgment suggests otherwise, which can potentially compromise patient safety when systems fail.

**2\. Lessons from Automation Failures**

The [UK Post Office Horizon scandal](https://www.bbc.com/news/articles/c1wpp4w14pqo), which wrongly prosecuted over 900 sub-postmasters due to incorrect information provided by the Horizon computer system, and the [Department for Work and Pensions (DWP) algorithm](https://www.thecanary.co/global/world-analysis/2024/06/24/benefit-fraud-dwp-algorithm/), which falsely flagged over 200,000 individuals for fraud, demonstrate how automation without adequate redress mechanisms can destroy lives. The urgency to address maternity care failures should not lead to the rushed deployment of AI without rigorous testing and safeguards.

**3\. Data Governance and Patient Autonomy**

The NHS aims to make patient data widely accessible for innovation, [including to private firms,](https://www.theguardian.com/society/2025/jan/13/ministers-mull-allowing-private-firms-to-make-profit-from-nhs-data-in-ai-push) raising ethical questions. Even anonymized datasets carry [re-identification risks,](https://ieeexplore.ieee.org/document/9779455) especially with longitudinal “cradle-to-grave” coverage. The UK’s [exemption of anonymized data from GDPR](https://www.hra.nhs.uk/planning-and-improving-research/research-planning/how-were-supporting-data-driven-technology/overview-legal-requirements-using-health-and-care-data-development-and-deployment-data-driven-technologies/2-types-health-and-care-information-and-legal-frameworks-protecting-them/#:~:text=regarded%20as%20personal%20data%20\(and%20therefore%20not%20subject%20to%20the%20UK%20GDPR\)) adds urgency to clarify privacy safeguards. Beyond consent, patients need meaningful ways to understand, question, or appeal AI-driven decisions about their care, i.e. true data autonomy, and not just access rights.

**4\. Regulatory Gaps and "Faster" Approval Routes**

While the 10 Year Health Plan promises faster regulatory reviews and ethical governance frameworks, the emphasis on ["faster, risk proportionate and more predictable routes to market" (p. 117)](https://assets.publishing.service.gov.uk/media/68760ad755c4bd0544dcae33/fit-for-the-future-10-year-health-plan-for-england.pdf) raises concerns about potentially lowered safety thresholds or streamlined approval processes that could compromise thorough evaluation. The plan lacks specifics on how deployed AI models will be audited, monitored for bias or [hallucination,](https://montrealethics.ai/careless-whisper-speech-to-text-hallucination-harms/) or corrected when errors occur.

**5\. Regulatory Gaps and "Faster" Approval Routes**

The plan does not specify how AI performance data will be communicated to the public or how liability will be handled when AI recommendations prove wrong. Currently, [individual care providers are responsible](https://transform.england.nhs.uk/information-governance/guidance/consent-and-confidential-patient-information/#:~:text=Your%20organisation%20is%20legally%20obliged%20to%20be%20transparent%20about%20how%20information%20is%20used%20and%20shared.%20It%20should%20make%20information%20readily%20available%20to%20patients%20and%20service%20users%20explaining%20how%20their%20information%20will%20be%20used%2C%20and%20their%20right%20to%20object.%20) for explaining how patient data is used, with NHS guidance stating that organizations are legally obliged to make this information readily available, including patients’ right to object. This may be manageable on a case-by-case basis today, but as AI tools are deployed system-wide, public-facing accountability measures will be needed. Healthcare workers will need clarity on their role and liability when AI systems provide incorrect guidance.

**6\. International Context and Timeline Concerns**

While this initiative could set a global standard, other regions are taking a more cautious approach. The establishes specific requirements for [high-risk AI systems in healthcare,](https://artificialintelligenceact.eu/annex/3/) including [mandatory third-party conformity assessments](https://pmc.ncbi.nlm.nih.gov/articles/PMC11379845/) and access to [regulatory sandboxes](https://artificialintelligenceact.eu/ai-regulatory-sandbox-approaches-eu-member-state-overview/) for testing before market deployment. The November 2025 deployment timeline for maternity care, while addressing urgent safety concerns, may not allow sufficient time for comprehensive testing and staff training across the complex NHS system.

The digitalization of the NHS has the potential to advance medical research and deliver care more efficiently while reducing bureaucratic burden on healthcare workers. However, the deployment of maternity care AI will serve as a critical test case for whether the UK can implement AI responsibly at scale, striking a balance between innovation, patient safety, equity, and public trust.

---

**Did we miss anything? Let us know in the comments below.**

---

### 💭 Insights & Perspectives:

---

![](https://substackcdn.com/image/fetch/$s_!bBvf!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F58100851-1e64-428a-8ba3-6aaa803c6ea9_1456x137.webp)

#### AI Policy Corner: Japan’s AI Promotion Act

This edition of our produced in partnership with the [Governance and Responsible AI Lab (GRAIL)](https://cla.purdue.edu/academic/polsci/research/labs/grail/index.html) at Purdue University, examines **Japan's AI Promotion Act**, enacted in May 2025 as the country's first comprehensive AI legislation. The Act represents Japan's strategic pivot toward becoming "the most AI-friendly country in the world," prioritizing innovation through light-touch regulation that promotes research, development, and utilization of AI technologies. Key provisions include establishing basic principles for AI policy, creating an AI Strategy Headquarters within the Cabinet led by the Prime Minister, and implementing measures to enhance international competitiveness while maintaining domestic research and development (R&D) capabilities. Notably, the Act relies on voluntary compliance without penalties for non-compliance, instead authorizing government investigations and countermeasures when citizen rights are infringed, reflecting Japan's deliberate approach to encourage investment while addressing AI governance through reputational incentives rather than punitive enforcement mechanisms.

> *To dive deeper, **[read the full article here](https://montrealethics.ai/ai-policy-corner-japans-ai-promotion-act/)**[.](https://montrealethics.ai/ai-policy-corner-japans-ai-promotion-act/)*

#### Study shows Canada among least AI literate nations: Canada 44th out of 47 countries in AI literacy

A recent [KPMG-University of Melbourne study](https://kpmg.com/ca/en/home/media/press-releases/2025/06/study-shows-canada-among-least-ai-literate-nations.html) places Canada 44th in AI training and literacy out of 47 countries, and 28th among the 30 advanced economies as defined by the International Monetary Fund (IMF), revealing critical gaps that reinforce [Kate Arthur's call for a national AI literacy strategy](https://substack.com/home/post/p-164015012) and support our case for establishing an independent [Office for Public AI Literacy](https://montrealethics.ai/canadas-minister-of-ai-and-digital-innovation-is-a-historic-first-heres-what-we-recommend/) within the Ministry of AI and Digital Innovation.

![](https://substackcdn.com/image/fetch/$s_!AVnV!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F35f94fd9-08f4-45a4-8a91-41506e79fa46_788x803.png)

The study found that fewer than four in 10 (38%) Canadians reported moderate or high **knowledge of AI,** compared to 52% globally. Additionally, less than one-quarter (24%) of Canadian respondents indicated that they had received **AI training**, compared to 39% globally. When it comes to **trust in AI systems,** Canada ranked 42nd out of 47 countries and 25th out of 30 advanced economies.

For a G7 nation, these rankings represent a national competitiveness challenge that requires coordinated, institutional responses through dedicated public AI literacy infrastructure.

> *To dive deeper, **[read the results of the KPMG-University of Melbourne study here](https://kpmg.com/ca/en/home/media/press-releases/2025/06/study-shows-canada-among-least-ai-literate-nations.html)***

---

### ❤️ Support Our Work

---

![](https://substackcdn.com/image/fetch/$s_!bzIU!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F093f61c1-be66-46ac-b3d2-b5477e121c7f_2000x293.png)

Help us keep ***The AI Ethics Brief*** free and accessible for everyone by becoming a paid subscriber on Substack or making a donation at **[montrealethics.ai/donate](https://montrealethics.ai/donate).** Your support sustains our mission of democratizing AI ethics literacy and honours **[Abhishek Gupta’s](https://montrealethics.ai/open-letter-moving-forward-together/)** legacy.

For corporate partnerships or larger contributions, please contact us at **[support@montrealethics.ai](https://brief.montrealethics.ai/p/)**

---

### ✅ Take Action:

---

Have an article, research paper, or news item we should feature? **Leave us a comment below** — we’d love to hear from you!