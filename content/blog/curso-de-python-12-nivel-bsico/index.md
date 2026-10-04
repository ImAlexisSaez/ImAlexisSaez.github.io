---
title: "Curso de Python #12 (Nivel básico)"
summary: Temas avanzados
date: 2019-09-07
lastmod: 2026-10-04
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

### 1. Funciones lambda

#### 1.1. Vídeo

{{< youtube tfYLcHbjc_A >}}

#### 1.2. Notas personales

En esta lección, estudiaremos las funciones _lambda_. Una función **lambda** es
una función anónima, y se utilizan en _Python_ a la hora de programar para
abreviar, ya que aligera la sintaxis del código. Además, no ocupan lugar en el
espacio de nombres asociado a las funciones de una aplicación.

Cualquier tarea que llevemos a cabo con una función _lambda_ se puede
desarrollar mediante una función normal, pero no así a la inversa (sobre todo
cuando su lógica es compleja).

Por ejemplo, para calcular el área de un triángulo, podemos construir la
función:

```python
def area_triangulo(b, h):
    return b * h / 2
```

```python
for b in range(1, 10, 5):
    for h in range(1, 10, 5):
        print(
            f"El área del triángulo de base {b} y altura {h} es {area_triangulo(b, h)}."
        )
```

```bash
El área del triángulo de base 1 y altura 1 es 0.5.
El área del triángulo de base 1 y altura 6 es 3.0.
El área del triángulo de base 6 y altura 1 es 3.0.
El área del triángulo de base 6 y altura 6 es 18.0.
```

No obstante, una función tan sencilla puede ser abreviada como una función
_lambda_.

```python
area_triangulo = lambda b, h: b * h / 2

for b in range(1, 10, 5):
    for h in range(1, 10, 5):
        print(
            f"El área del triángulo de base {b} y altura {h} es {area_triangulo(b, h)}."
        )
```

```bash
El área del triángulo de base 1 y altura 1 es 0.5.
El área del triángulo de base 1 y altura 6 es 3.0.
El área del triángulo de base 6 y altura 1 es 3.0.
El área del triángulo de base 6 y altura 6 es 18.0.
```

_Nota_: las funciones _lambda_, generalmente, no se asignan a variables. En
tales casos, conviene hacer uso de la instrucción `def` y definir una función
tal y como estamos habituados.

Usadas ''al vuelo'', su sintaxis queda como sigue:

```python
print("El cubo de 3 es " + str((lambda x:x**3) (3)))
```

```bash
El cubo de 3 es 27
```

### 2. Filter

#### 2.1. Vídeo

{{< youtube mTJKU7IxL0U >}}

#### 2.2. Notas personales

En esta lección, estudiaremos la función `filter()`, que forma parte de un
conjunto de funciones conocidas como ''de orden superior'' y nos permiten
utilizar en _Python_ el paradigma de **programación funcional**. La mencionada
función verifica que los elementos de una secuencia cumplen una condición,
devolviendo un iterador compuesto por aquellos que la satisfacen.

Por ejemplo, podemos construir un programa que detecte qué números son pares y
cuáles no lo son, devolviéndonos una lista compuesta por los que verifiquen
dicha condición:

```python
def numero_par(num):
    if num % 2 == 0:
        return True


numeros = [17, 24, 7, 39, 8, 51, 92]

print(filter(numero_par, numeros))  # objeto iterable

print(list(filter(numero_par, numeros)))
```

```bash
<filter object at 0x0000029E5BA262B0>
[24, 8, 92]
```

La función `numero_par()` la podemos abreviar un tanto como sigue:

```python
def numero_par(num):
    return num % 2 == 0
```

Es más, como es tan sencilla, incluso podemos prescindir de ella utilizando una
función _lambda_:

```python
numeros = [17, 24, 7, 39, 8, 51, 92]

print(list(filter(lambda x: x % 2 == 0, numeros)))
```

```bash
[24, 8, 92]
```

Habitualmente, utilizaremos la función `filter()` para filtrar objetos. Por
ejemplo, supongamos que tenemos varias instancias de la clase `Empleado` y
deseamos filtrarlas por el valor de uno de sus atributos:

```python
class Empleado:
    def __init__(self, nombre, cargo, salario):
        self.nombre = nombre
        self.cargo = cargo
        self.salario = salario

    def __str__(self):
        return f"{self.nombre} trabaja como {self.cargo} y cobra {self.salario} €."


lista_empleados = [
    Empleado("Juan", "Director", 75000),
    Empleado("Ana", "Presidenta", 85000),
    Empleado("Antonio", "Administrativo", 25000),
    Empleado("Sara", "Secretaria", 27000),
    Empleado("Mario", "Botones", 21000)
]

salarios_altos = filter(lambda e: e.salario > 50000, lista_empleados)

[print(s.__str__()) for s in salarios_altos]
```

```bash
Juan trabaja como Director y cobra 75000 €.
Ana trabaja como Presidenta y cobra 85000 €.
```

A modo de curiosidad, ya que me he avanzado y he utilizado comprensiones de
listas (ver la última línea del bloque de código anterior), resulta que mediante
ellas, en este ejemplo concreto, no es necesario recurrir al uso de la función
`filter()`:

```python
class Empleado:
    def __init__(self, nombre, cargo, salario):
        self.nombre = nombre
        self.cargo = cargo
        self.salario = salario

    def __str__(self):
        return f"{self.nombre} trabaja como {self.cargo} y cobra {self.salario} €."


lista_empleados = [
    Empleado("Juan", "Director", 75000),
    Empleado("Ana", "Presidenta", 85000),
    Empleado("Antonio", "Administrativo", 25000),
    Empleado("Sara", "Secretaria", 27000),
    Empleado("Mario", "Botones", 21000)
]

[print(e.__str__()) for e in lista_empleados if e.salario > 50000]
```

