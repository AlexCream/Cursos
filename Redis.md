# Curso profesional de Redis

## Fundamentos, desarrollo de aplicaciones y administración intermedia

**Nivel:** Fundamentos – Intermedio
**Duración recomendada:** 48 horas
**Modalidad:** Teórico-práctica
**Distribución sugerida:** 12 módulos de 4 horas
**Metodología:** explicación conceptual, demostraciones, ejercicios guiados, laboratorios, resolución de problemas y proyecto integrador.

---

# 1. Descripción general

Redis es una plataforma de datos en memoria orientada a estructuras de datos que puede utilizarse para resolver problemas de caché, sesiones, contadores, rankings, procesamiento de eventos, mensajería, almacenamiento temporal, coordinación distribuida y otros escenarios de baja latencia.

El propósito del curso es que el participante no se limite a memorizar comandos, sino que aprenda:

* cómo funciona Redis;
* cómo modelar información;
* cuándo utilizar cada estructura de datos;
* cómo diseñar claves;
* cómo controlar expiraciones;
* cómo implementar estrategias de caché;
* cómo evitar problemas de concurrencia;
* cómo utilizar Redis desde aplicaciones;
* cómo trabajar con persistencia;
* cómo implementar mensajería con Pub/Sub y Streams;
* cómo proteger una instancia;
* cómo implementar replicación y alta disponibilidad;
* cómo escalar mediante Redis Cluster;
* cómo diagnosticar consumo de memoria y problemas de rendimiento;
* y, especialmente, cuándo **no** utilizar Redis.

El curso se concentra inicialmente en las estructuras fundamentales: Strings, Hashes, Lists, Sets y Sorted Sets. Posteriormente introduce Streams, operaciones geoespaciales y funcionalidades especializadas. Redis actualmente incorpora además estructuras y capacidades para JSON, series temporales, datos probabilísticos y vectores, que se estudian como extensión del curso. La documentación oficial presenta Redis actualmente como una plataforma que puede utilizarse, entre otros escenarios, como caché, base de datos, motor de streaming y broker de mensajes.

---

# 2. Perfil de ingreso

El participante debería contar con:

* conocimientos básicos de programación;
* comprensión elemental del funcionamiento cliente-servidor;
* conocimientos básicos de terminal;
* conocimientos básicos de bases de datos;
* experiencia básica con Docker deseable, pero no obligatoria.

No se requiere experiencia previa con Redis.

---

# 3. Perfil de egreso

Al finalizar el curso, el participante podrá:

1. Explicar la arquitectura y modelo de funcionamiento de Redis.
2. Instalar y ejecutar Redis en ambientes de desarrollo.
3. Trabajar correctamente con `redis-cli`.
4. Diseñar esquemas de claves mantenibles.
5. Seleccionar estructuras de datos de acuerdo con el problema.
6. Administrar TTL, expiraciones y eliminación de claves.
7. Implementar estrategias de caché.
8. Construir contadores, sesiones, rankings, colas y limitadores de solicitudes.
9. Integrar Redis con aplicaciones.
10. Utilizar transacciones, operaciones atómicas y pipelines.
11. Implementar comunicación mediante Pub/Sub.
12. Implementar procesamiento de eventos mediante Streams.
13. Configurar persistencia RDB y AOF.
14. Comprender políticas de memoria y eviction.
15. Administrar usuarios y permisos mediante ACL.
16. Comprender replicación, Sentinel y Redis Cluster.
17. Utilizar herramientas de diagnóstico.
18. Identificar problemas de rendimiento.
19. Aplicar buenas prácticas de operación.
20. Diseñar una solución completa basada en Redis.

---

# 4. Herramientas del curso

## Software principal

* Redis Open Source
* Docker
* Docker Compose
* `redis-cli`
* Redis Insight
* Git
* Visual Studio Code o editor equivalente

## Lenguaje para prácticas de aplicación

Los conceptos centrales son independientes del lenguaje.

Para los ejemplos completos del curso se recomienda:

**Python + redis-py**

Opcionalmente pueden replicarse los ejercicios con:

* JavaScript/Node.js;
* Java;
* C#;
* Go;
* PHP.

Redis dispone de múltiples bibliotecas cliente, por lo que aprender primero mediante `redis-cli` facilita comprender qué operaciones ejecuta realmente la aplicación.

---

# 5. Entorno de laboratorio

## Redis mediante Docker

```bash
docker run -d \
  --name redis-lab \
  -p 6379:6379 \
  -v redis-data:/data \
  redis:8
```

Comprobar el contenedor:

```bash
docker ps
```

Ingresar al cliente:

```bash
docker exec -it redis-lab redis-cli
```

Probar la conexión:

```redis
PING
```

Resultado:

```text
PONG
```

Docker es actualmente una de las alternativas oficiales para ejecutar Redis Open Source durante desarrollo y aprendizaje.

---

## Redis Insight

Redis Insight proporciona una interfaz gráfica para explorar claves, ejecutar comandos y analizar una instancia Redis.

Ejemplo mediante Docker:

```bash
docker run -d \
  --name redisinsight \
  -p 5540:5540 \
  -v redisinsight:/data \
  redis/redisinsight:latest
```

Abrir:

```text
http://localhost:5540
```

La instalación mediante Docker y el puerto `5540` están documentados actualmente por Redis.

---

# 6. Organización del curso

## NIVEL I — FUNDAMENTOS

* Módulo 1. Introducción a Redis y arquitectura
* Módulo 2. Claves, Strings, TTL y comandos esenciales
* Módulo 3. Hashes, Lists, Sets y Sorted Sets
* Módulo 4. Modelado de información con Redis
* Módulo 5. Redis como sistema de caché
* Módulo 6. Integración de Redis con aplicaciones

**Duración:** 24 horas.

## NIVEL II — INTERMEDIO

* Módulo 7. Persistencia, memoria y políticas de eviction
* Módulo 8. Pub/Sub y Redis Streams
* Módulo 9. Atomicidad, transacciones, concurrencia y pipelines
* Módulo 10. Seguridad y ACL
* Módulo 11. Replicación, Sentinel y Redis Cluster
* Módulo 12. Rendimiento, observabilidad y proyecto integrador

**Duración:** 24 horas.

---

# MÓDULO 1. INTRODUCCIÓN A REDIS Y ARQUITECTURA

**Duración:** 4 horas

## Objetivos

El participante comprenderá qué es Redis, cómo funciona y qué problemas pretende solucionar.

## 1.1 ¿Qué es Redis?

Redis puede entenderse como un servidor de estructuras de datos en memoria.

Su principal diferencia frente a una base de datos relacional tradicional es que las aplicaciones no trabajan fundamentalmente con tablas y relaciones, sino con estructuras como:

```text
String
Hash
List
Set
Sorted Set
Stream
```

y otras estructuras especializadas.

Redis almacena principalmente información en memoria, pero dispone de mecanismos de persistencia en disco.

## 1.2 Redis no es simplemente un caché

Una simplificación habitual es:

> Redis = caché.

Redis puede utilizarse como caché, pero sus capacidades permiten resolver muchos otros problemas.

Ejemplos:

* sesiones;
* carritos de compra;
* tokens temporales;
* contadores;
* rankings;
* rate limiting;
* presencia de usuarios;
* colas;
* procesamiento de eventos;
* coordinación distribuida;
* datos geoespaciales;
* búsqueda;
* información temporal.

