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

Cuando un directorio es parte de un repositorio, se le llama *Working Directory*. Un directorio de trabajo o *working directory contiene la última versión descargada desde el repositorio junto con cualquier cambio que tenga que ser aprobado. Al estar trabajando en un proyecto, todos los cambios se realizan en el working directory.

Podemos ver los cuales de los ficheros han cambiado en el working directory y qué cambios van a ser aprobados (committed) al repositorio usando el comando git status.

La salida de este comando recibe el nombre de “working tree status“.

Tarea

En nuestro espacio de trabajo, o directorio scn1, creamos un archivo README.md y un par de archivos más.

A continuación, lanzamos el comando git status

Avanzado
Todos los ficheros que creamos en nuestro espacio aparecen como “untracked“ o no considerados por Git mientras no le digamos lo contrario. Los detalles para resolver esto se cubren en el siguiente paso.

Paso 3 - Git Add
Para guardar, o aprobar (commit) ficheros en nuestro repositorio GIT, primero se necesita añadirlos al stagging area (área de preparación). Git tiene tres áreas: un working directory, un staging area, y el propio repositorio en sí (directorio oculto .git). Los usuarios “mueven” (también se refiere a ello como “promueven/promote”) cambios desde el working directory al área de preparación o staging área, antes de aprobarlos/commit hacia el repositorio.

Uno de los enfoques clave con Git consiste en que los commits están concentrados, son pequeños y frecuentes. El área de preparación/staging area ayuda a mantener este flujo de trabajo permitiendo promover solo ciertos ficheros cada vez en lugar de obligar a subir todos los cambios del directorio de trabajo.

Tarea
Dentro del directorio en el que estamos, al que previamente hemos hecho git init, creamos un fichero “hello-world.js” con este contenido:

console.log("Hello World");
Luego, usa el comando git add para agregar hello-world.js a la staging area.

Avanzado
Importante: si hacemos cualquier otro cambio adicional a ese fichero posterior a la ejecución de git add (es decir, después de agregarlo a la staging area), el cambio no se reflejará hasta que no lances git add otra vez.

Protip
Tal y como se describió en el paso 2, el comando git status te permite ver el estado tanto del working directory como de la staging area en cualquier momento.

Paso 4 - Git Commit
Una vez que el fichero ha sido añadido a la satging area, se necesita que sea aprobado (commited) hacia el repositorio. El comando git commit -m “commit message” mueve ficheros desde la staging area o área de preparación hacia el repositorio, y almacena fecha/hora, autor y un mensaje de aprobación que puede usarse para agregar información de contexto adicional a los cambios, como por ejemplo un identificador de error, o número identificador de bug.

Solo los cambios añadidos a la staging area serán aprobados/commited ; cualquier fichero en el working directory que no haya sido añadido con git add (es decir, cualquier fichero no staged), no se incluirá en el commit de cambios.

Tarea
Usamos el editor nano o vim para crear un fichero README2.md

Le agregamos contenido. Lo añadimos a staging area.

Use git commit -m ““ para aprobar el fichero que hemos creado.

Ahora creamos otros dos ficheros. En ambos introducimos contenido.

Agregamos a staging SOLO uno de ellos.

Lanzamos git commit.

Posteriormente, comprobamos que quedan ficheros que no han subido al repositorio.

Avanzado
A cada commit se le asigna un hash SHA-1 que posibilita identificarlo para usos futuros. Obsérvalo.

Paso 5 - Git Ignore
A veces, hay ficheros o directorios que nunca querremos aprobar aunque estén en nuestro working directory , como por ejemplo configuración local de desarrollo. Para ignorar estos ficheros, usamos un fichero .gitignore lal raíz del repositorio.

El fichero .gitignore te permite definir máscaras o wildcards para los ficheros que deseamos ignorar; por ejemplo, el wildcard “.tmp” permitiría ignorar a todos los ficheros con extensión tmp* .

Cualquier fichero que corresponda a un wildcard no será mostrado en la salida de un git status y por lo tanto será ignorado cuando lancemos un comando git add.

Tarea
Construye con nano un fichero en la raíz del repositorio que permita ignorar los ficheros *.tmp.

Comprueba que el filtro construido funciona (crea ficheros con y sin extensión .tmp , intenta agregarlos a staging y haz commit).

Avanzado
IMPORTANTE: el propio .gitignore debería ser aprobado/committed al repositorio para asegurar que las reglas se cumplen en máquinas diferentes, ya que si no, solo se aplicaría a tu repositorio local.

Aún con el .gitignore, ¿existe alguna forma de agregar de forma forzada un tmp?

 

## Aprobando cambios (Parte I) 9:45 

[](pdfs/)

## Aprobando cambios (Parte II) 15:00 

[](pdfs/)

## Trabajo remoto 16:19 

[](pdfs/)

## Deshacer cambios 18:19 

[](pdfs/)

## Reparando conflictos de unión con merge 

[](pdfs/)

## Contenido adicional 5   
