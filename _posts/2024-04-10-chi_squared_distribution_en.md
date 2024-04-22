---
title: Chi-squared test
sidebar:
  nav: study-en
aside:
  toc: true
key: 20240410
tags: Statistics
lang: en
mathjax: true
mathjax_autoNumber: true
---
 


## Definition of Chi-Squared Distribution

| **DEFINITION** |
| ----- |
| **Chi-Squared Distribution** is defined for $$k$$ independent random variables $$X_1,\cdots, X_k$$ each following a standard normal distribution. The distribution of the random variable formed by summing the squares of these variables, <br><center>$$Q = \sum_{i=1}^{k} X_i^2$$</center><br> is called the chi-squared distribution. Hence,  <br><center> $$Q \sim X_k^{2}$$</center><br> where $$k$$ is known as **the degrees of freedom**. |

The probability density function (PDF) for a chi-squared distribution with degrees of freedom $$k$$ is given by:

$$
f(x; k) =\dfrac{1}{\Gamma (r/2) 2^{r/2}}x^{r/2-1}e^{-x/2}
$$

- $\\Gamma(k/2)\$  is the gamma function, which generalizes the factorial to $$(k/2)$$ .

## Understanding the Chi-Squared Distribution
What are degrees of freedom, and why does the chi-squared distribution take such a form? Let’s look at how the chi-squared distribution is graphed.

### Degrees of Freedom k=1
Let’s graph the chi-squared distribution for one standard normal random variable $$X$$ .

With one random variable, the degrees of freedom for the chi-squared distribution can be said to be 1.

- $$ -1.5 \leq x \leq -1$$ and $$ 1 \leq x \leq 1.5$$
<p align="center">
  <img class="image image--xl" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/chi_squared_distribution_k=1(1).png"/>
</p>

Squaring the random variables in the intervals $$ -1.5 \leq x \leq -1$$ and $$ 1 \leq x \leq 1.5$$ , these become variates of the chi-squared distribution. The probabilities are then accumulated in the chi-squared distribution interval $$ 1 \leq q \leq 2.25 $$ .  Repeat this for different intervals.

- $$ -2.5 \leq x \leq 2 $$ and $$ 2 \leq x \leq 2.5 $$

<p align="center">
  <img class="image image--xl" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/chi_squared_distribution_k=1(2).png"/>
</p>

- $$ -0.5 \leq x \leq 0 $$ and $$ 0 \leq x \leq 0.5 $$ 

<p align="center">
  <img class="image image--xl" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/chi_squared_distribution_k=1(3).png"/>
</p>

### Degrees of Freedom $$k \geq 2$$
Now note that the chi-squared distribution represents the 'sum' of squares.

For one degree of freedom, we graphed the distribution of the square of one independent variable. However, with two or more independent variables, we start to graph the distribution of the 'sum' of squares.

For independent random variables $$X_1, X_2$$ , $$ Q = X_1^2 + X_2^2$$ accumulates greater values in the same interval.


<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/chi_squared_distribution_k=2.png"/>
</p>

As the degrees of freedom increase to 3, 4, ..., the chi-squared distribution changes like this:

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/chi_squared_distribution_diff.png"/>
</p>

More random variables being added means greater variance, and the most probable value range also increases, shifting the graph to the right.

## Uses of Chi-Squared Distribution
Why do we need to model the sum of squares of random variables?

The sum of squares is **commonly used in mathematics to handle errors or deviations** - Although absolute values can also be used to eliminate direction, squaring is beneficial for differentiation. Let’s skip MSE and MAE discussions for now. - Up to this point, our understanding of the chi-squared distribution has discussed the distribution form of a new variable arising from the sum of squares of independent variables.  This understanding will later combine with concepts like p-value to expand further. For now, understanding that the sum of squares of independent variables forms such a distribution pattern is sufficient.

However, to take a brief peek, let’s consider **'errors' from a mathematical viewpoint** to guess how the chi-squared distribution might be used. This could be quite interesting.

Let’s think like Gauss and explore the 'error' between experimental measurements or observations and the true values. There might be numerous minute factors causing these errors, and let’s assume each error arises from the sum of these independent factors. By the central limit theorem, each of these errors would form a normal distribution. If scaled, these errors could be transformed into standard normal distributions. Then, a new random variable, which is the sum of the squares of these errors, would form a chi-squared distribution.

Wow, if we have grasped this content, we are prepared to utilize the chi-squared distribution going forward.

## (Pearson) Chi-Squared Statistic