## 1.3 Arquitectura básica

Modelo conceptual:

```text
Aplicación
    │
    │ TCP
    ▼
┌─────────────┐
│    Redis    │
│             │
│   memoria   │
└──────┬──────┘
       │
       ▼
   persistencia
       │
    RDB / AOF
```

Redis procesa comandos enviados por clientes.

Ejemplo:

```redis
SET usuario:1:nombre "Ana"
```

Posteriormente:

```redis
GET usuario:1:nombre
```

## 1.4 Redis frente a una base SQL

SQL:

```sql
SELECT nombre
FROM usuarios
WHERE id = 1;
```

Redis:

```redis
GET usuario:1:nombre
```

No implica que Redis sea "mejor" que SQL.

Son herramientas para problemas diferentes.

Una arquitectura real puede utilizar ambas:

```text
                 ┌─────────────┐
                 │ PostgreSQL  │
                 │ datos       │
                 │ permanentes │
                 └──────▲──────┘
                        │
                        │
Cliente ──► API ────────┤
                        │
                        ▼
                 ┌─────────────┐
                 │    Redis    │
                 │ caché       │
                 │ sesiones    │
                 │ eventos     │
                 └─────────────┘
```

## 1.5 ¿Cuándo utilizar Redis?

Adecuado cuando necesitamos:

* respuestas de baja latencia;
* datos accedidos frecuentemente;
* información temporal;
* contadores;
* estructuras de datos rápidas;
* expiración automática;
* procesamiento de eventos;
* estados de sesión;
* rankings.

## 1.6 ¿Cuándo NO utilizar Redis?

No debería utilizarse simplemente porque sea rápido.

Debe reconsiderarse cuando:

* el dataset excede considerablemente la memoria disponible;
* se necesita principalmente almacenamiento relacional complejo;
* las consultas dependen fuertemente de joins;
* Redis no aporta una ventaja arquitectónica;
* el sistema requiere características transaccionales que correspondan mejor a una base de datos relacional;
* el equipo no puede asumir la complejidad operacional adicional.

## Laboratorio 1

1. Instalar Redis.
2. Ejecutarlo mediante Docker.
3. Conectarse mediante `redis-cli`.
4. Ejecutar:

```redis
PING
SET curso "Redis"
GET curso
DEL curso
EXISTS curso
```

5. Conectarse mediante Redis Insight.
6. Crear y eliminar claves gráficamente.

### Entregable

Captura o evidencia del servidor ejecutándose y breve explicación de:

```text
Cliente → Redis → respuesta
```

---

# MÓDULO 2. CLAVES, STRINGS, TTL Y COMANDOS ESENCIALES

**Duración:** 4 horas

## Objetivo

Dominar las operaciones fundamentales y comprender el ciclo de vida de una clave.

---

## 2.1 Modelo clave-valor

Ejemplo:

```redis
SET nombre "Carlos"
GET nombre
```

Conceptualmente:

```text
nombre ─────────► Carlos
```

## 2.2 Convenciones para nombres

Evitar:

```text
user1
config2
x123
```

Preferir:

```text
usuario:1:nombre
usuario:1:sesion
producto:500:stock
curso:redis:alumno:15
```

Convención recomendada:

```text
entidad:id:propiedad
```

o:

```text
aplicacion:modulo:entidad:id
```

Ejemplo:

```text
tienda:producto:100
tienda:usuario:45
tienda:sesion:a72f92
```

---

## 2.3 Strings

Crear:

```redis
SET producto:1:nombre "Laptop"
```

Obtener:

```redis
GET producto:1:nombre
```

Crear únicamente si no existe:

```redis
SET recurso:123 "reservado" NX
```

Crear únicamente si existe:

```redis
SET configuracion:tema "oscuro" XX
```

Múltiples valores:

```redis
MSET nombre "Ana" edad "32" ciudad "La Paz"
```

```redis
MGET nombre edad ciudad
```

---

## 2.4 Contadores

Redis puede incrementar valores numéricos atómicamente:

```redis
SET visitas 0
INCR visitas
INCR visitas
GET visitas
```

También:

```redis
INCRBY visitas 10
DECR visitas
DECRBY visitas 5
```

Caso de uso:

```text
contador de visitas
intentos de login
productos vistos
descargas
likes
```

---

## 2.5 TTL

TTL significa *Time To Live*.

```redis
SET token:123 "abc"
EXPIRE token:123 60
```

Consultar:

```redis
TTL token:123
```

Después de 60 segundos Redis eliminará la clave.

También:

```redis
SET token:123 "abc" EX 60
```

Ejemplos típicos:

```text
sesiones
OTP
tokens
caché
reservaciones temporales
rate limiting
```

---

## 2.6 Inspección de claves

```redis
EXISTS usuario:1
TYPE usuario:1
TTL usuario:1
PTTL usuario:1
```

Eliminar:

```redis
DEL usuario:1
```

Eliminar asincrónicamente:

```redis
UNLINK usuario:1
```

---

## 2.7 SCAN frente a KEYS

Durante prácticas pequeñas:

```redis
KEYS *
```

Sin embargo, en instalaciones grandes no debe diseñarse una aplicación que dependa de recorrer todas las claves mediante `KEYS`.

Para exploración incremental:

```redis
SCAN 0
```

Con patrón:

```redis
SCAN 0 MATCH usuario:* COUNT 100
```

---

# Laboratorio 2 — Sistema de sesiones

Crear:

```redis
SET sesion:abc123 '{"usuario":25}' EX 1800
```

Consultar:

```redis
GET sesion:abc123
```

Consultar TTL:

```redis
TTL sesion:abc123
```

Renovar:

```redis
EXPIRE sesion:abc123 1800
```

Cerrar sesión:

```redis
DEL sesion:abc123
```

## Reto

Diseñar un sistema donde cada usuario pueda realizar solamente cinco intentos de autenticación durante 60 segundos.

Pistas:

```redis
INCR
EXPIRE
TTL
```

---

# MÓDULO 3. ESTRUCTURAS DE DATOS

**Duración:** 4 horas

Este módulo constituye uno de los elementos fundamentales del curso.

La selección de la estructura adecuada suele ser más importante que memorizar comandos.

---

# 3.1 Hashes

Representan conjuntos de campos y valores.

Ejemplo:

```redis
HSET usuario:100 \
 nombre "Ana" \
 edad 29 \
 ciudad "La Paz"
```

Consultar:

```redis
HGET usuario:100 nombre
```

Todos los campos:

```redis
HGETALL usuario:100
```

Incrementar:

```redis
HINCRBY usuario:100 puntos 10
```

Caso típico:

```text
usuario:100
 ├── nombre = Ana
 ├── edad = 29
 ├── ciudad = La Paz
 └── puntos = 350
```

Adecuados para:

* objetos;
* perfiles;
* configuraciones;
* información estructurada sencilla.

---

# 3.2 Lists

Lista ordenada de elementos.

Agregar:

```redis
LPUSH tareas "tarea1"
LPUSH tareas "tarea2"
```

Consultar:

```redis
LRANGE tareas 0 -1
```

Extraer:

```redis
LPOP tareas
```

También:

```redis
RPUSH
RPOP
```

Permiten construir patrones FIFO y LIFO.

Ejemplo FIFO:

```redis
RPUSH cola trabajo1
RPUSH cola trabajo2

LPOP cola
```

---

# 3.3 Sets

Colecciones sin elementos duplicados.

```redis
SADD curso:redis:alumnos 1 2 3 4
```

Consultar:

```redis
SMEMBERS curso:redis:alumnos
```

Comprobar:

```redis
SISMEMBER curso:redis:alumnos 3
```

Intersección:

```redis
SINTER curso:redis:alumnos curso:docker:alumnos
```

Unión:

```redis
SUNION curso:redis:alumnos curso:docker:alumnos
```

Ejemplo:

```text
Usuarios que cursan Redis
∩
Usuarios que cursan Docker
=
Usuarios que cursan ambos
```

---

# 3.4 Sorted Sets

Los Sorted Sets almacenan miembros únicos acompañados de una puntuación.

```redis
ZADD ranking 1500 usuario1
ZADD ranking 2200 usuario2
ZADD ranking 1700 usuario3
```

Consultar:

```redis
ZRANGE ranking 0 -1 WITHSCORES
```

Ranking inverso:

```redis
ZRANGE ranking 0 -1 REV WITHSCORES
```

Incrementar:

```redis
ZINCRBY ranking 200 usuario1
```

Casos de uso:

* rankings;
* puntuaciones;
* prioridades;
* colas ordenadas;
* tiempos;
* productos populares.

---

# 3.5 Operaciones geoespaciales

Ejemplo:

```redis
GEOADD sucursales \
 -110.3108 24.1426 "La Paz"
```

Puede utilizarse para representar ubicaciones y realizar búsquedas por distancia.

Casos:

* sucursales cercanas;
* restaurantes;
* conductores;
* puntos turísticos;
* servicios geolocalizados.

---

# Laboratorio 3 — Plataforma educativa

Modelar:

```text
usuarios
cursos
inscripciones
calificaciones
ranking
```

Requisitos:

1. Cada estudiante debe almacenarse en un Hash.
2. Las inscripciones se almacenarán en Sets.
3. El ranking utilizará Sorted Sets.
4. Los eventos recientes utilizarán Lists.

Ejemplo:

```redis
HSET estudiante:1 nombre "Laura" carrera "IGE"

SADD curso:redis:estudiantes 1

ZADD curso:redis:ranking 95 estudiante:1
```

---

# MÓDULO 4. MODELADO DE INFORMACIÓN

**Duración:** 4 horas

## Objetivo

Transformar requisitos de negocio en estructuras Redis eficientes.

---

# 4.1 Pensar en patrones de acceso

En Redis primero debemos preguntarnos:

> ¿Cómo se accederá a la información?

No únicamente:

> ¿Cómo está relacionada la información?

Ejemplo:

Necesidad:

```text
Obtener rápidamente los productos más vendidos.
```

Una solución:

```text
Sorted Set
```

```redis
ZINCRBY productos:ventas 1 producto:100
```

---

# 4.2 Patrón de claves

Ejemplo de una tienda:

```text
app:usuario:100
app:producto:500
app:categoria:laptops
app:carrito:100
app:sesion:abc
app:ranking:productos
```

---

# 4.3 Casos de modelado

## Sesiones

```text
sesion:<token>
```

TTL obligatorio.

## Carrito

```text
carrito:<usuario>
```

Hash:

```redis
HSET carrito:10 producto:15 2
```

## Favoritos

```text
usuario:10:favoritos
```

Set.

## Ranking

```text
ranking:ventas
```

Sorted Set.

## Usuarios activos

```text
usuarios:activos
```

Set o estructuras especializadas dependiendo del problema.

---

# 4.4 Anti-patrones

Evitar:

```text
KEYS *
```

como parte habitual de una aplicación.

Evitar nombres ambiguos:

```text
x
data
temp
lista
```

Evitar valores gigantescos sin análisis.

Evitar mantener datos sin TTL cuando deberían ser temporales.

Evitar utilizar Redis como reemplazo automático de la base de datos principal.

---

# Laboratorio 4 — Modelado

Diseñar en Redis una plataforma de reservaciones.

Debe contener:

```text
usuarios
servicios
reservaciones
disponibilidad
sesiones
servicios populares
```

El alumno debe entregar:

1. esquema de claves;
2. estructura Redis seleccionada;
3. justificación;
4. TTL correspondiente;
5. comandos de ejemplo.

---

# MÓDULO 5. REDIS COMO CACHÉ

**Duración:** 4 horas

## Objetivo

Comprender los principales patrones de caché y sus implicaciones.

---

# 5.1 ¿Qué es una caché?

Supongamos:

```text
Cliente
  │
  ▼
API
  │
  ▼
PostgreSQL
```

Cada consulta llega a la base de datos.

Agregamos Redis:

```text
Cliente
   │
   ▼
 API
   │
   ├────► Redis
   │       │
   │       └── HIT
   │
   └────► PostgreSQL
           │
           └── MISS
```

---

# 5.2 Cache Aside

Patrón fundamental.

Pseudocódigo:

```python
producto = redis.get("producto:100")

if producto:
    return producto

producto = database.buscar_producto(100)

redis.set(
    "producto:100",
    serializar(producto),
    ex=300
)

return producto
```

Flujo:

```text
buscar Redis
    │
    ├── existe ──► responder
    │
    └── no existe
            │
            ▼
        consultar DB
            │
            ▼
        guardar Redis
            │
            ▼
         responder
```

---

# 5.3 Cache Hit

La información existe.

```text
Redis → HIT
```

# 5.4 Cache Miss

La información no está almacenada.

```text
Redis → MISS → DB
```

---

# 5.5 Invalidación

Problema clásico:

```text
DB cambia
↓
Redis conserva versión anterior
↓
usuario recibe información obsoleta
```

Soluciones:

* TTL;
* invalidación explícita;
* actualización del caché;
* estrategias basadas en eventos.

---

# 5.6 Cache Aside

La aplicación administra el caché.

# 5.7 Write Through

La escritura actualiza caché y almacenamiento.

# 5.8 Write Behind

La escritura puede diferirse hacia el almacenamiento persistente.

Debe utilizarse cuidadosamente por las implicaciones de consistencia y durabilidad.

---

# 5.9 Cache Stampede

Supongamos que una clave muy popular expira.

```text
1000 solicitudes
       │
       ▼
Redis MISS
       │
       ▼
1000 consultas DB
```

Esto puede generar una sobrecarga.

Técnicas:

* locking;
* TTL con variación aleatoria;
* precarga;
* stale-while-revalidate;
* single-flight.

---

# 5.10 Cache Penetration

Consultas repetidas sobre información inexistente.

Ejemplo:

```text
producto:999999999
```

Puede mitigarse mediante:

* negative caching;
* validación;
* estructuras probabilísticas según el escenario.

---

# Laboratorio 5 — Caché de catálogo

Implementar:

```text
GET /productos/{id}
```

Comportamiento:

```text
1. consultar Redis
2. si existe → HIT
3. si no existe → DB
4. almacenar durante 5 minutos
5. responder
```

Registrar:

```text
CACHE HIT
CACHE MISS
```

Calcular posteriormente:

