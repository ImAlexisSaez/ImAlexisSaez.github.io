---
title: Inducción
math: true
weight: 10
sidebar:
    open: false
---

## Problemas resueltos

### Problema 1

Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$,

$$
1 + 2 + \cdots + n = \dfrac{n(n+1)}{2}.
$$

**Solución**: generalmente, cuando abordamos problemas en los que tenemos que
demostrar que cierta fórmula o afirmación se satisface, para un conjunto de
índices de cardinal infinito (en esta ocasión hablaríamos del conjunto $n\geq1$,
con $n\in\mathbb{N}$), es recomendable que llevemos a cabo una primera
aproximación a su resolución empleando el _principio de inducción matemática_.

Así pues, vamos a considerar la propiedad, que denotaremos por $P(n)$, dada en
el enunciado del problema,

$$
1+2+\cdots+n = \dfrac{n(n+1)}{2}.
$$

Por lo que respecta al _caso base_, $P(1)$, rápidamente comprobamos que se
verifica de manera trivial, ya que

$$
1 = \dfrac{1\cdot2}{2} = 1.
$$

Abordemos ahora el _paso inductivo_, para lo cual hemos de mostrar que si $P(n)$
se cumple, para un $n\geq1$, entonces asimismo se satisface $P(n+1)$, cuya
expresión es

$$
1+2+\cdots+n+(n+1)=\dfrac{(n+1)(n+2)}{2}.
$$

La clave en este tipo de situaciones consiste en encontrar una manera acertada
de manipular la conocida como _hipótesis de inducción_, $P(n)$, que nos ayude a
verificar el resultado que estamos buscando comprobar.

Por fortuna para nosotros, si nos fijamos en el miembro izquierdo de la ecuación
de $P(n+1)$, apreciamos que directamente aparece la suma de los $n$ primeros
números naturales, cuyo valor, por la _hipótesis de inducción_, es

$$
\dfrac{n(n+1)}{2}.
$$

Este hecho nos permite afirmar que

$$
1+2+\cdots+n+(n+1) = \dfrac{n(n+1)}{2} + (n+1).
$$

Ahora, sumando algebraicamente ambos términos,

$$
\dfrac{n(n+1)}{2} + (n+1)= \dfrac{n(n+1) + 2(n+1)}{2}= \dfrac{(n+1)(n+2)}{2},
$$

es decir, hemos llegado a mostrar que

$$
1+2+\cdots+n+(n+1)=\dfrac{(n+1)(n+2)}{2},
$$

completando así el _paso inductivo_.

Así pues, por el _principio de inducción matemática_, podemos concluir que
$P(n)$ se verifica para cada $n\in\mathbb{N}$, con $n\geq 1$.

### Problema 2

Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$,

$$
\sum_{k=1}^{n}{k^2} = \dfrac{n(n+1)(2n+1)}{6}.
$$

**Solución**: ante nosotros se plantea la tarea de demostrar una propiedad (la
identidad sugerida arriba), que supuestamente se satisface para una sucesión de
índices enteros que conforman un conjunto cuyo cardinal es infinito
($n\in\mathbb{N}$, con $n\geq 1$, en este caso). Entre las diferentes
estrategias que tenemos a nuestra disposición para abordar esta empresa, el
_principio de inducción matemática_ quizá sea el instrumento más aconsejable
para una primera aproximación a la resolución del problema.

Así pues, la manera en la que ahora procederemos será ciertamente similar a la
seguida en el problema 1. Para empezar, a simple vista, podemos apreciar
rápidamente que la igualdad se satisface de forma trivial para $n=1$, puesto que

$$
1 = \sum_{k=1}^{1}{k^2} = \dfrac{1\cdot2\cdot3}{6} = 1.
$$

Acto seguido, asumimos verdadera la identidad para un cierto $n\in\mathbb{N}$,
con $n\geq 1$, es decir, que efectivamente se verifica que

$$
\sum_{k=1}^{n}{k^2} = \dfrac{n(n+1)(2n+1)}{6},
$$

y estudiamos si se satisface asimismo para $n+1$. Así pues, ahora comprobaremos
si se cumple la igualdad

$$
\sum_{k=1}^{n+1}{k^2} = \dfrac{(n+1)(n+2)(2n+3)}{6}.
$$

Para ello, apliquemos la _hipótesis de inducción_ y llevemos a cabo algunas
operaciones algebraicas elementales, de manera que

$$
\begin{aligned}
\sum_{k=1}^{n+1}{k^2} &= (n+1)^2 + \sum_{k=1}^{n}{k^2}\\ & = (n+1)^2 + \dfrac{n(n+1)(2n+1)}{6}\\ & = \dfrac{6(n+1)^2 + n(n+1)(2n+1)}{6}\\ & = \dfrac{(n+1)(6(n+1) + n(2n+1))}{6}\\ & = \dfrac{(n+1)(2n^2+7n+6)}{6}\\ & = \dfrac{(n+1)(n+2)(2n+3)}{6},
\end{aligned}
$$

