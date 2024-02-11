
 # <center> [Ejercicios Git](#item1) </center>
  # <center> [Ejercicios GitFlow](#item2) </center>


## Ejercicios Git<a name="item1"></a>

Se deberá crear un repositorio y realizar una serie de operaciones desde la terminal y responder
a las preguntas del cuestionario, en el que se pregunta por comandos utilizados en ciertos pasos.

Los pasos a ejecutar son los siguientes (los pasos en negrita indican que hay una pregunta
asociada):


#### 1) Crear un repositorio

`mkdir clase-git`

`cd clase-git`

`git init`

#### 2) Crear un archivo git-nuestro.md con el contenido:

Git nuestro

Git nuestro que estas en los repos

Comprimidos sean tus commits

Venga a nosotros tu log

En el local como en el remote 

Danos hoy nuestro pull de cada día

Perdona nuestros conflictos

Como también perdonamos los de otros geeks

No nos dejes caer en detached HEAD

y líbranos de SVN

git commit --amend

`touch git-nuestro.md`  (y copiar y pegar el texto en él).

#### 3) Añadir git-nuestro.md al staging area

`git add git-nuestro.md`

#### 4) Mover lo que hay en el staging area al repositorio

`git commit -m "first commit" `

#### 5) Crear una rama llamada “styled”

`git branch styled`

#### 6) Listar las ramas que hay en el repositorio

`git branch`

#### 7) Moverse a la rama “styled”

`git checkout styled`

#### 8) Comprobar que se está en la rama correcta

`git branch`

#### 9) Modificar en el archivo git-nuestro.md:

*Git* nuestro que estás en los repos
Comprimidos sean tus *commits*
Venga a nosotros tu *log*
En el local como en el *remote*
Danos hoy nuestro *pull* de cada día
Perdona nuestros *conflictos*
Como también perdonamos los de otros geeks
No nos dejes caer en *detached HEAD*
y líbranos de *SVN*
`git commit --amend`

(copiar y pegar el nuevo texto)

#### 10) Añadir los cambios al staging area y luego pasarlos al repositorio

`git add git-nuestro.md`

`git commit -m "second commit"  `

#### 11) Deshacer el último commit (perdiendo los cambios realizados en el working copy)

`git log` para ver el id del commit al que quiero ir (el commit 1),
copio el id del commit

`git reset --hard idcommit1`

Con `git log` veo que ya no está el segundo commit, pero con `git reflog` veo que realmente sí que sigue registrado el commit

#### 12) Rehacer el último commit (el que acabamos de deshacer)

`git reset --hard idcommit2`

Con `git log` ya veo que me vuelve a aparecer.

#### 13) Hacer un merge con ‘master’ (styled absorbe a master)

`git branch` para ver que estoy en la rama styled. (Sí, lo estoy)

`git merge main`

#### 14) Volver a la rama master

`git checkout main`

#### 15) Crear una nueva rama llamada “htmlify”

`git branch htmlify`

#### 16) Cambiar a la rama htmlify

`git checkout htmlify`

#### 17) Modificar en el archivo git-nuestro.md:

<p><em>Git</em> nuestro que estas en los repos<br />
Comprimidos sean tus <em>commits</em><br />
Venga a nosotros tu <em>log</em><br />
En el local como en el <em>remote</em><br />
Danos hoy nuestro <em>pull</em> de cada día<br />
Perdona nuestros <em>conflictos</em><br />
Como también perdonamos los de otros geeks<br />
No nos dejes caer en <em>detached HEAD</em><br />
y líbranos de <em>SVN</em><br />
<code>git commit --amend</code></p>


#### 18) Hacer un commit

`git add git-nuestro.md`

`git commit -m "third commit" `

#### 19) Hacer un merge de “htmlify” en “styled” (styled absorbe a htmlify)

`git branch`  para ver en que rama estoy. Estoy en htmlfy.

`git checkout styled`

`git merge htmlify`

#### 20) Si hay conflictos, deberemos resolverlos quedándonos con el contenido de la rama “styled”.

Sí que hay conflictos, así que borro la parte que no quiero (la del htmlify) y hago

`git commit -m "solves conflict"`

Lanzo un `git log` para ver que se ha hecho correctamente.

#### 21) Desde “master”, hacer un merge con “styled”