```text
hit ratio =
hits / (hits + misses)
```

---

# MÓDULO 6. INTEGRACIÓN CON APLICACIONES

**Duración:** 4 horas

Para las prácticas se utilizará Python.

---

# 6.1 Cliente

Instalación:

```bash
pip install redis
```

Conexión:

```python
import redis

r = redis.Redis(
    host="localhost",
    port=6379,
    decode_responses=True
)

print(r.ping())
```

---

# 6.2 Strings

```python
r.set("usuario:1:nombre", "Ana")

nombre = r.get("usuario:1:nombre")

print(nombre)
```

---

# 6.3 TTL

```python
r.set(
    "sesion:abc",
    "usuario:1",
    ex=1800
)
```

---

# 6.4 Hashes

```python
r.hset(
    "usuario:1",
    mapping={
        "nombre": "Ana",
        "ciudad": "La Paz",
        "edad": 29
    }
)
```

Obtener:

```python
usuario = r.hgetall("usuario:1")
```

---

# 6.5 Sorted Sets

```python
r.zadd(
    "ranking",
    {
        "usuario:1": 100,
        "usuario:2": 250
    }
)
```

---

# 6.6 Serialización

Con JSON:

```python
import json

producto = {
    "id": 1,
    "nombre": "Laptop",
    "precio": 15000
}

r.set(
    "producto:1",
    json.dumps(producto),
    ex=300
)
```

Lectura:

```python
producto = json.loads(
    r.get("producto:1")
)
```

---

# 6.7 Pool de conexiones

Las aplicaciones reales deben reutilizar conexiones.

Conceptualmente:

```text
Aplicación
   │
   ▼
Connection Pool
 ├── conexión 1
 ├── conexión 2
 ├── conexión 3
 └── conexión N
       │
       ▼
     Redis
```

Crear conexiones continuamente añade trabajo innecesario.

---

# Laboratorio 6 — API

Crear una API sencilla con:

```text
GET /productos/{id}
POST /login
GET /ranking
```

Redis tendrá tres responsabilidades diferentes:

```text
productos → caché
sesiones  → TTL
ranking   → Sorted Set
```

El alumno deberá explicar por qué cada caso utiliza una estructura diferente.

---

# EVALUACIÓN PARCIAL — FUNDAMENTOS

## Examen práctico

Diseñar Redis para una plataforma de cursos.

Requisitos:

* estudiantes;
* sesiones;
* cursos;
* favoritos;
* contador de visitas;
* ranking;
* caché de cursos.

El estudiante deberá justificar cada estructura utilizada.

---

# NIVEL II — REDIS INTERMEDIO

# MÓDULO 7. PERSISTENCIA, MEMORIA Y EVICTION

**Duración:** 4 horas

Redis trabaja primordialmente en memoria, pero permite persistencia.

Actualmente la documentación oficial contempla:

* RDB;
* AOF;
* ausencia de persistencia;
* combinación RDB + AOF.

---

# 7.1 RDB

Genera snapshots del estado.

Conceptualmente:

```text
Memoria
   │
   │ snapshot
   ▼
dump.rdb
```

Ventajas:

* archivos compactos;
* buenas restauraciones;
* útil para respaldos.

Consideración:

Puede perderse información posterior al último snapshot dependiendo de la configuración.

---

# 7.2 AOF

Append Only File registra operaciones de escritura.

```text
SET usuario 1
INCR contador
HSET ...
```

Conceptualmente:

```text
operación
   │
   ▼
AOF
```

Durante recuperación, las operaciones pueden utilizarse para reconstruir el estado.

---

# 7.3 Estrategias

## Caché puro

Puede resultar aceptable:

```text
sin persistencia
```

si todos los datos pueden reconstruirse.

## Datos importantes

Evaluar:

```text
RDB
AOF
RDB + AOF
```

según:

* RPO;
* RTO;
* rendimiento;
* durabilidad requerida.

---

# 7.4 Memoria

Comandos:

```redis
INFO memory
```

```redis
MEMORY USAGE usuario:100
```

```redis
MEMORY STATS
```

---

# 7.5 maxmemory

Redis puede establecer un límite de memoria.

Conceptualmente:

```text
maxmemory = 2 GB
```

Cuando se alcanza el límite, la política configurada determina qué hacer.

---

# 7.6 Políticas de eviction

Conceptos a estudiar:

```text
noeviction
allkeys-lru
allkeys-lfu
allkeys-random
volatile-lru
volatile-lfu
volatile-random
volatile-ttl
```

El estudiante deberá comprender la diferencia entre:

```text
allkeys
```

y:

```text
volatile
```

---

# 7.7 LRU

Least Recently Used.

Prioriza eliminación de datos poco utilizados recientemente.

# 7.8 LFU

Least Frequently Used.

Prioriza elementos utilizados con menor frecuencia.

---

# Laboratorio 7

Configurar una instancia con:

```text
maxmemory
```

y una política de eviction.

Generar múltiples claves.

Observar:

```redis
INFO memory
```

y analizar qué sucede al alcanzar el límite.

Redis recomienda establecer límites de memoria en escenarios donde el crecimiento sin control podría consumir los recursos disponibles del sistema.

---

# MÓDULO 8. PUB/SUB Y REDIS STREAMS

**Duración:** 4 horas

---

# 8.1 Pub/Sub

Modelo:

```text
Publisher
    │
    ▼
  canal
 ┌──┴──┐
 ▼     ▼
S1     S2
```

Suscriptor:

```redis
SUBSCRIBE noticias
```

Publicador:

```redis
PUBLISH noticias "Nueva noticia"
```

---

# 8.2 Característica fundamental

Pub/Sub es apropiado para comunicación en tiempo real cuando un mensaje que no sea recibido no necesariamente necesita recuperarse.

Redis Pub/Sub utiliza semántica **at-most-once**: si el suscriptor pierde el mensaje, Redis no lo conserva para entregarlo posteriormente.

Por esta razón:

```text
Pub/Sub ≠ cola durable
```

---

# 8.3 Streams

Streams mantienen un registro de eventos.

Agregar:

```redis
XADD pedidos * \
 usuario 10 \
 producto 500 \
 cantidad 2
```

Leer:

```redis
XRANGE pedidos - +
```

---

# 8.4 Modelo

```text
Producer
    │
    ▼
┌───────────────────┐
│      STREAM       │
│                   │
│ evento 1          │
│ evento 2          │
│ evento 3          │
└────────┬──────────┘
         │
         ▼
    Consumer Group
      ├── Worker 1
      ├── Worker 2
      └── Worker 3
```

Streams funcionan como un log append-only y soportan grupos de consumidores.

---

# 8.5 Consumer Groups

Crear:

```redis
XGROUP CREATE pedidos procesadores 0 MKSTREAM
```

Leer:

```redis
XREADGROUP \
 GROUP procesadores worker1 \
 COUNT 1 \
 STREAMS pedidos >
```

Confirmar:

```redis
XACK pedidos procesadores <id>
```

Consultar pendientes:

```redis
XPENDING pedidos procesadores
```

---

# 8.6 Pub/Sub vs Streams

