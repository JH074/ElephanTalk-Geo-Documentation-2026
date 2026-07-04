# Configuración del Backend

Este proyecto consiste en dos servicios backend: una API de NestJS y una API de FastAPI. Ambos servicios están configurados para ejecutarse en contenedores Docker utilizando Docker Compose.

## Requisitos Previos

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Java 11+](https://www.oracle.com/java/technologies/javase/jdk11-archive-downloads.html) (para PhotonAPI)

## Configuración de Variables de Entorno

Crear el archivo `.env` en la raíz del proyecto de la API de NestJS (`./API/.env`):

```plaintext
# Usa host.docker.internal en lugar de localhost si MongoDB se ejecuta localmente en tu máquina host
MONGO_URI="mongodb://host.docker.internal:27017/tu-base-de-datos"
PORT=3000
JWT_SECRET="tu-secreto-jwt"
TOXICITY_URL="http://fastapi-service:8000"
TOXICITY_THRESHOLD=0.25
```

### Descripción de Variables

- **MONGO_URI**: Cadena de conexión a MongoDB. *Nota: Si estás ejecutando la API en Docker y tu base de datos corre directamente en tu máquina host (fuera de Docker), usa `mongodb://host.docker.internal:27017/` en lugar de `localhost` en macOS/Windows, o la IP de la interfaz puente `172.17.0.1` en Linux.*
- **PORT**: Puerto donde ejecutará la API de NestJS
- **JWT_SECRET**: Secreto para la firma de tokens JWT
- **TOXICITY_URL**: URL del servicio de FastAPI para análisis de toxicidad
- **TOXICITY_THRESHOLD**: Umbral de toxicidad (0.0 - 1.0)

## Instalación y Ejecución

### 1. Clonar el Repositorio

```bash
git clone https://github.com/tu-usuario/tu-repositorio.git
cd tu-repositorio
```

### 2. Configurar Variables de Entorno

Asegurar que el archivo `.env` esté en la ubicación correcta (`./API/.env`).

### 3. Construir y Levantar Servicios

```bash
docker-compose up --build
```

Este comando:
- Construye las imágenes Docker para ambos servicios
- Los levanta en sus respectivos puertos
- Crea la red Docker necesaria para la comunicación

## Servicios Disponibles

Una vez ejecutándose, los servicios estarán disponibles en:

- **NestJS API**: `http://localhost:3000`
- **FastAPI Service**: `http://localhost:8000`
- **PhotonAPI Service**: `http://localhost:2322` (ver [configuración específica](photon-api.md))

## Arquitectura Docker Compose

### Servicios Definidos

El archivo `docker-compose.yml` define dos servicios principales:

- **nestjs-api**: La API principal de NestJS
- **fastapi-service**: La API de FastAPI para moderación

### Red Docker

Ambos servicios están conectados a una red Docker llamada `backend-network` que permite la comunicación interna entre servicios.

## Dockerfiles

### Dockerfile de NestJS API

El Dockerfile realiza los siguientes pasos:

1. Usa imagen base con Node.js 20
2. Establece el directorio de trabajo
3. Copia e instala dependencias (`package.json` y `package-lock.json`)
4. Copia el código fuente de la aplicación
5. Copia el archivo `.env`
6. Compila el proyecto TypeScript
7. Expone el puerto 3000
8. Define el comando para ejecutar la aplicación

### Dockerfile de FastAPI

El Dockerfile realiza los siguientes pasos:

1. Usa imagen base con Python 3.10
2. Establece el directorio de trabajo
3. Copia e instala dependencias (`requirements.txt`)
4. **Descarga y almacena el modelo Detoxify** (optimización de imagen)
5. Copia el código fuente de la aplicación
6. Expone el puerto 8000
7. Define el comando para ejecutar la aplicación

## Comandos Útiles

### Detener Servicios
```bash
# Detener con Ctrl+C en la terminal
# O ejecutar en otra terminal:
docker-compose down
```

### Ver Logs
```bash
# Logs de todos los servicios
docker-compose logs -f

# Logs de un servicio específico
docker-compose logs -f nestjs-api
docker-compose logs -f fastapi-service
```

### Reconstruir Servicios
```bash
docker-compose up --build --force-recreate
```

### Ejecutar Comandos en Contenedores
```bash
# Acceder al contenedor de NestJS
docker-compose exec nestjs-api bash

# Acceder al contenedor de FastAPI
docker-compose exec fastapi-service bash
```

## Solución de Problemas

### Error de Conexión a MongoDB
- Verificar que `MONGO_URI` esté correctamente configurada
- Asegurar que MongoDB esté ejecutándose y accesible

### Error de Comunicación entre Servicios
- Verificar que `TOXICITY_URL` use el nombre del servicio Docker (`fastapi-service`)
- Asegurar que ambos servicios estén en la misma red Docker

### Problemas de Construcción de Imagen
- Limpiar imágenes Docker: `docker system prune -a`
- Verificar que todos los archivos necesarios estén presentes

### Puerto ya en Uso
- Cambiar los puertos en `docker-compose.yml`
- Detener otros servicios que usen los mismos puertos

!!! tip "Consejo"
    Para desarrollo, puedes usar `docker-compose up -d` para ejecutar en modo detached (en segundo plano).