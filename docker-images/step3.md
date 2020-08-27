## Crear una imagen con entrypoint y cmd

Vamos a crear una nueva imagen con otro archivo `Dockerfile` pero esta vez utilizaremos las directivas `ENTRYPOINT` y `CMD` para levantar un servicio cuando creemos nuestro contenedor. Para ello crearemos el archivo Dockerfile de la siguiente manera:

```
cat <<EOF >> Dockerfile
FROM python:3
WORKDIR /app
RUN touch index.html && echo "Hola desde python :)" > index.html
ENTRYPOINT ["python3", "-m", "http.server", "--bind", "0.0.0.0"]
CMD ["9000"]
```{{execute}}

Explicaremos punto a punto qué hace cada directiva:

`FROM`. La imagen se basa en python en su versión 3.
`WORKDIR`. Utiliza el directorio `/app` como directorio de trabajo.
`RUN`. Después crea un archivo llamado `index.html` y agrega el texto `Hola desde python :)` al archivo. Con esta directiva podemos correr comandos de shell.
`ENTRYPOINT`. Para correr el servidor web utiliza el módulo `http.server` de python. Esta directiva nos sirve para indicar qué comando correrá el contendor cuando sea creado.
`CMD`. Concatenamos al final la cadena de texto "9000" que sirve como parámetro para el comando indicado en el entrypoint

Docker ejecutará el comando `python3 -m http.server --bind 0.0.0.0 9000` y dado que la última parte, `"9000"` se incluye a través de la directiva `CMD` entonces podemos cambiarla si lo deseamos al momento de correr el contenedor con `docker run`.

Ahora crearemos la imagen con el siguiente comando: 

```
docker buld -t servidor:1.0 .
```{{execute}}

Una vez creada la imagen podemos correr un contenedor en modo detached, exponiendo el puerto 9000.

```
docker run -d -p 9000:9000 servidor:1.0
```{{execute}}

Podemos ver si el contenedor se encuentra corriendo.

```
docker ps
```{{execute}}

Hagamos una petición al servicio con el comando `curl localhost:9000`{{execute}}.

Ahora vamos a probar si efectivamente podemos modificar el puerto sobreescribiendo el valor indicado en la directiva `CMD`. Lo haremos de la siguiente manera.

```
docker run -d -p 3000:3000 servidor:1.0 3000
```{{execute}}

Una vez creado el contenedor verificamos que efectivamente se encuentre corriendo.

```
docker ps
```{{execute}}

Y ahora hacemos una petición con curl pero esta vez usando el puerto 3000. `curl localhost:3000`{{execute}}.
