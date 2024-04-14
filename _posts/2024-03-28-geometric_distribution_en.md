---
title: Geometric Distribution
sidebar:
  nav: study-en
aside:
  toc: true
key: 20240328
tags: Statistics
lang: en
mathjax: true
mathjax_autoNumber: true
---

If you understand the [binomial distribution](https://jenniione.github.io/2024/03/27/binomial_distribution_ko.html), the geometric distribution is not a difficult concept. While the binomial distribution models the number of successes in a series of Bernoulli trials, the geometric distribution measures **the number of trials until the first success** or **the number of failures before the first success**.

## Definition of the Geometric Distribution

| DEFINITION 1 |
| ------ |
| The **Geometric Distribution** models the number of trials until the first success in a series of Bernoulli trials.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

| DEFINITION 2 |
| ------ |
| The **Geometric Distribution** models the number of failures before the first success in a series of Bernoulli trials.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |

The geometric distribution is used to model the number of trials until success, with two definitions available. The primary difference between these definitions is whether the count of trials includes the first success. Definition 1 counts all trials including the first success, whereas Definition 2 only considers the trials before the first success.

For example, in coin tossing where a head is defined as success, assume the sequence 'tail-tail-tail-head' occurs. According to Definition 1, the number of trials until success, $X$, is 4. Under Definition 2, it considers only the failures before the first success, so $X$ would be 3. This distinction is crucial for interpreting the geometric distribution as it shows a difference of one trial depending on whether the success is included.

The geometric distribution is denoted as:

$$
\begin{equation} 
 \begin{aligned} 
x \sim \text{Geom}(p)
\end{aligned}   
\end{equation}
$$

And its probability mass function (PMF) is:

$$
\begin{equation} 
\begin{aligned} 
P(x) = (1-p)^{k-1} p \quad \text{ for } k =1,2,\cdots
\end{aligned} 
\end{equation}
$$

## Understanding the Geometric Distribution
To illustrate, consider the example of tossing a coin 10 times. Let's define success as getting a head and $X=x$ as the number of trials until success. When $x=3$, the probability is the product of two failures and one success, calculated as $(1-\frac{1}{2})^2(\frac{1}{2})=0.125$ .

## Memorylessness of the Geometric Distribution
A key property of the geometric distribution is its memorylessness, expressed mathematically as:

$$
P(X > s + t | X > s) = P(X > t)
$$

This implies that past outcomes do not influence future probabilities. For instance, even if six tails have already occurred in coin tossing, the probability of a head in the next toss remains $$1/2$$ . The fact that six tosses have occurred does not affect the trials going forward. Essentially, even if starting from scratch, the expected number of trials until the first success remains unchanged.

This property of the geometric distribution is particularly useful in network traffic analysis, queuing theory, and more. For instance, if the arrival time of web server requests follows a geometric distribution, the expected time until the next request does not change regardless of how much time has already passed. This can play a crucial role in optimizing wait times, system throughput, and resource allocation strategies.

## Practical Applications of the Geometric Distribution
The geometric distribution is essentially about observing outcomes until the first success. This characteristic can be used to analyze how many page visits are needed before a user makes their first purchase on a website, or to calculate the probability that a product or service continues without failure over a specific period. It can also assess the efficiency of specific strategies in A/B testing by analyzing the number of trials until a strategy succeeds.

<br/><br/>
**References**

[binomial and geometric distribution(pthao_nguyen, Zoran)](https://www.geogebra.org/m/twbv2tmk)