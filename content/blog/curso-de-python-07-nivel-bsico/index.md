---
title: "Curso de Python #07 (Nivel básico)"
summary: Programación orientada a objetos
date: 2019-08-07
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

### 1. Programación OO I

#### 1.1. Vídeo

{{< youtube 5Ohme4A2Weg >}}

#### 1.2. Notas personales

_Python_ es un lenguaje de programación orientado a objetos (POO). Existen,
principalemente, dos paradigmas de programación:

1. Programación orientada a procedimientos.
2. Programación orientada a objetos.

#### 1.3. Programación OP

Algunos ejemplos de lenguajes de programación que siguen este paradigma son:
Fortan, Cobol, Basic...

Entre sus principales desventajas encontramos:

- Las unidades de código son muy grandes en aplicaciones complejas (resultando
  en un número de líneas significativamente elevado).
- En aplicaciones complejas, el código resulta difícil de descifrar.
- Las aplicaciones generadas suelen ser poco reutilizables.
- Si existen fallos en alguna línea del código, es muy probable que el programa
  caiga en su totalidad.
- Aparición frecuente de **código espaguetti** (saltos en el flujo de ejecución
  del programa).
- Es difícil de depurar el código por otros programadores en caso de necesidad o
  error.

#### 1.4. Programación OO

La programación orientada a objetos consiste en trasladar el comportamiento que
tienen los objetos en la vida real al código de programación. Los objetos tienen
un estado, un comportamiento (¿qué puede hacer?) y unas propiedades.

Por ejemplo, pensemos en el objeto ''coche'':

- ¿Cuál es el estado de un coche? Puede estar parado, circulando, aparcado...
- ¿Qué propiedades tiene un coche? Tiene un color, un peso, un tamaño...
- ¿Qué comportamiento tiene un coche? Puede arrancar, frenar, acelerar, girar...

| Objeto                  | Coche                                |
| ----------------------- | ------------------------------------ |
| Propiedades (atributos) | Color, peso, alto, largo...          |
| Comportamiento          | Arrancar, frenar, girar, acelerar... |

Algunos ejemplos de lenguajes de programación que emplean este paradigma son:
C++, Java, VisualNet...

Entre las principales ventajas encontramos:

- Los programas están divididos en ''trozos'', ''partes'', ''módulos'' o
  ''clases'', es decir, existe **modularización**.
- El código es muy reutilizable. Aparece en el concepto de **herencia**.
- Si existen fallos en alguna línea del código, el programa es posible que
  continue con su funcionamiento, debido al **control de excepciones**.
- Surge el concepto de **encapsulamiento**.

El vocabulario más frecuente de este paradigma de programación incluye palabras
o expresiones como:

- Clase.
- Objeto.
- Ejemplar de clase. Instancia de clase. Ejemplarizar una clase. Instanciar una
  clase.
- Modularización.
- Encapsulamiento / encapsulación.
- Herencia.
- Polimorfismo.

### 2. Programación OO II

#### 2.1. Vídeo

{{< youtube 2UNrSiKEI8w >}}

#### 2.2. Notas personales

Una **clase** es un modelo donde se redactan las características comunes de un
grupo de objetos.

Una **instancia** (o **ejemplar** u **objeto**) es un miembro concreto de una
clase.

La **modularización** surge cuando un programa está compuesto de diversas
clases. Cada una de ellas funciona de manera independiente (facilitando así
enormemente su mantenimiento y control de excepciones) y es posible su
reutilización en otros programas.

La **encapsulación** nos permite proteger el funcionamiento interno de cierto
bloque de código, para que no pueda accederse o alterarse desde el exterior de
manera inadecuada. No obstante, todas las clases de un programa estarán
''conectadas'' entre sí de cierta manera (mediante **métodos de acceso** a
ciertas características de cada una de las clases).

El mencionado acceso se llevará a cabo empleando la **nomenclatura del punto**.
Por ejemplo, supongamos que hemos creado un objeto, de la clase `coche`, llamado
`miCoche`. Para acceder a sus propiedades, utilizaremos la sintaxis:

- `miCoche.color = ''rojo''`
- `miCoche.peso = 1500`
- `miCoche.ancho = 2000`
- `miCoche.alto = 900`

De forma similar, el acceso al comportamiento de este objeto se realizará
mediante la mencionada nomenclatura:

- `miCoche.arranca()`
- `miCoche.frena()`
- `miCoche.gira()`
- `miCoche.acelera()`

