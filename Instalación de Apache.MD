## Indice

1. <a href="#1-requisitos-previos">Requisitos previos:</a>
2. <a href="#2-pasos-para-realizar-la-instalación-en-local">Pasos para realizar la instalación en local:</a>
   - 2.1 Actualización de los repositorios:
   - 2.2 Instalación de Apache:
3. <a href="#3-acceso">Acceso:</a>


## 1. Requisitos previos:

Necesitaremos:

- Un servidor Ubuntu 20.04
- Cuenta de superusuario root

## 2. Pasos para realizar la instalación en local:

### 2.1 Actualización de los repositorios:

Primero actualizamos los repositorios y el sistema con los siguientes comandos:

```
sudo apt update && sudo apt upgrade
```
![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Apache/2.1.1.png)

### 2.2 Instalación de Apache:

Abrimos una terminal y escribimos lo siguiente:

```
sudo apt install apache 2
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Apache/2.2.1.png)

Es posible que nos aparezca este error:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Apache/2.2.2.png)

Esto es debido a un conflicto de puertos, por lo que debemos cambiar el puerto que usa pordefecto Apache (puerto 80).

Debemos realizar algunos cambios en este archivo:

```
sudo nano /etc/apache 2 /ports.conf
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Apache/2.2.3.png)

Y debemos cambiar el puerto 80 por otro puerto, en nuestro caso lo cambiaremos al 8081:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Apache/2.2.4.png)

Reiniciamos los servicios para que empiecen a escuchar por este puerto:

```
sudo systemctl restart apache 2
sudo service apache 2 restart
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Apache/2.2.5.png)

Luego de esto, ajustamos el firewall para que permita el tráfico desde el puerto sin cifrar:

```
sudo ufw allow 8081
```

Lo podemos verificar con el siguiente comando:

```
sudo ufw status
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Apache/2.2.6.png)


Por último, verificamos que está corriendo Apache correctamente:

```
sudo systemctl status apache2
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Apache/2.2.7.png)

## 3. Acceso:

Para comprobar si el servicio se está ejecutando correctamente colocamos en el navegador
la dirección **localhost: 8081** y debería mostrarnos la siguiente página:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Apache/3.1.1.png)
