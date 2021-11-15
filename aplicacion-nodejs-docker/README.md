# Aplicación NodeJS en Docker

## Índice
- <a href="#1">Crear la aplicación Node.js</a>
- <a href="#2">Crear el Dockerfile</a>
- <a href="#3">Fichero .dockerignore</a>
- <a href="#4">Construir la imagen</a>
- <a href="#5">Ejecutar la imagen</a>
- <a href="#6">Acceso web</a>



# <a name="1">Crear la aplicación Node.js</a>

Lo primero será crear un directorio que contendrá todos los fichero necesarios y dentro de este crear el un fichero **package.json** con el siguiente contenido.

![directorio](img/1.png)

![package.json](img/2.png)

Hecho esto ejecutaremos el comando:

```
npm install
```

![npm_install](img/3.png)

Esto nos generará un fichero **package-lock.json** en caso de tener la versión 5 o superior de npm.

![package-lock](img/4.png)

Lo siguiente será crear el fichero **server.js** con el siguiente contenido.

![server.js](img/5.png)



# <a name="2">Crear el Dockerfile</a>

Ahora tenemos que crear un fichero **Dockerfile** en el directorio con las siguientes instrucciones.

![dokcerfile](img/6.png)



# <a name="3">Fichero .dockerignore</a>

Crearemos un fichero **.dockerignore** que evitará que los módulos locales y logs de debug sean copiados en la imagen docker.

![dockerignore](img/7.png)



# <a name="4">Construir la imagen</a>

Dentro del directorio ejecutaremos el siguiente comando:

```
sudo docker build . -t nombre
```

![docker_build](img/8.png)

El resultado final debería ser tal que:

![resultado](img/9.png)

Podemos consultar la imagen en el listado de docker ejecutando:

```
sudo docker images
```

![docker_images](img/10.png)



# <a name="5">Ejecutar la imagen</a>

Ahora crearemos un contenedor con la imagen creada ejecutando el comando:

```
sudo docker run -p 49160:8080 -d nombre
```

![docker_run](img/11.png)

Podemos consultar el ID del contenedor ejecutando:

```
sudo docker ps
```

![docker_ps](img/12.png)

Y consultar sus logs mediante el ID ejecutando:

```
sudo docker logs ID
```

![docker_logs](img/13.png)



# <a name="6">Acceso web</a>
Finalmente podemos consultar nuestra aplicación accediendo mediante el navegador al puerto especificado.

![web](img/14.png)
