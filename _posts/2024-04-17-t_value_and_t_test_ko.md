---
title: t-value와 검정(t-test)
sidebar:
  nav: study-ko
aside:
  toc: true
key: 20240417
tags: 통계학
lang: ko
mathjax: true
mathjax_autoNumber: true
---

<p align = "center">
  <img src = "https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/t_distribution_and_t_test/t_test_cover.png">
  <br>
  출처: <a href = "https://datatab.net/tutorial/t-test">DATAtab</a>
</p>

앞서 카이제곱 분포에서 '오차'라는 개념을 접했다. 추론적 통계에 있어서 실제 모집단 값과 표본에서 관찰된 값 사이의 오차를 이해하는 것은 중요하다. 이 오차를 이해함으로써 우리는 표본을 통해 모집단의 실제 특성을 얼마나 정확하게 추론할 수 있는지, 그리고 그 추론에 얼마나 신뢰를 둘 수 있는지를 평가할 수 있다.

이번 섹션에서는 **<u>신뢰도를 고려</u>한 '두 집단'간의 '평균 차이'**를 통계적으로 분석하는 방법을 살펴보려고 한다. 특히, 작은 표본 크기에서의 분석에 관심을 두려한다. 

## 정규 분포의 한계
우리는 앞서 [중심 극한 정리](https://jenniione.github.io/2024/04/06/normal_distribution_and_clt_ko.html#%EC%A4%91%EC%8B%AC-%EA%B7%B9%ED%95%9C-%EC%A0%95%EB%A6%AC%EC%9D%98-%EC%A7%81%EA%B4%80%EC%A0%81-%EC%9D%B4%ED%95%B4)를 통해, 표본 평균들이 정규 분포를 이루며 모집단의 평균을 추정할 수 있음을 보았다. 그러나 이 이론은 샘플의 크기가 충분히 커야한다. 다시 말해 <u>샘플의 크기가 적을 경우 중심 극한 정리는 정규 분포를 보장하지 않는다</u>. 단, 이것이 샘플의 크기가 작다고 정규 분포를 따르지 않는다는 것은 아니니 혼동하면 안된다. 샘플의 크기가 작아도 정규 분포를 따를 수는 있지만 우리는 확신할 수 없다는 것이다. 

또한 z-분포를 이용한 모집단의 추정은 <u>모집단의 분산을 이용한다는 점에서도 한계</u>가 있다. 대부분의 실제 상황에서는 모집단 전체를 조사할 수도 없거니와, 모집단의 분산을 알지 못한다.

t-분포는 이러한 문제점들을 보완할 수 있는 분포로 고안되었다.

## t-value의 논리
단 하나의 표본 밖에 구하지 못 했고, 이것을 통해 모집단을 추정한다고 해보자. 심지어 표본의 크기도 그리 크지 못하다. 꽤나 극단적으로 들릴지 모르지만, 실제로 반번히 일어날 수 있는 문제이다. 이전에도 언급했지만 표본도 크고 그 수도 많다면 최고의 시나리오이다. 하지만 현실은 그리 녹록지 않다. **그럼 이 하나의 표본에서 모집단을 추정함에 있어서 우리를 불안하게 하는 요소는 무엇일까?** 이 작은 표본이 모집단을 정확히 대표하지 못할 가능성이다. 즉, 작은 표본으로 부터 얻은 평균이 모평균과 상당히 다를 수 있다. (물론 그럼에도 모집단과 유사성을 가질 수도 있다.) 그래서 우리는 이 작은 표본이 가지는 불확실성을 통계적으로 관리할 필요가 있다.

예를 들어 주머니에서 숫자 공을 뽑는다고 해보자. 몇 번을 뽑았는데 자꾸만 3이 적힌 공이 뽑힌다. 그럼 어느 순간 아마 주머니에 3이라는 공만 있는 건 아닌가 의심이 된다. 이것을 표본의 관측치를 이해하는 데 적용해 보자. 표본의 관측치들이 꽤나 하나의 값(표본 평균)에 모여있는 모양새를 보인다면, 우리는 모집단의 평균도 이 정도가 될 수 있을 거라고 추측할 수 있을 지 모른다. 반대로, 표본의 관측값이 들쭉날쭉 퍼져있다면 이것으로 모집단을 추정하는 것이 불안해질 지도 모른다. 이것을 통계적으로 이야기할 때, <u>표본의 분산이 적으면 불확실도가 줄어든다</u>고 한다. 

자 그럼 표본평균과 모평균이라는 두 값의 차이를 이해하는 데, 이러한 불확실도( $$SE$$ )의 개념을 도입해보자.

$$ t = \frac{\bar{X} - \mu}{SE} $$ 

여기서 SE(Standard Error)는 표준 오차를 의미한다

표준 오차에 대한 설명은 잠시 미뤄두고, 이러한 형태를 취함으로써 우리는 두 집단간의 차이를 그대로 받아들이는 지 않고, $$SE$$로 나눔으로써 <u>조작된 차이값</u> t를 이용할 것이다. 

실제로 표준 오차 $$SE$$는 표본으로부터 얻은 관측값이 표본 평균으로 부터 떨어진 정도를 의미하며, 다음과 같이 정의된다.

$$
SE = \frac{s}{\sqrt{n}}
$$

s(Standard Deviation)는 표준 편차로, 표준 오차는 표준 편차를 표본 크기의 제곱근으로 나눈값이다.

이것을 적용하면 수식 $$(1)$$ 은 다음과 같아진다.

$$
t = \frac{\bar{X} - \mu}{\frac{s}{\sqrt{n}}}
$$


즉, **t-value는 표본의 분산이 크다면, 두 집단간의 차이값이 작아지도록 설계**된 것이다.

<p align = "center">
  <img src = "https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/t_distribution_and_t_test/t_value.png">
  <br>
  출처: <a href = "https://datatab.net/tutorial/t-test">DATAtab</a>
</p>


## t-분포의 정의
t-value의 모양은 z-score와 닮아있다.

| t-value| z-score |
| ----- |
| <center> $$\begin{align*} & t = \frac{\bar{X} - \mu}{\frac{s}{\sqrt{n}}} \end{align*}$$ </center> | <center> $$\begin{align*} & Z = \frac{\bar{X} - \mu}{\frac{\sigma}{\sqrt{n}}} \end{align*} $$</center> | 

그렇다면 t-value로 정규화한 분포를 그린다면 이것은 무슨 의미를 가질까? 

우선, $$\bar{X} - \mu$$ 을 이해함에 있어 각각의 t-value는 표본 평균이 모평균으로 부터 떨어진 거리(얼마나 다른지)를 표준화하여 나타낸다. 따라서 t-분포는 가능한 모든 표본 평균과 모평균 사이의 표준화된 차이의 분포를 제공할 것이다.

또한, 분모에 모분산 대신 표본의 분산을 활용한 표준 오차을 적용함으로써, <u>작은 표본 크기에서 불확실성이 가중</u>된다. 실제로 t-분포는 정규 분포와 유사한 종모양이지만, **정규 분포보다 꼬리가 두꺼운 모양**을 띈다. $$s$$가 과소평가 되었을 때, t-value가 크게 나타날 수 있고 이는 t-분포의 꼬리 부분에서 더 높은 확률을 갖게 만든다.


<img class="image image--md" src = "https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/t_distribution_and_t_test/t_vs_normal.png" >
<br>
출처: <a href = "https://www.researchgate.net/publication/11984006_Article_7_An_introduction_to_hypothesis_testing_Parametric_comparison_of_two_groups_-_2?_tp=eyJjb250ZXh0Ijp7ImZpcnN0UGFnZSI6Il9kaXJlY3QiLCJwYWdlIjoiX2RpcmVjdCJ9fQ">ResearchGate</a>

우리는 이러한 모집단과 표본의 관계에서 확장하여 "두 집단"간의 차이의 분포를 확인하기 위해 t-분포를 활용할 수 있다.

## t-test의 종류
t-분포가 활용되는 각각의 검정 시나리오에서 t-value의 정의와 t-test 원리를 살펴보자. 

<p align = "center">
  <img src = "https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/t_distribution_and_t_test/types_of_t_test.png">
  <br>
  출처: <a href = "https://datatab.net/tutorial/t-test">DATAtab</a>
</p>

t-test 진행에 앞서, 주의할 점은 이 있다. 아래 모든 종류의 t-test는 각 집단의 모집단이 정규분포를 따른다는 가정을 전제로 한다. 표본의 크기가 충분히 크다면 중심극한 정리에 의해 t-검정 결과가 정규성에 민감하지 않을 수 있지만, 특히 표본의 크기가 작다면 Shapiro-Wilk 검정, Kolmogorov-Smirnov 검정 등을 활용해 정규성을 검정한 후 진행하는 것이 검증의 신뢰도를 높일 수 있다.
또한, 데이터가 정규 분포를 따르지 않는다면 비모수적인 검정방법을 사용하는 것이 더 적절하다.

<p align = "center">
  <img src = "https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/t_distribution_and_t_test/types_of_t_test_normality.png">
  <br>
  출처: <a href = "https://datatab.net/tutorial/t-test">Datatab</a>
</p>

또한 독립표본 t-test, 대응표본 t-test는 추가적인 가정을 중요하게 다뤄야 한다. 
이는 각각의 t-test 시나리오에서 자세히 다뤄보자.

### 단일 표본 t-test

단일 표본 t-test는 주로 한 그룹의 평균이 특정 기준값이나 모집단의 평균과 다른지를 검정하는데 사용한다. t-분포를 위해 앞서 살펴본 모집단과 표본의 관계에서 얻은 t-value가 활용된다. 따라서 검정통계량은 다음과 같다.

$$\begin{align*} & \text{(one sample t-test) } t = \frac{\bar{X} - \mu}{\frac{s}{\sqrt{n}}} \end{align*}$$

직작인의 평균 수면 시간이 권장 수면 시간과 다른지를 알아보는 단일 표본 t-test 를 생각해 보자.

한 회사의 배터리 수명이 40시간 이상 지속된다는 주장을 테스트하려고 한다.15개 배터리의 단순 무작위 표본을 사용하여 평균 44.9시간, 표준 편차 8.9시간을 산출했다. 유의수준 0.05를 사용하여 이 주장을 테스트하자.
{:.warning}

$$
\begin{align*}
& H_0 : \mu = 40 \\
& H_a : \mu > 40 \\
\end{align*}
$$

표본에서 관찰된 평균 수명이 44.9시간으로 나타났기 때문에, 대립가설을 $$\mu > 40$$ 으로 설정하였고, 이에 따라 단측검정(right-tailed test)를 진행하게 된다. 

우선 t-test의 논리를 설명하자면 다음과 같다.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/t_distribution_and_t_test/t_test_one_sample(1).png">
</p>

모평균이 40이라는 가정하에, 주어진 자유도와 모평균를 이용해 t-분포를 그린다. 이 t-분포는 모평균으로 부터 관찰될 수 있는 모든 표본 평균들을 나타낸다. 이 분포는 표준정규 분포와 달리 둘 사이의 불확실성을 조정한 분포이다. 그리고 관찰된 표본 평균이 44.9시간이기 때문에 이 t-분포에서 표본 평균이 40시간 보다 클 수 있는 확률(p-value)을 계산한다. 그리고 이 확률이 우리가 설정한 기준(유의수준, 대체로 0.05) 보다 작다면, 가정 하에 발견되기 어려운 값으로 판단하여, 이 표본 평균은 모평균의 특성을 제대로 반영하지 않는 굉장히 유의미한 차이를 가진다는 결론을 내릴 것이다. 이러한 논리는 카이제곱 검정 원리와도 유사하니 참고하면 좋을 것 같다. 

그럼 t-test를 진행해보자.

$$
\begin{align*}
& \mu=40, \bar{X}=44.9 , s=8.9, n=15, df = 15 - 1 =14 \\
\end{align*}
$$

주어진 조건에 따라 t-value를 계산하면 다음과 같다.

$$
\begin{align*}
& t = \frac{44.9 - 40}{\frac{8.9}{\sqrt{15}}} = 2.13 \\
\end{align*}
$$

이때의 p-value 즉, 자유도가 14인 t-분포 하에 $$t = 2.13$$ 일 확률을 구해보자. 이 계산은 t-분포표 혹은 컴퓨터를 이용한다.

$$
p-value = P(t_{df=14} > 2.13) = 0.026
$$

이 p-value가 의미하는 것은 실제 관찰된 표본 평균(40시간 이상 혹은 44.9시간)이 발견될 확률이 2.6%라는 것이다. 이 값은 우리가 "발견되기 어려운 확률"로 설정한 5%라는 유의수준보다 작다.

$$
p = 0.026 < \alpha = 0.05
$$

따라서, 우리가 관찰한 44.9라는 표본 평균이 나타날 확률은 "발견되기 어려운" 것이고, 귀무가설이었던 모평균이 40이라는 가설을 기각할 수 밖에 없는 두 집단 사이의 유의미한 차이가 있다고 결론을 내린다.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/t_distribution_and_t_test/t_test_one_sample(2).png">
</p>


### 독립 표본 t-test

독립 표본 t-test는 두 개의 독립적인 집단 간의 평균 차이를 통해 <u>두 집단이 같은 모평균을 가지고 있는지</u>를 통계적으로 평가한다. 이것을 다시 말하면 두 집단의 평균 차이가 유의미한지를 판단한다고 할 수 있다. 독립 표본 t-test에서의 검정 통계량은 다음과 같다.

$$
\begin{align*} & \text{(independent samples t-test) } t= \frac{\bar{X_1} - \bar{X_2}}{S_p \sqrt{\frac{1}{n_1} + \frac{1}{n_2}} } \end{align*}
$$

자유도는 $$df = n_1 + n_2 -2 $$ 이다.

이러한 정의를 위해서는 **독립성과 등분산성 가정이 필요**하다. 독립인 두 집단이라는 특수한 상황에서 활용되는 통계량이므로 두 집단이 독립이 아니라면 우리는 쌍체표본 t-test를 택할 것이다. 등분산성은 두집단의 분산이 같다는 것을 의미한다. 이 가정이 왜 필요한지는 독립 표본 시나리오에서의 t-검정 통계량 유도과정은 통해 살펴보자.

#### 검정통계량 유도과정

모평균과 표본의 관계에서 나아가, 독립인 두 집단간의 차이를 불확실성으로 나눈값으로 t-value를 정의해보자.

$$
t = \frac{\bar{X_1} - \bar{X_2}}{SE_{\bar{X_1} - \bar{X_2}}}
$$

분자는 두 집단의 차이, 분모는 두 집단의 차이의 표준 오차(불확실도)를 의미한다.

여기서 두 집단간의 차이의 불확실도를 정의하기 위해 우리는 다음과 같이 합동표준편차 $$s_p$$ (pooled standard deviation)를 채택하기로 한다.

$$
SE_{\bar{X_1} - \bar{X_2}} = s_p \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}
$$

