---
title: "수리통계학 Chapter 3-2"
excerpt: "Exponential Families, Location and Scale Families, Inequalities and Identities"
categories:
 - Statistics
tags:
 - Statistics       
use_math: true
toc: true
toc_sticky: true
---

# 3. Common Families of Distributions

## 3.3 Exponential Families

다음 형태로 표현될 수 있는 모든 pdf, pmf의 모임을 지수족이라고 한다.

\[
 f(x \mid \theta) = h(x)c(\theta)\exp\bigg(\sum_{i=1}^k w_i(\theta)t_i(x)\bigg)
\]

$h(x) \ge 0, c(\theta) \ge 0$이고 $w_i, t_i$들은 모두 실수값을 가지는 함수여야한다.

앞의 포스트에서 소개된 분포들은 대부분 지수족에 속하는 분포이다.

**예 3.1**

이항분포가 지수족에 속하는지 확인해보자.

$$
\begin{align*}
  f(x \mid p) &= \binom{n}{x} p^x(1-p)^{n-x}\\
  &=\binom{n}{x}(1-p)^n \exp \bigg(\log\bigg(\frac{p}{1-p}\bigg)x\bigg) 
\end{align*}
$$

여기서 $h(x) = \binom{n}{x}, c(p) = (1-p)^n, w(p) = \log (p/(1-p)), t(x) =x$라 두면 지수족임을 확인할 수 있다.

$($ $h,c$가 정의역에서 양수인지 확인해야 한다. $)$

**정리 3.1**

$X$가 지수족에 속하는 확률변수라고 하자. 

1. $E\bigg( \sum_i \frac{\partial w_i(\theta)}{\partial \theta_j} t_i (X)\bigg ) = \frac{\partial}{\partial \theta_j}\log c(\theta)$
2. $Var\bigg( \sum_i \frac{\partial w_i(\theta)}{\partial \theta_j} t_i(X)\bigg) = \frac{\partial^2}{\partial \theta_j^2}\log c(\theta) - E\bigg( \sum_i \frac{\partial^2 w_i(\theta)}{\partial \theta_j^2} t_i (X)\bigg )$

식을 보면 깔끔해보이지 않는다. 하지만 적분으로 정의되는 평균과 분산을 미분으로 쉽게 계산할 수 있음을 보여준다.경우에 따라 이 방식이 더 쉬울 수 있다.

**예 3.2**

앞에서 확인한 이항분포를 적용해보자.

$$
\begin{align*}
\frac{d}{dp} w(p) &= \frac{d}{dp}\log \frac{p}{1-p} = \frac{1}{p(1-p)}\\
\frac{d}{dp} \log c(p) &= \frac{d}{dp}n\log (1-p) = \frac{-n}{1-p}
\end{align*}
$$

위 정리의 1번식을 사용하면 

\[
 E\bigg( \frac{X}{p(1-p)} \bigg) = \frac{n}{1-p}
\]

을 얻고 양변에 $np$를 곱하면 $EX = np$를 얻는다.

## 3.4 Location ans Scale Families

하나의 pdf로 부터 여러 형태의 pdf를 만드는 방법들이 있다. 여기서는 3가지 방법을 살펴보기로 한다. 

**정리 4.1**

$f$가 pdf이고 $\mu \in \mathbb R, \sigma > 0$이라 하면 

\[
 g(x \mid \mu, \sigma) = \frac{1}{\sigma} f\bigg(\frac{x - \mu}{\sigma}\bigg)
\]

위와 같이 정의된 $g$도 pdf가 된다.

증명

$g \ge 0$임은 당연하다. 따라서 적분해서 1이 되는지 확인한다.

\[
 \int \frac{1}{\sigma} f\bigg(\frac{x - \mu}{\sigma}\bigg)dx = \int f(y)dy = 1
\]

**정의 4.1**

$f$가 pdf라고 하자. pdf의 모임 $\{f(x - \mu)\}$를 location family라고 한다.

**정의 4.2**

$f$가 pdf라고 하자. pdf의 모임 $\{f(x/\sigma)/\sigma\}$를 scale family라고 한다.

**정의 4.3**

$f$가 pdf라고 하자. pdf의 모임 $\{f((x - \mu)/\sigma)/\sigma\}$를 location-scale family라고 한다.

즉 평행이동과 적절한 상수배로 새로운 pdf를 만들 수 있다는 것이다.

**정리 4.2**

$f$가 pdf라고 하자.  $X$가 $f((x-\mu)/\sigma)/\sigma$를 pdf로 갖는 확률변수라면 $f(z)$를 pdf로 갖는 $X = \sigma Z + \mu$를 만족하는 확률변수 $Z$가 존재한다. 

생성된 pdf가 기존의 확률변수와 어떤 관계를 가지고 있는지 보여주는 정리이다. 앞서 말한 것처럼 적절한 평행이동과 상수배로 표현됨을 확인할 수 있다.

## 3.5 Inequalities and Identities

### Probability Inequalities

**정리 5.1 Chebychev**

$X$가 확률변수 $g(x) \ge 0$라고 하자. 그러면 양수 $r > 0$에 대해

\[
 P(g(X) \ge r) \le \frac{Eg(X)}{r}
\]

증명 

$$
\begin{align*}
    Eg(X) &= \int g(x)f_X(x)dx\\
    &\ge \int_{\{x : g(x) \ge r\}} g(x)f_X(x)dx\\
    &\ge r\int_{\{x : g(x) \ge r\}} f_X(x)dx\\
    &= rP(g(X) \ge r)
\end{align*}
$$

![Chevychev Theorem](../../assets/images/chevychev.png)

검은색이 $EX$, 빨간색이 $aP(X \ge a)$를 나타낸다.

### Identities

**정리 5.2**

$X \sim N(\theta, \sigma^2)$이고 미분가능한 함수 $g$에 대해 $E\mid g'(X)\mid < \infty$가 성립한다고 하자. 그러면

\[
 E(g(X)(X-\theta)) = \sigma^2Eg'(X)
\]

이 정리를 활용하면 고차원의 적률을 쉽게 계산가능하다.

**정리 5.3**

$\chi^2_p$를 자유도가 $p$인 카이제곱분포라고 하자. 임의의 함수 $h$에 대해 다음이 성립한다. 

$$
 Eh(\chi^2_p) = pE\bigg(\frac{h(\chi^2_{p+2})}{\chi^2_{p+2}}\bigg)
$$

기대값이 존재한다고 가정한다.