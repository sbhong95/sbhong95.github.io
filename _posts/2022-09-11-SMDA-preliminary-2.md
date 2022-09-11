---
title: "정사영, 최소제곱추정법"
excerpt: "Orthogonal projection, LSE"
categories:
 - Statistical Methodology
tag:
 - Projection
 - Orthogonal
 - Least Square Estimation
use_math: true
toc: true
toc_sticky: true
---


# Orthogonality

적당한 내적 공간 $V$가 주어져 있다고 하자. 내적을 이용하여 두 벡터 간의 각을 아래와 같이 정의한다.

$$
\cos \theta = \frac{\langle x, y\rangle}{\|x\|\|y\|}, \quad x, y \ne 0
$$

두 벡터의 내적이 0이면 $\cos \theta$가 자동적으로 0이 된다는 것을 확인 할 수 있다. 이럴 때 두 벡터가 orthogonal하다고 표현한다.

$$
\begin{align*}
\text{ $x$ and $y$ are orthogonal} &\Leftrightarrow \langle x, y\rangle = 0\\
&\Leftrightarrow x \perp y
\end{align*}
$$

## Orthogonal complement

**정의**

내적 공간 $V$의 부분공간 $S$가 있다고 하자. $S$의 orthogonal complement$(S^\perp)$를 다음 집합으로 정의한다.

$$
S^\perp = \{v \in V : \exists  \ s \in S\text{ s.t. } \langle v, s\rangle = 0\}
$$

즉 $S$의 벡터와 내적해서 0이 나오는 벡터들을 모아놓은 집합이다.


# 정사영, Orthogonal Projection

**정의**

$S \preceq V$일 때 $P_S: V \to V$가 다음 조건을 만족하면 orthogonal projection map이라 한다.

1. $P_S$ is linear.
2. $P_S$ is idempotent $P_S(v) = P_S(P_S(v))$.
3. $P_V$ is symmetric. $\langle P_S(v), w\rangle = \langle v, P_S(w)\rangle$.
4. $v \in S \Leftrightarrow P_S(v) = v, v \in S^\perp \Leftrightarrow P_S(v) = 0$.


$P_S(v)$와 $S$의 관계는 다음 식으로 나타낼 수 있다.

$$
P_S(v) = \argmin_{s \in S} \|v - s\|
$$

한 벡터와 한 공간 사이의 거리를 제일 작게 만들어주는 벡터를 찾아주는 과정이 orthogonal projection이 된다. 이 성질을 Least squre estimation에서 응용할 수 있다.

# LSE

최소제곱추정법(LSE)는 아래 문제를 말한다.

$$
\argmin_\beta \|Y - X\beta\|^2
$$

이 경우 $S = \operatorname{span}(X)$로 놓으면 Orthogonal projection을 찾으면 해결된다.