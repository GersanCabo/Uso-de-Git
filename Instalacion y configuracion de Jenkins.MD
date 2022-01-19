## 1. Configurar dominio.

Para esto simplemente debemos escribir lo siguiente en el archivo /etc/hosts:

Sustituyendo mi IP por la de su localhost.

## 2. Instalar Jenkins.

Primero agregamos la clave del repositorio al sistema:

```
wget - q - O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add
```

Ahora anexamos la dirección del repositorio de paquetes de Debian a sources.list:

```
sudo sh - c 'echo deb [http://pkg.jenkins.io/debian-stablebinary/](http://pkg.jenkins.io/debian-stablebinary/) > /etc/apt/sources.list.d/jenkins.list'
```

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

## 4. Configurar el firewall.

Para abrir el puerto 8080 escribimos lo siguiente:

```
sudo ufw allow 8080
```

Y comprobamos el estado del firewall para ver si se ha aplicado la regla:

Efectivamente, tenemos abierto el puerto 8080.


## 5. Configurar Jenkins.

Debemos acceder a la página inicial de Jenkins para empezar a configurarla:

Debemos acceder a la ubicación que se nos muestra para copiar la contraseña inicial yempezar la configuración inicial.

Una vez comenzada la configuración, instalamos los plugins recomendados y dejamos quetrabaje.

Cuando nos muestre el formulario de creación del usuario admin, rellenamos los campos(EL CORREO DEBE SER REAL).

Luego de esto nos pedirá la URL que preferimos para Jenkins, colocamos la quepreparamos en el primer paso junto al puerto:

Y con esto habremos terminado:


Lo podemos comprobar accediendo al panel de control de Jenkins:
