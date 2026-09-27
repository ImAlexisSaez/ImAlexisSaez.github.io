---
title: "Curso de Python #11 (Nivel básico)"
summary: Práctica guiada
date: 2019-09-01
lastmod: 2026-09-27
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

### 1. Práctica guiada I

#### 1.1. Vídeo

{{< youtube E0OqddzjFUY >}}

#### 1.2. Notas personales

En esta lección, y con el objetivo de reforzar los contenidos vistos hasta la
fecha, comenzaremos a esbozar una aplicación gráfica de tipo _CRUD_. Mediante
ella, conectaremos con una base de datos (BBDD) y podremos realizar las
operaciones básicas: _Create_, _Read_, _Update_ y _Delete_.

En el vídeo se explican los diferentes elementos y funcionalidades que
caracterizan a la aplicación propuesta, por si queremos lanzarnos a su
elaboración de antemano. No obstante, se procederá a su implementación en
posteriores lecciones.

### 2. Práctica guiada II

#### 2.1. Vídeo

{{< youtube o8E869dmK3U >}}

#### 2.2. Notas personales

En esta lección, comenzaremos a esbozar la interfaz gráfica de nuestra
aplicación _CRUD_. Para ello, empezamos tecleando:

```python
from tkinter import Tk

# Raíz de la aplicación
root = Tk()
root.title("Aplicación CRUD")
root.iconbitmap("icon.ico")

# Ejecución de la aplicación
root.mainloop()
```

A continuación, generamos la barra de menú superior:

```python
# Menú superior de la aplicación
barra_menu = Menu(root)
root.config(menu=barra_menu)

bbdd_menu = Menu(barra_menu, tearoff=0)
bbdd_menu.add_command(label="Conectar")
bbdd_menu.add_separator()
bbdd_menu.add_command(label="Salir")

borrar_menu = Menu(barra_menu, tearoff=0)
borrar_menu.add_command(label="Borrar campos")

crud_menu = Menu(barra_menu, tearoff=0)
crud_menu.add_command(label="Crear")
crud_menu.add_command(label="Leer")
crud_menu.add_command(label="Actualizar")
crud_menu.add_command(label="Borrar")

help_menu = Menu(barra_menu, tearoff=0)
help_menu.add_command(label="Licencia")
help_menu.add_separator()
help_menu.add_command(label="Acerca de...")

barra_menu.add_cascade(label="BBDD", menu=bbdd_menu)
barra_menu.add_cascade(label="Borrar", menu=borrar_menu)
barra_menu.add_cascade(label="CRUD", menu=crud_menu)
barra_menu.add_cascade(label="Ayuda", menu=help_menu)
```

Por lo que respecta al cuerpo de la aplicación, lo dividiremos en dos _frames_:
uno superior para organizar los campos de introducción de datos y otro inferior
para distribuir los cuatro botones que nos permitirán llevar a cabo acciones de
tipo _CRUD_.

Así pues, si, por ejemplo, optamos por construir los diferentes campos de
entrada que poseerá la aplicación, el bloque de código a escribir será:

```python
# Frame superior
campos_frame = Frame(root)
campos_frame.pack()

id_entry = Entry(campos_frame)
id_entry.grid(row=0, column=1, padx=2, pady=2)

name_entry = Entry(campos_frame)
name_entry.grid(row=1, column=1, padx=2, pady=2)

lastname_entry = Entry(campos_frame)
lastname_entry.grid(row=2, column=1, padx=2, pady=2)

address_entry = Entry(campos_frame)
address_entry.grid(row=3, column=1, padx=2, pady=2)

password_entry = Entry(campos_frame)
password_entry.grid(row=4, column=1, padx=2, pady=2)
password_entry.config(show="*")

comment_text = Text(campos_frame, width=15, height=5)
comment_text.grid(row=5, column=1, padx=2, pady=2)
comment_text_scrollvert = Scrollbar(campos_frame, command=comment_text.yview)
comment_text_scrollvert.grid(row=5, column=2, sticky="nsew")
comment_text.config(yscrollcommand=comment_text_scrollvert)
```

### 3. Práctica guiada III

#### 3.1. Vídeo

{{< youtube OJzFGgOSpvI >}}

#### 3.2. Notas personales

En esta lección, una vez declarados los campos de introducción de datos en la
anterior, nos centraremos en ubicar las etiquetas en la aplicación:

```python
id_label = Label(campos_frame, text="ID:")
id_label.grid(row=0, column=0, sticky="e", padx=2, pady=2)

name_label = Label(campos_frame, text="Nombre:")
name_label.grid(row=1, column=0, sticky="e", padx=2, pady=2)

lastname_label = Label(campos_frame, text="Apellido:")
lastname_label.grid(row=2, column=0, sticky="e", padx=2, pady=2)

address_label = Label(campos_frame, text="Dirección:")
address_label.grid(row=3, column=0, sticky="e", padx=2, pady=2)

password_label = Label(campos_frame, text="Contraseña:")
password_label.grid(row=4, column=0, sticky="e", padx=2, pady=2)

comment_label = Label(campos_frame, text="Comentarios:")
comment_label.grid(row=5, column=0, sticky="ne", padx=2, pady=2)
```

A continuación, ocupémonos de construir un _frame_ en la parte inferior del ya
disponible y disponer cuatro botones:

```python
# Frame inferior
botones_frame = Frame(root)
botones_frame.pack(expand=True)

crear_button = Button(botones_frame, text="Create")
crear_button.grid(row=0, column=0, sticky="e", padx=2, pady=2)

read_button = Button(botones_frame, text="Read")
read_button.grid(row=0, column=1, sticky="e", padx=2, pady=2)

update_button = Button(botones_frame, text="Update")
update_button.grid(row=0, column=2, sticky="e", padx=2, pady=2)

delete_button = Button(botones_frame, text="Delete")
delete_button.grid(row=0, column=3, sticky="e", padx=2, pady=2)
```

Así, ya únicamente nos resta programar la funcionalidad de la aplicación, tanto
para el menú, como para los botones recién creados.

### 4. Práctica guiada IV

#### 4.1. Vídeo

{{< youtube 5XPLCDp7nDk >}}

#### 4.2. Notas personales

En esta lección, implementaremos cierta funcionalidad a nuestra aplicación,
comenzando por el menú _BBDD_. Programaremos la función que realiza la conexión
a la base de datos (BBDD) y la que posibilita la opción de salir de la
aplicación.

Por lo que respecta a la conexión de la BBDD, como la primera vez que pulsemos
la función va a encargarse de crear la tabla, después hemos de controlar la
excepción que aparece al volver a llamar la función con dicha tabla ya creada.

```python
# Función para conectar a la BBDD
def conecta_bbdd():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    try:
        cursor.execute('''
            CREATE TABLE DATOS_USUARIOS (
            ID INTEGER PRIMARY KEY AUTOINCREMENT,
            NOMBRE_USUARIO VARCHAR(50),
            APELLIDO VARCHAR(50),
            DIRECCION VARCHAR(50),
            PASSWORD VARCHAR(50),
            COMENTARIOS VARCHAR(250))
            ''')
    except sqlite3.OperationalError:
        pass
    finally:
        messagebox.showinfo(
            title="Conexión a la base de datos",
            message="La conexión a la base de datos se ha realizado con éxito."
        )
```

Acto seguido, acudimos a la instrucción que gestiona el elemento del menú _BBDD_
correspondiente y la modificamos como sigue:

```python
bbdd_menu.add_command(label="Conectar", command=conecta_bbdd)
```

Finalmente, implementemos la función que gestiona la salida de la aplicación. El
código es idéntico al visto en lecciones anteriores:

```python
# Función para salir de la aplicación
def sale_aplicacion():
    valor = messagebox.askquestion(
        title="Salir",
        message="¿Deseas realmente salir de la aplicación?")
    if valor == "yes":
        root.destroy()
```

Y añadimos la funcionalidad al correspondiente elemento del menú _BBDD_:

```python
bbdd_menu.add_command(label="Salir", command=sale_aplicacion)
```

### 5. Práctica guiada V

#### 5.1. Vídeo

{{< youtube mNzHPglBuUk >}}

#### 5.2. Notas personales

En esta lección, analizaremos cómo limpiar los campos de registros (por si el
usuario comete algún error al transcribir los datos) e insertar datos en la base
de datos (BBDD), es decir, ejecutar la operación de tipo _Create_.

Para empezar, de cara a poder realizar manipulaciones sobre el texto que un
usuario escriba en los campos de registros, hemos de emplear variables de tipo
`StringVar`:

