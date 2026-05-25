---
title: La semana en problemas (S9)
summary:
    Esta semana se proponen algunos enunciados relacionados con espacios
    vectoriales.
date: 2023-11-07
lastmod: 2026-05-25
image:
    caption: Imagen generada por Leonardo.Ai
authors:
    - me
math: true
categories:
    - Problemas
tags:
    - Espacios vectoriales
status: published
---

Esta semana se proponen algunos enunciados relacionados con espacios
vectoriales.

### Ejercicio 1

Sea la aplicación $f:\mathbb{R}^3\rightarrow\mathbb{R}^2$ dada por
$f(1,0,1) = (0,1)$, $f(0,0,-1)=(1,1)$ y $f(2,1,1) = (1,0)$.

- a) Hallar la matriz de $f$ respecto de las bases canónicas.
- b) Hallar la matriz de $f$ respecto de las bases
  $$B_1 = \{(1,0,1), (0,0,-1), (2,1,1)\}$$ y $$B_2 = \{(0,1), (1,0)\}.$$
- c) Hallar las ecuaciones y dimensión de $ker f$ e $img f$.

### Ejercicio 2

Consideremos el espacio vectorial $\mathbb{C}^3$ sobre el cuerpo $\mathbb{C}$ de
los números complejos, y sea $f:\mathbb{C}^3\rightarrow\mathbb{C}^3$ la
aplicación lineal dada por $f(x,y,z) = (5x,-z,y)$.

- a) Hallar el núcleo y la imagen de $f$. ¿Se puede deducir alguna propiedad
  sobre $f$ de los resultados obtenidos en este apartado?
- b) Dar las dimensiones y unas bases de los subespacios hallados en a).
- c) Calcular los autovalores y autovectores de la matriz $A$ asociada a $f$
  respecto de la base canónica. Indicar los subespacios vectoriales propios.
- d) Justificar si $A$ es diagonalizable. En caso afirmativo, encontrar la
  matriz diagonal $D$ y la matriz de paso $P$. ¿Es la matriz $D$ hermítica?
- e) Hallar la expresión general de la matriz $A^n$, para $n\in\mathbb{N}$, y
  comprobar que para $n=1$ se obtiene la matriz $A$, lo que es necesario para
  que los apartados c), d) y e) estén bien resueltos.
- f) Hallar la expresión general de la matriz $A^n$ cuando $$n = 3 (mod\ 4).$$
- g) Demostrar que si $n$ es par, la matriz $A^n$ es diagonal y calcular su
  determinante.

### Ejercicio 3

Sean $f$ y $g$ dos endomorfismos del espacio vectorial $\mathbb{R}^3$ definidos
para todo $(x,y,z)\in\mathbb{R}^3$ como sigue:
$$f(x,y,z) = (x+y,2x-z,2y+z),\quad g(x,y,z) = (x,y,0)$$

- a) Halle una base, unas ecuaciones y la dimensión del núcleo de $f$ y del
  núcleo de $g$.
- b) Halle una base, unas ecuaciones y la dimensión de la imagen de $f$ y de la
  imagen de $g$.
- c) Determine las matrices asociadas a los endomorfismos $f$, $g$, $f\circ g$ y
  $g\circ f$ en la base canónica de $\mathbb{R}^3$.

### Ejercicio 4

Sea $f:\mathbb{R}^4\rightarrow\mathbb{R}^3$ una aplicación lineal con matriz
asociada en las bases $\{e_i\}$ de $\mathbb{R}^4$ y $\{e'_i\}$ de
$\mathbb{R}^3$:

$$
A = \begin{bmatrix} 3 & 0 & 1 & 1 \\ 2 & 1 & 1 & 5 \\ 1 & 2 & 1 &
0 \end{bmatrix}
$$

- a) Calcula la expresión matricial de la aplicación.
- b) Calcula $ker f$ y una base suya.
- c) Calcula $img f$ y una base suya.
- d) Escribe las bases canónicas de $f$ respecto a $\mathbb{R}^4$ y
  $\mathbb{R}^3$.

### Ejercicio 5

Sea $E$ un $K$-espacio vectorial con una base $B = \{u_1,u_2,u_3\}$. Sea $f$ la
única aplicación lineal $f:E\rightarrow E$ tal que $f(u_1) = u_2+u_3$,
$f(u_2) = u_1+u_2+2u_3$ y $f(u_3) = 2u_1+2u_2+2u_3$. Si $K=\mathbb{R}$,
$E=\mathbb{R}^3$, $B = \{(1,2,1), (1,0,1), (0,0,1)\}$, calcule

- a) $f(3,2,1)$
- b) La matriz de $f$ respecto de la base $B$.
- c) La dimensión del núcleo de $f$.
- d) La dimensión de la imagen de $f$.

### Ejercicio 6

Sea $f:\mathbb{R}^3\rightarrow\mathbb{R}^3$ un endomorfismo tal que

$$
\begin{align*} \left\{ \begin{aligned} f(u_1) & = u_1 + 2u_2 - u_3 \\ f(u_2) & =
-3u_1 - u_2 + 5u_3 \\ f(u_3) & = -2u_1 + u_2 + 2u_3 \end{aligned} \right.
\end{align*}
$$

donde $B = \{u_1,u_2,u_3\}$ es una base para el espacio vectorial
$(\mathbb{R}^3,+,\cdot)$. Hallar la matriz de la aplicación lineal $f$ respecto
de la base $B' = \{v_1,v_2,v_3\}$, en la que las imágenes de los vectores $v_1$,
$v_2$ y $v_3$ se expresan en las columnas de la matriz, donde

$$
\begin{align*} \left\{ \begin{aligned} v_1 & = u_2+u_3 \\ v_2 & =
u_1+u_3 \\ v_3 & = u_1+u_2 \end{aligned} \right. \end{align*}
$$
