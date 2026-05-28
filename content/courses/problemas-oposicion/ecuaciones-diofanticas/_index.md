---
title: Ecuaciones diofánticas
math: true
weight: 150
sidebar:
    open: false
---

## Problemas resueltos

### Problema 1

- (a) Sea $c$ un número entero positivo tal que $10\leq c\leq 100$. ¿Cuál es el
  valor mínimo de $c$ para el cual la ecuación $84x+990y=c$ admite solución
  entera?
- (b) Un hombre compra caballos y vacas, pagando $1770$ euros. Una vaca cuesta
  $21$ euros y un caballo $31$ euros. ¿Cuántos caballos y vacas ha comprado?

**Solución**: para el apartado (a), como

$$
\begin{aligned}
 84 &= 2^2 \cdot3\cdot7,\\  990 &= 2\cdot 3^2 \cdot5\cdot11,
\end{aligned}
$$

entonces $mcd(84, 990) = 6$. Para que la ecuación diofántica planteada admita
soluciones enteras, $6$ ha de dividir a $c$ y como buscamos el valor mínimo de
$c$, nuestra tarea se reduce pues a encontrar el primer múltiplo de $6$ que
pertenezca al intervalo $[10,100]$. La solución será, por tanto, $c=12$.

En cuanto al apartado (b), consideremos $x$ el número de vacas compradas e $y$
el total de caballos adquiridos. Dados sus respectivos precios y el importe
total desembolsado, planteamos la ecuación diofántica

$$
21x + 31y = 1770.
$$

Como $mcd(21,31) = 1$ y $1|1770$, estamos en condiciones de asegurar que la
anterior ecuación diofántica admite solución entera. Para aliviar cálculos,
empecemos llevando a cabo el cambio de variable

$$
\begin{aligned}
x &= 1770x^{\prime},\\ y &= 1770y^{\prime},
\end{aligned}
$$

con lo cual queda $21x^{\prime} + 31y^{\prime} = 1$. Despejando ahora la
variable $x^{\prime}$,

$$
\begin{aligned}
x^{\prime} = \dfrac{1-31y^{\prime}}{21} = -y^{\prime} + \dfrac{1 - 10y^{\prime}}{21} = -y^{\prime} + x^{\prime\prime},
\end{aligned}
$$

con

$$
x^{\prime\prime} = \dfrac{1-10y^{\prime}}{21},
$$

es decir, $21x^{\prime\prime} = 1-10y^{\prime}$, y despejando ahora la variable
$y^{\prime}$,

$$
y^{\prime} = \dfrac{1-21x^{\prime\prime}}{10},
$$

ecuación para la que, por tanteo, rápidamente observamos que si
$x^{\prime\prime} = 1$, entonces $y^{\prime} = (-2)$. Deshaciendo ahora los
cambios de variable realizados,

$$
\begin{aligned}
x^{\prime} &= -y^{\prime} + x^{\prime\prime} = 2 + 1 = 3,\\ x  &= 1770x^{\prime} = 1770\cdot3 = 5310,\\ y  &= 1770y^{\prime} = 1770\cdot(-2) = -3540,
\end{aligned}
$$

llegamos a una solución particular de la ecuación diofántica propuesta. Así, su
solución general queda

$$
\begin{aligned}
x &= 5310 + 31t,\\ y &= (-3540) - 21t,
\end{aligned}
$$

con $t$ número entero. El número de animales que ha comprado de cada clase ha de
ser, necesariamente, mayor o igual que cero, por lo que planteamos las
inecuaciones,

$$
\begin{aligned}
5310 + 31t &\geq 0\Rightarrow t\geq -\dfrac{5310}{31} = -171.29,\\ -3540-21t  &\geq 0\Rightarrow t\leq -\dfrac{3540}{21} = -168.57.
\end{aligned}
$$

Como $t$ ha de ser entero, concluimos que $-171\leq t\leq -169$. Por tanto,

| $t$    | $x$ (vacas) | $y$ (caballos) |
| ------ | ----------- | -------------- |
| $-171$ | $9$         | $51$           |
| $-170$ | $40$        | $30$           |
| $-169$ | $71$        | $9$            |

Siendo así la posible respuesta, al interrogante planteado en el enunciado del
ejercicio, cualquiera de las anteriores tres posibilidades.

### Problema 2

Estudia cuáles de estas ecuaciones diofánticas tiene solución entera y, en su
caso, calcúlala:

- (a) $25x+36y=10$.
- (b) $200x+1768y=8$.
- (c\) $40x+50y=3$.
- (d) $213x+1123y=18$.
- (e) $14x+165y=1$.

**Solución**: para el apartado (a), como $25=5^2$ y $36 = 2^2 \cdot3^2$,
entonces $mcd(25,36)=1$, y, dado que $1|10$, estamos en condiciones de asegurar
que la ecuación diofántica propuesta admite solución entera. Empecemos
despejando la variable $x$, por ser aquella cuyo coeficiente asociado es más
reducido. Así,

$$
x = \dfrac{10-36y}{25} = -y + \dfrac{10-11y}{25} = -y+x^{\prime},
$$

con

$$
x^{\prime}=\dfrac{10-11y}{25},
$$

esto es, $25x^{\prime} + 11y = 10$, luego

$$
y = \dfrac{10-25x^{\prime}}{11} = -2x^{\prime} + \dfrac{10-3x^{\prime}}{11} = -2x^{\prime}+y^{\prime},
$$

con

$$
y^{\prime}=\dfrac{10-3x^{\prime}}{11},
$$

es decir, $3x^{\prime} +11y^{\prime} =10$. Finalmente,

$$
x^{\prime} = \dfrac{10-11y^{\prime}}{3},
$$

por lo que basta probar para $y^{\prime}$ valores pertenecientes al _menor
sistema completo de restos módulo_ $3$. Para $y^{\prime} =2$, tenemos que
$x^{\prime} = (-4)$, y deshaciendo ahora los cambios de variable llevados a cabo
anteriormente,

$$
\begin{aligned}
y &= -2x^{\prime} + y^{\prime} = 8+2=10,\\ x &= -y + x^{\prime} = (-10) - 4 = -14,
\end{aligned}
$$

esto es, una solución particular para la ecuación diofántica planteada es
$(x_0,y_0) = ((-14), 10)$, mientras que su solución general queda

$$
\begin{aligned}
x &= (-14) + 36t,\\ y &= 10 - 25t,
\end{aligned}
$$

con $t$ número entero.

De cara al apartado (b), comencemos calculando el máximo común divisor de $200$
y $1768$ por el _Algoritmo de Euclides_. Tenemos que,

$$
\begin{aligned}
1768 &= 200\cdot8 + 168,\\ 200 &= 168\cdot1 +  32,\\ 168 &=  32\cdot5 +   8,\\ 32 &=   8\cdot4,
\end{aligned}
$$

por lo que $mcd(200,1768) = 8$ y, evidentemente, $8|8$, por lo que estamos en
condiciones de asegurar que la ecuación diofántica propuesta en este apartado
admite solución entera. Simplificando dicha ecuación por $8$ queda
$25x + 221y = 1$. Despejemos la variable $x$, por ser aquella cuyo coeficiente
es más reducido,

$$
x = \dfrac{1-221y}{25} = -8y + \dfrac{1-21y}{25} = -8y + x^{\prime},\quad\text{con}\quad x^{\prime} = \dfrac{1-21y}{25},
$$

esto es, $25x^{\prime} +21y = 1$, luego

$$
\begin{aligned}
y = \dfrac{1-25x^{\prime}}{21} = -x^{\prime} + \dfrac{1-4x^{\prime}}{21} = -x^{\prime} +y^{\prime},\quad\text{con}\quad y^{\prime} = \dfrac{1-4x^{\prime}}{21},
\end{aligned}
$$

es decir, $4x^{\prime} + 21y^{\prime} = 1$, por lo que

$$
\begin{aligned}
x^{\prime} = \dfrac{1-21y^{\prime}}{4},
\end{aligned}
$$

y ya únicamente basta probar valores para $y^{\prime}$ que pertenezcan al _menor
sistema completo de restos módulo_ $4$. Así, para $y^{\prime} = 1$, tenemos que
$x^{\prime} = (-5)$, y deshaciendo los cambios de variable llevados a cabo
arriba,

$$
\begin{aligned}
y &= -x^{\prime}+y^{\prime} = 5+1=6,\\ x &= -8y+x^{\prime} = (-48)-5 = (-53).
\end{aligned}
$$

Una solución para la ecuación diofántica planteada es $(x_0,y_0) = ((-53), 6)$,
y su solución general queda

$$
\begin{aligned}
x &= (-53) + 1768t,\\ y &= 6-200t,
\end{aligned}
$$

con $t$ número entero.