```python
id_data = StringVar()
name_data = StringVar()
lastname_data = StringVar()
address_data = StringVar()
password_data = StringVar()
```

A continuación, las asignamos a sus correspondientes `Entry`:

```python
id_entry = Entry(campos_frame, width=40, textvariable=id_data)
name_entry = Entry(campos_frame, width=40, textvariable=name_data)
lastname_entry = Entry(campos_frame, width=40, textvariable=lastname_data)
address_entry = Entry(campos_frame, width=40, textvariable=address_data)
password_entry = Entry(campos_frame, width=40, textvariable=password_data)
```

Después, construimos la función que limpia los campos de registros:

```python
# Función que limpia los registros de la aplicación
def limpia_registros():
    id_data.set("")
    name_data.set("")
    lastname_data.set("")
    address_data.set("")
    password_data.set("")
    comment_text.delete(1.0, END)
```

_Notas_:

- Notemos cómo se limpia un cuadro de comentario, ya que el procedimiento a
  seguir es un tanto diferente. Hemos de utilizar la función `delete()`,
  indicándole el punto de partida (`1.0`) y el de finalización (`END`).
- Al hilo de lo anterior, `END` es asimismo una instrucción de la librería
  `tkinter`, de manera que hemos de importarla si estamos siguiendo la
  estrategia de `from tkinter import ...`. De hecho, en mi código dicha
  instrucción comienza a adquirir una longitud considerable, siendo en la
  actualidad:

```python
from tkinter import Button, END, Entry, Frame, Label, Menu, messagebox, Scrollbar, StringVar, Text, Tk
```

Ahora, asignamos esta funcionalidad al elemento correspondiente el menú:

```python
borrar_menu.add_command(label="Borrar campos", command=limpia_registros)
```

Acto seguido, abordemos la primera operación _CRUD_, _Create_, que nos permitirá
añadir registros a la BBDD.

```python
# Función que inserta registros en la BBDD
def crud_create():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    cursor.execute("INSERT INTO DATOS_USUARIOS VALUES (NULL, '" +
                   name_data.get() + "', '" + lastname_data.get() + "','" +
                   address_data.get() + "','" + password_data.get() + "','" +
                   comment_text.get("1.0", END) + "')")
    conexion.commit()
    messagebox.showinfo(
        title="Crear registro",
        message="Registro insertado con éxito en la base de datos.")
    conexion.close()
```

_Notas_:

- No recogemos aquello que el usuario escribe en el campo _ID_, ya que lo hemos
  declarado en la tabla como clave primaria autoincrementable (de ahí el `NULL`
  en la instrucción _SQL_ de arriba). Este proceder puede resultar un tanto
  confuso para el usuario y admite margen de mejora.
- Es muy sencillo equivocarse a la hora de escribir la anterior instrucción
  _SQL_ por el elevado número de concatenaciones. Un enfoque alternativo
  consiste en escribir primero una serie de datos concretos de ejemplo y,
  después, poco a poco sustituir dichos datos por las correspondientes variables
  con sus métodos `get()` asociados.

Finalmente, añadimos la funcionalidad, tanto al elemento de menú
correspondiente, como al botón que figura en la parte inferior de la aplicación:

```python
crud_menu.add_command(label="Crear", command=crud_create)

crear_button = Button(botones_frame, text="Create", command=crud_create)
```

### 6. Práctica guiada VI

#### 6.1. Vídeo

{{< youtube nx3OE31y0IY >}}

#### 6.2. Notas personales

En esta lección, abordaremos la implementación de las operaciones de tipo _Read_
y _Update_. El criterio para posibilitar la lectura de registros será que el
usuario introduzca en el formulario la _ID_ de la cual desea consultar la
información pertinente.

En primer lugar, implementemos la función de lectura, apoyándonos en cómo
procedimos en anteriores lecciones:

```python
# Función que lee registros de la BBDD
def crud_read():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    cursor.execute("SELECT * FROM DATOS_USUARIOS WHERE ID=" + id_data.get())
    usuario = cursor.fetchall()
    for u in usuario:
        id_data.set(u[0])
        name_data.set(u[1])
        lastname_data.set(u[2])
        address_data.set(u[3])
        password_data.set(u[4])
        comment_text.insert(1.0, u[5])
    conexion.commit()
    conexion.close()
```

