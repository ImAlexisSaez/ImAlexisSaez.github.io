---
title: Configurando el tema Beautiful Hugo (II)
summary: "Lección 6: finalizamos la edición del archivo de configuración del tema Beautiful Hugo."
date: 2018-08-09
lastmod: 2026-06-20
image:
  caption: Imagen generada por Leonardo.Ai
authors:
  - me
categories:
  - Tutoriales
tags:
  - Beautiful Hugo
  - Hugo
  - Metablog
status: published
---
Nos quedamos, en la
[anterior entrada](/blog/configurando-el-tema-beautiful-hugo-i/) catalogada bajo
la etiqueta [Metablog](/tags/metablog/), a falta de revisar la parte final del
archivo de configuración `config.toml`. Terminemos pues de echarle un vistazo a
dicho fichero en este artículo.

Al finalizar la personalización de los parámetros básicos del sitio web, se
asomaba ante nosotros el siguiente, y muy extraño, bloque de código:

```toml
#[[Params.bigimg]]
#  src = "img/triangle.jpg"
#  desc = "Triangle"
#[[Params.bigimg]]
#  src = "img/sphere.jpg"
#  desc = "Sphere"
#  # position: see values of CSS background-position.
#  position = "center top"
#[[Params.bigimg]]
#  src = "img/hexagon.jpg"
#  desc = "Hexagon"
```

Nada intuitivo su contenido y carente por completo de comentarios, hecho nada
halagüeño. Sin embargo, basta que experimentemos un poco con la anteriores
líneas para comprobar que esta sección del archivo `config.toml` es la dedicada
a gestionar la aparición de un carrusel de imágenes en la página web de acceso,
situándolo justo detrás del título.

Conviene que le echemos un vistazo a la entrada que aparece en el propio blog de
ejemplo del tema _Beautiful Hugo_ hablando de la gestión de imágenes de
cabecera. En el caso de haber varias declaradas, estas rotan cada diez segundos.
Por otro lado, tenemos a nuestra disposición los siguientes parámetros de
configuración:

- `src`: ruta que apunta a la ubicación de la imagen de cabecera.
- `desc`: parámetro opcional que nos permite incorporar un pequeño texto sobre
  la imagen, a modo de pie de figura.

