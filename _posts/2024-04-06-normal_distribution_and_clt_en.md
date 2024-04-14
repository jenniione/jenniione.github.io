---
title: Normal Distribution and Central Limit Theorem
sidebar:
  nav: study-en
aside:
  toc: true
key: 20240406
tags: Statistics
lang: en
mathjax: true
mathjax_autoNumber: true
---

<p align="center">
  <img class="image image--xl" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/normal_distribution_cover.jpeg">
</p>

Statistical testing and modeling methodologies often assume a normal distribution. Other important distributions in statistics, such as the chi-squared, t-distribution, and F-distribution, are also deeply connected to the normal distribution, deriving from it or utilizing its properties. It's hard to imagine statistics without the normal distribution.

## Discovery of the Normal Distribution
Also known as the Gaussian distribution or the Laplace distribution, it is often referred to as the bell curve. Regardless of the name, what matters is that mathematicians of the time observed the normal distribution through their research, highlighting the need to define such a distribution. Let’s briefly explore how some mathematicians discovered the normal distribution.

The normal distribution was first presented as an <u>'approximation of the binomial distribution'</u> by **Abraham de Moivre**.

<p align = "center">
  <img class="image image--md" src = "https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/Abraham_de_moivre.jpg">
  <br>
  Abraham de Moivre
  <br>
  출처: <a href = "https://en.wikipedia.org/wiki/Abraham_de_Moivre">SWikipedia(Abraham de Moivre)</a>
</p>
{:.circle.shadow}

Abraham de Moivre studied how close the binomial distribution $$B(n,p)$$ came to a certain formula when $$n$$ was very large. He discovered that the approximation held relatively well even when $$n$$ was not significantly large, such as over 100.

$$
_{n}C_{k} p^k q^{n-k} \approx {\frac{1}{\sqrt{2 \pi npq}} e}^{-\frac{(k-np)^2}{2npq}}
$$

Later, **Johann Carl Friedrich Gauss** discovered that the <u>distribution of errors between observed values and true values followed a normal distribution</u>.

<p align = "center">
  <img class="image image--md" src = "https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/Carl_Friedrich_Gauss.jpeg">
  <br>
  Johann Carl Fredrich Gauss
  <br>
  출처: <a href = "https://en.wikipedia.org/wiki/Carl_Friedrich_Gauss">Wikipedia(Johann Carl Friedrich Gaus)</a>
</p>
{:.circle.shadow}

While studying how observed values deviated from true values, Gauss realized that these errors formed a distribution with a specific symmetry. He defined this distribution to aid in his research.

## Definition of the Normal Distribution
The normal distribution is entirely defined by **two parameters: mean $$\mu$$ and standard deviation $$\sigma$$** .  

| DEFINITION |
| ------ |
| The **normal distribution** can be expressed as  <br> <center> $$ X\sim N(\mu ,{ \sigma  }^{ 2 }) $$ </center> <br> The continuous random variable $$X$$ follows this probability density function (PDF): <br> <center> $$ \begin{equation} \begin{aligned} f(x; \mu, \sigma) = \frac{1}{\sqrt{2\pi \cdot \sigma^{2}}} e^{-\frac{1}{2} \left(\frac{x-\mu}{\sigma}\right)^{2}} \end{aligned} \end{equation} $$</center> |

