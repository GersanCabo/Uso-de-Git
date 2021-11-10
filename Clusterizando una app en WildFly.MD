# Clusterizando una app en WildFly


## Indice

- 1. Requisitos previos:
- 2. Preparamos el proyecto:
- 3. Desplegando el cluster de JBoss con Docker:
- LINK:


## 1. Requisitos previos:

Antes tendremos que instalar docker-compose:

```
sudo apt install docker-compose
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/1.1.1.png)


## 2. Preparamos el proyecto:

Descargamoseste proyecto, al cual le realizaremosun pequeño cambio.

- En el fichero web.xml sustituimos:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/2.1.1.png)

- Por:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/2.1.2.png)

Guardamos y lanzamos el siguiente comando en la carpeta del proyecto:

```
mvn clean install
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/2.1.3.png)

Tras esto, ya podremos arrancar el proyecto, lo probaremos con el siguiente comando:

```
mvn clean jetty:run
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/2.1.4.png)

Y accedemos mediante el navegador utilizando el puerto 8082:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/2.1.5.png)


## 3. Desplegando el cluster de JBoss con Docker:

Primero construiremos el fichero Dockerfile dentro de la carpeta de nuestra aplicación y le
añadimos lo siguiente:

```
FROM jboss/wildfly

ARG WAR_FILE=target/*.war
##COPY ${JAR_FILE} app.jar

ADD ${ARG} /opt/jboss/wildfly/standalone/deployments/

ARG WILDFLY_NAME
ARG CLUSTER_PW

ENV WILDFLY_NAME=${WILDFLY_NAME}
ENV CLUSTER_PW=${CLUSTER_PW}

ENTRYPOINT /opt/jboss/wildfly/bin/standalone.sh -b=0.0.0.0 -bmanagement=0.0.0.0 -Djboss.server.default.config=standalone-full-ha.xml -Djboss.node.name=${WILDFLY_NAME} -Djava.net.preferIPv4Stack=true -Djgroups.bind_addr=$(hostname -i) -Djboss.messaging.cluster.password=${CLUSTER_PW}

```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/3.1.1.png)

Como vemos, Dockerfile realizará el copiado del .war dentro de la carpeta deployments,
esto es necesario para que después podamos arrancarlo como cluster


Después de esto creamos otro fichero más en el mismo sitio, el docker-compose.yml, el
cual tendrá este contenido:

```
version: '3.5'
services:

  wildfly1:
    build:
      context: .
      args:
        WILDFLY_NAME: wildfly_1
        CLUSTER_PW: secret_password
    image: wildfly_1
    ports:
    - 8080:8080
    networks:
      wildfly_network:

  wildfly2:
    build:
      context: .
      args:
        WILDFLY_NAME: wildfly_2
        CLUSTER_PW: secret_password
    image: wildfly_2
    ports:
    - 8081:8080
    networks:
      wildfly_network:

networks:
  wildfly_network:
    ipam:
      driver: default

```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/3.1.2.png)

Por último, ejecutamos la sentencia docker-compose up para arrancar el cluster de dos
nodos que hemos creado:

```
docker-compose up
```
Nos aparece este error:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/3.1.3.png)

Lo hemos solucionado reconstruyendo la imagen con el siguiente comando:

```
docker-compose build
```

Y volvemos a colocar el comando anterior:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/3.1.4.png)

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/3.1.5.png)

Ya funciona WildFly por ambos puertos, por el 8081 y por el 8080:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/3.1.6.png)

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/ClusterWildFly/3.1.7.png)
