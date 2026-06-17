---
title: Los 34 grados de libertad de un estudio
summary:
    Breve análisis del artículo 'Degrees of freedom in planning, running,
    analyzing, and reporting psychological studies. A checklist to avoid
    p-hacking'.
date: 2018-08-02
lastmod: 2026-06-17
image:
    caption: Imagen generada por Leonardo.Ai
authors:
    - me
categories:
    - Estadística
tags:
    - Grados de libertad
    - Papers
status: published
---

Hace unos días, completé la lectura del estupendo artículo _"Degrees of freedom
in planning, running, analyzing, and reporting psychological studies. A
checklist to avoid p-hacking"_, cuya lista de autores es casi tan extensa como
el propio título, y de acceso abierto a través de
[este enlace](http://journal.frontiersin.org/article/10.3389/fpsyg.2016.01832/abstract).

En la línea de la famosa idea conocida como _"The Garden of Forking Paths"_,
acuñada por _Andrew Gelman_, el mencionado documento lista los múltiples grados
de libertad existentes en todas y cada una de las fases de un estudio. Ahora
bien, ¿a qué nos referimos cuando hablamos de los grados de libertad de un
estudio?

Sin entrar aquí en demasiado detalle, se trata de ciertas decisiones arbitrarias
(intencionadas o no) que los investigadores toman en sus investigaciones a la
hora de diseñarlas, recoger los datos de interés, analizar éstos y
posteriormente reportarlos en publicaciones científicas. Es lógico entonces que
nos planteemos la siguiente cuestión: ¿qué efecto poseen los grados de libertad
de un estudio sobre las conclusiones alcanzadas?

Entre otras, las dos principales consecuencias son, por un lado, el incremento
de la probabilidad de hallar resultados que no son más que falsos positivos, y,
por otra parte, la posibilidad de inflar las estimaciones para los tamaños de
los efectos observados. Así pues, ¿es posible evitar su aparición en un estudio?

A día de hoy, el mejor método (aunque dista de ser perfecto) para que un estudio
esté libre de grados de libertad es utilizar, de manera precisa y muy detallada,
un recurso conocido como _pre-registro_ (_preregistration_ en inglés). La idea
es presentar, e incluso someter a revisión de pares, el plan que seguirá cierta
investigación antes de realizar la propia recolección de los datos de interés.

En el citado artículo se ofrece un listado (no totalmente exhaustivo) de los
grados de libertad que puede presentar un estudio, restringiendo este al marco
de referencia habitual utilizado para el contraste de hipótesis. De esta forma,
los autores advierten que habría que eliminar o añadir ciertos grados de
libertad si es otra la metodología empleada.

Algunos de los mencionados grados de libertad están relacionados entre sí
(recomiendo consultar la tabla que figura en la última página del artículo) o
incluso pueden llegar a dar la impresión de aparecer por duplicado. No obstante,
se justifica este hecho por la importancia de adoptar cierta decisión en una
fase del estudio u otra.

A modo de resumen, estos son los 34 grados de libertad de un estudio,
desglosados en función de las distintas etapas de una investigación:

- _Fase de generación de hipótesis_:
    - _[T1]_ Llevar a cabo investigaciones exploratorias. Esto conduce a una
      práctica conocida como _"HARKing"_ (_"Hypothesizing After Results are
      Known"_, que vendría a ser generar hipótesis una vez se conocen los
      resultados).
    - _[T2]_ Declarar hipótesis imprecisas que no indiquen la dirección del
      posible efecto. Es un tipo especial de _"HARKing"_, ya que el investigador
      puede luego analizar los datos de dos maneras alternativas.
- _Fase de diseño_:
    - _[D1]_ Crear múltiples condiciones y variables independientes manipuladas.
      A medida que el diseño de un estudio adquiere complejidad, esta práctica
      puede conducir a posibles futuras decisiones con respecto a los niveles de
      las variables que se están considerando o sobre las condiciones en la que
      centra el foco de atención.
    - _[D2]_ Medir variables adicionales sin decidir de antemano si éstas serán
      bien covariables, bien variables independientes, bien variables
      mediadoras, o bien variables moderadoras.
    - _[D3]_ Registrar la misma variable dependiente de diferentes formas
      alternativas. Esta práctica puede tentar al investigador a adoptar al
      final la escala que favorezca la aparición de resultados significativos.
    - _[D4]_ Medir variables dependientes (o incluso probar teorías)
      adicionales, diseñadas en principio como secundarias en el estudio, que
      luego adopten un rol primario en los resultados del estudio si las
      variables principales fallan a la hora de mostrar efecto alguno (esto
      podría considerarse también como una especie de _"HARKing"_).
    - _[D5]_ Incorporar variables adicionales que permitan, _a posteriori_, al
      investigador, la exclusión del análisis de ciertos (o incluso grupos de)
      participantes, con el propósito de encontrar así resultados
      significativos.
    - _[D6]_ No realizar un análisis del poder estadístico del estudio. Es más,
      el investigador suele adoptar una posición extremadamente optimista al
      respecto de este asunto cuando trabaja con muestras pequeñas, lo cual se
      traduce en estudios de bajo poder estadístico.
    - _[D7]_ No informar acerca del plan de muestreo, permitiendo así la
      posibilidad de realizar, de manera consecutiva, múltiples pequeños
      estudios hasta dar con el resultado significativo deseado (y sin haber
      controlado el efecto que esta práctica posee sobre el _error de tipo I_).
- _Fase de recolección de datos_:
    - _[C1]_ No asignar los participantes de un estudio a las condiciones de
      forma aleatoria, lo cual da lugar a la posible aparición de variables de
      confusión.
    - _[C2]_ No escoger de manera acertada la técnica de enmascaramiento
      (simple, doble o triple ciego), bien para los participantes, bien para los
      investigadores, pudiendo sesgar así los resultados del estudio.
    - _[C3]_ Corregir, codificar o descartar datos durante la fase de
      recolección, de una forma no coherente con la técnica de enmascaramiento
      asociada al estudio.
    - _[C4]_ Determinar la regla de parada de recolección de datos en función de
      si se ha obtenido, o no, el resultado deseado.
- _Fase de análisis_: los puntos que se listan a continuación en este apartado
  son una serie de decisiones con marcado carácter
  [_ad hoc_](https://es.wikipedia.org/wiki/Ad_hoc) por parte del investigador.
    - _[A1]_ Seleccionar entre diferentes opciones de tratamiento para los datos
      incompletos o perdidos.
    - _[A2]_ Especificar el pre-procesamiento de los datos (limpieza,
      normalización, suavizado o correcciones).
    - _[A3]_ Dictaminar cómo lidiar con las violaciones de los supuestos
      estadísticos.
    - _[A4]_ Decidir cómo tratar con los valores atípicos.
    - _[A5]_ Determinar la variable dependiente de entre las múltiples
      alternativas existentes asociadas a una misma teoría.
    - _[A6]_ Probar diferentes maneras de anotar o registrar (o emplear
      distintas escalas para) una variable dependiente.
    - _[A7]_ Optar por una teoría alternativa como principal resultado.
    - _[A8]_ Escoger las variables independientes de entre un conjunto de
      variables independientes manipuladas.
    - _[A9]_ Usar las variables independientes manipuladas de diversas formas.
    - _[A10]_ Incluir diferentes variables probándolas bien como covariables,
      bien como variables independientes, bien como variables mediadoras, bien
      como variables moderadoras.
    - _[A11]_ Utilizar las variables independientes no manipuladas de distintas
      maneras.
    - _[A12]_ Usar un criterio alternativo de inclusión y exclusión de
      participantes.
    - _[A13]_ La propia determinación del modelo estadístico.
    - _[A14]_ La elección del método de estimación, el programa informático
      donde se va a llevar a cabo el análisis de datos, y la forma en la que se
      calculan los errores estándar.
    - _[A15]_ La elección del criterio de inferencia.
- _Fase de informe_:
    - _[R1]_ No asegurar la reproducibilidad del estudio.
    - _[R2]_ No habilitar (o facilitar la posibilidad de) la replicación del
      estudio.
    - _[R3]_ Para los estudios que han sido pre-registrados, no mencionar,
      falsificar o identificar erróneamente su pre-registro.
    - _[R4]_ No informar de los denominados "estudios fallidos" que fueron
      originalmente considerados relevantes para la investigación propuesta.
    - _[R5]_ No informar adecuadamente de los resultados y los _p_-valores.
    - _[R6]_ Formular hipótesis después de observar los resultados (el ya
      nombrado _"HARKing"_).

Los autores dedican en el artículo, a cada uno de los anteriores 34 puntos,
algunos párrafos para contextualizarlos, explicar su influencia sobre los
resultados y ofrecer buenas prácticas para evitar que hagan acto de presencia en
el estudio.

En resumen, una lectura que merece la pena y que recomiendo encarecidamente.
