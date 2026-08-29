# Curso de Docker y Tecnologías Relacionadas

## Nivel Fundamentos e Intermedio

### Duración sugerida

**40 a 50 horas**, distribuidas en teoría, demostraciones, prácticas y proyecto integrador.

### Modalidad

Presencial, virtual o híbrida.

### Nivel

Fundamentos → Intermedio.

### Requisitos previos

No se requiere experiencia previa con Docker. Se recomienda que el participante tenga conocimientos básicos de:

* sistemas operativos;
* uso de terminal;
* archivos y directorios;
* conceptos básicos de redes;
* Git;
* programación básica en algún lenguaje.

---

# 1. Objetivo general

Desarrollar en el participante las competencias necesarias para diseñar, construir, ejecutar, administrar y distribuir aplicaciones mediante contenedores Docker, utilizando buenas prácticas de arquitectura, redes, persistencia, seguridad, automatización y despliegue.

Al finalizar el curso, el participante será capaz de utilizar Docker como parte de un flujo moderno de desarrollo de software y estará preparado para comenzar posteriormente con tecnologías de orquestación como Kubernetes.

---

# 2. Competencias a desarrollar

Al terminar el curso, el participante podrá:

1. Explicar las diferencias entre máquinas virtuales y contenedores.
2. Instalar y configurar Docker correctamente.
3. Crear, ejecutar, detener y administrar contenedores.
4. Trabajar con imágenes Docker.
5. Construir imágenes mediante Dockerfile.
6. Optimizar imágenes mediante capas y multistage builds.
7. Administrar almacenamiento mediante volumes y bind mounts.
8. Configurar redes Docker.
9. Comunicar múltiples contenedores entre sí.
10. Crear entornos mediante Docker Compose.
11. Gestionar variables de entorno y configuraciones.
12. Implementar health checks.
13. Utilizar Docker Hub y registros privados.
14. Aplicar buenas prácticas de seguridad.
15. Analizar logs, procesos y consumo de recursos.
16. Diagnosticar problemas comunes.
17. Integrar Docker con Git y CI/CD.
18. Crear entornos de desarrollo reproducibles.
19. Diseñar arquitecturas multicontenedor.
20. Comprender los fundamentos de Kubernetes y la orquestación de contenedores.

---

# 3. Estructura general del curso

## BLOQUE I — Fundamentos

### Módulo 1. Introducción a Docker

### Módulo 2. Instalación y entorno de trabajo

### Módulo 3. Contenedores

### Módulo 4. Imágenes Docker

### Módulo 5. Dockerfile

### Módulo 6. Persistencia y almacenamiento

## BLOQUE II — Intermedio

### Módulo 7. Redes Docker

### Módulo 8. Docker Compose

### Módulo 9. Configuración y variables de entorno

### Módulo 10. Optimización de imágenes

### Módulo 11. Logs, monitoreo y diagnóstico

### Módulo 12. Seguridad en Docker

### Módulo 13. Docker Registry

### Módulo 14. Docker en desarrollo de software

### Módulo 15. Docker y CI/CD

### Módulo 16. Arquitecturas multicontenedor

### Módulo 17. Introducción a Kubernetes

## BLOQUE III — Proyecto integrador

---

# MÓDULO 1. INTRODUCCIÓN A DOCKER

## Objetivos

Comprender qué problema resuelve Docker y cómo funciona la tecnología de contenedores.

## Temas

### 1.1 El problema tradicional

Una aplicación normalmente depende de:

* sistema operativo;
* runtime;
* librerías;
* configuración;
* variables de entorno;
* servicios externos;
* versiones determinadas.

Un problema común es:

> "En mi computadora sí funciona."

Docker busca hacer que el entorno de ejecución sea reproducible.

---

## 1.2 ¿Qué es Docker?

Docker es una plataforma para construir, distribuir y ejecutar aplicaciones dentro de contenedores.

Un contenedor empaqueta:

* aplicación;
* dependencias;
* librerías;
* configuración necesaria para ejecutar la aplicación.

---

## 1.3 Máquina virtual vs contenedor

### Máquina virtual

```text
Hardware
│
Host OS
│
Hypervisor
├── Guest OS
│   └── App
├── Guest OS
│   └── App
```

Cada máquina virtual incorpora su propio sistema operativo.

### Contenedores

```text
Hardware
│
Host OS
│
Docker Engine
├── Container
├── Container
├── Container
```

Los contenedores comparten el kernel del sistema anfitrión.

---

## 1.4 Ventajas de los contenedores

* portabilidad;
* reproducibilidad;
* aislamiento;
* velocidad;
* menor consumo de recursos;
* facilidad de despliegue;
* facilidad de escalamiento;
* consistencia entre desarrollo y producción.

---

## 1.5 Conceptos fundamentales

### Docker Engine

Motor encargado de ejecutar los contenedores.

