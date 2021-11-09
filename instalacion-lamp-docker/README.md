# Instalación LAMP en Docker

## Índice
- <a href="#1">Pila LAMP</a>
- <a href="#2">Diagrama Docker</a>



# <a name="1">Pila LAMP</a>

Una pila es un conjunto de servicios o paquetes instalables y que se relacionan entre sí.

Utilizaremos Docker por la contenerización, creando un ambiente donde las aplicaciones eviten fallos por temas de dependencias.

La infraestructura que crearemos será la siguiente:

![infraestructura](img/1.png)



# <a name="2">Diagrama Docker</a>

Tendremos 3 contenedores que conforman un sistema distribuido interconectados entre sí, cada uno con servicios distintos que constituyeran la pila LAMP en la red local.

**Servidor web:**
* Nombre: **www**
* Puerto: **80**

**Servidor de base de datos:**
* Nombre: **db**
* Puerto: **3306**

**Servidor del sistema gestor de base de datos gráfico:**
* Nombre: **phpmyadmin**
* Puerto: **8000**

La estructura del proyecto es la siguiente:

![estructura](img/2.png)

En el fichero **Dockerfile** especificaremos la instalación de la versión **8.0.0** de **php** con **apache**. También modificaremos la variable de entorno DEBIAN_FRONTES a modo no interactivo e instalaremos algunas extensiones de comunicación y actualizaciones de repositorio.

![dokcerfile](img/3.png)

En el fichero **docker-compose.yml** definiremos los servicios **www**, **db** y **phpmyadmin**.

![docker-compose.yml](img/4.png)

En **dbname.sql** tendremos el siguiente contenido que se exporta a MySQL.

![dbname.sql](img/5.png)

Y en **index.php** la siguiente página de prueba, que comprueba la correcta carga del sitio y su conectividad con la base de datos.

![index.php](img/6.png)

Ya solo tendremos que lanzar la configuración ejecutando:

```
sudo docker-compose up -d
```

![docker-compose_up](img/7.png)

Y comprobar si los 3 contenedores funcionan correctamente ejecutando.

```
sudo docker-compose ps
```

![docker-compose_ps](img/8.png)

Si accedemos desde el navegador deberíamos poder observar la siguiente web.

![web](img/9.png)

También podemos comprobar el acceso a **phpmyadmin** accediendo desde el puerto **8000** con las credenciales especificadas en **docker-compose.yml**.

![php_login](img/10.png)

![phpmyadin](img/11.png)

Cualquier aplicación que queramos desplegar debemos colocarla dentro de **www** y acceder a ella desde la ruta **IP/app** o **localhost/app**.

![app](img/12.png)

Finalmente para detener el stack con Docker compose debemos ejecutar:

```
sudo docker-compose stop
```

![docker-compose_stop](img/13.png)
