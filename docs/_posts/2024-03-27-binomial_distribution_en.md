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



Before diving into the binomial distribution, let's briefly summarize the Bernoulli distribution and explore its relationship with the binomial distribution.

## Bernoulli Distribution
A Bernoulli experiment refers to a probability experiment where the outcome can either be a success or a failure. The probability distribution that represents the number of successes in a Bernoulli experiment, with a fixed success probability $$p$$, is known as the **Bernoulli distribution**. Therefore, the Bernoulli distribution is a probability distribution where the value of the random variable is either a success or a failure. Since **the outcome can only be one of two values, success or failure**, a Bernoulli random variable is classified as a **discrete random variable**.

one where the outcome can either be a success or a failure. The probability distribution that accounts for the number of successes in a Bernoulli experiment, with a fixed probability of success $$p$$, is the Bernoulli distribution.

$$ x  \{ \text{success, fail} \} \rightarrow \{0, 1\}$$

$$
\begin{equation}
\begin{aligned}
& P(x=0) = 1-p \\
& P(x=1) = p \\ \end{aligned}
\end{equation}
$$

If the random variable $$X$$ follows a Bernoulli distribution, it can be expressed as follows:

$$
\begin{equation} 
 \begin{aligned} 
& x \sim \text{Bern}(p)
\end{aligned}   
\end{equation}
$$

And its Probability Mass Function (PMF) can be represented by the following formula:

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


It is important to note that the Bernoulli distribution focuses on observational data from the result of **a single trial**, emphasizing the **probability of success $$p$$**. This aspect explains how the binomial distribution differs from the Bernoulli distribution.

## Definition of Binomial Distribution
**Definition**&nbsp;&nbsp; The Binomial Distribution models the number of successes in a fixed number $$n$$ of repeated Bernoulli trials, each with the same success probability $$p$$.
{:.info}

The binomial distribution is the probability distribution obtained by repeating a Bernoulli trial $$n$$ times. In other words, **the binomial distribution is an extension of the Bernoulli trial**. It models the probability distribution of the number of successes in $$n$$ repeated Bernoulli trials, not just a single Bernoulli trial. 
For example, consider the example of flipping a coin. When you perform a single coin toss with the probability of getting heads being $$p=1/2$$; the outcome follows a Bernoulli distribution. However, if the same coin is flipped 10 times, and the number of times heads appears is observed, this scenario follows a binomial distribution. The key here is that during the 10 flips, **each flip is independent, and the probability of success for each trial remains constant at $$p$$** (as is the case with a fixed $$p$$ in a Bernoulli trial).

The binomial distribution can be expressed as follows,
$$
\begin{equation} 
 \begin{aligned} 
x \sim \text{Bin}(n,p)
\end{aligned}   
\end{equation}
$$

ans its Probability Mass Function (PMF) is defined as follows.

$$
\begin{equation} 
P_X(x) = \ _{n}C_{x} p^k (1-p)^{n-x} \quad \text{ for } x =0,1,\cdots,n
\end{equation}
$$

## Real Insights into the Binomial Distribution
### Example of Flipping a Coin 10 Times

To grasp the Probability Mass Function, let's calculate the probability of outcomes in the scenario of flipping a coin 10 times.
Consider a success as the coin landing on heads, and let $$x$$ be the number of successes. Thus, $$x=0,1,2,⋯,10$$, representing the scenarios where the coin lands on heads 0 times, 1 time, 2 times, ... up to 10 times. Let's consider the probability when $$x=2$$, that is, the probability of the coin landing on heads 2 times in 10 flips.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/coin k=2.png">
</p>

As illustrated, each independent event of the coin landing on heads 2 times out of 10 flips has a probability of $$(\frac{1}{2})^2(1-\frac{1}{2})^{8}$$. This can occur in $$_{10}C_{2}$$ different ways. The calculation is as follows:


$$
_{10}C_{2}\left(\frac{1}{2}\right)^2 \left(1-\frac{1}{2}\right)^{8} = 0.0439
$$

Using the same method, calculating the probabilities for all values of $$x$$ yields the following results:

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

