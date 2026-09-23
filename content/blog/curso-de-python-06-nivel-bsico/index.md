---
title: "Curso de Python #06 (Nivel básico)"
summary: Excepciones
date: 2019-08-01
lastmod: 2026-09-23
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

### 1. Excepciones I

#### 1.1. Vídeo

{{< youtube 2MaAs7XU2T0 >}}

#### 1.2. Notas personales

Una **excepción** es un error que acontece durante la ejecución de un programa.
La sintaxis del código es correcta, pero, en el momento de ejecutarse el
algoritmo, sucede ''algo inesperado''.

Para ilustrar la aparición de excepciones, trabajemos con el siguiente código:

```python
def suma(num1, num2):
    return num1 + num2


def resta(num1, num2):
    return num1 - num2


def multiplica(num1, num2):
    return num1 * num2


def divide(num1, num2):
    return num1 / num2


op1 = (int(input("Introduce el primer número: ")))
op2 = (int(input("Introduce el segundo número: ")))

print("Operaciones disponibles: ")
print("- Suma")
print("- Resta")
print("- Multiplica")
print("- Divide")

operacion = input("Introduce la operación a realizar: ")

if operacion == "Suma":
    print(suma(op1, op2))
elif operacion == "Resta":
    print(resta(op1, op2))
elif operacion == "Multiplica":
    print(multiplica(op1, op2))
elif operacion == "Divide":
    print(divide(op1, op2))
else:
    print("Operación no contemplada.")

print("Operación ejecutada. Continuación de ejecución del programa ")
```

Un posible ejemplo de ejecución sería:

```bash
Introduce el primer número: 16
Introduce el segundo número: 4
Operaciones disponibles:
- Suma
- Resta
- Multiplica
- Divide
Introduce la operación a realizar: Multiplica
64
Operación ejecutada. Continuación de ejecución del programa
```

Sin embargo, si por accidente intentamos realizar una división entre 0:

```bash
Introduce el primer número: 2
Introduce el segundo número: 0
Operaciones disponibles:
- Suma
- Resta
- Multiplica
- Divide
Introduce la operación a realizar: Divide
Traceback (most recent call last):
  File "prac21_excepciones1_1.py", line 35, in <module>
    print(divide(op1, op2))
  File "prac21_excepciones1_1.py", line 14, in divide
    return num1 / num2
ZeroDivisionError: division by zero
```

De forma que el código se detiene en el preciso instante de la llamada a la
función `divide()` y deja de ejecutar las restantes líneas (la instrucción
`print()` final en esta ocasión), cuya importancia puede ser vital para
nosotros.

Este tipo de situaciones se aborda mediante una **captura** o **control de
excepción**. La idea es intentar realizar un bloque de código y, en el caso de
no poderse llevar a cabo dicha acción, que al menos el resto de programa siga
adelante.

Si nos fijamos en la **pila de llamadas** que nos muestran antes de arrojar el
error:

```bash
Traceback (most recent call last):
  File "prac21_excepciones1_1.py", line 35, in <module>
    print(divide(op1, op2))
  File "prac21_excepciones1_1.py", line 14, in divide
    return num1 / num2
ZeroDivisionError: division by zero
```

Leyendo de abajo hacia arriba, la instrucción `return num1 / num2`, ubicada en
la línea 14 del código, arroja un error de división por cero
(`ZeroDivisionError`). Para controlar esta circunstancia, usaremos un bloque de
tipo:

```python
try:
    instrucciones
except error:
    instrucciones
```

Así, nuestra función `divide()` la podríamos reescribir como sigue:

```python
def divide(num1, num2):
    try:
        return num1 / num2
    except ZeroDivisionError:
        print("No se puede dividir entre 0.")
        return "Operación errónea."
```

De manera que, replicando el anterior conflictivo ejemplo:

```bash
Introduce el primer número: 2
Introduce el segundo número: 0
Operaciones disponibles:
- Suma
- Resta
- Multiplica
- Divide
Introduce la operación a realizar: Divide
No se puede dividir entre 0.
Operación errónea.
Operación ejecutada. Continuación de ejecución del programa
```

Apreciamos que la última línea de código, aquel `print()` final, ahora
efectivamente sí llega a ejecutarse.

Por desgracia, no es el único punto conflictivo que presenta el código mostrado.
Por ejemplo, ¿qué sucede si introducimos una cadena de texto en lugar de un
número?

```bash
Introduce el primer número: 3
Introduce el segundo número: a
Traceback (most recent call last):
  File "prac21_excepciones1_1.py", line 22, in <module>
    op2 = (int(input("Introduce el segundo número: ")))
ValueError: invalid literal for int() with base 10: 'a'
```

_Python_ arroja un error de tipo `ValueError` que también habríamos de controlar
a través de un bloque `try` - `except`.

### 2. Excepciones II

#### 2.1. Vídeo

{{< youtube HH3c6ZBvSx8 >}}

#### 2.2. Notas personales

Recordemos el código final de la lección anterior:

```python
def suma(num1, num2):
    return num1 + num2


def resta(num1, num2):
    return num1 - num2


def multiplica(num1, num2):
    return num1 * num2


def divide(num1, num2):
    try:
        return num1 / num2
    except ZeroDivisionError:
        print("No se puede dividir entre 0.")
        return "Operación errónea."


op1 = (int(input("Introduce el primer número: ")))
op2 = (int(input("Introduce el segundo número: ")))

print("Operaciones disponibles: ")
print("- Suma")
print("- Resta")
print("- Multiplica")
print("- Divide")

operacion = input("Introduce la operación a realizar: ")

if operacion == "Suma":
    print(suma(op1, op2))
elif operacion == "Resta":
    print(resta(op1, op2))
elif operacion == "Multiplica":
    print(multiplica(op1, op2))
elif operacion == "Divide":
    print(divide(op1, op2))
else:
    print("Operación no contemplada.")

print("Operación ejecutada. Continuación de ejecución del programa.")
```

No obstante, este código es susceptible de presentar más errores. Por ejemplo,
introduciendo una cadena de texto en lugar de un número cuando nos solicitan los
datos.

Para solucionar ese detalle, podemos reescribir el correspondiente bloque de
código como sigue:

```python
try:
    op1 = (int(input("Introduce el primer número: ")))
    op2 = (int(input("Introduce el segundo número: ")))
except ValueError:
    print("Los valores introducidos no son correctos.")
```

El programa así modificado, presenta errores de lógica ahora, ya que si
introducimos una cadena de texto como dato, _Python_ no arroja error, pero
continua la ejecución del programa y al intentar llevar a cabo cualquier
operación de las disponibles, lanza un error de tipo `NameError`:

```bash
Introduce el primer número: 5
Introduce el segundo número: a
Los valores introducidos no son correctos.
Operaciones disponibles:
- Suma
- Resta
- Multiplica
- Divide
Introduce la operación a realizar: Suma
Traceback (most recent call last):
  File "prac22_excepciones2_1.py", line 36, in <module>
    print(suma(op1, op2))
NameError: name 'op2' is not defined
```

Una manera de abordar esta problemática es mediante un bucle infinito de tipo
`while`, forzando que el usuario introduzca valores admisibles para continuar la
ejecución del programa:

```python
while True:
    try:
        op1 = (int(input("Introduce el primer número: ")))
        op2 = (int(input("Introduce el segundo número: ")))
        break
    except ValueError:
        print("Los valores introducidos no son correctos. Inténtalo de nuevo.")
```

Siendo una posible ejecución del programa la que se muestra acto seguido:

```bash
Introduce el primer número: 5
Introduce el segundo número: a
Los valores introducidos no son correctos. Inténtalo de nuevo.
Introduce el primer número: ag
Los valores introducidos no son correctos. Inténtalo de nuevo.
Introduce el primer número: 5
Introduce el segundo número: 0
Operaciones disponibles:
- Suma
- Resta
- Multiplica
- Divide
Introduce la operación a realizar: Suma
5
Operación ejecutada. Continuación de ejecución del programa.
```

Elaboremos ahora una función `divide()` diferente a la vista en el ejemplo
anterior:

```python
def divide():
    op1 = (float(input("Dividendo: ")))
    op2 = (float(input("Divisor: ")))
    print("La división resulta: " + str(op1 / op2))
    print("Cálculo finalizado.")


divide()
```

Como antes, el programa arroja excepciones si intentamos dividir por cero o
introducimos cadenas de texto como datos. Capturémoslas de manera consecutiva:

```python
def divide():
    try:
        op1 = (float(input("Dividendo: ")))
        op2 = (float(input("Divisor: ")))
        print("La división resulta: " + str(op1 / op2))
    except ValueError:
        print("El valor introducido es erróneo.")
    except ZeroDivisionError:
        print("No se puede dividir entre cero.")
    print("Cálculo finalizado.")


divide()
```

Existe una alternativa genérica, aunque poco recomendable, que consiste en
teclear `except:` sin más e imprimir un mensaje neutro de error. Captura una
excepción de forma general, pero no informa sobre lo acontencido.

Por otro lado, cuando queremos que un código se ejecute siempre, existe la
posibilidad de ubicarlo en el interior de una claúsula `finally`:

```python
def divide():
    try:
        op1 = (float(input("Dividendo: ")))
        op2 = (float(input("Divisor: ")))
        print("La división resulta: " + str(op1 / op2))
    except ValueError:
        print("El valor introducido es erróneo.")
    except ZeroDivisionError:
        print("No se puede dividir entre cero.")
    finally:
        print("Cálculo finalizado.")


divide()
```

