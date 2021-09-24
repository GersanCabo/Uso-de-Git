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

> git --version

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