# IES Puerto de la Cruz Telesforo Bravo

## Indice

- 1. Requisitos previos:
- 2. Pasos para realizar la instalación en local:
   - 2.1 Actualización de los repositorios:
   - 2.2 Instalación de paquetes adiciones2.3 Instalación de GitLab
   - 2.4 Acceso

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

![2.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/instalacion%20de%20GitLab/2.1.png)

### 2.2 Instalación de paquetes adiciones2.3 Instalación de GitLab

Luego, para empezar, instalamos los paquetes necesarios para que funcione GitLabcorrectamente:

```
sudo apt install - y vim curl ca-certificates apt-transport-https
```

![2.2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/instalacion%20de%20GitLab/2.2.png)

### 2.3 Instalación de GitLab

Antes de instalarlo, configuraremos el repositorio APT en nuestro sistema e instalaremosotras dependencias necesarias; para hacer esto de manera rápida utilizaremos un script
que nos da el equipo de GitLab:

```
curl - s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
```

![2.3.1](![2.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/instalacion%20de%20GitLab/2.3.1.png))

Luego de esto, ya podremos instalar GitLab:

```
sudo apt install gitlab-ce
```

Para terminar, ejecutamos el siguiente comando para terminar la configuración y esperamosa que termine:

```
sudo gitlab-ctl reconfigure
```
### 2.4 Acceso

Al finalizar la instalación, podremos acceder a GitLab introduciendo la IP del servidor en el
navegador. Para saber nuestra IP utilizamosifconfig:

![2.4.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/instalacion%20de%20GitLab/2.4.1.png)

En nuestro caso tenemos varias tarjetas de red, pero la del servidor es la 127.0.0.
