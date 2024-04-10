---
title: 정규 분포와 중심 극한 정리
sidebar:
  nav: study-ko
aside:
  toc: true
key: 20240406
tags: 통계학
lang: ko
mathjax: true
mathjax_autoNumber: true
---

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/normal_distribution_cover.png">
</p>

많은 통계적 검정과 모델링 방법론은 정규 분포를 가정으로 한다. 카이제곱분포, t-분포, F-분포 등 통계학에서 다뤄지는 중요한 분포들 역시 정규분포과 깊은 연관이 있으며, 이로 부터 파생되거나 그 성질을 활용하니, 정규 분포가 없는 통계학은 상상하기 어려울 지경이다.

## 정규 분포의 발견
정규 분포는 가우스 분포 혹은 라플라스 분포라고도 불린다. 혹은 종모양이라고 해서 Bell Curve라고도 하는데, 여기서는 정규 분포(Normal Distribution)이라고 하겠다. 사실 이름이 어떻든 중요한 것은 당시대의 수학자들이 각자의 연구 과정에서 정규 분포를 관찰했다는 것이고, 이것이 이러한 분포를 정의할 필요성을 주었다는 사실이다. 간단하게 몇몇 수학자의 정규 분포의 발견을 보자.

정규 분포는 <u>'이항 분포의 근사'</u>로서 **Abraham de Moivre**에 의해 처음 발표되었다고 한다.

<p align="center">
  <img class="image image--md" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/Abraham_de_moivre.jpg"/>
</p>


Abraham de Moivres(드무아브르)는 이항 분포의 n이 아주 큰 경우 어떤 식에 가까워질 지를 연구하던 중, 다음과 같은 근사식을 찾았는데, 실제로 n이 100을 넘을 정도로 크지 않은 값이여도 비교적 잘 성립한다는 것을 발견했다.

$$
_{n}C_{k} p^k q^{n-k} \approx {\frac{1}{\sqrt{2 \pi npq}} e}^{-\frac{(k-np)^2}{2npq}}
$$

이후 **Johann Carl Friedrich Gauss**(가우스)는 참값과 관측값 사이의 오차를 탐구하던 중 <u>오차들의 분포가 정규 분포를 이룬다</u>는 것을 발견했다.

<p align="center">
  <img class="image image--md" src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/Carl_Friedrich_Gauss.jpeg"/>
</p>

그는 관측치로 부터 참값을 추적하는 연구 중, 참값과 관측값의 차이인 오차들이 대칭성을 가진 특정한 분포를 나타낸다는 것을 알았다. 연구 진행을 위해 이 오차들의 분포를 정의할 필요가 있다고 판단하여 이 분포를 정의하게 되었다.

## 정규 분포의 정의
정규 분포는 **평균 $\mu$ 와 표준편차 $\sigma$ 두 가지 파라미터**로 완전히 정의된다. 

정규 분포는 다음과 같이 표현할 수 있고,

$$
X\sim N(\mu ,{ \sigma  }^{ 2 })
$$

연속 확률 변수 $X에 대해 다음과 같은 확률 밀도 함수는(PDF)를 따른다.

$$
\begin{equation}
\begin{aligned}
f(x; \mu, \sigma) = \frac{1}{\sqrt{2\pi \cdot \sigma^{2}}} e^{-\frac{1}{2} \left(\frac{x-\mu}{\sigma}\right)^{2}}
\end{aligned}
\end{equation}
$$

## 정규 분포의 시뮬레이션
정규 분포는 평균을 기준으로 좌우 대칭적 분포를 띈다. 정규 분포의 평균값이 변함에 따라 어떻게 분포가 이동하는 지 보자.

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/normal_distribution_simulation_mean.png"/>
</p>

또, 분산은 분포가 평균을 기준으로 퍼진 정도를 나타낸다. 분산이 클 수록 넓게 퍼지고, 분산이 작을 수락 뾰족한 형태를 띈다.
<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/normal_distribution_simulation_var.png"/>
</p>