### 3. Programación OO III

#### 3.1. Vídeo

{{< youtube Y_SiIgxc-xI >}}

#### 3.2. Notas personales

Traslademos a código fuente algunos de los conceptos examinados en las dos
lecciones anteriores. La sintaxis para crear la clase `Coche` sería:

```python
class Coche():
    instrucciones
```

Empecemos declarando las **propiedades** de la clase `Coche`:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False
```

Definamos **comportamientos** para los futuros objetos que pertenezcan a esta
clase, que vienen determinados por distintos métodos:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False

    def function(self):
        pass
```

En _Sublime Text 3_ cuando empezamos a escribir `def` nos ofrece dos opciones,
crear una **función** o un **método**. La principal diferencia radica en que la
primera no pertenece a ninguna clase, al contrario que la segunda. Podemos, a
través de los cursores, escoger en el editor la opción que apunta a un método y
se nos proporciona la sintaxis de uno por defecto, como el que se muestra
arriba.

Una vez editado, el código queda:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False

    def arrancar(self):
        pass
```

_Nota_: `self` hace referencia al propio objeto perteneciente a la clase, es
decir, a la instancia perteneciente a la clase.

Construyamos un objeto de la clase `Coche` y veamos cómo acceder a sus
propiedades:

```python
mi_coche = Coche()  # Instanciación de una clase

print("Largo del coche: ", mi_coche.largo_chasis)  # Largo del coche:  250
print("Número de ruedas: ", mi_coche.ruedas)  # Número de ruedas:  4
```

Trabajemos en el método declarado, para ello, escribimos:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False

    def arrancar(self):
        self.en_marcha = True
```

Así, ahora:

```python
print("En marcha: ", mi_coche.en_marcha)  # En marcha:  False
mi_coche.arrancar()
print("En marcha: ", mi_coche.en_marcha)  # En marcha:  True
```

Esta última acción la podríamos haber llevado a cabo a través de otro
comportamiento, `estado`:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False

    def arrancar(self):
        self.en_marcha = True

    def estado(self):
        if self.en_marcha:
            return "El coche está en marcha."
        else:
            return "El coche está parado."


print(mi_coche.estado())  # El coche está parado.
mi_coche.arrancar()
print(mi_coche.estado())  # El coche está en marcha.
```

En resumen, hemos creado la clase `Coche`, que se caracteriza por poseer cuatro
propiedades y dos comportamientos.

### 4. Programación OO IV

#### 4.1. Vídeo

{{< youtube x5CY8fVyYLo >}}

#### 4.2. Notas personales

Partamos del código del último ejemplo de la lección anterior:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False

    def arrancar(self):
        self.en_marcha = True

    def estado(self):
        if self.en_marcha:
            return "El coche está en marcha."
        else:
            return "El coche está parado."
```

Generemos dos objetos y comparémoslos:

```python
mi_coche1 = Coche()
mi_coche2 = Coche()

print("Largo mi_coche1: ", mi_coche1.largo_chasis)  # Largo mi_coche1:  250
print("Largo mi_coche2: ", mi_coche2.largo_chasis)  # Largo mi_coche2:  250

mi_coche1.arrancar()
print(mi_coche1.estado())  # El coche está en marcha.
print(mi_coche2.estado())  # El coche está parado.
```

Sería buena idea que el método `arrancar()`, además de arrancar el coche, nos
informase de su estado (en marcha o parado). También, programaremos el método
`estado()` para que nos ofrezca información del coche:

```python
class Coche():
    largo_chasis = 250
    ancho_chasis = 120
    ruedas = 4
    en_marcha = False

    def arrancar(self, arrancamos):
        self.en_marcha = arrancamos
        if self.en_marcha:
            return "El coche está en marcha."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.ruedas, "ruedas. Un ancho de",
              self.ancho_chasis, "cm y un largo de", self.largo_chasis, "cm.")


mi_coche1 = Coche()
mi_coche2 = Coche()

print(mi_coche1.arrancar(True))  # El coche está en marcha.
print(mi_coche2.arrancar(False))  # # El coche está parado.
mi_coche1.estado()
# El coche tiene 4 ruedas. Un ancho de 120 cm y un largo de 250 cm.
mi_coche2.estado()
# El coche tiene 4 ruedas. Un ancho de 120 cm y un largo de 250 cm.
```