| DEFINITION |
| ------ |
| The following formula is known as the chi-squared statistic or Pearson chi-squared statistic. <br> <center>$$ \chi^2 = \sum_i \frac{(O_i - E_i)^2}{E_i} $$ </center><br> $$ \chi^2$$: chi-squared <br> $$O$$ : Observed values <br >$$E$$ : Expected values |

Although the definition and appearance of the chi-squared distribution might seem different, if we consider $$O_i - E_i$$ as one random variable, the sum of their squares falls under the chi-squared statistic. Dividing by $$E$$ standardizes the variance, adjusting the differences in each $$E_i$$ 's variance.

## Chi-Squared Test
The chi-squared test contrasts the theoretical chi-squared distribution with the chi-squared distribution based on actual observations. It is commonly used for goodness-of-fit tests and contingency analysis. This section will deeply explore the principles behind these tests, moving beyond mere calculations.

### Goodness-of-Fit Test
- Fairness test of a die
Let's test if a die is fair, i.e., if all numbers from 1 to 6 have an equal probability of appearing. For this purpose, let's assume we roll the die 600 times and observe the following frequencies:

| 1 | 2 | 3 | 4 | 5 | 6 |
| ------ | ------ | ------ | ------ | ------ | ------ |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 95 times &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 105 times &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 110 times &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 85 times &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 105 times &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 100 times &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |

To determine fairness, let's calculate the error between observed and true values using the differences squared. If the die were fair, the expected count for each number after 600 rolls would be $$600 / 6 = 100$$ . The error calculation is as follows: (We use the sum of squares to handle the errors)

$$
\chi^2 = \sum \frac{(O_i - E_i)^2}{E_i} = \frac{(95 - 100)^2}{100} + \frac{(105 - 100)^2}{100} + \cdots + \frac{(100 - 100)^2}{100} = 4
$$

Now, **is this error likely under the assumption of a fair die?**

Next, let's see how likely it is to observe an error sum of 4 under theoretical conditions.

Forgetting the observed error, assume we know nothing about the error, and think backward. Suppose there's a chi-squared distribution of 5 random error sums representing all possible probabilities.

What's the probability that my actual observation of 5 error sums occurs? Is it likely enough?

<u>Set a standard</u> of **5% (significance level)**, which is considered extremely low, allowing us to decide if an observation is unusual. If the probability of observing the statistic is less than 5%, it's difficult to view it as a typical error, suggesting <u>there's something unusual about my observed error</u>.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/goodness_of_fit_test(1).png"/>
</p>

Now, we can use the chi-squared table to find $$\chi=x$$ for a 95% probability when the degrees of freedom are 5.

$$
\chi^2(5)_{0.95} = 11.07 
$$

In a chi-squared distribution with 5 degrees of freedom, the sum of errors at 11.07 marks the boundary between 95% on the left and 5% on the right.

Let's compare the actual error sum of 4 with the theoretical threshold of 11.07.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/goodness_of_fit_test(2).png"/>
</p>

Since 4 is less than 11.07, it's within the range of errors that could occur under the assumption of fairness. Thus, we <u>cannot claim the die is unfair based on our observations</u>.

### Contingency Analysis
Contingency analysis is used when there are multiple categorical variables, like the data we often see in spreadsheets. The goal is to determine if there is an association between the categories.

<p align="center">
  <img class="image image--xl" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/crosstab(1)_en.png"/>
</p>

Is there a connection between gender and favorite subject? Let's assume there isn't (null hypothesis).

Under the assumption of independence, we can calculate the expected frequency for each cell. For instance, the expected frequency of males preferring science is calculated as follows:

$$
\frac{(totalfavoringscience) * (total males)} {total participants} = \frac{50 * 60} {100} = 30
$$ 

After calculating the expected frequencies for all cells, they look like this:

<p align="center">
  <img class="image image--xl" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/crosstab(2)_en.png"/>
</p>

Now, let's calculate the chi-squared statistic for the observed discrepancies.

$$
\chi^2 = \frac{(40-30)^2}{30} + \frac{(10-20)^2}{20} +
 \frac{(20-30)^2}{30} + \frac{(30-20)^2}{20}
= 16.666
$$

Compute the theoretical statistic:

With a degrees of freedom of $$(2-1) \times (2-1) = 1 $$ and a p-value of 0.05, the statistic is

$$
\chi^2(1)_{0.95} = 3.841
$$

Therefore, since $$ 3.841 \leq 16.666 $$ , <u>the observed statistic is highly unlikely, suggesting a statistically significant association between the variables</u>.


<br/><br/>
**참조**<br>
[Introduction to Probability Theory(STAT414, PennState Eberly College of Science)](https://online.stat.psu.edu/stat414/lesson/15/15.9)