| Característica            | Pub/Sub  | Streams |
| ------------------------- | -------- | ------- |
| Tiempo real               | Sí       | Sí      |
| Persistencia de mensajes  | No       | Sí      |
| Historial                 | No       | Sí      |
| Consumer Groups           | No       | Sí      |
| ACK                       | No       | Sí      |
| Procesamiento distribuido | Limitado | Sí      |
| Complejidad               | Baja     | Media   |

---

# Laboratorio 8 — Procesamiento de pedidos

Producer:

```text
API
```

genera:

```text
pedido_creado
```

El evento se almacena en:

```text
Stream: pedidos
```

Tres consumidores:

```text
inventario
notificaciones
analítica
```

Los estudiantes deberán simular:

1. producción;
2. consumo;
3. ACK;
4. mensaje pendiente;
5. recuperación del procesamiento.

---

# MÓDULO 9. ATOMICIDAD, CONCURRENCIA, TRANSACCIONES Y PIPELINES

**Duración:** 4 horas

---

# 9.1 Atomicidad

Muchas operaciones Redis individuales son atómicas.

Ejemplo:

```redis
INCR stock
```

es preferible a:

```text
GET
modificar localmente
SET
```

cuando necesitamos simplemente incrementar.

---

# 9.2 Condiciones de carrera

Problema:

```text
Cliente A → GET stock = 10
Cliente B → GET stock = 10

A resta 1
B resta 1

A SET 9
B SET 9
```

Resultado:

```text
9
```

pero deberían quedar:

```text
8
```

---

# 9.3 MULTI / EXEC

```redis
MULTI

INCR contador
HSET usuario:1 estado activo

EXEC
```

Los comandos se encolan hasta `EXEC`.

Redis documenta sus transacciones alrededor de:

```text
MULTI
EXEC
DISCARD
WATCH
```

y garantiza que los comandos de una transacción se ejecutan secuencialmente sin que otro cliente inserte operaciones entre ellos.

---

# 9.4 WATCH

Optimistic locking.

```redis
WATCH producto:100:stock
```

Leer valor.

Después:

```redis
MULTI
SET producto:100:stock 9
EXEC
```

Si otra operación modifica la clave observada antes del `EXEC`, la transacción puede abortarse.

---

# 9.5 Pipelines

Sin pipeline:

```text
cliente → comando → Redis
cliente ← resultado ← Redis

cliente → comando → Redis
cliente ← resultado ← Redis
```

Con pipeline:

```text
cliente ───── comando 1 ───►
        ├──── comando 2 ───► Redis
        └──── comando 3 ───►

cliente ◄──── respuestas ───
```

El objetivo principal es reducir round trips de red.

La documentación de optimización de Redis recomienda reducir viajes de red mediante pipelining o comandos que operen sobre múltiples valores cuando sea apropiado.

---

# 9.6 Lua / scripting

Los scripts permiten ejecutar lógica en el servidor de manera atómica.

Ejemplo conceptual:

```lua
local stock = tonumber(redis.call("GET", KEYS[1]))

if stock <= 0 then
    return 0
end

redis.call("DECR", KEYS[1])

return 1
```

El concepto es especialmente útil cuando una operación depende de varias instrucciones Redis.

---

# 9.7 Idempotencia

Una operación idempotente puede repetirse sin generar un efecto adicional inesperado.

Ejemplo:

```text
procesar pedido 100
```

Puede controlarse mediante:

```redis
SET pedido:100:procesado 1 NX
```

Si devuelve que la clave no pudo crearse:

```text
el pedido ya fue procesado
```

Este patrón es importante en procesamiento de eventos.

---

# Laboratorio 9 — Inventario concurrente

Problema:

```text
stock = 1

cliente A compra
cliente B compra
```

Solo uno debe tener éxito.

Resolver utilizando:

1. estrategia ingenua;
2. `WATCH`;
3. operación atómica;
4. script.

Comparar ventajas y complejidad.

---

# MÓDULO 10. SEGURIDAD Y ACL

**Duración:** 4 horas

Redis nunca debe considerarse seguro únicamente porque "está dentro de la red".

---

# 10.1 Principios

Aplicar:

```text
mínimo privilegio
autenticación
aislamiento de red
TLS cuando corresponda
usuarios específicos
restricción de comandos
restricción de claves
```

---

# 10.2 ACL

Redis permite definir usuarios y permisos.

Consultar:

```redis
ACL LIST
```

Usuarios:

```redis
ACL USERS
```

Crear un usuario:

```redis
ACL SETUSER appuser on >ClaveSegura
```

Después se restringen comandos y claves de acuerdo con las necesidades de la aplicación.

---

# 10.3 Principio de mínimo privilegio

Una aplicación que únicamente necesita:

```text
GET
SET
DEL
EXPIRE
```

no debería recibir permisos administrativos.

Separar:

```text
administrador
aplicación
monitorización
replicación
sentinel
```

---

# 10.4 No exponer Redis directamente a Internet

Arquitectura esperada:

```text
Internet
   │
   ▼
API
   │
   ▼
Red privada
   │
   ▼
Redis
```

No:

```text
Internet
   │
   ▼
Redis :6379
```

---

# 10.5 Secretos

No almacenar contraseñas Redis directamente en:

```text
repositorios Git
Dockerfile
código fuente
```

Preferir:

```text
variables de entorno
secret managers
Docker Secrets
Kubernetes Secrets
servicios especializados de secretos
```

---

# Laboratorio 10

Crear:

```text
admin
app-read
app-write
```

Probar que:

```text
app-read
```

pueda consultar determinada información pero no modificarla.

Intentar un comando prohibido y analizar la respuesta.

---

# MÓDULO 11. REPLICACIÓN, SENTINEL Y REDIS CLUSTER

**Duración:** 4 horas

---

# 11.1 Replicación

Modelo:

```text
         ┌───────────┐
         │  Primary  │
         └─────┬─────┘
               │
       ┌───────┴────────┐
       ▼                ▼
   Replica 1        Replica 2
```

Redis utiliza replicación primary-replica.

La replicación base es principalmente asíncrona.

---

# 11.2 ¿Para qué replicar?

* disponibilidad;
* redundancia;
* distribución de determinadas lecturas;
* recuperación ante fallos;
* arquitecturas de alta disponibilidad.

---

# 11.3 Redis Sentinel

Sentinel incorpora supervisión y mecanismos de failover para despliegues Redis no clusterizados.

Conceptualmente:

```text
       Sentinel
      /    |    \
     /     |     \
Primary Replica Replica
```

Ante una caída del primary, Sentinel puede participar en la elección y promoción de una réplica.

La documentación oficial define Sentinel como la solución de alta disponibilidad para despliegues Redis no clusterizados.

---

# 11.4 Redis Cluster

La replicación no resuelve por sí misma el problema:

```text
dataset demasiado grande
```

Para distribución horizontal:

```text
Redis Cluster
```

Redis Cluster divide las claves entre múltiples nodos.

```text
                   Cluster
              ┌──────┼──────┐
              ▼      ▼      ▼
            Node1  Node2  Node3
```

Redis Cluster proporciona sharding automático entre nodos y cierto grado de disponibilidad ante fallos.

---

# 11.5 Hash slots

Redis Cluster organiza el espacio de claves mediante slots.

Conceptualmente:

```text
KEY
 │
 ▼
hash
 │
 ▼
slot
 │
 ▼
node
```

Esto permite determinar qué nodo administra cada clave.

