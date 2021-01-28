---
title: "고유값 구하기"
excerpt: "Linear Equation"
categories:
 - Numerical Analysis
tags:
 - R
 - Computing
 - Eigenvalue
use_math: true
toc: true
toc_sticky: true
---

# 고유값 Eigenvalues 구하기

## Eigenvalues?

\[
Ax = \lambda x
\]

$n \times n$행렬 $A$에 대해 위 식을 만족하는 $\lambda$를 eigenvalue, $x$를 대응하는 eigenvector라고 한다. eigenvalue는 많은 정보를 갖고 있기 때문에 중요성이 높다. 따라서 eigenvalue를 알아내는 방법이 중요하다.

## Power method 

Power method는 가장 절대값이 큰 eigenvalue를 찾아내는 방법이다. eigenvector들의 모임 $\{e_i\},  i = 1,2,\dots,n$은 $\mathbb R^n$의 basis가 되므로 임의의 벡터 $x$에 대해 아래와 같이 표현가능하다. eigenvalue들을 절대값의 크기대로 나열했다고 가정하자.

\[
 Ax = c_1\lambda_1e_1 + c_2\lambda_2e_2 +\dotsb + c_n\lambda_ne_n    
\]

양변에 $A$를 곱하고 크기를 1로 정하는 방법을 계속 반복하다보면 $A^nx \to e_1$로 수렴을 하게 된다. $(\lambda_1/ \lambda_k)^m \to 0$이므로 뒤의 항은 다 0으로 수렴한다.

eigenvector를 구한다음에는 eigenvalue는 다음과 같이 구한다.

\[
\lambda_1 = e_1^T Ae_1
\]

## Power method extension.

$A$의 역행렬의 eigenvalue들은 $1/\lambda_1,1/\lambda_2,\dots,1/\lambda_n$이다. 따라서 역행렬에 대해 power method를 적용한다면 가장 절대값이 작은 eigenvalue를 구할 수 있다.

$A - \alpha I$의 eigenvalue들은 $\lambda_1 - \alpha,\lambda_2 - \alpha, \dots,\lambda_n - \alpha$이다. 따라서 위의 역행렬 방법과 같이 적용하면 $\alpha$에서 가장 가까운 eigenvalue도 구할 수 있다.

## QR method

먼저 Gram-Schmidt Process를 보자.

Gram-Schmidt 과정은 orthonormal vector들을 찾는 과정이다. 여기서는 벡터 공간이 유한하다고 가정하자.

1. linear independent인 $n$개의 벡터들$\{e_i\}을 고른다.
2. $e_1$을 크기가 1이 되도록 만든다. $(x_1)$
3. $x_2 = e_2 -  \langle e_2, x_1 \rangle x_1$
4. $x_k = e_k - \sum \langle e_k, x_i\rangle x_i$를 $n$번 반복한다.

