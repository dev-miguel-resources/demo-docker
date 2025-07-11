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