# Pipeline Jenkins en Java y Apache-Tomcat

## Índice
- <a href="#1">Creación repositorio</a>
- <a href="#2">Crear el Dockerfile</a>



# <a name="1">Creación repositorio</a>

Lo primero será crear un repositorio con el proyecto y ficheros de configuración.

![repo](img/1.png)

En el **index.jsp** añadimos nuestro nombre para hacer las comprobaciones finales.

![index](img/2.png)

El nombre que pongamos en el **web.xml** será la ruta para acceder a la aplicación.

![web.xml](img/3.png)

En el **Dockerfile** especificamos la versión de Tomcat y la copia del **.war**.

![Dockerfile](img/4.png)

En el **Jenkinsfile** ponemos los pasos que se seguirán.

![Jenkinsfile](img/5.png)

Como podemos ver, tenemos varias fases:

* Test Junit
* - Ejecutamos los test de la aplicación
* Build
* - Creamos el .war
* Deploy
* - Creamos el contenedor de docker
* - Ejecutamos el contenedor en el puerto especificado
* Test
* - Comprobamos que la pagina final contiene nuestro nombre



# <a name="2">Creación Pipeline</a>

En el panel de control de Jenkins creamos un nuevo Pipeline.

![pipeline](img/6.png)

Y añadimos la ruta de nuestro repositorio.

![repo](img/7.png)

Hecho esto ejecutamos el Pipeline y nos aseguramos que termine correctamente.

![log](img/8.png)

![view](img/9.png)

También comprobamos que podemos consultar la web desde el navegador.

![web](img/10.png)
