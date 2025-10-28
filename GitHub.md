# Práctica guiada Git/GitHub

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
Obsesrvamos que los dos archivos aún no han sido añadidos al repositorio local

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


## 4. Información (git show y git log)

* git show --> **Mostrar la información sobre la última versión que se ha guardado**

**Salida por pantalla:**
```bash
    commit ac4508c0c1b4ce946d17a486835a992cb82ca3af (HEAD -> master)
    Author: joeloto <joelme.0808@gmail.com>
    Date:   Sat Oct 25 18:46:23 2025 +0200

        Ampliada la explicación del texto

    diff --git a/texto.txt b/texto.txt
    index 1c24992..686418d 100644
    --- a/texto.txt
    +++ b/texto.txt
    @@ -1,3 +1,6 @@
    uno
    dos
    tres
    +cuatro
    +cinco
    +
```
Podemos ver como, efectivamente, el último ***commit*** realizado es el de “Ampliada la explicación del texto”

* git log --> **Mostrar todo los cambios que se han hecho en el repositorio local con sus fechas**

**Salida por pantalla:**
```bash
        commit ac4508c0c1b4ce946d17a486835a992cb82ca3af (HEAD -> master)
    Author: joeloto <joelme.0808@gmail.com>
    Date:   Sat Oct 25 18:46:23 2025 +0200

        Ampliada la explicación del texto

    commit 9f78fba6e8bb41f81c33378356ec2cae0e2efa9b
    Author: joeloto <joelme.0808@gmail.com>
    Date:   Sat Oct 25 18:26:35 2025 +0200

        Añadido archivo texto.txt

    commit c1188013892b3805a1586145d97b9b1eabd4d3fe
    Author: joeloto <joelme.0808@gmail.com>
    Date:   Sat Oct 25 18:19:19 2025 +0200

        Confirmación inicial
```
Podemos observar todos los ***commit*** realizados de más reciente a más antiguo 


## 5. Diferencias (git diff)

* git diff --> **Mostrar las diferencias del archivo qeu se acaba de modificar con el guardado en la última versión del repositorio**

**Salida por pantalla:**
```bash
    diff --git a/texto.txt b/texto.txt
    index 686418d..e623239 100644
    --- a/texto.txt
    +++ b/texto.txt
    @@ -1,6 +1,5 @@
    uno
    dos
    -tres
    cuatro
    cinco
    -
    +seis
```
Podemos observar los cambios realizados en el archivo *texto.txt*, la eleminiación de la línea 'tres' y la inclusión de la línea 'seis'

* git commit -a -m "Probando diff" --> **Mostrar que se añadido o eliminado comparando la primera versión guardada del archivo con la más reciente**

**Salida por pantalla:**
```bash
        [master 31edf3e] Probando diff
    1 file changed, 1 insertion(+), 2 deletions(-)
```


## 6. Ignorar archivos (.gitignore)

Creamos los nuevos archivos:

* nano .gitignore --> se encargará de ignorar ciertos archivos a la hora de hacer el ***git status***
* nano importante~ --> **No será ignorado**
* nano temporal~ --> **Sí será ignorado**

**Salida por pantalla del *git status*:**
```bash
    On branch master
    Untracked files:
    (use "git add <file>..." to include in what will be committed)
            .gitignore
            Hola.java
            importante~

    nothing added to commit but untracked files present (use "git add" to track)
```
El archivo *temporal~* fue ignorado

**Después de hacer el *git add* y el *git status* se nos mostrará:**
```bash
    [master 236cab9] Añadidos fuentes en java y archivos importantes
    3 files changed, 12 insertions(+)
    create mode 100644 .gitignore
    create mode 100644 Hola.java
    create mode 100644 importante~
```
**El *git status* nos indicará que todo está perfecto:**
```bash
    On branch master
    nothing to commit, working tree clean
```
**Para ver los elementos del directorio tras el último *commit* utilizaremos *git ls-tree --name-only -r HEAD*:**
```bash
    .gitignore
    Hola.java
    importante~
    script.sh
    texto.txt
``` 


## 7. Tags y gestión de versiones (git tag y git checkout)

* git show (numero commit) --> **Información sobre el commit al que pertenece el número**

**Ejemplo:**
```bash
    $ git show ac4508c0c1b4ce946d17a486835a992cb82ca3af
    commit ac4508c0c1b4ce946d17a486835a992cb82ca3af
    Author: joeloto <joelme.0808@gmail.com>
    Date:   Sat Oct 25 18:46:23 2025 +0200

        Ampliada la explicación del texto

    diff --git a/texto.txt b/texto.txt
    index 1c24992..686418d 100644
    --- a/texto.txt
    +++ b/texto.txt
    @@ -1,3 +1,6 @@
    uno
    dos
    tres
    +cuatro
    +cinco
    +
```
Como se puede ver nos muestra la información sobre el ***commit*** al que pertenece ese número

* git tag ... --> **Se suele utilizar para nombrar versiones**

**Ejemplos:**
```bash
    $ git tag v0.3 ac4508c0c1b4ce946d17a486835a992cb82ca3af
```
Darle un *tag* a la versión anterior, por ejemplo la del ***commit*** anterior, se realiza añadiendo el hash code


```bash
    $ git tag v0.7 
```
Darle un *tag* a la versión actual

**Si he hace *git log --oneline* posteriormente:**
```bash
    236cab9 (HEAD -> master, tag: v0.7) Añadidos fuentes en java y archivos importantes
    31edf3e Probando diff
    ac4508c (tag: v0.3) Ampliada la explicación del texto
    9f78fba Añadido archivo texto.txt
    c118801 Confirmación inicial
```
Podemos ver los *tag* que hemos asociado a cada uno de los elementos