### Docker CLI

Interfaz de línea de comandos.

```bash
docker
```

### Docker daemon

Servicio que administra:

* imágenes;
* contenedores;
* redes;
* volúmenes.

Normalmente:

```text
dockerd
```

### Imagen

Plantilla de solo lectura utilizada para crear contenedores.

### Contenedor

Instancia ejecutable de una imagen.

### Registry

Servidor que almacena imágenes Docker.

Ejemplo:

```text
Docker Hub
```

---

# Práctica 1

Verificar Docker.

```bash
docker --version
```

Consultar información.

```bash
docker info
```

Ejecutar el primer contenedor.

```bash
docker run hello-world
```

---

# MÓDULO 2. INSTALACIÓN Y ENTORNO DE TRABAJO

## Sistemas

Docker puede utilizarse desde:

* Linux;
* Windows;
* macOS.

En Windows y macOS suele utilizarse Docker Desktop.

---

## Componentes principales

```text
Docker CLI
     │
     ▼
Docker Engine
     │
 ┌───┼────┐
 ▼   ▼    ▼
Images Containers Networks
              │
           Volumes
```

---

## Comandos iniciales

```bash
docker version
```

```bash
docker info
```

```bash
docker help
```

Consultar ayuda:

```bash
docker run --help
```

---

# MÓDULO 3. CONTENEDORES

## 3.1 Ejecutar un contenedor

```bash
docker run nginx
```

Docker realizará:

```text
Buscar imagen local
        ↓
¿Existe?
   ↓       ↓
  Sí      No
           ↓
       Descargar
           ↓
Crear contenedor
           ↓
Ejecutar contenedor
```

---

## 3.2 Ejecutar en segundo plano

```bash
docker run -d nginx
```

`-d` significa:

```text
detached
```

---

## 3.3 Listar contenedores

Contenedores activos:

```bash
docker ps
```

Todos:

```bash
docker ps -a
```

---

## 3.4 Nombrar contenedores

```bash
docker run -d --name servidor-web nginx
```

---

## 3.5 Detener

```bash
docker stop servidor-web
```

---

## 3.6 Iniciar nuevamente

```bash
docker start servidor-web
```

---

## 3.7 Reiniciar

```bash
docker restart servidor-web
```

---

## 3.8 Eliminar

```bash
docker rm servidor-web
```

Forzar:

```bash
docker rm -f servidor-web
```

---

## 3.9 Ejecutar comandos dentro del contenedor

```bash
docker exec servidor-web ls
```

Abrir terminal:

```bash
docker exec -it servidor-web sh
```

o:

```bash
docker exec -it servidor-web bash
```

---

## 3.10 Logs

```bash
docker logs servidor-web
```

Seguimiento:

```bash
docker logs -f servidor-web
```

Últimas líneas:

```bash
docker logs --tail 100 servidor-web
```

---

## 3.11 Publicación de puertos

```bash
docker run -d \
-p 8080:80 \
nginx
```

Interpretación:

```text
localhost:8080
      │
      ▼
container:80
```

Formato:

```text
HOST:CONTAINER
```

---

# Práctica 2

Crear servidor:

```bash
docker run -d \
--name web \
-p 8080:80 \
nginx
```

Comprobar:

```text
http://localhost:8080
```

Consultar:

```bash
docker ps
```

Consultar logs:

```bash
docker logs web
```

Ingresar:

```bash
docker exec -it web sh
```

---

# MÓDULO 4. IMÁGENES DOCKER

## Listar imágenes

```bash
docker images
```

También:

```bash
docker image ls
```

---

## Descargar imagen

```bash
docker pull nginx
```

---

## Tags

Una imagen puede identificarse mediante:

```text
nombre:tag
```

Ejemplo:

```text
postgres:17
```

```text
node:22
```

```text
nginx:alpine
```

Cuando no se especifica tag:

```text
latest
```

---

## Eliminar imagen

```bash
docker rmi nginx
```

---

## Inspeccionar

```bash
docker inspect nginx
```

---

## Capas

Las imágenes Docker se construyen mediante capas.

Ejemplo:

```text
Ubuntu
   ↓
Node
   ↓
Dependencias
   ↓
Aplicación
```

Las capas permiten reutilización y cache.

---

# MÓDULO 5. DOCKERFILE

Un Dockerfile describe cómo construir una imagen.

---

## Ejemplo básico

Aplicación Node:

```dockerfile
FROM node:22-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

---

## FROM

Define imagen base.

```dockerfile
FROM node:22-alpine
```

---

## WORKDIR

Define directorio de trabajo.

```dockerfile
WORKDIR /app
```

---

## COPY

Copia archivos.

```dockerfile
COPY . .
```

---

## RUN

Ejecuta comandos durante la construcción.

```dockerfile
RUN npm install
```

---

## CMD

Comando predeterminado del contenedor.

```dockerfile
CMD ["npm", "start"]
```

---

## ENTRYPOINT

Define el ejecutable principal.

```dockerfile
ENTRYPOINT ["python"]
```

---

## EXPOSE

Documenta el puerto utilizado.

```dockerfile
EXPOSE 8080
```

Importante:

`EXPOSE` no publica automáticamente el puerto.

---

## Construir imagen

```bash
docker build -t mi-app .
```

---

## Ejecutar

```bash
docker run -p 3000:3000 mi-app
```

---

# .dockerignore

Evita copiar archivos innecesarios.

Ejemplo:

```text
node_modules
.git
.env
dist
coverage
README.md
```

---

# Práctica 3

Crear estructura:

```text
proyecto/
│
├── Dockerfile
├── .dockerignore
├── package.json
└── src/
```

Construir:

```bash
docker build -t curso-api:v1 .
```

Ejecutar:

```bash
docker run -d \
--name curso-api \
-p 3000:3000 \
curso-api:v1
```

---

# MÓDULO 6. PERSISTENCIA Y ALMACENAMIENTO

Por defecto los datos internos de un contenedor deben considerarse efímeros.

Cuando el contenedor se elimina:

```text
Container
   ↓
Filesystem
   ↓
Eliminado
```

Para datos persistentes existen diferentes mecanismos.

---

# 6.1 Volumes

Crear:

```bash
docker volume create datos
```

Listar:

```bash
docker volume ls
```

Utilizar:

```bash
docker run \
-v datos:/var/lib/postgresql/data \
postgres
```

---

# 6.2 Bind mounts

Relacionan un directorio del host con el contenedor.

```bash
docker run \
-v ./src:/app/src \
mi-app
```

Conceptualmente:

```text
Host                Container

./src  ───────────▶ /app/src
```

---

# 6.3 --mount

Sintaxis alternativa y explícita:

```bash
docker run \
--mount type=volume,source=datos,target=/data \
mi-app
```

---

# Diferencias

| Característica          | Volume          | Bind mount |
| ----------------------- | --------------- | ---------- |
| Administrado por Docker | Sí              | No         |
| Ruta host configurable  | No directamente | Sí         |
| Persistencia            | Sí              | Sí         |
| Desarrollo              | Bueno           | Excelente  |
| Producción              | Excelente       | Depende    |

---

# Práctica 4

Crear base PostgreSQL:

```bash
docker volume create postgres-data
```

```bash
docker run -d \
--name postgres \
-e POSTGRES_PASSWORD=123456 \
-v postgres-data:/var/lib/postgresql/data \
-p 5432:5432 \
postgres
```

Eliminar:

```bash
docker rm -f postgres
```

Crear nuevamente utilizando el mismo volumen.

Comprobar que los datos continúan existiendo.

---

# MÓDULO 7. REDES DOCKER

Docker proporciona redes virtuales para comunicar contenedores.

---

## Tipos principales

### bridge

Predeterminada para contenedores locales.

### host

Comparte red con el host.

### none

Sin conectividad.

---

## Listar

```bash
docker network ls
```

---

## Crear

```bash
docker network create backend
```

---

## Conectar contenedores

```bash
docker run -d \
--name database \
--network backend \
postgres
```

```bash
docker run -d \
--name api \
--network backend \
mi-api
```

La aplicación podrá acceder a:

```text
database:5432
```

No necesita conocer la IP.

Docker proporciona resolución DNS interna.

---

## Arquitectura

```text
Internet
   │
   ▼
Frontend
   │
   ▼
API
   │
   ▼
Database
```

Podemos tener:

```text
frontend-network
backend-network
```

---

# MÓDULO 8. DOCKER COMPOSE

Docker Compose permite definir aplicaciones multicontenedor mediante YAML.

Archivo habitual:

```text
compose.yaml
```

o:

```text
docker-compose.yml
```

---

## Ejemplo

```yaml
services:

  api:
    build: .
    ports:
      - "3000:3000"

  db:
    image: postgres:17
    environment:
      POSTGRES_USER: app
      POSTGRES_PASSWORD: secret
      POSTGRES_DB: database
```

---

## Ejecutar

```bash
docker compose up
```

Segundo plano:

```bash
docker compose up -d
```

---

## Detener

```bash
docker compose down
```

---

## Reconstruir

```bash
docker compose up -d --build
```

---

## Logs

```bash
docker compose logs
```

```bash
docker compose logs -f
```

Servicio específico:

```bash
docker compose logs api
```

---

# Compose con volumen

```yaml
services:

  db:
    image: postgres:17

    environment:
      POSTGRES_USER: app
      POSTGRES_PASSWORD: password
      POSTGRES_DB: appdb

    volumes:
      - postgres-data:/var/lib/postgresql/data

volumes:
  postgres-data:
