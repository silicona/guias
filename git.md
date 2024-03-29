# GIT

## Comandos

  [Enlace Guia](https://git-scm.com/book/es/v1/Fundamentos-de-Git-Deshaciendo-cosas)

### Globales

  - Obtener usuario o email
    - `git config --global user.name`
    - `git config --global user.email`
  - Configura el usuario o el email
    - `git config --global user.name 'usuario'`
    - `git config --global user.email 'usuario@dominio.com'`
  - Configura el modo de push (más abajo): `git config --global push.default matching/simple`
  - Configura un alias para los comandos: `git config --global alias.co checkout`
  - Activa los cambios en el bash
    - `source <archivo>`
    - `source ~/.bash_profile`

### Repositorios

  | Estado								| Acción				| Estado		| Accion 				| Estado 			| Accion 		| Estado 				|
  |:---------------------:|:-------------:|:---------:|:-------------:|:-----------:|:---------:|:-------------:|
  | Untracked - Unstaged	| `git add -A`	| Staged 		| `git commit`	| Repo local	| `git push`| Repo remoto		|

  - Inicia un repositorio: `git init` (en directorio raiz del proyecto)
  - Estado de los branches: `git status`
  - Añadir archivos sin seguimiento
    - `git add -A`
    - `git add .`
  - Confirma los archivos para enviar
    - `git commit -m 'Mensaje del commit'`
    - `git commit -a` (solo confirma archivos con seguimiento)
  - Eliminar staged (antes de commit)
    - `git reset`

  - Informe de commits
    - `git log` (da el SHA de cada commit)
    - `git log -p` (log con diff)

  - Compara el ultimo commit con la nueva version
    - `git diff` (cambios NO añadidos)
    - `git diff --staged` (cambios no confirmados)
    - `git diff master` (diff acepta dos argumentos; al dejar uno vacio, coge la rama actual para la comparación con master)

  - Eliminar archivos demasiado grandes
    - [Enlace a doc](https://help.github.com/articles/removing-sensitive-data-from-a-repository/)
    - Ejecutar en consola: `git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA' --prune-empty --tag-name-filter cat -- --all`
    - Incluir los archivos en .gitignore
    - Ejecutar en consola: `git push origin --force --all`

### Creando un repositorio

  - Añadir origen remoto: `git remote add origin https://.../xxxx.git`
  - Añadir repositorio local al remoto:
    - `git push <repo remoto> <branch>`
    - `git push -u origin master` (-u permite realizar pulls)
    - Modos de push:
      * **matching** - Sube el local a las ramas remotas con el mismo nombre
      * **simple** - Sube el local a la rama remota de git push
  - Obtener desde el repositorio remoto: `git pull origin master`
  - Clona el repositorio remoto en el local (carpeta incluida): `git clone https://..../xxx.git`

#### Nuevo repositorio desde comandos

    git init
    git add README.md
    git commit -m "first commit"
    git branch -M main
    git remote add origin https://github.com/silicona/aplicacion_banco_java.git
    git push -u origin main

#### Repositorio existente desde comandos

    git remote add origin https://github.com/silicona/aplicacion_banco_java.git
    git branch -M main
    git push -u origin main

#### Importar desde otro repositorio

Git soporta código de proyectos Subversion, Mercurial or TFS.

### Branching y Merging

  - Crear nueva rama y cambia a ella: `git checkout -b "nombre de rama"`
  - Cambia a una rama: `git checkout master` (vuelve al master para el merge)
  - Se junta la rama con el master: `git merge "nombre de rama"`
  - Obtiene los branchs remotos: `git fetch origin [nombre de branch remoto]`
  - Merge una branch remota en el master local: `git merge origin/[nombre de branch remoto]`
  - Obtener las ramas existentes y la actual: `git branch`
  - Borra una rama que no haya sido merged con el master: `git branch -D "nombre de rama"`
  - Devuelve el proyecto al inicio de la rama o el master: `git checkout -f`
  - Inicia Detaiched Head (permite crear nuevos commit y ramas sin molestar a los actuales): `git checkout <SHA de commit>`

## Paginas estáticas de Github

Crear la rama gh-pages
  - `git checkout -b "gh-pages"`

Acceder a la página por el navegador
  - https://[usuario Github].github.io/[nombre de repositorio]
  - [Ver página del Repositorio sitio_html](https://silicona.github.io/sitio_html/index)
  - [Ver página del Repositorio sitioweb](https://silicona.github.io/sitioweb)

## Recuperando logs

  - Historico: `git hist`
  - Mostrar las dos últimas entradas del historico: `git log -2`
  - Mostrar las n últimas entradas del historico: `git log -n`
  - Mostrar las diferencias entre logs por palabras
    - `git log -p --word-diff`
    - `git log -p --word-diff {+palabra_añadida+} [-palabra_eliminada-]`
  - Mostrar estadisticas: `git log --stat`


  | Opción        | Descripción |
  |:-------------:|:-----------:|
  | -p            | Muestra el parche introducido en cada confirmación. |
  | --word-diff   | Muestra el parche en formato de una palabra. |
  | --stat        | Muestra estadísticas sobre los archivos modificados en cada confirmación. |
  | --shortstat   | Muestra solamente la línea de resumen de la opción --stat. |
  | --name-only   | Muestra la lista de archivos afectados. |
  | --name-status | Muestra la lista de archivos afectados, indicando además si fueron añadidos, modificados o eliminados. |
  | --abbrev-commit | Muestra solamente los primeros caracteres de la suma SHA-1, en vez de los 40 caracteres de que se compone. |
  | --relative-date | Muestra la fecha en formato relativo (por ejemplo, “2 weeks ago” (“hace 2 semanas”)) en lugar del formato completo. |
  | --graph       | Muestra un gráfico ASCII con la historia de ramificaciones y uniones. |
  | --pretty      | Muestra las confirmaciones usando un formato alternativo. Posibles opciones son oneline, short, full, fuller y format (mediante el cual puedes especificar tu propio formato). |
  | --oneline     | Un cómodo acortamiento de la opción --pretty=oneline --abbrev-commit. |
  | --since=n.temp | Muestra desde hace un tiempo: n = entero y temp = (days, weeks, months, years) |
  | -(n)          | Muestra solamente las últimas n confirmaciones |
  | --since, --after  | Muestra aquellas confirmaciones hechas después de la fecha especificada. (--since=n.temp) n = entero y temp = (days, weeks, months, years) |
  | --until, --before | Muestra aquellas confirmaciones hechas antes de la fecha especificada. |
  | --author      | Muestra sólo aquellas confirmaciones cuyo autor coincide con la cadena especificada. |
  | --committer   | Muestra sólo aquellas confirmaciones cuyo confirmador coincide con la cadena especificada. |


## Gitk

Entorno visual para Git, incorporado. En consola: `gitk`


