En programación orientada a objetos, las características comunes suelen formar
parte de lo que se conoce como **estado inicial**. Para especificar dicho estado
utilizaremos un **constructor**, que es un método especial que le da estado a
los objetos que pertenecen a una clase. Su sintaxis vendrá dada por

```python
def __init__(self):
    propiedades
```

Así, el código de la clase quedaría:

```python
class Coche():
    def __init__(self):
        self.largo_chasis = 250
        self.ancho_chasis = 120
        self.ruedas = 4
        self.en_marcha = False

    def arrancar(self, arrancamos):
        self.en_marcha = arrancamos
        if self.en_marcha:
            return "El coche está en marcha."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.ruedas, "ruedas. Un ancho de",
              self.ancho_chasis, "cm y un largo de", self.largo_chasis, "cm.")
```

¿Qué sucede si intentamos ahora incrementar a cinco el número de ruedas del
segundo coche?

```python
mi_coche2 = Coche()

print(mi_coche2.arrancar(False))

mi_coche2.ruedas = 5

mi_coche2.estado()
```

```bash
El coche está parado.
El coche tiene 5 ruedas. Un ancho de 120 cm y un largo de 250 cm.
```

Esta acción, en ciertos casos, no debería estar permitida. Para ello, entra en
juego el concepto de **encapsulación**, que nos permitirá proteger propiedades
para que no se puedan modificar desde fuera de la propia clase. Su aplicación es
tan sencilla como preceder con `__` el nombre de la propiedad a proteger y en
aquellos lugares donde luego aparezca:

```python
class Coche():
    def __init__(self):
        self.largo_chasis = 250
        self.ancho_chasis = 120
        self.__ruedas = 4
        self.en_marcha = False

    def arrancar(self, arrancamos):
        self.en_marcha = arrancamos
        if self.en_marcha:
            return "El coche está en marcha."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.__ruedas, "ruedas. Un ancho de",
              self.ancho_chasis, "cm y un largo de", self.largo_chasis, "cm.")
```

```python
mi_coche2 = Coche()

print(mi_coche2.arrancar(False))

mi_coche2.__ruedas = 5

mi_coche2.estado()
```

```bash
El coche está parado.
El coche tiene 4 ruedas. Un ancho de 120 cm y un largo de 250 cm.
```

En esta ocasión, las cuatro propiedades deberían encapsularse. Incluso
`en_marcha`, ya que queremos modificarla únicamente desde el interior de la
clase.

La clase entonces quedaría:

```python
class Coche():
    def __init__(self):
        self.__largo_chasis = 250
        self.__ancho_chasis = 120
        self.__ruedas = 4
        self.__en_marcha = False

    def arrancar(self, arrancamos):
        self.__en_marcha = arrancamos
        if self.__en_marcha:
            return "El coche está en marcha."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.__ruedas, "ruedas. Un ancho de",
              self.__ancho_chasis, "cm y un largo de", self.__largo_chasis,
              "cm.")
```

De la misma manera, se pueden encapsular métodos, opción que estudiaremos en
futuras lecciones.

### 5. Programación OO V

#### 5.1. Vídeo

{{< youtube OU-e2uhoGxE >}}

#### 5.2. Notas personales

A continuación, abordaremos la encapsulación de métodos partiendo del último
ejemplo de la lección anterior:

```python
class Coche():
    def __init__(self):
        self.__largo_chasis = 250
        self.__ancho_chasis = 120
        self.__ruedas = 4
        self.__en_marcha = False

    def arrancar(self, arrancamos):
        self.__en_marcha = arrancamos
        if self.__en_marcha:
            return "El coche está en marcha."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.__ruedas, "ruedas. Un ancho de",
              self.__ancho_chasis, "cm y un largo de", self.__largo_chasis,
              "cm.")
```

Encapsular un método es hacer que sea únicamente accesible desde la propia
clase, no desde fuera.

Como aplicación práctica de este procedimiento, generemos un método que
compruebe que todo está en orden antes de arrancar, `chequeo_interno(self)`, que
llamaremos desde `arrancar()`.

