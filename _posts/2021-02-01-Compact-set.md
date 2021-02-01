---
title: "Compact set"
excerpt: 
categories:
 - Analysis
use_math: true
toc: true
toc_sticky: true
---

## Open cover

$(X, d)$가 거리 공간이고 $E \subset X$라고 하자. $E$의 open cover는 합집합이 $E$를 포함하는 열린 집합들의 모임이다. 수식으로 쓰면 

\[
    E = \cup_{\alpha \in A}F_\alpha
\]
에서 $\\{F_\alpha\\}_{\alpha \in A}$가 $E$의 open cover이다. open cover의 부분집합이 open cover가 되면 subcover라고 부르고 개수가 유한하다면 finite subcover라고 부른다.

## Compact set

$(X, d)$가 거리공간이고 $K \subset X$라고 하자. 다음 경우에 $K$가 compact set라고 한다.

$K$의 모든 open cover에 대해 항상 finite subcover가 존재한다.

정의가 쉽지 않다. 여기서 착각하기 쉬운 부분은 finite subcover가 존재한다는 부분에 있다. finite subcover가 존재하면 compact가 되는 것이 아니다. finite subcover는 전체공간 하나를 subcover라고 생각하면 항상 존재한다. 중요한 것은 모든 open cover에서 찾을 수 있냐는 것이다.

