---
title: Tutorial sobre Machine Learning con Python
summary:
    ¿Qué tal invertir las próximas seis horas y media de tu vida disfrutando de
    un tutorial sobre Machine Learning con Python? Suena interesante, ¿verdad?
    Al menos es así en esta especie de universo paralelo donde parece que vivo
    últimamente.
date: 2018-08-16
lastmod: 2026-06-22
image:
    caption: Imagen generada por Leonardo.Ai
authors:
    - me
categories:
    - Tutoriales
tags:
    - Machine learning
    - Python
    - SciPy
status: published
---

¿Te has quedado sin planes para el fin de semana? Aunque tu lista de tareas
pendientes y, generalmente, poco atractivas parezca haber crecido de manera
exponencial en los últimos tiempos, ¿el cuerpo te pide algo distinto?

¿Qué tal invertir las próximas seis horas y media de tu vida disfrutando de un
tutorial sobre _Machine Learning_ con _Python_? Suena interesante, ¿verdad? Al
menos es así en esta especie de universo paralelo donde parece que vivo
últimamente.

En la cuenta de _YouTube_ asociada a
[Enthought](https://www.youtube.com/user/EnthoughtMedia), creadores de la
conocida distribución _Canopy_ para _Python_, ha aparecido recientemente una
[lista de reproducción](https://www.youtube.com/playlist?list=PLYx7XA2nY5GfdAFycPLBdUDOUtdQIVoMf)
que alberga los tutoriales y charlas correspondientes a la última convención
_SciPy_: "SciPy 2017: Scientific Computing with Python Conference".

Aquel al que hacía referencia en el primer párrafo estuvo dividido en dos
sesiones, a las que podemos acceder directamente a través de los siguientes
enlaces:

- [Machine Learning with scikit learn Part One - SciPy 2017 Tutorial - Andreas Mueller & Alexandre Gram](https://youtu.be/2kT6QOVSgSg).
- [Machine Learning with scikit learn Part Two - SciPy 2017 Tutorial - Andreas Mueller & Alexandre Gram](https://youtu.be/WLYzSas511I).

No obstante, antes de lanzarte de cabeza a su visualización, te recomendaría
adoptases una actitud de aprendizaje activo para un mayor aprovechamiento. Es un
tutorial bastante práctico, que se apoya en el uso de numerosos _Jupyter
Notebooks_ que también tenemos a nuestra disposición sin coste alguno. ¿Por qué
no experimentar personalmente con el código para así reforzar las ideas vertidas
y el uso de distintos algoritmos?

La única pega que presenta esta aproximación al tutorial reside en que nuestro
equipo debe cumplir una serie de requisitos, que exploraremos rápidamente en la
siguiente sección.

## Instalación de las herramientas asociadas

En función de los distintos programas que ya estén instalados en nuestro
sistema, el paseo por el siguiente listado nos llevará más o menos tiempo:

1. Utilizando nuestro navegador favorito, dirijámonos en primer lugar al
   [repositorio](https://github.com/amueller/scipy-2017-sklearn) en _GitHub_,
   que contiene los _notebooks_ asociados al tutorial.

2. Echemos un rápido vistazo a su archivo `README.md`, que alberga información
   de interés sobre el mencionado tutorial, así como unas breves instrucciones
   para que configuremos nuestro equipo de manera adecuada y podamos utilizar el
   material disponible sin problema alguno.

3. Clonemos o "forkeemos" (no hace falta que lo compruebes, ambos sabemos que
   esa aberración no va a estar registrada en el diccionario, pero si utilizas
   _git_ me habrás entendido) el propio repositorio. Si no tienes cuenta en
   _GitHub_ o, directamente, no estás entiendo nada de lo que llevo escrito en
   este punto, sitúate en la parte superior derecha de la página asociada al
   repositorio, haz clic sobre el botón `Clone or download` y pulsa sobre el
   enlace `Download ZIP`. Descargarás un archivo comprimido que contiene todo el
   material de este repositorio, de forma que podrás descomprimirlo en tu unidad
   de disco duro donde desees y trabajar desde dicha localización.

4. Iniciemos _Jupyter Notebook_ y naveguemos por los directorios hasta alcanzar
   la ruta donde hayamos almacenado los materiales del repositorio. Si no
   dispones de esta aplicación en tu ordenador, una manera fácil de hacerte con
   ella, y a la vez con los módulos que se utilizarán a lo largo del tutorial,
   es descargar la distribución de _Python_
   [Anaconda](https://www.anaconda.com/download/) asociada a la versión 3.6 del
   mencionado lenguaje de programación. Por otro lado, si es la primera vez que
   escuchas hablar de _notebooks_ (en _R_ y _Python_ son muy populares hoy en
   día), te aconsejaría que previamente leyeses algún tutorial asociado a esta
   herramienta.
   [Este](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook#gs.uBagi2Q)
   es más que recomendable.

5. En la raíz del repositorio figura el _notebook_ `check_env.ipynb`. Abrámoslo
   y ejecutemos la única celda que lo compone, que es un bloque de código que
   comprueba si nuestro sistema cumple los requisitos necesarios para seguir sin
   problemas el tutorial. En el caso de que alguna de las líneas de la salida
   asociadas a los diversos módulos no esté precedida por un `[OK]`, tendremos
   que actualizar manualmente la versión del paquete correspondiente.

6. Opcionalmente, podemos descargar los conjuntos de datos asociados al tutorial
   (acción recomendable si en algunos momentos vamos a depender de redes wifi
   para trabajar con el material) sin más que teclear `python fetch_data.py`.

## Notebooks

En mi opinión, si tenemos un mínimo conocimiento de _Python_ y _Machine
Learning_, una buena manera de abordar el tutorial en sí consistiría en llevar a
cabo una lectura previa del _notebook_ que nos interese (experimentación con el
código incluida), para luego visualizar la parte de la grabación del tutorial
donde se desarrolla ese contenido en particular. Finalmente, con la explicación
todavía fresca en nuestras cabezas, podríamos reforzar el contenido leyendo de
nuevo el _notebook_ concreto. No obstante, si no cumples el primer requisito
comentado, directamente te aconsejaría empezar con la grabación e ir revisando
posteriormente cada _notebook_ a medida que se vayan abordando durante el vídeo.

A poco que eches un vistazo por encima al material disponible, comprobarás que
hay una cantidad más que considerable. Tanto que fue imposible abarcar los 23
_notebooks_ durante las dos sesiones que se llevaron a cabo y, en algunos casos,
ciertos temas fueron expuestos de manera bastante tangencial. Es por ello que
vuelvo a recomendar no limitarse únicamente a disfrutar de la grabación, sino
invertir también cierto tiempo en la lectura de los cuadernos, así como en la
experimentación con ellos (realización de ejercicios incluida).

Sin más preámbulos, a continuación, podemos acceder al listado completo de los
_notebooks_ disponibles, junto con sus respectivos enlaces tanto a _GitHub_ como
al instante en el que comienza su desarrollo en el vídeo de _YouTube_:

1. "Introduction to machine learning with sample applications, Supervised and
   Unsupervised learning".
   [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/01.Introduction_to_Machine_Learning.ipynb).
   [Youtube](https://youtu.be/2kT6QOVSgSg?t=2m11s).

2. "Scientific Computing Tools for Python: NumPy, SciPy, and matplotlib".
   [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/02.Scientific_Computing_Tools_in_Python.ipynb).
   [YouTube](https://youtu.be/2kT6QOVSgSg?t=20m40s).

3. "Data formats, preparation, and representation".
   [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/03.Data_Representation_for_Machine_Learning.ipynb).
   [YouTube](https://youtu.be/2kT6QOVSgSg?t=27m11s).

4. "Supervised learning: Training and test data".
   [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/04.Training_and_Testing_Data.ipynb).
   [YouTube](https://youtu.be/2kT6QOVSgSg?t=46m55s).

5. "Supervised learning: Estimators for classification".
   [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/05.Supervised_Learning-Classification.ipynb).
   [YouTube](https://youtu.be/2kT6QOVSgSg?t=1h6m52s).

6. "Supervised learning: Estimators for regression analysis".
   [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/06.Supervised_Learning-Regression.ipynb).
   [YouTube](https://youtu.be/2kT6QOVSgSg?t=1h37m43s).

7. "Unsupervised learning: Unsupervised Transformers".
   [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/07.Unsupervised_Learning-Transformations_and_Dimensionality_Reduction.ipynb).
   [YouTube](https://youtu.be/2kT6QOVSgSg?t=1h52m51s).

8. "Unsupervised learning: Clustering".
   [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/08.Unsupervised_Learning-Clustering.ipynb).
   [YouTube](https://youtu.be/2kT6QOVSgSg?t=2h20m25s).

9. "The scikit-learn estimator interface".
   [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/09.Review_of_Scikit-learn_API.ipynb).
   [YouTube](https://youtu.be/2kT6QOVSgSg?t=2h41m6s).

10. "Preparing a real-world dataset (titanic)".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/10.Case_Study-Titanic_Survival.ipynb).
    [YouTube](https://youtu.be/2kT6QOVSgSg?t=2h46m2s).

11. "Working with text data via the bag-of-words model".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/11.Text_Feature_Extraction.ipynb).
    [YouTube](https://youtu.be/WLYzSas511I?t=25s).

12. "Case Study - Text classification for SMS spam detection".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/12.Case_Study-SMS_Spam_Detection.ipynb).
    [YouTube](https://youtu.be/WLYzSas511I?t=19m47s).

13. "Cross-Validation".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/13.Cross_Validation.ipynb).
    [YouTube](https://youtu.be/WLYzSas511I?t=37m9s).

14. "Model complexity and grid search for adjusting hyperparameters".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/14.Model_Complexity_and_GridSearchCV.ipynb).
    [YouTube](https://youtu.be/WLYzSas511I?t=52m6s).

15. "Scikit-learn Pipelines".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/15.Pipelining_Estimators.ipynb).
    Debido a la falta de tiempo disponible, este _notebook_ tuvo que ser
    excluido de la sesión.

16. "Supervised learning: Performance metrics for classification".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/16.Performance_metrics_and_Model_Evaluation.ipynb).
    [YouTube](https://youtu.be/WLYzSas511I?t=1h14m58s).

17. "Supervised learning: Linear Models".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/17.In_Depth-Linear_Models.ipynb).
    [YouTube](https://youtu.be/WLYzSas511I?t=1h32m36s).

18. "Supervised learning: Decision trees and random forests, and ensemble
    methods".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/18.In_Depth-Trees_and_Forests.ipynb).
    [YouTube](https://youtu.be/WLYzSas511I?t=2h39s).

19. "Supervised learning: feature selection".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/19.Feature_Selection.ipynb).
    Por falta de tiempo, se excluyó de la sesión.

20. "Unsupervised learning: Hierarchical and density-based clustering
    algorithms".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/20.Unsupervised_learning-Hierarchical_and_density-based_clustering_algorithms.ipynb).
    [YouTube](https://youtu.be/WLYzSas511I?t=2h56m6s).

21. "Unsupervised learning: Non-linear dimensionality reduction".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/21.Unsupervised_learning-Non-linear_dimensionality_reduction.ipynb).
    Debido a la falta de tiempo disponible, este _notebook_ tuvo que ser
    excluido de la sesión.

22. "Unsupervised learning: Anomaly Detection".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/22.Unsupervised_learning-anomaly_detection.ipynb).
    [YouTube](https://youtu.be/WLYzSas511I?t=2h21m38s).

23. "Supervised learning: Out-of-core learning".
    [GitHub](https://github.com/amueller/scipy-2017-sklearn/blob/master/notebooks/23.Out-of-core_Learning_Large_Scale_Text_Classification.ipynb).
    Debido a la falta de tiempo disponible, este _notebook_ tuvo que ser
    excluido de la sesión.

## Enlaces de utilidad asociados al tutorial

Recojo, a continuación, algunos enlaces, que han surgido a lo largo del
artículo, relacionados con el tutorial:

- [Machine Learning with scikit learn Part One - SciPy 2017 Tutorial - Andreas Mueller & Alexandre Gram](https://youtu.be/2kT6QOVSgSg).
- [Machine Learning with scikit learn Part Two - SciPy 2017 Tutorial - Andreas Mueller & Alexandre Gram](https://youtu.be/WLYzSas511I).
- [Repositorio](https://github.com/amueller/scipy-2017-sklearn) en _GitHub_
  asociado al tutorial.
- [Anaconda](https://www.anaconda.com/download/).
- [Jupyter Notebook Tutorial: The Definitive Guide](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook#gs.y34eIOY).
