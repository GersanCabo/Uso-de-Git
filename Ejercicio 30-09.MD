## Indice

Inicializar un repositorio
Añadir README.md y primer commit
Crear una rama:
Moverse a una rama y crear hola.html:
Moverse a la rama principal y crear adios.html:
Realizar la mezcla:
Subir los cambios:
Muestra todos los cambios:

## Inicializar un repositorio

Primero creamos una carpeta mediante el comando mkdir:

```
mkdir nombreCarpeta
```
![1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejercicio%2030-09/1.png)

Luego iniciamos el repositorio mediante git init estando en la carpeta creada:

```
git init
```
![2](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejercicio%2030-09/2.png)

## Añadir README.md y primer commit

Creamos el README.md usando touch:

```
touch README.md
```

![3](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejercicio%2030-09/3.png)

Luego realizamos un git add. y un git commit - m “mensaje”, y con esto habremos realizado
el primer commit:

![4](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejercicio%2030-09/4.png)

## Crear una rama:

Creamos una rama nueva con este comando:

```
git branch nombreRama
```

![5](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejercicio%2030-09/5.png)

## Moverse a una rama y crear hola.html:

Nos movemos a la rama mediante git checkout nombreRama:

![6](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejercicio%2030-09/6.png)

Luego creamos el fichero hola.html mediante nano y añadimos el contenido del ejercicio:

![7](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejercicio%2030-09/7.png)

## Moverse a la rama principal y crear adios.html:

Usamos otra vez git checkout:

![1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejercicio%2030-09/8.png)

Y otra vez nano:

![1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejercicio%2030-09/9.png)

## Realizar la mezcla:

Para mezclar el repositorio master con el feature, nos ubicamos en master y utilizamos git
merge feature-1:

![1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejercicio%2030-09/10.png)

## Subir los cambios:

Como ya hemos fusionado las ramas, no hay nada que subir en local:

![1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejercicio%2030-09/11.png)

## Muestra todos los cambios:

Esto lo podemos hacer fácilmente con el comando git log --graph --all --oneline:

![1](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Ejercicio%2030-09/12.png)
