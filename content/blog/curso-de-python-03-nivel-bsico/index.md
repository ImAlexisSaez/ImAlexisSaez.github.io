---
title: "Curso de Python #03 (Nivel básico)"
summary: Condicionales
date: 2019-07-14
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

### 1. Condicionales I

#### 1.1. Vídeo

{{< youtube iV-4F0jGWak >}}

#### 1.2. Notas personales

Las estructuras condicionales nos permiten alterar el flujo de ejecución de un
programa. Por lo que respecta al condicional `if`, tiene la siguiente sintaxis:

```python
if condición:
    instrucciones
```

La anterior condición suele venir expresada a través de operadores de
comparación (`<`, `>`, `<=`, `>=`, `==`, `!=`). Veamos un sencillo ejemplo de
aplicación de una estructura condicional `if` en la definición de una función:

```python
def evaluacion(nota):
    valoracion = "Aprobado"
    if nota < 5:
        valoracion = "Suspenso"
    return valoracion


print(evaluacion(6))  # Aprobado
print(evaluacion(1))  # Suspenso
print(evaluacion(2.1))  # Suspenso
```

Programemos una versión interactiva del anterior bloque de instrucciones, donde
el usuario ha de introducir la nota durante la ejecución del código (a través de
la función `input()`). Para ello, necesitamos activar la consola mediante el
menú `Tools`, opción `SublimeREPL` y en el apartado `Python` seleccionamos
`Python - RUN current file`.

```python
def evaluacion(nota):
    valoracion = "Aprobado"
    if nota < 5:
        valoracion = "Suspenso"
    return valoracion


print("Programa de evaluación de notas de alumnos")

nota_alumno = input()

print(evaluacion(nota_alumno))
```

No obstante, si ejecutamos e insertamos una nota numérica (por ejemplo, `8`),
_Python_ nos arroja el siguiente error:

```python
# TypeError: '<' not supported between instances of 'str' and 'int'
```

Ello es debido a que cualquier información introducida por el usuario desde el
teclado se almacena como cadena de texto (`"8"`), y el operador `<` no está
preparado para comparar textos y números. Resolvemos esta situación empleando la
función `int()`.

```python
def evaluacion(nota):
    valoracion = "Aprobado"
    if nota < 5:
        valoracion = "Suspenso"
    return valoracion


print("Programa de evaluación de notas de alumnos")

nota_alumno = input()

print(evaluacion(int(nota_alumno)))
```

Siendo una iteración del programa, por ejemplo,

```bash
Programa de evaluación de notas de alumnos
8
Aprobado
```

La función `input()` admite la posibilidad de indicar un mensaje:

```python
def evaluacion(nota):
    valoracion = "Aprobado"
    if nota < 5:
        valoracion = "Suspenso"
    return valoracion


print("Programa de evaluación de notas de alumnos")

nota_alumno = input("Introduce la nota del alumno: ")

print(evaluacion(int(nota_alumno)))
```

Siendo ahora una iteración del programa, por ejemplo:

```bash
Programa de evaluación de notas de alumnos
Introduce la nota del alumno: 8
Aprobado
```

### 2. Condicionales II

#### 2.1. Vídeo

{{< youtube cf7o4s9nFu8 >}}

#### 2.2. Notas personales

En este vídeo ampliaremos las posibilidades de la estructura condicional `if`
mediante `else` y `elif`, quedando entonces su sintaxis como

```python
if condicion:
    instrucciones
elif condicion:
    instrucciones
else:
    instrucciones
```

Empecemos creando un programa de control de acceso:

```python
print("Verificación de acceso")

edad_usuario = int(input("Introduce tu edad: "))

if edad_usuario < 18:
    print("No puedes pasar.")
else:
    print("Puedes pasar.")
```

Veamos el resultado de algunas ejecuciones de este programa:

```bash
Verificación de acceso
Introduce tu edad: 19
Puedes pasar.
```

```bash
Verificación de acceso
Introduce tu edad: 15
No puedes pasar.
```

Añadamos al programa la posibilidad de mostrar un mensaje de error si el usuario
introduce un dato excesivamente elevado:

```python
print("Verificación de acceso")

edad_usuario = int(input("Introduce tu edad: "))

if edad_usuario < 18:
    print("No puedes pasar.")
elif edad_usuario > 100:
    print("Edad incorrecta.")
else:
    print("Puedes pasar.")
```

