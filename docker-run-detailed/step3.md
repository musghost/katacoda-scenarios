## Asignar un nombre a un contenedor

Todos los contenedores que hemos creado hasta este momento han tenido nombres aleatorios y esto es porque Docker los forma concatenando un adjetivo calificativo màs el nombre de un científico famoso, en Inglés.

Para nombrar un contenedor podemos hacer uso de la opción `-n` en el comando `docker run`.

Correremos un contenedor con nginx y le asignaremos el nombre `front`, lo haremos con el comando `docker run -d --name front nginx`{{execute}}. Si ejecutamo el comando `docker ps`{{execute}} podremos ver que el contendor tiene el nombre que le acabamos de asignar.

Vayamos de regreso al ejemplo del contenedor con Ubuntu. Vamos a correr un contenedor interactivo nuevo, pero esta vez asignaremos un nombre. Ejecutamos el comando `docker run -it --name terminal ubuntu bash`{{execute}}.

Si nos salimos y volvemos a listar los contenedores con `docker ps -a` podremos ver que también tiene un nombre. Para volver a entrar al contenedor podemos utilizar `docker start terminal`{{execute}} y `docker attach terminal`{{execute}}.

Nos salimos con `exit`{{execute}} del contenedor para estar nuevamente en el host.