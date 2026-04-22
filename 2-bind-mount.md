# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
# COMPLETAR CON EL COMANDO
docker run -d --name nginx-bind -P -v "C:\nginx\html:/usr/share/nginx/html" nginx:alpine

### ¿Qué sucede al ingresar al servidor de nginx?
<img width="1369" height="320" alt="image" src="https://github.com/user-attachments/assets/20886460-2ce1-40c4-ba1e-cfb872df211e" />

Al ingresar al servidor de nginx no se muestra la página por defecto, ya que la carpeta del contenedor fue reemplazada por la carpeta del host mediante bind mount. Como la carpeta html está vacía, no se muestra contenido o puede aparecer un error.

### ¿Qué pasa con el archivo index.html del contenedor?
El archivo index.html del contenedor deja de utilizarse, porque la ruta fue sobrescrita por la carpeta del host, por lo que nginx ya no usa su contenido interno.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?

<img width="1902" height="1078" alt="image" src="https://github.com/user-attachments/assets/5ee29c4c-af48-4d88-a5c9-7e0dd16661d1" />

Al ingresar nuevamente al servidor de nginx, se muestra el template web cargado desde la carpeta del host, ya que nginx está utilizando directamente los archivos del bind mount.

### Eliminar el contenedor
# COMPLETAR CON EL COMANDO

docker rm -f nginx-bind

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
Al crear nuevamente el contenedor, el template sigue apareciendo porque los archivos no estaban guardados dentro del contenedor sino en la carpeta del host. Como el bind mount vuelve a montar la misma carpeta, nginx sigue mostrando el mismo contenido.


