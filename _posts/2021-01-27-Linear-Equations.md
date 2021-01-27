---
title: "선형 연립 방정식"
excerpt: "Linear Equation"
categories:
 - Numerical Analysis
tags:
 - R
 - Computing
use_math: true
toc: true
toc_sticky: true
---

# 선형연립방정식 풀기

\[
Ax = b
\]

 위 선형 방정식을 푸는 방법은 쉽다.역행렬 $A^{-1}$를 찾아서 양변에 곱해주면 바로 답이 나온다. 하지만 역행렬을 구하는 과정은 복잡하고 컴퓨터를 이용한다고 해도 계산과정이 많다. 차원이 커지면 커질수록 역행렬을 구해서 곱해주는 방법은 효율성이 떨어진다.

 그러면 역행렬을 구하지 않고 해를 구하는 방법들에 대해서 알아보자.

## 1. LU 분해

행렬 $A$를 lower, upper triangular 행렬로 분해하여 푸는 방법이다.

1. $A = LU$로 분해
2. $Ly = b$를 만족하는 $y$를 찾는다.
3. $Ux = y$를 만족하는 $x$를 찾는다.  

위 과정에서 문제점은 $A = LU$를 만족하는 $L, U$가 유일하지 않다는 것이다. 따라서 보통 $L$의 대각 성분을 1로 고정한다. 그러면 왜 lower, upper matrix를 사용하는 지 보자.

![matrixexample](../../assets/images/matrix-example.png)

위 식의 해는 $(x_1,x_2,x_3) = (-1,0,1)$이다.

해를 구하는 과정을 생각해보면 $x_3 = 1$을 가장 먼저 얻고, 2번째 식을 통해 $x_2$, 마지막으로 $x_1$을 얻게 된다. 즉 순차적으로 각각의 해를 빠르게 얻을 수 있는 장점이 있다. 이 장점은 lower matrix일때도 마찬가지이다.

``R``에서는 행렬이 lower, upper matrix일경우의 함수를 지원한다.

```R
A = matrix(c(1,0,0,2,4,0,3,5,6),3)
b = c(2,5,6)
## A is an upper triangular matrix
x = backwardsolve(A, b)
```
lower matrix일 경우 ```forwardsolve()```가 있다.

## 2. Cholesky 분해

통계학에서는 Positive semi definite행렬을 자주 마주치게 된다. 대표적으로 분산행렬, 회귀분석에서 hat matrix가 있다. PSD행렬에는 여러 좋은 성질이 있지만 여기서 활용할 것은 대칭성이다. 

어떤 행렬 $M$이 symmetric이라고 해보자. $M$에 대해 각각 $LU$분해를 하면 대칭에 의해 $U = L^T$를 만족하도록 분해할 수 있다. 양쪽에 적당한 상수배를 하면 두 행렬이 다르게 할 수도 있다. 

Cholesky 분해도 ``R``에서 지원한다.

```R
chol()
```

## 3. 반복에 의한 풀이

행렬을 아래 그림과 같이 $A = L + D + U$로 분해한다. 

![jacobi](../../assets/images/jacobi.png)

그리고 $Ax = b$를 다음과 같이 정리한다.

$$
\begin{align*}
    Dx &= -Lx-Ux + b \\
    x &= D^{-1}(-Lx-Ux+b)
\end{align*}
$$

적당한 초기값을 잡아서 왼쪽에 대입하여 새로운 $x$를 얻은 다음 다시 왼쪽에 대입한다. 적당한 범위안에서 $x$의 변동이 멈추면 그 $x$를 해로 사용하는 방법이다.




