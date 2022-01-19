## 1. Configurar dominio.

Para esto simplemente debemos escribir lo siguiente en el archivo /etc/hosts:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsInstalacion/0.1.1.png)

Sustituyendo mi IP por la de su localhost.

## 2. Instalar Jenkins.

Primero agregamos la clave del repositorio al sistema:

```
wget - q - O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsInstalacion/1.1.1.png)

Ahora anexamos la dirección del repositorio de paquetes de Debian a sources.list:

```
sudo sh - c 'echo deb [http://pkg.jenkins.io/debian-stablebinary/](http://pkg.jenkins.io/debian-stablebinary/) > /etc/apt/sources.list.d/jenkins.list'
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsInstalacion/1.1.2.png)

Si fuese necesario, actualizamos los repositorios y el sistema:

```
sudo apt update && sudo apt upgrade
```

Por último, instalamos el Jenkins:

```
sudo apt install jenkins
```

## 3. Iniciar Jenkins.

Iniciamos Jenkins utilizando systemctl:

```
sudo systemctl start jenkins
```

Y verificamos que se haya iniciado correctamente:

```
sudo systemctl status jenkins
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsInstalacion/3.1.1.png)

## 4. Configurar el firewall.

Para abrir el puerto 8080 escribimos lo siguiente:

```
sudo ufw allow 8080
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsInstalacion/4.1.1.png)

Y comprobamos el estado del firewall para ver si se ha aplicado la regla:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsInstalacion/4.1.2.png)

Efectivamente, tenemos abierto el puerto 8080.


## 5. Configurar Jenkins.

Debemos acceder a la página inicial de Jenkins para empezar a configurarla:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsInstalacion/5.1.1.png)

Debemos acceder a la ubicación que se nos muestra para copiar la contraseña inicial yempezar la configuración inicial.

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsInstalacion/5.1.2.png)

Una vez comenzada la configuración, instalamos los plugins recomendados y dejamos quetrabaje.

Cuando nos muestre el formulario de creación del usuario admin, rellenamos los campos(EL CORREO DEBE SER REAL).

Luego de esto nos pedirá la URL que preferimos para Jenkins, colocamos la quepreparamos en el primer paso junto al puerto:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsInstalacion/5.1.3.png)

Y con esto habremos terminado:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsInstalacion/5.1.4.png)

Lo podemos comprobar accediendo al panel de control de Jenkins:


![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/JenkinsInstalacion/5.1.5.png)
