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

## 2. Pasos para realizar la instalación en local:

### 2.1 Actualización de los repositorios

Antes de instalar el Tomcat debemos asegurarnos de que nuestro sistema y nuestro repositorios de descarga estén actualizados a la última versión.

```
sudo apt update && sudo apt upgrade
```

### 2.2 Instalación de Apache-Tomcat

Instalamos la última versión estable de Tomcat 10 desde la página oficial, preferiblementeen formato .tar.gz, ya que es el más apropiado para Ubuntu.

Lo instalamos desde línea de comandos de la siguiente manera:

```
wget https://downloads.apache.org/tomcat/tomcat- 10 /v 10. 0. 12 /bin/apache-tomcat- 10. 0. 12 .tar.gz
```

- Creamos el nuevo usuario para Tomcat:

```
    sudo useradd - U - m - d /opt/tomcat - k /dev/null - s /bin/false tomcat
```

- Descomprimimos el paquete que acabamos de descargar en una ubicación lógica:

```
    sudo tar xf apache-tomcat- 10. 0. 12 .tar.gz - C /opt/tomcat/
```

- Le damos la propiedad de los archivos de Tomcat al usuario tomcat:

```
    sudo chown - R tomcat: /opt/tomcat/
```

- Creamos un enlace simbólico para ignorar el número de versión que está en elnombre de la carpeta del Tomcat y facilitarnos la instalación y la configuración:

```
   sudo ln - s /opt/tomcat/apache-tomcat- 10. 0. 12 / /opt/tomcat/apache-tomcat
```

- Ahora creamos un archivo de unidad para Systemd antes de empezar a configurar y,finalmente, iniciar el servicio:

```
   sudo nano /etc/systemd/system/tomcat 10 .service
```

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

- Iniciar el servicio:

```
    sudo systemctl start tomcat 10
```

- Verificamos el estado del servicio:
```
    systemctl status tomcat 10
```

- Activamos el inicio automático en el arranque:
```
    sudo systemctl enable tomcat 10
```
