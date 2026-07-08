---
title: "Curso de Python #02 (Nivel básico)"
summary: Tipos y variables
date: 2019-07-07
lastmod: 2026-07-08
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

### 1. Tipos, operadores y variables

#### 1.1. Vídeo

{{< youtube u4I9PqhqCo8 >}}

#### 1.2. Notas personales

Los **tipos de datos** disponibles en _Python_ son:

- Numéricos
    - Enteros (`int`)
    - Coma flotante (`float`)
    - Complejos
- Textos
- Booleanos
    - `True`
    - `False`

Los principales **operadores** en _Python_ son:

- Aritméticos: `+`, `-`, `*`, `/`, `%`, `**` y `//`.
- Comparación: `==`, `!=`, `>`, `<`, `>=` y `<=`.
- Lógicos: `AND`, `OR` y `NOT`.
- Asignación: `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `**=` y `//=`.
- Especiales: `is`, `is not`, `in` y `not in`.

Los operadores aritméticos nos permiten utilizar _Python_ a modo de calculadora.

```python
>>> 5 + 6 # Suma
11
>>> 11 - 8 # Resta
3
>>> 2 * 6 # Multiplicación
12
>>> 7 / 2 # División
3.5
>>> 10 % 3 # Módulo
1
>>> 5 ** 2 # Exponenciación
25
>>> 7 // 2 # División entera
3
```

Una **variable** es un espacio en la memoria del ordenador donde se almacenará
un valor que podrá cambiar durante la ejecución del programa. Para declararla,
utilizamos el patrón `nombre = valor` y su tipo lo establece el contenido, no el
contenedor.

_Nota_: en _Python_ todo son objetos (variables, números...).

```python
>>> nombre = 5
>>> type(nombre)
<class 'int'>
>>> nombre = "Alexis"
>>> type(nombre)
<class 'str'>
>>> nombre = 5.2
>>> type(nombre)
<class 'float'>
```

Definimos cadenas de texto mediante los símbolos `'`, `"` y `'''`, permitiendo
esta última opción saltos de líneas.

```python
>>> mensaje = 'Esto es un mensaje.'
>>> print(mensaje)
Esto es un mensaje.
>>> mensaje = "Esto es un mensaje."
>>> print(mensaje)
Esto es un mensaje.
>>> mensaje = '''Esto es un mensaje
... con tres saltos
... de línea.'''
>>> print(mensaje)
Esto es un mensaje
con tres saltos
de línea.
```

Los operadores de comparación suelen aparecer en bloques condicionales.

```python
>>> numero1 = 5
>>> numero2 = 7
>>> if numero1 > numero2:
...     print("El número 1 es mayor.")
... else:
...     print("El número 2 es mayor.")
...
El número 2 es mayor.
```

_Nota_: no confundir el operador de asignación `=` con el operador de
comparación `==`.

```python
>>> numero1 = 2
>>> numero2 = 3
>>> if numero1 == numero2:
...     print("Los números son iguales.")
... else:
...     print("Los números son diferentes.")
...
Los números son diferentes.
```

### 2. Funciones I

#### 2.1. Vídeo

{{< youtube VY448UWAQ_0 >}}

#### 2.2. Notas personales

Una **función** es un conjunto de líneas de código agrupadas, que funcionan como
una unidad realizando una tarea específica. Puede devolver valores, tener
parámetros o argumentos y recibe el nombre de **método** cuando está definida
dentro de una clase.

En _Python_ existen funciones predifinidas, como por ejemplo `print()`. Su
principal utilidad es la reutilización de código y su sintaxis es:

```python
def nombre(parámetros):
    instrucciones de la función
    return(opcional)
```

Ejecutamos (o llamamos) una función tecleando `nombre_función(parámetros)`.

A continuación, dejamos de lado el IDLE de _Sublime Text 3_ y pasamos a compilar
directamente ficheros desde el propio editor. Para ello, desplegamos el menú
`Tools` y en el apartado `Build System` escogemos la opción `Python`. Acto
seguido, creamos el fichero `funciones.py`, que contendrá la instrucción

```python
print("Estamos aprendiendo Python.")
```

y utilizamos la combinación de teclas `ctrl + b` para compilar. En la parte
inferior de la ventana aparecerá el resultado de la ejecución y el tiempo
invertido.

Ampliemos el anterior fichero a

```python
print("Estamos aprendiendo Python.")
print("Estamos aprendiendo instrucciones básicas.")
print("Poco a poco iremos avanzando.")
```

