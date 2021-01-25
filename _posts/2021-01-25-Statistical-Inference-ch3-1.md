---
title: "수리통계학 Chapter 3-1"
excerpt: "Distcrete Distributions, Continuous Distributions"
categories:
 - Statistics
tags:
 - Statistics       
use_math: true
toc: true
toc_sticky: true
---

# 3. Common Families of Distributions

Chapter 1, 2는 일반적인 이야기였으나 여기서는 구제척인 분포들을 다룬다.

## 3.1 Discrete Distributions

확률변수 $X$가 이산형이라는 것은 $X$의 표본공간이 countable이라는 것이다. 

- 균등분포 Distcrete Uniform $(1,N)$
  - pmf : $P(X = x \mid N) = 1/N, x = 1,2,...,N$
  - $EX = \frac{N+1}{2}, Var X = \frac{N^2 - 1}{12}$

- 초기하분포 Hypergeometric Distribution $(N,M,K)$
  - pmf : $P(X = x \mid N,M,K) = \binom {M}{x} \binom{N-M}{K-x} / \binom{N}{K}$ $x = 0,1,...,K$.
  - $EX = KM/N$

- 이항분포 Binomial $(n,p)$
  - pmf : $P(X = x \mid n,p) = \binom{n}{x} p^x(1 - p)^{n-x}$ $x = 0,1,...,n$
  - $EX = np, VarX = np(1-p)$
  - $n = 1$일 경우 베르누이 분포라 한다.

 **정리 1.1**

실수 $x,y$, 정수 $n \ge 0$에 대해 

\[
 (x + y)^n = \sum_{i=0}^n \binom{n}{i}x^iy^{n-i}
\]

다른 증명에 자주 쓰이는 정리다.

- 포아송분포 Poisson $(\lambda)$
  - pmf : $P(X =x \mid \lambda) = e^{-\lambda}\lambda^x / x!$ $x = 0,1,...$
  - $EX = Varx = \lambda$.

- 음이항분포 Negative Binomial $(r, p)$
  - pmf : $P(X =x \mid r,p) = \binom{x-1}{r-1}p^r(1-p)^{x-r}$ $x = r,r+1,...$

- 기하분포 Geometric $(p)$
  - pmf : $P(X = x \mid p) = p(1 - p)^{x -1 }$ $x =1,2,...$

## 3.2 Continuous Distributions

- 균등분포 $(a,b)$
  
  - pdf : $f(x \mid a,b) = 1 / (b - a)$
- 감마분포 $(\alpha, \beta)$
  
  - pdf : $f(x \mid \alpha, \beta) = \frac{x^{\alpha-1}}{\Gamma(\alpha)\beta^\alpha}\exp{(-x/\beta)}$
- 정규분포 $(\mu, \sigma)$
  
  - pdf : $f(x \mid \mu, \sigma) = \frac{1}{\sqrt{2\pi}\sigma} \exp{-[\frac{(x-\mu)^2}{2\sigma^2}]}$
- 베타분포 $(\alpha, \beta)$
  - pdf : $f(x \mid \alpha, \beta) = \frac{x^{\alpha-1}(1 - x)^{\beta - 1}}{B(\alpha, \beta)}$
  - $B(\alpha, \beta) = \frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha + \beta)}$
- 코시분포 $(\theta)$
  - pdf : $f(x \mid \theta) = \frac{1}{\pi}\frac{1}{1 + (x - \theta)^2}$

  