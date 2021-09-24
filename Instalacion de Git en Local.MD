# Instalación de Git en Local

<br>

## Indice

1. **Comprobar la instalación de Git**
2. **Instalar Git (mediante repositorio de Ubuntu)**
3. **Instalar git (mediante el sitio web de Git)**

    3.1. Instalamos dependencias
    
    3.2 Creamos un directorio temporal

    3.3 Descargamos el instalador
    
    3.4 Descomprimimos el archivo
    
    3.5 Creamos el paquete y lo instalamos

    3.6 Sustituimos el proceso de shell

4. **Configurar Git**

    4.1 Añadimos nuestro nombre y nuestro corrreo

    4.2 Consultar y modificar esta información

<br>

## 1. Comprobar la instalación de Git

Para ello colocamos el siguiente comando en la terminal:

```
git --version
```

Si nos responde con la versión de Git, significa que lo tenemos instalado, si estamos desactualizados o no lo tenemos instalado, seguimos con los pasos.

<br>

## 2. Instalar Git (mediante repositorio de Ubuntu)
Antes de instalar Git debemos actualizar los repositorios para que se nos instale la última versión disponible:

> sudo apt update

Luego de esto ya podemos instalar Git:

> sudo apt install git

Para ser más eficientes podemos combinar ambos comandos en uno solo:

> sudo apt update && sudo apt install git

Para confirmar que se ha instalado Git correctamente, utilizamos git --version de nuevo y nos deberia salir algo como esto:

![2.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Git/2.1.1.png)

<br>

## 3. Instalar Git (mediante el sitio web de Git)
Como se nos pide instalar la versión 2.29.3 (o posterior) y, a día de hoy, en los repositorios de Canonical la última versión es la 2.25.1, procedemos a realizar la instalación de esta otra forma.

### 3.1. Instalamos dependencias
Aunque hemos instalado Git anteriormente, intentamos instalar las dependencias por si acaso tenemos alguna desactualizada o por si se han añadido nuevas en esta última versión. El comando sería el siguiente:

> sudo apt update && sudo apt install libz-dev libssl-dev libcurl4-gnutls-dev libexpat1-dev gettext cmake gcc

### 3.2. Creamos un directorio temporal
Una vez instaladas las dependencias, creamos un directorio temporal donde poder albergar el paquete de instalación de Git mientras lo necesitemos. Pongo un ejemplo de este proceso:

![3.2.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Git/3.2.1.png)

### 3.3. Descargamos el instalador
Descargamos la última versión de Git (en nuestro caso se trata de la 2.33.0) y lo colocamos en la carpeta temporal, todo ello lo podemos hacer con el siguiente comando:

> curl -o git.tar.gz [https://mirrors.edge.kernel.org/pub/software/scm/git/git-manpages-2.33.0.tar.gz](https://mirrors.edge.kernel.org/pub/software/scm/git/git-manpages-2.33.0.tar.gz)

Puede darse el caso de que no tengamos la herramienta curl instalada para poder realizar la descarga desde línea de comandos, si fuese así, la descargamos de la siguiente manera:

> sudo apt install curl

Y volvemos a hacer el comando anterior, si ha salido exitosamente se nos mostrará algo como esto:

![3.3.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Git/3.2.1.png)

### 3.4. Descomprimimos el archivo
Para ello utilizamos el siguiente comando:

> tar -zxf git.tar.gz

Y entramos en el directorio que se acaba de crear:

> cd git-*

### 3.5. Creamos el paquete y lo instalamos
Primero creamos el paquete, esto tardara un poco (normalmente) y lo podemos hacer con el siguiente comando:

> make prefix=/usr/local all

Luego lo instalamos:

> sudo make prefix=/usr/local install

### 3.6. Sustituimos el proceso de shell
Sustituimos el proceso de shell para que utilice la versión de Git que acabamos de instalar:

> exec bash

Y, por último, comprobamos que está instalada la versión:

![3.6.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Git/3.5.1.png)

<br>

## 4. Configurar Git
Después de instalar la versión más reciente de Git, configuramos la herramienta para que tenga un correcto funcionamiento y tardemos menos tiempo en realizar ciertas acciones.

### 4.1. Añadimos nuestro nombre y nuestro correo
Esto lo podemos hacer mediante el comando git config. Estos datos los insertará Git en cada confirmación que hagamos.

Para insertar el nombre:

> git config --global user.name “Tu nombre”

Y para insertar el email:

> git config --global user.email “tucorreo@dominio.com”

Ejemplo:

![4.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Git/4.1.1.png)

### 4.2. Consultar y modificar esta información
Para listar toda esta información podemos hacer uso de un sencillo comando:

> git config --list

Ejemplo:

![4.2.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Git/4.2.1.png)

También podemos entrar directamente al archivo donde se almacena esta información, que además de permitirnos verla, también nos permitirá modificarla.

> nano ~/.gitconfig

Ejemplo:

![4.2.2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalaci%C3%B3n%20de%20Git/4.2.2.png)