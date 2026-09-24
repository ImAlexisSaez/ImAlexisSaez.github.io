---
title: "Curso de Python #08 (Nivel básico)"
summary: Métodos y archivos
date: 2019-08-14
lastmod: 2026-09-24
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

### 1. Cadenas

#### 1.1. Vídeo

{{< youtube zH0VsRuD2ok >}}

#### 1.2. Notas personales

Examinemos algunos de los métodos disponibles en _Python_ a la hora de trabajar
con cadenas de texto, que son objetos de tipo `String`. Entre los más habituales
encontramos:

- `upper()`
- `lower()`
- `capitalize()`
- `count()`
- `find()`
- `isdigit()`
- `isalum()`
- `isalpha()`
- `split()`
- `strip()`
- `replace()`
- `rfind()`

Para obtener más información sobre su utilización, conviene que visitemos
[esta página](http://pyspanishdoc.sourceforge.net/lib/string-methods.html).

Veamos algunos ejemplos sencillos que ilustren el uso de algunos de los
anteriores métodos:

```python
nombre_usuario = input("Introduce tu nombre de usuario: ")

print("El nombre es:", nombre_usuario)
print("El nombre es:", nombre_usuario.upper())
print("El nombre es:", nombre_usuario.lower())
print("El nombre es:", nombre_usuario.capitalize())
```

```bash
Introduce tu nombre de usuario: Alexis Sáez
El nombre es: Alexis Sáez
El nombre es: ALEXIS SÁEZ
El nombre es: alexis sáez
El nombre es: Alexis sáez
```

Algunas de estas funciones resultan útiles a la hora de validar los datos que un
usuario proporciona a nuestros programas:

```python
edad = input("Introduce la edad: ")

while not edad.isdigit():
    print("Por favor, introduce un valor numérico.")
    edad = input("Introduce la edad: ")

if int(edad) < 18:
    print("No puede pasar.")
else:
    print("Puede pasar.")
```

```bash
Introduce la edad: 8iu9
Por favor, introduce un valor numérico.
Introduce la edad: o9098
Por favor, introduce un valor numérico.
Introduce la edad: 99
Puede pasar.
```

**Ejercicio**: crea un programa que pida introducir una dirección de email por
teclado. El programa debe imprimir en consola si la dirección de email es
correcta o no en función de si esta tiene el símbolo `@`. Si tiene una `@` la
dirección será correcta. Si tiene más de una o ninguna `@` la dirección será
errónea. Si la `@` está al comienzo de la dirección de email o al final, la
dirección también será errónea

```python
email = input("Introduce email: ")

if email.count("@") == 1 and email.count("@", 1, len(email) - 1) == 1:
    print("La dirección de correo es correcta.")
else:
    print("La dirección de correo es incorrecta.")
```

### 2. Módulos

#### 2.1. Vídeo

{{< youtube t93x-vnFvP4 >}}

#### 2.2. Notas personales

Un **módulo** es un archivo con extensión `.py`, `.pyc` (Python compilado) o
fichero escrito en _C_ para _CPython_, que posee su propio espacio de nombres y
que puede contener variables, funciones, clases e incluso otros módulos.

Sirve para organizar y reutilizar el código (**modularización** y
**reutilización**). Se genera uno creando un archivo con extensión `.py` (o
`.pyc` o archivo en C) y guardándolo donde nos interese.

Vamos a crear un módulo que, siguiendo la organización del
[repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0) de código,
se llamará `modulo_matematicas.py`. En su interior tecleamos las siguientes
líneas:

```python
def sumar(op1, op2):
    print("El resultado de la suma es:", op1 + op2)


def restar(op1, op2):
    print("El resultado de la resta es:", op1 - op2)


def multiplicar(op1, op2):
    print("El resultado de la multiplicación es:", op1 * op2)
```

Ahora, generamos otro archivo, `script_1.py`, e importamos el anterior módulo,
utilizando para ello la instrucción `import`:

```python
import modulo_matematicas as modulo

modulo.sumar(5, 7)

modulo.restar(9, 5)

modulo.multiplicar(4, 9)
```

```bash
El resultado de la suma es: 12
El resultado de la resta es: 4
El resultado de la multiplicación es: 36
```

Como el nombre del módulo generado es un tanto extenso, he utilizado la
instrucción `as`, que permite reescribir dicho nombre y, en mi caso, abreviarlo
para que su uso sea más cómodo.

Una alternativa a esta estrategia la encontramos en el fichero `script_2.py`,
donde se utiliza `from ... import ...`:

```python
from modulo_matematicas import sumar

sumar(5, 7)
```

```bash
El resultado de la suma es: 12
```

En el bloque de código anterior, únicamente hemos importado la función `sumar()`
de nuestro módulo. Podemos añadir más funciones separándolas mediante comas o
importar todo el contenido del módulo utilizando el carácter `*`:

```python
from modulo_matematicas import sumar, restar

sumar(5, 7)

restar(12, 6)
```

```bash
El resultado de la suma es: 12
El resultado de la resta es: 6
```

```python
from modulo_matematicas import *

sumar(5, 7)

restar(12, 6)

multiplicar(12, 12)
```

```bash
El resultado de la suma es: 12
El resultado de la resta es: 6
El resultado de la multiplicación es: 144
```

No obstante, es peligroso actuar así, pues, en ocasiones, podemos reescribir
métodos de manera accidental y arribar a resultados no deseados. Además, en
aplicaciones complejas, por motivos de optimización, utilizar el carácter `*`
provoca que se reserve demasiado espacio en memoria al tener que almacenar todo
el contenido del módulo importado.

Creemos un módulo, `modulo_vehiculos.py` con las clases utilizadas en la lección
de herencia asociada al apartado de programación orientada a objetos:

```python
class Vehiculo():
    def __init__(self, marca, modelo):
        self.marca = marca
        self.modelo = modelo
        self.enmarcha = False
        self.acelera = False
        self.frena = False

    def arrancar(self):
        self.enmarcha = True

    def acelerar(self):
        self.acelera = True

    def frenar(self):
        self.frena = True

    def estado(self):
        print("Marca:", self.marca, "\nModelo:", self.modelo, "\nEn marcha:",
              self.enmarcha, "\nAcelerando:", self.acelera, "\nFrenando:",
              self.frena)


class Furgoneta(Vehiculo):
    def carga(self, cargar):
        self.cargado = cargar
        if self.cargado:
            return "La furgoneta está cargada."
        else:
            return "La furgoneta no está cargada."


class Moto(Vehiculo):
    hcaballito = ""

    def caballito(self):
        self.hcaballito = "Voy haciendo el caballito."

    def estado(self):
        print("Marca:", self.marca, "\nModelo:", self.modelo, "\nEn marcha:",
              self.enmarcha, "\nAcelerando:", self.acelera, "\nFrenando:",
              self.frena, "\n", self.hcaballito)


class VehiculoElec(Vehiculo):
    def __init__(self, marca, modelo):
        super().__init__(marca, modelo)
        self.autonomia = 100

    def cargar_energia(self):
        self.cargando = True
```

Y ahora, en el fichero `script_5.py` tecleamos:

```python
from modulo_vehiculos import *

mi_coche = Vehiculo("Mazda", "MX5")
mi_coche.estado()
```

```bash
Marca: Mazda
Modelo: MX5
En marcha: False
Acelerando: False
Frenando: False
```

_Python_ busca los módulos en el mismo directorio donde está guardado el fichero
desde el cual se realiza la llamada de importación. En caso de no hallarlo ahí,
pasa a revisar el `syspath` (es un conjunto de directorios entre los que está,
por ejemplo, el de instalación de _Python_).

Si no tenemos los módulos en ninguna de ambas ubicaciones, _Python_ arrojará un
error al ejecutar el programa. Para solucionar esta situación estudiaremos el
uso de **paquetes** en la próxima lección.

### 3. Paquetes I

#### 3.1. Vídeo

{{< youtube nRieWujis4s >}}

#### 3.2. Notas personales

Los **paquetes** son directorios donde se almacenarán módulos relacionados entre
sí. Sirven para organizar el código de una aplicación y reutilizar los
mencionados módulos.

Un paquete se crea generando un directorio en cuyo interior haya presente un
archivo denominado `__init__.py`.

Imaginemos que nuestro objetivo es elaborar un programa que realice diversos
cálculos matemáticos y estadísticos. Vamos a empezar creando un directorio
denominado `calculos`, en consonancia con la nomenclatura que estamos siguiendo
para los ficheros del
[repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).

En su interior creamos el mencionado archivo `__init__.py` (sin contenido
alguno), acción que le transmite a _Python_ la información de que la carpeta
`calculos` funcionará como un paquete.

Añadimos ahora a la carpeta el módulo `calculos_generales.py`, cuyo contenido es
el siguiente:

```python
def sumar(op1, op2):
    print("El resultado de la suma es:", op1 + op2)


def restar(op1, op2):
    print("El resultado de la resta es:", op1 - op2)


def multiplicar(op1, op2):
    print("El resultado de la multiplicación es:", op1 * op2)


def dividir(dividendo, divisor):
    print("El resultado de la división es:", dividendo / divisor)


def potenciar(base, exponente):
    print("El resultado de la potenciación es:", base**exponente)


def redondear(numero):
    print("El resultado del redondeo es:", round(numero))
```

Ahora, desde la raíz del directorio, veamos cómo podemos utilizar nuestro
paquete recién creado:

```python
from calculos.calculos_generales import dividir

dividir(10, 3)
```

```bash
El resultado de la división es: 3.3333333333333335
```

Recordemos que podemos importar todo el contenido del módulo utilizando el
carácter `*`:

```python
from calculos.calculos_generales import *

dividir(10, 3)

redondear(4.6)

potenciar(2, 10)
```

```bash
El resultado de la división es: 3.3333333333333335
El resultado del redondeo es: 5
El resultado de la potenciación es: 1024
```

Podemos crear **subpaquetes**, esto es, un paquete dentro de otro, siguiendo de
manera recursiva el procedimiento explicado.

Por ejemplo, para afinar un poco más, creemos dos directorios dentro de la
carpeta del paquete, denominados `basicos` (para suma, resta, multiplicación y
división) y `redondeo-potencia` (para redondear y calcular potencias). Cada una
de ellas ha de llevar en su interior su correspondiente fichero `__init__.py`.

En la carpeta `basicos` incluimos el módulo `operaciones_basicas.py`, cuyo
contenido será:

```python
def sumar(op1, op2):
    print("El resultado de la suma es:", op1 + op2)


def restar(op1, op2):
    print("El resultado de la resta es:", op1 - op2)


def multiplicar(op1, op2):
    print("El resultado de la multiplicación es:", op1 * op2)


def dividir(dividendo, divisor):
    print("El resultado de la división es:", dividendo / divisor)
```

Mientras que en la carpeta `redondeo_potencia` generamos el módulo
`redondea_y_potencia`, compuesto por el siguiente bloque de código:

```python
def potenciar(base, exponente):
    print("El resultado de la potenciación es:", base**exponente)


def redondear(numero):
    print("El resultado del redondeo es:", round(numero))
```

Para utilizar estos últimos módulos creados, tecleamos:

```python
from calculos.basicos.operaciones_basicas import sumar
from calculos.redondeo_potencia.redondea_y_potencia import potenciar

sumar(5, 7)
potenciar(2, 10)
```

```bash
El resultado de la suma es: 12
El resultado de la potenciación es: 1024
```

### 4. Paquetes II

#### 4.1. Vídeo

{{< youtube Zf9sN-w0BVE >}}

#### 4.2. Notas personales

Veamos cómo crear **paquetes distribuibles** para que otras personas puedan
utilizar nuestro código fuente. El proceso a seguir se reduce a dos sencillos
pasos:

1. Crear el paquete.
2. Instalar el paquete.

En la lección anterior generamos el paquete `calculos` como una carpeta en el
interior del directorio del
[repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0) donde
estamos almacenando todos los archivos de este curso. Desde la raíz del
mencionado directorio, utilizamos los módulos contenidos en dicho paquete en,
por ejemplo, `paquetes_1.py`.

Ahora bien, si movemos este último archivo a otro directorio, _Python_
seguramente no será capaz de encontrar el paquete `calculos`. Para solventar
esta situación, hemos de proceder a su instalación.

En primer lugar, creamos un archivo denominado `setup.py` en la raíz del
directorio, que contendrá una descripción del paquete que vamos a distribuir
(nombre, versión, autor...). En su interior, tecleamos:

```python
from setuptools import setup

setup(name="prac35_calculos",
      version="1.0",
      description="Paquete de cálculos matemáticos",
      author="Alexis Sáez",
      author_email="cucoalexis@hotmail.com",
      url="https://imalexissaez.github.io/",
      packages=["prac35_calculos"])
```

A continuación, abrimos la terminal de _Windows_ y nos dirigimos a la carpeta
donde hemos almacenado el fichero `setup.py` (la instrucción `cd` es clave en
este proceso). Escribimos ahora

```bash
python setup.py sdist
```

Si todo ha ido bien, habrán aparecido dos nuevas carpetas:

- `calculos.egg-info`
- `dist`

En esta última hallamos el archivo comprimido denominado `calculos-1.0.tar.gz`.
Este es el fichero que podemos enviar por correo electrónico o subir a alguna
plataforma online para distribuirlo a otras personas.

Acto seguido, imaginemos que lo hemos recibido y queremos instalarlo. Para ello,
desde la terminal de _Windows_ acudimos al directorio donde resida el fichero
comprimido y tecleamos:

```bash
pip3 install calculos-1.0.tar.gz
```

Recibiremos rápidamente en la consola el mensaje ''Successfully installed
calculos-1.0''.

Ahora, desde cualquier carpeta de nuestro ordenador, podemos emplear el paquete
recién instalado escribiendo, por ejemplo:

```python
from calculos.calculos_generales import sumar

sumar(6, 7)
```

```bash
El resultado de la suma es: 13
```

_Nota_: para comprobar que efectivamente el procedimiento se ha llevado a cabo
con éxito, he creado una nueva carpeta, `test_paquete`, y allí he ubicado el
archivo `paquetes.py`. De no haber instalado correctamente el paquete, _Python_
habría sido incapaz de encontrar la función `sumar()` utilizando la instrucción
dada arriba.

Finalmente, para desinstalar el paquete, desde la terminal de _Windows_
tecleamos:

```bash
pip3 uninstall calculos
```

### 5. Archivos I

#### 5.1. Vídeo

{{< youtube V87m9SltcI8 >}}

#### 5.2. Notas personales

En esta lección abordaremos cómo trabajar con ficheros externos de texto,
utilizando para tal empresa el módulo `io`. Nuestro objetivo será conseguir la
**persistencia de datos**, es decir, salvaguardar los datos que estamos
manipulando para que no se pierdan al finalizar una sesión de _Python_.

Existen dos alternativas para conseguir el mencionado objetivo:

- Manejar archivos externos.
- Trabajar con bases de datos (BBDD).

Las fases necesarias para guardar cierta información en archivos externos son:

1. Creación del archivo externo.
2. Apertura del archivo externo.
3. Manipulación del archivo externo.
4. Cierre del archivo externo.

La documentación del módulo `io` la podemos encontrar en
[este enlace](https://docs.python.org/3/library/io.html).

Veamos un ejemplo sencillo en el que crearemos un archivo donde almacenar una
frase. Empecemos tecleando:

```python
from io import open

archivo_texto = open("archivo.txt", "w")
```

_Nota_: un archivo lo podemos abrir en modo lectura (`r`), escritura (`w`),
agregar (`a`)...

Si ahora acudimos al interior de la carpeta, encontraremos un archivo de texto
vacío denominado `archivo.txt`. En absoluto es necesario que almacenemos el
fichero en una carpeta, pero únicamente procedo así para que el
[repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0) mantenga una
estructura coherente.

A continuación, veamos cómo incluir información (texto) en dicho archivo:

```python
from io import open

# Creación + Apertura
archivo_texto = open("archivo.txt", "w")

frase = "Es un estupendo día para estudiar Python\nen Youtube."

# Manipulación
archivo_texto.write(frase)

# Cierre
archivo_texto.close()
```

De esta manera, hemos incluido el texto declarado en la variable `frase` en el
fichero `archivo.txt`.

Acto seguido, estudiemos cómo abrir un archivo en modo lectura y acceder a su
contenido:

```python
from io import open

archivo_texto = open("archivo.txt", "r")

texto = archivo_texto.read()

archivo_texto.close()

print(texto)
```

```bash
Es un estupendo día para estudiar Python
en Youtube.
```

Otro método que nos puede resultar de utilidad a la hora de leer un archivo es
`readlines()`, que accede a la información almacenada línea a línea y la guarda
en una lista:

```python
from io import open

archivo_texto = open("archivo.txt", "r")

lineas_texto = archivo_texto.readlines()

archivo_texto.close()

print(lineas_texto)
```

```bash
['Es un estupendo día para estudiar Python\n', 'en Youtube.']
```

Al ser una lista, podemos utilizar ahora todo lo que hemos aprendido sobre
ellas:

```python
print(lineas_texto[0])
```

```bash
Es un estupendo día para estudiar Python
```

Finalmente, veamos cómo abrir un archivo para agregar información. Para no
alterar el contenido de `archivo.txt`, almacenaremos sus frases en una variable,
las escribiremos en un nuevo fichero, `archivo2.txt`, y sobre este último será
donde agreguemos contenido adicional:

```python
from io import open

archivo1 = open("archivo.txt", "r")
texto = archivo1.read()
archivo1.close()

archivo2 = open("archivo2.txt", "w")
archivo2.write(texto)
archivo2.close()

archivo2 = open("archivo2.txt", "a")
archivo2.write("\n¡Mañana más!")
archivo2.close()
```

Si acudimos a la carpeta, comprobaremos la existencia de un fichero denominado
`archivo2.txt`, que contiene tres líneas.

### 6. Archivos II

#### 6.1. Vídeo

{{< youtube 0dEYVSRYl_s >}}

#### 6.2. Notas personales

Continuemos el estudio de la manipulación de ficheros externos de texto, con el
módulo `io`, analizando en esta ocasión cómo manejar punteros en texto.

Para ello, movamos el último archivo de texto generado en la lección anterior
(`archivo2.txt`) a la carpeta, para así mantener la coherencia de la estructura
de ficheros del
[repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0). Tras ello,
tecleemos:

```python
from io import open

archivo = open("archivo2.txt", "r")

print(archivo.read())

archivo.close()
```

```bash
Es un estupendo día para estudiar Python
en Youtube.
¡Mañana más!
```

Si no indicamos lo contrario, la función `.read()` sitúa el puntero al inicio
del archivo y comienza entonces su lectura. Cuando finaliza esta, la posición
del puntero se ubica tras el último carácter. Esto implica que si ahora
escribimos de nuevo la instrucción `print(archivo.read())`, nada se mostraría en
la consola, puesto que tras la posición que ha quedado el puntero no existe
información alguna.

Se puede inicializar la posición del puntero utilizando la función `.seek()`,
que como argumento recibe el carácter desde el que deseamos comenzar la lectura
del archivo.

```python
from io import open

archivo = open("archivo2.txt", "r")

print(archivo.read())

archivo.seek(0)  # Reinicio posición puntero

print(archivo.read())

archivo.seek(10)  # Establezco posición puntero en carácter 10

print(archivo.read())

archivo.close()
```

```bash
Es un estupendo día para estudiar Python
en Youtube.
¡Mañana más!
Es un estupendo día para estudiar Python
en Youtube.
¡Mañana más!
pendo día para estudiar Python
en Youtube.
¡Mañana más!
```

Con el método `.read()` también podemos modificar la función del puntero, aunque
de manera algo diferente a cómo se lleva a cabo el proceso con `.seek()`. La
primera lee hasta la posición del puntero que le indiquemos como argumento,
mientras que la segunda posiciona el puntero en una posición y la lectura se
efectúa a partir de dicha posición.

```python
from io import open

archivo = open("archivo2.txt", "r")

print(archivo.read(11))
print(archivo.read())

archivo.close()
```

```bash
Es un estup
endo día para estudiar Python
en Youtube.
¡Mañana más!
```

Para situar el puntero justo en medio de un archivo de texto podemos emplear la
siguiente estrategia:

```python
from io import open

archivo = open("archivo2.txt", "r")

archivo.seek(len(archivo.read()) / 2)

print(archivo.read())

archivo.close()
```

```bash
r Python
en Youtube.
¡Mañana más!
```

¿Y si queremos situar el puntero al final de la primera línea?

```python
from io import open

archivo = open("archivo2.txt", "r")

archivo.seek(len(archivo.readline()))

print(archivo.read())

archivo.close()
```

```bash

en Youtube.
¡Mañana más!
```

Un archivo lo podemos abrir, simultáneamente, en modo lectura y escritura
(`"r+"`), para realizar ambas acciones a la vez si nos es preciso. Generemos un
fichero denominado `archivo3.txt`, con el mismo contenido que aquel con el que
llevamos trabajando a lo largo de toda esta lección. Después, tecleamos:

```python
from io import open

archivo = open("archivo3.txt", "r+")  # lectura y escritura

archivo.write("Comienzo del texto: ")

archivo.seek(0)

print(archivo.read())

archivo.close()
```

```bash
Comienzo del texto: para estudiar Python
en Youtube.
¡Mañana más!
```

Al abrir el archivo, el puntero se posiciona al principio del mismo. Así, cuando
usamos el método `.write()`, efectivamente sobreescribimos el contenido que
originalmente hubiera (en tantas posiciones como longitud posea la nueva cadena
de texto).

Así, para incluir una línea en mitad del documento (la segunda en este caso
particular), un posible enfoque sería:

```python
from io import open

archivo = open("archivo3.txt", "r+")  # lectura y escritura

lineas = archivo.readlines()

lineas[1] = "Esta línea ha sido incluida desde el exterior.\n"

archivo.seek(0)

archivo.writelines(lineas)

archivo.seek(0)

print(archivo.read())

archivo.close()
```

```bash
Comienzo del texto: para estudiar Python
Esta línea ha sido incluida desde el exterior.
¡Mañana más!
```

### 7. Serialización I

#### 7.1. Vídeo

{{< youtube SOimkkfQIOM >}}

#### 7.2. Notas personales

En esta lección estudiaremos cómo serializar colecciones de ciertos objetos. La
**serialización** consiste en guardar en un fichero externo una lista, un
diccionario o, incluso, un objeto; con la particularidad de que la codificación
de dicho fichero es binaria.

Esta estrategia resulta de utilidad a la hora de compartir archivos por
Internet, ya que su distribución es más sencilla, o bien si deseamos guardarlo
en un dispositivo de almacenamiento externo o en una base de datos.

Para tal empresa utilizaremos la biblioteca de _Python_ `pickle`, para
aprovechar los métodos:

- `dump()`: vuelca datos en un fichero binario externo, y
- `load()`: carga datos de un fichero binario externo.

Veamos un ejemplo sencillo de aplicación de ambas funciones. Almacenaremos en un
archivo binario externo una lista de nombres y, posteriormente, la rescataremos:

```python
import pickle

nombres = ["Pedro", "Ana", "María", "Isabel"]

fichero = open("lista_nombres", "wb")

pickle.dump(nombres, fichero)

fichero.close()

del fichero
```

_Notas_:

- A la hora de crear el fichero externo en modo escritura, con el método
  `open()`, hemos de indicarle que esta será binaria, para lo cual el
  correspondiente parámetro toma como valor de argumento `"wb"`.
- La instrucción `del` borra el puntero de la memoria hacia la variable
  `fichero`, dejando de estar disponible su acceso a partir de ese momento.
- Al ejecutar el anterior bloque de código, en la carpeta correspondiente del
  [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0)),
  aparecerá un archivo externo de tipo binario denominado `lista_nombres`.

A continuamos, veamos cómo rescatar la información que reside en el interior del
mencionado fichero.

```python
import pickle

fichero = open("lista_nombres", "rb")

lista = pickle.load(fichero)

fichero.close()

print(lista)
```

```bash
['Pedro', 'Ana', 'María', 'Isabel']
```

_Nota_: para activar el modo de lectura de archivos binarios, el parámetro
correspondiente de la función `open()` ha de tomar el valor de argumento `"rb"`.

### 8. Serialización II

#### 8.1. Vídeo

{{< youtube CkfDnMC79b4 >}}

#### 8.2. Notas personales

En esta lección, continuaremos estudiando el tema de la serialización,
analizando ahora cómo llevar a cabo el proceso cuando hay objetos implicados.

Aprovechemos la clase `Vehiculo` que generamos anteriormente y cuyo código
fuente recordemos era:

```python
class Vehiculo():
    def __init__(self, marca, modelo):
        self.marca = marca
        self.modelo = modelo
        self.enmarcha = False
        self.acelera = False
        self.frena = False

    def arrancar(self):
        self.enmarcha = True

    def acelerar(self):
        self.acelera = True

    def frenar(self):
        self.frena = True

    def estado(self):
        print("Marca:", self.marca, "\nModelo:", self.modelo, "\nEn marcha:",
              self.enmarcha, "\nAcelerando:", self.acelera, "\nFrenando:",
              self.frena)
```

A continuación, importemos la librería `pickle` y creemos una lista con algunas
instancias de la clase `Vehiculo`:

```python
import pickle

coche1 = Vehiculo("Mazda", "MX5")
coche2 = Vehiculo("Seat", "León")
coche3 = Vehiculo("Renault", "Megane")

coches = [coche1, coche2, coche3]

fichero = open("coches", "wb")

pickle.dump(coches, fichero)

fichero.close()

del fichero
```

_Notas:_

- Recordemos que estamos creando ficheros externos cuya codificación es binaria,
  es por ello que el valor del parámetro correspondiente de la función `open()`
  es `"wb"`.
- Al ejecutar el anterior bloque de código, aparecerá en la carpeta asociada del
  [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0)) el
  fichero `coches`.

Para rescatar la información de este archivo que acabamos de generar, tecleamos:

```python
import pickle


class Vehiculo():
    def __init__(self, marca, modelo):
        self.marca = marca
        self.modelo = modelo
        self.enmarcha = False
        self.acelera = False
        self.frena = False

    def arrancar(self):
        self.enmarcha = True

    def acelerar(self):
        self.acelera = True

    def frenar(self):
        self.frena = True

    def estado(self):
        print("Marca:", self.marca, "\nModelo:", self.modelo, "\nEn marcha:",
              self.enmarcha, "\nAcelerando:", self.acelera, "\nFrenando:",
              self.frena)


fichero = open("coches", "rb")

coches = pickle.load(fichero)

print(coches)
```

```bash
[<__main__.Vehiculo object at 0x00000259428D65C0>, <__main__.Vehiculo object at 0x00000259428F7F28>, <__main__.Vehiculo object at 0x00000259428F7F98>]
```

Efectivamente, disponemos ahora de una lista con tres objetos. No obstante,
recordemos que tenemos el método `estado` para acceder a información de interés
sobre dichos objetos. Así, si escribimos:

```python
for coche in coches:
    print(coche.estado())
```

```bash
Marca: Mazda
Modelo: MX5
En marcha: False
Acelerando: False
Frenando: False
None
Marca: Seat
Modelo: León
En marcha: False
Acelerando: False
Frenando: False
None
Marca: Renault
Modelo: Megane
En marcha: False
Acelerando: False
Frenando: False
None
```

