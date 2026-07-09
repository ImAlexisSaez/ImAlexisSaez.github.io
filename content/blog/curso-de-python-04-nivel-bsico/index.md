---
title: "Curso de Python #04 (Nivel básico)"
summary: Bucles
date: 2019-07-21
lastmod: 2026-07-09
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

### 1. Bucles I

#### 1.1 Vídeo

{{< youtube GQGhU1526Oo >}}

#### 1.2. Notas personales

Abordaremos ahora otro tipo de estructura de control de flujo (las estructuras
condicionales asimismo lo eran): los **bucles**.

La utilidad de un **bucle** es repetir una o varias líneas de código tantas
veces como sea preciso (siendo esta cantidad conocida de antemano o no). En
_Python_ tenemos dos tipos de bucles:

- _determinados_: sabemos a priori cuántas veces se repetirá el bloque de
  código, e
- _indeterminados_: desconocemos a priori el número de repeticiones del bloque
  de código.

Empecemos viendo el primer tipo, al que pertenece la instrucción `for`, cuya
sintaxis es:

```python
for variable in elemento_a_recorrer:
    instrucciones
```

donde el `elemento_a_recorrer` puede ser una lista, una tupla, una cadena de
texto...

Por ejemplo, para imprimir tres veces una palabra, una posible estrategia sería:

```python
for i in [1, 2, 3]:
    print("Hola")
```

Aunque hemos utilizado una lista de números, no es imprescindible. El siguiente
ejemplo consigue el mismo resultado:

```python
for i in ["enero", "febrero", "marzo"]:
    print("Hola")
```

En ambos casos, el elemento a recorrer es una lista de tres elementos y es por
ello que el mensaje `"Hola"` se repite en tres ocasiones, tantas como el
mencionado número de elementos de la correspondiente lista.

Si en lugar de un texto predeterminado optamos por imprimir la propia variable
en ambos casos, el resultado es:

```python
for i in [1, 2, 3]:
    print(i)

# 1
# 2
# 3
```

```python
for i in ["enero", "febrero", "marzo"]:
    print(i)

# enero
# febrero
# marzo
```

La variable no tiene que denominarse necesariamente `i`:

```python
for meses in ["enero", "febrero", "marzo"]:
    print(meses)

# enero
# febrero
# marzo
```

### 2. Bucles II

#### 2.1. Vídeo

{{< youtube D416qOEDrhI >}}

#### 2.2. Notas personales

Las instrucciones `print()` que aparecen en los bucles de tipo `for` insertan un
salto de línea en cada iteración:

```python
for i in ["Píldoras", "Informáticas", 3]:
    print("Hola")

# Hola
# Hola
# Hola
```

Si deseamos que la impresión se produzca en la misma línea, hemos de declarar
adecuadamente el argumento `end` de la función `print()`:

```python
for i in ["Píldoras", "Informáticas", 3]:
    print("Hola", end=" ")

# Hola Hola Hola
```

Si el elemento a recorrer es una cadena de texto, el bucle `for` ejecutará
tantas iteraciones como letras tenga esta:

```python
for i in "Alexis":
    print(i, end="-")

# A-l-e-x-i-s-
```

Esta característica nos permite, por ejemplo, programar una primera aproximación
a un verificador de direcciones de correo electrónico, que nos indique que una
es correcta si alberga una arroba en su declaración:

```python
email = False

for i in "direccion@dominio.com":
    if i == "@":
        email = True

if email == True:
    print("El email es correcto.")
else:
    print("El email no es correcto.")

# El email es correcto.
```

El anterior bloque de código se puede simplificar un tanto:

```python
for i in "direccion@dominio.com":
    if i == "@":
        email = True

if email:
    print("El email es correcto.")
else:
    print("El email no es correcto.")

# El email es correcto.
```

Generemos una versión interactiva de este programa:

```python
def evalua_email(direcc):
    email = False

    for i in direcc:
        if i == "@":
            email = True
    if email:
        print("El email es correcto.")
    else:
        print("El email no es correcto.")


direcc = input("Introduce tu dirección de correo electrónico: ")

evalua_email(direcc)
```

Podemos ampliar la función de verificación de correos electrónicos para que
compruebe si también hay un carácter `.` en la cadena de texto:

```python
def evalua_email(direcc):
    arroba = False
    punto = False

    for i in direcc:
        if i == "@":
            arroba = True
        if i == ".":
            punto = True
    if arroba and punto:
        print("El email es correcto.")
    else:
        print("El email no es correcto.")


direcc = input("Introduce tu dirección de correo electrónico: ")

evalua_email(direcc)
```

Veamos el uso del tipo `range` en combinación con el bucle `for`:

```python
for i in range(5):
    print(i)

# 0
# 1
# 2
# 3
# 4
```

### 3. Bucles III

#### 3.1. Vídeo

{{< youtube KFz-mXB7qVI >}}

