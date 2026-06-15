---
title:
    Análisis de la convocatoria de junio de 2026 de la EBAU (Ciencias Sociales)
summary: One-sentence takeaway for busy readers (also used in cards and SEO).
date: 2026-06-15
lastmod: 2026-06-15
image:
    caption: Imagen generada por Leonardo.Ai
authors:
    - me
categories:
    - Reflexiones
tags:
    - Matemáticas Aplicadas a las Ciencias Sociales II
    - EBAU
status: published
---

### Resumen

| Bloque       | Opción recomendada | Dificultad | Tiempo estimado |
| :----------- | :----------------- | :--------- | :-------------- |
| Álgebra      | A                  | Baja       | 15 - 20 minutos |
| Análisis     | B                  | Media      | 20 - 25 minutos |
| Probabilidad | Única              | Media      | 15 - 20 minutos |

### Introducción

La convocatoria de junio de 2026 se ha caracterizado, principalmente, por el
escollo que los estudiantes seguramente encontraron a la hora de abordar el
**bloque de análisis**. La primera opción de este distaba del tipo habitual de
enunciados que trabajan con funciones definidas a trozos y de no ejecutar con
fortuna el primer apartado, quedaba descartado el resto del ejercicio. En cuanto
a la segunda opción, aunque asequible si se trabajaba con calma, venía con la
etiqueta de ser un problema, con la repulsa que ello provoca habitualmente en el
alumnado.

Por otro lado, las propuestas para el **bloque de álgebra** no incluyeron
sorpresa desagradable alguna y los dos enunciados debían haber resultado, al
menos, familiares al alumnado.

En cuanto al **bloque de probabilidad**, aunque este año se anunció como novedad
el estudio de las distribuciones binomial y normal (y personalmente esperaba un
ejercicio sobre ellas), nos presentaron una actividad de probabilidad clásica
asequible, pues era similar a otras propuestas en cursos anteriores. No
obstante, aquí la trampa estribaba en el trabajo previo a los apartados, pues un
mal planteamiento de esta parte seguramente echaría por la borda completamente
el ejercicio.

A continuación, analicemos uno a uno los ejercicios propuestos en esta
convocatoria.

### Ejercicio 1. A.

Consideramos las matrices:

$$
\begin{align*} B = \begin{bmatrix} 4 & -1 \\ -2 & 3
\end{bmatrix},\quad C = \begin{bmatrix} 1 & 0 \\ 0 & 1 \\ 1 & 0
\end{bmatrix}\quad\text{y}\quad D = \begin{bmatrix} 1 & -1 \\ -2 & 0 \\ 1 & 3
\end{bmatrix}. \end{align*}
$$

a) Determina la matrix $X$ que es solución de la ecuación $$4XB + C^tD = I,$$
siendo $I$ la matriz identidad de orden $2$ y $C^t$ la traspuesta de la matriz
$C$.

b) Una matriz $A$ se dice que es idempotente si $A^2 = A$. Consideramos la
matriz:

$$
\begin{align*} F = \begin{bmatrix} 1 & 1 & 0 \\ 0 & 0 & z \end{bmatrix}.
\end{align*}
$$

Determina para qué valores de $z$ la matriz $FC$ es idempotente.

**Comentario**: en mi opinión, esta era la actividad a elegir para el bloque de
álgebra: asequible, rápida de realizar y sin trampas ocultas. Además, los
apartados de este ejercicio eran independientes entre sí, por lo que errar en
uno de ellos no producía "consecuencias de arrastre".

- En el apartado a), hallar la matriz $X$ de la ecuación matricial no era en
  absoluto complejo y requería simplemente manipulaciones algebraicas
  elementales. Si a ello añadimos que la matriz de la cual debíamos calcular su
  inversa era de orden $2$ (agilizando por tanto mucho este proceso), resulta un
  apartado sencillo.

- El apartado b) se reducía a averiguar qué valor debía tomar una variable para
  que dos matrices fuesen iguales. Este tipo de apartados, aunque raros en la
  Comunidad Valenciana, sí que es cierto que han aparecido en ocasiones
  anteriores, por lo que el alumnado debería haberlo encontrado, cuanto menos,
  familiar.

### Ejercicio 1. B.

Una granja desea crear una mezcla de fertilizante líquida utilizando dos
compuestos comerciales, NutriMax y BioGrow. Cada litro de estos compuestos
aporta diferentes cantidades de unidades de nitrógeno, fósforo y potasio. Para
que el cultivo sea productivo, los agrónomos han determinado que se deben
aplicar al terreno como mínimo $8$ unidades de nitrógeno, $6$ unidades de
fósforo y $10$ unidades de potasio. Se sabe que un litro de NutriMax contiene
$2$ unidades de nitrógeno, $1$ unidad de fósforo y $1$ unidad de potasio,
mientras que un litro de BioGrow contiene $1$ unidad de nitrógeno, $1$ unidad de
fósforo y $2$ unidades de potasio. El coste de un litro de NutriMax es de $5$
euros y el de BioGrow es de $4$ euros.

a) ¿Cuántos litros de cada producto han de utilizarse para que el coste de la
mezcla sea mínimo?

b) ¿Cuál es dicho coste mínimo?

