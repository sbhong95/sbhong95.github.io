---
title: "측도, 확률"
excerpt: "Measure theory"
categories:
 - Theoretical Statistics
tag:
 - Measure theory
 - Measure Integral
use_math: true
toc: true
toc_sticky: true
---


# 확률 공간

다음 세 가지가 정의되어 있으면 확률 공간이라고 한다. 

$(\mathcal X, \mathcal F, \mathbf P)$

- $\mathcal X$ : 표본 공간
- $\mathcal F$ : $\mathcal X$의 시그마필드
- $\mathbf P : \mathcal F \to [0,1]$ : 확률 함수, 측도 

앞의 두 가지만 있을 경우 $(\mathcal X, \mathcal F)$, 측도 공간이라고 한다. (Measurable space).

**정의 Sigma field, Sigma algebra**

$\mathcal X$의 부분집합들의 모임 $\mathcal F$가 아래 세가지 조건을 만족하면 시그마 필드라고 한다.

1. $\emptyset \in \mathcal F$
2. $A \in \mathcal F \Rightarrow A^c \in \mathcal F$
3. $\{A_i\} \in \mathcal F \Rightarrow \cup A_i \in \mathcal F$

2,3 조건과 드모르간 법칙을 활용하면 적당한 교집합도 포함하고 있다는 것을 확인 할 수 있다.

**예제**

1. 멱집합($\mathcal{P(X)}$)

이 경우 모든 부분집합들을 포함하고 있으므로 당연히 3가지 조건을 만족한다. 하지만 $\mathcal X = \mathbb R^n$일 경우 이 집합은 너무 크다.

2. Borel sigma algebra.

$\mathcal X = \mathbb R^n$일 경우 아래의 $n$-cell로 만들 수 있는 가장 작은 sigma-algebra를 Borel sigma algebra라고 한다.

$$
[a_1, b_1] \times \dotsb \times [a_n, b_n]
$$

시그마 필드의 정의에 따라 $[a_1, b_1]$혹은 $(a_1, b_1)$로 정의하여도 아무런 상관이 없다. 한 쪽은 열고 다른 쪽은 닫아도 마찬가지이다.

# 측도, Measure

**정의 Measure**

측도 공간 ($\mathcal {X, F}$)에서 아래 조건을 만족하는 함수 $\mu : \mathcal F \to [0,\infty]$를 측도 (Measure)라고 한다.

$$
\mu(\bigcup^\infty A_i) = \sum^\infty\mu(A_i), \quad A_i\text{s are disjoint} 
$$

전체 집합에 대한 함수값$(\mu(\mathcal X))$가 1이면 확룰 측도라고 부른다.

전체 집합에 대해 유한할 경우는 finite라고 한다.

전체 집합에 대해 무한하지만 $\mu(A_i) < \infty, \cup A_i = \mathcal X$를 만족하는 집합열이 존재하면 sigma-finite라고 한다.

**예제**

1. Counting measure 

$\mathcal X$가 countable set일 경우 $\mu(A) = |A|$라고 정의한 것을 counting measure라고 한다.

2. Lebesgue measure

$\mathcal X = \mathbb R^n$ 일 경우 $\mu(A) = \int\dotsb\int_A 1 dx_1\dotsb dx_n$라고 정의한 것을 Lebesgue measure라고 한다.

Lebesgue measure는 sigma-finite measure이다.


## Null set

주어진 확률공간에서 

$$
\mu(N) = 0
$$
일 경우 $N$을 Null set이라고 한다. 

Null set을 제외한 곳에서 어떤 명제가 참일 경우, __거의 어디서나__ 성립한다고 한다. (a.e.$\mu$)

# Measureble function

**정의 Measureble function**

두 측도 공간 $(\mathcal {X, F}), (\mathcal {Y, G})$가 있다고 하자. 함수 $f:\mathcal{X \to Y}$가 아래 조건을 만족하면 measurable function이라고 한다.

$$
\forall g \in \mathcal G, \quad f^{-1}(g) \equiv \{x \in \mathcal x : f(x) \in g\} \in \mathcal X
$$

위상을 활용하여 연속함수를 정의하는 방법과 똑같다.

## Random variable

위 정의에서 $X$가 표본공간이고 $Y = \mathbb R^n$, $\mathcal G$가 적절한 Borel sigma field일 경우 $f$를 random variable이라고 한다.


# Measure Integral

4단계를 통해 어떤 함수에 대해 측도로 적분하는 법을 알아보자. 먼저 Indicator function :$1_A(x) = I(x \in A)$라고 하자.

1. Indicator function에 대해서는 다음과 같이 정의한다.

$$
\int 1_Ad\mu = \mu(A)
$$

2. Simple function

유한한 Indicator function들의 선형결합으로 만들 수 있는 함수들을 Simple function이라고 부르기로 하자. Simple function에 대한 적분은 아래와 같다. $(\alpha_i > 0)$

$$
\int Sd\mu = \int \sum\alpha_i 1_{A_i}d\mu = \sum \alpha_i\int 1_{A_i}d\mu = \sum\alpha_i\mu(A_i)
$$

3. Nonnegative function.

$f$로 단조 증가하며 수렴하는 simple function sequence $\{f_i\}$를 만들 수 있다. 이 경우 

$$
\int fd\mu := \lim \int f_nd\mu
$$

로 적분값을 정의한다.

4. General function.

일반적인 함수 $f$를 다음과 같이 표현할 수 있다.
$$
f = f^+ - f^-, \quad f^+ = \max\{f, 0\}, \ \ f^- = -\min\{f, 0\}
$$

$f^+, f^-$는 3번의 nonnegative function이므로 적분값을 구한 다음 차이를 적분값으로 정의한다.

이렇게 정의된 적분값이 존재하는 경우, 

$$
\int f^+d\mu + \int f^-d\mu  = \inf |f|d\mu < \infty
$$

이 함수가 적분가능 (integrable)하다고 부른다.




