# Despliegue en Apache-Tomcat

## Indice

1. Requisitos previos:
2. Construcción del proyecto:
3. Lanzamos el Hola Mundo:


### 1. Requisitos previos:

Debemos disponer de:

- JDK instalado.

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/HolaMundoWar/1.1.1.png)

- Apache Maven.

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/HolaMundoWar/1.1.2.png)

### 2. Construcción del proyecto:

Nos bajamos el proyecto Java de esteenlacey realizamoslos siguientes cambios:

Buscamos en el fichero web.xml la siguiente línea:

```
<display-name>app-web-alumno</display-name>
```
Y cambiamos “alumno” por nuestro nombre:

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/HolaMundoWar/2.1.1.png)

Luego, en el fichero index.jsp, sustituimos alumno por nuestro nombre:

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/HolaMundoWar/2.1.2.png)

Y lanzamos el comando para generar el .war mediante Maven:

```
mvn clean install
```

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/HolaMundoWar/2.1.3.png)
  
Y si se ha montado correctamente nos aparecerá esto:

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/HolaMundoWar/2.1.4.png)

Y nos habrá aparecido una nueva carpeta target, la cual contendrá una archivo.war.

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/HolaMundoWar/2.1.5.png)

También podemos formar nuestra propia estructura web mediante Maven, utilizando el
siguiente comando:

```
mvn archetype:generate -DgroupId=es.company.name -DartifactId=app-name
-DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
```

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/HolaMundoWar/a.png)
  
Y así se nos crearía una plantilla desde donde podremos seguir desarrollando nuestra
aplicación web.

### 3. Lanzamos el Hola Mundo:

Para ello, nos logueamos como superusuario y copiamos el archivo .war a la carpeta
webapps del Tomcat:

```
cp archivo rutaDestino
```

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/HolaMundoWar/c.png)

Y probamos si se ha iniciado escribiendo en el navegador el puerto del tomcat y el nombre
del .war, sin colocar .war al final.

  ![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/HolaMundoWar/d.png)
