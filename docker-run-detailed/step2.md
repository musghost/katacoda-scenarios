## Correr contenedores interactivos

Ahora toca correr un contenedor interactivo. Para ello podemos hacer uso de la opción `-t`, con la que indicamos que vamos a requerir un `tty`, o sea, una terminal. También necesitamos utilizar la opción `-i` que indica que el contenedor será interactivo. Podríamos escribir las dos opciones por separado, como `docker run -i -t`, pero generalmente las escribimos juntas para ahorrarnos unos caracteres: `docker run -it`.

Para este ejemplo correremos un contenedor de Ubuntu de forma interactiva con el comando `docker run -it ubuntu bash`{{execute}}.

Una vez andentro del contenedor podemos ejecutar los comandos que queramos, tal como `apt-get update`{{execute}} y luego podemos instalar paquetes, por ejemplo `apt-get install -y vim`{{execute}}... y sí, esto lo hemos visto en la sección pasada, pero ahora conoces un poco más las opciones que utilizamos para correr este contenedor.

Podemos salirnos del contenedor con el comando `exit`{{execute}}. Esto nos llevará de regreso al host y dado que el contenedor ha terminado el proceso de bash cuando nos salimos entonces el contenedor dejará de correr sólo podremos ver su estado corriendo `docker ps -a` en la columna `Status`.

Para volver a correr el mismo contenedor ejecutamos `docker start ` + el nombre del contendor o su ID. Pero cuando lo iniciemos veremos que no sucede nada, es decir, no estamos dentro del contendor, para ello podemos ejecutar el comando `docker attach ` + el nombre del contenedor. A veces hay que dar doble Enter para poder ver de nuevo la terminal del contenedor.

Una vez adentro, podemos ejecutar los comandos que queramos y luego `exit`{{execute}} para regresar al host.