---

# 11.6 Replication vs Sentinel vs Cluster

| Tecnología  | Objetivo principal                                   |
| ----------- | ---------------------------------------------------- |
| Replication | Copias de datos                                      |
| Sentinel    | Alta disponibilidad/failover                         |
| Cluster     | Sharding + escalabilidad horizontal + disponibilidad |

No son sinónimos.

---

# Laboratorio 11

Crear mediante Docker varias instancias Redis.

Primera práctica:

```text
Primary
   │
   └── Replica
```

Comprobar:

```redis
INFO replication
```

Segunda práctica:

dibujar una arquitectura Sentinel.

Tercera práctica:

analizar el diseño:

```text
3 primaries
3 replicas
```

para Redis Cluster.

---

# MÓDULO 12. RENDIMIENTO, OBSERVABILIDAD Y OPERACIÓN

**Duración:** 4 horas

---

# 12.1 INFO

Primer comando de diagnóstico:

```redis
INFO
```

Secciones importantes:

```text
server
clients
memory
persistence
stats
replication
cpu
keyspace
```

Ejemplo:

```redis
INFO memory
```

---

# 12.2 SLOWLOG

Consultar comandos lentos:

```redis
SLOWLOG GET
```

También:

```redis
SLOWLOG LEN
```

---

# 12.3 Latencia

Redis dispone de herramientas específicas para analizar latencia.

Ejemplos:

```redis
LATENCY LATEST
LATENCY HISTORY
LATENCY DOCTOR
```

El monitor debe configurarse previamente según el escenario.

La documentación oficial recomienda comprobar operaciones lentas y utilizar Slow Log al diagnosticar problemas de latencia.

---

# 12.4 Benchmark

Herramienta:

```bash
redis-benchmark
```

Ejemplo:

```bash
redis-benchmark -t set,get -n 100000
```

No debe confundirse un benchmark sintético con el rendimiento real de una aplicación.

Se deben evaluar:

```text
latencia
throughput
concurrencia
tamaño de valores
red
CPU
memoria
persistencia
comando ejecutado
```

---

# 12.5 Complejidad de comandos

No todos los comandos tienen el mismo costo.

El alumno debe acostumbrarse a revisar:

```text
O(1)
O(log N)
O(N)
```

Una operación O(N) sobre diez elementos puede ser trivial.

La misma operación sobre millones puede convertirse en un problema.

---

# 12.6 Big Keys

Una clave puede contener una estructura excesivamente grande.

Ejemplo:

```text
Hash → millones de campos
```

aunque Redis tenga pocas claves.

Esto puede generar:

* consumo elevado;
* operaciones costosas;
* problemas al eliminar;
* latencia;
* replicación más pesada.

---

# 12.7 Hot Keys

Una sola clave recibe una gran proporción del tráfico.

Ejemplo:

```text
producto:oferta-del-dia
```

Aunque exista un cluster, una única clave pertenece a un nodo determinado.

Por ello puede aparecer un hotspot.

---

# 12.8 Métricas importantes

Supervisar:

```text
used_memory
used_memory_rss
connected_clients
blocked_clients
keyspace_hits
keyspace_misses
evicted_keys
expired_keys
instantaneous_ops_per_sec
rejected_connections
replication lag
latencia
CPU
```

---

# 12.9 Cache Hit Ratio

```text
hit ratio =
keyspace_hits /
(keyspace_hits + keyspace_misses)
```

Interpretarlo en función de la aplicación.

Un valor alto no implica necesariamente que la estrategia de caché sea correcta.

---

# Laboratorio 12 — Diagnóstico

Se proporciona una instancia deliberadamente problemática.

El estudiante deberá investigar:

```text
memoria
evictions
latencia
comandos lentos
TTL
big keys
hit ratio
```

y elaborar:

```text
problema
evidencia
causa probable
acción correctiva
```

---

# 13. CONTENIDOS COMPLEMENTARIOS

Después del nivel intermedio pueden incorporarse unidades especializadas.

## Redis JSON

Permite trabajar con documentos JSON estructurados.

Casos:

```text
catálogos
perfiles
documentos
APIs
```

## Time Series

Orientado a datos asociados con tiempo.

Ejemplos:

```text
temperatura
telemetría
IoT
métricas
sensores
```

## Estructuras probabilísticas

Aplicables a problemas como:

```text
cardinalidad aproximada
detección aproximada de pertenencia
frecuencias
```

cuando la exactitud absoluta puede intercambiarse por eficiencia.

## Vector Search / Vector Sets

Permiten trabajar con representaciones vectoriales.

Aplicaciones:

```text
búsqueda semántica
recomendadores
RAG
sistemas de IA
similitud
```

Redis actualmente documenta soporte para estructuras especializadas de vectores y consultas de similitud, además de otras estructuras avanzadas.

---

# 14. TECNOLOGÍAS RELACIONADAS

Un profesional que utiliza Redis también debe comprender dónde se ubica respecto de otras tecnologías.

## Redis vs PostgreSQL/MySQL

Redis:

```text
acceso rápido
estado temporal
caché
estructuras de datos
eventos
```

SQL:

```text
relaciones
integridad
consultas complejas
persistencia primaria
analítica transaccional
```

Frecuentemente:

```text
Redis + PostgreSQL
```

es más apropiado que:

```text
Redis vs PostgreSQL
```

---

# Redis vs Memcached

Ambos pueden utilizarse para caché.

Redis ofrece un conjunto mucho más amplio de estructuras y funcionalidades.

Memcached mantiene un modelo deliberadamente más sencillo.

La selección debe depender del problema y de la complejidad operacional aceptable.

---

# Redis Streams vs Kafka

No deben considerarse equivalentes absolutos.

Streams puede resolver numerosas necesidades de procesamiento de eventos dentro de una arquitectura que ya utiliza Redis.

Kafka está específicamente diseñado alrededor de una plataforma distribuida de event streaming a gran escala.

La elección depende de:

```text
volumen
retención
ecosistema
arquitectura
escalabilidad
operación
garantías requeridas
```

---

# Redis Pub/Sub vs RabbitMQ

Pub/Sub:

```text
simple
baja latencia
mensajes efímeros
```

RabbitMQ:

```text
broker especializado
colas
routing
acknowledgements
durabilidad configurable
```

Si perder mensajes no es aceptable, Redis Pub/Sub generalmente no será el mecanismo apropiado.

---

# 15. PATRONES QUE EL ALUMNO DEBE DOMINAR

Al finalizar el curso deberá poder implementar:

## 1. Caché

```text
cache-aside
```

## 2. Sesiones

```text
SET + TTL
```

## 3. Contadores

```text
INCR
```

## 4. Rate limiting

```text
INCR + EXPIRE
```

## 5. Rankings

```text
Sorted Set
```

## 6. Favoritos

```text
Set
```

## 7. Colas sencillas

```text
List
```

## 8. Eventos

```text
Stream
```

## 9. Comunicación efímera

```text
Pub/Sub
```

## 10. Objetos

```text
Hash
```

## 11. Bloqueo/operación condicional

```text
SET NX
```

## 12. Procesamiento idempotente

```text
SET ... NX
```

combinado con una estrategia adecuada de negocio.

---

# 16. PROYECTO INTEGRADOR