e imaginemos que necesitamos que las anteriores tres líneas se impriman cinco
veces. Podemos, simplemente, copiar y pegar el anterior bloque de código
reiteradamente:

```python
print("Estamos aprendiendo Python.")
print("Estamos aprendiendo instrucciones básicas.")
print("Poco a poco iremos avanzando.")

print("Estamos aprendiendo Python.")
print("Estamos aprendiendo instrucciones básicas.")
print("Poco a poco iremos avanzando.")

print("Estamos aprendiendo Python.")
print("Estamos aprendiendo instrucciones básicas.")
print("Poco a poco iremos avanzando.")

print("Estamos aprendiendo Python.")
print("Estamos aprendiendo instrucciones básicas.")
print("Poco a poco iremos avanzando.")

print("Estamos aprendiendo Python.")
print("Estamos aprendiendo instrucciones básicas.")
print("Poco a poco iremos avanzando.")
```

Las funciones nos permiten reutilizar código para, precisamente, evitar que
actuemos como arriba. Definamos una función llamada `mensaje()` y ejecutémosla
tantas veces como deseemos.

```python
def mensaje():
    print("Estamos aprendiendo Python.")
    print("Estamos aprendiendo instrucciones básicas.")
    print("Poco a poco iremos avanzando.")
```

Ahora, la tarea que buscábamos realizar quedaría como:

```python
mensaje()
mensaje()
mensaje()
mensaje()
mensaje()
```

Entre distintas llamadas a una función puede haber cualquier otro tipo de
instrucción:

```python
mensaje()

print("Ejecutando código fuera de función")

mensaje()
```

### 3. Funciones II

#### 3.1. Vídeo

{{< youtube vawEHhV_HFA >}}

#### 3.2. Notas personales

Comencemos definiendo una función que suma dos números dados (5 y 7), mediante
el mecanismo aprendido en la lección anterior:

```python
def suma():
    num1 = 5
    num2 = 7
    print(num1 + num2)


suma()
```

Podemos reutilizar tantas veces como queramos la función `suma()`. No obstante,
su utilidad así declarada es bastante limitada. Nos gustaría que no siempre
sumara los dos mismos valores, sino aquellos que nos interesen en cada llamada.
Para ello emplearemos los **parámetros** o **argumentos**.

_Nota_: aunque el autor del curso se refiere a los términos ''parámetros'' y
''argumentos'' casi como si fueran sinónimos, en realidad hay un sutil matiz que
los diferencia: los **parámetros** son las variables que aparecen en la
definición de una función o método; cuando se produce la llamada a dicha
función, los **argumentos** son los datos que pasamos a los parámetros de la
mencionada función.

Definamos de nuevo la función `suma()`, ahora con dos parámetros, con el
objetivo de que realice la suma de dos números que pasaremos como argumentos:

```python
def suma(num1, num2):
    print(num1 + num2)


suma(5, 7)  # 12
suma(2, 3)  # 5
suma(35, 358)  # 393
```

Tal y como está declarada la nueva función de suma, **obligatoriamente** hemos
de pasarle dos argumentos o sino aparecerán errores.

```python
suma(7)
# TypeError: suma() missing 1 required positional argument: 'num2'
```

```python
suma(1, 2, 3)
# TypeError: suma() takes 2 positional arguments but 3 were given
```

Puede resultar conveniente, por legibilidad, pasar los argumentos a una función
utilizando el esquema `parámetro=valor`.

```python
suma(num1=5, num2=7)  # 12
```

Además, las funciones

- pueden poseer parámetros de diferentes tipos y
- devuelven valores siempre y cuando empleemos la instrucción `return`.

```python
def suma(num1, num2):
    resultado = num1 + num2
    return resultado


suma(5, 7)
```

La ejecución del anterior bloque de código no muestra resultado alguno en la
consola. La función devuelve el resultado, pero no lo hemos imprimido. Así,

```python
print(suma(5, 7))  # 12
```

Una ventaja de utilizar la instrucción `return` reside en que podemos almacenar
los valores que devuelve una función en variables y trabajar posteriormente con
ellas.

```python
almacena_resultado = suma(5, 8)
print(almacena_resultado)  # 13

actualiza_resultado = suma(almacena_resultado, 8)
print(actualiza_resultado)  # 13 + 8 = 21
```

_Nota técnica_: _Python_ pasa siempre los valores por referencia, no por valor.

### 4. Listas

#### 4.1. Vídeo

{{< youtube Q8hugySbLQQ >}}

#### 4.2. Notas personales

Una **lista** es una estructura de datos que nos permite almacenar gran cantidad
de valores. En _Python_, estos pueden añadirse de manera dinámica y ser de
diferentes tipos.

Su sintaxis es `nombre = [elem1, elem2, elem3...]` y los elementos están
localizados mediante un índice, que en _Python_ comienza por 0.

A continuación, creemos una lista con cuatro elementos de tipo texto y veamos
cómo imprimirla y acceder a elementos concretos de ella:

```python
mi_lista = ["María", "Pepe", "Marta", "Antonio"]

print(mi_lista)  # ["María", "Pepe", "Marta", "Antonio"]
print(mi_lista[:])  # ["María", "Pepe", "Marta", "Antonio"]

print(mi_lista[2])  # Marta
print(mi_lista[0])  # María
```

Si empleamos índices que superan el rango de elementos de una lista, _Python_
nos arroja un error:

```python
print(mi_lista[4])
# IndexError: list index out of range
```

No obstante, sí es posible utilizar índices con valor negativo, que nos permiten
acceder (empezando por `-1`) a los elementos de una lista desde la derecha:

```python
print(mi_lista[-1]) # Antonio
print(mi_lista[-3]) # Pepe
```

Obviamente, esta estrategia también está limitada por el número de elementos de
la lista y no podemos pasar índices negativos fuera de su correspondiente rango:

```python
print(mi_lista[-5])
# IndexError: list index out of range
```

Además, podemos acceder a porciones de una lista, mediante la sintaxis
`nombre[a:b]`, que extrae todos los elementos comprendidos entre los índices `a`
y el anterior a `b`. Por ejemplo:

```python
print(mi_lista[0:2])  # ["María", "Pepe"]
print(mi_lista[0:1])  # ["María"]
print(mi_lista[-3:-1])  # ["Pepe", "Marta"]
```

Se pueden omitir algunos de los anteriores índices indicados y _Python_
sobreentiende que comienza o acaba en el extremo correspondiente:

```python
print(mi_lista[:2])  # ["María", "Pepe"]
print(mi_lista[2:])  # ["Marta", "Antonio"]
print(mi_lista[-2:])  # ["Marta", "Antonio"]
```

_Nota técnica_: cuando accedemos a una porción, se conserva el tipo lista, pero
no así si se extrae un único elemento en particular.

```python
print(type(mi_lista[2]))  # <class 'str'>
print(type(mi_lista[2:3]))  # <class 'list'>
```

Agregamos elementos al final de la lista utilizando `.append()`:

```python
mi_lista.append("Sandra")
print(mi_lista)  # ["María", "Pepe", "Marta", "Antonio", "Sandra"]
```

Usaremos `.insert(posición, elemento)`, si buscamos añadir un elemento en un
punto intermedio:

```python
mi_lista.insert(2, "Paco")
print(mi_lista)  # ["María", "Pepe", "Paco", "Marta", "Antonio", "Sandra"]
```

Es posible agregar varios elementos al final de una lista utilizando `.extend()`
y pasando como argumento otra lista:

```python
mi_compra = ["Manzanas"]
print(mi_compra)  # ["Manzanas"]

mi_compra.extend(["Aguacates", "Sandía"])
print(mi_compra)  # ["Manzanas", "Aguacates", "Sandía"]
```

Para acceder al índice de un elemento, empleamos `.index(elemento)`:

```python
print(mi_lista.index("Antonio"))  # 4
print(mi_compra.index("Sandía"))  # 2
```

Si intentamos acceder al índice de elementos que no están incluidos en la lista,
_Python_ arroja un error:

```python
print(mi_compra.index("Melón"))
# ValueError: 'Melón' is not in list
```

En una lista, puede haber elementos iguales en posiciones distintas. La función
`.index()` nos devolverá el valor del índice del primer elemento repetido:

```python
mi_compra.extend(mi_compra)
print(mi_compra)  # ["Manzanas", "Aguacates", "Sandía", "Manzanas", "Aguacates", "Sandía"]
print(mi_compra.index("Manzanas"))  # 0
```

Para comprobar si un elemento se encuentra o no en una lista, utilizamos `in`:

```python
print("Pepe" in mi_lista)  # True
print("Ana" in mi_lista)  # False
```

Tal y como mencionamos arriba, una lista puede almacenar sin problemas elementos
de diferentes tipos:

```python
mezcla = ["Alexis", True, 10, 3.14]
print(mezcla)  # ["Alexis", True, 10, 3.14]
```

