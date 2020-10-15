---
title: "Fisher Informwhat??"
date: 2020-10-15
tags: [likelihood, statistic, fisher information]
header:
  image: "/images/likelihood/head.jpeg"
excerpt: "here is some information about Fisher Information"
mathjax: "true"
---
Hi you! Here I'm going to talk to you a little bit about Fisher Information. If you're reading this post, I'm sure you've heard of it, and can now appreciate the beautiful classic theory of mathematical statistics about the likelihood function. But let's not lose focus, and let's talk about Fisher Information.

For begin with, do you know what formula is down here?

$$
\mathbb{E}\left[ \left( \frac{\partial \log f(X|\theta)}{\partial \theta} \right)^2 \right]
$$

Maybe that way you don't recognize it, but maybe that makes more sense.

$$
-\mathbb{E}\left[ \frac{\partial^2 \log f(X|\theta)}{\partial \theta^2} \right]
$$

If you said Fisher Information, you were right. And if you don't know that, I would like to tell you that this quantity is the infamous Fisher Information, and that's what I'm going to talk about here. And I will try my best not to show more formulas, because I know it scares people (even though I love it).

The Fisher Information is an important quantity in Mathematical Statistics, which plays a fundamental role in classical statistics, especially in the asymptotic theory of Maximum-Likelihood Estimation (MLE), and in the Cramér-Rao loer bound (I will make a post just about that).

Informally, Fisher Information provides a measure of the amount of "information" that a random variable carries over a parameter $$ \theta $$. More formally, the Fisher Information is the variance of the score function (I will also post about it).

In [this post](https://scpatricio.github.io/likelihood/){:target="_blank" rel="noopener"} I commented on the likelihood function and why we maximize it to obtain an estimate of unknown parameters, also known as MLE. Now let's go back to this post. The log-likelihood is a function of $$\theta$$, and is random because it depends on $$X$$



I see ya in the next post, or on [twitter](http://twitter.com/scpatricio){:target="_blank" rel="noopener"}.

### References

> Bolfarine, Heleno, and Mônica Carneiro Sandoval. Introdução à inferência estatística. Vol. 2. SBM, 2001.

> Casella, George, and Roger L. Berger. Statistical inference. Vol. 2. Pacific Grove, CA: Duxbury, 2002.

> DUDEWICZ, Edward J.; MISHRA, Satya. Modern mathematical statistics. John Wiley & Sons, Inc., 1988.
