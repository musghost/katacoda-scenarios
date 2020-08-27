## Crear una imagen con docker build

Para crear una imagen con el comando `docker build` necesitamos utilizar un archivo llamado Dockerfile. Ese archivo nos sirve para colocar directivas con las cuales podemos construir la imagen. En el siguiente ejemplo vamos a construir una imagen con las mismas características que la anterior:

1. Imagen basada en Ubuntu.
2. Actualizaremos los paquetes con apt-get.
3. Instalaremos vim.

Para ello crearemos un archivo llamado `Dockerfile` de la siguiente manera:

```
cat <<EOF >> Dockerfile
FROM debian
RUN apt-get update
RUN apt-get install -qqy vim
EOF
```{{execute}}

Una vez creado el archivo podemos crear la imagen con el siguiente comando.

```
docker buld -t vim:2.0 .
```{{execute}}

Una vez creada la imagen de Docker vamos a correr un contenedor y verificar que efectivamente podemos correr el comando vim

```
docker run -it vim:2.0 vim
```{{execute}}

Podemos salir de vim ejecutando `:wq`{{execute}}.