y, por tanto, la identidad se verifica para $n+1$. El _principio de inducción
matemática_ nos permite concluir que es cierta para cada $n\in\mathbb{N}$.

### Problema 3

Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$,

$$
1^3 + 2^3 + \cdots + n^3=(1+2+3+\cdots+n)^2.
$$

**Solución**: para empezar, y de cara a aliviar ligeramente la escritura en un
futuro, podemos plantear de manera más compacta la identidad dada en el
enunciado del presente problema como sigue

$$
1^3 + 2^3 + \cdots + n^3 = \sum_{k=1}^{n}{k^3} = \left(\sum_{k=1}^{n}{k}\right)^2 = (1+2+3+\cdots+n)^2.
$$

En esta ocasión, si optamos por una aproximación similar a la seguida en los
problemas anteriores, la demostración puede volverse un tanto tediosa debido a
los cálculos implicados. Es por ello que, utilizando el resultado probado en el
problema 1, la igualdad que buscamos verificar aquí sería equivalente a

$$
\sum_{k=1}^{n}{k^3} = \left(\sum_{k=1}^{n}{k}\right)^2
= \left(\dfrac{n(n+1)}{2}\right)^2
= \dfrac{n^2(n+1)^2}{4}.
$$

Una vez alcanzada una expresión más manejable para la identidad planteada,
empleamos el _principio de inducción matemática_ para probarla. Rápidamente
comprobamos que se verifica de manera trivial para $n=1$, puesto que

$$
1 = 1^3 = \dfrac{1^2\cdot2^2}{4} = \dfrac{4}{4} = 1.
$$

Ahora, suponemos cierta la identidad para un número dado $n\in\mathbb{N}$, con
$n\geq 1$, es decir, que efectivamente se cumple que

$$
\sum_{k=1}^{n}{k^3} = \dfrac{n^2(n+1)^2}{4},
$$

y estudiamos si se satisface asimismo para $n+1$. Así pues, acto seguido, el
objetivo que tenemos entre manos es verificar si es cierta la igualdad

$$
\sum_{k=1}^{n+1}{k^3} = \dfrac{(n+1)^2(n+2)^2}{4}.
$$

Apliquemos la _hipótesis de inducción_ y llevemos a cabo algunas operaciones
algebraicas elementales, de manera que

$$
\begin{aligned}
\sum_{k=1}^{n+1}{k^3} &= (n+1)^3 + \sum_{k=1}^{n}{k^3}\\ &= (n+1)^3 + \dfrac{n^2(n+1)^2}{4}\\ &= \dfrac{4(n+1)^3 + n^2(n+1)^2}{4}\\ &= \dfrac{(n+1)^2(4(n+1)+n^2)}{4}\\ &= \dfrac{(n+1)^2(n^2+4n+4)}{4}\\ &= \dfrac{(n+1)^2(n+2)^2}{4}
\end{aligned}
$$

y, por tanto, la identidad se verifica para $n+1$. El _principio de inducción
matemática_ nos permite concluir que es cierta para cada $n\in\mathbb{N}$.

### Problema 4

Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$,

$$
1^4+2^4+\cdots+n^4=\dfrac{n(n+1)(6n^3+9n^2+n-1)}{30}.
$$

**Solución**: vaya por delante que estamos ante uno de esos problemas que
rápidamente se ganan el apelativo de tediosos, no tanto por su dificultad, sino
por el elevado número de operaciones algebraicas que debemos llevar a cabo
durante el proceso de su resolución.

Cuando en una propiedad a verificar aparecen involucrados polinomios de grado
considerable, la segunda parte del _principio de inducción matemática_ conlleva
el desarrollo de múltiples binomios de la forma $(n+1)^m$, con $m\in\mathbb{N}$.
Para reducir un tanto el tedio, siempre es aconsejable que, en primer lugar,
factoricemos los mencionados polinomios.

Como nota curiosa, consultados diferentes recursos didácticos, la fórmula para
la suma de las potencias cuartas de los $n$ primeros números naturales suele
venir dada por

$$
1^4 + 2^4 + \cdots + n^4=\dfrac{6n^5+15n^4+10n^3-n}{30},
$$

hecho que nos puede llevar a sospechar que la proporcionada en el enunciado del
presente problema ya está completamente factorizada.

No obstante, como por naturaleza hemos de ser recelosos, utilicemos el _Teorema
de la raíz racional_ para investigar si podemos escribir el polinomio
$6n^3 + 9n^2 + n - 1$ de una manera que nos resulte más cómoda de cara a futuras
operaciones con él. Recordemos que, dada una ecuación polinómica con
coeficientes enteros