```

---

# Compose con redes

```yaml
services:

  api:
    build: .
    networks:
      - backend

  db:
    image: postgres:17
    networks:
      - backend

networks:
  backend:
```

---

# Dependencias

```yaml
depends_on:
  - db
```

Ejemplo:

```yaml
services:

  api:
    build: .
    depends_on:
      - db

  db:
    image: postgres:17
```

Importante:

`depends_on` controla principalmente orden de inicio, pero no necesariamente garantiza que una aplicación esté lista para recibir conexiones.

Por ello pueden utilizarse healthchecks.

---

# MÓDULO 9. VARIABLES DE ENTORNO

Docker permite introducir configuración mediante variables.

```bash
docker run \
-e DATABASE_HOST=db \
-e DATABASE_PORT=5432 \
mi-api
```

---

# Archivo .env

```env
DB_USER=app
DB_PASSWORD=secret
DB_NAME=appdb
```

Compose:

```yaml
environment:
  POSTGRES_USER: ${DB_USER}
  POSTGRES_PASSWORD: ${DB_PASSWORD}
```

---

## No subir secretos

`.gitignore`:

```text
.env
```

Nunca deberían almacenarse contraseñas reales directamente en:

```text
Dockerfile
compose.yaml
repositorios públicos
```

---

# MÓDULO 10. OPTIMIZACIÓN DE IMÁGENES

## Problema

Dockerfile:

```dockerfile
COPY . .

RUN npm install
```

Cualquier cambio invalida la caché.

Mejor:

```dockerfile
COPY package*.json ./

RUN npm ci

COPY . .
```

---

# Multi-stage builds

Permiten separar compilación y ejecución.

Ejemplo:

```dockerfile
FROM node:22-alpine AS build

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build


FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html
```

Resultado:

```text
Etapa Build
Node + compilador + dependencias
             │
             ▼
        archivos dist
             │
             ▼
Etapa final
Nginx + aplicación
```

Ventajas:

* imágenes más pequeñas;
* menor superficie de ataque;
* despliegue más rápido;
* menos dependencias innecesarias.

---

# MÓDULO 11. LOGS, RECURSOS Y DIAGNÓSTICO

## Logs

```bash
docker logs container
```

---

## Estadísticas

```bash
docker stats
```

Muestra:

```text
CPU
Memory
Network
Processes
```

---

## Procesos

```bash
docker top container
```

---

## Inspect

```bash
docker inspect container
```

Puede mostrar:

* IP;
* mounts;
* variables;
* configuración;
* redes;
* estado.

---

## Espacio utilizado

```bash
docker system df
```

---

## Limpieza

```bash
docker system prune
```

Precaución: elimina recursos no utilizados.

---

# Estrategia de troubleshooting

Cuando un contenedor falla:

```text
1. docker ps -a
      ↓
2. docker logs
      ↓
3. docker inspect
      ↓
4. verificar variables
      ↓
5. verificar red
      ↓
6. verificar volumen
      ↓
7. entrar al container
```

---

# MÓDULO 12. HEALTHCHECKS

Docker puede verificar la salud de una aplicación.

Dockerfile:

```dockerfile
HEALTHCHECK \
CMD curl -f http://localhost:3000/health || exit 1
```

Compose:

```yaml
healthcheck:
  test:
    - CMD
    - curl
    - -f
    - http://localhost:3000/health
  interval: 30s
  timeout: 10s
  retries: 3
```

Estados posibles:

```text
starting
healthy
unhealthy
```

---

# MÓDULO 13. SEGURIDAD

Docker no debe considerarse automáticamente seguro simplemente por utilizar contenedores.

---

## Principios

### No ejecutar como root

Dockerfile:

```dockerfile
RUN addgroup -S appgroup \
    && adduser -S appuser -G appgroup

USER appuser
```

---

## Utilizar imágenes pequeñas

Preferir cuando sea posible:

```text
alpine
slim
distroless
```

---

## Fijar versiones

Evitar depender únicamente de:

```text
latest
```

Preferible:

```text
node:22-alpine
postgres:17
```

---

## No guardar secretos

Evitar:

```dockerfile
ENV PASSWORD=123456
```

---

## Actualizar imágenes

Las imágenes deben mantenerse actualizadas para reducir vulnerabilidades conocidas.

---

## Escanear vulnerabilidades

Dependiendo de las herramientas disponibles pueden emplearse analizadores como:

```text
Docker Scout
Trivy
Grype
```

---

## Reducir superficie de ataque

No instalar:

* compiladores innecesarios;
* herramientas de debugging;
* utilidades no utilizadas;
* shells si no son necesarias.

---

## Principio de mínimo privilegio

El contenedor debe recibir únicamente los permisos que necesita.

---

# MÓDULO 14. DOCKER REGISTRY

Un registry almacena imágenes Docker.

Ejemplos:

```text
Docker Hub
GitHub Container Registry
GitLab Container Registry
Amazon ECR
Google Artifact Registry
Azure Container Registry
Harbor
```

---

## Login

```bash
docker login
```

---

## Tag

```bash
docker tag mi-api usuario/mi-api:1.0
```

---

## Push

```bash
docker push usuario/mi-api:1.0
```

---

## Pull

```bash
docker pull usuario/mi-api:1.0
```

---

# Versionamiento recomendado

Ejemplo:

```text
api:1
api:1.1
api:1.1.0
api:develop
api:staging
api:production
```

En proyectos formales puede utilizarse Semantic Versioning.

```text
MAJOR.MINOR.PATCH
```

Ejemplo:

```text
2.4.1
```

---

# MÓDULO 15. DOCKER EN DESARROLLO

Docker puede utilizarse para crear entornos reproducibles.

Arquitectura típica:

```text
Developer
   │
