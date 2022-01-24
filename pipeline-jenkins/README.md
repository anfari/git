# Pipeline Jenkins

## Índice
- <a href="#1">Requisitos previos</a>
- <a href="#2">Creación Pipeline Java</a>
- <a href="#3">Pipeline Node.js</a>
- <a href="#4">Pipeline Ruby</a>
- <a href="#5">Pipeline Python</a>
- <a href="#6">Pipeline PHP</a>
- <a href="#7">Pipeline Go</a>
- <a href="#8">Panel de Control</a>



# <a name="1">Requisitos previos</a>

Necesitaremos instalar los plugins que nos permitirán que **docker** funcione correctamente, estos son:

* Docker
* Docker Pipeline

Para ello vamos al **Panel de Control → Gestor de plugins** y los buscamos en **Todos los plugins**.

![plugins](img/1.png)

Y esperamos a que se instalen.

![install](img/2.png)



# <a name="2">Creación Pipeline Java</a>

Lo primero será desde el **Panel de Control** seleccionar **Nueva Tarea**.

![new](img/3.png)

Especificaremos un nombre y seleccionamos **Pipeline**.

![name](img/4.png)

Nos aparecerá un menú con muchas opciones, las cuales no necesitaremos actualmente, añadimos una descripción si lo deseamos…

![options](img/5.png)

Y en la última opción añadimos las instrucciones a seguir.

![script](img/6.png)

Luego simplemente guardamos y lanzamos el Pipeline, en caso de que nos salga un error como el siguiente:

![error](img/7.png)

Podemos darnos cuenta de que el usuario Jenkins necesita pertenecer al grupo docker para tener los permisos necesarios, por lo que hacemos eso mismo.

![group](img/8.png)

Si volvemos a ejecutarlo el resultado será correcto.

![success](img/9.png)

En el Pipeline podemos ver una tabla con las últimas ejecuciones y sus resultados.

![pipeline](img/10.png)

Y en el Panel de control podemos consultar todos los Pipelines simultáneamente.

![panel](img/11.png)



# <a name="3">Pipeline Node.js</a>

Como ya hemos explicado la creación del Pipeline, a continuación solo mostraremos las instrucciones de cada uno y su resultado.

![script](img/12.png)

![success](img/13.png)



# <a name="4">Pipeline Ruby</a>

![script](img/14.png)

![success](img/15.png)



# <a name="5">Pipeline Python</a>

![script](img/16.png)

![success](img/17.png)



# <a name="6">Pipeline PHP</a>

![script](img/18.png)

![success](img/19.png)



# <a name="7">Pipeline Go</a>

![script](img/20.png)

![success](img/21.png)



# <a name="8">Panel de Control</a>

Finalmente, como se comentó anteriormente, podemos consultar el estado de todos los Pipelines simultáneamente desde el Panel de Control.

![panel](img/22.png)

Los iconos que vemos a la izquierda tienen su significado.

El primero significa el resultado de la última ejecución:

* El verde que ha funcionado correctamente.
* La X roja que ha fallado.
* Un icono girando que se encuentra en proceso.
* Un guion que se ha abortado.
* Una exclamación que es inestable.

El segundo icono tiene varios estados:

* Sol: Más del 80% de los test son correctos.
* Sol nublado: Entre el 61% y el 80% son correctos.
* Nublado: Entre el 41% y el 60$ son correctos.
* Lloviendo: Entre el 21% y el 40% son correctos.
* Tormenta: Menos del 21% son correctos.
