---
title: "수리통계학 Chapter 1-2"
excerpt: "Random Variable, Distribution Function"
categories:
 - Statistics
tags:
 - Statistics
use_math: true
toc: true
toc_sticky: true
---

# 1. Probability Theory

## 1.4 Random Variables

많은 경우 표본공간 자체가 수로 이루어진 경우가 있다. 예를 들어 시험 성적이라던가 등등 있다. 하지만 표본 공간이 숫자가 아닌 경우가 더 많을 것이다. 정치적 성향, 좋아하는 음악 장르 등등이 있다.

**정의 4.1 확률 변수 Random Variable**

확률변수 $X$는 표본공간에서 실수로 가는 함수이다. $(X : S \mapsto \mathbb R)$ 

즉 확률 변수는 규칙을 의미한다. 표본공간의 각 사건들을 어떤 실수로 나타낼 것인지를 정한 규칙이다. 그렇기 때문에 사실 확률변수 자체에는 랜덤성이 없다. 랜덤성이 생기는 곳은 실험 혹은 관찰에 나오는 사건에 있다.

## 1.5 Distribution Functions.

각 확률변수 $X$마다 누적분포함수 (c.d.f.)를 정의하자.

**정의 5.1 누적분포함수 Cumulative distribution function**

$X$의 누적분포함수 $F_X(x)$는 다음과 같이 정의한다.

\[F_X(x) = P_X(X \le x)\]

**정리 5.1**

어떤 함수 $F$가 누적분포함수인 것의 필요충분조건은 다음과 같다.

1. $\lim_{x \to -\infty}F(x) = 0, \lim_{x \to \infty}F(x) = 1$
2. $F$는 증가함수이다.
3. $F$는 오른쪽 연속이다. $(\lim_{x \downarrow x_0}F(x) = F(x_0))$

**정의 5.2**

누적분포함수가 연속일 경우 $X$를 연속확률변수, 계단함수일 경우 이산확률변수라고 정의한다. 

누적분포함수가 연속이라는 것은 표본공간이 uncountable을 나타낸다.
이산확률변수는 표본공간이 countable이다.

**정의 5.3 identically distributed**

두 확률변수 $X,Y$가 i.d.라는 것은 모든 집합 $A$에 대해 
\[ P(X = A) = P(Y = A) \]
를 말한다.

위의 정의가 $X = Y$를 말하는 것은 아니라는 것을 알아야 한다. 정의 5.3에서 표본공간은 등장하지도 않았다.

**예시 5.1**

동전 던지기를 3번한다고 하자.
$X =$ 앞면 개수, $Y =$ 뒷면 개수라 하면 모든 $i$에 대해서 $P(X = i) = P(Y = i)$가 성립함을 알 수 있다. 하지만 $X \ne Y$인 것은 당연하다.

**정리 5.2**

다음 문장은 동치이다.
1. 확률변수 $X, Y$는 i.d.이다
2. $F_X(x) = F_Y(x)$

## 1.6 Density and Mass Functions

확률질량함수 _이산형_, 확률밀도함수  _연속형_ 를 알아보자.

**정의 6.1 확률질량함수 Probability mass function, pmf**

이산 확률변수의 확률질량함수는 다음과 같이 정의한다.
\[
f_X(x) = P(X = x)
\]

모든 확률의 합은 1이므로 가능한 값들을 다 더하면 1이어야 한다.

확률질량함수는 모든 이산형 확률변수에 대해 각각 존재한다. 하지만 지금 살펴볼 밀도함수는 그렇지 않다.

**정의 6.2 확률밀도함수 Probability density function, pdf**

연속 확률변수의 확률밀도함수는 분포함수 $F$에 대해 다음을 만족하는 $f$를 말한다.
\[
F_X(x) = \int_{-\infty}^x f_X(t)dt
\]

$F_X$에 따라 $f$가 존재하지 않는 경우가 생기기도 한다. 따라서 pdf가 존재하지 않는 연속형 확률변수가 있지만 여기서는 다루지 않는다.

**정리 1.6.5**

$f_X$가 확률변수 $X$의 pdf 혹은 pmf인 필요충분조건은 다음과 같다.

1. $f_X(x) \ge 0$
2. $\sum f_X(x) = 1$ 또는 $\int f_X(x)dx = 1$

첫 조건은 모든 확률이 0보다 크거나 같다는 확률의 공리를 떠올리면 이해하기 쉽다.
두 번째 조건도 확률의 합이 1이 된다는 것을 생각하면 이해하기 쉽다.