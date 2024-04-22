---
title: 카이제곱 분포와 검정
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
 


## 카이제곱 분포의 정의

| **DEFINITION** |
| ----- |
| **카이제곱 분포(Chi-Squared Distribution)**은 $$k$$ 개의 서로 독립이며, 표준 정규 분포를 따르는 확률 변수 $$X_1,\cdots, X_k$$ 에 대하여, 각각의 확률 변수를 제곱한 다음 합하여 얻어지는 확률변수 <br><center>$$Q = \sum_{i=1}^{k} X_i^2$$</center><br>의 분포이다. 즉, <br><center> $$Q \sim X_k^{2}$$</center><br> 이다. 이때, $k$를 **자유도**라고 한다.|

자유도가 $k$인 카이제곱 분포의 확률 밀도 함수(PDF)는 다음과 같다.

$$
f(x; k) =\dfrac{1}{\Gamma (r/2) 2^{r/2}}x^{r/2-1}e^{-x/2}
$$

- $\\Gamma(k/2)\$ 는 감마 함수로, $\(k/2\)$ 의 인자(factorial)에 대한 일반화된 형태이다.

## 카이제곱 분포의 이해
자유도는 무엇이고, 카이제곱 분포는 왜 저런 모양을 띄는 걸까? 이를 이해해 보기 위해, 카이제곱 분포가 어떻게 그려지는 지 보자.

### 자유도 k=1
표준 정규 분포를 따르는 하나의 확률 변수 $$X$$에 대한 카이제곱 분포를 그려보자. 

하나의 확률 변수이므로 카이제곱 분포의 자유도는 1이라고 할 수 있다. 

- $$ -1.5 \leq x \leq -1$$ 와 $$ 1 \leq x \leq 1.5$$
<p align="center">
  <img class="image image--xl" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/chi_squared_distribution_k=1(1).png"/>
</p>

구간 $$ -1.5 \leq x \leq -1$$ 와 $$ 1 \leq x \leq 1.5$$ 의 확률 변수들을 제곱하면, 이것은 카이제곱 분포의 변량이 된다. 그리고, 제곱함으로써 그 확률값은 카이제곱 분포의 동일한 구간 $$ 1 \leq q \leq 2.25 $$ 에 누적된다. 같은 방식은 다양한 구간에서 반복해 보자.

- $$ -2.5 \leq x \leq 2 $$ 와 $$ 2 \leq x \leq 2.5 $$

<p align="center">
  <img class="image image--xl" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/chi_squared_distribution_k=1(2).png"/>
</p>

- $$ -0.5 \leq x \leq 0 $$ 와 $$ 0 \leq x \leq 0.5 $$ 

<p align="center">
  <img class="image image--xl" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/chi_squared_distribution_k=1(3).png"/>
</p>

### 자유도 $$k \geq 2$$
이제부터 카이제곱 분포가 제곱의 **'합'**임을 주목하자. 

자유도가 1일 때는, 하나의 독립 변수를 제곱한 분포를 그렸다. 하지만, 독립 변수가 2개 이상일 때는 본격적으로 제곱의 '합'의 분포를 그리게 된다.

각각의 독립적인 확률변수 $$X_1, X_2$$ 에 대해 $$ Q = X_1^2 + X_2^2$$ 은 다음과 같이 같은 구간에서 더 큰 값을 누적하게 된다.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/chi_squared_distribution_k=2.png"/>
</p>

자유도가 3, 4, ... 로 점점 커질 때, 카이제곱 분포는 다음과 같이 변화한다.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/chi_squared_distribution_diff.png"/>
</p>

더 많은 확률 변수를 합한다는 것은 분산이 커지고, 가장 큰 확률 값을 갖는 구간 역시 커진다는 것을 의미하며, 그래프가 오른쪽으로 이동한다.

## 카이제곱 분포의 활용
그럼 굳이 확률 변수들의 제곱의 합을 분포로 나타낼 필요성은 무엇일까?

제곱의 합은 사실 수학에서 **오차나 편차 등 '차이'를 다루기 위해 많이 사용**된다. - 물론, 방향성을 없애기 위해 절댓값을 활용할 수도 있지만 제곱이 미분에 유리하다. MSE 와 MAE 에 대한 이야기는 넘어가자.- 사실 지금까지의 카이제곱의 이해는 독립 변수들의 제곱의 합으로 발생하는 새로운 변수의 분포 형태를 이야기한 것이다. 이것이 이후의 p-value 등의 개념과 결합하여 확장되니, 우선은 서로 독립인 변수들의 제곱의 합이 이러한 분포 형태를 띈다라는 것을 이해하고 넘어가는 것으로 충분하다. 

