---
title: Probability Distribution
sidebar:
  nav: study-en
aside:
  toc: true
key: 20240327
tags: Stastistics
lang: en
---

A simple explanation of a random variable is that it connects **<u>the outcome</u> of <u>a random preocess</u> to a number**. A common example is flipping a coin. Flipping a coin 5 times at random and the total number of heads obtained can be considered a random variable. Understanding that flipping a coin 5 times is a random process is not difficult, making it an intuitive concept. So, what does it mean to connect such results to a number?

To understand this, let's discuss 'magnitude or scale' from a mathematical perspective. The outcome of random processes, like rolling dice, carries uncertainty. Can we mathematically express the 'how much' of this uncertainty? If the outcome is expressed numerically, it would allow for the most intuitive interpretation. What if it could even be operated on?... From this approach, we can appreciate the value of defining a random variable. In fact, this level of understanding might be sufficient. However, for those who wish to delve deeper into academic study, we can explore the concept of a random variable more mathematically.

<br/>
## Mathematical Approach
To delve into the concept of a random variable as defined in probability theory, it's necessary to start with some foundational concepts. Although this requires a deep mathematical understanding, I will attempt to approach it in as intuitive a manner as possible. Let's approach the mathematical definition of a random variable step by step

### Measure Theory
To grasp the concept of measure, let's first imagine **"a scenario where a cap is filled with water".**

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/random_variables/water_glass.jpeg">
</p>

<br/>To answer the question "How much water is in the cup?", we <u>define and measure 'volume'</u>. If we assign a 'volume' to a certain set, such as a three-dimentional object, it means we are <u>assigning a concept of 'size' to that set</u>. This concept is referred to as **measure** in mathematics. Measure theory deals with the generalized concept of measure, including size, area, volume, etc., and is a theory that measures and analyzes the size of sets and functions. This theory plays a crucial role, especially in probability theory and functional analysis, which explains why we frequently encounter sets in our study of probability. **What's important to note is that the 'probability' we discuss prepresents this concept of size as a 'measure'.** Therefore, we can only truly understand the definition of probability based on measure theory.

<br/>
### Probability
When we conduct an experiment to obtain results from a certain phenomenon, we achieve what are called realization. This term 'realization' might feel unfamiliar. If you think of it as the outcome which is the result of the experiment, it becomes easier to understand. Now, let's delve into the concept of probability based on measure theory through the example of rolling dice, which is a type of random experiment.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/random_variables/definition_random_variable_1.png">
</p>

<br/> 
In the sample space $$\Omega = \{1,2,3,4,5,6\}$$, to mathematically discuss the magnitude of the event ($$\mathcal{F}$$) where a die lands on 2, we utilize a measure called probability, denoted by $$Pr(\cdot)$$. Through this definition, we articulate that the probability of the event where the die shows a 2 is $$Pr(2) = \frac{1}{6}$$.

$$
\begin{equation} 
\begin{aligned} 
& Pr(1) = Pr(2) = Pr(3) = Pr(4) = Pr(5) = Pr(6) = 1/6
\end{aligned} 
\end{equation}
$$

In other words, **"probability is a measure for the realization from a random experiment"**, and by using the measure known as probability $Pr(\cdot)$$, we can obtain the measured realization of the size of elements within the space.

### $$\sigma$$-field $$\mathcal{B}$$
To define probability without contradictions by introducing the concept of measure, it's necessary to precisely define the objects of measurement. This is where the $$\sigma$$-field comes in. A $$\sigma$$-field is defined as a collection of sets that satisfies certain conditions.


(i) $\emptyset \in \mathcal{B}$  <br/>
(ii) $A \in \mathcal{B} \Rightarrow A^c \in \mathcal{B}$ <br/>
(iii) $A_i \in \mathcal{B} \Rightarrow \cup_{i=1}^{\infty}A_i \in \mathcal{B}$ <br/>

(i) It includes the non-empty set, (ii) the complement, and (iii) is closed under countable unions and intersections of sets $$S$$, defined as a collection of subsets. Given such a collection of sets, we can define a measurable space, which allows for the consistent definition of measure and probability.

<br/>
- **Measure**<br/>
A measure $$\mu$$ is a type of set function in a measurable space $$(U, \mathcal{B})$$ that assigns elements in $$[0,\infty]$$ to elements of the $$\sigma$$-field.
\begin{equation} 
\begin{aligned} 
\mu : \mathcal{B} \rightarrow [0, \infty]
\end{aligned} 
\end{equation}
  - $$\mu(\emptyset) = 0$$: The measure of the empty set is 0.<br/>
  - For any sequence of mutually exclusive sets $$A_j$$, $$A_j$$, the measure of their union is equal to the sum of their measures : $$\mu(\cup_{i=1}^{\infty} A_i) = \sum_{i=1}^{\infty} \mu(A_i)$$.

<br/>
- **Probability**<br/>
Probability refers to a normalized measure on the extire set $$U$$ such that $$\mu(U)=1$$, indicating that the measure satisfies the condition of the total measure of the sample space being 1.

Probability can be described as a measure where the total probability across the entire sample space equals 1.

---

### Definition of a Random Variable
Noew, it's time to examine the definition of a random variable.

**Definition&nbsp;&nbsp; A random variable $$x$$ is a function defined on the sample space $$\Omega$$. This function serves to transform an element of the probability space $$(\Omega, \mathcal{F}, P)$$ into an element of the Boral measurable space $$(\mathbb{R}, \mathcal{B})$$ 

Here, the space created by the set of real numbers is referred to as the BOrel measurable space, and the associated $$\sigma$$-field in this context is termed the Borel set.

<details>
<summary>Borel Measurable Space</summary>
<div markdown="1">

**Borel Measurable Space**: Consists of the set of real numbers $$\mathbb{R}$$ and the Borel $$\sigma$$ algebra $$\mathcall{B}$$. The Borel $$\sigma$$-algebra includes open intervals on the real line and encompasses all sets that can be generated from these intervals. Essentially, this makes it possible to measure events in the commonly dealt with real number space.

</div>
</details>

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/random_variables/definition_random_variable_2.png">
</p>

- $$\Omega$$ : Known as the Space, this represents the entire set of possible elements or outcomes.
- $$\mathcal{F}$$ : Signifies the subsets of the sample space, referred to as Events.
- $$Pr$$ : Acts as the operator that performs measurement, assigning probabilites to elements of the sample space.

Through these complex concepts, we conclude that a random variable is essentially a function that transforms an element of the sample space into a real number. By defining this, we become interested in practically applying the probability of a random variable $$x$$, denoted as $$Pr(x)$$

## Types of Random Variables

Random variables are broadly classified into discrete and continuous types. A random variable that can take on either a finite number of values or a countably infinite number of values, such as the outcome of rolling a dice or baseball game socres, is called a **discrete random variables**. The Probability Mass Function(PMF) of a discrete random variable can assign a clear probability to each value. On the other hand, a random variable that can take values in a continuous range, such as temperature, stock prices, duration, speed, or measurements of an object's length, is called a **continuous random variable**. Although the Probability Density Function(PDF) of a continuous random variable cannot assign a probability to each specific value, it can express the probability over a range of values.

Discrete probability distributions include, notably, the binomial distribution, Poisson distribution, and geometric distribution, while continuous probability distributions include the normal distribution, uniform distribution, and exponential distribution. The following outlines the relations among various probability distributions.