```python
class Coche():
    def __init__(self):
        self.__largo_chasis = 250
        self.__ancho_chasis = 120
        self.__ruedas = 4
        self.__en_marcha = False

    def arrancar(self, arrancamos):
        self.__en_marcha = arrancamos

        if self.__en_marcha:
            chequeo = self.chequeo_interno()

        if self.__en_marcha and chequeo:
            return "El coche está en marcha."
        elif self.__en_marcha and not chequeo:
            return "Algo ha ido mal en el chequeo. No podemos arrancar."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.__ruedas, "ruedas. Un ancho de",
              self.__ancho_chasis, "cm y un largo de", self.__largo_chasis,
              "cm.")

    def chequeo_interno(self):
        print("Realizando chequeo interno.")

        self.gas = "Ok"
        self.aceite = "Ok"
        self.puertas = "Ok"

        if self.gas == "Ok" and self.aceite == "Ok" and self.puertas == "Ok":
            return True
        else:
            return False
```

Así, si ahora tecleamos:

```python
mi_coche1 = Coche()

print(mi_coche1.arrancar(True))

mi_coche1.estado()

print("---- Segundo vehículo ----")

mi_coche2 = Coche()

print(mi_coche2.arrancar(False))

mi_coche2.estado()
```

El resultado será:

```bash
Realizando chequeo interno.
El coche está en marcha.
El coche tiene 4 ruedas. Un ancho de 120 cm y un largo de 250 cm.
---- Segundo vehículo ----
El coche está parado.
El coche tiene 4 ruedas. Un ancho de 120 cm y un largo de 250 cm.
```

El método `chequeo_interno()` es accesible desde fuera de la clase (no está
encapsulado), pero, ¿es lógico que podamos acceder a él en cualquier momento?
¿Incluso si está parado? Si el método está diseñado para ejecutarse únicamente
en el momento previo a arrancar, hemos de ''protegerlo''.

```python
mi_coche2 = Coche()

print(mi_coche2.arrancar(False))
print(mi_coche2.chequeo_interno())  # Absurdo en este caso
mi_coche2.estado()
```

```bash
El coche está parado.
Realizando chequeo interno.
True
El coche tiene 4 ruedas. Un ancho de 120 cm y un largo de 250 cm.
```

Para encapsular el mencionado método, utilizamos la estrategia de `__`:

```python
class Coche():
    def __init__(self):
        self.__largo_chasis = 250
        self.__ancho_chasis = 120
        self.__ruedas = 4
        self.__en_marcha = False

    def arrancar(self, arrancamos):
        self.__en_marcha = arrancamos

        if self.__en_marcha:
            chequeo = self.__chequeo_interno()

        if self.__en_marcha and chequeo:
            return "El coche está en marcha."
        elif self.__en_marcha and not chequeo:
            return "Algo ha ido mal en el chequeo. No podemos arrancar."
        else:
            return "El coche está parado."

    def estado(self):
        print("El coche tiene", self.__ruedas, "ruedas. Un ancho de",
              self.__ancho_chasis, "cm y un largo de", self.__largo_chasis,
              "cm.")

    def __chequeo_interno(self):
        print("Realizando chequeo interno.")

        self.gas = "Ok"
        self.aceite = "Ok"
        self.puertas = "Ok"

        if self.gas == "Ok" and self.aceite == "Ok" and self.puertas == "Ok":
            return True
        else:
            return False
```

De forma que si ahora escribimos:

```python
mi_coche2 = Coche()

print(mi_coche2.arrancar(False))
print(mi_coche2.__chequeo_interno())
mi_coche2.estado()
```

El resultado es:

```bash
El coche está parado.
Traceback (most recent call last):
  File "prac28_poo5_1.py", line 50, in <module>
    print(mi_coche2.__chequeo_interno())
AttributeError: 'Coche' object has no attribute '__chequeo_interno'
```

Es decir, _Python_ arroja un error. No nos deja llamar al método
`__chequeo_interno()` desde fuera de la propia clase `Coche` porque está
encapsulado.

¿Cuándo encapsular una variable o un método? No existe una ''regla de oro'',
esto es, habremos de hacerlo cuando la clase así lo precise, dependiendo del
comportamiento que posea una clase y en función del criterio del propio
programador.

### 6. Programación OO VI

#### 6.1. Vídeo

{{< youtube u_VbLsIyzRk >}}

#### 6.2. Notas personales

En programación orientada a objetos, el concepto de **herencia** intenta dar una
réplica aproximada de su contrapartida en la vida real. De una clase, denominada
en ocasiones **clase padre** o **superclase**, heredarán otras clases atributos,
métodos... Se conocen estas últimas como **subclases** de la anterior (y también
como **superclases** si de ellas también heredan otras).

