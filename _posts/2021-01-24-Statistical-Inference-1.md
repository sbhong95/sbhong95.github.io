---
title: "수리통계학 Chapter 1-1"
excerpt: "Set theory, Probability theory, Conditional Probability"
categories:
 - Statistics
tags:
 - Statistics
use_math: true
toc: true
toc_sticky: true
---

# 1. Probability Theory

## 1.1 Set Theory
확률론의 기반이 되는 집합론부터 천천히 시작한다.

**정의 1.1 표본공간 (Sample Space)**

- 어떤 시험의 모든 결과를 모아놓은 집합
- $S$로 표기하자

가장 간단한 예로 동전 한 개 던지기를 살펴보면 
$$
S = \{앞면, 뒷면\}
$$

수능 시험 점수를 생각해보면
$$
S = \{0, 1, 2, .\dots, 100\}
$$

마지막으로 버스 대기 시간을 생각해보자.
$$
S = [0, \infty)
$$

세 가지의 예를 살펴봤는데 표본 공간을 두가지로 분류 할 수 있다.

- 표본 공간이 countable인 경우
  - 유한한 경우
  - 자연수 전체 집합이랑 1-1 대응을 만들 수 있는 경우
- 표본 공간이 uncountable인 경우
  - 위의 경우에 해당하지 않는 경우
  - 실수 집합이랑 1-1 대응을 할 수 있는 경우가 된다.  

첫번째와 두번째 예는 countable, 마지막 예는 uncountable인 경우가 된다.

**정의 1.2 사건 (Event)**

어떤 시험에서에서 나올수 있는 결과를 말한다. 표본공간을 사용한다면, 모든 부분집합이 사건이된다. ($S$도 포함한다.)


**정의 1.3 서로소 집합 (Disjoint set)**

두 사건 $A,B$에 대해서 $A \cap B = \emptyset$일 경우 서로소 라고 한다. 
사건 $A_1, A_2,....$에 대해서 모든 경우에 대해 $A_i \cap A_j = \emptyset$일 경우 pairwise disjoint라고 한다.

**정의 1.4 분할(Partition)**

pairwise disjoint인 사건들 $A_1, A_2, ...$들의 합집합이 $S$가되면 $\{A_1, A_2, ...\}$를 $S$의 분할이라 한다.
$$
\cup^\infty_{i=1} A_i = S, \quad A_i \cap A_j =\emptyset \text{ for all }i,j
$$

분할의 예로 $A_i = [i, i+1)$라 하면 $S = [0,\infty)$의 분할이 된다.

## 1.2 Basics of Probability Theory

여기서는 확률을 공리를 사용해서 정의해보자. 

### 1.2.1 Axiomatic Foundatoins

각 사건 $A$들에 대해 0과 1사이의 한 숫자를 대응시키고 우리는 이 숫자를 $A$의 확률이라고 부른다. $P(A)$라고 쓴다.

$P(A)$라는 표기를 보면 $P$라는 함수의 정의역을 생각해 볼 필요가 있다.(?) 사실 모든 사건에 대해 확률을 정의할 수 없는 경우가 있다. 왜 정의할 수 없는 경우가 생기는 가에 대해서는 여기서 다루지는 않는다. 하지만 정의할 수 있는 경우는 어떤 특징이 있는지 보자.

**정의 2.1 시그마 대수 (Sigma algebra)**

S의 부분집합들의 모임 $\mathcal B$가 다음 3가지 조건을 만족하면 시그마 대수라고 한다.

1. $\emptyset \in \mathcal B$
2. $A \in \mathcal B \Rightarrow A^c \in \mathcal B$
3. $A_1,A_2,... \in \mathcal B \Rightarrow \cup_{i=1}^\infty A_i \in \mathcal B$

먼저 $\mathcal B$는 표본공간의 부분집합들의 모임(집합)이라는 것을 확인하자.

조건 1,2만 보면 $\{\emptyset, S\}$는 시그마 대수가 된다. 따라서 어떤 표본공간이던지 시그마 대수는 존재한다. 그리고 조건 1은 $S \in \mathcal B$로 바꿔 적어도 별 상관이 없다.

조건 2는 $\mathcal B$가 여집합에 닫혀있다는 것을 보여준다. 조건 3은 임의의 countable한 합집합에 닫혀 있다는 것을 보여준다. 여기서 드모르간의 법칙을 생각해보자. $(A_i \in \mathcal B)$

$$
\left(\cup_{n=1}^\infty A_i^c\right)^c = \cap_{i=1}^\infty A_i
$$

좌변의 집합을 보면 조건 2,3에 의해 $\mathcal B$의 원소임을 알 수 있다. 따라서 우변의 집합도 원소가 되므로 countable한 교집합에도 닫혀있다는 것이 확인가능하다. 

$i+1$번째 부터의 집합을 모두 공집합이라 하면 유한한 합집합, 교집합에 대해 성립함을 쉽게 확인 가능하다.

결론적으로 $^c, \cap, \cup$ 이 세가지 연산을 countable 만큼 조합해서 만든 집합은 시그마 대수안에 포함되어 있다.


*예시 1*
$S$가 유한한 집합이라고 해보자. 그러면 $S$의 모든 부분집합을 모은 집합을 $\mathcal B$라 하면 $\mathcal B$는 시그마 대수가 된다. 

*예시 2*
$S = (-\infty, \infty)$라 하자.

