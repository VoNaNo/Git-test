git init
- Para iniciar, empezar a usar git en el proyecto

git help ; git help atributo cómo (add, status...) "

git status
- Para ver el estado de los archivos, por si falta agregar alguno.

---------------> git-add

git add . ; git add -a
- Para agregar los archivos antes de guardarlos en un commit.

---------------> git-commit

git commit -m " Description the commit "
- Para guardar el progreso

git commit --amend -m "CAMBIAR LA DESCRIPCION DEL ULTIMO COMMIT"
- Para cambiar la descripcion del ultimo commit que se creo

---------------> git-log

git log
- Para ver todos los commits que se hayan creado con sus codigos hash.

git log > commits.text
- Para crear un block de notas con todos los commits registrados.

---------------> git-reset

* Tipos de (git reset) {
---
    [low] git reset --soft {
        Es git reset más sencillo y que no toca el "working area", No toca el codigo.

        example: git reset --soft CODIGO-HASD-DEL-COMMIT
        (El commit seleccionado sera borrado sin tocar el codigo)
    }
---
    [normal] git reset --mixed {
        Este git reset borra el "Staging area", sin tocar el "Working area".
    } (no se usa mucho)
---
    [hard] git reset --hard {
        Este git reset borra absolutamente todo (codigo) lo que hay en el commit.

        example: git reset --hard CODIGO-HASD-DEL-COMMIT
        (Regresamos al commit inicial "primer-commit", borrando los otros commits junto con el codigo de los mismos)
    }
}

---------------> git-checkout

-> Commits

git checkout Codigo hash del commit
- Para viajar a travez de commits

git checkout master
- Para ir al ultimo commit creado

git checkout sirve para viajar entre commits y branchs

-> Branchs

git checkout NOMBRE_DE_LA_BRANCH
- Para ir a la rama seleccionada

git checkout -b NOMBRE_DE_LA_BRANCH
- Para crear una rama y movernos a la misma de una vez.

---------------> git-branch {Ramas del proyecto}

- "Head" es el commit en el que nos encontramos

Ramas(branch): Lineas de tiempo
rama master > rama principal del proyecto

git branch
- Para ver las ramas que tengamos disponibles

git branch NOMBRE_DE_LA_BRANCH
- Para crear una rama

git branch -a
- Para ver las ramas ocultas

git branch -D NOMBRE_DE_LA_BRANCH
- Para eliminar ramas

(Cuando se crea una rama, se crear a partir de la rama 
en la que estabamos al crear dicha rama; por lo tanto,
iniciara con los mismos commits de la rama anterior)

---------------> git-merge {fusionando branchs}

1) primero hay que ubicarse en la rama que va a absorver
2) insertar el comando:
 git merge NOMBRE_DE_LA_BRANCH_QUE_SERA_ABSORVIDA

Al hacer una fusion pueden salir dos tipos de mensajes:
    a) fast-forward: simple y automatico
    b) manual merge: largo y manual

---------------> git-remote | git-push {Para enlazar y subir a github}

git remote add origin ENLACE
- Para enlazar un proyecto con un repositorio de github

git remote remove origin
- Para desenlazar el proyecto del repositorio

git remote -v
- Para ver si esta enlazado

git push origin NOMBRE_DE_LA_BRANCH
- Manda nuestros cambios(commits) al repositorio de github

git push origin NOMBRE_DE_LA_BRANCH -f
- Para forzar los cambios en el repositorio, generalmente se usa cuando cambiamos el nombre de un commit de forma local y lo queremos actualizar en el repositorio remoto.

---------------> git-tag {Para colorcar versiones}

    * Tags anotadas
- Las tags anotadas son almacenadas como abjetos completos dentro de la base de git y contienen más informacion.

        git tag -a v1.0 -m "mensaje"
    - La version se añadira al ultimo commit que haya sido creado

        git tag -a v1.0 -m "mensaje" CODIGO_SHA_DEL_COMMIT
    - Para añadir la version a un commit en especifico

    * Tags ligeras
- Son otra forma de crear tags, más simples y con poca informacion.

        git tag v1.0

    git push origin v1.0

    git push origin --tags


---------------> git-fetch {Trabajar en equipo}
git fetch origin
- fetch es para copiar o bajar los cambios del commit 

git merge origin/master