En mi caso, tras navegar un rato por [Unsplash](https://unsplash.com/),
descargué fotografías hasta componer un carrusel de cinco imágenes a las que no
incorporé pie de figura alguno. Por tanto, el anterior bloque de código me ha
quedado como sigue:

```toml
#
# Configuración del carrusel de imágenes de la página de inicio
#
[[Params.bigimg]]
  src = "img/homepage-cabecera-01.jpg"
[[Params.bigimg]]
  src = "img/homepage-cabecera-02.jpg"
[[Params.bigimg]]
  src = "img/homepage-cabecera-03.jpg"
[[Params.bigimg]]
  src = "img/homepage-cabecera-04.jpg"
[[Params.bigimg]]
  src = "img/homepage-cabecera-05.jpg"
```

Desvelado el anterior misterio, continuemos con la revisión del archivo
`config.toml`. El siguiente bloque de instrucciones hace referencia a los datos
sobre el autor del sitio web (nombre, correo electrónico, etc.). Nos permite,
además, configurar una amplia gama de enlaces a nuestras cuentas de redes
sociales para así facilitar la conexión entre personas. Originalmente, dicho
bloque presenta el siguiente aspecto:

```toml
[Author]
  name = "Some Person"
  website = "yourwebsite.com"
  email = "youremail@domain.com"
  facebook = "username"
  googleplus = "+username" # or xxxxxxxxxxxxxxxxxxxxx
  github = "username"
  gitlab = "username"
  bitbucket = "username"
  twitter = "username"
  reddit = "username"
  linkedin = "username"
  xing = "username"
  stackoverflow = "users/XXXXXXX/username"
  snapchat = "username"
  instagram = "username"
  youtube = "user/username" # or channel/channelname
  soundcloud = "username"
  spotify = "username"
  bandcamp = "username"
  itchio = "username"
  vk = "username"
  paypal = "username"
  telegram = "username"
```

Personalmente, no utilizo apenas las redes sociales y confieso que, del anterior
listado, ni siquiera conozco algunas de ellas. Así pues, como no podía ser de
otra manera, en mi caso el anterior bloque de código ha quedado ciertamente
reducido:

```toml
#
# Configuración del autor
#
[Author]
  name    = "Alexis Sáez"
  website = "https://imalexissaez.github.io/"
  email   = "imalexissaez@gmail.com"
  github  = "ImAlexisSaez"
  twitter = "imalexissaez"
```

El último bloque de instrucciones que se presenta ante nosotros nos ofrece la
posibilidad de configurar el menú que aparece en la parte superior derecha y
presenta el siguiente aspecto:

```toml
[[menu.main]]
    name = "Blog"
    url = ""
    weight = 1

[[menu.main]]
    name = "About"
    url = "page/about/"
    weight = 3

[[menu.main]]
    identifier = "samples"
    name = "Samples"
    weight = 2

[[menu.main]]
    parent = "samples"
    name = "Big Image Sample"
    url = "post/2017-03-07-bigimg-sample"
    weight = 1

[[menu.main]]
    parent = "samples"
    name = "Math Sample"
    url = "post/2017-03-05-math-sample"
    weight = 2

[[menu.main]]
    parent = "samples"
    name = "Code Sample"
    url = "post/2016-03-08-code-sample"
    weight = 3

[[menu.main]]
    name = "Tags"
    url = "tags"
    weight = 3
```

No obstante, de momento, dejaremos el anterior bloque tal cual figura arriba y
ya procederemos en un futuro a su modificación, cuando incorporemos algunos
cambios adicionales al sitio web.

Fin del archivo `config.toml`, fin de la entrada, ¿verdad? Todavía no. Nos
quedan un par de detalles a los que echarles un vistazo.

Para empezar, a continuación, configuraremos las taxonomías de nuestro sitio
web. ¿Qué es una taxonomía? Sin pretender entrar en detalles técnicos aquí, para
que nos hagamos una idea, una taxonomía es un instrumento que nos permite
agrupar contenido relacionado. Los ejemplos más habituales a los que estamos
acostumbrados son _categorías_ y _etiquetas_ (que aquí se llamarán _categories_
y _tags_), que facilitan al lector encontrar artículos que comparten cierta
temática.

En mi caso, para _Infinitos Contrastes_, conservaré ambas, aunque renombrando su
versión inglesa al castellano, para facilitar después la configuración de la
localización de la plantilla. Así, `categories` pasará a ser `apartados`,
mientras que `tags` se convertirá en `etiquetas`. Además, declararé una nueva
taxonomía denominada `proyectos`, que me facilitará agrupar fácilmente
contenido, llegado el caso, de distintos apartados o etiquetas.

Todo ello se traduce en incluir el siguiente bloque de código en el fichero
`config.toml`:

```toml
#
# Configuración de taxonomías
#
[taxonomies]
  category = "categories"
  tag      = "tags"
  apartado = "apartados"
  proyecto = "proyectos"
  etiqueta = "etiquetas"
```

Recomiendo seguir la estructura `singular = plural` marcada en la
[guía oficial](https://gohugo.io/content-management/taxonomies/) de taxonomías
de _Hugo_. De hecho, dado que la formación de plurales en inglés y castellano es
diferente, afinaría un poco la anterior recomendación señalando que conviene
escoger parejas en donde el plural se diferencie del singular únicamente por el
carácter `s` final.

¿Por qué debemos cuidar tanto el detalle a la hora de declarar taxonomías? Es
posible que en un futuro nos adentremos en la personalización de las plantillas
del tema y _Hugo_ incorpora útiles funciones para recorrer bucles apoyándose en
esta curiosa relación singular-plural. Es por ello que no vamos a pegarnos un
tiro en los pies declarando parejas de variables y valores que luego nos impidan
aprovecharnos de las mencionadas herramientas.

Por último, para finalizar este artículo, echaremos un vistazo a la
configuración del [permalink](https://gohugo.io/content-management/urls/) de las
entradas del sitio web. Por defecto, _Hugo_ utiliza el directorio donde se
encuentre el contenido (generalmente es `\post\`) y lo concatena con el título
de la entrada, para el que sustituye espacios por guiones.

Para empezar, me gustaría que apareciese el día de publicación del artículo en
el _permalink_, siguiendo el formato `/año/mes/día`. Por otro lado, como soy
consciente de que utilizar caracteres extraños a ojos del alfabeto inglés
(tildes, eñes, etc.), en ocasiones, es fuente de problemas, en cada entrada
definiré manualmente mi propio _slug_, para evitar que la traducción automática
del título hacia su correspondiente parte del _permalink_ dé lugar a resultados
no deseados.

Así pues, mi archivo `config.toml` finaliza con el siguiente bloque código:

```toml
#
# Configuración del permalink
#
[permalinks]
  post = "/:year/:month/:day/:slug/"
```

En el siguiente artículo catalogado bajo la etiqueta [Metablog](/tags/metablog/)
dejaremos a un lado, de momento, la configuración de la plantilla para estudiar
cómo generar contenido (en forma de artículos) para nuestro sitio web.