A continuación, en el apartado (c\), como $40 = 2^3 \cdot5$ y $50 = 2\cdot5^2$,
resulta que $mcd(40,50) = 10$, y dado que $10\nmid 3$, estamos en condiciones de
asegurar que la ecuación diofántica propuesta no admite solución entera.

Para el apartado (d), empecemos calculando el máximo común divisor de $213$ y
$1123$ utilizando el _Algoritmo de Euclides_,

$$
\begin{aligned}
1123 &= 213\cdot5 + 58,\\ 213 &=  58\cdot3 + 39,\\ 58 &=  39\cdot1 + 19,\\ 39 &=  19\cdot2 +  1,\\ 19 &=   1\cdot19,
\end{aligned}
$$

por lo que $mcd(213, 1123)=1$, esto es, la ecuación diofántica admite solución
entera, ya que, obviamente, $1|18$. Por comodidad en los cálculos, empecemos
llevando a cabo el cambio de variable

$$
\begin{aligned}
x &= 18x^{\prime},\\ y &= 18y^{\prime},
\end{aligned}
$$

y así queda, $213x^{\prime} + 1123y^{\prime}=1$. Despejando la variable
$x^{\prime}$, por ser aquella cuyo coeficiente asociado es más reducido,
llegamos a que

$$
x^{\prime} = \dfrac{1-1123y^{\prime}}{213} = -5y^{\prime} + \dfrac{1-58y^{\prime}}{213} = -5y^{\prime}+x^{\prime\prime},
$$

con

$$
x^{\prime\prime} = \dfrac{1-58y^{\prime}}{213},
$$

esto es, $213x^{\prime\prime} + 58y^{\prime} = 1$. Ahora,

$$
y^{\prime} = \dfrac{1-213x^{\prime\prime}}{58} = -3x^{\prime\prime} + \dfrac{1-39x^{\prime\prime}}{58} = -3x^{\prime\prime} + y^{\prime\prime},
$$

con

$$
y^{\prime\prime} = \dfrac{1-39x^{\prime\prime}}{58},
$$

es decir, $39x^{\prime\prime} + 58y^{\prime\prime} = 1$. A continuación,

$$
x^{\prime\prime} = \dfrac{1-58y^{\prime\prime}}{39} = -y^{\prime\prime} + \dfrac{1-19y^{\prime\prime}}{39} = -y^{\prime\prime} + x^{\prime\prime\prime},
$$

con

$$
x^{\prime\prime\prime} = \dfrac{1-19y^{\prime\prime}}{39},
$$

esto es, $39x^{\prime\prime\prime} + 19y^{\prime\prime}=1$. Acto seguido,

$$
y^{\prime\prime} = \dfrac{1-39x^{\prime\prime\prime}}{19} = -2x^{\prime\prime\prime} + \dfrac{1-x^{\prime\prime\prime}}{19} = -2x^{\prime\prime\prime} + y^{\prime\prime\prime},
$$

con

$$
y^{\prime\prime\prime} = \dfrac{1-x^{\prime\prime\prime}}{19},
$$

es decir, $x^{\prime\prime\prime} +19y^{\prime\prime\prime} = 1$, luego
$x^{\prime\prime\prime} = 1-19y^{\prime\prime\prime}$. Una solución particular
para esta última es
$(x^{\prime\prime\prime}_0, y^{\prime\prime\prime}_0) = (1,0)$, y así,
deshaciendo los cambios de variable realizados, arribamos a

$$
\begin{aligned}
y^{\prime\prime}_0 &= -2x^{\prime\prime\prime}_0 + y^{\prime\prime\prime}_0 = (-2)+0 = (-2),\\ x^{\prime\prime}_0 &= -y^{\prime\prime}_0 + x^{\prime\prime\prime}_0 = 2+1 = 3,\\ y^{\prime}_0  &= -3x^{\prime\prime}_0 + y^{\prime\prime}_0 = (-9) - 2 = (-11),\\ x^{\prime}_0  &= -5y^{\prime}_0 + x^{\prime\prime}_0 = 55 + 3 = 58,\\ y_0   &= 18y^{\prime}_0 = (-198),\\ x_0   &= 18x^{\prime}_0 = 1044,
\end{aligned}
$$

por lo que la solución general a la ecuación diofántica planteada es

$$
\begin{aligned}
x &= 1044 + 1123t,\\ y &= (-198) - 213t,
\end{aligned}
$$

con $t$ número entero.

Finalmente, en el apartado (e), como

$$
\begin{aligned}
14 &= 2\cdot7,\\ 165 &= 3\cdot5\cdot11,
\end{aligned}
$$

entonces $mcd(14,165)=1$, por lo que la ecuación diofántica propuesta admite
solución entera. Despejando la variable $x$, por ser aquella cuyo coeficiente
asociado es más reducido, tenemos que

$$
x=\dfrac{1-165y}{14}=-11y+\dfrac{1-11y}{14}=-11y+x^{\prime},
$$

con

$$
x^{\prime}=\dfrac{1-11y}{14},
$$

esto es, $14x^{\prime}+11y=1$. Ahora,

$$
y=\dfrac{1-14x^{\prime}}{11}=-x^{\prime}+\dfrac{1-3x^{\prime}}{11}=-x^{\prime}+y^{\prime},
$$

con

$$
y^{\prime}=\dfrac{1-3x^{\prime}}{11},
$$

es decir, $3x^{\prime} +11y^{\prime}=1$. A continuación,

$$
\begin{aligned}
x^{\prime} =\dfrac{1-11y^{\prime}}{3},
\end{aligned}
$$

por lo que basta probar, para $y^{\prime}$, valores pertenecientes al _menor
sistema completo de restos módulo_ $3$. Para $y^{\prime}_0=2$, es cierto que
$x^{\prime}_0 = (-7)$, y deshaciendo los cambios de variable llevados a cabo,

$$
\begin{aligned}
y_0 &= -x^{\prime}_0 + y^{\prime}_0 = 7+2=9,\\ x_0 &= -11y_0 + x^{\prime}_0 = (-99)-7 = (-106),
\end{aligned}
$$

llegamos a una solución particular para la ecuación diofántica planteada. Así,
su solución general queda

$$
\begin{aligned}
x &= (-106) + 165t,\\ y &= 9-14t,
\end{aligned}
$$

con $t$ número entero.

### Problema 3

Halla las soluciones enteras de la ecuación $x^2 - y^2 = 36$.

**Solución**: al ser $36$ par y múltiplo de $4$, $36 = 2^2 \cdot 3^2$, estamos
en condiciones de asegurar que la ecuación diofántica planteada admite solución
entera. Escribimos $x^2 - y^2=36$ como $(x+y)(x-y)=36$, y consideramos

$$
\begin{aligned}
36 &= 36\cdot1 \\ &= 18\cdot2 \\ &= 12\cdot3 \\ &= 9\cdot4 \\ &= 6\cdot6 \\ &= 4\cdot9 \\ &= 3\cdot12 \\ &= 2\cdot18 \\ &= 1\cdot36,
\end{aligned}
$$

descartando automáticamente aquellos casos en los que la paridad de ambos
términos no coincide.

Así, para $36 = 18\cdot2$, tenemos el sistema de ecuaciones lineales

$$
\begin{aligned}
x+y &= 18,\\ x-y &=  2,
\end{aligned}
$$

con solución $x = 10$ e $y = 8$. Para la descomposición $36 = (-18)\cdot(-2)$ el
sistema de ecuaciones lineales que conformaríamos posee como solución
$x = (-10)$ e $y = (-8)$.

A continuación, si $36 = 6\cdot6$, tenemos el sistema de ecuaciones lineales

$$
\begin{aligned}
x+y &= 6,\\ x-y &= 6,
\end{aligned}
$$

con solución $x = 6$ e $y = 0$. Para la descomposición $36 = (-6)\cdot(-6)$ el
sistema de ecuaciones lineales que conformaríamos posee como solución $x = (-6)$
e $y = 0$.

Acto seguido, si $36 = 2\cdot18$, tenemos el sistema de ecuaciones lineales

$$
\begin{aligned}
x+y &=  2,\\ x-y &= 18,
\end{aligned}
$$

con solución $x = 10$ e $y = (-8)$. Para la descomposición $36 = (-2)\cdot(-18)$
el sistema de ecuaciones lineales que conformaríamos posee como solución
$x = (-10)$ e $y = 8$.

Queda así resuelta la ecuación diofántica planteada en el enunciado del
ejercicio.

### Problema 4

Halla las soluciones enteras de la ecuación $3x+2y+9z=12$.

**Solución**: dado que $mcd(2,3,9)=1$, estamos en condiciones de asegurar que la
ecuación diofántica planteada admite solución entera. Al encontrar tres
incógnitas, para empezar, hemos de comprobar si algún par de coeficientes está
compuesto por números primos entre sí. En esta ocasión, como $mcd(2,3)=1$
podemos, por ejemplo, fijar como variables $x$ e $y$, de manera que escribimos
la ecuación diofántica como sigue,

