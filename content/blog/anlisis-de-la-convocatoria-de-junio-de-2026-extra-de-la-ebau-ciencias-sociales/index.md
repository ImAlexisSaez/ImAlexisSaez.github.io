---
title:
    Análisis de la convocatoria de junio de 2026 (extra) de la EBAU (Ciencias
    Sociales)
summary:
    Un invitado sorpresa, en forma de logaritmo neperiano, que roba el
    protagonismo de una convocatoria que, por otro lado, resulta mucho más
    asequible que la correspondiente prueba de la mañana.
date: 2026-06-20
lastmod: 2026-06-20
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
| Álgebra      | A                  | Baja       | 20 - 25 minutos |
| Análisis     | B                  | Baja       | 20 - 25 minutos |
| Probabilidad | Única              | Baja       | 10 - 15 minutos |

### Introducción

La convocatoria de la tarde para la prueba de EBAU correspondiente a
_Matemáticas Aplicadas a las Ciencias Sociales II_ impacta a primera vista por
la presencia de un **logaritmo neperiano** en el bloque correspondiente a
análisis. Si bien es cierto que en la reunión de EBAU dejaron caer que no
debíamos perder de vista el estudio de, al menos, las funciones logarítmicas y
exponenciales, parecía una versión moderna del cuento de _Pedro y el lobo_
(siempre se dice, nunca aparece).

Al final el lobo ha hecho acto de presencia y obliga a replantearse sesiones en
el mencionado bloque para futuros cursos. En mi caso particular, admito que es
una familia de funciones a las que he dado menos cariño del que se merecían.
Aunque he abordado actividades similares a la propuesta en la opción 2. A., así
como enunciados en la parte de representación de funciones que incluían
logaritmos y exponenciales, sí que es cierto que mi enfoque con respecto a este
tema ha sido muy tangencial en comparación con el tiempo invertido en otras
familias de funciones.

Ahora bien, el resto de la convocatoria es bastante asequible, pues no se desvía
en exceso de los patrones que se observan en cursos anteriores. Todos los
ejercicios son "parecidos" a los de pruebas recientes y, además, la propuesta
para el bloque de probabilidad ha sido, por su sencillez, un soplo de aire
fresco para los ejercicios a los que nos tenían últimamente acostumbrados.

### Ejercicio 1. A.

Una empresa dedicada al desarrollo de videojuegos dispone de tres equipos de
trabajo: uno formado por $8$ personas encargadas del diseño de los personajes,
otro compuesto por $15$ personas responsables de la creación de las pantallas
del juego, y un tercero de $14$ personas dedicado al sonido y la ambientación.
La empresa desarrolla juegos de consola y juegos de ordenador. Cada juego de
consola genera un beneficio diario de $100$ euros, mientras que cada juego de
ordenador produce un beneficio diario de $90$ euros. Para la elaboración de
ambos tipos de juegos se requiere una persona del equipo de diseño de
personajes. Además, para el diseño de las pantallas de un juego de consola se
necesitan dos personas y para el de un juego de ordenador se necesita solo una.
Para el sonido y la ambientación de un juego de ordenador se necesitan dos
personas y para un juego de consola solo una. Se pide:

- a) ¿Cuántos juegos de consola y cuántos de ordenador se tienen que hacer para
  que el beneficio diario sea máximo?
- b) ¿Cuál es el beneficio diario máximo?

**Comentario**: propuesta clásica de programación lineal, con una región
factible **acotada** de cinco vértices. Tanto dicha región factible, como las
restricciones a imponer al problema, son fáciles de extraer del enunciado y no
hay ninguna sorpresa desagrable escondida. Como siempre, el único contratiempo
de este tipo de propuesta es la cantidad de tiempo a invertir para que su
resolución quede completamente justificada.

En mi opinión, a la vista del sistema de ecuaciones propuesto en la siguiente
actividad, esta **era la opción a abordar del bloque de álgebra**.

### Ejercicio 1. B.

Una empresa estudia los precios de la subscripción a las plataformas de
streaming Metfilm, Lamparx y Tuing. En el año 2023, con $1850$ euros se pudieron
contratar $40$ subscripciones a Metfilm, $50$ a Lamparx y $20$ a Tuing. En 2024,
Metfilm y Lamparx subieron la cuota $1$ euro mientras que Tuing mantuvo el
precio y, con el mismo presupuesto, se tuvieron que reducir $2$ subscripciones
de Metfilm y $3$ de Lamparx, pero se pudo mantener el número de subscripciones a
Tuing. Teniendo en cuenta que Metfilm era $5$ euros más cara que Lamparx en el
año 2023, calcula el coste de subscripción de cada compañía en cada año.

