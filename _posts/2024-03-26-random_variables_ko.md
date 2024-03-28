---
title: 확률 변수
sidebar:
  nav: study-ko
aside:
  toc: true
key: 20240326
tags: 통계학
lang: ko
mathjax: true
mathjax_autoNumber: true
---

확률 변수를 쉽게 설명하자면 **<u>무작위적인 시행(Random Process)</u>에 따른 <u>결과를 숫자로 연결</u>하는 것**이라고 이해할 수 있다. 가장 일반적인  예로 동전 던지기가 있다. <u>임의로 동전을 5번 던져서</u> 나온 <u>앞면의 합계</u>는 확률 변수라고 할 수 있다. 동전을 5번 던지는 행위가 무작위 시행이라는 것을 이해하기 어렵지 않은, 꽤나 직관적인 개념이다. 그렇다면 이러한 결과를 수치로 연결한다는 것은 어떤 의미가 있을까? 

이를 이해하기 위해 수학의 입장에서 '크기 혹은 규모'에 대해서 이야기 해보려고 한다. 주사위 던지기와 같은 무작위적 시행의 결과는 **불확실성**을 갖는다. 이러한 '얼마나'라는 불확실성의 크기를 수학적으로 표현할 수 있을까? 물론 그 결과가 수치로써 표현된다면 가장 직관적인 해석이 가능할 것이다. 심지어 연산도 가능하다면?... 이러한 접근에서 확률 변수를 정의하는 것의 가치를 이해해 볼 수 있다. 사실 이 정도의 이해만으로도 충분할 수 있다. 하지만 보다 학문적 공부를 진행해보고자 확률 변수의 개념을 수학적으로 탐색해 보고자 한다.

<br/> 
## 수학적 접근

확률론에서 정의하는 확률 변수를 이해하기 위해서는 선행되어야 할 개념들이 있다. 수학적으로 꽤나 심도있는 이해를 요구하지만 가능하다면 직관적으로 이해해 보려고 한다. 차근차근 확률 변수의 수학적 정의에 접근해보자.

<br/> 
### 측도론(Measure Theory)
측도(Measure)라는 개념을 먼저 이해하기 위해 **'컵에 물이 담겨져 있는 상황'**을 가정해보자. 
<br/>

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/random_variables/water_glass.jpeg">
</p>

<br/>'물이 얼마나 담겨 있을까?'라는 질문에 답을 하기 위해 우리는 <u>'부피'를 정의하고 측정</u>한다. 3차원 입체라는 어떠한 집합에 '부피'라는 크기를 부여하게 된다면, 이는 그 <u>집합에 '크기'라는 개념을 부여하는 것</u>이 된다. 이를 수학에서 **측도(Measure)**라고 한다. 측도론은 크기, 면적, 부피 등의 일반화한 측도(Measure)의 개념을 다루는 분야로, 집합과 함수의 크기를 측정하고 분석하는 이론이다. 이 이론은 특히 확률론과 함수해석학에서 중요한 역할을 하는데, 우리가 확률을 공부하면서 자꾸만 집합을 마주치는 이유이기도 하다. **중요한 것은, 우리가 이야기하는 '확률'이 바로 이러한 크기라는 속성을 나타내는 '측도'라는 것이다.** 따라서 측도론에 기반하여 확률을 이해할 수 있어서야 비로소 그 정의를 이해할 수 있다.


<br/> 
### 확률(Probability) 

우리는 어떠한 현상으로부터 결과를 얻기 위해 실험(Experiment)을 하고, 실현값(Outcome)을 얻을 수 있다. 실현값이라는 단어가 다소 생소하게 느껴질 수 있다. 이는 결과값 즉, Outcome이라고 생각한다면 이해가 쉬워진다. 자, 그럼 주사위 던지기라는 확률 실험(Random Experiment)을 통해 측도론에 기반한 확률의 개념을 이해해 보자.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/random_variables/definition_random_variable_1.png">
</p>

<br/> 
표본공간 $$\Omega=\{1,2,3,4,5,6\}$$ 에서 주사위의 눈이 2가 나오는 사건(Event, $$\mathcal{F}$$)의 크기를 수학적으로 말하기 위해, 우리는 확률 $$Pr(\cdot)$$ 라는 측도를 사용할 수 있다. 그리고 이를 정의함으로써 $$Pr(2) = 1/6$$ 와 같은 실현값(Outcome)을 얻을 수 있게 된다.

$$
\begin{equation} 
\begin{aligned} 
& Pr(1) = Pr(2) = Pr(3) = Pr(4) = Pr(5) = Pr(6) = 1/6
\end{aligned} 
\end{equation}
$$

다시말해, **'확률'은 이러한 확률 실험(Random Experiment)의 실현값(Realization)에 대한 측도(Measure)**이며, 우리는 확률 $$Pr(\cdot)$$이라는 측도를 사용하여 공간 내 원소의 크기를 측정한 실현값(Realization)을 얻을 수 있다.

### $$\sigma$$-field $$\mathcal{B}$$
이렇게 측도라는 개념을 도입하여 확률을 모순없이 정의하기 위해서는 측정 대상을 엄밀히 정의하는 과정이 필요한데, 그러한 측정대상을 정의하는 것이 바로 $$\sigma$$-field이다. $$\sigma$$-field는 다음과 같이 정의되는 집합들의 모입이다.