여기서 합동표준편차 $$s_p$$ 는 두 집단의 표본 분산을 합쳐 가중 평균을 낸 것으로, 이 <u>두 분산을 동일한 가중치로 결합</u>한다는 의미를 갖고 있다. ( $$\sqrt{\frac{1}{n_1} + \frac{1}{n_2}}$$ 은 각 집단의 평균에 대한 분산의 기여도를 조정한다.)
그러면 독립 표본에서의 t-value를 다음과 같이 정의된다.

$$
t = \frac{\bar{X}_1 - \bar{X}_2}{\sqrt{\frac{(n_1-1)s_1^2 + (n_2-1)s_2^2}{n_1+n_2-2}} \cdot \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}}
$$

즉, **두 집단으로부터의 분산을 동일한 가중치로 결합을 위해 우리는 등분산성을 가정한다**.

#### 독립 표본 t-test 시나리오

두 대학교에서 각각 학생들의 스트레스 수준을 측정하였다. 대학 A와 대학 B의 학생들을 대상으로 스트레스 점수를 조사하고, 이 두 대학 학생들의 스트레스 수준이 다른지 알아보기 위해 독립표본 t-test를 실시하려고 한다.
{:.warning}

두 집단의 관측치는 다음과 같다.

대학 A의 스트레스 점수 (점): 51, 45, 33, 45, 67

