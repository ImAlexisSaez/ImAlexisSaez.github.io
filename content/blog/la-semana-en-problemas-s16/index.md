---
title: La semana en problemas (S16)
summary: Esta semana se proponen algunos enunciados relacionados con funciones.
date: 2023-12-26
lastmod: 2026-05-23
image:
    caption: Imagen generada por Leonardo.Ai
math: true
authors:
    - me
categories:
    - Problemas
tags:
    - Funciones
status: published
---

Esta semana se proponen algunos enunciados relacionados con funciones.

### Ejercicio 1

Demuestre que cualquier aplicación lineal de $\mathbb{R}$ en $\mathbb{R}$ es una
función continua.

### Ejercicio 2

Sea $f$ una función real de variable real tal que, para cada
$x, y\in\mathbb{R}$,

$$
f(x + y) = f(x) + f(y).
$$

- a) Calcule la expresión de $f(x)$, para $x\in\mathbb{Q}$.
- b) Demuestre que si $f$ es continua, entonces $f(x) = ax$ para todo
  $x\in\mathbb{R}$, donde $a$ es una constante.

### Ejercicio 3

Supongamos que $f:\mathbb{R}\rightarrow\mathbb{R}$, siendo $f$ no nula y
cumpliendo que:

$$
f(x + y) = f(x)\cdot f(y),\qquad \forall x, y\in\mathbb{R}.
$$

Demuestre que si $f$ es continua, existe una constante $c\in\mathbb{R}$ tal que
$f(x) = e^{cx}$.

### Ejercicio 4

Demuestre que si una función $f$ real de variable real cumple que

$$
f(x) - f(y) \leq (x - y)^2
$$

para cualesquiera números reales $x$ e $y$, entonces $f$ es una función
constante.

### Ejercicio 5

La aplicación $f:\mathbb{Z}\rightarrow\mathbb{Z}$ cumple, para cualesquiera
$m,n\in\mathbb{Z}$, que:

$$
f(m^2 + f(n)) = f(m)^2 + n.
$$

Demuestre que:

- a) $f(0) = 0$
- b) $f(1) = 1$
- c) $f(n) = n$, para todo $n\in\mathbb{Z}$.

### Ejercicio 6

Sea $f:\mathbb{R}\rightarrow\mathbb{R}$ una función que satisface la relación

$$
f(x + y) = f(x)\cdot f(y)
$$

para cualesquiera $x,y\in\mathbb{R}$. Demuestre que:

- a) Si $f$ se anula en un punto, entonces se anula en $\mathbb{R}$.
- b) $f$ es continua si y solo si es continua en un punto de $\mathbb{R}$.

### Ejercicio 7

Halle la condición necesaria y suficiente que debe cumplir la base $a$ de un
sistema de logritmos para que en dicho sistema exista, al menos, un número igual
a su logaritmo.

### Ejercicio 8

Resuelva la siguiente ecuación en $\mathbb{R}$, conocido $\alpha\in\mathbb{R}$:

$$
\left(\frac{1+ix}{1-ix}\right)^4 = \frac{1+i\tan{\frac{\alpha}{2}}}{1-i\tan{\frac{\alpha}{2}}}.
$$

### Ejercicio 9

Dado $n\in\mathbb{N}$, se considera la ecuación

$$
x^{2n} - 1 = 0.
$$

- a) Calcule sus soluciones en el cuerpo $\mathbb{C}$ de los números complejos.
- b) Demuestre que, para $x\neq\pm 1$ y $n > 1$, se cumple la _identidad de
  Cotes_:
  $$\frac{x^{2n}-1}{x^2-1} = \prod_{k=1}^{n-1}{\left(x^2 - 2x\cos{\frac{k\pi}{n}} + 1\right)}.$$
- c) Halle el valor del producto:
  $$\sin{\frac{\pi}{2n}}\sin{\frac{2\pi}{2n}}\cdots\sin{\frac{(n-1)\pi}{2n}}.$$
