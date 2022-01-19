
> **IES Puerto de la Cruz Telesforo Bravo**

![](https://github.com/GersanCabo/Uso-de-Git/tree/main/img/vertopal_c67f3f4db0e148c9a5b5244f2870e65a/media/image1.png){width="4.458333333333333in"
height="1.7083333333333333in"}

![](https://github.com/GersanCabo/Uso-de-Git/tree/main/img/vertopal_c67f3f4db0e148c9a5b5244f2870e65a/media/image2.png){width="5.0625in"
height="1.7083333333333333in"}

> **CONSTRUCCIÓN DE UN SERVICIO DE EMPRESA**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

**\_\_\_\_**

**DESPLIEGUE DE APLICACIONES WEB**

Autor:

Gersán Cabo Del Pino

**[Indice]{.ul}**

+------------------------------------------------------+-------+
| > **1. Preparación de los contenedores:**            | **3** |
+======================================================+=======+
| > **2. Levantamos los contenedores:**                | **5** |
+------------------------------------------------------+-------+
| > **3. Camuflamos la IP mediante un proxy inverso:** | **7** |
+------------------------------------------------------+-------+
| > **LINK:**                                          | **7** |
+------------------------------------------------------+-------+

> **1. Preparación de los contenedores:**
>
> Para empezar, creamos la siguiente estructura de directorios:

![](https://github.com/GersanCabo/Uso-de-Git/tree/main/img/vertopal_c67f3f4db0e148c9a5b5244f2870e65a/media/image3.png){width="4.009722222222222in"
height="1.7388877952755906in"}

> Y en los archivos ponemos lo siguiente:

+----------------------------------+----------------------------------+
|                                  | > **docker-compose.yml:** En     |
|                                  | > este archivo tenemos declarado |
|                                  | > el servidor, la base de        |
+==================================+==================================+
| > datos, el PHPMyAdmin y         |                                  |
| > servidor SFTP. En este último  |                                  |
| > hemos creado un usuario        |                                  |
+----------------------------------+----------------------------------+
| > llamado test.                  |                                  |
+----------------------------------+----------------------------------+
| version: \"3.5\"                 |                                  |
+----------------------------------+----------------------------------+
| services:                        |                                  |
+----------------------------------+----------------------------------+
| > www:                           |                                  |
+----------------------------------+----------------------------------+
| > build: .                       |                                  |
+----------------------------------+----------------------------------+
| > ports:                         |                                  |
+----------------------------------+----------------------------------+
| > \- \"8090:80\"                 |                                  |
+----------------------------------+----------------------------------+
| > volumes:                       |                                  |
+----------------------------------+----------------------------------+
| > \- ./www:/var/www              |                                  |
+----------------------------------+----------------------------------+
| > links:                         |                                  |
+----------------------------------+----------------------------------+
| > \- db                          |                                  |
+----------------------------------+----------------------------------+
| > networks:                      |                                  |
+----------------------------------+----------------------------------+
| > \- default                     |                                  |
+----------------------------------+----------------------------------+
| > db:                            |                                  |
+----------------------------------+----------------------------------+
| > image: mysql:8.0               |                                  |
+----------------------------------+----------------------------------+
| > ports:                         |                                  |
+----------------------------------+----------------------------------+
| > \- \"3306:3306\"               |                                  |
+----------------------------------+----------------------------------+
| > command:                       |                                  |
| > \--default-authenticat         |                                  |
| ion-plugin=mysql_native_password |                                  |
+----------------------------------+----------------------------------+
| > environment:                   |                                  |
+----------------------------------+----------------------------------+
| > MYSQL_DATABASE: dbname         |                                  |
+----------------------------------+----------------------------------+
| > MYSQL_ROOT_PASSWORD: test      |                                  |
+----------------------------------+----------------------------------+
| > volumes:                       |                                  |
+----------------------------------+----------------------------------+
| > \-                             |                                  |
| > ./                             |                                  |
| dump:/docker-entrypoint-initdb.d |                                  |
+----------------------------------+----------------------------------+
| > \- ./conf:/etc/mysql/conf.d    |                                  |
+----------------------------------+----------------------------------+
| > \- persistent:/var/lib/mysql   |                                  |
+----------------------------------+----------------------------------+
| > networks:                      |                                  |
+----------------------------------+----------------------------------+

