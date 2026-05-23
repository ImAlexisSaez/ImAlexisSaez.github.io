---
title: ¿Cómo transcurre la migración al nuevo sitio?
summary: Una actualización de Hugo desencadenó errores, frustración y una migración inesperada. Doce artículos recuperados después, el proyecto sigue vivo y yo he aprendido (por las malas) que lo primero es actualizar Node.
date: 2026-05-23
lastmod: 2026-05-23
image:
  caption: Imagen generada por Leonardo.Ai
authors:
  - me
categories:
  - Reflexiones
tags:
  - Hugo
  - Página web
status: published
---
### Aprendiendo a querer los mensajes de error

Esta semana ha estado plagada de pensamientos del estilo "¿En qué momento tuve
que tocar nada de la web?" y "¿Pero por qué no son más claros los mensajes de
error?". No obstante, tras unas primeras frustraciones importantes, a estas
alturas tengo la impresión de que el proceso de migración está en marcha y, lo
más sorprendente, hasta puede que llegue a buen puerto.

### El primer muro: no poder trabajar en local

El primer escollo que encontré fue la imposibilidad de trabajar localmente con
la web. Por algún críptico error, que era totalmente indescifrable para un
servidor, tras instalar las extensiones adecuadas en _VS Code_, no había manera
de compilar la web localmente para estudiar qué efecto tenían los cambios que
estaba realizando.

Esto provocó que el flujo de trabajo fuera un tanto tedioso, pues cada
modificación tenía que subirla a _Github_, esperar que estuviera la página web
disponible y comprobar que las modificaciones estaban en línea con la idea que
tenía en la cabeza cuando las apliqué. De esta manera, cualquier mínimo cambio
iniciaba un camino a recorrer de tortuosas esperas.

Dichas esperas alcanzaban su momento álgido cuando cometía algún error y, de
repente, la web desaparecía por completo, sin más indicación para guiarme que un
somero "La página web que estás buscando no está disponible". Durante esta
semana he tenido muchos más errores de ese tipo de los que me gustaría confesar
y hubo algún que otro momento en que la idea de abandonar el proyecto rondó por
mi cabeza.

### La solución: actualizar Node (y un merecido autorreproche)

Cansado de este tipo de situaciones, me animé a abordar el problema desde su
raíz, intentando averiguar el motivo que me impedía compilar localmente la
página web. Tras algún escarceo con documentación, foros e IA, resultó que la
solución era mucho más sencilla de lo que cabía esperar (con el consiguiente
mensaje de crítica dirigido a mí mismo: "Si es que tenía que haber empezado por
aquí"): actualizar _Node_ a su última versión. ¡Los quebraderos de cabeza que me
ha dado una acción tan simple!

En mi defensa voy a argumentar que el ecosistema de esta plantilla ha crecido
tanto que desconozco muchas de las partes que lo componen y es posible que en un
futuro tenga que lidiar con situaciones similares.

### Cambios estructurales: adiós al "copiar y pegar"

Por otro lado, la filosofía que rige la organización de los archivos en la
página web ha cambiado. Eso conlleva que el proceso no se reduzca a un simple
"Meto todas mis antiguas carpetas aquí y apañado".

Empecé recuperando los últimos artículos que había publicado en el anterior blog
(una serie de problemas matemáticos propuestos de nivel de oposición) y encontré
varias sorpresas:

- Los parámetros de cada artículo difieren un tanto de los que tenía
  implementados originalmente. Debo hacer cambios menores en todas las
  cabeceras.
- Algunos de los bloques de matemáticas contenidos en estos artículos, tal y
  como estaban escritos originalmente, no compilan en esta nueva plantilla. Eso
  hizo que me llevara las manos a la cabeza en más de una ocasión. Sin embargo,
  confieso que una vez superado el primer ataque de pánico, tiene solución
  relativamente sencilla, aunque he de modificar individualmente cada bloque
  afectado. Esto hace que la recuperación de artículos vaya a ser un proceso que
  requiera una buena inversión de tiempo.
- Por si no hubiera suficiente cantidad de inconveniente, me ha dado por
  regenerar las imágenes de portada utilizando
  [Leonardo.Ai](https://leonardo.ai/), lo cual se ha convertido en un pozo sin
  fondo de tiempo de escritura de _prompts_ que únicamente es capaz de detener
  el límite diario de _tokens_.

Con todo, en una semana he logrado recuperar aproximadamente una docena de
artículos del blog y estoy bastante contento con el resultado.

### El registro de lecturas: de portadas a tabla

He rediseñado también la parte del registro de lecturas que voy completando. En
la web original inicié tal registro con un bloque que contenía las portadas de
aquellos libros cuya lectura había finalizado. El principal problema residía en
que la magnitud del mencionado bloque empezaba a ser considerable (no estoy muy
seguro de que este hecho, en sí, sea un auténtico "problema") y no terminaba de
gustarme estéticamente la sección correspondiente.

Así pues, he decidido mover de la página de inicio dicho registro y, además,
convertirlo en una tabla donde cada título incluye un enlace a
[Goodreads](https://www.goodreads.com/) para así poder profundizar sobre el
mismo. Más claro, más útil y visualmente más limpio.

### De proyectos a cursos

Finalmente, he retomado el proyecto que abordaba los problemas matemáticos de
oposición. En la nueva plantilla, este tipo de proyectos ha pasado a denominarse
**cursos**. No me desagrada el cambio, pues creo que el enfoque es adecuado para
el contenido de dicho proyecto.

No obstante, el proceso está resultando un tanto tedioso, pues encuentro el
mismo problema con los bloques matemáticos que comenté arriba para los artículos
del blog. Sin prisa, pero sin pausa, iré recuperando las diferentes secciones
que componían dicho curso y hasta me estoy planteando la resolución de algunos
de los problemas que en él aparecen propuestos.

### Lo que viene (con realismo)

Me adentro las próximas semanas en el cierre de curso para la ESO, por lo que el
tiempo que podré dedicar a la página web va a estar bastante limitado.

No obstante, en pequeños ratos perdidos continuaré recuperando contenido antiguo
de la web, con esa extraña sensación en el cuerpo de "¿Cuál será la siguiente
inesperada sorpresa con la que deba batallar?".

Sea cual sea, ya tengo claro que lo primero será actualizar _Node_.
