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

En esta lección aprenderemos cómo podemos crear ramas en nuestro repositorio. Una rama (branch ) permite trabajar, de forma efectiva, en un working directory completamente nuevo. El resultado es que un único repositorio Git puede tener múltiples versiones diferentes del código base, entre las cuales podemos intercambiarnos sin movernos de directorio.

La rama por defecto en Git se llama master . Las ramas adicionales permiten llevar a cabo las mismas operaciones y comandos que podrías efectuar en la rama master , como cambios de tipo committing , merging y pushing.

Como ramas adicionales, funcionan de la misma manera que master y son ideales para prototipado y experimentos o pruebas que permiten ser fusionadas a la rama master si se decide así.

Cuando conmutamos o nos cambiamos de rama, Git cambia los contenidos del working directory. Esto es muy llamativo y sorprendente las primeras veces que lo usamos. Usando esta funcionalidad, no necesitamos cambiar configuraciones o parámetros para reflejar que estamos en ramas o ubicaciones diferentes.

Paso 1 - Git Branch
Las ramas se crean basándonos en otra rama, generalmente master. El comando:

git branch <new_branch> <starting_branch>
toma una rama existente y crea una rama separada para trabajar en ella. Justo en el punto de lanzar el comando, las dos ramas son idénticas. Para cambiar de una rama a otra, usamos el comando:

git branch <new_branch>
Tarea
Creamos un nuevo repositorio y lo inicializamos.

Vamos a gitlab, creamos un nuevo proyecto de tipo privado, y lo inicializamos con un README.md automático.

Agregamos el origin de nuestro proyecto gitlab y lo descargamos a nuestro master.

Creamos una nueva rama réplica y la llamamos “new_branch”.

Nos cambiamos a ella.

Avanzado
El comando git checkout -b creará y hará checkout de la nueva rama creada; es decir, es lo mismo que un git branch + git checkout

Paso 2 – Listar las ramas
Para listar todas las ramas usamos el comando git branch.

El argumento adicional -a incluirá también las ramas remotas, y el parámetro -v incluirá el mensaje commit de HEAD de la rama. Recomendable usar ambos siempre.

Tarea
Usando la carpeta de proyecto del paso anterior, listar todas las ramas con su último mensaje de commit lanzando git branch

Paso 3 – Hacer fusión (merge) a master
Supongamos que se ha producido un commit a una nueva rama. Para fusionar (merge) dentro de la rama master, deberíamos primero hacer chekout a la rama objetivo (posicionarnos sobre ella), en este caso master, y estando en ella, lanzar un git merge para fusionar los cambios de la nueva rama sobre la rama master.

Ejemplo de llamada:

git merge rama_origen rama_destino_del_merge
Tarea
Usando la carpeta de proyecto de nuestro ejercicio anterior, hacemos checkout a new_branch.

Modifico el archivo README.md, lo llevo a staging y lo apruebo.

Ahora, me cambio a master y fusiono.

Compruebo los cambios. Los apruebo.

Paso 4 - Push Branches
Tal y como hemos visto en pasos anteriores, si queremos subir el contenido de una rama a una ubicación remota, tenemos que usar el comando:

git push <remote_name> <branch_name>
Ejemplo:

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
Tarea
Trabajar en una carpeta de proyecto y subir cambios a gitlab. Comprobar que se suben correctamente.

Paso 5 – Limpiar ramas
Limpiar ramas es importante para borrar ruido y confusión en un proyecto. Para borrar una rama se necesita usar el argumento -d. Por ejemplo:

git branch -d <branch_name>
Tarea
Ahora que hemos fusionado la rama en master en el paso anterior, ya no nos hace falta. Borrémosla para mantener el repositorio limpio y comprensible.

## Experimentando con ramas (Parte II) 3:36 

## Experimentando con ramas (Parte III) 3:25 

## Encontrando errores 9:34 

[](pdfs/)

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
