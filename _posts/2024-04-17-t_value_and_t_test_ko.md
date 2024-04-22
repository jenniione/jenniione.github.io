---
title: t-분포와 t-검정
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

앞서 카이제곱 분포에서 '오차'라는 개념을 접했다. 추론적 통계에 있어서 실제 모집단 값과 표본에서 관찰된 값 사이의 오차를 이해하는 것은 중요하다. 이 오차를 이해함으로써 우리는 표본을 통해 모집단의 실제 특성을 얼마나 정확하게 추론할 수 있는지, 그리고 그 추론에 얼마나 신뢰를 둘 수 있는지를 평가할 수 있다.

이번 섹션에서는 **<u>신뢰도를 고려</u>한 '두 집단'간의 '평균 차이'**를 통계적으로 분석하는 방법을 살펴보려고 한다. 특히, 작은 표본 크기에서의 분석에 관심을 두려한다. 

## 정규 분포의 한계
우리는 앞서 [중심 극한 정리](https://jenniione.github.io/2024/04/06/normal_distribution_and_clt_ko.html#%EC%A4%91%EC%8B%AC-%EA%B7%B9%ED%95%9C-%EC%A0%95%EB%A6%AC%EC%9D%98-%EC%A7%81%EA%B4%80%EC%A0%81-%EC%9D%B4%ED%95%B4)를 통해, 표본 평균들이 정규 분포를 이루며 모집단의 평균을 추정할 수 있음을 보았다. 그러나 이 이론은 샘플의 수가 충분히 커야한다. 이것은 다시 말해 <u>샘플의 수가 적다면 정규 분포를 이용한 추정 방식에 어려움</u>이 있다는 의미이기도 하다. 또한 z-분포를 이용한 모집단의 추정은 <u>모집단의 분산을 이용한다는 점에서도 한계</u>가 있다. 대부분의 실제 상황에서는 모집단 전체를 조사할 수도 없거니와, 모집단의 분산을 알지 못한다. t-분포는 이러한 문제점을 해결하기 위해 고안된 분포이다.

## t-value의 논리
단 하나의 표본 밖에 구하지 못 했고, 이것을 통해 모집단을 추정한다고 해보자. 심지어 표본의 크기도 그리 크지 못하다. 꽤나 극단적으로 들릴지 모르지만, 실제로 빈번히 일어나는 상황이다. 다른 포스트에서도 언급했지만 표본도 크고 그 수도 많다면 최고의 시나리오겠지만, 현실은 그리 녹록지 않다. 그럼 이 하나의 표본에서 모집단을 추정함에 있어서 우리를 불안하게 하는 요소는 무엇일까? 이 작은 표본이 모집단을 정확히 대표하지 못할 가능성이다. 즉, 작은 표본으로 부터 얻은 평균이 모평균과 상당히 다를 수 있다. 그래서 우리는 이 작은 표본이 가지는 불확실성을 통계적으로 관리할 필요가 있다.

예를 들어 주머니에서 숫자 공을 뽑는다고 해보자. 몇 번을 뽑았는데 자꾸만 3이 적힌 공이 뽑힌다. 그럼 어느 순간 아마 주머니에 3이라는 공만 있는 건 아닌가 의심이 된다. 이것을 표본의 관측치를 이해하는 데 적용해 보자. 표본의 관측치들이 꽤나 하나의 값(표본 평균)에 모여있는 모양새를 보인다면, 우리는 모집단의 평균도 이 정도가 될 수 있을 거라고 추측할 수 있을 지 모른다. 반대로, 표본의 관측값이 들쭉날쭉 퍼져있다면 이것으로 모집단을 추정하는 것이 불안해질 지도 모른다. 이것을 통계적으로 이야기할 때, **표본의 분산이 적으면 불확실도가 줄어든다**고 한다. 

자 그럼 표본평균과 모평균이라는 두 값의 차이를 이해하는 데, 이러한 불확실도( $$SE$$ )의 개념을 도입해보자.

$$
t = \frac{\bar{X} - \mu}{SE}
$$

  - SE(Standard Error) : 표준 오차

표준 오차에 대한 설명은 잠시 미뤄두고, 이러한 형태를 취함으로써 우리는 두 집단간의 차이를 그대로 받아들이는 지 않고, $$SE$$로 나눔으로써 조작된 차이값 t를 이용할 것이다. 

실제로 표준 오차 $$SE$$는 표본으로부터의 관측값이 표본 평균으로 부터 떨어진 정도를 의미하며, 다음과 같이 정의된다.

$$
SE = \frac{s}{\sqrt{n}}
$$

- s(Standard Deviation) : 표준 편차

이것을 적용하면 수식 $$(1)$$ 은 다음과 같아진다.

$$
t = \frac{\bar{X} - \mu}{\frac{s}{\sqrt{n}}}
$$


즉, **t-value는 표본의 분산이 크다면, 두 집단간의 차이값이 작아지도록 설계**된 것이다.

<p align = "center">
  <img class="image image--md" src = "https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/t_distribution_and_t_test/t_value.png">
  <br>
  출처: <a href = "https://datatab.net/tutorial/t-test">DATAtab</a>
</p>


## t-분포의 정의
t-value의 모양은 z-score와 닮아있다.

| t-value| z-score |
| ----- |
| <center> $$\begin{align*} & t = \frac{\bar{X} - \mu}{\frac{s}{\sqrt{n}}} \end{align*}$$ </center> | <center> $$\begin{align*} & Z = \frac{\bar{X} - \mu}{\frac{\sigma}{\sqrt{n}}} \end{align*} $$</center> | 

그렇다면 t-value로 정규화한 분포를 그린다면 이것은 무슨 의미를 가질까? 

중심극한정리에 의해 각각의 표본 평균은 모집단 평균에 대해 정규 분포를 이루는 경향이 있다. 우리는 이 표본 평균들의 분포를 t-value를 이용해 정규화 할 수 있고, 그 분포는 작은 표본에 대한 불확실도가 가중된 모양을 띄게 될 것이다.

각각의 t-value는 표본 평균이 모평균으로 부터 떨어진 거리(얼마나 다른지)를 표준화하여 나타낸다. 따라서 t-분포는 가능한 모든 표본 평균과 모평균 사이의 표준화된 차이의 분포를 제공할 것이다.


표본 평균과 모집단을 단순히 "두 집단"으로 보고 일반화할 수 있다. t-분포는 이러한 두 집단 사이에서 하나의 집단에서 다른 집단과의 차이의 분포를 나타낸다.

그럼 이론적으로 하나의 모집단에서 무작위로 추출된 많은 독립적인 표본에 대해 t-value를 이용해 표준화 하면 이 값들은 t-분포 형태를 띄게 된다. 

이때, 
실제로 t-분포는 정규 분포와 유사한 종모양이지만, **정규 분포보다 꼬리가 두꺼운 모양**을 띄게 된다. 이것은 모분산 대신 표본의 분산을 적용함으로써, <u>작은 표본 크기에서 불확실성이 가중</u>되기 때문이다. $$s$$가 과소평가 되었을 때, t-값이 크게 나타날 수 있고 이는 t-분포의 꼬리 부분에서 더 높은 확률을 갖게 만든다.

<p align = "center">
  <img class="image image--md" src = "https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/t_distribution_and_t_test/t_vs_normal.jpeg">
  <br>
  출처: <a href = "https://analystprep.com/cfa-level-1-exam/quantitative-methods/t-distribution/">AnalystPREP</a>
</p>

## t-test의 종류
표본과 모집단을 좀 더 일반화해서 어떤 두 집단간의 차이를 이해하는데 t-분포를 활용할 수도 있다. 각 상황에 따라 t-value는 약간의 차이가 있겠지만, 한 집단의 분산으로 그 차이를 조정한다는 원리는 유지된다. t-분포를 이용한 검정 시나리오를 살펴보자.
### 단일 표본 t-test
단일 표본 t-test는 주로 한 그룹의 평균이 특정 기준값이나 모집단의 평균과 다른지를 검정하는데 사용한다. 직작인의 평균 수면 시간이 권장 수면 시간과 다른지를 알아보는 단일 표본 t-test 를 생각해 보자.

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




같은 모집단에서 추출된 샘플들을 가지고, 모집단의 평균으로 추정되는 값($$\mu = c$$)과 같은지 검정
         
검정통계량
$$
t = \frac{\bar{X}-\mu}{s / \sqrt{n}}
$$


### 독립 표본 t-test

$$
t = \frac{\bar{X}_1-\bar{X}_2-c}{S_{p}\sqrt{\frac{1}{n_{1}}+\frac{1}{n_{2}}}}
$$


$$
S_{p} = \sqrt{\frac{(n_{1}-1)s^2_{X_{1}}+(n_{2}-1)s^2_{X_{2}}}{n_{1}+n_{2}-2}}
$$

### 대응 표본 t-test

$$
t=\frac{\bar{D}-d}{s/\sqrt{n}}
$$

$$\bar{D}$$ : 대응표본 차이의 평균 - 점수차이의 평균  
$$d$$ : 모평균 차이 



두 집단 사이의 차이를 알고 싶어서
물론 평균이 그 차이를 보여줄 수도 있지만, 그 차이가 믿을 만한지 모르겠다.


작은 표본으로부터의 추론
알려지지 않은 모집단
실제 적용의 높은 가능성

정규분포처럼 생겼지만, 꼬리가 더 두껍 > 불확실성이 더 커진다 / 분산이 커진다



<br/><br/>
**참조**<br>
[Understanding t-Tests: t-values and t-distributions(Minitab Blog)](https://blog.minitab.com/en/adventures-in-statistics-2/understanding-t-tests-t-values-and-t-distributions)
https://calcworkshop.com/hypothesis-test/one-sample-t-test/#chapter
https://blog.naver.com/gdpresent/221138172138