_Nota_: como podemos comprobar arriba, si hacemos la recuperación de la
serialización en un fichero distinto, la definición de la clase `Vehiculo` es
necesario que figure asimismo (en caso contrario arroja _Python_ un error). El
problema radica en que el nuevo archivo no tiene información sobre la clase
`Vehiculo` ni, por supuesto, del método `estado()`.

### 9. Guardado permanente

#### 9.1. Vídeo

{{< youtube J3qvf1fTCsU >}}

#### 9.2. Notas personales

En esta lección, continuaremos estudiando cómo guardar datos de forma permanente
en ficheros externos, reforzando así los contenidos aprendidos hasta el momento.

Empecemos importando la librería `pickle` y creando una clase sencilla:
`Persona`.

```python
import pickle


class Persona:
    def __init__(self, nombre, genero, edad):
        self.nombre = nombre
        self.genero = genero
        self.edad = edad
        print("Se ha creado una persona nueva con el nombre de", self.nombre)

    def __str__(self):
        return "{} {} {}".format(self.nombre, self.genero, self.edad)
```

_Nota_: el método `__str__()` convierte en cadena de texto la información de un
objeto.

Así, si ahora tecleamos:

```python
sandra = Persona("Sandra", "Femenino", "29")
```

```bash
Se ha creado una persona nueva con el nombre de Sandra
```