+----------------------------------+----------------------------------+
| > \- default                     |                                  |
+==================================+==================================+
| > phpmyadmin:                    |                                  |
+----------------------------------+----------------------------------+
| > image: phpmyadmin/phpmyadmin   |                                  |
+----------------------------------+----------------------------------+
| > links:                         |                                  |
+----------------------------------+----------------------------------+
| > \- db:db                       |                                  |
+----------------------------------+----------------------------------+
| > ports:                         |                                  |
+----------------------------------+----------------------------------+
| > \- 8000:80                     |                                  |
+----------------------------------+----------------------------------+
| > environment:                   |                                  |
+----------------------------------+----------------------------------+
| > MYSQL_USER: root               |                                  |
+----------------------------------+----------------------------------+
| > MYSQL_PASSWORD: test           |                                  |
+----------------------------------+----------------------------------+
| > MYSQL_ROOT_PASSWORD: test      |                                  |
+----------------------------------+----------------------------------+
| > sftp:                          |                                  |
+----------------------------------+----------------------------------+
| > image: atmoz/sftp              |                                  |
+----------------------------------+----------------------------------+
| > ports:                         |                                  |
+----------------------------------+----------------------------------+
| > \- \"9922:22\"                 |                                  |
+----------------------------------+----------------------------------+
| > command:                       |                                  |
| > t                              |                                  |
| est:test:1001:12345:/gersan-home |                                  |
+----------------------------------+----------------------------------+
| > networks:                      |                                  |
+----------------------------------+----------------------------------+
| > \- default                     |                                  |
+----------------------------------+----------------------------------+
| volumes:                         |                                  |
+----------------------------------+----------------------------------+
| > persistent:                    |                                  |
+----------------------------------+----------------------------------+
| \-                               | > **Dockerfile:** Aquí realizo   |
|                                  | > las instalaciones y            |
|                                  | > activaciones de modulos de     |
|                                  | > Apache                         |
+----------------------------------+----------------------------------+
| > pertinentes:                   |                                  |
+----------------------------------+----------------------------------+
| FROM php:8.0.0-apache            |                                  |
+----------------------------------+----------------------------------+
| ARG                              |                                  |
| DEBIAN_FRONTEND=noninteractive   |                                  |
+----------------------------------+----------------------------------+
| RUN docker-php-ext-install       |                                  |
| mysqli                           |                                  |
+----------------------------------+----------------------------------+
| RUN apt-get update \\            |                                  |
+----------------------------------+----------------------------------+
| > && apt-get install -y          |                                  |
| > libzip-dev \\                  |                                  |
+----------------------------------+----------------------------------+
| > && apt-get install -y          |                                  |
| > zlib1g-dev \\                  |                                  |
+----------------------------------+----------------------------------+
| > && rm -rf                      |                                  |
| > /var/lib/apt/lists/\* \\       |                                  |
+----------------------------------+----------------------------------+
| > && docker-php-ext-install zip  |                                  |
+----------------------------------+----------------------------------+
| RUN a2enmod rewrite              |                                  |
+----------------------------------+----------------------------------+

