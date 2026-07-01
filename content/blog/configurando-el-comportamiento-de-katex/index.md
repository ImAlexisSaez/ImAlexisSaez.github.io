---
title: Configurando el comportamiento de KaTeX
summary: "Lección 9: revisamos cómo añadir ecuaciones en línea y, además, modificamos el tamaño de la letra para las expresiones matemáticas."
date: 2018-09-18
lastmod: 2026-07-01
image:
  caption: Imagen generada por Leonardo.Ai
authors:
  - me
categories:
  - Tutoriales
tags:
  - Beautiful Hugo
  - Hugo
  - KaTeX
  - Metablog
status: published
---
El tema _Beautiful Hugo_ viene, por defecto, configurado para que podamos
escribir expresiones matemáticas utilizando
[KaTeX](https://khan.github.io/KaTeX/). Tras unos minutos experimentando con
esta tecnología surge enseguida la primera duda: ¿cómo puedo escribir ecuaciones
en línea?

Para empezar, recomiendo encarecidamente que acudamos a la página de
[versiones](https://github.com/Khan/KaTeX/releases) de _KaTeX_ y nos hagamos con
la última de ellas, para estar al día en las opciones que ofrece esta
herramienta. A la hora de escribir estas líneas, dicha versión venía etiquetada
como `v0.10.0-rc.1`.

Para ello, hacemos clic sobre el enlace denominado `katex.zip` y así iniciaremos
la descarga de un archivo comprimido, del cual nos interesan especialmente dos
archivos contenidos en su interior:

- `katex.min.css` y
- `katex.min.js`.

El primero de ellos lo ubicaremos, dentro del directorio donde hayamos decidido
almacenar localmente el sitio web, en la ruta `\static\css\`, mientras que el
segundo en `\static\js\`, sobrescribiendo en ambos casos las antiguas versiones
que existiesen en dichas carpetas.

Una vez al día, la siguiente tarea implica la modificación de una de las
plantillas del tema _Beautiful Hugo_, concretamente la denominada como
`footer.html`, ubicada en la ruta `\layouts\partials\`. Editamos el mencionado
fichero con _Sublime Text 3_ y buscamos la siguiente línea:

```html
<script>
    renderMathInElement(document.body);
</script>
```

Vamos a configurar _KaTeX_ de manera que reconozca las expresiones encerradas
entre `$` o `\\(` como ecuaciones en línea, mientras que las delimitadas por
`$$` o `\\[` como ecuaciones centradas en sus propias líneas. Para ello,
tecleamos en el lugar de la anterior instrucción el siguiente bloque de código:

```html
<script>
    renderMathInElement(document.body, {
        delimiters: [
            { left: "$$", right: "$$", display: true },
            { left: "\\[", right: "\\]", display: true },
            { left: "$", right: "$", display: false },
            { left: "\\(", right: "\\)", display: false },
        ],
    });
</script>
```

Una vez habilitada la opción de escribir ecuaciones en línea, un hecho salta a
la vista de inmediato: ¿no parece que el tamaño de letra para las expresiones
matemáticas es mayor que el declarado para el texto estándar? Efectivamente,
peculiaridad que, en mi opinión, desluce bastante el aspecto (e incluso diría
que dificulta la lectura) de los artículos.

La solución pasa por modificar la hoja de estilos del tema _Beautiful Hugo_,
almacenada en el archivo `main.css`, que está ubicado en la ruta `\static\css\`.
Tras experimentar con cierto rango de valores para el tamaño de fuente de los
objetos de la clase `.katex`, al final me he decantado por la siguiente
solución, que he colocado al principio del fichero `main.css`:

```css
/* Modificación para hacer que el tamaño de letra de KaTeX sea similar al de la web */
.katex {
    font-size: 1.1em !important;
}
```

En los próximos artículos catalogados bajo la etiqueta
[Metablog](/tags/metablog/) continuaremos con la edición de diversas plantillas
del tema _Beautiful Hugo_, para terminar de aprender cómo adaptarlo a nuestro
gusto.