La principal utilidad de la herencia es la reutilización de código cuando se
generan clases ''similares''. Hemos de estudiar las características y
comportamientos que poseen en común todos los objetos con los que deseamos
trabajar. Todo ello lo englobaremos en una **superclase**, de la cual luego
heredarán otras clases, que aun teniendo características en común, también es
cierto que existen otras peculiaridades que las diferencian.

Veamos un ejemplo práctico:

```python
# Clase Padre
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


# Clase hija
class Moto(Vehiculo):
    pass


mi_moto = Moto("Honda", "CBR")

mi_moto.estado()
```

```bash
Marca: Honda
Modelo: CBR
En marcha: False
Acelerando: False
Frenando: False
```

Estamos utilizando métodos de la clase `Vehiculo` a través de la clase `Moto`
gracias a la herencia.

### 7. Programación OO VII

#### 7.1. Vídeo

{{< youtube jMQQN9OxwVc >}}

#### 7.2. Notas personales

Continuemos con el ejemplo de la lección anterior:

```python
# Clase Padre
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


# Clase hija
class Moto(Vehiculo):
    pass
```

Construyamos la clase `Moto`, añadiendo un comportamiento nuevo, `caballito`,
que se va a sumar a los cuatro heredados de la clase `Vehiculo`:

```python
class Moto(Vehiculo):
    hcaballito = ""

    def caballito(self):
        hcaballito = "Voy haciendo el caballito."
```

Ahora podríamos teclear:

```python
mi_moto = Moto("Honda", "CBR")

mi_moto.caballito()

mi_moto.estado()
```

```bash
Marca: Honda
Modelo: CBR
En marcha: False
Acelerando: False
Frenando: False
```

El programa ''funciona'' (al menos no arroja errores), pero no nos está
informando si estamos haciendo el caballito o no.

Abordemos esta situación sobreescribiendo el método `estado` heredado de la
clase `Vehiculo`, para así incorporar la información sobre el nuevo
comportamiento de la clase `Moto`.

Para sobreescribir un método de la clase padre definimos uno en la clase hija
que se caracterice por tener el mismo nombre y número de parámetros:

```python
class Moto(Vehiculo):
    hcaballito = ""

    def caballito(self):
        self.hcaballito = "Voy haciendo el caballito."

    def estado(self):
        print("Marca:", self.marca, "\nModelo:", self.modelo, "\nEn marcha:",
              self.enmarcha, "\nAcelerando:", self.acelera, "\nFrenando:",
              self.frena, "\n", self.hcaballito)
```

De esta manera, la ejecución del siguiente bloque de código:

```python
mi_moto = Moto("Honda", "CBR")

mi_moto.caballito()

mi_moto.estado()
```

Produce como resultado ahora:

```bash
Marca: Honda
Modelo: CBR
En marcha: False
Acelerando: False
Frenando: False
 Voy haciendo el caballito.
```

Modifiquemos el código para albergar la posibilidad de trabajar con furgonetas:

```python
class Furgoneta(Vehiculo):
    def carga(self, cargar):
        self.cargado = cargar
        if self.cargado:
            return "La furgoneta está cargada."
        else:
            return "La furgoneta no está cargada."
```

Así,

```python
mi_furgo = Furgoneta("Renault", "Kangoo")

mi_furgo.arrancar()

mi_furgo.estado()

mi_furgo.carga(True)
```

```bash
Marca: Renault
Modelo: Kangoo
En marcha: True
Acelerando: False
Frenando: False
```

Todo funciona de manera adecuada, con la salvedad de que no estamos viendo que
la furgoneta está cargada. Como el método `carga()` devuelve una cadena de
texto, añadiendo una función `print()` solucionamos el entuerto:

```python
mi_furgo = Furgoneta("Renault", "Kangoo")

mi_furgo.arrancar()

mi_furgo.estado()

print(mi_furgo.carga(True))
```

```bash
Marca: Renault
Modelo: Kangoo
En marcha: True
Acelerando: False
Frenando: False
La furgoneta está cargada.
```

Obviamente, una instrucción del tipo `mi_moto.carga()` arroja un error, ya que
no hereda de `Furgoneta` la clase `Moto`, sino de `Vehiculo`.

Añademos soporte para vehículos electrónicos:

```python
class VehiculoElec():
    def __init__(self):
        self.autonomia = 100

    def cargar_energia(self):
        self.cargando = True
```

