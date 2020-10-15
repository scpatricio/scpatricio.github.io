---
title: "on the cornerstones of statistical learning"
date: 2020-10-16
tags: [statistic, statistical learning]
header:
  image: "/images/rhistory/LSM2.jpg"
excerpt: "did you know that statistical learning started in the 19th century?"
mathjax: "true"
---

A few weeks ago I started reading [The Elements of Statistical Learning](http://web.stanford.edu/~hastie/Papers/ESLII.pdf){:target="_blank" rel="noopener"} again, a book that I think is the best one to start really venturing into the world of statistical learning. And then I came across the history of statistical learning. I thought the story of how it all started and the first method presented in the 19th century was fantastic, and I thought “man, people need to know that”. And here I am, to share this story and also a little bit about the method that is considered as the first statistical learning method. Let's do it.

As I commented in this post, the first statistical learning method was presented by Legendre. He was honored with the first publication of this method, in his work called _Nouvelles methodses pour la determination des orbites des cometes_, published in Paris in 1805. As the name of the work suggests, Legendre used the least squares method to determine the orbit of comets. At the time, this method was an inventor, and its value was immediately recognized by the leading astronomers and geodesists of the time.

But 4 years after the first clear and concise exposition of the least squares method, Carl Friedrich Gauss published his method of calculating the orbits of celestial bodies, where he claimed to have the least squares method since 1795. However, in this publication Gauss managed to connect the least squares method to the principles of probability and normal distribution.

In his work, Gauss also specified a mathematical form of the probability density for the observations, depending on a finite number of unknown parameters, and defined an estimation method that minimizes the estimation error. Today we can address the same problem by maximizing the log-likelihood function, assuming that the estimation error has a normal distribution and thus enjoys consistency, functional invariance, efficiency and asymptotic normality, which are some of the properties of Maximum-Likelihood Estimation.

However, the least squares method was only related to linear regression analysis in 1822, when Gauss was able to affirm that the approach of this method for this type of analysis provides the best results in the sense that in a linear model where errors have mean zero and are independent (uncorrelated) and with the same variance. Since then, researchers in error theory and statistics have found many different ways to implement this method.

After all this, it is clear that the least squares method is very old and, despite this, it is still widely used today for supervised and unsupervised learning problems. Even used as a loss function for deep neural network models, which are the most powerful and current methods of machine learning.

I have to confess that for me this wave of data science that we are experiencing now, is nothing more than the popularization of various statistical methods that were created centuries ago. And this is great, because now we have more people interested in developing and improving statistical techniques, which results in a boom in the development of this science.

Finally, after several years, statistics are being recognized as science, and not just as a tool, as they have been until the last decade. Finally, the glorification of statistics.

I see ya in the next post, or on [twitter](http://twitter.com/scpatricio){:target="_blank" rel="noopener"}.

### References

> Friedman, Jerome, Trevor Hastie, and Robert Tibshirani. The elements of statistical learning. Vol. 1. No. 10. New York: Springer series in statistics, 2001.
APA

> Merriman, Mansfield. "On the history of the method of least squares." The Analyst 4.2 (1877): 33-36.
APA

> Stigler, Stephen M. The history of statistics: The measurement of uncertainty before 1900. Harvard University Press, 1986.
APA
