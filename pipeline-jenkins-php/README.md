# Pipeline Jenkins en PHP

## Índice
- <a href="#1">Creación repositorio</a>
- <a href="#2">Creación Pipeline</a>



# <a name="1">Creación repositorio</a>

Lo primero que haremos será crear un repositorio con el proyecto a utilizar, que tendrá una estructura como la siguiente.

![repo](img/1.png)

Dentro de la carpeta **src** tendremos nuestro fichero **index.php** y una imagen que emplearemos en la página.

![src](img/2.png)

El fichero php tiene el siguiente contenido:

![index](img/3.png)

En el fichero **Dockerfile** especificamos la versión de php y puerto a utilizar entre otras cosas.

![Dockerfile](img/4.png)

En el fichero **Jenkinsfile** especificamos los pasos para la construcción del contenedor y el puerto desde el que conectaremos.

![Jenkinsfile](img/5.png)



# <a name="2">Creación Pipeline</a>

Desde el panel de control de Jenkins creamos un nuevo Pipeline.

![pipeline](img/6.png)

En este caso haremos que se ejecute desde un repositorio Git como se ve a continuación.

![repo](img/7.png)

Finalmente ejecutamos el Pipeline y comprobamos que la salida es correcta.

![console](img/8.png)

Podemos comprobar desde el navegador que la página funciona correctamente.

![web](img/9.png)
