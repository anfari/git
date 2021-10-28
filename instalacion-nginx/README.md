# Instalación Nginx

## Índice
- <a href="#1">Requisitos previos</a>
- <a href="#2">Instalar Nginx</a>
- <a href="#3">Ajustes de firewall</a>
- <a href="#4">Configurar bloques de servidor</a>
- <a href="#5">Comprobar su servidor web</a>



# <a name="1">Requisitos previos</a>

Necesitaremos tener un servidor **Ubuntu** y un usuario no root con privilegios de sudo.

# <a name="2">Instalar Nginx</a>

Antes de realizar cualquier instalación es recomendable actualizar nuestro índice local de paquetes:

```
sudo apt update
```

![update](img/1.png)

Ya que Nginx está disponible en los repositorios de Ubuntu, podemos instalarlo ejecutando:

```
sudo apt install nginx
```

![install](img/2.png)


# <a name="3">Ajustes de firewall</a>

Lo primero que debemos hacer tras la instalación es permitir el acceso al servicio en el firewall, para ello listaremos las aplicaciones con las que **ufw** sabe trabajar con:

```
sudo ufw app list
```

![ufw_list](img/3.png)

Ya que solamente utilizaremos el puerto “80” u 84 en nuestro caso pues lo cambiaremos más adelante, habilitaremos **Nginx HTTP**:

```
sudo ufw allow 'Nginx HTTP'
```

![ufw_allow](img/4.png)

Podemos verificarlo consultando las excepciones con:

```
sudo ufw status
```

![ufw_status](img/5.png)


# <a name="4">Configurar bloques de servidor</a>

Los bloques de servidor nos permiten encapsular los detalles de la configuración y alojar más de un dominio en el mismo servidor, por lo que configuraremos un dominio **your_domain**, siendo el primer paso crear su directorio:

```
sudo mkdir -p /var/www/your_domain/html
```

![mkdir](img/6.png)

Y asignamos con la variable **$USER** el propietario:

```
sudo chown -R $USER:$USER /var/www/your_domain/html
```

![chown](img/7.png)

Y ejecutamos el siguiente comando para asegurarnos unos permisos correctos:

```
sudo chmod -R 755 /var/www/your_domain
```

![chmod](img/8.png)

Y creamos un index.html de ejemplo:

```
sudo nano /var/www/your_domain/html/index.html
```

![index.html](img/9.png)

Creamos un nuevo archivo de configuración para nuestro dominio donde especificaremos también el puerto que utilizaremos:

```
sudo nano /etc/nginx/sites-available/your_domain
```

![your_domain](img/10.png)

Habilitamos el archivo creando un enlace simbólico en **sites-enabled**:

```
sudo ln -s /etc/nginx/sites-available/your_domain /etc/nginx/sites-enabled/
```

![ln -s](img/11.png)

Modificamos el fichero **/etc/nginx/nginx.conf** y descomentamos la linea **#server_names_hash_bucket_size** para evitar un problema de memoria que pueda surgir al agregar nombres de servidor:

```
sudo nano /etc/nginx/nginx.conf
```

![nginx.conf](img/12.png)

Comprobamos que los archivos de Nginx no tengan errores de sintaxis:

```
sudo nginx -t
```

![nginx -t](img/13.png)

Y reiniciamos el servicio de Nginx:

```
sudo systemctl restart nginx
```

![restart](img/14.png)


# <a name="5">Comprobar su servidor web</a>

Ejecutamos el siguiente comando para comprobar el estado del servicio:

```
sudo systemctl status nginx
```

![status](img/15.png)

Si accedemos desde el navegador comprobaremos que se muestra nuestra página.

![web](img/16.png)

Por último podemos modificar el archivo **/etc/hosts** para acceder con el nombre de dominio:

```
sudo nano /etc/hosts
```

![hosts](img/17.png)

Y ahora podemos acceder desde cualquiera de estos nombres.

![web](img/18.png)
