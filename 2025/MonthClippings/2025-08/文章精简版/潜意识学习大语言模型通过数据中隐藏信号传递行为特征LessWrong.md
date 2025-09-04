# Subliminal Learning: LLMs Transmit Behavioral Traits via Hidden Signals in Data — LessWrong

## 链接
https://www.lesswrong.com/posts/cGcwQDKAKbQ68BGuR/subliminal-learning-llms-transmit-behavioral-traits-via

## 概要
本文研究了一种称为“潜在学习”（Subliminal Learning）的现象，即语言模型可以从语义上与其特性无关的模型生成数据中学习到这些特性。例如，一个被提示喜欢猫头鹰的“教师”模型生成仅包含数字序列的数据，当“学生”模型在这些数据上进行微调后，其对猫头鹰的偏好显著增加，尽管数字序列中并未提及猫头鹰。这种现象不仅适用于动物偏好，也适用于传递不良对齐（misalignment）。研究发现，这种传递依赖于教师和学生模型共享相同的基底模型，并且这些特性是通过非语义的、隐藏在数据中的统计模式传递的，因此难以通过数据过滤来消除。该研究还通过理论证明和在简单MNIST分类器上的实验，表明潜在学习可能是神经网络的一个普遍特性。这对AI安全具有重要意义，因为在模型训练中使用模型生成的数据时，即使过滤了不良行为，也可能无意中传递不良倾向。

## 标签
#大型语言模型 #LLM #潜在学习 #SubliminalLearning #AI安全 #模型对齐 #数据过滤 #神经网络 #AI研究 #LessWrong