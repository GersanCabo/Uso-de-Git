## Indice

- 1. Requisitos previos:
- 2. Pasos para realizar la instalación en local:
   - 2.1 Actualización de los repositorios:
   - 2.2 Instalación de Apache:
- 3. Acceso:


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
![](){width="5.323611111111111in"
height="0.21877843394575677in"}

### 2.2 Instalación de Apache:

Abrimos una terminal y escribimos lo siguiente:

```
sudo apt install apache 2
```

Es posible que nos aparezca este error:

Esto es debido a un conflicto de puertos, por lo que debemos cambiar el puerto que usa pordefecto Apache (puerto 80).

Debemos realizar algunos cambios en este archivo:

```
sudo nano /etc/apache 2 /ports.conf
```


Y debemos cambiar el puerto 80 por otro puerto, en nuestro caso lo cambiaremos al 8081:

Reiniciamos los servicios para que empiecen a escuchar por este puerto:

```
sudo systemctl restart apache 2
sudo service apache 2 restart
```

Luego de esto, ajustamos el firewall para que permita el tráfico desde el puerto sin cifrar:

```
sudo ufw allow 8081
```

Lo podemos verificar con el siguiente comando:

```
sudo ufw status
```

Por último, verificamos que está corriendo Apache correctamente:

```
sudo systemctl status apache2
```


## 3. Acceso:

Para comprobar si el servicio se está ejecutando correctamente colocamos en el navegador
la dirección **localhost: 8081** y debería mostrarnos la siguiente página:
