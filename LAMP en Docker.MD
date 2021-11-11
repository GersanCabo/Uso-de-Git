# LAMP en Docker


## Indice

**1. Creando el LAMP**


## 1. Creando el LAMP:

La estructura del proyecto que vamos a crear va a ser el siguiente:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/lampDocker/01.png)

Creamos las carpetas respectivas y empezamos a crear los ficheros empezando por el **Dockerfile** :

```
FROM php: 8. 0. 0 - apache
ARG DEBIAN_FRONTEND=noninteractive
RUN docker-php-ext-install mysqli
RUN apt-get update \
  && apt-get install - y libzip-dev \
  && apt-get install - y zlib 1 g-dev \
  && rm - rf /var/lib/apt/lists/* \
  && docker-php-ext-install zip

RUN a 2 enmod rewrite
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/lampDocker/02.png)

Luego pasamos al fichero **docker-compose.yml** :

```
version: " 3. 5 "
services:
  www:
    build:.
    ports:
      - "80:80"
    volumes:
      - ./www:/var/www/html
    links:
      - db
    networks:
      - default
  db:
    image: mysql: 8. 0
    ports:
      - "3306:3306"
    command: - -default-authentication-plugin=mysql_native_password
    environment:
      MYSQL_DATABASE: dbname
      MYSQL_ROOT_PASSWORD: test
    volumes:
      - ./dump:/docker-entrypoint-initdb.d
      - ./conf:/etc/mysql/conf.d
      - persistent:/var/lib/mysql
    networks:
      - default
  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    links:
      - db:db
    ports:
      - 8000:80
    environment:
      MYSQL_USER: admin
      MYSQL_PASSWORD: test
      MYSQL_ROOT_PASSWORD: test
volumes:
  persistent:
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/lampDocker/03.png)

Y seguimos con el fichero **dbname.sql** :

```
SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
SET time_zone = "+ 00 : 00 ";

/*! 40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;

/*! 40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;

/*! 40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;

/*! 40101 SET NAMES utf 8 mb 4 */;

CREATE TABLE `Data` (
`id` int( 11 ) NOT NULL,
`name` varchar( 20 ) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin 1 ;

INSERT INTO `Data` (`id`, `name`) VALUES ( 1 , 'OpenWebinars Article'), ( 2 , 'Crashell'), ( 3 , 'Jerson Martinez'), ( 4 ,'Antonio Moreno');

/*! 40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;

/*! 40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;

/*! 40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;

```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/lampDocker/04.png)

Por último, creamos el fichero **index.html** en su respectiva ubicación:

```
<html>
    <head>
        <title>Welcome to LAMP Infrastructure</title>
        <meta charset="utf-8">
        <link rel="stylesheet" href="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
        <script src="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js"></script>
    </head>
    <body>
        <div class="container-fluid">
          <img src="https://manolohidalgo.com/wp-content/uploads/2020/10/fondo-despliegue2.jpg" alt="despliegues app web">
            <?php
                echo "<h1>¡Hola, soy Alumno y te da la bienvenida!</h1>";

                $conn = mysqli_connect('db', 'root', 'test', "dbname");
                $query = 'SELECT * From Data';
                $result = mysqli_query($conn, $query);

                echo '<table class="table table-striped">';
                echo '<thead><tr><th></th><th>id</th><th>name</th></tr></thead>';
                while($value = $result->fetch_array(MYSQLI_ASSOC)){
                    echo '<tr>';
                    echo '<td><a href="#"><span class="glyphicon glyphicon-search"></span></a></td>';
                    foreach($value as $element){
                        echo '<td>' . $element . '</td>';
                    }

                    echo '</tr>';
                }
                echo '</table>';

                $result->close();
                mysqli_close($conn);
            ?>
        </div>
    </body>
</html>

```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/lampDocker/05.png)

Luego de crear todo esto, ya podemos lanzar el contenedor, para ello nos ubicamos en la carpeta del proyecto y escribimos el siguiente comando:

```
docker-compose up - d
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/lampDocker/06.png)

Como vemos, se han creado los contenedores.

Para comprobar si se han creado los contenedores, usamos este comando:

```
docker-compose ps
```

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/lampDocker/07.png)

Y probamos si podemos acceder a ellos desde el navegador:

PHPMyAdmin:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/lampDocker/09.png)

Y podemos entrar con el usuario root:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/lampDocker/10.png)

Y también al Apache:

![](https://github.com/GersanCabo/Uso-de-Git/blob/main/img/lampDocker/11.png)

Como vemos por los datos de la base de datos que nos muestra el PHPMyAdmin y el Apache, también se pueden conectar estos procesos correctamente con el servidor MySQL, por lo que los tres funcionan correctamente.