Docker Compose
   │
   ├── Frontend
   ├── API
   ├── PostgreSQL
   ├── Redis
   └── Mail service
```

---

# Hot Reload

Ejemplo:

```yaml
services:

  api:
    build: .

    volumes:
      - ./src:/app/src

    ports:
      - "3000:3000"
```

Los cambios locales se reflejan en el contenedor.

---

# Desarrollo vs producción

Conviene separar configuraciones.

Ejemplo:

```text
compose.yaml
compose.dev.yaml
compose.prod.yaml
```

---

# MÓDULO 16. DOCKER CON BASES DE DATOS

## PostgreSQL

```yaml
services:

  postgres:
    image: postgres:17

    environment:
      POSTGRES_USER: app
      POSTGRES_PASSWORD: secret
      POSTGRES_DB: appdb

    volumes:
      - postgres-data:/var/lib/postgresql/data

    ports:
      - "5432:5432"

volumes:
  postgres-data:
```

---

## MySQL

```yaml
services:

  mysql:
    image: mysql

    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: appdb
```

---

## Redis

```yaml
services:

  redis:
    image: redis:alpine
```

---

# MÓDULO 17. ARQUITECTURA MULTICONTENEDOR

Ejemplo de arquitectura moderna:

```text
                    Internet
                        │
                        ▼
                     Nginx
                        │
               ┌────────┴─────────┐
               ▼                  ▼
            Frontend             API
                                   │
                      ┌────────────┼────────────┐
                      ▼            ▼            ▼
                  PostgreSQL     Redis        Storage
```

Docker Compose:

```yaml
services:

  frontend:
    build: ./frontend

  api:
    build: ./api

  postgres:
    image: postgres:17

  redis:
    image: redis:alpine

  nginx:
    image: nginx
```

---

# MÓDULO 18. REVERSE PROXY

Un reverse proxy recibe las solicitudes y las dirige al servicio correspondiente.

Ejemplo:

```text
Usuario
   │
   ▼
Nginx
 ├──── /api ─────▶ API
 │
 └──── / ────────▶ Frontend
```

Tecnologías frecuentes:

```text
Nginx
Traefik
HAProxy
Caddy
```

---

# MÓDULO 19. DOCKER Y GIT

Dockerfile y Compose normalmente se almacenan en Git.

Ejemplo:

```text
proyecto/
│
├── frontend/
│   └── Dockerfile
│
├── backend/
│   └── Dockerfile
│
├── compose.yaml
├── .env.example
├── .gitignore
└── README.md
```

---

# .env.example

En lugar de almacenar secretos:

```env
DB_USER=
DB_PASSWORD=
DB_NAME=
JWT_SECRET=
```

---

# MÓDULO 20. DOCKER Y CI/CD

Docker se integra especialmente bien con pipelines.

Proceso:

```text
Developer
   │
   ▼
Git Push
   │
   ▼
CI/CD
   │
   ├── Test
   │
   ├── Build Docker image
   │
   ├── Security scan
   │
   └── Push Registry
          │
          ▼
        Deploy
```

---

## Pipeline conceptual

```yaml
steps:

  - checkout

  - test

  - docker build

  - docker push

  - deploy
```

---

# GitHub Actions conceptual

```yaml
name: Docker Build

on:
  push:
    branches:
      - main

jobs:

  build:

    runs-on: ubuntu-latest

    steps:

      - uses: actions/checkout@v4

      - name: Build
        run: docker build -t mi-api .
```

Posteriormente puede incorporarse:

```text
login registry
push image
deploy
```

---

# MÓDULO 21. LIMITACIÓN DE RECURSOS

Los contenedores pueden limitar CPU y memoria.

Ejemplo:

```bash
docker run \
--memory="512m" \
--cpus="1.0" \
mi-api
```

Esto evita que un servicio consuma recursos excesivos.

---

# MÓDULO 22. POLÍTICAS DE REINICIO

Docker puede reiniciar automáticamente servicios.

Ejemplo:

```bash
docker run \
--restart unless-stopped \
nginx
```

Compose:

```yaml
restart: unless-stopped
```

Opciones comunes:

```text
no
always
on-failure
unless-stopped
```

---

# MÓDULO 23. BUENAS PRÁCTICAS DE DOCKERFILE

## 1. Utilizar imágenes pequeñas

```dockerfile
FROM node:22-alpine
```

---

## 2. Copiar primero dependencias

```dockerfile
COPY package*.json ./