Veamos el resultado de ejecutar el anterior programa con distintos valores de
edad:

```bash
Verificación de acceso
Introduce tu edad: 25
Puedes pasar.
```

```bash
Verificación de acceso
Introduce tu edad: 15
No puedes pasar.
```

```bash
Verificación de acceso
Introduce tu edad: 124
Edad incorrecta.
```

Para reforzar el uso de esta estructura condicional, elaboremos un programa que
asigna a cada calificación numérica su correspondiente etiqueta:

```python
print("Control de calificaciones")

nota_alumno = int(input("Introduce la nota: "))

if nota_alumno < 0:
    print("Nota incorrecta.")
elif nota_alumno < 5:
    print("Insuficiente.")
elif nota_alumno < 6:
    print("Suficiente.")
elif nota_alumno < 7:
    print("Bien.")
elif nota_alumno < 9:
    print("Notable.")
elif nota_alumno <= 10:
    print("Sobresaliente.")
else:
    print("Nota incorrecta.")
```

Veamos el resultado de ejecutar el anterior programa con distintas
calificaciones:

```bash
Control de calificaciones
Introduce la nota: -6
Nota incorrecta.
```

```bash
Control de calificaciones
Introduce la nota: 4
Insuficiente.
```

```bash
Control de calificaciones
Introduce la nota: 6
Bien.
```

```bash
Control de calificaciones
Introduce la nota: 7
Notable.
```

```bash
Control de calificaciones
Introduce la nota: 10
Sobresaliente.
```

```bash
Control de calificaciones
Introduce la nota: 12
Nota incorrecta.
```

**Ejercicio 1**: crea un programa que pida dos números _enteros_ por teclado. El
programa tendrá una función llamada `devuelve_max` encargada de devolver el
número más alto de los dos introducidos.

```python
def devuelve_max(n1, n2):
    if n1 < n2:
        return n2
    else:
        return n1


num1 = int(input("Introduce el primer número: "))
num2 = int(input("Introduce el segundo número: "))

print("El máximo es: " + str(devuelve_max(num1, num2)))
```

**Ejercicio 2**: crea un programa que pida por teclado ''Nombre'', ''Apellido''
y ''Tfno''. Esos tres datos deberán ser almacenados en una lista y mostrar en
consola el mensaje: ''Los datos personales son: nombre apellido teléfono'' (Se
mostrarán los datos introducidos por teclado).

```python
nombre = input("Nombre: ")
apell = input("Apellido: ")
tfno = input("Teléfono: ")

datos = [nombre, apell, tfno]

print("Los datos personales son: " +
      datos[0] + " " + datos[1] + " " + datos[2])
```

**Ejercicio 3**: crea un programa que pida tres números por teclado. El programa
imprime en consola la media aritmética de los números introducidos.

```python
num1 = float(input("Introduce el primer número: "))
num2 = float(input("Introduce el segundo número: "))
num3 = float(input("Introduce el tercer número: "))

media = (num1 + num2 + num3) / 3

print("La media aritmética es: " + str(media))
```

### 3. Condicionales III

#### 3.1. Vídeo

{{< youtube qxgEolsC6rg >}}

#### 3.2. Notas personales

Aunque en _Python_ no existe una instrucción de tipo `switch`, como en otros
lenguajes de programación, veremos que, gracias a la concatenación de operadores
de comparación, a los operadores lógicos `and` y `or`, y al operador `in`,
disponemos de bastante versatilidad a la hora de trabajar con estructuras
condicionales.

