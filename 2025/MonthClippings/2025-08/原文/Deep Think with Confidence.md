---
title: "Deep Think with Confidence"
source: "https://arxiviq.substack.com/p/deep-think-with-confidence"
author:
  - "[[Grigory Sapunov]]"
published: 2025-08-24
created: 2025-08-26
description: "DeepConf: Scaling LLM Reasoning with Confidence, Not Just Compute"
tags:
  - "clippings"
---
### DeepConf: Scaling LLM Reasoning with Confidence, Not Just Compute

**Authors:***Yichao Fu, Xuewei Wang, Yuandong Tian, Jiawei Zhao*  
**Paper:**[https://arxiv.org/abs/2508.15260](https://arxiv.org/abs/2508.15260)  
**Code:**[https://jiaweizzhao.github.io/deepconf](https://jiaweizzhao.github.io/deepconf)

## TL;DR

**WHAT was done?** The authors introduce Deep Think with Confidence (DeepConf), a test-time inference method that enhances the reasoning capabilities of Large Language Models (LLMs). Instead of treating all generated reasoning paths equally, DeepConf leverages the model's internal log-probabilities to derive localized confidence scores. It operates in two modes: an *offline* mode that filters completed reasoning traces and applies confidence-weighted majority voting, and a novel *online* mode that dynamically terminates the generation of low-confidence traces mid-stream. This is achieved without any additional model training or complex hyperparameter tuning.

**WHY it matters?** This work addresses the critical challenge of high computational cost and diminishing returns in popular test-time scaling methods like self-consistency. By intelligently filtering out low-quality reasoning and enabling early stopping, DeepConf achieves state-of-the-art accuracy (e.g., 99.9% on the AIME 2025 benchmark with GPT-OSS-120B) while dramatically reducing the number of generated tokens—by up to 84.7%. This makes high-performance LLM reasoning more efficient, scalable, and economically viable, paving the way for more practical deployment in real-world applications.

![](https://substackcdn.com/image/fetch/$s_!EqLQ!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc14868cf-d1c3-44ff-951a-19f9b9c07ee7_1280x896.png)

## Details

### The Challenge: Brute-Force Reasoning is Inefficient

Large Language Models (LLMs) have shown remarkable progress in complex reasoning tasks, largely thanks to test-time scaling techniques like self-consistency ([https://arxiv.org/abs/2203.11171](https://arxiv.org/abs/2203.11171), more on this and related techniques [here](https://gonzoml.substack.com/p/chain-of-thought-tree-of-thought)). The principle is simple: generate multiple reasoning paths ("thoughts") for a single problem and take the majority answer. While effective, this brute-force strategy has significant drawbacks—it's computationally expensive, leads to diminishing returns, and treats every thought as equally valid. This challenge has spurred a wave of research into more efficient reasoning. While methods like Early-Stopping Self-Consistency ([https://arxiv.org/abs/2401.10480](https://arxiv.org/abs/2401.10480)) also terminate generation early, DeepConf's distinction lies in its use of localized, internal confidence signals rather than just answer convergence.

This paper introduces Deep Think with Confidence (DeepConf), a method that shifts the paradigm from "thinking more" to "thinking smarter." It equips LLMs with a form of introspection, allowing them to assess the quality of their own reasoning paths and discard the unpromising ones.

### Methodology: Quantifying Confidence to Guide Reasoning

DeepConf's core innovation lies in its use of model-internal signals to quantify the quality of a reasoning trace. The method requires no retraining and is built upon several novel confidence metrics designed to be more discerning than simple average token probability.

#### Fine-Grained Confidence Metrics

The authors move beyond a single, global confidence score for an entire trace, arguing that such measures can mask critical breakdowns in the reasoning process. Instead, they introduce several localized metrics derived from **Token Confidence** (*C\_i*), defined as the negative average log-probability of the top-k tokens at each step (Equation 2).

![](https://substackcdn.com/image/fetch/$s_!diyF!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F96518c4b-1089-4d5e-9a88-47689f55e4dd_817x195.png)

These include:

- **Group Confidence (*****C\_G\_i*****)**: The average token confidence over a sliding window of recent tokens (e.g., 2048), providing a smoother, localized signal of reasoning quality (Equation 4).
	![](https://substackcdn.com/image/fetch/$s_!Yrqv!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F65eb9c17-c5dd-450b-ae6a-df7dce476d56_548x65.png)
- **Bottom 10% Group Confidence (*****C\_bottom-10*****)**: The mean of the
	bottom 10% of group confidences within the trace (Equation 5).
	![](https://substackcdn.com/image/fetch/$s_!eYvq!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Faf8aaa2c-ceb1-4874-9b53-b1ada7623ac4_560x66.png)
- **Lowest Group Confidence (*****C\_least*****)**: The confidence of the single least-confident group in the entire trace. This metric is particularly effective at flagging traces with a significant "moment of confusion" (Equation 6).
	![](https://substackcdn.com/image/fetch/$s_!oB9k!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F66c4cb13-c880-409e-bd8a-7f66e129d77a_536x46.png)
- **Tail Confidence (*****C\_tail*****)**: The average confidence over the last portion of the trace, based on the observation that the final steps of reasoning are often the most critical for reaching a correct conclusion (Equation 7).
	![](https://substackcdn.com/image/fetch/$s_!j-Cw!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F04a19286-ddb9-4f4a-85ce-00958b4d9baf_552x62.png)

Experiments show these localized metrics are significantly better at separating correct and incorrect reasoning traces than a simple global average (Figure 2).

![](https://substackcdn.com/image/fetch/$s_!suCV!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F0322999e-dc45-40e6-9d6c-7b559639cae7_1100x303.png)

#### Dual Modes of Operation: Offline and Online

DeepConf operates in two distinct modes to offer flexibility for different use cases:

1. **Offline Thinking with Confidence**: In this mode (Algorithm 1), all reasoning traces for a given problem are generated first.
	![](https://substackcdn.com/image/fetch/$s_!unqg!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc7e52ac7-de82-4224-9e30-3f6e53d22f7b_1069x300.png)
	DeepConf then applies a two-step refinement process. First, it performs **Confidence Filtering**, selecting only the top- *η* percent of traces based on one of the confidence metrics. Second, it uses **Confidence-Weighted Majority Voting**, where the vote from each surviving trace is weighted by its confidence score. This ensures that answers supported by high-quality reasoning are given more prominence.
	![](https://substackcdn.com/image/fetch/$s_!B2su!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F18f2157f-942d-41af-a615-fd1df099614d_1380x791.png)
2. **Online Thinking with Confidence**: This more groundbreaking mode (Algorithm 2) optimizes efficiency in real-time through a dynamic pruning mechanism:
	![](https://substackcdn.com/image/fetch/$s_!hcVH!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F345120d8-7d3b-4b46-836a-cd5619a617c2_1076x489.png)
	- **Offline Warmup & Thresholding**: For each new problem, a small set of initial traces (e.g., 16) is generated to calibrate a dynamic **stopping threshold (*****s*****)**. This threshold is determined by the confidence of the weakest trace among the top-performing ones in the warmup set (e.g., the 90th percentile of `Lowest Group Confidence` scores).
	- **Real-time Early Stopping**: For all subsequent traces, the model’s local `Group Confidence` is monitored at each step. If it ever drops below the pre-computed threshold *s*, the generation of that trace is immediately terminated, saving significant computation on a path likely to fail (Figure 4).
		![](https://substackcdn.com/image/fetch/$s_!7x2p!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F3aaba6ed-311a-400c-bb26-6329c337a243_1104x532.png)
	- **Adaptive Sampling**: To further trim costs, trace generation halts entirely once the leading answer achieves a strong consensus (e.g., its share of votes exceeds a 95% threshold), preventing the model from generating more traces than necessary.

### Experimental Results: A Leap in Accuracy and Efficiency

The authors conduct an extensive evaluation across five challenging reasoning benchmarks (AIME, BRUMO, HMMT, GPQA) and five powerful open-source models (DeepSeek, Qwen3, GPT-OSS). The results are striking.

![](https://substackcdn.com/image/fetch/$s_!tb8Z!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc5ce1f22-0ca9-4046-89d0-0b7bb1ca3368_825x521.png)

**Exceptional Accuracy:** In offline mode, DeepConf with aggressive filtering (retaining the top 10% most confident traces) consistently outperforms standard majority voting. The headline result is its performance on AIME 2025 with GPT-OSS-120B, where it achieves **99.9% accuracy**, a significant jump from the 97.0% of standard majority voting and effectively saturating the benchmark (Figure 1, Table 1). Similar substantial gains are seen across other models, such as DeepSeek-8B on AIME25 (82.3% → 87.4%).

![](https://substackcdn.com/image/fetch/$s_!SXmx!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F34a6e157-5008-4442-92d5-87db03f85351_544x314.png)

**Dramatic Efficiency Gains:** The online mode demonstrates remarkable efficiency. Compared to generating the full set of traces for majority voting, DeepConf reduces the total number of generated tokens by **43-79%** across most tasks (Table 2).

![](https://substackcdn.com/image/fetch/$s_!0CVP!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb09901cc-897c-4859-8669-240d4d31c662_1096x559.png)

For GPT-OSS-120B on AIME25, the token reduction reaches an incredible **84.7%**. This reduction often comes with an *increase* in accuracy. For example, with DeepSeek-8B on AIME24, DeepConf-low reduces tokens by 77.9% while improving accuracy by 5.8 percentage points (Figure 7).

![](https://substackcdn.com/image/fetch/$s_!BE6g!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F5715b6a4-ed3d-46db-be8f-616fe5e04e99_1108x312.png)

Furthermore, extensive ablation studies in the paper's appendix confirm the method's robustness, showing that performance gains are not overly sensitive to the specific size of the warmup set or filtering percentage.

### Broader Impact and Future Directions

DeepConf is a powerful example of **test-time scaling**, a paradigm focused on eliciting better performance from existing models at inference time rather than through more expensive retraining. By making this test-time computation vastly more efficient, the paper shows that we can achieve the benefits of 'thinking more' without the prohibitive costs, offering a practical path to scaling LLM intelligence.

The authors identify the primary limitation as the "confidently wrong" problem—cases where a model is highly confident in an incorrect answer, which can mislead the filtering process. Future work will focus on improving confidence calibration techniques and extending the DeepConf framework to guide policy exploration in reinforcement learning.

### Conclusion

"Deep Think with Confidence" presents a simple, powerful, and immediately applicable method for optimizing LLM reasoning. By shifting the focus from brute-force generation to confidence-guided selection and early termination, it delivers a rare combination of improved accuracy and vastly superior computational efficiency. The paper provides a well-written, thoroughly evaluated contribution that offers a practical solution to one of the key challenges in scaling LLM intelligence. It is a valuable piece of work that highlights a promising path toward more scalable, reliable, and cost-effective AI reasoning systems.