**Comentario**: un ejercicio a resolver mediante el planteamiento de un sistema
de ecuaciones en el que, como ya resulta habitual, **dos ecuaciones son
sencillas de formular y la restante es un poco más enrevesada**. El error típico
aparece al olvidar los paréntesis, lo cual nos lleva a una respuesta absurda
(coste de una subscripción por encima de los $3000$ euros, así como coste
negativo para otra subscripción).

No obstante, dominados este tipo de planteamientos (hay propuestas similares en
convocatorias recientes), sí que es cierto que es un ejercicio mucho más rápido
de resolver que el propuesto en 1. A. Además, utilizando el método de Gauss para
resolver el sistema de ecuaciones resultante, si se escoge el pivote
adecuadamente, en dos operaciones queda la matriz ampliada escalonada.

### Ejercicio 2. A.

Se considera la función:

$$
    \begin{align*}
        f(x) =
        \begin{cases}
            \ln{\left(x^2 + a\right)}, & x\leq 1,      \\
            \left(x + 1\right)^2,      & 1 < x \leq 4, \\
            5x + \dfrac{b}{x + 1},     & x > 4.
        \end{cases}
    \end{align*}
$$

- a) Estudia la continuidad de la función y determina cuáles deben ser los
  valores de $a$ y $b$ para que sea continua en todo punto.
- b) Supongamos que $a = 54$ y que $b = 25$. Determina el máximo absoluto y el
  mínimo absoluto de esta función en el intervalo $[-1, 5]$.
- c) Calcula el área de la región delimitada por esta función, el eje $OX$, la
  recta de ecuación $x = 2$ y la recta de ecuación $x = 3$.

**Comentario**: ver un logaritmo neperiano en una función a trozos seguramente
es una **invitación directa a escoger la otra propuesta** del bloque de
análisis. Además, la ecuación logarítmica a resolver, aunque es inmediata, no es
trivial, lo cual puede suponer también un importante freno para quien aborde
este ejercicio.

Sin embargo, superados ese par de escollos y recordando cómo se deriva un
logaritmo, es una propuesta muy clásica para este tipo de problemas. Existe un
poco de inquina en el apartado b), pues el valor propuesto para el parámetro $a$
es cercano al obtenido en el apartado a), pero no igual, generándose en $x = 1$
una discontinuidad que debe tenerse en cuenta a la hora de estudiar los extremos
absolutos.

Finalmente, la integral del apartado c) es un regalo, pues se trata de una
función polinómica positiva en el intervalo de integración considerado.

### Ejercicio 2. B.

Dada la función

$$
    \begin{align*}
        f(x) = \dfrac{x^2 - 2x + 4}{x^2 - 4}.
    \end{align*}
$$

Se pide:

- a) Su dominio y los puntos de corte con los ejes coordenados.
- b) Las asíntotas horizontales y verticales, si existen.
- c) Los intervalos de crecimiento y decrecimiento, y los máximos y mínimos
  locales, si existen, y el valor de estos.
- d) La representación gráfica de la función a partir de los resultados
  obtenidos en los apartados anteriores.

**Comentario**: en mi opinión, la **opción ganadora del bloque de análisis**. Un
ejercicio muy clásico de representación de una función racional (de esos que
abordamos muchos en clase y dejamos propuestos docenas de ellos). Salvando la
inversión de tiempo que este tipo de problemas requiere y que los extremos
relativos se alcanzan en puntos de coordenadas irracionales, poco más hay que
añadir para esta propuesta.

### Ejercicio 3.

Una consultoría realiza una prueba de calidad a nuevas empresas para detectar si
tienen una gestión adecuada. Tras años de estudios, se ha llegado a la
conclusión de que el $70\%$ de las empresas estudiadas están bien gestionadas y
de que, en este caso, la prueba indica que está bien gestionada en el $90\%$ de
los casos. Se sabe que la probabilidad de que la prueba detecte como bien
gestionada una empresa que está mal gestionada es del $5\%$.

- a) Calcula la probabilidad de que una empresa esté mal gestionada y la prueba
  haya indicado que está mal gestionada.
- b) Si la prueba ha indicado que una empresa está bien gestionada, ¿cuál es la
  probabilidad de que la empresa esté bien gestionada?
- c) Calcula la probabilidad de que el resultado de la prueba sea incorrecto.

**Comentario**: ejercicio clásico de **Bayes**, con un enunciado para nada
enrevesado y donde **todos sus apartados son asequibles**. Al no ver en la
convocatoria de la mañana un ejercicio de distribuciones de probabilidad,
personalmente esperaba encontrarlo aquí, pero parece que tendremos que esperar,
al menos, a las propuestas de julio.

Aquí, organizando la información adecuadamente mediante un diagrama de árbol y
poniendo atención a qué nos piden en cada apartado, está practicamente hecho. Es
más, considero que, salvando el apartado b), es una actividad que se puede
abordar perfectamente en los últimos niveles de la ESO.
