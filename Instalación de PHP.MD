# Instalación de PHP

## Indice

- 1. Requisitos previos:
- 2. Instalar PHP:
- 3. Configurar PHP:
- 4. Probar PHP:

## 1. Requisitos previos:

Debemos disponer de:

- Un servidor Ubuntu 20.04:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionNginx/1.1.1.png)

- Un usuario non-root que tenga privilegios sudo.

## 2. Instalar PHP:

Primero actualizamos el sistema y la lista de paquetes:

```
sudo apt update && sudo apt upgrade
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionPHP/1.1.1.png)

Después de esto, ya podremos instalar PHP para Apache:

```
sudo apt install -y php
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionPHP/1.1.2.png)

Y lo instalamos también para Nginx:

```
sudo apt install -y php-fpm
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionPHP/1.1.3.png)

## 3. Configurar PHP:

Configuramos Nginx para conectar con el servicio PHP-FPM, para ello editamos el siguiente archivo:

```
sudo nano /etc/nginx/sites-available/default
```

Y activamos el bloque location dejándolo de la siguiente manera:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionPHP/2.1.1.png)

Y recargamos la configuración de Nginx:

```
sudo systemctl reload nginx
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionPHP/2.1.2.png)

## 4. Probar PHP:

Creamos un archivo PHP para poder probarlo en nuestro servidor:

```
sudo nano /var/www/html/info.php
```

Y escribimos lo siguiente:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionPHP/3.1.1.png)

Por último, accedemos al archivo mediante la dirección de nuestro servidor:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/InstalacionPHP/3.1.2.png)
