---
title: HelloWorld
date: 2016-12-08 03:09:55
tags: Machine Learning
categories: Math
---

#This is HelloWorld
8月的时候把David Silver的强化学习课上了，但是一直对其中概念如何映射到现实问题中不理解，半个月前突然发现OpenAI提供了一个python库Gym，它创造了强化学习的environment，可以很方便的启动一个强化学习任务来自己实现算法，并且提供了不少可以解决的问题来练手。本文针对如何解决入门问题CartPole，来解释一下怎么将之前课上的算法转化成实现代码。本文主要阐述了对生成式对抗网络的理解，首先谈到了什么是对抗样本，以及它与对抗网络的关系，然后解释了对抗网络的每个组成部分，再结合算法流程和代码实现来解释具体是如何实现并执行这个算法的，最后通过给出一个基于对抗网络改写的去噪网络，效果虽然挺差的，但是还是挺有意思的。

<!-- more -->

本文主要阐述了对生成式对抗网络的理解，首先谈到了什么是对抗样本，以及它与对抗网络的关系，然后解释了对抗网络的每个组成部分，再结合算法流程和代码实现来解释具体是如何实现并执行这个算法的，最后给出一个基于对抗网络改写的去噪网络运行的结果，效果虽然挺差的，但是有些地方还是挺有意思的。


14年的时候Szegedy在研究神经网络的性质时，发现针对一个已经训练好的分类模型，将训练集中样本做一些细微的改变会导致模型给出一个错误的分类结果，这种虽然发生扰动但是人眼可能识别不出来，并且会导致误分类的样本被称为对抗样本，他们利用这样的样本发明了对抗训练(adversarial training)，模型既训练正常的样本也训练这种自己造的对抗样本，从而改进模型的泛化能力[1]。如下图所示，在未加扰动之前，模型认为输入图片有57.7%的概率为熊猫，但是加了之后，人眼看着好像没有发生改变，但是模型却认为有99.3%的可能是长臂猿。


这个问题乍一看很像过拟合，在Goodfellow在15年[3]提到了其实模型欠拟合也能导致对抗样本，因为从现象上来说是输入发生了一定程度的改变就导致了输出的不正确，例如下图一，上下分别是过拟合和欠拟合导致的对抗样本，其中绿色的o和x代表训练集，红色的o和x即对抗样本，明显可以看到欠拟合的情况下输入发生改变也会导致分类不正确(其实这里我觉得有点奇怪，因为图中所描述的对抗样本不一定就是跟原始样本是同分布的，感觉是人为造的一个东西，而不是真实数据的反馈)。在[1]中作者觉得这种现象可能是因为神经网络的非线性和过拟合导致的，但Goodfellow却给出了更为准确的解释，即对抗样本误分类是因为模型的线性性质导致的，说白了就是因为
