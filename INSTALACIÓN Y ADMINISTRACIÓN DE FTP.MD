<h1>Instalación y administración de FTP</h1>

## Indice

- 1. Instalar FTP
- 2. Verificar el servicio FTP
- 3. Configurar el servidor FTP
   - 3.1 Instalar cliente FileZilla:
   - 3.2 Modo Pasivo:
   - 3.3 Seguridad TLS:
- LINK:


## 1. Instalar FTP

Primero actualizamos los repositorios:

```
sudo apt update
```
Luego, instalamos el paquete vsftpd:

```
sudo apt install - y vsftpd
```
A continuación debemos habilitar que se permita el tráfico desde el firewall a los puertos
predeterminados, para el puerto de comandos tendremos que colocar el siguiente comando:

```
sudo ufw allow ftp
```
Y para habilitar el puerto de datos sería lo siguiente:

```
sudo ufw allow ftp-data
```
## 2. Verificar el servicio FTP

Ahora, desde otra máquina de nuestra red (tengo la máquina con adaptador puente) nos
conectaremos a nuestro servidor Ubuntu mediante FTP.

Para ello lo que nos propone el ejercicio es comprobarlo desde el navegador, pero desde
2020 Chrome ha desactivado el FTP por defecto y Firefox lo eliminó de su código, así que
creo que lo mejor será realizar la conexión desde la propia terminal:

```
ftpdireccion-ip
```
Y nos pedirá el usuario desde el que queremos acceder y la contraseña del mismo.


## 3. Configurar el servidor FTP

### 3.1 Instalar cliente FileZilla:

Para instalar FileZilla en nuestro cliente debemos realizar el siguiente comando:

```
sudo apt install filezilla
```
### 3.2 Modo Pasivo:

Normalmente la configuración por defecto del servidor FTP en Ubuntu es en modo activo,
así que lo configuraremos en pasivo para que nos permita la conexión desde clientes que
no se encuentren tras un firewall. Para ello debemos editar el siguiente archivo:

```
sudo nano /etc/vsftpd.conf
```
Y añadir lo siguiente al final del archivo:

...
pasv_enable=YES
pasv_min_port= 30000
pasv_max_port= 30050

Y recargamos la configuración del servicio:

```
sudo systemctl reload vsftpd
```
Por último, activamos el acceso a ese rango de puertos desde el firewall:

```
sudo ufw allow 30000 : 30050 /tcp
```

Y probamos que nos sigue funcionando:

### 3.3 Seguridad TLS:

En el caso de que queramos acceder con usuarios externos debemos cifrar la conexión,
pero para que el cifrado funcione correctamente al ingresar con un dominio debemos crear
primero una serie de certificados autofirmados:

```
sudo openssl req - x 509 - newkey rsa: 2048 - days 3650 - nodes - out /etc/ssl/certs/daw.dpl.crt - keyout
/etc/ssl/private/daw.dpl.key
```
Una vez ingresado este comando, nos solicitará una serie de datos:

Y ahora debemos editar el archivo vsftpd.conf y buscar lo siguiente:

```
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO
```

Y cambiarlo por:

```
rsa_cert_file=/etc/ssl/certs/daw.dpl.crt
rsa_private_key_file=/etc/ssl/private/daw.dpl.key
ssl_enable=YES
```
Y reiniciamos el servidor FTP:

```
sudo systemctl restart vsftpd
```
