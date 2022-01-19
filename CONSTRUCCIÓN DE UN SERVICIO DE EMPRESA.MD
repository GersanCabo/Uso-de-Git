## 1. Preparación de los contenedores:

Para empezar, creamos la siguiente estructura de directorios:

Y en los archivos ponemos lo siguiente:

- **docker-compose.yml:** En este archivo tenemos declarado el servidor, la base de
    datos, el PHPMyAdmin y servidor SFTP. En este último hemos creado un usuario
    llamado test.

```
version: "3.5"
services:
www:
  build:.
  ports:
    "8090:80"
  volumes:
    ./www:/var/www
  links:
    db
  networks:
    default
db:
  image: mysql:8.
  ports:
    "3306:3306"
  command: --default-authentication-plugin=mysql_native_password
  environment:
    MYSQL_DATABASE: dbname
    MYSQL_ROOT_PASSWORD: test
  volumes:
    ./dump:/docker-entrypoint-initdb.d
    ./conf:/etc/mysql/conf.d
  persistent:/var/lib/mysql
  networks:
    default
phpmyadmin:
  image: phpmyadmin/phpmyadmin
  links:
    db:db
  ports:
    8000:
  environment:
    MYSQL_USER: root
    MYSQL_PASSWORD: test
    MYSQL_ROOT_PASSWORD: test
sftp:
  image: atmoz/sftp
  ports:
    "9922:22"
  command: test:test:1001:12345:/gersan-home
  networks:
    default
    
volumes:
  persistent:
 
 ```

- **Dockerfile:** Aquí realizo las instalaciones y activacionesde modulos de Apache
    pertinentes:

```
FROM php:8.0.0-apache
ARG DEBIAN_FRONTEND=noninteractive
RUN docker-php-ext-install mysqli
RUN apt-get update \
&& apt-get install -y libzip-dev \
&& apt-get install -y zlib1g-dev \
&& rm -rf /var/lib/apt/lists/* \
&& docker-php-ext-install zip

RUN a2enmod rewrite
```

- **script.sql:** Aquí tendremos una base de datos de ejemplo:

```
SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
SET time_zone = "+00:00";

CREATE TABLE `Blog` (
`id` int( 11 ) NOT NULL,
`name` varchar( 20 ) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

INSERT INTO `Blog` (`id`, `name`) VALUES ( 1 , 'Articulos Java'), ( 2 ,
'Articulos Php'), ( 3 , 'Articulos Phyton'), ( 4 , 'Articulos JavaScript');

```

- **index.php:** Esta sera la pagina de inicio:

```
<html>
  <head>
    <title>Gersán System Home</title>
  </head>
  <body>
    <?php echo '<p>Pagina inicial de Gersán System</p>'; ?>
  </body>
</html>
```

## 2. Levantamos los contenedores:

Realizamos un **sudo docker-compose up -d** en el directoriocorrespondiente:

Y comprobamos que podemos acceder correctamente desde la maquina local:


Como vemos funciona la página principal y se muestra la frase generada mediante PHP, por
lo que también se ha realizado correctamente la instalación de PHP.

Por otro lado, también vemos que podemos acceder al PHPMyAdmin y que esté, a su vez,
tiene acceso a la base de datos MySQL.

Para finalizar, observamos que la conexión mediante SFTP se realiza y que el directorio
home del usuario “test” aparece.


## 3. Camuflamos la IP mediante un proxy inverso:

Debemos primero activar una serie de modulos de nuestro Apache local:

```
sudo a2enmod proxy a2enmod proxy_http a2enmod proxy_ajp a2enmod rewrite a2enmod deflate a2enmod
headers a2enmod proxy_balancer a2enmod proxy_connect a2enmod proxy_html a2enmod lbmethod_byrequests
```
Y reiniciamos Apache:

```
systemctl restart apache2
```
Ahora debemos editar **etc/apache2/sites-available/000-default.conf** y cambiar lo
siguiente:

Guardamos los cambios y colocamos esta sentencia en **/etc/hosts:**

Con esto, al colocar el dominio nos direccionará a la IP de nuestra máquina que, a su vez,
nos redireccionará al puerto correspondiente del servidor Docker.