$$
a_mn^m + a_{m-1}n^{m-1} + \cdots + a_0=0,
$$

si $a_0$ y $a_m$ son enteros distintos de cero, entonces las posibles soluciones
que son del tipo $n = p/q$ satisfacen:

- $p$ es divisor de $a_0$.
- $q$ es divisor de $a_m$.
- $p$ y $q$ son primos entre sí.

En nuestro problema, el conjunto de candidatos para $p$ es $\\{\pm1\\}$,
mientras que para $q$ es $\\{\pm1,\pm2,\pm3,\pm6\\}$ y rápidamente podemos
comprobar que $n = -1 / 2$ es solución del polinomio dado. Así,

$$
6n^3 + 9n^2 + n - 1 = (2n + 1)(3n^2 + 3n - 1),
$$

de manera que

$$
\begin{aligned}
\sum_{k=1}^{n}{k^4} &= 1^4+2^4+\cdots+n^4\\ &= \dfrac{n(n+1)(6n^3+9n^2+n-1)}{30}\\ &=\dfrac{n(n+1)(2n+1)(3n^2+3n-1)}{30}.
\end{aligned}
$$

Una vez hemos alcanzado una expresión irreducible para el polinomio que figura
en el numerador de la identidad anterior, utilizamos el _principio de inducción
matemática_ para comprobar dicha igualdad. Enseguida observamos que se satisface
de manera trivial para $n=1$, puesto que

$$
1 = 1^4 = \dfrac{1\cdot2\cdot3\cdot5}{30}=1.
$$

A continuación, suponemos verdadera la identidad para un cierto
$n\in\mathbb{N}$, con $n\geq 1$, es decir, que efectivamente se verifica que

$$
\sum_{k=1}^{n}{k^4} = \dfrac{n(n+1)(2n+1)(3n^2+3n-1)}{30}
$$

y estudiamos si se satisface para $n+1$. Así pues, el objetivo que tenemos ahora
entre manos es comprobar si

$$
\begin{aligned}
\sum_{k=1}^{n+1}{k^4} &= \dfrac{(n+1)(n+2)(2(n+1)+1)(3(n+1)^2+3(n+1)-1)}{30}\\ &= \dfrac{(n+1)(n+2)(2n+3)(3n^2+9n+5)}{30}.
\end{aligned}
$$

Apliquemos la _hipótesis de inducción_ y llevemos a cabo algunas operaciones
algebraicas elementales, de forma que

$$
\begin{aligned}
\sum_{k=1}^{n+1}{k^4} &= (n+1)^4 + \sum_{k=1}^{n}{k^4}\\ &= (n+1)^4 + \dfrac{n(n+1)(2n+1)(3n^2+3n-1)}{30}\\ &= \dfrac{30(n+1)^4 + n(n+1)(2n+1)(3n^2+3n-1)}{30}\\ &= \dfrac{(n+1)(30(n+1)^3+n(2n+1)(3n^2+3n-1))}{30}.
\end{aligned}
$$

Por tanto, el resultado quedaría probado siempre y cuando fuesen equivalentes
las expresiones de los polinomios $(n+2)(2n+3)(3n^2+9n+5)$ y
$30(n+1)^3 + n(2n+1)(3n^2+3n-1)$. Efectivamente, si desarrollamos

$$
\begin{aligned}
(n+2)(2n+3) &= 2n^2+3n+4n+6 = 2n^2+7n+6,\\ (2n^2+7n+6)(3n^2+9n+5) &= 6n^4+39n^3+91n^2+89n+30,
\end{aligned}
$$

y, por otro lado,

$$
\begin{aligned}
30(n+1)^3 &= 30n^3 + 90n^2 + 90n + 30,\\ n(2n+1)(3n^2+3n-1) &= 6n^4+9n^3+n^2-n,
\end{aligned}
$$

de manera que la suma de estas dos últimas ecuaciones asciende a
$6n^4 + 39n^3 + 91n^2 + 89n + 30,$ y, por tanto, la identidad se verifica para
$n+1$. El _principio de inducción matemática_ nos permite concluir que es cierta
para cada $n\in\mathbb{N}$.

### Problema 5

Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$,

$$
n<2^n.
$$

**Solución**: hagamos uso del _principio de inducción matemática_ para demostrar
la desigualdad planteada en el enunciado del problema. Enseguida apreciamos que
esta se cumple de forma trivial para $n=1$, ya que

$$
1 < 2^1 = 2.
$$

Ahora, asumimos cierta la desigualdad para un $n\in\mathbb{N}$ dado, con
$n\geq 1$, es decir, que efectivamente se cumple que

$$
n < 2^n,
$$

y estudiamos si se verifica asimismo para $n+1$. Así pues, el objetivo pasa
ahora por demostrar que se satisface la siguiente desigualdad

$$
n+1 < 2^{n+1}.
$$

Apoyándonos en que $n+1\leq n+n = 2n$, para cada $n\in\mathbb{N}$, (siendo una
desigualdad estricta cuando $n>1$) y en la _hipótesis de inducción_, tenemos que

$$
n+1 \leq n+n = 2n < 2\cdot 2^n = 2^{n+1},
$$

es decir, la desigualdad se verifica para $n+1$. El _principio de inducción
matemática_ nos permite concluir que es cierta para cada $n\in\mathbb{N}$.

### Problema 6

Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$, $4^{n+1} + 5^{2n-1}$
es un múltiplo de 21.

**Solución**: para empezar, decimos que un número $m$ es múltiplo de 21 cuando
existe un número $k\in\mathbb{Z}$ de manera que podemos escribir $m=21k$. Así,
podemos redactar de nuevo el enunciado del ejemplo como sigue: demuestra que,
para cada número $n\in\mathbb{N}$, existe un número $k\in\mathbb{Z}$ tal que

$$
4^{n+1} + 5^{2n-1}=21k.
$$

Utilicemos el _principio de inducción matemática_ para comprobar la anterior
identidad. Rápidamente apreciamos que se cumple de manera trivial para $n=1$,
puesto que

$$
4^{1+1}+5^{2-1} = 4^2 + 5 = 16 + 5 = 21,
$$

y bastaría entonces que tomásemos $k=1$ para constatar que es múltiplo de 21.

Acto seguido, suponemos cierta la igualdad para un $n\in\mathbb{N}$ dado, con
$n\geq 1$, es decir, que efectivamente se cumple que existe un número
$k\in\mathbb{Z}$ tal que

$$
4^{n+1}+5^{2n-1}=21k,
$$

y estudiamos si se satisface asimismo para $n+1$. De esta manera, nuestro
objetivo será demostrar que existe un $k^\prime\in\mathbb{Z}$ tal que se
verifica la siguiente identidad,

$$
4^{n+2} + 5^{2n+1} = 21k^\prime.
$$

Podemos escribir el miembro izquierdo de la ecuación anterior como

$$
4^{n+2} + 5^{2n+1} = 4\cdot4^{n+1} + 5^{2n+1},
$$

y utilizar, acto seguido, la _hipótesis de inducción_, que afirma que existe
$k\in\mathbb{Z}$ tal que $4^{n+1} + 5^{2n-1}=21k$. La clave reside en despejar
adecuadamente el término que nos interesa de dicha hipótesis. Así, como
$4^{n+1} + 5^{2n-1}=21k$, entonces $4^{n+1}=21k - 5^{2n-1}$ y, sustituyendo
arriba, tenemos que

$$
\begin{aligned}
4\cdot4^{n+1} + 5^{2n+1} &= 4(21k - 5^{2n-1}) + 5^{2n+1}\\ &= 4\cdot 21k - 4\cdot 5^{2n-1} + 5^{2n+1}\\ &= 4\cdot 21k - 4\cdot 5^{2n-1} + 5^2\cdot5^{2n-1}\\ &= 4\cdot 21k + 5^{2n-1}(5^2-4)\\ &= 4\cdot 21k + 21\cdot5^{2n-1}\\ &= 21(4k + 5^{2n-1})\\ &= 21k^\prime,
\end{aligned}
$$

con $k^\prime=4k + 5^{2n-1}\in\mathbb{Z}$ y, por tanto, la identidad se verifica
para $n+1$. El _principio de inducción matemática_ nos permite concluir que es
cierta para cada $n\in\mathbb{N}$.

## Problemas propuestos

**Problema 7**: demuestra que $(3^n - 2n^2 - 1)\equiv 0\pmod{8}$, para cada
número natural $n$. ¿Es cierto que dicha expresión también es múltiplo de $24$
para todo número natural $n$?

**Problema 8:** demuestra que $11^{n+1} + 12^{2n-1}$ es múltiplo de $133$, para
cada número natural $n$.

**Problema 9:** demuestra que $(6^n - 1)(7^n - 1)$ es múltiplo de $30$, para
cada número natural $n$.

**Problema 10:** demuestra que $3^{3n+3} - 26n - 27$ es múltiplo de $169$, para
cada número natural $n$.

**Problema 11:**

- (a) Prueba que, para cada número natural $n$,
  $(3^n - 2n^2 - 1)\equiv 0\pmod{8}$.
- (b) Prueba que, si $n$ es un número natural que no es múltiplo de $3$,
  entonces $(3^n - 2n^2 - 1)\equiv 0\pmod{24}$.
