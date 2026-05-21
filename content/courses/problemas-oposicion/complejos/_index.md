---
title: Números complejos
math: true
weight: 90
sidebar:
    open: false
---

## Problemas resueltos

### Problema 1

Dada una constante real positiva, $a$, y el conjunto

$$
M_a = \left\{z\in\mathbb{C}^* : \left|z+\dfrac{1}{z}\right|=a \right\},
$$

donde $\mathbb{C}^* = \mathbb{C}\backslash\{(0,0)\}$, encuentre los valores
mínimo y máximo de $|z|$ cuando $z\in M_a$.

**Solución**: hemos de ser capaces de extraer información sobre el módulo de
$z$, $|z|$, a partir de la expresión de la ecuación que define al conjunto
$M_a$. Por las propiedades de la conjugación, sabemos que
$z\overline{z} = |z|^2$, de manera que una posible estrategia a seguir sería
elevar al cuadrado ambos miembros de la ecuación que define a $M_a$ y
desarrollar la expresión resultante mediante las propiedades de la conjugación.
Así,

$$
\begin{aligned}
a^2 &= \left|z+\dfrac{1}{z}\right|^2 = \left(z+\dfrac{1}{z}\right)\overline{\left(z+\dfrac{1}{z}\right)} = \left(z+\dfrac{1}{z}\right)\left(\overline{z}+\dfrac{1}{\overline{z}}\right)\\\\ &= z\overline{z} + \dfrac{z}{\overline{z}} + \dfrac{\overline{z}}{z} + \dfrac{1}{z\overline{z}} = z\overline{z} + \dfrac{z^2 + \overline{z}^2}{\overline{z}z} + \dfrac{1}{z\overline{z}},
\end{aligned}
$$

pero recordemos que $z\overline{z} = |z|^2$, por lo que la anterior ecuación
quedaría

$$
a^2 = |z|^2 + \dfrac{z^2+\overline{z}^2}{|z|^2}+\dfrac{1}{|z|^2},
$$

y multiplicando ambos miembros por $|z|^2$, número que sabemos es distinto de
cero porque $z\in\mathbb{C}^*$, tenemos

$$
a^2|z|^2 = |z|^4 + z^2 + \overline{z}^2 + 1.
$$

Ahora bien, a primera vista, la anterior expresión parece que quiere conducirnos
hacia alguna especie de ecuación bicuadrada en $|z|$. Efectivamente, si
reordenamos los términos de manera adecuada, llegamos a

$$
|z|^4 - a^2|z|^2 + 1 = - (z^2 + \overline{z}^2)
$$

y si completamos el cuadrado del miembro derecho,

$$
\begin{aligned}
|z|^4 - a^2|z|^2 + 1 &= - (z^2 + \overline{z}^2 + 2z\overline{z} - 2z\overline{z})\\\\ &= - (z + \overline{z})^2 + 2z\overline{z}\\\\ &= - (z + \overline{z})^2 + 2|z|^2,
\end{aligned}
$$

es decir,

$$
|z|^4 - (a^2+2)|z|^2 + 1 = - (z+\overline{z})^2 \leq 0.
$$

Por lo tanto, tras realizar operaciones algebraicas sobre la ecuación que define
al conjunto $M_a$, hemos llegado a que la expresión de cierta ecuación
bicuadrada en $|z|$ debe ser menor o igual que cero. Investiguemos si de ella
podemos extraer alguna condición sobre el módulo de $z$ que nos permita dar
respuesta al problema planteado.

Resolviendo $|z|^4 - (a^2 + 2)|z|^2 + 1 = 0$ y teniendo en cuenta que es
positivo el coeficiente asociado a $|z|^4$, tenemos que
$|z|^4 - (a^2 + 2)|z|^2 + 1 \leq 0$ si, y solo si,

$$
|z|^2\in \left[
\dfrac{2+a^2 - \sqrt{a^4+4a^2}}{2}, \dfrac{2+a^2 + \sqrt{a^4+4a^2}}{2}
\right],
$$

que es equivalente a decir que

$$
|z|\in \left[
\dfrac{-a + \sqrt{a^2+4}}{2}, \dfrac{a + \sqrt{a^2+4}}{2}
\right].
$$

Veamos esta última equivalencia en detalle, pues puede no resultarnos trivial a
primera vista. La idea aquí es representar ambos extremos del intervalo que
hemos obtenido para $|z|^2$ como cuadrados de ciertas expresiones. Si somos
capaces de llevar a cabo tal tarea, únicamente bastará aplicar la raíz cuadrada
(que, recordemos, es una transformación monótona creciente) para, de esta
manera, llegar a la conclusión obtenida para $|z|$.

Centrémonos en la expresión del extremo inferior del intervalo definido para
$|z|^2$ (el razonamiento a seguir sería análogo para el superior). Por un lado,

$$
2+a^2 - \sqrt{a^4 + 4a^2} = 2+a^2 - a\sqrt{a^2 + 4},
$$

expresión que nos invita a experimentar con el desarrollo de
$(-a + \sqrt{a^2 + 4})^2$. Así,