Para eliminar elementos, usamos `.remove()`:

```python
mezcla.remove(True)
print(mezcla)  # ["Alexis", 10, 3.14]
```

En particular, podemos suprimir el último elemento de una lista mediante
`.pop()`:

```python
mezcla.pop()
print(mezcla)  # ["Alexis", 10]
```

El operador `+` concatena listas:

```python
lista1 = ["Ana", 5]
lista2 = [True, 2.1]
lista3 = lista1 + lista2
print(lista3)  # ["Ana", 5, True, 2.1]
```

El operador `*` repite la lista un número determinado de veces.

```python
print(lista1 * 2)  # ["Ana", 5, "Ana", 5]
```

### 5. Tuplas

#### 5.1. Vídeo

{{< youtube Ufqh8aoR9hE >}}

#### 5.2. Notas personales

Una **tupla** es una lista inmutable que

- no permite añadir, eliminar, mover elementos...
- permite la extracción de porciones, que continuan siendo tuplas, y
- posibilita búsquedas de índice (`.index()`) y comprobaciones de si un elemento
  pertenece o no a ella (`in`).

Son útiles porque

- son más rápidas en cuanto a ejecución se refiere,
- requieren menos espacio (mayor optimización),
- formatean cadenas de texto, y
- pueden utilizarse como claves en un diccionario, a diferencia de las listas.

Su sintaxis es `nombre = (elem1, elem2, elem3...)`, siendo el uso de los
paréntesis opcional aunque recomendable. El acceso a los elementos funciona como
en las listas.

```python
mi_tupla = ("Alexis", 10, 1, 1995)

print(mi_tupla)  # ("Alexis", 10, 1, 1995)
print(mi_tupla[1])  # 10
print(mi_tupla[-1])  # 1995
```

Existen funciones que nos permiten convertir tuplas en listas (`list()`) y
viceversa (`tuple()`):

```python
mi_lista = list(mi_tupla)
print(mi_lista)  # ["Alexis", 10, 1, 1995]

mi_tupla = tuple(mi_lista)
print(mi_tupla)  # ("Alexis", 10, 1, 1995)
```

Comprobamos la pertenencia de un elemento a la tupla mediante `in`:

```python
print("Alexis" in mi_tupla)  # True
print(3.14 in mi_tupla)  # False
```

Con `.count()` obtenemos el número de elementos que se encuentran dentro de una
tupla:

```python
mi_tupla = ("Alexis", 1, 2, 2, True, 2, "Alexis")

print(mi_tupla.count("Alexis"))  # 2
print(mi_tupla.count(1))  # 2 (True cuenta como 1)
print(mi_tupla.count(2))  # 3
```

El método `len` nos permite hallar la longitud de una tupla, siendo el índice
del último elemento igual a `len - 1`:

```python
print(len(mi_tupla))  # 7
print(mi_tupla[len(mi_tupla) - 1])  # "Alexis"
```

Podemos crear tuplas unitarias siguiendo el patrón `nombre = (elem,)`:

```python
mi_tupla = ("Alexis",)

print(type(mi_tupla))  # <class 'tuple'>
print(len(mi_tupla))  # 1
```

Como mencionamos, los paréntesis son opcionales:

```python
mi_tupla = "Alexis", 3.14, True, 10

print(type(mi_tupla))  # <class 'tuple'>
print(mi_tupla)  # ("Alexis", 3.14, True, 10)
```

Esta sintaxis se conoce como **empaquetado de tupla** y hemos de ser cautos,
pues en un futuro, al combinarla con el uso de funciones, puede dar lugar a
confusiones.

El proceso inverso, **desempaquetado de tuplas**, nos permite asignar los
elementos de una tupla a diferentes variables:

```python
mi_tupla = ("Alexis", 3.14, True, 10)

nombre, pi, alto, mes = mi_tupla

print(nombre)  # Alexis
print(pi)  # 3.14
print(alto)  # True
print(mes)  # 10
```

### 6. Diccionarios

#### 6.1. Vídeo

{{< youtube 2OmgHl8lp0I >}}

#### 6.2. Notas personales

Un **diccionario** es una estructura de datos que nos permite almacenar valores
de diferentes tipos (enteros, cadenas de texto, decimales...) e incluso listas,
tuplas y otros diccionarios.

Su principal característica reside en que cada dato se almacena asociado a una
clave única, de tal forma que se crea una relación de tipo `clave:valor` para
cada elemento guardado. Además, los mencionados elementos no están ordenados, es
decir, el orden es indiferente (por la presencia las referidas claves únicas) a
la hora de guardar información en un diccionario.

