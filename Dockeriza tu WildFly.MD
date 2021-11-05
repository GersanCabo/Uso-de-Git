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

Dentro de esta carpeta creamos el Dockerfile:

```
nano Dockerfile
```

Y le añadimos la siguiente configuración:


## 2. Construcción de la imagen:

La construiremos con el siguiente comando:

```
sudo docker build -q --rm --tag=jboss/wildfly:25.0.0.Final-config .
```

Verificamos que existe la imagen dentro del docker:

```
sudo docker images
```

Como podemos ver, esta la primera en la lista, así que se ha construido la imagen correctamente.


## 3. Uso de la nueva imagen:

Ahora probaremos la imagen que hemos creado:

```
sudo docker run -d -p 8080:8080 -p 9990:9990 -p 8009:8009 --name servidor-wilfly-config -it
jboss/wildfly:25.0.0.Final-config
```

Después de esto, ejecutamos la siguiente sentencia para ver si nuestro contenedor estácorriendo:

```
sudo docker ps -a
```

Entramos al servidor de WildFly como lo hemos hecho anteriormente:

Y probamos si nos deja entrar en la consola de administración con el usuario admin:

Como podemos ver funciona correctamente y nos deja entrar a la consola sin problema.