Y, a continuación, generemos una clase para trabajar con biciletas eléctricas.
Estas tienen marca, modelo, pueden arrancar, frenar... y a la vez también poseen
autonomia y la posibilidad de cargar energía. _Python_ nos permite heredar de
dos o más clases, que se conoce como **herencia múltiple**:

```python
class BicicletaElec(VehiculoElec, Vehiculo):
    pass
```

Hemos de tener en cuenta que cuando se da herencia múltiple, a la hora de tomar
el constructor o los diferentes métodos, se da la preferencia según hayamos
ordenado las clases padres de las que hereda. En este caso, no podemos iniciar
una bicicleta eléctrica con marca y modelo, aprovechando así el constructor de
la clase `Vehiculo`, ya que la clase `VehiculoElec` posee su propio constructor
y este último tiene preferencia por haber colocado esta clase primero en la
definición de `BicicletaElec`.

```python
mi_bici = BicicletaElec("Orbea", "HCI30")
```

```bash
Traceback (most recent call last):
  File "prac30_poo7_3.py", line 58, in <module>
    mi_bici = BicicletaElec("Orbea", "HCI30")
TypeError: __init__() takes 1 positional argument but 3 were given
```

No obstante, si intercambiamos el orden de las clases padre en la definición de
`BicicletaElec`:

```python
class BicicletaElec(Vehiculo, VehiculoElec):
    pass


mi_bici = BicicletaElec("Orbea", "HCI30")

mi_bici.estado()
```

La ejecución ya no arroja errores, mostrando el siguiente resultado:

```bash
Marca: Orbea
Modelo: HCI30
En marcha: False
Acelerando: False
Frenando: False
```

### 8. Programación OO VIII

#### 8.1. Vídeo

{{< youtube oe04X1B14YY >}}

#### 8.2. Notas personales

En esta lección estudiaremos el uso de las funciones

- `super()` e
- `isinstance()`.

Partimos del último ejemplo de la lección anterior:

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


class VehiculoElec():
    def __init__(self):
        self.autonomia = 100

    def cargar_energia(self):
        self.cargando = True


class BicicletaElec(VehiculoElec, Vehiculo):
    pass
```

Si queremos crear un objeto de la clase `BicicletaElec` que posea una marca y un
modelo, tenemos dos opciones disponibles:

- Acudir al método `__init__()` de la clase `VehiculoElec` y copiar las líneas
  que nos interesen del método homónimo de la clase `Vehiculo`. No obstante,
  este enfoque es, cuanto menos, poco elegante.
- Utilizar la función `super()`, cuya utilidad reside en que procede a llamar al
  método de la clase padre.

Veamos esta segunda aproximación con un ejemplo un tanto más sencillo:

```python
class Persona():
    def __init__(self, nombre, edad, residencia):
        self.nombre = nombre
        self.edad = edad
        self.residencia = residencia

    def describir(self):
        print("Nombre:", self.nombre, "\nEdad:", self.edad, "\nResidencia:",
              self.residencia)


class Empleado(Persona):
    def __init__(self, salario, antiguedad):
        self.salario = salario
        self.antiguedad = antiguedad
```

Ahora podríamos comenzar a construir objetos de ambas clases:

```python
antonio = Persona("Antonio", 55, "España")

antonio.describir()
```

```bash
Nombre: Antonio
Edad: 55
Residencia: España
```

Para constuir un objeto de la clase `Empleado`, hemos de tener en cuenta que
tomará como argumentos los parámetros declarados en dicha clase, y no los de
`Persona`. No obstante, a la hora de emplear el método `describir()`
encontraremos problemas tal y como están programadas ambas clases:

```python
juan = Empleado(1500, 15)

