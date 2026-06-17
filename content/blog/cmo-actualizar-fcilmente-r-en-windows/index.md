---
title: ¿Cómo actualizar fácilmente R en Windows?
summary:
    El proceso de actualización de la versión del lenguaje de programación R
    puede resultar un tanto tedioso si lo llevamos a cabo de forma manual.
    Veamos cómo hacer más liviana esta pesada carga.
date: 2018-08-04
lastmod: 2026-06-17
image:
    caption: Imagen generada por Leonardo.Ai
authors:
    - me
categories:
    - Tutoriales
tags:
    - R
    - Windows
status: published
---

El proceso de actualización de la versión del lenguaje de programación _R_ puede
resultar un tanto tedioso si lo llevamos a cabo de forma manual. Veamos cómo
hacer más liviana esta pesada carga.

Por fortuna, tenemos a nuestra disposición el paquete
[installr](https://cran.r-project.org/web/packages/installr/index.html), que se
encarga de todo el anterior procedimiento automáticamente, a través de la
llamada a la función `updateR()`.

De esta forma, basta con que tengamos a mano un _script_ similar al que se
muestra a continuación, y procedamos a ejecutarlo cuando se anuncie una nueva
versión de _R_:

```r
# Instala el paquete
install.packages("installr")

# Actualiza R
library(installr)
updateR()
```

Al utilizar la función `updateR()`:

- Se comprueba cuál es la última versión de _R_. Si estamos al día, nos mostrará
  una ventana de confirmación de tal hecho. En caso contrario, nos dará la
  posibilidad de consultar las novedades de dicha versión y nos permitirá
  proceder a su descarga e instalación.
- Una vez completado el proceso, nos preguntará si deseamos mover (y borrar) las
  librerías desde nuestra antigua versión a la nueva. Además, nos dará la opción
  de ponerlas al día. Dependiendo del número de librerías que tengamos
  instaladas, completar estas acciones puede llevarnos un buen rato.

Si usamos _RStudio_, al principio se nos mostrará un aviso sugiriéndonos que
llevemos a cabo todo el proceso desde la propia interfaz de _R_, en lugar de a
través de este _IDE_. No obstante, en mi experiencia, podemos tranquilamente
ignorar la advertencia y realizar el procedimiento utilizando _RStudio_. Al
terminar, bastará con que reiniciemos el programa para que todo funcione con
normalidad.

Finalmente, podemos ahorrarnos la sucesión de ventanas emergentes si sabemos de
antemano que queremos actualizar _R_, mover (no copiar) las librerías y
actualizarlas. Para ello, reescribimos el anterior script como sigue:

```r
# Instala / carga el paquete
if(!require(installr)) {install.packages("installr"); require(installr)}

# Instala R, mueve y actualiza paquetes
updateR(F, T, T, F, T, F, T)
```
