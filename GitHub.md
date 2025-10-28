# Práctica guiada GitHub

## Creación del directorio y de sus archivos

* mkdir prueba_git --> **Creación del directorio**
* cd prueba_git --> **Moverse al directorio**
* nano texto.txt --> **Creación del primer archivo**
* nano script.sh --> **Creación del segundo archivo**


## 1. Inicialización (init y status)

* git init --> **Creación del repositorio vacío**
* **Salida por pantalla:**
```bash
    Initialized empty Git repository in C:/Users/Usuario/prueba_git/.git/
```
* git status --> **Ver estado del repositorio**
* **Salida por pantalla:**
```bash
    On branch master

    No commits yet

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
            script.sh
            texto.txt

    nothing added to commit but untracked files present (use "git add" to track)
```
* git branch -m main --> **Cambiar de master a main**

**Inicialmente:**
```bash 
    Usuario@DESKTOP-UVIGJE8 MINGW64 ~/prueba_git (master)
```
**Posteriormente:**
```bash 
    Usuario@DESKTOP-UVIGJE8 MINGW64 ~/prueba_git (main)
```
* git branch -m master --> **Restaurarlo a master**


## 2. Añadiendo archivos (add y commit)

* git add script.sh --> **Añadir el archivo al repositorio local**
* git status --> **Volver a ver el estado del repositorio local**

**Salida por pantalla:**
```bash
    On branch master

    No commits yet

    Changes to be committed:
    (use "git rm --cached <file>..." to unstage)
            new file:   script.sh

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
            texto.txt
```
Se puede ver que *texto.txt* aún no ha sido añadido al repositorio, en cambio *script.sh* sí

* git commit -m "Confirmación inicial" --> **Comentario para guardar los cambios dentro del repositorio**

**Salida por pantalla:**
```bash
    $ git commit -m "Confirmación inicial"
    [master (root-commit) c118801] Confirmación inicial
    1 file changed, 2 insertions(+)
    create mode 100644 script.sh
```

* git status --> **Volver a ver el estado del repositorio local**
**Salida por pantalla:**
```bash
    On branch master
    Untracked files:
        (use "git add <file>..." to include in what will be committed)
            texto.txt

    nothing added to commit but untracked files present (use "git add" to track)
```
Se nos indica que aún no se ha hecho un ***git add*** de *texto.txt*, por lo que no está añadido al repositorio

**Procedemos a añadir *texto.txt***

* git add texto.txt
* git commit -m “Añadido archivo texto.txt”
* git status

**Salida por pantalla:**
```bash
    On branch master
    nothing to commit, working tree clean
```
Al hacer el ***git status*** se nos indica que ya no hay nada pendiente que añadir al repositorio local


## 3. Modificando archivos

* nano texto.txt --> **Modificar el archivo**
* git status

**Salida por pantalla:**
```bash
    On branch master
    Changes not staged for commit:
        (use "git add <file>..." to update what will be committed)
        (use "git restore <file>..." to discard changes in working directory)
            modified:   texto.txt

    no changes added to commit (use "git add" and/or "git commit -a")
```
Se nos indica que como el archivo *texto.txt* ha sido modificado hay que volver a añadirlo al repositorio

* git add texto.txt --> **Añadir el archivo**
* git status

**Salida por pantalla:**
```bash
    On branch master
    Changes to be committed:
        (use "git restore --staged <file>..." to unstage)
            modified:   texto.txt
```
Nos pide hacer el ***commit*** para guardar los cambios 

**Se vuelve a modificar el archivo y a hacer el ***git status*****

* nano texto.txt --> **Modificar el archivo**
* git status

**Salida por pantalla:**
```bash
    On branch master
    Changes to be committed:
        (use "git restore --staged <file>..." to unstage)
            modified:   texto.txt

    Changes not staged for commit:
        (use "git add <file>..." to update what will be committed)
        (use "git restore <file>..." to discard changes in working directory)
            modified:   texto.txt
```
Se nos inica que el archivo está preparado para el ***commit**, pero si lo hacemos no se guardaran los últimos cambios realizados, se añadirán los anteriores

**Para añadir los últimos cambios realizados**

* git add texto.txt
* git commit -m “Ampliada la explicación del texto”
* git status

**Salida por pantalla:**
```bash
    On branch master
    nothing to commit, working tree clean
```
Ahora sí se nos indica que todos los cambios están añadidos al repositorio local


