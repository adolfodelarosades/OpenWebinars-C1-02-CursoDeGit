2. Herramientas de trabajo 12m
   * Instalación y configuración 7:15 
   * Servidor GIT básico e introducción a GitLab 4:57 
   * Contenido adicional 1
   
   
## Instalación y configuración 7:15 

[Instalación y configuración](pdfs/Herrramientas_de_trabajo.pdf)

### Descarga de GIT

https://github.com/git-for-windows/git/releases/download/v2.18.0.windows.1/Git-2.18.0-32-bit.exe

### Descarga de TkDIFF

http://www.posoft.de/html/tkdiffMain.html

Por defecto, tenemos vimdiff en una distro de GIT para las diferencias de ficheros, pero si este binario lo metemos en:

```sh
c:\archivosdeprograma\git\usr\bin\tkdiff
```

### Configuración

```sh
git config —global user.name “TU NOMBRE”
git config —global user.email tunombre@tudominio.com
git config —global diff.tool vimdiff
git config —global diff.tool tkdiff
git config —global credential.helper manager
```

En un windows si trabajamos en proyectos compartidos (LF a CRLF)

```sh
git config —global core.autocrlf true
```

En un linux, para que haga lo contrario (LF a CRLF):

```sh
git config —global core.autocrlf input
```

Dejarlo como está, sin alterar nada (para proyectos en los que todos tendremos el mismo SO)

```sh
git config —global core.autocrlf false
```

## Servidor GIT básico e introducción a GitLab 4:57 

## Contenido adicional 1   
