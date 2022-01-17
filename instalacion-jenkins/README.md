# Instalación Jenkins

## Índice
- <a href="#1">Dominio Apache</a>
- <a href="#2">Instalación Jenkins</a>
- <a href="#3">Iniciar Jenkins</a>
- <a href="#4">Abrir firewall</a>
- <a href="#5">Configuración Jenkins</a>



# <a name="1">Dominio Apache</a>

Lo primero que haremos será crear un dominio por el cual accederemos a la herramienta durante y tras su instalación y configuración. Este se llamara en mi caso **www.antonioic.com**.

![dominio](img/1.png)

Después de crear el dominio crearemos un enlace simbólico en la carpeta **/etc/apache2/sites-enabled**.

![ln -s](img/2.png)



# <a name="2">Instalación Jenkins</a>

Agregamos la clave del repositorio al sistema:

```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add
```

![wget](img/3.png)

Si el resultado en **OK**, procedemos a anexar la dirección del repositorio de paquetes a source.list del servidor:

```
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```

![anexar](img/4.png)

Ahora actualizaremos los repositorios del sistema:

```
sudo apt update
```

![update](img/5.png)

Y procedemos a instalar **Jenkins**:

```
sudo apt install jenkins
```

![install](img/6.png)



# <a name="3">Iniciar Jenkins</a>

Iniciamos el servicio:

```
sudo systemctl start jenkins
```

![start](img/7.png)

Y comprobamos el estado del servicio:

```
sudo systemctl status jenkins
```

![status](img/8.png)



# <a name="4">Abrir firewall</a>

Permitimos el puerto 8080 en el firewall UFW:

```
sudo ufw allow 8080
```

![allow](img/9.png)

En caso de que tengamos el firewall desactivado, ejecutaremos los siguientes comandos para habilitarlos y permitir OenSSH:

```
sudo ufw allow OpenSSH
sudo ufw enable
```

![allow](img/10.png)

![enable](img/11.png)

Y comprobamos el estado del firewall:

```
sudo ufw status
```

![status](img/12.png)



# <a name="5">Configuración Jenkins</a>

Ahora que ya tenemos el servicio instalado y funcionando, accedemos desde el navegador utilizando el dominio que hemos creado.

![web](img/13.png)

Para acceder necesitamos la contraseña de administrador que podemos consultar en el siguiente fichero:

```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

![password](img/14.png)

La pegamos en el campo y accederemos a la instalación de complementos, donde seleccionaremos **Install suggested plugins**.

![plugins](img/15.png)

Y esperamos a que se complete el proceso de instalación

![install](img/16.png)

Al terminar nos pedirá configurar el primer usuario administrador del sistema, paso que podemos saltar y seguir empleando la contraseña anteriormente mencionada, pero que no haremos y configuraremos.

![user](img/17.png)

En la siguiente pantalla nos pedirá confirmar la URL para instanciar Jenkins.

![url](img/18.png)

Hecho esto habremos acabado la configuración.

![ready](img/19.png)

Si hacemos clic en **Start using Jenkins** nos llevará al panel principal de Jenkins.

![panel](img/20.png)
