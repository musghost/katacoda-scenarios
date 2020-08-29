## Montar volúmenes a contenedores

Montar volúmenes en Docker no es más que hacer que un directorio en el host sea visible en el filesystem de un contenedor.

La manera más sencilla de montar volúmenes a contenedores es utilizando la opción `-v` del comando `docker run`. Podemos montar dos tipos de volúmenes: bind-mount y volúmenes.

Bind-mount monta directorios que no están administrados por Docker. Y cuando hablamos de volúmenes de Docker nos referemos a los directorios que Docker administra y guarda en `/var/lib/docker/volumes`.

Comenzaremos por montar un volumen de la manera más sencilla posible corriendo el comando `docker run -n cont_vol -it -v /directorio ubuntu bash`{{execute}}.

Una vez adentro del contenedor podemos ver que el directorio `/directorio` se encuentra en el filesystem del contenedor y lo podemos comprobar ejecutando `ls -la /`{{execute}}.

Si accedemos al contenedor con `cd /directorio`{{execute}} y creamos un par de archivos con `touch archivo1 && touch archivo2`{{execute}} podremos verlos reflejados en el host.

Después nos salimos del contenedor con `exit`{{execute}}.

```
docker inspect cont_vol || grep -A5 Mounts
```{{execute}}

Si revisamos el contenido del directorio indicado en el valor de `Source` con el comando `ls -la` podremos ver que los archivos que creamos dentro del contenedor se encuentran ahí.

Podemos también ver que Docker creó un objeto tipo volumen automáticamente al cual asignó un nombre aleatorio. Si ejecutamos `docker volume ls`{{execute}} podemos ver que el volumen aparece ahí. Si ejecutamos `docker volume inspect ` y le pasamos el ID del volumen entonces veremos la misma información.
