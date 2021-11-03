# Instalación de WildFly en Docker

## Indice

**1. Descarga la imagen del docker WildFly:**

## 1. Descarga la imagen del docker WildFly:

Primero descargaremos la versión 25.0.0.Final de la imagen oficial de WildFly para Docker:

```
sudo docker pull jboss/wildfly: 25.0.0.Final
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionWildlyDocker/1.1.1.png)

Ahora miramos el listado de imágenes descargadas:

```
sudo docker images
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionWildlyDocker/1.1.2.png)

Como vemos, se encuentra ahí nuestra imagen descargada, con lo que ahora solo nos queda arrancar un contenedor con la imagen y comprobar si nos funciona el servidor:

```
sudo docker run -d -p 5000:8080 --name "servidor-desa" jboss/wildfly
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionWildlyDocker/1.1.3.png)

Por último, para acceder a WildFly debemos conocer el IP del contenedor, así que usamosel comando ip a:

```
ip a
```

Y debemos buscar una salida como esta:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionWildlyDocker/1.1.4.png)

Como vemos ahi, la IP del contenedor es 172.17.0.1, así que, para terminar, la colocamos en el navegador junto al puerto correspondiente, en este caso el 5000 de nuestra máquina:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionWildlyDocker/1.1.5.png)
