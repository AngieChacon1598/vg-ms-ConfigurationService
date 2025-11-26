# Configuration Service

Microservicio de configuración disponible como imagen Docker.

## 🐳 Docker Hub

Esta imagen está disponible en Docker Hub:

**🔗 [angie14/configurationservice](https://hub.docker.com/r/angie14/configurationservice)**

## 📦 Instalación

### Descargar la imagen

Para descargar la última versión de la imagen:

```bash
docker pull angie14/configurationservice:latest
```

## 🚀 Uso

### Ejecutar el contenedor

Para ejecutar el contenedor en modo detached (segundo plano):

```bash
docker run -d -p 5004:5004 --name configurationservice angie14/configurationservice:latest
```

**Parámetros del comando:**
- `-d`: Ejecuta el contenedor en segundo plano (modo detached)
- `-p 5004:5004`: Mapea el puerto 5004 del contenedor al puerto 5004 del host
- `--name configurationservice`: Asigna un nombre al contenedor para facilitar su gestión

### Verificar que el contenedor está corriendo

```bash
docker ps
```

### Ver los logs del contenedor

```bash
docker logs configurationservice
```

### Detener el contenedor

```bash
docker stop configurationservice
```

### Iniciar el contenedor nuevamente

```bash
docker start configurationservice
```

### Eliminar el contenedor

```bash
docker rm configurationservice
```

## 📝 Notas

- El servicio estará disponible en `http://localhost:5004` después de iniciar el contenedor
- Para más información sobre la imagen, visita la [página en Docker Hub](https://hub.docker.com/r/angie14/configurationservice)