El objetivo será crear algunos objetos de dicha clase, almacenarlos en una lista
(empresa que realizaremos a través de otra clase, `ListaPersonas`) y después
volcar la información en un fichero externo, al cual podamos acceder en
cualquier instante.

```python
import pickle


class Persona:
    def __init__(self, nombre, genero, edad):
        self.nombre = nombre
        self.genero = genero
        self.edad = edad
        print("Se ha creado una persona nueva con el nombre de", self.nombre)

    def __str__(self):
        return "{} {} {}".format(self.nombre, self.genero, self.edad)


class ListaPersonas:
    personas = []

    def agregar_personas(self, persona):
        self.personas.append(persona)

    def mostrar_personas(self):
        for persona in self.personas:
            print(persona.__str__())


lista_personas = ListaPersonas()

sandra = Persona("Sandra", "Femenino", "29")
lista_personas.agregar_personas(sandra)

antonio = Persona("Antonio", "Masculino", "39")
lista_personas.agregar_personas(antonio)

ana = Persona("Ana", "Femenino", "20")
lista_personas.agregar_personas(ana)

lista_personas.mostrar_personas()
```

```bash
Se ha creado una persona nueva con el nombre de Sandra
Se ha creado una persona nueva con el nombre de Antonio
Se ha creado una persona nueva con el nombre de Ana
Sandra Femenino 29
Antonio Masculino 39
Ana Femenino 20
```

