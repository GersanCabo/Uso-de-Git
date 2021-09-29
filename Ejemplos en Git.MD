# Ejemplos en Git

<br>

## Indice

1. <a href="#ejercicio-1">**Ejercicio 1**</a>
2. <a href="#ejercicio-2">**Ejercicio 2**</a>
3. <a href="#ejercicio-3">**Ejercicio 3**</a>
4. <a href="#ejercicio-4">**Ejercicio 4**</a>
5. <a href="#ejercicio-5">**Ejercicio 5**</a>
6. <a href="#ejercicio-6">**Ejercicio 6**</a>
7. <a href="#ejercicio-7">**Ejercicio 7**</a>
8. <a href="#ejercicio-8">**Ejercicio 8**</a>
9. <a href="#ejercicio-9">**Ejercicio 9**</a>

<br>

## Ejercicio 1

**● Mostrar el historial de cambios del repositorio.**

&nbsp;&nbsp;&nbsp;&nbsp;Lo hacemos con el comando git log

&nbsp;&nbsp;&nbsp;&nbsp;![1.1..1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/1.1.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;Como podemos ver solo ha habido un commit.

**● Crear la carpeta capítulos y crear dentro de ella el fichero capitulo1.txt con el siguiente texto:**

> Git es un sistema de control de versiones ideado por Linus Torvalds.

&nbsp;&nbsp;&nbsp;&nbsp;Lo hacemos usando los siguientes comandos:

&nbsp;&nbsp;&nbsp;&nbsp;![1.2.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/1.2.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;Después del primer comando se nos abrirá nano y podremos escribir el texto.

**● Añadir los cambios a la zona de intercambio temporal.**

&nbsp;&nbsp;&nbsp;&nbsp;Esto lo hacemos mediante "*git add .*"

&nbsp;&nbsp;&nbsp;&nbsp;![1.3.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/1.3.1.png)

**● Hacer un commit de los cambios con el mensaje Añadido capítulo 1.**

&nbsp;&nbsp;&nbsp;&nbsp;Esto se hace con el comando *git commit -m “mensaje”*

&nbsp;&nbsp;&nbsp;&nbsp;![1.4.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/1.4.1.png)

**● Volver a mostrar el historial de cambios del repositorio.**

&nbsp;&nbsp;&nbsp;&nbsp;![1.5.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/1.4.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;Como podemos ver, esta nuestro último commit.

<br>

## Ejercicio 2

**● Crear el fichero capitulo2.txt en la carpeta capítulos con el siguiente texto.**

**El flujo de trabajo básico con Git consiste en:**

>1- Hacer cambios en el repositorio. 
>
>2- Añadir los cambios a la zona de intercambio temporal. 
>
> 3- Hacer un commit de los cambios.**

&nbsp;&nbsp;&nbsp;&nbsp;Usamos nano y escribimos el texto:

&nbsp;&nbsp;&nbsp;&nbsp;![2.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/2.1.1.png)

**● Añadir los cambios a la zona de intercambio temporal.**

&nbsp;&nbsp;&nbsp;&nbsp;Lo añadimos asi:

&nbsp;&nbsp;&nbsp;&nbsp;![2.2.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/2.2.1.png)

**● Hacer un commit de los cambios con el mensaje Añadido capítulo 2.**

&nbsp;&nbsp;&nbsp;&nbsp;Realizamos el commit de la siguiente manera:

&nbsp;&nbsp;&nbsp;&nbsp;![2.3.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/2.3.1.png)

**● Mostrar las diferencias entre la última versión y las dos versiones anteriores.**

&nbsp;&nbsp;&nbsp;&nbsp;Lo podemos hacer con el comando git show.

&nbsp;&nbsp;&nbsp;&nbsp;Primero, para comparar la última versión con la primera versión, basta con usar el comando solo, ya que esta es la última versión que tenemos en remoto:

&nbsp;&nbsp;&nbsp;&nbsp;![2.4.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/2.4.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;También podemos obtener el mismo resultado colocando el número de identificación del commit:

&nbsp;&nbsp;&nbsp;&nbsp;![2.4.2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/2.4.2.png)

&nbsp;&nbsp;&nbsp;&nbsp;Este número lo podemos obtener mediante el comando git log, como ya hemos visto anteriormente.

&nbsp;&nbsp;&nbsp;&nbsp;Hacemos lo mismo pero colocando el número de identificación del penúltimo commit:

&nbsp;&nbsp;&nbsp;&nbsp;![2.4.3](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/2.4.3.png)

&nbsp;&nbsp;&nbsp;&nbsp;PD: A posteriori hemos descubierto una manera más rápida de comparar ambas versiones usando el comando git diff y colocando que queremos comparar la última versión (HEAD) con las dos siguientes(HEAD~2):

&nbsp;&nbsp;&nbsp;&nbsp;![2.4.4](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/2.4.4.png)

<br>

## Ejercicio 3

**● Crear el fichero capitulo3.txt en la carpeta capítulos con el siguiente texto.**

> Git permite la creación de ramas lo que permite tener distintas versiones del mismo
proyecto y trabajar de manera simultánea en ellas.

&nbsp;&nbsp;&nbsp;&nbsp;Creamos el fichero con nano, escribimos el contenido y lo mostramos:

&nbsp;&nbsp;&nbsp;&nbsp;![3.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/3.1.1.png)

**● Añadir los cambios a la zona de intercambio temporal.**

&nbsp;&nbsp;&nbsp;&nbsp;Añadimos todos los cambios usando git add .

&nbsp;&nbsp;&nbsp;&nbsp;![1.3.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/1.3.1.png)

**● Hacer un commit de los cambios con el mensaje Añadido capítulo 3.**

&nbsp;&nbsp;&nbsp;&nbsp;![3.3.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/3.3.1.png)

**● Mostrar las diferencias entre la primera y la última versión del repositorio.**

&nbsp;&nbsp;&nbsp;&nbsp;Esto lo podremos hacer con la siguiente sintaxis:

```
git diff codigoHashPrimeraVersion..HEAD
```
&nbsp;&nbsp;&nbsp;&nbsp;El comando sería este:

&nbsp;&nbsp;&nbsp;&nbsp;![3.4.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/3.4.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;Y la salida debería ser algo así:

&nbsp;&nbsp;&nbsp;&nbsp;![3.4.2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/3.4.2.png)