(i) $\emptyset \in \mathcal{B}$  <br/>
(ii) $A \in \mathcal{B} \Rightarrow A^c \in \mathcal{B}$ <br/>
(iii) $A_i \in \mathcal{B} \Rightarrow \cup_{i=1}^{\infty}A_i \in \mathcal{B}$ <br/>

(i)공집합이 아니면서, (ii)여집합, 그리고 (iii) 셀 수 있는 합집합, 교집합에 대하여 닫혀있는 집합 S의 부분집합의 모임이라고 정의된다. 이러한 집합의 모입이 주어졌을 때, 측정할 수 있는 공간, 즉 가측공간(Measurable Space)를 정의할 수 있고, 측도와 확률을 모순없이 정의할 수 있다.

<br/>
- **측도(Measure)**<br/>
측도$$\mu$$란 가측공간 $$(U, \mathcal{B})$$에서 $$\sigma$$-field의 원소를 사용하여 $$[0,\infty]$$의 값을 반환하는 일종의 집합 합수(set function)이다.<br/>
\begin{equation} 
\begin{aligned} 
\mu : \mathcal{B} \rightarrow [0, \infty]
\end{aligned} 
\end{equation}
  - $$\mu(\emptyset) = 0$$: 공집합에 대한 측도응 0이다.<br/>
  - 서로소 집합들 $$A_j$$, $$A_j$$ 들에 대하여 $$\mu(\cup_{i=1}^{\infty} A_i) = \sum_{i=1}^{\infty} \mu(A_i)$$이 성립한다.

<br/>
- **확률(Probability)**<br/>
확률(Probability)이란 전체집합 $$U$$에 대하여 $$\mu(U)=1$$의 크기를 만족하도록 정규화된 측도(Nomarlized Measure)를 의미한다.

<br/>

확률은 전체 표본공간에 대한 확률의 총량이 1인 측도라고 할 수 있다.



---

### 확률 변수의 정의
이제 확률 변수의 정의를 살펴볼 시간이다.

**정의**&nbsp;&nbsp; 확률 변수 $$x$$는 표본공간 $$\Omega$$ 에 정의된 함수를 의미한다. 이 함수는 확률공간$$(\Omega, \mathcal{F}, P)$$ 의 하나의 원소를 Borel 가측공간 $$(\mathbb{R}, \mathcal{B})$$ 의 원소로 변환하는 역할을 수행한다.<br/>
{:.info}

여기서, 실수들의 집합으로 만들어진 공간을 Borel 가측공간(mesurable space)라고 하며, 이 때 $$\sigma$$-field를 Borel set이라고 한다. 

<details>
<summary>Borel 가측공간</summary>
<div markdown="1">

**Borel 가측공간 (Borel Measurable Space)**: 실수 집합 $$\mathbb{R}$$ 과 Borel 시그마-대수 $$\mathcal{B}$$ 로 구성된다. Borel 시그마-대수는 실수선 위에서 열린 구간을 포함하고, 이로부터 생성될 수 있는 모든 집합의 컬렉션이다. 이것은 기본적으로 우리가 흔히 다루는 실수 세계의 사건들을 측정 가능하게 한다.

</div>
</details>

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/random_variables/definition_random_variable_2.png">
</p>

- $$\Omega$$ : 표본공간(sample space)라고 하며, 나올 수 있는 원소들의 전체 집합(=set)을 의미한다
- $$\mathcal{F}$$ : 표본공간의 부분집합을 의미하며 사건(event)이라고 부른다.
- $$Pr$$ : 측도(measure)를 수행하는 연산자로써 표본공간의 원소에 확률을 부여하는 역할한다.

꽤나 어려운 개념들을 거쳐왔지만 결론적으로 확률 변수란 **표본공간의 하나의 원소를 실수값으로 변환해주는 함수**이다. 또한 이를 정의함으로써 우리는 실직절으로 확률 변수$x$의 확률인 $Pr(x)$의 활용에 관심을 갖게 된다.


## 확률 변수의 유형
확률 변수는 크게 이산형 확률 변수와 연속형 확률 변수로 분류된다.
주사위 던지기, 야구경기 점수와 같이 유한하거나 셀 수 있는 무한한 값을 가지는 확률 변수를 이산형 확률변수라고 한다.
반면에 온도, 기간, 속력, 무게 등 

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/random_variables/types of random variables.webp">
</p>
<!-- <p align="center">
  <img src="https://miro.medium.com/v2/resize:fit:1400/format:webp/0*rIxj8CrYFPE9bT2d.png">
</p> -->

<br/><br/>
**참조**

[Probability and Statistics for Data Science (Carlos Fernandez-Granda)](https://cims.nyu.edu/~cfgranda/pages/stuff/probability_stats_for_DS.pdf)<br/>
[ALIDA (Gyubeom Edward Im)](https://alida.tistory.com/84)<br/>
[Types of Probability Distributions (Jagandeep Singh)](https://jagan-singhh.medium.com/types-of-probability-distributions-9333d18ed817)