**Ejecutando:**
```bash
    $ git show v0.3
    commit ac4508c0c1b4ce946d17a486835a992cb82ca3af (tag: v0.3)
    Author: joeloto <joelme.0808@gmail.com>
    Date:   Sat Oct 25 18:46:23 2025 +0200

        Ampliada la explicación del texto

    diff --git a/texto.txt b/texto.txt
    index 1c24992..686418d 100644
    --- a/texto.txt
    +++ b/texto.txt
    @@ -1,3 +1,6 @@
    uno
    dos
    tres
    +cuatro
    +cinco
    +
```
Si ejecutamos ***git show*** + el nombre del *tag* se nos muestra la informaión del elemento ligado al propio *tag*

**Más comandos relacionados con las versiones:**
```bash 
    $ git checkout v0.3
```
Para ir a una versión anterior

```bash
    $ git checkout master
```
Para volver a la versión actual

##### Nota: estos *tags* son almacenados en .git/refs/tags


## 8. Ramas

* git branch ... --> **Comando de creación de una rama**
```bash
    $ git branch Prueba
```

**Ejecutando *git log --oneline* posteriormente:**
```bash
    236cab9 (HEAD -> master, tag: v0.7, Prueba) Añadidos fuentes en java y archivos importantes
    31edf3e Probando diff
    ac4508c (tag: v0.3) Ampliada la explicación del texto
    9f78fba Añadido archivo texto.txt
    c118801 Confirmación inicial
```
Se nos indica que hay dos ramas, la principal (master) y la se acaba de crear (Prueba)

* git branch --> **Listado de ramas**
```bash
    $ git branch
    Prueba
    * master
```
##### Nota: las ramas son almacenadas en .git/refs/heads

* git switch ... --> **Cambio de rama**
```bash
    $ git switch Prueba
```
El cambio se puede ver en el prompt:
```bash
    Usuario@DESKTOP-UVIGJE8 MINGW64 ~/prueba_git (Prueba)
```

**Ejecutando de nuevo el *git branch*:**
```bash
    $ git branch
    * Prueba
    master
```
Observamos que el asterisco se ha situado el la rama 'Prueba'

**Y ejecutando:**
```bash
    $ git log --oneline
    236cab9 (HEAD -> Prueba, tag: v0.7, master) Añadidos fuentes en java y archivos importantes
    31edf3e Probando diff
    ac4508c (tag: v0.3) Ampliada la explicación del texto
    9f78fba Añadido archivo texto.txt
    c118801 Confirmación inicial
```
Vemos como HEAD apunta ahora a 'Prueba' por lo que todos los ***commit*** que se hagan a partir de ahora quedarán guardados en 'Prueba'

Por otro lado si se modifica el archivo *Hola.java*, se hace el ***commit*** y se le añade un *tag* podremos ver los distintos *tag* asociados a cada rama, claro está la modificación del archivo *Hola.java* quedará guardado en esta rama
```bash
    $ git commit -a -m "LLegan los Ents a Java"

    $ git tag v0.7-Ent-Release

    $ git log --oneline
    e02c911 (HEAD -> Prueba, tag: v0.7-Ent-Release) LLegan los Ents a Java
    236cab9 (tag: v0.7, master) Añadidos fuentes en java y archivos importantes
    31edf3e Probando diff
    ac4508c (tag: v0.3) Ampliada la explicación del texto
    9f78fba Añadido archivo texto.txt
    c118801 Confirmación inicial
```
* git switch master --> **Volver a la rama principal**

**Verificamos el contenido de *Hola.java*:**
```bash
    $ cat Hola.java
class Hola {
    public static void main(String[] args) {
        System.out.println("Welcome to the Java World");
    }
}
```
Podemos observar que en esta rama está guardada la versión anterior del archivo

* git merge ... --> **Fusionar las ramas**
```bash
    $ git merge Prueba
    Updating 236cab9..e02c911
    Fast-forward
    Hola.java | 2 +-
    1 file changed, 1 insertion(+), 1 deletion(-)
```
Al utilizar este comando se debe tener especial cuidado ya que a veces genera conflictos o problemas


## 9. Eliminar y quitar de seguimiento

* git rm .. --> **Eliminar archivos**
* git reset HEAD ... --> **Quitar archivos en seguimiento**

**Ejemplos:**
```bash
    $ git rm importante~
```
Eliminación del archivo *importante~*

```bash
    $ git reset HEAD *.class
```
Se elimina de seguimiento todos los archivos con extensión *.class*


## 10. Repositorios remotos: GitHub

Uno de los sitios más útiles para trabajar con repositorios Git y compartir distintos proyectos es [GitHub](https://www.github.com)

Comando útiles:

* git clone ... --> **Clonar un repositorio de GitHub**
```bash
    $ git clone https://github.com/joeloto/Practica-GitHub
```

```bash
    $ git clone https://github.com/joeloto/Practica-GitHub
```
Aquí se enlaza el proyecto *prueba_git* con el repositorio de GitHub

* git push -u origin master --> **Mandar cambios al repositorio remoto**

Por otro lado si lo que se busca es sincronizar un repositorio local con uno de GitHub lo que se debe hacer es:
```bash
    $ git remote add origin https://github.com/joeloto/PracticaGit.git
```

También si se desea descargar primero lo del repositorio remoto se debe hacer:
```bash
    $ git pull origin master https://github.com/joeloto/PracticaGit.git
```