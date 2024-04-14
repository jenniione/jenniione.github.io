---
title: 이항 분포
sidebar:
  nav: study-ko
aside:
  toc: true
key: 20240327
tags: 통계학
lang: ko
mathjax: true
mathjax_autoNumber: true
---



이항 분포에 앞서, 베르누이 분포에 대해 간략히 정리하고, 이항 분포와 베르누이 분포가 어떤 관계가 있는지 알아보자.
## 베르누이 분포
확률 실험의 결과가 성공 혹은 실패로 나타나는 실험을 베르누이 실험(Bernoulli Experiment)라고 한다. 그리고 성공 확률이 $$p$$로 고정된 베르누이 실험에서 성공의 횟수를 나타내는 확률 분포가 바로 **베르누이 분포**이다. 즉, 베르누이 분포는 **확률 변수의 값이 성공 혹은 실패로 나타나는 확률 분포**이며, 그 결과가 성공 혹은 실패, 두 값 중 하나만 가지므로 베르누이 확률 변수는 **이산 확률 변수**라고 할 수 있다. 

$$ x  \{ \text{success, fail} \} \rightarrow \{0, 1\}$$

$$
\begin{equation}
\begin{aligned}
& P(x=0) = 1-p \\
& P(x=1) = p \\ \end{aligned}
\end{equation}
$$

확률 변수 $$X$$가 베르누이 분포에 의해 발생된다면 다음과 같이 표현할 수 있다.

$$
\begin{equation} 
 \begin{aligned} 
& x \sim \text{Bern}(p)
\end{aligned}   
\end{equation}
$$

그리고 그 확률 질량 함수(PMF)는 다음과 같이 수식으로 나타낼 수 있다. 
$$
\begin{split}
\begin{align}
\text{Bern}(x; p) = 
\begin{cases} 
p   & \text{if }x=1, \\
1-p & \text{if }x=0
\end{cases}
\end{align}
\end{split}
$$

여기서 주목해야 할 점은, 베르누이 분포는 **한번의 시행**에 대한 결과에서 **성공 확률 $$p$$**에 집중한 관찰 데이터라는 점이다. 이 점은 이항 분포가 베르누이 분포와 어떻게 다른지를 설명하게 된다.

## 이항 분포의 정의

| DEFINITION |
| ------ |
| **이항 분포(Binomial Distribution)**은 동일한 확률 $$p$$ 로 성공하는 베르누이 시행을 고정된 수 $$n$$ 번을 반복할 때의 성공 횟수를 모델링하는 확률 분포이다. |

이항 분포는 베르누이 시행을 $$n$$번 반복하여 얻게된 확률 분포이다. 다시말해, **이항분포는 베르누이 시행의 확장**이라고 할 수 있다. 단 한 번의 베르누이 시행이 아닌, $$n$$번의 반복된 베르누이 시행에서 성공 횟수에 대한 확률 분포를 모델링한 것이 바로 이항 분포이다.
동전 던지기의 예를 들어보자. 앞면이 나올 확률이 $$p=1/2$$인 동전 던지기를 한번 시행 했을때, 그 결과는 베르누이 분포를 따르게 된다. 하지만 동일한 동전을 10번 던지고 앞면이 나온 횟수를 관찰하는 경우, 이 시나리오는 이항 분포를 따르게 된다. 여기서 핵심은 10번 던지는 동안 **각각의 던지기가 독립적이며, 각 시행의 성공 확률은 $$p$$ 로 동일해야 한다**는 점이다.(원래 베르누이 시행의 성공확률은 고정된 $$p$$를 갖는다.)

이항 분포는 다음과 같이 표현할 수 있으며,

$$
\begin{equation} 
 \begin{aligned} 
x \sim \text{Bin}(n,p)
\end{aligned}   
\end{equation}
$$

이항 분포의 확률 질량 함수(PMF)는 다음과 같이 정의된다.

$$
\begin{equation} 
P_X(x) = \ _{n}C_{x} p^k (1-p)^{n-x} \quad \text{ for } x =0,1,\cdots,n
\end{equation}
$$

