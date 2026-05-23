---
title: La semana en problemas (S17)
summary: Esta semana se proponen algunos enunciados relacionados con límites.
date: 2024-01-23
lastmod: 2026-05-23
image:
    caption: Imagen generada por Leonardo.Ai
math: true
authors:
    - me
categories:
    - Problemas
tags:
    - Límites
status: published
---

Esta semana se proponen algunos enunciados relacionados con límites.

### Ejercicio 1

Calcula:

$$
\lim_{n\rightarrow\infty}{\frac{\sum_{i=1}^{n}{i^2}}{n^3}}.
$$

### Ejercicio 2

Calcula:

$$
\lim_{n\rightarrow\infty}{\left(\frac{3}{1}\right)^{\frac{1}{n}}\cdot\left(\frac{4}{2}\right)^{\frac{2}{n}}\cdot\ldots\cdot\left(\frac{n+2}{n}\right)^{\frac{n}{n}}}.
$$

### Ejercicio 3

Calcula:

$$
\lim_{n\rightarrow\infty}{\sqrt[n]{n^2+1}}.
$$

### Ejercicio 4

Calcula:

$$
\lim_{n\rightarrow\infty}{\frac{\ln{n!}}{n}}.
$$

### Ejercicio 5

Calcule:

$$
\lim_{x\rightarrow\infty}{\frac{x + \sin{x}}{x - \sin{x}}}.
$$

### Ejercicio 6

Calcule:

$$
E = \lim_{n\rightarrow\infty}{ \left[\frac{1}{1\cdot 2} + \frac{1}{2\cdot 3} + \ldots + \frac{1}{(n-1)n} + \frac{1}{n(n+1)} \right] }.
$$

### Ejercicio 7

Calcule:

$$
\lim_{n\rightarrow\infty}{ \frac{1}{n^2} \left[ \frac{2}{1} + \frac{3^2}{2} + \frac{4^3}{3^2} + \ldots + \frac{(n+1)^n}{n^{n-1}} \right] }.
$$

### Ejercicio 8

Calcule:

$$
\lim_{n\rightarrow\infty}{\sqrt[n]{\binom{n}{0}\binom{n}{1}\cdots\binom{n}{n}} }.
$$

### Ejercicio 9

Calcule:

$$
\lim_{n\rightarrow\infty}{\sqrt[n^2]{\binom{n}{0}\binom{n}{1}\cdots\binom{n}{n}} }.
$$

### Ejercicio 10

Estudie la continuidad de la función $f:[0, 1]\rightarrow\mathbb{R}$ dada por

$$
f(x) := \left\{ \begin{aligned} 0, & \quad\text{ si }x = 0\text{ o }x\notin\mathbb{Q} \\ \frac{1}{q}, & \quad\text{ si }x = \frac{p}{q},\ p,q\in\mathbb{N}^+,\ mcd(p,q)=1 \end{aligned} \right.
$$

### Ejercicio 11

Sea $f:[0, 1] \rightarrow [0, 1]$ una función real tal que

$$
f(x) = \left\{ \begin{aligned} x, & \quad\text{ si }x\text{\ es racional} \\ 1 - x, & \quad\text{ si }x\text{\ no es racional} \end{aligned} \right.
$$

- (a) Estudie la continuidad en los puntos $x_0 = \frac{1}{2}$ y
  $x_1 = \frac{1}{4}$.
- (b) Estudie la derivabilidad en dichos puntos.

### Ejercicio 12

Una semicircunferencia de radio $r$ se divide en $n + 1$ partes iguales y se uno
un punto cualquiera de la división con los extremos, formándose un triángulo
rectángulo de área $A(k)$. Se pide el límite, cuando $n\rightarrow\infty$, de la
media aritmética de las áreas de esos triángulos.

### Ejercicio 13

Sea $f\in\mathcal{C}^2(\mathbb{R})$ una función tal que:

$$
\lim_{x\rightarrow 0}{\left( 1 + x + \frac{f(x)}{x} \right)^{1/x}} = e^3.
$$

Calcule razonadamente $f(0)$, $f'(0)$ y $f''(0)$.
