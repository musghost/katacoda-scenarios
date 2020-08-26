## Publicar o abrir un puerto en un contendor

Hasta ahora hemos creado contenedores de nginx pero no hemos hecho ninguna petición al servidor. Corramos nuevamente el comando que ejecutamos anteriormente para correr el contenedor de nginx `docker run -d --name front nginx`{{execute}}, si ejecutamos `docker ps`{{execute}} podemos ver que en la columna `PORTS` se indica que expone el puerto 80/tcp, pero si ejecutamos `curl localhost`{{execute}} el comando arroja un error diciendo que no se ha podido conectar... esto es porque no hemos publicado el puerto.

Vamos a borrar el contenedor con `docker rm --force front`{{execute}} y luego recrearlo pero ahora publicando el puerto 80 para poder abrir el puerto. Para ello ejecutaremos `docker run -d --name front -p 80 nginx`{{execute}} y si volvemos a ver los contenedores corriendo con `docker ps`{{execute}} podremos notar que en la columna `PORT` algo como `0.0.0.0:32768->80/tcp`. Esto significa que Docker asignó aleatoriamente un puerto en el host para mapear el puerto 80 en el host. Probablemente Docker asignó otro puerto diferente de 32768.

Ahora toma el puerto que Docker haya asignado y ejecuta `curl localhost:PUERTO`.

Vamos a borrar el contenedor nuevamente `docker rm --force front`{{execute}} y lo recrearemos pero ahora asignaremos el puerto 8080 al host también con el siguiente comando `docker run -d --name front -p 8080:80 nginx`{{execute}} para hacer que Docker escuche al puerto 8080 y sea mapeado al puerto 80 del contenedor.

Ahora podemos ejecutar el comando `curl localhost:8080`.
