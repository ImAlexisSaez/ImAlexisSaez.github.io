---
title: VSCode + LaTeX, solucionando el problema con latexindent
summary: Este artículo está dirigido a mi cada vez más olvidadizo 'yo del futuro', para cuando se encuentre en la misma tesitura que he experimentado estos días al realizar la transición de TeXMaker hacia VSCode como editor para trabajar con LaTeX.
date: 2023-09-09
lastmod: 2026-06-03
image:
  caption: Imagen generada por Leonardo.Ai
authors:
  - me
categories:
  - Tutoriales
tags:
  - LaTeX
  - VSCode
status: published
---
### Introducción y requisitos previos

Este artículo está dirigido a mi cada vez más olvidadizo ''yo del futuro'', para
cuando se encuentre en la misma tesitura que he experimentado estos días al
realizar la transición de TeXMaker hacia VSCode como editor para trabajar con
LaTeX. No obstante, bienvenida sea aquella persona que se haya topado con este
problema y no desee dar todas esas vueltas al asunto que me he visto obligado a
rodar.

Antes de nada, añado un poco de contexto a la entrada, con el objetivo de que no
se reduzca a una mera receta de pasos a seguir (aunque al final del artículo
habrá una de esas). Como suele ser habitual en estas fechas, con la llegada del
verano arriban nuevos proyectos a puerto. Dado que he estado utiizando VSCode
como editor en algunos cursos de programación, ¿por qué no investigar qué tal se
comporta esta herramienta a la hora de trabajar con LaTeX?

Por tanto, en las siguientes líneas, parto de la base de que:

- Windows es el sistema operativo instalado en el ordenador. De hecho, sin
  pretender desvelar demasiados ''spoilers'', es el principal culpable del
  problema que da lugar a este texto. Tras leer algunos artículos y las
  discusiones de ciertos foros, en otros sistemas operativos no se produce
  conflicto alguno con la herramienta _latexindent_.