## 중심 극한 정리(Central Limit Theorem, CLT)
사실 이번 포스트는 정규 분포를 빙자한 중심 극한 정리라고 해도 무방하다. 

그만큼 중심 극한 정리는 정규 분포와 떼놓고 말하기 어렵기도 하고, 단순히 '봐봐, 정규 분포가 되지'라고 설명하고 넘어가기에는 중심 극한 정리가 정규 분포를 얼마나 중요하게 만들고 있는지 설명하는데 부족함이 크다고 생각한다.

또, 이 정리를 마치 '어떤 분포든 그 시행을 무수히 하면 정규 분포가 되는 이론'이라고 오해하는 경우도 간혹 있어, 여기서 자세히 공부해 보려고 한다. (쉽게 설명하려는 의도로 같은 의미로 '샘플'과 '표본', '동일한 분포'와 '고정된 분포'라는 표현을 혼용해서 사용하니 참고 바란다.)

**정의**&nbsp;&nbsp; 중심 극한 정리(CLT:Central Limit Theorem)는 다음과 같이 정의된다. 고정된 분포를 가진 집단에서, 독립적인 무작위 샘플링을 시행했을 때, 샘플의 크기(샘플링의 규모)가 클수록 그 <u>샘플의 평균들의 분포(혹은 그 합)는 정규분포를 따른다</u>.
{:.info}

자, 하나 하나 그 의미를 따져보자.

- 고정된 분포를 가진 집단 : 그 분포의 형태는 상관없지만 전혀 다른 분포를 가진 집단에서 샘플링이 되어서는 안된다. 다시 말해, **모집단이 어떠한 특정 분포를 따르더라도 그 모집단에 대해 중심 극한 정리는 유효**하다.
- 독립적인 무작위 샘플링 : 말 그대로 하나 하나의 샘플링이 서로 독립적이며 무작위로 발생해야 한다.
- 샘플링의 크기가 크다면 : 흔히 이를 샘플링의 횟수를 많이 하면이라고 오해하기 쉽다. 하지만 정확히는 **'한 회에 발생하는 샘플링의 규모가 클수록'**을 의미한다.
- 평균들의 분포가 정규분포를 따른다 : '샘플링의 횟수가 많다면 분포가 정규 분포가 된다'라고 오해할 때 간과하기 쉬운 포인트가 **'평균들의 분포가'** 정규 분포를 따른다는 것이다. 이는 각각의 샘플링에서 얻은 평균들의 분포가 정규 분포를 따른다는 것을 의미한다.

종합하여, **<u>어떤 특정 분포를 따르는 모집단이더라도, 그 모집단에서 독립적이고 무작위적인 방식으로 샘플을 추출한다면, 더 큰 규모의 샘플에서 추출하는 방식일수록, 각각의 샘플들로 부터 얻은 평균들의 분포가 정규 분포를 따르게 된다</u>**는 것이다.

### 중심 극한 정리의 직관적 이해
어떤 모집단으로부터 얻은 여러 샘플들에서 평균들을 모았다고 생각해 보자. 한번에 뽑는 샘플의 요소가 많아질 수록 샘플에서 얻은 평균들은 모집단의 특성을 더 잘 반영하게 될 것이다. 이것을 직관적으로 이해하는 것은 어려운 일이 아니다. 

쉬운 예로 여론 조사를 떠올려보자. 우리는 무작위로 뽑은 100명의 집단 보다 1,000명의 집단에서 실시한 여론조사가 국민의 의견을 더 잘 반영한다고 한다. 혹은 믿을만 하다고도 한다. (신뢰성에 대한 이야기 역시 할 이야기가 많지만 우선은 넘어가도록 한다.) 왜 그렇게 생각할까? 더 큰 규모에서 샘플링이 시도된다면 모집단의 특성을 더 잘 나타낼 것이라는 것을 우린 직감적으로 이해할 수 있다. 특히, <u>모집단의 '평균'이라는 특성은 샘플의 규모가 크면 클수록 샘플의 평균에서 더 잘 나타나고, 샘플의 평균들은 모집단의 평균으로 수렴</u>하려고 할 것이다. 

