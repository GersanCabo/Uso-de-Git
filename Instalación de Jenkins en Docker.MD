## Indice

- 1. Bajar y arrancar la imagen de Jenkins:
   - 1.1. Bajar la imagen
   - 1.2. Arrancar la imagen
- 2. Instalar y arrancar Jenkins a través de Docker:
   - 2.1. Construcción del Dockerfile
   - 2.2. Construcción del plugins.txt
   - 2.3. Construcción de docker-compose.yml
   - 2.4. Construcción de la imagen
- LINK:


## 1. Bajar y arrancar la imagen de Jenkins:

### 1.1. Bajar la imagen

Nos descargamos esta imagen:

```
sudo docker pull jenkins/jenkins:lts
```

Cuando termine la descarga, comprobamos que se haya bajado:

```
sudo docker images
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsDocker/1.1.1.png)

### 1.2. Arrancar la imagen

Ahora ejecutamos un contenedor a partir de esta imagen:

```
docker run - p 8080 : 8080 - p 50000 : 50000 - v /home/gersan:/var/jenkins_home jenkins/jenkins:lts
```

Y verificamos que podemos ingresar:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsDocker/1.2.1.png)

Y a partir de aquí podríamos seguir con el punto 5 de la <a href='https://github.com/GersanCabo/Uso-de-Git/blob/main/Instalacion%20y%20configuracion%20de%20Jenkins.MD'>anterior práctica</a>.


## 2. Instalar y arrancar Jenkins a través de Docker:

### 2.1. Construcción del Dockerfile

```
FROM jenkins/jenkins

USER root
RUN apt-get -y update && apt-get install -y maven

USER jenkins
COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt
```

**Línea 1:** Seleccionamos nuestra imagen de Jenkins

**Línea 3:** Iniciamos como el usuario root

**Línea 4** : Actualizamos los repositorios e instalamos Maven

**Línea 6** : Iniciamos como el usuario jenkins

**Línea 7:** Copiamos el archivo plugins.txt desde nuestrodirectorio local al directorio indicado en la máquina.

**Línea 8:** Arrancamos el script encargado de instalarlos plugins que indicamos en plugins.txt

### 2.2. Construcción del plugins.txt

Aquí colocaremos los plugins que nos interesa instalar, en nuestro caso serán <a href='https://github.com/GersanCabo/Uso-de-Git/blob/main/txt/plugins.txt'>estos</a>.

### 2.3. Construcción de docker-compose.yml

```
version: '3'
services:
master:
  build:.
  image: dpl/jenkins:latest
  restart: unless-stopped
  hostname: jenkins
  ports:
    "8080:8080"
    "50000:50000"
  volumes:
    jenkins_home:/var/jenkins_home
    
volumes:
  jenkins_home:
```

En este fichero indicamos a Docker el nombre del directorio donde construiremos la imagen, la imagen que utilizaremos para el mismo, puertos, etc.

### 2.4. Construcción de la imagen

Colocamos el siguiente comando para crear la imagen a partir de estos ficheros:

```
docker-compose build
```

Y, si no ha sucedido ningún error en la descarga de los plugins, ya podremos colocar este comando para arrancar el contenedor a partir de esta imagen:

```
docker-compose up - d
```
Y comprobamos que podemos acceder desde el navegador:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsDocker/2.4.1.png)

Para acceder a la contraseña inicial colocamos el siguiente comando:

```
docker exec - it jenkinsdocker_master_ 1 cat /var/jenkins_home/secrets/initialAdminPassword
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsDocker/2.4.2.png)

Y a partir de aquí podríamos seguir con el punto 5 de la <a href='https://github.com/GersanCabo/Uso-de-Git/blob/main/Instalacion%20y%20configuracion%20de%20Jenkins.MD'>anterior práctica</a>.
