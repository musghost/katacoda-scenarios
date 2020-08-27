## Crear una imagen con docker commit

Vamos a crear una imagen que contenga el programa vim. Para ello primero correremos un contenedor interactivo `docker run -it --name vim-contenedor ubuntu bash`{{execute}}.

Una vez adentro del contenedor instalaremos vim con `apt-get update && apt-get install vim -qqy`{{execute}}.

Cuando vim haya sido instado podemos acceder a él ejecutando `vim`{{execute}}. Para salir de vim tienes que ejecutar `:q`{{execute}}... esperamos que puedas salir de vim :S

Salimos del contenedor con `exit`{{execute}} para regresar al host y ahora crearemos una imagen basándonos en el contenido del contenedor que acabamos de ejecutar en el cual instalamos vim.

Ejecutaremos el comando `docker commit -m "Imagen con vim" vim-contenedor vim:1.0`. Con ello indicamos que vamos crear una imagen basándonos en el contendo del contenedor llamado `vim-contenedor` y la imagen será llamada `vim` y tendrá el tag `1.0`.

Una vez ejecutado ahora podemos listar las imágenes y ver que efectivamente está ahi con `docker images`.

Ahora correremos un contendor interactivo utilizando la nueva imagen con el comando `docker run -it vim:1.0 vim`. Y podemos ver que abre directamente el comando `vim`. Para salir de vim tienes que ejecutar nuevamente `:q`{{execute}}... nuevamente esperamos que puedas salir de vim :S