대학 B의 스트레스 점수 (점): 40, 65, 76, 58, 47

자유도 $$= 5 + 5 - 2 = 8$$ 일 때 독립 표본 통계량 정의에 따라 t-value를 구하면 다음과 같다.

$$ t = -1.065$$ 

이때의 p-value를 구하면,

$$
p-value = P(t_{df=8} > -1.065) = 0.317
$$

이고, 

$$
p = 0.317 > \alpha = 0.05
$$

p-value 와 유의수준 0.05를 비교했을 때, p-value의 값이 훠씬 크지 때문에 따라서 두 집단은 통계적으로 유의성을 나타내지 않는다고 할 수 있다.

### 대응 표본 t-test

대응표본 t-test는 그 이름이 다양하다. 쌍체표본(paired), 의존표본(dependent) 이라고도 한다. 그 이름처럼 **동일한 실험 대상에서 얻은 두 관련 표본(즉, 두 관측값의 쌍)사이의 평균 차이를 비교할 때 사용되는 검정방법**을 말한다. 따라서 정규성과 함께 의존성을 가진다면 대응표본 t-test를 진행할 수 있다.

<p align = "center">
  <img src = "https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/t_distribution_and_t_test/paired_t_test.png">
  <br>
  출처: <a href = "https://www.graphpad.com/guides/prism/latest/statistics/stat_graphing_results_paired_t.htm">GraphPad</a>
