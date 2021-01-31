---
title: "least-upper-bound property"
excerpt: 
categories:
 - Analysis
use_math: true
toc: true
toc_sticky: true
---



## Least-Upper-Bound-Property

order가 주어진 집합 $S$의 Least-Upper-Bound-Property은 다음을 말한다.

\[
    E \subset S, E \ne \emptyset, E \text{ 가 위로 유계 } \Rightarrow \sup E \in S
\]

즉 공집합을 제외한 $S$의 부분집합에 대해 $\sup$이 존재할 경우를 말한다. 이 성질이 존재하면 어떤 일이 있는지 보자.

**정리 1**

$S$가 Least-Upper-Bound-Property을 갖고 있고 $B \subset S$라고 하자. $B$가 공집합이 아니고 아래로 유계라고 하자. $L$을 $B$의 lower bound들의 집합이라 하면 $\sup L$가 $S$에 존재하고 
\[
    \sup L  = \inf B
\]

증명  

1. $B$가 아래로 유계이므로 $L$은 공집합이 아니다. 
2. 또한 lower bound들의 집합이므로 $S$의 부분집합이다. 
3. $B$가 공집합이 아니므로 $b \in B$가 존재한다. lower bound의 정의에 따라 다음이 성립한다.

\[ \forall l \in L, b \in B \Rightarrow l < b \]

따라서 $L$은 위로 유계이다.

1-3을 조합하면 Least-Upper-Bound-Property의 성립 조건이 된다. 따라서 $\sup L$이 존재한다.

$\alpha = \sup L$이 $\inf B$가 맞는지 확인하자.

$\alpha > b$일 경우 $b$는 $L$의 upper bound가 될 수 없다. 따라서 3에서 봤듯이 $b \not\in B$이다. 대우를 적용하면 
\[
 b \in B \Rightarrow \alpha \le b
\]
를 얻는다. 즉 $\alpha$는 $b$의 lower bound가 된다.

$\alpha = \sup L$이므로 $L$의 어떤 원소들보다도 $\alpha$가 크다. $L$의 원소들은 모두 $B$의 lower bound이므로 
$\alpha = \inf B$가 성립한다.




