---
title: "Supremum, Infimum"
excerpt: "upper bound, lower bound"
categories:
 - Analysis
tag:
 - Supreme
 - Infimum
use_math: true
toc: true
toc_sticky: true
---

# Sup, inf

order가 정의된 집합에서의 개념들을 알아보자.

## maximum, minimum

$S$에서 order가 정의되었고 $E \subset S$라고 하자.

1. 다음 경우에 $a$를 $E$의 maximum이라 한다.
\[
    a \in E, \quad e \le a, \quad \forall e \in E
\]
2. 다음 경우에 $a$를 $E$의 minimum이라 한다.
\[
    a\in E, \quad a \le e, \quad \forall e \in E
\]

3. 다음 경우에 $E$가 위로 유계라고 한다.
\[
    \exists \beta \in S \text{ s.t. } x \le \beta \quad \forall x \in E
\]
이 경우 $\beta$를 $E$의 upper bound라고 한다.

4. 다음 경우에 $E$가 아래로 유계라고 한다.
\[
    \exists \beta \in S \text{ s.t. } \beta \le x \quad \forall x \in E
\]
이 경우 $\beta$를 $E$의 lower bound라고 한다.

위의 4가지 정의들은 다음 정의들을 위한 것이다.

## Supremum

$S$에서 order가 정의되었고 $E \subset S$라고 하자. $E$가 위로 유계이고 다음 조건들을 만족하는 $\alpha \in S$가 존재한다고 하자.

1. $\alpha$는 $E$의 upper bound이다.
2. $\gamma < \alpha$라면 $\gamma$는 $E$의 upper bound가 아니다.

그러면 $\alpha$를 $E$의 supremum이라 하고 $\sup E$라고 쓴다.


1,2번 조건을 다르게 표현하면 $E$의 upper bound들의 miniumum이 $\alpha$라고 말할 수 있다.
((
## Infimum

마찬가지로 infimum을 보자.

$S$에서 order가 정의되었고 $E \subset S$라고 하자. $E$가 아래로 유계이고 다음 조건들을 만족하는 $\alpha \in S$가 존재한다고 하자.

1. $\alpha$는 $E$의 lower bound이다.
2. $\alpha < \gamma$라면 $\gamma$는 $E$의 lower bound가 아니다.

그러면 $\alpha$를 $E$의 infimum이라 하고 $\inf E$라고 쓴다.


## 차이

maximum과 supremum의 정의를 다시 보자.

$a$가 $E$의 maximum이라면 자동적으로 supremum이 된다. 그럼 두 정의의 차이가 어디서 발생하는지 보면 $a \in E$에서 나타난다. supremum의 정의에서는 해당 집합의 원소일 필요가 없다. 구체적인 예로
 구간 $(0,1)$을 살펴보자.

 $(0,1)$에서 어떤 원소를 뽑아도 그것보다 큰 원소를 찾을 수 있다. 이 내용은 나중에 아르키메디안 성질 포스트에서 다룰 예정이다. 따라서 maximum을 찾을 수가 없다. 하지만 모든 원소가 1보다 작다는 것은 당연히 알 수 있다. 따라서 1을 maximum이라 할 수 없다. 이때 사용하는 것이 Supremum이다.

 minimum과 infimum의 관계도 마찬가지이다. $(0,1)$의 infimum은 0이지만 해당집합에 원소가 아니다. 