관점을 살짝 틀어보기 위해 **극단적인 상황**을 가정해 보자. 모집단 만큼이나 큰 샘플에서 평균을 얻는다고 생각해 보자. 아마 여러차례 샘플링을 시도하여 평균을 구한다면, 그 값은 웬만하면 모집단의 평균처럼 나올 것이다. 물론 정확히 모집단의 평균이 아닌 값들도 관찰될 되겠지만, <u>작은 오차는 빈번하게 발생할 수 있어도 큰 오차는 드물게 발생</u>할 것이다. 이것은 다음과 같이 해석될 수 있다. **더 큰 샘플링을 시도할 수록 샘플들의 평균은 모집단의 평균을 더 정확히 추정**하며, 추적의 과정에서 발생하는 오차들이 큰 오차보다는 작은 오차들이 나타나는 형태로 나름 대칭성을 갖고 분포한다는 것이다. 

이렇게 생각해보니 중심 극한 정리가 "당연한 거 아니야?"라고 말할 수 있을 만큼 이해할 법 하다.

**'오차'**라는 이야기를 했는데, 사실 가우스도 참값과 관측값으로 부터의 오차를 탐구하다 이 오차들이 정규 분포의 형태를 띈다는 것을 확인하고 이 분포를 정의하게 된 것이니 정규 분포가 앞으로 어떻게 활용될 수 있는지 짐작해 볼 수 있겠다.
 
### 수학적 고찰
앞서 이해한 중심 극한 정리를 수학적 관점에서 다시 정의하자면 다음과 같다.

**정의**&nbsp;&nbsp; 중심극한정리(central limit theorem)은 무작위로 추출된 표본의 크기가 커질수록 표본 평균의 분포는 모집단의 분포 모양과는 관계없이 정규분포 가까워진다는 정리이다. 임의의 분포를 갖는 확률변수 $$x_1, x_2, \cdots, x_n$$ 들이 서로 독립이면서 동일한 분포를 갖고 있다고 하자(=i.i.d).이들의 평균을 $$\mathbb{E}(x_i) = \mu$$, 분산을 $$\text{var}(x_i)=\sigma^2$$ 라고 했을 때 $$\mathbf{x} = [x_1, x_2, \cdots, x_n]^{\intercal}$$ 은 $$n$$ 이 커질수록 다음과 같은 표준정규분포로 수렴하게 된다.</u>.
{:.info}

$$
\begin{equation} 
\begin{aligned}
\frac{\mathbf{x}- n\mu}{\sigma \sqrt{n}} \sim \mathcal{N}(0,1)
 \end{aligned}
\end{equation}
$$

#### 중심 극한 정리의 증명
중심 극한 정리의 증명 방법에는 여러가지 버전이 존재한다. 초기 형태였던 라플라스에 의한 방법은 이항 분포의 정규 분포 근사에 초점이 맞춰져 있고, 현재가 가장 활발히 활용되는 방식은 모멘트 생성 함수의 성질을 이용하는 린데베르그-레비의 중심 극한 정리이다. 이번 섹션에서는 특성 함수와 합성곱을 활용하여 전통적인 방법 보다 직관적인 접근 방법으로 접근해 보려고 한다.

**명제**&nbsp;&nbsp; 독립적이고 동일하게 분포된(i.i.d.) 무작위 변수들의 '합'이, 적절하게 정규화될 때, 정규 분포에 수렴한다.
{:.warning}

- **확률 변수의 합성곱 정의**<br/>
우선, 합성곱이라는 개념을 어떻게 확률변수에 어떻게 적용되는 지 살펴보자.

두 개의 확률 변수 $X$, $Y$이 서로 독립이라고 하자. 그러면 새로운 확률 변수 $Z = X + Y$에 대한 확률은 다음과 같이 정의할 수 있다.

$$
P(Z) = \sum_{k=-\infty}^{\infty}{P(X)P(Y)}
$$

