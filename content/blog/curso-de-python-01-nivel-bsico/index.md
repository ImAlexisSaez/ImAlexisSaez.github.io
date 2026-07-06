---
title: "Curso de Python #01 (Nivel básico)"
summary: Introducción a Python
date: 2019-07-01
lastmod: 2026-07-06
image:
    caption: Imagen generada por Leonardo.Ai
authors:
    - me
categories:
    - Programación
tags:
    - Python
status: published
---

### 1. Introducción del curso

#### 1.1. Vídeo

{{< youtube G2FCfQj-9ig >}}

#### 1.2. Notas personales

En este vídeo, se presenta el curso de _Python_ y los motivos de su desarrollo.
Después se revisa el **temario**, que aborda:

- Introducción. Requisitos previos. Instalación software.
- Fundamentos y sintaxis básica del lenguaje.
- POO con Python.
- Algoritmos, listas y tramos.
- BBDD.
- Trabajo con gráficos y contenidos.
- Procesos y tareas.
- Programación de red. Sockets.
- Ejercicios prácticos.

La lección termina con un breve apartado de FAQ.

### 2. Introducción a Python

#### 2.1. Vídeo

{{< youtube 9ojhJsXNWCI >}}

#### 2.2. Notas personales

En este vídeo, se repasa la historia de _Python_ y sus principales
características. Entre ellas, destacan:

- Lenguaje interpretado de alto nivel, orientado a objetos, versátil y que es de
  código abierto.
- Gramática sencilla, clara y muy legible, con tipado dinámico y fuerte

A través de [este enlace](https://www.python.org/downloads/) descargamos la
última versión de _Python_ (3.7.3 a la hora de escribir estas líneas). Si
queremos la versión de 64 bits para _Windows_, hemos de buscarla en
[esta página](https://www.python.org/downloads/windows/).

Durante su instalación:

- Activamos la casilla que añade la ruta de _Python_ al `PATH`.
- Pulsamos, al final de la instalación, sobre la opción que elimina la
  restricción de longitud máxima sobre las rutas del `PATH`.

Con respecto a los IDE, en el curso se utilizará
[Sublime Text 3](https://www.sublimetext.com/3), aunque se ofrecen como
alternativas [Eclipse](https://www.eclipse.org/ide/) y
[Notepad++](https://notepad-plus-plus.org/).

### 3. Sintaxis básica

#### 3.1. Vídeo

{{< youtube yppT6GPZMyo >}}

#### 3.2. Notas personales

En el IDLE de _Python_, tecleamos:

```python
>>> print("¡Hola mundo!") # Esto es una instrucción
¡Hola mundo!
```

Usando `;` escribimos varias instrucciones en una misma línea, aunque es
desaconsejable por restar legibilidad.

```python
>>> print("¡Hola mundo!"); print("¡Bienvenidos!")
¡Hola mundo!
¡Bienvenidos!
```

Introducimos los **comentarios** con el símbolo `#` para:

- Anotar el código, facilitando futuros mantenimientos.
- Desactivar bloques de instrucciones, para localizar errores cometidos.

```python
>>> # Esto es un comentario
...
```

Mediante el símbolo `\` dividimos una instrucción en varias líneas, aunque es
desaconsejable por restar legibilidad.

```python
>>> mi_nombre = "Mi nombre es Alexis."
>>> mi_nombre
'Mi nombre es Alexis.'
>>> mi_nombre = "Mi nombre es \
... Alexis"
>>> mi_nombre
'Mi nombre es Alexis'
```

Construimos los bloques de código mediante **identación**. El IDLE se encarga
automáticamente de procurarla:

```python
>>> a = 0
>>> for i in range(5):
...     a += 1
...     print(a)
...
1
2
3
4
5
>>>
```

Durante el curso, usaremos el IDLE de _Sublime Text 3_. Para ello, descargamos
el editor a través de [este enlace](https://www.sublimetext.com/3) y lo
instalamos. Al iniciarlo:

- Desplegamos el menú `Tools` y seleccionamos `Command Palette...`.
- Escribimos `Install Package Control` y clicamos sobre la opción que aparece.
- Desplegamos, de nuevo, el menú `Tools`, seleccionamos `Command Palette...` y
  tecleamos `install package`.
- En la siguiente ventana, escribimos `SublimeREPL`, para así tener el
  interprete de _Python_ disponible desde el propio editor.
- Para activarlo, desde el menú `Tools`, seleccionamos ahora `SublimeREPL` y
  buscamos `Python`. Entre las opciones que aparecen, escogemos `Python`.
