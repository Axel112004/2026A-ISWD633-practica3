## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
docker network create net-wp

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
La carpeta db del host contiene los archivos de datos de MySQL, es decir, donde se guardan las bases de datos y la información interna para que persista.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD

docker run -d --name mysql-wp --network net-wp -v ${PWD}\db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root123 -e MYSQL_DATABASE=wordpress -e MYSQL_USER=wpuser -e MYSQL_PASSWORD=wp123 mysql:8

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
La carpeta db, que inicialmente estaba vacía, ahora contiene archivos y subcarpetas creados automáticamente por MySQL para almacenar la base de datos y su información interna.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Al eliminar y volver a crear el contenedor, la información se mantiene. Esto sucede porque los datos de WordPress y MySQL están almacenados en carpetas del host mediante volúmenes (db y www), por lo que no se pierden al eliminar el contenedor.
<img width="1907" height="1077" alt="image" src="https://github.com/user-attachments/assets/c239773f-7c1b-4ae9-8786-cbfcba7c3a94" />