이 부분이 잘 이해가 되지 않는다면, $X$를 동전 던지기의 앞면이 나올 사건, $Y$를 주사위 던지기의 짝수가 나올 사건, $Z$를 동전과 주사위를 던졌을 때 앞면과 짝수가 나올 사건이라고 했을떄, Z의 확률을 구하기 위해, $X$, $Y$의 확률의 곱을 계산하고 있는 자신의 모습을 떠올려보자. 또, 이러한 내용을 전문적으로 아주 잘 설명하고 있는 [이 블로그](https://colah.github.io/posts/2014-07-Understanding-Convolutions/)를 방문해 보길 추천한다.

$X$, $Y$의 확률 밀도 함수를 각각 $f(x)$, $g(x)$라고 하면, $Z = X + Y$의 확률 밀도 함수 $(f*g)(z)$ 는 다음과 같은 함수의 합성곱으로 표현될 수 있다.

$$
(f*g)(z) = \int_{-\infty}^{\infty}f(z-y)g(y)dy = \int_{-\infty}^{\infty}g(z-x)f(x)dx
$$

합이 곱으로 변환된다는 점에 주목하자. 이러한 성질을 확률 변수의 특성 함수를 정의함으로써 활용하고자 한다.

- **확률 변수의 특성 함수 정의**

임의의 확률 밀도 함수 $f_X(x)$에 대한 특성 함수는 다음과 같이 정의한다. (t는 실수)

$$\phi_X(t) = E[e^{itX}] = \int_{-\infty}^{\infty}e^{jtx}f_X(x)dx$$

이러한 특성 함수의 정의에서 다음과 같은 성질로 복소수 지수 함수 $e^{itX}$의 절대값은 항상 1이다.

$$
|e^{itx}| = |\cos(tx) + i\sin(tx)| =  \sqrt{\cos^2(tx) + \sin^2(tx)} = 1 
$$

이러한 특성 함수 정의는 라플라스 변환, 확률 생선 함수, 혹은 모멘트 생성 함수와 같은 다른 변환들과 비교했을 때, 모든 확률 분포에 대해 적분이 존재한다는 매우 큰 장점을 갖는다.

- **맥클로린 급수 전개**

앞선 특성 함수 정의에서 $$e^{jtx}$ 는 맥클로린 급수 전개를 이용해 다음과 같이 전개할 수 있다.

$$
e^{jtx}=\sum_{k=1}^{\infty}\frac{(jtx)^k}{k!}=1+jtx+\frac{(jtx)^2}{2!}+\frac{(jtx)^3}{3!}+\cdots = 1+jtx+\frac{(jtx)^2}{2!}+O(t^2)
$$

$O(t^2)$ 은 네 번째 항부터 마지막까지의 항을 뭉뚱그려 쓴 것이다. 이것을 특성 함수 전개에 적용하면,

$$
\phi_X(t) = \int_{-\infty}^{\infty}e^{jtx}f_Y(t)dy=\int_{-\infty}^{\infty}\left\{1+jtx-\frac{t^2}{2}x^2+O(t^2)\right\}f_X(x)dy\notag
$$

$$
=\int_{-\infty}^{\infty}f_X(x)dy + \int_{-\infty}^{\infty}xf_X(x)dy - \frac{t^2}{2}\int_{-\infty}^{\infty}x^2f_X(x)dy+O(t^2)\notag
$$

$$
=1+jtE\left[x\right]-\frac{t^2}{2}E\left[x^2\right]+O(t^2)
$$

이 된다.

- **정규화된 확률 변수 $Z_i$의 특성 함수**

자, 확률 변수 $X$를 평균이 0($E(x)=0$)이고, 분산이 1(Var[x]=1)로 정규화한 새로운 확률 변수 $Z_i = \frac{X_i - \mu}{\sigma}$에 대한 특성 함수를 보려고 한다. 앞서 특성 함수의 전개를 봤듯이, $Z_i$에 대한 특성 함수는 다음과 같이 정리된다.

$$
\phi_Z(t) = E\left[e^{jtz}\right]=\int_{-\infty}^{\infty}e^{jtz}f_Z(z)dx
$$

$$
=1+jtE\left[z\right]-\frac{t^2}{2}E\left[z^2\right]+O(t^2)
$$

$$
= 1+0-\frac{t^2}{2}+O(t^2) 
$$

$$
= 1-\frac{t^2}{2}+O(t^2)
$$

- **$n$개의 $Z_i$의 합에 대한 특성 함수**
$n$개의 독립적인 확률변수 $Z_i$의 합 $S_n = \sum_{i=1}^{n} Z_i = Z_1 + Z_2 + \cdots + Z_n$에 대한 특성 함수는, 합성곱의 성질을 이용하여 다음과 같이 나타낼 수 있다.

$$\phi_{S_n}(t) = \left( \phi_{Z}(t) \right)^n$$


앞선 정규화된 $Z$의 특성 함수 전개를 적용하면,

$$
\phi_{S_n}(t) = \left( \phi_{Z}(t) \right)^n = [1-\frac{t^2}{2N}+O\left(\frac{t^2}{N}\right)]^N
$$

이 된다. 여기서, $n$을 무한대로 보내면 $O(\frac{t^2}{N})$이 $\frac{t^2}{2N}$ 보다 빠르게 0에 수렴하므로, 그 극한값은 다음과 같이 수렴한다는 것을 알 수 있다.

$$
\lim_{N\rightarrow \infty}\phi_{S_N}(t) = \lim_{N\rightarrow\infty}\left[1-\frac{t^2}{2N}\right]^N=e^{-t^2/2}
$$

## 정규 분포의 중요성

<p align="center">
  <img src="https://raw.githubusercontent.com/jenniione/jenniione.github.io/master/pics/normal_distribution/central limit theorem.webp">
</p>

샘플링 기법에 기반한 추론적 통계에서, 표본 평균들의 분포를 이해하는 것은 모평균을 추적함에 있어 중요하다. 그런데 중심 극한 정리에 따르면 충분히 큰 샘플에서 샘플링이 이루어 졌을 때, 모평균에 대해 전혀 알지 못해도, 이 표본 평균들의 분포가 정규 분포로 수렴한다. 일반적으로 많은 상황에서 우리는 제한된 관측치를 가지고 모집단을 추정해 본다. 이때, 관측치들을 일정하게 샘플링해 얻은 평균값들의 분포를 통해 모집단의 분포를 추정하려는 시도는, 우리가 정규 분포를 필연적으로, 꽤나 자주 마주하게 만들 것이다.


<br/><br/>
**참조**<br/>
[Wikipedia(Abraham de Moivre)](https://en.wikipedia.org/wiki/Abraham_de_Moivre)<br/>
[Wikipedia(Johann Carl Friedrich Gaus)](https://en.wikipedia.org/wiki/Carl_Friedrich_Gauss)<br/>
[Normal Distribution: An Introductory Guide to PDF and CDF(Teena Mary)](https://integratedmlai.com/normal-distribution-an-introductory-guide-to-pdf-and-cdf/)<br/>
[가우시안(Gaussian)-정규분포(Normal Distribution).너란 분포 정말(친절한 데이터 사이언스 강좌)](https://recipesds.tistory.com/entry/%EA%B0%80%EC%9A%B0%EC%8B%9C%EC%95%88Gaussian-%EC%A0%95%EA%B7%9C%EB%B6%84%ED%8F%ACNormal-Distribution-%EB%84%88%EB%9E%80-%EB%B6%84%ED%8F%AC-%EC%A0%95%EB%A7%90)<br/>
[“Python Implementation of Central Limit Theorem: Exploring Sample Data to Infer Population Parameters”(Amanatullah)](https://medium.com/@amanatulla1606/python-implementation-of-central-limit-theorem-exploring-sample-data-to-infer-population-595e39e0c98e)<br/>
[Understanding Convolutions(colah's blog)](https://colah.github.io/posts/2014-07-Understanding-Convolutions/)<br/>
[Characteristic Functions and the Central Limit Theorem(University of Waterloo)](https://sas.uwaterloo.ca/~dlmcleis/s901/chapt6.pdf)<br/>