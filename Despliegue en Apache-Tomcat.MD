# Despliegue en Apache-Tomcat

## Indice

1. Requisitos previos:
2. Construcción del proyecto:
3. Lanzamos el Hola Mundo:


### 1. Requisitos previos:

Debemos disponer de:

- JDK instalado.
- Apache Maven.

### 2. Construcción del proyecto:

Nos bajamos el proyecto Java de esteenlacey realizamoslos siguientes cambios:

Buscamos en el fichero web.xml la siguiente línea:

```
<display-name>app-web-alumno</display-name>
```
Y cambiamos “alumno” por nuestro nombre:

Luego, en el fichero index.jsp, sustituimos alumno por nuestro nombre:

Y lanzamos el comando para generar el .war mediante Maven:

```
mvn clean install
```

Y si se ha montado correctamente nos aparecerá esto:

Y nos habrá aparecido una nueva carpeta target, la cual contendrá una archivo.war.

También podemos formar nuestra propia estructura web mediante Maven, utilizando el
siguiente comando:

```
mvn archetype:generate -DgroupId=es.company.name -DartifactId=app-name
-DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
```

Y así se nos crearía una plantilla desde donde podremos seguir desarrollando nuestra
aplicación web.

### 3. Lanzamos el Hola Mundo:

Para ello, nos logueamos como superusuario y copiamos el archivo .war a la carpeta
webapps del Tomcat:

```
cp archivo rutaDestino
```

Y probamos si se ha iniciado escribiendo en el navegador el puerto del tomcat y el nombre
del .war, sin colocar .war al final.