```bash
Juan trabaja como Director y cobra 75000 €.
Ana trabaja como Presidenta y cobra 85000 €.
```

### 3. Map

#### 3.1. Vídeo

{{< youtube 4dkjpHI6vpA >}}

#### 3.2. Notas personales

En esta lección, estudiaremos la función `map()`, que, como `filter()`, también
forma parte de un conjunto de funciones conocidas como ''de orden superior'' y
nos permiten utilizar en _Python_ el paradigma de **programación funcional**.

La filosofía de ambas funciones es ciertamente similar ya que, por ejemplo,
`map()` aplica una función a cada elemento de un objeto de tipo iterable
(listas, tuplas...) devolviendo a su vez un objeto de tipo iterable que contiene
los resultados de dicha aplicación.

Retomemos la clase definida en la lección anterior, junto con la lista de
empleados generada:

```python
class Empleado:
    def __init__(self, nombre, cargo, salario):
        self.nombre = nombre
        self.cargo = cargo
        self.salario = salario

    def __str__(self):
        return f"{self.nombre} trabaja como {self.cargo} y cobra {self.salario} €."


lista_empleados = [
    Empleado("Juan", "Director", 6700),
    Empleado("Ana", "Presidenta", 7500),
    Empleado("Antonio", "Administrativo", 1200),
    Empleado("Sara", "Secretaria", 1250),
    Empleado("Mario", "Botones", 1000)
]
```

_Nota_: hemos modificado los salarios para que sus cantidades sean mensuales, en
lugar de las anuales declaradas en la lección anterior.

Imaginemos ahora que todos los empleados recibien un extra monetario en forma de
comisión, que hemos de agregar a su salario mensual.

```python
def calcula_comision(empleado):
    empleado.salario *= 1.03
    return empleado


lista_empleados_comision = map(calcula_comision, lista_empleados)

[print(e) for e in lista_empleados_comision]
```

```bash
Juan trabaja como Director y cobra 6901.0 €.
Ana trabaja como Presidenta y cobra 7725.0 €.
Antonio trabaja como Administrativo y cobra 1236.0 €.
Sara trabaja como Secretaria y cobra 1287.5 €.
Mario trabaja como Botones y cobra 1030.0 €.
```

¿Y si queremos aplicar la comisión solamente a aquellos trabajadores que tengan
un salario inferior a 3000 euros?

```python
def calcula_comision(empleado):
    if empleado.salario <= 3000:
        empleado.salario *= 1.03
    return empleado


lista_empleados_comision = map(calcula_comision, lista_empleados)

[print(e) for e in lista_empleados_comision]
```

```bash
Juan trabaja como Director y cobra 6700 €.
Ana trabaja como Presidenta y cobra 7500 €.
Antonio trabaja como Administrativo y cobra 1236.0 €.
Sara trabaja como Secretaria y cobra 1287.5 €.
Mario trabaja como Botones y cobra 1030.0 €.
```

### 4. Expresiones regulares I

#### 4.1. Vídeo

{{< youtube qpwn3gRtxCo >}}

#### 4.2. Notas personales

En esta lección, comenzaremos el estudio de las **expresiones regulares** en
_Python_, que son una secuencia de caracteres que forman un patrón de búsqueda y
sirven para el trabajo y procesamiento de texto. Por ejemplo, podemos estar
interesados, entre otras tareas, en:

- Buscar un texto que se ajuste a un formato determinado (correo electrónico).
- Buscar si existe o no una cadena de caracteres dentro de un texto.
- Contar el número de coincidencias dentro de un texto.