모든 실수 $a,b$에 대해 
$$
(a,b), \ (a,b], \ [a,b), \ [a,b]
$$
를 모아놓은 집합 $\mathcal B$는 시그마 대수가 된다.

이제 확률 함수 $P$를 보자.

**정의 2.2 확률함수 (Probability function)**

표본공간 $S$와 $S$의 시그마 대수 $\mathcal B$에 대해서 확률함수 $P$를 정의한다. 함수의 정의역은 $\mathcal B$이고 다음 조건을 만족해야한다.

1. 모든 $A \in \mathcal B$에 대해 $P(A) \ge 0$
2. $P(S) = 1$
3. $A_1,A_2,\dots$ 가 pairwise disjoint 일 경우 $A_1,A_2, \dots \in \mathcal B \Rightarrow P(\cup A_i) = \sum P(A_i)$


위의 3가지 조건을 확률의 공리라고 부른다. 3번째 조건에서 좌변을 보면 시그마 대수의 3번째 조건이 필요하다는 것을 알 수 있다.

### 1.2.2 The Calculus of Probabilities

확률의 공리로부터 뭘 유도할 수 있는지 살펴보자.

**정리 2.1**
$P$는 확률함수 $A \in \mathcal B$라 하자. 그러면 다음이 성립한다.

1. $P(\emptyset) = 0$
2. $P(A) \le 1$
3. $P(A^c) = 1 - P(A)$

3번 부터 보자. $S = A \cup A^c$이므로 $1 = P(S) = P(A) + P(A^c)$에서 바로 유도된다. (두 집합은 당연히 서로소이다.)

3번에 따라 1번은 바로 유도된다.

공리 1번에 따라 $P(A^c) \ge 0$이므로 2번도 유도된다.


**정리 2.2**
$P$는 확률함수 $A,B \in \mathcal B$라 하자. 그러면 다음이 성립한다.

1. $P(B \cap A^c) = P(B) - P(A\cap B)$
2. $P(A \cup B) = P(A) + P(B) - P(A \cap B) \le 1$
3. $A \subset B \Rightarrow P(A) \le P(B)$

증명

1. $B \cap A, B\cap A^c$는 서로소이므로 성립한다.
2. $P(B)$를 1번의 식으로 대입하면 
$$
P(A \cup B) = P(A) + P(B \cap A^c)
$$
를 얻고 우변의 두 집합이 서로소이므로 등호가 성립함을 알 수 있다.

3.$B = A \cup (B\cap A^c)$ 이므로 $P(B)  - P(A) = P(B \cap A^c) \ge 0$이다.  

**정리 2.3**
$P$는 확률함수 $A_1,A_2,... \in \mathcal B$, ${C_i}$는 $S$의 분할이라 하자. 그러면 다음이 성립한다.

1. $P(A) = \sum P(A\cap C_i)$
2. $P(\cup A_i) \le \sum P(A_i)$

증명 
1. $A = A \cap S = A \cap (\cup C_i) = \cup (A \cap C_i)$
2.  집합 $B_i$를 다음과 같이 정의한다. 
$$
B_i = A_i \setminus \cup^{i-1}_{j=1} A_j, \  B_1 = A_1
$$
그러면 $\cup^\infty A_i = \cup^\infty B_i$가 됨을 확인할 수 있다. $B_i$는 pairwise disjoint를 만족하도록 정의했으므로
$$
P(\cup A_i) = P(\cup B_i) = \sum P(B_i)
$$
가 성립한다. 여기에 각 $i$에 대해
$$
P(B_i) \le P(A_i) 
$$
가 성립하므로 증명이 끝난다.

## 1.3 Conditional Probability and Independence

여기서는 조건부 확률에 대해 다룬다.

**정의 3.1 조건부 확률 (Conditonal probabilty)**

사건 $A,B$에 대해 $P(B) > 0$이면 B가 주어졌을때 $A$의 조건부 확률을 다음과 같이 정의한다.
$$
P(A \mid B) = \frac{P(A\cap B)}{P(B)}
$$

$A,B$가 서로소라면 $P(A\mid B) = P(B \mid A) = 0$이다.

앞에서 확률함수는 표본공간과 시그마 대수가 주어진채로 정의된다는 것을 보았다. 그럼 조건부 확률의 경우 어떤 표본공간과 시그마 대수를 사용하는 것일까?

조건부 확률 $P(\cdot \mid B$)는 표본공간을 $B$로 제한한 함수로 이해할 수 있다. 시그마 대수 또한 새로 정의한다.
$$
\mathcal B' = \{A \cap B \mid A \in \mathcal B\}
$$


**정리 3.1 베이즈 정리**

$\{A_i\}$가 표본공간의 분할이고 $B$가 어떤 사건이라고 하자. 그러면 
$$
P(A_i \mid B) = \frac{P(B \mid A_i)P(A_i)}{\sum P(B\mid A_j)P(A_j)}
$$

**정의 3.2 독립 Independence**

두 사건 $A, B$가 독립이라는 것은 다음을 말한다.

$$P(A \cap B) = P(A)P(B)$$

사건들 $A_1, A_2, ...,A_n$가 mutually independent라는 것은 다음을 말한다.
$$ P(\cap A_i) = \prod P(A_i) $$

**정리 3.2**

두 사건 $A,B$가 독립일 경우 다음도 독립이다.

1. $A, B^c$
2. $A^c, B$
3. $A^c, B^c$