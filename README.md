# Curso de _Git_ & _GitHub_

https://jonmircha.com/git

https://www.youtube.com/watch?v=suzMNqDQiyU&t=13s&ab_channel=jonmircha


## Para repositorios nuevos

git init
git add .
git commit -m "Primer commit"
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main
Para repositorios existentes
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main

## Para reemplazar la rama master por main en GitHub

## Paso 1
### Crea la rama local main y pásale el historial de la rama master
git branch -m master main


## Paso 2
### Haz un push de la nueva rama local main en el repositorio remoto de GitHub
git push -u origin main


## Paso 3
### Cambia el HEAD actual a la rama main
git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main
## Paso 4
### Cambia la rama default de master a main en tu repositorio de GitHub. 

## Paso 5
### Elimina la rama master del repositorio remoto
git push origin --delete master

## Para reemplazar la rama master por main en Git
git config --global init.defaultBranch main

## Para sacar la ayuda

### Ayuda en la terminal
git "comando" -h
### Ayuda en el navegador
git help "comando"


## Ignorar archivos

En el archivo **.gitignore** incluimos todo lo que NO queramos incluir en nuestro repositorio. Lo podemos crear manualmente o con gitignore.io.

### Rsto es un comentario (Dentro del archivo gitignore)
archivo.ext
carpeta
/archivo_desde_raiz.ext
### Ignorar todos los archivos que terminen en .log
*.log
### Excepto production.log
!production.log
### Ignorar los archivos terminados en .txt dentro de la carpeta doc,
### pero no en sus subcarpetas
doc/*.txt
### Ignorar todos los archivos terminados en .txt dentro de la carpeta doc
### y también en sus subcarpetas
doc/**/*.txt


## Clonar repositorios

### Siempre terminado en **.git**
git clone https://github.com/usuario/repositorio.git


## Manejo de ramas (branches)

### Crear rama
git branch nombre-rama

### Cambiar de rama
git checkout nombre-rama

### Crear una rama y cambiarte a ella
git checkout -b rama

### Eliminar rama
git branch -d nombre-rama

### Eliminar ramas remotas
git push origin --delete nombre-rama

#eliminar rama (forzado)
git branch -D nombre-rama

### Listar todas las ramas del repositorio
git branch

### Lista ramas no fusionadas a la rama actual
git branch --no-merged

### Lista ramas fusionadas a la rama actual
git branch --merged

### Rebasar ramas
git checkout rama-secundaria
git rebase rama-principal

### Si es la primera vez que hago un push a una rama nueva (crea la rama en el remoto y hace el push)
git push -u origin "nombre-rama"

### Borro la rama en el repositorio remoto
git push origin --delete "nombre-rama"

**Cuando creas una rama, la rama nueva toma como referencia el contendio desde la rama donde saltas**


## Fusiones
Une dos ramas. Para hacer una fusión necesitamos:

Situarnos en la rama que se quedará con el contenido fusionado.
Fusionar.
Cuando se fusionan ramas se pueden dar 2 resultados diferentes:

Fast-Forward: La fusión se hace automática, no hay conflictos por resolver.
Manual Merge: La fusión hay que hacerla manual, para resolver conflictos de duplicación de contenido.

### Nos cambiamos a la rama principal que quedará de la fusión
git checkout rama-principal

### Ejecutamos el comando merge con la rama secundaria a fusionar
git merge rama-secundaria



### Cambios
Puedes agregar modificaciones al último cambio

## Sin editar el mensaje del último commit
git commit --amend --no-edit
{
    1- "Agrego el contenido que falto"
    2- git commit --amend --no-edit
    3- git add .
    4- git commit --amend --no-edit (Aca ya estaria hecho, luego se puede hacer el push)
}

## Editando el mensaje del último commit
git commit --amend -m "nuevo mensaje para el último commit"

## Eliminar el último commit
git reset --hard HEAD~1

Podemos desplazarnos en el historial del repositorio hacia atrás o adelante en cambios o ramas , sin afectar el repositorio como tal.

## Cambiar a una rama
git checkout nombre-rama

## Cambiar a un commit en particular
git checkout id-commit



## Registro del historial

### git log nos permite conocer todo el historial de un proyecto, con la información de la fecha, el autor y id de cada cambio.
git log

### muestra en una sola línea por cambio
git log --oneline

### guarda el log en la ruta y archivo que especifiquemos
git log > commits.txt

### muestra el historial con el formato que indicamos
git log --pretty=format:"%h - %an, %ar : %s"

### cambiamos la n por cualquier número entero y mostrará los n cambios recientes
git log -n

### muestra los cambios realizados después de la fecha especificada
git log --after="2019-07-07 00:00:00"

### muestra los cambios realizados antes de la fecha especificada
git log --before="2019-07-08 00:00:00"

### muestra los cambios realizados en el rango de fecha especificado
git log --after="2019-07-07 00:00:00" --before="2019-07-08 00:00:00"

### muestra una gráfica del historial de cambios, rama y fusiones
git log --oneline --graph --all

### muestra todo el registro de acciones del log
### incluyendo inserciones, cambios, eliminaciones, fusiones, etc.
git reflog

### diferencias entre el Working Directory y el Staging Area
git diff



## Reseteo del historial
Podemos eliminar el historial de cambios del proyecto hacia adelante con respecto de un punto de referencia.

### Nos muestra el listado de archivos nuevos (untracked), borrados o editados
git status

### Borra HEAD
git reset --soft

### Borra HEAD y Staging
git reset --mixed

### Borra todo: HEAD, Staging y Working Directory
git reset --hard

### Deshace todos los cambios después del commit indicado, preservando los cambios localmente
git reset id-commit

### Desecha todo el historial y regresa al commit especificado
git reset --hard id-commit

































