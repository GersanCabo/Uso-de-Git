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

&nbsp;&nbsp;&nbsp;&nbsp;Lo hacemos con el comando *git log*

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

<br>

## Ejercicio 4

**● Añadir al final del fichero indice.txt la siguiente línea:**

> Capítulo 5: Conceptos avanzados

&nbsp;&nbsp;&nbsp;&nbsp;Como no existe ningún indice.txt, lo realizaremos en el README.md:

&nbsp;&nbsp;&nbsp;&nbsp;![4.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/4.1.1.png)

**● Añadir los cambios a la zona de intercambio temporal.**

&nbsp;&nbsp;&nbsp;&nbsp;Lo realizamos:

&nbsp;&nbsp;&nbsp;&nbsp;![1.3.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/1.3.1.png)

**● Hacer un commit de los cambios con el mensaje Añadidocapítulo 5 al índice.**

&nbsp;&nbsp;&nbsp;&nbsp;Realizamos el commit con el mensaje:

&nbsp;&nbsp;&nbsp;&nbsp;![4.1.3](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/4.1.3.png)

**● Mostrar quién ha hecho cambios sobre el fichero indice.txt.**

&nbsp;&nbsp;&nbsp;&nbsp;Para ver qué personas han realizado cambios sobre indice.txt, debemos utilizar el siguiente comando:

```
git annotatenombreArchivo
```

&nbsp;&nbsp;&nbsp;&nbsp;En nuestro caso esta será la respuesta:

&nbsp;&nbsp;&nbsp;&nbsp;![4.1.4](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/4.1.4.png)

<br>

## Ejercicio 5

**● Crear una nueva rama bibliografía y mostrar las ramas del repositorio.**

&nbsp;&nbsp;&nbsp;&nbsp;Para hacer trabajar con ramas debemos usar el siguiente comando:

```
git branch
```

&nbsp;&nbsp;&nbsp;&nbsp;Y para crear una rama debemos usar ese comando seguido del nombre de la rama:

```
git branchNombreRama
```

&nbsp;&nbsp;&nbsp;&nbsp;Nos quedaría tal que así:

&nbsp;&nbsp;&nbsp;&nbsp;![5.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/5.1.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;Y si queremos ver todas nuestras ramas, usamos otra vez el comando anterior pero seguido de -av:

&nbsp;&nbsp;&nbsp;&nbsp;![5.1.2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/5.1.2.png)

## Ejercicio 6

**● Crear el fichero capitulos/capitulo4.txt y añadir el texto siguiente:**

&nbsp;&nbsp;&nbsp;&nbsp;En este capítulo veremos cómo usar GitHub para alojar repositorios en remoto.

&nbsp;&nbsp;&nbsp;&nbsp;Nos ubicamos en la carpeta capítulos y creamos el archivo usando nano:

&nbsp;&nbsp;&nbsp;&nbsp;![6.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/6.1.1.png)

**● Añadir los cambios a la zona de intercambio temporal.**

&nbsp;&nbsp;&nbsp;&nbsp;Volvemos a utilizar “git add .”, como en los ejercicios anteriores.

&nbsp;&nbsp;&nbsp;&nbsp;![1.3.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/1.3.1.png)

**● Hacer un commit con el mensaje “Añadido capítulo 4.”**

&nbsp;&nbsp;&nbsp;&nbsp;Hacemos el commit para subir los cambios:

&nbsp;&nbsp;&nbsp;&nbsp;![6.1.3](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/6.1.3.png)

**● Mostrar la historia del repositorio incluyendo todas las ramas.**

&nbsp;&nbsp;&nbsp;&nbsp;Para esto utilizaremos el comando *git log*, pero incluyendo algunos extras:

```
git log --graph --all --oneline
```

&nbsp;&nbsp;&nbsp;&nbsp;Con esto nos saldrán los cambios realizados en todas las ramas:

&nbsp;&nbsp;&nbsp;&nbsp;![6.1.4](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/6.1.4.png)

&nbsp;&nbsp;&nbsp;&nbsp;Como podemos ver, este último cambio lo hemos realizado en la rama main.

<br>

## Ejercicio 7

**● Cambiar a la rama bibliografia.**

&nbsp;&nbsp;&nbsp;&nbsp;Para cambiar entre ramas utilizamos el siguiente comando:

```
git checkoutnombreRama
```

&nbsp;&nbsp;&nbsp;&nbsp;Este sería el resultado:

&nbsp;&nbsp;&nbsp;&nbsp;![7.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/7.1.1.png)

**● Crear el fichero bibliografia.txt y añadir la siguiente referencia:**

> &nbsp;&nbsp;&nbsp;&nbsp;Chacon, S. and Straub, B. Pro Git. Apress.

&nbsp;&nbsp;&nbsp;&nbsp;Nos situamos en la carpeta libros y creamos el fichero con nano:

&nbsp;&nbsp;&nbsp;&nbsp;![7.1.2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/7.1.2.png)

**● Añadir los cambios a la zona de intercambio temporal.**

&nbsp;&nbsp;&nbsp;&nbsp;Realizamos de nuevo un *git add .* :

&nbsp;&nbsp;&nbsp;&nbsp;![1.3.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/1.3.1.png)

**● Hacer un commit con el mensaje “Añadida primera referencia bibliográfica.”**

&nbsp;&nbsp;&nbsp;&nbsp;Realizamos el commit con el mensaje dicho:

&nbsp;&nbsp;&nbsp;&nbsp;![7.1.4](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/7.1.4.png)

**● Mostrar la historia del repositorio incluyendo todas las ramas.**

&nbsp;&nbsp;&nbsp;&nbsp;Utilizamos el comando *git log* con los extras que hemos usado anteriormente:

&nbsp;&nbsp;&nbsp;&nbsp;![7.1.5](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/7.1.5.png)

&nbsp;&nbsp;&nbsp;&nbsp;Como podemos ver, el último commit se ha realizado sobre la rama bibliografía, la cual, debido a esto, está adelantada respecto a la rama main.

## Ejercicio 8

**● Fusionar la rama bibliografia con la rama master.**

&nbsp;&nbsp;&nbsp;&nbsp;Primero debemos situarnos en la rama main. Para esto usamos el *git checkout*:

&nbsp;&nbsp;&nbsp;&nbsp;![8.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/8.1.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;Una vez aquí, realizamos la fusión de la rama bibliografía con la rama main de la siguiente manera:

```
git merge nombreRama
```

&nbsp;&nbsp;&nbsp;&nbsp;En nuestro caso quedaría tal que así:

&nbsp;&nbsp;&nbsp;&nbsp;![8.1.2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/8.1.2.png)

**● Mostrar la historia del repositorio incluyendo todas las ramas.**

&nbsp;&nbsp;&nbsp;&nbsp;Volvemos a utilizar el comando que ya hemos usado en otros ejercicios:

&nbsp;&nbsp;&nbsp;&nbsp;![8.2.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/8.2.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;Como podemos ver se representa la fusión de la rama bibliografía con la rama main.

**● Eliminar la rama bibliografia.**

&nbsp;&nbsp;&nbsp;&nbsp;Ahora que ya hemos fusionado la rama bibliografía con la rama main, no necesitamos que siga existiendo la rama bibliografía.

&nbsp;&nbsp;&nbsp;&nbsp;La eliminamos de la siguiente manera:

```
git  branch -d nombreRama
```

&nbsp;&nbsp;&nbsp;&nbsp;Y nos mostraría esto:

&nbsp;&nbsp;&nbsp;&nbsp;![8.3.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/8.3.1.png)

**● Mostrar de nuevo la historia del repositorio incluyendo todas las ramas.**

&nbsp;&nbsp;&nbsp;&nbsp;Utilizamos el mismo comando del apartado 2:

&nbsp;&nbsp;&nbsp;&nbsp;![8.4.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/8.4.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;La respuesta a este comando es la misma que nos dio antes, esto es debido a que, aunque eliminemos la rama, el git log nos seguirá mostrando el recorrido que tuvo y su historia.

## Ejercicio 9

**● Crear la rama bibliografia.**

&nbsp;&nbsp;&nbsp;&nbsp;La creamos utilizando *git branch nombreRama*:

&nbsp;&nbsp;&nbsp;&nbsp;![9.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/9.1.1.png)

**● Cambiar a la rama bibliografia.**

&nbsp;&nbsp;&nbsp;&nbsp;Lo haremos utilizando *git checkout nombreRama*:

&nbsp;&nbsp;&nbsp;&nbsp;![9.2.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/9.2.1.png)

**● Cambiar el fichero bibliografia.txt para que contenga las siguientes referencias:**

&nbsp;&nbsp;&nbsp;&nbsp;Lo editamos con nano:

&nbsp;&nbsp;&nbsp;&nbsp;![9.3.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/9.3.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;Subimos estos cambios para poder cambiar de rama después:

&nbsp;&nbsp;&nbsp;&nbsp;![9.3.2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/9.3.1.png)

**● Cambiar a la rama master.**

&nbsp;&nbsp;&nbsp;&nbsp;Volvemos a utilizar git checkout nombreRama:

&nbsp;&nbsp;&nbsp;&nbsp;![9.4.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/9.4.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;Como podemos ver, nos avisa de que el main está adelantado a la rama remota por 7 commits.

**● Cambiar el fichero bibliografia.txt para que - contenga las siguientes referencias:**

> &nbsp;&nbsp;&nbsp;&nbsp;Chacon, S. and Straub, B. Pro Git. Apress.
> &nbsp;&nbsp;&nbsp;&nbsp;Loeliger, J. and McCullough, M. Version control with Git. O’Reilly.

&nbsp;&nbsp;&nbsp;&nbsp;Volvemos a utilizar nano:

&nbsp;&nbsp;&nbsp;&nbsp;![9.5.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/9.5.1.png)

**● Añadir los cambios a la zona de intercambio temporal y hacer un commit con el mensaje “Añadida nueva referencia bibliográfica.”**

&nbsp;&nbsp;&nbsp;&nbsp;Realizamos un *git add .* y, luego, un *git commit -m“mensaje”*:

&nbsp;&nbsp;&nbsp;&nbsp;![9.6.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/9.6.1.png)

**● Fusionar la rama bibliografia con la rama master.**

&nbsp;&nbsp;&nbsp;&nbsp;Para esto utilizaremos el comando *git merge nombreRama* estando en la rama main:

&nbsp;&nbsp;&nbsp;&nbsp;![9.7.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/9.7.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;Como podemos ver se nos avisa de un conflicto en el fichero bibliografia.txt, el cual debemos solucionar a mano para completar la fusión.

**● Resolver el conflicto dejando el fichero bibliografia.txt con las referencias:**

> &nbsp;&nbsp;&nbsp;&nbsp;Chacon, S. and Straub, B. Pro Git. Apress.
> &nbsp;&nbsp;&nbsp;&nbsp;Loeliger, J. and McCullough, M. Version control with Git. O’Reilly.
> &nbsp;&nbsp;&nbsp;&nbsp;Hodson, R. Ry’s Git Tutorial. Smashwords (2014)

&nbsp;&nbsp;&nbsp;&nbsp;Realizamos estos cambios para solucionar el conflicto, podemos editar el fichero con nano:

&nbsp;&nbsp;&nbsp;&nbsp;![9.8.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/9.8.1.png)

**● Añadir los cambios a la zona de intercambio temporal y hacer un commit con el mensaje “Resuelto conflicto de bibliografía.”**

&nbsp;&nbsp;&nbsp;&nbsp;Realizamos los dos comandos pertinentes:

&nbsp;&nbsp;&nbsp;&nbsp;![9.9.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/9.9.1.png)

**● Mostrar la historia del repositorio incluyendo todas las ramas.**

&nbsp;&nbsp;&nbsp;&nbsp;Realizamos el comando *git log --graph --all --oneline*:

&nbsp;&nbsp;&nbsp;&nbsp;![9.10.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejemplos%20en%20Git/9.10.1.png)

&nbsp;&nbsp;&nbsp;&nbsp;Como podemos ver, se nos muestran todos los commits y fusiones realizados en todas la ramas.