# Servicio Rest-WS WildFly

## Indice

- 1. <a href="#1-requisitos-previos">Requisitos previos:</a>
- 2. Instalación de los servicios:
   - 2.1. Descarga de los ejemplos:
   - 2.2. Instalación de Servicio Hello-RS:
   - 2.3. Instalación de Servicio Hello-WS:
- LINK:


## 1. Requisitos previos:

Necesitaremos:

- Un servidor Ubuntu 20.04:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/1.1.1.png)

- Cuenta de superusuario root:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/1.1.2.png)

- JDK instalado:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/1.1.3.png)

- Para ir adelantando, Maven instalado:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/Instalacion%20Wildfly/1.1.4.png)

- Tener desplegado el servidor de aplicaciones WilFly:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/restWildFly/1.1.5.png)


## 2. Instalación de los servicios:

### 2.1. Descarga de los ejemplos:

Clonamos el repositorio con los ejemplos, está en este <a href="https://github.com/wildfly/quickstart/">enlace</a>.

### 2.2. Instalación de Servicio Hello-RS:

Accedemos al directorio helloworld-rs y ejecutamos el siguiente comando:

```
mvn clean install
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/restWildFly/2.2.1.png)

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/restWildFly/2.2.2.png)

Luego de esto deberemos desplegar el servicio en el Wildfly, para ello accedemos a la
página principal de nuestro servidor WildFly y nos dirigimos a la pestaña “deployments”.

Luego pulsamos sobre el botón “+” y seleccionamos el .war creado. Por último, solo nos
queda probar si el servicio funciona.

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/restWildFly/2.2.3.png)

### 2.3. Instalación de Servicio Hello-WS:

Accedemos al directorio helloworld-ws y ejecutamos el siguiente comando:

```
mvn clean install
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/restWildFly/2.3.1.png)

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/restWildFly/2.3.2.png)

Luego de esto deberemos desplegar el servicio en el Wildfly, para ello accedemos a la
página principal de nuestro servidor WildFly y nos dirigimos a la pestaña “deployments”.

Luego pulsamos sobre el botón “+” y seleccionamos el .war creado. Por último, solo nos
queda probar si el servicio funciona.

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/restWildFly/2.3.3.png)
