---
title: "비선형 연립 방정식"
excerpt: "Nonlinear Equation"
categories:
 - Numerical Analysis
tags:
 - R
 - Computing
use_math: true
toc: true
toc_sticky: true
---

# 비선형방정식 풀기

이전 글에서는 선형방정식을 풀었지만 비선형방정식을 다루는 경우도 많다. 먼저 $x$가 스칼라인 경우를 보자.

\[
f(x) = 0
\]

## 1. Bisection method

**중간값 정리 Intermediate Value Theorem**

함수 $f$가 $[a,b]$에서 연속이고 $k$가 $f(a), f(b)$사이의 값이라고 하자.$(f(a) \ne f(b))$ 그러면 $f(c) = k$를 만족하는 $c \in (a,b)$가 존재한다. 

$k = 0$으로 두고 위 정리를 응용하면 연속함수 $f$에 대해 $f(a)f(b) < 0$이면 그 구간에 해가 반드시 존재한다는 것을 알 수 있다.

Bisection 방법은 해가 반드시 존재한다는 위 정리를 기반으로 구간의 길이를 점점 좁혀가서 해를 정하는 방법이다.

코드로 보자.
```R
bisection <- function(f, a, b, eps = 1e-06){
  if (f(a) * f(b) > 0 ) stop("The interval is not valid")
  len <- b - a
  while(len > eps){
    mid <- (a + b) / 2
    if(abs(f(mid)) < eps) return(mid)
    if(f(a) * f(mid) < 0){
      b <- mid
    }else{
      a <- mid
    }
  }
  return((a + b) / 2)
}
```


## 2. Newton method

Bisection method는 해 근처에서 연속함수임을 가정한다. Newton method는 여기서 추가로 미분가능을 필요로 한다. 가정이 더 필요한 만큼 Bisection 보다는 빠른 속도로 해에 접근한다.

```R
newton <- function(f,  fprime, init, eps){
  max_iter <-500; iter_n <- 0; error <- 1
  table <- data.frame(0, init)
  while(error > eps){
    temp <- ini
    diff <- f(init) / fprime(init)
    init <- init - diff
    error <- abs(diff)
    iter_n <- iter_n + 1
    table[iter_n + 1, ] = c(iter_n, init)
    if((iter_n > max_iter)){
      return(list(root = init, table= table))
    }
  }
  return(list(root = ini, table = table))
}
```

Bisection과는 다르게 운이 안 좋으면 수렴을 하지 않는다. 즉 해를 찾지 못할 수 있는 가능성이 존재한다.


## 3. Multi-dimension

Bisection방법은 다차원으로 확장이 가능하지 않다. 하지만 Newton방법은 미분가능이 모두 보장되면 다차원으로 확장이 가능하다.

하지만 도함수로 구성된 행렬 $($Hessian$)$의 역행렬을 구하는 문제가 생긴다. 매 단계마다 역행렬을 구해야하므로 계산량이 복잡해진다. 따라서 Hessian행렬을 근사하거나 아니면 고정시켜서 활용하는 방법이 존재한다. 나중에 GLM방법에서 다시 보도록 하자.


## 4. 단점

중근의 경우를 생각해보면 해 근처에 부호가 바뀌지 않는다. 따라서 Bisection 방법을 적용하려고 보면 어떻게 구간을 잡아도 알고리즘이 돌아가지 않는다.

같은 경우에 뉴턴 방법을 적용하려고 보면 미분값이 0으로 다가가기 때문에 수치적으로 불안정하다. 이 경우 이계도함수가 존재한다면 활용해서 알고리즘을 고칠 수 있다.

생각한 구간에 다른 해가 있을 경우 여러 개 중 하나가 발견될 뿐이다.