Su sintaxis es `nombre = {clave:valor}`.

Creemos un diccionario que almacene países (clave) y capitales (valor), y veamos
cómo se accede a cada uno de sus elementos:

```python
mi_dicc = {"Alemania": "Berlin",
           "Francia": "París",
           "Reino Unido": "Londres",
           "España": "Madrid"}

print(mi_dicc["Francia"])  # París
print(mi_dicc["España"])  # Madrid

print(mi_dicc)  # {'Alemania': 'Berlin', 'Francia': 'París', 'Reino Unido': 'Londres', 'España': 'Madrid'}
```

Agregamos nuevos elementos al diccionario con el patrón `nombre[clave] = valor`:

```python
mi_dicc["Italia"] = "Lisboa"

print(mi_dicc)  # {'Alemania': 'Berlin', 'Francia': 'París', 'Reino Unido': 'Londres', 'España': 'Madrid', 'Italia': 'Lisboa'}
```

Modificamos un valor asignado a una clave simplemente sobreescribiéndolo:

```python
mi_dicc["Italia"] = "Roma"

print(mi_dicc)  # {'Alemania': 'Berlin', 'Francia': 'París', 'Reino Unido': 'Londres', 'España': 'Madrid', 'Italia': 'Roma'}
```

Suprimimos elementos con `del`:

```python
del mi_dicc["Reino Unido"]

print(mi_dicc)  # {'Alemania': 'Berlin', 'Francia': 'París', 'España': 'Madrid', 'Italia': 'Roma'}
```

Generemos un diccionario que presente diferentes tipos de datos:

```python
mi_dicc = {"Alemania": "Berlín",
           23: "Jordan",
           "Mosqueteros": 3}

print(mi_dicc)  # {'Alemania': 'Berlín', 23: 'Jordan', 'Mosqueteros': 3}
```

Empleemos una tupla (el procedimiento sería similar si optamos por una lista)
para asignar la clave a cada uno de los valores:

```python
mi_tupla = ("España", "Francia", "Reino Unido", "Alemania")
mi_dicc = {mi_tupla[0]: "Madrid",
           mi_tupla[1]: "París",
           mi_tupla[2]: "Londres",
           mi_tupla[3]: "Berlín"}

print(mi_dicc)  # {'España': 'Madrid', 'Francia': 'París', 'Reino Unido': 'Londres', 'Alemania': 'Berlín'}

print(mi_dicc["España"])  # Madrid
print(mi_dicc[mi_tupla[0]])  # Madrid
```

También podemos almacenar tuplas (o listas...) como valores:

```python
mi_dicc = {23: "Jordan",
           "Nombre": "Michael",
           "Equipo": "Chicago",
           "Anillos": (1991, 1992, 1993, 1996, 1997, 1998)}

print(mi_dicc)  # {23: 'Jordan', 'Nombre': 'Michael', 'Equipo': 'Chicago', 'Anillos': (1991, 1992, 1993, 1996, 1997, 1998)}
print(mi_dicc["Equipo"])  # Chicago
print(mi_dicc["Anillos"])  # (1991, 1992, 1993, 1996, 1997, 1998)
```

Asimismo, guardemos un diccionario dentro de otro:

```python
mi_dicc = {23: "Jordan",
           "Nombre": "Michael",
           "Equipo": "Chicago",
           "Anillos": {"Temporadas": (1991, 1992, 1993, 1996, 1997, 1998)}}

print(mi_dicc)  # {23: 'Jordan', 'Nombre': 'Michael', 'Equipo': 'Chicago', 'Anillos': {'Temporadas': (1991, 1992, 1993, 1996, 1997, 1998)}}
print(mi_dicc["Anillos"])  # {'Temporadas': (1991, 1992, 1993, 1996, 1997, 1998)}
```

Algunos métodos interesantes a conocer son:

- `.keys()`, para acceder a las claves de un diccionario;
- `.values()`, para conocer los valores de un diccionario; y
- `len()`, para averiguar la longitud de un diccionario:

```python
print(mi_dicc.keys())  # dict_keys([23, 'Nombre', 'Equipo', 'Anillos'])
print(mi_dicc.values())  # dict_values(['Jordan', 'Michael', 'Chicago', {'Temporadas': (1991, 1992, 1993, 1996, 1997, 1998)}])
print(len(mi_dicc))  # 4
```
