# Dockeriza tu WildFly


## Indice

- 1. Creación del fichero dockerfile:
- 2. Construcción de la imagen:
- 3. Uso de la nueva imagen:


## 1. Creación del fichero dockerfile:

Primero creamos el directorio de trabajo y entramos en él, lo podemos hacer de la siguiente forma:

```
mkdir wildfly-config
cd wildfly-config
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/DockerizandoWildfly/1.1.1.png)

Dentro de esta carpeta creamos el Dockerfile:

```
nano Dockerfile
```

Y le añadimos la siguiente configuración:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/DockerizandoWildfly/1.1.2.png)

## 2. Construcción de la imagen:

La construiremos con el siguiente comando:

```
sudo docker build -q --rm --tag=jboss/wildfly:25.0.0.Final-config .
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/DockerizandoWildfly/2.1.1.png)

Verificamos que existe la imagen dentro del docker:

```
sudo docker images
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/DockerizandoWildfly/2.1.2.png)

Como podemos ver, esta la primera en la lista, así que se ha construido la imagen correctamente.


## 3. Uso de la nueva imagen:

Ahora probaremos la imagen que hemos creado:

```
sudo docker run -d -p 8080:8080 -p 9990:9990 -p 8009:8009 --name servidor-wilfly-config -it
jboss/wildfly:25.0.0.Final-config
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/DockerizandoWildfly/3.1.1.png)

Después de esto, ejecutamos la siguiente sentencia para ver si nuestro contenedor estácorriendo:

```
sudo docker ps -a
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/DockerizandoWildfly/3.1.2.png)

Entramos al servidor de WildFly como lo hemos hecho anteriormente:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/DockerizandoWildfly/3.1.3.png)

Y probamos si nos deja entrar en la consola de administración con el usuario admin:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/DockerizandoWildfly/3.1.4.png)

Como podemos ver funciona correctamente y nos deja entrar a la consola sin problema.
