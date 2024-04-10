---
title: 카이제곱 분포
sidebar:
  nav: study-ko
aside:
  toc: true
key: 20240410
tags: 통계학
lang: ko
mathjax: true
mathjax_autoNumber: true
---
 
<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/chi_squared_distribution_wiki.png">
</p>


## 카이제곱 분포의 정의
카이제곱 분포(Chi-Squared Distribution)은 $k$개의 서로 독립이며, 표준 정규 분포를 따르는 확률 변수 $X_1,\cdots, X_k$ 에 대하여, 각각의 확률 변수를 제곱한 다음 합하여 얻어지는 확률변수 

$$
Q = \sum_{i=1}^{k} X_i^2
$$

의 분포이다. 즉, $Q \sim X_k^{2}$ 이다.

이때, $k$를 자유도라고 하며, 카이제곱 분포의 단일 파라미터가 된다.

자유도가 $k$인 카이제곱 분포의 확률 밀도 함수(PDF)는 다음과 같다.

$$
f(x; k) = \frac{1}{2^{k/2}\Gamma(k/2)} x^{(k/2)-1} e^{-x/2}
$$

- $\(\Gamma(k/2)\)$ 는 감마 함수로, $\(k/2\)$ 의 인자(factorial)에 대한 일반화된 형태이다.

## 카이제곱 분포의 활용
일반적으로 통계에서 제곱의 합을 구하는 행위는 오차나 편차를 분석할 때 유용하다. 카이제곱 분포가 오차나 편차를 다루는 방식에서 어떻게 작용하는지 생각해 보자. 이를 위해서는 앞선 [정규분포와 중심 극한 정리](https://jenniione.github.io/2024/04/06/normal_distribution_ko.html)에 대한 이해가 선행되어야 한다.

예를 들어, 우리가 관찰하려는 확률 변수 $X$가 실험적 측정이나 관측에서 발생한 어떠한 오차 혹은 편차라고 생각해보자. 오차나 편차는 수많은 미세한 요인들의 합으로 이해할 수 있다. 그럼 측정 오차가 여러 독립적인 원인에 의해 발생했다면, 그 합으로 이루어진 오차 $Y$ 는 중심 극한 정리에 의해 정규 분포에 근사한다. 물론, 표준 정규 분포로 스케일링이 가능하다.

카이제곱 분포는 표준 정규 분포된 독립 변수 $Y$ (오차) 들의 제곱 합의 분포를 보려는 시도이다. (제곱은 오차의 방향을 무시, 크기만을 고려하기 위함.)
이때, 만약 자유도가 3개 라면, 표준 정규 분포에서 3개의 변수를 뽑아 제곱하여 합한다. 

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/normal_to_chi.png">
</p>

이러한 과정을 굉장히 많이 반복하여 분포를 확인하면 다음과 같다.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/chi_squared_distribution_ex.png">
</p>

그럼 이 분포가 의미하는 것은 무엇일까? 오차의 합이 10이 나오는 확률은 0.05가 되지 않는다. 실제로 관측되거나 예상되는 값과 오차의 합이 나올 수 있는 확률을 비교함으로써 관측된 값이 우연에 의한 것인지, 혹은 유의미한 것인지를 판단할 수 있다는 것이다.

<br/><br/>
**참조**

