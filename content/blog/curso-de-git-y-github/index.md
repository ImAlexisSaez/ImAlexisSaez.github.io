---
title: Curso de Git y GitHub
summary: En este curso aprenderemos a utilizar la herramienta de control de versiones más popular actualmente, Git. Además, examinaremos la plataforma GitHub, que facilita enormemente la posibilidad de trabajar de manera colaborativa.
date: 2023-06-25
lastmod: 2026-06-04
image:
  caption: Imagen generada por Leonardo.Ai
authors:
  - me
categories:
  - Programación
tags:
  - Git
  - Github
  - The Odin Project
status: published
---
### 1. Introducción

A estas alturas, he claudicado y me he resignado a que, seguramente, acabe el
verano y no haya sido capaz de completar el curso de fundamentos de
[The Odin Project](https://www.theodinproject.com/). ¡Es imposible! Hay una
infinidad de “rabbit holes” en los que caer que son realmente tentadores. Aunque
en el propio curso recomienda esquivarlos, mi capacidad para mirar hacia otro
lado parece ser muy limitada.

De esta forma, una vez que he logrado salir del asociado a los comandos de la
terminal de Linux, le ha tocado el turno a Git. Aunque es una herramienta que he
estado utilizando durante más de un año, sí que es cierto que mi manejo de esta
es muy básico. Utilizo únicamente el flujo de comandos `git add`, `git commit` y
`git push`, desaprovechando así las tremendas posibilidades que sé que ofrece,
pero que nunca me he esforzado por aprender.

Así pues, durante las siguientes semanas voy a trabajar este aspecto utilizando
un recurso de la plataforma Udemy: el curso
[The Git & GitHub Bootcamp](https://www.udemy.com/course/git-and-github-bootcamp/),
que viene de la mano de Colt Steele. El instructor hace las sesiones muy amenas
y el temario que cubre el curso, a primera vista y desde cierto desconocimiento,
parece bastante completo. En mi caso, a partir de la cuarta sección de este, los
conceptos y comandos que se nombran me resultan desconocidos.

Finalmente, como estoy tomando apuntes en [Obsidian](https://obsidian.md/)
mientras visualizo las lecciones (es todo un espectáculo ver la cantidad de
aplicaciones que tengo abiertas a la hora de seguir cualquier curso),
seguramente inicie una serie de entradas en el blog relacionadas con Git.

### 2. Instalación y configuración

Para empezar, y simplemente para que quede constancia; aunque Git es una
herramienta que manejamos principalmente desde la terminal, existen diversas
aplicaciones que permiten que la usemos mediante una interfaz gráfica, como, por
ejemplo:

- GitHub Desktop
- SourceTree
- Tower
- GitKraken
- Ungit

No obstante, a pesar de las múltiples comodidades que ofrecen estas;
emplearemos, en la medida de lo posible, la terminal a la hora de utilizar Git.
Esto es debido a que su uso deja de ser intuitivo cuando queremos sacar provecho
de las características más avanzadas de esta herramienta.

A continuación, los pasos que hemos de seguir para **instalar Git en Windows**
son:

1. Descargamos el instalador de Git para Windows de
   [esta página](https://git-scm.com/).
2. Instalamos Git con las opciones y los componentes que vienen marcados por
   defecto. No obstante, en el editor de texto por defecto, conviene que
   seleccionemos VSCode en lugar de Vim.
3. Ejecutamos Git Bash y escribimos en la terminal `git --version` para
   comprobar que la instalación se ha llevado a cabo con éxito.

Ahora, una vez hemos instalado Git, conviene que determinemos el valor de un par
de variables importantes: el nombre de usuario y la cuenta de correo
electrónico. Para empezar, si queremos determinar el nombre de usuario en Git,
el comando que introducimos en la terminal es:

```bash
git config --global user.name "<nombre>"
```

Por otro lado, si queremos declarar la cuenta de correo electrónico, la
instrucción correspondiente que tecleamos es:

```bash
git config --global user.email <cuenta@de.correo>
```

Ahora, una vez establecidos ambos, podemos comprobar que los datos introducidos
son correctos escribiendo:

```bash
git config user.name
```

```bash
git config user.email
```

Dentro de este marco, enseguida apreciamos la importancia de conocer el uso de
la terminal que ofrece Git Bash. En este apartado, sin pretender ser
exhaustivos, listamos los comandos que emplearemos con frecuencia en esta
herramienta:

- `cd`: cambia de directorio. Para regresar a un nivel inferior de la ruta
  escribimos `cd ..`.
- `clear`: limpia la terminal.
- `ls`: devuelve una lista con los contenidos de un directorio (archivos,
  carpetas...).
- `mkdir`: crea un directorio (o varios).
- `pwd`: devuelve el actual directorio de trabajo.
- `rm`: elimina un archivo (o varios). Incluso suprime un directorio por
  completo si añadimos el atributo `-rf` (`r` para ''recursive'' y `f` para
  ''force'').
- `start .`: ejecuta el explorador de archivos de Windows y muestra los
  contenidos del directorio actual mediante la interface gráfica. En otros
  sistemas operativos, el comando equivalente es `open .`.
- `touch`: crea un archivo (o varios).

Por otro lado, si deseamos consultar más detalles sobre el uso de una terminal
de Linux de tipo Bash, podemos consultar el curso de comandos de Linux.

### 3. Referencias

- [The Git & GitHub Bootcamp](https://www.udemy.com/course/git-and-github-bootcamp/)
- [The Odin Project](https://www.theodinproject.com/)

### 4. Historial de versiones del artículo

- 2023.06.26: Escribe la sección sobre instalación y configuración
- 2023.06.25: Escribe la sección de introducción