#### 3.2. Notas personales

Veamos algunas opciones de la función `print()` a la hora de imprimir el valor
de variables durante la ejecución de un bucle:

```python
for i in range(5):
    print(f"valor de la variable {i}")

# valor de la variable 0
# valor de la variable 1
# valor de la variable 2
# valor de la variable 3
# valor de la variable 4
```

La `f` que aparece antes del texto entrecomillado indica el uso de **funciones
f**, que permiten interesantes opciones de cara a la impresión de textos en la
consola. En esta ocasión, concatena la cadena de caracteres con el valor que
toma la variable en cada iteración, indicada por `{i}`.

El tipo `range` admite el uso de argumentos adicionales:

```python
for i in range(5, 10):
    print(f"valor de la variable {i}")

# valor de la variable 5
# valor de la variable 6
# valor de la variable 7
# valor de la variable 8
# valor de la variable 9
```

```python
for i in range(5, 50, 5):
    print(f"valor de la variable {i}")

# valor de la variable 5
# valor de la variable 10
# valor de la variable 15
# valor de la variable 20
# valor de la variable 25
# valor de la variable 30
# valor de la variable 35
# valor de la variable 40
# valor de la variable 45
```

La función `len` también resulta de utilidad a la hora de emplear bucles `for`.
Veámosla en acción retomando el ejemplo de la validación de una dirección de
correo electrónico visto en la lección anterior:

```python
valido = False

email = input("Introduce tu email: ")

for i in range(len(email)):
    if email[i] == "@":
        valido = True

if valido:
    print("El email es correcto.")
else:
    print("El email no es correcto.")
```

**Ejercicio 1**: crea un programa que muestre los números impares del 1 al 100.
Los números deberán aparecer una al lado del otro sin salto de línea.

```python
for i in range(1, 100, 2):
    print(i, end=" ")
```

**Ejercicio 2**: crea un programa que pida por teclado introducir una
contraseña. La contraseña no podrá tener menos de 8 caracteres ni espacios en
blanco. Si la contraseña es correcta, el programa imprime ''Contraseña OK''. En
caso contrario imprime ''Contraseña errónea''.

```python
def evalua_password(password):
    valido = True
    if len(password) < 8 or " " in password:
        valido = False
    return valido


password = input("Introduce contraseña: ")

if evalua_password(password):
    print("Constraseña OK.")
else:
    print("Contraseña errónea.")
```

**Ejercicio 3**: crea un programa que evalúe si una dirección de correo
electrónico es válida o no en función de si tiene `@` o `.` Hay que tener en
cuenta que la dirección se considera correcta si solo tiene una `@` y si tiene
uno o más `.`.

```python
def evalua_mail(mail):
    arroba = False
    punto = False

    if "." in mail:
        punto = True

    contador = 0
    for i in mail:
        if i == "@":
            contador += 1

    if contador == 1:
        arroba = True

    return punto and arroba


mail = input("Introduce dirección de correo electrónico: ")

if evalua_mail(mail):
    print("Dirección de correo electrónico VÁLIDA.")
else:
    print("Dirección de correo electrónico INVÁLIDA.")
```

### 4. Bucles IV

#### 4.1. Vídeo

{{< youtube UfUM6uzl5SM >}}

#### 4.2. Notas personales

Estudiemos el bucle **while**, que es tipo _indeterminado_ porque no sabemos a
priori cuántas veces ejecutará el bloque de código contenido en su interior. Su
sintaxis es:

```python
while condición:
    instrucciones
```

En el siguiente ejemplo, no obstante, vemos cómo programar un bucle `while` para
que funcione como uno de tipo _determinado_:

```python
i = 1

while i <= 10:
    print(f"Iteración: {i}.")
    i += 1

print("Fin de ejecución del bucle while.")

# Iteración: 1.
# Iteración: 2.
# Iteración: 3.
# Iteración: 4.
# Iteración: 5.
# Iteración: 6.
# Iteración: 7.
# Iteración: 8.
# Iteración: 9.
# Iteración: 10.
# Fin de ejecución del bucle while.
```

Generemos ahora un programa que nos solicite la edad y, en caso de ser el dato
introducido un número negativo, vuelva a preguntarnos de nuevo (siendo así un
ejemplo de bucle `while` de tipo _indeterminado_):

```python
edad = int(input("Introduce tu edad: "))

while edad < 0 or edad > 110:
    print("Has introducido una edad incorrecta. Vuelve a intentarlo.")
    edad = int(input("Introduce tu edad: "))

print(f"Tienes {edad} años. Gracias por colaborar.")
```

Si un usuario se empeña en introducir datos negativos o muy elevados, puede dar
lugar a la aparición de un bucle ''infinito''. Veamos una estrategia para evitar
este tipo de situaciones con un programa que nos permita hallar la raíz cuadrada
de un número:

```python
import math

print("Programa de cálculo de raíces cuadradas")

numero = int(input("Introduce un número: "))

intentos = 0  # Para ejecutar el bucle while un número de veces determinado

while numero < 0:
    print("No se puede hallar la raíz de un número negativo.")
    if intentos == 2:
        print("Has consumido demasiados intentos.")
        print("El programa ha finalizado")
        break
    numero = int(input("Introduce un número: "))
    if numero < 0:
        intentos += 1

if intentos < 2:
    solucion = math.sqrt(numero)
    print(f"La raíz cuadrada de {numero} es {solucion}.")
```

_Notas_:

- La instrucción `break` detiene la ejecución del bucle. Es decir, si durante el
  transcurso de la ejecución de un bucle llegamos a una situación donde se lee
  una instrucción `break`, en ese instante, el flujo del programa deja el bucle
  y salta a la primera línea de código que se encuentra a continuación del
  mencionado bucle.
- En la línea `solucion = math.sqrt(numero)` introducimos el uso de la clase
  `math`, que hemos importado en la primera línea de código (`import math`). Es
  un concepto que se estudiará posteriormente en el curso, pero dicha
  instrucción sirve para encontrar la raíz cuadrada de un número. La utilidad de
  importar clases reside en que podemos aprovechar funciones ya programadas y no
  hemos de ''reinventar la rueda''.

**Ejercicio 1**: crea un programa que pida números infinitamente. Los números
introducidos deben ser cada vez mayores. El programa finalizará cuando se
introduce un número menor que el anterior.

```python
numero = int(input("Introduce un número entero: "))

condicion = True

while condicion:
    num1 = numero
    numero = int(input("Introduce un número entero mayor que el anterior: "))
    if num1 > numero:
        print(f"Valor incorrecto: {num1} no es mayor que {numero}.")
        condicion = False
    else:
        print(f"Valor correcto: {numero} es mayor que {num1}")
```

**Ejercicio 2**: crea un programa que pida números positivos indefinidamente. El
programa termina cuando se introduce un número negativo. Finalmente el programa
muestras la suma de todos los números introducidos.

```python
print("Cálculo de la suma de una serie de números positivos.")
print("Instrucciones: ")
print("- Introduce tantos números positivos como desees sumar.")
print("- Introduce un número negativo para calcular la suma.")

suma = 0
num = int(input("Introduce un número positivo: "))

while num > 0:
    suma += num
    num = int(input("Introduce un número positivo: "))

print(f"La suma de los valores positivos introducios es {suma}.")
```

### 5. Bucles V

#### 5.1. Vídeo

{{< youtube c8WCRTU4udo >}}

#### 5.2. Notas personales

En esta lección, abordaremos el uso de las instrucciones:

- `continue`: provoca que el flujo de ejecución de un programa, dentro de un
  bucle, salte a la siguiente iteración de este.
- `pass`: en cuanto se lee en el interior de un bucle, devuelve `null` (es como
  si no ejecutara el bucle). Su uso es reducido, salvo en definición de clases o
  casos muy concretos (dejar bucles vacíos, que sabemos serán precisos, para
  programar en un futuro próximo).
- `else`: cuando un bucle finaliza todas sus iteraciones, entonces comienza a
  leer las contenidas en el bloque de código asociado a esta instrucción.

Veamos algunos ejemplos:

```python
for letra in "Python":
    print(f"Viendo la letra {letra}.")

# Viendo la letra P.
# Viendo la letra y.
# Viendo la letra t.
# Viendo la letra h.
# Viendo la letra o.
# Viendo la letra n.
```

```python
for letra in "Python":
    if letra == "h":
        continue
    print(f"Viendo la letra {letra}.")

# Viendo la letra P.
# Viendo la letra y.
# Viendo la letra t.
# Viendo la letra o.
# Viendo la letra n.
```

Elaboremos, a continuación, un programa que cuente el número de caracteres de
una cadena de texto, ignorando los espacios en blanco:

```python
nombre = "Píldoras Informáticas"

print(len(nombre))  # 21 (considera espacio en blanco como carácter)

contador = 0

for i in nombre:
    if i == " ":
        continue
    contador += 1

print(contador)  # 20
```

Cuando queremos crear una clase (o función), tan pequeña como sea posible, pero
que seguramente en un futuro ampliemos, la instrucción `pass` es de suma
utilidad:

```python
class mi_clase:
    pass  # A implementar más tarde
```

Por lo que respecta a la instrucción `else`, veamos un código para comprobar si
una dirección de correo electrónico posee o no una arroba:

```python
email = input("Introduce tu email: ")

for i in email:
    if i == "@":
        arroba = True
        break
else:
    arroba = False

print(arroba)
```

Hemos de ser cautos, pues generalmente asociamos la instrucción `else` a
estructuras condicionales y no a bucles. Fijarse en la identación del programa
es clave.
