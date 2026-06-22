---
title: Breve introducción a la librería readr
summary: En este artículo exploraremos las posibilidades que nos ofrece una librería de R, readr, integrante del famoso 'tidyverso', de cara a la importación y exportación de nuestros conjuntos de datos.
date: 2018-08-14
lastmod: 2026-06-22
image:
  caption: Imagen generada por Leonardo.Ai
authors:
  - me
categories:
  - Tutoriales
tags:
  - R
  - readr
status: published
---
En este artículo exploraremos las posibilidades que nos ofrece una librería de
_R_, _readr_, integrante del famoso _tidyverso_, de cara a la importación y
exportación de nuestros conjuntos de datos.

No me ha disgustado, en absoluto, el sistema que caracteriza los cursos de la
plataforma [DataCamp](https://www.datacamp.com/home). Píldoras condensadas de
teoría acompañadas, de inmediato, por ejercicios para su aplicación directa,
ofreciendo así un enfoque para el aprendizaje bastante práctico y ameno. He
tomado algunas notas personales para el curso abierto, que en el portal aparece,
relativo a la librería
[readr](https://cran.r-project.org/web/packages/readr/index.html): "_Reading
Data into R with readr_", al que podemos acceder a través del
[siguiente enlace](https://www.datacamp.com/community/open-courses/reading-data-into-r-with-readr#gs.tdqZLKQ).

El material está desglosado en dos capítulos. En el primero de ellos,
aprenderemos diversas funciones, contenidas en este paquete, que facilitarán
enormemente la labor de importar datos utilizando el lenguaje de programación
_R_. En el segundo, el objetivo será utilizar las herramientas que la librería
pone a nuestra disposición para analizar y convertir las clases que poseen las
columnas del conjunto de datos recién importado.

_readr_ es una componente del denominado _tidyverso_ (_tidyverse_ en inglés, que
parece que siempre suena mejor), un conjunto de librerías que todo usuario de
_R_ debería si no dominar, al menos conocer, para así resolver ciertas
situaciones de la manera más sencilla posible (basta imaginar tener que hacer a
mano algunas de las tareas que paquetes como _dplyr_ o _tidyr_ llevan a cabo
para darse cuenta de este hecho).

## 1. Importando datos con _readr_

### 1.1. Archivos `.csv`

A la hora de importar conjuntos de datos en _R_, uno de los formatos más
habituales en los que hallamos información es en archivos separados por comas
(_comma separated values_), cuya extensión suele ser `.csv`. En ellos
encontramos múltiples líneas que recogen la tabla de interés, y en las cuales
los valores aparecen, de manera consecutiva, separados por el carácter `,`.

Para importar este tipo de ficheros en nuestra sesión de _R_, utilizaremos la
función `read_csv()`. Para acceder a su documentación, en primer lugar,
cargaremos la librería _readr_ (o la instalaremos si todavía no lo hemos hecho).

```r
if(!require(readr)) {install.packages("readr")}
```

    ## Loading required package: readr

```r
library(readr)
```

```r
?read_csv
```

El único argumento que hemos de pasar a esta función, de manera obligatoria, es
`file`, el nombre del archivo que pretendemos importar (o bien la ruta completa
donde éste se encuentra). El resto son opcionales, y deberían resultarnos
familiares la mayoría de ellos si hemos trabajado alguna vez con funciones del
tipo `read.table()` o `read.csv()`. Algunas de las ventajas que utilizar
`read_csv()` ofrece son:

- No convierte, automáticamente, las columnas con cadenas de caracteres a
  factores, como sí hacen por defecto las otras funciones referidas en el
  párrafo anterior.
- Reconoce ocho clases diferentes de datos (`integer`, `logical`, etc.), dejando
  el resto como cadenas de caracteres.

Pongamos a prueba su uso importando un conjunto de datos que contiene tanto los
pesos, como el tipo de alimentación, de 71 pollos. El archivo de interés es
`chickwts.csv`, por lo que empezaremos especificando la ruta para acceder a él
en el argumento `file`. Como en el segundo capítulo llevaremos a cabo algunas
acciones sobre los conjuntos de datos que aparecerán en esta sección, todos los
ficheros que importemos los almacenaremos en objetos dentro de _R_.

```r
cwts <- read_csv(file = "datasets/chickwts.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   weight = col_integer(),
    ##   feed = col_character()
    ## )

Es interesante el mensaje que aparece en la consola al ejecutar la anterior
instrucción, ya que nos informa el resultado del análisis, que la función
realiza, para inferir las clases de cada una de las columnas que componen la
tabla. Echemos un vistazo al contenido del archivo que acabamos de importar.

```r
head(cwts)
```

    ## # A tibble: 6 × 2
    ##   weight      feed
    ##    <int>     <chr>
    ## 1    179 horsebean
    ## 2    160 horsebean
    ## 3    136 horsebean
    ## 4    227 horsebean
    ## 5    217 horsebean
    ## 6    168 horsebean

```r
str(cwts)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    71 obs. of  2 variables:
    ##  $ weight: int  179 160 136 227 217 168 108 124 143 140 ...
    ##  $ feed  : chr  "horsebean" "horsebean" "horsebean" "horsebean" ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 2
    ##   .. ..$ weight: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   .. ..$ feed  : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

A primera vista, la columna `feed` posiblemente estaría mejor codificada bajo la
clase `factor` (aunque esto siempre va a depender de nuestros intereses y el uso
que tengamos en mente para esta variable). No obstante, recordemos que éste no
es el comportamiento que por defecto incorpora la función `read_csv()` (aunque
después veremos cómo declarar con antelación las clases para las columnas de un
archivo y posibilitar su lectura como factores).

Utilicemos de nuevo esta función con otro conjunto de datos, `chickwts2.csv`
(más información relativa al peso y tipo de alimentación de 18 pollos
distintos), que usaremos más adelante en este capítulo, cuando lleguemos al
apartado de exportar tablas a ficheros.

```r
cwts2 <- read_csv("datasets/chickwts2.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   weight = col_integer(),
    ##   feed = col_character()
    ## )

```r
head(cwts2)
```

    ## # A tibble: 6 × 2
    ##   weight  feed
    ##    <int> <chr>
    ## 1    309  corn
    ## 2    229  corn
    ## 3    213  corn
    ## 4    257  corn
    ## 5    244  corn
    ## 6    271  corn

```r
str(cwts2)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    18 obs. of  2 variables:
    ##  $ weight: int  309 229 213 257 244 271 243 248 257 303 ...
    ##  $ feed  : chr  "corn" "corn" "corn" "corn" ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 2
    ##   .. ..$ weight: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   .. ..$ feed  : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

### 1.2. Archivos `.tsv`

La librería _readr_ posee también una función específica para la lectura de los
archivos separados por tabulaciones, cuya extensión suele ser `.tsv` (aunque
personalmente también he visto alguno que utiliza `.tab`). Se trata de
`read_tsv()` y si accedemos a su documentación comprobaremos que su uso es
exactamente idéntico al de la función que exploramos en la sección anterior.

```r
?read_tsv
```

Investiguemos alguno de los argumentos que podemos declarar, de manera opcional,
en esta función (y, por tanto, lo que aprendamos será de utilidad también de
cara al uso de `read_csv()`). Por ejemplo, para controlar el nombre de las
columnas de la tabla que deseamos importar, el argumento `col_names` es el
indicado, y puede tomar los siguientes valores:

- `TRUE`: utiliza la información disponible en la primera línea del archivo para
  declarar los nombres de las columnas, no incluyéndolos por tanto en el
  interior de la propia tabla.
- `FALSE`: genera, de manera automática, los clásicos nombres `X1`, `X2`, `X3`,
  etc., para las columnas, y empieza a incluir la información en la tabla desde
  la primera fila.
- La última opción disponible es utilizar un vector que contenga los nombres de
  las columnas, y, como antes, desde la primera fila se insertarán los datos en
  el interior de la tabla.

Por ejemplo, importemos a continuación el fichero `salaries.tsv`. Si abrimos el
archivo con un editor de texto plano cualquiera, comprobaremos que la primera
línea no contiene los respectivos nombres para cada una de las columnas, y dado
que no conocemos de antemano qué declara cada una, usar el argumento
`col_names = FALSE` parece la opción más adecuada.

```r
salaries <- read_tsv("datasets/Salaries.tsv", col_names = FALSE)
```

    ## Parsed with column specification:
    ## cols(
    ##   X1 = col_character(),
    ##   X2 = col_character(),
    ##   X3 = col_integer(),
    ##   X4 = col_integer(),
    ##   X5 = col_character(),
    ##   X6 = col_integer()
    ## )

```r
head(salaries)
```

    ## # A tibble: 6 × 6
    ##          X1    X2    X3    X4    X5     X6
    ##       <chr> <chr> <int> <int> <chr>  <int>
    ## 1      Prof     B    19    18  Male 139750
    ## 2      Prof     B    20    16  Male 173200
    ## 3  AsstProf     B     4     3  Male  79750
    ## 4      Prof     B    45    39  Male 115000
    ## 5      Prof     B    40    41  Male 141500
    ## 6 AssocProf     B     6     6  Male  97000

```r
str(salaries)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    397 obs. of  6 variables:
    ##  $ X1: chr  "Prof" "Prof" "AsstProf" "Prof" ...
    ##  $ X2: chr  "B" "B" "B" "B" ...
    ##  $ X3: int  19 20 4 45 40 6 30 45 21 18 ...
    ##  $ X4: int  18 16 3 39 41 6 23 45 20 18 ...
    ##  $ X5: chr  "Male" "Male" "Male" "Male" ...
    ##  $ X6: int  139750 173200 79750 115000 141500 97000 175000 147765 119250 129000 ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 6
    ##   .. ..$ X1: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ X2: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ X3: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   .. ..$ X4: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   .. ..$ X5: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ X6: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

En la llamada a la función `read_tsv()`, hemos recibido por consola el siguiente
mensaje:

    Parsed with column specification:
    cols(
      X1 = col_character(),
      X2 = col_character(),
      X3 = col_integer(),
      X4 = col_integer(),
      X5 = col_character(),
      X6 = col_integer()
    )

Como ya comentábamos en la sección anterior, esta información nos indica la
clase que la función `read_tsv()` ha inferido para todas y cada una de las
columnas contenidas en el archivo. De hecho, este comportamiento no se restringe
únicamente a las funciones `read_csv()` y `read_tsv()`, sino a todas las
implementadas en la librería _readr_ cuya empresa es, precisamente, la lectura
de ficheros de datos.

A través del argumento `col_types` tenemos cierto control sobre la declaración
de la clase de las columnas, utilizando funciones predefinidas del estilo
`col_*()` (como `col_integer()`, `col_character()`, etc.). La forma de usar este
argumento es muy sencilla: simplemente tenemos que escribir `col_types = cols()`
e incluir en el interior de `cols()` los nombres de las columnas y la clase que
deseamos posean (siguiendo el estilo de, por ejemplo, el mensaje por consola que
mostrábamos arriba).

Una función que nos puede interesar, en este momento, es `col_skip()`, que le
indica a _R_ que omita una determinada columna a la hora de importar la
información de un archivo de datos. Veamos su uso con más detalle a través de un
ejemplo. Supongamos que sólo estamos interesados en las columnas primera, quinta
y sexta del anterior fichero de datos. Así pues, no tendríamos más que escribir:

```r
salaries <- read_tsv("datasets/Salaries.tsv", col_names = FALSE,
                     col_types = cols(
                         X2 = col_skip(),
                         X3 = col_skip(),
                         X4 = col_skip()
                     ))
```

```r
head(salaries)
```

    ## # A tibble: 6 × 3
    ##          X1    X5     X6
    ##       <chr> <chr>  <int>
    ## 1      Prof  Male 139750
    ## 2      Prof  Male 173200
    ## 3  AsstProf  Male  79750
    ## 4      Prof  Male 115000
    ## 5      Prof  Male 141500
    ## 6 AssocProf  Male  97000

```r
str(salaries)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    397 obs. of  3 variables:
    ##  $ X1: chr  "Prof" "Prof" "AsstProf" "Prof" ...
    ##  $ X5: chr  "Male" "Male" "Male" "Male" ...
    ##  $ X6: int  139750 173200 79750 115000 141500 97000 175000 147765 119250 129000 ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 6
    ##   .. ..$ X1: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ X2: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_skip" "collector"
    ##   .. ..$ X3: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_skip" "collector"
    ##   .. ..$ X4: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_skip" "collector"
    ##   .. ..$ X5: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ X6: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

### 1.3. Archivos `.csv` (formato europeo)

En muchos países de este continente, usamos la coma como separador decimal, de
manera que los archivos separados por comas, en realidad, terminan siendo
separados por el símbolo `;` (punto y coma). Por curiosidad, puedes probar a
crear una tabla sencilla en, por ejemplo, _Excel_ y exportarla como archivo
separado por comas, para luego abrir el archivo con un editor de texto plano y
verificar que, efectivamente, los valores están separados por `;` (en realidad
este comportamiento se puede modificar desde las opciones de formato del sistema
operativo, pero no entraremos en ese tipo de detalles).

En previsión de esta particularidad, la librería _readr_ pone a nuestra
disposición la función `read_csv2()`, que identifica el símbolo `;` como
separador de valores, mientras que `,` queda como separador decimal. Obviando
esta salvedad, su uso es idéntico al de las funciones presentadas en los
anteriores apartados.

Tomemos ahora el archivo `trees.csv` (que contiene información sobre la
circunferencia, la altura y el volumen de cerezos negros), el cual viene dado en
el formato al que nos estamos refiriendo aquí, e importémoslo directamente con
la función `read_csv()`, en lugar de con `read_csv2()`, para ver qué sucede.

```r
trees_wrong <- read_csv("datasets/trees.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   `Girth";"Height";"Volume` = col_character()
    ## )

    ## Warning: 30 parsing failures.
    ## row col  expected    actual
    ##   1  -- 1 columns 3 columns
    ##   2  -- 1 columns 3 columns
    ##   3  -- 1 columns 3 columns
    ##   4  -- 1 columns 3 columns
    ##   5  -- 1 columns 3 columns
    ## ... ... ......... .........
    ## See problems(...) for more details.

En favor de la función `read_csv()` hay que decir que, al menos, nos indica la
existencia de ciertos problemas, o situaciones inesperadas, durante la
importación del archivo. De todas formas, podemos observar cómo ha procedido a
generar una tabla con una única columna, en lugar de las correspondientes tres
que hubiese sido lo adecuado en esta ocasión. Comprobemos qué contiene el objeto
`trees_wrong`.

```r
dim(trees_wrong)
```

    ## [1] 31  1

```r
head(trees_wrong)
```

    ## # A tibble: 6 × 1
    ##   `Girth";"Height";"Volume`
    ##                       <chr>
    ## 1                         8
    ## 2                         8
    ## 3                         8
    ## 4                        10
    ## 5                        10
    ## 6                        10

```r
str(trees_wrong)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    31 obs. of  1 variable:
    ##  $ Girth";"Height";"Volume: chr  "8" "8" "8" "10" ...
    ##  - attr(*, "problems")=Classes 'tbl_df', 'tbl' and 'data.frame': 30 obs. of  4 variables:
    ##   ..$ row     : int  1 2 3 4 5 6 7 8 9 10 ...
    ##   ..$ col     : chr  NA NA NA NA ...
    ##   ..$ expected: chr  "1 columns" "1 columns" "1 columns" "1 columns" ...
    ##   ..$ actual  : chr  "3 columns" "3 columns" "3 columns" "3 columns" ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 1
    ##   .. ..$ Girth";"Height";"Volume: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

Veamos ahora el resultado que obtenemos al utilizar la función `read_csv2()`.

```r
trees <- read_csv2("datasets/trees.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   Girth = col_double(),
    ##   Height = col_integer(),
    ##   Volume = col_double()
    ## )

```r
dim(trees)
```

    ## [1] 31  3

```r
head(trees)
```

    ## # A tibble: 6 × 3
    ##   Girth Height Volume
    ##   <dbl>  <int>  <dbl>
    ## 1   8.3     70   10.3
    ## 2   8.6     65   10.3
    ## 3   8.8     63   10.2
    ## 4  10.5     72   16.4
    ## 5  10.7     81   18.8
    ## 6  10.8     83   19.7

```r
str(trees)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    31 obs. of  3 variables:
    ##  $ Girth : num  8.3 8.6 8.8 10.5 10.7 10.8 11 11 11.1 11.2 ...
    ##  $ Height: int  70 65 63 72 81 83 66 75 80 75 ...
    ##  $ Volume: num  10.3 10.3 10.2 16.4 18.8 19.7 15.6 18.2 22.6 19.9 ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 3
    ##   .. ..$ Girth : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ Height: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   .. ..$ Volume: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

### 1.4. Archivos con ancho de columna fijo

En ocasiones, el formato en el que encontramos los archivos de datos es similar
al mostrado en _R_ a la hora de imprimir en consola un `data.frame`. Es decir,
cada columna posee un total de caracteres fijos y éstas se separan usando
espacios en blanco (que también se utilizan para rellenar aquellos valores cuya
longitud es menor que la correspondiente a su columna).

El archivo `names.txt` constituye un ejemplo de lo comentado en el párrafo
anterior. En su interior encontramos los nombres de ciertos personajes famosos,
el estado donde supuestamente residen y, como no podía ser de otra manera, sus
falsos números de teléfono.

La función adecuada para lidiar con estos casos es `read_table()`, cuya
documentación ofrece un listado de argumentos bastante familiares a estas
alturas.

```r
?read_table
```

Importemos pues el fichero `names.txt`, declarando adecuadamente los nombres
para las columnas utilizando el parámetro `col_names`.

```r
names <- read_table("datasets/names.txt",
                    col_names = c("name", "state", "phone"))

names
```

    ## # A tibble: 6 × 3
    ##                  name        state        phone
    ##                 <chr>        <chr>        <chr>
    ## 1       Oprah Winfrey         null 800-555-4111
    ## 2         Walt Disney      Florida 407-555-4341
    ## 3       Michael Scott Pennsylvania 570-555-2301
    ## 4        Cosmo Kramer     New York 212-555-9337
    ## 5 Rutherford B. Hayes         Ohio 220-555-1388
    ## 6   Chester A. Arthur      Vermont 802-555-8383

```r
str(names)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    6 obs. of  3 variables:
    ##  $ name : chr  "Oprah Winfrey" "Walt Disney" "Michael Scott" "Cosmo Kramer" ...
    ##  $ state: chr  "null" "Florida" "Pennsylvania" "New York" ...
    ##  $ phone: chr  "800-555-4111" "407-555-4341" "570-555-2301" "212-555-9337" ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 3
    ##   .. ..$ name : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ state: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ phone: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

Aprovechemos este particular ejemplo para ilustrar el tratamiento de los valores
perdidos con las funciones de la librería _readr_ dedicadas a importar archivos
de datos. Por defecto, sólo se reconoce `NA` como valor perdido, pero, en esta
ocasión, si nos fijamos en la primera fila de la tabla, han optado por usar
`null` para registrar la ausencia de información para ciertos atributos
concretos.

No supone esto demasiado inconveniente, puesto que utilizando el parámetro `na`
podemos declarar, mediante un vector, qué cadenas de texto deben ser
consideradas como valores perdidos (y automáticamente pasarán a ser `NA` en el
objeto que creemos en _R_). Por defecto, `na = "NA"`, de manera que simplemente
tenemos que declarar `na = c("NA", "null")` en nuestro caso.

```r
names2 <- read_table("datasets/names.txt",
                     col_names = c("name", "state", "phone"),
                     na = c("NA", "null"))
head(names2)
```

    ## # A tibble: 6 × 3
    ##                  name        state        phone
    ##                 <chr>        <chr>        <chr>
    ## 1       Oprah Winfrey         <NA> 800-555-4111
    ## 2         Walt Disney      Florida 407-555-4341
    ## 3       Michael Scott Pennsylvania 570-555-2301
    ## 4        Cosmo Kramer     New York 212-555-9337
    ## 5 Rutherford B. Hayes         Ohio 220-555-1388
    ## 6   Chester A. Arthur      Vermont 802-555-8383

### 1.5. Archivos de texto

Es posible que nuestro interés no se centre tanto en examinar tablas de datos,
como texto propiamente dicho, sobretodo ahora que tan de moda está el análisis
de sentimiento (para estudiar opiniones, discursos, etc.). La librería _readr_
pone a nuestra disposición un par de funciones que nos serán útiles en estos
casos:

- `read_lines()`: devuelve un vector de cadenas de texto, donde cada elemento
  recoge una línea del archivo de datos original.

```r
?read_lines
```

- `read_file()`: devuelve un vector de dimensión unitaria que contiene el texto
  completo del archivo de datos original, y donde los saltos de línea se
  representan utilizando `\n`.

```r
?read_file
```

En el fichero `tweets.txt` encontramos algunos _tuits_ correspondientes a la
cuenta `@RealCarrotFacts` (puedes comprobar que, efectivamente, existe dicha
cuenta y que es un tanto curiosa). Procedamos a importar su contenido utilizando
ambas funciones, para así apreciar de manera práctica la diferencia.

```r
tweets <- read_lines("datasets/tweets.txt")
tweets
```

    ## [1] "carrots  can be eat by most people"
    ## [2] "On predisents day we honor the big US man himself: Aberham Liclon.   Tall, skinny, dry, and cruncy - he was america's carrot"
    ## [3] "knock knoc who is there? yup: carosot   ( joke )"
    ## [4] "it is 2016 time for a carot emoji   please!"
    ## [5] "when life give you lemnos ,  have a carrot"
    ## [6] "If you squent your eyes real hard a football  look like  a dry brown carrot   Honestly"

```r
str(tweets)
```

    ##  chr [1:6] "carrots  can be eat by most people" ...

```r
tweets_all <- read_file("datasets/tweets.txt")
tweets_all
```

    ## [1] "carrots  can be eat by most people\nOn predisents day we honor the big US man himself: Aberham Liclon.   Tall, skinny, dry, and cruncy - he was america's carrot\nknock knoc who is there? yup: carosot   ( joke )\nit is 2016 time for a carot emoji   please!\nwhen life give you lemnos ,  have a carrot\nIf you squent your eyes real hard a football  look like  a dry brown carrot   Honestly"

```r
str(tweets_all)
```

    ##  chr "carrots  can be eat by most people\nOn predisents day we honor the big US man himself: Aberham Liclon.   Tall, skinny, dry, and"| __truncated__

### 1.6. Escribiendo archivos `.csv` y `.tsv`

Una vez hemos importado nuestro conjunto de datos de interés, y realizamos sobre
él ciertas manipulaciones, es bastante probable que deseemos almacenar el
resultado en un archivo para su posterior uso y disfrute. La librería _readr_
contiene varias funciones del estilo `write_*()` (por ejemplo, `write_csv()` o
`write_tsv()`) orientadas a satisfacer esta necesidad, y que se caracterizan por
un par de detalles realmente interesantes:

- A diferencia de funciones como `write.csv()`, no añaden por defecto los
  números (o nombres) de las filas al archivo exportado, lo cual suele ser el
  comportamiento deseado en la mayoría de ocasiones.
- El parámetro `col_names` adopta como valor el contrario al que posee `append`,
  manera de actuar que tiene todo el sentido del mundo. Si decidimos continuar
  añadiendo datos a un archivo que previamente hemos exportado, declararemos
  `append = TRUE` y, por tanto, no aparecerán de nuevo, y en mitad del fichero,
  los nombres de las columnas.

Veamos este último punto con mayor detalle a través de un ejemplo. En primer
lugar, exportaremos a un archivo separado por comas el objeto `cwts` que
generamos en una sección anterior. A Continuación, añadiremos al mencionado
archivo el contenido del objeto `cwts2`.

```r
write_csv(cwts, "chickwts.csv")

write_csv(cwts2, "chickwts.csv", append=TRUE)
```

Procedamos ahora a importar el fichero recién generado y examinémoslo.

```r
cwts3 <- read_csv("chickwts.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   weight = col_integer(),
    ##   feed = col_character()
    ## )

```r
head(cwts3)
```

    ## # A tibble: 6 × 2
    ##   weight      feed
    ##    <int>     <chr>
    ## 1    179 horsebean
    ## 2    160 horsebean
    ## 3    136 horsebean
    ## 4    227 horsebean
    ## 5    217 horsebean
    ## 6    168 horsebean

```r
str(cwts3)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    89 obs. of  2 variables:
    ##  $ weight: int  179 160 136 227 217 168 108 124 143 140 ...
    ##  $ feed  : chr  "horsebean" "horsebean" "horsebean" "horsebean" ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 2
    ##   .. ..$ weight: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   .. ..$ feed  : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

### 1.7. Escribiendo archivos `.rds`

Es posible que estemos interesados en exportar no solamente los valores de una
tabla, sino ciertos _metadatos_ asociados a ella, como pueden ser, por ejemplo,
las clases de las diferentes columnas que la compongan. No es fácil incorporar
este tipo de información a un archivo separado por comas o tabulaciones, por lo
que la librería _readr_ nos ofrece la posibilidad de exportar un objeto completo
de _R_ a través de la función `write_rds()`.

```r
?write_rds
```

La mencionada función no es más que un _wrapper_ (desconozco la traducción a
español de este término) de la función `saveRDS()`, con la única particularidad
de que, por defecto, no comprime el archivo resultante (aunque este
comportamiento se puede definir a través del parámetro `compress`).

Ilustremos su aplicación mediante un ejemplo. Exportaremos el objeto `trees` que
generamos en una sección anterior utilizando la función `write_rds()`, para a
continuación importarlo inmediatamente con `read_rds()` y asignarlo a `trees2`.
Finalmente, compararemos si ambos objetos son idénticos, empleando para ello la
función `identical()`.

```r
write_rds(trees, "trees.rds")

trees2 <- read_rds("trees.rds")

identical(trees, trees2)
```

    ## [1] TRUE

## 2. Analizando datos con readr

### 2.1. Modificando la clase de las columnas

Aunque las funciones para importar archivos de datos que pone a nuestra
disposición la librería _readr_, realizan una labor estupenda a la hora de
inferir la clase de cada una de las columnas que componen una tabla, su
comportamiento dista de ser perfecto. Esto se traducirá, seguramente, en la
necesidad de llevar a cabo ciertas modificaciones, sobre las mencionadas clases,
para algunos casos concretos.

Para ello, la función adecuada a utilizar es `type_convert()`, que incorpora el
conocido argumento `col_types` en su llamada. Ilustremos su uso y aprovechemos,
además, para emplear la notación abreviada para los tipos de datos que **readr**
ofrece. Tomaremos el objeto `trees` y declararemos todas sus columnas de tipo
`numeric`.

```r
?type_convert
```

```r
trees3 <- type_convert(trees,
                       col_types = cols(
                           Girth  = "d",
                           Height = "d",
                           Volume = "d")
                       )
```

    ## Warning: The following named parsers don't match the column names: Girth,
    ## Height, Volume

```r
str(trees3)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    31 obs. of  3 variables:
    ##  $ Girth : num  8.3 8.6 8.8 10.5 10.7 10.8 11 11 11.1 11.2 ...
    ##  $ Height: int  70 65 63 72 81 83 66 75 80 75 ...
    ##  $ Volume: num  10.3 10.3 10.2 16.4 18.8 19.7 15.6 18.2 22.6 19.9 ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 3
    ##   .. ..$ Girth : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ Height: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   .. ..$ Volume: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

_Nota_: aunque la función se utiliza tal y como está descrito (e incluso en el
propio curso de _DataCamp_ ésta sería la respuesta adecuada), he encontrado
algún tipo de problema al emplear `type_convert()`, de forma que no reconoce los
nombres de las columnas.

### 2.2. Transformando columnas de texto en factores

Una de las características de las funciones de importación de datos de la
librería _readr_ es que no interpretan, de manera automática, las columnas que
poseen cadenas de texto como factores. No obstante, en ocasiones nos puede
interesar que la clase de algunas columnas sea `factor`.

En estas situaciones, podemos utilizar la función `parse_factor()` sobre las
columnas del objeto recién importado que buscamos sean factores, especificando,
si queremos, los niveles que adoptan.

```r
?parse_factor
```

Ilustremos su uso mediante un ejemplo. En el objeto `salaries`, que generamos en
el capítulo anterior, la primera columna, `X1`, contiene el tipo de profesor
universitario; mientras que la segunda, `X5`, hace referencia al sexo de la
persona. Transformemos ambas en factores.

```r
salaries$X1 <- parse_factor(salaries$X1,
                            levels = c("Prof", "AsstProf", "AssocProf"))

salaries$X5 <- parse_factor(salaries$X5,
                            levels = c("Male", "Female"))
```

```r
head(salaries)
```

    ## # A tibble: 6 × 3
    ##          X1     X5     X6
    ##      <fctr> <fctr>  <int>
    ## 1      Prof   Male 139750
    ## 2      Prof   Male 173200
    ## 3  AsstProf   Male  79750
    ## 4      Prof   Male 115000
    ## 5      Prof   Male 141500
    ## 6 AssocProf   Male  97000

```r
str(salaries)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    397 obs. of  3 variables:
    ##  $ X1: Factor w/ 3 levels "Prof","AsstProf",..: 1 1 2 1 1 3 1 1 1 1 ...
    ##  $ X5: Factor w/ 2 levels "Male","Female": 1 1 1 1 1 1 1 1 1 2 ...
    ##  $ X6: int  139750 173200 79750 115000 141500 97000 175000 147765 119250 129000 ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 6
    ##   .. ..$ X1: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ X2: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_skip" "collector"
    ##   .. ..$ X3: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_skip" "collector"
    ##   .. ..$ X4: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_skip" "collector"
    ##   .. ..$ X5: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ X6: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

### 2.3. Trabajando con fechas

Si una de las columnas del archivo de datos viene dada en la forma `YYYY-MM-DD`,
las funciones de importación de la librería _readr_ la interpretarán
automáticamente como de tipo `Date` (fecha).

No obstante, si en la tabla están presentes algunos valores que son fechas y no
se ajustan a la estructura comentada arriba, a través de la función
`parse_date()` (y su argumento `format`) podemos lidiar con esta situación.

```r
?parse_date
```

Consideremos el siguiente ejemplo: en el archivo `weather.csv`, donde se recogen
distintos indicadores relacionados con el clima, la columna `date` contiene la
fecha en el formato "mes/día/año". Con esta información, procedamos a
transformar la clase de la columna de manera oportuna.

```r
weather <- read_csv("datasets/weather.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   origin = col_character(),
    ##   date = col_character(),
    ##   hour = col_integer(),
    ##   temp = col_double(),
    ##   dewp = col_double(),
    ##   humid = col_double(),
    ##   wind_dir = col_integer(),
    ##   wind_speed = col_double(),
    ##   wind_gust = col_double(),
    ##   precip = col_double(),
    ##   pressure = col_double(),
    ##   visib = col_double()
    ## )

```r
head(weather)
```

    ## # A tibble: 6 × 12
    ##   origin       date  hour  temp  dewp humid wind_dir wind_speed wind_gust
    ##    <chr>      <chr> <int> <dbl> <dbl> <dbl>    <int>      <dbl>     <dbl>
    ## 1    EWR 12/22/2013     9 64.94 60.98 87.00      190   13.80936 15.891535
    ## 2    EWR  7/23/2013     6 77.00 75.20 94.19      140    4.60312  5.297178
    ## 3    EWR 10/30/2013    11 44.96 35.96 70.52        0    0.00000  0.000000
    ## 4    EWR 12/25/2013    21 28.04  6.08 38.69      250    3.45234  3.972884
    ## 5    EWR  6/18/2013     9 66.02 62.06 87.05       10    5.75390  6.621473
    ## 6    EWR   5/5/2013    15 57.92 37.04 45.58       NA    4.60312  5.297178
    ## # ... with 3 more variables: precip <dbl>, pressure <dbl>, visib <dbl>

```r
str(weather)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    500 obs. of  12 variables:
    ##  $ origin    : chr  "EWR" "EWR" "EWR" "EWR" ...
    ##  $ date      : chr  "12/22/2013" "7/23/2013" "10/30/2013" "12/25/2013" ...
    ##  $ hour      : int  9 6 11 21 9 15 11 11 15 20 ...
    ##  $ temp      : num  64.9 77 45 28 66 ...
    ##  $ dewp      : num  60.98 75.2 35.96 6.08 62.06 ...
    ##  $ humid     : num  87 94.2 70.5 38.7 87 ...
    ##  $ wind_dir  : int  190 140 0 250 10 NA 310 0 350 290 ...
    ##  $ wind_speed: num  13.81 4.6 0 3.45 5.75 ...
    ##  $ wind_gust : num  15.89 5.3 0 3.97 6.62 ...
    ##  $ precip    : num  0.01 0.01 0 0 0 0 0 0 0 0 ...
    ##  $ pressure  : num  1010 NA 1026 1033 1012 ...
    ##  $ visib     : num  10 4 10 10 10 10 10 0.25 10 10 ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 12
    ##   .. ..$ origin    : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ date      : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ hour      : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   .. ..$ temp      : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ dewp      : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ humid     : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ wind_dir  : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   .. ..$ wind_speed: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ wind_gust : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ precip    : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ pressure  : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ visib     : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

```r
weather$date <- parse_date(weather$date,
                           format = "%m/%d/%Y")
```

```r
head(weather)
```

    ## # A tibble: 6 × 12
    ##   origin       date  hour  temp  dewp humid wind_dir wind_speed wind_gust
    ##    <chr>     <date> <int> <dbl> <dbl> <dbl>    <int>      <dbl>     <dbl>
    ## 1    EWR 2013-12-22     9 64.94 60.98 87.00      190   13.80936 15.891535
    ## 2    EWR 2013-07-23     6 77.00 75.20 94.19      140    4.60312  5.297178
    ## 3    EWR 2013-10-30    11 44.96 35.96 70.52        0    0.00000  0.000000
    ## 4    EWR 2013-12-25    21 28.04  6.08 38.69      250    3.45234  3.972884
    ## 5    EWR 2013-06-18     9 66.02 62.06 87.05       10    5.75390  6.621473
    ## 6    EWR 2013-05-05    15 57.92 37.04 45.58       NA    4.60312  5.297178
    ## # ... with 3 more variables: precip <dbl>, pressure <dbl>, visib <dbl>

```r
str(weather)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    500 obs. of  12 variables:
    ##  $ origin    : chr  "EWR" "EWR" "EWR" "EWR" ...
    ##  $ date      : Date, format: "2013-12-22" "2013-07-23" ...
    ##  $ hour      : int  9 6 11 21 9 15 11 11 15 20 ...
    ##  $ temp      : num  64.9 77 45 28 66 ...
    ##  $ dewp      : num  60.98 75.2 35.96 6.08 62.06 ...
    ##  $ humid     : num  87 94.2 70.5 38.7 87 ...
    ##  $ wind_dir  : int  190 140 0 250 10 NA 310 0 350 290 ...
    ##  $ wind_speed: num  13.81 4.6 0 3.45 5.75 ...
    ##  $ wind_gust : num  15.89 5.3 0 3.97 6.62 ...
    ##  $ precip    : num  0.01 0.01 0 0 0 0 0 0 0 0 ...
    ##  $ pressure  : num  1010 NA 1026 1033 1012 ...
    ##  $ visib     : num  10 4 10 10 10 10 10 0.25 10 10 ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 12
    ##   .. ..$ origin    : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ date      : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ hour      : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   .. ..$ temp      : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ dewp      : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ humid     : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ wind_dir  : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_integer" "collector"
    ##   .. ..$ wind_speed: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ wind_gust : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ precip    : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ pressure  : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   .. ..$ visib     : list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_double" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

### 2.4. Trabajando con números

Es posible que la tabla que deseamos importar contenga, entre sus valores,
expresiones numéricas asociadas cantidades monetarias, de manera que incluyan
caracteres no numéricos (como el símbolo de la moneda o diversos separadores de
millares, por ejemplo).

En estos casos, la función a utilizar, de la librería _readr_, es
`parse_number()`, que omite los mencionados caracteres no numéricos presentes en
los valores de una columna.

```r
?parse_number
```

En el archivo `debt.csv` tenemos datos relacionados con la deuda nacional de
_Estados Unidos_ para ciertos años. Importemos el archivo y examinemos su
contenido.

```r
debt <- read_csv("datasets/national_debt.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   V1 = col_character(),
    ##   V2 = col_character()
    ## )

```r
head(debt)
```

    ## # A tibble: 6 × 2
    ##        V1                     V2
    ##     <chr>                  <chr>
    ## 1 9/30/15 $18,150,617,666,484.30
    ## 2 9/30/14 $17,824,071,380,733.80
    ## 3 9/30/13 $16,738,183,526,697.30
    ## 4 9/30/12 $16,066,241,407,385.80
    ## 5 9/30/11 $14,790,340,328,557.10
    ## 6 9/30/10 $13,561,623,030,891.70

```r
str(debt)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    16 obs. of  2 variables:
    ##  $ V1: chr  "9/30/15" "9/30/14" "9/30/13" "9/30/12" ...
    ##  $ V2: chr  "$18,150,617,666,484.30" "$17,824,071,380,733.80" "$16,738,183,526,697.30" "$16,066,241,407,385.80" ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 2
    ##   .. ..$ V1: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ V2: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

Apliquemos ahora la función `parse_number()` a la segunda columna de la tabla.

```r
debt$V2 <- parse_number(debt$V2)
head(debt)
```

    ## # A tibble: 6 × 2
    ##        V1           V2
    ##     <chr>        <dbl>
    ## 1 9/30/15 1.815062e+13
    ## 2 9/30/14 1.782407e+13
    ## 3 9/30/13 1.673818e+13
    ## 4 9/30/12 1.606624e+13
    ## 5 9/30/11 1.479034e+13
    ## 6 9/30/10 1.356162e+13

```r
str(debt)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    16 obs. of  2 variables:
    ##  $ V1: chr  "9/30/15" "9/30/14" "9/30/13" "9/30/12" ...
    ##  $ V2: num  1.82e+13 1.78e+13 1.67e+13 1.61e+13 1.48e+13 ...
    ##  - attr(*, "spec")=List of 2
    ##   ..$ cols   :List of 2
    ##   .. ..$ V1: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   .. ..$ V2: list()
    ##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
    ##   ..$ default: list()
    ##   .. ..- attr(*, "class")= chr  "collector_guess" "collector"
    ##   ..- attr(*, "class")= chr "col_spec"

### 2.5. Accediendo a los metadatos de un archivo

En ocasiones, puede resultar de utilidad tener una idea previa de cómo las
funciones de la librería _readr_ van a interpretar las columnas de un conjunto
de datos antes de importarlo. De esta forma, en el caso de que las clases
inferidas no sean las adecuadas, podemos optar por declarar el tipo de alguna de
ellas con antelación.

Con tal fin existen las funciones `spec_csv()` y `spec_tsv()`, para los archivos
separados por comas y por tabulaciones, respectivamente. En el caso de tener que
trabajar con otro tipo de ficheros (por ejemplo, `.csv` en formato europeo),
usaremos `spec_delim()`, especificando el símbolo que hace las veces de
separador de columnas en el archivo de datos.

```r
?spec_csv
```

Por ejemplo, retomemos el primer ejemplo de este documento, aquel que trabajaba
con el archivo `chickwts.csv`, que contenía información relativa al peso y tipo
de alimentación de ciertos pollos. Veamos cuáles serían las clases que la
función `read_csv()` inferiría para sus columnas a la hora de importarlo.

```r
spec_csv("datasets/chickwts.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   weight = col_integer(),
    ##   feed = col_character()
    ## )

    ## cols(
    ##   weight = col_integer(),
    ##   feed = col_character()
    ## )
