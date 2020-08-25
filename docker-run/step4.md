## Borrar un contenedor

Para borrar un contenedor necesitamos saber su nombre o ID. Primero vemos qué contenedores existen que no se encuentren corriendo, es decir, con status `Exited`, para ello utilizamos el comando `docker ps -a` y tomamos el valor de `Container ID` de cualquier contenedor y se lo pasamos como parámetro al comando `docker rm`.

Después de ejecutarlo vuelve a correr el comando `docker ps -a` para revisar que efectivamente el contenedor ha sido borrado.

