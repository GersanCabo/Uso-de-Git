# Instalación de Nginx


## Indice

- 1. Requisitos previos:
- 2. Instalar Nginx:
- 3. Aplicar ajustes al firewall:
- 4. Comprobar servidor web:
- 5. Administrar Nginx:
- 6. Configurar bloques de servidor:
- LINK:


## 1. Requisitos previos:

Debemos disponer de:

- Un servidor Ubuntu 20.04:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/1.1.1.png)

- Un usuario non-root que tenga privilegios sudo.


## 2. Instalar Nginx:

Primero debemos actualizar el sistema operativo y nuestros repositorios antes de instalarnada:

```
sudo apt update && sudo apt upgrade
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/2.1.1.png)

Procedemos a instalar Nginx desde los repositorios de Ubuntu:

```
sudo apt install nginx
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/2.1.2.png)


## 3. Aplicar ajustes al firewall:

Primero deberíamos enumerar los perfiles con los que sabe trabajar el firewall:

```
sudo ufw app list
```


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/3.1.1.png)

Como podemos ver, Nginx cuenta con tres perfiles:

- Nginx Full: Este perfil abre el puerto 80 (http) y el 443 (https).
- Nginx HTTP: Este perfil abre el puerto 80.
- Nginx HTTPS: Este perfil abre el puerto 443.
- 
Normalmente elegiriamos el HTTPS, pero, para esta práctica , activaremos el HTTP.

Podemos hacerlo con el siguiente comando:

```
sudo ufw allow ‘Nginx HTTP’
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/3.1.2.png)

Verificamos los cambios:

```
sudo ufw status
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/3.1.3.png)


## 4. Comprobar servidor web:

Nos aseguramos de que el servicio está en activo:

```
systemctl status nginx
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/3.1.4.png)

Hemos probado a iniciar el servicio pero nos mandaba un error un poco ambiguo, de todas maneras, tras reiniciar la máquina se ha arreglado:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/3.1.5.png)

Sabemos que esta activado, ahora procedemos a comprobar que funciona, para ellocolocamos en el navegador nuestra IP pública de la siguiente manera:

```
http://your_server_ip
```

Para conocer nuestra IP podremos, por ejemplo, conectarnos aforma: <a href="icanhazip.com">icanhazip.com</a> de esta

```
curl - 4 icanhazip.com
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/3.1.6.png)

Al colocarla en el navegador nos aparece la página de acceso al router:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/3.1.7.png)


## 5. Administrar Nginx:

Repasaremos algunos de los comandos básicos de administración de servicios:

Para detener nuestro servidor utilizamos lo siguiente:

```
sudo systemctl stop nginx
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/4.1.1.png)

Para iniciar nuestro servidor utilizamos este:

```
sudo systemctl start nginx
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/4.1.2.png)

Para detener e iniciar seguidamente nuestro servidor podemos usar este:

```
sudo systemctl restart nginx
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/4.1.3.png)

Para recargar las configuraciones del servicio podemos utilizar este comando:

```
sudo systemctl reload nginx
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/4.1.4.png)

Para deshabilitar el inicio del servicio al encender el servidor, debemos usar este comando:

```
sudo systemctl disable nginx
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/4.1.5.png)

Para volver a habilitarlo:

```
sudo systemctl enable nginx
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/4.1.6.png)


## 6. Configurar bloques de servidor:

Crearemos el directorio your_domain, que será nuestro dominio de ejemplo provisional.

```
sudo mkdir - p /var/www/your_domain/html
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/6.1.1.png)

Ponemos la propiedad del directorio a la variable de entorno $USER:

```
sudo chown - R $USER:$USER /var/www/your_domain/html
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/6.1.2.png)

Para asegurarnos de tener los permisos correctos y proteger los archivos, ejecutamos elsiguiente comando:

```
sudo chmod - R 755 /var/www/your_domain
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/6.1.3.png)

Después de esto, creamos una página de ejemplo para probar nuestro dominio:

```
nano /var/www/your_domain/html/index.html
```

Y escribimos en ella un html simple, como este por ejemplo:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/6.1.4.png)

Para que Nginx presente este contenido debemos crear un archivo de configuración paraeste dominio:

```
sudo nano /etc/nginx/sites-available/your_domain
```

Y debe tener esto en su interior esto:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/6.1.5.png)

Luego de esto, creamos un enlace entre este archivo y el directorio sites-enabled:

```
sudo ln - s /etc/nginx/sites-available/your_domain/etc/nginx/sites-enabled/
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/6.1.6.png)

Para evitar posibles problemas relacionados con la memoria de depósito de hash por elnombre del servidor, tenemos que realizar un pequeño ajuste en nginx.conf descomentando una línea:

```
sudo nano /etc/nginx/nginx.conf
```

La línea es esta:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/6.1.7.png)

A continuación comprobamos que no hayamos escrito algo de forma errónea en los archivos de Nginx:

```
sudo nginx - t
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/6.1.8.png)

Si hemos obtenido un resultado afirmativo, reiniciamos el servicio para que corra con losnuevos cambios.

```
sudo systemctl restart nginx
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/6.1.9.png)