$$
3x+2y=12-9z.
$$

A continuación, trabajamos con la ecuación $3x+2y=1$, para la cual, despejando
la variable $y$ por ser aquella cuyo coeficiente es más reducido, hallamos que

$$
y = \dfrac{1-3x}{2},
$$

por lo que basta probar, para $x$, valores pertenecientes al _menor sistema
completo de restos módulo_ $2$. Así, para $x=1$ es cierto que $y = (-1)$, y
entonces la solución particular a la ecuación diofántica propuesta arriba queda

$$
\begin{aligned}
x_0 &= 1\cdot(12-9z) = 12-9z,\\ y_0 &= (-1)\cdot(12-9z) = (-12) + 9z,
\end{aligned}
$$

por lo que su solución general es

$$
\begin{aligned}
x &= 12 - 9z + 2t,\\ y &= (-12) + 9z - 3t,
\end{aligned}
$$

con $t$ y $z$ números enteros.

### Problema 5

Halla las soluciones enteras de la ecuación

$$
30x+42y+70z-105u=(-3).
$$

**Solución**: como

$$
\begin{aligned}
30 &= 2\cdot3\cdot5,\\ 42 &= 2\cdot3\cdot7,\\ 70 &= 2\cdot5\cdot7,\\ 105 &= 3\cdot5\cdot7,
\end{aligned}
$$

entonces $mcd(30,42,70,105)=1$, por lo que estamos en condiciones de asegurar
que la ecuación diofántica propuesta admite solución entera. A diferencia del
problema anterior, en esta ocasión ningún par de coeficientes está conformado
por números primos entre sí. El procedimiento que seguiremos será entonces:

1. Escogeremos dos coeficientes cualesquiera.
2. Despejaremos para conseguir una ecuación diofántica con dos variables.
3. Dividiremos por el máximo común divisor de los mencionados coeficientes y
   resolveremos dicha ecuación.

De esta manera, si empezamos considerando los coeficientes asociados a las
variables $x$ e $y$, como $mcd(30,42)=6$, la ecuación

$$
30x+42y = (-3) - 70z + 105u
$$

la podemos simplificar por $6$, llegando así a

$$
5x+7y = \dfrac{(-3)-70z+105u}{6} = v,\quad\text{con}\quad v = \dfrac{(-3)-70z+105u}{6}.
$$

Llevando a cabo el cambio de variable $x = vx^{\prime}$ e $y = vy^{\prime}$, la
ecuación queda $5x^{\prime} +7y^{\prime}=1$, y despejando la variable
$x^{\prime}$, por ser aquella cuyo coeficiente asociado es más reducido,

$$
x^{\prime} = \dfrac{1-7y^{\prime}}{5},
$$

hallando que para $y^{\prime}_0 = (-2)$, entonces $x^{\prime}_0 = 3$.
Deshaciendo el cambio de variable efectuado, $x_0 = 3v$ e $y_0 = -2v$ es una
solución particular para la ecuación diofántica planteada unas líneas arriba,
por lo que su solución general queda

$$
\begin{aligned}
x &= 3v + 7t,\\ y &= -2v - 5t,
\end{aligned}
$$

con $t$ número entero.

No obstante, recordemos que declaramos antes que

$$
v = \dfrac{(-3) - 70z + 105u}{6},
$$

esto es $105u - 70z - 6v = 3$, que resulta ser una ecuación diofántica de tres
variables del mismo tipo que aquella con la cual iniciamos este ejercicio (el
máximo común divisor de sus coeficientes asciende a $1$, pero no existe algún
par de ellos que sean primos entre sí), pero con una incógnita menos. Como
$mcd(6,70,105) = 1$, estamos en condiciones de asegurar que esta última ecuación
diofántica planteada admite solución entera. Tomando, por ejemplo, los
coeficientes asociados a las variables $u$ y $z$, escribimos entonces la
ecuación $105u-70z = 3+6v$, que podemos simplificar por $35$, quedando así

$$
3u-2z = \dfrac{3+6v}{35} = w,\quad\text{con}\quad w = \dfrac{3+6v}{35}.
$$

Al igual que antes, si consideramos el cambio de variable $u = wu^{\prime}$ y
$z = wz^{\prime}$, la anterior ecuación se convierte en
$3u^{\prime} -2z^{\prime} =1$. Despejando la variable $z^{\prime}$, por ser
aquella cuyo coeficiente asociado es más reducido,

$$
z^{\prime} = \dfrac{1-3u^{\prime}}{2}.
$$

Luego, para $u^{\prime}_0 =(-1)$ hallamos que $z^{\prime}_0 =(-2)$, y
deshaciendo el cambio de variable efectuado, $u_0 = -w$ y $z_0 = -2w$ es una
solución particular de esta ecuación diofántica, por lo que su solución general
queda

$$
\begin{aligned}
u &= -w+2t^{\prime},\\ z &= -2w+3t^{\prime},
\end{aligned}
$$

con $t^{\prime}$ número entero.

Finalmente, como definimos antes $$w = \dfrac{3+6v}{35},$$ generamos al ecuación
diofántica $35w-6v=3$, que sabemos admite solución entera pues $mcd(6,35) = 1$.
Así, despejando ahora la variable $w$, $$w=\dfrac{3+6v}{35},$$ y entonces
$v_0 = (-18)$ y $w_0=3$ es una solución particular para ella. De esta manera, su
solución general es

$$
\begin{aligned}
v &= (-18)+35t^{\prime\prime},\\ w &= 3+6t^{\prime\prime}
\end{aligned}
$$

con $t^{\prime\prime}$ número entero. Únicamente nos resta reemplazar
adecuadamente los resultados alcanzados para que así la solución quede expresada
en función de valores enteros. Así,

$$
\begin{aligned}
x &= 3v+7t = (-54) + 7t + 105t^{\prime\prime},\\ y &= -2v-5t = 36 - 5t - 70t^{\prime\prime},\\ z &= -2w + 3t^{\prime} = (-6) + 3t^{\prime} - 12t^{\prime\prime},\\ u &= -w+2t^{\prime} = (-3) + 2t^{\prime} - 6t^{\prime\prime},
\end{aligned}
$$

con $t$, $t^{\prime}$ y $t^{\prime\prime}$ números enteros.

### Problema 6

En su último viaje a Estados Unidos, el señor Martínez cambió un cheque de
viaje. El cajero, al pagarle, confundió el número de dólares con los centavos y
viceversa. El señor Martínez gastó 68 centavos en sellos y comprobó que el
dinero que le quedaba era el doble del importe del cheque de viaje que había
cambiado. ¿Qué valor mínimo tenía el cheque de viaje?

**Solución**: al leer el enunciado, enseguida apreciamos dos partes que nos
sirven de pista hacia el tipo de problema que tenemos entre manos. Para empezar,
cuando aparece ''el dinero que le quedaba era el doble del importe del cheque de
viaje que había cambiado'', debemos sospechar que, en algún momento de la
resolución del ejercicio, plantearemos una ecuación algebraica, posiblemente
lineal. Esta poseerá múltiples soluciones, quizá incluso infinitas, ya que en la
cuestión se interesan por el ''valor mínimo''. Al estar trabajando con dólares y
centavos, cantidades monetarias que usualmente se representan utilizando números
enteros, todo ello nos va a hacer pensar rápidamente en ecuaciones diofánticas.

Así pues, una de las claves de este ejercicio reside en trabajar en centavos,
para evitar así operar con decimales. De esta manera, si el señor Martínez viajó
a Estados con un cheque de viaje cuyo valor ascendía a $a$ dólares y $b$
centavos, con $a$ y $b$ números enteros mayores o iguales de cero, en total el
valor de dicho cheque era de $100a + b$ centavos.

Ahora, en el banco se equivocaron al cambiarle el cheque de viaje,
intercambiando los papeles de dólares y centavos, de forma que, al final, el
señor Martínez recibió $100b + a$ centavos. De estos, gastó 68 centavos en
sellos, quedándole entonces disponible $100b + a - 68$ centavos.

La anterior cantidad nos dicen que equivalía al doble del importe del cheque de
viaje que había cambiado ($2(100a + b)$), es decir, tenemos la ecuación
diofántica

$$
100b + a - 68 = 200a + 2b,
$$

que queda, operando,

$$
199a-98b=-68.
$$

Obtengamos el $mcd(199,98)$ utilizando el _Algoritmo de Euclides_:

$$
\begin{aligned}
199 &= 98\cdot 2 + 3,\\ 98 &= 3\cdot 32 + 2,\\ 3 &= 2\cdot 1 + 1,\\ 2 &= 1\cdot 2,
\end{aligned}
$$