RUN npm ci

COPY . .
```

---

## 3. Utilizar .dockerignore

```text
.git
node_modules
.env
```

---

## 4. No ejecutar como root

```dockerfile
USER node
```

---

## 5. Multi-stage builds

Separar:

```text
build
runtime
```

---

## 6. Fijar versiones

Mejor:

```dockerfile
FROM node:22-alpine
```

que depender indefinidamente de:

```dockerfile
FROM node:latest
```

---

## 7. Una responsabilidad principal

No se recomienda utilizar un contenedor como si fuera una máquina virtual completa.

Preferible:

```text
Container API
Container Database
Container Cache
```

en lugar de:

```text
Container
├── API
├── Database
├── Redis
└── Nginx
```

---

# MÓDULO 24. COMANDOS ESENCIALES

## Contenedores

```bash
docker ps
```

```bash
docker ps -a
```

```bash
docker run
```

```bash
docker stop
```

```bash
docker start
```

```bash
docker restart
```

```bash
docker rm
```

```bash
docker exec
```

```bash
docker logs
```

---

## Imágenes

```bash
docker images
```

```bash
docker pull
```

```bash
docker build
```

```bash
docker rmi
```

```bash
docker tag
```

```bash
docker push
```

---

## Volúmenes

```bash
docker volume ls
```

```bash
docker volume create
```

```bash
docker volume inspect
```

```bash
docker volume rm
```

---

## Redes

```bash
docker network ls
```

```bash
docker network create
```

```bash
docker network inspect
```

```bash
docker network connect
```

```bash
docker network disconnect
```

---

## Compose

```bash
docker compose up
```

```bash
docker compose up -d
```

```bash
docker compose down
```

```bash
docker compose ps
```

```bash
docker compose logs
```

```bash
docker compose build
```

```bash
docker compose restart
```

---

# MÓDULO 25. DOCKER INTERNO

Para comprender Docker a nivel intermedio es conveniente conocer tres tecnologías fundamentales de Linux.

## Namespaces

Proporcionan aislamiento.

Pueden aislar:

```text
procesos
red
usuarios
filesystem
hostname
```

---

## Control Groups — cgroups

Controlan recursos como:

```text
CPU
RAM
I/O
```

---

## Filesystems por capas

Docker utiliza sistemas de archivos por capas.

Conceptualmente:

```text
Layer 4  Application
Layer 3  Dependencies
Layer 2  Runtime
Layer 1  Base OS
```

Esto permite:

* reutilización;
* cache;
* almacenamiento eficiente.

---

# MÓDULO 26. DOCKER ENGINE Y CONTAINERD

Arquitectura simplificada:

```text
Docker CLI
    │
    ▼
Docker Engine
    │
    ▼
containerd
    │
    ▼
runc
    │
    ▼
Linux Kernel
```

### containerd

Gestiona el ciclo de vida de los contenedores.

### runc

Ejecuta contenedores siguiendo estándares OCI.

---

# MÓDULO 27. OPEN CONTAINER INITIATIVE

OCI define estándares para contenedores.

Principalmente:

```text
OCI Image Specification

OCI Runtime Specification
```

Esto permite que el ecosistema de contenedores no dependa exclusivamente de Docker.

---

# MÓDULO 28. ALTERNATIVAS Y TECNOLOGÍAS RELACIONADAS

Además de Docker existen tecnologías como:

### Podman

Motor de contenedores con arquitectura daemonless.

### containerd

Runtime ampliamente utilizado.

### Buildah

Construcción de imágenes.

### CRI-O

Runtime especializado en Kubernetes.

---

# MÓDULO 29. ORQUESTACIÓN

Docker Compose funciona muy bien para:

* desarrollo;
* pruebas;
* entornos pequeños;
* despliegues simples.

Cuando existen:

```text
50 containers
100 containers
500 containers
```

se vuelve necesario un orquestador.

---

# MÓDULO 30. INTRODUCCIÓN A KUBERNETES

Kubernetes administra aplicaciones contenerizadas distribuidas.

Permite:

* escalamiento;
* autorecuperación;
* balanceo;
* despliegues graduales;
* administración de configuración;
* descubrimiento de servicios.

---

# Arquitectura conceptual

```text
Kubernetes Cluster

Control Plane
     │
 ┌───┴───────────┐
 ▼               ▼
Node 1          Node 2
 │               │
Pods            Pods
 │               │
