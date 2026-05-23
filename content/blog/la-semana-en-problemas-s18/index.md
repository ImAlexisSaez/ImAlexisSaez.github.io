---
title: La semana en problemas (S18)
summary: Esta semana se proponen algunos enunciados relacionados con derivadas.
date: 2024-01-30
lastmod: 2026-05-23
image:
    caption: Imagen generada por Leonardo.Ai
math: true
authors:
    - me
categories:
    - Problemas
tags:
    - Derivadas
status: published
---

Esta semana se proponen algunos enunciados relacionados con derivadas.

### Ejercicio 1

Sea la función $f(x) = \ln{(1 + x^2)} - \arctan{x}$. Demuestre que

$$
    f^{(n)}(x) = \frac{P_n(x)}{(1 + x^2)^n}
$$

donde $P_n(x)$ representa un polinomio de grado $n$ con $n$ ceros reales
diferentes.

### Ejercicio 2

Para cada par de números reales distintos $r$ y $s$ se llama ''derivada
generalizada $(r, s)$'' de la función $f$ en el punto $a\in\mathbb{R}$ al
siguiente límite:

$$
    f^{(r, s)}(a) = \lim_{h\rightarrow 0}{\frac{f(a + rh) - f(a + sh)}{(r - s)h}}.
$$

- (a) Demuestre que si la función $f$ es derivable en el punto $a$, entonces
  $f^{(r,s)}(a)$ existe y coincide con la derivada ordinaria $f'(a)$.
- (b) Obtenga $f^{(2,1)}(x)$ y $f'(x)$ en el caso de la función
  $f(x) = x - E(x)$, donde $E(x)$ es la parte entera de $x$, es decir, el mayor
  entero no superior a $x$. Compare e interprete los resultados.
- (c) Obtenga $f^{(1, -1)}(x)$ y $f'(x)$ para la función ''valor absoluto''
  $f(x) = |x|$. Compare e interprete los resultados.
- (d)
    - i. Calcule $f^{(2,1)}(0)$ en el caso de la función
      $f(x) = \sin{\left(\frac{\pi}{\ln{2}}\cdot\ln{(x^2)}\right)}$.
    - ii. ¿Está definida $f(0)$ en este caso?
    - iii. ¿Existe $\lim_{x\rightarrow 0}{f(x)}?$
    - iv. ¿Existe la derivada $f'(0)$ de $f$ en $0$?

### Ejercicio 3

Sea $f:\mathbb{R}\rightarrow\mathbb{R}$ una función derivable en $\mathbb{R}$,
dos veces derivable en el origen y tal que $f(0) = 0$. Sea
$F:\mathbb{R}\rightarrow\mathbb{R}$ la función tal que

$$
    F(0) = f'(0),\qquad F(x) = \frac{1}{x}\int_{0}^{x}{\frac{f(t)}{t}dt} \quad\text{para } x\neq 0
$$

- (a) Estudie la derivabilidad de $F$.
- (b) ¿Es $F$ de clase $\mathcal{C}^1$ en $\mathbb{R}$?
