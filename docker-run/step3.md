## Correr un contenedor con Ubuntu

Vamos a utilizar el comando `docker run -it ubuntu bash`{{execute}} para correr un contenedor de Ubuntu. Una vez ejecutado ese comando Docker descargará la imagen y después correrá el comando, por lo que la terminal estará disponible para usarse cuando veamos un tty como el siguiente.

```
root@9df55f0a4335:/#
```

Ahora podremos ejecutar `apt-get update`{{execute}} para actualizar los repositorios y después ` apt-get install vim -y` para instalar vim.

Ahora exploremos los procesos del contenedor ejecutando `ps aux`{{execute}} y veremos que sólo hay dos procesos.

Después exploremos un poco el filesystem con el comando `ls /`{{execute}}.

Una vez explorado, ejecutamos `exit`{{execute}} para salirnos del contenedor y volver al host.