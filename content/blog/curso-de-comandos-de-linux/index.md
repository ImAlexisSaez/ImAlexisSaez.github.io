---
title: Curso de comandos de Linux
summary: En este curso aprenderemos a utilizar la terminal de *Linux* empezando desde los comandos más básicos y con el objetivo de emplear esta herramienta de una forma eficiente para realizar las operaciones cotidianas.
date: 2023-06-05
lastmod: 2026-06-05
image:
  caption: Imagen generada por Leonardo.Ai
authors:
  - me
categories:
  - Programación
tags:
  - Linux
  - Terminal
  - The Odin Project
status: published
---
### 1. Introducción

Esta semana he estado echando un vistazo a la plataforma
[The Odin Project](https://www.theodinproject.com/) y más concretamente a su
curso de fundamentos,
[Foundations](https://www.theodinproject.com/paths/foundations/courses/foundations).
Este es el punto de partida común que comparten las dos especializaciones de
desarrollo web ofrecidas en este sitio: una basada en **Ruby** y otra en
**JavaScript**.

Su primera sección, ''Introduction'', es ciertamente interesante, pues trata
temas tan variados como el aprendizaje en sí, la gestión de la frustración o la
manera de realizar preguntas adecuadamente para obtener ayuda útil. Es un
aspecto que la mayoría de los cursos no aborda y los recursos que ofrece esta
plataforma son muy interesantes.

Completada dicha sección, la siguiente lleva por título ''Prerequisites'' y se
centra en el funcionamiento básico de los ordenadores y de Internet. Además, es
donde empezamos a configurar nuestro entorno de desarrollo para trabajar a lo
largo de este curso. Como no podía ser de otra manera, sin ni tan siquiera haber
generado un solo fichero, ya comienzan a aparecer los retos (que, por otra
parte, bienvenidos sean tras las conclusiones que se extraen de las charlas que
figuran en la sección ''Introduction''):

- **The Odin Project** no da soporte oficial para Windows. ¿Qué sistema
  operativo utiliza un servidor? Efectivamente, Windows. No obstante, la
  plataforma no nos deja de lado y ofrece alternativas muy bien detalladas para
  seguir los contenidos de la especialización. A la hora de escribir estas
  líneas, estoy probando la emulación de una distribución de Linux, **Xubuntu**,
  a través de **Oracle VM VirtualBox** (he tenido hasta que trastear la BIOS
  para permitir la emulación en mi ordenador).
- La propia plataforma nos aconseja no caer en ''rabbit holes'' que nos
  distraigan y centrarnos en seguir sus contenidos. La misma plataforma, casi en
  cada uno de sus apartados, nos enseña docenas de tentadores ''rabbit holes''
  en los que perdernos.

De hecho, esta serie de artículos para el blog son fruto de haber caído en uno
de ellos, pues una vez instalado Xubuntu recomiendan aprender los principales
comandos que se emplean en su terminal. Para ello enlazan a una lista de
reproducción en YouTube de 24 vídeos del canal
[LearnLinuxTV](https://www.youtube.com/channel/UCxQKHvKbmSzGMvUrVtJYnUA).

A continuación, comparto las notas tomadas durante el cuarto vídeo, que
corresponde al primero del curso en el cual se empieza a utilizar la terminal.

### 2. Navegando por el sistema de ficheros

Para empezar, el comando `ls` muestra el contenido del directorio actual de
trabajo (`ls` es la abreviatura de ''list storage''). Así, al iniciar una nueva
terminal, accederíamos con él a los contenidos de la carpeta del usuario.

Si tecleamos `ls /` accedemos a los contenidos almacenados en la raíz del
sistema (`/`). Asimismo, con `ls /home` se muestran las carpetas habilitadas
para los distintos usuarios del sistema. En mi caso, tras la instalación de
Xubuntu siguiendo las instrucciones de la plataforma, únicamente aparece la
carpeta `alexis`.

Por comodidad, para limpiar la terminal y dejar de mostrar la información
acumulada hasta el momento, podemos emplear el comando `clear` o, en ocasiones,
dependiendo de la distribución de Linux que tengamos en nuestro sistema, la
combinación de teclas `Ctrl + L`.

Por otra parte, podemos añadir atributos a un comando de la terminal. Por
ejemplo, si tecleamos `ls -l /` obtendremos mucha más información que antes de
cada una de las carpetas y de los ficheros ubicados en la raíz del sistema (el
atributo `-l` indica ''long listing''). Además, cada carpeta o fichero aparece
en su propia línea. Al inicio de cada una de las mencionadas líneas aparece una
extraña secuencia de caracteres que, en su mayor parte, recoge los permisos
asociados a la correspondiente carpeta o archivo. De momento, si nos centramos
únicamente en el primer carácter:

- `d`: indica directorio o carpeta.
- `-`: indica que es un archivo.
- `l`: indica un enlace a otro archivo.

Una alternativa a la combinación `ls -l` es el comando `ll`.

En la raíz del sistema encontramos algunos directorios de vital importancia.
Aunque de momento no entraremos en profundidad en los detalles de cada uno de
ellos, para hacernos una idea resulta que:

- `bin`: es el directorio que contiene los programas ejecutables del sistema.
- `boot`: es el directorio que contiene los archivos necesarios para iniciar el
  sistema operativo.
- `home`: es el directorio asociado a los usuarios del sistema.
- `etc`: es el directorio que contiene los archivos de configuración del
  sistema.
- `media`: es el directorio donde se montan dispositivos externos (usb,
  cd-rom...).
- `var`: es el directorio que contiene ''logs'' del sistema.

La terminal de algunas distribuciones de Linux emplea un código de colores para
diferenciar los distintos tipos de elementos almacenados. Así, el color azul
suele indicar carpetas; el blanco, archivos; y el verde, archivos binarios.

Para cambiar de directorio y navegar por el sistema de archivos utilizamos el
comando `cd`, que es la abreviatura de ''change directory''. Por ejemplo, `cd /`
nos lleva a la raíz del sistema y combinando los comandos `cd` y `ls` es como
habitualmente nos desplazaremos por el interior del sistema de archivos. En
cualquier momento podemos acceder a la ruta del directorio actual de trabajo en
el que nos encontramos sin más que teclear `pwd`, que es la abreviatura de
''print working directory''.

La tilde o virgulilla, `~`, actúa como atajo hacia la carpeta del usuario. Así,
con `cd ~` acudimos directamente a nuestra carpeta de usuario.

### 3. Edición básica de archivos

Para empezar, creamos un archivo mediante el comando `touch`, al que pasamos
como argumento el nombre deseado para el mencionado archivo. Por ejemplo, para
generar un fichero denominado `testfile.txt` tecleamos `touch testfile.txt`.

Acto seguido, si escribimos `ls -l`, observamos que un nuevo archivo aparece en
el listado, cuyo tamaño es `0`.

Ahora, para acceder al contenido de un archivo, empleamos el comando `cat`. Por
ejemplo, en el caso del fichero que acabamos de generar, teclearíamos
`cat testfile.txt`, aunque, al estar vacío, la terminal no arroja información
alguna cuando ejecutamos el anterior comando. Por otro lado, si tecleamos de
nuevo `touch testfile.txt`, se actualizará la fecha de creación del fichero.

Cambiando de tercio, podemos editar archivos empleando el comando `nano`, que
nos da acceso a un editor de texto plano. Si lo iniciamos de esta manera, no
estaremos modificando ningún archivo (basta observar que en la parte superior
aparece `New Buffer`).

En la parte inferior de la aplicación figura el menú con todas sus opciones. El
símbolo `^`, que aparece en todas ellas, ha de ser interpretado como el uso de
la tecla `Ctrl`. Así, el atajo `^X`, para salir del programa, ha de ser
ejecutado mediante la combinación `Ctrl + X`. Asimismo, para guardar (o salvar)
un archivo tras escribir cierto texto, el atajo es `^O`, que equivale a la
combinación `Ctrl + O`.

Si cerramos el editor de texto y ejecutamos `ls -l`, observaremos que aparece el
nuevo archivo y este, a diferencia del anterior, posee cierto tamaño y podemos
revisar sus contenidos mediante el comando `cat`.

Al comando `nano` le podemos añadir un atributo con el nombre del fichero que
queremos editar. Por ejemplo, `nano test3.txt`. Este archivo no existía en el
directorio actual, de manera que cuando salvemos lo creará con los contenidos
que hayamos escrito. Siguiendo esta lógica, podríamos editar el archivo
`testfile.txt` que generamos al principio de la sección tecleando
`nano testfile.txt`.

La terminal posee autocompletado a través de la tecla `Tab`. Así, escribiendo el
principio del nombre de un archivo o directorio y pulsando dicha tecla, se
autocompleta la línea.

Con el comando `which` podemos saber si una instrucción está disponible para su
uso en la terminal. Por ejemplo, `which nano` nos devuelve la ruta hacia el
ejecutable, mientras que `which prueba` no muestra salida, es decir, no existe
ningún comando o aplicación en mi sistema con el nombre `prueba`.

### 4. Una breve mirada a Vim

Un editor de texto plano muy completo es **Vim** y, por tanto, es recomendable
aprender su uso. Quizá no a corto plazo, dada su elevada curva de aprendizaje;
pero por sus muchos beneficios merece la pena invertir un tiempo a medio plazo
para dominar esta aplicación si continuamos por la senda de la programación.

En mi caso particular, al teclear en la terminal `which vim`, esta no arroja
respuesta alguna. Es decir, la mencionada aplicación no está instalada en mi
sistema. Para solventar esta situación, basta teclear:

```bash
sudo apt install vim-nox
```

Vim, como ya hemos mencionado, es un editor de texto plano más avanzado que
`nano`, por lo que su uso es más complejo. Para empezar, salir de la propia
aplicación no es nada intuitivo y lo haremos tecleando `:q` en el modo
''command''.

Así pues, ya apreciamos que existen diversos modos o estados en Vim. Por
ejemplo, pulsando la tecla `i` activamos el modo ''insert'' (mediante el cual
podemos editar un archivo de la manera habitual) y con la tecla `Esc`
retrocederíamos de nuevo al modo ''command''. En este último modo, no podemos
escribir como habitualmente estamos acostumbrados, sino que es el modo que
empleamos en Vim para introducir instrucciones o comandos al programa.

De esta forma, para salvar el archivo que hemos escrito a través del modo
''insert'', volvemos al modo ''command'' y escribimos `:w` (si pulsamos intro a
continuación, recibiremos un error por no asignar un nombre al archivo). Así,
tecleamos `:w test4.txt`. Al igual que sucedía con `nano`, podemos lanzar Vim
con el nombre de un archivo como atributo, de manera que abrirá dicho fichero al
iniciarse.

El atajo `shift + I` es muy útil, pues activa el modo ''insert'' y coloca el
cursor al final del archivo.

Si usamos `vim test4.txt` y añadimos texto, bastará en el modo ''command''
teclear para `:w` para guardar el archivo (pues ya posee nombre asignado).

Para borrar una línea por completo, podemos emplear el atajo que consiste en
pulsar `d` dos veces en el modo ''command''.

### 5. Moviendo y renombrando archivos

Para empezar, de cara a copiar un archivo usamos el comando `cp`, que posee dos
argumentos: el archivo a copiar y el nombre del nuevo archivo donde será
copiado. Por ejemplo:

```bash
cp test2.txt newfile.txt
```

Ahora, con el comando `cat` podemos comprobar que el contenido de ambos archivos
es exactamente el mismo. No obstante, existe otro comando más apropiado para
llevar a cabo esta tarea de comparación: `diff`, que nos indica en qué difieren
dos archivos. Así,

```bash
diff newfile.text test2.txt
```

No arroja salida alguna, es decir, no hay ninguna diferencia entre ambos
archivos. Sin embargo,

```bash
diff newfile.text test3.txt
```

Sí arroja resultados, pues son ficheros cuyos contenidos difieren.

Por otra parte, de cara a borrar un archivo, el comando a usar es `rm`. Por
ejemplo

```bash
rm newfile.txt
```

Este comando también elimina directorios (con el atributo `-r` que activa la
recursión), por lo que hemos de ser cautos cuando lo empleamos. Esta instrucción
no mueve el archivo a una suerte de ''Papelera de reciclaje'' como en Windows,
sino que lo elimina por completo del sistema. Si después lo queremos recuperar
tendríamos que usar herramientas específicas de recuperación de archivos en
memoria.

A continuación, antes de aprender a mover archivos, creemos un nuevo directorio,
con el comando `mkdir` para almacenarlos. Por ejemplo

```bash
mkdir linux-notes
```

Ahora, para mover los archivos, el comando a emplear es `mv` cuyo primer
argumento será el nombre del archivo a mover y el segundo su destino.

Podemos emplear ''comodines'' en las instrucciones de la terminal para algunos
comandos. Por ejemplo, `*.txt` se traduce en todos los archivos cuya extensión
sea `.txt`. De esta manera, podemos mover en bloque todos los ficheros de prueba
que hemos creado hasta el momento.

```bash
mv *.txt linux-notes
```

Recordemos que con el comando `cd` cambiamos el directorio y si tecleamos
`cd ..` volvemos un paso atrás en la ruta (o a un nivel inferior). Así,
siguiendo la misma lógica, si queremos mover un paso atrás en la ruta alguno de
los archivos, basta escribir

```bash
cd linux-notes
mv testfile.txt ..
cd ..
ls -l
```

Además, hemos de tener en cuenta que si `..` indica un nivel inferior, `.`
indica el nivel actual (el directorio de trabajo). Esto nos permite usar el
comando `mv` para mover archivos hacia la actual ruta donde nos encontremos. Por
ejemplo, para traer de vuelta el archivo `testfile.txt` al directorio
`linux-notes`, bastaría teclear:

```bash
cd linux-notes
md ../testfile.txt .
ls -l
```

Finalmente, de cara a renombrar archivos, empleamos el mismo comando que para
moverlos. Por ejemplo

```bash
mv test3.txt abc.txt
ls -l
```

Con este comando también hemos de ser cautos para no renombrar un archivo con el
nombre de un fichero existente, pues podemos sobrescribirlo. En algunas
distribuciones de Linux esto sucede directamente (Xubuntu es un ejemplo de esta
forma de proceder) y en otras pregunta si deseamos realizar dicha acción.

### 6. Configurando la terminal

En esta sección nos adentraremos en la configuración de la terminal (Bash por
defecto en la mayoría de las distribuciones de Linux). Para ello, hemos de ser
conscientes de la existencia de archivos escondidos (''hidden files'') en
nuestro sistema operativo, que no se muestran por defecto al listar los
contenidos de un directorio mediante el comando `ls`.

Para que dicho listado incluya los mencionados ficheros escondidos, tecleamos
`ls -a`. Los archivos que aparecen con un punto delante de su nombre son los
ficheros escondidos a los que hacíamos referencia antes y que no se listan por
defecto al emplear el comando `ls` sin atributos.

Podemos encadenar atributos en un comando de una manera bastante cómoda. Por
ejemplo, teclear `ls -la` tiene el efecto de añadir los atributos `-l` y `-a` al
comando `ls`.

Así pues, si ejecutamos `ls -la` en la carpeta `/home` y observamos el principio
de largo listado que aparece, nos daremos cuenta de la existencia de un archivo
denominado `.bashrc`. Utilizando `nano .bashrc` podemos acceder a su contenido.
Las líneas que comienzan con el símbolo `#` son comentarios. Por otra parte,
hemos de llevar cuidado de realizar modificaciones en este archivo y luego
sobrescribir, pues las consecuencias pueden distar de ser deseables.

En caso de realizar alguna modificación con catastróficas consecuencias, podemos
recuperar una especie de configuración por defecto en `/etc/skel/.bashrc`. La
carpeta `skel` `contiene ciertos ficheros de configuración por defecto para
asignarlos cuando creamos un nuevo usuario en el sistema. Por otro lado, si en
Google buscamos ''Xubuntu .bashrc'', el primer resultado contiene las líneas de
la configuración por defecto de la terminal en Xubuntu.

En esta lección únicamente nos vamos a limitar a crear un ''alias''. Para ello,
añadimos al archivo la línea:

```bash
alias c=clear
```

Guardamos el fichero (con `Ctrl + O`, como indica en el menú inferior) y ahora,
en la terminal, no es necesario escribir `clear` para limpiar la pantalla. Basta
con teclear `c` y pulsar intro.

En mi caso, ha sido necesario reiniciar la terminal para que el cambio tuviera
efecto.

Así, al abrir la terminal, esta accede al archivo de su configuración y tiene en
cuenta las instrucciones allí declaradas. Si en un futuro hemos de realizar
modificaciones al comportamiento de esta herramienta, seguramente lo hagamos a
través de este archivo de configuración.

### 7. El archivo `.bashrc` original

Como temo que fruto de experimentar con este archivo surja alguna consecuencia
desastrosa, dejo a continuación una copia del contenido original del mismo.

```bash
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
 # We have color support; assume it's compliant with Ecma-48
 # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
 # a case would tend to support setf rather than setaf.)
 color_prompt=yes
    else
 color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
```

### 8. Abordando el uso de alias

Al final de la sección anterior, incluimos un ''alias'' en el archivo de
configuración de la terminal que nos permite limpiar esta tecleando únicamente
`c`.

Así pues, un ''alias'' nos ofrece la posibilidad de crear nuevos comandos a
partir de los ya existentes. En la mayoría de los casos se busca automatizar
tareas cotidianas de una manera más corta o incluir ciertos atributos por
defecto cuando tecleamos la versión sin atributos de un determinado comando.

Para tener acceso a un listado de los ''alias'' disponibles en nuestra terminal,
basta teclear en ella `alias`. En ella podemos apreciar que uno de los comandos
que examinamos en lecciones anteriores, `ll`, no es más que un ''alias'' del
comando `ls`, al que añade los atributos `-alF`. De hecho, el propio comando
`ls` es un ''alias'' de sí mismo configurando cierta opción para colorear.

En mi caso, el anterior listado es reducido, ya que apenas cuenta con diez
líneas. Sin embargo, es posible acceder a la definición concreta de un
''alias'', como el generado para la tecla `c`, escribiendo `alias c`. La
terminal devuelve `alias c='clear'`. A medida que incorporemos más y más
''alias'', puede resultar conveniente acceder a la definición concreta de uno de
ellos para disponer de todos sus detalles.

Si en algún momento precisamos eliminar un ''alias'', simplemente hemos de
utilizar el comando `unalias` declarando como argumento el atajo
correspondiente. Por ejemplo, `unalias c` desactivaría la posibilidad de limpiar
la pantalla de la terminar utilizando únicamente la tecla `c`. No obstante, como
dicho ''alias'' está incluido en el archivo de configuración de la terminal,
cuando iniciemos una nueva sesión de esta, volverá a estar disponible el
''alias'' asignado a la tecla `c`. Para eliminarlo por completo, deberíamos
editar el mencionado archivo de configuración y suprimir la línea
correspondiente a la definición de dicho ''alias''.

Cambiando de tercio, es posible que nos resulte útil conocer los cinco procesos
que más uso están haciendo de la CPU. El comando asociado a ello es un tanto
complejo:

```bash
ps auxf | sort -nr -k 3 | head -5
```

De esta forma, si este es un dato que queremos consultar con cierta frecuencia,
tiene sentido definir un ''alias'' para el mismo:

```bash
alias cp5='ps auxf | sort -nr -k 3 | head -5'
```

En realidad, el anterior ''alias'' no es un comando, sino una composición de
comandos. Como podemos apreciar, usa el símbolo `|` para redirigir los
resultados de un comando hacia el argumento de entrada para otro. En el ejemplo
anterior, se ejecuta el comando `ps` con ciertos atributos, la salida del cual
se envía al comando `sort` y esta al comando `head` para producir el resultado
final que se muestra en la terminal.

Así, para conocer el mismo dato, pero asociado al uso de la memoria, podemos
definir un ''alias'' que es ciertamente similar al anterior:

```bash
alias mem5 = 'ps auxf | sort -nr -k 4 | head -5'
```

Finalmente, algunos ''alias'' recomendados son

```bash
alias h='history'
alias install='sudo apt install'
```

Aunque, como hemos visto arriba, si nos encontramos en una situación donde
habitualmente escribimos largos comandos o encadenamos siempre la misma
secuencia de comandos, es recomendable definir un ''alias'' que nos ahorre
tiempo.

### 9. Introducción a los permisos en Linux

Para empezar, la manera en que Linux gestiona los permisos es un tanto diferente
a la que lleva a cabo Windows. Por ejemplo, al teclear `ls -l` en la terminal,
dentro de la carpeta de usuario (`cd ~` para acceder a ella si estamos ubicados
en un directorio de trabajo distinto), para la carpeta `Desktop` la línea
comienza con la secuencia:

```bash
drwxr-xr-x
```

El primer carácter, `d`, recordemos, indica que es un directorio. (`-` para
archivos). El resto de los caracteres de la secuencia nos indica lo que podemos
hacer (o no) con el directorio o archivo en cuestión. Para interpretar dicha
secuencia de caracteres, hemos de dividirla en cuatro secciones:

- Sección 1: el primer carácter, que sabemos indica el tipo de elemento del que
  se trata (archivo, directorio o enlace).
- Sección 2: los siguientes tres caracteres, que hacen referencia a los permisos
  del usuario al que pertenece el archivo o directorio. Dicho usuario aparece en
  la tercera columna del listado que genera el comando `ls -l`.
- Sección 3: los siguientes tres caracteres, que hacen referencia a los permisos
  del grupo al cual pertenece el archivo o directorio. Dicho grupo aparece en la
  cuarta columna del listado que genera el comando `ls -l`.
- Sección 4: los siguientes tres caracteres, que hacen referencia a los permisos
  del resto de usuarios que ni son propietarios ni pertenecen al grupo en
  cuestión (se denomina ''world'' en ocasiones a los usuarios a los que afecta
  esta sección).

En cada una de las posiciones de las secciones 2, 3 y 4 encontramos una letra de
la secuencia `rwx` o bien un guion, `-`, que indica que el correspondiente
permiso no está disponible. El orden siempre es `rwx` en dichas secciones, por
lo que una subsecuencia como `r-x` indica la ausencia del permiso `w` para ese
elemento en concreto en la sección asociada.

Ahora bien, ¿qué significa cada una de las letras?

- `r` es para ''read'', esto es, es la letra asociada al permiso de lectura.
- `w` es para ''write'', esto es, es la letra asociada al permiso de escritura o
  edición (incluso nos permitiría eliminar el elemento en concreto).
- `x` es para ''execute'', esto es, es la letra asociada al permiso de
  ejecución. Está reservada para aquellos elementos en los que podemos insertar
  comandos y ejecutarlos como si fueran programas.

Para editar permisos en un elemento, empleamos el comando `chmod`. Por ejemplo,
si deseamos añadir el permiso de ejecución a un archivo denominado `test.txt`,
escribiríamos:

```bash
chmod +x test.txt
```

Al volver a ejecutar `ls -l` observamos que el permiso `x` está disponible para
el usuario, para el grupo y para el resto. Además, la terminal cambia su color a
verde, para indicar que ahora es un archivo ejecutable.

Para devolver los permisos a su estado inicial, basta teclear:

```bash
chmod -x test.txt
```

Además, como cabría esperar, podemos configurar el permiso `x` de manera que
afecte solo a una sección. Por ejemplo, para asignar únicamente al propietario
del archivo el permiso `x` hemos de escribir:

```bash
chmod u+x test.txt
```

Para habilitar todos los permisos en un elemento a cualquier usuario, hemos de
teclear `chmod a+rwx`. Por ejemplo:

```bash
chmod a+rwx test.txt
```

No es una práctica recomendable para directorios o archivos que contengan
información sensible.

Por otro lado, la letra correspondiente para el grupo es `g`, de manera que si
deseo retirar todos los permisos al grupo tendría que teclear:

```bash
chmod g-rwx test.txt
```

Esta configuración tiene poco sentido, pues todo el mundo tiene los permisos
`rwx`.

Finalmente, para hacer referencia al resto de usuarios que ni son propietarios,
ni pertenecen al grupo, la letra es `o`. Así, para retirarlos los permisos `rwx`
teclearíamos:

```bash
chmod o-rwx test.txt
```

Acto seguido, devolvamos los permisos a su estado original:

```bash
chmod u-x test.txt
chmod g+rw test.txt
chmod o+r test.txt
```

Cambiando de tercio, los permisos se gestionan de manera diferente si se trata
de archivos o de directorios. En el caso de los directorios:

- `r` nos permite visualizar su contenido.
- `w` nos permite editar o modificar el directorio.
- `x` nos permite acceder a su interior.

### 10. Examinando el uso de recursos del sistema

En esta sección abordaremos la gestión de recursos del sistema como, por
ejemplo, uso de memoria, uso de espacio en disco, etc. El primer comando que
analizaremos es `free`. Este nos ofrece información relevante sobre el uso de
memoria del sistema. No obstante, por defecto, la ofrece en ''bytes'',
comportamiento que podemos modificar haciendo uso del atributo `-m`:

```bash
free -m
```

En mi caso, al estar la distribución de Xubuntu virtualizada, los datos
corresponden a los declarados en la configuración de la máquina virtual y no a
los correspondientes al ordenador en sí.

Por otro lado, ¿cuál es la diferencia entre las columnas ''free'' y
''available''? El dato que aparece en la columna ''free'' está verdaderamente
libre de uso, mientras que ''available'' tiene en cuenta que algunas
aplicaciones reservan parte de la memoria para su uso y puede que actualmente no
estén haciendo uso de dicha reserva. Por ello este dato es más elevado, aunque,
según las necesidades de las aplicaciones, es bastante variable.

A continuación, para analizar el espacio en disco usado, empleamos el comando
`df` (abreviatura de ''disk free''). Para una lectura más cómoda de los números
que aparecen en su salida, conviene agregar el atributo `-h`, que transforma las
cantidades a ''megabytes'' o ''gigabytes'' según convenga.

A modo anecdótico, el espacio en disco puede agotarse:

- Cuando almacenamos demasiados elementos cuyo tamaño es considerable
  (películas, videojuegos...).
- Cuando almacenamos demasiados elementos, aunque su tamaño sea reducido. Cada
  distribución tiene un límite a este respecto y viene dado por el concepto de
  **Inodes**. Para acceder al listado de ''Inodes'' disponibles, basta teclear
  `df -i`.

Acto seguido, otro comando de gran utilidad es `htop`, que, en mi caso, no viene
instalado por defecto en Xubuntu. Así pues, para solventar esta situación:

```bash
sudo apt install htop
htop
```

A primera vista, nos recuerda al administrador de tareas de Windows y nos ofrece
una cantidad enorme de información acerca de los recursos del sistema. Aún
siendo una herramienta que se ofrece en la línea de comandos, podemos emplear el
ratón para movernos por los diferentes menús disponibles.

Desde esta herramienta podemos cerrar procesos haciendo uso de la combinación
`F9 + 15 SIGTERM` o, de haber quedado la aplicación totalmente congelada, con
`F9 + 9 SIGKILL`. Para cerrar, hacemos clic sobre la opción correspondiente o
simplemente pulsamos `F10`.

Finalmente, otro comando útil es `uptime`, que indica cuánto tiempo lleva en
marcha la sesión actual y la carga media. Estos tres últimos valores no han de
ser interpretados como porcentajes, pues los ordenadores de hoy en día poseen
varios núcleos (un `0.12` no equivale pues a un 12% de carga, a no ser que
nuestra máquina tenga un único núcleo). Además,

- El primer valor hace referencia a la carga media durante el último minuto.
- El segundo valor es con respecto a los últimos cinco minutos.
- El tercer valor es con respecto a los últimos quince minutos.

Los valores hemos de interpretarlos como tareas a la espera de ser ejecutadas
por el sistema. Por ejemplo, `0,12` indica que, de media, menos de una tarea
está en espera de ser ejecutada; es decir, el sistema está trabajando de manera
bastante desahogada.

En otras palabras, y utilizando como analogía un supermercado, el número de
núcleos del ordenador haría las veces de cajeros, mientras que las tareas serían
los clientes a la espera de pagar sus compras. Si tenemos 2 núcleos y hay un
cliente, el sistema funcionará bien e incluso habrá un cajero que se estará
aburriendo en ese momento determinado. Con dos clientes todavía no encontramos
problema, pues cada cajero está atendiendo su tarea asociada. El problema es
cuando el número de clientes asciende, por ejemplo, a 20, pues los dos cajeros
no dan abasto y las colas serán largas. En este último caso, algunas de las
tareas del sistema tardarán en poder llevarse a cabo.

### 11. Gestionando los paquetes

En esta sección abordaremos la instalación, eliminación y actualización de
paquetes en nuestro sistema.

Los métodos que se describen a continuación están diseñados para distribuciones
basadas en **Debian** o **Ubuntu**.

El primer paso a llevar a cabo es la actualización de nuestro índice local de
paquetes disponibles en el repositorio, es decir, en el servidor online desde el
cual los descargaremos. Para ello, tecleamos:

```bash
sudo apt update
```

En mi caso concreto, la mayoría de servidores con los que conecta son de Ubuntu,
pero también observamos que aparece alguno de Google o de Microsoft.

A continuación, una vez actualizado el índice de paquetes, podemos buscar
paquetes concretos en él desde la propia línea de comandos:

```bash
apt search firefox
```

En esta ocasión no necesitamos anteceder el comando con `sudo`, pues no vamos a
realizar cambios en el sistema. Cuando queramos instalar un paquete, por
ejemplo, sí será necesario incluir ese comando en la sentencia.

El listado es bastante extenso en este ejemplo concreto, pues muestra todos los
paquetes relacionados con Firefox (desde idiomas a extensiones, pasando por el
propio navegador en sí).

Para instalar un paquete concreto, la instrucción es `sudo apt install` seguida
el nombre del paquete a instalar. Por ejemplo, para instalar el editor de texto
plano Vim escribimos:

```bash
sudo apt install vim-nox
```

Como ejemplo más práctico, instalemos a continuación
[Apache](https://ubuntu.com/server/docs/web-servers-apache), que es un servidor
web que utilizamos a diario:

```bash
apt search apache
```

```bash
sudo apt install apache2
```

A la hora de instalar este paquete, el comando `apt` se encarga de gestionar sus
dependencias, de manera que nos indica qué paquetes adicionales son necesarios
para realizar la instalación del que nos interesa. Como esta operación implica
llevar a cabo más cambios de los que indicamos desde la línea de comandos, la
instalación se detiene y espera a que el usuario confirme si realmente desea
instalar tanto el paquete indicado como sus correspondientes dependencias.

Además de las dependencias, `apt` recomienda la instalación de paquetes
adicionales por su utilidad, aunque no fuerza a su instalación y deberíamos
llevar a cabo el proceso después de manera manual.

Una vez instalado Apache, si escribimos en la barra de direcciones de Chrome (o
cualquier navegador), `localhost` nos aparecerá la página por defecto de Apache.

Por otro lado, para eliminar un paquete del sistema, la instrucción es
`sudo apt remove` seguida el nombre del paquete a eliminar. Por ejemplo:

```bash
sudo apt remove apache2
```

Por defecto, no elimina las dependencias asociadas a Apache. Para solventar la
situación tecleamos `sudo apt autoremove`.

Acto seguido, actualicemos los paquetes que tenemos instalados en nuestro
sistema. En mi caso, desde que iniciamos la lección, la terminal me ha indicado
cada vez que poseo 21 paquetes que no están actualizados. Para ello tecleamos

```bash
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
```

La última instrucción conviene ejecutarla cuando hayan quedado paquetes a
eliminar o haya algunos que deban instalarse por primera vez, pues
`sudo apt upgrade` no realiza estas labores por defecto.

Por cuestiones de seguridad, conviene actualizar los paquetes con frecuencia.

Finalmente, en el caso que se hayan realizado actualizaciones del ''kernel'',
conviene reiniciar el sistema, para lo cual escribimos `sudo reboot`.

### 12. Gestionando procesos en Linux

En esta sección abordaremos cómo gestionar procesos en Linux. Estudiaremos el
comando `systemctl`, que permite iniciar, detener y reiniciar servicios que se
ejecutan en segundo plano (que habitualmente reciben el nombre de ''units'').

Comencemos instalando de nuevo Apache, que nos servirá de base para los ejemplos
de esta lección:

```bash
sudo apt install apache2
```

Recordemos que si ahora abrimos el navegador y escribimos en la barra de
direcciones `localhost`, accederemos a la página por defecto de Apache. Esto es
posible debido a que se ejecuta en segundo plano, como podemos comprobar si
tecleamos en la terminal:

```bash
systemctl status apache2
```

Aparece `enabled` en la fila correspondiente a `Loaded:`, esto es, cuando
iniciemos el sistema, Apache automáticamente se iniciará. Además, es el
comportamiento que viene predefinido al instalar este paquete, pues así está
declarado en `vendor preset`, con un valor asimismo de `enabled`.

Estas características son las responsables de que una vez hayamos instalado el
paquete, hayamos podido acceder a la página por defecto de Apache en el
navegador sin tener que iniciar proceso alguno para ello.

En la línea encabezada por `Active:` observamos que está activo el proceso y en
funcionamiento, indicándonos desde cuándo.

Por otro lado, en la parte final deberíamos haber tenido acceso a cierta
información (''logs''), pero en mi distribución no aparece por defecto. Para
visualizar los ''logs'' hemos de anteceder el anterior comando con `sudo`:

```bash
sudo systemctl status apache2
```

Podemos desactivar Apache sin más que teclear:

```bash
sudo systemctl disable apache2
```

Sin embargo, si ahora ejecutamos `systemctl status apache2`, observamos que el
proceso sigue en funcionamiento (`active (running)`), pero en la línea
encabezada con `Loaded:` ahora aparece `disabled`, lo cual indica que la próxima
vez que iniciemos el sistema, Apache no se iniciará de manera automática.

Para detener el proceso, hemos de teclear:

```bash
sudo systemctl stop apache2
systemctl status apache2
```

Ahora podemos observar como en la línea encabezada por `Active:` figura
`inactive (dead)`. De hecho, si refrescamos la página del navegador aparece un
error en la misma.

A continuación, restauremos el comportamiento por defecto de Apache. Para
empezar, asegurémosnos que arranca automáticamente la próxima vez que iniciemos
el sistema. Para ello:

```bash
sudo systemctl enable apache2
systemctl status apache2
```

Así, comprobamos que vuelve a aparecer `enabled` en la línea encabezada por
`Loaded:`. Ahora, iniciamos el proceso sin más que teclear:

```bash
sudo systemctl start apache2
systemctl status apache2
```

De manera que todo vuelve a funcionar como al principio de la lección.

Finalmente, para reiniciar un proceso, hemos de escribir:

```bash
sudo systemctl restart apache2
systemctl status apache2
```

De forma que comprobamos que se ha reiniciado el proceso observando desde cuándo
está activo.

### 13. Revisando ''logs''

En esta sección abordaremos la gestión de ''logs'', a los que recurriremos
habitualmente para examinar la información que recopilen nuestras aplicaciones
(errores, acciones...).

A la hora de trabajar con ''logs'' es posible que necesitemos privilegios de
administrador (**root**) para revisar algunos de ellos, por lo que quizá nos
veamos forzados a emplear el comando `sudo`.

Empecemos revisando `syslog`, que contiene una enorme cantidad de información
que el sistema va almacenando en dicho archivo. Para ello, emplearemos el
comando `cat`:

```bash
sudo cat /var/log/syslog
```

¿Qué más ''logs'' tenemos a nuestra disposición?

```bash
cd /var/log/
ls -l
```

A modo de curiosidad, el sistema gestiona ''logs'' como `syslog` de manera
inteligente, rotándolos y comprimiéndolos para que ocupen el menor espacio
posible.

En el interior del directorio de ''logs'' observamos que existen asimismo
carpetas. Por ejemplo, hay una asociada al paquete Apache que instalamos en
lecciones anteriores

```bash
sudo su
cd apache2/
ls -l
cat error.log
exit
```

Mi usuario no tiene permiso para acceder a la carpeta de ''logs'' de Apache.
Buscando en Google
[este post](https://stackoverflow.com/questions/8221820/cd-into-directory-without-having-permission)
de **stackoverflow** ha resultado de ayuda. Activamos un modo de ''súper
usuario'' con `sudo su`, ejecutamos los comandos deseados y salimos de dicho
modo con `exit`.

En el ''log'' `dmesg` encontramos información principalmente referente al
''hardware'' del sistema:

```bash
sudo cat dmesg
```

A modo de curiosidad, Linux posee un comando específico para acceder a este tipo
de información sin necesidad de revisar el correspondiente ''log''. Por ejemplo,
podemos volver a nuestra carpeta de usuario y teclear `sudo dmesg`:

```bash
cd ~
sudo dmesg
```

Así, tenemos acceso a una cantidad de información apabullante de bajo nivel
sobre el sistema.

Por otra parte, como estamos trabajando con archivos de extensión considerable,
quizá sea conveniente utilizar de manera adicional los comandos `head` o `tail`
para centrar el foco de atención, respectivamente, en el principio o el final
del archivo (10 líneas por defecto):

```bash
sudo head /var/log/syslog
sudo tail /var/log/syslog
```

Con el atributo `-n` declaramos el número de líneas que deseamos consultar:

```bash
sudo head -n 15 /var/log/syslog
sudo tail -n 5 /var/log/syslog
```

Un atributo muy útil para `tail` es `-f` (''follow''), que deja la terminal en
suspenso y nos permite ver cambios en tiempo real en el correspondiente ''log'':

```bash
sudo tail -n 5 -f /var/log/syslog
```

Así, podemos controlar cualquier cambio en el sistema (por ejemplo, el reinicio
de un proceso) que añada información a `syslog`. Para terminar el seguimiento
del archivo, usamos la combinación de teclas `Ctrl + c`.

Una aplicación práctica la encontramos a la hora de reproducir errores que los
usuarios reportan en tiempo real para cierto servidor.

Finalmente, otro comando de utilidad para revisar ''logs'' es `journalctl`:

```bash
sudo journalctl -u apache2
```

Este comando también permite realizar seguimiento con el atributo `-f`.

Podemos conseguir resultados similares concatenando `cat` y `grep` (este último
comando nos permite realizar búsqueda de texto sobre un archivo o salida de otro
comando):

```bash
sudo cat /var/log/syslog | grep apache2
```

### 14. Gestionando usuarios

En esta sección abordaremos la gestión de usuarios, en concreto la creación y
eliminación de usuarios, así como la creación y eliminación de grupos. Antes de
empezar, es importante conocer la existencia del siguiente archivo:

```bash
cat /etc/passwd
```

En él encontramos un listado de todos los usuarios existentes en nuestro
sistema. En la mayoría de los casos, la línea finaliza con `/nologin`, es decir,
son usuarios necesarios para llevar a cabo ciertas tareas de determinadas
aplicaciones y no para acceder al sistema en sí.

En la línea correspondiente a mi usuario, `alexis`,

```bash
alexis:x:1000:1000:alexis,,,:/home/alexis:/bin/bash
```

Los números `1000` que aparecen son, respectivamente, las referencias para el
usuario (''uid'') y el grupo al que pertenece (también denominado `alexis` en
este caso particular). A continuación, figura nuestro directorio de usuario
(`/home/alexis`) y nuestra terminal por defecto (`/bin/bash`). Tras mi nombre de
usuario aparece una `x`, que es la posición que ocuparía nuestra contraseña
(oculta ahora mismo bajo ese carácter `x`). La contraseña, de hecho, se almacena
en otro archivo diferente, ya que dista de ser idóneo que las contraseñas de los
usuarios estén en un archivo de texto de libre acceso.

En general, si el ''uid'' es mayor o igual que `1000` se tratará de un usuario
real, mientras que aquellos que posean referencias inferiores seguramente sean
usuarios de sistema (y no aparecerán por defecto en las ventanas de ''login'' de
usuario).

A continuación, si tecleamos `sudo cat /etc/shadow`, el archivo muestra
información sensible, pero no de forma abierta. En lugar de aparecer nuestra
contraseña, aparece su _hash_ (para los usuarios de sistema sí que aparece
directamente su contraseña).

Un atajo útil de teclado es `!!` que ejecuta el anterior comando escrito en la
terminal. Cuando escribimos una instrucción y no se lleva a cabo por falta de
permisos, simplemente hemos de teclear `sudo !!` para intentar ejecutarla con
permisos de ''super user''.

Otro archivo importante para conocer es `cat /etc/group`, que nos muestra un
listado de los grupos definidos en nuestro sistema, con sus respectivas
referencias (así como sus contraseñas ocultas por el carácter `x`).

Si estamos interesados en conocer a qué grupos pertenecemos, no es necesario
revisar el anterior fichero, ya que basta con teclear `groups`.

¿Cómo creamos un usuario? Mediante `adduser` seguido del nombre del nuevo
usuario. Por ejemplo, `adduser batman`. Sin embargo, encontramos un problema al
ejecutar el anterior comando, ya que la terminal nos indica que solo el usuario
`root` puede añadir un usuario o un grupo al sistema. Como en anteriores
ocasiones, solventamos la situación escribiendo:

```bash
sudo adduser batman
```

Esta acción añade el usuario `batman`, así como el grupo `batman`, además de
generar un directorio de usuario para él y proporcionarle ciertos archivos de
configuración por defecto del sistema desde `/etc/skel`. Después, nos pide una
contraseña para dicho usuario. A continuación, podemos indicar (o dejar en
blanco) algunos datos del usuario, como su nombre completo, número de
habitación, número de teléfono...

Si ahora escribimos `ls -l /home/`, aparece un nuevo directorio asociado al
usuario `batman`.

Para cambiar a este usuario, hemos de escribir `su - batman` e introducir su
correspondiente contraseña (la que hemos definido al crear el usuario). Si ahora
tecleamos `logout` (o usamos la combinación de teclas `Ctrl + d`), volvemos a
nuestro usuario principal. Por otro lado, si escribimos `sudo su - batman`
cambiamos de usuario sin necesidad de introducir la contraseña (al trabajar con
`sudo` es como si adoptáramos el papel del todopoderoso usuario `root`).

Con el comando `passwd` podemos cambiar la contraseña de un usuario.

Para cambiar de usuario a `root`, hemos de teclear `sudo su -`.

Ahora, para eliminar un usuario el comando es `userdel -r` seguido del nombre
del usuario a suprimir:

```bash
sudo userdel -r batman
```

El atributo `-r` se emplea para eliminar asimismo el directorio del usuario, por
lo que hemos de actuar con cautela cuando llevamos a cabo este proceso.

Acto seguido, para añadir un grupo, el comando es `groupadd` seguido del nombre
del grupo:

```bash
sudo groupadd heroes
cat /etc/group
```

Para introducir nuestro usuario en este nuevo grupo, el comando a emplear es:

```bash
sudo usermod -aG heroes alexis
groups
```

No obstante, aunque hemos ejecutado el comando, no aparece el grupo `heroes`
asociado a nuestro usuario. Para ello, hemos de hacer ''logout'' y ''login'' en
el sistema. Sin embargo, en este momento, basta teclear `groups alexis` para
comprobar que, efectivamente, mi usuario pertenece al grupo `heroes`.

Eliminar un usuario de un grupo es también sencillo, ya que basta teclear:

```bash
sudo gpasswd -d alexis heroes
groups alexis
```

Finalmente, para eliminar un grupo, escribimos:

```bash
sudo groupdel heroes
```

Y podemos comprobar que, efectivamente, no pertenece al listado de grupos
tecleando, por ejemplo, `tail /etc/group` y observando que no aparece al final
ninguna línea asociada a `heroes`.

### 15. Examinando el historial de la terminal

En esta sección abordaremos cómo aprovechar de nuevo acciones llevadas a cabo en
la terminal.

En primer lugar, con las teclas de los cursores (arriba y abajo en este caso
particular), podemos desplazarnos por el historial de comandos ejecutados. Ello
nos permite ejecutarlos de nuevo o editarlos para lanzarlos de una forma
ligeramente diferente a la terminal.

En segundo lugar, a través del comando `history`, tenemos acceso a la totalidad
de comandos ejecutados en la terminal. Cada uno de ellos posee un número de
referencia al principio de la línea, de manera que podemos ejecutarlos haciendo
uso de dicho número, siempre y cuando antecedamos la referencia con el símbolo
de exclamación `!` (por ejemplo `!283`)

Ahora bien, si queremos que un comando no figure en el historial, basta pulsar
la tecla de espacio antes de empezar a escribir el comando en cuestión:

```bash
 sudo apt upgrade
```

No obstante, este comportamiento depende de la distribución de Linux empleada.
En Xubuntu, efectivamente, podemos emplear este recurso para evitar que ciertos
comandos aparezcan listados en el historial.

¿Qué puede llevarnos a querer omitir comandos en el historial? Por ejemplo,
quizá sea una práctica recomendable para aquellos que posean cierta información
sensible (datos, contraseñas...).

Finalmente, el historial también es una herramienta útil para averiguar cómo se
han resueltos incidencias en el pasado (por otras personas, si es la primera vez
que administramos cierto servidor que lleva operativo un tiempo).

### 16. Redirecciones

En esta sección abordaremos cómo redirigir la salida de ciertos comandos para
que esta asuma el papel de entrada para otras instrucciones.

Empecemos redirigiendo la salida de un comando hacia un archivo, acción que nos
puede resultar de gran utilidad para almacenar, por ejemplo, cierta información
del sistema o de sus usuarios. Para llevar a cabo dicha acción, utilizamos el
símbolo `>`:

```bash
ls -l > file.txt
cat file.txt
```

A continuación, si volvemos a ejecutar el comando `ls -l > file.txt`, no
observaremos cambio alguno, pues el archivo se sobrescribe. Podemos modificar
este comportamiento (un tanto peligroso y desaconsejable si no actuamos con
extrema cautela) utilizando `>>`, pues añade la salida del comando al final del
archivo en lugar de sobrescribirlo:

```bash
ls -l >> file.txt
```

En general, se recomienda el uso de `>>` para evitar la pérdida de información
que provoca `>`.

Por otra parte, podemos encadenar comandos con el símbolo `|` (''pipe''). Por
ejemplo, imaginemos que queremos listar los contenidos de un directorio, pero
filtrar (a través del comando `grep`) solo aquellos elementos que contengan la
palabra `file`:

```bash
ls -l | grep file
```

Como no podía ser de otra manera, podemos emplear esta filosofía a la hora de
examinar ''logs'':

```bash
cat file.txt | sort | uniq
```

A primera vista, aunque hayamos usado el comando `uniq`, apreciamos elementos
repetidos. No obstante, el diablo está en los detalles, pues a medida que hemos
ido incorporando listados al archivo `file.txt` su tamaño ha ido incrementándose
y de ahí que aparezca en varias ocasiones.

Finalmente, para contar el número de elementos aproximadamente, puede resultar
de utilidad la siguiente instrucción:

```bash
ls -l | wc -l
```

### 17. Streams

En esta sección abordaremos los ''streams'', un concepto relacionado con la
redirección de la salida de comandos hacia la entrada de otros. Hay tres tipos
de ''streams'' en Linux que conviene conocer:

- ''standard input'' (`stdin`)
- ''standard output'' (`stdout`)
- ''standard error'' (`stderr`)

Entre los tres anteriores, el más sencilla de entender es ''standard output'',
pues es el ''stream'' que se genera al emplear comandos que producen cierta
salida a la terminal. Por ejemplo, `ls -l`.

A continuación, el ''stream'' de ''standard error'' aparece cuando los comandos
que empleamos arrojan errores en la terminal (aunque produzca información, como
en el caso anterior, no hemos de confundir este ''stream'' con ''standard
output'', pues se trata de un mensaje de error). Por ejemplo, si en nuestro
sistema no disponemos de ningún directorio denominado `Turtles`, el siguiente
comando produciría una salida al ''stream'' de ''standard error'':
`ls /Turtles`.

Acto seguido, en el siguiente ejemplo, listemos los contenidos del directorio
del usuario (en mi caso, `alexis`):

```bash
ls -l /home/alexis/
```

Si ahora tecleamos `echo $?`, la terminal arroja `0` (que hemos de interpretar
como que la operación ha sido llevada a cabo con éxito). La combinación `$?` es
una variable asociada a la salida producida por el comando anterior, mientras
que `echo` nos permite transmitir información a la consola (por ejemplo,
`echo "Hola mundo"` imprime en la terminal el mensaje `Hola mundo`).

No obstante, si ahora escribimos:

```bash
ls -l /Turtles/
echo $?
```

En esta ocasión, la terminal arroja `2`, que al ser un número distinto de cero
hemos de interpretar como un error. Así, a la hora de escribir programas
(conocidos generalmente como ''bash scripts''), este comportamiento nos puede
resultar de utilidad para distinguir ''standard output'' de ''standard error'' y
actuar de manera acorde a cada uno.

Al hilo de la anterior idea, el uso del comando `find`, que se emplea para
buscar archivos, aporta también buenos ejemplos para entender la distinción de
los anteriores ''streams''. Por ejemplo, si tecleamos:

```bash
find / -name *.log
```

En el extenso listado observamos la presencia de numerosos errores
(`Permission denied`). Una vía de escape a esta situación es ejecutar el
anterior comando bajo el auspicio de `sudo`, aunque recurrir al usuario `root`
para evitar errores no es una buena práctica y únicamente deberíamos emplearlo
cuando no existe alternativa posible. Así pues, en su lugar, escribimos:

```bash
find / -name *.log 2> /dev/null
```

Esto es, buscamos por nombre todos los archivos desde la raíz del sistema cuya
extensión sea `log`, capturamos los errores (de ahí el código `2`) y los
redirigimos a `/dev/null`, que es una suerte de purgatorio.

Actuando de tal forma, observamos únicamente los ''logs'' para los cuales
tenemos permisos. No quiere decir esto que hayan desaparecido el resto de los
anteriores ''logs'', sino que han sido desviados a `/dev/null`, en lugar de
aparecer en el ''standard output''.

No hemos hablado todavía del ''stream'' de ''standard input'', pero hace
referencia a todo ''input'' o entrada del usuario. Por ejemplo, se trata de
''standard input'' cuando recogemos en variables para un programa datos que el
usuario introduce de alguna manera.

En nuestros programas, podemos hacer referencia a cada uno de los ''streams''
por número:

- `stdin`, mediante `0`.
- `stdout`, mediante `1`.
- `stderr`, mediante `2`.

Así, podemos modificar el anterior comando, de forma que los errores los
almacene en un archivo, `errors.txt`, y en la terminal aparezcan únicamente
aquellos ''logs'' para los cuales disponemos de permisos:

```bash
find / -name *.log 2> errors.txt
```

Análogamente, podemos recopilar aquellos ''logs'' para los cuales tenemos
permisos en un archivo, `success.txt`, sin más que capturar el ''standard
output'':

```bash
find / -name *.log 1> success.txt
```

### 18. Variables

En esta sección abordaremos el concepto de variable en Linux. Estudiaremos cómo
crear una variable y cómo leer su contenido. Su uso está más enfocado a la
programación de _scripts_, pero ocasionalmente pueden surgir a la hora de
manejar comandos en la terminal.

Para empezar, recodemos que el comando `echo` devuelve a la terminal el
contenido de una cadena de texto o, en este caso particular, de una variable:

```bash
echo "Hello world!"
```

A continuación, estudiemos cómo crear una variable. Por convención, el nombre de
estas se suele escribir en mayúsculas:

```bash
HELLOMSG="Hello world!"
```

De esta manera, hemos creado la variable `HELLOMSG`, que contiene el mensaje
`"Hello world!"`. Para leer su contenido, accedemos a ella en la terminal a
través del comando `echo` y antecediendo el nombre de la variable con el símbolo
`$`:

```bash
echo $HELLOMSG
```

Por otra parte, las variables no tienen por qué siempre cadenas de texto:

```bash
MY_NUM=3
MY_NUM2=10
```

```bash
echo $MY_NUM
echo $MY_NUM2
```

Las variables son específicas a la sesión de la terminal. Su alcance está
limitado a la terminal en concreto donde se han definido y se perderán una vez
esta se cierre. Una forma de solventar esta situación es añadiéndolas al archivo
de configuración `.bashrc`.

Además, podemos insertar variables dentro de cadenas de texto, para así
personalizar mensajes. Por ejemplo:

```bash
MY_NAME="Alexis"
echo $MY_NAME
echo "My name es $MY_NAME"
```

Por otra parte, también podemos emplear variables como argumentos de comandos
que hemos visto en lecciones anteriores:

```bash
MY_DIR="/etc/"
ls $MY_DIR
```

Si nos encontramos en la tesitura de tener que escribir repetidamente largas
cadenas de texto, el uso de variables nos puede ahorrar mucho tiempo.

Finalmente, a través del comando `env` tenemos acceso al listado de variables de
entorno definidas en el sistema.

Las que hemos definido anteriormente no aparecen en el anterior listado, pues no
están definidas como variables de entorno. Para ello, deberíamos teclear
`export MY_NAME="Alexis"`.

### 19. El comando `find`

En esta sección abordaremos un comando de extrema utilidad en Linux, `find`,
encargado de buscar archivos en el sistema.

Para empezar, si no indicamos un directorio como argumento del comando `find`,
este asume como valor por defecto el actual directorio de trabajo. Así, si
queremos buscar por nombre el directorio `Music`, basta con que escribamos:

```bash
find -name Music
```

De esta forma, obtenemos como salida la ruta `./Music`, que nos ubica el
mencionado directorio. Ahora, actuando de manera análoga:

```bash
cd /var/
find -name log
```

En esta ocasión, aparece un listado de extensión considerable (la mayoría
compuesto por errores debidos a faltas de permisos) que podemos filtrar mediante
el uso de otros parámetros. Por ejemplo, si únicamente estamos interesados en
encontrar directorios, podemos añadir `-type d` (el valor `f` correspondería al
tipo asociado a archivos):

```bash
find -type d -name log
```

Por otra parte, recordemos que podemos redirigir los errores que aparecen en la
salida hacia `/dev/null`, para que así no se muestren en el listado de la
terminal:

```bash
find -type d -name log 2> /dev/null
```

A continuación, volvamos al directorio de usuario y desde allí busquemos en la
carpeta `/var` aquellos archivos terminados en `log` (enviando cualquier error a
`/dev/null`):

```bash
cd ~
find /var -type f -name "*log" 2> /dev/null
```

Es una buena práctica escribir la cadena a buscar entrecomillada.

Además, con el uso de comodines, es fácil modificar el comando anterior para que
muestre los archivos que en su nombre contengan el texto `log`:

```bash
find /var -type f -name "*log*" 2> /dev/null
```

Por otro lado, ¿y si queremos encontrar los archivos que han sido modificados en
la última semana? Usamos para ello el atributo `-mtime` y le pasamos como
argumento el número de días:

```bash
find /var/log -type f -name *.log -mtime -7
```

Además, podemos ejecutar comandos a los resultados de la búsqueda a través del
atributo `-exec`. Por ejemplo, si queremos eliminar aquellos ''logs'' que posean
7 días de antigüedad, añadiríamos al final `-exec rm {} \;`, donde las llaves
hacen referencia a cada línea de la salida del comando find. No obstante, como
mencionamos en lecciones anteriores, hemos de ser cautos a la hora de emplear el
comando `rm` para no eliminar del sistema información importante.

### 20. Cambiando permisos numéricamente

En esta sección abordaremos la gestión de permisos numéricamente. Recordemos que
el tratamiento de permisos ya lo estudiamos en la novena sección, aunque en ella
los establecimos a través de la secuencia de caracteres `rwx`.

Así, las equivalencias numéricas de dichos permisos son:

- `4` equivale a `r`
- `2` equivale a `w`
- `1` equivale a `x`

En la práctica, empleando el comando `chmod` podemos escribir:

```bash
touch test-permissions.txt
ls -l
chmod 400 test-permissions.txt
ls -l
```

Como podemos observar, el propietario dispone del permiso de lectura (dado el
`4` que figura al principio del código), mientras que el resto de los permisos
quedan desactivados. Además, ni el grupo, ni el resto de los usuarios, posee
permiso alguno, pues para ellos hemos declarado un `0` en cada caso (el primer
cero hace referencia al grupo, mientras que el segundo está asociado al resto de
usuarios).

Siguiendo esta filosofía, con `chmod 444 test-permissions.txt`, tanto el
administrador, como el grupo y el resto de los usuarios poseerían el permiso de
lectura para este fichero en concreto.

En cuanto al permiso para escritura, generamos ejemplos similares a los
anteriores sin más que teclear `chmod 200 test-permissions.txt` o
`chmod 222 test-permissions.txt`.

Ahora bien, ¿cómo asignamos varios permisos simultáneamente? Por ejemplo, para
que el administrador posea todos los permisos disponibles sobre el archivo,
hemos de teclear:

```bash
chmod 700 test-permissions.txt
ls -l
```

Por tanto:

- `7` asigna los permisos `rwx`.
- `6` asigna los permisos `rw-`.
- `5` asigna los permisos `r-x`.
- `3` asigna los permisos `-wx`.

Seguramente, a estas alturas, hayamos detectado el patrón de funcionamiento. Si
queremos asignar varios permisos, simplemente hemos de realizar la suma de sus
valores e introducir ese resultado en el dígito deseado del código numérico. Por
ejemplo, `rwx`, echando cuentas, equivale a `4 + 2 + 1`, esto es, a `7`.
Análogamente, `-wx`, equivale a `0 + 2 + 1`, es decir, a `3`.

En la práctica, un código de permisos muy frecuente para archivos es `644`.

Aunque en la sección hemos trabajado únicamente con ficheros, la misma filosofía
se emplea para directorios. No obstante, hemos de recordar que los permisos no
tienen exactamente el mismo significado para archivos que para carpetas, como
bien comentamos en la novena sección de este artículo.

### 21. Referencias

- [Linux Commands for Beginners](https://youtube.com/playlist?list=PLT98CRl2KxKHaKA9-4_I38sLzK134p4GJ)
- [The Odin Project](https://www.theodinproject.com/)

### 22. Historial de versiones del artículo

- 2023.06.12: Escribe la sección sobre el cambio numérico de permisos
- 2023.06.11: Escribe la sección sobre el comando `find`
- 2023.06.10: Escribe la sección sobre variables
- 2023.06.09: Escribe la sección sobre ''streams''
- 2023.06.07: Escribe la sección sobre redirecciones
- 2023.06.05: Reunifica las doce primeras lecciones en un único artículo
- 2023.06.01: Escribe la sección sobre el historial de la terminal
- 2023.05.31: Escribe la sección sobre la gestión de usuarios
- 2023.05.30: Escribe la sección sobre la revisión de ''logs''
- 2023.05.29: Escribe la sección sobre la gestión de procesos
- 2023.06.28: Escribe la sección sobre la gestión de paquetes
- 2023.06.27: Escribe la sección sobre el control de recursos del sistema
- 2023.05.26: Escribe la sección sobre permisos
- 2023.06.25: Escribe la sección sobre el uso de alias
- 2023.06.24: Escribe la sección sobre la configuración de la terminal
- 2023.06.23: Escribe la sección sobre mover y renombrar archivos
- 2023.05.22: Escribe la sección sobre la edición de archivos
- 2023.06.21: Escribe las secciones de introducción y navegación por el sistema
  de ficheros
