## Correr un contenedor con el comando docker run

Vamos a correr un contenedor de Docker sencillo. Para ello utilizarás el comando `docker run nginx`{{execute}}.

Notarás que docker descargará la imagen de Docker Registry, ya que no se encuentra en el host.

```
Using default tag: latest
latest: Pulling from library/nginx
bf5952930446: Pull complete 
cb9a6de05e5a: Pull complete 
9513ea0afb93: Pull complete 
b49ea07d2e93: Pull complete 
a5e4a503d449: Pull complete 
Digest: sha256:b0ad43f7ee5edbc0effbc14645ae7055e21bc1973aee5150745632a24a752661
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest
```

Ahora puedes detener el contenedor con la combinación de teclas `Ctrl+C`.