Además, es posible también programar utilizando la combinación `try` -
`finally`:

```python
def divide():
    try:
        op1 = (float(input("Dividendo: ")))
        op2 = (float(input("Divisor: ")))
        print("La división resulta: " + str(op1 / op2))
    finally:
        print("Cálculo finalizado.")


divide()
```

Veamos algunas posibles ejecuciones de este último bloque de código:

```bash
Dividendo: 4
Divisor: 2
La división resulta: 2.0
Cálculo finalizado.
```

```bash
Dividendo: aaa
Cálculo finalizado.
Traceback (most recent call last):
  File "prac22_excepciones2_3.py", line 10, in <module>
    divide()
  File "prac22_excepciones2_3.py", line 3, in divide
    op1 = (float(input("Dividendo: ")))
ValueError: could not convert string to float: 'aaa'
```

```bash
Dividendo: 5
Divisor: 0
Cálculo finalizado.
Traceback (most recent call last):
  File "prac22_excepciones2_3.py", line 10, in <module>
    divide()
  File "prac22_excepciones2_3.py", line 5, in divide
    print("La división resulta: " + str(op1 / op2))
ZeroDivisionError: float division by zero
```

La cadena de texto `"Cálculo finalizado"` se muestra por pantalla,
independientemente de la presencia o no de excepciones durante la ejecución del
algoritmo.

_Nota técnica_: toda instrucción `try` ha de estar acompañada bien de su
correspondiente `except`, bien de `finally`, bien de ambas; pero no puede
aparecer en solitario.

### 3. Excepciones III

#### 3.1. Vídeo

{{< youtube dLH-oay4Bts >}}

#### 3.2. Notas personales

Estudiemos cómo lanzar excepciones, de forma intencionada, a través de la
instrucción `raise`. Veremos su utilidad cuando trabajemos, más adelante, con
clases.

Generemos un sencillo programa cuyo objetivo sea evaluar nuestra edad:

```python
def evalua_edad(edad):
    if edad < 20:
        return "Eres muy joven."
    elif edad < 40:
        return "Eres joven."
    elif edad < 65:
        return "Eres maduro."
    elif edad < 100:
        return "Cuídate."


print(evalua_edad(18))  # Eres muy joven.
print(evalua_edad(70))  # Cuídate.
```

Sin embargo, la función así definida presenta este curioso comportamiento:

```python
print(evalua_edad(-15))  # Eres muy joven.
```

Evidentemente, podemos arreglar esta situación mediante estructuras
condicionales, pero veremos a continuación cómo emplear la instrucción `raise`
para abordar el presente caso.

```python
def evalua_edad(edad):
    if edad < 0:
        raise TypeError("No se permiten edades negativas.")
    if edad < 20:
        return "Eres muy joven."
    elif edad < 40:
        return "Eres joven."
    elif edad < 65:
        return "Eres maduro."
    elif edad < 100:
        return "Cuídate."


print(evalua_edad(18))
print(evalua_edad(70))
print(evalua_edad(-15))
```

Al ejecutar el anterior programa, obtenemos:

```bash
Eres muy joven.
Cuídate.
Traceback (most recent call last):
  File "prac23_excepciones3_2.py", line 16, in <module>
    print(evalua_edad(-15))
  File "prac23_excepciones3_2.py", line 3, in evalua_edad
    raise TypeError("No se permiten edades negativas.")
TypeError: No se permiten edades negativas.
```

_Nota_: hemos de usar alguno de los tipos de error disponibles en _Python_, no
pdemos cualquier cadena de texto sin más ahí. No obstante, dicho esto, cuando
generemos clases podremos elaborar también errores personalizados.

Pasemos a programar un algoritmo que calcule la raíz cuadrada de un número mayor
o igual que cero:

```python
import math


def calcula_raiz(num):
    if num < 0:
        raise ValueError("El número no puede ser negativo.")
    else:
        return math.sqrt(num)


op = (int(input("Introduce un número mayor o igual que cero: ")))

print(calcula_raiz(op))

print("Programa terminado.")
```

Controlemos la excepción que aparece si introducimos un número negativo:

```python
import math


def calcula_raiz(num):
    if num < 0:
        raise ValueError("El número no puede ser negativo.")
    else:
        return math.sqrt(num)


op = (int(input("Introduce un número mayor o igual que cero: ")))

try:
    print(calcula_raiz(op))
except ValueError as ErrorDeNumeroNegativo:
    print(ErrorDeNumeroNegativo)

print("Programa terminado.")
```

Un par de ejecuciones del anterior programa, por ejemplo, podrían ser:

```bash
Introduce un número mayor o igual que cero: 144
12.0
Programa terminado.
```

```bash
Introduce un número mayor o igual que cero: -144
El número no puede ser negativo.
Programa terminado.
```