</p>

위 그래프는 전과 후를 데이터를 선으로 연결함하고 있다. 이처럼 같은 사람이 다른 약을 복용하기 전후의 효과를 측정하거나 치료 전휴의 환자 상태를 측정하는 등 <u>같은 대상이 두 가지 다른 조건을 경험</u>했을 때, <u>시간에 따른 변화를 측정</u>할 때 대응표본 t-test가 활용된다.

독립 표본 t-test에서의 검정 통계량은 다음과 같다.

$$
\text{(paired sample t-test)} t = \frac{\bar{D}}{s_D/\sqrt{n}}
$$

$$s_D$$는 $$D$$ 의 표준오차를 의미한다. 그 원리를 자세히 이해해 보자.

#### 검정통계량 유도과정

두 의존성을 가진 집단의 차이를 앞선 t-value의 논리에 따라 설정하면 다음과 같다.

$$
t = \frac{\bar{D}}{SE_D}
$$

이때, $$\bar{D} = X_i - Y_i$$ 로 각 쌍의 차이의 평균을 의미한다. 여기서 주의할 점이 있다. 독립표본 검정통계량의 분자는 두 그룹의 "평균의 차이"였다. 반면에 대응표본 검정통계량의 분자는 "차이의 평균"을 의미한다. 대응표본에서 우리는 두 개체군에 대해 차이값을 계산한 후 그 차이들의 평균을 구한다. 이러한 접근방식은 **대응표본 t-test가 같은 그룹 간의 차이가 아닌, 그 그룹 안의 개체(또는 서로 관련된 개체)간의 차이를 분석**하기 위해 그 변화에 관심을 갖기 때문이다.

