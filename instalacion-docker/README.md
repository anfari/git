# Instalación de Docker

## Índice
- <a href="#1">Instalar Docker</a>
- <a href="#2">Trabajar con imágenes de Docker</a>
- <a href="#3">Administrar contenedores de Docker</a>




# <a name="1">Instalar Docker</a>

Lo primero será actualizar la lista de paquetes:

```
sudo apt update && sudo apt upgrade
```

![update-upgrade](img/1.png)

Instalamos los paquetes necesarios para permitir a apt utilizar paquetes a través de HTTPS:

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

![install_packages](img/2.png)

Añadimos la **clave GPG** para el repositorio oficial de Docker:

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

![curl](img/3.png)

Agregamos el repositorio de Dokcer a APT:

```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu 	focal stable"
```

![add-apt-repository](img/4.png)

Y actualizamos con los paquetes de Docker del repositorio agregado:

```
sudo apt upgrade
```

![update](img/5.png)

Nos aseguramos de que vamos a realizar la instalación desde el repositorio de Docker:

```
apt-cache policy docker-ce
```

![policy](img/6.png)

E instalamos Docker:

```
sudo apt install docker-ce
```

![install](img/7.png)

Comprobamos que funciona correctamente:

```
sudo systemctl status docker
```

![status](img/8.png)


# <a name="2">Trabajar con imágenes de Docker</a>

Los contenedores de Docker se construyen con imágenes y la mayoría de aplicaciones y distribuciones ya tienen imágenes alojadas en Docker Hub.

Vamos a acceder y descargar una imagen de ejemplo:

```
sudo docker run hello-world
```

![docker_run](img/9.png)


# <a name="3">Administrar contenedores de Docker</a>

Para ver los contenedores activos de Docker ejecutamos:

```
sudo docker ps
```

![docker_ps](img/10.png)

Para ver todos los contenedores, activos e inactivos, ejecutamos:

```
sudo docker ps -a
```

![ps-a](img/11.png)

Y para ver el último contenedor creado utilizamos:

```
sudo docker ps -l
```

![ps-l](img/12.png)

Podemos también listar las imágenes:

```
sudo docker images
```

![docker_images](img/13.png)