## Simulation of the Normal Distribution
The normal distribution is symmetric around the mean. Check out how the normal distribution changes as the mean and variance vary using the [Geogebra simulation (Normal Distribution by Joseph Manthey)](https://www.geogebra.org/m/EmRVMnXa).

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/normal_distribution_simulation_mean.png"/>
</p>

The mean is the center of the bell curve. As the mean changes, the normal distribution shifts left or right.

Let's also examine how variance changes.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/normal_distribution_simulation_var.png"/>
</p>

Variance indicates how spread out the distribution is around the mean. A larger variance spreads the curve wider, while a smaller variance makes it sharper.

## Central Limit Theorem (CLT)
Throughout this learning note, I've continually marveled at the beauty of the bell-shaped curve and pondered why the normal distribution is so crucial. This leads me to the Central Limit Theorem (CLT).

Essentially, this post could well be about the Central Limit Theorem masquerading as a discussion on the normal distribution.

The CLT is integral to the importance of the normal distribution, explaining why it's more than just "Look, it becomes a normal distribution." There’s also a common misconception that the theorem simply states, "Any distribution will become normal if its trials are repeated enough," which merits further exploration.

**Definition**&nbsp;&nbsp; The Central Limit Theorem (CLT) states that for a population with a fixed distribution, <u>the distribution of the sample means (or their sum)</u>, when sampled independently and repeatedly, <u>becomes increasingly normal</u> as the sample size increases.
{:.info}

Let's examine each aspect in detail:

- Population with a fixed distribution : The shape of the distribution doesn't matter, but sampling from a population with a totally different distribution is not allowed. In other words, the Central Limit Theorem **applies regardless of the specific distribution followed by the population**.
- Independent random sampling : As the name implies, each sampling must be independent and random.
- If the sample size is large: This is often misunderstood as needing a high number of samples. However, it actually means **'the larger the size of each sample, the better'.**
- Distribution of the averages follows a normal distribution: A common misunderstanding is thinking "if there are many samplings, the distribution becomes normal," but it's crucial to understand that it's **the distribution of the 'averages'** that follows the normal distribution. This means the distribution of the averages obtained from each sampling follows a normal distribution.

In summary, **<u>even if a population follows a specific distribution, if samples are drawn from it in an independent and random manner, especially if the samples drawn are large, the distribution of the averages obtained from these samples will follow a normal distribution.</u>**

### Intuitive Understanding of the Central Limit Theorem
Imagine gathering averages from multiple samples drawn from a population. The larger each sample is, the more accurately those averages will reflect the characteristics of the population. This isn’t difficult to grasp.

Consider opinion polls as an example. We generally trust a survey of 1,000 people more than one of 100 people because we believe the larger sample more accurately reflects the views of the entire population. Even without discussing reliability in detail, it's evident why we think this way: <u>larger samples tend to provide a better approximation of the population's true average</u>.

For an **extreme scenario**, imagine a sample as large as the population itself. The averages obtained from several such samples would likely be very close to the actual population average. <u>Although not every single average would exactly match the population mean, large deviations would be rare</u>, and smaller errors would occur more frequently. This demonstrates that **larger samples more accurately estimate the population mean**, with a distribution of errors that is symmetric and tends to be normal.

This intuitive understanding makes the Central Limit Theorem seem almost obvious.

**"Error"** was mentioned earlier, and Gauss had discovered that the errors between observed values and true values follow a normal distribution, which led him to define this distribution. From here, we can speculate on how the normal distribution might be utilized in the future.
 
### Mathematical Definition
To define the Central Limit Theorem mathematically:

Let's redefine the Central Limit Theorem from a mathematical perspective as previously understood intuitively.

| DEFINITION |
| ------|
| The **Central Limit Theorem (CLT)** states that as the size of a randomly drawn sample increases, the distribution of the sample means approaches a normal distribution, regardless of the population's initial distribution. Given random variables that are independent and identically distributed (i.i.d)*, with a valid mean $$\mu$$ and variance $$\frac{\sigma}{\sqrt{n}}$$, the mean $$N(\mu, \frac{\sigma^2}{n})$$ converges to a normal distribution with mean $$\mu$$ and standard deviation : <br> <center> $$\sqrt{n}((\frac{1}{n} \sum_{i=1}^{n}X_i) - \mu) \rightarrow N(0, \sigma^2)$$ <center/> <br> * i.i.d : Independent and Identically Distributed random variables |

If the sample mean $$\overline{X}$$ is standardized to $$Z= \frac{\overline{X}-\mu}{\sigma/\sqrt{n}}$$ , this statistic $$Z$$ approximates a standard normal distribution according to the Central Limit Theorem.

### Proof of the Central Limit Theorem
There are several methods to prove the Central Limit Theorem. The initial form by Laplace focused on the approximation of the binomial distribution to a normal distribution, and today the most common method involves using properties of moment-generating functions through the Lindeberg-Lévy CLT. However, this section opts for a more intuitive approach using characteristic functions and convolution, rather than the traditional method.

Previously, it was stated that the Central Limit Theorem implies that <u>the distribution of the 'averages'</u> or <u>the 'sum' of the samples</u> converges to a normal distribution. The proposition we are proving here is **the convergence of the 'sum' of variables**, so take care not to lose your way in the proof.

**Proposition**&nbsp;&nbsp; The 'sum' of independent and identically distributed (i.i.d.) random variables converges to a normal distribution when properly normalized.
{:.warning}

The proof can be quite complex, so subtitles are added to follow the critical ideas more easily.

- **Definition of the Convolution of Random Variables**<br/>
First, let's understand how convolution applies to probability variables. Suppose random variables $X$ and $Y$ are independent. The probability of a new random variable $$Z = X + Y$$ can be defined as follows:

$$
P(Z) = \sum_{k=-\infty}^{\infty}{P(X)P(Y)}
$$

If this concept is unclear, think of $$X$$ as the event of getting heads in a coin toss, $$Y$$ as the event of getting an even number in a dice roll, and $$Z$$ as the event of getting both heads in the coin toss and an even number in the dice roll in one go. Essentially, you're calculating the probability of $$Z$$ by multiplying the probabilities of $$X$$ and $$Y$$. For a deeper understanding, [this blog](https://colah.github.io/posts/2014-07-Understanding-Convolutions/) explains convolution beautifully.

If $$X$$ and $$Y$$ have probability density functions $$f(x)$$ and $$g(x)$$, respectively, the probability density function for $$Z=X+Y$$ is the convolution of $$f$$ and $$g$$, denoted as:

$$
(f*g)(z) = \int_{-\infty}^{\infty}f(z-y)g(y)dy = \int_{-\infty}^{\infty}g(z-x)f(x)dx
$$

Note how the sum turns into a product through convolution. This property will be utilized by defining the characteristic function of the random variables.

- **Definition of the Characteristic Function**
The characteristic function for any probability density function $$f_X(x)$$ is defined as (where $$t$$ is a real number): 

$$\phi_X(t) = E[e^{itX}] = \int_{-\infty}^{\infty}e^{jtx}f_X(x)dx$$

From this definition, it's clear that the absolute value of the complex exponential function $$e^{itX}$$ is always 1:

$$
|e^{itx}| = |\cos(tx) + i\sin(tx)| =  \sqrt{\cos^2(tx) + \sin^2(tx)} = 1 
$$

This characteristic function definition has a significant advantage over other transformations like Laplace transforms, as the integral exists for all probability distributions.

- **McLaurin Series Expansion**
Using the McLaurin series expansion, $$e^{jtx}$$ can be expanded as follow

$$
e^{jtx}=\sum_{k=1}^{\infty}\frac{(jtx)^k}{k!}=1+jtx+\frac{(jtx)^2}{2!}+\frac{(jtx)^3}{3!}+\cdots = 1+jtx+\frac{(jtx)^2}{2!}+O(t^2)
$$

$$O(t^2)$$ represents the terms from the fourth term onwards grouped together. This expansion can be applied to the characteristic function:

$$
\phi_X(t) = \int_{-\infty}^{\infty}e^{jtx}f_Y(t)dy=\int_{-\infty}^{\infty}\left\{1+jtx-\frac{t^2}{2}x^2+O(t^2)\right\}f_X(x)dy\notag
$$

$$
=\int_{-\infty}^{\infty}f_X(x)dy + \int_{-\infty}^{\infty}xf_X(x)dy - \frac{t^2}{2}\int_{-\infty}^{\infty}x^2f_X(x)dy+O(t^2)\notag
$$

$$
=1+jtE\left[x\right]-\frac{t^2}{2}E\left[x^2\right]+O(t^2)
$$

이 된다.

- **Characteristic Function for Normalized Random Variable $$Z_i$$**
Let's consider a normalized random variable $$Z_i = \frac{X_i - \mu}{\sigma}$$, where $$E(x)=0$$ and $$Var[x]=1$$ . The characteristic function for $$Z_i$$ simplifies as follows:

$$
\phi_Z(t) = E\left[e^{jtz}\right]=\int_{-\infty}^{\infty}e^{jtz}f_Z(z)dx
$$

$$
=1+jtE\left[z\right]-\frac{t^2}{2}E\left[z^2\right]+O(t^2)
$$

$$
= 1+0-\frac{t^2}{2}+O(t^2) 
$$

$$
= 1-\frac{t^2}{2}+O(t^2)
$$

- **Characteristic Function for the Sum of $n$ $$Z_i$$**
For the sum of $$n$$ independent $$$Z_i$$, the characteristic function for $$S_n = \sum_{i=1}^{n} Z_i = Z_1 + Z_2 + \cdots + Z_n$$ is:


$$\phi_{S_n}(t) = \left( \phi_{Z}(t) \right)^n$$


Applying the expansion of the characteristic function of the standardized variable $$Z$$, we get:

$$
\phi_{S_n}(t) = \left( \phi_{Z}(t) \right)^n = [1-\frac{t^2}{2N}+O\left(\frac{t^2}{N}\right)]^N
$$

When $$n$$ approaches infinity, $$O(\frac{t^2}{N})$$ converges to zero faster than $$\frac{t^2}{2N}$$ , and therefore, the limit value converges as follows:

$$
\lim_{N\rightarrow \infty}\phi_{S_N}(t) = \lim_{N\rightarrow\infty}\left[1-\frac{t^2}{2N}\right]^N=e^{-t^2/2}
$$

### Sample Size and Number of Samples
Statisticians typically say that a sample size of 30 or more is sufficient for a distribution to safely follow a normal distribution, but this is just a rule of thumb. In reality, more samples may be needed if the population distribution is highly asymmetric.
**Sample size** <u>guarantees the accuracy and representativeness of individual samples</u>, and a **sufficient number of samples** <u>relates to the reliability of the entire study and the generalizability of the results</u>. The following represents the distribution of averages from samples of integers from 1 to 10.

<p align = "center">
  <img src = "https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/normal_distribution_small_n_of_samples.png">
  <br>
  Simulation of Sample Size and Number of Samples
  <br>
  출처: <a href = "https://demonstrations.wolfram.com/TheCentralLimitTheorem/#related-demonstrationss">Wolfram, The Central Limit Theorem(Chris Boucher)</a>
</p>

If the number of samples is excessively low, no matter how large the sample size, it merely accumulates the distribution of the samples, not the population. This result should be seriously considered for generalizability. Therefore, simply thinking "if the sample size is large, it converges to a normal distribution!" needs caution.

Ideally, both a large sample size and a high number of samples would be the best scenario.

## So, why Is the Normal Distribution Important?

<p align="center">
  <img class="image image--xl" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/central limit theorem.webp">
</p>

In inferential statistics based on sampling techniques, understanding the distribution of sample means is crucial for tracking the population mean. According to the Central Limit Theorem, if sampling is conducted from sufficiently large samples, even without knowing anything about the population mean, the distribution of these sample means will converge to a normal distribution. Typically, in many scenarios, we try to estimate the population distribution based on the distribution of average values obtained from consistently sampled observations. This attempt ensures that we frequently encounter the normal distribution inevitably.

<br/><br/>
**참조**<br/>
[Normal Distribution: An Introductory Guide to PDF and CDF(Teena Mary)](https://integratedmlai.com/normal-distribution-an-introductory-guide-to-pdf-and-cdf/)<br/>
[가우시안(Gaussian)-정규분포(Normal Distribution).너란 분포 정말(친절한 데이터 사이언스 강좌)](https://recipesds.tistory.com/entry/%EA%B0%80%EC%9A%B0%EC%8B%9C%EC%95%88Gaussian-%EC%A0%95%EA%B7%9C%EB%B6%84%ED%8F%ACNormal-Distribution-%EB%84%88%EB%9E%80-%EB%B6%84%ED%8F%AC-%EC%A0%95%EB%A7%90)<br/>
[“Python Implementation of Central Limit Theorem: Exploring Sample Data to Infer Population Parameters”(Amanatullah)](https://medium.com/@amanatulla1606/python-implementation-of-central-limit-theorem-exploring-sample-data-to-infer-population-595e39e0c98e)<br/>
[Understanding Convolutions(colah's blog)](https://colah.github.io/posts/2014-07-Understanding-Convolutions/)<br/>
[Characteristic Functions and the Central Limit Theorem(University of Waterloo)](https://sas.uwaterloo.ca/~dlmcleis/s901/chapt6.pdf)<br/>
[Sampling Distribution of the Mean Simulation](https://portal.eller.arizona.edu/sampling/)<br/>