# Dockerizando Wildfly

## Índice
- <a href="#1">Creación del fichero dockerfile para Wildfly</a>
- <a href="#2">Uso de la nueva imagen</a>



# <a name="1">Creación del fichero dockerfile para Wildfly</a>

Lo primero será crear el directorio de trabajo:

```
mkdir wildfly-config
```

![mkdir](img/1.png)

Creamos el fichero de configuración con el siguiente contenido:

```
nano Dockerfile
```

![Dockerfile](img/2.png)

Construimos la imagen:

```
sudo docker build -q --rm --tag=jboss/wildfly:25.0.0.Final-config .
```

![docker_build](img/3.png)

Y verificamos que existe dentro de docker:

```
sudo docker images
```

![focker_images](img/4.png)


# <a name="2">Uso de la nueva imagen</a>

Probamos la imagen recién creada ejecutando:

```
sudo docker run -d -p 8080:8080 -p 9990:9990 -p 8009:8009 --name servidor-wilfly-config -it jboss/wildfly:25.0.0.Final-config
```

![docker_run](img/5.png)

Verificamos que el contenedor está arrancado:

```
sudo docker ps -a
```

![ps-a](img/6.png)

Ahora ya podemos acceder a Wildfly desde el navegador.

![web](img/7.png)

Y podemos comprobar el acceso a la consola de administración con el usuario creado.

![login](img/8.png)

![console](img/9.png)