## Plataforma de comercio electrónico en tiempo real

El estudiante desarrollará una pequeña aplicación que combine Redis con una base de datos persistente.

Arquitectura:

```text
                    ┌─────────────┐
                    │   Cliente   │
                    └──────┬──────┘
                           │
                           ▼
                    ┌─────────────┐
                    │     API     │
                    └───┬─────┬───┘
                        │     │
              ┌─────────┘     └─────────┐
              ▼                         ▼
       ┌─────────────┐           ┌─────────────┐
       │    Redis    │           │ PostgreSQL  │
       └─────────────┘           └─────────────┘
              │
              ▼
       ┌─────────────┐
       │   Streams   │
       └──────┬──────┘
              │
       ┌──────┼─────────┐
       ▼      ▼         ▼
    Email  Inventario Analítica
```

---

# 16.1 Requisito 1 — Sesiones

```text
sesion:<token>
```

TTL:

```text
30 minutos
```

---

# 16.2 Requisito 2 — Caché de productos

```text
producto:<id>
```

Implementar Cache Aside.

Registrar:

```text
HIT
MISS
```

---

# 16.3 Requisito 3 — Productos populares

Sorted Set:

```text
ranking:productos
```

Cada visita:

```redis
ZINCRBY ranking:productos 1 producto:100
```

---

# 16.4 Requisito 4 — Rate limiting

Máximo:

```text
100 solicitudes/minuto/usuario
```

Redis deberá controlar las solicitudes.

---

# 16.5 Requisito 5 — Carrito

Utilizar:

```text
Hash
```

Ejemplo:

```redis
HSET carrito:100 producto:1 2
```

---

# 16.6 Requisito 6 — Eventos

Al confirmar compra:

```redis
XADD pedidos * \
 pedido 500 \
 usuario 100 \
 total 2500
```

---

# 16.7 Requisito 7 — Worker

Crear un consumidor que procese:

```text
pedido creado
```

y confirme posteriormente:

```redis
XACK
```

---

# 16.8 Requisito 8 — Seguridad

Crear un usuario de aplicación con ACL.

No utilizar el usuario administrativo para la API.

---

# 16.9 Requisito 9 — Persistencia

Configurar y justificar:

```text
RDB
AOF
RDB + AOF
o sin persistencia
```

para cada escenario relevante.

---

# 16.10 Requisito 10 — Observabilidad

Registrar:

```text
cache hits
cache misses
memoria
operaciones
latencia
errores
eventos pendientes
```

---

# 17. ENTREGABLES DEL PROYECTO

El proyecto deberá contener:

1. repositorio Git;
2. `README.md`;
3. `docker-compose.yml`;
4. código de la aplicación;
5. diagrama de arquitectura;
6. esquema de claves Redis;
7. estrategia de TTL;
8. estrategia de caché;
9. estrategia de persistencia;
10. configuración básica de ACL;
11. demostración de Streams;
12. evidencias de pruebas;
13. resultados de benchmark;
14. breve informe técnico.

---

# 18. EVALUACIÓN DEL CURSO

Propuesta:

| Evidencia                      | Porcentaje |
| ------------------------------ | ---------: |
| Ejercicios y cuestionarios     |       10 % |
| Laboratorios                   |       35 % |
| Examen práctico de fundamentos |       15 % |
| Proyecto integrador            |       30 % |
| Examen práctico final          |       10 % |
| **Total**                      |  **100 %** |

---

# 19. RÚBRICA DEL PROYECTO

| Criterio                        | Ponderación |
| ------------------------------- | ----------: |
| Diseño de claves                |        10 % |
| Selección de estructuras        |        15 % |
| Estrategia de caché             |        10 % |
| TTL y gestión del ciclo de vida |        10 % |
| Atomicidad/concurrencia         |        10 % |
| Streams/eventos                 |        10 % |
| Seguridad                       |        10 % |
| Persistencia                    |         5 % |
| Rendimiento y observabilidad    |        10 % |
| Documentación y arquitectura    |        10 % |

---

# 20. EXAMEN PRÁCTICO FINAL

## Escenario

Una aplicación vende 10,000 boletos para un evento.

Durante los primeros minutos pueden conectarse miles de usuarios simultáneamente.

El sistema necesita:

```text
sesiones
stock disponible
contador de visitas
ranking de eventos
limitación de solicitudes
confirmación de compras
eventos de compra
caché
```

## Preguntas

### Problema 1

¿Qué estructura utilizaría para sesiones?

Explique:

```text
estructura
clave
TTL
```

### Problema 2

¿Cómo evitaría vender dos veces el último boleto?

### Problema 3

¿Cómo implementaría:

```text
máximo 20 solicitudes/minuto?
```

### Problema 4

¿Qué utilizaría para un ranking de eventos?

### Problema 5

¿Pub/Sub o Streams para registrar compras?

Justifique.

### Problema 6

¿Qué ocurriría si Redis se reinicia?

Relacionar la respuesta con:

```text
RDB
AOF
```

### Problema 7

¿Cómo escalaría Redis si el dataset ya no cabe cómodamente en un solo nodo?

### Problema 8

¿Cómo detectaría problemas de memoria y comandos lentos?

---

# 21. RESPUESTAS ESPERADAS DEL EXAMEN

No existe necesariamente una única arquitectura correcta, pero se esperan razonamientos similares a:

```text
sesión          → String/Hash + TTL
contador        → INCR
ranking         → Sorted Set
favoritos       → Set
caché           → String/Hash + TTL
eventos         → Streams
mensajes efímeros → Pub/Sub
```

El stock requiere una operación que impida condiciones de carrera mediante operaciones atómicas, control optimista o scripting.

La evaluación debe valorar principalmente:

> la justificación técnica de la decisión.

---

# 22. PREGUNTAS DE REPASO

## Fundamentos

1. ¿Qué diferencia existe entre Redis y una base de datos relacional?
2. ¿Por qué Redis es considerado un servidor de estructuras de datos?
3. ¿Cuál es la diferencia entre `SET` y `HSET`?
4. ¿Qué representa TTL?
5. ¿Cuándo utilizar un Set?
6. ¿Cuándo utilizar un Sorted Set?
7. ¿Cuál es la diferencia entre List y Set?
8. ¿Qué estructura utilizaría para un ranking?
9. ¿Qué estructura utilizaría para favoritos?
10. ¿Qué problema resuelve Cache Aside?

## Intermedio

11. ¿Qué diferencia existe entre RDB y AOF?
12. ¿Qué es eviction?
13. ¿Qué diferencia existe entre LRU y LFU?
14. ¿Qué diferencia existe entre Pub/Sub y Streams?
15. ¿Qué es un consumer group?
16. ¿Para qué sirve `XACK`?
17. ¿Qué problema resuelve `WATCH`?
18. ¿Qué ventaja proporciona pipeline?
19. ¿Qué es una condición de carrera?
20. ¿Qué función tiene ACL?
21. ¿Qué diferencia existe entre replicación y Sentinel?
22. ¿Qué problema resuelve Redis Cluster?
23. ¿Qué es una hot key?
24. ¿Qué es una big key?
25. ¿Qué información proporciona `INFO memory`?

---

# 23. HOJA RÁPIDA DE COMANDOS

## Básicos

