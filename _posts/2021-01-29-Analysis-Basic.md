---
title: "해석개론 기초 정의"
excerpt: "Cartesian product, Relation, Order"
categories:
 - Analysis
tag:
 - Cartesian Product
 - Relation
use_math: true
toc: true
toc_sticky: true
---

# 기본적인 정의들

 바닥부터 시작하는 정의들을 한번 살펴보자.

## Cartesian Product

두 집합 $S, T$에 대해서  아래의 집합을 Cartesian product $S \times T$라고 하기로 한다.

\[
    S \times T = \{(x, y) : x \in S, y \in T\}
\]

즉 각 집합에서 원소를 하나씩 뽑아서 만들 수 있는 모든 순서쌍을 모아놓은 집합이다. 뭐 별거 있나 싶은 이유는 자연스럽게 사용하고 있기 때문이다.

**예**

\[
    \mathbb R^2 = \{(x,y): x \in \mathbb R, y \in \mathbb R\}
\]

평면 $\mathbb R^2$를 보면 Cartesian product의 정의에 잘 부합함을 볼 수 있다. 

## Relation

$S$의 Relation이라는 것은 cartesian product $S \times S$의 부분집합을 말한다.

$\mathcal R$이 $S$ relation이면 다음과 같이 표기한다. 

\[
 x \sim y \Leftrightarrow (x,y) \in \mathcal R     
\]

추상적인 정의라서 내용이 쉽게 다가오지 않는다.

## Order

Order는 relation의 하나로 다음 성질들을 만족한다.

1. $x, y \in S$에 대해 다음 중 하나만 성립한다.
$$ x < y \quad x = y \quad y < x$$
2. $x,y,z \in S$에 대해 $x < y, y < z$이면 $x < z$이다.

첫번째 조건을 Relation의 정의와 함께 생각해보면 집합 $S$의 서로 다른 어떤 두 원소를 뽑아도 순서쌍이 오직 하나가 relation에 들어가 있다는 것이다. 또 서로 같은 원소로 이루어진 순서쌍은 없다는 것을 말한다.

## Equivalence relation

다음 성질들을 만족하는 relation을 equivalence relation이라고 한다.

1. $x \sim x$
2. $x \sim y \Leftrightarrow y \sim x$
3. $x \sim y, y\sim z \Rightarrow x \sim z$

앞서 정의한 order가 equivalence relation이 되는지 살펴보자.

먼저 3번 조건을 보면 order의 2번 조건과 일치함을 알 수 있다.

하지만 1,2번 조건은 order의 1번 조건에 위배됨을 알 수 있다. 특히 1번 조건은 order와 정면으로 어긋난다.

