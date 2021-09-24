---
title: Self-supervised
subtitle: Self-supervised and Recommendation
layout: "page"
icon: fa-book
order: 4
---

### 介绍一下self-supervised和在推荐中的做法。

截止2021年3月，对SimCLR，MoCo，BYOL，SimSiam，Twins。这几个发展的路线，总结比较好的见[文章](https://github.com/newlei/papernote/blob/main/files_collected/self_supervised/summary_self_supervised.pdf)，对SimSiam分析的不错的见[文章](https://github.com/newlei/papernote/blob/main/files_collected/self_supervised/SimSiam_su.pdf)

简单说一下结论：

- 通过Contrastive learning来实现self-supervised能够达到很好的效果。但是利用Contrastive learning是需要正负样本的，SimCLR和MoCo中便是如此，且认为负样本非常重要，需要足够的负样本。这点在一些视觉任务中也到到了验证。

- BYOL就开始去除负样本，认为不使用负样本也得达到非常好的效果。SimSiam是在BYOL基础上做减法。同样说明了self-supervised中不需要负样本依旧可以。但是不使用负样本，模型就会有陷入平凡解的风险。解决方法是：predictor模块，避免了直接拉近正样本对，对于梯度的直接回传，让模型陷入平凡解。

- Twins从embedding本身出发，而不是样本出发。约束不同视角下特征的相关矩阵接近恒等矩阵，即让不同的维度的特征尽量表示不同的信息，从而提升特征的表征能力。Twins相当于了需要大的维度特征（8192-dim）来做，SimCLR是需要大的batchsize（大的样本）。相当于把InfoNCE里面batch样本index（b）换成这个方法里的dimension index (i)。



CVPR2020 Tutorial，介绍一下大致情况。
https://abursuc.github.io/slides//2021-cvpr-ssl/ssl-intro.html#1
CVPR2020 Tutorial，介绍很细致。
https://abursuc.github.io/slides/2020_tutorial_cvpr//self_supervised_learning.html#1

SimCLR，MoCo，BYOL，SimSiam，Twins。这几个模型，从前到后是经典的几篇文章，展示了发展脉络。

Deep Graph Infomax代码和论文，用于Graph数据
https://github.com/PetarV-/DGI

推荐中相关文章3篇
Self-supervised Graph Learning for Recommendation
https://arxiv.org/pdf/2010.10783.pdf

S3-Rec: Self-Supervised Learning for Sequential
Recommendation with Mutual Information Maximization
https://dl.acm.org/doi/pdf/10.1145/3340531.3411954

Self-Supervised Reinforcement Learning for
Recommender Systems
https://dl.acm.org/doi/pdf/10.1145/3397271.3401147

分类总结了各种方向上的论文
https://github.com/jason718/awesome-self-supervised-learning