If represented as a histogram, it would appear as follows.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/coin distribution.png">
</p>

### An Intuitive Look at Binomial Distribution

The binomial distribution is used to calculate the probability of obtaining certain outcomes from repeating a probabilistic event, like flipping a coin, that has two possible results, multiple times.

To understand how it can be applied in practice for a more intuitive comprehension, let's look into scenarios where the binomial distribution is considered.

- Example 1<br/>
Suppose a marketing team sends emails to 1,000 customers individually. Based on previous experience, let's assume the probability of receiving a reply is 0.5. What then is the probability of receiving replies from 50 customers out of the 1,000 emails sent?

This is a simple problem of calculating the binomial distribution probability $$P_X(50)$$ with $$n=1,000$$, $$p=0.5$$. The binomial distribution fundamentally **utilizes the number of trials and the fixed probability of success** to calculate the **probability of success occurring**.

Furthermore, the concept of the binomial distribution can be utilized in conducting A/B tests. Consider the example below.

- Example 2<br/>
Let's assume an A/B test is conducted to compare the effectiveness of two designs (A and B) in increasing the click-through rate on a website. Suppose design B was shown to 1,000 visitors to the website, and 150 clicked on it. We want to assess whether the click-through rate for design B is statistically significantly different from a 10% click-through rate for design A.

Assuming the independence of each visitor's click action, the action of clicking by each website visitor results in a binomial outcome of click (success) or no click (failure). With the success probability $$p$$ set to 10%, the number of trials $$n$$ to 1,000, and the number of successes to 150, we can perform a binomial test.

## Mean and Variance of Binomial Distribution
For a random variable $$X$$ following a binomial distribution with a total number of trials $$n$$ and a success probability $$p$$, 

the mean are

$$E(X) = np$$

and the variance are

$$Var(X) = np(1-p)$$

The proofs for each are as follows:

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


## The Normal Approximation to the Binomial Distribution
As we adjust the parameters of the binomial distribution, let's explore the various shapes it can exhibit. There are numerous simulatiors accessible online for this purpose, such as the "Parameters of the Binomial Distribution" simulation by shanlee on GeoGebra.
What transformation does the binomial distribution undergo as $$n$$, the number of trials, continues to increase?


<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/binomial distribution to normal distribution.png">
</p>

When conducting 50 coin flips, one can observe that the resulting distribution resembles the **bell shape** of a normal distribution. However, by operating the simulation directly, it's discernible that this approximation is **only feasible when the values of $$n$$ and $$p$$ are not extreme**. If $$n$$ is too small, or if $$n$$ is sufficiently large but $$p$$ is too small or too large, the shape deviates significantly from that of a normal distribution.


<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/small n.png">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/small p.png">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/huge p.png">
</p>

Mathetically, if the number of trials $$n$$ in a binomial distribution is sufficiently large such that $$np≥5$$ and $$np(1−p)≥5$$, then the binomial distribution can be approximated by a normal distribution with mean $$np$$ and variance $$np(1−p)$$. This can be intuitively understood through simulation. Directly operating the simulation reveals that the approximation to a normal distribution becomes **more accurate as $$n$$ increases, and as $$p$$ is not too close to 0 or 1 but closer to 0.5**.

How many hits might a baseball player with a .300 batting average get in 100 at-bats? How many people might actually die if 100 people were infected with a disease with a 30% mortality rate? Many real-world events can be said to follow a binomial distribution. If the normal distribution can represent an approximation of the binomial distribution, then the normal distribution can also describe many events.

<br/><br/>
**References**

[Parameters of the Binomial Distribution(shanlee)](https://www.geogebra.org/m/hGkW4vwJ)<br/>
[데이터 사이언스 스쿨](https://datascienceschool.net/02%20mathematics/08.02%20%EB%B2%A0%EB%A5%B4%EB%88%84%EC%9D%B4%EB%B6%84%ED%8F%AC%EC%99%80%20%EC%9D%B4%ED%95%AD%EB%B6%84%ED%8F%AC.html)<br/>
[기초통계 개념정리(김진섭)](https://bookdown.org/mathemedicine/Stat_book/normal-distribution.html#-1)<br/>
