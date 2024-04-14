---
title: Poisson Distribution
sidebar:
  nav: study-en
aside:
  toc: true
key: 20240402
tags: Statistics
lang: en
mathjax: true
mathjax_autoNumber: true
---

<p align="center">
  <img class="image image--md" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/poisson_distribution/Simeon Denis Poisson.jpg"/>
</p>

The French mathematician Siméon Denis Poisson first introduced the Poisson distribution as a form of discrete probability distribution. Later, in 1898, the Polish mathematician Ladislaus Bortkiewicz effectively modeled the frequency of accidental deaths from horse kicks in the Prussian army using the Poisson distribution, demonstrating its practical application.

## Transition from Binomial to Poisson Distribution
### Poisson Cases
Earlier simulations of the [binomial distribution](https://jenniione.github.io/2024/03/27/binomial_distribution_ko.html#%EC%9D%B4%ED%95%AD-%EB%B6%84%ED%8F%AC%EC%9D%98-%EC%A0%95%EA%B7%9C-%EB%B6%84%ED%8F%AC-%EA%B7%BC%EC%82%AC) revealed various forms it could take. Particularly, **when the number of trials $$n$$ is large but the probability of success $$p$$ is extremely small**, the distribution adopts a unique shape, as observed here:

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/small p.png">
</p>

Such cases are not ideally explained by the binomial distribution and are more suitably described by the Poisson distribution. Let's delve deeper into events handled by the Poisson distribution.

### Limitations of the Binomial Distribution for Poisson Cases
Consider Ladislaus Bortkiewicz's problem of the frequency of Prussian soldiers dying from horse kicks. Observing over 20 years, about 10 soldiers per year seemed to die from such incidents. How likely is it that only 5 soldiers would die in a year?

If we only consider a binomial distribution where observing a soldier's death is a success, setting $$n$$ becomes ambiguous. Even if we consider one year as one trial, totaling 20 trials, binomial distribution struggles **due to the randomness of annual death counts**, despite an average of 10 per year. All 10 soldiers would show up in the first year, or in the second year... , it seems quite difficult to use the binomial distribution unless you are looking for the probability of it appearing at once every 20 years.

### Transition to Poisson Distribution
To address this, we need to move away from the binomial parameters $$n$$ and $$p$$ , and introduce a new parameter, $$\lambda$$, representing the average number of events per unit time or space. Here, $$\lambda$$ becomes a kind of expected value $$\lambda=np$$ . With a constant $$\lambda$$ like 'average 10 years,' as $$n$$ approaches infinity, $$p$$ approaches zero:

$$
\lim_{n\rightarrow \infty}p=\lim_{n\rightarrow \infty}\frac{\lambda}{n} = 0
$$

Let's apply this to the probability density function of the binomial distribution and derive its limit:

$$
\lim_{n \to \infty} B(k; n, p) 
$$

$$
= \lim_{n \to \infty}  { {n}\choose{k} }  p^k(1-p)^{n-k}
$$

$$
= \lim_{n \to \infty}  \dfrac{n!}{k!(n-k)!}(\dfrac{\lambda}{n})^k  (1-\dfrac{\lambda}{n})^{n-k}
$$

$$
= \lim_{n \to \infty}  {\left[  \dfrac{n!}{(n-k)!  n^k} \right]}  \left[  \dfrac{\lambda^k}{k!}  (1-\dfrac{\lambda}{n})^{n}  \right]  {\left[  (1-\dfrac{\lambda}{n})^{-k}\right]}
$$

$$
= \lim_{n \to \infty}  {\left[  \dfrac{n(n-1)\dotsb(n-(k-1))}{n^k} \right]}  \left[  \dfrac{\lambda^k}{k!}  (1-\dfrac{\lambda}{n})^{n}  \right]  {\left[  (1-\dfrac{\lambda}{n})^{-k}\right]}
$$

$$
= 1\left[  \dfrac{\lambda^k}{k!}  e^{-\lambda}\right] 1
$$

$$
= (\frac{\lambda^k}{k!})e^{-\lambda}\\
$$

Therefore,

- (6) : As $$n$$ approaches infinity, and since $$k$$ is relatively small, the above limit is calculated.

$$
Pr(K=k) = (\frac{\lambda^k}{k!})e^{-\lambda}
$$

Ultimately, with a fixed $$\lambda$$, we derived the probability density function of the binomial distribution as $$n$$ approaches infinity, allowing us to express events difficult to describe with binomial parameters using just the single new parameter $$\lambda$$ .

## Definition of the Poisson Distribution

| DEFINITION |
| ------ |
| The **Poisson Distribution** models the number of events occurring in a fixed unit of time or space. When a random variabel $$x$$ follows the Poisson distribution, it is denoted as <br> <center> $$ \begin{aligned} x \sim \text{Pois}(\lambda) \end{aligned} $$ </center> <br/> with the probability mass function given by: <br> <center> $$\begin{aligned} P(x) = \frac{\lambda^{k} e^{-\lambda}}{k!} \quad \text{ for } k =0,1,2,\cdots \end{aligned} $$</center>

|

## Intuitive Understanding of the Poisson Distribution
The Poisson distribution models the frequency of rare events over a particular time interval or space, **effectively calculating the probability of specific outcomes given an average value**. How can this be practically important?

- Example 1<br/>
Suppose a city typically experiences <u>two instances of Disease $$A$$ per month</u>. Public health officials want to know the probability of <u>zero occurrences</u> next month:

$$
Pr(K=0) 
$$

$$
= \frac{e^{-2} \times 2^0} {0!}
$$

$$
= 0.1353
$$

This means there is <u>a 13% chance that the disease will not occur next month</u>, based on average observations.

- Example 2<br/>
An e-commerce website processes an <u>average of 200 orders on a typical day</u> without special promotions or events. The operations team might want to know the probability of exactly <u>250 orders</u> to adjust delivery preparations or customer service staffing effectively:

$$
P(X=250) = \frac{e^{-200} \times 200^{250}}{250!} = 0.000077
$$

This low probability suggests that <u>days with significantly higher than expected order volumes are rare</u>, helping in planning resources efficiently for inventory, shipping

이처럼 포아송 분포는 다양한 상황에서 중요한 정보를 해석하는 데 활용될 수 있다.  

## Simulation of the Poisson Distribution
The parameter of the Poisson distribution is $$\lambda$$ .  Let's explore how the Poisson distribution changes as $$\lambda$$ varies.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/poisson_distribution/poisson_distribution.png">
</p>

The graph above shows $$\lambda=1$$, illustrating that when the value is very small, most probabilities are concentrated around 0 or 1. 

Also, for $$\lambda=10$$ and $$\lambda=30$$, **as $$\lambda$$ increases, the probability of events is more evenly distributed, and the shape of the graph approximates a normal distribution**.

In fact, **as $$\lambda$$ increases, the Poisson distribution approximates a normal distribution $$N(\lambda, \lambda^{2})$$ .**

<br/><br/>
**Referencess**

[Wikipedia, Poisson Distribution](https://ko.wikipedia.org/wiki/%ED%91%B8%EC%95%84%EC%86%A1_%EB%B6%84%ED%8F%AC)<br/>
[Angelo's Math Notes(Angelo)](https://angeloyeo.github.io/2021/04/26/Poisson_distribution.html)
