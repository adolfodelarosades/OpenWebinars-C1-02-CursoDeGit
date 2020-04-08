# 3. Organización del código fuente y otros elementos del proyecto 67m
   * Creación de un repositorio 8:04 
   * Aprobando cambios (Parte I) 9:45 
   * Aprobando cambios (Parte II) 15:00 
   * Trabajo remoto 16:19 
   * Deshacer cambios 18:19 
   * Reparando conflictos de unión con merge 
   * Contenido adicional 5
   
## Creación de un repositorio 8:04 

[Creación de un repositorio](pdfs/Creación_de_un_repositorio.pdf)

En esta lección aprenderemos a inicializar un repositorio GIT y a probar (commit) ficheros en el control de versiones.

El control de versiones te permite grabar cambios en un fichero o grupo de ficheros permitiendo volver atrás a una versión específica si se requiere.

Git es un Sistema de Control de Versiones Distribuido (Distributed Version Control System). Esto quiere decir que, en lugar de disponer de una instantánea de los últimos ficheros, disponemos de un espejo (mirror) completo del repositorio en nuestra máquina local. El repositorio mantiene un registro de los cambios, cuándo sucedieron y quién los efectuó. Tener todo el repositorio en nuestra máquina local reduce los retrasos provocados por tráfico de red y te permite seguir trabajando cuando estamos desconectados.

### Paso 1 - Git Init

Para almacenar un directorio bajo control de versiones, se necesita crear un repositorio. Con GIT se inicializa un repositorio en el primer nivel del directorio de un proyecto.

Aprovecharemos esta práctica para introducir los settings iniciales de Git.

#### Tarea

Introducir previamente los settings iniciales de Git que vamos a utilizar.

Posteriormente, iniciaremos un nuevo proyecto, y será necesario crear un nuevo repositorio. Se usará el comando git init para crear el repositorio.

#### Avanzado

Después de inicializar un repositorio, se crea un nuevo subdirectorio oculto *.git* . Este subdirectorio contiene los metadatos que Git utiliza para almacenar su información. Explorar los contenidos del mismo para ver su contenidos.

### Paso 2 - Git Status

Cuando un directorio es parte de un repositorio, se le llama *Working Directory*. Un directorio de trabajo o *working directory* contiene la última versión descargada desde el repositorio junto con cualquier cambio que tenga que ser aprobado. Al estar trabajando en un proyecto, todos los cambios se realizan en el *working directory*.

Podemos ver los cuales de los ficheros han cambiado en el *working directory* y qué cambios van a ser aprobados (*committed*) al repositorio usando el comando git status.

La salida de este comando recibe el nombre de *“working tree status“*.

#### Tarea

En nuestro espacio de trabajo, o directorio scn1, creamos un archivo README.md y un par de archivos más.

A continuación, lanzamos el comando git status

#### Avanzado

Todos los ficheros que creamos en nuestro espacio aparecen como “untracked“ o no considerados por Git mientras no le digamos lo contrario. Los detalles para resolver esto se cubren en el siguiente paso.

### Paso 3 - Git Add

