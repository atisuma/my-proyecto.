</center>

***Nombre:***
***Curso:*** 

### ÍNDICE

+ [Introducción](#id1)
+ [Objetivos](#id2)
+ [Material empleado](#id3)
+ [Desarrollo](#id4)
+ [Conclusiones](#id5)


#### ***Introducción***. <a name="id1"></a>

Aquí explicamos brevemente la parte teórica que tiene que ver con la práctica que se va a realizar

#### ***Objetivos***. <a name="id2"></a>

Aquí explicamos los objetivos que se pretenden alcanzar al realizar la práctica.

#### ***Material empleado***. <a name="id3"></a>

Enumeramos el material empleado tanto hardware como software y las configuraciones que hacemos (configuraciones de red por ejemplo) 

#### ***Desarrollo***. <a name="id4"></a>

Creamos un repositorio en nuestra cuenta de github con el nombre "my-proyecto."y clonamos
el repositorio fuera el repositorio de trabajo de clase, creando manualmente un repositorio en github y mediante el comando
 `git clone git@github.com:alumno-XXX/my-proyecto-millonario.git`.
 ![captura1](ut1/a3/img/cap1.png)
cambiando *alumno-XXX* y *my-proyecto-millonario.git* por el nombre de usuario del git hub y el nombre del repositorio creado.
Despues subimos los cambios con un`git add .` y despues un `git commit -m "commit inicial"` en la terminal.
![captura2](ut1/a3/img/cap2.png)
Seguidamente hacemos un `git push origin master` para subir todo al repo correspondiente.
![captura3](ut1/a3/img/cap3.png)
Como se puede ver en la captura, al hacer el `git push origin master` da un error, esto se arregla poniendo directamente un `git push`,de esta manera se subirán todos los cambio al repo.

>Pregunta sobre el clonado del repo:Si ya tenemos el clon del repositorio podemos saltarnos el paso del clonar el repositorio he irnos directamente al commit inicial.

Ahora, creamos un README privado, que después git hub ignorará a la hora de hacer el push y podremos tener nuestro propio documento privado.
![captura4](ut1/a3/img/cap4.png)
Creamos una carpeta y metemos los comandos:
`echo "privado.txt" >> .gitignore`
`echo "/privada" >> .gitignore`
![captura5](ut1/a3/img/cap5.png)
Después volvemos a hacer un `git add .` y `un git commit -m "añadido fichero .gitignore"` Recuerda hacer un `git push` si vas a dejar de trabajar.
>Pregunta sobre fichero y directorio privado: No, git hub debería de ignorar el fichero si tiene el `.gitignore` bien escrito.

Ahora añadimos un fichero, con los comandos `touch 1.txt`

>Pregunta sobre add y commit:El comando `add .` añade los cambios al repositorio local, el comando `git commit -m "Lo que sea "`los sube y los actualiza también en repositorio local donde nos avisara si hay cambios y si hay errores, por ultimo el `git push` los sube directamente al repositorio alojado en git hub.
#### ***Conclusiones***. <a name="id5"></a>