Almacenemos ahora la lista de personas que hemos generado en un fichero externo.
Para ello, incluiremos los pasos necesarios del mencionado proceso en el
constructor de la clase `ListaPersonas`:

```python
class ListaPersonas:
    personas = []

    def __init__(self):
        fichero = open("lista_de_personas", "ab+")
        fichero.seek(0)  # Desplazamos cursor al principio

        try:
            self.personas = pickle.load(fichero)  # Cargamos información
            print("Se cargaron {} personas.".format(len(self.personas)))
        except EOFError:
            print("El fichero está vacío.")  # Para la primera vez que abrimos
        finally:
            fichero.close()
            del fichero

    def agregar_personas(self, persona):
        self.personas.append(persona)

    def mostrar_personas(self):
        for persona in self.personas:
            print(persona.__str__())


lista_personas = ListaPersonas()
```

```bash
El fichero está vacío.
```

_Nota_: en la función `open()`, el valor del argumento `"ab+"` nos permite
agregar información a un fichero de codificación binaria.

A continuación, modifiquemos el método `agregar_personas()` para que una vez
añadida a la lista la nueva información, la almacene en el fichero externo.

```python
class ListaPersonas:
    personas = []

    def __init__(self):
        fichero = open("lista_de_personas", "ab+")
        fichero.seek(0)  # Desplazamos cursor al principio

        try:
            self.personas = pickle.load(fichero)  # Cargamos información
            print("Se cargaron {} personas.".format(len(self.personas)))
        except EOFError:
            print("El fichero está vacío.")  # Para la primera vez que abrimos
        finally:
            fichero.close()
            del fichero

    def agregar_personas(self, persona):
        self.personas.append(persona)
        self.guardar_personas()

    def mostrar_personas(self):
        for persona in self.personas:
            print(persona.__str__())

    def guardar_personas(self):
        fichero = open("lista_de_personas", "wb")
        pickle.dump(self.personas, fichero)
        fichero.close()
        del fichero
```

