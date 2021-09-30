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

mkdir nombreCarpeta

Luego iniciamos el repositorio mediante git init estando en la carpeta creada:

git init

## Añadir README.md y primer commit

Creamos el README.md usando touch:

touch README.md

Luego realizamos un git add. y un git commit - m “mensaje”, y con esto habremos realizado
el primer commit:

## Crear una rama:

Creamos una rama nueva con este comando:

git branch nombreRama

## Moverse a una rama y crear hola.html:

Nos movemos a la rama mediante git checkout nombreRama:

Luego creamos el fichero hola.html mediante nano y añadimos el contenido del ejercicio:

## Moverse a la rama principal y crear adios.html:

Usamos otra vez git checkout:

Y otra vez nano:

## Realizar la mezcla:

Para mezclar el repositorio master con el feature, nos ubicamos en master y utilizamos git
merge feature-1:

## Subir los cambios:

Como ya hemos fusionado las ramas, no hay nada que subir en local:

## Muestra todos los cambios:

Esto lo podemos hacer fácilmente con el comando git log --graph --all --oneline:
