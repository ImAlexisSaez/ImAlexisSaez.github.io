---
title: Determinantes
math: true
weight: 190
sidebar:
    open: false
---

## Problemas resueltos

### Problema 1

Sea $k$ un número natural no nulo y sea $f$ la función real de variable real
dada por:

$$
f(x) =
\begin{vmatrix}
\binom{1}{0} & 0 & 0 &\ldots & 0 & x\\\\ \binom{2}{0} & \binom{2}{1} & 0 &\ldots & 0 & x^2\\\\ \binom{3}{0} & \binom{3}{1} & \binom{3}{2} & \ldots & 0 & x^3\\\\ \vdots & \vdots & \vdots & \ddots & \vdots & \vdots\\\\ \binom{k}{0} & \binom{k}{1} & \binom{k}{2} & \ldots & \binom{k}{k-1} & x^k\\\\ \binom{k+1}{0} & \binom{k+1}{1} & \binom{k+1}{2} &\ldots & \binom{k+1}{k-1} & x^{k+1}
\end{vmatrix}.
$$

a) Calcular $f(x + 1) - f(x)$.

b) Expresar la suma $1^k + 2^k + \cdots + n^k$ mediante esta función.

**Solución**: en lugar de abordar directamente la resolución del primer
apartado, detengámonos por un instante a analizar la expresión del determinante
dado por la función $f(x)$. Los números combinatorios que aparecen y, sobre
todo, la forma en que lo hacen, seguramente hayan captado nuestra atención.
Resulta, cuanto menos, familiar ese patrón, ¿verdad? Parte de él es el que
aparece en el famoso _triángulo de Pascal_, si expresamos sus componentes
utilizando números combinatorios.

Ahora bien, de manera automática, y supongo que por deformación matemática,
cuando viene a nuestra cabeza el _triángulo de Pascal_, enseguida pensamos en el
_teorema del binomio_, que recordemos afirma que

$$
\begin{aligned}
(x+y)^n &= \sum_{k=0}^{n}{\binom{n}{k}x^{n-k}y^k}\\\\ &= \binom{n}{0}x^n + \binom{n}{1}x^{n-1}y+\cdots+\binom{n}{n-1}xy^{n-1}+\binom{n}{n}y^n.
\end{aligned}
$$

Merece la pena explorar la idea de una posible relación entre el _teorema del
binomio_ y la expresión de $f(x)$. Para empezar, en la última columna del
determinante encontramos las potencias de $x$, pero no observamos la existencia
de más potencias en el resto de los elementos de dicho determinante. Este hecho
nos invita a pensar que quizá sea conveniente que particularmente estudiemos el
desarrollo del binomio $(1+x)^n$, dado el valor de las potencias de uno. Además,
si ahora echamos un vistazo rápido al enunciado del primer apartado, aparece un
$(1+x)$, ¡puede que estemos sobre la pista de la senda correcta!

Desarrollemos $(1+x)^n$, para algunos valores concretos de $n$, utilizando para
ello el _teorema del binomio_:

$$
\begin{aligned}
(1+x)^1 &= \dbinom{1}{0} + \dbinom{1}{1}x,\\\\ (1+x)^2 &= \dbinom{2}{0} + \dbinom{2}{1}x + \dbinom{2}{2}x^2,\\\\ (1+x)^3 &= \dbinom{3}{0} + \dbinom{3}{1}x + \dbinom{3}{2}x^2 + \dbinom{3}{3}x^3,\\\\ (1+x)^4 &= \dbinom{4}{0} + \dbinom{4}{1}x + \dbinom{4}{2}x^2 + \dbinom{4}{3}x^3 + \dbinom{4}{4}x^4.
\end{aligned}
$$

Para empezar, enseguida apreciamos que las potencias de $x$ vienen siempre
acompañadas por un número combinatorio. No obstante, como dado $n\in\mathbb{N}$,
tenemos que

$$
\binom{n}{n}=1,
$$

podemos reescribir la última columna del determinante dado por $f(x)$ de la
siguiente manera:

$$
f(x) =
\begin{vmatrix}
\binom{1}{0} & 0 & 0 &\ldots & 0 & \binom{1}{1}x^{\phantom{1}}\\\\ \binom{2}{0} & \binom{2}{1} & 0 &\ldots & 0 & \binom{2}{2}x^2\\\\ \binom{3}{0} & \binom{3}{1} & \binom{3}{2} & \ldots & 0 & \binom{3}{3}x^3\\\\ \vdots & \vdots & \vdots & \ddots & \vdots & \vdots\\\\ \binom{k}{0} & \binom{k}{1} & \binom{k}{2} & \ldots & \binom{k}{k-1} & \binom{k}{k}x^k\\\\ \binom{k+1}{0} & \binom{k+1}{1} & \binom{k+1}{2} &\ldots & \binom{k+1}{k-1} & \binom{k+1}{k+1}x^{k+1}
\end{vmatrix}
$$

