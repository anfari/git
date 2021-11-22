# Balanceo de carga en Apache

## Índice
- <a href="#1">Activación de los módulos necesarios de Apache</a>
- <a href="#2">Configuración de Apache para balancear la carga del tráfico HTTP</a>
- <a href="#3">Creación del proyecto y contenedores</a>




# <a name="1">Activación de los módulos necesarios de Apache</a>

Lo primero será activar todos los módulos necesarios:

```
a2enmod proxy
a2enmod proxy_http
a2enmod proxy_ajp
a2enmod rewrite
a2enmod deflate
a2enmod headers
a2enmod proxy_balancer
a2enmod proxy_connect
a2enmod proxy_html
a2enmod lbmethod_byrequests
```

Esto lo haremos con permisos de sudo.

![a2enmod](img/1.png)

En la activación nos pedirá reiniciar el servicio, pero esperaremos a activarlos todos.

![a2enmod](img/2.png)



# <a name="2">Configuración de Apache para balancear la carga del tráfico HTTP</a>

Vamos a editar el fichero de configuración por defecto **/etc/apache2/sites-enable/000-default.conf** al que añadiremos las siguientes lineas **dentro del VirtualHost**.

![000-default.conf](img/3.png)

Y reiniciamos el servicio de apache:

```
sudo systemctl restart apache2
```

![restart](img/4.png)



# <a name="3">Creación del proyecto y contenedores</a>

Para esto aprovecharemos un proyecto anterior que mostraba el puerto por el que realizábamos la conexión.

![web.xml](img/5.png)

![index.jsp](img/6.png)

El fichero **dockerfile** será el mismo empleado para wildfly en las anteriores ocasiones.

![dockerfile](img/7.png)

Y en el fichero **docker-compose.yml** configuraremos solo los contenedores wildfly.

![docker-compose](img/8.png)

![docker-compose](img/9.png)

Hecho esto solo compilaremos el proyecto.

![mvn_install](img/10.png)

![success](img/11.png)

Y lanzaremos la creación de los contenedores:

```
sudo docker-compose up -d –build
```

![docker-compose_up](img/12.png)

Y comprobamos que se han creado correctamente y escuchan en el puerto deseado:

```
sudo docker ps
```

![docker_ps](img/13.png)

Y hemos terminado la configuración, si accedemos a apache desde el navegador nos irá redireccionando a los diferentes puertos disponibles por orden para balancear la carga.

![web](img/14.png)

![web](img/15.png)

![web](img/16.png)

![web](img/17.png)
