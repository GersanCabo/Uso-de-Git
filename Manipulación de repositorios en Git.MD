
# Manipulación de repositorios en Git

<br>

## Indice

1. <a href="#1-configuración-inicial">**Configuración inicial**</a>
2. <a href="#2-creación-de-un-repositorio">**Creación de un repositorio**</a>
3. <a href="#3-comprobar-el-estado-del-repositorio">**Comprobar el estado del repositorio**</a>
4. <a href="#4-realizando-commits">**Realizando commit’s**</a>
5. <a href="#5-modificación-de-ficheros">**Modificación de ficheros**</a>
6. <a href="#6-historial">**Historial**</a>

<br>

## 1. Configuración inicial
Configuramos Git definiendo nuestro nombre, correo electrónico y activamos el coloreado de los mensajes de salida. Esto lo podemos hacer con estos sencillo comandos:

```
git config --global user.name “Tu nombre”
git config --global user.email “tucorreo@dominio.com”
git config --global color.ui auto
```

En nuestro caso queda tal que así:

![1.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/1.1.1.png)

Podemos comprobar estas configuraciones con git config --list 

![1.1.2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/1.1.2.png)

<br>

## 2. Creación de un repositorio
Vamos a crear un repositorio al que llamaremos dpl, para ello primero creamos la carpeta, luego nos ubicamos en ella y, por último, iniciamos el repositorio:

```
mkdir dpl
cd dpl
git init
```

Por último, para comprobar que se ha creado el repositorio, listamos el contenido de la carpeta:

```
ls -la
```

![2.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/2.1.1.png)

Como podemos ver, en el repositorio se ha creado una carpeta oculta con los archivos que necesita git.

<br>

## 3. Comprobar el estado del repositorio
Podemos comprobar el estado del repositorio con git status:

```
git status
```

![3.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/3.1.1.png)

Como podemos ver, no hay nada que añadir al repositorio local, ya que no hemos realizado cambios en la carpeta.

Ahora crearemos un archivo de ejemplo en la carpeta:

![3.1.2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/3.1.2.png)

Y volvemos a comprobar el estado del repositorio:

![3.1.3](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/3.1.3.png)

Como podemos ver, ahora se nos muestra que se ha creado un nuevo archivo en el repositorio y que no hemos empezado a darle un seguimiento al mismo. Para empezar a seguirlo y así, más tarde, añadirlo al commit, debemos usar la siguiente sentencia:

```
git add indice.txt
```

De esta forma añadiremos el archivo a la zona de intercambio temporal, en la que estará hasta que hagamos un commit y lo subamos definitivamente al repositorio local.

Si volvemos a hacer un git status, comprobaremos que ha cambiado su estado:

![3.1.4](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/3.1.4.png)

<br>

## 4. Realizando commit’s
Después de hacer el git add, debemos realizar un git commit para terminar de subir los cambios al repositorio, además, podremos añadir un comentario junto al commit, el cual quedará registrado en el repositorio.

```
git commit -m “Añadido índice de la asignatura DPL”
```

Si volvemos a hacer un git status, veremos que ya no tenemos ningún archivo pendiente.

![4.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/4.1.1.png)

<br>

## 5. Modificación de ficheros
Ahora probaremos a modificar un fichero para ver otra de las características de git, el git diff, el cual nos permitirá comparar los nuevos cambios con la versión que tenemos en el repositorio. Para empezar, modificamos el archivo indice.txt:

![5.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/5.1.1.png)

Y luego realizamos el comando anteriormente dicho:

```
git diff
```

![5.1.2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/5.1.2.png)

Como podemos ver, con git diff se nos muestra los archivos que han sido modificados, el número de líneas que se han añadido y, por último, nos muestra el documento con las líneas añadidas y eliminadas.

Para finalizar, añadimos los cambios al repositorio:

![5.1.3](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/5.1.3.png)

<br>

## 6. Historial
Por último, mostraremos otro comando importante de Git, el git show, el cual nos mostrará los cambios de la última versión del repositorio respecto a la anterior.

Con lo que usamos el comando para ver cual es la respuesta:

![6.1.1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/6.1.1.png)

Como podemos ver, los cambios de la última versión del repositorio respecto a la anterior, resultan ser los mismos que hemos visto anteriormente con el git diff, ya que la que antes era la versión que aún no habíamos subido al repositorio, ahora es la última versión del repositorio.

Probemos a hacer un cambio y a volver a probar el comando, por ejemplo, podemos editar el comentario del último commit:

```
git commit --amend -m “mensaje”
```

![6.1.2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Manipulaci%C3%B3n%20de%20repositorios%20en%20Git/6.1.2.png)

Podemos ver que ha cambiado el comentario que vemos al hacer el git show, mostrando ahora el nuevo mensaje pero conservando la fecha de subida del commit.
