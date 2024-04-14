---
title: Binomial Distribution
sidebar:
  nav: study-en
aside:
  toc: true
key: 20240327
tags: Statistics
lang: ko
mathjax: true
mathjax_autoNumber: true
---

Before discussing the binomial distribution, let's briefly review the Bernoulli distribution and explore how it relates to the binomial distribution.

## Bernoulli Distribution
A Bernoulli experiment is one in which the outcome of a probability experiment is either success or failure. The probability distribution that represents the number of successes in a Bernoulli experiment with a fixed success probability $$p$$ is known as the **Bernoulli Distribution**. Thus, a Bernoulli distribution is a probability distribution where the random variable **takes only two possible values, success or failure**, making it a **discrete random variable**.

one where the outcome can either be a success or a failure. The probability distribution that accounts for the number of successes in a Bernoulli experiment, with a fixed probability of success $$p$$, is the Bernoulli distribution.

$$ x  \{ \text{success, fail} \} \rightarrow \{0, 1\}$$

$$
\begin{equation}
\begin{aligned}
& P(x=0) = 1-p \\
& P(x=1) = p \\ \end{aligned}
\end{equation}
$$

If a random variable $$X$$ follows the Bernoulli distribution, it can be expressed as:

$$
\begin{equation} 
 \begin{aligned} 
& x \sim \text{Bern}(p)
\end{aligned}   
\end{equation}
$$

The probability mass function (PMF) for the Bernoulli distribution is:

$$
\begin{split}
\begin{align}
\text{Bern}(x; p) = 
\begin{cases} 
p   & \text{if }x=1, \\
1-p & \text{if }x=0
\end{cases}
\tag{8.2.2}
\end{align}
\end{split}
$$

The key point here is that the Bernoulli distribution focuses on the probability of success $$p$$ for **a single trial**. This characteristic differentiates it from the binomial distribution.

## Definition of Binomial Distribution

| DEFINITION |
| ------ |
| **The Binomial Distribution** models the number of successes in a fixed number $$n$$ of repeated Bernoulli trials, each with the same probability $$p$$ of success. |

The binomial distribution is essentially the result of repeating a Bernoulli trial $$n$$ times. In other words, **the binomial distribution is an extension of the Bernoulli trial**. Instead of just one Bernoulli trial, the binomial distribution models the probability distribution of the number of successes over $$n$$ repeated trials.

For example, flipping a coin with a success probability of $$p=1/2$$ once follows a Bernoulli distribution. However, if you flip the same coin 10 times and observe the number of heads, this scenario follows a binomial distribution. The key is that **each flip is independent, and the success probability for each trial remains constant at $$p$$** .

The binomial distribution is expressed as:

$$
\begin{equation} 
 \begin{aligned} 
x \sim \text{Bin}(n,p)
\end{aligned}   
\end{equation}
$$

And its probability mass function (PMF) is defined as:

$$
\begin{equation} 
P_X(x) = \ _{n}C_{x} p^k (1-p)^{n-x} \quad \text{ for } x =0,1,\cdots,n
\end{equation}
$$

## Understanding the Binomial Distribution
### 10 Coin Flips Example
To understand the probability mass function, let's calculate the probability for the scenario of flipping a coin 10 times. Let's say success is when the coin shows heads, and $$x$$ is the number of successes, where $$x=0,1,2,⋯,10$$, representing the cases where heads appear 0, 1, 2, ..., up to 10 times. For instance, when $$x=2$$, i.e., two heads in 10 flips, the probability is given by:

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/coin k=2.png">
</p>

As illustrated, each independent event of the coin landing on heads 2 times out of 10 flips has a probability of $$(\frac{1}{2})^2(1-\frac{1}{2})^{8}$$. This can occur in $$_{10}C_{2}$$ different ways. The calculation is as follows:


$$
_{10}C_{2}\left(\frac{1}{2}\right)^2 \left(1-\frac{1}{2}\right)^{8} = 0.0439
$$

Similarly, you can calculate the probabilities for all values of 

$$x=0 ;  \frac{10!}{1!\cdot9!}
\left(\frac{1}{2}\right)^0 \left(1-\frac{1}{2}\right)^{10} = 0.0010
$$

$$
x=1 ;  \frac{10!}{1!\cdot9!}
\left(\frac{1}{2}\right)^1 \left(1-\frac{1}{2}\right)^{9} = 0.0098
$$

$$
x=2 ; \frac{10!}{2! 8!}\left(\frac{1}{2}\right)^2 \left(1-\frac{1}{2}\right)^{8} = 0.0439
$$

<center>⋮</center>

