### Docker Compose Commands

### 1. Para ejecutar un archivo docker-compose.yaml

```
docker compose up -d
docker-compose up -d
```

### 2. Para eliminar lo definido en el docker compose

```
docker compose down
```

### 3. Para listar y filtrar servicios gestionados por docker compose

```
docker compose ps
docker compose ps | findStr <name> or <service> or <image> (windows)
docker compose ps | grep <name> or <service> or <image> (linux-mac)
```

### 4. Para detener todos los servicios

```
docker compose stop
```

### 5. Para despertar todos los servicios

```
docker compose start
```

### 6. Para detener un determinado servicio

```
docker compose stop <name-service>
```

### 7. Para despertar un determinado servicio

```
docker compose start <name-service>
```