Containers      Containers
```

---

# Conceptos iniciales

## Pod

Unidad mínima desplegable.

```text
Pod
 └── Container
```

Puede contener más de un contenedor.

---

## Deployment

Administra réplicas y despliegues.

---

## Service

Proporciona conectividad estable hacia los pods.

---

## ConfigMap

Configuración no sensible.

---

## Secret

Datos sensibles.

---

## Ingress

Entrada HTTP/HTTPS hacia aplicaciones.

---

# Relación Docker → Kubernetes

Lo aprendido con Docker sigue siendo fundamental.

```text
Dockerfile
   ↓
Docker Image
   ↓
Registry
   ↓
Kubernetes
   ↓
Pods
```

---

# PROYECTO INTEGRADOR

## Desarrollo de plataforma multicontenedor

Construir una aplicación con la siguiente arquitectura:

```text
                    Internet
                        │
                        ▼
                      Nginx
                        │
            ┌───────────┴───────────┐
            ▼                       ▼
         React                    API
                                   │
                         ┌─────────┴─────────┐
                         ▼                   ▼
                    PostgreSQL             Redis
```

---

# Requisitos

El proyecto deberá incluir:

```text
Dockerfile Frontend
Dockerfile Backend
Docker Compose
PostgreSQL
Redis
Nginx
Volumes
Networks
Variables de entorno
Healthchecks
Restart policies
.dockerignore
README
```

---

# Arquitectura de red

Crear al menos:

```text
frontend-network

backend-network
```

La base de datos no debería ser accesible directamente desde Internet en un entorno de producción.

---

# Persistencia

La base de datos utilizará:

```text
postgres-data
```

mediante Docker volume.

---

# Configuración

Crear:

```text
.env.example
```

No almacenar:

```text
.env
```

en Git.

---

# Entregables

```text
proyecto/
│
├── frontend/
│   ├── Dockerfile
│   └── .dockerignore
│
├── backend/
│   ├── Dockerfile
│   └── .dockerignore
│
├── nginx/
│   └── nginx.conf
│
├── compose.yaml
│
├── .env.example
│
├── .gitignore
│
└── README.md
```

---

# PROYECTO FINAL — NIVEL INTERMEDIO

El alumno deberá demostrar que puede ejecutar:

```bash
git clone proyecto
```

después:

```bash
docker compose up -d
```

y obtener automáticamente todo el sistema.

Ese es uno de los principales objetivos del uso correcto de contenedores:

> infraestructura reproducible.

---

# EVALUACIÓN

## Evaluación sugerida

| Componente             | Porcentaje |
| ---------------------- | ---------: |
| Prácticas individuales |       25 % |
| Cuestionarios          |       15 % |
| Ejercicios Dockerfile  |       15 % |
| Docker Compose         |       15 % |
| Proyecto integrador    |       30 % |

---

# Prácticas propuestas

## Práctica 1

Ejecutar Nginx.

## Práctica 2

Administrar contenedores.

## Práctica 3

Crear una imagen personalizada.

## Práctica 4

Utilizar bind mounts.

## Práctica 5

Persistir PostgreSQL.

## Práctica 6

Crear red Docker.

## Práctica 7

Conectar API y PostgreSQL.

## Práctica 8

Crear Docker Compose.

## Práctica 9

Implementar variables de entorno.

## Práctica 10

Crear multistage build.

## Práctica 11

Implementar healthcheck.

## Práctica 12

Publicar una imagen en Registry.

## Práctica 13

Analizar vulnerabilidades.

## Práctica 14

Limitar recursos.

## Práctica 15

Configurar reverse proxy.

## Práctica 16

Pipeline CI/CD.

## Práctica 17

Proyecto multicontenedor.

---

# EJERCICIOS DE TROUBLESHOOTING

El instructor puede proporcionar escenarios deliberadamente incorrectos.

## Caso 1

```text
Error:
port already allocated
```

El alumno debe identificar que el puerto está ocupado.

---

## Caso 2

```text
API cannot connect database
```

Revisar:

```text
hostname
network
variables
database health
```

---

## Caso 3

Los datos desaparecen al eliminar PostgreSQL.

Identificar:

```text
falta de volume
```

---

## Caso 4

La imagen pesa 1.8 GB.

El alumno deberá reducirla utilizando:

```text
imagen Alpine/Slim
.dockerignore
multistage build
eliminación de dependencias innecesarias
```

---

## Caso 5

El servicio funciona localmente pero no puede accederse desde el navegador.

Revisar:

```text
EXPOSE
-p
binding 0.0.0.0
firewall
```

---

# PREGUNTAS DE REPASO

## Fundamentos

1. ¿Qué diferencia existe entre imagen y contenedor?
2. ¿Qué diferencia existe entre contenedor y máquina virtual?
3. ¿Qué función cumple Docker Engine?
4. ¿Qué es Docker Hub?
5. ¿Qué representa un tag?

## Dockerfile

6. ¿Qué función cumple FROM?
7. ¿Cuál es la diferencia entre RUN y CMD?
8. ¿Para qué sirve WORKDIR?
9. ¿Qué función cumple .dockerignore?
10. ¿Qué ventajas tienen los multistage builds?

## Persistencia

11. ¿Qué diferencia existe entre volume y bind mount?
12. ¿Por qué no debe almacenarse una base de datos únicamente dentro del filesystem del contenedor?

## Redes

13. ¿Cómo se comunican dos contenedores de la misma red?
14. ¿Por qué es preferible utilizar nombres DNS de servicios en lugar de IP?

## Compose

15. ¿Qué problema resuelve Docker Compose?
16. ¿Qué hace `docker compose up -d`?
17. ¿Qué diferencia existe entre `down` y `stop`?

## Seguridad

18. ¿Por qué no conviene ejecutar aplicaciones como root?
19. ¿Por qué evitar `latest` en producción?
20. ¿Por qué los secretos no deben almacenarse en el Dockerfile?

---

# CHEAT SHEET

## Ejecutar

```bash
docker run IMAGE
```

## Segundo plano

```bash
docker run -d IMAGE
```

## Puertos

```bash
docker run -p 8080:80 IMAGE
```

## Nombre

```bash
docker run --name app IMAGE
```

## Listar

```bash
docker ps
```

## Logs

```bash
docker logs -f app
```

## Terminal

```bash
docker exec -it app sh
```

## Build

```bash
docker build -t app .
```

## Volume

```bash
docker volume create data
```

## Red

```bash
docker network create backend
```

## Compose

```bash
docker compose up -d
```

## Detener Compose

```bash
docker compose down
```

## Estadísticas

```bash
docker stats
```

## Inspeccionar

```bash
docker inspect app
```

---

# RUTA DE APRENDIZAJE POSTERIOR

Una vez terminado este curso recomiendo seguir la siguiente progresión:

```text
Docker
   │
   ▼
