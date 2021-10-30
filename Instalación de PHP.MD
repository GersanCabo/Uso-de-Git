# Instalación de PHP

## Indice

- 1. Requisitos previos:
- 2. Instalar PHP:
- 3. Configurar PHP:
- 4. Probar PHP:

## 1. Requisitos previos:

Debemos disponer de:

- Un servidor Ubuntu 20.04:
- Un usuario non-root que tenga privilegios sudo.

## 2. Instalar PHP:

Primero actualizamos el sistema y la lista de paquetes:

```
sudo apt update && sudo apt upgrade
```

Después de esto, ya podremos instalar PHP para Apache:

```
sudo apt install -y php
```

Y lo instalamos también para Nginx:

```
sudo apt install -y php-fpm
```

## 3. Configurar PHP:

Configuramos Nginx para conectar con el servicio PHP-FPM, para ello editamos el siguiente archivo:

```
sudo nano /etc/nginx/sites-available/default
```

Y activamos el bloque location dejándolo de la siguiente manera:


Y recargamos la configuración de Nginx:

```
sudo systemctl reload nginx
```

## 4. Probar PHP:

Creamos un archivo PHP para poder probarlo en nuestro servidor:

```
sudo nano /var/www/html/info.php
```

Y escribimos lo siguiente:

Por último, accedemos al archivo mediante la dirección de nuestro servidor:
