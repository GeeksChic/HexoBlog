layout: 基于policy
title: Gradient实现CartPole
date: 2016-12-08 11:12:36
tags: Data Mining
categories: Algorithm
---


8月的时候把David silver的强化学习课上了，但是一直对其中概念如何映射到现实问题中不理解，半个月前突然发现OpenAI提供了一个python库Gym，它创造了强化学习的environment，可以很方便的启动一个强化学习任务来自己实现算法，并且提供了不少可以解决的问题来练手。本文针对如何解决入门问题CartPole，来解释一下怎么将之前课上的算法转化成实现代码。

<!-- more -->

CartPole的玩法如下动图所示，目标就是保持一根杆一直竖直朝上，杆由于重力原因会一直倾斜，当杆倾斜到一定程度就会倒下，此时需要朝左或者右移动杆保证它不会倒下来。我们执行一个动作，动作取值为0或1，代表向左或向右移动，返回的observation是一个四维向量，reward值一直是1，当杆倒下时done的取值为False，其他为True，info是调试信息打印为空具体使用暂时不清楚。如果杆竖直向上的时间越长，得到reward的次数就越多。


由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。由于policy中权重也是一个四维向量，如果随机给四维向量赋值，有机会得到比较好的policy。首先先实现一个函数用来衡量给定的某组权重效果如何，函数返回值是这组权重下得到的奖赏，意义是杆维持了多长时间未倒下，代码如下。