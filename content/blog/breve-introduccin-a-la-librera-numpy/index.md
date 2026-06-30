---
title: Breve introducción a la librería NumPy
summary:
    Tras la buena experiencia vivida después de la sesión dedicada a Machine
    learning, de la convención SciPy 2017, me he animado a seguir explorando la
    lista de reproducción del canal de Youtube asociado a la cuenta de
    Enthought.
date: 2018-08-18
lastmod: 2026-06-30
image:
    caption: Imagen generada por Leonardo.Ai
authors:
    - me
categories:
    - Tutoriales
tags:
    - NumPy
    - Python
status: published
---

Tras la buena experiencia vivida después de la sesión dedicada a _machine
learning_, de la convención _SciPy 2017_, me he animado a seguir explorando la
[lista de reproducción](https://www.youtube.com/playlist?list=PLYx7XA2nY5GfdAFycPLBdUDOUtdQIVoMf)
del canal de _Youtube_ asociado a la cuenta de _Enthought_.

Varios títulos han captado poderosamente mi atención (a la hora de escribir
estas líneas, la mencionada lista de reproducción sobrepasa los noventa vídeos),
pero teniendo en cuenta que todo el ecosistema de _SciPy_ se asienta sobre la
librería _NumPy_, he terminado considerando que la elección más sensata era
optar por _"Introduction to Numerical Computing with NumPy"_, que viene de la
mano de Dillon Niederhut.

Este artículo recoge las notas personales tomadas durante la visualización de
dicho tutorial, al cual podemos acceder a través del siguiente
[enlace](https://youtu.be/lKcwuPnSHIQ), y que posee asociado un
[repositorio](https://github.com/enthought/Numpy-Tutorial-SciPyConf-2017) en
_GitHub_ que, principalmente, conviene tener a mano para seguir algunos de los
ejercicios planteados durante la sesión.

Antes de empezar, me gustaría destacar que el material está enfocado a
principiantes, por lo que el ritmo es bastante más sosegado que el llevado por
aquel de _machine learning_ que mencionaba en el primer párrafo. Además, me ha
parecido ciertamente curiosa la manera de tratar a los participantes, intentando
en todo momento que se sientan en un entorno de aprendizaje bastante
confortable.

### 1. ¿Por qué aprender a utilizar la librería _NumPy_?

Qué mejor manera de empezar esta entrada que justificando la necesidad de
aprender a utilizar la librería _NumPy_. Introducirse al manejo de un nuevo
módulo (y no digamos ya dominarlo) es una tarea que normalmente requiere una
buena inversión de horas de estudio y experimentación, y _NumPy_, por desgracia,
no es la excepción que rompe la mencionada regla. Así pues, ¿por qué aprender a
utilizar la librería _NumPy_?

La respuesta, _grosso modo_, vendría dada por el más que discutible rendimiento
del lenguaje de programación _Python_ a la hora de llevar a cabo cálculos
numéricos. Ilustremos este hecho con un sencillo ejemplo: sumaremos los
elementos de una lista que contendrá los primeros mil números enteros positivos
(que construiremos con la función `range()`), midiendo el tiempo que requiere la
mencionada operación a través del comando mágico `%timeit`.

```python
test_list = list(range(1001))

%timeit sum(test_list)
```

    100000 loops, best of 3: 10.8 µs per loop

Ahora repitamos la misma operación empleando funciones de la librería _NumPy_.
Para ello:

- importaremos el módulo siguiendo la convención establecida, es decir,
  escribiendo `import numpy as np`,
- creamos una réplica de la anterior lista (que, en breve, empezaremos a llamar
  _array_) utilizando la función `arange()`, y
- sumaremos sus elementos mediante la función `sum()`.

```python
import numpy as np

test_array = np.arange(1001)

%timeit np.sum(test_array)
```

    The slowest run took 14.21 times longer than the fastest. This could mean that an intermediate result is being cached.
    100000 loops, best of 3: 5.02 µs per loop

Hemos reducido a la mitad el tiempo que precisa el sistema para realizar el
cálculo numérico requerido. No obstante, quizá no logre impactarnos el hecho de
pasar de 11 a 5 microsegundos. Intentemos forzar un tanto el anterior ejemplo
incrementando de manera significativa el número de elementos.

```python
n = 1000001
test_list  = list(range(n)) # Python
test_array = np.arange(n)   # NumPy
```

```python
%timeit sum(test_list)
```

    10 loops, best of 3: 46.3 ms per loop

```python
%timeit np.sum(test_array)
```

    1000 loops, best of 3: 748 µs per loop

El resultado ahora sí que debería ser una buena justificación de cara a decidir
si invertir o no nuestro preciado tiempo en aprender a utilizar la librería
_NumPy_. Esta considerable mejora en el tiempo de ejecución para cálculos
numéricos se produce en cualquier tipo de operación matemática que llevemos a
cabo empleando funciones de dicho módulo.

Si tenemos en mente utilizar el lenguaje de programación _Python_ para analizar
datos, considerando que al final casi todo se reduce a realizar cálculos
numéricos con matrices de dimensiones considerables, _NumPy_ se convierte
entonces en una herramienta esencial.

Sin entrar en demasiados detalles técnicos, esta situación se produce debido a
que:

1. es distinta, y mucho más eficiente, la manera en que se accede a los
   elementos de un _array_ de _NumPy_ con respecto a como _Python_ procede a
   realizar tal tarea en sus estructuras de datos básicas,
2. el número de comprobaciones intermedias a la hora de llevar a cabo cálculos
   numéricos es menor en _NumPy_, y
3. _NumPy_ está escrito utilizando el lenguaje de programación _C_, que es
   bastante más rápido que _Python_.

Sin embargo, no es oro todo lo que reluce en _NumPy_. En futuras secciones
veremos que las, _a priori_, ventajas expuestas en el listado anterior
(sobretodo las dos primeras), conllevan aparejados ciertos inconvenientes de los
que hemos de ser conscientes para evitar _bugs_ en nuestros códigos.

### 2. ¿Qué está pasando aquí? Primeras sorpresas que nos regala _Numpy_

Para empezar, al utilizar los _arrays_ de _NumPy_, vamos a perder ciertas
características deseables que poseen las estructuras de datos básicas de
_Python_. Por ejemplo, los elementos de una lista en _Python_ pueden ser
heterogéneos, es decir, de diversos tipos. En una misma lista podemos almacenar
números enteros, cadenas de texto, números decimales y valores lógicos sin
problema alguno. No obstante, todos los elementos de un _array_ de _NumPy_,
obligatoriamente, deben pertenecer al mismo tipo. Por otro lado, estamos
acostumbrados a ampliar o reducir el tamaño de una lista en _Python_ de manera
dinámica, mientras que en _NumPy_ tendremos que trabajar con _arrays_ de
dimensión fija preestablecida. Esto último no es del todo cierto, pero reajustar
el tamaño de un _array_ en _NumPy_ no es una operación eficiente, por lo que no
se suele realizar salvo contadas excepciones.

Sin embargo, aquello esbozado en el párrafo anterior palidece ante la pérdida de
esas "redes de seguridad" a las que _Python_ nos tiene acostumbrados. Ilustremos
la situación mediante algunos ejemplos: crearemos un _array_ en _NumPy_ a través
de la función `array()`, pasándole una lista con los elementos que queremos
pertenezcan al mencionado _array_. Además, impondremos que dichos elementos sean
del tipo `int8`, utilizando para ello el argumento `dtype`.

_Nota_: para conocer más detalles sobre los distintos tipos disponibles para los
elementos de _array_, podemos echar un vistazo a la
[página](https://docs.scipy.org/doc/numpy/reference/arrays.dtypes.html) de la
documentación oficial asociada al tema.

```python
a = np.array([-1, 0, 1, 100], dtype='int8')

a
```

    array([ -1,   0,   1, 100], dtype=int8)

Empecemos llevando a cabo algunas operaciones básicas. Por ejemplo, ¿qué sucede
en _Python_ cuando intentamos dividir un número por cero?

```python
1 / 0
```

    ---------------------------------------------------------------------------
    ZeroDivisionError                         Traceback (most recent call last)
    <ipython-input-7-b710d87c980c> in <module>()
    ----> 1 1 / 0

    ZeroDivisionError: division by zero

```python
1 // 0
```

    ---------------------------------------------------------------------------
    ZeroDivisionError                         Traceback (most recent call last)
    <ipython-input-8-8ba90f639c23> in <module>()
    ----> 1 1 // 0

    ZeroDivisionError: integer division or modulo by zero

_Python_ arroja una excepción si encuentra una situación de este tipo,
deteniendo por completo el proceso de la que forme parte. Probemos ahora a
dividir por cero el _array_ `a` declarado arriba.

_Nota_: en _NumPy_ las operaciones aritméticas sobre vectores se realizan
elemento a elemento, por lo que una instrucción del estilo `a + 1` lo que hace
es sumar una unidad a cada una de las componentes del _array_ `a`.

```python
a / 0
```

    C:\Anaconda3\lib\site-packages\ipykernel_launcher.py:1: RuntimeWarning: divide by zero encountered in true_divide
      """Entry point for launching an IPython kernel.
    C:\Anaconda3\lib\site-packages\ipykernel_launcher.py:1: RuntimeWarning: invalid value encountered in true_divide
      """Entry point for launching an IPython kernel.

    array([-inf,  nan,  inf,  inf])

```python
a // 0
```

    C:\Anaconda3\lib\site-packages\ipykernel_launcher.py:1: RuntimeWarning: divide by zero encountered in floor_divide
      """Entry point for launching an IPython kernel.

    array([0, 0, 0, 0], dtype=int8)

Recibimos un _warning_ en la consola, pero el proceso continúa. Es más, incluso
devuelve un resultado que es, cuanto menos, curioso. Para la división entera,
obtenemos un vector cuyos elementos son todos nulos, mientras que para la
división estándar, los elementos son `inf` (infinito) o `nan` (_Not A Number_ o,
lo que es lo mismo, una entidad indefinida).

Por mucho que hayamos declarado de tipo entero (`int8`) los elementos de nuestro
_array_ `a`, ya no estamos trabajando, por así decirlo, con los _integer_ de
_Python_, y son distintas las reglas definidas para ellos. Con _NumPy_ hemos de
ser muy conscientes de este hecho, para evitar todo tipo de "situaciones
curiosas".

```python
a // 0 + 1
```

    C:\Anaconda3\lib\site-packages\ipykernel_launcher.py:1: RuntimeWarning: divide by zero encountered in floor_divide
      """Entry point for launching an IPython kernel.

    array([1, 1, 1, 1], dtype=int8)

La siguiente sorpresa la podemos encontrar si, por el motivo que sea, nos
interesa elevar al cuadrado las componentes del _array_ `a` declarado arriba.

```python
a
```

    array([ -1,   0,   1, 100], dtype=int8)

```python
a ** 2
```

    array([ 1,  0,  1, 16], dtype=int8)

Todo parece correcto hasta que llegamos a un más que sorprendente $100^2 = 16$.
¿Qué acaba de suceder aquí?
[Integer overflow](https://en.wikipedia.org/wiki/Integer_overflow). Al declarar
que el tipo de los elementos de nuestro _array_ `a` sería `int8`, nos es
imposible representar un número tan grande como `100 ** 2`. En esta ocasión, ni
siquiera recibimos un _warning_ que nos advierta de que se ha producido tal
situación.

Recuperemos ahora el tema de los `nan` que brevemente ha aparecido anteriormente
al llevar a cabo una división por cero.

```python
a / 0
```

    C:\Anaconda3\lib\site-packages\ipykernel_launcher.py:1: RuntimeWarning: divide by zero encountered in true_divide
      """Entry point for launching an IPython kernel.
    C:\Anaconda3\lib\site-packages\ipykernel_launcher.py:1: RuntimeWarning: invalid value encountered in true_divide
      """Entry point for launching an IPython kernel.

    array([-inf,  nan,  inf,  inf])

A la hora de analizar tablas de datos, es ciertamente frecuente encontrar que
los valores pérdidos se codifiquen como `nan`. Curiosamente, en _NumPy_, tenemos
que:

```python
np.nan == np.nan
```

    False

Hecho que, por otra parte, es bastante lógico. Si tenemos una entidad
indefinida, difícil será que podamos comparar si es igual a otra entidad
indefinida. No obstante, esta filosofía invalida la búsqueda de valores perdidos
por la clásica vía de comparación con `nan`. En _NumPy_, para comprobar la
existencia de dichos valores y que han sido codificados como `nan`, tendremos
que emplear funciones del tipo `isnan()`.

```python
np.isnan(np.nan)
```

    True

```python
np.isnan(a / 0)
```

    C:\Anaconda3\lib\site-packages\ipykernel_launcher.py:1: RuntimeWarning: divide by zero encountered in true_divide
      """Entry point for launching an IPython kernel.
    C:\Anaconda3\lib\site-packages\ipykernel_launcher.py:1: RuntimeWarning: invalid value encountered in true_divide
      """Entry point for launching an IPython kernel.

    array([False,  True, False, False], dtype=bool)

Finalmente, como tanto los `inf` como los `nan` se codifican de manera distinta
a los números enteros, no vamos a poder tener en un _array_ de enteros ciertos
elementos declarados como `nan`.

```python
np.array([1, 2, np.nan], dtype='int8')
```

    ---------------------------------------------------------------------------
    ValueError                                Traceback (most recent call last)
    <ipython-input-18-6d8f5ee90faf> in <module>()
    ----> 1 np.array([1, 2, np.nan], dtype='int8')

    ValueError: cannot convert float NaN to integer

No obstante, con otros tipos de datos, esta situación no se da.

```python
np.array([1, 2, np.nan], dtype='float32')
```

    array([  1.,   2.,  nan], dtype=float32)

Así pues, a modo de resumen, la moraleja que extraemos de este apartado sería
que, si vamos a utilizar la librería _NumPy_, tenemos que empezar a prestar más
atención a las representaciones binarias de nuestros datos y su efecto a la hora
de trabajar numéricamente con ellas.

### 3. Creando _arrays_ especiales en _NumPy_

La librería _NumPy_ contiene una serie de funciones orientadas a generar
_arrays_ especiales como, por ejemplo, aquellos cuyas componentes son todas
nulas, todas unos o, incluso, que consistan en una serie de huecos vacíos a
rellenar en un futuro.

```python
np.zeros
```

    <function numpy.core.multiarray.zeros>

```python
np.ones
```

    <function numpy.core.numeric.ones>

```python
np.empty
```

    <function numpy.core.multiarray.empty>

Las anteriores funciones mostradas requieren como argumento obligatorio, para
crear los _arrays_ asociados, el número total de elementos (si buscamos generar
un _array_ unidimensional) o una _tupla_ que contenga las distintas dimensiones
(si deseamos crear un _array_ multidimensional).

```python
np.zeros(5)
```

    array([ 0.,  0.,  0.,  0.,  0.])

```python
np.ones((2, 2))
```

    array([[ 1.,  1.],
           [ 1.,  1.]])

```python
np.empty((3, 3, 3))
```

    array([[[  1.04468097e-311,   1.04464737e-311,   9.34598925e-307],
            [  8.45605478e-307,   1.37962592e-306,   1.24610994e-306],
            [  1.29061821e-306,   4.45057637e-308,   8.90051274e-307]],

           [[  8.45596650e-307,   1.11261434e-306,   4.45061880e-308],
            [  1.69109959e-306,   7.56603882e-307,   4.45063578e-308],
            [  1.24606309e-306,   1.78019625e-306,   9.34610469e-307]],

           [[  8.90051274e-307,   1.95810846e-306,   1.29062229e-306],
            [  1.33506605e-306,   1.37962388e-306,   1.37961302e-306],
            [  8.45596650e-307,   2.44033110e-312,   0.00000000e+000]]])

En los elementos que componen el _array_ generado a partir de la función
`empty()` encontramos aquello que previamente residía en memoria en el instante
anterior a la creación de dicho array. Es por ello que, en ocasiones, si
procedemos a revisarlos inmediatamente después de su declaración, encontremos
valores curiosos tipo `9.34598925e-307`.

### 4. Accediendo a los elementos de un _array_

Partiendo del _array_ `a` que declaramos en una sección anterior, en esta
veremos cómo acceder a sus elementos. En _NumPy_ podemos utilizar las clásicas
estrategias de _get_ y _slice_ a las que estamos acostumbrados en _Python_ para
extraer elementos de sus estructuras de datos básicas.

```python
a
```

    array([ -1,   0,   1, 100], dtype=int8)

Así, por ejemplo, para acceder al primer elemento de `a`, `-1`, no tenemos más
que escribir:

```python
a[0]
```

    -1

```python
type(a[0])
```

    numpy.int8

Como suele ser habitual en _Python_, al emplear estrategias de tipo _get_
perdemos la estructura de datos de la que partíamos. Al ejecutar `a[0]` el
resultado deja de ser un _array_ de _NumPy_ para convertirse, en este caso, en
un número entero. Como ya advertimos en una sección anterior, a la hora de
trabajar con _NumPy_ debemos en todo momento saber con qué tipo de dato estamos
trabajando y las reglas bajo las que se rige. El entero que acabamos de extraer
del _array_ `a`, como hemos podido comprobar mediante la función `type()`, es de
tipo `numpy.int8`, no de tipo `int` como a primera vista podríamos sospechar.
Cierta cautela se nos exige si tras la extracción tenemos en mente llevar a cabo
cualquier tipo de operación matemática con el mencionado valor.

```python
a[0] // 0
```

    C:\Anaconda3\lib\site-packages\ipykernel_launcher.py:1: RuntimeWarning: divide by zero encountered in floor_divide
      """Entry point for launching an IPython kernel.

    0

Podemos utilizar también índices negativos para acceder a los elementos de un
_array_.

```python
a[-1]
```

    100

Además, como comentábamos al principio, es posible emplear estrategias de tipo
_slice_ para recuperar ciertas partes de los _arrays_ declarados. Por ejemplo:

```python
a[0:2]
```

    array([-1,  0], dtype=int8)

En esta ocasión, la estructura de datos se conserva, puesto que el resultado de
la extracción continúa siendo un _array_.

Por otro lado, las reglas habituales del uso de estrategias de tipo _slice_ se
mantienen para los _arrays_ de _NumPy_. Por ejemplo:

```python
a[:2]
```

    array([-1,  0], dtype=int8)

```python
a[::2]
```

    array([-1,  1], dtype=int8)

Finalmente, aunque los _arrays_ sean, generalmente, de tamaño fijo, son un tipo
de estructura de datos mutable, es decir, podemos modificar en cualquier momento
el valor de sus elementos. Por ejemplo, para reemplazar en el _array_ `a` el
elemento `100` por un `5`, simplemente tendríamos que teclear:

```python
a[-1] = 5

a
```

    array([-1,  0,  1,  5], dtype=int8)

### 5. Trabajando con _arrays_ multidimensionales

Para generar _arrays_ multidimensionales no tenemos más que anidar listas (`[]`)
en la declaración del argumento de la función `array()`. Por ejemplo, podemos
generar un _array_ bidimensional siguiendo un patrón similar al que figura a
continuación:

```python
b = np.array([[0, 1, 2],
              [3, 4, 5],
              [6, 7, 8],
              [9, 10, 11]])

b
```

    array([[ 0,  1,  2],
           [ 3,  4,  5],
           [ 6,  7,  8],
           [ 9, 10, 11]])

El _array_ `b` es bidimensional, como bien podemos comprobar a través de sus
atributos `.ndim` y `.shape`.

```python
b.ndim
```

    2

```python
b.shape
```

    (4, 3)

Al tratarse `b` de los primeros once números enteros positivos (incluyendo el
`0`), para evitar errores a la hora de introducir los datos, podríamos haber
empleado primero la función `arange()`, para luego emplear `reshape()` y
transformar el _array_ unidimensional en uno bidimensional.

```python
b = np.arange(12).reshape(4, 3)

b
```

    array([[ 0,  1,  2],
           [ 3,  4,  5],
           [ 6,  7,  8],
           [ 9, 10, 11]])

Es posible que, en este preciso instante, estemos tentados a denominar la
primera dimensión del _array_ `b` como _filas_ y la segunda como _columnas_, por
su similaridad con las tablas de datos con las que estamos acostumbrados a
lidiar. No obstante, debemos ser cautos con esta nomenclatura, puesto que con
_NumPy_ podemos generar _arrays_ $n$-dimensionales y, en ese contexto, es un
tanto confuso hablar de _filas_ y _columnas_.

El acceso a los elementos del _array_ `b` lo podemos llevar a cabo, al igual que
en la sección anterior, mediante estrategias de tipo _get_ o _slice_. Por
ejemplo:

```python
b[2, 2]
```

    8

```python
type(b[2, 2])
```

    numpy.int32

```python
b[:2, :2]
```

    array([[0, 1],
           [3, 4]])

Como era de esperar, no tenemos por qué utilizar la misma estrategia en todas
las dimensiones del _array_, pero sí debemos prestar atención a la estructura de
datos resultante (o más bien a su dimensión) cuando empleamos ambos tipos.

```python
b[1:3, -1]
```

    array([5, 8])

```python
b[1:3, -1:]
```

    array([[5],
           [8]])

Dependiendo de si acto seguido vamos a utilizar el anterior resultado para
llevar a cabo algún tipo de cálculo matemático, este detalle puede resultar de
vital relevancia.

Si estamos interesados en que el resultado de la extracción conserve el número
de dimensiones del objeto original, en todas y cada una de las dimensiones hemos
de emplear estrategias de tipo _slice_.

```python
b[:1, :1]
```

    array([[0]])

```python
b[:1, :1].ndim
```

    2

```python
b[:1, :1].shape
```

    (1, 1)

**Ejercicio**: dado el _array_ tridimensional `c`:

```python
c = np.arange(24).reshape(2, 3, 4)

c
```

    array([[[ 0,  1,  2,  3],
            [ 4,  5,  6,  7],
            [ 8,  9, 10, 11]],

           [[12, 13, 14, 15],
            [16, 17, 18, 19],
            [20, 21, 22, 23]]])

Se pide:

1. Extraer el número `17`.
2. Extraer el _array_

    ```
    [[ 0,  1,  2,  3],
     [ 4,  5,  6,  7],
     [ 8,  9, 10, 11]].
    ```

3. Extraer el _array_ `[12, 13, 14, 15]`.

**Solución**:

```python
c[1, 1, 1]
```

    17

```python
c[0, :, :]
```

    array([[ 0,  1,  2,  3],
           [ 4,  5,  6,  7],
           [ 8,  9, 10, 11]])

```python
c[1, 0, :]
```

    array([12, 13, 14, 15])

_Nota_: este ejercicio resulta trivial si previamente optamos por convertir el
_array_ tridimensional `c` en uno unidimensional utilizando la función
`flatten()`:

```python
c.flatten()
```

    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
           17, 18, 19, 20, 21, 22, 23])

**Ejercicio**: dado el _array_ bidimensional `a`:

```python
a = np.arange(25).reshape(5, 5)

a
```

    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14],
           [15, 16, 17, 18, 19],
           [20, 21, 22, 23, 24]])

Se pide:

1. Extraer el _array_ `[20, 21, 22, 23, 24]`.
2. Extraer el _array_

    ```
    [[ 1,  3],
     [ 6,  8],
     [11, 13],
     [16, 18],
     [21, 23]].
    ```

3. Extraer el _array_

    ```
    [[ 5,  7],
     [15, 17]].
    ```

**Solución**:

```python
a[4, :] # a[-1, :]
```

    array([20, 21, 22, 23, 24])

```python
a[:, 1::2] # a[:, 1:4:2]
```

    array([[ 1,  3],
           [ 6,  8],
           [11, 13],
           [16, 18],
           [21, 23]])

```python
a[1::2, 0:4:2] # a[1::2, :3:2]
```

    array([[ 5,  7],
           [15, 17]])

Esta manera de extraer los elementos de un _array_ es extremadamente rápida y
eficiente (coste de orden constante), característica deseable a hora de llevar a
cabo análisis de datos de tablas cuyas dimensiones sean considerables. No
obstante, con estrategias de _get_ y _slice_ no siempre seremos capaces de
acceder fácilmente a cualquier subconjunto de elementos de un _array_, teniendo
que recurrir entonces a lo que se conoce como _fancy indexing_.

### 6. Accediendo a los elementos de un _array_ mediante _Fancy indexing_

La primera estrategia de acceso a los elementos de un _array_ empleando _fancy
indexing_ consiste, simplemente, en utilizar una llamada de tipo _get_ donde
proporcionaremos una lista (`[]`) que contenga los índices de los elementos que
deseamos extraer. Ilustremos la manera de proceder mediante algunos ejemplos.

```python
a = np.arange(4)

a
```

    array([0, 1, 2, 3])

Si ahora buscamos acceder al primer (índice `0`) y último (índice `3`) elemento
de `a`, escribiríamos:

```python
a[[0, 3]]
```

    array([0, 3])

De la misma forma podemos extraer los elementos primero, segundo y último de `a`

```python
a[[0, 1, 3]]
```

    array([0, 1, 3])

```python
a[[0, 1, -1]] # versión con índices negativos
```

    array([0, 1, 3])

Veamos a continuación cómo proceder a la hora de trabajar con _arrays_
bidimensionales.

```python
b = np.arange(12).reshape(4, 3)

b
```

    array([[ 0,  1,  2],
           [ 3,  4,  5],
           [ 6,  7,  8],
           [ 9, 10, 11]])

Supongamos que buscamos extraer los números `2` y `6`. Necesitaremos ahora pasar
dos listas a la llamada de tipo _get_ para acceder a dichos números, una con sus
índices asociados a la primera dimensión (`0` y `2` en este caso) y otra con sus
correspondientes índices de la segunda dimensión (`2` y `0` en esta ocasión).

```python
b[[0, 2], [2, 0]]
```

    array([2, 6])

Seguramente quede más clara la manera de proceder si ilustramos la anterior
estrategia para un _array_ tridimensional.

```python
c
```

    array([[[ 0,  1,  2,  3],
            [ 4,  5,  6,  7],
            [ 8,  9, 10, 11]],

           [[12, 13, 14, 15],
            [16, 17, 18, 19],
            [20, 21, 22, 23]]])

Si nos interesa acceder a los números `6` y `17`, dentro de la estrategia de
tipo _get_ tendríamos que declarar tres listas (porque el array `c` es
tridimensional), cada una de ellas compuesta por dos elementos (debido a que
buscamos extraer dos números), indicando los índices de los mencionados números
para todas y cada una de las dimensiones del _array_ `c`.

Para el caso del número `6`:

- Índice de la primera dimensión: `0`.
- Índice de la segunda dimensión: `1`.
- Índice de la tercera dimensión: `2`.

Para el caso del número `17`:

- Índice de la primera dimensión: `1`.
- Índice de la segunda dimensión: `1`.
- Índice de la tercera dimensión: `1`.

Ahora, la intuición seguramente nos llevaría a escribir una llamada del tipo
`c[[0, 1, 2], [1, 1, 1]]`, a partir de las "coordenadas en el espacio" de los
números buscados, recibiendo entonces un error en la consola.

```python
c[[0, 1, 2], [1, 1, 1]]
```

    ---------------------------------------------------------------------------
    IndexError                                Traceback (most recent call last)
    <ipython-input-63-2310a6526161> in <module>()
    ----> 1 c[[0, 1, 2], [1, 1, 1]]

    IndexError: index 2 is out of bounds for axis 0 with size 2

Debemos intentar evitar pensar en los elementos de un _array_ multidimensional a
partir de sus coordenadas y hacerlo empleando directamente el número de
dimensiones. Para que la anterior instrucción hubiese funcionado, el _array_ `c`
tendría que haber sido bidimensional (porque encontramos declaradas dos listas)
y el objetivo acceder a tres elementos (debido a que cada una de las listas
posee tres componentes).

De esta manera, para extraer los números `6` y `17` de `c`, hemos de teclear:

```python
c[[0, 1], [1, 1], [2, 1]]
```

    array([ 6, 17])

A medida que el número de elementos a los que queremos acceder o la cantidad de
dimensiones del _array_ se incrementan, esta forma de proceder se vuelve
ciertamente un tanto tediosa. Es por ello que, en ocasiones, conviene emplear
una estrategia alternativa de _fancy indexing_ cuyo funcionamiento se asienta en
el adecuado uso de _máscaras_.

Supongamos que, trabajando con el _array_ `c`, estamos interesados en acceder a
todos aquellos elementos que sean estrictamente mayores que `16`. Si escribimos:

```python
c > 16
```

    array([[[False, False, False, False],
            [False, False, False, False],
            [False, False, False, False]],

           [[False, False, False, False],
            [False,  True,  True,  True],
            [ True,  True,  True,  True]]], dtype=bool)

Obtenemos un _array_ tridimensional formado por valores lógicos, y de la misma
dimensión que `c`, que, para todos y cada uno de sus elementos, nos informa de
si satisface la condición planteada (`True`) o no (`False`). Dicha información
se la podemos suministrar a una estrategia de tipo _get_ para así acceder a los
elementos que nos interese.

```python
c[c > 16]
```

    array([17, 18, 19, 20, 21, 22, 23])

Como no podía ser de otra manera, la concatenación de accesos está también
permitida. En el caso de buscar el primer elemento estrictamente mayor que `16`
podríamos teclear:

```python
c[c > 16][0]
```

    17

No obstante, en ocasiones resulta un tanto confusa esta forma de proceder,
sobretodo si el número de dimensiones con las que trabajamos es considerable y
concatenamos varios accesos de este estilo. Posiblemente facilita más la lectura
del código escribir la anterior instrucción en dos líneas, de la siguiente
manera:

```python
d = c[c > 16]

d[0]
```

    17

Sin embargo, la pregunta lógica que podríamos plantearnos en este instante es,
¿conviene que declaremos un nuevo objeto, con todo el coste de almacenamiento
que ello supone, simplemente por mejorar levemente la legibilidad de nuestros
códigos? La respuesta, aunque pueda parecer sorprendente, es afirmativa, dado
que, posiblemente, no estaremos creando un nuevo _array_ sino simplemente una
nueva cabecera que apunta al _array_ del que estamos extrayendo datos.

Sí, es un tanto confuso el final del anterior párrafo y, para añadir más
complejidad al asunto si cabe, es una situación que conlleva ciertos efectos
"curiosos" de los que hemos de ser conscientes para evitar _bugs_ de difícil
detección (qué recuerdos de los tiempos de _punteros_ con el lenguaje de
programación _C_). Las líneas que figuran a continuación son dignas de una
segunda parte para la sección del tutorial "¿Qué está pasando aquí? Primeras
sorpresas que nos regala _Numpy_".

Rescatemos el _array_ `c`:

```python
c
```

    array([[[ 0,  1,  2,  3],
            [ 4,  5,  6,  7],
            [ 8,  9, 10, 11]],

           [[12, 13, 14, 15],
            [16, 17, 18, 19],
            [20, 21, 22, 23]]])

Y almacenemos en un nuevo objeto `d` el resultado de cierta extracción de
elementos:

```python
d = c[:, 1:2, 1:3]

d
```

    array([[[ 5,  6]],

           [[17, 18]]])

Si ahora accedemos a cierta información de interés sobre el objeto `d`, a partir
de su atributo `flags`, encontramos que:

```python
d.flags
```

      C_CONTIGUOUS : False
      F_CONTIGUOUS : False
      OWNDATA : False
      WRITEABLE : True
      ALIGNED : True
      UPDATEIFCOPY : False

El atributo `OWNDATA` posee como valor `False`, es decir, el _array_ no controla
sus propios datos. Hemos generado un nuevo objeto, `d`, pero no se ha llevado a
cabo ninguna copia independiente de sus elementos en memoria, sino simplemente
la creación de una cabecera con información que apunta hacia los elementos de
interés del _array_ `c` que nos permiten construir el _array_ `d`.

Esta forma de proceder es ciertamente eficiente, porque copiar datos en memoria
es una operación costosa tanto en tiempo de ejecución como en espacio para
almacenamiento. Sin embargo, conlleva aparejada la siguiente "curiosa" (y, por
otra parte, muy lógica) situación.

```python
d[0, 0, 0] = 1000
```

```python
d
```

    array([[[1000,    6]],

           [[  17,   18]]])

```python
c
```

    array([[[   0,    1,    2,    3],
            [   4, 1000,    6,    7],
            [   8,    9,   10,   11]],

           [[  12,   13,   14,   15],
            [  16,   17,   18,   19],
            [  20,   21,   22,   23]]])

Cambios en el _array_ `d` afectan al _array_ `c` del cual se originó, por lo que
se exige, como ya viene siendo habitual a estas alturas con la librería _NumPy_,
cierta cautela a la hora de llevar a cabo algunas operaciones.

Sin embargo, si utilizamos las estrategias de _fancy indexing_, esbozadas en la
sección anterior, generalmente no encontraremos este tipo de situaciones.
_NumPy_ tratará de, en un principio, resolver la situación creando únicamente
una nueva cabecera, pero, de no ser posible (situación sumamente habitual),
procederá a realizar una copia de los datos de interés.

```python
e = c[c > 16]

e
```

    array([1000,   17,   18,   19,   20,   21,   22,   23])

```python
e.flags
```

      C_CONTIGUOUS : True
      F_CONTIGUOUS : True
      OWNDATA : True
      WRITEABLE : True
      ALIGNED : True
      UPDATEIFCOPY : False

```python
e[0] = 5

e
```

    array([ 5, 17, 18, 19, 20, 21, 22, 23])

```python
c
```

    array([[[   0,    1,    2,    3],
            [   4, 1000,    6,    7],
            [   8,    9,   10,   11]],

           [[  12,   13,   14,   15],
            [  16,   17,   18,   19],
            [  20,   21,   22,   23]]])

Esta situación también se presenta al emplear las funciones `reshape()` o al
trasponer un _array_. En lugar de crear una nueva copia de los datos, únicamente
se genera una cabecera en memoria que apunta a las direcciones adecuadas para
componer los nuevos _arrays_. Esto conlleva, por tanto, que apenas suponga coste
alguno el utilizar este tipo de funciones.

```python
f = np.array([[1, 2], [3, 4]])

f
```

    array([[1, 2],
           [3, 4]])

```python
f.flags
```

      C_CONTIGUOUS : True
      F_CONTIGUOUS : False
      OWNDATA : True
      WRITEABLE : True
      ALIGNED : True
      UPDATEIFCOPY : False

```python
g = f.reshape(4, 1)

g
```

    array([[1],
           [2],
           [3],
           [4]])

```python
g.flags
```

      C_CONTIGUOUS : True
      F_CONTIGUOUS : True
      OWNDATA : False
      WRITEABLE : True
      ALIGNED : True
      UPDATEIFCOPY : False

```python
h = f.T

h
```

    array([[1, 3],
           [2, 4]])

```python
h.flags
```

      C_CONTIGUOUS : False
      F_CONTIGUOUS : True
      OWNDATA : False
      WRITEABLE : True
      ALIGNED : True
      UPDATEIFCOPY : False

Como colofón, si examinamos el atributo `.flags` del propio objeto `c`:

```python
c.flags
```

      C_CONTIGUOUS : True
      F_CONTIGUOUS : False
      OWNDATA : False
      WRITEABLE : True
      ALIGNED : True
      UPDATEIFCOPY : False

Teniendo en cuenta que el _array_ `c` no se ha generado a partir de un objeto
distinto, ¿no debería poseer el atributo `OWNDATA` el valor `True`? La
justificación reside en la expresión que hemos empleado para crear dicho _array_
y que, a estas alturas de la vida y del tutorial, posiblemente hayamos ya
olvidado.

Recordemos que habíamos tecleado `c = np.arange(24).reshape(2, 3, 4)`, de manera
que la función `arange()` comienza creando una cabecera con la información del
_array_ (del estilo `.ndim` o `.shape`), así como reservando cierto espacio en
memoria para almacenar sus elementos. Después, la función `reshape()` únicamente
genera una nueva cabecera apuntando de manera adecuada a los mencionados
elementos y es por ello que el _array_ `c` no cree que sea el propietario de los
datos que lo integran. No obstante, que el valor del atributo `OWNDATA` sea
`False` indica que sus datos podrían o no ser manipulados desde otro objeto,
pero no implica que necesariamente puedan serlo.

**Ejercicio**: dado el _array_ bidimensional `a`:

```python
a = np.arange(25).reshape(5, 5)

a
```

    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14],
           [15, 16, 17, 18, 19],
           [20, 21, 22, 23, 24]])

Se pide:

1. Extraer el _array_ `[ 1,  7, 13, 19]`.
2. Extraer el _array_ compuesto por los números divisibles entre `3`.

**Soluciones**:

```python
a[[0, 1, 2, 3], [1, 2, 3, 4]] # alternativa: a[np.arange(4), np.arange(4)+1]
```

    array([ 1,  7, 13, 19])

Resolvamos el segundo apartado paso por paso:

```python
a % 3
```

    array([[0, 1, 2, 0, 1],
           [2, 0, 1, 2, 0],
           [1, 2, 0, 1, 2],
           [0, 1, 2, 0, 1],
           [2, 0, 1, 2, 0]], dtype=int32)

```python
a % 3 == 0
```

    array([[ True, False, False,  True, False],
           [False,  True, False, False,  True],
           [False, False,  True, False, False],
           [ True, False, False,  True, False],
           [False,  True, False, False,  True]], dtype=bool)

```python
a[a % 3 == 0]
```

    array([ 0,  3,  6,  9, 12, 15, 18, 21, 24])

### 7. Operaciones con _arrays_

En esta última sección del _notebook_ veremos dos tipos de operaciones:

- matemáticas: conservan la dimensión del _array_ (como, por ejemplo, la suma
  `+`), y
- de reducción: disminuyen la dimensión del _array_ (como, por ejemplo, la media
  `mean()`).

Las operaciones matemáticas entre _arrays_ en _NumPy_ se suelen llevar a cabo
elemento, por lo que debemos ser cautos con las dimensiones de los _arrays_
implicados en la operación, ya que en _NumPy_ no se produce ningún tipo de
"reciclaje de _arrays_" (como al que estamos habituados si utilizamos el
lenguaje de programación _R_).

```python
a
```

    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14],
           [15, 16, 17, 18, 19],
           [20, 21, 22, 23, 24]])

```python
a + 5
```

    array([[ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14],
           [15, 16, 17, 18, 19],
           [20, 21, 22, 23, 24],
           [25, 26, 27, 28, 29]])

```python
a + a
```

    array([[ 0,  2,  4,  6,  8],
           [10, 12, 14, 16, 18],
           [20, 22, 24, 26, 28],
           [30, 32, 34, 36, 38],
           [40, 42, 44, 46, 48]])

```python
a + np.arange(7)
```

    ---------------------------------------------------------------------------
    ValueError                                Traceback (most recent call last)
    <ipython-input-94-825c7dd057ef> in <module>()
    ----> 1 a + np.arange(7)

    ValueError: operands could not be broadcast together with shapes (5,5) (7,)

Estaremos en condiciones de llevar a cabo operaciones entre _arrays_ de
distintas dimensiones siempre y cuando verifique las reglas de _broadcasting_,
que podemos consultar en la siguiente
[página](https://docs.scipy.org/doc/numpy/user/basics.broadcasting.html) de la
documentación oficial. _Grosso modo_, dos dimensiones son compatibles bien
cuando son iguales, bien cuando una de ellas es `1`, y el proceso de comparación
se lleva a cabo de atrás hacia delante.

```python
a + np.arange(5)
```

    array([[ 0,  2,  4,  6,  8],
           [ 5,  7,  9, 11, 13],
           [10, 12, 14, 16, 18],
           [15, 17, 19, 21, 23],
           [20, 22, 24, 26, 28]])

```python
a.shape
```

    (5, 5)

```python
np.arange(5).shape
```

    (5,)

Así,

    a:                5 x 5
    np.arange(5):         5
    a + np.arange(5): 5 x 5

Esquema que, a primera vista, no parece satisfacer las reglas de _broadcasting_,
puesto que en la dimensión situada a la izquierda, tenemos un `5` para el
_array_ `a`, pero no hay elemento alguno para `np.arange(5)`. No obstante,
internamente, _NumPy_ aplica a `np.arange(5)` un `reshape(1, 5)` para poder
llevar a cabo la suma, quedando ahora el esquema:

    a:                             5 x 5
    np.arange(5).reshape(1, 5):    1 x 5
    a + np.arange(5).reshape(1,5): 5 x 5

Cumpliéndose así las mencionadas reglas.

Por lo que respecta a las operaciones de reducción, algunas de las más
habituales vienen dadas a través de las funciones:

- `np.sum()`
- `np.mean()`
- `np.std()`
- `np.var()`
- `np.min()`
- `np.max()`
- `np.argmin()`
- `np.argmax()`

Veamos algunos ejemplos de su aplicación a _arrays_ unidimensionales:

```python
b
```

    array([[ 0,  1,  2],
           [ 3,  4,  5],
           [ 6,  7,  8],
           [ 9, 10, 11]])

```python
b.flatten()
```

    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11])

```python
np.sum(b.flatten())
```

    66

```python
np.mean(b.flatten())
```

    5.5

```python
np.max(b.flatten())
```

    11

```python
np.argmax(b.flatten())
```

    11

Ahora bien, si trabajamos con la versión multidimensional del _array_ `b`,
podemos aplicar las operaciones de reducción por dimensiones, utilizando el
argumento `axis`. En _arrays_ bidimensionales, vamos a estar fuertemente
tentados a denominar estas operaciones bien con la coletilla "por columnas"
(para `axis=0`), bien "por filas" (para `axis=1`), pero recordemos que tal
nomenclatura se vuelve confusa cuando la dimensión del _array_ es estrictamente
superior a `2`.

```python
b
```

    array([[ 0,  1,  2],
           [ 3,  4,  5],
           [ 6,  7,  8],
           [ 9, 10, 11]])

```python
np.sum(b, axis=0) # reducción de la primera dimensión (suma por "columnas")
```

    array([18, 22, 26])

```python
np.sum(b, axis=1) # reducción de la segunda dimensión (suma por "filas")
```

    array([ 3, 12, 21, 30])

```python
np.argmax(b, axis=0)
```

    array([3, 3, 3], dtype=int64)

```python
np.argmax(b, axis=1)
```

    array([2, 2, 2, 2], dtype=int64)

Si aplicamos la función `argmax()` directamente al array bidimensional `b`,
_NumPy_ actuará internamente como hicimos nosotros anteriormente, aplicando la
función `flatten()` para luego buscar en qué posición reside el elemento de
mayor valor y devolver dicha posición. Esta información, en _arrays_
unidimensionales es bastante informativa, pero es complicada de interpretar en
_arrays_ multidimensionales. Si deseamos acceder a los índices, para cada una de
las dimensiones, donde se alcanza el mayor valor, podemos hacer uso de la
función `unravel_index()` de la siguiente manera:

```python
np.unravel_index(np.argmax(b), b.shape)
```

    (3, 2)

Finalmente, veamos cómo se propagan los elementos `nan` al llevar a cabo
operaciones matemáticas y de reducción:

```python
a = a.astype('float64')

a
```

    array([[  0.,   1.,   2.,   3.,   4.],
           [  5.,   6.,   7.,   8.,   9.],
           [ 10.,  11.,  12.,  13.,  14.],
           [ 15.,  16.,  17.,  18.,  19.],
           [ 20.,  21.,  22.,  23.,  24.]])

```python
a[2, 3] = np.nan

a
```

    array([[  0.,   1.,   2.,   3.,   4.],
           [  5.,   6.,   7.,   8.,   9.],
           [ 10.,  11.,  12.,  nan,  14.],
           [ 15.,  16.,  17.,  18.,  19.],
           [ 20.,  21.,  22.,  23.,  24.]])

```python
a + 5
```

    array([[  5.,   6.,   7.,   8.,   9.],
           [ 10.,  11.,  12.,  13.,  14.],
           [ 15.,  16.,  17.,  nan,  19.],
           [ 20.,  21.,  22.,  23.,  24.],
           [ 25.,  26.,  27.,  28.,  29.]])

```python
np.sum(a)
```

    nan

```python
np.sum(a, axis=0)
```

    array([ 50.,  55.,  60.,  nan,  70.])

```python
np.sum(a, axis=1)
```

    array([  10.,   35.,   nan,   85.,  110.])

En resumen, la librería _NumPy_ contiene un conjunto de herramientas más que
recomendable para todas aquellas personas que en su día a día utilicen el
lenguaje de programación _Python_ para llevar a cabo cualquier tipo de cálculo
numérico. Un considerable incremento en la velocidad y una gestión de memoria
más eficiente, cuya única contrapartida aparejada es requerir un buen
entendimiento de las características del problema, así como de todas las
implicaciones que los pasos para resolverlo conllevan.
