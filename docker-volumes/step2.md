## Montar archivos de configuración

Para montar archivos de configuración generalmente usamos el método bind-mount de Docker lo cual significa montar un archivo o directorio que se encuentre fuera del directorio `/var/lib/docker/volumes` por lo que Docker no puede usar el comando `docker volume` para administrarlos.

Para hacer un ejemplo práctico vamos a crear un archivo llamado `index.html` y ahí colocaremos un documento de HTML que después serviremos con un contenedor de nginx.

Primero creamos el archivo con el comando `touch ~/index.html`{{execute}} y después agregamos el contendido con el siguiente comando.

```
cat <<EOF >> index.html
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Hola. Estoy en un contenedor :)</title>
</head>
<body>
	<h1>Soy un archivo en un host,</h1>
	<p>Pero también en un contenedor. Es fácil de explicar...</p>
</body>
</html>
EOF
```{{execute}}

Ahora usaremos ese archivo para montarlo en un contenedor de nginx y servirlo como página web.

```
docker container run -d --name servidor-nginx -v $PWD:/usr/share/nginx/html -p 8080:80 nginx
```{{execute}}

Una vez corriendo el contenedor vamos a hacer una petición al contenedor de nginx.

```
curl localhost:8080
```{{execute}}

Podemos montar directorios y/o archivos a cualquier contenedor por lo que no tenemos que montar cada archivo que queramos reflejar en el contendor.