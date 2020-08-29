## Reutilizar volúmenes

Vamos a crear un volumen llamado `base_datos` de la siguiente manera `docker volume create`{{execute}}.

Ahora descargamos la imagen de postgres con el comando `docker pull postgres`{{execute}}.

Lo que haremos será utilizar ese volumen que creamos para montarlo a un contenedor de postgres. Vamos correr el siguiente comando.

```
docker run -d --name base_postgres \
    -e POSTGRES_PASSWORD=root \
    -v base_datos:/var/lib/postgresql/data \
    postgres
```{{execute}}

Una vez que esté corriendo el contenedor vamos a inyectar un proceso de bash `docker exec -it base_postgres psql -U postgres -p`{{execute}} y recuerda que la contraseña que le asignamos es `root`.

Ahora crearemos una base de datos ejecutando `CREATE DATABASE ejemplo;`{{execute}}.

Después nos conectamos a esa base de datos `\c ejemplo`{{execute}} y creamos una tabla `CREATE TABLE tabla_ejemplo (name text);`{{execute}}. Y para terminar insertamos algún dato `INSERT INTO tabla_ejemplo (name) VALUES ('Amsterdam');`.

Nos salimos del contenedor y lo borramos. `docker rm --force postgresdb`{{execute}}. Después vemos que efectivamente se encuentre borrado com `docker ps -a`{{execute}}.

Ahora vamos a volver a crear otro contenedor y le vamos a montar el mismo volumen para ver que efectivamente nuestros datos sigan ahí.

```
docker container run -d --name postgresdb -v volumen-postgres postgres
```{{execute}}

Ahora podemos ejecutar los siguentes comandos para ver que la base de datos sigue ahí.

```
docker container exec -it postgresdb psql
\l
\c ejemplo
\dt
select * from tabla_ejemplo;
```

