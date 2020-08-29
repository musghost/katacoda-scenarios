## Administrar volúmenes

Como lo vimos anteriormente, para administrar los volúmenes necesitamos utilizar el comando `docker volume`.

Vamos a listar los volúmenes existentes con `docker volume ls`{{execute}}. Y después podemos borrarlos utilizando el comando `docker volume rm ` que recibe como argumento el ID o nombre del volumen.

Si queremos borrar un volúmen que esté ocupado por un contenedor que se encuentre corriendo entonces primero tenemos que detemer y borrar el contenedor. Una vez que el volumen se encuentre libre entonces podremos borrarlo sin problema alguno.