# INSTALACIÓN DE WILDFLY

## Indice

- 1. Requisitos previos:
- 2. Pasos para la instalación:
   - 2.1. Actualización de los repositorios:
   - 2.2. Instalación de WildFly:
- 3. Configuración de WildFly:
- 4. Acceso a WildFly:
- 5. Añadir usuarios:
- 6. Gestionar la consola en remoto:

## 1. Requisitos previos:

Necesitaremos:

- Un servidor Ubuntu 20.04

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/1.1.1.png)

- Cuenta de superusuario root

    ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/1.1.2.png)

- JDK instalado:

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/1.1.3.png)

- Para ir adelantando, Maven instalado:

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/1.1.4.png)
  
## 2. Pasos para la instalación:

### 2.1. Actualización de los repositorios:

Primero, antes de empezar cualquier instalación, debemos actualizar el sistema y losrepositorios que usamos. Esto lo podemos hacer con el siguiente comando:

```
sudo apt update && sudo apt upgrade
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.1.1.png)

### 2.2. Instalación de WildFly:

Lo descargamos desde el repositorio oficial usando el comando wget junto al link del mismo:

```
wget https://github.com/wildfly/wildfly/releases/download/ 25. 0. 0 .Final/wildfly- 25. 0. 0 .Final.tar.gz
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.1.png)

- Creamos un nuevo grupo en el sistema para WildFly:

  ```
  sudo groupadd - r wildfly
  ```
  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.2.png)

- Creamos un nuevo usuario y lo introducimos en el grupo:

  ```
  sudo useradd - r - g wildfly - d /opt/wildfly - s /sbin/nologin wildfly
  ```
  
  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.3.png)

- Descomprimimos el paquete:

  ```
  tar - xvzf wildfly- 25. 0. 0 .Final.tar.gz
  ```
  
  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.4.png)

- Lo movemos a su ubicación definitiva:

  ```
  sudo mv wildfly- 25. 0. 0 .Final /opt/wildfly
  ```
  
  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.5.png)

- Damos acceso al usuario y grupo wildfly:

  ```
  sudo chown - R wildfly:wildfly /opt/wildfly/
  ```
  
  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.6.png)

- Creamos la carpeta /etc/wildfly antes de comenzar la configuración:

  ```
  sudo mkdir - p /etc/wildfly
  ```
  
  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.7.png)
  
- Copiamos el archivo .conf a esta nueva carpeta:

  ```
  sudo cp /opt/wildfly/docs/contrib/scripts/systemd/wildfly.conf /etc/wildfly/
  ```
  
  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.8.png)

- Terminamos de configurar el arranque con los siguientes comandos:

  ```
  sudo cp /opt/wildfly/docs/contrib/scripts/systemd/launch.sh /opt/wildfly/bin/
  sudo sh - c 'chmod +x /opt/wildfly/bin/*.sh'
  sudo cp /opt/wildfly/docs/contrib/scripts/systemd/wildfly.service /etc/systemd/system/
  sudo systemctl daemon-reload
  ```
  
  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.8.1.png)
  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.8.2png)

- Luego de esto, ya podremos iniciar el servicio:

  ```
  sudo systemctl start wildfly
  ```
  
  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.9.png)

- Verificamos que el servicio está iniciado:

  ```
  sudo systemctl status wildfly
  ```
  
  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.10.png)

- Habilitamos el inicio automático del servicio cada vez que iniciamos el equipo:

  ```
  sudo systemctl enable wildfly
  ```
  
  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/2.2.11.png)

## 3. Configuración de WildFly:

Tenemos que permitir el tráfico por algún puerto, en nuestro caso usaremos el puerto 8084.

Para ello debemos acceder al fichero donde se declara el puerto de entrada:

```
sudo nano /opt/wildfly/standalone/configuration/standalone.xml
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/3.1.1.png)

Y cambiar la siguiente sentencia:

```
<socket-binding name="http" port="${jboss.http.port: 8080 }"/>
```

Por esta:

```
<socket-binding name="http" port="${jboss.http.port: 8084 }"/>
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/3.1.2.png)

Y le decimos al firewall que permita el tráfico desde el puerto 8084:

```
sudo ufw allow 8084 /tcp
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/3.1.3.png)

## 4. Acceso a WildFly:

Tan solo tendremos que colocar en el navegador lo siguiente:

```
http://localhost/8084
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/4.1.1.png)

## 5. Añadir usuarios:

Primero creamos al usuario administrador ejecutando el siguiente script:

```
sudo /opt/wildfly/bin/add-user.sh
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/5.1.1.png)

Seleccionamos la opción a:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/5.1.2.png)

Y seguimos las indicaciones del script:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/5.1.3.png)

## 6. Gestionar la consola en remoto:

Primero entramos al archivo de configuración:

```
sudo nano /etc/wildfly/wildfly.conf
```

Y debemos añadir esta línea:

```
WILDFLY_CONSOLE_BIND= 0. 0. 0. 0
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/6.1.1.png)

Luego entramos a este otro fichero y verificamos que se encuentren estas líneas:

```
sudo nano /opt/wildfly/bin/launch.sh
```

```
$WILDFLY_HOME/bin/domain.sh - c $ 2 - b $ 3 - bmanagement $ 4
else
$WILDFLY_HOME/bin/standalone.sh - c $ 2 - b $ 3 - bmanagement $ 4
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/6.1.2.png)

Y reiniciamos el servicio para que se vuelva a iniciar con los cambios realizados:

```
sudo systemctl restart wildfly
```

Ahora editamos este otro fichero y colocamos lo siguiente:

```
sudo nano /etc/systemd/system/wildfly.service
ExecStart=/opt/wildfly/bin/launch.sh $WILDFLY_MODE $WILDFLY_CONFIG $WILDFLY_BIND
$WILDFLY_CONSOLE_BIND
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/6.1.3.png)

Reiniciamos el demonio y el servicio:

```
sudo systemctl daemon-reload
sudo systemctl restart wildfly
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/6.1.4.png)

Si queremos también podemos habilitar el acceso remoto a la consola de administraciónmodificando estas líneas en el fichero standalone.xml:

```
<interfaces>
<interface name="management">
<inet-address value="${jboss.bind.address.management: 127. 0. 0. 1 }"/>
</interface>
<interface name="public">
<inet-address value="${jboss.bind.address: 127. 0. 0. 1 }"/>
</interface>
</interfaces>
```

Para ello podemos comentar las etiquetas inet-address o indicar que la IP pública es 0.0.0.

