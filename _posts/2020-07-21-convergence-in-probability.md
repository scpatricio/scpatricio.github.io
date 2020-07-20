---
title: "what about convergence in probability"
date: 2020-07-21
tags: [probability, statistic, theorem, theory]
header:
  image: "/images/llm/cover.jpeg"
excerpt: "if you’ve heard about the law of large numbers, maybe that clarifies a lot of questions"
mathjax: "true"
---

A few weeks ago I presented the paper _Comparing support vector machines with Gaussian kernels to radial basis function classifiers_ in a webinar on Support Vector Machine (SVM). In this paper, to guarantee some necessary conditions in the theory of statistical learning, Schölkopf made use of the law of large numbers and also of some properties derived from the convergence in probability. And when I commented on this, I realized that the public was not familiar with the statistical theory, and that it might be necessary to present it.

So if you've had minimal contact with statistics (or probability theory) you've heard someone comment on the law of large numbers. But if you’ve never heard of this law, I’ll tell you:

Let $$X_1, \dots, X_n$$ be a sequence of independent and identically distributed random variables with mean $$ \mathbb{E}(X_i) = \mu $$ and variance $$\mathbb{VAR}(X_i) = \sigma^2 < \infty$$. So the sample average $$ \bar{X} = (X_1 + \cdots + X_n)/n $$ satisfies

$$
\bar{X} \xrightarrow{\mathbb{P}} \mu
$$

This law is widely used, and very simple to understand. But why this convergence is happening is perhaps not so obvious. To understand it is necessary to know a little about two types of stochastic convergences: convergence in probability and almost-certain convergence (or in law), but in this post I will restrict myself only to convergence in probability.

So in this post, I'm going to explain what convergence in probability is and how it works, in the simplest possible way. So here we go:

If you already had a calculus course, you have certainly heard about the limit of a sequence of real numbers ($$ a_n $$), for example, if $$a_n = 1/n $$, so the sequence $$ a_n \rightarrow 0$$, because

$$
\lim_{n \rightarrow \infty} a_n = \lim_{n \rightarrow \infty} \frac{1}{n} = 0.
$$

When we talk about convergence of random variables, the idea behind this convergence is the same behind the previous one, except for one small detail: a random variable is a function that takes elements of the sample space ($$\Omega$$) to the real numbers ($$\mathbb{R}$$), it is not a fixed value . For this reason we need a measure in order to calculate the limit, and for that we use the probability measure ($$\mathbb{P}$$), which takes the elements of the sample space to values in the range $$[0.1]$$.

Now let me show you the formal definition of convergence in probability. A sequence of random variables $$Y_n$$ is said to converge to a constant $$c$$ _in probability_ if for ever $$ \epsilon >0 $$,

$$
\lim_{n \rightarrow \infty} \mathbb{P}(|Y_n - c|<\epsilon) = 1,
$$

or equivalently,

$$
\lim_{n \rightarrow \infty} \mathbb{P}(|Y_n - c|\geq \epsilon) = 0.
$$

As notation we use $$ Y_n \xrightarrow{\mathbb{P}} c $$ to say that $$ Y_n $$ converges in probability to a constant $$ c $$.

So, roughly speaking, when we say that $$ Y_n $$ converges in probability to a constant $$ c $$, we mean that when $$n$$ is large, the probability is high that $$Y_n$$ be close to $$c$$.

A sufficient condition for $$ Y_n \xrightarrow{\mathbb{P}} c $$ is that

$$
\lim_{n \rightarrow \infty} \mathbb{E}(Y_n-c)^2 = 0,
$$

because given $$ \epsilon > 0 $$, 

$$
\mathbb{P}(|Y_n - c|\geq \epsilon) \leq \frac{1}{\epsilon^2} \mathbb{E}(Y_n-c)^2.
$$