$$
x=10 ; \frac{10!}{10! 0!}\left(\frac{1}{2}\right)^{10} \left(1-\frac{1}{2}\right)^{0} = 0.0010
$$

Displayed as a histogram, this distribution would look as follows:

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/coin distribution.png">
</p>

### Intuitive Understanding of the Binomial Distribution
The binomial distribution calculates the probability of obtaining certain outcomes from repeated trials, such as flipping a coin, where there are two possible results each time.

To understand how the binomial distribution is practically used, let’s explore some real-life applications.

- Example 1<br/>
Suppose a marketing team sends emails to 1,000 customers. Based on previous experiences, assume the probability of receiving a reply is 0.5. What is the probability of receiving replies from exactly 50 customers? 

This is a straightforward calculation using the binomial distribution $$P_X(50)$$ where $$n=1000$$ and $$p=0.5$$ . The binomial distribution fundamentally calculates the **probability of achieving a certain number of successes** given **fixed trial counts and success probability**.

Furthermore, the concept of the binomial distribution can be utilized in conducting A/B tests. Consider the example below.

- Example 2<br/>
Consider conducting an A/B test to compare the effectiveness of two website designs, A and B. Let's assume 1,000 visitors are shown design B, and 150 click on it. We want to assess whether the click rate for design B significantly differs from design A's expected click rate of 10%, assuming each visitor's click is an independent event.

In this scenario, each website visitor's action (click or no click) results in a binomial outcome. We can set the success probability (p) at 10%, the number of trials (n) at 1,000, and the number of successes at 150, and perform a binomial test.

## Mean and Variance of the Binomial Distribution
For a binomially distributed random variable $$X$$ , with trial number $$n$$ and success probability $$p$$ :

The expected value is:

$$E(X) = np$$

The variance is:

$$Var(X) = np(1-p)$$

These are demonstrated as follows:

$$
\begin{split}
\begin{align}
\begin{aligned}
\text{E}[X] 
&= \sum_{x_i \in \Omega} x_i p(x_i) \\
&= 1 \cdot \mu + 0 \cdot (1 - \mu) \\
&= \mu
\end{aligned}
\end{align}
\end{split}
$$
<br/>

$$
\begin{split}
\begin{align}
\begin{aligned}
\text{Var}[X] 
&= \sum_{x_i \in \Omega} (x_i - \mu)^2 p(x_i) \\
&= (1 - \mu)^2 \cdot \mu + (0 - \mu)^2 \cdot (1 - \mu) \\
&= \mu(1-\mu)
\end{aligned}
\end{align}
\end{split}
$$

## Approximation of the Binomial Distribution to a Normal Distribution
Let's observe how the binomial distribution changes by freely altering its parameters, easily verified through various online simulations, including the GeoGebra "Parameters of the Binomial Distribution (shanlee)" simulation.

As the number of trials increases, what happens to the binomial distribution?

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/binomial distribution to normal distribution.png">
</p>

 For example, after conducting 50 coin flips, we can see the distribution resembles a **bell-shaped** normal distribution. However, direct simulation shows this is **only feasible when values of $$n$$ and $$p$$ are not extreme**. If $$n$$ is too small, or $$n$$ is large but $$p$$ is very small or large, the shape diverges significantly from a normal distribution.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/small n.png">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/small p.png">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/huge p.png">
</p>

Mathematically, if the binomial distribution’s $$n$$ is large enough such that $$np≥5$$ and $$np(1−p)≥5$$, it approximates a normal distribution with mean $$np$$ and the variance $$np(1−p)$$ . This approximation becomes **more accurate as $$n$$ increases and $$p$$ is neither close to 0 nor 1 but closer to 0.5**.

Practically, many real-world events follow a binomial distribution. For instance, how many hits will a 0.3 hitter make in 100 at-bats? How many people might die from a disease with a 30% mortality rate among 100 infected individuals? If the normal distribution can approximate the binomial distribution, it also becomes a powerful tool for explaining a wide range of phenomena.

<br/><br/>
**References**

[Parameters of the Binomial Distribution(shanlee)](https://www.geogebra.org/m/hGkW4vwJ)<br/>
[데이터 사이언스 스쿨](https://datascienceschool.net/02%20mathematics/08.02%20%EB%B2%A0%EB%A5%B4%EB%88%84%EC%9D%B4%EB%B6%84%ED%8F%AC%EC%99%80%20%EC%9D%B4%ED%95%AD%EB%B6%84%ED%8F%AC.html)<br/>
[기초통계 개념정리(김진섭)](https://bookdown.org/mathemedicine/Stat_book/normal-distribution.html#-1)<br/>