```redis
PING
SET
GET
DEL
UNLINK
EXISTS
TYPE
SCAN
```

## Expiración

```redis
EXPIRE
PEXPIRE
TTL
PTTL
PERSIST
```

## Strings

```redis
SET
GET
MSET
MGET
INCR
DECR
INCRBY
APPEND
```

## Hashes

```redis
HSET
HGET
HGETALL
HMGET
HDEL
HEXISTS
HINCRBY
```

## Lists

```redis
LPUSH
RPUSH
LPOP
RPOP
LRANGE
LLEN
```

## Sets

```redis
SADD
SREM
SMEMBERS
SISMEMBER
SINTER
SUNION
SDIFF
SCARD
```

## Sorted Sets

```redis
ZADD
ZRANGE
ZREM
ZCARD
ZSCORE
ZRANK
ZINCRBY
```

## Streams

```redis
XADD
XRANGE
XREAD
XGROUP
XREADGROUP
XACK
XPENDING
XINFO
```

## Pub/Sub

```redis
PUBLISH
SUBSCRIBE
PSUBSCRIBE
UNSUBSCRIBE
```

## Transacciones

```redis
WATCH
MULTI
EXEC
DISCARD
UNWATCH
```

## Administración

```redis
INFO
CONFIG GET
CONFIG SET
DBSIZE
CLIENT LIST
SLOWLOG GET
MEMORY STATS
MEMORY USAGE
```

## Seguridad

```redis
ACL LIST
ACL USERS
ACL GETUSER
ACL SETUSER
```

---

# 24. BUENAS PRÁCTICAS FINALES

## Desarrollo

* diseñar las claves antes de programar;
* utilizar nombres consistentes;
* seleccionar la estructura correcta;
* establecer TTL para información temporal;
* reutilizar conexiones;
* minimizar round trips;
* evitar operaciones innecesariamente costosas;
* medir antes de optimizar.

## Caché

* definir estrategia de invalidación;
* evitar TTL idénticos para grandes cantidades de claves cuando pueda generar expiraciones masivas;
* evaluar cache stampede;
* medir hit ratio;
* determinar comportamiento ante caída de Redis.

## Seguridad

* no exponer Redis públicamente;
* utilizar ACL;
* aplicar mínimo privilegio;
* proteger credenciales;
* utilizar redes privadas;
* evaluar TLS según el entorno.

## Producción

* establecer límites de memoria;
* definir política de eviction;
* comprender persistencia;
* supervisar replicación;
* establecer métricas;
* revisar SLOWLOG;
* identificar hot keys;
* identificar big keys;
* realizar pruebas de recuperación;
* no asumir que una réplica equivale a un backup.

---

# 25. MAPA MENTAL FINAL

```text
REDIS
│
├── Datos
│   ├── Strings
│   ├── Hashes
│   ├── Lists
│   ├── Sets
│   ├── Sorted Sets
│   ├── Streams
│   └── Geospatial
│
├── Ciclo de vida
│   ├── TTL
│   ├── Expiration
│   └── Eviction
│
├── Patrones
│   ├── Cache
│   ├── Sessions
│   ├── Counters
│   ├── Ranking
│   ├── Rate limiting
│   └── Queues
│
├── Concurrencia
│   ├── Atomic operations
│   ├── MULTI / EXEC
│   ├── WATCH
│   ├── Lua
│   └── Pipelines
│
├── Mensajería
│   ├── Pub/Sub
│   └── Streams
│
├── Persistencia
│   ├── RDB
│   └── AOF
│
├── Seguridad
│   └── ACL
│
├── Alta disponibilidad
│   ├── Replication
│   └── Sentinel
│
├── Escalabilidad
│   └── Redis Cluster
│
└── Operación
    ├── INFO
    ├── SLOWLOG
    ├── Memory
    ├── Latency
    └── Benchmark
```

---

# 26. SECUENCIA DIDÁCTICA RECOMENDADA

Cada sesión de cuatro horas puede distribuirse aproximadamente como:

```text
45 min  → explicación conceptual
45 min  → demostración del instructor
15 min  → descanso
75 min  → laboratorio guiado
45 min  → reto individual o por equipos
15 min  → discusión y conclusiones
```

El objetivo es evitar un curso basado exclusivamente en comandos.

La secuencia didáctica recomendada es:

```text
concepto
   ↓
problema
   ↓
estructura Redis
   ↓
comandos
   ↓
implementación
   ↓
prueba
   ↓
medición
   ↓
discusión
```

---

# 27. CRITERIO PEDAGÓGICO CENTRAL

El estudiante no debería terminar el curso pensando:

> "Sé usar `SET`, `GET`, `HSET` y `ZADD`."

Debería terminar pensando:

> "Puedo analizar un problema, determinar si Redis es apropiado, seleccionar una estructura de datos, definir claves y TTL, implementar el patrón necesario y evaluar las implicaciones de consistencia, memoria, seguridad, persistencia, escalabilidad y rendimiento."

Ese es el criterio de dominio esperado para un nivel **fundamentos–intermedio**.

---

# 28. RUTA DE CONTINUACIÓN

Una vez dominado este curso, la siguiente etapa puede dividirse en cuatro especializaciones:

### Redis para Backend

```text
FastAPI / Django / Node.js
sessions
cache
rate limiting
distributed locks
testing
```

### Redis DevOps

```text
Sentinel
Cluster
backups
monitorización
Docker
Kubernetes
HA
capacity planning
```

### Redis Streaming

```text
Streams
consumer groups
idempotencia
reintentos
dead letter strategies
event-driven architecture
```

### Redis para IA y datos avanzados

```text
JSON
search
vector search
embeddings
semantic search
RAG
time series
probabilistic structures
```

Estas especializaciones constituyen una progresión natural hacia un nivel avanzado.

---

# 29. DOCUMENTACIÓN BASE

El curso debe mantenerse alineado con la documentación oficial de Redis, en particular las secciones dedicadas a estructuras de datos, instalación, administración, persistencia, seguridad, replicación, Sentinel, Cluster, Streams y optimización.

Para estructuras de datos y selección del tipo apropiado debe utilizarse la documentación oficial de tipos y comparación de estructuras.

Para administración y operación resultan especialmente importantes las guías oficiales de persistencia, replicación, Cluster, memoria y latencia.

---

# 30. RESULTADO FINAL DEL CURSO

Al terminar, el participante habrá recorrido la progresión:

```text
¿Qué es Redis?
       ↓
¿Cómo almaceno información?
       ↓
¿Qué estructura debo utilizar?
       ↓
¿Cómo diseño mis claves?
       ↓
¿Cómo implemento TTL?
       ↓
¿Cómo creo un caché?
       ↓
¿Cómo lo conecto con una aplicación?
       ↓
¿Cómo manejo concurrencia?
       ↓
¿Cómo proceso eventos?
       ↓
¿Cómo persisto información?
       ↓
¿Cómo protejo Redis?
       ↓
¿Cómo consigo alta disponibilidad?
       ↓
¿Cómo escalo?
       ↓
¿Cómo diagnostico problemas?
       ↓
¿Cómo diseño una solución Redis real?
```

Con ello se cubre un nivel completo de **fundamentos e intermedio**, dejando preparada la base para Redis avanzado, arquitecturas distribuidas y utilización de Redis en aplicaciones de IA.
