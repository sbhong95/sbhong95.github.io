---
title: "컴팩트 집합과 전체 공간"
excerpt: 
categories:
 - Analysis
use_math: true
toc: true
toc_sticky: true
---

open, closed의 개념은 전체 공간이 어떤가에도 달려 있다. compact도 전체공간에 따라 바뀌는 지 보기로 하자.

## Compact relative to Space.

**정리 1**

$X$가 거리공간이고 $K \subset Y \subset X$라고 하자. $K$가 $X$에서 compact인 것과 $K$가 $Y$에서 compact인 것은 동치이다.

**증명**

먼저 $X$에서 compact라고 하자. $\{E_\alpha^Y : \alpha \in A\}$를 $Y$에서 $K$의 임의의 open cover라고 하자. $X$가 $Y$를 포함하는 거리공간이므로 각각의 open cover 원소에 대해 $E_\alpha^X \cap Y = E_\alpha^Y$를 만족하는 $X$에서의 집합이 존재한다. 이 집합들을 모으면 정의에 따라 $K$의 open cover가 되고 compact를 가정했으므로 finite subcover가 존재한다. finite subcover에 대응하는 각 $E_\alpha^Y$를 모으면 finite subcover가 되므로 $Y$에서도 compact set이 된다.

다음으로 $Y$에서 compact라고 가정하자. 이 경우도 마찬가지로 $X$에서의 임의의 open cover를 뽑고 대응하는 $Y$의 open cover를 구성하면 finite subcover를 찾을 수 있다.


