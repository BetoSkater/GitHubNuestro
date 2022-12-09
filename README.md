# GitHubNuestro
Subida del ejercicio GitNuestro

1. Pregunta 1:¿Qué comando utilizaste en el paso 11? ¿Por qué?

	El comando utilizado ha sido **"git reset -hard HEAD~1"**.
El enunciado indica que se han de deshacer los cambios perdiendo las 
modificaciones realizadas en el working copy. Por lo que se ha de usar el
comando que incluye la palabra hard, ya que de esta forma se borra el 
trabajo del working copy. En caso de haber usado "git reset HEAD~1",
el contenido del working copy se habría mantenido.

2. ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?
	En primer lugar se ha usado el comando **"git reflog"** para localizar el 
commit en cuestión. Atendiendo a los mensajes de los commits, el commit al 
que se ha de volver es en este caso el "52f5356" donde el puntero HEAD 
estaba en "HEAD@1".

	Seguidamente, se usa el comando **"git reset 52f5356"** , y aquí Git 
indica que hay cambios que no están en el staging area. Para ver con más 
detalle a qué se refiere, se usa **"git status"**. Git muestra un mensaje 
en el que indica  que el fichero git-nuesto.md está modificado. Para no 
liarla, se usa el comando **"nano git-nuestro.md"** para ver el estado del 
fichero. Se ve que es el fichero sin modificar, lo cual era de esperar al 
haber utilizado un hard reset.

	Con toda esta información, de las opciones ofertadas se escoge usar **"git 
restore git-nuestro.md"** para recuperar el fichero original que tenía el 
commit al que se ha vuelto. Finalmente se vuelve a visualizar el fichero 
con **"nano git-nuestro.md"** para confirmar que es el fichero modificado 
en el paso 10.

3. El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?

	No, hacer un merge desde la rama "styled" para absorber la rama "main" 
no genera ningún conflicto. Esto se debe a que en la rama "style" ya se 
tiene el único commit que tiene la rama "main".

4. El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?
	Si, existe un conflicto por lo que el merge automático falla. El 
problema reside en el fichero git-nuestro.md. En la rama styled las 
palabras de interés están marcadas con asteriscos, mientras que en la 
versión del fichero de la rama htmlify, el resaltado está realizado usando 
HTML.

5. El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?

	No, no ha habido ningún conflicto. El motivo es que se ha producido un 
merge fast-foward. El estado inicial de cada rama es el siguiente:
    * Rama main: contiene el primer commit (commit A).
    * Rama styled: contiene el primer commit (commit A), el commit de 
marcado (commit B) y el commit tras el merge no fast-foward (commit C).

	Como la rama main tiene el mismo commit A por lo que no dará problemas. 
Se puede decir que no hay conflicto posible ya que además, la rama main no 
tiene ningún commit más, por lo que no hay posibles problemas entre ambas 
ramas. Git sabe que la rama más actualizada es styled, así que absorbe 
todos sus commits sin ningún problema moviendose el puntero HEAD con la 
rama main al commit C.

6. ¿Qué comando o comandos utilizaste en el paso 25?

	El comando para poder dibujar el grafo esquemático desde la terminal 
es **"git log --graph"**

7. El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?

	Si, podría serlo perfectamente. En el punto de partida las dos ramas 
tienen el siguiente aspecto.
    * Rama main: A<-B<-C
    * Rama title: A<-B<-C<-D
	La única diferencia que tienen es el commit D. Por lo que se podría 
hacer un merge fastfowards, moviendo el puntero HEAD y a la rama main al 
commit D. No sería necesario crear un commit E cómo ha sido en este caso, 
es redundante.

8. ¿Qué comando o comandos utilizaste en el paso 27?
    
	Al haber realizado un merge no fast forward, git sabe cual es el 
commit que ha "absorbido" al otro, por lo que simplemente se puede usar 
**"git reset HEAD~1"**

9. ¿Qué comando o comandos utilizaste en el paso 28?

	Para recuperar el fichero sin el título, se usa **"git restore 
git-nuestro.md"** 

10. ¿Qué comando o comandos utilizaste en el paso 29?

	Para asegurar que se borra del todo, se ha usado el comando **"git 
branch -D title"**

11. ¿Qué comando o comandos utilizaste en el paso 30?

	En primer lugar se realiza un **"git reflog"** para localizar el commit 
del merge (ya que se hizo un merge no fast forward). El commit 1695ba7 
tiene de mensaje "merge title", por lo que ese es el commit al que se ha 
de ir. Tras esto se usa **"git checkout 1695ba7"** para volver al commit 
del merge (commit E).
	Se pasa a estar en un estado de Detatched-HEAD y Git informa de que para 
no perder estos commits se ha de crear una rama. Por lo que se crea una 
rama, se hace checkout a main y desde aquí un merge fast-forward.
	Se usa **"git switch -c titulo2"** para crear una rama y hacer un checkout 
a esta donde está HEAD.
Se usa **"git checkout main"** y seguidamente **"git merge titulo2"**.

12. ¿Qué comando o comandos usaste en el paso 32?

	En primer lugar se usa **"git log"** para ver la lista de commits. Se 
busca el mensaje (creación del rezo git.nuestro.md) de interés y se usa 
**"git reset 3a31d54....3b"** (en este caso se ha usado el identificador 
completo).

13. ¿Qué comando o comandos usaste en el punto 33?

	Como en el caso anterior, se han usado **"git log"** y **"git reset 
1695a7"**