이제 분모에 불확실도를 나타내는 지표를 확인해보자. 우리는 집단 간 차이의 분산을 적극 활용하면 된다. 
즉, 차이( $$D$$ )의 표준 오차인 $$SE_D$$ 를 구하면 된다.

$$
SE_D = \frac{s_D}{\sqrt{n}}
$$

그리고 이 표준 오차는 차이의 표본 표준 편차인 $$s_D$$ 로써 다음과 같이 계산할 수 있다.

$$
s_D = \sqrt{\frac{\sum (D_i - \overline{D})^2}{n - 1}}
$$

그리 어렵지 않은 개념이라고 생각한다. 앞의 내용을 잘 따라왔다면 같은 원리로 진행되기 때문에 이후 설명을 간추리려고 한다. 대응표본의 원리만을 이해하기 위해 이곳으로 바로 왔다면 부디 [단일 표본 t-test](http://jenniione.github.io/2024/04/17/t_value_and_t_test_ko.html#%EB%8B%A8%EC%9D%BC-%ED%91%9C%EB%B3%B8-t-test)을 먼저 살펴보길 바란다. 

그래도 아쉬우니 아주 간단한 대응표본 t-test 시나리오도 보자.

#### 대응표본 t-test 시나리오

최근 개발된 수면 개선 프로그램의 효과를 검증하기 위해 10명의 참가자가 이 프로그램을 사용하기 전후로 수면의 질에 대한 점수를 제출하였다. 이 데이터를 사용하여 대응표본 t-test를 실시해 프로그램의 효과가 통계적으로 유의한지 검증하고자 한다.
{:.warning}

관측치는 다음과 같다.

수면 점수 전 (프로그램 사용 전): 5, 7, 6, 3, 4, 8, 5, 6, 7, 5

수면 점수 후 (프로그램 사용 후): 7, 8, 7, 5, 6, 9, 6, 7, 8, 6

이 관측치를 가지고 대응표본 통계량을 구하면 다음과 같고,

$$ 
t = 8.510
$$

그 확률 p-value는 다음과 같이 계산된다.

$$
p-value = P(t_{df=9} > 8.510) = 0.000013
$$

$$
p = 0.000013 > \alpha = 0.05
$$

그 결과 p-value가 매우 낮기 때문에, 우연히 발생한 결과일 가능성이 매우 낮다고 할 수 있다. 따라서 이 대응표본 t-test를 통해 수면 개선 프로그램이 통계적으로 유의미하게 수면 점수를 개선 시켰다고 해석한다.

사실 이 모든 과정을 우리는 이제 직접 손으로 계산하지 않는다.
프로그래밍을 통해 단 몇 줄의 코드로 쉽게 p-value를 구할 수 있기 때문이다. 그래서 t-test를 "p-value가 0.05보다 작으냐?"라는 결과만으로 접근할 수도 있다. 하지만 그 원리를 이해한다면 많은 통계적 접근 원리와 수학적 논리의 유사성을 파악할 수 있을 것이다. 


<br/><br/>
**참조**<br>
[The t Test](https://www.math.arizona.edu/~jwatkins/ttest.pdf)<br>
[Understanding t-Tests: t-values and t-distributions(Minitab Blog)](https://blog.minitab.com/en/adventures-in-statistics-2/understanding-t-tests-t-values-and-t-distributions)<br>
[CalWorkshop](https://calcworkshop.com/hypothesis-test/one-sample-t-test/#chapter
https://blog.naver.com/gdpresent/221138172138)<br>
[DATAtab](https://datatab.net/tutorial/paired-t-test)