# Modificando y clusterizando un servicio Rest en WildFly


## Indice

- 1. Instalación de WildFly en Docker:
- 2. Dockerizar WildFly:
   - 2.1 Creación del fichero Dockerfile:
   - 2.2 Construcción de la imagen:
- 3. Desplegar clusters de WildFly:
   - 3.1 Preparamos el proyecto:
   - 3.2 Desplegamos los clusters:
- 4. Instalar BBDD y PHPMyAdmin:
   - 4.1 Preparamos el proyecto:
   - 4.2 Desplegamos y probamos:


## 1. Instalación de WildFly en Docker:

Si no tenemos descargada la imagen de WildFly, la descargamos:

```
sudo docker pull jboss/wildfly: 25. 0. 0 .Final
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/1.1.1.png)

Y comprobamos que se ha descargado la imagen:

```
sudo docker images
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/1.1.2.png)


## 2. Dockerizar WildFly:

### 2.1 Creación del fichero Dockerfile:

Primero debemos crear un directorio de trabajo y ubicarnos en él, podemos hacerlo de la
siguiente forma:

```
mkdir wildfly-config
cd wildfly-config
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/2.1.1.png)

Dentro de esta carpeta creamos el Dockerfile:

```
nano Dockerfile
```

Y le añadimos la siguiente configuración:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/2.1.2.png)

### 2.2 Construcción de la imagen:

La construiremos con el siguiente comando:

```
sudo docker build -q --rm --tag=jboss/wildfly: 25. 0. 0 .Final-config.
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/2.2.1.png)

Verificamos que existe la imagen dentro del docker:

```
sudo docker images
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/2.2.2.png)

Como podemos ver, esta la primera en la lista, así que se ha construido la imagen
correctamente.

## 3. Desplegar clusters de WildFly:

### 3.1 Preparamos el proyecto:

Descargamoseste proyectoy probamos que Maven funcionacorrectamente antes de seguir
con los pasos:

```
mvn clean install
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/3.1.1.png)

Luego de esto, empezamos a crear los ficheros necesarios para desplegar los cluster de
WildFly con este proyecto, para empezar creamos dentro del proyecto el fichero Dockerfile,
que debe contener lo siguiente:

```
FROM jboss/wildfly: 25. 0. 0 .Final-config

ARG WAR_FILE=target/*.war
##COPY ${JAR_FILE} app.jar

ADD ${ARG} /opt/jboss/wildfly/standalone/deployments/

ARG WILDFLY_NAME
ARG CLUSTER_PW

ENV WILDFLY_NAME=${WILDFLY_NAME}
ENV CLUSTER_PW=${CLUSTER_PW}

ENTRYPOINT /opt/jboss/wildfly/bin/standalone.sh - b= 0. 0. 0. 0 - bmanagement= 0. 0. 0. 0

- Djboss.server.default.config=standalone-full-ha.xml - Djboss.node.name=${WILDFLY_NAME}
- Djava.net.preferIPv 4 Stack=true - Djgroups.bind_addr=$(hostname - i)
- Djboss.messaging.cluster.password=${CLUSTER_PW}
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/3.1.2.png)

Y creamos el docker-compose.yml en la misma ubicación:

```
version: ' 3. 5 '
services:

wildfly 1 :
build:
context:.
args:
WILDFLY_NAME: wildfly_ 1
CLUSTER_PW: secret_password
image: wildfly_ 1
ports:

- 8080 : 8080
networks:
wildfly_network:

wildfly 2 :
build:
context:.
args:
WILDFLY_NAME: wildfly_ 2
CLUSTER_PW: secret_password
image: wildfly_ 2
ports:

- 8081 : 8080
networks:
wildfly_network:

wildfly 3 :
build:
context:.
args:
WILDFLY_NAME: wildfly_ 3
CLUSTER_PW: secret_password
image: wildfly_ 3
ports:

- 8082 : 8080
networks:
wildfly_network:

networks:
wildfly_network:
ipam:
driver: default
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/3.1.3.png)

### 3.2 Desplegamos los clusters:

Desplegamos todo con el siguiente comando estando ubicados en al carpeta del proyecto:

```
docker-compose up
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/3.2.1.png)

Y, como vemos, ahora tenemos acceso a WildFly desde los tres puertos:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/3.2.2.png)
![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/3.2.3.png)
![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/3.2.4.png)

Y, como no, también es accesible la aplicación helloworld-rs desde WildFly:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/3.2.5.png)
![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/3.2.6.png)

## 4. Instalar BBDD y PHPMyAdmin:

### 4.1 Preparamos el proyecto:

La estructura de la carpeta que vamos a crear para desplegar el servidor de la base de
datos, va a ser el siguiente:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/4.1.1.png)

Creamos las carpetas respectivas y empezamos a crear los ficheros empezando por el
**Dockerfile** :

```
FROM php: 8. 0. 0 - apache
ARG DEBIAN_FRONTEND=noninteractive
RUN docker-php-ext-install mysqli
RUN apt-get update \
&& apt-get install - y libzip-dev \
&& apt-get install - y zlib 1 g-dev \
&& rm - rf /var/lib/apt/lists/* \
&& docker-php-ext-install zip

RUN a 2 enmod rewrite
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/4.1.2.png)

Luego pasamos al fichero **docker-compose.yml** :

```
version: " 3. 5 "
services:
db:
image: mysql: 8. 0
ports:

- " 3306 : 3306 "
command: - -default-authentication-plugin=mysql_native_password
environment:
MYSQL_DATABASE: dbname
MYSQL_ROOT_PASSWORD: test
volumes:
- ./dump:/docker-entrypoint-initdb.d
- ./conf:/etc/mysql/conf.d
- persistent:/var/lib/mysql
networks:
- default
phpmyadmin:
image: phpmyadmin/phpmyadmin
links:
- db:db
ports:
- 8000 : 80
environment:
MYSQL_USER: admin
MYSQL_PASSWORD: test
MYSQL_ROOT_PASSWORD: test
volumes:
persistent:
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/4.1.3.png)

Y seguimos con el fichero **dbname.sql** :

```
SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
SET time_zone = "+ 00 : 00 ";

/*! 40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*! 40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*! 40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*! 40101 SET NAMES utf 8 mb 4 */;

CREATE TABLE `Data` (
`id` int( 11 ) NOT NULL,
`name` varchar( 20 ) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin 1 ;

INSERT INTO `Data` (`id`, `name`) VALUES ( 1 , 'OpenWebinars Article'), ( 2 , 'Crashell'), ( 3 , 'Jerson Martinez'), ( 4 ,
'Antonio Moreno');


#### /*! 40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;

#### /*! 40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;

#### /*! 40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/4.1.4.png)

### 4.2 Desplegamos y probamos:

Volvemos a desplegar todos los servidores utilizando el comando anterior:

```
sudo docker-compose up - d
```

Y confirmamos que podemos acceder al PHPMyAdmin y que conecta con la base de datos:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/4.2.1.png)

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/RestWildflyDocker/4.2.2.png)
