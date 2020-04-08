# 4. Flujos de trabajo 58m
   * Experimentando con ramas (Parte I) 6:24 
   * Experimentando con ramas (Parte II) 3:36 
   * Experimentando con ramas (Parte III) 3:25 
   * Encontrando errores 9:34 
   * Git Blame 4:39 
   * Siendo "quisquilloso" con Git 6:37 
   * Reescribir la historia de un proyecto con Rebase 7:28 
   * Etiquetas 5:13 
   * Moverse adelante y atrás entre estados de un repositorio git 7:43 
   * Git Stash 3:46 
   * Contenido adicional 6
   
## Experimentando con ramas (Parte I) 6:24

[Experimentando con ramas](pdfs/Experimentando_con_ramas.pdf)

En esta lección aprenderemos cómo podemos crear ramas en nuestro repositorio. Una rama (*branch*) permite trabajar, de forma efectiva, en un *working directory* completamente nuevo. El resultado es que un único repositorio Git puede tener múltiples versiones diferentes del código base, entre las cuales podemos intercambiarnos sin movernos de directorio.

La rama por defecto en Git se llama *master*. Las ramas adicionales permiten llevar a cabo las mismas operaciones y comandos que podrías efectuar en la rama *master*, como cambios de tipo *committing*, *merging* y *pushing*.

Como ramas adicionales, funcionan de la misma manera que *master* y son ideales para prototipado y experimentos o pruebas que permiten ser fusionadas a la rama *master* si se decide así.

Cuando conmutamos o nos cambiamos de rama, Git cambia los contenidos del *working directory*. Esto es muy llamativo y sorprendente las primeras veces que lo usamos. Usando esta funcionalidad, no necesitamos cambiar configuraciones o parámetros para reflejar que estamos en ramas o ubicaciones diferentes.

### Paso 1 - Git Branch

Las ramas se crean basándonos en otra rama, generalmente *master*. El comando:

```sh
git branch <new_branch> <starting_branch>
```

toma una rama existente y crea una rama separada para trabajar en ella. Justo en el punto de lanzar el comando, las dos ramas son idénticas. Para cambiar de una rama a otra, usamos el comando:

```sh
git branch <new_branch>
```

#### Tarea

Creamos un nuevo repositorio y lo inicializamos.

Vamos a gitlab, creamos un nuevo proyecto de tipo privado, y lo inicializamos con un README.md automático.

Agregamos el origin de nuestro proyecto gitlab y lo descargamos a nuestro master.

Creamos una nueva rama réplica y la llamamos “new_branch”.

Nos cambiamos a ella.

#### Avanzado

El comando *git checkout -b* creará y hará *checkout* de la nueva rama creada; es decir, es lo mismo que un *git branch + git checkout*

### Paso 2 – Listar las ramas

Para listar todas las ramas usamos el comando *git branch*.

El argumento adicional *-a* incluirá también las ramas remotas, y el parámetro *-v* incluirá el mensaje *commit* de HEAD de la rama. Recomendable usar ambos siempre.

#### Tarea

Usando la carpeta de proyecto del paso anterior, listar todas las ramas con su último mensaje de *commit* lanzando *git branch*

### Paso 3 – Hacer fusión (merge) a master

Supongamos que se ha producido un *commit* a una nueva rama. Para fusionar (*merge*) dentro de la rama *master*, deberíamos primero hacer *chekout* a la rama objetivo (posicionarnos sobre ella), en este caso master, y estando en ella, lanzar un *git merge* para fusionar los cambios de la nueva rama sobre la rama *master*.

Ejemplo de llamada:

```sh
git merge rama_origen rama_destino_del_merge
```

#### Tarea

Usando la carpeta de proyecto de nuestro ejercicio anterior, hacemos checkout a new_branch.

Modifico el archivo README.md, lo llevo a staging y lo apruebo.

Ahora, me cambio a master y fusiono.

Compruebo los cambios. Los apruebo.

### Paso 4 - Push Branches

Tal y como hemos visto en pasos anteriores, si queremos subir el contenido de una rama a una ubicación remota, tenemos que usar el comando:

```sh
git push <remote_name> <branch_name>
```

Ejemplo:

```sh
$ git push origin master
warning: redirecting to https://gitlab.com/juancarlos.rubio/ej06-branches.git/
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 2 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 340 bytes | 340.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://gitlab.com/juancarlos.rubio/ej06-branches
   14a0d49..31980bc  master -> master
```

#### Tarea

Trabajar en una carpeta de proyecto y subir cambios a gitlab. Comprobar que se suben correctamente.

### Paso 5 – Limpiar ramas

Limpiar ramas es importante para borrar ruido y confusión en un proyecto. Para borrar una rama se necesita usar el argumento *-d*. Por ejemplo:

```sh
git branch -d <branch_name>
```

#### Tarea

Ahora que hemos fusionado la rama en *master* en el paso anterior, ya no nos hace falta. Borrémosla para mantener el repositorio limpio y comprensible.

## Experimentando con ramas (Parte II) 3:36 

## Experimentando con ramas (Parte III) 3:25 

## Encontrando errores 9:34 

[Encontrando errores](pdfs/Encontrando_errores.pdf)

Los errores de software o bugs han constituido un problema desde que existe el software. Puesto que Git guarda todos los cambios en el repositorio, se convierte en una gran fuente de información y en una herramienta de diagnóstico cuando tratamos de identificar cómo llegaron a introducirse los problemas de código.