$$
\begin{aligned}
(-a + \sqrt{a^2+4})^2 &= a^2 + a^2 + 4 - 2a\sqrt{a^2+4}\\\\ &= 2a^2+4 - 2a\sqrt{a^2+4}\\\\ &= 2(a^2+2-a\sqrt{a^2+4})\\\\ &= 2(a^2+2-\sqrt{a^4+4a^2}),
\end{aligned}
$$

de forma que

$$
\dfrac{2+a^2 - \sqrt{a^4+4a^2}}{2} = \dfrac{(-a + \sqrt{a^2+4})^2}{2\cdot 2} = \left(\dfrac{-a + \sqrt{a^2+4}}{2}\right)^2.
$$

Por tanto, hemos llegado a que

$$
\begin{aligned}
\min{|z|} &= \dfrac{-a+\sqrt{a^2+4}}{2},\\\\ \max{|z|} &= \dfrac{a+\sqrt{a^2+4}}{2},
\end{aligned}
$$

y los valores extremos se alcanzarán cuando se dé la igualdad en la inecuación
considerada, es decir, cuando $-(z+\overline{z})^2 = 0$, que equivale a la
condición $z=-\overline{z}$. Así pues, los valores extremos se alcanzarán para
los números complejos $z\in M_a$ tales que $z=-\overline{z}$.

## Problemas propuestos

**Problema 2:** halla el conjunto de puntos de la variable compleja $z$ tal que
$RE(z^2) > 2$.

**Problema 3:** halla la curva definida por

$$
RE\left(\frac{1}{z}\right) = \frac{1}{4}.
$$

**Problema 4:** calcula $\sqrt{-15-8i}$.

**Problema 5:** resuelve $z^2 + (2i - 3)z + 5-i = 0$.

**Problema 6:** halla las raíces quintas de la unidad.

**Problema 7:** sean $r_i$, con $i=1,\ldots,5$, las raíces quintas de la unidad.
Halla el valor de

$$
A = r_1^n + r_2^n + r_3^n + r_4^n + r_5^n.
$$

**Problema 8:** calcula $(1+\sqrt{3}i)^n + (1-\sqrt{3}i)^n$.

**Problema 9:** sea

$$
z = \left(\frac{-1+\sqrt{3}i}{2}\right)^n + \left(\frac{-1-\sqrt{3}i}{2}\right)^n.
$$

Prueba que $z=2$ si $n$ es múltiplo de $3$ y $z=-1$ en cualquier otro caso.

**Problema 10:** escribe en forma binómica $e^{\sqrt{i}}$.

**Problema 11:** si

$$
z + \frac{1}{z} = 2\cos{t},
$$

calcula

$$
z^n + \frac{1}{z^n}.
$$

**Problema 12:** halla un número complejo que cumpla $z^5 = \overline{z}$.

**Problema 13:** calcula $3^i$.

**Problema 14:** calcula $\log_{1 + i}{(8 - 8i)}$.

**Problema 15:** resuelve

- (a) $\cos{(z)} = 2$.
- (b) $\sin{(z)} = 4$.

**Problema 16:** resuelve $\cosh^2{(z)} - 3\sinh{(z)} + 1 = 0$.

**Problema 17:** dados los puntos $A(1, 2)$ y $B(3,3)$, determina, como número
complejo en forma binómica, los vértices de un triángulo equilátero con centro
$A$, sabiendo que $B$ es uno de sus vértices.

**Problema 18:** determine los vértices de un cuadrado sabiendo que

- (a) Su centro es el punto $(2, 3)$.
- (b) Si se traslada el centro al origen, se gira un ángulo de $60$ grados, en
  sentido positivo, y se reducen los lados del cuadrado a la mitad; los vértices
  del nuevo cuadrado son los afijos de las raíces de un polinomio de grado
  cuatro, con coeficientes reales, que tiene la raíz $x = 1$.

**Problema 19:** los afijos $z_1, z_2, z_3, z_4, z_5$ y $z_6$ son los vértices
consecutivos de un hexágono regular. Sabiendo que $z_1 = 0$ y que
$z_4 = 4 + 6i$, halla $z_2, z_3, z_5$ y $z_6$.

**Problema 20:** dados tres complejos $z_1, z_2$ y $z_3$, demuestra que si
forman un triángulo equilátero, se cumple que

$$
z_1^2 + z_2^2 + z_3^2 = z_1z_2 + z_1z_3 + z_2z_3.
$$

**Problema 21:** siendo $a$ un número complejo fijo, determina (en función de
$a$) los posibles números complejos $z$, tales que las imágenes en el plano
complejo de los afijos $a^2z, az^2$ y $z^3$ son vértices de un triángulo
equilátero.

**Problema 22:** calcula

- (a) $\prod_{k=1}^{n-1}{\left(e^{\frac{2k\pi i}{n}} - 1\right)}$.
- (b) $\prod_{k=1}^{n-1}{\sin{\left(\frac{k\pi}{n}\right)}}$.

**Problema 23:** dado un número real $a$ y un número natural $n$, calcula

$$
\cos{(a)} + \cos{(2a)} + \cos{(3a)} + \cdots + \cos{(na)}.
$$

**Problema 24:** calcula

$$
\sum_{n=0}^{\infty}{\frac{\cos{(n\alpha)}}{2^n}}.
$$
