---
title: "what about convergence in probability?"
date: 2020-07-21
tags: [probability, statistic, theorem, theory]
header:
  image: "/images/llm/cover.jpeg"
excerpt: "if you’ve heard about the law of large numbers, maybe that clarifies a few questions"
mathjax: "true"
---

A few weeks ago I presented the paper _Comparing support vector machines with Gaussian kernels to radial basis function classifiers_ in a webinar on Support Vector Machine (SVM). In this paper, to guarantee some necessary conditions in the theory of statistical learning, Schölkopf made use of the law of large numbers and also of some properties derived from the convergence in probability. I remember that when I commented on this, I realized that the public was not familiar with the statistical theory, and that it might be necessary to present it.

So if you've had minimal contact with statistics or probability theory, you've heard someone comment on the law of large numbers. But if you’ve never heard of this law, I’ll tell you:

Let $$X_1, \dots, X_n$$ be a sequence of independent and identically distributed random variables with mean $$ \mathbb{E}(X_i) = \mu $$ and variance $$\mathbb{VAR}(X_i) = \sigma^2 < \infty$$. So the sample average $$ \bar{X} = (X_1 + \cdots + X_n)/n $$ satisfies

$$
\bar{X} \xrightarrow{\mathbb{P}} \mu
$$

This law is widely used, and very simple to understand. But why this convergence is happening is perhaps not so obvious. To understand it is necessary to know a little about two types of stochastic convergences: convergence in probability and convergence in law, but in this post I will restrict myself only to convergence in probability.

I'm going to explain what convergence in probability is and how it works, in the simplest possible way. So here we go:

If you already had a calculus course, you have certainly heard about the limit of a sequence of real numbers ($$ a_n $$). For example, if $$a_n = 1/n $$, so the sequence $$ a_n \rightarrow 0$$, because

$$
\lim_{n \rightarrow \infty} a_n = \lim_{n \rightarrow \infty} \frac{1}{n} = 0,
$$

or we can say that for ever $$ \epsilon >0 $$ there's $$ n_0 $$ such that $$n > n_0$$ implies $$\lvert a_n - 0 \rvert < \epsilon$$. That is, for $$n$$ large enough, $$a_n$$ will be as close to $$0$$ as you want.

When we talk about convergence of random variables, the idea behind this convergence is the same behind the previous one, except for one small detail: a random variable is a function that takes elements of the sample space ($$\Omega$$) to the real numbers ($$\mathbb{R}$$). It is not a fixed value . For this reason we need a measure in order to calculate the limit, and for that we use the probability measure ($$\mathbb{P}$$), which takes the elements of the sample space to values in the range $$[0.1]$$.

Now let me show you a formal definition of convergence in probability. A sequence of random variables $$Y_n$$ is said to converge to a constant $$c$$ _in probability_ if for ever $$ \epsilon >0 $$,

$$
\lim_{n \rightarrow \infty} \mathbb{P}(|Y_n - c|<\epsilon) = 1,
$$

or equivalently,

$$
\lim_{n \rightarrow \infty} \mathbb{P}(|Y_n - c|\geq \epsilon) = 0.
$$

As notation we use $$ Y_n \xrightarrow{\mathbb{P}} c $$ to say that $$ Y_n $$ converges in probability to a constant $$ c $$. So, roughly speaking, when we say that, we mean that when $$n$$ is large, the probability is high that $$Y_n$$ be close to $$c$$.

There are several tricks to demonstrate that a random variable sequence converges in probability to a constant, and [Chebyshev inequality](https://en.wikipedia.org/wiki/Chebyshev%27s_inequality){:target="_blank" rel="noopener"} is often useful. But I will not go into many technical details, because that is not the purpose of this post.

All of this was to show you what is happening behind the scenes when we say that the sample average converges to the theoretical mean. And when you read that a sequence of random variables converges to a constant, you understand that behind the scenes there may be a convergence in probability.

I see ya in the next post, or on [twitter](http://twitter.com/scpatricio){:target="_blank" rel="noopener"}.

### References

> James, Barry R. Probabilidade: um curso em nível intermediário. No. 519.2. 1996.

> Jiang, Jiming. Large sample techniques for statistics. Springer Science & Business Media, 2010.

> Lehmann, Erich Leo. Elements of large-sample theory. Springer Science & Business Media, 2004.

> Schölkopf, Bernhard, et al. "Comparing support vector machines with Gaussian kernels to radial basis function classifiers." IEEE transactions on Signal Processing 45.11 (1997): 2758-2765.

> Shiryaev, Albert N. Probability-1. Springer, 2016.
