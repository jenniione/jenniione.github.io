---
title: Random Variables
sidebar:
  nav: study-en
aside:
  toc: true
key: 20240327
tags: Statistics
lang: en
---

Understanding a random variable can be simplified as linking **<u>the outcomes of a random process</u> to numbers**. A common example is flipping a coin. Consider flipping a coin five times; the total number of heads represents a random variable. This act of flipping the coin five times is a straightforward concept of a random process. What then does it mean to link such results numerically?

To grasp this, let's discuss 'magnitude or scale' from a mathematical perspective. The outcome of random processes like rolling dice is uncertain. How can we mathematically express this 'how much' uncertainty? Clearly, if we can express results numerically, they are much easier to interpret. And what if these can also be manipulated mathematically? This insight underpins the value of defining random variables. Indeed, this level of understanding may suffice. However, for a more scholarly exploration, let's delve into the mathematical concept of random variables.

<br/>
## Mathematical Approach
Understanding random variables defined in probability theory requires grasping several prerequisite concepts. Although these concepts demand a profound understanding, let's try to approach them intuitively step-by-step.

### Measure Theory
First, consider "a situation where a cup contains water". 

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/random_variables/water_glass.jpeg">
</p>


<br/>To answer 'how much water is there?', we <u>define and measure 'volume'</u>. If we can assign 'volume' to a certain set, such as the three-dimensional object, we are essentially <u>attributing a 'size' to that set</u>. In mathematics, this is known as a **measure**. Measure theory deals with the generalized concepts of measure, such as size, area, and volume, analyzing and measuring the magnitude of sets and functions. This theory plays a crucial role in probability theory and functional analysis, explaining why we frequently encounter sets in our study of probability. **Importantly, the 'probability' we discuss is a measure that represents this concept of magnitude**. Thus, understanding probability based on measure theory is essential to grasping its definition.


<br/>
### Probability
We conduct experiments to obtain results from phenomena and receive outcomes. The term 'Realization' might seem unfamiliar but simply refers to the outcome which is the result of an experiment. Let's understand the concept of probability based on measure theory through a dice-rolling experiment.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/random_variables/definition_random_variable_1.png">
</p>

<br/> 
In the sample space $$\Omega = \{1,2,3,4,5,6\}$$, we use the measure known as probability to $$Pr(\cdot)$$ to define the size of the event ($$\mathcal{F}$$) where the dice shows two, giving us an outcome of $$Pr(2) = \frac{1}{6}$$. 

$$
\begin{equation} 
\begin{aligned} 
& Pr(1) = Pr(2) = Pr(3) = Pr(4) = Pr(5) = Pr(6) = 1/6
\end{aligned} 
\end{equation}
$$

**Thus, 'probability' is the measure for the realization(outcomes) in a random experiment**, allowing us to measure the magnitude of elements within the space using the probability measure $$Pr(\cdot)$$.


### $$\sigma$$-field $$\mathcal{B}$$
To define probability consistently using the concept of measure, we need a well-defined measurement target, known as the $$\sigma$$-field. The $$\sigma$$-field is a collection of sets defined as follows:

(i) $\emptyset \in \mathcal{B}$  <br/>
(ii) $A \in \mathcal{B} \Rightarrow A^c \in \mathcal{B}$ <br/>
(iii) $A_i \in \mathcal{B} \Rightarrow \cup_{i=1}^{\infty}A_i \in \mathcal{B}$ <br/>

(i) It includes the non-empty set, (ii) the complement, and (iii) is closed under countable unions and intersections of sets $$S$$, defined as a collection of subsets. Given such a collection of sets, we can define a measurable space, which allows for the consistent definition of measure and probability.

These are collections of subsets of a set $$S$$ that is (i)<u>the non-empty set</u> and are (ii)<u>closed under complementation</u> and (iii)<u>countable unions and intersections</u>. Given such a set, we can define a measurable space, enabling consistent definitions of measure and probability.

<br/>
- **Measure**<br/>
A measure $$\mu$$ is a set function from a $$\sigma$$-field to $$[0,\infty]$$ within a measurabel space $$(U, \mathcal{B})$$ :<br/>
\begin{equation} 
\begin{aligned} 
\mu : \mathcal{B} \rightarrow [0, \infty]
\end{aligned} 
\end{equation}
  - $$\mu(\emptyset) = 0$$: The measure of the empty set is 0.<br/>
  - For disjoint sets $$A_i$$, $$A_j$$, $$\mu(\cup_{i=1}^{\infty} A_i) = \sum_{i=1}^{\infty} \mu(A_i)$$ holds. : the measure of their union is equal to the sum of their measures.

<br/>
- **Probability**<br/>
Probability is a normalized measure where the total measure of the universal set $$U$$ is 1.

<br/>

Probability thus represents the total measure of probability over the entire sample space as a measure equaling 1.

---

### Definition of a Random Variable
Now, let's examine the definition of a random variable.

| DEFINITION |
| ------ |
| **A random variable** $$x$$ is defined as a function on the sample space  $$\Omega$$. This function ransforms an element of the probability space $$(\Omega, \mathcal{F}, P)$$ into an element of the Borel measurable space $$(\mathbb{R}, \mathcal{B})$$ <br><br>Here, the space formed by the set of real numbers is referred to as the Borel measurable space, and the $$σ$$-field is known as the Borel set. |


<details>
<summary>Borel Measurable Space</summary>
<div markdown="1">

**Borel Measurable Space**: Composed of the real number set $$\mathbb{R}$$ and the Borel $$\sigma$$ algebra $$\mathcall{B}$$. The Borel $$\sigma$$-algebra includes all sets that can be generated from open intervals on the real line, effectively making the commonly encountered real-world events measurable.

</div>
</details>

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/random_variables/definition_random_variable_2.png">
</p>

- $$\Omega$$ : Known as the sample space, representing the complete set of possible outcomes.
- $$\mathcal{F}$$ : Refers to the subsets of the sample space, known as events.
- $$Pr$$ : Acts as the operator performing the measurement, assigning probabilities to the elements of the sample space.

In essence, a random variable transforms an element of the sample space into a real number, further facilitating the practical use of the probabilities of random variables $Pr(x)$.

## Types of Random Variables
Random variables are broadly classified into discrete and continuous types. **Discrete random variables**, such as dice rolls or baseball game scores, have finite or countably infinite values. Their probability mass function (PMF) assigns clear probabilities to each value. Conversely, **continuous random variables**, like temperature or stock prices, span a continuous range of values. Their probability density function (PDF) cannot assign probabilities to specific values but can express probabilities over intervals.

Discrete distributions include the binomial, Poisson, and geometric distributions, while continuous distributions feature the normal, uniform, and exponential distributions. The following diagram illustrates the relationships among various probability distributions.

<br/><br/>
**References**

[Probability and Statistics for Data Science (Carlos Fernandez-Granda)](https://cims.nyu.edu/~cfgranda/pages/stuff/probability_stats_for_DS.pdf)<br/>
[ALIDA (Gyubeom Edward Im)](https://alida.tistory.com/84)<br/>
[Types of Probability Distributions (Jagandeep Singh)](https://jagan-singhh.medium.com/types-of-probability-distributions-9333d18ed817)
