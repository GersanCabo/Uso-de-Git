# Servicio Rest-WS WildFly

## Indice

- 1. Requisitos previos:
- 2. Instalación de los servicios:
   - 2.1. Descarga de los ejemplos:
   - 2.2. Instalación de Servicio Hello-RS:
   - 2.3. Instalación de Servicio Hello-WS:
- LINK:


## 1. Requisitos previos:

Necesitaremos:

- Un servidor Ubuntu 20.04:
- Cuenta de superusuario root:
- JDK instalado:
- Para ir adelantando, Maven instalado:
- Tener desplegado el servidor de aplicaciones WilFly:


## 2. Instalación de los servicios:

### 2.1. Descarga de los ejemplos:

Clonamos el repositorio con los ejemplos, está en este <a href="https://github.com/wildfly/quickstart/">enlace</a>.

### 2.2. Instalación de Servicio Hello-RS:

Accedemos al directorio helloworld-rs y ejecutamos el siguiente comando:

```
mvn clean install
```

Luego de esto deberemos desplegar el servicio en el Wildfly, para ello accedemos a la
página principal de nuestro servidor WildFly y nos dirigimos a la pestaña “deployments”.

Luego pulsamos sobre el botón “+” y seleccionamos el .war creado. Por último, solo nos
queda probar si el servicio funciona.

### 2.3. Instalación de Servicio Hello-WS:

Accedemos al directorio helloworld-ws y ejecutamos el siguiente comando:

```
mvn clean install
```

Luego de esto deberemos desplegar el servicio en el Wildfly, para ello accedemos a la
página principal de nuestro servidor WildFly y nos dirigimos a la pestaña “deployments”.

Luego pulsamos sobre el botón “+” y seleccionamos el .war creado. Por último, solo nos
queda probar si el servicio funciona.
