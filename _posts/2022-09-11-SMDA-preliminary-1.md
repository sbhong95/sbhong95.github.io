---
title: "여러 수학 공간들"
excerpt: "Spaces"
categories:
 - Statistical Methodology
tag:
 - Vector space
 - Metric space
 - Normed space
 - Inner product space
use_math: true
toc: true
toc_sticky: true
---

# 벡터공간 Vector space

수학에서 객체를 다루는데 사용하는 기본적인 공간이다.

전체집합 $V$, 체 $\mathbb F$, 닫힌 연산 $+: V \times V \to V$, 상수배 $\cdot: \mathbb F \times V \to V$으로 벡터공간 $(V, F, +, \cdot)$을 정의한다.

여기서는 실수 체$(\mathbb R)$만 사용하기로 한다.

모든 $x,y,z \in V, \alpha, \beta \in \mathbb R$에 대해 아래 성질을 만족하면 $V$를 벡터 공간이라고 한다.

연산에 대해

1. 교환 법칙 : $x + y = y + x$
2. 결합 법칙 : $(x + y) + z = x + (y + z)$
3. 항등원 : $\exists \ 0$ s,t. $x + 0 = x$
4. 역원 : $\exists -x$ s.t. $x + (-x) = 0$

상수배에 대해

5. 분배 법칙 : $\alpha\cdot (x + y) = \alpha \cdot x + \alpha \cdot y$
6. $\alpha(\beta \cdot x) = \alpha \beta \cdot x$
7. $(\alpha + \beta)\cdot x = \alpha \cdot x + \beta \cdot x$
8. $1 \cdot x = x$ 

## 선형 결합 Linear combination

$a_1,...a_n \in \mathbb R, x_1, ..., x_n \in V$ 가 있을 때, 

$$ 
a_1 \cdot x_1 + \dotsb + a_n\cdot x_n \in V
$$  
로 표현된 벡터를 $x_i$들의 선형결합이라고 하고 $a_i$들을 해당하는 벡터들의 좌표라고 한다.

만약 
$$
a_1 \cdot x_1 + \dotsb + a_n\cdot x_n  = 0
$$
의 해가 $a_1 = \dots = a_n = 0$ 하나만 있을 경우 linearly independent라고 하고 아닌 경우는 linearly dependent라고 한다.

## Linear subspace

벡터공간 $V$의 부분집합 $S$가 벡터 공간이 되면 $V$의 부분공간이라고 하고 $S \preceq V$라고 쓴다.

부분공간이라면 원래 벡터 공간의 연산을 공유한다.


**예제 Linear span**

$A = \{x_1, ..., x_n\} \subseteq V$의 모든 선형 결합을 모아놓은 집합을 span$(A)$라고 하자. 
그러면 span($A$)는 $V$의 부분공간이 된다.

# 거리 공간 Metric space

집합 $M$위에 아래 조건을 만족하는 함수 $d : M \times M \to \mathbb R$이 있으면 $(M, d)$를 거리 공간이라 한다.

모든 $x,y,z \in M$에 대해
1. $d(x, y) \ge 0$
2. $d(x, y) = 0 \Leftrightarrow x = y$
3. $d(x, y) = d(y, x)$
4. $d(x, z) \le d(x,y) + d(y, z)$

거리공간은 벡터 공간일 필요는 없다. 

# Normed space

벡터 공간 $V$에 아래 조건을 만족하는 함수 $\|\cdot\| : V \to \mathbb R$이 있으면 Normed space라고 한다.

모든 $x,y \in V, \alpha \in \mathbb R$에 대해
1. $\|x\| \ge 0$
2. $\|x\| = 0 \Leftrightarrow x = 0$
3. $\|\alpha x\| = |\alpha| \|x\|$
4. $\|x + y\| \le \|x\| + \|y\|$

Normed space에서 $d(x, y) = \|x - y\|$를 정의하면 거리 공간의 정의를 만족한다는 것을 확인할 수 있다. 따라서 $Normed space$는 항상 거리 공간이지만 역은 성립하지 않는다.

# 내적 공간 Inner product space

벡터 공간 $V$에 아래 조건을 만족하는 함수 $\langle \cdot, \cdot\rangle : V\times V \to \mathbb R$이 있으면 내적 공간라고 한다.

모든 $x,y, z \in V, \alpha \in \mathbb R$에 대해
1. $\langle x, x\rangle \ge 0$
2. $\langle x, x\rangle = 0 \Leftrightarrow x = 0$
3. $\langle \alpha x, y \rangle =\alpha\langle x, y\rangle$
4. $\langle x, y + z\rangle = \langle x, y\rangle + \langle x, z\rangle$
5. $\langle x, y\rangle = \langle y, x\rangle$

내적 공간에서 $\|x \| = \sqrt{\langle x,x \rangle}$를 정의하면 Normed space의 정의를 만족한다는 것을 확인할 수 있다. 따라서 내적 공간은 항상 Normed space이지만 역은 성립하지 않는다.

# 비교

Inner product가 주어지면 Norm이 유도되고 유도된 Norm에서 다시 metric이 유도된다. 

Complete Normed space, Complete Inner product space를 각각 $Banach space, Hilbert space$라고 한다.
