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

통계학에서는 대칭행렬 중 특히 Positive semi definite행렬을 자주 마주치게 된다. 대표적으로 분산행렬, 회귀분석에서 hat matrix가 있다. 여기서는 대칭성을 활용한 방법을 알아보자.

어떤 행렬 $M$이 symmetric이라고 해보자. $M$에 대해 각각 $LU$분해를 하면 대칭에 의해 $U = L^T$를 만족하도록 분해할 수 있다. 양쪽에 적당한 상수배를 하면 두 행렬이 다르게 할 수도 있다. 

Cholesky 분해도 ``R``에서 지원한다.

```R
chol()
```

## 3. 반복에 의한 풀이

먼저 diagonally dorminant에 대해 알아보자. 

어떤 행렬이 diagonally dorminant라는 것은 모든 $i$에 대해 다음이 성립한다는 것을 말한다.

\[
\mid a_{ii}\mid \ge \sum_{i \ne j} \mid a_{ij} \mid 
\]

이제 소개할 Jacobi 방법은 diagonally dorminant행렬에 대해 적용할 수 있는 방법이다.

먼저 행렬을 아래 그림과 같이 $A = L + D + U$로 분해한다. 

![jacobi](../../assets/images/jacobi.png)

그리고 $Ax = b$를 다음과 같이 정리한다.

$$
\begin{align*}
    Dx &= -Lx-Ux + b \\
    x &= D^{-1}(-Lx-Ux+b)
\end{align*}
$$

적당한 초기값을 잡아서 왼쪽에 대입하여 새로운 $x$를 얻은 다음 다시 왼쪽에 대입한다. 적당한 범위안에서 $x$의 변동이 멈추면 그 $x$를 해로 사용하는 방법이다.


## 4. R code 

내장된 함수 대신 직접 ``R``로 짜보자.

LU decomposition method

```R
swap <- function(P, i, j){
  temp   <- P[i, ];  P[i, ] <- P[j, ];   P[j, ] <- temp
  return(P)
}
solve.LU <- function(A, b){
  n <- nrow(A); L <- matrix(0, n, n); P <- diag(n)
  
  for (k in 1:(n-1)){
    j <- which.max(abs(A[k:n, k])) + (k - 1)
    if(A[j, k] == 0) stop("Singular matrix")
    A <- swap(A, k, j)
    L <- swap(L, k, j)
    P <- swap(P, k, j)
    b <- swap(b, k, j)
    L[(k+1):n, k] <- A[(k+1):n, k] / A[k,k]
    A[(k+1):n, k] <- 0
    A[(k+1):n, (k+1):n] <- A[(k+1):n, (k+1):n] - outer(L[(k+1):n, k],  A[k, (k+1):n])
  }
  
  if(A[n, n] == 0) stop("Singular matrix")
  diag(L) <- 1
  x <- forwardsolve(L, b)
  x <- backsolve(A, x)
  obj <- list(x = x, L = L, U = A, P = P)
  return(obj)
}
```

Cholesky method

```R
CD <- function(M){
  n <- nrow(M)
  L <- matrix(0, n, n)
  L[1, 1] <- sqrt(M[1, 1])
  for(k in 1:(n-1)){
    L[k+1, 1:k] <- forwardsolve(L[1:k,1:k],M[1:k, k + 1] )
    L[k+1, k+1] <- sqrt(M[k+1, k+1] - sum(L[k+1, 1:k]^2))
  }
  return(L)
}

L <- CD(M)
x <- forwardsolve(L, b)
x <- backsolve(t(L), x)
```

Jacobi iterative method
```R
jacobi <- function(A, b, x = rep(0, length(b)), eps = 1e-06){
  D <- diag(diag(A))
  diag(A) <- 0
  b_new <-  b / D
  A_new <- A / D
  err <- 1
  while(err > eps){
    x_new <- A_new %*% x + b_new
    err <- sqrt(sum((x_new - x)^2))
    x <- x_new
  }
  return(x)
}
```