## 이항 분포의 이해
### 10번의 동전 던지기 예시
확률 질량 함수를 이해하기 위해서, 앞선 10번의 동전 던지기의 확률을 직접 구해보자.
앞면이 나오는 경우를 성공이라 하고, $$x$$를 성공 횟수라고 하자. 즉, $$x = 0, 1, 2, \cdots, 10$$ 이고, 각각은 앞면이 0번, 1번, 2번, ... 10번 나오는 경우를 의미할 것이다. $$x=2$$일 떄, 즉 10번의 시행 중 동전의 앞면이 2번 나오는 확률을 생각해 보자.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/coin k=2.png">
</p>

그림과 같이 각각의 독립된 $$(\frac{1}{2})^2(1-\frac{1}{2})^{8}$$의 확률이 $$ _{10}C_{2}$$의 경우의 수로 출현할 수 있다. 이것은 다음과 같이 계산된다.

$$
_{10}C_{2}\left(\frac{1}{2}\right)^2 \left(1-\frac{1}{2}\right)^{8} = 0.0439
$$

같은 방법으로, 모든 x에 대해서 그 확률을 계산해 보면 다음과 같다.


$$x=0 ;  \frac{10!}{1!\cdot9!}
\left(\frac{1}{2}\right)^0 \left(1-\frac{1}{2}\right)^{10} = 0.0010
$$

$$
x=1 ;  \frac{10!}{1!\cdot9!}
\left(\frac{1}{2}\right)^1 \left(1-\frac{1}{2}\right)^{9} = 0.0098
$$

$$
x=2 ; \frac{10!}{2! 8!}\left(\frac{1}{2}\right)^2 \left(1-\frac{1}{2}\right)^{8} = 0.0439
$$

<center>⋮</center>

$$
x=10 ; \frac{10!}{10! 0!}\left(\frac{1}{2}\right)^{10} \left(1-\frac{1}{2}\right)^{0} = 0.0010
$$

이것을 히스토그램으로 나타내면 다음과 같다.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/coin distribution.png">
</p>

### 직관적 이항 분포
이항 분포는 동전 던지기처럼 두 가지 결과가 있는 확률적 사건을 몇 번 반복했을 때, 어떤 결과를 얻을 확률을 구하기 위해 사용된다.

실제로 어떻게 활용될 수 있는 지, 보다 직관적인 이해를 위해 실제로 이항 분포의 활용이 고려되는 알아보자.

- 예시 1<br/>
마케팅 팀에서 1,000명의 고객에게 메일을 각각 발송했다. 이전의 경험을 토대로 회신을 받을 수 있는 확률이 0.5라고 가정하자. 자, 발송된 1,000개의 메일에 대해 50명의 고객으로 부터 회신을 받을 확률은 어떻게 될까?

아주 간단한 $$n=1,000$$, $$p=0.5$$인 이항 분포의 확률 $$P_X(50)$$을 구하는 문제이다.
이처럼 이항 분포는 기본적으로 **시행 횟수와 성공 확률이 고정**되었을 때, **성공이 출현할 확률**을 구할 때 활용될 수 있다.

또한, A/B테스를 진행하며 이항 분포의 개념이 활용될 수 있다. 아래 예시를 보자.
- 예시 2<br/>
웹사이트의 버튼 클릭률을 높이기 위해 두 가지 디자인(A와 B)의 효과를 비교하는 A/B테스트를 수행한다고 가정해 보자. 웹사이트 방문자 1,000명에게 B디자인을 노출시킨 후, 150명이 클릭했다. 우리는 디자인 B의 클릭률이 디자인 A의 클릭률 10%와 통계적으로 유의미하게 다른지를 평가하고자 한다.

방문자의 클릭 여부가 독립이라는 가정 하에, 각 웹사이트 방문자가 클릭하는 행위는 클릭(성공) 또는 비클릭(실패)의 이항 결과를 갖는다. 우리는 성공 확률 p를 10%, 시도 횟수 n은 1,000명, 성공 횟수 150명으로 설정하고 이항 검정을 수행할 수 있다.

