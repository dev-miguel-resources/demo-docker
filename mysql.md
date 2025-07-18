# Montar un servidor de MYSQL usando Docker

### 1. Descargar la imagen de MYSQL desde Docker Hub

```
docker pull mysql
```

### 2. Verificar y filtrar imágenes de MYSQL desde la lista de imágenes de Docker

```
docker images (listar todas)
docker images | findStr <string-busqueda> (para linux/mac: se ocupa grep)
Comentario: Se puede filtrar por el nombre de la imagen ó por su ID
```

### 3. Eliminar una imagen

```
docker rmi mysql ó docker rmi <ID>
```

### 4. Crear un contenedor sin nombre con la imagen de MYSQL

```
docker create mysql:8
```

### 5. Eliminar un contenedor

```
docker rm <name-container> | <ID>
docker rm -f <name-container> | <ID> (eliminación forzada de contenedores en ejecución)
```

### 6. Crear un contenedor con nombre

```
docker create --name mysqlserver mysql:8
```

### 7. Listar contenedores

```
docker ps -a (lista todos los contenedores independientes de su status)
docker ps -a | findStr mysqlserver (windows)
docker ps -a | grep mysqlserver (linux/mac)
docker ps (lista solo los que estén en ejecución exitosa)
docker ps | findStr mysqlserver (windows)
docker ps | grep mysqlserver (linux/mac)
```

### 8. Para iniciar o intentar despertar un contenedor 

```
docker start mysqlserver
```

### 9. Para inspeccionar el contenedor 

```
docker logs mysqlserver ó <ID>
```

### 10. Crear y ejecutar un contenedor con variables de entorno, puertos y modo detached 

```
docker run -d --name mysqlserver -p 3310:3306 -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_USER=user -e MYSQL_PASSWORD=1234 -e MYSQL_DATABASE=sqldb mysql:8
```

### 11. Para detener un contenedor

```
docker stop <name-container> or <ID> (detención controlada)
docker kill <name-container> or <ID> (no recomendado): detención forzada que puede generar perdida de información
```

### 12. Para inspeccionar un contenedor, imagenes, volumenes y redes

```
docker inspect mysqlserver (contenedor)
docker inspect mysql:8 (imagen)
docker inspect vol-mysql
docker inspect net-mysql-new
```

### 13. Para ingresar a la red virtual de Docker desde windows

```
\\wsl$ (para habilitar la red virtual de docker en windows)
```

### 14. Para crear un contenedor con un volumen anónimo

```
docker run -d --name mysqlserver -p 3310:3306 -v /var/lib/mysql -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_USER=user -e MYSQL_PASSWORD=1234 -e MYSQL_DATABASE=sqldb mysql:8
```

### 15. Para listar y filtrar volumenes

```
docker volume ls
docker volume ls | findStr <name-volume> or <ID> (windows)
docker volume ls | grep <name-volume> or <ID> (linux/mac)
```

### 16. Para eliminar un contenedor con un volumen anónimo

```
docker rm -fv <name-container>
```

### 17. Para eliminar un volumen especifico nombrado o anónimo

```
docker volume rm <name-volume> OR <name-ID>
```

### 18. Para eliminar volumenes huerfanos

```
docker volume prune
```

### 19. Para crear un contenedor con un volumen asociado de tipo host

```
docker run -d --name mysqlserver -p 3310:3306 -v E:\docker_examples\docker\volume_mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_USER=user -e MYSQL_PASSWORD=1234 -e MYSQL_DATABASE=sqldb mysql:8
```

### 20. Para eliminar mediante comandos un volumen host
```
rmdir /s /q E:\docker_examples\docker\volume_mysql (windows)
rm -rf /ruta/a/la/carpeta (linux/mac)
```

### 21. Para crear un contenedor con un volumen asociado de tipo nombrado
```
docker run -d --name mysqlserver -p 3310:3306 -v volume-mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_USER=user -e MYSQL_PASSWORD=1234 -e MYSQL_DATABASE=sqldb mysql:8
```

### 22. Para crear una red de Docker
```
docker network create <name-network>
docker network create <name-network> -d <type-network>
```

### 22. Para listar las redes
```
docker network ls
```

### 23. Para filtrar un listado de redes
```
docker network ls | findStr new (windows)
docker network ls | grep new (linux/mac)
```

### 24. Para eliminar una red
```
docker network remove <network-name>
```

### 25. Para conectar una red con un contenedor
```
docker network connect <name-network> <name-container>
```

### 26. Para desconectar un contenedor de una red asociada
```
docker network disconnect <name-network> <name-container>
```

### 27. Para crear el contenedor en conjunto de su vinculación de red
```
docker run -d --name mysqlserver --network net-mysql-new -p 3310:3306 -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_USER=user -e MYSQL_PASSWORD=1234 -e MYSQL_DATABASE=sqldb mysql:8
```