juan.describir()
```

```bash
Traceback (most recent call last):
  File "prac31_poo8_2.py", line 24, in <module>
    juan.describir()
  File "prac31_poo8_2.py", line 8, in describir
    print("Nombre:", self.nombre, "\nEdad:", self.edad, "\nResidencia:",
AttributeError: 'Empleado' object has no attribute 'nombre'
```

Podemos reescribir el constructor de la clase `Empleado`, haciendo uso de la
función `super()`, como sigue:

```python
class Empleado(Persona):
    def __init__(self, salario, antiguedad):
        super().__init__("Juan", 33, "Italia")
        self.salario = salario
        self.antiguedad = antiguedad
```

De manera que ahora el código no arrojará error alguno:

```python
juan = Empleado(1500, 15)

juan.describir()
```

```bash
Nombre: Juan
Edad: 33
Residencia: Italia
```

No obstante, programado así, todos nuestros empleados se llamarían Juan,
tendrían 33 años y serían italianos. Veamos cómo generalizar el funcionamiento
de la anterior clase:

```python
class Empleado(Persona):
    def __init__(self, salario, antiguedad, nombre_empleado, edad_empleado,
                 residencia_empleado):
        super().__init__(nombre_empleado, edad_empleado, residencia_empleado)
        self.salario = salario
        self.antiguedad = antiguedad

    def describir(self):
        super().describir()
        print("Salario:", self.salario, "\nAntigüedad:", self.antiguedad)
```

De paso, hemos mejorado también el método `describir()`, que procede a llamar al
de la clase padre y, además, añade la información correspondiente al salario y a
la antigüedad. De este modo,

```python
juan = Empleado(1500, 15, "Juan", 33, "Italia")

juan.describir()
```

```bash
Nombre: Juan
Edad: 33
Residencia: Italia
Salario: 1500
Antigüedad: 15
```

La función `isinstance()` nos informa si un objeto es instancia de una clase
determinada:

```python
juan = Empleado(1500, 15, "Juan", 33, "Italia")

juan.describir()

print(isinstance(juan, Persona))  # True
print(isinstance(juan, Empleado))  # True

marco = Persona("Marco", 51, "Francia")

print(isinstance(marco, Persona))  # True
print(isinstance(marco, Empleado))  # False
```

Con todo, modifiquemos el ejemplo inicial para permitir que una bicicleta
eléctrica admita marca y modelo.

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


class BicicletaElec(VehiculoElec, Vehiculo):
    pass
```

Notemos que:

- Hemos utilizado la función `super()` en el método `__init__()` de
  `VehiculoElec`.
- Hemos declarado que la clase `VehiculoElec` hereda de `Vehiculo`.

Así,

```python
mi_bici = BicicletaElec("Orbea", "HCI30")

mi_bici.estado()
```

```bash
Marca: Orbea
Modelo: HCI30
En marcha: False
Acelerando: False
Frenando: False
```

### 9. Programación OO IX

#### 9.1. Vídeo

{{< youtube kV1cN_bqcSw >}}

#### 9.2. Notas personales

En esta lección, abordaremos el concepto de **polimorfismo**. Un objeto puede
cambiar de forma dependiendo del contexto en el que se utilice y, por tanto,
modificar tanto sus propiedades como sus comportamientos asociados.

Como _Python_ es un lenguaje de tipado dinámico, esta característica es sencilla
de utilizar.

Veamos un ejemplo:

```python
class Coche():
    def desplazamiento(self):
        print("Me desplazo utilizando cuatro ruedas.")


class Moto():
    def desplazamiento(self):
        print("Me desplazo utilizando dos ruedas.")


class Camion():
    def desplazamiento(self):
        print("Me desplazo utilizando seis ruedas.")
```

Así, si ahora tecleamos:

```python
mi_vehiculo = Moto()

mi_vehiculo.desplazamiento()

mi_vehiculo2 = Coche()

mi_vehiculo2.desplazamiento()

mi_vehiculo3 = Camion()

mi_vehiculo3.desplazamiento()
```

```bash
Me desplazo utilizando dos ruedas.
Me desplazo utilizando cuatro ruedas.
Me desplazo utilizando seis ruedas.
```

Si tuviésemos cientos de vehículos y quisiéramos utilizar sus comportamientos,
habríamos de seguir el patrón esbozado arriba.

No obstante, nos podemos aprovechar de la magia del polimorfismo creando una
función como se muestra a continuación:

```python
def desplazamiento_vehiculo(vehiculo):
    vehiculo.desplazamiento()
```

Y como el objeto `vehiculo` posee la capacidad de adquirir el rol de cualquiera
de los vehículos programados arriba (coche, moto o camión), _Python_ en todo
momento sabrá a qué método `desplazamiento()` acudir en cada instante.

Así, si escribimos:

```python
mi_vehiculo = Camion()

desplazamiento_vehiculo(mi_vehiculo)

mi_vehiculo = Coche()

desplazamiento_vehiculo(mi_vehiculo)

mi_vehiculo = Moto()

desplazamiento_vehiculo(mi_vehiculo)
```

```bash
Me desplazo utilizando seis ruedas.
Me desplazo utilizando cuatro ruedas.
Me desplazo utilizando dos ruedas.
```