Conviene que consultemos la
[documentación oficial](https://docs.python.org/3/library/re.html) del módulo
asociado a las expresiones regulares, `re`, en _Python_.

A continuación, veamos algunos ejemplos sencillos. Empecemos ilustrando el uso
del método `search()`, que nos permite buscar una cadena de texto concreta y nos
ofrece su localización:

```python
import re

cadena = "Vamos a aprender expresiones regulares."

print(re.search("aprender", cadena))
```

```bash
<re.Match object; span=(8, 16), match='aprender'>
```

Apreciamos que la ejecución nos devuelve un objeto, de tipo `Match`, que en el
intervalo de caracteres `(8, 16)` ha encontrado la cadena de texto de interés,
`aprender`.

Ahora bien, si insertamos una cadena de texto que no figure en la variable
`cadena`, el resultado que arroja la ejecución del programa es `None`:

```python
import re

cadena = "Vamos a aprender expresiones regulares."

print(re.search("Python", cadena))
```

```bash
None
```

Obviamente, podemos pasar variables a la función `search()`:

```python
import re

cadena = "Vamos a aprender expresiones regulares."

texto_buscar = "aprender"

if re.search(texto_buscar, cadena) is not None:
    print("Texto encontrado.")
else:
    print("Texto no encontrado.")
```

```bash
Texto encontrado.
```

Hemos encontrado el texto, efectivamente, pero, ¿en qué carácter comienza?
Utilizando el método `start()` hallamos la respuesta:

```python
import re

cadena = "Vamos a aprender expresiones regulares."

texto_buscar = "aprender"

texto_encontrado = re.search(texto_buscar, cadena)

print(texto_encontrado.start())
```

```bash
8
```

Análogamente,

```python
print(texto_encontrado.end())
```

```bash
16
```

Al hilo de las acciones anteriores, el método `span()` nos devuelve una tupla
con los valores mostrados arriba:

```python
print(texto_encontrado.span())
```

```bash
(8, 16)
```

Finalmente, examinemos la utilidad del método `findall()`, para lo cual hemos de
ampliar un poco la cadena de texto original suministrada:

```python
import re

cadena = '''
    Vamos a aprender expresiones regulares en Python.
    Python es un lenguaje de sintaxis sencilla.'''

texto_buscar = "Python"

print(re.findall(texto_buscar, cadena))
```

```bash
['Python', 'Python']
```

Accedemos a una lista que contiene el texto de interés, tantas veces como
repeticiones figuren en él. Empleando ahora la función `len()`:

```python
import re

cadena = '''
    Vamos a aprender expresiones regulares en Python.
    Python es un lenguaje de sintaxis sencilla.'''

texto_buscar = "Python"

print(len(re.findall(texto_buscar, cadena)))
```

```bash
2
```

### 5. Expresiones regulares II

#### 5.1. Vídeo

{{< youtube V8316ao08tQ >}}

#### 5.2. Notas personales

En esta lección, continuaremos el estudio de las expresiones regulares abordando
los denominados **metacaracteres** (o _caracteres comodín_).

Empecemos con las _anclas_, que dentro de una lista nos van a permitir encontrar
coincidencias al principio y al final de cada elemento de esta. Por ejemplo,
mediante el ancla `^`, las buscamos al inicio de la cadena de texto:

```python
import re

lista_nombres = ["Ana Gómez",
                 "María Martín",
                 "Sandra López",
                 "Santiago Martín"]

for nombre in lista_nombres:
    if re.findall("^Sandra", nombre):
        print(nombre)
```

```bash
Sandra López
```

El último bucle lo podemos compactar utilizando comprensiones de listas de la
siguiente forma:

```python
[print(nombre) for nombre in lista_nombres if re.findall("^Sandra", nombre)]
```

Así, podemos extraer de `lista_nombres`, si nos interesa, todos los nombres que
comiencen por `S`:

```python
import re

lista_nombres = ["Ana Gómez",
                 "María Martín",
                 "Sandra López",
                 "Santiago Martín"]

[print(nombre) for nombre in lista_nombres if re.findall("^S", nombre)]
```

```bash
Sandra López
Santiago Martín
```

¿Y si queremos todos los nombres cuyo apellido sea `Martín`? El ancla `$` es el
metacarácter que hemos de emplear:

```python
import re

lista_nombres = ["Ana Gómez",
                 "María Martín",
                 "Sandra López",
                 "Santiago Martín"]

[print(nombre) for nombre in lista_nombres if re.findall("Martín$", nombre)]
```

```bash
María Martín
Santiago Martín
```

Veamos otro ejemplo de su uso, trabajando ahora con una lista de dominios,
estamos interesados en encontrar aquellos que acaben en `.es`:

```python
import re

urls = ["https://pildorasinformaticas.es",
        "ftp://pildorasinformaticas.es",
        "https://pildorasinformaticas.com",
        "ftp://pildorasinformaticas.com"]

[print(url) for url in urls if re.findall(".es$", url)]
```

```bash
https://pildorasinformaticas.es
ftp://pildorasinformaticas.es
```

Quizá nos interese hallar qué dominios son de tipo `ftp`:

```python
import re

urls = ["https://pildorasinformaticas.es",
        "ftp://pildorasinformaticas.es",
        "https://pildorasinformaticas.com",
        "ftp://pildorasinformaticas.com"]

[print(url) for url in urls if re.findall("^ftp", url)]
```

```bash
ftp://pildorasinformaticas.es
ftp://pildorasinformaticas.com
```

Por otro lado, tenemos las **clases de caracteres**, que nos permiten introducir
patrones de búsqueda utilizando el operador `[]`. Cambiemos ligeramente los
dominios para ver su utilidad (buscando aquellos dominios que contengan el
carácter `ñ`):

```python
import re

urls = ["https://pildorasinformaticas.es",
        "ftp://pildorasinformaticas.es",
        "https://pildorasinformaticas.com",
        "ftp://pildorasinformaticas.com",
        "https://informaticaenespaña.es"]

[print(url) for url in urls if re.findall("[ñ]", url)]
```

```bash
https://informaticaenespaña.es
```

Un ejemplo un tanto más complejo: en una lista de palabras, queremos encontrar
si se hallan las palabras `niños` y `niñas`. Como solo se diferencias ambas
cadenas en un carácter, podemos escribir:

```python
import re

urls = ["hombres", "mujeres", "mascotas", "niños", "niñas"]

[print(url) for url in urls if re.findall("niñ[oa]s", url)]
```

```bash
niños
niñas
```

_Nota_: al escribir `[oa]` no exigimos que deban estar presentes los dos
caracteres y en ese preciso orden. La función `findall()` nos arrojará una
coincidencia cuando alguno de los dos esté presente (o ambos, siendo indiferente
el orden en el que se encuentren en este último caso).

Esta estrategia es también útil cuando lidiamos con tildes:

```python
import re

urls = ["hombres", "mujeres", "mascotas", "camión", "camion"]

[print(url) for url in urls if re.findall("cami[oó]n", url)]
```

```bash
camión
camion
```

### 6. Expresiones regulares III

#### 6.1. Vídeo

{{< youtube Q4vXCQd1zwc >}}

#### 6.2. Notas personales

En esta lección, continuaremos el estudio de las expresiones regulares
analizando cómo trabajar con **rangos**. Estos nos permiten buscar patrones
indicando un rango de números, de caracteres, etc.

Por ejemplo, a partir de una lista de nombres, supongamos que estamos
interesados en hallar todos aquellos que tengan letras comprendidas entre la `o`
y la `t`:

```python
import re

nombres = ["Ana", "Pedro", "María", "Rosa", "Sandra", "Celia"]

[print(nombre) for nombre in nombres if re.findall("[o-t]", nombre)]
```

```bash
Pedro
María
Rosa
Sandra
```

_Nota_: los rangos son _case sensitive_, esto es, distinguen entre minúsculas y
mayúsculas. Por ejemplo, si combinamos el rango anterior con el ancla `^`, la
ejecución no arrojará resultado alguno, porque todos los nombres están
declarados con su inicial en mayúscula.

```python
import re

nombres = ["Ana", "Pedro", "María", "Rosa", "Sandra", "Celia"]

[print(nombre) for nombre in nombres if re.findall("^[o-t]", nombre)]
```

No obstante, completando el rango solucionamos esta situación:

```python
import re

nombres = ["Ana", "Pedro", "María", "Rosa", "Sandra", "Celia"]

[print(nombre) for nombre in nombres if re.findall("^[o-tO-T]", nombre)]
```

```bash
Pedro
Rosa
Sandra
```

A continuación, estudiemos el uso de rangos cuando se nos presenta una lista de
códigos:

```python
import re

codigos = ["Ma1", "Se1", "Ma2", "Ba1", "Ma3", "Va1", "Va2", "Ma4"]

[print(codigo) for codigo in codigos if re.findall("Ma[0-3]", codigo)]
```

```bash
Ma1
Ma2
Ma3
```

Por otro lado, _Python_ nos permite la posibilidad de negar rangos, es decir, de
obtener aquellos resultados que no se ajustan al patrón de búsqueda
especificado. Para ello, antecediendo el rango, utilizamos el carácter `^`:

```python
import re

codigos = ["Ma1", "Se1", "Ma2", "Ba1", "Ma3", "Va1", "Va2", "Ma4"]

[print(codigo) for codigo in codigos if re.findall("Ma[^0-3]", codigo)]
```

```bash
Ma4
```

Acto seguido, agreguemos algunos códigos nuevos y sigamos experimentando el uso
de rangos:

```python
import re

codigos = ["Ma1", "Se1", "Ma2", "Ba1", "Ma3", "Va1", "Va2", "Ma4",
           "MaA", "Ma5", "MaB", "MaC"]

[print(codigo) for codigo in codigos if re.findall("Ma[0-3A-B]", codigo)]
```

```bash
Ma1
Ma2
Ma3
MaA
MaB
```

Ahora, insertemos algunos caracteres especiales en mitad de ciertos códigos y
veamos entonces cómo lidiar con ellos. Imaginemos que buscamos todos aquellos
cuyo tercer carácter sea bien un punto, bien dos puntos:

```python
import re

codigos = ["Ma.1", "Se1", "Ma2", "Ba1", "Ma:3", "Va1", "Va2", "Ma4",
           "MaA", "Ma.5", "MaB", "Ma:C"]

[print(codigo) for codigo in codigos if re.findall("Ma[.:]", codigo)]
```

```bash
Ma.1
Ma:3
Ma.5
Ma:C
```

### 7. Expresiones regulares IV

#### 7.1. Vídeo

{{< youtube u3WBRgpxQcc >}}

#### 7.2. Notas personales

En esta lección, finaliremos la serie dedicada a expresiones regulares
profundizando en el uso de las funciones `match()` y `search()` del módulo `re`.
La función `match()` busca coincidencias, con respecto a un patrón determinado,
siempre al comienzo del texto.

```python
import re

nombre1 = "Sandra López"
nombre2 = "Antonio Gómez"
nombre3 = "María López"

if re.match("Sandra", nombre1):
    print("Hemos encontrado el nombre.")
else:
    print("No hemos encontrado el nombre.")
```

```bash
Hemos encontrado el nombre.
```

Por otro lado, podemos evitar el comportamiento _case sensitive_ de esta función
mediante el parámetro `re.IGNORECASE`. Cambiemos `Sandra` por `sandra` y
comprobémoslo:

```python
import re

nombre1 = "Sandra López"
nombre2 = "Antonio Gómez"
nombre3 = "María López"

if re.match("sandra", nombre1, re.IGNORECASE):
    print("Hemos encontrado el nombre.")
else:
    print("No hemos encontrado el nombre.")
```

```bash
Hemos encontrado el nombre.
```

Además, tenemos a nuestra disposición el uso de comodines en los patrones de
búsqueda. Así, si añadimos dos nuevos nombres ''parecidos'', `Lara` y `Jara`,
mediante el carácter `.` (que representa un carácter qualquiera sin determinar)
podemos comprobar si ambos pertenecen o no a un listado de nombres:

```python
import re

nombres = ["Sandra López", "Antonio Gómez", "María López",
           "Jara Martín", "Lara Pérez"]

[print(nombre, end="\n") for nombre in nombres if re.match(".ara", nombre)]
```

```bash
Jara Martín
Lara Pérez
```

A continuación, veamos cómo emplear el patrón `\d` para averiguar si una cadena
comienza o no por un número:

```python
import re

datos = ["Alexis Sáez", "123456789", "Number1"]

[print(d) for d in datos if re.match("\d", d)]
```

```bash
123456789
```

Ahora, cambiemos de tercio y estudiemos la función `search()` que, a diferencia
de `match()` (que se limita a buscar al comienzo de un texto), examina la cadena
de texto completa. Retomemos el ejemplo de los nombres y busquemos la aparición
de ciertos apellidos concretos:

```python
import re

nombres = ["Sandra López", "Antonio Gómez", "María López",
           "Jara Martín", "Lara Pérez"]

[print(nombre, end="\n") for nombre in nombres if re.search("López", nombre)]
```

```bash
Sandra López
María López
```

No obstante, la principal utilidad de `search()` reside en la búsqueda de
determinados patrones dentro de una cadena de caracteres de extensión
considerable:

```python
import re

codigos = [
    '''
    Lorem ipsum dolor sit amet, 42consectetur adipiscing elit.
    Maecenas leo erat, varius non laoreet sed, cursus ut tortor.
    Morbi maximus pulvinar ante, ut pulvinar ex malesuada blandit.
    Maecenas venenatis, sapien vitae sodales viverra, ante urna
    tincidunt tellus, a faucibus elit dui congue dui. Quisque congue
    sed ex in sollicitudin. Pellentesque luctus justo quis felis
    feugiat, et semper erat laoreet. Curabitur id dui arcu. Curabitur
    purus massa, placerat id pretium ac, ornare eleifend ante.
    ''',
    '''
    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    Maecenas 42leo erat, varius non laoreet sed, cursus ut tortor.
    Morbi maximus pulvinar ante, ut pulvinar ex malesuada blandit.
    Maecenas venenatis, sapien vitae sodales viverra, ante urna
    tincidunt tellus, a faucibus elit dui congue dui. Quisque congue sed
    ex in sollicitudin. Pellentesque luctus justo quis felis feugiat, et
    semper erat laoreet. Curabitur id dui arcu. Curabitur purus massa,
    placerat id pretium ac, ornare eleifend ante.
    ''',
    '''
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas
    leo erat, varius non laoreet sed, cursus ut tortor. Morbi maximus
    pulvinar ante, ut pulvinar ex malesuada blandit. Maecenas venenatis,
    sapien vitae sodales viverra, ante urna tincidunt tellus, a faucibus
    elit dui congue dui. Quisque congue sed ex in sollicitudin.
    Pellentesque luctus justo quis felis feugiat, et semper erat laoreet.
    Curabitur id dui arcu. Curabitur purus massa, placerat id pretium ac,
    ornare eleifend ante.
    ''']

[print(c, end="\n") for c in codigos if re.search("42", c)]
```

```bash
    Lorem ipsum dolor sit amet, 42consectetur adipiscing elit.
    Maecenas leo erat, varius non laoreet sed, cursus ut tortor.
    Morbi maximus pulvinar ante, ut pulvinar ex malesuada blandit.
    Maecenas venenatis, sapien vitae sodales viverra, ante urna
    tincidunt tellus, a faucibus elit dui congue dui. Quisque congue
    sed ex in sollicitudin. Pellentesque luctus justo quis felis
    feugiat, et semper erat laoreet. Curabitur id dui arcu. Curabitur
    purus massa, placerat id pretium ac, ornare eleifend ante.


    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    Maecenas 42leo erat, varius non laoreet sed, cursus ut tortor.
    Morbi maximus pulvinar ante, ut pulvinar ex malesuada blandit.
    Maecenas venenatis, sapien vitae sodales viverra, ante urna
    tincidunt tellus, a faucibus elit dui congue dui. Quisque congue sed
    ex in sollicitudin. Pellentesque luctus justo quis felis feugiat, et
    semper erat laoreet. Curabitur id dui arcu. Curabitur purus massa,
    placerat id pretium ac, ornare eleifend ante.
```

### 8. Decoradoras I

#### 8.1. Vídeo

{{< youtube DQXm6bIZgvk >}}

#### 8.2. Notas personales

En esta lección, introduciremos el uso de las **decoradoras** (o _funciones
decoradoras_), que son funciones que añaden ciertos comportamientos a otras (de
ahí el nombre, puesto que las ''decoran'' incorporando funcionalidades
adicionales).

La estructura de una decoradora, de forma abstracta, es la siguiente:

- Son tres funciones (`A`, `B` y `C`), donde `A` recibe como parámetro a `B`
  para devolver `C`.
- Esto es, una decoradora devuelve siempre una función.

Su sintaxis queda como sigue:

```python
def funcion_decoradora(funcion):  # funcion_A(funcion_B)
    def funcion_interna():        # funcion_C
        # codigo funcion interna
    return funcion_interna
```

Veamos su aplicación práctica mediante un ejemplo muy sencillo, en el que la
utilidad de la decoradora será casi nula y nos servirá únicamente para
comprender su funcionamiento, sin añadir excesiva complejidad al código fuente.

En primer lugar, tecleamos:

```python
def suma():
    print(15 + 20)


def resta():
    print(30 - 10)


suma()
resta()
```

```bash
35
20
```

Acto seguido, supongamos que deseamos añadir a todas las funciones cierto
comportamiento adicional. Para ello, podemos acudir a su código y modificarlas
una por una (en este ejemplo son dos, pero imaginemos un caso donde hubiera
cientos de funciones) o utilizar una decoradora:

```python
def funcion_decoradora(funcion_parametro):
    def funcion_interior():
        # Acciones adicionales que decoran
        print("Vamos a realizar un cálculo: ")
        funcion_parametro()
        # Acciones adicionales que decoran
        print("Hemos terminado el cálculo.")
    return funcion_interior
```

A continuación, para añadir el decorador a cualquiera de las funciones ya
previamente existentes, escribimos:

```python
@funcion_decoradora
def suma():
    print(15 + 20)


def resta():
    print(30 - 10)


suma()
resta()
```

```bash
Vamos a realizar un cálculo:
35
Hemos terminado el cálculo.
20
```

Notemos cómo el decorador solo afecta a la función `suma()`, pues así lo hemos
declarado arriba. Bastaría replicar la estrategia para decorar asimismo la
función `resta()`.

### 9. Decoradoras II

#### 9.1. Vídeo

{{< youtube \_IwlE3Z7U04 >}}

{{< youtube KOw0tpcspH4 >}}

#### 9.2. Notas personales

En esta lección, continuamos el estudio de las funciones generadoras, analizando
cómo utilizar parámetros con ellas. Para ello, retomemos el código del ejemplo
de la lección anterior:

```python
def funcion_decoradora(funcion_parametro):
    def funcion_interior():
        # Acciones adicionales que decoran
        print("Vamos a realizar un cálculo: ")
        funcion_parametro()
        # Acciones adicionales que decoran
        print("Hemos terminado el cálculo.")
    return funcion_interior


@funcion_decoradora
def suma():
    print(15 + 20)


@funcion_decoradora
def resta():
    print(30 - 10)


suma()
resta()
```

Modifiquemos las funciones `suma()` y `resta()` para que admitan la posibilidad
de recibir parámetros:

```python
@funcion_decoradora
def suma(n1, n2):
    print(n1 + n2)


@funcion_decoradora
def resta(n1, n2):
    print(n1 - n2)
```

A continuación, en la `funcion_interior()` y en `funcion_parametros()`, que
figuran dentro de la `funcion_decoradora()`, gestionamos esos parámetros
utilizando `*args`, que posibilita que una función reciba un número
indeterminado de parámetros. Así,

```python
def funcion_decoradora(funcion_parametro):
    def funcion_interior(*args):
        # Acciones adicionales que decoran
        print("Vamos a realizar un cálculo: ")
        funcion_parametro(*args)
        # Acciones adicionales que decoran
        print("Hemos terminado el cálculo.")
    return funcion_interior
```

De esta manera, si ejecutamos ahora el código para las siguientes llamadas de
las funciones `suma()` y `resta()`:

```python
suma(10, 5)
resta(25, 20)
```

```bash
Vamos a realizar un cálculo:
15
Hemos terminado el cálculo.
Vamos a realizar un cálculo:
5
Hemos terminado el cálculo.
```

Por otro lado, incluso podemos ampliar la funcionalidad de nuestra decoradora,
permitiendo la posibilidad de admitir parámetros que sigan el patrón _key =
value_. Para ello, utilizamos en la definición de `funcion_interior()` y
`funcion_parametro()` la convención `**kwargs` como sigue:

```python
def funcion_decoradora(funcion_parametro):
    def funcion_interior(*args, **kwargs):
        # Acciones adicionales que decoran
        print("Vamos a realizar un cálculo: ")
        funcion_parametro(*args, **kwargs)
        # Acciones adicionales que decoran
        print("Hemos terminado el cálculo.")
    return funcion_interior
```

A continuación, construimos una función que realice la potenciación de un número
y procedemos a su llamada, utilizando ahora el esquema _key = value_:

```python
@funcion_decoradora
def potencia(base, exponente):
    print(pow(base, exponente))


potencia(base=5, exponente=2)
```

```bash
Vamos a realizar un cálculo:
25
Hemos terminado el cálculo.
```

### 10. Documentación

#### 10.1. Vídeo

{{< youtube SJqANWdRG4I >}}

#### 10.2. Notas personales

En esta lección, estudiaremos cómo documentar nuestros programas, esto es,
incluir comentarios en clases, métodos, módulos, etc., con el objetivo de
facilitar el trabajo en equipo sobre todo; resultando especialmente útil cuando
las aplicaciones son complejas.

Para empezar, tomemos como referencia este sencillo código, que contiene la
definición de dos funciones y llamadas a estas:

```python
def area_cuadrado(lado):
    return "El área del cuadrado es: " + str(lado * lado)


def area_triangulo(base, altura):
    return "El área del triángulo es: " + str(base * altura / 2.)


print(area_cuadrado(5))
print(area_triangulo(3, 6))
```

```bash
El área del cuadrado es: 25
El área del triángulo es: 9.0
```

A continuación, para documentarlas, tras su definición insertamos el comentario
oportuno encerrado por una triple comilla. De esta manera, mediante el atributo
`__doc__`, incluso podemos acceder a la documentación de una función en tiempo
de ejecución:

```python
def area_cuadrado(lado):
    """Calcula el área de un cuadrado dado su lado."""
    return "El área del cuadrado es: " + str(lado * lado)


def area_triangulo(base, altura):
    """Calcula el área de un triángulo dada su base y su altura."""
    return "El área del triángulo es: " + str(base * altura / 2.)


# print(area_cuadrado(5))
# print(area_triangulo(3, 6))

print(area_cuadrado.__doc__)
print(area_triangulo.__doc__)
```

```bash
Calcula el área de un cuadrado dado su lado.
Calcula el área de un triángulo dada su base y su altura.
```

Por otro lado, obtenemos el mismo resultado empleando la función `help()` que,
además, nos ofrece acceso a la cabecera de la definición de la función y al
módulo donde se encuentra:

```python
def area_cuadrado(lado):
    """Calcula el área de un cuadrado dado su lado."""
    return "El área del cuadrado es: " + str(lado * lado)


def area_triangulo(base, altura):
    """Calcula el área de un triángulo dada su base y su altura."""
    return "El área del triángulo es: " + str(base * altura / 2.)


# print(area_cuadrado(5))
# print(area_triangulo(3, 6))

# print(area_cuadrado.__doc__)
# print(area_triangulo.__doc__)

help(area_cuadrado)
help(area_triangulo)
```

```bash
Help on function area_cuadrado in module __main__:

area_cuadrado(lado)
    Calcula el área de un cuadrado dado su lado.

Help on function area_triangulo in module __main__:

area_triangulo(base, altura)
    Calcula el área de un triángulo dada su base y su altura.
```

Ahora, modifiquemos ligeramente el código para generar una clase `Areas`, en
cuyo interior se encuentren las dos anteriores funciones, y veamos cómo acceder
a la documentación generada antes:

```python
class Areas:
    def area_cuadrado(lado):
        """Calcula el área de un cuadrado dado su lado."""
        return "El área del cuadrado es: " + str(lado * lado)

    def area_triangulo(base, altura):
        """Calcula el área de un triángulo dada su base y su altura."""
        return "El área del triángulo es: " + str(base * altura / 2.)


help(Areas.area_cuadrado)
help(Areas.area_triangulo)
```

```bash
Help on function area_cuadrado in module __main__:

area_cuadrado(lado)
    Calcula el área de un cuadrado dado su lado.

Help on function area_triangulo in module __main__:

area_triangulo(base, altura)
    Calcula el área de un triángulo dada su base y su altura.
```

Además, para obtener una documentación general de la clase basta teclear:

```python
help(Areas)
```

```bash
Help on class Areas in module __main__:

class Areas(builtins.object)
 |  Methods defined here:
 |
 |  area_cuadrado(lado)
 |      Calcula el área de un cuadrado dado su lado.
 |
 |  area_triangulo(base, altura)
 |      Calcula el área de un triángulo dada su base y su altura.
 |
 |  ----------------------------------------------------------------------
 |  Data descriptors defined here:
 |
 |  __dict__
 |      dictionary for instance variables (if defined)
 |
 |  __weakref__
 |      list of weak references to the object (if defined)
```

Finalmente, también podemos documentar la propia clase:

```python
class Areas:
    """Esta clase calcula las áreas de diferentes figuras geométricas."""
    def area_cuadrado(lado):
        """Calcula el área de un cuadrado dado su lado."""
        return "El área del cuadrado es: " + str(lado * lado)

    def area_triangulo(base, altura):
        """Calcula el área de un triángulo dada su base y su altura."""
        return "El área del triángulo es: " + str(base * altura / 2.)


help(Areas)
```

```bash
Help on class Areas in module __main__:

class Areas(builtins.object)
 |  Esta clase calcula las áreas de diferentes figuras geométricas.
 |
 |  Methods defined here:
 |
 |  area_cuadrado(lado)
 |      Calcula el área de un cuadrado dado su lado.
 |
 |  area_triangulo(base, altura)
 |      Calcula el área de un triángulo dada su base y su altura.
 |
 |  ----------------------------------------------------------------------
 |  Data descriptors defined here:
 |
 |  __dict__
 |      dictionary for instance variables (if defined)
 |
 |  __weakref__
 |      list of weak references to the object (if defined)
```

_Nota_: utilizando esta misma estrategia, podemos documentar asimismo módulos.

### 11. Pruebas I

#### 11.1. Vídeo

{{< youtube BUNEkSFlmys >}}

#### 11.2. Notas personales

En esta lección, analizaremos cómo realizar pruebas, utilizando la documentación
para ello. Esta forma de proceder la podemos llevar a cabo con el módulo
`doctest` de _Python_.

Para empezar, partamos de este sencillo código, que contiene una función que
calcula el área del triángulo dada su base y su altura:

```python
def area_triangulo(base, altura):
    return base * altura / 2.


print(area_triangulo(2, 4))
```

```bash
4.0
```

A continuación, documentemos la función `area_triangulo()` siguiendo el
procedimiento visto en la lección anterior e incluyamos ahí nuestra primera
prueba (antecediéndola mediante `>>>`). Luego, una vez importado el módulo
`doctest`, incluimos la instrucción `doctest.testmod()`:

```python
import doctest


def area_triangulo(base, altura):
    """
    Calcula el área de un triángulo dada su base y altura.

    >>> area_triangulo(3, 6)
    9.0

    """
    return base * altura / 2.


doctest.testmod()
```

Al ejecutar el anterior bloque de código, no observamos respuesta alguna en la
consola de _Python_, lo cual es una buena señal, pues significa que se han
superado los tests planteados sin encontrar ningún problema.

Ahora, imaginemos que nos hemos equivocado escribiendo el test (también valdría
modificando la expresión que devuelve la instrucción `return`) y decimos que ha
de resultar `8.0` el área de un triángulo de base `3` y altura `6`:

```python
import doctest


def area_triangulo(base, altura):
    """
    Calcula el área de un triángulo dada su base y altura.

    >>> area_triangulo(3, 6)
    8.0

    """
    return base * altura / 2.


doctest.testmod()
```

```bash
**********************************************************************
File "pruebas_2.py", line 8, in __main__.area_triangulo
Failed example:
    area_triangulo(3, 6)
Expected:
    8.0
Got:
    9.0
**********************************************************************
1 items had failures:
   1 of   1 in __main__.area_triangulo
***Test Failed*** 1 failures.
```

Acto seguido, compliquemos ligeramente el ejemplo y hagamos que la función
`area_triangulo()` devuelva una cadena de caracteres en lugar de un valor
numérico. Ello implica redactar con cuidado la prueba:

```python
import doctest


def area_triangulo(base, altura):
    """
    Calcula el área de un triángulo dada su base y altura.

    >>> area_triangulo(3, 6)
    'El área del triángulo es 9.0'

    """
    return "El área del triángulo es " + str(base * altura / 2.)


doctest.testmod()
```

_Nota_: hemos de proceder con cautela porque, en esta ocasión, las comillas `'`
y `"` no son intercambiables.

Obviamente, tenemos la posibilidad de realizar varias pruebas:

```python
import doctest


def area_triangulo(base, altura):
    """
    Calcula el área de un triángulo dada su base y altura.

    >>> area_triangulo(3, 6)
    'El área del triángulo es 9.0'

    >>> area_triangulo(2, 4)
    'El área del triángulo es 4.0'

    >>> area_triangulo(4, 5)
    'El área del triángulo es 10.0'

    """
    return "El área del triángulo es " + str(base * altura / 2.)


doctest.testmod()
```

No obstante, llevar a cabo múltiples pruebas tiene sentido cuando la complejidad
del código se incrementa. Recordemos el código que generamos para comprobar si
una dirección de correo electrónico era correcta en función de si presentaba o
no el carácter `@`:

```python
import doctest


def check_mail(mail_user):
    """
    Evalúa un mail recibido en busca de @.
    Si tiene una @ es correcto.
    Si tiene más de una @ es incorrecto.
    Si la @ está al final es incorrecto.

    >>> check_mail("alexis@cursos.es")
    True

    >>> check_mail("alexiscursos.es@")
    False

    >>> check_mail("alexis.cursos.es")
    False

    >>> check_mail("alexis@cursos@es")
    False
    """

    arroba = mail_user.count("@")
    return not (arroba != 1 or mail_user.rfind('@') == len(mail_user) - 1)


doctest.testmod()
```

### 12. Pruebas II

#### 12.1. Vídeo

{{< youtube 64v9X7K-iuc >}}

#### 12.2. Notas personales

En esta lección, continuaremos el estudio de las pruebas que realizamos
utilizando la documentación, pero incrementando un tanto su complejidad (con
expresiones anidadas), para así ver las opciones que nos plantea el módulo
`doctest`.

Para empezar, partamos del siguiente código fuente, que no es todo lo eficiente
que debería, pero que cumple su propósito a efectos metodológicos para ilustrar
pruebas con expresiones anidadas:

```python
import math


def raiz_cuadrada(lista_numeros):
    """
    La función devuelve una lista con la raíz cuadrada de
    los elementos numéricos pasados por parámetros en otra
    lista.
    """
    return [math.sqrt(n) for n in lista_numeros]


print(raiz_cuadrada([1, 4, 9, 16]))
```

```bash
[1.0, 2.0, 3.0, 4.0]
```

A continuación, para diseñar una prueba que contenta estructuras complejas como
condicionales o bucles, simplemente hemos de utilizar `...` apropiadamente para
anidar instrucciones:

```python
import doctest
import math


def raiz_cuadrada(lista_numeros):
    """
    La función devuelve una lista con la raíz cuadrada de
    los elementos numéricos pasados por parámetros en otra
    lista.

    >>> lista = []
    >>> for i in [4, 9, 16]:
    ...     lista.append(i)
    >>> raiz_cuadrada(lista)
    [2.0, 3.0, 4.0]
    """
    return [math.sqrt(n) for n in lista_numeros]


doctest.testmod()
```

Acto seguido, analicemos cómo implementar pruebas que arrojen excepciones. Por
ejemplo, incluyamos un elemento negativo en la lista que pasamos como argumento
a la función `raiz_cuadrada()`:

```python
print(raiz_cuadrada([4, -9, 16]))
```

```bash
Traceback (most recent call last):
  File "pruebas_2.py", line 27, in <module>
    print(raiz_cuadrada([4, -9, 16]))
  File "pruebas_2.py", line 22, in raiz_cuadrada
    return [math.sqrt(n) for n in lista_numeros]
  File "pruebas_2.py", line 22, in <listcomp>
    return [math.sqrt(n) for n in lista_numeros]
ValueError: math domain error
```

No obstante, para diseñar una prueba que contemple el uso de número negativos en
general (y no el de esta lista en concreto), utilizaremos `...` y nos quedaremos
únicamente con la primera y última línea de la excepción arrojada arriba:

```python
import doctest
import math


def raiz_cuadrada(lista_numeros):
    """
    La función devuelve una lista con la raíz cuadrada de
    los elementos numéricos pasados por parámetros en otra
    lista.

    >>> lista = []
    >>> for i in [4, 9, 16]:
    ...     lista.append(i)
    >>> raiz_cuadrada(lista)
    [2.0, 3.0, 4.0]

    >>> lista = []
    >>> for i in [4, -9, 16]:
    ...     lista.append(i)
    >>> raiz_cuadrada(lista)
    Traceback (most recent call last):
    ...
    ValueError: math domain error
    """
    return [math.sqrt(n) for n in lista_numeros]


doctest.testmod()
```

### 13. Ejecutables

#### 13.1. Vídeo

{{< youtube Vr9vl0qlggE >}}

#### 13.2. Notas personales

En esta lección, estudiaremos cómo generar un ejecutable de una aplicación
escrita en _Python_ y que tomará el formato nativo del sistema operativo en el
que estemos trabajando (`.exe` en _Windows_, por ejemplo).

Para empezar, desde la terminal del sistema, instalamos `pyinstaller`,
utilizando para ello la instrucción:

```bash
pip3 install pyinstaller
```

A continuación, rescatemos los archivos de la aplicación que simulaba una
calculadora, correspondiente a la lección 50. Generemos una copia de ellos, por
coherencia con la estructura del
[repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0), en el
directorio `/lecciones/78/`.

Ahora, desde la terminal, nos desplazamos a dicho directorio y tecleamos:

```bash
pyinstaller calculadora.py
```

Esto es, la instrucción `pyinstaller` seguida del nombre del archivo del cual
deseamos generar un ejecutable.

El proceso da a luz a una cantidad considerable de ficheros y carpetas, siendo
de nuestro interés la denominada `/dist/`, en cuyo interior encontraremos otra
designada como `/calculadora/`, que contiene la aplicación lista para ser
distribuida. Si hacemos doble clic sobre `calculadora.exe`, podemos corroborar
que la aplicación funciona a la perfección.

Ahora bien, tras ella aparece la propia terminal de _Python_, característica que
quizá no nos interese y posiblemente solo deseemos trabajar con la interfaz
gráfica de la calculadora. Para conseguirlo, hemos de incluir el modificador
`--windowed`, en la llamada a `pyinstaller`, a la hora de crear el ejecutable:

```bash
pyinstaller --windowed calculadora.py
```

No obstante, la aplicación requiere de la presencia de todos los ficheros
contenidos en el directorio `/calculadora/` para su correcto funcionamiento.
Sería deseable que todo ello se ''compilase'' en un único archivo y que se
pudiera ejecutar en cualquier ordenador, independientemente de si tiene o no
instalado _Python_. El mencionado comportamiento se obtiene agregando el
modificador `--onefile` a la anterior instrucción, esto es,

```bash
pyinstaller --windowed --onefile calculadora.py
```

Ahora, en la carpeta `/dist/` hallamos únicamente el archivo.

Finalmente, de cara a modificar el icono de la aplicación, simplemente hemos de
añadir un nuevo modificador a la instrucción `pyinstaller`: `--icon=./icon.ico`,
siendo `icon.ico` el nombre del archivo que contiene el icono y que se ubica en
el mismo directorio donde se halla el fichero `calculadora.py`. Así pues,
tecleamos:

```bash
pyinstaller --windowed --onefile --icon=./icon.ico calculadora.py
```