`git checkout main`

`git merge styled`


#### 22) Crear una rama “title” y cambiarse a esa rama.

`git checkout -b title`

#### 23) Añadir un título (a tu gusto) al archivo git-nuestro.mdy hacer un commit. 

 Le he puesto "oracion de git".
 
 `git add git-nuestro.md`
 
 `git commit -m "adds title" `

#### 24) Volver a la rama master

`git checkout main`

#### 25) Dibujar el diagrama

`git log --graph`

#### 26) Hacer un merge “no fast-forward” de “title” en “master” (master absorbe a title)

`git merge --no-ff title`

#### 27) Deshacer el merge (sin perder los cambios del working copy)

Hago `git log` y veo el id del commit.

`git reset --hard c9e4f78`

#### 29) Eliminar la rama “title”

`git branch -d title`


#### 31) Volver a master y eliminar el resto de ramas

`git checkout main`

`git branch -d styled`

`git branch -d htmlify`

#### 32) Volver al commit inicial cuando se creó el poema

`git checkout 47f38ef`

#### 33) Volver al estado final, cuando pusimos título al poema

`git checkout c9e4f78`

#### 34) Crear los siguientes tags:

inicial: en el primer commit   `git tag -a inicial 47f38ef`

styled: modificación del paso 10  `git tag -a styled f5f81b0`

htmlify: modificación del paso 17-18  `git tag -a 5a5d4ce`


-----------------------------------------------------------------------
-----------------------------------------------------------------------


## Ejercicios GitFlow<a name="item2"></a>


#### 1. Configura las claves RSA en tu ordenador para poder autenticarte en GitHub

Primero voy a ver si las tengo ya creadas.

Mediante comandos lo puedo comprobar con: `ls -al ~/.ssh`

También se puede hacer entrando en la raíz de mi disco y buscando la carpeta oculta .ssh 

Está vacía, lo que significa que no tengo las claves y las tengo que crear.

Para crearla tecleo:

`ssh-keygen -t ed25519 -C "mi email"`

Para verificar que se ha creado vuelvo a teclear: `ls -al ~/.ssh`

y esta vez ya veo los dos archivo en la carpeta .ssh

Para añadir mi clave privada al ssh agent uso el comando:

`ssh-add ~/.ssh/id_ed25519`

Para copiar mi clave pública y ponerla en Github escribo:

`cat ~/.ssh/id_ed25519.pub`

y copio el contenido (mi clave pública).

En mi perfil de Github voy a settings, access, SSH and GPG keys y copio mi clave en el espacio destinado para ello (donde pone Key).

También añado una descripción para la key.

Ya está añadida la clave :)


Para comprobar que está todo bien uso el comando:

`ssh -T git@github.com`

Me pide que acepte la conexión, la acepto, y ya estoy conectada a Github.

#### 2. Añade el origen a tu repositorio local

`git remote add origin https://github.com/datasilvia/clase-git.git`

#### 3. Haz push del código

`git push -u origin main`

#### 4. Elimina todos los tags que tuvieras en local

`git tag` (para ver los tags que tengo)

`git tag --delete inicial`

`git tag --delete styled`

`git tag --delete htmlify`

#### 5. Haz un tag de v1.0 del estado anterior que tuvieras en el repositorio

`git tag v1.0`

#### 6. Haz push de ese tag

`git push --tags`

#### 7. Crea una rama develop a partir de main y haz push al repositorio

`git branch develop`

`git push`

#### 8. Crea una rama feature y traduce el ejercicio al inglés

Como las ramas feature se crean en develop, primero me muevo a la rama develop con `git checkout develop`  y ya ahí creo la rama feature usando `git branch feature`.
Voy a mergear feature con develop , asi que me cambio a develop con `git checkout develop` y mergeo con  `git merge feature`

#### 9. Crea un hotfix para sustituir todas las ocurrencias de la palabra git del ejercicio por “GIT” y taggea la v1.1. Recuerda integrar la rama en develop.

`git branch hotfix`

Sustituyo los "git" por "GIT".

`git checkout develop`

`git merge hotfix`

`git tag V.1.1`

#### 10. Mergea develop en main y taggea la versión 2.0

`git checkout main`

`git merge develop`

`git tag 2.0`

`git push --tags`