luego $mcd(199, 98) = 1$ y como $1|68$ sabemos que la ecuación diofántica admite
solución entera.

Despejamos entonces $b$, por ser la variable cuyo coeficiente asociado es más
pequeño, quedando así

$$
b = \dfrac{199a + 68}{98}.
$$

Ahora, como el valor que figura en el denominador de la igualdad anterior es
$98$, a continuación, tendríamos que darle a $a$, de manera ordenada, valores
del _menor sistema completo de restos módulo_ $98$ hasta hallar una solución
particular.

No obstante, en lugar de llevar a cabo tan titánica labor, aprovecharemos las
operaciones realizadas durante el _Algoritmo de Euclides_ para descomponer la
anterior fracción como sigue:

$$
b = 2a + \dfrac{3a+68}{98} = 2a + b^{\prime},
$$

con

$$
b^{\prime} = \dfrac{3a+68}{98},
$$

que equivale a $98b^{\prime} = 3a + 68$, ecuación en la que ahora despejaremos
$a$, teniendo que

$$
a = \dfrac{98b^{\prime} - 68}{3}.
$$

Podemos así dar valores a $b^{\prime}$, ya que únicamente tendríamos que probar
$b^{\prime}=0$, $b^{\prime}=1$ y $b^{\prime}=2$ (que conforma el _menor sistema
completo de restos módulo_ $3$). Para $b^{\prime}=0$, $a\notin\mathbb{Z}$, pero
si $b^{\prime}=1$, entonces $a=10$ y, por tanto, $b = 2a+b^{\prime} = 21$,
quedando así la solución particular como sigue:

$$
\begin{aligned}
a_0 &= 10,\\ b_0 &= 21,
\end{aligned}
$$

mientras que la solución general es

$$
\begin{aligned}
a &= 10 - 98t,\\ b &= 21 - 199t,
\end{aligned}
$$

con $t\in\mathbb{Z}$.

Una vez resuelta la ecuación diofántica, centrémonos de nuevo en aquello que nos
pedían en el enunciado: ''¿Qué valor mínimo tenía el cheque de viaje?''. Como
hablamos de cantidades monetarias, tanto $a$, como $b$, han de ser mayores o
iguales que cero, es decir,

$$
\begin{aligned}
a &= 10 -98t \geq0 \Rightarrow t\leq\dfrac{10}{98},\\ b &= 21 - 199t \geq0 \Rightarrow t\leq\dfrac{21}{199},
\end{aligned}
$$

y $t\in\mathbb{Z}$. Por consiguiente, el valor mínimo se alcanza cuando $t=0$,
donde $a=10$ y $b=21$. Así, el señor Martínez viajó a Estados Unidos con un
cheque de viaje cuyo valor ascendía a 10 dólares y 21 centavos.

### Problema 7

Una persona ha comprado entradas para el cine para personas adultas por un
precio de $640$ unidades monetarias (_um_) cada una y para menores de edad a
$330$ _um_. Sabiendo que invirtió $7140$ _um_ y que compró menos entradas de
adultos que de menores, hallar el número de entradas que adquirió.

**Solución**: sean $x$ el número de entradas para personas adultas compradas e
$y$ el número de entradas para menores de edad compradas, con
$x,y\in\mathbb{N}$. Dados los precios del enunciado y la cantidad total
invertida, planteamos la siguiente ecuación diofántica:

$$
640x + 330y = 7140,
$$

que es equivalente, simplificando por $10$, a

$$
64x + 33y = 714.
$$

Utilicemos el _Algoritmo de Euclides_ para hallar el $mcd(64,33)$ y decidir así
si la ecuación admite o no solución entera. Tenemos que:

$$
\begin{aligned}
64 &= 33\cdot 1 + 31,\\ 33 &= 31\cdot 1 + 2,\\ 31 &= 2\cdot 15 + 1,\\ 2 &= 1\cdot 2,
\end{aligned}
$$

luego $mcd(64,33) = 1$, y como $1|714$, estamos en condiciones de asegurar que
la ecuación diofántica admite solución entera. Como $714$ es un número
ciertamente elevado, comencemos llevando a cabo el cambio de variable

$$
\begin{aligned}
x &= 714x^{\prime},\\ y &= 714y^{\prime},
\end{aligned}
$$

de manera que la ecuación diofántica queda $64x^{\prime} + 33y^{\prime} = 1$ y
nos invita a despejar $y^{\prime}$, por ser la variable cuyo coeficiente
asociado es más reducido, de forma que

$$
y^{\prime} = \dfrac{1-64x^{\prime}}{33}.
$$

Ahora, como el valor que figura en el denominador de la igualdad anterior es
$33$, a continuación, tendríamos que darle a $x^{\prime}$, de manera ordenada,
valores del _menor sistema completo de restos módulo_ $33$ hasta hallar una
solución particular.

No obstante, en lugar de llevar a cabo tan titánica labor, aprovecharemos las
operaciones realizadas durante el _Algoritmo de Euclides_ para descomponer la
anterior fracción como sigue:

$$
y^{\prime} = -x^{\prime} + \dfrac{1 - 31x^{\prime}}{33} = -x^{\prime} + y^{\prime\prime},
$$

con

$$
y^{\prime\prime} = \dfrac{1 - 31x^{\prime}}{33},
$$

que equivale a $33y^{\prime\prime} = 1 - 31x^{\prime}$, de manera que ahora
tendríamos que despejar $x^{\prime}$, quedando:

$$
x^{\prime} = \dfrac{1-33y^{\prime\prime}}{31} = -y^{\prime\prime} + \dfrac{1-2y^{\prime\prime}}{31}=-y^{\prime\prime} + x^{\prime\prime},
$$

con

$$
x^{\prime\prime} = \dfrac{1-2y^{\prime\prime}}{31},
$$

que equivale a $31x^{\prime\prime} = 1-2y^{\prime\prime}$, y despejando
$y^{\prime\prime}$ tenemos que

$$
y^{\prime\prime} = \dfrac{1-31x^{\prime\prime}}{2}.
$$

Tras aplicar en retiradas ocasiones la misma estrategia de descomposición, hemos
alcanzado un valor razonable para el denominador de la anterior ecuación.
Podemos así dar valores a $x^{\prime\prime}$, ya que únicamente tendríamos que
probar $x^{\prime\prime} =0$, y $x^{\prime\prime} =1$ (que conforma el _menor
sistema completo de restos módulo_ $2$). Para $x^{\prime\prime} =0$,
$y^{\prime\prime} \notin\mathbb{Z}$, pero para $x^{\prime\prime} =1$,
$y^{\prime\prime} = -15$. Ahora,

$$
\begin{aligned}
x^{\prime} &= -y^{\prime\prime} + x^{\prime\prime} = 15+1 = 16,\\ y^{\prime} &= -x^{\prime} + y^{\prime\prime} = -16 -15 = -31,\\ x  &= 714x^{\prime} = 714\cdot 16 = 11424,\\ y  &= 714y^{\prime} = 714\cdot(-31) = -22134,
\end{aligned}
$$

por lo que la solución particular queda

$$
\begin{aligned}
x_0 &= 11424,\\ y_0 &= -22134,
\end{aligned}
$$

mientras que la solución general es

$$
\begin{aligned}
x  &= 11424 + 33t,\\ y  &= -22134 - 64t,
\end{aligned}
$$

con $t\in\mathbb{Z}$.

Ahora que hemos resuelto la ecuación diofántica, centrémonos en sacar el número
de entradas. Por un lado, en ambos casos debe tratarse de un número mayor o
igual que cero, es decir, tanto $x\geq0$, como $y\geq0$. Además, nos dicen que
compró menos entradas de adultos que de menores, es decir, que $x<y$. Todo esto
da lugar a las siguientes condiciones:

$$
\begin{aligned}
x  = 11424 + 33t&\geq0,\\ y  = -22134 - 64t&\geq0,\\ 11424 + 33t &< -22134 - 64t,
\end{aligned}
$$

con $t\in\mathbb{Z}$. De la primera inecuación, se llega a que

$$
t\geq -\dfrac{11424}{33},
$$

luego $t\geq -346$. De la segunda inecuación, se llega a que

$$
t\leq -\dfrac{22134}{64},
$$

luego $t\leq -346$, con lo cual $t=346$, cantidad que, efectivamente, también
verifica la tercera inecuación. Así,

$$
\begin{aligned}
x &= 11424 + 33\cdot(-346) = 6,\\ y &= -22134 - 64\cdot(-346) = 10,
\end{aligned}
$$

es decir, compró $6$ entradas para adultos y $10$ entradas para menores de edad.

### Problema 8

Halla los números naturales $n$ de manera que se cumpla que

$$
1+2+ \cdots +n = k^2,
$$

con $k$ número natural.

