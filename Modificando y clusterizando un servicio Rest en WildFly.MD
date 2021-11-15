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

