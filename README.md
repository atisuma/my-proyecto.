</center>

***Nombre:Samuel Rodriguez***
***Curso:1ºdaw*** 

### ÍNDICE

+ [Introducción](#id1)
+ [Objetivos](#id2)
+ [Material empleado](#id3)
+ [Desarrollo](#id4)
+ [Conclusiones](#id5)


#### ***Introducción***. <a name="id1"></a>

En esta práctica hemos trabajado con **Git y GitHub** para aprender cómo crear, clonar y gestionar repositorios.  
También hemos visto cómo hacer *commits*, subir cambios, crear ramas y etiquetas (*tags*), y cómo resolver conflictos entre ramas.  
Todo esto sirve para controlar versiones de los proyectos y trabajar de forma ordenada.


#### ***Objetivos***. <a name="id2"></a>

- Aprender a crear y clonar un repositorio en GitHub.  
- Conocer los comandos básicos de Git (`add`, `commit`, `push`, `branch`, `merge`, etc.).  
- Saber cómo ignorar archivos usando `.gitignore`.  
- Crear y manejar ramas para organizar el trabajo.  
- Usar etiquetas (*tags*) para marcar versiones del proyecto.  
- Resolver conflictos al hacer merges entre ramas.  
- Subir el trabajo correctamente al repositorio.


#### ***Material empleado***. <a name="id3"></a>

**Hardware:**  
- Ordenador
- Teclado
- Ratón

**Software:**  
- Sistema operativo ubuntu
- Git instalado.  
- Navegador web  
- Editor de texto  

**Configuraciones:**  
- Cuenta activa en GitHub.  
- Configuración básica de Git (`git config --global user.name` y `git config --global user.email`).  
- Clave SSH configurada en GitHub para poder clonar y subir repositorios sin pedir contraseña.


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

Seguimos creando un tag con el comando `git tag v0.1` y los subimos al repositorio remoto con `git push --tag origin master`

>Pregunta sobre tag en un repositorio git:Un tag en un repositorio git es una referencia que está directamente relacionada con un commit específico, se usa para marcar puntos importantes en el proyecto.

Ahora creamos una rama con `git branch v0.2` y la posicionamos en nuestra carpeta de trabajo y hacemos un `git checkout v0.2` para comprobar que todo es correcto, añadimos un fichero y le hacemos un commit con los comandos `touch 2.txt`,`git add .`,`git commit -m "añadido 2.txt"`.

>pregunta sobre ranas:Las ramas sirven para trabajar en partes del proyecto sin afectar al código principal. En equipos pequeños se usan pocas ramas, y en empresas grandes se usan muchas para organizar el trabajo.

Creamos una rama remota y hacemos un puch para tenerla guardada con `git push origin v0.2`
Volvemos a la rama principal para unir los cambios hechos en la rama v0.2 y hacemos un merge
`git checkout master`
`git merge v0.2 -m "merge v0.2 sin conflictos"`
En este caso no hay conflictos porque los archivos que se modificaron en `v0.2` no afectan a los que estaban en la rama principal.

>pregunta sobre si deberia haber conflicto:No, porque en la rama `v0.2` no se modificaron los mismos archivos que en `master`.

Ahora vamos a crear una situación donde sí haya conflicto.  
Primero, en la rama principal añadimos la palabra “Hola” al archivo `1.txt` y guardamos los cambios:

`git checkout master`
`echo "Hola" >> 1.txt`
`git add .`
`git commit -m "hola en 1.txt"`


Luego cambiamos a la rama `v0.2` y en ese mismo archivo escribimos “Adios”:

`git checkout v0.2`
`echo "Adios" >> 1.txt`
`git add .`
`git commit -m "adios en 1.txt"`


Cuando intentamos unir de nuevo las dos ramas, Git detecta que el mismo archivo fue cambiado de manera diferente en las dos, y aparece un **conflicto**:

`git checkout master`
`git merge v0.2`

Abrimos el archivo, decidimos qué parte queremos conservar, y guardamos los cambios con:

`git add .`
`git commit -m "arreglado merge en 1.txt"`

>prgunta sobre porque se genera conflicto:Porque el mismo archivo fue modificado en ambas ramas y Git no sabe cuál versión mantener.

Podemos ver qué ramas ya se unieron al proyecto principal y cuáles no:

`git branch --merged`
`git branch --no-merged`

Esto nos ayuda a saber qué ramas siguen pendientes de fusionar.
Si todavía hay algún conflicto, abrimos el archivo con un editor, corregimos lo que haga falta, y volvemos a guardar los cambios:
`nano 1.txt`
`git add .`
`git commit -m "arreglado merge en 1.txt"`

Una vez que la rama `v0.2` ya está unida y no la necesitamos, la borramos.  
También creamos un nuevo *tag* para marcar el estado actual del proyecto:

`git tag v0.2`
`git branch -d v0.2`

Esto deja el repositorio más limpio y organizado.
Por último, configuramos un comando para ver de forma resumida todos los cambios, ramas y etiquetas del proyecto:

`git config --global alias.list 'log --oneline --decorate --graph --all'`
`git list`

Con este comando podemos ver todo el historial del proyecto de una forma visual, mostrando las ramas y sus *tags*.
#### ***Conclusiones***. <a name="id5"></a>
Esta práctica me ha ayudado a comprender cómo funciona Git y cómo se usa con GitHub.  
Hemos aprendido a crear repositorios, hacer commits, trabajar con ramas y etiquetas, y resolver conflictos entre versiones.  
 
Con GitHub además podemos guardar el trabajo en la nube y compartirlo fácilmente.