En esta lección exploraremos diferentes formas para encontrar en cuál commit se introdujo un determinado problema.

### Paso 1 - Git Diff entre dos Commits

El comando *git diff* es el modo más simple de comparar qué ha cambiado entre commits. Mostrará las diferencias entre dos commits.

##### Ejemplo:

Podemos visualizar las diferencias entre dos *commits* visualizando los *hash-id’s*

```sh
$ git diff HEAD~2 HEAD
diff --git a/README.md b/README.md
index 77927c0..c8831b2 100644
--- a/README.md
+++ b/README.md
@@ -1,2 +1,3 @@
 # ej06-branches

+## Y agrego este subtitulo al fichero README.md
diff --git a/codigo.js b/codigo.js
new file mode 100644
index 0000000..cac68b2
--- /dev/null
+++ b/codigo.js
@@ -0,0 +1 @@
+mas codigo
```

Posibilidades comunes:

**git diff** muestra las diferencias entre el *working directory* y el *commit*. En este caso, el commit es HEAD, así que mostraría los cambios que hemos hecho desde nuestro último *commit*. Incluyendo los ficheros *untracked* o los ficheros *unstaged*, es decir, nuestro working directory.

**git diff —cached** muestra las diferencias solo entre nuestro *staged changes* y el estado almacenado en él. Es decir, que si no he hecho “git add” a ciertos ficheros que haya modificado, no se analizan las diferencias entre ellos y el *commit*.

### Paso 2 - Git Log

El comando *git log* permite ver los mensajes de *commit* pero por defecto no muestra una salida de lo que en realidad se modificó. Afortunadamente, el comando es extremadamente flexible y permite opciones adicionales que proporcionan visualizaciones útiles de lo sucedido en el histórico del repositorio.

#### Ejemplos:

Para ver una introducción o entradilla de información de los *commits* en una vista reducida, podemos usar el comando git log —oneline

La salida de información del *commit* con las diferencias que se hayan producido se puede lograr agregando el parámetro *-p* , lanzándolo así: git log -p

Esto mostraría todo el repositorio al completo… Demasiada información. Podemos delimitar un poco usando otro parámetro: *-n* . Con él, especificamos un límite de *commits* a mostrar desde HEAD.

Por ejemplo; el comando:

```sh
git log -p -n 2
```

mostraría HEAD y HEAD~1.

Si conocemos el periodo de tiempo o fechas que queremos consultar (útil para localizar versiones con garantías de estar libres de fallos, por ejemplo) podemos usar:

```sh
 *--since="2 weeks ago"* y --until="1 day ago".
``` 

(admite *“1 hour ago”* y otras variantes en inglés).

Y como en otros comandos Git, podemos obtener un rango de salida de *commits* usando intervalos como por ejemplo HEAD…HEAD~1

Podemos localizar patrones en el asunto del *commit* con el parámetro *grep*:

Ejemplo:

```sh
git log --grep="Initial"
```

mostraría la salida de commits que incluyesen la cadena “Initial” en su mensaje. También podemos usar un pipeline y redirigirlo al comando unix *grep* normalmente. Esto puede ser muy útil cuando tratamos de localizar números de registro de bug (*bug-tracking numbers*).

#### Avanzado

Tal y como hemos visto, el log puede ser ruidoso. Probemos las posibilidades del comando *git log* agregándole el parámetro *-m* y juguemos con las consultas para obtener resultados deseados.

### Paso 3 - Git Blame

Disponer de una cultura de “culpa” (*blame*) no es deseable, aunque puede ser útil para conocer quién trabajó en ciertas secciones del fichero para ayudar a realizar mejoras en el futuro.

En estas circunstancias es donde *git blame* puede ser de utilidad.

git blame muestra la revisión y el autor que modificó cada línea de un fichero.

##### Ejemplo:

Lanzar *git blame* sobre un fichero mostrará quién tocó cada línea.

```sh
git blame list.html
```

Y si conocemos las líneas que pueden estar afectadas, podemos filtrar el rango de líneas de salida:

```sh
git blame -L 6,8 list.html
industriasi@alvarez MINGW32 ~/ownCloud/temporal/git/code/ej06-branches (maste
$ git blame README.md
^14a0d49 (Juan Carlos Rubio 2018-09-06 16:38:29 +0000 1) # ej06-branches
^14a0d49 (Juan Carlos Rubio 2018-09-06 16:38:29 +0000 2)
31980bcd (Juan Carlos Rubio 2018-09-06 19:00:02 +0200 3) ## Y agrego este subtitulo al fichero README.md
```

#### Tarea

Probemos la ejecución y las posibilidades de estas herramientas.

Creamos un nuevo proyecto. Inicializamos. Nos vinculamos a https://github.com/sharkdp/bat

Hacemos pull. Buscamos logar los últimos 15 cambios.

Lanzamos *blame* sobre el fichero *src/output.rs*

## Git Blame 4:39 

[](pdfs/)

## Siendo "quisquilloso" con Git 6:37 

[](pdfs/)

## Reescribir la historia de un proyecto con Rebase 7:28 

[](pdfs/)

## Etiquetas 5:13 

[](pdfs/)

## Moverse adelante y atrás entre estados de un repositorio git 7:43 

[](pdfs/)

## Git Stash 3:46 

[](pdfs/)

## Contenido adicional 6   