그렇지만 조금 아쉬우니 잠깐 엿보기를 위해, **수학적 시각에서 '오차'**를 바라보며 카이제곱 분포의 쓰임을 짐작해 보려고 한다. 꽤나 흥미로운 이야기가 될 것 같다. 

자, 우리는 가우스처럼 어떤 실험적 측정이나 관측에서 참값과의 차이, 측 '오차'를 탐구해 보려고 한다. 오차가 발생하는 수많은 미세한 요인들이 있을 것이고, 각각의 오차들이 이런 독립적 요인들의 합으로 발생했다고 하자. 그렇다면 중심 극한 정리에 의해 각각의 오차들은 정규 분포가 될 것이다. 정규 분포라면 물론 스케일링을 통해 표준 정규 분포로 변환할 수 있다. 각각의 오차들은 표준 정규 분포가 되었다. 그렇다면 이 각각의 오차들의 제곱의 합이라는 새로운 확률 변수는 카이제곱 분포의 형태가 될 것이다.

와우, 이 내용을 이해했다면 우리는 앞으로 카이제곱 분포를 활용하기 위한 준비가 되었다.

## (피어슨) 카이제곱 통계량

| DEFINITION |
| ------ |
| 다음과 같은 공식을 카이제곱 통계량 혹은 피어슨 카이제곱 통계량이라고 한다. <br> <center>$$ \chi^2 = \sum_i \frac{(O_i - E_i)^2}{E_i} $$ </center><br> $$ \chi^2$$: 카이제곱 <br> $$O$$ : 관측값 <br >$$E$$ : 기댓값 |

앞선 카이제곱 분포의 정의와 모양이 조금 달라보이지만, $$O_i - E_i$$ 를 하나의 확률 변수로 보면, 확률 변수들의 제곱의 합이므로 카이제곱 통계량이고 할 수 있다. 여기서 $$ E $$ 로 나누는 행위는 분산의 정규화를 의미한다. 각각의 $$E_i$$ 의 (분산의) 차이를 조정한다고 생각할 수 있다.


## 카이제곱 검정
카이제곱 검정은 이론상의 카이제곱 분포와 실제 관측에 따른 카이제곱 분포의 차이를 대조 검증하는 것이라고 할 수 있다. 대표적인 적합도 검정과 교차 분석을 해보려고 한다. 이 부분의 이해는 통계하면 들어봤을 법한 t-value, p-value로 확장되니 원리를 정확히 이해할 필요가 있다고 생각한다. 하지만 단순 계산을 넘어 검정의 원리를 설명하는 글들을 많지 않았던 것 같아 적합도 검정에서는 그 원리를 정말 자세하게 다뤄보려고 한다. 

### 적합도 검정
- 주사위의 공정성 검정
주사위 던지를 했는데, 1부텉 6까지의 모든 숫자가 나올 확률이 동일할까? 즉, 이 주사위가 공정할까?에 대한 답을 해보려고 한다. 그래서 실제로 이 주사위를 가지고 600번 던지기를 했다. 그리고 다음과 같은 관측 빈도를 확인 했다.


| 1 | 2 | 3 | 4 | 5 | 6 |
| ------ | ------ | ------ | ------ | ------ | ------ |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 95회 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 105회 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 110회 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 85회 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 105회 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 100회 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |

그럼 공정한지를 판단하기 위해 참값과 관측값 사이의 오차를 이용해 보려고 한다. 만약 이 주사위가 공정했다면 600번의 던지기에서 각 숫자들이 나올 기대 횟수는 $$600 / 6 = 100$$ 회 일 것이다. 그럼 그 오차들은 다음과 같이 계산해 볼 수 있다. (우리는 오차를 다루기 위해 제곱합을 이용하는 것이다.)

$$
\chi^2 = \sum \frac{(O_i - E_i)^2}{E_i} = \frac{(95 - 100)^2}{100} + \frac{(105 - 100)^2}{100} + \cdots + \frac{(100 - 100)^2}{100} = 4
$$

자, 관측에 따른 오차(합)는 4가 된다. 그럼 **이 오차가 주사위가 공정하다는 가정하에 관측될 법한 오차일까?**

