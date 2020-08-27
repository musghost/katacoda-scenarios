## Eliminar imágenes

Para borrar una imagen debemos hacer uso del comando `docker rmi` y pasar como parámetro el nombre o el ID de la imagen que queremos borrar.

Vamos a listar las imágenes con `docker images`{{execute}}.

Después borramos alguna imagen tomando su nombre como referencia. Por ejemplo, podemos borrar la imagen que creamos `servidor:1.0` de la siguiente manera `docker rmi servidor:1.0`{{execute}}.
