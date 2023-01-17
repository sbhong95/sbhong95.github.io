---
title: "라돈 - 니코딤 정리"
excerpt: "Radon-Nikodym", "Fubini"
categories:
 - Theoretical Statistics
tag:
 - Absolutely continuous
 - Radon-Nikodym
 - Product measure
 - Fubini
use_math: true
toc: true
toc_sticky: true
---


# 라돈-니코딤 정리 (Radon-Nikodym theorem)

## Absolute continuity

측도 공간$(\mathcal X, F)$에서 측도 $\mu, \nu$가 주어졌다고 하자.

아래의 경우에 $\nu$가 $\mu$에 대해 절대 연속($\mu \ll \nu$)이라고 한다.

$$
\nu(A) = 0 \Rightarrow \mu(A) = 0
$$

## 라돈 니코딤 정리

finite measure $\mu$와 sigma finite measure $\nu$가 주어지고 $\mu \ll \nu$라고 하자.

그러면 다음을 만족하는 nonnegative measurable function $f$가 존재한다.

$$
\mu(A) = \int_A fd\nu = \int f1_Ad\nu
$$

함수 $f$를 라돈-니코딤 도함수라고 부르고 $f = \frac{d\mu}{d\nu}$라고 쓴다.


$\mu$가 확률 측도, $\nu$가 counting measure라면 $f$는 p.m.f.가 된다.

$\nu$가 Lebesgue measure일 경우 $f$는 p.d.f.가 된다.

라돈 니코딤 도함수는 유일하지 않지만 거의 모든 곳에서 같다.


# 푸비니 정리 (Fubini Theorem)

## Product measure

두 공간$(\mathcal{X, A}, \mu), (\mathcal{Y, B}, \nu)$가 측도공간이라고 하자.

$A \land B$를 $A \times B$로 생성된 가장 작은 sigma algebra$(\sigma(A\times B))$라고 하자. 

그러면 product measure $\mu \times \nu$가 $(\mathcal{X \times y, A \times B})$가 유일하게 존재한다.

$$
(\mu \times \nu)(A \times B) = \mu(A)\nu(B)
$$

## Fubini's Theorem

$f$가 nonnegative라면 다음이 성립한다.

$$
\int f d(\mu\times\nu) = \int \int f(x, y)d\nu(y)d\mu(x) = \int \int f(x, y)d\mu(x)d\nu(y) 
$$

$\int |f| d(\mu\times\nu) < \infty$라면 $f$가 nonnegative일 필요는 없다.