**Comentario**: aquí tenemos un problema clásico de programación lineal, con
**región no acotada**, muy similar a algunos aparecidos en cursos anteriores.
Aunque su resolución es mecánica y no entraña dificultad oculta (salvo la
posible "sorpresa" de que tres restricciones compartan punto de intersección),
este tipo de ejercicios siempre requieren su buena inversión de tiempo para que
todo quede medianamente justificado.

### Ejercicio 2. A.

El valor de mercado de una empresa (en millones de euros) depende del tiempo $t$
(en años) y viene dado por la función:

$$
\begin{align*} g(t) = \begin{cases} t^2 +
2, & 0\leq t\leq 1, \\ \dfrac{a}{t} + 2, & 1 < t\leq 2, \\ ct + \dfrac{b}{t^2},
& 2 < t\leq 4. \end{cases} \end{align*}
$$

a) Teniendo en cuenta que la función debe ser continua y que $g'(3) = 23/27$,
determina $a$, $b$ y $c$.

b) La empresa ha tenido tres gerentes, el primero cuando $t\in[0, 1]$, el
segundo cuando $t\in(1, 2]$ y el tercero cuando $t\in(2, 4]$. Determina si con
todos los gerentes el valor de mercado ha ido creciendo.

c) Determina los máximos y mínimos absolutos y relativos para el valor de
mercado.

d) El salario de un gerente al año es cien mil veces la integral de la función
$g$ durante el período que ha estado. Calcula el salario del primer gerente.

**Comentario**: posiblemente, **el ejercicio a evitar de este bloque**. No es
nada habitual que propongan funciones a trozos con tres parámetros. Es el típico
ejercicio del que abordamos uno o dos en clase, dejamos otro par propuestos para
el alumnado, pero no hacemos demasiado hincapié en ellos. Resolver el primer
apartado requiere invertir una cantidad considerable de tiempo (plantear
condiciones de continuidad, derivar y resolver un sistema de ecuaciones).
Además, de no hallar correctamente el valor de los tres parámetros, resulta muy
complicado llevar a cabo el resto del ejercicio, pues dificulta el estudio de la
monotonía de la función y el cálculo de la integral correspondiente.

**Reflexión personal**: cuando ofreces opcionalidad en un bloque, pero planteas
una actividad como esta, no estás realmente dando opcionalidad, sino abocando a
que escojan la otra propuesta.

### Ejercicio 2. B.

Cierta empresa tecnológica ofrece servicio de almacenamiento de datos en la
nube. Sus ingresos $I$ (en unidades monetarias) dependen de la cantidad de datos
almacenados $x$ (en terabytes), siendo $I(x) = 400x$, y su función de gastos $G$
(en unidades monetarias) depende también de la cantidad de datos almacenados $x$
(en terabytes), siendo $G(x) = 4x^2 + 100$.

a) Calcula la cantidad de datos que maximiza el beneficio (ingresos menos
gastos), e indica cuál es el beneficio máximo que puede obtener la empresa.

b) El ratio ingresos / gastos mide la eficiencia financiera de la empresa.
Calcula la cantidad de datos para los cuales la eficiencia financiera de la
empresa es máxima, e indica cuál es esa eficiencia máxima.

c) Calcula

$$\int_{0}^{2}{G(x)^2dx}.$$

**Comentario**: la opción a escoger para el bloque de análisis sin lugar a
dudas. Si bien es cierto que es un problema, es bastante asequible y en línea
con enunciados aparecidos en cursos anteriores. Dos apartados para estudiar
monotonía y uno para realizar el cálculo de una sencilla integral definida.

Las única posibles pegas que encuentro son:

- Que el alumnado no recuerde el concepto de ratio. Además, no ayuda mucho que
  la pista escriba la ratio en línea haciendo uso del símbolo `/`. De haber
  mostrado dicha pista como una fracción estoy seguro que su utilidad habría
  aumentado muchos enteros.
- Que el alumnado, aunque llevemos desde 2º de la ESO haciendo hincapié en ello,
  no calcule correctamente el cuadrado de un binomio.

### Ejercicio 3.

En una empresa de pinturas se sabe que hay tres tipos de empleados: becarios,
aprendices y maestros. El $50\%$ de los empleados son becarios y el $35\%$
aprendices. Entre los becarios, el $80\%$ tiene estudios superiores y entre los
maestros tan solo el $15\%$ no tiene estudios superiores. Se sabe que el $79\%$
de los empleados de la empresa tiene estudios superiores. Seleccionamos al azar
un empleado de esta empresa.

a) Calcula la probabilidad de que el empleado seleccionado tenga estudios
superiores y sea aprendiz.

b) Si sabemos que el empleado no tiene estudios superiores, ¿cuál es la
probabilidad de que sea aprendiz?

c) Calcula la probabilidad de la intersección de los sucesos ''el empleado
seleccionado es aprendiz o becario'' y ''el empleado seleccionado tiene estudios
superiores o es aprendiz''. \end{itemize}

**Comentario**: ejercicio estándar de probabilidad clásica y de los que aparecen
varios en convocatorias de cursos anteriores. Estos son los que en clase
denomino como de tipo "$x$ y $1 - x$" y deben arrancarse haciendo un buen uso
del teorema de la probabilidad total.

- En el caso de identificar bien el tipo de problema, sus dos primeros apartados
  eran bastante asequibles.
- El tercero de ellos, en cambio, requiere algo de trabajo con álgebra de
  sucesos, pero tampoco es excesivamente complejo (al menos comparado con el
  similar que propusieron en 2025).