**Solución**: observamos rápidamente que para $n = 1$ se verifica la propiedad,
sin más que tomar asimismo $k = 1$. El enunciado propuesto en el ejercicio es
equivalente a hallar los números triangulares que son cuadrados perfectos. La
ecuación diofántica $1+2+ \cdots +n = k^2$ podemos escribirla de manera más
compacta utilizando la conocida expresión para la suma de los primeros $n$
números naturales. Así,

$$
\dfrac{n(n+1)}{2} = k^2,
$$

o, equivalentemente, $n^2 +n=2k^2$, dando lugar pues a la siguiente ecuación de
segundo grado en $n$, $n^2 +n-2k^2 =0$. Por tanto,

$$
n = \dfrac{(-1)\pm\sqrt{1+8k^2}}{2}.
$$

Como buscamos valores naturales para $n$, podemos prescindir del signo $-$ que
aparece en el numerador. Además, $1+8k^2$ ha de ser un cuadrado perfecto, que
también necesitaremos sea impar, para que el numerador sea par y así $n$,
efectivamente, pertenezca al conjunto de los números naturales. De esta manera,
como ha de ser $1+8k^2$ un cuadrado perfecto, planteamos la ecuación
$1+8k^2 = p^2$, que nos lleva a la _ecuación de Pell_

$$
p^2 -8k^2 =1,
$$

de la cual sabemos posee infinitas soluciones en los enteros, pues $8$ no es un
cuadrado perfecto. Por tanteo, una solución particular es $p=3$ y $k=1$, ya que
$3^2 - 8\cdot1^2=1$. Expresamos ahora la diferencia de cuadrados como producto
de una suma y una diferencia, de forma que

$$
3^2 - 8\cdot 1^2 =1\Leftrightarrow (3+\sqrt{8})(3-\sqrt{8})=1.
$$

De igual manera, la sucesión de soluciones enteras, que denotaremos por
$(p_n,k_n)$, debe cumplir que $(p_n + k_n\sqrt{8})(p_n - k_n\sqrt{8})=1$.
Obtengamos la solución general utilizando recurrencias, de manera que,

$$
p_{n+1} + k_{n+1}\sqrt{8} = (p_n+k_n\sqrt{8})(3+\sqrt{8}) = 3p_n + \sqrt{8}p_n + 3\sqrt{8}k_n + 8k_n,
$$

luego

$$
\begin{aligned}
p_{n+1} &= 3p_n + 8k_n,\\ k_{n+1} &=  p_n + 3k_n.
\end{aligned}
$$

Utilizando notación matricial,

$$
\begin{bmatrix}
p_{n+1}\\ k_{n+1}
\end{bmatrix}
= \begin{bmatrix}
3 & 8\\ 1 & 3
\end{bmatrix}
\begin{bmatrix}
p_n\\ k_n
\end{bmatrix}.
$$

Ahora, $$n = \dfrac{(-1) + p}{2},$$ por lo que la solución general del ejercicio
queda como

$$
\begin{bmatrix}
p_{n+1}\\ k_{n+1}
\end{bmatrix}
= \begin{bmatrix}
3 & 8\\ 1 & 3
\end{bmatrix}
\begin{bmatrix}
p_n\\ k_n
\end{bmatrix},
$$

con $(p_1,k_1) = (3,1)$ y

$$
n = \dfrac{(-1) + p_n}{2}.
$$

Así, para $p_1 = 3$, tenemos que $n = ((-1)+3) / 2 = 1$. Obtengamos algunas
soluciones adicionales,

$$
\begin{bmatrix}
p_{2}\\ k_{2}
\end{bmatrix}
= \begin{bmatrix}
3 & 8\\ 1 & 3
\end{bmatrix}
\begin{bmatrix}
3\\ 1
\end{bmatrix}
= \begin{bmatrix}
17 \\ 6
\end{bmatrix},
$$

y entonces, para $p_2=17$ queda $n = ((-1) + 17) / 2 = 8$, esto es,

$$
1+2+ \cdots +7+8 = 6^2.
$$

Ahora,

$$
\begin{bmatrix}
p_3\\ k_3
\end{bmatrix}
= \begin{bmatrix}
3 & 8\\ 1 & 3
\end{bmatrix}
\begin{bmatrix}
17\\ 6
\end{bmatrix}
= \begin{bmatrix}
99\\ 35
\end{bmatrix},
$$

y, por tanto, para $p=99$ queda $n = ((-1) + 99)/2 = 49$, es decir,

$$
1+2+ \cdots +48+49 = 35^2,
$$

bastando aplicar el procedimiento tantas veces como soluciones deseemos
encontrar.

### Problema 9

Se compran manzanas y naranjas, en total $12$ piezas de fruta y cuestan $1.32$
euros. Si una manzana vale $3$ céntimos más que una naranja y hay más manzanas
que naranjas, ¿cuántas piezas de cada fruta compramos?

**Solución**: sea $x$ el número de manzanas ($M$) compradas, de manera que el
total de naranjas ($N$) adquiridas será $12-x$. Por otro lado, si denotamos por
$y$ el precio de las naranjas ($P_N$), será $y+3$ el precio de las manzanas
($P_M$). Expresemos el desembolso realizado, $1.32$ euros, en céntimos, esto es,
$132$ céntimos, para así trabajar con números enteros. De esta manera,
multiplicando las cantidades por los precios e igualando al mencionado
desembolso, podemos plantear la siguiente ecuación diofántica,

$$
x(y+3) + (12-x)y=132,
$$

es decir, $xy+3x+12y-xy=132$, que, simplificando, queda la ecuación
$3x+12y=132$. Como $mcd(3,12) = 3$ y $3|132$, estamos en condiciones de asegurar
que la ecuación diofántica propuesta admite solución entera. Así pues,
simplificando por el máximo común divisor queda

$$
x+4y=44.
$$

Como, en total, se adquieren $12$ piezas de frutas y se compran más manzanas que
naranjas, resulta que $7\leq x\leq 11$. Luego,

| $x$ ($M$) | $12-x$ ($N$) | $y+3$ ($P_M$)      | $y$ ($P_N$)        |
| --------- | ------------ | ------------------ | ------------------ |
| $7$       | $5$          | $\notin\mathbb{N}$ | $\notin\mathbb{N}$ |
| $8$       | $4$          | $12$               | $9$                |
| $9$       | $3$          | $\notin\mathbb{N}$ | $\notin\mathbb{N}$ |
| $10$      | $2$          | $\notin\mathbb{N}$ | $\notin\mathbb{N}$ |
| $11$      | $1$          | $\notin\mathbb{N}$ | $\notin\mathbb{N}$ |

Por tanto, compramos $8$ manzanas, a $12$ céntimos cada una, y $4$ naranjas, a
$9$ céntimos la unidad. A modo anecdótico, es cierto que para $x=12$ también
encontraríamos solución entera al problema. No obstante, si interpretamos el
enunciado de manera que al menos ha comprado una unidad de cada tipo de fruta,
esta solución quedaría descartada automáticamente, pues impide la adquisición de
naranjas.

### Problema 10

Para abonar una factura de $1840$ pesetas se entregan libras esterlinas y dan la
vuelta en marcos. Calcula las libras esterlinas entregadas y los marcos
devueltos suponiendo que se ha entregado la cantidad mínima de libras necesarias
para pagar y que la devolución es en marcos ($1$ marco $=$ $70$ pesetas, $1$
libra $=$ $180$ pesetas).

**Solución**: sea $x$ la cantidad de libras esterlinas entregadas e $y$ el total
de marcos recibidos en la devolución. Como la factura viene dada en pesetas y
tenemos indicadas las tasas de conversión de las otras dos monedas en relación a
las pesetas, trabajaremos durante el resto del ejercicio con esta unidad
monetaria.

Con ello en mente, la cantidad que desembolso en libras para cumplir con la
factura más el total de marcos que recibo en concepto de devolución ha de
ascender a $1840$ pesetas, esto es,

$$
180x + 70y = 1840.
$$

Ahora bien, como $70 = 2\cdot5\cdot7$ y $180 = 2^2 \cdot 3^2 \cdot5$,
$mcd(70, 180) = 10$. Dado que, trivialmente, $10|1840$, la ecuación diofántica
propuesta admite solución entera. Simplificando dicha ecuación por $10$, tenemos
que $18x + 7y = 184$, expresión que nos invita, para empezar, a llevar a cabo el
cambio de variable

$$
\begin{aligned}
x &= 184x^{\prime},\\ y &= 184y^{\prime}
\end{aligned}
$$

que la transforma en $18x^{\prime} +7y^{\prime} =1$. Ahora, despejando la
variable $y^{\prime}$, por ser aquella cuyo coeficiente asociado es más
reducido, hallamos que

$$
y^{\prime} = \dfrac{1-18x^{\prime}}{7},
$$