Ahora, centremos nuestra atención en la primera fila del determinante. Si
sumamos el elemento que figura en la primera columna al que reside en la última,
tendríamos

$$
\binom{1}{0} + \binom{1}{1}x = (1+x)^1 = 1+x.
$$

Este hecho nos sugiere que llevemos a cabo la transformación sobre el
determinante que consiste en sustituir la última columna por una combinación
lineal de esta con la primera columna, que sabemos, por las propiedades de los
determinantes, que no altera el valor de $f(x)$. Utilizando la notación habitual
de operaciones sobre determinantes, estaríamos proponiendo llevar a cabo la
transformación

$$
C^{\prime}_{k+1}\rightarrow C_1 + C_{k+1}.
$$

Pasemos, a continuación, a estudiar la segunda fila determinante. Con la idea
del párrafo anterior en mente, ¿podemos llegar a conseguir el desarrollo del
binomio $(1+x)^2$? En realidad, tenemos casi todos los elementos de dicho
desarrollo, a falta de una $x$ que tendría que estar multiplicando al elemento
que aparece en la segunda columna. No obstante, recordemos aquí que $x$ no es
más que un número real, por lo que podríamos multiplicar toda la segunda columna
por $x$ y sumarla, junto con la primera columna, a la última. Es decir, la idea
es llevar a cabo la transformación

$$
C^{\prime}_{k+1}\rightarrow C_1 + xC_2 + C_{k+1},
$$

que permitiría que el elemento de la última columna fuese precisamente
$(1+x)^2$.

Empezamos a atisbar un patrón aquí, ¿verdad? Analizando la tercera fila,
llegaríamos a proponer la transformación

$$
C^{\prime}_{k+1}\rightarrow C_1 + xC_2 + x^2C_3 + C_{k+1},
$$

y, siguiendo con el razonamiento, la transformación que al final llevaremos a
cabo sobre el determinante será la siguiente:

$$
C^{\prime}_{k+1}\rightarrow C_1 + xC_2 + x^2C_3 + \cdots + x^{k-1}C_k + C_{k+1},
$$

que hace que los elementos de la última columna sean binomios de la forma
$(1+x)^n$, con $0\leq n\leq k+1$.

¡Cuidado! No es cierta la conclusión escrita arriba o, al menos, no lo es para
todos los valores indicados de $n$. Si nos fijamos con atención, se cumple para
$n=1$, para $n=2$, y así sucesivamente hasta llegar a $n=k$, ¡pero nos faltaría,
para $n=k+1$, un término del desarrollo del binomio! Si nos damos cuenta, no
aparece en el determinante

$$
\binom{k+1}{k}x^k,
$$

pero como esa expresión no deja de ser un número, podemos sumarlo y restarlo en
esa posición para conseguir así el desarrollo del binomio $(1+x)^{k+1}$,
quedando entonces la expresión de $f(x)$ como sigue:

$$
f(x) =
\begin{vmatrix}
\binom{1}{0} & 0 & 0 &\ldots & 0 & 1+x\\\\ \binom{2}{0} & \binom{2}{1} & 0 &\ldots & 0 & (1+x)^2\\\\ \binom{3}{0} & \binom{3}{1} & \binom{3}{2} & \ldots & 0 & (1+x)^3\\\\ \vdots & \vdots & \vdots & \ddots & \vdots & \vdots\\\\ \binom{k}{0} & \binom{k}{1} & \binom{k}{2} & \ldots & \binom{k}{k-1} & (1+x)^k\\\\ \binom{k+1}{0} & \binom{k+1}{1} & \binom{k+1}{2} &\ldots & \binom{k+1}{k-1} & (1+x)^{k+1} - \binom{k+1}{k}x^k
\end{vmatrix}
$$

Esa resta que aparece en el último elemento de la diagonal principal nos invita
a seguir aplicando propiedades de los determinantes y separar en dos el dado en
$f(x)$. Así, podemos escribir

$$
f(x) = g(x) + h(x),
$$

donde

$$
g(x) =
\begin{vmatrix}
\binom{1}{0} & 0 & 0 &\ldots & 0 & 1+x\\\\ \binom{2}{0} & \binom{2}{1} & 0 &\ldots & 0 & (1+x)^2\\\\ \binom{3}{0} & \binom{3}{1} & \binom{3}{2} & \ldots & 0 & (1+x)^3\\\\ \vdots & \vdots & \vdots & \ddots & \vdots & \vdots\\\\ \binom{k}{0} & \binom{k}{1} & \binom{k}{2} & \ldots & \binom{k}{k-1} & (1+x)^k\\\\ \binom{k+1}{0} & \binom{k+1}{1} & \binom{k+1}{2} &\ldots & \binom{k+1}{k-1} & (1+x)^{k+1}
\end{vmatrix},
$$