Así, si ejecutamos ahora el siguiente bloque de código:

```python
lista_personas = ListaPersonas()

sandra = Persona("Sandra", "Femenino", "29")
lista_personas.agregar_personas(sandra)

antonio = Persona("Antonio", "Masculino", "39")
lista_personas.agregar_personas(antonio)

ana = Persona("Ana", "Femenino", "20")
lista_personas.agregar_personas(ana)
```

```bash
El fichero está vacío.
Se ha creado una persona nueva con el nombre de Sandra
Se ha creado una persona nueva con el nombre de Antonio
Se ha creado una persona nueva con el nombre de Ana
```

Recuperemos la información guardada en el fichero externo, utilizando para ello
un método que añadiremos a la clase `ListaPersonas`, `mostrar_informacion`:

```python
class ListaPersonas:
    personas = []

    def __init__(self):
        fichero = open("lista_de_personas", "ab+")
        fichero.seek(0)  # Desplazamos cursor al principio

        try:
            self.personas = pickle.load(fichero)  # Cargamos información
            print("Se cargaron {} personas.".format(len(self.personas)))
        except EOFError:
            print("El fichero está vacío.")  # Para la primera vez que abrimos
        finally:
            fichero.close()
            del fichero

    def agregar_personas(self, persona):
        self.personas.append(persona)
        self.guardar_personas()

    def mostrar_personas(self):
        for persona in self.personas:
            print(persona.__str__())

    def guardar_personas(self):
        fichero = open("lista_de_personas", "wb")
        pickle.dump(self.personas, fichero)
        fichero.close()
        del fichero

    def mostrar_informacion(self):
        print("La información del fichero externo es la siguiente:")
        for persona in self.personas:
            print(persona.__str__())
```

Así,

```python
lista_personas.mostrar_informacion()
```

```bash
La información del fichero externo es la siguiente:
Sandra Femenino 29
Antonio Masculino 39
Ana Femenino 20
```

Agreguemos una nueva persona. Para ello, tecleamos por ejemplo:

```python
juan = Persona("Juan", "Masculino", "47")
lista_personas.agregar_personas(juan)

lista_personas.mostrar_informacion()
```

```bash
Se ha creado una persona nueva con el nombre de Juan
La información del fichero externo es la siguiente:
Sandra Femenino 29
Antonio Masculino 39
Ana Femenino 20
Juan Masculino 47
```
