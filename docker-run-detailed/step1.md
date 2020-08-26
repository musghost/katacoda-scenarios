## Correr un comando en modo detached

Para correr contenedores en modo detached tenemos que utilizar la opción `-d` del comando `docker run`.

Vamos a correr un contenedor de nginx en modo detached utilizando el siguiente comando `docker run -d nginx`{{execute}}.

Después de correrlo podemos ver que Docker imprime una cadena de texto, esta cadena es el ID del contenedor.

Veamos si nuestro contenedor está corriendo. Para ello utilizaremos el comando `docker ps`{{execute}}. 

Después de ejecutar el comando podemos ver que se encuentra corriendo si nos fijamos en el valor de la columna `Status`, que es `Running`.
