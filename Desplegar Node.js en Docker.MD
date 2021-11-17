# Desplegar Node.js en Docker


## Indice

- 1. Primeros pasos:
- 2. Crear el Dockerfile:
- 3. Crear el .dockerignore:
- 4. Construir la imagen:
- 5. Arrancar el contenedor:
- 5. Testear el contenedor:


## 1. Primeros pasos:

Para empezar, creamos un nuevo directorio donde contendremos los archivos necesarios
para crear el servidor Node.js.

Empezaremos con el **package.json** , el cual deberá tener este contenido:

```
{
"name": "docker_web_app",
"version": "1.0.0",
"description": "Node.js on Docker",
"author": "First Last <first.last@example.com>",
"main": "server.js",
"scripts": {
"start": "node server.js"
},
"dependencies": {
"express": "^4.16.1"
}
}
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/NodeDocker/1.1.1.png)

Una vez creado este archivo, lanzamos el siguiente comando sobre nuestra carpeta:

```
npm install
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/NodeDocker/1.1.2.png)

Y nos habrá creado el archivo package-lock.json

Después de esto, creamos el fichero server.js, el cual definirá nuestra web app usando el
framework Express.js:

```
'use strict';

const express = require('express');

// Constants
const PORT = 8080 ;
const HOST = '0.0.0.0';

// App
const app = express();
app.get('/', (req, res) => {
res.send('Hello World');
});

app.listen(PORT, HOST);
console.log(`Running on [http://${HOST}:${PORT}`);](http://${HOST}:${PORT}`);)
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/NodeDocker/1.1.3.png)


## 2. Crear el Dockerfile:

Creamos un archivo llamado Dockerfile que tenga de contenido lo siguiente:

```
FROM node:

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY..

EXPOSE 8080
CMD [ "node", "server.js" ]
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/NodeDocker/2.1.1.png)


## 3. Crear el .dockerignore:

Para prevenir que archivos indeseados se copien a la imagen de Docker cuando la
construyamos, apuntamos sus nombres en este archivo:

```
node_modules
npm-debug.log
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/NodeDocker/3.1.1.png)


## 4. Construir la imagen:

Después de realizar todos los pasos anteriores, procedemos a construir la imagen de la que
posteriormente arrancaremos el servidor.

Utilizaremos este comando:

```
docker build. - t <your username>/node-web-app
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/NodeDocker/4.1.1.png)

Comprobamos que la imagen ha sido creada:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/NodeDocker/4.1.2.png)

Efectivamente, ha sido creada.


## 5. Arrancar el contenedor:

Para arrancar el contenedor a partir de la imagen que hemos creado, utilizamos este
comando:

```
docker run - p 49160 : 8080 - d <your username>/node-web-app
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/NodeDocker/5.1.1.png)

Para comprobar que ha arrancado correctamente, miramos los logs de la app:

```
docker logs <container id>
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/NodeDocker/5.1.2.png)

Y, efectivamente, ha arrancado y es accesible desde el puerto 8080 del contenedor.


## 6. Testear el contenedor:

Podemos enviar una petición al servidor usando la herramienta curl:

```
curl - i localhost: 49160
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/NodeDocker/6.1.1.png)

Como vemos, el servidor responde con lo esperado, con lo que nos está funcionando
correctamente.
