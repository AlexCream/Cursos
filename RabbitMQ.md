# Curso completo de RabbitMQ
## Nivel fundamentos e intermedio

**Versión del curso:** 1.0  
**Fecha de actualización:** agosto de 2026  
**Base técnica:** RabbitMQ 4.x, revisado contra la documentación oficial de RabbitMQ 4.3.5  
**Nivel:** Fundamentos e intermedio  
**Enfoque:** teoría + práctica + diseño + operación  
**Lenguaje principal de laboratorio:** Python 3.11+  
**Cliente principal:** `pika` (AMQP 0-9-1)  
**Cliente asíncrono complementario:** `aio-pika`  
**Entorno recomendado:** Docker / Docker Compose  

---

# Índice

1. [Presentación del curso](#1-presentación-del-curso)
2. [Resultados de aprendizaje](#2-resultados-de-aprendizaje)
3. [Requisitos previos](#3-requisitos-previos)
4. [Entorno general de prácticas](#4-entorno-general-de-prácticas)
5. [Módulo 1. Fundamentos de mensajería](#módulo-1-fundamentos-de-mensajería)
6. [Módulo 2. Arquitectura de RabbitMQ](#módulo-2-arquitectura-de-rabbitmq)
7. [Módulo 3. Instalación, Docker y Management UI](#módulo-3-instalación-docker-y-management-ui)
8. [Módulo 4. Primer productor y consumidor](#módulo-4-primer-productor-y-consumidor)
9. [Módulo 5. Exchanges, bindings y routing keys](#módulo-5-exchanges-bindings-y-routing-keys)
10. [Módulo 6. Work Queues y consumidores competidores](#módulo-6-work-queues-y-consumidores-competidores)
11. [Módulo 7. Acknowledgements, requeue y prefetch](#módulo-7-acknowledgements-requeue-y-prefetch)
12. [Módulo 8. Durabilidad y garantías de entrega](#módulo-8-durabilidad-y-garantías-de-entrega)
13. [Módulo 9. Publisher Confirms y mensajes no enrutables](#módulo-9-publisher-confirms-y-mensajes-no-enrutables)
14. [Módulo 10. TTL, Dead Letter Exchanges y reintentos](#módulo-10-ttl-dead-letter-exchanges-y-reintentos)
15. [Módulo 11. Idempotencia, duplicados y orden](#módulo-11-idempotencia-duplicados-y-orden)
16. [Módulo 12. Tipos de cola: Classic, Quorum y Streams](#módulo-12-tipos-de-cola-classic-quorum-y-streams)
17. [Módulo 13. Patrones Pub/Sub, RPC y Request/Reply](#módulo-13-patrones-pubsub-rpc-y-requestreply)
18. [Módulo 14. RabbitMQ asíncrono con aio-pika](#módulo-14-rabbitmq-asíncrono-con-aio-pika)
19. [Módulo 15. Integración con FastAPI](#módulo-15-integración-con-fastapi)
20. [Módulo 16. Seguridad, usuarios, permisos, vhosts y TLS](#módulo-16-seguridad-usuarios-permisos-vhosts-y-tls)
21. [Módulo 17. Administración, políticas y CLI](#módulo-17-administración-políticas-y-cli)
22. [Módulo 18. Monitorización y observabilidad](#módulo-18-monitorización-y-observabilidad)
23. [Módulo 19. Clustering y alta disponibilidad](#módulo-19-clustering-y-alta-disponibilidad)
24. [Módulo 20. Rendimiento y dimensionamiento](#módulo-20-rendimiento-y-dimensionamiento)
25. [Módulo 21. Pruebas, diagnóstico y resolución de problemas](#módulo-21-pruebas-diagnóstico-y-resolución-de-problemas)
26. [Módulo 22. Patrones de arquitectura y buenas prácticas](#módulo-22-patrones-de-arquitectura-y-buenas-prácticas)
27. [Proyecto integrador](#proyecto-integrador)
28. [Evaluación sugerida](#evaluación-sugerida)
29. [Checklist para producción](#checklist-para-producción)
30. [Glosario](#glosario)
31. [Referencias oficiales](#referencias-oficiales)

---

# 1. Presentación del curso

RabbitMQ es un **message broker** o intermediario de mensajería. Su función es recibir mensajes de aplicaciones productoras, aplicar reglas de enrutamiento y entregar esos mensajes a uno o varios consumidores.

El propósito de este curso es aprender RabbitMQ desde sus fundamentos hasta un nivel intermedio que permita:

- diseñar topologías de mensajería;
- desarrollar productores y consumidores;
- manejar errores y reintentos;
- implementar garantías razonables de entrega;
- seleccionar correctamente el tipo de cola;
- administrar y observar RabbitMQ;
- utilizar RabbitMQ en arquitecturas distribuidas;
- evitar errores frecuentes en producción.

El curso utiliza principalmente **AMQP 0-9-1** para los laboratorios con Python y `pika`, pero explica también el papel de **AMQP 1.0** y de RabbitMQ Streams.

> RabbitMQ 4.x ha evolucionado respecto de versiones antiguas. En particular, las **Classic Mirrored Queues** ya no forman parte de RabbitMQ desde 4.0. Para cargas que requieren replicación y alta seguridad de datos se deben estudiar principalmente **Quorum Queues** y **Streams**.

---

# 2. Resultados de aprendizaje

Al finalizar, el participante será capaz de:

1. Explicar la diferencia entre comunicación síncrona y asíncrona.
2. Identificar productor, consumidor, exchange, queue, binding y routing key.
3. Crear topologías RabbitMQ mediante código.
4. Implementar exchanges `direct`, `fanout`, `topic` y `headers`.
5. Diseñar Work Queues con múltiples consumidores.
6. Utilizar acknowledgements manuales y `prefetch`.
7. Comprender las limitaciones de las garantías *at-most-once*, *at-least-once* y *exactly-once*.
8. Habilitar Publisher Confirms.
9. Implementar Dead Letter Exchanges.
10. Diseñar estrategias de reintento sin crear ciclos infinitos.
11. Construir consumidores idempotentes.
12. Elegir entre Classic Queues, Quorum Queues y Streams.
13. Gestionar vhosts, usuarios, permisos y políticas.
14. Monitorizar RabbitMQ con Management UI, Prometheus y Grafana.
15. Comprender los fundamentos de clustering y consenso.
16. Integrar RabbitMQ con aplicaciones web asíncronas.
17. Diagnosticar fallos comunes.
18. Diseñar una arquitectura de mensajería mantenible y preparada para producción.

---

# 3. Requisitos previos

## Conocimientos

Se recomienda:

- fundamentos de programación;
- Python básico o intermedio;
- terminal o PowerShell;
- nociones de HTTP y APIs;
- conceptos básicos de Docker;
- conocimientos generales de sistemas distribuidos, aunque no son obligatorios.

## Software

- Docker Desktop o Docker Engine;
- Docker Compose;
- Python 3.11 o superior;
- editor como VS Code;
- Git;
- opcional: `curl`, Postman o Bruno.

Verificación:

```bash
docker --version
docker compose version
python --version
git --version
```

---

# 4. Entorno general de prácticas

Cree una carpeta:

```text
curso-rabbitmq/
├── docker-compose.yml
├── requirements.txt
├── src/
│   ├── producer.py
│   └── consumer.py
└── labs/
```

## `docker-compose.yml`

```yaml
services:
  rabbitmq:
    image: rabbitmq:4.3-management
    container_name: rabbitmq-course
    hostname: rabbitmq-course
    environment:
      RABBITMQ_DEFAULT_USER: curso
      RABBITMQ_DEFAULT_PASS: curso123
    ports:
      - "5672:5672"
      - "15672:15672"
      - "15692:15692"
    volumes:
      - rabbitmq_data:/var/lib/rabbitmq

volumes:
  rabbitmq_data:
```

> Las credenciales anteriores son exclusivamente para desarrollo local. No deben utilizarse en producción.

Iniciar:

```bash
docker compose up -d
```

Comprobar:

```bash
docker compose ps
```

Management UI:

```text
http://localhost:15672
```

Credenciales:

```text
usuario: curso
contraseña: curso123
```

## Dependencias Python

`requirements.txt`:

```text
pika>=1.3,<2
aio-pika>=9,<10
fastapi>=0.110
uvicorn[standard]>=0.27
```

Instalar:

```bash
python -m venv .venv
```

Linux/macOS:

```bash
source .venv/bin/activate
```

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

```bash
pip install -r requirements.txt
```

Cadena de conexión usada durante el curso:

```text
amqp://curso:curso123@localhost:5672/%2F
```

---

# Módulo 1. Fundamentos de mensajería

## Objetivos

- comprender por qué existe un message broker;
- distinguir comunicación síncrona y asíncrona;
- identificar ventajas y costos de la mensajería.

## 1.1 Comunicación síncrona

En una interacción síncrona:

```text
Cliente -> Servicio A -> Servicio B -> Respuesta
```

El emisor normalmente espera el resultado.

Ejemplos:

- HTTP REST;
- llamada RPC;
- consulta SQL.

Ventajas:

- modelo mental sencillo;
- respuesta inmediata;
- fácil de depurar en sistemas pequeños.

Desventajas:

- mayor acoplamiento temporal;
- fallos en cascada;
- dependencia de disponibilidad inmediata;
- dificultad para absorber picos.

## 1.2 Comunicación asíncrona

```text
Productor -> Broker -> Consumidor
```

El productor entrega un mensaje al broker y continúa.

Ventajas:

- desacoplamiento temporal;
- absorción de picos;
- procesamiento diferido;
- escalabilidad horizontal;
- resiliencia.

Costos:

- consistencia eventual;
- duplicados;
- necesidad de idempotencia;
- observabilidad más compleja;
- depuración distribuida;
- mayor complejidad operacional.

## 1.3 ¿Qué es un mensaje?

Un mensaje suele contener:

```json
{
  "event_id": "evt_123",
  "type": "order.created",
  "occurred_at": "2026-08-28T12:00:00Z",
  "payload": {
    "order_id": 1001,
    "customer_id": 55,
    "total": 1299.90
  }
}
```

Conviene separar:

- metadatos;
- tipo de evento;
- identificador único;
- versión del esquema;
- contenido de negocio.

## 1.4 Broker vs base de datos

RabbitMQ no debe tratarse como una base de datos convencional.

Una base de datos optimiza:

- persistencia de estado;
- consultas;
- relaciones;
- índices;
- transacciones.

RabbitMQ optimiza:

- transporte;
- enrutamiento;
- buffering;
- entrega;
- coordinación de consumidores.

## Ejercicio

Clasifique como síncrono, asíncrono o híbrido:

1. consultar saldo bancario;
2. generar una miniatura de una imagen;
3. enviar correo de bienvenida;
4. confirmar un pago;
5. actualizar un índice de búsqueda;
6. ejecutar una auditoría nocturna.

---

# Módulo 2. Arquitectura de RabbitMQ

## Objetivos

- conocer los componentes principales;
- comprender el flujo de un mensaje;
- diferenciar conexión y canal.

## 2.1 Componentes

```mermaid
flowchart LR
    P[Publisher] --> E[Exchange]
    E -->|Binding + Routing Key| Q1[Queue A]
    E -->|Binding + Routing Key| Q2[Queue B]
    Q1 --> C1[Consumer 1]
    Q2 --> C2[Consumer 2]
```

### Publisher

Aplicación que publica mensajes.

### Exchange

Recibe publicaciones y decide hacia qué colas o streams se enrutan.

### Queue

Buffer desde el que consumen las aplicaciones.

### Binding

Relación entre exchange y queue.

### Routing key

Valor utilizado por ciertos exchanges para decidir el destino.

### Consumer

Suscripción que recibe mensajes.

### Virtual host

Espacio lógico aislado que contiene exchanges, colas, bindings, permisos y políticas.

## 2.2 Flujo

```text
1. Productor abre conexión.
2. Crea un channel.
3. Publica en un exchange.
4. RabbitMQ evalúa bindings.
5. El mensaje llega a una o más queues.
6. RabbitMQ lo entrega a consumidores.
7. El consumidor confirma, rechaza o devuelve el mensaje.
```

## 2.3 Connection vs Channel

Una conexión TCP es relativamente costosa.

Un **channel** es una conexión lógica multiplexada dentro de una conexión TCP.

Regla práctica:

> Reutilice conexiones de larga duración y abra channels según las necesidades de concurrencia. No cree una conexión nueva por mensaje.

## 2.4 Declaración idempotente de topología

Es frecuente que las aplicaciones declaren sus exchanges y colas durante el arranque.

Si una entidad ya existe con los mismos parámetros, la declaración funciona.

Si existe con parámetros incompatibles, RabbitMQ cerrará el channel con error.

---

# Módulo 3. Instalación, Docker y Management UI

## 3.1 Puertos principales

| Puerto | Uso |
|---|---|
| 5672 | AMQP sin TLS |
| 5671 | AMQP con TLS, cuando se configura |
| 15672 | Management UI / HTTP API |
| 15692 | Prometheus, si el plugin está habilitado |
| 5552 | RabbitMQ Stream Protocol, cuando se habilita |

## 3.2 Estado del nodo

```bash
docker exec rabbitmq-course rabbitmq-diagnostics status
```

Ping:

```bash
docker exec rabbitmq-course rabbitmq-diagnostics ping
```

Listado de plugins:

```bash
docker exec rabbitmq-course rabbitmq-plugins list
```

## 3.3 Management UI

Explore:

- **Overview**
- **Connections**
- **Channels**
- **Exchanges**
- **Queues and Streams**
- **Admin**

Observe:

- mensajes ready;
- mensajes unacknowledged;
- tasa de publicación;
- tasa de entrega;
- consumidores;
- memoria;
- conexiones.

## Laboratorio

1. Inicie RabbitMQ.
2. Entre a Management UI.
3. Identifique el exchange por defecto.
4. Observe los exchanges predefinidos.
5. Revise las conexiones activas.
6. Ejecute `rabbitmq-diagnostics status`.

---

# Módulo 4. Primer productor y consumidor

## 4.1 Productor

`src/producer.py`:

```python
import json
import pika

URL = "amqp://curso:curso123@localhost:5672/%2F"

connection = pika.BlockingConnection(pika.URLParameters(URL))
channel = connection.channel()

channel.queue_declare(
    queue="hello",
    durable=True,
)

message = {
    "message": "Hola RabbitMQ",
    "source": "curso"
}

channel.basic_publish(
    exchange="",
    routing_key="hello",
    body=json.dumps(message).encode(),
    properties=pika.BasicProperties(
        content_type="application/json",
        delivery_mode=pika.DeliveryMode.Persistent,
    ),
)

print("Mensaje publicado")
connection.close()
```

## 4.2 Consumidor

`src/consumer.py`:

```python
import json
import pika

URL = "amqp://curso:curso123@localhost:5672/%2F"

connection = pika.BlockingConnection(pika.URLParameters(URL))
channel = connection.channel()

channel.queue_declare(
    queue="hello",
    durable=True,
)

def callback(ch, method, properties, body):
    data = json.loads(body)
    print("Recibido:", data)

    ch.basic_ack(delivery_tag=method.delivery_tag)

channel.basic_consume(
    queue="hello",
    on_message_callback=callback,
    auto_ack=False,
)

print("Esperando mensajes...")
channel.start_consuming()
```

Ejecutar:

Terminal 1:

```bash
python src/consumer.py
```

Terminal 2:

```bash
python src/producer.py
```

## 4.3 Exchange por defecto

Cuando:

```python
exchange=""
```

se usa el **default exchange**.

Cada queue se encuentra vinculada de forma automática a este exchange mediante una routing key igual al nombre de la queue.

Por eso:

```python
routing_key="hello"
```

envía el mensaje a la cola `hello`.

## Práctica

Modifique el productor para enviar:

```json
{
  "id": 1,
  "type": "task.created",
  "data": {
    "name": "procesar reporte"
  }
}
```

---

# Módulo 5. Exchanges, bindings y routing keys

RabbitMQ incluye varios tipos de exchange.

## 5.1 Direct

Enruta cuando la routing key coincide con la binding key.

```mermaid
flowchart LR
    P[Publisher] --> E[Direct Exchange]
    E -->|error| Q1[error.queue]
    E -->|info| Q2[info.queue]
```

Declaración:

```python
channel.exchange_declare(
    exchange="logs.direct",
    exchange_type="direct",
    durable=True,
)

channel.queue_declare(queue="logs.error", durable=True)

channel.queue_bind(
    exchange="logs.direct",
    queue="logs.error",
    routing_key="error",
)
```

Publicar:

```python
channel.basic_publish(
    exchange="logs.direct",
    routing_key="error",
    body=b"Fallo de base de datos",
)
```

### Casos

- comandos por categoría;
- prioridad lógica;
- separación por tipo exacto.

---

## 5.2 Fanout

Ignora la routing key y envía a todas las queues vinculadas.

```mermaid
flowchart LR
    P[Publisher] --> E[Fanout]
    E --> QA[Email]
    E --> QB[Analytics]
    E --> QC[Audit]
```

```python
channel.exchange_declare(
    exchange="events.broadcast",
    exchange_type="fanout",
    durable=True,
)
```

Casos:

- broadcasting;
- invalidación de caché;
- eventos que deben ser procesados por subsistemas independientes.

---

## 5.3 Topic

Permite patrones con palabras separadas por puntos.

Comodines:

- `*` = exactamente una palabra;
- `#` = cero o más palabras.

Routing keys:

```text
order.created
order.cancelled
customer.created
inventory.stock.low
```

Bindings:

```text
order.*
#
inventory.#
*.created
```

Ejemplo:

```python
channel.exchange_declare(
    exchange="domain.events",
    exchange_type="topic",
    durable=True,
)

channel.queue_bind(
    exchange="domain.events",
    queue="analytics",
    routing_key="#",
)

channel.queue_bind(
    exchange="domain.events",
    queue="orders",
    routing_key="order.*",
)
```

## 5.4 Headers

Enruta con base en headers y no principalmente en routing keys.

Útil cuando los criterios no encajan naturalmente en una clave jerárquica.

Ejemplo conceptual:

```text
format=pdf
tenant=acme
priority=high
```

## Decisión rápida

| Necesidad | Exchange |
|---|---|
| Coincidencia exacta | Direct |
| Enviar a todos | Fanout |
| Enrutamiento jerárquico | Topic |
| Criterios por metadatos | Headers |

## Laboratorio

Construya:

```text
exchange: ecommerce.events
tipo: topic

queues:
- email-service
- inventory-service
- analytics-service
```

Bindings sugeridos:

```text
email-service      -> order.created
inventory-service  -> order.*
analytics-service  -> #
```

---

# Módulo 6. Work Queues y consumidores competidores

Una Work Queue permite repartir trabajo entre instancias equivalentes.

```mermaid
flowchart LR
    P[Producer] --> Q[task.queue]
    Q --> W1[Worker 1]
    Q --> W2[Worker 2]
    Q --> W3[Worker 3]
```

Una sola copia de un mensaje de una queue se entrega normalmente a un consumidor.

## Ejemplo

```python
import time

def callback(ch, method, properties, body):
    print("Procesando:", body.decode())
    time.sleep(2)
    ch.basic_ack(method.delivery_tag)
```

Inicie varias instancias:

```bash
python worker.py
python worker.py
python worker.py
```

Publique 20 tareas.

## Escalamiento horizontal

Si el backlog crece:

```text
Producer rate > Consumer processing rate
```

se puede:

- optimizar consumidores;
- incrementar concurrencia;
- agregar más instancias;
- revisar prefetch;
- particionar la carga;
- utilizar Streams/Super Streams si el patrón lo requiere.

## Riesgo

Más consumidores no garantiza rendimiento infinito.

Los límites pueden estar en:

- base de datos;
- APIs externas;
- CPU;
- disco;
- red;
- locks;
- tasa de escritura;
- capacidad del broker.

---

# Módulo 7. Acknowledgements, requeue y prefetch

## 7.1 Acknowledgement

Un acknowledgement indica que el consumidor terminó de procesar un mensaje.

### Auto-ack

```python
auto_ack=True
```

RabbitMQ considera entregado el mensaje inmediatamente.

Ventaja:

- mayor simplicidad.

Riesgo:

- si el proceso muere durante el trabajo, el mensaje puede perderse desde la perspectiva de la aplicación.

### Ack manual

```python
auto_ack=False
```

Después de procesar:

```python
ch.basic_ack(delivery_tag=method.delivery_tag)
```

Este es el enfoque habitual cuando se necesita mayor seguridad.

## 7.2 Reject y nack

Rechazar sin requeue:

```python
ch.basic_reject(
    delivery_tag=method.delivery_tag,
    requeue=False,
)
```

Nack:

```python
ch.basic_nack(
    delivery_tag=method.delivery_tag,
    requeue=False,
)
```

Requeue:

```python
ch.basic_nack(
    delivery_tag=method.delivery_tag,
    requeue=True,
)
```

## 7.3 Cuidado con requeue infinito

Patrón peligroso:

```text
consume
 -> error
 -> requeue
 -> consume
 -> error
 -> requeue
 -> ...
```

Consecuencias:

- consumo de CPU;
- ruido;
- starvation;
- incremento de tráfico;
- cola bloqueada por mensajes venenosos.

Solución:

- reintentos limitados;
- backoff;
- DLQ;
- clasificación de errores;
- idempotencia.

## 7.4 Prefetch

```python
channel.basic_qos(prefetch_count=10)
```

Controla cuántas entregas no confirmadas pueden estar en vuelo.

### Prefetch bajo

Ventajas:

- mejor distribución entre consumidores;
- menor trabajo acumulado por consumidor.

Desventajas:

- puede reducir throughput.

### Prefetch alto

Ventajas:

- mejor utilización de consumidores rápidos;
- menos espera.

Desventajas:

- más memoria;
- distribución menos uniforme;
- más mensajes retenidos por consumidores lentos.

No existe un valor universal.

## Laboratorio

1. Use `prefetch_count=1`.
2. Inicie tres workers.
3. Publique 30 mensajes.
4. Repita con `prefetch_count=10`.
5. Compare distribución y rendimiento.

---

# Módulo 8. Durabilidad y garantías de entrega

## 8.1 Queue durable

```python
channel.queue_declare(
    queue="orders",
    durable=True,
)
```

Indica que la definición puede sobrevivir al reinicio del broker.

## 8.2 Exchange durable

```python
channel.exchange_declare(
    exchange="orders.events",
    exchange_type="topic",
    durable=True,
)
```

## 8.3 Mensaje persistente

```python
properties=pika.BasicProperties(
    delivery_mode=pika.DeliveryMode.Persistent
)
```

Esto mejora la durabilidad, pero por sí solo no constituye una garantía completa de extremo a extremo.

## 8.4 Tres modelos conceptuales

### At-most-once

```text
0 o 1 entregas
```

Puede perder mensajes, pero evita reintentos.

### At-least-once

```text
1 o más entregas
```

No presupone que no haya duplicados.

Es el modelo más común en sistemas robustos.

### Exactly-once

En un sistema distribuido real, la garantía *exactly-once end-to-end* es difícil y normalmente depende de restricciones y coordinación adicionales.

En la práctica se diseña:

```text
at-least-once delivery
+
idempotent processing
=
efecto de negocio equivalente a una vez
```

## 8.5 Qué se necesita para mayor seguridad

En términos generales:

Productor:

- conexión confiable;
- publisher confirms;
- manejo de mensajes no enrutables;
- estrategia ante reconexión.

Broker:

- queue adecuada;
- persistencia;
- disco confiable;
- replicación cuando aplique.

Consumidor:

- ack manual;
- idempotencia;
- retries limitados;
- DLQ.

---

# Módulo 9. Publisher Confirms y mensajes no enrutables

Publisher Confirms permiten conocer cuándo RabbitMQ ha aceptado responsabilidad sobre un mensaje.

## 9.1 Activación con `pika`

```python
channel.confirm_delivery()
```

Ejemplo:

```python
import pika

channel.confirm_delivery()

try:
    channel.basic_publish(
        exchange="orders.events",
        routing_key="order.created",
        body=b'{"order_id":1001}',
        mandatory=True,
        properties=pika.BasicProperties(
            delivery_mode=pika.DeliveryMode.Persistent
        ),
    )
    print("Publicación confirmada")
except pika.exceptions.UnroutableError:
    print("Mensaje no enrutable")
except pika.exceptions.NackError:
    print("RabbitMQ rechazó la publicación")
```

## 9.2 `mandatory=True`

Solicita que un mensaje que no pueda ser enrutado a ninguna queue sea retornado al publisher.

Sin una estrategia para unroutable messages, una publicación puede ser aceptada por un exchange pero terminar sin destino.

## 9.3 Throughput

No es buena práctica esperar una confirmación bloqueante por cada mensaje cuando se requiere alto rendimiento.

Estrategias:

1. confirmación individual;
2. confirmación por lotes;
3. confirms asíncronos/streaming.

Para cargas altas, el enfoque asíncrono normalmente ofrece mejor throughput.

## Práctica

1. Declare un exchange sin bindings.
2. Publique con `mandatory=True`.
3. Capture el error.
4. Cree un binding.
5. Publique nuevamente.

---

# Módulo 10. TTL, Dead Letter Exchanges y reintentos

## 10.1 TTL

TTL puede aplicarse a mensajes o queues.

### TTL por queue

```python
arguments = {
    "x-message-ttl": 60_000
}

channel.queue_declare(
    queue="temporary.jobs",
    durable=True,
    arguments=arguments,
)
```

El valor está en milisegundos.

## 10.2 Dead Letter Exchange

Un mensaje puede convertirse en dead letter cuando, entre otros casos:

- un consumidor lo rechaza sin requeue;
- expira por TTL;
- una queue supera ciertos límites;
- una Quorum Queue supera el límite de entregas aplicable.

Topología:

```mermaid
flowchart LR
    P[Producer] --> E[orders.exchange]
    E --> Q[orders.queue]
    Q --> C[Consumer]
    C -->|reject / nack no requeue| DLX[orders.dlx]
    DLX --> DLQ[orders.dead]
```

## 10.3 Configuración didáctica

```python
channel.exchange_declare(
    exchange="orders.dlx",
    exchange_type="direct",
    durable=True,
)

channel.queue_declare(
    queue="orders.dead",
    durable=True,
)

channel.queue_bind(
    exchange="orders.dlx",
    queue="orders.dead",
    routing_key="dead",
)

channel.queue_declare(
    queue="orders.main",
    durable=True,
    arguments={
        "x-dead-letter-exchange": "orders.dlx",
        "x-dead-letter-routing-key": "dead",
    },
)
```

> Para producción, RabbitMQ recomienda preferir **policies** frente a `x-arguments` codificados rígidamente cuando la configuración puede administrarse operacionalmente. Las policies permiten modificar comportamiento sin redeplegar aplicaciones.

## 10.4 Tipos de error

### Transitorio

Ejemplos:

- timeout de API;
- conexión temporalmente caída;
- lock temporal.

Acción:

```text
retry con backoff
```

### Permanente

Ejemplos:

- JSON inválido;
- campo obligatorio ausente;
- regla de negocio imposible.

Acción:

```text
DLQ inmediata
```

## 10.5 Retry tradicional con TTL + DLX

```text
main.queue
   |
   | error temporal
   v
retry.queue --TTL--> exchange principal --> main.queue
```

Es útil, pero añade complejidad y movimiento adicional de mensajes.

## 10.6 Delayed Retries en Quorum Queues, RabbitMQ 4.3

RabbitMQ 4.3 incorporó **Delayed Retries** para Quorum Queues.

La queue puede apartar internamente un mensaje y volverlo elegible para entrega después de un retraso, sin necesitar el ciclo clásico de DLX + TTL.

Parámetros relacionados:

```text
x-delayed-retry-type
x-delayed-retry-min
x-delayed-retry-max
```

Ejemplo conceptual:

```python
arguments = {
    "x-queue-type": "quorum",
    "x-delayed-retry-type": "all",
    "x-delayed-retry-min": 5_000,
    "x-delayed-retry-max": 60_000,
}
```

RabbitMQ 4.3 puede aplicar backoff lineal hasta el máximo configurado.

> Use esta función cuando su versión, protocolo y cliente sean compatibles y la semántica encaje con el caso de uso. No convierta cada error en retry automático: primero clasifique el fallo.

## 10.7 Poison message

Un mensaje venenoso falla permanentemente cada vez que se procesa.

Debe existir una política clara:

```text
max attempts
 -> dead letter
 -> observabilidad
 -> inspección
 -> corrección
 -> replay controlado si procede
```

## Laboratorio

Implemente un consumidor que:

- procese mensajes válidos;
- rechace JSON inválido;
- simule un error temporal;
- envíe fallos permanentes a DLQ;
- agregue `message_id`.

---

# Módulo 11. Idempotencia, duplicados y orden

## 11.1 ¿Por qué existen duplicados?

Escenario:

```text
1. consumidor procesa DB
2. commit exitoso
3. antes del ACK se pierde conexión
4. RabbitMQ vuelve a entregar
```

El mensaje no estaba perdido: el broker no recibió el ack.

Resultado: **redelivery**.

## 11.2 Consumidor idempotente

Un consumidor idempotente produce el mismo efecto de negocio aunque procese un mensaje repetido.

Ejemplo de estrategia:

```text
tabla processed_messages

message_id    processed_at
evt_123       ...
evt_124       ...
```

Pseudocódigo:

```python
def handle(message):
    if already_processed(message["event_id"]):
        return

    with transaction():
        apply_business_change(message)
        mark_as_processed(message["event_id"])
```

## 11.3 Dedupe

Opciones:

- tabla de inbox;
- clave única;
- cache con expiración;
- estado del agregado;
- secuencia/versionado.

## 11.4 Outbox Pattern

Problema:

```text
DB commit correcto
RabbitMQ publish falla
```

Solución:

```mermaid
flowchart LR
    A[Application Transaction] --> DB[(Business Tables)]
    A --> O[(Outbox Table)]
    O --> R[Outbox Relay]
    R --> MQ[RabbitMQ]
```

En una sola transacción de base de datos:

```text
actualizar negocio
+
insertar evento en outbox
```

Otro proceso publica la outbox.

## 11.5 Inbox Pattern

En el consumidor:

```text
RabbitMQ
 -> Inbox
 -> lógica de negocio
```

La inbox registra mensajes ya tratados.

## 11.6 Orden

No asuma orden global.

El orden puede romperse por:

- múltiples consumidores;
- retries;
- requeues;
- prioridades;
- procesamiento paralelo;
- particiones.

Si el orden es crítico:

- defina la unidad de orden;
- por ejemplo `order_id`;
- serialice por agregado;
- use Single Active Consumer cuando corresponda;
- evalúe Streams y particionamiento.

---

# Módulo 12. Tipos de cola: Classic, Quorum y Streams

RabbitMQ 4.x obliga a elegir el tipo de almacenamiento de acuerdo con el caso.

## 12.1 Classic Queue

Adecuada para muchos casos simples o cuando no se requiere replicación de la queue.

Características generales:

- modelo de queue tradicional;
- baja complejidad;
- útil para cargas temporales o escenarios sencillos;
- no sustituye una estrategia HA cuando la pérdida no es aceptable.

## 12.2 Quorum Queue

Está basada en consenso **Raft**.

```python
channel.queue_declare(
    queue="orders.quorum",
    durable=True,
    arguments={
        "x-queue-type": "quorum"
    },
)
```

Características:

- replicada;
- orientada a seguridad de datos;
- adecuada para queues críticas y duraderas;
- requiere mayoría disponible;
- publisher confirms son esenciales para aprovechar sus garantías.

En RabbitMQ 4.3 destacan, entre otras mejoras:

- prioridades estrictas de mensajes;
- delayed retries;
- consumer timeouts mejorados.

Una Quorum Queue intercambia parte de la latencia y el costo de I/O por mejores propiedades de seguridad y replicación.

## 12.3 Streams

Un Stream es conceptualmente un log append-only.

```text
Producer -> [0][1][2][3][4][5] -> Consumers
```

A diferencia de una queue tradicional:

- el consumo es no destructivo;
- puede releerse;
- los consumidores usan offsets;
- está diseñado para throughput elevado;
- es persistente y replicado.

Casos:

- event streaming;
- replay;
- pipelines de datos;
- grandes fan-outs;
- backlogs extensos;
- procesamiento de históricos + tiempo real.

## 12.4 Super Streams

Permiten particionar un stream para aumentar paralelismo y throughput.

Conceptualmente:

```text
super-stream
├── partition-0
├── partition-1
├── partition-2
└── partition-3
```

Se necesita una estrategia de particionamiento estable.

## 12.5 Comparación

| Característica | Classic | Quorum | Stream |
|---|---:|---:|---:|
| Queue tradicional | Sí | Sí | No exactamente |
| Replicación | No como quorum | Sí | Sí |
| Raft | No | Sí | Componentes replicados |
| Consumo destructivo | Sí | Sí | No |
| Replay | No | No | Sí |
| Alta seguridad de datos | Media según diseño | Alta | Alta, con semántica distinta |
| Backlog muy grande | Depende | Menos ideal | Ideal |
| Fan-out masivo | Depende | Menos ideal | Muy adecuado |

## Regla práctica

Use:

- **Classic** para casos simples donde la replicación de la queue no es requisito principal;
- **Quorum** para mensajes críticos que necesitan una queue replicada;
- **Streams** cuando necesita replay, fan-out, alto throughput o log persistente.

---

# Módulo 13. Patrones Pub/Sub, RPC y Request/Reply

## 13.1 Pub/Sub

Cada servicio necesita su propia queue.

Incorrecto para broadcasting:

```text
event -> una queue -> varios consumidores
```

Eso distribuye mensajes, no duplica el evento a cada servicio.

Correcto:

```text
            -> email.queue
exchange ---|-> audit.queue
            -> analytics.queue
```

## 13.2 Event Notification

Evento pequeño:

```json
{
  "event_id": "evt_1",
  "type": "customer.updated",
  "customer_id": 98
}
```

El consumidor consulta el estado si lo necesita.

Ventaja:

- mensajes pequeños.

Costo:

- dependencia de otra lectura.

## 13.3 Event-Carried State Transfer

```json
{
  "event_id": "evt_1",
  "type": "customer.updated",
  "customer": {
    "id": 98,
    "name": "Ana",
    "segment": "B2B"
  }
}
```

Ventaja:

- mayor autonomía.

Costo:

- duplicación de datos;
- evolución de esquemas.

## 13.4 RPC

RabbitMQ permite implementar Request/Reply:

```text
Client -> request queue -> Worker
Client <- reply queue   <- Worker
```

Propiedades importantes:

- `correlation_id`;
- `reply_to`.

Ejemplo conceptual:

```python
properties=pika.BasicProperties(
    correlation_id="req-123",
    reply_to="reply.queue"
)
```

## 13.5 Direct Reply-To

RabbitMQ ofrece Direct Reply-To para ciertos casos de RPC y evita declarar una queue temporal tradicional por cliente.

## Cuándo NO usar RPC sobre RabbitMQ

No utilice RabbitMQ para disfrazar una arquitectura totalmente síncrona.

Si cada servicio:

```text
A espera B
B espera C
C espera D
```

se recuperan muchos problemas del acoplamiento síncrono.

---

# Módulo 14. RabbitMQ asíncrono con aio-pika

`aio-pika` integra RabbitMQ con `asyncio`.

## 14.1 Producer robusto

```python
import asyncio
import json
import aio_pika

URL = "amqp://curso:curso123@localhost/"

async def main():
    connection = await aio_pika.connect_robust(URL)

    async with connection:
        channel = await connection.channel(
            publisher_confirms=True
        )

        exchange = await channel.declare_exchange(
            "domain.events",
            aio_pika.ExchangeType.TOPIC,
            durable=True,
        )

        message = aio_pika.Message(
            body=json.dumps({
                "event_id": "evt-100",
                "type": "order.created",
                "order_id": 100
            }).encode(),
            content_type="application/json",
            delivery_mode=aio_pika.DeliveryMode.PERSISTENT,
            message_id="evt-100",
        )

        await exchange.publish(
            message,
            routing_key="order.created",
            mandatory=True,
        )

asyncio.run(main())
```

## 14.2 Consumer

```python
import asyncio
import json
import aio_pika

URL = "amqp://curso:curso123@localhost/"

async def process_message(message: aio_pika.IncomingMessage):
    async with message.process(requeue=False):
        payload = json.loads(message.body)
        print(payload)

async def main():
    connection = await aio_pika.connect_robust(URL)

    channel = await connection.channel()
    await channel.set_qos(prefetch_count=20)

    queue = await channel.declare_queue(
        "async.orders",
        durable=True,
    )

    await queue.consume(process_message)

    print("Consumidor iniciado")
    await asyncio.Future()

asyncio.run(main())
```

## 14.3 `connect_robust`

Ayuda a recuperar conexiones y topología después de interrupciones.

No elimina la necesidad de:

- idempotencia;
- reconexión bien diseñada;
- publisher confirms;
- timeouts;
- monitorización.

---

# Módulo 15. Integración con FastAPI

RabbitMQ puede desacoplar trabajos pesados de una API.

## Arquitectura

```mermaid
flowchart LR
    U[Client] --> API[FastAPI]
    API --> DB[(DB)]
    API --> MQ[RabbitMQ]
    MQ --> W[Worker]
    W --> EXT[Servicio externo]
```

## 15.1 Patrón

```text
POST /reports
 -> validar
 -> crear registro
 -> publicar job
 -> responder 202 Accepted
```

El trabajo real ocurre fuera del request HTTP.

## 15.2 Ejemplo simplificado

```python
from contextlib import asynccontextmanager

import aio_pika
from fastapi import FastAPI

rabbit_connection = None
rabbit_channel = None
jobs_exchange = None

@asynccontextmanager
async def lifespan(app: FastAPI):
    global rabbit_connection, rabbit_channel, jobs_exchange

    rabbit_connection = await aio_pika.connect_robust(
        "amqp://curso:curso123@localhost/"
    )

    rabbit_channel = await rabbit_connection.channel(
        publisher_confirms=True
    )

    jobs_exchange = await rabbit_channel.declare_exchange(
        "jobs",
        aio_pika.ExchangeType.DIRECT,
        durable=True,
    )

    yield

    await rabbit_connection.close()

app = FastAPI(lifespan=lifespan)
```

Endpoint:

```python
import json
import uuid
import aio_pika

@app.post("/reports", status_code=202)
async def create_report():
    job_id = str(uuid.uuid4())

    body = json.dumps({
        "job_id": job_id,
        "type": "report.generate"
    }).encode()

    await jobs_exchange.publish(
        aio_pika.Message(
            body=body,
            content_type="application/json",
            delivery_mode=aio_pika.DeliveryMode.PERSISTENT,
            message_id=job_id,
        ),
        routing_key="report.generate",
        mandatory=True,
    )

    return {
        "job_id": job_id,
        "status": "accepted"
    }
```

## 15.3 Consideración transaccional

Problema:

```text
guardar DB
publicar evento
```

Si solo una operación funciona, existe inconsistencia.

Para procesos críticos, estudie:

- Transactional Outbox;
- idempotencia;
- correlación;
- reintentos del relay.

---

# Módulo 16. Seguridad, usuarios, permisos, vhosts y TLS

## 16.1 Virtual hosts

RabbitMQ es multi-tenant a nivel lógico.

Crear:

```bash
docker exec rabbitmq-course \
  rabbitmqctl add_vhost ecommerce
```

Los recursos de un vhost están separados lógicamente.

Ejemplos:

```text
/dev
/staging
/prod
```

o por producto:

```text
/ecommerce
/billing
/notifications
```

## 16.2 Usuarios

```bash
docker exec rabbitmq-course \
  rabbitmqctl add_user ecommerce_app strong_dev_password
```

## 16.3 Permisos

RabbitMQ separa permisos de:

- `configure`;
- `write`;
- `read`.

Ejemplo:

```bash
docker exec rabbitmq-course \
  rabbitmqctl set_permissions \
  -p ecommerce \
  ecommerce_app \
  ".*" \
  ".*" \
  ".*"
```

En producción aplique **least privilege**.

No dé `.*` indiscriminadamente si la aplicación solo necesita recursos específicos.

## 16.4 Usuario `guest`

El usuario predeterminado `guest` está deliberadamente limitado para conexiones remotas.

No diseñe un despliegue de producción alrededor de `guest/guest`.

## 16.5 TLS

TLS protege:

- credenciales;
- payload;
- metadatos;
- tráfico cliente-broker.

Puede utilizarse:

- TLS server-side;
- validación de certificado;
- mTLS;
- autenticación basada en certificado.

En producción:

```text
amqps://...
```

y no:

```text
amqp://...
```

cuando la red no sea totalmente confiable.

## 16.6 Secretos

No coloque contraseñas en:

- repositorios Git;
- imágenes Docker;
- archivos `.env` versionados;
- logs.

Use:

- secret managers;
- Kubernetes Secrets con controles adecuados;
- Vault;
- mecanismos de la plataforma cloud;
- rotación de credenciales.

---

# Módulo 17. Administración, políticas y CLI

## 17.1 Herramientas

RabbitMQ incluye:

- `rabbitmqctl`;
- `rabbitmq-diagnostics`;
- `rabbitmq-plugins`;
- `rabbitmq-queues`;
- `rabbitmq-streams`;
- `rabbitmqadmin`.

## 17.2 Listar queues

```bash
docker exec rabbitmq-course \
  rabbitmqctl list_queues \
  name messages_ready messages_unacknowledged consumers
```

## 17.3 Exchanges

```bash
docker exec rabbitmq-course \
  rabbitmqctl list_exchanges name type
```

## 17.4 Bindings

```bash
docker exec rabbitmq-course \
  rabbitmqctl list_bindings
```

## 17.5 Conexiones

```bash
docker exec rabbitmq-course \
  rabbitmqctl list_connections
```

## 17.6 Políticas

Las policies permiten administrar configuraciones sobre grupos de queues.

Ejemplo de DLX:

```bash
rabbitmqctl set_policy \
  DLX \
  "^orders\." \
  '{"dead-letter-exchange":"orders.dlx"}' \
  --apply-to queues \
  --priority 7
```

Ventajas:

- cambios sin recompilar;
- operación centralizada;
- configuración por patrón;
- separación entre código y operación.

## 17.7 Definitions

RabbitMQ permite exportar/importar definiciones de topología y configuración.

Útil para:

- reproducibilidad;
- infraestructura como código;
- recuperación;
- despliegues.

No confunda definitions con backup de mensajes.

---

# Módulo 18. Monitorización y observabilidad

Un broker no debe operarse “a ciegas”.

## 18.1 Señales esenciales

Monitorice:

- conexiones;
- channels;
- consumers;
- publish rate;
- deliver rate;
- ack rate;
- mensajes ready;
- mensajes unacknowledged;
- memoria;
- disco;
- file descriptors;
- alarms;
- nodos;
- replicas;
- latencia de consumidores;
- errores de conexión.

## 18.2 Ready vs Unacked

### Ready

Mensajes esperando ser entregados.

Si crece constantemente:

```text
entrada > procesamiento
```

### Unacked

Mensajes entregados pero no confirmados.

Si crece:

- consumidores lentos;
- prefetch alto;
- bloqueos;
- problemas de ack;
- trabajos excesivamente largos.

## 18.3 Management UI

Es excelente para:

- desarrollo;
- inspección;
- troubleshooting.

No es la opción recomendada como almacenamiento histórico principal de métricas.

## 18.4 Prometheus

RabbitMQ incluye plugin Prometheus.

Habilitar:

```bash
docker exec rabbitmq-course \
  rabbitmq-plugins enable rabbitmq_prometheus
```

Métricas:

```text
http://localhost:15692/metrics
```

Comprobar:

```bash
curl http://localhost:15692/metrics
```

RabbitMQ recomienda Prometheus/Grafana para monitorización de producción.

## 18.5 Métricas de aplicación

No basta con mirar RabbitMQ.

El productor debe medir:

- publicaciones;
- confirms;
- nacks;
- errores;
- tiempo de publicación.

El consumidor:

- mensajes procesados;
- fallos;
- retries;
- DLQ;
- tiempo de procesamiento;
- redeliveries.

## 18.6 Correlation ID

Propague identificadores:

```text
trace_id
correlation_id
message_id
causation_id
```

Ejemplo:

```json
{
  "message_id": "evt-1",
  "correlation_id": "order-100",
  "causation_id": "cmd-88"
}
```

Facilita seguir un flujo distribuido.

---

# Módulo 19. Clustering y alta disponibilidad

## 19.1 Cluster

Un cluster contiene múltiples nodos RabbitMQ.

No significa automáticamente que cada queue esté replicada.

La estrategia de queue importa.

## 19.2 RabbitMQ 4.3 y Raft

RabbitMQ 4.3 utiliza **Khepri** como único almacén de metadatos.

Los componentes replicados clave se apoyan en Raft:

- Khepri;
- Quorum Queues;
- coordinadores de Streams.

Las antiguas estrategias de partición asociadas a Mnesia ya no son el modelo de operación de RabbitMQ 4.3.

## 19.3 Quorum

En un grupo de tres miembros:

```text
N1
N2
N3
```

la mayoría es:

```text
2 de 3
```

Puede tolerarse la pérdida de un miembro manteniendo mayoría.

Con cinco:

```text
3 de 5
```

pueden perderse hasta dos para mantener mayoría.

## 19.4 Consistencia vs disponibilidad

Cuando no existe mayoría, una estructura basada en consenso puede preferir dejar de aceptar ciertas operaciones antes que aceptar estados inconsistentes.

Esta decisión es fundamental en sistemas distribuidos.

## 19.5 Clustering no es disaster recovery

Un cluster local no sustituye:

- backup;
- recuperación ante desastre;
- multi-region bien diseñada;
- planes de continuidad;
- pruebas de restore.

## Laboratorio conceptual

Diseñe un cluster de tres nodos y responda:

1. ¿Qué queue debe ser Quorum?
2. ¿Qué pasa si cae un nodo?
3. ¿Qué pasa si caen dos?
4. ¿Dónde está el almacenamiento?
5. ¿Cómo se conectan los clientes?
6. ¿Qué monitoriza el balanceador?
7. ¿Cómo se manejan los upgrades?

---

# Módulo 20. Rendimiento y dimensionamiento

## 20.1 Variables

El rendimiento depende de:

- tamaño del mensaje;
- tasa de publicación;
- tasa de consumo;
- persistencia;
- tipo de queue;
- publisher confirms;
- número de bindings;
- prefetch;
- CPU;
- memoria;
- velocidad de disco;
- replicación;
- latencia de red;
- patrón de consumidor.

## 20.2 Throughput

```text
messages / second
```

Pero no use solo esta métrica.

También importa:

```text
MB/s
latencia p50
latencia p95
latencia p99
backlog
```

## 20.3 Tamaño del mensaje

Mensajes muy grandes:

- consumen memoria;
- aumentan I/O;
- incrementan latencia;
- reducen throughput;
- agravan reintentos.

Para objetos grandes considere:

```text
RabbitMQ -> referencia/URL/ID
Object Storage -> contenido
```

en vez de transportar binarios enormes.

## 20.4 Backlog

Capacidad aproximada:

```text
backlog_growth = publish_rate - consume_rate
```

Si:

```text
publish = 5,000 msg/s
consume = 4,000 msg/s
```

el backlog crece:

```text
1,000 msg/s
```

En una hora:

```text
3,600,000 mensajes
```

## 20.5 Little's Law

Como aproximación:

```text
L = λW
```

donde:

- `L` = trabajos en sistema;
- `λ` = tasa de llegada;
- `W` = tiempo promedio.

Es útil para razonar sobre concurrencia y latencia.

## 20.6 Benchmarking

No mida solo “mensajes pequeños en localhost”.

Pruebe:

- tamaño real;
- confirmaciones reales;
- tipo de queue real;
- número real de bindings;
- persistencia;
- red;
- consumidores;
- fallo de nodos;
- recuperación.

---

# Módulo 21. Pruebas, diagnóstico y resolución de problemas

## 21.1 Fallos a probar

- consumidor termina antes del ack;
- broker reinicia;
- mensaje no enrutable;
- productor pierde conexión;
- consumidor pierde conexión;
- payload inválido;
- downstream lento;
- DLQ crece;
- disco casi lleno;
- memoria bajo presión;
- nodo de cluster cae.

## 21.2 Mensajes acumulados

Síntoma:

```text
messages_ready aumenta
```

Preguntas:

1. ¿Hay consumidores?
2. ¿Están activos?
3. ¿Procesan más lento que la entrada?
4. ¿Están bloqueados?
5. ¿Hay errores downstream?
6. ¿El prefetch es razonable?

## 21.3 Muchos unacked

```text
messages_unacknowledged alto
```

Revise:

- prefetch;
- tareas demasiado largas;
- deadlocks;
- consumidor sin ack;
- concurrencia interna.

## 21.4 Mensajes desaparecen

Revise:

- `auto_ack`;
- queue no durable;
- mensaje no persistente;
- unroutable;
- exchange/binding incorrecto;
- TTL;
- DLX;
- límites de queue;
- publicación sin confirms.

## 21.5 Duplicados

No asuma que RabbitMQ está “mal”.

Puede ser una consecuencia normal de *at-least-once*.

Revise:

- ack después de efectos de negocio;
- caídas entre commit y ack;
- reconexiones;
- publisher retry;
- outbox;
- idempotencia.

## 21.6 Comandos útiles

```bash
rabbitmq-diagnostics ping
rabbitmq-diagnostics status
rabbitmqctl list_queues
rabbitmqctl list_exchanges
rabbitmqctl list_bindings
rabbitmqctl list_connections
rabbitmqctl list_channels
rabbitmqctl list_consumers
```

---

# Módulo 22. Patrones de arquitectura y buenas prácticas

## 22.1 Commands vs Events

### Command

Expresa intención:

```text
GenerateInvoice
ChargePayment
SendEmail
```

Normalmente existe un destinatario lógico.

### Event

Expresa un hecho:

```text
InvoiceGenerated
PaymentCharged
EmailSent
```

Puede interesar a múltiples consumidores.

No mezcle semánticas indiscriminadamente.

## 22.2 Naming

Ejemplo consistente:

Exchanges:

```text
ecommerce.events
billing.events
notifications.commands
```

Queues:

```text
inventory.order-created.v1
email.order-created.v1
analytics.all-events.v1
```

Routing keys:

```text
order.created
order.cancelled
payment.completed
inventory.stock.low
```

## 22.3 Versionado

Evite romper consumidores.

Opciones:

- versionar payload;
- campos opcionales;
- evolución compatible;
- routing key versionada en cambios mayores;
- Schema Registry externo si el ecosistema lo requiere.

Ejemplo:

```json
{
  "schema_version": 2,
  "event_id": "evt-1",
  "type": "order.created",
  "payload": {}
}
```

## 22.4 Mensajes autocontenidos

Incluya suficiente contexto para:

- validar;
- rastrear;
- deduplicar;
- procesar.

Evite mensajes ambiguos como:

```json
{
  "id": 18
}
```

sin tipo, versión ni correlación.

## 22.5 No usar RabbitMQ como cron universal

Para tareas programadas complejas puede convenir:

- scheduler;
- workflow engine;
- job system específico.

RabbitMQ puede participar, pero no debe forzarse a resolver toda necesidad temporal.

## 22.6 No hacer “chatty messaging”

Evite transformar cada llamada de función en un mensaje.

La mensajería debe representar límites útiles:

- eventos de dominio;
- trabajos asíncronos;
- integración;
- comandos distribuidos;
- streams.

## 22.7 Evitar queues sin dueño

Cada queue debería tener:

- propósito;
- owner;
- consumidor esperado;
- política de retención;
- DLQ;
- alertas;
- documentación.

## 22.8 Backpressure

Si un downstream soporta:

```text
100 req/s
```

no tiene sentido que 50 consumidores generen:

```text
5,000 req/s
```

RabbitMQ ayuda a bufferizar, pero no elimina el límite real.

Implemente:

- concurrency limit;
- rate limit;
- prefetch adecuado;
- circuit breaker cuando aplique;
- delayed retry;
- pausa controlada de consumidores.

---

# Proyecto integrador

## Sistema: procesamiento de pedidos de comercio electrónico

Construirá una arquitectura:

```mermaid
flowchart LR
    API[Orders API] --> OE[orders.events]
    OE -->|order.created| IQ[inventory.order-created]
    OE -->|order.created| EQ[email.order-created]
    OE -->|#| AQ[analytics.events]

    IQ --> IW[Inventory Worker]
    EQ --> EW[Email Worker]
    AQ --> AW[Analytics Worker]

    IW --> DLX[orders.dlx]
    DLX --> DLQ[orders.dead]
```

## Requisitos

### Productor

Debe:

- publicar JSON;
- utilizar `message_id`;
- incluir `correlation_id`;
- publicar con persistencia;
- utilizar Publisher Confirms;
- usar `mandatory=True`.

### Exchange

```text
orders.events
tipo: topic
durable: true
```

### Inventory

Queue:

```text
inventory.order-created
```

Debe:

- ser Quorum Queue;
- usar ack manual;
- utilizar prefetch;
- simular fallos;
- impedir duplicados mediante `event_id`.

### Email

Queue:

```text
email.order-created
```

Debe:

- recibir `order.created`;
- ejecutar consumo independiente;
- utilizar ack manual.

### Analytics

Queue:

```text
analytics.events
```

Binding:

```text
#
```

### DLQ

Debe:

- recibir fallos permanentes;
- conservar información de diagnóstico;
- generar métrica o log.

## Payload

```json
{
  "schema_version": 1,
  "event_id": "0259ef14-7328-46bd-95ea-a66f5bc59073",
  "type": "order.created",
  "occurred_at": "2026-08-28T20:00:00Z",
  "correlation_id": "order-1001",
  "payload": {
    "order_id": 1001,
    "customer_id": 50,
    "items": [
      {
        "sku": "ABC-01",
        "quantity": 2
      }
    ]
  }
}
```

## Entregables

```text
project/
├── docker-compose.yml
├── README.md
├── requirements.txt
├── producer/
│   └── app.py
├── inventory_worker/
│   └── app.py
├── email_worker/
│   └── app.py
├── analytics_worker/
│   └── app.py
└── tests/
```

## Casos de prueba

1. Pedido normal.
2. Dos consumidores Inventory.
3. Worker termina antes del ack.
4. Mensaje duplicado.
5. JSON inválido.
6. Error transitorio.
7. Error permanente.
8. Exchange sin binding esperado.
9. Reinicio de RabbitMQ.
10. Reinicio de consumidor.
11. Acumulación temporal de backlog.
12. Recuperación de backlog.

## Criterios de aceptación

El proyecto debe demostrar:

- desacoplamiento;
- routing correcto;
- confirms;
- ack manual;
- idempotencia;
- DLQ;
- retries controlados;
- observabilidad;
- documentación.

---

# Evaluación sugerida

| Evidencia | Ponderación |
|---|---:|
| Ejercicios de módulos 1–5 | 10% |
| Work Queues, acks y prefetch | 10% |
| Exchanges y routing | 10% |
| Publisher Confirms | 10% |
| DLX y retries | 10% |
| Quorum Queues y Streams | 10% |
| Seguridad y administración | 10% |
| Observabilidad | 10% |
| Proyecto integrador | 20% |

## Rúbrica del proyecto

### Excelente

- topología correcta;
- código claro;
- idempotencia real;
- confirms;
- ack manual;
- retries limitados;
- DLQ operativa;
- logs correlacionados;
- documentación reproducible;
- pruebas de fallos.

### Satisfactorio

- topología funcional;
- manejo básico de errores;
- persistencia;
- algunos mecanismos de seguridad y observabilidad.

### Insuficiente

- auto-ack sin justificación;
- requeue infinito;
- sin idempotencia;
- sin manejo de mensajes no enrutables;
- sin DLQ;
- topología no documentada.

---

# Checklist para producción

## Aplicación productora

- [ ] Reutiliza conexiones.
- [ ] Maneja reconexión.
- [ ] Usa Publisher Confirms cuando la pérdida importa.
- [ ] Maneja mensajes no enrutables.
- [ ] Incluye `message_id`.
- [ ] Incluye `correlation_id`.
- [ ] Tiene timeout y manejo de errores.
- [ ] No publica payloads innecesariamente grandes.
- [ ] Usa Outbox si debe coordinar DB + publicación crítica.

## Consumidor

- [ ] Usa ack manual cuando corresponde.
- [ ] Es idempotente.
- [ ] Distingue error transitorio y permanente.
- [ ] Tiene retries limitados.
- [ ] Tiene DLQ.
- [ ] Tiene prefetch revisado con pruebas.
- [ ] Tiene límites de concurrencia.
- [ ] Propaga trazas/correlación.
- [ ] No hace requeue infinito.

## Broker

- [ ] Versión soportada.
- [ ] Configuración reproducible.
- [ ] Disco dimensionado.
- [ ] Memoria dimensionada.
- [ ] Quorum Queues donde la criticidad lo exige.
- [ ] Políticas documentadas.
- [ ] Backups y restore probados.
- [ ] Estrategia de upgrades.
- [ ] TLS.
- [ ] Credenciales rotables.
- [ ] Least privilege.
- [ ] Prometheus/Grafana.
- [ ] Alertas de disk/memory alarms.
- [ ] Alertas de backlog.
- [ ] Alertas de DLQ.
- [ ] Métricas de publishers y consumers.

## Arquitectura

- [ ] Commands y Events tienen semántica clara.
- [ ] Existe ownership de queues.
- [ ] Existe estrategia de versionado.
- [ ] Existe política de retención.
- [ ] Existe plan de replay cuando aplica.
- [ ] Existe estrategia de disaster recovery.
- [ ] Se documentaron garantías reales y no supuestas.

---

# Glosario

**ACK**  
Confirmación enviada por el consumidor para indicar procesamiento satisfactorio.

**AMQP**  
Advanced Message Queuing Protocol.

**Binding**  
Regla que relaciona exchange con queue o stream.

**Broker**  
Servidor intermediario encargado de recibir, enrutar y entregar mensajes.

**Channel**  
Conexión lógica dentro de una conexión AMQP.

**Consumer**  
Aplicación o suscripción que recibe mensajes.

**Dead Letter**  
Mensaje que ya no sigue su flujo normal y es redirigido según configuración.

**DLQ**  
Dead Letter Queue.

**DLX**  
Dead Letter Exchange.

**Durable**  
Propiedad que permite que una entidad sobreviva reinicios, dentro de la semántica correspondiente.

**Exchange**  
Entidad que recibe publicaciones y ejecuta routing.

**Fanout**  
Exchange que distribuye a todos sus bindings.

**Idempotencia**  
Propiedad por la que repetir una operación no cambia el resultado efectivo después de la primera aplicación válida.

**Message Broker**  
Sistema intermediario de mensajería.

**NACK**  
Confirmación negativa.

**Outbox Pattern**  
Patrón para coordinar de forma confiable cambios en DB y publicación de mensajes.

**Prefetch**  
Límite de mensajes no confirmados que se entregan por adelantado a un consumidor.

**Producer / Publisher**  
Aplicación que publica mensajes.

**Publisher Confirm**  
Mecanismo mediante el cual RabbitMQ confirma al publisher la aceptación de una publicación.

**Queue**  
Estructura desde la que se entregan mensajes a consumidores.

**Quorum Queue**  
Queue replicada basada en Raft.

**RabbitMQ**  
Broker de mensajería open source.

**Routing Key**  
Clave usada por exchanges para el enrutamiento.

**Stream**  
Log persistente y replicado con consumo no destructivo.

**Topic Exchange**  
Exchange que enruta mediante patrones jerárquicos.

**TTL**  
Time To Live.

**Virtual Host**  
Espacio lógico que agrupa y separa recursos RabbitMQ.

---

# Ruta de aprendizaje recomendada

## Fase 1 — Fundamentos

Complete:

```text
Módulos 1–7
```

Meta:

- productores;
- consumidores;
- exchanges;
- queues;
- routing;
- ack;
- prefetch.

## Fase 2 — Confiabilidad

Complete:

```text
Módulos 8–11
```

Meta:

- durabilidad;
- confirms;
- DLX;
- retries;
- idempotencia;
- orden.

## Fase 3 — Intermedio

Complete:

```text
Módulos 12–15
```

Meta:

- Quorum;
- Streams;
- patrones;
- async;
- FastAPI.

## Fase 4 — Producción

Complete:

```text
Módulos 16–22
```

Meta:

- seguridad;
- administración;
- observabilidad;
- clustering;
- rendimiento;
- troubleshooting;
- arquitectura.

---

# Prácticas adicionales

## Práctica A — Sistema de notificaciones

Eventos:

```text
user.created
password.reset.requested
invoice.generated
```

Servicios:

```text
email
sms
push
audit
```

Diseñe exchanges, queues y bindings.

## Práctica B — Procesamiento de imágenes

```text
API
 -> image.jobs
 -> resize worker
 -> metadata worker
```

Preguntas:

- ¿Queue compartida o queues separadas?
- ¿Qué ocurre si un procesamiento tarda 10 minutos?
- ¿Qué prefetch usaría?
- ¿Cómo detectaría poison messages?

## Práctica C — Auditoría

Todos los eventos:

```text
#
```

deben llegar a una queue de auditoría.

Determine:

- retención;
- almacenamiento;
- replay;
- si una Stream sería mejor.

## Práctica D — Carga

Publique:

```text
10,000
100,000
1,000,000
```

mensajes controlados.

Mida:

- publish rate;
- consume rate;
- backlog;
- memoria;
- CPU;
- latencia.

Nunca haga pruebas de carga sobre producción sin autorización.

---

# Preguntas de repaso

1. ¿Cuál es la función de un exchange?
2. ¿En qué se diferencia una queue de un exchange?
3. ¿Qué es un binding?
4. ¿Qué diferencia existe entre `direct` y `topic`?
5. ¿Por qué `fanout` sirve para Pub/Sub?
6. ¿Qué riesgo tiene `auto_ack=True`?
7. ¿Qué problema evita prefetch?
8. ¿Por qué puede haber duplicados?
9. ¿Qué significa idempotencia?
10. ¿Qué problema resuelve Outbox?
11. ¿Qué es un DLX?
12. ¿Qué diferencia hay entre retry y requeue?
13. ¿Por qué un requeue infinito es peligroso?
14. ¿Qué confirma Publisher Confirm?
15. ¿Qué hace `mandatory=True`?
16. ¿Cuándo elegir Quorum Queue?
17. ¿Cuándo elegir Stream?
18. ¿Qué significa consumo no destructivo?
19. ¿Qué es un vhost?
20. ¿Qué permisos separa RabbitMQ?
21. ¿Por qué TLS es necesario?
22. ¿Qué diferencia existe entre ready y unacked?
23. ¿Por qué clustering no implica que toda queue esté replicada?
24. ¿Qué papel juega Raft en RabbitMQ moderno?
25. ¿Por qué exactamente una vez no debe asumirse?
26. ¿Cómo se prueba la resiliencia de un consumidor?
27. ¿Qué métricas deben tener las aplicaciones?
28. ¿Cómo se identifica un poison message?
29. ¿Cómo se diseña un esquema de eventos evolutivo?
30. ¿Cuál es la diferencia semántica entre command y event?

---

# Respuestas breves de repaso

1. Enrutar publicaciones.
2. El exchange enruta; la queue almacena/entrega.
3. Regla de relación entre entidades.
4. Direct usa coincidencia exacta; topic usa patrones.
5. Duplica el flujo hacia todas las queues vinculadas.
6. Pérdida lógica si el consumidor falla durante procesamiento.
7. Controla entregas no confirmadas en vuelo.
8. Por fallos entre efectos de negocio y confirmación, entre otras causas.
9. Poder repetir sin multiplicar el efecto de negocio.
10. Coordinar DB y publicación confiable.
11. Exchange al que se dead-letterean mensajes.
12. Retry es estrategia; requeue es una operación concreta.
13. Puede generar loops de alta carga.
14. Que RabbitMQ ha aceptado responsabilidad según la semántica del tipo de destino.
15. Solicita retorno cuando no existe destino enrutable.
16. Mensajes críticos y queue replicada.
17. Replay, alto throughput, fan-out y log.
18. Leer no elimina automáticamente el registro del stream.
19. Aislamiento lógico de recursos.
20. Configure, write y read.
21. Protege tráfico y credenciales.
22. Ready espera entrega; unacked ya fue entregado y espera confirmación.
23. La replicación depende del tipo de estructura.
24. Consenso y replicación en componentes clave.
25. Los fallos distribuidos pueden producir ambigüedad y repetición.
26. Inyectando fallos reales controlados.
27. Éxitos, errores, latencia, confirms, retries, redelivery y DLQ.
28. Falla repetidamente por una causa permanente.
29. Versionado y evolución compatible.
30. Command expresa intención; event expresa un hecho.

---

# Referencias oficiales

Este curso se basa prioritariamente en documentación oficial de RabbitMQ.

## Documentación principal

- RabbitMQ 4.3 Documentation  
  https://www.rabbitmq.com/docs

- RabbitMQ Tutorials  
  https://www.rabbitmq.com/tutorials

- How to Use RabbitMQ  
  https://www.rabbitmq.com/docs/use-rabbitmq

- Production Deployment Guidelines  
  https://www.rabbitmq.com/docs/production-checklist

## Conceptos de desarrollo

- Publishers  
  https://www.rabbitmq.com/docs/publishers

- Consumers  
  https://www.rabbitmq.com/docs/consumers

- Consumer Acknowledgements and Publisher Confirms  
  https://www.rabbitmq.com/docs/confirms

- Exchanges  
  https://www.rabbitmq.com/docs/exchanges

- Queues  
  https://www.rabbitmq.com/docs/queues

- Dead Letter Exchanges  
  https://www.rabbitmq.com/docs/dlx

- Time-To-Live and Expiration  
  https://www.rabbitmq.com/docs/ttl

## Tipos de almacenamiento

- Quorum Queues  
  https://www.rabbitmq.com/docs/quorum-queues

- Streams and Super Streams  
  https://www.rabbitmq.com/docs/streams

- Stream Plugin  
  https://www.rabbitmq.com/docs/stream

## Operación

- Management Plugin  
  https://www.rabbitmq.com/docs/management

- Monitoring  
  https://www.rabbitmq.com/docs/monitoring

- Virtual Hosts  
  https://www.rabbitmq.com/docs/vhosts

- Authentication, Authorisation, Access Control  
  https://www.rabbitmq.com/docs/access-control

- TLS Support  
  https://www.rabbitmq.com/docs/ssl

- Clustering and Network Partitions  
  https://www.rabbitmq.com/docs/partitions

- Manual Pages  
  https://www.rabbitmq.com/docs/manpages

## RabbitMQ 4.3

- RabbitMQ 4.3 Highlights, 23 de abril de 2026  
  https://www.rabbitmq.com/blog/2026/04/23/rabbitmq-4.3-release

---

# Nota de actualización tecnológica

Este material fue preparado para **RabbitMQ 4.x** y revisado contra la documentación de **RabbitMQ 4.3.5** disponible en agosto de 2026.

Aspectos especialmente importantes del RabbitMQ moderno:

1. Las **Classic Mirrored Queues** fueron retiradas a partir de RabbitMQ 4.0.
2. Las **Quorum Queues** son la opción principal cuando se necesita una queue replicada y con alta seguridad de datos.
3. **Streams** proporcionan semántica de log persistente y consumo no destructivo.
4. RabbitMQ 4.3 utiliza **Khepri** como único almacén de metadatos.
5. RabbitMQ 4.3 incorpora mejoras relevantes en Quorum Queues, incluyendo **Delayed Retries**, **Consumer Timeouts** y prioridades estrictas.
6. **Prometheus + Grafana** es el enfoque recomendado por RabbitMQ para monitorización de producción.

Antes de desplegar una solución real, revise siempre la documentación correspondiente a la versión exacta que utilizará.

---

# Fin del curso

Una secuencia efectiva para dominar RabbitMQ es:

```text
comprender
-> implementar
-> romper
-> observar
-> recuperar
-> medir
-> rediseñar
```

La competencia real no consiste solo en poder publicar y consumir mensajes, sino en diseñar qué ocurrirá cuando:

- una red falle;
- un consumidor se duplique;
- un mensaje llegue dos veces;
- una base de datos no responda;
- un nodo se reinicie;
- una queue crezca;
- una publicación no sea enrutable;
- un mensaje sea venenoso;
- un servicio cambie de versión.

Ese es el punto en el que RabbitMQ deja de ser únicamente una biblioteca de mensajería y se convierte en una pieza bien comprendida de una arquitectura distribuida.
