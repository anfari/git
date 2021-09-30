# Ejercicio Práctico Git

Lo primero será crear un directorio con el nombre **ejercicio_git_nombre_alumno** donde iniciaremos el repositorio utilizando el comando:
```
 git init
```
![git_init](img/1.png)

Ahora añadimos el archivo **README**.

![README](img/2.png)

Y realizamos el primer commit del repositorio.

![commit](img/3.png)


Crearemos una nueva rama llamada **feature-1**.

![branch](img/4.png)

A la cual nos moveremos y crearemos el fichero **hola.html** con el siguiente contenido:

![hola.html](img/5.png)

Creamos un commit con la nueva adicción.

![commit](img/6.png)

Y volvemos a la rama master para crear el fichero **adios.html** con el contenido:

![adios.html](img/7.png)

Realizamos una mezcla de las ramas en el repositorio local empleando el comando:
```
git merge nombre_rama
```
![merge](img/8.png)

Y finalmente mostramos los cambios realizados en el repositorio con el comando **git log** o sus variantes.

![log](img/9.png)

![log](img/10.png)