+----------------------------------+----------------------------------+
|                                  | **script.sql:** Aquí tendremos   |
|                                  | una base de datos de ejemplo:    |
+==================================+==================================+
| > SET SQL_MODE =                 |                                  |
| > \"NO_AUTO_VALUE_ON_ZERO\";     |                                  |
+----------------------------------+----------------------------------+
| > SET time_zone = \"+00:00\";    |                                  |
+----------------------------------+----------------------------------+
| > CREATE TABLE \`Blog\` (        |                                  |
+----------------------------------+----------------------------------+
| > \`id\` int(11) NOT NULL,       |                                  |
+----------------------------------+----------------------------------+
| > \`name\` varchar(20) NOT NULL  |                                  |
+----------------------------------+----------------------------------+
| > ) ENGINE=InnoDB DEFAULT        |                                  |
| > CHARSET=latin1;                |                                  |
+----------------------------------+----------------------------------+
| > INSERT INTO \`Blog\` (\`id\`,  |                                  |
| > \`name\`) VALUES (1,           |                                  |
| > \'Articulos Java\'), (2,       |                                  |
+----------------------------------+----------------------------------+
| \'Articulos Php\'), (3,          |                                  |
| \'Articulos Phyton\'), (4,       |                                  |
| \'Articulos JavaScript\');       |                                  |
+----------------------------------+----------------------------------+
|                                  | **index.php:** Esta sera la      |
|                                  | pagina de inicio:                |
+----------------------------------+----------------------------------+
| \<html\>                         |                                  |
+----------------------------------+----------------------------------+
| > \<head\>                       |                                  |
+----------------------------------+----------------------------------+
| > \<title\>Gersán System         |                                  |
| > Home\</title\>                 |                                  |
+----------------------------------+----------------------------------+
| > \</head\>                      |                                  |
+----------------------------------+----------------------------------+
| > \<body\>                       |                                  |
+----------------------------------+----------------------------------+
| > \<?php echo \'\<p\>Pagina      |                                  |
| > inicial de Gersán System       |                                  |
| > \</p\>\'; ?\>                  |                                  |
+----------------------------------+----------------------------------+
| > \</body\>                      |                                  |
+----------------------------------+----------------------------------+
| > \</html\>                      |                                  |
+----------------------------------+----------------------------------+

> **2. Levantamos los contenedores:**
>
> Realizamos un **sudo docker-compose up -d** en el directorio
> correspondiente:
>
> ![](https://github.com/GersanCabo/Uso-de-Git/tree/main/img/vertopal_c67f3f4db0e148c9a5b5244f2870e65a/media/image4.png){width="6.156943350831146in"
> height="1.0208333333333333in"}
>
> Y comprobamos que podemos acceder correctamente desde la maquina
> local:

![](https://github.com/GersanCabo/Uso-de-Git/tree/main/img/vertopal_c67f3f4db0e148c9a5b5244f2870e65a/media/image5.png){width="3.520832239720035in"
height="0.9375in"}

![](https://github.com/GersanCabo/Uso-de-Git/tree/main/img/vertopal_c67f3f4db0e148c9a5b5244f2870e65a/media/image6.png){width="6.270833333333333in"
height="4.886111111111111in"}

![](https://github.com/GersanCabo/Uso-de-Git/tree/main/img/vertopal_c67f3f4db0e148c9a5b5244f2870e65a/media/image7.png){width="6.270833333333333in"
height="1.8333333333333333in"}

> Como vemos funciona la página principal y se muestra la frase generada
> mediante PHP, por lo que también se ha realizado correctamente la
> instalación de PHP.
>
> Por otro lado, también vemos que podemos acceder al PHPMyAdmin y que
> esté, a su vez, tiene acceso a la base de datos MySQL.
>
> Para finalizar, observamos que la conexión mediante SFTP se realiza y
> que el directorio home del usuario "test" aparece.
>
> **3. Camuflamos la IP mediante un proxy inverso:**
>
> Debemos primero activar una serie de modulos de nuestro Apache local:

sudo a2enmod proxy a2enmod proxy_http a2enmod proxy_ajp a2enmod rewrite
a2enmod deﬂate a2enmod

headers a2enmod proxy_balancer a2enmod proxy_connect a2enmod proxy_html
a2enmod lbmethod_byrequests

> Y reiniciamos Apache:

systemctl restart apache2

> Ahora debemos editar **etc/apache2/sites-available/000-default.conf**
> y cambiar lo siguiente:

![](https://github.com/GersanCabo/Uso-de-Git/tree/main/img/vertopal_c67f3f4db0e148c9a5b5244f2870e65a/media/image8.png){width="2.9680555555555554in"
height="1.0319444444444446in"}

> Guardamos los cambios y colocamos esta sentencia en **/etc/hosts:**

![](https://github.com/GersanCabo/Uso-de-Git/tree/main/img/vertopal_c67f3f4db0e148c9a5b5244f2870e65a/media/image9.png){width="2.8652777777777776in"
height="0.2916666666666667in"}

> Con esto, al colocar el dominio nos direccionará a la IP de nuestra
> máquina que, a su vez, nos redireccionará al puerto correspondiente
> del servidor Docker.

![](https://github.com/GersanCabo/Uso-de-Git/tree/main/img/vertopal_c67f3f4db0e148c9a5b5244f2870e65a/media/image10.png){width="4.218055555555556in"
height="1.0527777777777778in"}

> **LINK:**
