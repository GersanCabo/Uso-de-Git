# Instalación de Apache-Tomcat

## Indice

1. <a href="#1-requisitos-previos">Requisitos previos:</a>
2. <a href="#2-pasos-para-realizar-la-instalación-en-local">Pasos para realizar la instalación en local:</a>
   - 2.1 Actualización de los repositorios:
   - 2.2 Instalación de Apache-Tomcat:
3. <a href="#3-acceso-a-apache-tomcat">Acceso a Apache-Tomcat:</a>

## 1. Requisitos previos:

Necesitaremos:

- Un servidor Ubuntu 20.04
- Cuenta de superusuario root
- Tener Java instalado (Lo podemos comprobar con java-version)


   ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/1.1.1.png)



## 2. Pasos para realizar la instalación en local:

### 2.1 Actualización de los repositorios

Antes de instalar el Tomcat debemos asegurarnos de que nuestro sistema y nuestro repositorios de descarga estén actualizados a la última versión.

```
sudo apt update && sudo apt upgrade
```


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/2.1.1.png)



### 2.2 Instalación de Apache-Tomcat

Instalamos la última versión estable de Tomcat 10 desde la página oficial, preferiblementeen formato .tar.gz, ya que es el más apropiado para Ubuntu.

Lo instalamos desde línea de comandos de la siguiente manera:

```
wget https://downloads.apache.org/tomcat/tomcat- 10 /v 10. 0. 12 /bin/apache-tomcat- 10. 0. 12 .tar.gz
```


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/2.2.1.png)



- Creamos el nuevo usuario para Tomcat:

```
    sudo useradd - U - m - d /opt/tomcat - k /dev/null - s /bin/false tomcat
```


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/2.2.2.png)



- Descomprimimos el paquete que acabamos de descargar en una ubicación lógica:

```
    sudo tar xf apache-tomcat- 10. 0. 12 .tar.gz - C /opt/tomcat/
```


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/2.2.3.png)



- Le damos la propiedad de los archivos de Tomcat al usuario tomcat:

```
    sudo chown - R tomcat: /opt/tomcat/
```


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/2.2.4.png)



- Creamos un enlace simbólico para ignorar el número de versión que está en elnombre de la carpeta del Tomcat y facilitarnos la instalación y la configuración:

```
   sudo ln - s /opt/tomcat/apache-tomcat- 10. 0. 12 / /opt/tomcat/apache-tomcat
```


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/2.2.5.png)



- Ahora creamos un archivo de unidad para Systemd antes de empezar a configurar y,finalmente, iniciar el servicio:

```
   sudo nano /etc/systemd/system/tomcat 10 .service
```


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/2.2.6.png)



Y copiamos lo siguiente:

```
[Unit]
Description=Tomcat 10. 0 servlet container para Ubuntu 20. 04 LTS
After=network.target
[Service]
Type=forking
User=tomcat
Group=tomcat
Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom"
Environment="CATALINA_BASE=/opt/tomcat/apache-tomcat"
Environment="CATALINA_HOME=/opt/tomcat/apache-tomcat"
Environment="CATALINA_PID=/opt/tomcat/apache-tomcat/temp/tomcat.pid"
Environment="CATALINA_OPTS=-Xms 512 M - Xmx 1024 M - server - XX:+UseParallelGC"
ExecStart=/opt/tomcat/apache-tomcat/bin/startup.sh
ExecStop=/opt/tomcat/apache-tomcat/bin/shutdown.sh
[Install]
WantedBy=multi-user.target
```


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/2.2.7.png)



- Iniciar el servicio:

```
    sudo systemctl start tomcat 10
```


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/2.2.8.png)



- Verificamos el estado del servicio:
```
    systemctl status tomcat 10
```


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/2.2.9.png)



- Activamos el inicio automático en el arranque:
```
    sudo systemctl enable tomcat 10
```


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/2.2.10.png)



## 3. Acceso a Apache-Tomcat:

Como ya hemos instalado anteriormente el Apache y el GitLab, tenemos ocupado el puerto 8080, con lo que entramos al server.xml ubicado en /opt/tomcat/apache-tomcat-xx.x.xx/conf para cambiar el puerto por defecto por el que conecta el Tomcat.

Encontraremos algo así:


![Connector port = 8080](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/3.1.1.png)



Y debemos cambiarlo a esto:


![Connector port = 8083](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/3.1.2.png)



Y reiniciamos el servicio:


![sudo systemctl restart tomcat10](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/3.1.3.png)



Ahora solo nos quedaría verificar que está corriendo Tomcat en el puerto 8083, para ello entramos a la barra de dirección del navegador y colocamos lo siguiente en la dirección:

```
localhost:8083 
    o
nuestraIP:8083
```


Y nos deberia salir una página de inicio como esta:


![Pagina de inicio de Tomcat](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20TomCat/3.1.4.png)
