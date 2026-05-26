---
title: La semana en problemas (S8)
summary: Esta semana se proponen algunos enunciados relacionados con estructuras algebraicas y espacios vectoriales.
date: 2023-10-31
lastmod: 2026-05-26
image:
  caption: Imagen generada por Leonardo.Ai
authors:
  - me
math: true
categories:
  - Problemas
tags:
  - Espacios vectoriales
  - Estructuras algebraicas
status: published
---
Esta semana se proponen algunos enunciados relacionados con estructuras
algebraicas y espacios vectoriales.

### Ejercicio 1

Dado el conjunto $A = \{a, b, c\}$ se pide:

- a) Decir de una forma razonada el número de sus particiones, escribiéndolas a
  continuación.
- b) Demostrar que, dado un conjunto $H$, si se cumple que
  $P_1 = \{\alpha_1, \alpha_2, \ldots, \alpha_k\}$ y
  $P_2 = \{\beta_1, \beta_2, \ldots, \beta_p\}$ son particiones del mismo, el
  conjunto
  $$P = \{X \subset H | X = \alpha_i \cap \beta_j \neq \varnothing, \forall i,j\}$$
  es otra partición de $H$.

### Ejercicio 2

Sea $\mathbb{C}^*$ el grupo multiplicativo de los complejos no nulos y
$G = \{1, -1, i, -i\}$ (grupo).

- a) Probar que $G$ es un subgrupo de $\mathbb{C}^*$.
- b) Determinar los isomorfismos de $G$ sobre el conjunto $\mathbb{Z}_4$ de las
  clases residuales módulo $4$.

### Ejercicio 3

Responda a las siguientes cuestiones:

- a) El conjunto $\{a + 4b: a,b\in\mathbb{Q}\}$ tiene estructura de anillo
  respecto de la suma y el producto ordinarios de los números reales. Probar que
  este anillo no tiene estructura de cuerpo y encontrar un elemento del conjunto
  que no posea inverso.
- b) En este ejercicio se aborda el concepto de anillo y de cuerpo que, como se
  sabe, son estructuras algebraicas básicas de la teoría de conjuntos. Relacione
  ésta con el currículo de secundaria y dé una aplicación didáctica de algún
  concepto que aparezca en dicha teoría.

### Ejercicio 4

Demuestre que el núcleo de un homomorfismo de anillos es un ideal.

### Ejercicio 5

Demuéstrese que el conjunto
$C = \{(x,y,y,-x)\in\mathbb{R}^4: x,y\in\mathbb{R}\}$ con las operaciones

$$
\begin{align*} (x,y,y,-x) + (w,z,z,-w) & =
(x+w, y+z, y+z, -(x+w)), \\ k(x,y,y,-x) & = (kx, ky, ky, -kx), k\in\mathbb{R},
\end{align*}
$$

constituye un espacio vectorial de dos dimensiones.

### Ejercicio 6

Dado el número real $a$, considérese la matriz $A\in M_{4\times 3}(\mathbb{R})$
y el vector $b\in\mathbb{R}^4$ siguientes:

$$
\begin{align*} A =
\begin{bmatrix} -1 & 2 & 0 \\ 0 & 1 & -1 \\ -1 & 1 & 1 \\ 0 & 1 & -1
\end{bmatrix}, b = \begin{bmatrix} 0 \\ 1 \\ a-2 \\ a^2 \end{bmatrix},
\end{align*}
$$

y el subespacio $F$ de $\mathbb{R}^4$ cuyas ecuaciones implícitas en la base
canónica de $\mathbb{R}^4$ son

$$
\begin{align*} F = \left\{
\begin{aligned} x_1 + x_2 - x_4 & = 0 \\ x_1 + x_3 + x_4 & = 0 \end{aligned}
\right. \end{align*}
$$

- a) Discuta, y resuelva cuando sea compatible, el sistema $AX = b$.
- b) Calcule unas ecuaciones implícitas del subespacio $E$ de $\mathbb{R}^4$
  generado por las columnas de $A$.
- c) Encuentre una base del subespacio $E\cap F$.
- d) Calcule la matriz respecto de las bases canónicas de $\mathbb{R}^3$ y
  $\mathbb{R}^4$ de la aplicación lineal $T:\mathbb{R}^3\rightarrow\mathbb{R}^4$
  que cumple
  $$\begin{align*} T(e_1) = f(e_2+e_3),\quad T(e_2) =
  f(e_3),\quad\text{y}\quad T(e_3)=f(e_2), \end{align*}$$
  donde $B := \{e_1, e_2, e_3\}$ es la base canónica de $\mathbb{R}^3$ y
  $f\mathbb{R}^3\rightarrow\mathbb{R}^4$ es la aplicación lineal cuya matriz
  asociada en las respectivas bases canónicas de $\mathbb{R}^3$ y $\mathbb{R}^4$
  es $A$.

### Ejercicio 7

En el espacio vectorial $\mathbb{Q}^4$ se consideran los subespacios:

$$
\begin{align*} S_1 = \left\langle \begin{bmatrix} 1 \\ 1 \\ 0 \\ 0
\end{bmatrix}, \begin{bmatrix} 1 \\ 0 \\ -1 \\ 0 \end{bmatrix}, \begin{bmatrix}
1 \\ 3 \\ 2 \\ 0 \end{bmatrix} \right\rangle, S_2 = \left\{ \begin{aligned} x-y
& =0 \\ x-z & =0 \end{aligned} \right. \text{ y } S_3 = \{y+z = 0\}.
\end{align*}
$$

- a) Halle $dim(S_1+S_2)$ y $dim(S_1\cap S_2)$.
- b) Halle una base de $S_1\cap S_3$.
- c) ¿Qué dimensión tiene $S_1+S_3$.

### Ejercicio 8

- a) Demostrar que el subconjunto de $\mathbb{R}^4$ formado por todas las
  cuaternas $(x,y,z,t)$ que verifican las relaciones:
    $$
    \begin{align*} \left\{ \begin{aligned} x+y+z+t & =0 \\ x-y+z-t & =0
    \end{aligned} \right. \end{align*}
    $$
    forma un subespacio vetorial de $(\mathbb{R}^4, +, \cdot)$.
- b) Probar que los vectores $\{u_1 = (2,1,-2,-1), u_2 = (1,0,-1,0)\}$ forman
  una base para dicho subespacio vectorial.
- c) Hallar las coordenadas del vector $u = (4,1,-4,-1)$ respecto de la base
  $\{u_1, u_2\}$.