Antes de nada, siguiendo las instrucciones de
[este post](https://stackoverflow.com/a/19977184), creamos un atajo para
ejecutar de manera más ágil nuestros programas. Ahora ya no hemos de navegar por
los menús cada vez que deseemos realizar una ejecución en la consola,
simplemente hemos de emplear la combinación de teclas `ctrl + alt + b` (mientras
que para cerrarla usamos la combinación de teclas `ctrl + w`).

Empecemos creando un programa que controle si un dato numérico introducido para
la edad es válido, es decir, no es negativo ni un valor muy elevado. Para ello,
utilizaremos la concatenación de operadores de comparación, teniendo en cuenta
que su lectura se realiza de izquierda a derecha:

```python
def comprueba_edad(edad):
    if 0 < edad < 100:
        print("La edad es correcta.")
    else:
        print("La edad es incorrecta.")


comprueba_edad(5)  # La edad es correcta.
comprueba_edad(135)  # La edad es incorrecta.
comprueba_edad(-7)  # La edad es incorrecta.
```

Creemos ahora un programa que evaluará el salario de diferentes trabajadores de
una empresa:

```python
sal_presidente = int(input("Introduce el salario del presidente: "))
print("Salario presidente: " + str(sal_presidente))

sal_director = int(input("Introduce el salario del director: "))
print("Salario director: " + str(sal_director))

sal_jefe_area = int(input("Introduce el salario del jefe de área: "))
print("Salario jefe de área: " + str(sal_jefe_area))

sal_administrativo = int(input("Introduce el salario del administrativo: "))
print("Salario administrativo: " + str(sal_administrativo))

if sal_administrativo < sal_jefe_area < sal_director < sal_presidente:
    print("Todo funciona correctamente.")
else:
    print("Algo falla en esta empresa.")
```

### 4. Condicionales IV

#### 4.1. Vídeo

{{< youtube rDGsWYnQEJY >}}

#### 4.2. Notas personales

A continuación, veremos el uso de los operadores lógicos `and` y `or`, y del
operador `in`. Para ello, crearemos un programa que evalúe si un alumno tiene o
no derecho a beca, dependiendo de

- la distancia a la que vive del centro,
- el número de hermanos, y
- el salario familiar.

```python
print("Programa de evaluación de becas - Curso 2018/19")

dist_escuela = int(input("Introduce la distancia a la escuela (en km): "))
print("Distancia a la escuela: " + str(dist_escuela))

num_hermanos = int(input("Introduce el número de hermanos en el centro: "))
print("Número de hermanos: " + str(num_hermanos))

sal_familiar = int(input("Introduce el salario anual bruto: "))
print("Salario anual bruto: " + str(sal_familiar))

if dist_escuela > 40 and num_hermanos > 2 and sal_familiar <= 20000:
    print("Tienes derecho a beca")
else:
    print("No tienes derecho a beca")
```

Revisemos la estrutura condicional para que no sea tan complicado tener derecho
a una beca:

```python
print("Programa de evaluación de becas - Curso 2018/19")

distancia_escuela = int(input("Introduce la distancia a la escuela (en km): "))
print("Distancia a la escuela: " + str(distancia_escuela))

numero_hermanos = int(input("Introduce el número de hermanos en el centro: "))
print("Número de hermanos: " + str(numero_hermanos))

salario_familiar = int(input("Introduce el salario anual bruto: "))
print("Salario anual bruto: " + str(salario_familiar))

if distancia_escuela > 40 or numero_hermanos > 2 or salario_familiar <= 20000:
    print("Tienes derecho a beca")
else:
    print("No tienes derecho a beca")
```

Estudiemos ahora el uso del operador `in`. Crearemos un programa donde un alumno
debe escoger una asignatura opcional de entre un listado predeterminado:

```python
print("Asignaturas optativas - Curso 2018/19")

print("- Informática gráfica")
print("- Pruebas de software")
print("- Usabilidad y accesibilidad")

asignatura = input("Escoge la asignatura optativa: ")

if asignatura in ("Informática gráfica", "Pruebas de software",
                  "Usabilidad y accesibilidad"):
    print("Asignatura elegida: " + asignatura)
else:
    print("La asignatura escogida no está contemplada.")
```

_Python_ es **case sensitive** (distingue entre mayúsculas y minúsculas). Para
solucionar esta situación, utilizamos las funciones `lower()` y `upper()`,
funciones que escriben, respectivamente, una cadena de caracteres toda en
minúsculas o mayúsculas.

```python
print("Asignaturas optativas - Curso 2018/19")

print("- Informática gráfica")
print("- Pruebas de software")
print("- Usabilidad y accesibilidad")

opcion = input("Escoge la asignatura optativa: ")

asignatura = opcion.lower()

if asignatura in ("informática gráfica", "pruebas de software",
                  "usabilidad y accesibilidad"):
    print("Asignatura elegida: " + asignatura)
else:
    print("La asignatura escogida no está contemplada.")
```
