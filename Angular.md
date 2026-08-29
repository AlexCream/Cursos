# Curso Profesional de Angular Moderno
## Fundamentos e Intermedio — Angular 22, TypeScript, Signals, RxJS, REST, Testing y Arquitectura Frontend

> **Versión del curso:** 1.0  
> **Actualizado:** 28 de agosto de 2026  
> **Versión objetivo:** Angular 22.x  
> **Nivel:** Fundamentos → Intermedio  
> **Modalidad:** Teórico-práctica  
> **Duración sugerida:** 110–130 horas  
> **Proyecto transversal:** TaskFlow — Sistema de gestión de proyectos y tareas

---

## Índice

1. [Presentación del curso](#1-presentación-del-curso)
2. [Objetivo general](#2-objetivo-general)
3. [Competencias a desarrollar](#3-competencias-a-desarrollar)
4. [Requisitos previos](#4-requisitos-previos)
5. [Entorno tecnológico](#5-entorno-tecnológico)
6. [Metodología de trabajo](#6-metodología-de-trabajo)
7. [Proyecto transversal](#7-proyecto-transversal)
8. [Módulo 0. Fundamentos del desarrollo web moderno](#módulo-0-fundamentos-del-desarrollo-web-moderno)
9. [Módulo 1. JavaScript moderno para Angular](#módulo-1-javascript-moderno-para-angular)
10. [Módulo 2. TypeScript](#módulo-2-typescript)
11. [Módulo 3. Introducción a Angular](#módulo-3-introducción-a-angular)
12. [Módulo 4. Angular CLI y configuración del proyecto](#módulo-4-angular-cli-y-configuración-del-proyecto)
13. [Módulo 5. Arquitectura y componentes](#módulo-5-arquitectura-y-componentes)
14. [Módulo 6. Templates y data binding](#módulo-6-templates-y-data-binding)
15. [Módulo 7. Control flow, directivas y pipes](#módulo-7-control-flow-directivas-y-pipes)
16. [Módulo 8. Comunicación y ciclo de vida](#módulo-8-comunicación-y-ciclo-de-vida)
17. [Módulo 9. Signals y reactividad moderna](#módulo-9-signals-y-reactividad-moderna)
18. [Módulo 10. Servicios e inyección de dependencias](#módulo-10-servicios-e-inyección-de-dependencias)
19. [Módulo 11. Angular Router](#módulo-11-angular-router)
20. [Módulo 12. Formularios](#módulo-12-formularios)
21. [Módulo 13. HTTP y APIs REST](#módulo-13-http-y-apis-rest)
22. [Módulo 14. RxJS y programación reactiva](#módulo-14-rxjs-y-programación-reactiva)
23. [Módulo 15. Gestión de estado](#módulo-15-gestión-de-estado)
24. [Módulo 16. Autenticación, autorización y seguridad](#módulo-16-autenticación-autorización-y-seguridad)
25. [Módulo 17. UI, estilos y accesibilidad](#módulo-17-ui-estilos-y-accesibilidad)
26. [Módulo 18. Testing con Vitest](#módulo-18-testing-con-vitest)
27. [Módulo 19. Rendimiento y optimización](#módulo-19-rendimiento-y-optimización)
28. [Módulo 20. SSR, SSG e hidratación](#módulo-20-ssr-ssg-e-hidratación)
29. [Módulo 21. Arquitectura profesional y buenas prácticas](#módulo-21-arquitectura-profesional-y-buenas-prácticas)
30. [Módulo 22. Build, configuración y despliegue](#módulo-22-build-configuración-y-despliegue)
31. [Módulo 23. Angular heredado y migración](#módulo-23-angular-heredado-y-migración)
32. [Módulo 24. Proyecto integrador](#módulo-24-proyecto-integrador)
33. [Evaluación del curso](#evaluación-del-curso)
34. [Ruta de profundización](#ruta-de-profundización)
35. [Checklist de competencias](#checklist-de-competencias)
36. [Referencias oficiales](#referencias-oficiales)

---

# 1. Presentación del curso

Angular es un framework de desarrollo web orientado a la construcción de aplicaciones robustas, mantenibles y escalables. Integra una solución coherente para componentes, templates, inyección de dependencias, routing, formularios, acceso HTTP, renderizado del lado del servidor, pruebas y herramientas de compilación.

Este curso sigue el enfoque de **Angular moderno**, con énfasis en:

- componentes **standalone**;
- **Signals**;
- `input()`, `output()` y APIs modernas;
- control flow con `@if`, `@for` y `@switch`;
- inyección mediante `inject()`;
- aplicaciones **zoneless**;
- estrategia de detección eficiente;
- RxJS para flujos asíncronos;
- formularios reactivos y Signal Forms;
- `HttpClient`, `resource()` y `httpResource()`;
- routing con lazy loading;
- pruebas con **Vitest**;
- SSR, SSG e hidratación;
- arquitectura por funcionalidades.

También se incluye una sección de compatibilidad con proyectos anteriores que utilizan `NgModule`, decoradores tradicionales para entradas/salidas o patrones basados en Zone.js.

---

# 2. Objetivo general

Desarrollar las competencias necesarias para diseñar, construir, probar, optimizar y desplegar aplicaciones web profesionales con Angular, aplicando TypeScript, arquitectura basada en componentes, programación reactiva, consumo de APIs REST, gestión de estado, autenticación, pruebas automatizadas y buenas prácticas de ingeniería de software.

---

# 3. Competencias a desarrollar

Al finalizar el curso, el estudiante podrá:

- comprender la arquitectura de una aplicación Angular;
- utilizar Angular CLI;
- programar correctamente con TypeScript;
- diseñar componentes reutilizables;
- utilizar standalone components;
- crear interfaces dinámicas mediante templates;
- emplear Signals para estado reactivo;
- trabajar con Observables y RxJS;
- implementar servicios e inyección de dependencias;
- diseñar navegación con Angular Router;
- crear formularios tipados;
- validar información;
- consumir servicios REST;
- gestionar errores HTTP;
- implementar interceptores;
- gestionar autenticación y autorización;
- implementar guards;
- trabajar con estado local, compartido y global;
- escribir pruebas unitarias;
- optimizar el rendimiento;
- implementar lazy loading y `@defer`;
- comprender SSR, SSG e hidratación;
- estructurar aplicaciones por dominios;
- configurar builds de producción;
- desplegar aplicaciones Angular;
- interpretar y mantener proyectos Angular heredados.

---

# 4. Requisitos previos

## Conocimientos

Se recomienda comprender:

- HTML básico;
- CSS básico;
- JavaScript básico;
- terminal o consola;
- conceptos fundamentales de Git.

No es necesario dominar previamente TypeScript ni Angular.

## Software

- Node.js compatible con Angular 22;
- npm;
- Git;
- Visual Studio Code o IDE equivalente;
- navegador Chromium/Firefox moderno;
- Angular CLI.

Para Angular 22.0.x, la tabla oficial de compatibilidad indica:

```text
Node.js:
^22.22.3
o ^24.15.0
o ^26.0.0

TypeScript:
>= 6.0.0 y < 6.1.0

RxJS:
^6.5.3 o ^7.4.0
```

Comprobar versiones:

```bash
node --version
npm --version
git --version
```

---

# 5. Entorno tecnológico

Tecnologías utilizadas durante el curso:

```text
HTML5
CSS3
JavaScript ES202x
TypeScript
Node.js
npm
Git
GitHub
Angular 22
Angular CLI
Angular Router
Angular Forms
Angular Signals
Angular HttpClient
RxJS
REST
JSON
Vitest
Angular DevTools
```

Tecnologías opcionales para profundización:

```text
Angular Material
Tailwind CSS
NgRx
NestJS
Docker
GitHub Actions
Firebase
Vercel
Netlify
Azure
AWS
```

---

# 6. Metodología de trabajo

Cada módulo utiliza la secuencia:

```text
Concepto
    ↓
Demostración
    ↓
Práctica guiada
    ↓
Ejercicio individual
    ↓
Integración en TaskFlow
    ↓
Revisión / refactorización
```

Distribución sugerida:

| Actividad | Porcentaje |
|---|---:|
| Teoría | 25 % |
| Demostraciones | 15 % |
| Prácticas | 35 % |
| Proyecto integrador | 20 % |
| Evaluaciones | 5 % |

---

# 7. Proyecto transversal

Durante todo el curso se construirá:

# TaskFlow

Sistema para administrar proyectos, tareas y usuarios.

## Funcionalidades

```text
Autenticación
├── Inicio de sesión
├── Cierre de sesión
├── Persistencia de sesión
└── Protección de rutas

Dashboard
├── Estadísticas
├── Proyectos recientes
├── Tareas pendientes
└── Actividad

Proyectos
├── Listar
├── Buscar
├── Filtrar
├── Crear
├── Consultar
├── Editar
└── Eliminar

Tareas
├── Listar
├── Crear
├── Editar
├── Cambiar estado
├── Asignar usuario
└── Eliminar

Usuarios
├── Perfil
└── Preferencias

Sistema
├── Routing
├── Lazy loading
├── Guards
├── HTTP
├── Interceptors
├── Signals
├── RxJS
├── Testing
└── Manejo de errores
```

## Arquitectura objetivo

```text
src/app/
│
├── core/
│   ├── auth/
│   ├── guards/
│   ├── interceptors/
│   ├── services/
│   └── config/
│
├── shared/
│   ├── ui/
│   ├── directives/
│   ├── pipes/
│   ├── models/
│   └── utils/
│
├── features/
│   ├── auth/
│   ├── dashboard/
│   ├── projects/
│   ├── tasks/
│   └── users/
│
├── app.config.ts
├── app.routes.ts
└── app.ts
```

---

# Módulo 0. Fundamentos del desarrollo web moderno

**Duración sugerida:** 5 horas

## Objetivos

- comprender cliente y servidor;
- distinguir frontend y backend;
- comprender HTTP;
- entender SPA, CSR, SSR y SSG;
- repasar HTML y CSS.

## 0.1 Arquitectura cliente-servidor

```text
Navegador
    ↓ HTTP/HTTPS
Frontend Angular
    ↓ HTTP/HTTPS
API
    ↓
Base de datos
```

Angular suele encargarse de:

- interfaz;
- navegación;
- estado del cliente;
- validación de formularios;
- comunicación con APIs;
- experiencia de usuario.

El backend administra normalmente:

- reglas de negocio;
- autenticación;
- persistencia;
- autorización;
- integridad de los datos.

## 0.2 HTTP

Métodos principales:

| Método | Uso típico |
|---|---|
| GET | consultar |
| POST | crear |
| PUT | reemplazar |
| PATCH | modificar parcialmente |
| DELETE | eliminar |

Estados comunes:

```text
200 OK
201 Created
204 No Content
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
409 Conflict
422 Unprocessable Content
500 Internal Server Error
```

## 0.3 SPA

SPA:

> Single Page Application.

El navegador carga una aplicación y la navegación posterior se administra principalmente en el cliente.

## 0.4 Repaso HTML

```html
<header>
  <h1>TaskFlow</h1>
</header>

<main>
  <section>
    <h2>Proyectos</h2>

    <form>
      <label for="name">Nombre</label>
      <input id="name" name="name">
    </form>
  </section>
</main>
```

Temas:

- HTML semántico;
- formularios;
- tablas;
- atributos;
- accesibilidad;
- ARIA cuando sea necesario.

## 0.5 Repaso CSS

```css
.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(16rem, 1fr));
  gap: 1rem;
}
```

Repasar:

- box model;
- cascada;
- especificidad;
- Flexbox;
- Grid;
- media queries;
- custom properties;
- responsive design.

## Práctica

Crear una pantalla estática del dashboard de TaskFlow únicamente con HTML y CSS.

---

# Módulo 1. JavaScript moderno para Angular

**Duración sugerida:** 6 horas

## Objetivos

- dominar sintaxis moderna;
- trabajar con objetos y arreglos;
- comprender asincronía;
- utilizar módulos.

## 1.1 Variables

```ts
const framework = 'Angular';
let version = 22;
```

Evitar `var` salvo que se esté analizando código heredado.

## 1.2 Funciones

```ts
function sum(a: number, b: number) {
  return a + b;
}
```

Arrow function:

```ts
const sum = (a: number, b: number) => a + b;
```

## 1.3 Objetos

```ts
const user = {
  id: 1,
  name: 'Ana',
  active: true
};
```

## 1.4 Desestructuración

```ts
const { name, active } = user;
```

## 1.5 Spread

```ts
const updatedUser = {
  ...user,
  active: false
};
```

Es esencial para actualización inmutable.

## 1.6 Arrays

```ts
const tasks = [
  { id: 1, title: 'Diseñar', completed: false },
  { id: 2, title: 'Programar', completed: true }
];
```

Dominar:

```text
map
filter
find
findIndex
some
every
reduce
sort
toSorted
```

Ejemplo:

```ts
const pendingTasks = tasks.filter(task => !task.completed);
```

## 1.7 Optional chaining

```ts
project.owner?.name
```

## 1.8 Nullish coalescing

```ts
const name = project.name ?? 'Sin nombre';
```

## 1.9 Promesas

```ts
const response = await fetch('/api/projects');
const projects = await response.json();
```

## 1.10 Módulos

```ts
export function calculateTotal() {}

import { calculateTotal } from './utils';
```

## Práctica

Construir un gestor de tareas en JavaScript sin Angular.

Debe permitir:

- agregar;
- editar;
- eliminar;
- completar;
- filtrar;
- calcular estadísticas.

---

# Módulo 2. TypeScript

**Duración sugerida:** 8 horas

## Objetivos

- comprender tipado estático;
- modelar dominios;
- trabajar con interfaces y tipos;
- utilizar genéricos;
- evitar abuso de `any`.

## 2.1 Tipos básicos

```ts
let name: string;
let age: number;
let active: boolean;
```

## 2.2 Inferencia

```ts
const framework = 'Angular';
```

TypeScript infiere:

```text
string
```

## 2.3 Arrays

```ts
const technologies: string[] = [
  'Angular',
  'TypeScript',
  'RxJS'
];
```

## 2.4 Interfaces

```ts
interface Project {
  id: number;
  name: string;
  description: string;
  status: ProjectStatus;
}
```

## 2.5 Type aliases

```ts
type ProjectStatus =
  | 'pending'
  | 'active'
  | 'completed';
```

## 2.6 Propiedades opcionales

```ts
interface User {
  id: number;
  name: string;
  avatarUrl?: string;
}
```

## 2.7 Readonly

```ts
interface User {
  readonly id: number;
  name: string;
}
```

## 2.8 Union types

```ts
let id: number | string;
```

## 2.9 Literal types

```ts
type Theme = 'light' | 'dark';
```

## 2.10 Generics

```ts
interface ApiResponse<T> {
  data: T;
  success: boolean;
}
```

Uso:

```ts
type ProjectResponse = ApiResponse<Project[]>;
```

## 2.11 Clases

```ts
class User {
  constructor(
    public id: number,
    public name: string
  ) {}
}
```

## 2.12 Utility Types

Dominar:

```text
Partial<T>
Required<T>
Readonly<T>
Pick<T>
Omit<T>
Record<K, V>
ReturnType<T>
Parameters<T>
```

Ejemplo:

```ts
type CreateProjectDto = Omit<Project, 'id'>;
```

## 2.13 `unknown` vs `any`

Evitar:

```ts
function parse(value: any) {}
```

Preferir:

```ts
function parse(value: unknown) {
  if (typeof value === 'string') {
    // seguro
  }
}
```

## 2.14 Narrowing

```ts
function printId(id: string | number) {
  if (typeof id === 'string') {
    console.log(id.toUpperCase());
  }
}
```

## 2.15 Type guards

```ts
function isProject(value: unknown): value is Project {
  return (
    typeof value === 'object' &&
    value !== null &&
    'id' in value &&
    'name' in value
  );
}
```

## Práctica

Modelar:

```text
User
Project
Task
Comment
ProjectStatus
TaskStatus
ApiResponse<T>
PaginatedResponse<T>
LoginRequest
LoginResponse
```

---

# Módulo 3. Introducción a Angular

**Duración sugerida:** 4 horas

## Objetivos

- comprender qué resuelve Angular;
- conocer su arquitectura;
- distinguir Angular de una biblioteca;
- comprender el ecosistema.

Angular integra:

```text
Componentes
Templates
Dependency Injection
Routing
HTTP
Forms
Signals
Testing
SSR
Build
CLI
```

## 3.1 Conceptos centrales

```text
Application
├── Components
├── Services
├── Routes
├── State
└── Infrastructure
```

## 3.2 Componente

Un componente combina:

```text
estado + comportamiento + template + estilos
```

## 3.3 Standalone

Angular moderno permite declarar dependencias directamente en componentes:

```ts
@Component({
  selector: 'app-project-list',
  imports: [],
  templateUrl: './project-list.html'
})
export class ProjectList {}
```

## 3.4 Bootstrap

Una aplicación moderna utiliza configuración como:

```ts
bootstrapApplication(App, appConfig);
```

## Práctica

Analizar la estructura de una aplicación Angular nueva e identificar el propósito de cada archivo.

---

# Módulo 4. Angular CLI y configuración del proyecto

**Duración sugerida:** 4 horas

## 4.1 Instalar Angular CLI

```bash
npm install -g @angular/cli
```

Verificar:

```bash
ng version
```

## 4.2 Crear aplicación

```bash
ng new taskflow
```

## 4.3 Ejecutar

```bash
cd taskflow
ng serve
```

## 4.4 Compilar

```bash
ng build
```

## 4.5 Generadores

```bash
ng generate component features/projects/project-list
ng generate service features/projects/data/project
ng generate guard core/auth/auth
ng generate interceptor core/http/auth
ng generate pipe shared/pipes/initials
ng generate directive shared/directives/autofocus
```

Abreviaturas:

```bash
ng g c
ng g s
ng g guard
ng g interceptor
ng g pipe
ng g directive
```

## 4.6 npm

Comandos esenciales:

```bash
npm install
npm install paquete
npm uninstall paquete
npm update
npm run start
npm run build
npm run test
```

## 4.7 package.json

Comprender:

```json
{
  "scripts": {},
  "dependencies": {},
  "devDependencies": {}
}
```

## 4.8 tsconfig

Conceptos:

- strict mode;
- paths;
- target;
- module;
- Angular compiler options.

## Práctica

Crear el repositorio de TaskFlow y realizar el primer commit:

```bash
git init
git add .
git commit -m "chore: initialize Angular application"
```

---

# Módulo 5. Arquitectura y componentes

**Duración sugerida:** 7 horas

## Objetivos

- crear componentes;
- separar responsabilidades;
- organizar una aplicación por feature.

## 5.1 Componente básico

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-project-card',
  template: `
    <article>
      <h2>{{ name }}</h2>
    </article>
  `
})
export class ProjectCard {
  name = 'Sistema ERP';
}
```

## 5.2 Template externo

```ts
@Component({
  selector: 'app-project-card',
  templateUrl: './project-card.html',
  styleUrl: './project-card.css'
})
export class ProjectCard {}
```

## 5.3 Estructura por funcionalidad

Preferir:

```text
features/
└── projects/
    ├── project-list/
    ├── project-detail/
    ├── project-form/
    ├── project.routes.ts
    └── data/
```

Evitar una estructura global excesivamente genérica:

```text
components/
services/
models/
```

cuando mezcla funcionalidades no relacionadas.

## 5.4 Componentes inteligentes y presentacionales

Una separación útil:

```text
Container
├── obtiene estado
├── coordina acciones
└── conecta servicios

Presentational
├── recibe datos
├── representa UI
└── emite eventos
```

No debe aplicarse dogmáticamente; depende del tamaño y reutilización.

## Práctica

Crear:

```text
AppShell
Header
Sidebar
Dashboard
ProjectList
ProjectCard
TaskList
TaskCard
```

---

# Módulo 6. Templates y data binding

**Duración sugerida:** 6 horas

## 6.1 Interpolación

```html
<h1>{{ project.name }}</h1>
```

## 6.2 Property binding

```html
<button [disabled]="saving">
  Guardar
</button>
```

## 6.3 Event binding

```html
<button (click)="save()">
  Guardar
</button>
```

## 6.4 Class binding

```html
<span [class.completed]="task.completed">
  {{ task.title }}
</span>
```

## 6.5 Style binding

```html
<div [style.width.%]="progress"></div>
```

## 6.6 Atributos

```html
<button [attr.aria-label]="label">
  ...
</button>
```

## 6.7 Two-way binding

```html
<input [(ngModel)]="name">
```

## 6.8 Expresiones de template

Mantenerlas simples.

Evitar lógica pesada:

```html
<!-- evitar -->
{{ projects.filter(...).sort(...).map(...) }}
```

Preferir:

```ts
visibleProjects = computed(() => {
  // transformación
});
```

## Práctica

Crear un listado interactivo con:

- búsqueda;
- estado de carga;
- selección;
- botón de acción;
- estilos condicionales.

---

# Módulo 7. Control flow, directivas y pipes

**Duración sugerida:** 6 horas

## 7.1 `@if`

```html
@if (loggedIn()) {
  <p>Bienvenido</p>
} @else {
  <a routerLink="/login">Iniciar sesión</a>
}
```

## 7.2 `@for`

```html
@for (project of projects(); track project.id) {
  <app-project-card [project]="project" />
} @empty {
  <p>No existen proyectos.</p>
}
```

## 7.3 `track`

Debe utilizar una identidad estable cuando sea posible:

```html
@for (project of projects(); track project.id) {
```

## 7.4 `@switch`

```html
@switch (task.status) {
  @case ('pending') {
    <span>Pendiente</span>
  }
  @case ('doing') {
    <span>En proceso</span>
  }
  @case ('done') {
    <span>Terminada</span>
  }
  @default {
    <span>Desconocido</span>
  }
}
```

## 7.5 Directivas

Ejemplo conceptual:

```ts
@Directive({
  selector: '[appAutofocus]'
})
export class AutofocusDirective {}
```

## 7.6 Pipes

Uso:

```html
{{ project.createdAt | date }}
{{ project.budget | currency }}
```

Pipe personalizado:

```ts
@Pipe({
  name: 'initials'
})
export class InitialsPipe implements PipeTransform {
  transform(name: string): string {
    return name
      .split(' ')
      .map(part => part[0])
      .join('')
      .toUpperCase();
  }
}
```

## Práctica

Crear:

- pipe `initials`;
- directiva `autofocus`;
- estados empty/loading/error;
- listado con `@for`.

---

# Módulo 8. Comunicación y ciclo de vida

**Duración sugerida:** 6 horas

## 8.1 Inputs

API moderna:

```ts
project = input.required<Project>();
```

Input opcional:

```ts
compact = input(false);
```

## 8.2 Outputs

```ts
deleted = output<number>();
```

Uso:

```ts
deleteProject() {
  this.deleted.emit(this.project().id);
}
```

Padre:

```html
<app-project-card
  [project]="project"
  (deleted)="removeProject($event)"
/>
```

## 8.3 Model inputs

Para ciertos escenarios de binding bidireccional:

```ts
value = model('');
```

## 8.4 Referencias de template

```html
<input #searchInput>
<button (click)="search(searchInput.value)">
  Buscar
</button>
```

## 8.5 View queries

Estudiar:

```text
viewChild
viewChildren
contentChild
contentChildren
```

## 8.6 Ciclo de vida

Comprender:

```text
constructor
ngOnInit
ngOnChanges
ngAfterViewInit
ngOnDestroy
```

y alternativas modernas relacionadas con renderizado.

## Regla práctica

No utilizar hooks simplemente porque existen.

Preferir estado derivado y APIs reactivas cuando resuelvan el problema de forma más declarativa.

## Práctica

Crear un componente de filtros reutilizable que reciba opciones y emita cambios.

---

# Módulo 9. Signals y reactividad moderna

**Duración sugerida:** 9 horas

## Objetivos

- comprender Signals;
- distinguir estado fuente y derivado;
- utilizar `computed`;
- utilizar `effect` correctamente;
- interoperar con RxJS.

## 9.1 Signal

```ts
count = signal(0);
```

Leer:

```ts
this.count();
```

Asignar:

```ts
this.count.set(10);
```

Actualizar:

```ts
this.count.update(value => value + 1);
```

## 9.2 Arrays

```ts
projects = signal<Project[]>([]);
```

Agregar:

```ts
this.projects.update(projects => [
  ...projects,
  newProject
]);
```

## 9.3 Objetos

Evitar mutar:

```ts
this.user().name = 'Ana';
```

Preferir:

```ts
this.user.update(user => ({
  ...user,
  name: 'Ana'
}));
```

## 9.4 `computed`

```ts
completedProjects = computed(() =>
  this.projects()
    .filter(project => project.status === 'completed')
);
```

El estado derivado debe calcularse, no duplicarse.

Evitar:

```ts
projects = signal<Project[]>([]);
completedProjects = signal<Project[]>([]);
```

si el segundo valor puede derivarse del primero.

## 9.5 `effect`

```ts
effect(() => {
  localStorage.setItem(
    'theme',
    this.theme()
  );
});
```

Usos apropiados:

- integración con APIs imperativas;
- almacenamiento;
- logging;
- sincronización con elementos no reactivos.

Evitar utilizar `effect` para copiar estado entre signals.

## 9.6 `linkedSignal`

Útil cuando un estado depende de otro, pero sigue siendo modificable.

Ejemplo conceptual:

```text
lista de opciones
      ↓
selección inicial
      ↓
usuario puede cambiarla
```

## 9.7 `resource`

Modelo asíncrono reactivo:

```ts
userResource = resource({
  params: () => ({
    id: this.userId()
  }),
  loader: ({ params }) =>
    fetch(`/api/users/${params.id}`)
      .then(response => response.json())
});
```

Estudiar:

```text
value
status
isLoading
error
reload
```

## 9.8 `httpResource`

Analizar como opción cuando una consulta HTTP puede modelarse declarativamente con Signals.

## 9.9 Interoperabilidad con RxJS

Herramientas importantes:

```text
toSignal
toObservable
takeUntilDestroyed
rxResource
```

## Práctica

Crear un store local de proyectos con:

```text
projects
selectedProjectId
selectedProject
filter
filteredProjects
loading
error
```

---

# Módulo 10. Servicios e inyección de dependencias

**Duración sugerida:** 6 horas

## 10.1 Servicio

```ts
@Injectable({
  providedIn: 'root'
})
export class ProjectService {}
```

## 10.2 `inject`

```ts
private readonly projectService = inject(ProjectService);
```

## 10.3 Separación de responsabilidades

Evitar:

```text
Component
├── UI
├── HTTP
├── almacenamiento
├── reglas de negocio
├── autenticación
└── logs
```

Preferir:

```text
Component
    ↓
Facade / Store / Service
    ↓
API Service
    ↓
HttpClient
```

## 10.4 InjectionToken

Ejemplo:

```ts
export const API_URL =
  new InjectionToken<string>('API_URL');
```

Provisión:

```ts
{
  provide: API_URL,
  useValue: 'https://api.example.com'
}
```

## 10.5 Providers

Comprender:

```text
useClass
useValue
useFactory
useExisting
```

## 10.6 Jerarquía de inyectores

Comprender alcance:

- aplicación;
- ruta;
- componente;
- árbol descendiente.

## Práctica

Crear:

```text
ProjectApi
ProjectStore
AuthService
NotificationService
StorageService
```

---

# Módulo 11. Angular Router

**Duración sugerida:** 8 horas

## Objetivos

- diseñar navegación;
- utilizar parámetros;
- implementar lazy loading;
- proteger rutas.

## 11.1 Configuración

```ts
export const routes: Routes = [
  {
    path: '',
    redirectTo: 'dashboard',
    pathMatch: 'full'
  },
  {
    path: 'dashboard',
    loadComponent: () =>
      import('./features/dashboard/dashboard')
        .then(m => m.Dashboard)
  }
];
```

## 11.2 Router outlet

```html
<router-outlet />
```

## 11.3 RouterLink

```html
<a routerLink="/projects">
  Proyectos
</a>
```

## 11.4 Parámetros

Ruta:

```ts
{
  path: 'projects/:id',
  loadComponent: () =>
    import('./project-detail/project-detail')
      .then(m => m.ProjectDetail)
}
```

URL:

```text
/projects/42
```

## 11.5 Query parameters

```text
/projects?page=2&status=active
```

## 11.6 Navegación programática

```ts
private router = inject(Router);

openProject(id: number) {
  this.router.navigate(['/projects', id]);
}
```

## 11.7 Rutas hijas

```text
/projects/:id
/projects/:id/tasks
/projects/:id/settings
```

## 11.8 Lazy loading

Carga bajo demanda:

```ts
{
  path: 'projects',
  loadChildren: () =>
    import('./features/projects/project.routes')
      .then(m => m.PROJECT_ROUTES)
}
```

## 11.9 Guards

```ts
export const authGuard: CanActivateFn = () => {
  const auth = inject(AuthService);

  return auth.isAuthenticated()
    ? true
    : inject(Router).createUrlTree(['/login']);
};
```

Estudiar:

```text
CanActivate
CanActivateChild
CanDeactivate
CanMatch
```

## 11.10 Resolver

Analizar cuándo conviene resolver datos antes de activar una ruta y cuándo es preferible cargar dentro del componente.

## 11.11 404

```ts
{
  path: '**',
  loadComponent: () =>
    import('./shared/not-found/not-found')
      .then(m => m.NotFound)
}
```

## Práctica

Implementar:

```text
/login
/dashboard
/projects
/projects/:id
/projects/:id/edit
/tasks
/profile
/settings
```

---

# Módulo 12. Formularios

**Duración sugerida:** 10 horas

## 12.1 Estrategias

Angular dispone de diferentes enfoques:

```text
Template-driven Forms
Reactive Forms
Signal Forms
```

## 12.2 Template-driven

```html
<form #form="ngForm">
  <input
    name="name"
    [(ngModel)]="project.name"
    required
  >
</form>
```

Adecuados para formularios sencillos.

## 12.3 Reactive Forms

```ts
form = new FormGroup({
  name: new FormControl('', {
    nonNullable: true
  }),
  description: new FormControl('')
});
```

## 12.4 FormBuilder

```ts
private readonly fb = inject(FormBuilder);

form = this.fb.nonNullable.group({
  name: ['', Validators.required],
  description: [''],
  status: ['pending' as ProjectStatus]
});
```

## 12.5 Validadores

```ts
Validators.required
Validators.minLength(3)
Validators.maxLength(100)
Validators.email
Validators.pattern(...)
```

## 12.6 Validador personalizado

```ts
export function forbiddenName(
  control: AbstractControl
): ValidationErrors | null {
  return control.value === 'admin'
    ? { forbiddenName: true }
    : null;
}
```

## 12.7 Cross-field validation

Ejemplo:

```text
fecha inicio <= fecha fin
password === confirmPassword
```

## 12.8 FormArray

```ts
members = this.fb.array([
  this.fb.control('')
]);
```

## 12.9 Estados

Comprender:

```text
valid
invalid
dirty
pristine
touched
untouched
pending
```

## 12.10 Signal Forms

Analizar:

- modelo signal;
- esquema;
- validación;
- estado reactivo;
- interoperabilidad con Reactive Forms.

Ejemplo conceptual:

```ts
loginModel = signal({
  email: '',
  password: ''
});
```

## Práctica

Crear formulario profesional de proyecto:

```text
Nombre *
Descripción
Responsable *
Fecha de inicio *
Fecha de fin
Estado *
Prioridad *
Integrantes[]
Etiquetas[]
```

Debe incluir:

- validaciones;
- mensajes;
- estados;
- deshabilitado durante guardado;
- confirmación de salida si existen cambios sin guardar.

---

# Módulo 13. HTTP y APIs REST

**Duración sugerida:** 9 horas

## 13.1 Configurar HttpClient

```ts
provideHttpClient()
```

## 13.2 GET

```ts
getProjects() {
  return this.http.get<Project[]>(
    `${this.apiUrl}/projects`
  );
}
```

## 13.3 POST

```ts
createProject(dto: CreateProjectDto) {
  return this.http.post<Project>(
    `${this.apiUrl}/projects`,
    dto
  );
}
```

## 13.4 PUT

```ts
updateProject(
  id: number,
  dto: UpdateProjectDto
) {
  return this.http.put<Project>(
    `${this.apiUrl}/projects/${id}`,
    dto
  );
}
```

## 13.5 PATCH

```ts
updateStatus(
  id: number,
  status: ProjectStatus
) {
  return this.http.patch<Project>(
    `${this.apiUrl}/projects/${id}`,
    { status }
  );
}
```

## 13.6 DELETE

```ts
deleteProject(id: number) {
  return this.http.delete<void>(
    `${this.apiUrl}/projects/${id}`
  );
}
```

## 13.7 Parámetros

```ts
const params = {
  page: 1,
  size: 20,
  status: 'active'
};

return this.http.get<Project[]>(
  `${this.apiUrl}/projects`,
  { params }
);
```

## 13.8 Headers

```ts
new HttpHeaders({
  'X-Correlation-Id': correlationId
});
```

## 13.9 Interceptor funcional

```ts
export const authInterceptor: HttpInterceptorFn =
  (request, next) => {
    const auth = inject(AuthService);

    const token = auth.token();

    if (!token) {
      return next(request);
    }

    return next(
      request.clone({
        setHeaders: {
          Authorization: `Bearer ${token}`
        }
      })
    );
  };
```

## 13.10 Error interceptor

Centralizar cuando corresponda:

- errores de red;
- 401;
- 403;
- 500;
- correlation IDs;
- logging.

No convertir todos los errores en mensajes genéricos.

## 13.11 Tipado de respuestas

```ts
interface PaginatedResponse<T> {
  items: T[];
  page: number;
  pageSize: number;
  total: number;
}
```

## 13.12 CORS

Comprender:

- origen;
- preflight;
- headers;
- configuración del backend.

CORS no debe "solucionarse" desactivando seguridad del navegador.

## Práctica

Conectar TaskFlow con una API REST real o simulada.

---

# Módulo 14. RxJS y programación reactiva

**Duración sugerida:** 11 horas

## Objetivos

- comprender Observable;
- utilizar operadores;
- cancelar operaciones;
- evitar memory leaks.

## 14.1 Observable

```ts
const observable = new Observable<number>(
  observer => {
    observer.next(1);
    observer.next(2);
    observer.complete();
  }
);
```

## 14.2 Observable vs Promise

Una Promise representa normalmente un resultado futuro.

Un Observable puede modelar una secuencia de valores.

## 14.3 Pipe

```ts
source$.pipe(
  map(value => value * 2),
  filter(value => value > 10)
);
```

## 14.4 Operadores esenciales

### Transformación

```text
map
scan
```

### Efectos

```text
tap
finalize
```

### Filtrado

```text
filter
take
first
debounceTime
distinctUntilChanged
```

### Higher-order mapping

```text
switchMap
mergeMap
concatMap
exhaustMap
```

### Errores

```text
catchError
retry
retryWhen
```

### Combinación

```text
combineLatest
forkJoin
merge
concat
zip
```

## 14.5 `switchMap`

Buscador:

```ts
searchControl.valueChanges.pipe(
  debounceTime(300),
  distinctUntilChanged(),
  switchMap(term =>
    this.projectApi.search(term)
  )
);
```

Útil para:

- búsquedas;
- autocompletado;
- cambios de ruta;
- peticiones sustituibles.

## 14.6 `mergeMap`

Para operaciones concurrentes independientes.

## 14.7 `concatMap`

Para operaciones que deben mantener orden.

## 14.8 `exhaustMap`

Excelente para evitar dobles envíos:

```text
click
click
click
 ↓
exhaustMap
 ↓
primera operación hasta completar
```

## 14.9 `catchError`

```ts
this.api.getProjects().pipe(
  catchError(error => {
    return of([]);
  })
);
```

No ocultar errores sin una estrategia explícita.

## 14.10 Suscripciones

Evitar suscribirse manualmente cuando no es necesario.

Opciones:

- `async` pipe;
- `toSignal`;
- `resource`;
- `httpResource`.

## 14.11 Limpieza

Si hay una suscripción imperativa:

```ts
source$
  .pipe(takeUntilDestroyed())
  .subscribe();
```

## 14.12 Signals vs RxJS

### Signals

Especialmente adecuados para:

```text
estado de UI
estado síncrono
estado derivado
vista
```

### RxJS

Especialmente adecuado para:

```text
event streams
WebSockets
cancelación
debounce
composición asíncrona
flujos HTTP complejos
```

Una arquitectura moderna puede utilizar ambos.

## Práctica

Crear buscador reactivo con:

- `debounceTime`;
- `distinctUntilChanged`;
- `switchMap`;
- estado de carga;
- error;
- cancelación.

---

# Módulo 15. Gestión de estado

**Duración sugerida:** 8 horas

## Objetivos

- identificar tipos de estado;
- evitar estado global innecesario;
- diseñar stores con Signals;
- conocer NgRx.

## 15.1 Tipos de estado

```text
UI local
Feature state
Session state
Server state
URL state
Global application state
```

## 15.2 Estado local

```ts
open = signal(false);
```

## 15.3 Estado de feature

```ts
@Injectable()
export class ProjectStore {
  readonly projects = signal<Project[]>([]);
  readonly loading = signal(false);
  readonly error = signal<string | null>(null);

  readonly activeProjects = computed(() =>
    this.projects().filter(
      project => project.status === 'active'
    )
  );
}
```

## 15.4 Encapsulación

Preferir:

```ts
private readonly _projects = signal<Project[]>([]);

readonly projects = this._projects.asReadonly();
```

## 15.5 Actualizaciones

```ts
add(project: Project) {
  this._projects.update(projects => [
    ...projects,
    project
  ]);
}
```

## 15.6 Estado en URL

Filtros que el usuario debería poder compartir o recargar pueden pertenecer al URL:

```text
/projects?status=active&page=2
```

No todo filtro debe almacenarse globalmente.

## 15.7 Cuándo usar una biblioteca de estado

Evaluar NgRx cuando existan:

- múltiples dominios interdependientes;
- flujos complejos;
- auditoría de cambios;
- efectos complejos;
- equipo amplio;
- necesidad clara de convenciones globales.

No introducir NgRx solo porque el proyecto utiliza Angular.

## 15.8 Conceptos de NgRx

Introducción:

```text
Store
Actions
Reducers
Selectors
Effects
Entity
Signal Store
```

Este módulo no requiere convertir todo TaskFlow a NgRx; el objetivo es poder tomar una decisión arquitectónica informada.

## Práctica

Implementar `ProjectStore` con Signals y comparar su complejidad conceptual con una solución de estado global.

---

# Módulo 16. Autenticación, autorización y seguridad

**Duración sugerida:** 8 horas

## Objetivos

- implementar flujo de login;
- proteger rutas;
- comprender límites de seguridad frontend.

## 16.1 Autenticación

Flujo simplificado:

```text
Login Form
   ↓
POST /auth/login
   ↓
Servidor valida
   ↓
Token / sesión
   ↓
Cliente actualiza sesión
```

## 16.2 Modelo

```ts
interface AuthUser {
  id: string;
  name: string;
  roles: string[];
}
```

## 16.3 AuthService

```ts
@Injectable({
  providedIn: 'root'
})
export class AuthService {
  private readonly _user =
    signal<AuthUser | null>(null);

  readonly user = this._user.asReadonly();

  readonly authenticated = computed(
    () => this._user() !== null
  );
}
```

## 16.4 Guard

```ts
export const authGuard: CanActivateFn = () => {
  const auth = inject(AuthService);
  const router = inject(Router);

  return auth.authenticated()
    ? true
    : router.createUrlTree(['/login']);
};
```

## 16.5 Roles

```ts
export const adminGuard: CanActivateFn = () => {
  const auth = inject(AuthService);

  return auth.user()?.roles.includes('admin')
    ?? false;
};
```

## Advertencia esencial

Un guard **no implementa seguridad real del backend**.

El servidor debe validar siempre:

- identidad;
- permisos;
- propiedad del recurso;
- entrada recibida.

## 16.6 Tokens

Analizar:

- cookies `HttpOnly`;
- cookies `Secure`;
- `SameSite`;
- access token;
- refresh token;
- riesgos de `localStorage`.

No presentar `localStorage` como ubicación universalmente segura para tokens sensibles.

## 16.7 XSS

Buenas prácticas:

- evitar HTML no confiable;
- no utilizar `bypassSecurityTrust...` sin comprender riesgos;
- no construir HTML desde entrada del usuario;
- utilizar mecanismos de sanitización de Angular.

## 16.8 CSRF

Comprender cuándo aplica y cómo intervienen:

- cookies;
- SameSite;
- tokens anti-CSRF;
- configuración de backend.

## Práctica

Implementar:

- login;
- logout;
- restauración de sesión;
- guard;
- interceptor;
- menú condicionado por permisos.

---

# Módulo 17. UI, estilos y accesibilidad

**Duración sugerida:** 6 horas

## 17.1 Estilos por componente

```css
:host {
  display: block;
}
```

## 17.2 Design tokens

```css
:root {
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --radius-md: 0.5rem;
}
```

## 17.3 Responsive design

Pensar desde tamaños pequeños hacia grandes.

## 17.4 Componentización

Crear UI reusable:

```text
Button
Card
Modal
Dialog
Badge
Spinner
EmptyState
ErrorState
Pagination
```

## 17.5 Angular Material

Revisar:

```bash
ng add @angular/material
```

Comprender:

- theming;
- componentes;
- accesibilidad;
- CDK.

## 17.6 Accesibilidad

Principios:

- HTML semántico;
- navegación por teclado;
- foco visible;
- labels;
- contraste;
- textos alternativos;
- `aria-*` solo cuando aporte semántica necesaria.

Ejemplo:

```html
<label for="project-name">
  Nombre del proyecto
</label>

<input
  id="project-name"
  [formControl]="form.controls.name"
>
```

Evitar:

```html
<div (click)="save()">Guardar</div>
```

Preferir:

```html
<button type="button" (click)="save()">
  Guardar
</button>
```

## Práctica

Realizar una auditoría básica de accesibilidad del dashboard.

---

# Módulo 18. Testing con Vitest

**Duración sugerida:** 10 horas

Angular moderno utiliza Vitest como runner principal de pruebas unitarias.

## Objetivos

- comprender test unitario;
- probar componentes;
- probar servicios;
- probar HTTP;
- probar routing.

## 18.1 Estructura

```ts
describe('ProjectService', () => {
  it('should ...', () => {
    // arrange
    // act
    // assert
  });
});
```

## 18.2 AAA

```text
Arrange
Act
Assert
```

## 18.3 Servicio

```ts
describe('ProjectStore', () => {
  it('adds a project', () => {
    // ...
  });
});
```

## 18.4 Component Test

Estudiar:

```text
TestBed
ComponentFixture
query
events
bindings
```

## 18.5 HTTP Testing

Probar:

- URL;
- método;
- body;
- headers;
- respuesta;
- error.

## 18.6 Router Testing

Probar:

- navegación;
- guards;
- parámetros;
- redirecciones.

## 18.7 Qué probar

Prioridad:

```text
reglas
transformaciones
estados
comportamiento
integraciones internas
casos límite
errores
```

Evitar tests que solo duplican la implementación.

## 18.8 Cobertura

La cobertura es una métrica, no una meta por sí sola.

Un 100 % de cobertura no garantiza buenas pruebas.

## Práctica

Crear pruebas para:

```text
ProjectStore
ProjectApi
ProjectForm
ProjectCard
authGuard
authInterceptor
```

---

# Módulo 19. Rendimiento y optimización

**Duración sugerida:** 7 horas

## 19.1 Medir antes de optimizar

Herramientas:

- browser DevTools;
- Performance;
- Network;
- Lighthouse;
- Angular DevTools.

## 19.2 Detección de cambios

Comprender la relación entre:

- Signals;
- OnPush;
- zoneless;
- eventos;
- actualizaciones.

Angular moderno avanza hacia un modelo zoneless y eficiente.

## 19.3 Estado inmutable

Evitar mutaciones difíciles de rastrear.

Preferir:

```ts
this.projects.update(items =>
  items.map(project =>
    project.id === updated.id
      ? updated
      : project
  )
);
```

## 19.4 Lazy loading

Separar features:

```text
auth
dashboard
projects
tasks
admin
```

## 19.5 `@defer`

Ejemplo:

```html
@defer (on viewport) {
  <app-analytics />
} @placeholder {
  <div>Cargando módulo...</div>
}
```

Triggers a estudiar:

```text
idle
viewport
interaction
hover
timer
immediate
when
```

## 19.6 Imágenes

Utilizar dimensiones apropiadas y estrategias modernas de carga.

## 19.7 Listas

Utilizar claves estables:

```html
@for (task of tasks(); track task.id) {
```

## 19.8 Bundle

Analizar:

- dependencias grandes;
- imports;
- lazy loading;
- librerías duplicadas.

## 19.9 Evitar cálculos en template

Mover cálculos a:

```text
computed
selectors
pipes puros
```

## Práctica

Comparar métricas antes y después de:

- lazy loading;
- `@defer`;
- optimización de lista;
- eliminación de dependencia innecesaria.

---

# Módulo 20. SSR, SSG e hidratación

**Duración sugerida:** 6 horas

## 20.1 CSR

Client-Side Rendering.

El navegador recibe la aplicación y genera principalmente la interfaz.

## 20.2 SSR

Server-Side Rendering.

El servidor genera HTML inicial.

Ventajas potenciales:

- contenido inicial más rápido;
- SEO;
- metadatos;
- experiencia inicial.

## 20.3 SSG

Static Site Generation.

Las páginas se generan previamente cuando el contenido puede conocerse antes de la petición.

## 20.4 Hidratación

El cliente reutiliza el HTML generado por el servidor y lo convierte en una aplicación interactiva.

## 20.5 Elegir estrategia

### CSR

Aplicaciones internas:

```text
ERP
CRM
panel administrativo
```

### SSR

Sitios públicos con contenido dinámico:

```text
e-commerce
portales
marketplaces
```

### SSG

Contenido relativamente estable:

```text
documentación
landing pages
blogs
catálogos estáticos
```

No son reglas absolutas.

## 20.6 Browser APIs

Cuidado con:

```ts
window
document
localStorage
navigator
```

en código ejecutado también en servidor.

## Práctica

Analizar qué partes de TaskFlow podrían beneficiarse de SSR y cuáles no.

---

# Módulo 21. Arquitectura profesional y buenas prácticas

**Duración sugerida:** 10 horas

## Objetivos

- diseñar features mantenibles;
- definir responsabilidades;
- evitar sobrearquitectura.

## 21.1 Arquitectura por feature

```text
features/
└── projects/
    ├── pages/
    ├── ui/
    ├── data-access/
    ├── state/
    ├── models/
    └── project.routes.ts
```

La profundidad debe adaptarse al tamaño del proyecto.

Un proyecto pequeño no necesita veinte carpetas por feature.

## 21.2 Capas conceptuales

```text
UI
 ↓
Feature / Facade / State
 ↓
Data Access
 ↓
Backend
```

## 21.3 Smart vs dumb

Utilizar la separación cuando reduzca acoplamiento.

No convertir cada elemento visual en una abstracción innecesaria.

## 21.4 DTO vs modelo de UI

Respuesta del servidor:

```ts
interface ProjectDto {
  project_id: string;
  project_name: string;
}
```

Modelo cliente:

```ts
interface Project {
  id: string;
  name: string;
}
```

Mapper:

```ts
function mapProject(dto: ProjectDto): Project {
  return {
    id: dto.project_id,
    name: dto.project_name
  };
}
```

Esto reduce acoplamiento con contratos externos cuando el proyecto lo necesita.

## 21.5 Principios SOLID

Aplicar con criterio:

- SRP;
- OCP;
- LSP;
- ISP;
- DIP.

Angular ya facilita DIP mediante inyección de dependencias.

## 21.6 DRY

No eliminar toda repetición automáticamente.

A veces dos fragmentos similares representan conceptos distintos.

## 21.7 KISS

Preferir la solución más sencilla que cubra adecuadamente el requisito.

## 21.8 YAGNI

No implementar:

- store global;
- microfrontends;
- WebSockets;
- arquitectura hexagonal;
- event bus;

si el proyecto no lo necesita.

## 21.9 Manejo de errores

Separar:

```text
Network error
Validation error
Authorization error
Domain error
Unexpected error
```

## 21.10 Logging

No dejar:

```ts
console.log(...)
```

dispersos como mecanismo de observabilidad de producción.

## 21.11 Configuración

Separar:

- constantes;
- configuración de entorno;
- URLs;
- feature flags.

Nunca incluir secretos en el frontend.

## 21.12 Nomenclatura

Mantener nombres precisos:

```text
ProjectList
ProjectDetail
ProjectApi
ProjectStore
ProjectForm
```

Evitar:

```text
Manager
Helper
Utils
CommonService
GlobalService
```

cuando no expresan responsabilidad clara.

## 21.13 Imports

Mantener dependencias explícitas y evitar ciclos.

## Práctica

Realizar una revisión arquitectónica de TaskFlow y refactorizar:

- duplicación;
- responsabilidades;
- estado;
- nombres;
- dependencias.

---

# Módulo 22. Build, configuración y despliegue

**Duración sugerida:** 6 horas

## 22.1 Desarrollo

```bash
ng serve
```

## 22.2 Producción

```bash
ng build
```

## 22.3 Configuraciones

Comprender:

```text
development
staging
production
```

## 22.4 Variables y secretos

Regla:

> Todo lo que llega al navegador debe considerarse visible para el usuario.

Nunca colocar:

```text
password de BD
private API secret
JWT signing key
cloud secret key
```

en Angular.

## 22.5 Configuración runtime

Analizar cuándo la configuración debe cargarse al iniciar la aplicación en vez de quedar incorporada al bundle.

## 22.6 Hosting estático

Opciones:

- Firebase Hosting;
- Netlify;
- Vercel;
- Cloudflare;
- Azure Static Web Apps;
- AWS;
- Nginx/Apache.

## 22.7 SPA fallback

Un hosting SPA debe redirigir rutas del cliente hacia el documento principal cuando corresponda.

Ejemplo conceptual:

```text
/projects/42
      ↓
index.html
      ↓
Angular Router
```

## 22.8 CI/CD

Pipeline conceptual:

```text
Push
 ↓
Install
 ↓
Lint
 ↓
Test
 ↓
Build
 ↓
Deploy
```

## Práctica

Generar build de producción y desplegar TaskFlow en una plataforma elegida.

---

# Módulo 23. Angular heredado y migración

**Duración sugerida:** 6 horas

Un desarrollador intermedio debe poder leer proyectos anteriores.

## 23.1 NgModule

Código tradicional:

```ts
@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule
  ],
  bootstrap: [
    AppComponent
  ]
})
export class AppModule {}
```

Comprender:

```text
declarations
imports
providers
exports
bootstrap
```

## 23.2 Inputs tradicionales

```ts
@Input()
project!: Project;
```

## 23.3 Outputs tradicionales

```ts
@Output()
deleted = new EventEmitter<number>();
```

## 23.4 Estructuras históricas

Es frecuente encontrar:

```html
<div *ngIf="condition"></div>

<div *ngFor="let item of items"></div>
```

El estudiante debe reconocerlas aunque el curso privilegie control flow moderno.

## 23.5 Constructor injection

Código existente:

```ts
constructor(
  private projectService: ProjectService
) {}
```

Sigue siendo importante saber leerlo.

## 23.6 Zone.js

Comprender su función histórica en Angular y la transición hacia aplicaciones zoneless.

## 23.7 Migración

Proceso:

```text
Actualizar Angular
   ↓
Ejecutar migraciones oficiales
   ↓
Resolver incompatibilidades
   ↓
Ejecutar tests
   ↓
Migrar patrones gradualmente
```

No realizar refactorizaciones masivas simultáneamente con una actualización crítica sin pruebas adecuadas.

## 23.8 `ng update`

```bash
ng update
```

Consultar:

```bash
ng update @angular/core @angular/cli
```

## Práctica

Tomar un componente con:

- `NgModule`;
- `@Input`;
- `@Output`;
- `*ngIf`;
- `*ngFor`;

y convertirlo progresivamente a estilo moderno.

---

# Módulo 24. Proyecto integrador

**Duración sugerida:** 15–20 horas

# TaskFlow — entrega final

## 24.1 Requisitos funcionales

### Autenticación

- login;
- logout;
- sesión;
- guard;
- interceptor.

### Dashboard

Mostrar:

- cantidad de proyectos;
- proyectos activos;
- tareas pendientes;
- tareas completadas;
- actividades recientes.

### Proyectos

Implementar:

```text
GET    /projects
GET    /projects/:id
POST   /projects
PUT    /projects/:id
DELETE /projects/:id
```

### Tareas

Implementar:

```text
GET    /tasks
POST   /tasks
PATCH  /tasks/:id
DELETE /tasks/:id
```

### Filtros

Permitir:

- texto;
- estado;
- prioridad;
- responsable.

### Formularios

Validar:

- campos obligatorios;
- longitudes;
- fechas;
- relaciones entre campos.

## 24.2 Requisitos técnicos

La aplicación debe utilizar:

- Angular standalone;
- TypeScript estricto;
- Signals;
- `computed`;
- servicios;
- Dependency Injection;
- Router;
- lazy loading;
- Reactive Forms o Signal Forms;
- HttpClient;
- interceptor;
- RxJS;
- guards;
- pruebas;
- manejo de errores.

## 24.3 Requisitos de calidad

Debe incluir:

```text
README
arquitectura consistente
nombres claros
sin secretos
manejo de loading
manejo de empty state
manejo de error state
responsive design
accesibilidad básica
```

## 24.4 Arquitectura sugerida

```text
src/app/
│
├── core/
│   ├── auth/
│   │   ├── auth.service.ts
│   │   ├── auth.guard.ts
│   │   └── auth.models.ts
│   │
│   ├── http/
│   │   ├── auth.interceptor.ts
│   │   └── error.interceptor.ts
│   │
│   └── config/
│
├── shared/
│   ├── ui/
│   │   ├── button/
│   │   ├── spinner/
│   │   ├── empty-state/
│   │   └── error-state/
│   │
│   ├── directives/
│   └── pipes/
│
├── features/
│   ├── auth/
│   │
│   ├── dashboard/
│   │
│   ├── projects/
│   │   ├── pages/
│   │   ├── ui/
│   │   ├── data-access/
│   │   ├── state/
│   │   ├── models/
│   │   └── project.routes.ts
│   │
│   ├── tasks/
│   │
│   └── users/
│
├── app.config.ts
└── app.routes.ts
```

## 24.5 Flujo técnico esperado

```text
UI
 ↓
ProjectStore
 ↓
ProjectApi
 ↓
HttpClient
 ↓
Interceptor
 ↓
REST API
```

Respuesta:

```text
REST API
 ↓
ProjectApi
 ↓
ProjectStore
 ↓
Signal
 ↓
computed
 ↓
Template
```

## 24.6 Entregables

1. repositorio Git;
2. código fuente;
3. README;
4. diagrama de arquitectura;
5. aplicación desplegada;
6. colección o documentación de API;
7. pruebas automatizadas;
8. informe breve de decisiones técnicas.

---

# Evaluación del curso

Distribución sugerida:

| Elemento | Valor |
|---|---:|
| Prácticas por módulo | 25 % |
| Ejercicios técnicos | 15 % |
| Evaluación de fundamentos | 10 % |
| Evaluación intermedia | 10 % |
| Proyecto integrador | 35 % |
| Documentación y presentación | 5 % |

## Rúbrica del proyecto

### Funcionalidad — 30 %

- CRUD correcto;
- routing;
- formularios;
- autenticación;
- manejo de estados.

### Arquitectura — 20 %

- separación de responsabilidades;
- estructura;
- servicios;
- estado;
- tipado.

### Calidad — 15 %

- legibilidad;
- naming;
- reutilización;
- simplicidad.

### Reactividad — 10 %

- Signals;
- RxJS;
- estado derivado;
- ausencia de suscripciones innecesarias.

### Testing — 10 %

- servicios;
- componentes;
- casos importantes;
- errores.

### UX y accesibilidad — 10 %

- estados;
- formularios;
- navegación;
- responsive;
- teclado.

### Documentación — 5 %

- instalación;
- ejecución;
- arquitectura;
- decisiones.

---

# Ruta de profundización

Después del nivel intermedio se recomienda continuar con:

## Angular avanzado

```text
Advanced Signals
custom equality
linkedSignal
resources
httpResource
advanced DI
route providers
SSR avanzado
hydration
incremental hydration
performance profiling
custom build configuration
```

## RxJS avanzado

```text
Subjects
BehaviorSubject
ReplaySubject
Schedulers
multicasting
custom operators
error recovery
WebSockets
```

## Estado

```text
NgRx Store
NgRx Effects
NgRx Entity
NgRx Signal Store
```

## Arquitectura

```text
DDD frontend
hexagonal architecture
monorepos
Nx
microfrontends
Module Federation
design systems
```

## Testing

```text
Vitest avanzado
Testing Library
Playwright
Cypress
contract testing
visual regression
```

## Backend recomendado

Para una ruta full-stack TypeScript:

```text
Angular
   ↓
NestJS
   ↓
PostgreSQL
```

Temas:

```text
REST
OpenAPI
JWT / sessions
PostgreSQL
ORM
Docker
testing
CI/CD
```

---

# Checklist de competencias

El estudiante debería poder marcar lo siguiente al finalizar.

## JavaScript

- [ ] Comprendo `const` y `let`.
- [ ] Utilizo destructuring.
- [ ] Utilizo spread.
- [ ] Trabajo con `map`, `filter`, `find` y `reduce`.
- [ ] Comprendo Promises y `async/await`.
- [ ] Comprendo ES Modules.

## TypeScript

- [ ] Creo interfaces.
- [ ] Creo type aliases.
- [ ] Utilizo unions.
- [ ] Utilizo generics.
- [ ] Utilizo utility types.
- [ ] Evito `any` innecesario.
- [ ] Comprendo narrowing.

## Angular

- [ ] Creo un proyecto.
- [ ] Creo componentes.
- [ ] Utilizo standalone components.
- [ ] Utilizo data binding.
- [ ] Utilizo `@if`.
- [ ] Utilizo `@for`.
- [ ] Utilizo `@switch`.
- [ ] Creo pipes.
- [ ] Creo directivas.

## Comunicación

- [ ] Utilizo `input()`.
- [ ] Utilizo `output()`.
- [ ] Comprendo el ciclo de vida.
- [ ] Utilizo view queries cuando son necesarias.

## Signals

- [ ] Utilizo `signal`.
- [ ] Utilizo `computed`.
- [ ] Utilizo `effect` correctamente.
- [ ] Evito duplicar estado derivado.
- [ ] Comprendo `resource`.
- [ ] Interopero Signals y RxJS.

## Dependency Injection

- [ ] Creo servicios.
- [ ] Utilizo `inject`.
- [ ] Comprendo providers.
- [ ] Comprendo `InjectionToken`.

## Router

- [ ] Creo rutas.
- [ ] Utilizo parámetros.
- [ ] Utilizo query params.
- [ ] Implemento lazy loading.
- [ ] Creo guards.
- [ ] Manejo 404.

## Forms

- [ ] Creo Reactive Forms.
- [ ] Creo validadores.
- [ ] Utilizo FormArray.
- [ ] Manejo errores.
- [ ] Comprendo Signal Forms.

## HTTP

- [ ] Utilizo HttpClient.
- [ ] GET.
- [ ] POST.
- [ ] PUT/PATCH.
- [ ] DELETE.
- [ ] Creo interceptores.
- [ ] Manejo errores.
- [ ] Comprendo CORS.

## RxJS

- [ ] Comprendo Observables.
- [ ] Utilizo `map`.
- [ ] Utilizo `switchMap`.
- [ ] Distingo `mergeMap`, `concatMap` y `exhaustMap`.
- [ ] Utilizo `catchError`.
- [ ] Utilizo `debounceTime`.
- [ ] Evito memory leaks.

## Arquitectura

- [ ] Organizo por feature.
- [ ] Separo UI y acceso a datos.
- [ ] Distingo estado local y global.
- [ ] Evito sobrearquitectura.
- [ ] Diseño modelos y DTOs conscientemente.

## Seguridad

- [ ] Comprendo autenticación.
- [ ] Comprendo autorización.
- [ ] Sé que guards no sustituyen autorización del servidor.
- [ ] Comprendo XSS.
- [ ] Comprendo CSRF.
- [ ] No almaceno secretos en frontend.

## Testing

- [ ] Escribo pruebas con Vitest.
- [ ] Pruebo servicios.
- [ ] Pruebo componentes.
- [ ] Pruebo HTTP.
- [ ] Pruebo guards.

## Rendimiento

- [ ] Implemento lazy loading.
- [ ] Utilizo `@defer`.
- [ ] Utilizo `track`.
- [ ] Comprendo zoneless.
- [ ] Sé medir antes de optimizar.

## Producción

- [ ] Genero un build.
- [ ] Configuro entornos.
- [ ] Despliego una SPA.
- [ ] Comprendo CI/CD básico.

---

# Ejercicios adicionales

## Ejercicio 1 — Contador reactivo

Crear:

```text
+
-
reset
```

con Signals.

## Ejercicio 2 — Lista de usuarios

Consumir:

```text
GET /users
```

Mostrar:

```text
loading
success
empty
error
```

## Ejercicio 3 — Search

Crear buscador con:

```text
FormControl
debounceTime
distinctUntilChanged
switchMap
```

## Ejercicio 4 — Dashboard

Signals:

```text
tasks
completedTasks
pendingTasks
completionRate
```

## Ejercicio 5 — Formulario dinámico

Crear proyecto con una cantidad dinámica de integrantes.

## Ejercicio 6 — Autenticación

Implementar:

```text
AuthService
authGuard
authInterceptor
```

## Ejercicio 7 — Estado

Crear:

```text
ProjectStore
```

con:

```text
projects
loading
error
selectedProject
filteredProjects
```

## Ejercicio 8 — Optimización

Implementar:

```text
lazy loading
@defer
track
```

y comparar comportamiento.

## Ejercicio 9 — Testing

Escribir tests para:

```text
ProjectStore
ProjectApi
ProjectCard
ProjectForm
```

## Ejercicio 10 — Refactor legacy

Migrar un módulo tradicional hacia standalone y control flow moderno.

---

# Preguntas de repaso

## Fundamentos

1. ¿Qué diferencia existe entre frontend y backend?
2. ¿Qué es una SPA?
3. ¿Qué diferencia existe entre CSR y SSR?
4. ¿Qué función cumple TypeScript?

## Angular

5. ¿Qué es un componente?
6. ¿Qué problema resuelve Dependency Injection?
7. ¿Qué es un standalone component?
8. ¿Cuándo debe utilizarse un servicio?

## Signals

9. ¿Qué diferencia existe entre `signal` y `computed`?
10. ¿Cuándo utilizar `effect`?
11. ¿Por qué no es conveniente duplicar estado derivado?

## RxJS

12. ¿Qué es un Observable?
13. ¿Cuándo usar `switchMap`?
14. ¿Cuál es la diferencia entre `switchMap` y `mergeMap`?
15. ¿Cuándo utilizar `exhaustMap`?

## HTTP

16. ¿Qué diferencia existe entre POST, PUT y PATCH?
17. ¿Qué es un interceptor?
18. ¿Qué significa un error HTTP 401?
19. ¿Cuál es la diferencia entre 401 y 403?

## Router

20. ¿Qué es lazy loading?
21. ¿Para qué sirve un guard?
22. ¿Por qué un guard no constituye seguridad del backend?

## Arquitectura

23. ¿Qué estado debería mantenerse en URL?
24. ¿Cuándo introducir un store global?
25. ¿Qué señales indican sobrearquitectura?

## Testing

26. ¿Qué debería probarse?
27. ¿Por qué 100 % de cobertura no garantiza calidad?
28. ¿Cuál es la finalidad de Arrange-Act-Assert?

## Producción

29. ¿Por qué no deben almacenarse secretos en Angular?
30. ¿Qué necesita un servidor para soportar correctamente rutas SPA?

---

# Glosario

| Término | Significado |
|---|---|
| SPA | Single Page Application |
| CSR | Client-Side Rendering |
| SSR | Server-Side Rendering |
| SSG | Static Site Generation |
| DI | Dependency Injection |
| Signal | Primitiva reactiva de Angular |
| Observable | Flujo de datos de RxJS |
| Pipe | Transformación para templates |
| Guard | Control de navegación |
| Interceptor | Middleware de peticiones HTTP |
| Lazy loading | Carga bajo demanda |
| Hydration | Reutilización en cliente del HTML renderizado en servidor |
| DTO | Data Transfer Object |
| Store | Contenedor de estado |
| CRUD | Create, Read, Update, Delete |
| API | Application Programming Interface |
| REST | Estilo arquitectónico para servicios web |
| CORS | Cross-Origin Resource Sharing |
| XSS | Cross-Site Scripting |
| CSRF | Cross-Site Request Forgery |
| CI/CD | Continuous Integration / Continuous Delivery |

---

# Referencias oficiales

Las siguientes fuentes deben utilizarse como referencia primaria al avanzar en el curso:

- Angular Documentation: https://angular.dev/
- Angular CLI: https://angular.dev/tools/cli
- Angular Components: https://angular.dev/guide/components
- Templates: https://angular.dev/guide/templates
- Signals: https://angular.dev/guide/signals
- Dependency Injection: https://angular.dev/guide/di
- Routing: https://angular.dev/guide/routing
- Forms: https://angular.dev/guide/forms
- HTTP Client: https://angular.dev/guide/http
- Testing: https://angular.dev/guide/testing
- Zoneless Angular: https://angular.dev/guide/zoneless
- Angular Style Guide: https://angular.dev/style-guide
- Angular Version Compatibility: https://angular.dev/reference/versions
- Angular Releases: https://angular.dev/reference/releases
- Angular Roadmap: https://angular.dev/roadmap
- RxJS: https://rxjs.dev/
- TypeScript: https://www.typescriptlang.org/docs/
- Node.js: https://nodejs.org/docs/latest/api/
- MDN Web Docs: https://developer.mozilla.org/

---

# Ruta sugerida de estudio

```text
Fundamentos web
      ↓
JavaScript
      ↓
TypeScript
      ↓
Angular CLI
      ↓
Components
      ↓
Templates
      ↓
Signals
      ↓
Services + DI
      ↓
Router
      ↓
Forms
      ↓
HTTP
      ↓
RxJS
      ↓
State
      ↓
Authentication
      ↓
Testing
      ↓
Performance
      ↓
SSR / SSG
      ↓
Architecture
      ↓
Deployment
      ↓
Proyecto final
```

---

# Conclusión

Dominar Angular no consiste únicamente en aprender comandos o memorizar APIs. Un desarrollador Angular competente debe comprender tres dimensiones simultáneamente:

```text
Framework
+
Programación reactiva
+
Arquitectura de software
```

El nivel fundamental proporciona la capacidad de construir componentes, formularios, navegación y comunicación HTTP.

El nivel intermedio exige además comprender:

- estado;
- RxJS;
- Signals;
- arquitectura;
- testing;
- seguridad;
- rendimiento;
- despliegue;
- mantenimiento.

La meta final del curso es que el estudiante pueda enfrentarse a una aplicación Angular real, comprender su estructura, implementar nuevas funcionalidades y tomar decisiones técnicas razonadas sin depender exclusivamente de tutoriales paso a paso.

---

**Fin del curso**