Docker Compose
   │
   ▼
Linux avanzado
   │
   ▼
Redes
   │
   ▼
CI/CD
   │
   ▼
Container Registry
   │
   ▼
Kubernetes
   │
   ▼
Helm
   │
   ▼
GitOps
   │
   ├── Argo CD
   │
   └── Flux
   │
   ▼
Observabilidad
   │
   ├── Prometheus
   ├── Grafana
   └── Loki
```

---

# Stack recomendado para practicar

Para un proyecto suficientemente realista:

```text
Frontend
React
    │
    ▼
Nginx

Backend
Go / Node.js

Database
PostgreSQL

Cache
Redis

Containers
Docker

Orchestration local
Docker Compose

Repository
Git + GitHub

CI/CD
GitHub Actions
```

Una arquitectura particularmente didáctica sería:

```text
React
  │
  ▼
Nginx
  │
  ▼
Go API
  │
  ├─────────▶ Redis
  │
  ▼
PostgreSQL
```

Con este entorno pueden estudiarse prácticamente todos los conceptos de Docker de nivel fundamentos e intermedio.

---

# CRONOGRAMA SUGERIDO DE 40 HORAS

| Sesión | Tema                           |        Horas |
| ------ | ------------------------------ | -----------: |
| 1      | Introducción a contenedores    |            2 |
| 2      | Docker Engine y CLI            |            2 |
| 3      | Administración de contenedores |            3 |
| 4      | Imágenes Docker                |            2 |
| 5      | Dockerfile                     |            4 |
| 6      | Volúmenes y persistencia       |            3 |
| 7      | Redes Docker                   |            3 |
| 8      | Docker Compose                 |            4 |
| 9      | Variables y configuración      |            2 |
| 10     | Optimización y multistage      |            3 |
| 11     | Logs y troubleshooting         |            2 |
| 12     | Seguridad                      |            3 |
| 13     | Registries                     |            2 |
| 14     | CI/CD                          |            2 |
| 15     | Arquitecturas multicontenedor  |            2 |
| 16     | Kubernetes introductorio       |            1 |
|        | **Total**                      | **40 horas** |

---

# RESULTADO ESPERADO

Al terminar el curso, el participante no solamente deberá conocer comandos de Docker.

Debe poder recibir un sistema como:

```text
React
Go
PostgreSQL
Redis
Nginx
```

y diseñar de manera autónoma:

```text
Dockerfiles
   +
Networks
   +
Volumes
   +
Environment Variables
   +
Healthchecks
   +
Docker Compose
   +
Container Registry
   +
CI/CD
```

hasta conseguir un entorno reproducible:

```bash
git clone repository

docker compose up -d
```

y posteriormente poder diagnosticar, mantener y evolucionar esa infraestructura.

Ese sería el nivel adecuado para considerar que una persona domina **Docker a nivel intermedio**.