por lo que basta probar, para $x^{\prime}$, valores pertenecientes al _menor
sistema completo de restos módulo_ $7$. Para $x^{\prime}_0 = 2$, resulta que
$y^{\prime}_0 = (-5)$, y deshaciendo el anterior cambio de variable,

$$
\begin{aligned}
x_0 &= 184x^{\prime} = 184\cdot2 = 368,\\ y_0 &= 184y^{\prime} = 184\cdot(-5) = (-920),
\end{aligned}
$$

es una solución particular para la ecuación diofántica planteada. Su solución
genera queda, entonces,

$$
\begin{aligned}
x &= 368 + 7t,\\ y &= (-920) - 18t,
\end{aligned}
$$

con $t$ número entero.

De entre las infinitas soluciones que tenemos a nuestra disposición, busquemos
aquella que se ajusta a los dictados del enunciado del ejercicio, es decir,
aquella para la cual se desembolsa la mínima cantidad de libras esterlinas
necesarias para abonar la factura. Esta situación se traduce en averiguar el
valor de $x$ tal que, $18x \geq 184$. Sustituyendo,

$$
18(368 + 7t)\geq 184,
$$

es decir, $6624 + 126t \geq 184$. Por tanto, $126t \geq (-6498)$, luego
$t\geq (-51.6)$ y como $t$ ha de ser entero, la inecuación entonces queda
$t\geq (-51)$. Como buscamos el menor valor para el que satisface la inecuación,
este será, evidentemente, $t=(-51)$, resultando entonces

$$
\begin{aligned}
x &= 368 + 7\cdot(-51) = 11,\\ y &= (-920) - 18\cdot(-51) = -2,
\end{aligned}
$$

esto es, abonaremos la factura con $11$ libras esterlinas y nos devolverán $2$
marcos.

### Problema 11

Un granjero compró vacas, cerdos y pollos. En total $100$ animales por $100$
euros. Hay al menos uno de cada. Si una vaca cuesta $10$ euros, un cerdo $3$
euros y un pollo $0.50$ euros, ¿cuántos animales de cada clase compró?

**Solución**: sea $x$ el número de vacas, $y$ el total de cerdos y $z$ la
cantidad de pollos adquiridos. Como se compran $100$ animales, tenemos la
ecuación lineal $x+y+z=100$, con la restricción de que $x\geq1$, $y\geq1$ y
$z\geq1$ ya que nos indican que, al menos, se compra un animal de cada tipo.
Finalmente, dados los precios suministrados y el desembolso llevado a cabo,
encontramos la ecuación $10x+3y + 0.5z = 100$. Así pues, hemos de resolver el
sistema de ecuaciones

$$
\begin{aligned}
10x+3y+0.5z &= 100,\\ x+y+z &= 100,
\end{aligned}
$$

con la restricción adicional indicada arriba. Despejando la variable $z$ de la
segunda ecuación, $z = 100-x-y$, y sustituyéndola en la primera ecuación del
sistema,

$$
10x + 3y + 50 - 0.5x - 0.5y = 100,
$$

esto es, $10x+3y-0.5x-0.5y=50$, o bien $19x+5y=100$, ecuación diofántica que
sabemos admite solución entera, puesto que $mcd(5,19)=1$ y, obviamente, $1|100$.
Así, despejando la variable $y$, por ser aquella cuyo coeficiente asociado es
más reducido,

$$
y = \dfrac{100 - 19x}{5},
$$

por lo que basta probar, para $x$, valores pertenecientes al _menor sistema
completo de restos módulo_ $5$. Para $x_0=0$, hallamos que $y_0 = 20$, siendo
esta una solución particular de la ecuación diofántica propuesta. Su solución
general, por tanto, queda

$$
\begin{aligned}
x &= 5t,\\ y &= 20-19t,
\end{aligned}
$$

con $t$ número entero. Como hemos de comprar, al menos, un animal de cada tipo,
tanto $x$ como $y$ han de ser positivas. De $5t>0$ concluimos que $t>0$;
mientras que de $20-19t>0$ deducimos que $t\leq 1$. Así, como $t$ es un número
entero, únicamente puede tomar el valor $t=1$, dejando así $x=5$, $y=1$ y
$z = 100-x-y = 100-5-1=94$. Es decir, el granjero compró $5$ vacas, un cerdo y
$94$ pollos.

### Problema 12

Halla un cuadrado de cinco cifras que sea igual a cinco veces otro cuadrado, más
uno.

**Solución**: el enunciado del ejercicio nos lleva a plantear la ecuación
$x^2 = 5y^2 +1$, equivalente a $x^2 -5y^2 =1$, _ecuación de Pell_ que sabemos
posee infinitas soluciones en los enteros al no ser $5$ un cuadrado perfecto.
Por tanteo, hallamos la solución particular $x=9$ e $y=4$, ya que
$9^2 - 5\cdot4^2 =1$. Expresamos ahora la diferencia de cuadrados como producto
de una suma y una diferencia, de forma que

$$
9^2 - 5\cdot4^2 =1 \Leftrightarrow (9+4\sqrt{5})(9-4\sqrt{5}) = 1.
$$

Análogamente, la sucesión de soluciones enteras, que denotaremos por
$(x_n,y_n)$, debe cumplir que $(x_n+y_n\sqrt{5})(x_n-y_n\sqrt{5})=1$. Expresamos
la solución general utilizando recurrencias, de manera que,

$$
\begin{aligned}
x_{n+1} + y_{n+1}\sqrt{5} &= (x_n + y_n\sqrt{5})(9+4\sqrt{5})\\ &= 9x_n + 4\sqrt{5}x_n + 9\sqrt{5}y_n + 20y_n,
\end{aligned}
$$

luego

$$
\begin{aligned}
x_{n+1} &= 9x_n + 20y_n,\\ y_{n+1} &= 4x_n + 9y_n.
\end{aligned}
$$

Utilizando notación matricial,

$$
\begin{bmatrix}
x_{n+1}\\ y_{n+1}
\end{bmatrix}
= \begin{bmatrix}
9 & 20\\ 4 & 9
\end{bmatrix}
\begin{bmatrix}
x_n\\ y_n
\end{bmatrix},
$$

con $(x_1,y_1) = (9,4)$. La solución particular hallada no cumple los requisitos
impuestos en el enunciado del ejercicio, por lo que procederemos a obtener la
siguiente.

$$
\begin{bmatrix}
x_2\\ y_2
\end{bmatrix}
= \begin{bmatrix}
9 & 20\\ 4 & 9
\end{bmatrix}
\begin{bmatrix}
9\\ 4
\end{bmatrix}
= \begin{bmatrix}
161\\ 72
\end{bmatrix},
$$

que es la solución que estamos persiguiendo, pues
$161^2 = 25921 = 5\cdot72^2+1$.

### Problema 13

El diámetro de una moneda de $5$ pesetas es de $37$ mm y el de una peseta es de
$23$ mm, ¿de cuántas maneras puede obtenerse la longitud de un metro alineando
monedas de $5$ pesetas y de pesetas?

**Solución**: sea $x$ el número de monedas de $5$ pesetas e $y$ la cifra total
de monedas de $1$ peseta. Expresando todas las cantidades involucradas en el
enunciado del ejercicio en milímetros, para así trabajar con números enteros,
hemos de resolver la ecuación diofántica

$$
37x+23y=1000,
$$

para encontrar el número de maneras en las que puede obtenerse un metro
alineando monedas de los dos tipos indicados.

Como $23$ y $37$ son números primos, tenemos que $mcd(23,37)=1$, y dado que,
trivialmente, $1|1000$, estamos en condiciones de asegurar que la anterior
ecuación diofántica planteada admite solución entera. De cara a su resolución,
para empezar, llevemos a cabo el cambio de variable

$$
\begin{aligned}
x &= 1000x^{\prime},\\ y &= 1000y^{\prime}
\end{aligned}
$$

de manera que la ecuación diofántica se transforma en
$37x^{\prime} + 23y^{\prime} = 1$. Utilizando el _Algoritmo de Euclides_, como

$$
\begin{aligned}
37 &= 23\cdot1 + 14,\\ 23 &= 14\cdot1 +  9,\\ 14 &=  9\cdot1 +  5,\\  9 &=  5\cdot1 +  4,\\  5 &=  4\cdot1 +  1,\\  4 &=  1\cdot4,
\end{aligned}
$$

además de haber comprobado que $mcd(23,37)=1$, podemos encontrar una solución
particular a la ecuación diofántica sin más que expresar dicho máximo común
divisor como combinación lineal de $23$ y $37$. Para ello,

