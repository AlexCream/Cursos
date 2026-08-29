# Curso Profesional de FastAPI: Fundamentos e Intermedio

> **Modalidad:** teórico-práctica  
> **Nivel:** fundamentos → intermedio  
> **Lenguaje principal:** Python  
> **Enfoque:** desarrollo profesional de APIs REST, persistencia, seguridad, pruebas, asincronía, arquitectura y despliegue  
> **Actualización de contenidos:** agosto de 2026  
> **Duración sugerida:** 60–80 horas  
> **Proyecto integrador:** API de gestión comercial con usuarios, productos y pedidos

---

## Índice

1. [Presentación del curso](#1-presentación-del-curso)
2. [Objetivos de aprendizaje](#2-objetivos-de-aprendizaje)
3. [Perfil de ingreso y requisitos](#3-perfil-de-ingreso-y-requisitos)
4. [Metodología de trabajo](#4-metodología-de-trabajo)
5. [Tecnologías del curso](#5-tecnologías-del-curso)
6. [Módulo 0. Fundamentos de APIs, HTTP, REST y ASGI](#módulo-0-fundamentos-de-apis-http-rest-y-asgi)
7. [Módulo 1. Python moderno para FastAPI](#módulo-1-python-moderno-para-fastapi)
8. [Módulo 2. Primer proyecto con FastAPI](#módulo-2-primer-proyecto-con-fastapi)
9. [Módulo 3. Rutas, parámetros y solicitudes HTTP](#módulo-3-rutas-parámetros-y-solicitudes-http)
10. [Módulo 4. Pydantic y validación de datos](#módulo-4-pydantic-y-validación-de-datos)
11. [Módulo 5. Respuestas, errores y diseño de contratos](#módulo-5-respuestas-errores-y-diseño-de-contratos)
12. [Módulo 6. Inyección de dependencias](#módulo-6-inyección-de-dependencias)
13. [Módulo 7. Persistencia con SQLAlchemy 2.x](#módulo-7-persistencia-con-sqlalchemy-2x)
14. [Módulo 8. PostgreSQL, migraciones con Alembic y capas de acceso](#módulo-8-postgresql-migraciones-con-alembic-y-capas-de-acceso)
15. [Módulo 9. Autenticación, autorización y seguridad](#módulo-9-autenticación-autorización-y-seguridad)
16. [Módulo 10. Asincronía, concurrencia y servicios externos](#módulo-10-asincronía-concurrencia-y-servicios-externos)
17. [Módulo 11. Middleware, CORS, archivos y tareas en segundo plano](#módulo-11-middleware-cors-archivos-y-tareas-en-segundo-plano)
18. [Módulo 12. WebSockets y comunicación en tiempo real](#módulo-12-websockets-y-comunicación-en-tiempo-real)
19. [Módulo 13. Pruebas automatizadas](#módulo-13-pruebas-automatizadas)
20. [Módulo 14. Configuración, logging y observabilidad](#módulo-14-configuración-logging-y-observabilidad)
21. [Módulo 15. Arquitectura intermedia y buenas prácticas](#módulo-15-arquitectura-intermedia-y-buenas-prácticas)
22. [Módulo 16. Docker, despliegue y operación](#módulo-16-docker-despliegue-y-operación)
23. [Proyecto integrador](#proyecto-integrador)
24. [Evaluación sugerida](#evaluación-sugerida)
25. [Ruta de estudio](#ruta-de-estudio)
26. [Errores frecuentes y diagnóstico](#errores-frecuentes-y-diagnóstico)
27. [Checklist de una API lista para producción](#checklist-de-una-api-lista-para-producción)
28. [Glosario](#glosario)
29. [Referencias oficiales](#referencias-oficiales)

---

# 1. Presentación del curso

FastAPI es un framework moderno de Python orientado a la creación de APIs web. Aprovecha el sistema de tipos de Python para definir contratos de entrada y salida, validación, documentación OpenAPI e inyección de dependencias.

Este curso está diseñado para llevar a una persona que conoce los fundamentos de programación en Python desde una API mínima hasta una aplicación organizada, persistente, segura, probada y desplegable.

El curso no se limita a aprender decoradores como `@app.get()` o `@app.post()`. Su objetivo es comprender el ecosistema necesario para desarrollar servicios backend mantenibles:

- HTTP y REST.
- Python moderno y type hints.
- FastAPI.
- Pydantic.
- OpenAPI.
- SQLAlchemy.
- PostgreSQL.
- Alembic.
- OAuth2 y JWT.
- Hashing seguro de contraseñas.
- `async` / `await`.
- Pruebas con `pytest` y `httpx`.
- Docker.
- Configuración y logging.
- Diseño por capas.
- Principios básicos de operación en producción.

> **Idea central:** aprender FastAPI es aprender a construir un servicio HTTP completo, no solamente a escribir endpoints.

---

# 2. Objetivos de aprendizaje

## Objetivo general

Desarrollar APIs profesionales con FastAPI aplicando fundamentos de HTTP, validación tipada, persistencia relacional, seguridad, pruebas automatizadas, asincronía, arquitectura modular y despliegue.

## Al finalizar el nivel fundamentos, el estudiante podrá

- Explicar qué es una API y cómo funciona HTTP.
- Crear y ejecutar aplicaciones FastAPI.
- Diseñar endpoints REST.
- Utilizar parámetros de ruta, query, headers y cuerpos JSON.
- Validar información con Pydantic.
- Definir modelos de respuesta.
- Manejar errores HTTP.
- Utilizar documentación automática OpenAPI.
- Organizar una aplicación con `APIRouter`.
- Aplicar inyección de dependencias.

## Al finalizar el nivel intermedio, el estudiante podrá

- Integrar FastAPI con PostgreSQL y SQLAlchemy 2.x.
- Gestionar migraciones mediante Alembic.
- Implementar autenticación con OAuth2/Bearer/JWT.
- Aplicar autorización basada en roles o permisos.
- Comprender cuándo usar código síncrono y asíncrono.
- Consumir servicios HTTP externos.
- Crear tareas en segundo plano.
- Implementar middleware y CORS.
- Crear WebSockets básicos.
- Diseñar suites de pruebas con `pytest`.
- Administrar configuración mediante variables de entorno.
- Contenerizar una aplicación con Docker.
- Estructurar una aplicación mediante capas.
- Preparar un servicio para entornos de producción.

---

# 3. Perfil de ingreso y requisitos

## Conocimientos mínimos

Se recomienda conocer:

- Variables y tipos básicos.
- Condicionales y ciclos.
- Funciones.
- Listas y diccionarios.
- Módulos y paquetes.
- Clases.
- Excepciones.
- Uso básico de terminal.

## Software

Recomendado:

- Python 3.12 o superior.
- Git.
- Visual Studio Code, PyCharm o editor equivalente.
- PostgreSQL.
- Docker Desktop o Docker Engine.
- `curl`, Bruno, Insomnia o Postman para probar APIs.
- `uv` como gestor de proyecto y dependencias.

FastAPI admite versiones de Python anteriores a 3.12, pero para un curso nuevo resulta conveniente trabajar con sintaxis moderna.

---

# 4. Metodología de trabajo

Cada módulo se divide en:

1. **Objetivos.**
2. **Teoría esencial.**
3. **Ejemplos de código.**
4. **Práctica guiada.**
5. **Ejercicios.**
6. **Entregable.**
7. **Preguntas de revisión.**

Se recomienda utilizar Git desde el inicio:

```bash
git init
git add .
git commit -m "chore: initialize FastAPI course project"
```

Convención sugerida para commits:

```text
feat: nueva funcionalidad
fix: corrección
refactor: reorganización sin cambio funcional
test: pruebas
docs: documentación
chore: tareas de mantenimiento
```

---

# 5. Tecnologías del curso

| Tecnología | Propósito |
|---|---|
| Python | Lenguaje |
| FastAPI | Framework web |
| Starlette | Base ASGI utilizada por FastAPI |
| Pydantic | Validación y serialización |
| Uvicorn | Servidor ASGI |
| OpenAPI | Especificación del contrato HTTP |
| SQLAlchemy 2.x | ORM y toolkit SQL |
| PostgreSQL | Base de datos relacional |
| Alembic | Migraciones |
| PyJWT | Creación y validación de JWT |
| pwdlib + Argon2 | Hashing de contraseñas |
| pytest | Framework de pruebas |
| HTTPX | Cliente HTTP y apoyo para pruebas |
| Docker | Contenedores |
| Git | Control de versiones |

---

# Módulo 0. Fundamentos de APIs, HTTP, REST y ASGI

**Nivel:** fundamentos  
**Duración sugerida:** 3–4 horas

## Objetivos

- Comprender la función de una API.
- Comprender cliente, servidor, request y response.
- Manejar los conceptos principales de HTTP.
- Diferenciar REST, OpenAPI y ASGI.

## 0.1 ¿Qué es una API?

Una API —Application Programming Interface— define una forma controlada de interacción entre componentes de software.

En una API web normalmente tenemos:

```text
Cliente
   |
   | HTTP Request
   v
API / Servidor
   |
   | lógica + datos
   v
Base de datos / servicios
   |
   | HTTP Response
   v
Cliente
```

Ejemplos de clientes:

- Aplicación web.
- Aplicación móvil.
- Otro backend.
- Script Python.
- Dispositivo IoT.
- Herramienta de análisis de datos.

## 0.2 Anatomía de una solicitud HTTP

Una petición contiene, según el caso:

- Método.
- URL.
- Ruta.
- Query string.
- Headers.
- Cookies.
- Body.

Ejemplo conceptual:

```http
POST /api/v1/products?notify=true HTTP/1.1
Host: api.example.com
Content-Type: application/json
Authorization: Bearer <token>

{
  "name": "Laptop",
  "price": 25000
}
```

## 0.3 Métodos HTTP

| Método | Uso típico | Idempotente |
|---|---|---|
| GET | Consultar | Sí |
| POST | Crear/procesar | Generalmente no |
| PUT | Reemplazar | Sí |
| PATCH | Modificar parcialmente | Depende del diseño |
| DELETE | Eliminar | Conceptualmente sí |

## 0.4 Códigos de estado importantes

### 2xx — éxito

- `200 OK`
- `201 Created`
- `202 Accepted`
- `204 No Content`

### 4xx — error del cliente

- `400 Bad Request`
- `401 Unauthorized`
- `403 Forbidden`
- `404 Not Found`
- `409 Conflict`
- `422 Unprocessable Content`
- `429 Too Many Requests`

### 5xx — error del servidor

- `500 Internal Server Error`
- `502 Bad Gateway`
- `503 Service Unavailable`

## 0.5 ¿Qué significa REST?

REST es un estilo arquitectónico. En APIs REST suele ser recomendable representar recursos mediante sustantivos:

```text
GET    /products
GET    /products/10
POST   /products
PATCH  /products/10
DELETE /products/10
```

Evitar, como regla general:

```text
GET /getProducts
POST /createProduct
POST /deleteProduct
```

No porque sean imposibles, sino porque desaprovechan la semántica de HTTP.

## 0.6 JSON

JSON es uno de los formatos más usados para APIs:

```json
{
  "id": 25,
  "name": "Teclado",
  "price": 1200.50,
  "active": true,
  "tags": ["usb", "periferico"]
}
```

## 0.7 OpenAPI

OpenAPI describe formalmente:

- Rutas.
- Operaciones.
- Parámetros.
- Esquemas.
- Respuestas.
- Seguridad.

FastAPI genera un esquema OpenAPI a partir del código y del tipado.

## 0.8 WSGI y ASGI

WSGI fue diseñado para aplicaciones web síncronas de Python.

ASGI soporta patrones modernos, incluidos:

- `async` / `await`.
- Conexiones de larga duración.
- WebSockets.

FastAPI es una aplicación ASGI. Uvicorn puede ejecutarla como servidor ASGI.

## Práctica guiada

Diseña en papel una API para una biblioteca:

```text
GET    /books
GET    /books/{book_id}
POST   /books
PATCH  /books/{book_id}
DELETE /books/{book_id}
```

Para cada endpoint define:

- Request esperado.
- Response.
- Código HTTP correcto.
- Posibles errores.

## Ejercicios

1. Diseña una API para cursos y estudiantes.
2. Explica la diferencia entre `401` y `403`.
3. Explica cuándo usarías `POST` y cuándo `PUT`.
4. Identifica recursos en un sistema de comercio electrónico.

## Entregable

Documento `api-design.md` con al menos 10 operaciones HTTP.

---

# Módulo 1. Python moderno para FastAPI

**Nivel:** fundamentos  
**Duración:** 4–5 horas

## Objetivos

- Reforzar type hints.
- Comprender `Annotated`.
- Trabajar con módulos y excepciones.
- Introducir `async` y `await`.

## 1.1 Type hints

```python
def calculate_total(price: float, quantity: int) -> float:
    return price * quantity
```

Tipos modernos:

```python
def find_user(user_id: int) -> dict[str, str] | None:
    ...
```

Colecciones:

```python
names: list[str] = []
scores: dict[str, float] = {}
```

## 1.2 `Annotated`

`Annotated` permite agregar metadatos a un tipo:

```python
from typing import Annotated

UserId = Annotated[int, "Identificador del usuario"]
```

FastAPI utiliza este mecanismo intensivamente:

```python
from typing import Annotated
from fastapi import Query

limit: Annotated[int, Query(ge=1, le=100)] = 20
```

## 1.3 Excepciones

```python
def divide(a: float, b: float) -> float:
    if b == 0:
        raise ValueError("b cannot be zero")
    return a / b
```

## 1.4 Módulos y paquetes

Estructura:

```text
app/
├── __init__.py
├── main.py
├── models.py
└── services.py
```

Importación:

```python
from app.services import calculate_total
```

## 1.5 Comprensiones

```python
active_products = [
    product
    for product in products
    if product["active"]
]
```

## 1.6 `async` y `await`

Ejemplo:

```python
import asyncio

async def fetch_data() -> str:
    await asyncio.sleep(1)
    return "done"
```

`await` permite ceder el control mientras se espera una operación compatible con asincronía.

### Regla inicial

Usa `async def` cuando la cadena de operaciones I/O que invocas es asíncrona.

Usa `def` cuando trabajas con una biblioteca bloqueante y no tienes una razón específica para convertir la operación.

No conviertas todo a `async` de forma automática.

## Práctica

Crea:

```python
class Product:
    ...
```

y funciones tipadas para:

- Crear.
- Buscar.
- Calcular impuesto.
- Aplicar descuento.

## Ejercicio de revisión

Explica por qué el tipado es especialmente útil en FastAPI.

---

# Módulo 2. Primer proyecto con FastAPI

**Nivel:** fundamentos  
**Duración:** 4 horas

## Objetivos

- Crear un proyecto.
- Ejecutar FastAPI.
- Conocer Swagger UI y ReDoc.
- Comprender una path operation.

## 2.1 Crear proyecto con `uv`

```bash
uv init fastapi-course --bare
cd fastapi-course
uv add "fastapi[standard]"
```

Crear:

```text
fastapi-course/
├── pyproject.toml
└── main.py
```

## 2.2 Primera aplicación

```python
from fastapi import FastAPI

app = FastAPI(
    title="FastAPI Course API",
    version="1.0.0",
)

@app.get("/")
async def root():
    return {"message": "Hello FastAPI"}
```

Ejecutar:

```bash
uv run fastapi dev
```

De forma alternativa:

```bash
uv run uvicorn main:app --reload
```

## 2.3 Documentación automática

Por defecto:

```text
/docs
/redoc
/openapi.json
```

FastAPI utiliza el tipado y los modelos para producir el contrato OpenAPI.

## 2.4 Decoradores

```python
@app.get("/products")
async def list_products():
    ...
```

- `app`: instancia de `FastAPI`.
- `.get`: método HTTP.
- `"/products"`: ruta.
- Función: handler/path operation function.

## 2.5 CRUD temporal en memoria

```python
from fastapi import FastAPI, HTTPException

app = FastAPI()

products: dict[int, dict] = {
    1: {"id": 1, "name": "Keyboard", "price": 900.0}
}

@app.get("/products")
def list_products():
    return list(products.values())

@app.get("/products/{product_id}")
def get_product(product_id: int):
    product = products.get(product_id)

    if not product:
        raise HTTPException(
            status_code=404,
            detail="Product not found",
        )

    return product
```

## Práctica guiada

Agregar:

- `GET /health`
- `GET /products`
- `GET /products/{id}`

## Ejercicios

1. Crear `/about`.
2. Crear una colección de categorías.
3. Devolver `404` cuando no exista una categoría.
4. Revisar el esquema `/openapi.json`.

## Entregable

Primera API funcional versionada con Git.

---

# Módulo 3. Rutas, parámetros y solicitudes HTTP

**Nivel:** fundamentos  
**Duración:** 5 horas

## Objetivos

- Dominar parámetros de ruta.
- Utilizar query parameters.
- Leer headers y cookies.
- Recibir cuerpos JSON.
- Aplicar restricciones.

## 3.1 Path parameters

```python
@app.get("/products/{product_id}")
def get_product(product_id: int):
    return {"product_id": product_id}
```

Si el valor no puede validarse como entero, FastAPI devuelve automáticamente un error de validación.

## 3.2 Query parameters

```python
@app.get("/products")
def list_products(
    skip: int = 0,
    limit: int = 20,
    search: str | None = None,
):
    return {
        "skip": skip,
        "limit": limit,
        "search": search,
    }
```

Request:

```text
GET /products?skip=20&limit=10&search=keyboard
```

## 3.3 Restricciones con `Query`

```python
from typing import Annotated
from fastapi import Query

@app.get("/products")
def list_products(
    limit: Annotated[int, Query(ge=1, le=100)] = 20,
):
    return {"limit": limit}
```

## 3.4 `Path`

```python
from fastapi import Path

@app.get("/products/{product_id}")
def get_product(
    product_id: Annotated[int, Path(gt=0)],
):
    return {"id": product_id}
```

## 3.5 Headers

```python
from fastapi import Header

@app.get("/client")
def client_info(
    user_agent: Annotated[str | None, Header()] = None,
):
    return {"user_agent": user_agent}
```

## 3.6 Body

Los cuerpos complejos se modelan normalmente con Pydantic:

```python
from pydantic import BaseModel

class ProductCreate(BaseModel):
    name: str
    price: float
    stock: int = 0

@app.post("/products")
def create_product(product: ProductCreate):
    return product
```

## 3.7 Status codes

```python
from fastapi import status

@app.post(
    "/products",
    status_code=status.HTTP_201_CREATED,
)
def create_product(product: ProductCreate):
    return product
```

## 3.8 Diseño de paginación

Versión inicial:

```text
GET /products?offset=0&limit=20
```

Para proyectos mayores se pueden considerar:

- Offset/limit.
- Página/tamaño.
- Cursor.

## Práctica

Construir operaciones para productos con:

- filtro por nombre;
- precio mínimo;
- precio máximo;
- paginación;
- ordenamiento controlado.

## Reto

Diseñar:

```text
GET /products?min_price=100&max_price=5000&active=true&limit=20
```

Validar que:

- `limit` esté entre 1 y 100;
- precio mínimo no sea negativo.

---

# Módulo 4. Pydantic y validación de datos

**Nivel:** fundamentos → intermedio  
**Duración:** 5–6 horas

## Objetivos

- Crear esquemas.
- Validar datos.
- Diferenciar modelos de entrada y salida.
- Aplicar validadores.
- Evitar exponer campos privados.

## 4.1 `BaseModel`

```python
from pydantic import BaseModel

class ProductCreate(BaseModel):
    name: str
    description: str | None = None
    price: float
    stock: int = 0
```

## 4.2 `Field`

```python
from pydantic import BaseModel, Field

class ProductCreate(BaseModel):
    name: str = Field(min_length=2, max_length=120)
    price: float = Field(gt=0)
    stock: int = Field(default=0, ge=0)
```

## 4.3 Modelos separados

No reutilices siempre un único esquema.

```python
class ProductBase(BaseModel):
    name: str
    price: float

class ProductCreate(ProductBase):
    stock: int = 0

class ProductUpdate(BaseModel):
    name: str | None = None
    price: float | None = None
    stock: int | None = None

class ProductRead(ProductBase):
    id: int
    stock: int
```

Ventajas:

- Menor exposición accidental.
- Contratos más claros.
- Evolución más sencilla.
- Permisos por operación.

## 4.4 Tipos especiales

```python
from datetime import datetime
from uuid import UUID
from pydantic import BaseModel, EmailStr

class UserRead(BaseModel):
    id: UUID
    email: EmailStr
    created_at: datetime
```

## 4.5 Validadores

Pydantic v2:

```python
from pydantic import BaseModel, field_validator

class ProductCreate(BaseModel):
    name: str
    price: float

    @field_validator("name")
    @classmethod
    def normalize_name(cls, value: str) -> str:
        value = value.strip()

        if not value:
            raise ValueError("name cannot be empty")

        return value
```

## 4.6 Serialización

```python
product = ProductCreate(
    name="Mouse",
    price=500,
)

data = product.model_dump()
```

JSON:

```python
json_data = product.model_dump_json()
```

## 4.7 Validación a nivel de modelo

Cuando una regla depende de varios campos, utiliza validación de modelo.

Ejemplo conceptual:

```text
start_date <= end_date
min_price <= max_price
```

## 4.8 DTO, esquema y modelo ORM

No confundas:

```text
Pydantic model
    -> contrato/validación/serialización

SQLAlchemy model
    -> representación persistente

Domain entity
    -> concepto del dominio, si la arquitectura lo necesita
```

En proyectos pequeños pueden estar muy próximos. En proyectos complejos conviene separarlos.

## Práctica

Crear:

- `UserCreate`
- `UserRead`
- `ProductCreate`
- `ProductUpdate`
- `ProductRead`
- `OrderCreate`
- `OrderRead`

## Error intencional

Prueba:

```json
{
  "name": "",
  "price": -200,
  "stock": -5
}
```

Analiza la respuesta de validación de FastAPI.

---

# Módulo 5. Respuestas, errores y diseño de contratos

**Nivel:** fundamentos  
**Duración:** 4 horas

## Objetivos

- Controlar modelos de respuesta.
- Elegir status codes.
- Crear errores consistentes.
- Comprender filtrado de respuesta.

## 5.1 `response_model`

```python
@app.post(
    "/products",
    response_model=ProductRead,
    status_code=201,
)
def create_product(product: ProductCreate):
    ...
```

FastAPI puede validar y filtrar la salida de acuerdo con el modelo declarado.

## 5.2 Evitar fuga de información

Incorrecto:

```python
class User(BaseModel):
    id: int
    email: str
    hashed_password: str
```

Si ese mismo modelo se usa como salida, podrías exponer `hashed_password`.

Mejor:

```python
class UserRead(BaseModel):
    id: int
    email: str
```

## 5.3 `HTTPException`

```python
from fastapi import HTTPException

if product is None:
    raise HTTPException(
        status_code=404,
        detail="Product not found",
    )
```

## 5.4 `409 Conflict`

Útil para conflictos de estado:

```python
if email_exists:
    raise HTTPException(
        status_code=409,
        detail="Email already registered",
    )
```

## 5.5 Error uniforme

Un proyecto puede adoptar un formato:

```json
{
  "error": {
    "code": "PRODUCT_NOT_FOUND",
    "message": "Product not found"
  }
}
```

Para ello se pueden utilizar exception handlers.

## 5.6 Exception handler

```python
from fastapi import Request
from fastapi.responses import JSONResponse

class DomainError(Exception):
    def __init__(self, code: str, message: str):
        self.code = code
        self.message = message

@app.exception_handler(DomainError)
async def domain_error_handler(
    request: Request,
    exc: DomainError,
):
    return JSONResponse(
        status_code=400,
        content={
            "error": {
                "code": exc.code,
                "message": exc.message,
            }
        },
    )
```

## 5.7 Headers de respuesta

```python
from fastapi import Response

@app.get("/example")
def example(response: Response):
    response.headers["X-App-Version"] = "1.0"
    return {"ok": True}
```

## Práctica

Definir política de errores:

- Recurso inexistente → 404.
- Correo duplicado → 409.
- Credenciales inválidas → 401.
- Permiso insuficiente → 403.
- Validación → 422.

---

# Módulo 6. Inyección de dependencias

**Nivel:** fundamentos → intermedio  
**Duración:** 5 horas

## Objetivos

- Comprender `Depends`.
- Reutilizar lógica.
- Administrar recursos.
- Crear dependencias anidadas.

## 6.1 Problema

Sin dependencias:

```python
@app.get("/products")
def products():
    # validar token
    # abrir sesión
    # verificar permisos
    # ejecutar operación
    ...
```

Repetir esta lógica en cada endpoint produce acoplamiento y duplicación.

## 6.2 Dependencia básica

```python
from typing import Annotated
from fastapi import Depends

def pagination(
    skip: int = 0,
    limit: int = 20,
) -> dict[str, int]:
    return {
        "skip": skip,
        "limit": min(limit, 100),
    }

@app.get("/products")
def list_products(
    page: Annotated[dict, Depends(pagination)],
):
    return page
```

## 6.3 Alias tipado

```python
PaginationDep = Annotated[
    dict[str, int],
    Depends(pagination),
]
```

Uso:

```python
@app.get("/products")
def list_products(page: PaginationDep):
    ...
```

## 6.4 Dependencias con `yield`

Son especialmente útiles para recursos cuyo ciclo de vida debe cerrarse:

```python
def get_resource():
    resource = open_resource()

    try:
        yield resource
    finally:
        resource.close()
```

Esto se aplicará después a sesiones de base de datos.

## 6.5 Dependencias jerárquicas

```text
endpoint
  └── require_admin
        └── get_current_user
              └── decode_token
```

## 6.6 Casos de uso

- Sesión de base de datos.
- Usuario autenticado.
- Autorización.
- Paginación.
- Tenant actual.
- Cliente HTTP.
- Feature flags.
- Servicios.

## Práctica

Crear:

- `get_current_user()`
- `require_active_user()`
- `require_admin()`

Por ahora pueden devolver datos simulados.

---

# Módulo 7. Persistencia con SQLAlchemy 2.x

**Nivel:** intermedio  
**Duración:** 7–8 horas

## Objetivos

- Comprender ORM.
- Crear modelos SQLAlchemy modernos.
- Administrar sesiones.
- Implementar CRUD persistente.
- Comprender transacciones.

## 7.1 ORM

Un ORM permite mapear clases a tablas.

```text
Clase Product
      |
      v
Tabla products
```

No elimina la necesidad de comprender SQL.

## 7.2 Instalación

Para práctica local:

```bash
uv add sqlalchemy
```

SQLite puede utilizarse primero para simplificar.

## 7.3 Base declarativa

```python
from sqlalchemy.orm import DeclarativeBase

class Base(DeclarativeBase):
    pass
```

## 7.4 Modelo moderno

```python
from sqlalchemy import String
from sqlalchemy.orm import Mapped, mapped_column

class Product(Base):
    __tablename__ = "products"

    id: Mapped[int] = mapped_column(primary_key=True)
    name: Mapped[str] = mapped_column(String(120), index=True)
    price: Mapped[float]
    stock: Mapped[int] = mapped_column(default=0)
```

## 7.5 Engine

```python
from sqlalchemy import create_engine

engine = create_engine(
    "sqlite:///./app.db",
)
```

Para SQLite en ciertos escenarios con FastAPI:

```python
engine = create_engine(
    "sqlite:///./app.db",
    connect_args={"check_same_thread": False},
)
```

## 7.6 Session factory

```python
from sqlalchemy.orm import sessionmaker

SessionLocal = sessionmaker(
    bind=engine,
    autoflush=False,
    expire_on_commit=False,
)
```

## 7.7 Dependencia de sesión

```python
from typing import Annotated
from fastapi import Depends
from sqlalchemy.orm import Session

def get_db():
    db = SessionLocal()

    try:
        yield db
    finally:
        db.close()

DbSession = Annotated[Session, Depends(get_db)]
```

## 7.8 Insertar

```python
def create_product(
    data: ProductCreate,
    db: Session,
) -> Product:
    product = Product(**data.model_dump())

    db.add(product)
    db.commit()
    db.refresh(product)

    return product
```

## 7.9 Consultar con SQLAlchemy 2.x

```python
from sqlalchemy import select

statement = select(Product).where(
    Product.id == product_id
)

product = db.scalar(statement)
```

Listado:

```python
statement = (
    select(Product)
    .offset(skip)
    .limit(limit)
)

products = db.scalars(statement).all()
```

## 7.10 Actualizar

```python
for key, value in data.model_dump(
    exclude_unset=True
).items():
    setattr(product, key, value)

db.commit()
db.refresh(product)
```

## 7.11 Eliminar

```python
db.delete(product)
db.commit()
```

## 7.12 Transacciones

Una transacción agrupa operaciones que deben comportarse como unidad lógica.

Ejemplo: crear pedido.

```text
1. Crear Order
2. Crear OrderItem
3. Reducir stock
4. Confirmar

Si falla un paso:
ROLLBACK
```

Nunca diseñes operaciones complejas suponiendo que cada `commit()` aislado es suficiente.

## 7.13 Relaciones

```python
from sqlalchemy import ForeignKey
from sqlalchemy.orm import relationship

class Order(Base):
    __tablename__ = "orders"

    id: Mapped[int] = mapped_column(primary_key=True)
    user_id: Mapped[int] = mapped_column(
        ForeignKey("users.id")
    )

    items: Mapped[list["OrderItem"]] = relationship(
        back_populates="order",
        cascade="all, delete-orphan",
    )
```

## Práctica

Migrar el CRUD de productos desde memoria hacia SQLite.

## Ejercicios

- Restricción de nombre.
- Búsqueda.
- Paginación.
- Actualización parcial.
- Relación categoría-producto.
- Manejo de duplicados.

---

# Módulo 8. PostgreSQL, migraciones con Alembic y capas de acceso

**Nivel:** intermedio  
**Duración:** 7 horas

## Objetivos

- Utilizar PostgreSQL.
- Configurar un driver.
- Crear migraciones.
- Comprender repositorios y servicios.

## 8.1 ¿Por qué PostgreSQL?

Para proyectos profesionales ofrece:

- Transacciones robustas.
- Constraints.
- Índices.
- Tipos avanzados.
- Excelente soporte SQL.
- Ecosistema maduro.

## 8.2 Driver

En un stack síncrono puede utilizarse un driver PostgreSQL compatible con SQLAlchemy.

En un stack asíncrono se puede utilizar un driver asíncrono, por ejemplo `asyncpg`.

Este curso primero recomienda consolidar el diseño de persistencia en modo síncrono y después estudiar el modo asíncrono.

## 8.3 Variables de entorno

Nunca incrustes credenciales reales:

```python
DATABASE_URL = "postgresql://user:password@localhost/db"
```

en repositorios públicos.

La configuración debe provenir del entorno.

## 8.4 Alembic

Instalar:

```bash
uv add alembic
```

Inicializar:

```bash
uv run alembic init alembic
```

Crear revisión:

```bash
uv run alembic revision \
  --autogenerate \
  -m "create products table"
```

Aplicar:

```bash
uv run alembic upgrade head
```

Historial:

```bash
uv run alembic history
```

Reversión:

```bash
uv run alembic downgrade -1
```

## 8.5 Autogenerate no sustituye la revisión humana

Antes de ejecutar una migración:

1. Leer el archivo generado.
2. Revisar constraints.
3. Revisar renombres.
4. Analizar pérdida de datos.
5. Probar upgrade.
6. Probar estrategia de rollback cuando sea pertinente.

## 8.6 Arquitectura por capas

Una separación útil:

```text
Router
  |
  v
Service / Use case
  |
  v
Repository
  |
  v
SQLAlchemy
  |
  v
PostgreSQL
```

### Router

Se ocupa principalmente de HTTP.

```python
@router.post("/products")
def create_product(
    payload: ProductCreate,
    service: ProductServiceDep,
):
    return service.create(payload)
```

### Service

Reglas de negocio.

```python
class ProductService:
    def create(self, data: ProductCreate):
        if data.stock < 0:
            raise ValueError("Invalid stock")

        return self.repository.create(data)
```

### Repository

Persistencia.

```python
class ProductRepository:
    def __init__(self, db: Session):
        self.db = db

    def get_by_id(self, product_id: int):
        statement = select(Product).where(
            Product.id == product_id
        )
        return self.db.scalar(statement)
```

## 8.7 ¿Siempre necesito Repository?

No.

Para un CRUD pequeño, introducir demasiadas capas puede hacer más difícil el proyecto.

Úsalo cuando proporcione ventajas reales:

- reglas de negocio crecientes;
- múltiples adaptadores;
- pruebas aisladas;
- acceso persistente complejo;
- aplicación mantenida por un equipo.

## Práctica

Crear una migración para:

- `users`;
- `products`;
- `orders`;
- `order_items`.

---

# Módulo 9. Autenticación, autorización y seguridad

**Nivel:** intermedio  
**Duración:** 8 horas

## Objetivos

- Diferenciar autenticación y autorización.
- Aplicar hashing de contraseñas.
- Crear y validar JWT.
- Utilizar Bearer tokens.
- Implementar roles básicos.
- Comprender riesgos comunes.

## 9.1 Autenticación vs autorización

**Autenticación:**

> ¿Quién eres?

**Autorización:**

> ¿Qué puedes hacer?

## 9.2 Nunca almacenar contraseñas en texto plano

Incorrecto:

```text
password = "secret123"
```

en la base de datos.

Se debe almacenar un hash resistente diseñado para contraseñas.

La documentación actual de FastAPI utiliza `pwdlib` y recomienda Argon2 para su ejemplo moderno.

Instalar:

```bash
uv add "pwdlib[argon2]" pyjwt
```

## 9.3 Hashing

```python
from pwdlib import PasswordHash

password_hash = PasswordHash.recommended()

def hash_password(password: str) -> str:
    return password_hash.hash(password)

def verify_password(
    plain_password: str,
    hashed_password: str,
) -> bool:
    return password_hash.verify(
        plain_password,
        hashed_password,
    )
```

## 9.4 JWT

Un JWT típicamente contiene claims:

```json
{
  "sub": "42",
  "exp": 1780000000
}
```

Un JWT firmado **no significa cifrado**. No guardes secretos en su payload.

## 9.5 Crear token

```python
from datetime import datetime, timedelta, timezone
import jwt

ALGORITHM = "HS256"

def create_access_token(
    subject: str,
    secret_key: str,
    expires_minutes: int = 30,
) -> str:
    expires_at = (
        datetime.now(timezone.utc)
        + timedelta(minutes=expires_minutes)
    )

    payload = {
        "sub": subject,
        "exp": expires_at,
    }

    return jwt.encode(
        payload,
        secret_key,
        algorithm=ALGORITHM,
    )
```

La clave debe provenir del entorno o de un gestor de secretos.

## 9.6 OAuth2 Password Bearer

```python
from fastapi.security import OAuth2PasswordBearer

oauth2_scheme = OAuth2PasswordBearer(
    tokenUrl="/auth/token"
)
```

## 9.7 Obtener usuario actual

Flujo:

```text
Request
  |
Authorization: Bearer TOKEN
  |
oauth2_scheme
  |
decode JWT
  |
sub
  |
buscar usuario
  |
current_user
```

## 9.8 Roles

Ejemplo:

```python
def require_admin(
    current_user: CurrentUser,
):
    if current_user.role != "admin":
        raise HTTPException(
            status_code=403,
            detail="Insufficient permissions",
        )

    return current_user
```

## 9.9 `401` vs `403`

- `401`: no existe autenticación válida.
- `403`: la identidad fue reconocida, pero no posee permiso suficiente.

## 9.10 Riesgos comunes

- Secretos en Git.
- JWT sin expiración.
- Tokens excesivamente largos.
- Contraseñas en logs.
- CORS permisivo sin necesidad.
- SQL construido por concatenación.
- Ausencia de rate limiting en servicios expuestos.
- Exposición de mensajes internos.
- Dependencias sin actualizar.
- No utilizar HTTPS en producción.
- Confiar en campos enviados por el cliente para permisos.
- Autorizar solo en frontend.

## 9.11 Refresh tokens

Conceptualmente:

```text
Access token:
  corto
  utilizado frecuentemente

Refresh token:
  más duradero
  utilizado para obtener nuevos access tokens
```

Su implementación requiere políticas claras de:

- revocación;
- rotación;
- almacenamiento;
- expiración;
- detección de reutilización.

No debe añadirse de forma improvisada.

## Práctica

Implementar:

```text
POST /auth/register
POST /auth/token
GET  /users/me
GET  /admin/stats
```

---

# Módulo 10. Asincronía, concurrencia y servicios externos

**Nivel:** intermedio  
**Duración:** 6 horas

## Objetivos

- Comprender I/O-bound vs CPU-bound.
- Elegir entre `def` y `async def`.
- Utilizar HTTPX asíncrono.
- Introducir SQLAlchemy AsyncSession.

## 10.1 I/O-bound

Operaciones que esperan:

- Base de datos.
- HTTP.
- Archivos.
- Red.
- Colas.

## 10.2 CPU-bound

Operaciones intensivas de:

- cálculo;
- compresión;
- procesamiento de imagen;
- modelos pesados;
- transformación numérica.

`async` no convierte una operación CPU-bound en una operación paralela.

## 10.3 Endpoint asíncrono

```python
@app.get("/example")
async def example():
    result = await async_operation()
    return {"result": result}
```

## 10.4 Consumir una API con HTTPX

```bash
uv add httpx
```

```python
import httpx

async def get_exchange_rate() -> dict:
    async with httpx.AsyncClient(
        timeout=10.0
    ) as client:
        response = await client.get(
            "https://example.org/api/rates"
        )
        response.raise_for_status()
        return response.json()
```

## 10.5 Reutilizar clientes

Crear un `AsyncClient` por cada llamada puede resultar ineficiente en aplicaciones con alto tráfico.

En aplicaciones reales se puede gestionar un cliente durante el lifespan de la aplicación.

## 10.6 SQLAlchemy asíncrono

SQLAlchemy 2.x ofrece:

- `create_async_engine`.
- `AsyncSession`.
- `async_sessionmaker`.

Ejemplo:

```python
from sqlalchemy.ext.asyncio import (
    AsyncSession,
    async_sessionmaker,
    create_async_engine,
)

engine = create_async_engine(DATABASE_URL)

AsyncSessionLocal = async_sessionmaker(
    engine,
    expire_on_commit=False,
)
```

Dependencia:

```python
async def get_db():
    async with AsyncSessionLocal() as session:
        yield session
```

Consulta:

```python
result = await session.execute(
    select(Product)
)

products = result.scalars().all()
```

## 10.7 Regla crítica de sesión

Una misma `AsyncSession` no debe compartirse indiscriminadamente entre tareas concurrentes.

Cada flujo de trabajo concurrente debe manejar su contexto de sesión de forma segura.

## 10.8 Timeout

Toda integración externa debe plantearse preguntas como:

```text
¿cuánto esperar?
¿qué hacer en timeout?
¿cuántos reintentos?
¿qué errores reintentar?
¿cómo evitar duplicar una operación?
```

## Práctica

Crear endpoint:

```text
GET /external/status
```

que consulte un servicio externo con timeout y tratamiento de errores.

---

# Módulo 11. Middleware, CORS, archivos y tareas en segundo plano

**Nivel:** intermedio  
**Duración:** 5 horas

## Objetivos

- Configurar CORS.
- Crear middleware.
- Recibir archivos.
- Ejecutar tareas ligeras después de una respuesta.

## 11.1 CORS

CORS controla qué orígenes de navegador pueden acceder al backend bajo determinadas condiciones.

```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=[
        "https://app.example.com"
    ],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

En producción evita usar una política más permisiva de la necesaria.

## 11.2 Middleware

Ejemplo de medición:

```python
from time import perf_counter
from fastapi import Request

@app.middleware("http")
async def add_process_time(
    request: Request,
    call_next,
):
    start = perf_counter()

    response = await call_next(request)

    elapsed = perf_counter() - start
    response.headers["X-Process-Time"] = str(elapsed)

    return response
```

## 11.3 Archivos

```python
from fastapi import File, UploadFile

@app.post("/files")
async def upload_file(
    file: UploadFile = File(...),
):
    return {
        "filename": file.filename,
        "content_type": file.content_type,
    }
```

Considerar:

- tamaño;
- extensión;
- MIME type;
- malware;
- nombres de archivo;
- almacenamiento;
- permisos;
- limpieza.

## 11.4 BackgroundTasks

```python
from fastapi import BackgroundTasks

def write_audit_log(message: str):
    with open("audit.log", "a") as file:
        file.write(message + "\n")

@app.post("/notifications")
def create_notification(
    background_tasks: BackgroundTasks,
):
    background_tasks.add_task(
        write_audit_log,
        "notification created",
    )

    return {"accepted": True}
```

## 11.5 ¿Cuándo NO usar `BackgroundTasks`?

No es una cola distribuida.

Para trabajo:

- pesado;
- prolongado;
- que requiere reintentos durables;
- distribuido;
- que debe sobrevivir reinicios;

considera una arquitectura con workers y colas, como Celery/RQ/Dramatiq u otra solución apropiada.

## Práctica

Agregar:

- CORS.
- middleware de request ID.
- subida de imagen de producto.
- tarea ligera de auditoría.

---

# Módulo 12. WebSockets y comunicación en tiempo real

**Nivel:** intermedio  
**Duración:** 4 horas

## Objetivos

- Entender WebSocket.
- Crear conexión bidireccional.
- Diseñar un gestor básico de conexiones.

## 12.1 HTTP vs WebSocket

HTTP convencional:

```text
request -> response
```

WebSocket:

```text
conexión persistente
cliente <------> servidor
```

Casos:

- chat;
- dashboards;
- colaboración;
- presencia;
- actualizaciones en tiempo real.

## 12.2 Endpoint WebSocket

```python
from fastapi import WebSocket

@app.websocket("/ws")
async def websocket_endpoint(
    websocket: WebSocket,
):
    await websocket.accept()

    while True:
        message = await websocket.receive_text()

        await websocket.send_text(
            f"Received: {message}"
        )
```

## 12.3 Desconexiones

```python
from fastapi import WebSocketDisconnect

try:
    ...
except WebSocketDisconnect:
    ...
```

## 12.4 Escalabilidad

Un `set` o una lista en memoria sirve para aprendizaje o una sola instancia.

Con varias réplicas:

```text
API instance A
API instance B
API instance C
```

se necesita un mecanismo compartido de pub/sub o mensajería para sincronizar eventos.

## Práctica

Crear un canal de notificaciones de cambios de inventario.

---

# Módulo 13. Pruebas automatizadas

**Nivel:** fundamentos → intermedio  
**Duración:** 7 horas

## Objetivos

- Crear pruebas unitarias.
- Probar endpoints.
- Utilizar fixtures.
- Aislar base de datos.
- Probar autenticación.

## 13.1 Instalación

```bash
uv add --dev pytest httpx
```

## 13.2 TestClient

```python
from fastapi.testclient import TestClient
from app.main import app

client = TestClient(app)

def test_health():
    response = client.get("/health")

    assert response.status_code == 200
    assert response.json() == {
        "status": "ok"
    }
```

## 13.3 Patrón Arrange–Act–Assert

```python
def test_create_product():
    # Arrange
    payload = {
        "name": "Mouse",
        "price": 500,
        "stock": 10,
    }

    # Act
    response = client.post(
        "/products",
        json=payload,
    )

    # Assert
    assert response.status_code == 201
```

## 13.4 Fixtures

```python
import pytest

@pytest.fixture
def product_payload():
    return {
        "name": "Keyboard",
        "price": 1000,
        "stock": 5,
    }
```

## 13.5 Dependency overrides

Una gran ventaja de la inyección de dependencias es sustituir componentes en tests.

```python
app.dependency_overrides[get_db] = get_test_db
```

Útil para:

- base de datos de pruebas;
- usuario simulado;
- servicio externo falso.

## 13.6 Qué probar

### Happy path

```text
producto válido -> 201
```

### Validación

```text
precio negativo -> 422
```

### Recurso inexistente

```text
id inválido -> 404
```

### Conflicto

```text
correo repetido -> 409
```

### Autenticación

```text
sin token -> 401
token inválido -> 401
```

### Autorización

```text
usuario no admin -> 403
```

## 13.7 Pirámide conceptual

```text
        E2E
      Integration
      Unit tests
```

No todos los proyectos deben seguir proporciones idénticas, pero es útil diferenciar responsabilidades.

## 13.8 Test de servicio

```python
def test_cannot_order_more_than_stock():
    ...
```

Las reglas de negocio importantes deberían poder probarse sin depender exclusivamente de HTTP.

## Práctica

Crear al menos 20 pruebas para:

- autenticación;
- productos;
- pedidos;
- errores.

---

# Módulo 14. Configuración, logging y observabilidad

**Nivel:** intermedio  
**Duración:** 5 horas

## Objetivos

- Separar configuración del código.
- Manejar ambientes.
- Generar logs útiles.
- Comprender métricas y tracing.

## 14.1 Configuración

Instalar:

```bash
uv add pydantic-settings
```

Ejemplo:

```python
from pydantic_settings import (
    BaseSettings,
    SettingsConfigDict,
)

class Settings(BaseSettings):
    app_name: str = "Commerce API"
    environment: str = "development"
    database_url: str
    secret_key: str

    model_config = SettingsConfigDict(
        env_file=".env",
        env_file_encoding="utf-8",
    )

settings = Settings()
```

No subas `.env` con secretos a Git.

`.gitignore`:

```text
.env
.venv/
__pycache__/
.pytest_cache/
```

## 14.2 Ambientes

Ejemplo:

```text
development
testing
staging
production
```

Los binarios/código deberían mantenerse esencialmente iguales; lo que cambia es configuración.

## 14.3 Logging

Evita depender de `print()`.

```python
import logging

logger = logging.getLogger(__name__)

logger.info("product_created")
logger.warning("low_stock")
logger.exception("unexpected_error")
```

## 14.4 Qué incluir en logs

Según el caso:

- timestamp;
- nivel;
- request ID;
- ruta;
- duración;
- identificadores no sensibles;
- código de error.

Evitar:

- contraseñas;
- tokens;
- datos financieros completos;
- secretos;
- información personal innecesaria.

## 14.5 Logs estructurados

En sistemas distribuidos suele ser útil producir eventos estructurados:

```json
{
  "event": "order_created",
  "order_id": 123,
  "duration_ms": 48
}
```

## 14.6 Tres pilares clásicos

- Logs.
- Métricas.
- Trazas.

### Métricas típicas

- requests/segundo;
- latencia;
- errores;
- saturación;
- conexiones;
- uso de CPU/memoria.

## 14.7 Health endpoints

Ejemplo simple:

```python
@app.get("/health")
def health():
    return {"status": "ok"}
```

En producción puede distinguirse:

- liveness;
- readiness.

No es conveniente hacer health checks extremadamente costosos.

---

# Módulo 15. Arquitectura intermedia y buenas prácticas

**Nivel:** intermedio  
**Duración:** 7 horas

## Objetivos

- Modularizar.
- Separar responsabilidades.
- Diseñar servicios mantenibles.
- Evitar arquitecturas innecesariamente complejas.

## 15.1 Estructura propuesta

```text
app/
├── __init__.py
├── main.py
├── api/
│   ├── __init__.py
│   ├── deps.py
│   └── routes/
│       ├── auth.py
│       ├── products.py
│       └── orders.py
├── core/
│   ├── config.py
│   ├── security.py
│   └── logging.py
├── db/
│   ├── base.py
│   ├── session.py
│   └── models/
│       ├── user.py
│       ├── product.py
│       └── order.py
├── schemas/
│   ├── user.py
│   ├── product.py
│   └── order.py
├── repositories/
│   ├── product.py
│   └── order.py
├── services/
│   ├── product.py
│   └── order.py
└── exceptions.py

tests/
├── conftest.py
├── test_auth.py
├── test_products.py
└── test_orders.py
```

No es una estructura obligatoria. Adáptala al tamaño del proyecto.

## 15.2 Routers

```python
from fastapi import APIRouter

router = APIRouter(
    prefix="/products",
    tags=["Products"],
)

@router.get("/")
def list_products():
    ...
```

Registrar:

```python
app.include_router(
    router,
    prefix="/api/v1",
)
```

## 15.3 Versionado

```text
/api/v1/products
```

No toda modificación requiere una nueva versión. Una nueva versión es relevante cuando existe una ruptura de contrato que debe convivir con consumidores existentes.

## 15.4 Principio de responsabilidad

Router:

- HTTP.
- validación de request ya modelada.
- status code.
- dependencia.
- mapping de excepciones cuando corresponda.

Service:

- reglas de negocio.
- coordinación de operaciones.

Repository:

- consultas y persistencia.

## 15.5 No colocar todo en `main.py`

Una aplicación creciente en un solo archivo:

```text
main.py de 5000 líneas
```

dificulta:

- pruebas;
- revisión;
- ownership;
- navegación;
- reutilización.

## 15.6 No crear arquitectura ceremonial

También es un problema tener:

```text
Controller
Service
UseCase
Interactor
Manager
Facade
Repository
Gateway
Adapter
Provider
```

para un CRUD de tres endpoints sin reglas complejas.

La arquitectura debe pagar su costo con claridad, testabilidad o capacidad de cambio.

## 15.7 Separar modelos de entrada y salida

Especialmente:

```text
UserCreate
UserUpdate
UserRead
UserInternal
```

## 15.8 Manejo de dominio

En un proyecto más maduro:

```python
class InsufficientStockError(Exception):
    pass
```

El servicio puede lanzar una excepción de dominio y la capa HTTP traducirla a `409 Conflict`.

Así, la lógica de negocio no necesita conocer `HTTPException`.

## 15.9 Unit of Work

Cuando una operación coordina múltiples repositorios dentro de una transacción, puede ser útil modelar explícitamente una unidad de trabajo.

Ejemplo conceptual:

```text
with unit_of_work:
    order = order_repository.create(...)
    inventory_repository.decrease(...)
    unit_of_work.commit()
```

No es requisito para todos los sistemas.

## 15.10 Idempotencia

Operaciones críticas pueden requerir idempotency keys.

Ejemplo:

```http
POST /payments
Idempotency-Key: 41ae...
```

El servidor evita ejecutar dos veces una operación repetida accidentalmente.

Este tema es especialmente relevante para pagos, pedidos y operaciones externas.

## Práctica

Refactorizar el proyecto desde CRUD directo hacia routers + services + repositories.

---

# Módulo 16. Docker, despliegue y operación

**Nivel:** intermedio  
**Duración:** 6 horas

## Objetivos

- Crear una imagen Docker.
- Usar Docker Compose.
- Comprender procesos y workers.
- Preparar configuración de producción.

## 16.1 Dockerfile básico

Un ejemplo educativo:

```dockerfile
FROM python:3.12-slim

WORKDIR /app

COPY pyproject.toml uv.lock ./

RUN pip install uv \
    && uv sync --frozen --no-dev

COPY . .

CMD [
  "uv",
  "run",
  "uvicorn",
  "app.main:app",
  "--host",
  "0.0.0.0",
  "--port",
  "8000"
]
```

Para producción debes ajustar la construcción según el gestor de dependencias y la estrategia de imagen elegida.

## 16.2 `.dockerignore`

```text
.git
.venv
__pycache__
.pytest_cache
.env
tests
```

## 16.3 Compose

```yaml
services:
  api:
    build: .
    ports:
      - "8000:8000"
    environment:
      DATABASE_URL: postgresql://app:app@db:5432/app
    depends_on:
      - db

  db:
    image: postgres:17
    environment:
      POSTGRES_USER: app
      POSTGRES_PASSWORD: app
      POSTGRES_DB: app
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

Las contraseñas anteriores son exclusivamente demostrativas para desarrollo local.

## 16.4 Desarrollo vs producción

En desarrollo:

```text
--reload
```

En producción:

```text
NO --reload
```

## 16.5 Workers

Más workers pueden aumentar capacidad de procesamiento, pero:

- consumen memoria;
- cada worker tiene su propio proceso;
- el estado en memoria no se comparte automáticamente;
- el pool de conexiones debe dimensionarse;
- no resuelven una consulta lenta.

## 16.6 Proxy inverso

Una arquitectura puede incluir:

```text
Internet
   |
Load Balancer / Reverse Proxy
   |
FastAPI
   |
PostgreSQL
```

Dependiendo de la plataforma, HTTPS, balanceo y terminación TLS pueden estar administrados por infraestructura externa.

## 16.7 Migraciones durante despliegue

No hagas que múltiples réplicas ejecuten migraciones de manera descoordinada.

Mejor:

```text
pipeline/deploy job
   |
alembic upgrade head
   |
arranque/reemplazo de aplicación
```

La estrategia exacta depende de la infraestructura.

## 16.8 Principios de producción

- HTTPS.
- Secretos fuera del código.
- Backups.
- Logs.
- Monitoring.
- Timeouts.
- Límites de recursos.
- Health checks.
- Migraciones controladas.
- Dependencias fijadas.
- Usuario no-root cuando sea viable.
- Imágenes mínimas.
- CI/CD.
- Rollback plan.

## Práctica

Ejecutar localmente:

```bash
docker compose up --build
```

Comprobar:

```text
GET /health
GET /docs
```

---

# Proyecto integrador

## Nombre

**Commerce API — API de usuarios, catálogo y pedidos**

## Objetivo

Construir una API backend profesional que integre los contenidos de fundamentos e intermedio.

## Funcionalidades mínimas

### Usuarios

```text
POST /api/v1/auth/register
POST /api/v1/auth/token
GET  /api/v1/users/me
```

### Productos

```text
GET    /api/v1/products
GET    /api/v1/products/{id}
POST   /api/v1/products
PATCH  /api/v1/products/{id}
DELETE /api/v1/products/{id}
```

### Pedidos

```text
POST /api/v1/orders
GET  /api/v1/orders
GET  /api/v1/orders/{id}
```

## Reglas

1. Un usuario debe autenticarse para crear pedidos.
2. Solo administradores pueden crear/modificar/eliminar productos.
3. Un pedido no puede solicitar una cantidad superior al stock.
4. El stock debe disminuir dentro de la misma transacción lógica que crea el pedido.
5. Un usuario ordinario solo puede consultar sus propios pedidos.
6. El precio final del pedido debe calcularse en backend.
7. Nunca confiar en un `total` enviado por el cliente.
8. Las contraseñas se almacenan mediante hash seguro.
9. JWT debe expirar.
10. Los secretos se cargan desde configuración externa.

## Modelo de datos conceptual

```text
User
----
id
email
hashed_password
role
is_active
created_at

Product
-------
id
name
description
price
stock
is_active
created_at

Order
-----
id
user_id
status
total
created_at

OrderItem
---------
id
order_id
product_id
quantity
unit_price
```

## Relaciones

```text
User 1 -------- N Order
Order 1 ------- N OrderItem
Product 1 ----- N OrderItem
```

## Estados de pedido sugeridos

```text
pending
confirmed
cancelled
```

No permitas transiciones arbitrarias.

Ejemplo:

```text
pending -> confirmed
pending -> cancelled
confirmed -> cancelled  # solo si reglas lo permiten
```

## Estructura del proyecto final

```text
commerce-api/
├── app/
│   ├── main.py
│   ├── api/
│   │   ├── deps.py
│   │   └── routes/
│   │       ├── auth.py
│   │       ├── products.py
│   │       └── orders.py
│   ├── core/
│   │   ├── config.py
│   │   └── security.py
│   ├── db/
│   │   ├── base.py
│   │   ├── session.py
│   │   └── models/
│   ├── schemas/
│   ├── repositories/
│   ├── services/
│   └── exceptions.py
├── alembic/
├── tests/
├── .env.example
├── .gitignore
├── Dockerfile
├── compose.yaml
├── pyproject.toml
├── uv.lock
└── README.md
```

## Etapa 1 — API en memoria

Implementar:

- productos;
- esquemas;
- validación;
- errores;
- documentación.

## Etapa 2 — Persistencia

Agregar:

- SQLAlchemy.
- PostgreSQL.
- relaciones.
- Alembic.

## Etapa 3 — Seguridad

Agregar:

- registro;
- login;
- JWT;
- roles.

## Etapa 4 — Lógica de pedidos

Agregar:

- transacciones;
- stock;
- totales;
- permisos.

## Etapa 5 — Calidad

Agregar:

- pruebas.
- logging.
- configuración.
- tratamiento consistente de errores.

## Etapa 6 — Operación

Agregar:

- Dockerfile.
- Compose.
- health endpoint.
- documentación de despliegue.

## Requisitos técnicos

El proyecto debe:

- usar type hints;
- tener modelos Pydantic diferenciados;
- utilizar `APIRouter`;
- utilizar dependencias;
- implementar al menos una regla de negocio en service;
- usar SQLAlchemy 2.x;
- usar migraciones;
- contener al menos 25 pruebas;
- evitar secretos en el repositorio;
- incluir `.env.example`;
- incluir documentación de ejecución;
- producir un esquema OpenAPI válido.

---

# Evaluación sugerida

| Componente | Porcentaje |
|---|---:|
| Ejercicios de fundamentos | 15% |
| CRUD + validación | 15% |
| Persistencia + migraciones | 15% |
| Seguridad | 15% |
| Pruebas | 15% |
| Proyecto integrador | 25% |

## Rúbrica del proyecto integrador

### 1. Diseño HTTP — 15 puntos

- Rutas consistentes.
- Métodos apropiados.
- Status codes correctos.
- Contratos claros.

### 2. Validación — 10 puntos

- Schemas separados.
- Restricciones.
- Manejo de entradas inválidas.

### 3. Persistencia — 15 puntos

- Modelos relacionales.
- Constraints.
- Migraciones.
- Transacciones.

### 4. Seguridad — 15 puntos

- Password hashing.
- JWT.
- Expiración.
- Autorización.

### 5. Arquitectura — 15 puntos

- Modularidad.
- Separación de responsabilidades.
- Dependencias.
- Código mantenible.

### 6. Pruebas — 15 puntos

- Casos positivos.
- Casos negativos.
- Seguridad.
- Reglas de negocio.

### 7. Operación — 10 puntos

- Docker.
- Configuración.
- Health check.
- Logs.

### 8. Documentación — 5 puntos

- README.
- Ejemplos.
- Variables de entorno.
- Pasos de ejecución.

---

# Ruta de estudio

## Semana 1

- Módulo 0.
- Módulo 1.
- Módulo 2.

**Resultado:** primera API.

## Semana 2

- Módulo 3.
- Módulo 4.
- Módulo 5.

**Resultado:** CRUD validado en memoria.

## Semana 3

- Módulo 6.
- Módulo 7.

**Resultado:** CRUD persistente.

## Semana 4

- Módulo 8.

**Resultado:** PostgreSQL + Alembic + capas.

## Semana 5

- Módulo 9.

**Resultado:** autenticación y autorización.

## Semana 6

- Módulo 10.
- Módulo 11.
- Módulo 12.

**Resultado:** integración asíncrona y capacidades avanzadas.

## Semana 7

- Módulo 13.
- Módulo 14.

**Resultado:** pruebas y observabilidad.

## Semana 8

- Módulo 15.
- Módulo 16.
- Proyecto final.

**Resultado:** servicio integrable y desplegable.

---

# Errores frecuentes y diagnóstico

## 1. `ModuleNotFoundError`

Verificar:

```bash
uv run python -c "import fastapi; print(fastapi.__version__)"
```

Ejecuta los comandos desde el proyecto correcto.

## 2. Uvicorn no encuentra `app`

Si tienes:

```text
app/main.py
```

y dentro:

```python
app = FastAPI()
```

entonces:

```bash
uv run uvicorn app.main:app --reload
```

Significa:

```text
app.main -> módulo
app      -> variable
```

## 3. Ruta estática vs ruta dinámica

Orden peligroso:

```python
@app.get("/users/{user_id}")
...

@app.get("/users/me")
...
```

Dependiendo del diseño, `"me"` podría interpretarse como parámetro. Diseña las rutas conscientemente y revisa el orden cuando existan colisiones.

## 4. `422`

No significa necesariamente que FastAPI esté fallando.

Normalmente significa:

```text
el request no cumple el contrato esperado
```

Revisar:

- tipo;
- nombre;
- ubicación;
- body;
- JSON;
- validaciones.

## 5. `401`

Revisar:

- header `Authorization`;
- formato `Bearer <token>`;
- expiración;
- firma;
- secret/algoritmo;
- usuario.

## 6. `403`

El usuario puede estar autenticado pero no autorizado.

## 7. Error de conexión a PostgreSQL

Revisar:

- host;
- puerto;
- usuario;
- contraseña;
- nombre de DB;
- driver;
- red de Docker;
- servicio iniciado.

Dentro de Compose, el host suele ser el nombre del servicio, no `localhost`.

## 8. Migración no detecta modelos

Alembic necesita conocer el `MetaData` que contiene los modelos.

Revisar `target_metadata`.

## 9. N+1 queries

Si una consulta de órdenes dispara otra consulta por cada relación, puede existir un problema N+1.

Analiza estrategias de carga de relaciones en SQLAlchemy.

## 10. Bloqueo en endpoint async

Si ejecutas una operación bloqueante pesada dentro de `async def`, puedes bloquear el event loop.

Identifica la naturaleza de la dependencia.

## 11. Estado global

No almacenes estado crítico únicamente en:

```python
global_cache = {}
```

si pretendes ejecutar múltiples procesos/réplicas y esperas consistencia.

## 12. Crear sesión global de DB

Evita:

```python
db = SessionLocal()
```

como sesión reutilizada globalmente para todos los requests.

La sesión debe tener ciclo de vida controlado.

---

# Checklist de una API lista para producción

## Diseño

- [ ] Recursos y rutas coherentes.
- [ ] Versionado definido si aplica.
- [ ] Status codes correctos.
- [ ] Contratos OpenAPI revisados.
- [ ] Paginación para colecciones grandes.
- [ ] Estrategia de idempotencia para operaciones críticas.

## Datos

- [ ] Migraciones.
- [ ] Constraints en base de datos.
- [ ] Índices revisados.
- [ ] Transacciones.
- [ ] Backups.
- [ ] Política de restauración probada.

## Seguridad

- [ ] HTTPS.
- [ ] Secretos externos.
- [ ] Contraseñas hasheadas.
- [ ] Tokens con expiración.
- [ ] Roles/permisos verificados en backend.
- [ ] CORS restringido.
- [ ] Dependencias actualizadas.
- [ ] No se registran tokens/contraseñas.
- [ ] Límites de tamaño de archivos/requests cuando corresponda.
- [ ] Rate limiting o protección perimetral cuando corresponda.

## Calidad

- [ ] Linter.
- [ ] Formatter.
- [ ] Type checking si el equipo lo adopta.
- [ ] Tests automatizados.
- [ ] Tests de integración.
- [ ] CI.

## Operación

- [ ] Logs.
- [ ] Métricas.
- [ ] Health checks.
- [ ] Timeouts.
- [ ] Alertas.
- [ ] Contenedor reproducible.
- [ ] Configuración por entorno.
- [ ] Estrategia de rollback.
- [ ] Migraciones coordinadas.

---

# Guía práctica de comandos

## Crear proyecto

```bash
uv init commerce-api --bare
cd commerce-api
```

## Dependencias principales

```bash
uv add "fastapi[standard]"
uv add sqlalchemy alembic
uv add pydantic-settings
uv add pyjwt "pwdlib[argon2]"
uv add httpx
```

Agrega el driver PostgreSQL adecuado al modo síncrono/asíncrono elegido.

## Desarrollo

```bash
uv run fastapi dev
```

o:

```bash
uv run uvicorn app.main:app --reload
```

## Testing

```bash
uv run pytest
```

Verbose:

```bash
uv run pytest -v
```

Archivo:

```bash
uv run pytest tests/test_products.py
```

Caso:

```bash
uv run pytest \
  tests/test_products.py::test_create_product
```

## Alembic

```bash
uv run alembic revision \
  --autogenerate \
  -m "create initial tables"

uv run alembic upgrade head

uv run alembic current

uv run alembic history
```

## Docker

```bash
docker build -t commerce-api .
docker compose up --build
docker compose down
```

---

# Ejercicios acumulativos

## Ejercicio 1 — catálogo

Crear:

```text
GET /products
GET /products/{id}
POST /products
```

## Ejercicio 2 — validación

Agregar:

- nombre mínimo 2 caracteres;
- precio > 0;
- stock >= 0.

## Ejercicio 3 — filtros

Agregar:

```text
GET /products?search=...
GET /products?min_price=...
GET /products?max_price=...
```

## Ejercicio 4 — DB

Persistir productos.

## Ejercicio 5 — migraciones

Agregar campo:

```text
sku
```

con restricción de unicidad.

## Ejercicio 6 — usuarios

Crear registro e inicio de sesión.

## Ejercicio 7 — autorización

Solo admin puede:

```text
POST /products
PATCH /products/{id}
DELETE /products/{id}
```

## Ejercicio 8 — pedidos

Crear pedido y disminuir stock.

## Ejercicio 9 — rollback

Provocar un error durante la creación del pedido y verificar que el stock no quede modificado parcialmente.

## Ejercicio 10 — pruebas

Automatizar cada comportamiento anterior.

---

# Preguntas de revisión por nivel

## Fundamentos

1. ¿Qué diferencia existe entre path parameter y query parameter?
2. ¿Qué función cumple Pydantic?
3. ¿Qué representa `response_model`?
4. ¿Qué es OpenAPI?
5. ¿Cuándo usar `404`?
6. ¿Qué significa `422`?
7. ¿Qué es una dependencia?
8. ¿Qué hace Uvicorn?
9. ¿Qué significa ASGI?
10. ¿Por qué separar modelos de entrada y salida?

## Intermedio

1. ¿Qué diferencia hay entre sesión, conexión y transacción?
2. ¿Por qué las migraciones deben versionarse?
3. ¿Qué significa que un JWT esté firmado?
4. ¿Por qué JWT no implica cifrado?
5. ¿Cuál es la diferencia entre autenticación y autorización?
6. ¿Cuándo utilizar `async def`?
7. ¿Por qué una tarea pesada no debería ejecutarse con `BackgroundTasks`?
8. ¿Cómo sustituye FastAPI dependencias durante tests?
9. ¿Por qué una sesión SQLAlchemy no debe ser global?
10. ¿Qué problema resuelve un repository?
11. ¿Cuándo un repository sería sobreingeniería?
12. ¿Qué es N+1?
13. ¿Qué es idempotencia?
14. ¿Por qué no se debe calcular el total de un pedido confiando en el frontend?
15. ¿Qué implica escalar WebSockets a varias instancias?

---

# Examen práctico sugerido

Construir en 3–4 horas una API de tareas:

```text
User
Task
```

## Requisitos

```text
POST   /auth/register
POST   /auth/token
GET    /tasks
POST   /tasks
PATCH  /tasks/{id}
DELETE /tasks/{id}
```

Reglas:

- usuario autenticado;
- cada usuario solo ve sus tareas;
- título obligatorio;
- estado `pending` o `done`;
- PostgreSQL;
- migración;
- al menos 8 tests.

## Criterios

- Corrección funcional.
- Diseño de rutas.
- Validación.
- Seguridad.
- Organización.
- Pruebas.
- Calidad del código.

---

# Extensiones después del nivel intermedio

Una vez dominado el contenido de este curso, continuar con:

## Arquitectura

- Clean Architecture.
- Hexagonal Architecture.
- Domain-Driven Design.
- CQRS, cuando exista necesidad real.
- Event-driven architecture.

## Persistencia

- Optimización SQL.
- Índices.
- EXPLAIN.
- Locks.
- Isolation levels.
- Pooling.
- SQLAlchemy avanzado.

## Seguridad

- OAuth2 Authorization Code + PKCE.
- OpenID Connect.
- Integración con proveedores de identidad.
- Rotación de claves.
- JWKS.
- RBAC/ABAC avanzado.
- Auditoría.
- OWASP API Security.

## Rendimiento

- Profiling.
- Caching.
- Redis.
- Rate limiting.
- Backpressure.
- Load testing.
- Gunicorn/Uvicorn u opciones de ejecución de la plataforma.

## Mensajería

- Celery.
- RabbitMQ.
- Redis.
- Kafka.
- Outbox pattern.

## Observabilidad

- OpenTelemetry.
- Prometheus.
- Grafana.
- tracing distribuido.
- logs estructurados.

## Infraestructura

- Kubernetes.
- CI/CD.
- secret managers.
- managed databases.
- infraestructura como código.

---

# Glosario

**API:** interfaz que permite interacción entre sistemas.

**ASGI:** especificación de interfaz para aplicaciones Python asíncronas y servidores.

**Bearer token:** token enviado normalmente en el header `Authorization`.

**CRUD:** Create, Read, Update, Delete.

**Dependency Injection:** técnica para proporcionar dependencias a componentes sin construirlas directamente dentro de ellos.

**DTO:** objeto usado para transportar datos entre límites o capas.

**Endpoint:** combinación de ruta y operación expuesta por una API.

**HTTP:** protocolo de comunicación utilizado en la web.

**Idempotencia:** propiedad por la cual repetir una operación produce el mismo efecto observable relevante.

**JWT:** formato de token firmado que puede transportar claims.

**Migration:** cambio versionado al esquema de una base de datos.

**OpenAPI:** especificación para describir APIs HTTP.

**ORM:** mapeo entre objetos y estructuras relacionales.

**Pydantic:** biblioteca de validación y serialización basada en type hints.

**Repository:** abstracción que concentra acceso a persistencia.

**REST:** estilo arquitectónico para sistemas distribuidos.

**Router:** agrupación modular de operaciones HTTP.

**Service:** componente que suele concentrar reglas o coordinación de negocio.

**Transaction:** conjunto de operaciones de base de datos tratadas como una unidad.

**Uvicorn:** servidor ASGI utilizado comúnmente con FastAPI.

**WebSocket:** protocolo de comunicación bidireccional persistente.

---

# Referencias oficiales

> Estas fuentes deben ser la primera referencia cuando una API, recomendación o sintaxis cambie entre versiones.

## FastAPI

- Documentación: https://fastapi.tiangolo.com/
- Tutorial: https://fastapi.tiangolo.com/tutorial/
- Dependencias: https://fastapi.tiangolo.com/tutorial/dependencies/
- Seguridad: https://fastapi.tiangolo.com/tutorial/security/
- JWT: https://fastapi.tiangolo.com/tutorial/security/oauth2-jwt/
- Testing: https://fastapi.tiangolo.com/tutorial/testing/
- Background Tasks: https://fastapi.tiangolo.com/tutorial/background-tasks/

## Pydantic

- https://docs.pydantic.dev/

## SQLAlchemy

- https://docs.sqlalchemy.org/
- ORM: https://docs.sqlalchemy.org/en/20/orm/
- AsyncIO: https://docs.sqlalchemy.org/en/20/orm/extensions/asyncio.html

## Alembic

- https://alembic.sqlalchemy.org/

## Uvicorn

- https://www.uvicorn.org/

## PostgreSQL

- https://www.postgresql.org/docs/

## HTTPX

- https://www.python-httpx.org/

## pytest

- https://docs.pytest.org/

## Docker

- https://docs.docker.com/
- Python guide: https://docs.docker.com/guides/python/

## Python

- https://docs.python.org/3/

---

# Cierre

FastAPI reduce una gran cantidad de código incidental, pero una API profesional continúa requiriendo decisiones de ingeniería.

La progresión recomendada es:

```text
HTTP
  ↓
Python tipado
  ↓
FastAPI
  ↓
Pydantic
  ↓
Dependencies
  ↓
SQLAlchemy + PostgreSQL
  ↓
Alembic
  ↓
Security
  ↓
Async
  ↓
Testing
  ↓
Architecture
  ↓
Docker / Deployment
  ↓
Observability
```

El objetivo final no es memorizar funciones de FastAPI. Es desarrollar la capacidad de diseñar, construir, probar, proteger, desplegar y mantener servicios backend con criterio técnico.

---

## Resumen de competencias finales

Al terminar el curso deberías poder responder afirmativamente a lo siguiente:

- [ ] Puedo diseñar una API REST coherente.
- [ ] Comprendo request, response, headers, body y status codes.
- [ ] Puedo crear endpoints FastAPI tipados.
- [ ] Puedo validar datos con Pydantic.
- [ ] Puedo controlar los modelos de respuesta.
- [ ] Puedo usar inyección de dependencias.
- [ ] Puedo persistir información con SQLAlchemy 2.x.
- [ ] Puedo trabajar con PostgreSQL.
- [ ] Puedo versionar cambios de esquema con Alembic.
- [ ] Puedo almacenar contraseñas de forma segura.
- [ ] Puedo crear autenticación mediante JWT.
- [ ] Puedo implementar autorización.
- [ ] Entiendo las implicaciones de `async`/`await`.
- [ ] Puedo probar endpoints y lógica de negocio.
- [ ] Puedo configurar la aplicación mediante variables de entorno.
- [ ] Puedo producir logs útiles.
- [ ] Puedo modularizar la aplicación.
- [ ] Puedo contenerizarla con Docker.
- [ ] Comprendo los principales requisitos antes de producción.