Luego, añadimos la funcionalidad, tanto al elemento del menú correspondiente,
como al botón asociado:

```python
crud_menu.add_command(label="Leer", command=crud_read)

read_button = Button(botones_frame, text="Read", command=crud_read)
```

_Nota_: así programa la funcionalidad, la aplicación no responde cuando se
inserta un _ID_ que no figura en la base de datos. Habría de mostrar un mensaje
de advertencia mediante la clase `messagebox`.

Acto seguido, ocupémonos de la función de tipo _Update_, que será muy similar a
la programada para _Create_:

```python
# Función que actualiza registros de la BBDD
def crud_update():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    cursor.execute("UPDATE DATOS_USUARIOS SET NOMBRE_USUARIO='" +
                   name_data.get() + "', APELLIDO='" + lastname_data.get() +
                   "', DIRECCION='" + address_data.get() + "', PASSWORD='" +
                   password_data.get() + "', COMENTARIOS='" +
                   comment_text.get("1.0", END) + "'")
    conexion.commit()
    messagebox.showinfo(
        title="Actualizar registro",
        message="Registro actualizado con éxito en la base de datos.")
    conexion.close()
```

Después, añadimos el comportamiento, tanto al elemento del menú asociado, como
al botón correspondiente:

```python
crud_menu.add_command(label="Actualizar", command=crud_update)

update_button = Button(botones_frame, text="Update", command=crud_update)
```

### 7. Práctica guiada VII

#### 7.1. Vídeo

{{< youtube nj-alxd7YvM >}}

#### 7.2. Notas personales

En esta lección, abordaremos cómo borrar registros (operación de tipo _Delete_)
y la creación de consultas parametrizadas.

En cuanto a la primera tarea, empecemos construyendo la correspondiente función:

```python
# Función que borra registros de la BBDD
def crud_delete():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    cursor.execute("DELETE FROM DATOS_USUARIOS WHERE ID=" + id_data.get())
    conexion.commit()
    conexion.close()
    messagebox.showinfo(
        title="Borrar registro",
        message="Registro borrado con éxito en la base de datos.")
```

Acto seguido, añadimos la funcionalidad, tanto al elemento del menú asociado,
como al botón correspondiente:

```python
crud_menu.add_command(label="Borrar", command=crud_delete)

delete_button = Button(botones_frame, text="Delete", command=crud_delete)
```

A continuación, analicemos cómo modificar algunas de las consultas _SQL_ para
hacerlas parametrizadas y que su escritura sea mucho más sencilla:

```python
# Función que inserta registros en la BBDD
def crud_create():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    datos = name_data.get(), lastname_data.get(), address_data.get(), password_data.get(), comment_text.get("1.0", END)
    cursor.execute("INSERT INTO DATOS_USUARIOS VALUES (NULL, ?, ?, ?, ?, ?)", (datos))
    conexion.commit()
    messagebox.showinfo(
        title="Crear registro",
        message="Registro insertado con éxito en la base de datos.")
    conexion.close()
```

```python
# Función que actualiza registros de la BBDD
def crud_update():
    conexion = sqlite3.connect("usuarios")
    cursor = conexion.cursor()
    datos = name_data.get(), lastname_data.get(), address_data.get(), password_data.get(), comment_text.get("1.0", END)
    cursor.execute("UPDATE DATOS_USUARIOS SET NOMBRE_USUARIO=?, APELLIDO=?, DIRECCION=?, PASSWORD=?, COMENTARIOS=? WHERE ID=" + id_data.get(), (datos))
    conexion.commit()
    messagebox.showinfo(
        title="Actualizar registro",
        message="Registro actualizado con éxito en la base de datos.")
    conexion.close()
```

Finalmente, como extra, incluyamos funcionalidad para los dos elementos del menú
_Ayuda_:

```python
# Función licencia
def licencia():
    messagebox.showwarning(title="Licencia",
                           message="Producto bajo licencia GNU.")


# Función acerca de...
def acerca_de():
    messagebox.showinfo(title="Acerca de...",
                        message="Aplicación creada por Alexis Sáez.")
```

Ahora, incorporemos dicha funcionalidad en los elementos del menú:

```python
help_menu.add_command(label="Licencia", command=licencia)

help_menu.add_command(label="Acerca de...", command=acerca_de)
```