$$
\begin{aligned}
1 &= 5 - 4\cdot1\\ &= 5 - 1\cdot(9\cdot1 - 5) \\ &= (-9) + 2\cdot5 = (-9) + 2(14\cdot1 - 9) \\ &= 2\cdot14 - 3\cdot9 \\ &= 2\cdot14 - 3(23\cdot1 - 14) \\ &= (-3)\cdot23 + 5\cdot14 \\ &= (-3)\cdot23 + 5(37 - 23\cdot1) \\ &= 5\cdot37 - 8\cdot23,
\end{aligned}
$$

y dado que, recordemos, la ecuación diofántica es
$37x^{\prime} +23y^{\prime} =1$, igualando, arribamos a que $x^{\prime}_0=5$ e
$y^{\prime}_0=(-8)$. Deshaciendo ahora el cambio de variable realizado,

$$
\begin{aligned}
x_0 &= 1000x^{\prime}_0 = 5000,\\ y_0 &= 1000y^{\prime}_0 = (-8000),
\end{aligned}
$$

es una solución particular para la ecuación diofántica $37x+23y=1000$. Por
tanto, su solución general queda

$$
\begin{aligned}
x &= 5000 + 23t,\\ y &= (-8000) - 37t,
\end{aligned}
$$

con $t$ número entero. Dado que el número de monedas que alineamos ha de ser
mayor o igual que cero, planteamos las inecuaciones,

$$
5000 + 23t\geq 0\qquad\text{y}\qquad (-8000) - 37t\geq 0,
$$

esto es,

$$
-\dfrac{5000}{23}\leq t\leq -\dfrac{8000}{37},
$$

es decir, $(-217.4)\leq t\leq (-216.2)$ y como $t$ ha de ser un número entero,
únicamente deja como solución $t=(-217)$. Por tanto,

$$
\begin{aligned}
x &= 5000 + 23\cdot(-217) = 9,\\ y &= (-8000) - 37\cdot(-217) = 29,
\end{aligned}
$$

esto es, solamente podemos obtener un metro alineando las monedas indicadas de
una manera y es utilizando $9$ monedas de $5$ pesetas y $29$ monedas de $1$
peseta.

### Problema 14

Determina las dimensiones de un rectángulo sabiendo que sus lados miden un
número entero de centímetros, pero no un número entero de palmos, y que su área
expresada en palmos cuadrados es igual a su perímetro expresado en palmos
lineales. Considera que un palmo equivale a $20$ centímetros.

**Solución**: sean $x$ e $y$ las medidas de los lados del rectángulo expresadas
en centímetros, mientras que denotemos por $a$ y $b$ las correspondientes
medidas obtenidas en palmos. El área del rectángulo, en palmos cuadrados, es
$a\cdot b$, cantidad que nos dicen ha de ser igual a su perímetro en palmos
lineales, que viene dado por $2a+2b = 2(a+b)$. Por tanto, resulta que

$$
a\cdot b = 2(a + b).
$$

Dado que un palmo equivale a $20$ centímetros, es cierto que $x = 20a$ e
$y = 20b$, y despejando $a$ y $b$, hallamos que

$$
\begin{aligned}
a &= \dfrac{x}{20},\\ b &= \dfrac{y}{20}.
\end{aligned}
$$

Sustituyendo los resultados alcanzados, tenemos que

$$
\dfrac{x}{20}\cdot\dfrac{y}{20} = 2\left(\dfrac{x}{20} + \dfrac{y}{20}\right),
$$

esto es, $xy = 40x+40y$, ecuación diofántica no lineal que abordaremos
despejando una de las variables y forzando a que la restante tome valores
enteros. Así, $xy-40x = 40y$, es decir, $x(y-40) = 40y$, de donde

$$
x = \dfrac{40y}{y-40}.
$$

Como $x$ ha de tomar valores enteros, estudiaremos, a continuación, las
posibilidades para la fracción que acabamos de obtener. Si llevamos a cabo la
división de polinomios, es cierto que

$$
\dfrac{40y}{y-40} = 40 + \dfrac{1600}{y-40},
$$

con $y\neq 40$ ($y=40$ no es una solución aceptable en este contexto, pues al
ser múltiplo de $20$, uno de los lados del rectángulo poseería una longitud
igual a un número entero de palmos). Hemos llegado entonces a que $y-40$ debe
ser un divisor de $1600$.

Ahora bien, $1600 = 2^6 \cdot 5^2$, situación que produce un total de

$$
(6+1)\cdot(2+1) = 21
$$

divisores, por lo que, acto seguido, analizaremos todos y cada uno de los casos.
Para empezar, listemos el conjunto de divisores. Para llevar a cabo tal tarea de
forma relativamente sencilla, recordemos que la expresión de la suma de los
divisores era

$$
(1+2+2^2 +\cdots+2^6 )\cdot(1+5+5^2 ),
$$

de manera que si prescindimos de la operación suma, cada uno de los productos
resulta ser un divisor de $1600$. Por ejemplo, multiplicando $1$ por
$1,2,2^2,\ldots, 2^6$ aparecen los divisores

$$
\{1,2,4,8,16,32,64\}.
$$

Multiplicando ahora $5$ por $1,2,2^2,\ldots, 2^6$, obtenemos los divisores

$$
\{5,10,20,40,80,160,320\}.
$$

Finalmente, multiplicando $5^2$ por $1,2,2^2 ,\ldots,2^6$, encontramos los
divisores

$$
\{25,50,100,200,400,800,1600\}.
$$

En definitiva, el conjunto de divisores de $1600$ es

$$
\begin{aligned}
\{&1, 2, 4, 5, 8, 10, 16, 20, 25, 32, 40, 50,\\ &64, 80, 100, 160, 200, 320, 400, 800, 1600\}.
\end{aligned}
$$

A continuación, vemos que algunos casos los podemos descartar rápidamente. ¿Es
válida la solución $y-40=20$? No, ya que implicaría $y=60 = 3\cdot20$, es decir,
$y$ sería entonces un múltiplo entero de palmos, longitud no permitida por las
restricciones que impone el enunciado del ejercicio. El mismo razonamiento es
válido para los valores $40$, $80$, $160$, $320$, $100$, $200$, $400$, $800$ y
$1600$.

Para el resto de casos, conformamos la siguiente tabla

| $y-40$ | $x$                           | Nota                                         |
| ------ | ----------------------------- | -------------------------------------------- |
| $1$    | $40 + \dfrac{1600}{1} = 1640$ | Solución no válida: $x$ es múltiplo de $20$. |
| $2$    | $40 + \dfrac{1600}{2} = 840$  | Solución no válida: $x$ es múltiplo de $20$. |
| $4$    | $40 + \dfrac{1600}{4} = 440$  | Solución no válida: $x$ es múltiplo de $20$. |
| $5$    | $40 + \dfrac{1600}{5} = 360$  | Solución no válida: $x$ es múltiplo de $20$. |
| $8$    | $40 + \dfrac{1600}{8} = 240$  | Solución no válida: $x$ es múltiplo de $20$. |
| $10$   | $40 + \dfrac{1600}{10} = 200$ | Solución no válida: $x$ es múltiplo de $20$. |
| $16$   | $40 + \dfrac{1600}{16} = 140$ | Solución no válida: $x$ es múltiplo de $20$. |
| $25$   | $40 + \dfrac{1600}{25} = 104$ | Solución válida.                             |
| $32$   | $40 + \dfrac{1600}{32} = 90$  | Solución válida.                             |
| $50$   | $40 + \dfrac{1600}{50} = 72$  | Solución válida.                             |
| $64$   | $40 + \dfrac{1600}{64} = 65$  | Solución válida.                             |

Por tanto, las dimensiones del rectángulo vienen dadas por los pares
$(104, 65)$, $(90, 72)$, $(72, 90)$ y $(65, 104)$.

## Problemas propuestos

**Problema 15:**

- (a) ¿Se puede llenar un depósito de $25$ litros, de manera exacta, con
  garrafas de $6$ y $8$ litros?
- (b) Halla las soluciones enteras de la ecuación $14x + 21y = 777$.

**Problema 16:** halla las soluciones enteras de la ecuación $79x + 23y = 5$.

**Problema 17:** halla las soluciones enteras de la ecuación $14x + 10y = 4$.

**Problema 18:** halla las soluciones enteras de la ecuación $16x + 26y = 14$.

**Problema 19:** halla las soluciones enteras de la ecuación $525x + 100y = 50$.

**Problema 20:** halla las soluciones enteras de la ecuación $1027x + 712y = 1$.

**Problema 21:** estudia cuál de estas ecuaciones diofánticas tiene solución y,
en caso afirmativo, calcúlala:

- (a) $25x + 36y = 10$.
- (b) $200x + 1768y = 8$.
- (c) $40x + 50y = 3$.
- (d) $213x + 1123y = 18$.
- (e) $14x + 165y = 1$.

**Problema 22:** halla la expresión general de las raíces enteras de la ecuación
$37x - 13y = 8$.

