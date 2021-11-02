# Instalación Docker

## Indice

- 1. Instalar Docker:
- 2. Trabajar con imágenes de Docker:
- 3. Administrar contenedores de Docker:
- LINK:

## 1. Instalar Docker:

Primero actualizamos nuestras listas de paquetes:

```
sudo apt update
```

A continuación, instalamos algunos paquetes necesarios para seguir con la instalación:

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

Añadimos la clave GPG para trabajar con el repositorio oficial de Docker y tener así la versión más reciente:

```
curl - fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Agregamos el repositorio de Docker a las fuentes de APT:

```
sudo add-apt-repository "deb [arch=amd 64 ] https://download.docker.com/linux/ubuntu focal stable"
```

Volvemos a actualizar la lista de paquetes, ya que ahora tenemos la de Docker:

```
sudo apt update
```

Antes de instalar, nos aseguramos de que se va a instalar la versión del repositorio deDocker y no la de Ubuntu.

```
apt-cache policy docker-ce
```

Como vemos, el candidato principal es el que se descarga desde el repositorio de Docker,así que podemos proseguir.

Y, por fin, instalamos Docker:

```
sudo apt install docker-ce
```

Y comprobamos que está corriendo:

```
sudo systemctl status docker
```

Si el resultado es similar al que muestro en la imagen, significa que ha arrancado correctamente y que ya está corriendo en nuestro sistema.

## 2. Trabajar con imágenes de Docker:

Para comprobar que podemos descargar y arrancar las imágenes alojadas en Docker Hub,escribimos lo siguiente:

```
sudo docker run hello-world
```

Y nos mostrará algo como lo siguiente:

## 3. Administrar contenedores de Docker:

Para ver los contenedores que tenemos activos, usamos este comando:

```
sudo docker ps
```

Si queremos incluir a los inactivos en la lista, añadimos un -a:

```
sudo docker ps -a
```

Para ver el último contenedor que hemos creado, añadimos un -l:

```
sudo docker ps -l
```

Con sudo docker images listaremos la imagen de la que se derivó la nuestra:

```
sudo docker images
```
