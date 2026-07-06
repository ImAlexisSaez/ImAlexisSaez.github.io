---
title: Unos cambios rápidos a las plantillas
summary: "Lección 11: implementando la localización al español de ciertos elementos de la web."
date: 2019-06-01
lastmod: 2026-07-06
image:
  caption: Imagen generada por Leonardo.Ai
authors:
  - me
categories:
  - Tutoriales
tags:
  - CSS
  - Beautiful Hugo
  - Hugo
  - Metablog
status: published
---
En esta entrada recojo el código necesario para localizar a español ciertas
secciones de la página web, incluyendo un experimento que al final no terminó de
convencerme, pero que comparto por si sirviera de inspiración a la creatividad
ajena.

Al final de cada una de las entradas del blog aparece un apartado de
_etiquetas_, que permite agrupar fácilmente contenidos relacionados. Cambiemos
la cabecera de esta sección de `Tags:` a `Etiquetas:`. Para ello, editamos con
_Sublime Text 3_ el archivo `main.css` (ubicado en la ruta `\static\css\`) y
buscamos el siguiente bloque de código:

```css
.blog-tags:before {
    content: "Tags: ";
}
```

Acto seguido, modificamos el valor del atributo `content`:

```css
.blog-tags:before {
    content: "Etiquetas: ";
}
```

y guardamos los cambios realizados.

Siguiendo con esta misma filosofía, traduzcamos ese `View all` que aparece en
las páginas de índice que agrupan contenidos por taxonomías. Para ello, editamos
el archivo `terms.html` (ubicado en la ruta `\layouts\_default\`) y, utilizando
el buscador de _Sublime Text 3_, nos situamos donde aparece la mencionada cadena
de caracteres y la sustituimos, por ejemplo, por `Ver todos`.

Todavía podemos mejorar un tanto la localización a español del tema a través de
las taxonomías. Con tal objetivo en mente, modifiquemos el fichero `config.toml`
(ubicado en el directorio raíz de la página web) como sigue, de

```toml
#
# Configuración de taxonomías
#
[taxonomies]
  category = "categories"
  tag      = "tags"
  project  = "projects"
```

a

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

Ahora, editamos la plantilla `single.html` (ubicada en la ruta
`\layouts\_default\`) y sustituimos el bloque de código:

```html
{{ if .Params.tags }}
<div class="blog-tags">
    {{ range .Params.tags }}
    <a href="{{ $.Site.LanguagePrefix | absURL }}/tags/{{ . | urlize }}/"
        >{{ . }}</a
    >&nbsp; {{ end }}
</div>
{{ end }}
```

por

```html
{{ if .Params.etiquetas }}
<div class="blog-tags">
    {{ range .Params.etiquetas }}
    <a href="{{ $.Site.LanguagePrefix | absURL }}/etiquetas/{{ . | urlize }}/"
        >{{ . }}</a
    >&nbsp; {{ end }}
</div>
{{ end }}
```

Si queremos que aparezca en las entradas del blog información sobre el apartado
o proyecto al que pertenecen, no tendríamos más que incorporar dos nuevos
bloques a continuación, utilizando el anterior como guía y llevando a cabo las
adaptaciones pertinentes. Por otro lado, sería más que recomendable crear en el
archivo de estilos _css_ las clases `blog-etiquetas`, `blog-apartados` y
`blog-proyectos`, para mejorar el mantenimiento de la localización del tema en
un futuro.

A continuación, hemos de editar las plantillas `list.html` e `index.html`
(ubicadas ambas en la ruta `\layouts\_default`), substituyendo los bloques de
código

```html
{{ if .Params.tags }}
<div class="blog-tags">
    {{ range .Params.tags }}
    <a href="{{ $.Site.LanguagePrefix | absURL }}/tags/{{ . | urlize }}/"
        >{{ . }}</a
    >&nbsp; {{ end }}
</div>
{{ end }}
```

por

```html
{{ if .Params.etiquetas }}
<div class="blog-tags">
    {{ range .Params.etiquetas }}
    <a href="{{ $.Site.LanguagePrefix | absURL }}/etiquetas/{{ . | urlize }}/"
        >{{ . }}</a
    >&nbsp; {{ end }}
</div>
{{ end }}
```

Añadiendo, acto seguido, bloques análogos para `apartados` y `proyectos` si lo
hemos considerado oportuno.

Este cambio nos obliga a actualizar la ruta de acceso a la página de etiquetas,
por lo que debemos editar el archivo `config.toml` (ubicado en el directorio
raíz de la página web) de manera que el bloque de código

```toml
[[menu.main]]
    name = "Etiquetas"
    url = "tags"
    weight = 3
```

pase a ser

```toml
[[menu.main]]
    name = "Etiquetas"
    url = "etiquetas"
    weight = 3
```

Finalmente, nos queda modificar el estilo de la cabecera de la página de
etiquetas. Para ello editamos el archivo `main.css` (ubicado en la ruta
`\static\css\`) buscando el término `header` y añadiendo la cadena
correspondiente a etiquetas. Por ejemplo, para el bloque de código

```css
.intro-header .page-heading,
.intro-header .tags-heading {
    text-align: center;
}
```

la modificación quedaría como sigue

```css
.intro-header .page-heading,
.intro-header .tags-heading,
.intro-header .etiquetas-heading {
    text-align: center;
}
```

En total, hemos de proceder de esta manera en tres ocasiones.

Y ya que estamos con las manos en la masa, creemos las clases de estilos para
`etiquetas`, `apartados` y `proyectos` trabajando sobre los bloques de código
originales que aparecen tras el comentario `/* --- Tags --- */` (recordemos que
cualquier modificación puede implicar después que hayamos de editar la cabeceras
de las páginas tal y como hicimos hace un instante). Así pues, nos van a quedar
bloques como el que aparece a continuación:

```css
.blog-tags,
.blog-apartados,
.blog-etiquetas,
.blog-proyectos {
    font-family: "Open Sans", "Helvetica Neue", Helvetica, Arial, sans-serif;
    color: #999;
    font-size: 15px;
    margin-bottom: 30px;
}
```

Aquellos en los que aparece el atributo `before` no los podemos agrupar tan
fácilmente. No obstante, no deja de ser trabajo de _copy&paste_.

Como he comentado arriba, no debemos olvidar añadir a las clases de las
cabeceras las líneas correspondientes, de forma que nos aparezcan bloques como
el que figura acto seguido:

```css
.intro-header .page-heading,
.intro-header .tags-heading,
.intro-header .apartados-heading,
.intro-header .etiquetas-heading,
.intro-header .proyectos-heading {
    text-align: center;
}
```

A continuación, hacemos una nueva modificación sobre el fichero `config.toml`
(ubicado en el directorio raíz de la página web) y cambiamos el nombre del menú
principal _Blog_ por _Inicio_. Así, el bloque de código

```toml
[[menu.main]]
    name = "Blog"
    url = ""
    weight = 1
```

pasa a ser

```toml
[[menu.main]]
    name = "Inicio"
    url = ""
    weight = 1
```

Acto seguido, en la plantilla `single.html` (ubicada en la ruta
`\layouts\_default`) añado, en la ubicación donde aparecen las etiquetas,
información sobre el apartado y el proyecto al que pertenece una entrada en
particular. Por tanto, el bloque de código

```html
{{ if .Params.etiquetas }}
<div class="blog-etiquetas">
    {{ range .Params.etiquetas }}
    <a href="{{ $.Site.LanguagePrefix | absURL }}/etiquetas/{{ . | urlize }}/"
        >{{ . }}</a
    >&nbsp; {{ end }}
</div>
{{ end }}
```

a

```html
{{ if .Params.apartados }}
<div class="blog-apartados">
    {{ range .Params.apartados }}
    <a href="{{ $.Site.LanguagePrefix | absURL }}/apartados/{{ . | urlize }}/"
        >{{ . }}</a
    >&nbsp; {{ end }}
</div>
{{ end }} {{ if .Params.etiquetas }}
<div class="blog-etiquetas">
    {{ range .Params.etiquetas }}
    <a href="{{ $.Site.LanguagePrefix | absURL }}/etiquetas/{{ . | urlize }}/"
        >{{ . }}</a
    >&nbsp; {{ end }}
</div>
{{ end }} {{ if .Params.proyectos }}
<div class="blog-proyectos">
    {{ range .Params.proyectos }}
    <a href="{{ $.Site.LanguagePrefix | absURL }}/proyectos/{{ . | urlize }}/"
        >{{ . }}</a
    >&nbsp; {{ end }}
</div>
{{ end }}
```

Sin embargo, aunque es una opción razonable, no me convence cómo queda, por lo
que, en mi caso, voy a dejarlo como estaba. No obstante, comparto el código
fuente por si alguien tiene interés en realizar esta modificación.

Por último, quizá quede todo un poco mejor si damos acceso a las diferentes
secciones desde el menú superior derecho, con un desplegable. Para ello,
modificamos el fichero `config.toml` (ubicado en el directorio raíz de la página
web) y dejamos la sección dedicada al menú como figura a continuación:

```toml
#
# Configuración del menú superior derecho
#
[[menu.main]]
    identifier = "menu"
    name       = "Menú"
    weight     = 1

[[menu.main]]
    parent = "menu"
    name   = "Apartados"
    url    = "apartados/"
    weight = 1

[[menu.main]]
    parent = "menu"
    name   = "Etiquetas"
    url    = "etiquetas/"
    weight = 2

[[menu.main]]
    parent = "menu"
    name   = "Proyectos"
    url    = "proyectos/"
    weight = 3

[[menu.main]]
    name   = "Acerca de"
    url    = "page/about/"
    weight = 2
```

Concluyo aquí esta extensa entrada, dejando la etiqueta
[MetaBlog](/tags/metablog/) en espera, pues en estos momentos estoy más centrado
en la generación de contenido para la página web, que en la edición de la misma.