**Problema 23:** sea $c$ un número entero positivo tal que $10\leq c\leq 100$.
¿Cuál es el valor mínimo de $c$ para el cual la ecuación $84x + 990y = c$ admite
soluciones enteras?

**Problema 24:** halla el menor número natural $m$ de manera que la ecuación
$533x + 299y = 20000 + m$ tenga soluciones enteras y calcúlalas.

**Problema 25:** halla

- (a) el menor entero positivo $a$ tal que la ecuación $1001x + 770y = 10^6 + a$
  admite soluciones naturales.
- (b) para dicho valor de $a$, determina las soluciones naturales de dicha
  ecuación.

**Problema 26:** se dispone de un gran suministro de agua, un gran cubo con
desagüe y dos garrafas que contienen $7$ y $9$ litros. ¿Cómo podría ponerse un
litro de agua en el cubo?

**Problema 27:** un hombre compra caballos y vacas, pagando $1770$ euros. Una
vaca cuesta $21$ euros y un caballo $31$ euros, ¿cuántos caballos y vacas ha
comprado?

**Problema 28:** para abonar una factura de $1840$ pesetas, se entregan libras
esterlinas y dan la vuelta en marcos. Calcula las libras esterlinas entregadas y
los marcos devueltos, suponiendo que se ha entregado la cantidad mínima de
libras necesarias para pagar y que la devolución sea en marcos ($1$ marco $=70$
pesetas, $1$ libra esterlina $=180$ pesetas).

**Problema 29:** se compran manzanas y naranjas. En total, $12$ piezas de fruta,
que cuestan $1.32$ euros. Si una manzana vale $3$ céntimos más que una naranja y
hay más manzanas que naranjas, ¿cuántas piezas de cada fruta se han comprado?

**Problema 30:** una persona va a un supermercado y compra $12$ litros de leche,
unos de leche entera y otros de desnatada, por $1200$ pesetas. Si la leche
entera vale $30$ pesetas más por litro que la desnatada y ha comprado el mínimo
posible de leche desnatada, ¿cuántos litros habrá comprado de cada una?

**Problema 31:** halla las soluciones enteras de las ecuaciones diofánticas

- (a) $6x + 8y + 14z = 22$.
- (b) $6x + 10y + 15z = 31$.

**Problema 32:** encuentra todas las soluciones enteras positivas de la ecuación
$43x + 7y + 17z = 400$.

**Problema 33:** un granjero compró vacas, cerdos y pollos. En total, $100$
animales por $100$ euros. Hay al menos uno de cada. Si una vaca cuesta $10$
euros, un cerdo $3$ euros y un pollo $0.50$ euros, ¿cuántos animales de cada
clase compró?

**Problema 34:** en una tienda de animales los loros cuestan $5$ euros, los
periquitos $3$ euros cada uno y los canarios $10$ céntimos cada uno. Compramos
$100$ animales y pagamos $100$ euros. ¿Cuántos compramos de cada clase?

**Problema 35:** resuelve, en los números naturales, el siguiente sistema,
demostrando que tiene una única solución:

$$
\begin{aligned}
x + y + z + p + t &= 25,\\ y - 2z - p &= 0,\\ x - t &= 1,\\ -x + y + z &= 0.
\end{aligned}
$$

**Problema 36:** halla las soluciones naturales de las ecuaciones

- (a) $x^2 - y^2 = 46$.
- (b) $x^2 - y^2 = 36$.

**Problema 37:** halla las soluciones enteras de la ecuación $x^2 - y^2 = 24$.

**Problema 38:** encuentra todas las soluciones naturales de la ecuación
$x^2 - y^2 = 252$.

**Problema 39:** halla soluciones enteras no triviales para la ecuación
$x^2 - 7y^2 = 1$.

**Problema 40:** halla soluciones enteras no triviales para la ecuación
$x^2 - 3y^2 = 1$.

**Problema 41:** halla las soluciones enteras no triviales para la ecuación
$x^2 - 15y^2 = 1$.

**Problema 42:** prueba que $3$, $4$ y $5$ es la única solución de
$x^2 + y^2 = z^2$ en enteros positivos consecutivos.

**Problema 43:** ¿qué cuadrado de cinco cifras, al quitarle una unidad, se puede
descomponer en suma de cinco cuadrados idénticos?

**Problema 44:** halla los números naturales $n$ de manera que se cumpla que
$1+2+\cdots+n = k^2$, con $k$ número natural.

**Problema 45:** ¿cuál es el menor triángulo cuyos lados son números enteros
consecutivos y su área es múltiplo de $20$?

**Problema 46:** halla todos los triángulos cuyos lados son tres números enteros
consecutivos y su área es asimismo un número entero.

**Problema 47:** determina las dimensiones de un rectángulo sabiendo que sus
lados miden un número entero de centímetros, pero no un número entero de palmos;
y que su área, expresada en palmos cuadrados, es igual a su perímetro, expresado
en palmos lineales. Considera que un palmo equivale a $20$ centímetros.

**Problema 48:** en su último viaje a Estados Unidos, el señor Martínez cambió
un cheque de viaje. El cajero, al pagarle, confundió el número de dólares con el
de centavos y viceversa. El señor Martínez gastó $68$ centavos en sellos y
comprobó que el dinero que le quedaba era el doble del importe del cheque de
viaje que había cambiado. ¿Qué valor mínimo tenía el cheque de viaje?

**Problema 49:** una persona ha comprado entradas para el cine para personas
adultas por un precio de $640$ u. m. cada una y para menores de edad a $330$ u.
m. Sabiendo que invirtió $7140$ u. m. y que compró menos entradas de adultos que
de menores, halla el número de entradas que adquirió.

**Problema 50:** los lados de un rectángulo vienen dados por números naturales.
¿Cuál será la longitud de dichos lados para que el perímetro y la superficie de
dicha figura se expresen con el mismo número?

**Problema 51:** halla un número de seis cifras que es igual a las seis últimas
cifras de su cuadrado.

**Problema 52:** halla dos números enteros tales que la suma de sus cuadrados es
el doble de su suma.

**Problema 53:** prueba que existen cuadrados de la forma
$1 + 2 ^ {x^2} + 2 ^ {y^2}$.

**Problema 54:** sean $a$, $b$ y $c$ números naturales distintos.

- (a) Halla un conjunto infinito de soluciones de la ecuación
  $a^2 + b^2 + c^2 = 2c(a + b)$.
- (b) Demuestra que, si $a<b<c$, la ecuación
  $a^3 - c^3 + b^3 = 3b(a - c)(a + c - b)$ no tiene solución.

**Problema 55:** halla las soluciones enteras de las ecuaciones diofánticas:

- (a) $2x^2 + x - 3y = 7$.
- (b) $x^2 + x + 2y = 3$.
- (c) $x^2 + x + 3y = 2$.

**Problema 56:** halla las soluciones enteras de la ecuación $109x + 89y = 1$
utilizando el algoritmo de Euclides.

**Problema 57:** encuentra todas las soluciones positivas de

$$
\frac{a}{13} + \frac{b}{19} = \frac{230}{247}.
$$

**Problema 58:** encuentra el inverso de $46$ en $\mathbb{Z}_{53}$.

**Problema 59:** los precios de dos productos son $18$ y $33$ euros por unidad.
¿Cuál es el número mínimo y máximo de unidades que se pueden haber vendido si se
han cobrado $639$ euros?

**Problema 60:** un sastre invierte $13$ horas en diseñar un pantalón y $37$
horas en diseñar un modelo de camisa. Si trabaja $2000$ horas, ¿cuántas camisas
y pantalones debería diseñar para conseguir la mejor combinación entre
pantalones y camisas?

**Problema 61:** halla todos los números naturales menores que $1000$ que sean
múltiplos de $28$ y que, divididos por $15$, den de resto $9$.

**Problema 62:** halla las soluciones enteras de la ecuación
$$\sqrt{(x+y)(x-y) + (2x+2y-3)y - 2(x-7)} = x+y+3.$$

**Problema 63:** halla las soluciones enteras de la ecuación $x^2 - y^2 = 8$.

**Problema 64:** encuentra el inverso de $37$ en $\mathbb{Z}_{62}$.

**Problema 65:** encuentra un número natural $n$ tal que $n^2 + 10n$ es cuadrado
perfecto.

**Problema 66:** encuentra el inverso de $7$ en $\mathbb{Z}_{31}$.

**Problema 67:** una mujer compra $12$ vestidos, unos rojos y otros blancos,
gastándose $1200$ euros. Si los trajes rojos valen $30$ euros más que los
blancos, ¿cuántos vestidos ha comprado de cada color?

**Problema 68:** en un corral hay conejos y gallinas, contándose $22$ patas.
¿Cuántas gallinas y conejos hay?