Para guardar, o aprobar (commit) ficheros en nuestro repositorio GIT, primero se necesita añadirlos al *stagging area* (área de preparación). Git tiene tres áreas: un *working directory*, un *staging area*, y el propio repositorio en sí (directorio oculto .git). Los usuarios “mueven” (también se refiere a ello como “promueven/*promote*”) cambios desde el *working directory* al área de preparación o *staging área*, antes de aprobarlos/*commit* hacia el repositorio.

Uno de los enfoques clave con Git consiste en que los *commits* están concentrados, son pequeños y frecuentes. El área de preparación/staging area ayuda a mantener este flujo de trabajo permitiendo promover solo ciertos ficheros cada vez en lugar de obligar a subir todos los cambios del directorio de trabajo.

#### Tarea

Dentro del directorio en el que estamos, al que previamente hemos hecho git init, creamos un fichero “hello-world.js” con este contenido:

```js
console.log("Hello World");
```

Luego, usa el comando git add para agregar *hello-world.js* a la staging area.

#### Avanzado

Importante: si hacemos cualquier otro cambio adicional a ese fichero posterior a la ejecución de *git add* (es decir, después de agregarlo a la *staging area*), el cambio no se reflejará hasta que no lances *git add* otra vez.

#### Protip

Tal y como se describió en el paso 2, el comando git status te permite ver el estado tanto del *working directory* como de la *staging area* en cualquier momento.

#### Paso 4 - Git Commit

Una vez que el fichero ha sido añadido a la satging area, se necesita que sea aprobado (commited) hacia el repositorio. El comando git commit -m “commit message” mueve ficheros desde la staging area o área de preparación hacia el repositorio, y almacena fecha/hora, autor y un mensaje de aprobación que puede usarse para agregar información de contexto adicional a los cambios, como por ejemplo un identificador de error, o número identificador de *bug*.

Solo los cambios añadidos a la staging area serán aprobados/*commited*; cualquier fichero en el *working directory* que no haya sido añadido con git add (es decir, cualquier fichero no *staged*), no se incluirá en el commit de cambios.

#### Tarea

Usamos el editor nano o vim para crear un fichero README2.md

Le agregamos contenido. Lo añadimos a staging area.

Use git commit -m ““ para aprobar el fichero que hemos creado.

Ahora creamos otros dos ficheros. En ambos introducimos contenido.

Agregamos a staging **SOLO** uno de ellos.

Lanzamos git commit.

Posteriormente, comprobamos que quedan ficheros que no han subido al repositorio.

#### Avanzado

A cada commit se le asigna un hash SHA-1 que posibilita identificarlo para usos futuros. Obsérvalo.

### Paso 5 - Git Ignore

A veces, hay ficheros o directorios que nunca querremos aprobar aunque estén en nuestro *working directory* , como por ejemplo configuración local de desarrollo. Para ignorar estos ficheros, usamos un fichero *.gitignore* lal raíz del repositorio.

El fichero *.gitignore* te permite definir máscaras o *wildcards* para los ficheros que deseamos ignorar; por ejemplo, el wildcard “.tmp” *permitiría ignorar a todos los ficheros con extensión* tmp* .

Cualquier fichero que corresponda a un *wildcard* no será mostrado en la salida de un git status y por lo tanto será ignorado cuando lancemos un comando git add.

#### Tarea

Construye con nano un fichero en la raíz del repositorio que permita ignorar los ficheros *.tmp.

Comprueba que el filtro construido funciona (crea ficheros con y sin extensión .tmp , intenta agregarlos a *staging* y haz commit).

#### Avanzado

IMPORTANTE: el propio .gitignore debería ser aprobado/*committed* al repositorio para asegurar que las reglas se cumplen en máquinas diferentes, ya que si no, solo se aplicaría a tu repositorio local.

Aún con el .gitignore, ¿existe alguna forma de agregar de forma forzada un tmp?

## Aprobando cambios (Parte I) 9:45 

[Aprobando cambios I](pdfs/Aprobando_cambios.pdf)

### Paso 1 - Git Status

Tal y como se ha discutido en la lección previa, git status nos permite visualizar los cambios en el *working directory* y en la *staging area* comparando con el repositorio.

Dado que el repositorio actual en el que lanzamos git status muestra que un cambio hecho en nuestro *working directory* y tenemos en él un fichero previamente aprobado (por ejemplo hello-world.js), si lo modificamos, y a la vez creamos otro fichero, commited.js, que ni siquiera ha sido movido aún a *staging area*, ¿qué nos mostrará?

#### Tarea

Modificamos fichero “hello-world.js” agregándole un comentario.

Creamos un fichero commited.js

Lanzamos

```sh
git status
```

### Paso 2 - Git Diff

El comando git diff permite comparar cambios en el *working directory* contra una versión previamente aprobada. Por defecto, el comando compara el *working directory* y el commit que llamamos *HEAD* (el más reciente).

Si se desea comparar el *working directory* contra una versión más antigua, entonces podemos proporcionar su *hash_id* como parámetro en la llamada al comando; así: git diff .

Comparar contra *commits* mostrará los cambios en todos los ficheros que se hayan modificado. Si deseamos comparar los cambios en un único fichero, podemos pasar su nombre como parámetro:

```sh
 git diff committed.js
``` 
 
Incluso ambas funcionalidades, así:

```sh
 git diff <commit> committed.js.
```

#### Avanzado

Por defecto, la salida está en formato diff.

By default the output is in the combined diff format. The command git difftool will load an external tool of your choice to view the differences.

En nuestro caso, elegiremos tkdiff, descargándola y colocándola donde se ha indicado arriba.

Si queremos vimdiff:

```sh
git config --global diff.tool vimdiff
```

Si queremos tkdiff:

```sh
git config --global diff.tool vimdiff
```

#### Tarea

Hagamos una prueba modificando un fichero respecto de la versión anterior que esté aprobada.

Ejecutemos:

```sh
git diff
git difftool
```

Y veamos las posibilidades que tiene la herramienta.

### Paso 3 - Git Add

Anteriormente, vimos que podíamos aprobar un cambio mediante *commit* siempre y cuando previamente hubiésemos agregado el archivo al área de preparación (stage) mediante el comando git add .

#### Avanzado

Si renombramos (*mv*) o borramos (*rm*) ficheros, se necesita especificar esos ficheros con un git add para que sean registrados como un cambio. Esto a veces resulta confuso.

De forma alternativa, se puede usar git mv y el comando git rm de git para llevar a cabo la acción sobre el fichero, y además incluir el cambio en la staging area.

#### Tarea

Practicamos agregando cambios con el comando git add

Practicamos haciendo renombrado y renombrado sin “git mv” y sin “git rm”. ¿Qué sucede?

Lo solucionamos con git add.

Ahora repetimos el proceso con git mv y el comando git rm. ¿Qué sucede?

### Paso 4 – Diferencias en estado preparado (Staged)

Una vez que los cambios están en la *staging area* no se mostrarán en la salida de git diff

Por defecto, git diff solo comparará el *working diretory* y no el staging area .

Para comparar cambios en el *staging area* contra el *commit* previo, debemos proporcionar el parámetro git diff —staged . Esto posibilita asegurarnos de que hemos preparado (*staged*) todos nuestros cambios.

#### Tarea

* Lanzamos git rm README.md y efectuamos un commit.

* Ahora lanzar “git diff” y “git diff —staged” y ver si hay diferencia.

* Creamos un archivo README.md con nano y agregamos contenido.

* Posteriormente, hemos de lanzar “git diff” y “git diff —staged” y ver si hay diferencia.

* Ahora lanzamos git add de ese fichero recién creado.

Si lanzamos ahora ambos comandos, ¿hay alguna diferencia?

### Paso 5 - Git Log

El comando git log permite visualizar el histórico del repositorio y el *commit log* .

#### Avanzado

El formato de la salida de log es muy flexible. Por ejemplo para sacar cada *commit* en una única línea, el comando es:

```sh
 git log --pretty=format:"%h %an %ar - %s"
```

También funciona así:

```sh
git log --pretty="%h %an %ar - %s"
```

Podemos encontrar más detalles y opciones usando:

```sh
 git log --help
``` 

#### Tarea

Probar la salida del comando git log agregando las opciones descritas.

### Paso 6 - Git Show

Mientras que git log te dice el autor del commit y el mensaje, para visualizar los cambios efectuados en el *commit* se necesita usar el comando git show .

Al igual que otros comandos, por defecto, “git show” muestra los cambios del *commit* HEAD. Podemos usar el comando git show para visualizar cambios más antiguos.

#### Tarea

Usar git log para obtener varios números de *commit*. Lanzar git show con dos de ellos.

## Aprobando cambios (Parte II) 15:00 

## Trabajo remoto 16:19 

[Trabajo remoto](pdfs/3.3_Trabajando_remotamente.pdf)

En esta lección aprenderemos cómo podemos compartir cambios en nuestro repositorio con otras personas, y combinar sus cambios dentro de nuestro repositorio.

Con Git como DVCS, tenemos nuestro repositorio local conteniendo todos los logs, ficheros y cambios realizados desde que se inicializó el repositorio. Para asegurar que todos están trabajando en la copia más reciente, es necesario compartir los cambios. Cuando compartimos estos cambios con otros repositorios, solo se sincronizarán las diferencias, por lo que es un procedimiento extremadamente rápido.

Paso 1 - Git Remote
Los repositorios remotos permiten compartir cambios desde o hacia nuestro repositorio. Las ubicaciones remotas son generalmente servidores locales, una máquina de un equipo de trabajo o bien un almacén de repositorios en la nube como GitLab o Github.

Los repositorios remotos se añaden usando el comando git remote con un nombre amigable y una ubicación remota; normalmente una conexión HTTPS o SSH (para esto último no hace falta software específico como GitLab).

Ejemplo: https://github.com/sharkdp/bat

El nombre amigable permite referenciar la localización en otros comandos. Nuestro repositorio local puede referenciar múltiples repositorios remotos, dependiendo de nuestras necesidades.

Tarea
Trabajaremos en otro directorio. Crearemos la carpeta scn3 y esa será nuestro working directory.

Agregaremos el repositorio remoto https://github.com/sharkdp/bat usando el comando git remote con el nombre amigable origin.

Formato de llamada:

git remote add origin /s/remote-project/1
git fetch origin
Avanzado
Si usamos git clone que será tratado en una lección futura, cuando se clona el repositorio, se agrega automáticamente como descriptor amigable que lo referencia, el nombre origin.

Paso 2 - Git Push
Cuando estamos listos para compartir nuestros commits, es necesario hacer un push de ellos a un repositorio remoto usando git push. Un flujo de trabajo habitual de GIT sería llevar a cabo múltiples commits pequeños conforme vamos finalizando tareas, y hacerles un push a un repositorio remoto en hitos relevantes, como cuando finalizamos un bloque de trabajo, de manera que aseguramos la sincronización del código dentro de un equipo.

El comando git push se acompaña de dos parámetros. El primero es el nombre amigable del repositorio remoto (normalmente origin). El segundo es el nombre de la rama (normalmente, rama master). Por defecto, todos los repositorios tienen una rama master donde se trabaja con el código.

Tarea
Haremos push de los commits de la rama master a la ubicación remota (origin).

Para este ejercicio, vamos crearnos un usuario en gitlab. Crearemos un nuevo proyecto y nos vincularemos a él. Hacemos un pull. Posteriormente, crearemos un archivo (por ejemplo README2.md), y lo aprobaremos commit en nuestro master. Por último, lo subiremos al repositorio de Gitlab

Paso 3 - Git Pull
El comando git push permite subir los cambios a un repositorio remoto, mientras que git pull funciona de forma inversa. El comando git pull permite sincronizar cambios de un repositorio remoto en nuestra versión local.

Los cambios desde el repositorio remoto son automáticamente fusionados (merge) en la rama en la que estamos trabajando en el momento de lanzar el comando.

Tarea
Crear un nuevo repositorio llamado scn3-pull.
Descargar (pull) los cambios de una ubicación remota https://github.com/sharkdp/bat a nuestra rama master.
Borrar los archivos siguientes appveyor.yml Cargo.lock Cargo.toml LICENSE-APACHE LICENSE-MIT README.md
Agregar un archivo LEEME.txt
Aprobar los cambios.
Lanzar un “ls” para ver los archivos de la rama master.
Hacer un checkout para cambiarnos a origin/master.
Lanzar un “ls” para ver los archivos de la rama origin/master.
Conmutarnos de nuevo a la rama master y volver a lanzar un comando “ls”
En el siguiente paso exploraremos qué cambios se han efectuado.

IMPORTANTE: Podemos crear y cambiar de rama con un mismo comando.

git checkout -b nombre-rama
Esto nos capacita para descargar una versión de repositorio, y luego versionar

Paso 4 - Git Log
Tal y como se ha descrito en la lección previa, podemos usar git log para ver el histórico del repositorio. El comando git show permitirá ver los cambios realizados en cada commit.

En esta prueba, vamos a usar el repositorio anterior, que tenemos vinculado al proyecto BAT y vamos a filtrar los commits que lleven la cadena Fix o fix. Al más reciente de los cuales, le lanzaremos un git show <hashid> para visualizar los cambios.

Avanzado
Usar el modificador –pretty para llevar a cabo la consulta de commits en el repositorio remoto de BAT

## Deshacer cambios 18:19 

[](pdfs/)

## Reparando conflictos de unión con merge 

[](pdfs/)

## Contenido adicional 5   