## 이항 분포의 평균과 분산
총 시행 횟수가 $$n$$, 성공 확률이 $$p$$인 이항 분포를 따르는 확률 변수 X에 대해,

기댓값은

$$E(X) = np$$

분산은

$$Var(X) = np(1-p)$$

이다. 각각의 증명은 다음과 같다.

$$
\begin{split}
\begin{align}
\begin{aligned}
\text{E}[X] 
&= \sum_{x_i \in \Omega} x_i p(x_i) \\
&= 1 \cdot \mu + 0 \cdot (1 - \mu) \\
&= \mu
\end{aligned}
\end{align}
\end{split}
$$
<br/>

$$
\begin{split}
\begin{align}
\begin{aligned}
\text{Var}[X] 
&= \sum_{x_i \in \Omega} (x_i - \mu)^2 p(x_i) \\
&= (1 - \mu)^2 \cdot \mu + (0 - \mu)^2 \cdot (1 - \mu) \\
&= \mu(1-\mu)
\end{aligned}
\end{align}
\end{split}
$$


## 이항 분포의 정규 분포 근사
자, 그럼 이항 분포의 파라미터를 자유롭게 변경하며 이항 분포의 여러 모양을 관찰해 보자. 
이러한 결과를 쉽게 확인할 수 있는 다양한 시뮬레이션이 온라인에 공개되어 있고, 그 중  GeoGebra에서 Parameters of the Binomial Distribution(shanlee) 시뮬레이션을 활용했다.
n이 계속 증가한다면, 즉 시행을 많이 한다면 이항 분포는 어떻게 변할까? 

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/binomial distribution to normal distribution.png">
</p>

50번의 동전 던지기를 시행했을 때 **종모양(bell shape)**의 정규 분포와 유사한 형태를 띄는 것을 확인할 수 있다. 하지만 시뮬레이션을 직접 작동해보면, **$n$ 과 $p$ 의 값이 극단적이지 않은 경우에만 가능**하다는 것을 알 수 있다. $n$ 이 너무 작거나, $n$ 이 충분히 크지만 $p$ 가 너무 작거나 클 경우 정규 분포의 모양과 많이 벗어나게 된다.


<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/small n.png">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/small p.png">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/binomial_distribution/huge p.png">
</p>

수학적으로 이항 분포의 $n$ 이 충분히 커서 $np>=5$, $np(1-p)>=5$ 조건을 만족하면, 이항 분포의 평균이 $np$, 분산이 $np(1-p)$ 인 정규 분포에 근사할 수 있다고 한다. 이는 실제로 시뮬레이션을 통해 직관적으로 이해할 수 있다. 시뮬레이션을 직접 작동해 보면, **$n$ 이 클수록, $p$ 가 0이나 1에 가깝지 않고, 0.5에 가까울수록 정규 분포로의 근사가 더욱 정확**해지는 것을 확인할 수 있다.

타율 3할인 타자가 100번 타석에 들어서면 안타를 얼마나 칠까? 사망률이 30%인 감염병에 100명이 걸렸을 때 실제로 얼마나 사망할까? 등 실제 많은 사건들 이항 분포를 따른다고 할 수 있다. 정규 분포가 이항 분포의 근사값으로 표현된다면 정규 분포 역시 많은 사건을 설명할 수 있는 분포가 될 것이다.

<br/><br/>
**참조**

[Parameters of the Binomial Distribution(shanlee)](https://www.geogebra.org/m/hGkW4vwJ)<br/>
[데이터 사이언스 스쿨](https://datascienceschool.net/02%20mathematics/08.02%20%EB%B2%A0%EB%A5%B4%EB%88%84%EC%9D%B4%EB%B6%84%ED%8F%AC%EC%99%80%20%EC%9D%B4%ED%95%AD%EB%B6%84%ED%8F%AC.html)<br/>
[기초통계 개념정리(김진섭)](https://bookdown.org/mathemedicine/Stat_book/normal-distribution.html#-1)<br/>
