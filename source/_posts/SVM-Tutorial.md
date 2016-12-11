---
title: SVM Tutorial
date: 2016-12-10 19:54:55
tags: Algorithm
categories: Data Science
---


SVMs (Support Vector Machines) are a useful technique for data classification. Although SVM is considered easier to use than Neural Networks, users not familiar with it often get unsatisfactory results at First. Here we outline a cookbook" approach which usually gives reasonable results.

<!-- more -->


Note that this guide is not for SVM researchers nor do we guarantee you will achieve the highest accuracy. Also, we do not intend to solve challenging or difficult problems. Our purpose is to give SVM novices a recipe for rapidly obtaining acceptable results. Although users do not need to understand the underlying theory behind SVM, we briey introduce the basics necessary for explaining our procedure. A classification task usually involves separating data into training and testing sets. Each instance in the training set contains one \target value" (i.e. the class labels) and several attributes" (i.e. the features or observed variables). The goal of SVM is to produce a model (based on the training data) which predicts the target values of the test data given only the test data attributes \eqref{label1}.
$$f(x)=x+3$$
另一个问题在于，当比较小的时候，这种方式是不可行的。
$$a = x^2 - y^3 \tag{1}\label{label1}$$
另一个问题在于，当比较小的时候，这种方式是不可行的。
$$k(x_1,x_2)=(\langle x_1,x_2 \rangle+1)^2$$