- [MiKTeX](https://miktex.org/) y [VSCode](https://code.visualstudio.com/) se
  han instalado adecuadamente.

### Explorando LaTeX Workshop

Así pues, para empezar, en VSCode existe una extensión bastante popular para
trabajar con LaTeX:
[LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop).
En su página de presentación me llaman la atención poderosamente algunas
características llamativas, aunque también es cierto que la mayoría de ellas
están disponibles en TeXMaker. Su instalación es sencilla y la configuración que
viene por defecto parece adecuada en un primer vistazo por encima. Recalco aquí
la palabra vistazo, pues la extensión cuenta, a la hora de escribir estas
líneas, con la nada desdeñable cantidad de 157 opciones para afinar su
comportamiento.

Además, puesto que había investigado brevemente la posible transición de
TeXMaker a VSCode, aprovecho enseguida este interesante
[artículo](https://mathjiajia.github.io/vscode-and-latex/) e incluyo en las
preferencias de usuario de VSCode las siguientes líneas:

```json
"latex-workshop.latex.tools": [
 {
  "name": "latexmk",
  "command": "latexmk",
  "args": [
   "-synctex=1",
   "-interaction=nonstopmode",
   "-file-line-error",
   "-pdf",
   "-outdir=%OUTDIR%",
   "%DOC%"
  ],
  "env": {}
 },
 {
  "name": "xelatex",
  "command": "xelatex",
  "args": [
   "-synctex=1",
   "-interaction=nonstopmode",
   "-file-line-error",
   "%DOC%"
  ],
  "env": {}
 },
 {
  "name": "pdflatex",
  "command": "pdflatex",
  "args": [
   "-synctex=1",
   "-interaction=nonstopmode",
   "-file-line-error",
   "%DOC%"
  ],
  "env": {}
 },
 {
  "name": "bibtex",
  "command": "bibtex",
  "args": [
   "%DOCFILE%"
  ],
  "env": {}
 }
],
```

```json
"latex-workshop.latex.recipes": [
 {
  "name": "pdfLaTeX",
  "tools": [
   "pdflatex"
  ]
 },
 {
  "name": "latexmk 🔃",
  "tools": [
   "latexmk"
  ]
 },
 {
  "name": "xelatex",
  "tools": [
   "xelatex"
  ]
 },
 {
  "name": "pdflatex ➞ bibtex ➞ pdflatex`×2",
  "tools": [
   "pdflatex",
   "bibtex",
   "pdflatex",
   "pdflatex"
  ]
 },
 {
 "name": "xelatex ➞ bibtex ➞ xelatex`×2",
 "tools": [
   "xelatex",
   "bibtex",
   "xelatex",
   "xelatex"
  ]
 }
]
```

En cuanto al primer bloque de código, muestra algunos de los comandos empleados
a la hora de compilar documentos en LaTeX. Además, indica cómo pasar argumentos
de cara a la compilación, ofreciéndome así una guía para que los personalice
según mis intereses personales. En mis documentos utilizo habitualmente
`pdflatex` o `xelatex`, pero nunca está de más disponer de plantillas
adicionales de compilación.

Por lo que respecta al segundo bloque de código, es todavía más interesante,
pues enseña cómo ''encadenar'' comandos para que se ejecuten de manera
secuencial de forma sencilla. Para esta tarea, en mi caso particular, confieso
que todavía utilizaba archivos de procesos por lotes. Al igual que antes, con
los ejemplos incluidos es posible diseñar fácilmente la cadena de comandos que
mejor se ajuste a mis necesidades.

### La batalla con Latexindent

Por otra parte, y cambiando de tercio completamente, una de las extensiones que
más me ha convencido a la hora de trabajar con VSCode es
[Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode).
Se encarga de formatear la disposición del código de manera automática,
ajustando espacios verticales y horizontales según unas reglas predefinidas, de
manera que me ahorra el tiempo que antes invertía en ello (que no era poco, ya
que cada cual tiene sus manías). Desafortunadamente, no soporta LaTeX y en este
preciso instante comienza un pequeño calvario para mí.

Sin embargo, por fortuna, existe una herramienta destinada a ello:
_latexindent_. Ahora bien, aunque es la opción que por defecto incorpora la
extensión LaTeX Workshop para esta tarea, en un primer momento no da signos de
funcionar correctamente.

Como no podía ser de otra manera, empiezo a dar vueltas:

- En esta
  [discusión](https://tex.stackexchange.com/questions/577250/how-to-use-latexindent-on-windows)
  descubro que es un problema que únicamente afecta a los usuarios de Windows.
  Además, aunque _latexindent_ está incluido dentro del ecosistema de paquetes
  de LaTeX, por mucho que desinstale e instale el mismo desde el gestor de
  paquetes de MiKTeX, el problema no se soluciona. En la respuesta de la
  mencionada discusión se incluye una sección denominada ''What works'', pero ya
  directamente el primer paso no sé cómo llevarlo a cabo.
- A continuación, acudo a la página web oficial de la herramienta:
  [latexindent.pl](https://github.com/cmhughes/latexindent.pl). Su
  [manual](http://mirrors.ctan.org/support/latexindent/documentation/latexindent.pdf)
  de usuario aconseja a los usuarios de Windows descargar un archivo ejecutable
  preparado específicamente para este sistema operativo. Actuar así, además, me
  permite esquivar la instalación de **Perl**. Por consiguiente, accedo a la
  página de [releases](https://github.com/cmhughes/latexindent.pl/releases) y me
  hago con la versión `3.22.2` del ejecutable, la más actual a la hora de
  escribir estas líneas.
- Acto seguido, añado la ruta donde he ubicado dicho ejecutable al PATH del
  sistema y reinicio. Sin embargo, este camino tampoco arroja buenos frutos,
  pues _latexindent_ sigue sin funcionar en VSCode.
- Finalmente, tras experimentar brevemente en la terminal del sistema, descubro
  que al ejecutar `latexindent` el sistema no accede al ejecutable que acabo de
  descargar, sino al incluido en la instalación de MiKTeX. Es más, aunque
  desinstale el paquete desde el gestor de MiKTeX, ejecutar el comando lleva a
  su instalación. De esta forma, el problema se reduce a dar respuesta a la
  siguiente cuestión: ¿cómo puedo hacer que el sistema busque antes la
  herramienta en la nueva ruta? En esta ocasión la respuesta es sencilla: subir
  en el PATH la mencionada ruta por delante de la asociada a MiKTeX.

En resumen, a modo de **TL;DR**, para utilizar en VSCode la herramienta
_latexindent_ y dar formato de manera automática a los documentos de LaTeX:

1. Descarga el ejecutable para Windows desde la página oficial de
   [releases](https://github.com/cmhughes/latexindent.pl/releases).
2. Añade al PATH la ruta donde ubiques dicho ejecutable.
3. Posiciona dicha ruta por delante de la asociada a MiKTeX.

### Referencias

- [A Fast Guide on Writing LaTeX with LaTeX Workshop in VS Code](https://mathjiajia.github.io/vscode-and-latex/)
- [How to use latexindent on Windows?](https://tex.stackexchange.com/questions/577250/how-to-use-latexindent-on-windows)
- [latexindent.pl](https://github.com/cmhughes/latexindent.pl)
- [MiKTeX](https://miktex.org/)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [VSCode](https://code.visualstudio.com/)