y

$$
h(x) =
\begin{vmatrix}
\binom{1}{0} & 0 & 0 &\ldots & 0 & 0\\\\ \binom{2}{0} & \binom{2}{1} & 0 &\ldots & 0 & 0\\\\ \binom{3}{0} & \binom{3}{1} & \binom{3}{2} & \ldots & 0 & 0\\\\ \vdots & \vdots & \vdots & \ddots & \vdots & \vdots\\\\ \binom{k}{0} & \binom{k}{1} & \binom{k}{2} & \ldots & \binom{k}{k-1} & 0\\\\ \binom{k+1}{0} & \binom{k+1}{1} & \binom{k+1}{2} &\ldots & \binom{k+1}{k-1} & - \binom{k+1}{k}x^k
\end{vmatrix}.
$$

Ahora bien, enseguida nos damos cuenta de que la única diferencia entre $f(x)$ y
$g(x)$ radica en que allí donde aparece $x$ en $f(x)$, figura ahora $1+x$ en
$g(x)$, lo cual nos permite concluir que $g(x) = f(1+x)$.

Por otro lado, en $h(x)$ tenemos una matriz triangular inferior, cuyo
determinante sabemos es igual al producto de los elementos que componen su
diagonal principal, es decir,

$$
\begin{aligned}
h(x) &= -\binom{1}{0}\binom{2}{1}\binom{3}{2}\binom{4}{3}\cdots\binom{k+1}{k}x^k\\\\ &=-2!\dfrac{3!}{2!}\dfrac{4!}{3!}\cdots\dfrac{(k+1)!}{k!}x^k\\\\ &=-(k+1)!x^k.
\end{aligned}
$$

Así, como

$$
f(x) = g(x) + h(x) = f(1+x) - (k+1)!x^k,
$$

la respuesta para el primer apartado de este problema sería:

$$
f(x+1) - f(x) = (k+1)!x^k.
$$

En el segundo apartado nos piden calcular el valor de la suma

$$
1^k + 2^k + \cdots + n^k
$$

utilizado $f(x)$. Enseguida nos damos cuenta de que aparece $x^k$ en la
expresión final del apartado anterior, hecho que nos invita a asignarle el valor
$n$ a la variable $x$, quedando entonces la ecuación

$$
f(n+1) - f(n) = (k+1)!n^k.
$$

Siguiendo esta idea, para conseguir que aparezca $(n-1)^k$, asignaríamos el
valor $n-1$ a la variable $x$, obteniendo así la ecuación

$$
f(n) - f(n-1) = (k+1)!(n-1)^k.
$$

Iteramos sucesivamente esta manera de proceder, de forma que al final tenemos el
siguiente conjunto de ecuaciones:

$$
\begin{aligned}
f(n+1) - f(n) &= (k+1)!n^k,\\\\ f(n) - f(n-1) &= (k+1)!(n-1)^k,\\\\ f(n-1) - f(n-2) &= (k+1)!(n-2)^k,\\\\ \vdots & \\\\ f(2) - f(1) &= (k+1)!1^k,
\end{aligned}
$$

y sumando todas ellas, llegamos a que

$$
f(n+1) - f(1) = (k+1)!(1^k+2^k+\cdots+n^k).
$$

Ahora bien,

$$
f(1) =
\begin{vmatrix}
\binom{1}{0} & 0 & 0 &\ldots & 0 & 1\\\\ \binom{2}{0} & \binom{2}{1} & 0 &\ldots & 0 & 1\\\\ \binom{3}{0} & \binom{3}{1} & \binom{3}{2} & \ldots & 0 & 1\\\\ \vdots & \vdots & \vdots & \ddots & \vdots & \vdots\\\\ \binom{k}{0} & \binom{k}{1} & \binom{k}{2} & \ldots & \binom{k}{k-1} & 1\\\\ \binom{k+1}{0} & \binom{k+1}{1} & \binom{k+1}{2} &\ldots & \binom{k+1}{k-1} & 1
\end{vmatrix},
$$

y si recordamos que, dado $n\in\mathbb{N}$,

$$
\binom{n}{0} = 1,
$$

resulta que la primera columna es igual a la última, provocando ello que
$f(1)=0$ y, finalmente, que

$$
1^k + 2^k + \cdots + n^k = \dfrac{f(n+1)}{(k+1)!},
$$

expresión que da respuesta a la cuestión planteada en el segundo apartado del
problema.

## Problemas propuestos

Pendiente de recopilación.