이제, 이론 상으로 오차(합)가 4가 나오는 것이 얼마나 가능한 일인지 판단할 것이다. 

앞서 관측된 오차는 잊자. 그리고 오차에 대한 아무런 정보가 없다고 생각하고, 거꾸로 추적해 보자. 어떤 5개의 오차들의 합인 어떤 카이제곱 분포가 있다. 이 카이제곱 분포는 5개의 임의의 오차들의 합으로 가능한 모든 확률값들을 나타내고 있다. 

그럼 이 그래프에서 내가 실제로 관찰한 5개의 오차 합이 나타날 확률은 어떻게 될까? 충분히 발생할 수 있는 오차일까? 

그래서 이런 오차의 합이 나타나는 건 어려워 혹은 가능해라고 판단할 수 있는 <u>기준을 설정</u>할 것이다.  **5%(유의수준)**도 드물다고 말해도 되는 굉장히 작은 확률이라고 생각한다. 그래서 관측치가 나타날 확률이 5%보다 적다면, 이건 일반적인 오차라고 보기 어렵다, 즉 내가 <u>관측한 오차에 뭔가 문제가 있다</u>고 판단할 것이다.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/goodness_of_fit_test(1).png"/>
</p>

그럼 우리는 카이제곱 표를 이용해 자유도가 5일때, 95% 확률을 나타내는 $$\chi=x$$을 찾을 수 있다.

$$
\chi^2(5)_{0.95} = 11.07 
$$

자유도가 5인 카이제곱 분포에서 오차의 합 11.07을 기준으로 왼쪽은 95%, 오른쪽은 5%가 된다.

그럼 관측치의 오차의 합인 4와 이론상의 기준인 11.07을 비교해 보자.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/goodness_of_fit_test(2).png"/>
</p>

4는 11.07보다 작으므로, 충분히 나타날 수 있는 오차의 범위 내에 있다고 할 수 있다. 

즉, 주사위가 공정하다고 가정했을 때, 충분히 발생할 수 있는 오차의 범위에 있다. 따라서 우리는 <u>주사위가 공정하지 않다고 말할 근거가 없다</u>.

가끔 로또를 보며 각각의 번호가 공정한 확률로 나오는 걸까? 궁금할 때가 있다. 자유도가 크고, 관측값 계산이 복잡하겠지만 같은 원리로 적용해 볼 수 있지 않을까?

### 교차 분석
교차 분석은 우리가 다루는 엑셀 데이터처럼 범주형 변수가 여러개일 경우 활용하는 분석 방법이다. 목적은 범주들 간의 연관성이 있는지를 파악하는 것이다.

<p align="center">
  <img class="image image--xl" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/crosstab(1).png"/>
</p>

성별과 선호 과목은 연관성이 있을까? 연관성이 없다고 가정하자.(귀무가설)

두 범주가 독립이라는 가정하에 각각의 기대빈도를 구할 수 있다. 예를 들어 과학을 선호하는 남성의 기대 빈도는 다음과 같이 계산된다.

$$
\frac{(총 과학 선호하는 사람) * (총 남성수)} {총 사람 수} = \frac{50 * 60} {100} = 30
$$ 

모든 셀의 기대빈도를 구하면 다음과 같다.

<p align="center">
  <img class="image image--xl" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/chi_squared_distribution/crosstab(2).png"/>
</p>

관측된 오차의 카이제곱 통계량을 구하자.

$$
\chi^2 = \frac{(40-30)^2}{30} + \frac{(10-20)^2}{20} +
 \frac{(20-30)^2}{30} + \frac{(30-20)^2}{20}
= 16.666
$$

이론적 통계량을 구해보자.

자유도는 $$(2-1) \times (2-1) = 1 $$ 이고 p-value 0.05에 대한 통계량은

$$
\chi^2(1)_{0.95} = 3.841
$$

이다.

따라서, $$ 3.841 \leq 16.666 $$ 이므로 <u>관측 통계량은 굉장히 발생 확률이 낮다고 할 수 있으므로, 두 변수 사이의 통계적으로 유의미한 연관성이 있을 가능성이 높다고 해석</u>할 수 있다. 



<br/><br/>
**참조**<br>
[Introduction to Probability Theory(STAT414, PennState Eberly College of Science)](https://online.stat.psu.edu/stat414/lesson/15/15.9)
