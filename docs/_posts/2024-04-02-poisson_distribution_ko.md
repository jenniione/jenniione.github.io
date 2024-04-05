---
title: 포아송 분포
sidebar:
  nav: study-ko
aside:
  toc: true
key: 20240402
tags: 통계학
lang: ko
mathjax: true
mathjax_autoNumber: true
---

<p align="center">
  <img class="image image--md" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/poisson_distribution/Simeon Denis Poisson.jpg"/>
</p>

프랑스의 수학자 Siméon Denis Poisson는 이산 확률 분포의 한 형태로 포아송 분포를 처음 소개하였다. 이후 1898년 폴란드계 수학자 Ladislaus Bortkiewicz가 프로이센 군대의 군인들이 말차기로 우연히 죽는 빈도를 포아송 분포로 잘 모델링해 보임으로써 포아송 분포의 실제 적용이 이루어졌다.

## 이항 분포의 포아송 분포로의 전환
### 포아송 케이스
앞서 [이항 분포의 시뮬레이션](https://jenniione.github.io/2024/03/27/binomial_distribution_ko.html#%EC%9D%B4%ED%95%AD-%EB%B6%84%ED%8F%AC%EC%9D%98-%EC%A0%95%EA%B7%9C-%EB%B6%84%ED%8F%AC-%EA%B7%BC%EC%82%AC)을 통해, 다양한 경우의 이항 분포 형태를 확인할 수 있었다. 그 중 극단적인 n(시행횟수), p(성공확률)의 값에 대한 이항 분포는 정규 분포로의 근사와는 다른 독특한 분포 형태를 취했다. 특히 **시행 횟수인 n이 충분히 큼에도 불구하고 성공 확률 p값이 지나치게 작을 경우**, 다음과 같은 분포를 보인다는 것을 보았다.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/small p.png">
</p>

이러한 사건은 사실 이항 분포로 설명되는 대부분의 사건들과는 다른 특별한 케이스로, 이항 분포로 설명하기에 최적화되었다고 말하기 어렵다. 포아송 분포는 이러한 특별한 사건을 집중적으로 설명하기 위해 소개된 분포라고 할 수 있다. 포아송 분포가 다루는 사건에 대해 보다 자세히 살펴보자.

### 포아송 케이스에 대한 이항 분포의 한계
포아송 분포의 실제 적용에 기여한  Ladislaus Bortkiewicz의 '프로이센 군대의 군인들이 말차기로 우연히 죽는 빈도' 문제를 생각해 보자. 어느날 프로이센의 군대를 관찰하던 중 군인들이 말차기로 우연히 죽는다는 것을 발견했다. 20년동안 매년 10명 정도의 군인이 말에 치여 사망하는 것 같다. 한해에 5명의 군인만이 말에 차여 사망할 확률을 알 수 있을까?
이 문제를 해결하기 위해 군인이 죽는지(성공)를 관찰하는 이항 분포만을 고려한다고 가정해 보자. 동전 던지기처럼 군인의 죽음을 관찰하는 n번의 시행이 이루어진다고 했을 때, n을 설정한다는 것은 꽤나 모호하다. 그럼에도 1년을 한번의 시행으로 쳐서 20번의 시행이 이루어졌다고 접근하여도 10명 군인이 1년째에 모두 나타거나, 2년째, ..., 20년째에 한번에 나타나는 확률을 구하지 않는 이상 이항 분포의 활용은 꽤나 어려워 보인다. 이는 매년 평균적으로 10명이 죽는다고 해도, 시간을 기준으로 관찰시 **매년 죽은 군인 수라는 사건 발생의 무작위성 때문**이다.

### 포아송 분포로의 접근과 유도
우리는 이 문제를 해결하기 위해 n과 p라는 이항분포의 파라미터에서 벗어나서, '매년 10명'이라는 새로운 파라미터로 문제를 접근할 필요가 있다. 이를 $$\lambda$$ 라고 하자. 즉 <u>$\lambda$ 는 단위 시간/공간 당 평균 발생 횟수</u>가 된다. 이는 이항 분포의 맥락에서 일종의 기댓값으로 $$\lambda = np$$ 가 된다. '평균 10년'이라는 일정한 $$\lambda$$ 이 주어졌을 때, 시간(시행)의 연속성을 적용하여 $$n$$ 을 무한대로 보내면 $$p$$ 는 0으로 접근한다고 볼 수 있다. 

$$
\lim_{n\rightarrow \infty}p=\lim_{n\rightarrow \infty}\frac{\lambda}{n} = 0
$$

그럼, 이항 분포의 확률 밀도 함수에 이를 적용하여 그 극한값을 도출해 보자.


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

따라서,

- (6) : $$n$$ 이 무한대로 갈때, $$k$$는 상대적으로 작은 상수이므로 위와 같은 극한값이 계산된다. 

$$
Pr(K=k) = (\frac{\lambda^k}{k!})e^{-\lambda}
$$

결국 우리는 고정된 $$lambda$$가 주어졌을 때, n을 무한대로 보내는 이항 분포의 확률 밀도 함수를 도출해 냄으로써, 이항 분포의 파라미터로 설명하기 어려운 사건을 $$lambda$$라는 새로운 파라미터 하나로써 표현할 수 있게 되었다.

## 포아송 분포의 정의
**정의**&nbsp;&nbsp; 포아송(Poisson Distribution)은 단위 시간 또는 공간에서 발생하는 사건의 수를 모델링하는 확률 분포이다. 
{:.info}

확률 변수 $$x$$가 포아송 분포를 따르는 경우 다음과 같이 표기하며,

$$
\begin{aligned} 
x \sim \text{Pois}(\lambda)
\end{aligned}   
$$

그 확률 질량 함수는 다음과 같다.

$$
\begin{aligned} 
P(x) = \frac{\lambda^{k} e^{-\lambda}}{k!} \quad \text{ for } k =0,1,2,\cdots
\end{aligned}
$$



## 직관적 포아송 분포
포아송 분포는 특정 시간 간격이나 공간에서 발생하는 드문 사건의 횟수를 모델링하는 사용된다. 다시 말해, **시행 횟수가 굉장히 크지만 드물게 발생할 확률을 가진 이항적 사건에서, 평균값이 주어졌을 때, 특정 값이 발생할 확률을 효과적으로 계산**할 수 있도록 한다. 이러한 확률 계산은 어떤 상황에서 중요하게 활용될 수 있을까?

- 예시 1<br/>
어떤 도시에서 $A$라는 질병이 <u>평균적으로 한 달에 2회</u> 발생한다. 보건 당국은 자원 할당과 질병 대응 준비를 위해 다음 달에 이 질병이 <u>발생하지 않을</u> 수 있을지 알고 싶다.

$$
Pr(K=0) 
$$

$$
= \frac{e^{-2} \times 2^0} {0!}
$$

$$
= 0.1353
$$

질병이 평균적으로 관찰되는 수치를 기반해 보았을 때, <u>다음 달에 이 질병이 발생하지 않을 확률은 13%</u>라고 할 수 있다.


- 예시 2<br/>
이커머스 웹사이트가 특정 마케팅 캠페인이나 이벤트가 없는 일반적인 날을 기준으로 <u>평균적으로 하루 200건</u>의 주문을 처리한다. 운영팀은 예상 주문량에 따라 배송 준비나 고객 서비스 인력을 조정하는 등 효율적인 관리를 수행하기 위해, 현재 어느 정도의 주문 처리 능력을 보유하고 있는 것인지 알고 싶다. 정확히 </u>250건</u>을 처리할 수 있는 확률은 어떻게 될까? 


$$
P(X=250) = \frac{e^{-200} \times 200^{250}}{250!} = 0.000077
$$

이는 웹사이트 운영에 있어서 <u>특정 일의 주문량이 예상치를 초과할 확률이 얼마나 낮은지</u>를 보여준다. 특별히 높은 주문량을 처리할 준비를 해야할 날이 드물다는 정보를 통해, 재고, 배송, 고객 서비스 등의 자원 배치를 효과적으로 계획할 수 있다.

이처럼 포아송 분포는 다양한 상황에서 중요한 정보를 해석하는 데 활용될 수 있다.  


## 포아송 분포의 시뮬레이션
포아송 분포의 파라미터는 $$\lambda$$ 하나이다. 그렇다면 $$\lambda$$ 값이 변함에 따라 포아송 분포는 어떻게 변화하는 지 살펴보자.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/poisson_distribution/poisson_distribution.png">
</p>

위 그래프는 $$\lambda = 1$$로, 그 값이 매우 작을 때, 대부분의 확률이 0 또는 1로 집중되어 있다는 것을 보여준다.

또한 $$\lambda = 10$$, $$\lambda = 30$$ 일 때를 보면, **$$\lambda$$값이 커질 수록, 사건 발생 확률이 더 넓고 고르게 분포하며 그래프의 모양이 정규분포에 근사**할 수 있음을 시각적으로 보여준다.

실제로 포아송 분포는 **$$\lambda$$ 가 커지면 정규분포 $$N(\lambda, \lambda^{2})$$ 에 근사**한다.


<br/><br/>
**참조**

[Wikipedia, Poisson Distribution](https://ko.wikipedia.org/wiki/%ED%91%B8%EC%95%84%EC%86%A1_%EB%B6%84%ED%8F%AC)<br/>
[Angelo's Math Notes(Angelo)](https://angeloyeo.github.io/2021/04/26/Poisson_distribution.html)
