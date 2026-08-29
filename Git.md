# Curso completo de Git y tecnologías relacionadas

## Nivel Fundamentos e Intermedio

### Duración sugerida

**45 a 50 horas**

### Nivel

Fundamentos → Intermedio

### Modalidad

Presencial, virtual, híbrida o autoestudio.

### Enfoque

Teórico-práctico, orientado al desarrollo profesional de software y al trabajo colaborativo.

---

# 1. Objetivo general

Desarrollar las competencias necesarias para utilizar Git de manera profesional como sistema de control de versiones distribuido, administrando repositorios, ramas, historial, conflictos, colaboración remota, estrategias de integración, recuperación ante errores y automatización de flujos de trabajo.

Al finalizar el curso, el participante deberá ser capaz de integrarse de manera segura a un equipo de desarrollo que utilice GitHub, GitLab u otra plataforma basada en Git.

---

# 2. Competencias a desarrollar

Al finalizar el curso, el participante podrá:

1. Explicar qué problema resuelve un sistema de control de versiones.
2. Diferenciar Git de GitHub, GitLab y otros servicios.
3. Crear y clonar repositorios.
4. Comprender Working Tree, Staging Area y Repository.
5. Crear commits correctamente.
6. Consultar y analizar el historial.
7. Trabajar profesionalmente con ramas.
8. Fusionar ramas.
9. Resolver conflictos.
10. Trabajar con repositorios remotos.
11. Utilizar `fetch`, `pull` y `push`.
12. Comprender `merge` y `rebase`.
13. Utilizar Pull Requests y Merge Requests.
14. Diseñar estrategias de ramas.
15. Utilizar Conventional Commits.
16. Deshacer cambios de manera segura.
17. Recuperar trabajo aparentemente perdido.
18. Utilizar `stash`.
19. Utilizar `cherry-pick`.
20. Crear tags y versiones.
21. Utilizar `reflog`.
22. Diagnosticar errores mediante `bisect`.
23. Utilizar hooks.
24. Trabajar con submodules.
25. Utilizar worktrees.
26. Comprender Git LFS.
27. Aplicar seguridad a repositorios.
28. Integrar Git con CI/CD.
29. Diseñar un flujo colaborativo para equipos.
30. Administrar correctamente un repositorio de producción.

---

# 3. Requisitos previos

Se recomienda conocimiento básico de:

* sistemas operativos;
* archivos y directorios;
* terminal;
* desarrollo de software;
* algún lenguaje de programación.

No se requiere conocimiento previo de Git.

---

# 4. Estructura del curso

## BLOQUE I — Fundamentos

### Módulo 1. Control de versiones

### Módulo 2. Introducción a Git

### Módulo 3. Instalación y configuración

### Módulo 4. Arquitectura interna básica

### Módulo 5. Primer repositorio

### Módulo 6. Staging Area

### Módulo 7. Commits

### Módulo 8. Historial y diferencias

### Módulo 9. `.gitignore`

## BLOQUE II — Trabajo con ramas

### Módulo 10. Ramas

### Módulo 11. Estrategias de nomenclatura

### Módulo 12. Merge

### Módulo 13. Conflictos

### Módulo 14. Rebase

### Módulo 15. Rebase interactivo

## BLOQUE III — Git remoto y colaboración

### Módulo 16. Repositorios remotos

### Módulo 17. Fetch, Pull y Push

### Módulo 18. GitHub y GitLab

### Módulo 19. Pull Request / Merge Request

### Módulo 20. Estrategias de trabajo colaborativo

### Módulo 21. Conventional Commits

## BLOQUE IV — Git intermedio

### Módulo 22. Restore, Reset y Revert

### Módulo 23. Reflog

### Módulo 24. Stash

### Módulo 25. Cherry-pick

### Módulo 26. Tags y versiones

### Módulo 27. Bisect y Blame

### Módulo 28. Hooks

### Módulo 29. Worktrees

### Módulo 30. Submodules

### Módulo 31. Git LFS

### Módulo 32. Seguridad

## BLOQUE V — Git profesional

### Módulo 33. Git + CI/CD

### Módulo 34. Administración de repositorios

### Módulo 35. Troubleshooting

### Módulo 36. Proyecto integrador

---

# MÓDULO 1. CONTROL DE VERSIONES

## 1.1 El problema

Supongamos un proyecto:

```text
proyecto/
├── app.go
├── database.go
├── auth.go
└── config.go
```

Se realizan modificaciones durante meses.

Sin control de versiones terminamos con:

```text
proyecto-final/
proyecto-final2/
proyecto-final-ahora-si/
proyecto-final-definitivo/
proyecto-final-definitivo2/
```

Esto genera problemas:

* no sabemos qué cambió;
* no sabemos quién realizó el cambio;
* no sabemos por qué cambió;
* no podemos regresar fácilmente;
* varias personas pueden sobrescribir trabajo;
* resulta difícil identificar cuándo apareció un error.

---

# 1.2 ¿Qué hace un sistema de control de versiones?

Registra la evolución de un proyecto.

Conceptualmente:

```text
Versión 1
   │
   ▼
Versión 2
   │
   ▼
Versión 3
   │
   ▼
Versión 4
```

Podemos regresar a cualquier estado anterior.

---

# 1.3 Sistemas centralizados

Ejemplo conceptual:

```text
Developer ───┐
Developer ───┼──▶ Servidor central
Developer ───┘
```

---

# 1.4 Sistemas distribuidos

Git es distribuido.

Cada desarrollador normalmente posee una copia completa del repositorio y su historial.

```text
                 GitHub/GitLab
                      │
       ┌──────────────┼──────────────┐
       ▼              ▼              ▼
Developer A      Developer B      Developer C
Repository       Repository       Repository
complete         complete         complete
```

---

# MÓDULO 2. INTRODUCCIÓN A GIT

## 2.1 ¿Qué es Git?

Git es un sistema de control de versiones distribuido.

Permite administrar:

```text
Código
Documentación
Configuración
Infraestructura
Scripts
Proyectos científicos
Sitios web
Aplicaciones
```

---

# 2.2 Git no es GitHub

Esta distinción es fundamental.

```text
Git
│
└── Sistema de control de versiones
```

Mientras:

```text
GitHub
GitLab
Bitbucket
Gitea
Forgejo
Azure DevOps
```

son plataformas que pueden alojar repositorios Git y proporcionar herramientas adicionales.

---

# MÓDULO 3. INSTALACIÓN Y CONFIGURACIÓN

Verificar instalación:

```bash
git --version
```

---

## Identidad

```bash
git config --global user.name "Nombre Apellido"
```

```bash
git config --global user.email "correo@ejemplo.com"
```

Consultar:

```bash
git config --global --list
```

---

## Configuración por repositorio

También podemos tener diferente identidad en determinado proyecto:

```bash
git config user.name "Nombre Profesional"
```

```bash
git config user.email "correo-profesional@ejemplo.com"
```

---

## Configurar editor

Ejemplo VS Code:

```bash
git config --global core.editor "code --wait"
```

---

## Rama inicial

Para evitar depender de la configuración o de la versión instalada de Git puede definirse explícitamente la rama inicial:

```bash
git init -b main
```

La documentación oficial permite seleccionar la rama mediante `--initial-branch` / `-b` y configurar `init.defaultBranch`.

También puede establecerse globalmente:

```bash
git config --global init.defaultBranch main
```

---

# MÓDULO 4. ARQUITECTURA BÁSICA DE GIT

Uno de los conceptos más importantes del curso.

Git trabaja conceptualmente con tres áreas principales:

```text
Working Directory
       │
     git add
       ▼
Staging Area
       │
   git commit
       ▼
Repository
```

---

# 4.1 Working Directory

Son los archivos con los que estamos trabajando actualmente.

```text
proyecto/
├── main.go
├── auth.go
└── database.go
```

---

# 4.2 Staging Area

También denominada:

```text
Index
```

Representa qué cambios formarán parte del siguiente commit.

---

# 4.3 Repository

Historial almacenado por Git.

Se encuentra principalmente en:

```text
.git/
```

La documentación oficial describe que `git init` crea esta estructura interna con elementos como objetos y referencias.

---

# Flujo

```text
Modificar archivo

       │

       ▼

Working Tree

       │
    git add

       ▼

Staging Area

       │
   git commit

       ▼

Repository
```

---

# MÓDULO 5. PRIMER REPOSITORIO

Crear proyecto:

```bash
mkdir curso-git
```

```bash
cd curso-git
```

Inicializar:

```bash
git init -b main
```

---

## Consultar estado

```bash
git status
```

---

## Crear archivo

```bash
echo "# Curso Git" > README.md
```

Consultar:

```bash
git status
```

Aparecerá como:

```text
Untracked files
```

---

# MÓDULO 6. STAGING AREA

Agregar archivo:

```bash
git add README.md
```

Consultar:

```bash
git status
```

Ahora aparecerá preparado para commit.

---

## Agregar todos los cambios

```bash
git add .
```

---

## Agregar determinados archivos

```bash
git add auth.go database.go
```

---

## Añadir interactivamente partes de un archivo

Nivel intermedio:

```bash
git add -p
```

Permite seleccionar qué cambios de un mismo archivo entrarán al commit.

Esto es extremadamente útil para crear commits pequeños y coherentes.

---

# MÓDULO 7. COMMITS

## ¿Qué es un commit?

Un commit representa un punto del historial.

Conceptualmente:

```text
A ← B ← C ← D
```

Cada letra representa un commit.

---

## Primer commit

```bash
git commit -m "docs: add initial README"
```

---

## Buen commit

Un buen commit debería representar:

> una unidad lógica de cambio.

Evitar:

```text
Cambios
```

```text
actualización
```

```text
cosas nuevas
```

```text
final
```

---

## Mejor

```text
feat: add authentication endpoint
```

```text
fix: prevent duplicate user registration
```

```text
docs: document authentication flow
```

---

# Anatomía conceptual de un commit

Un commit contiene referencias a:

```text
Snapshot
Author
Date
Message
Parent commit
```

---

# MÓDULO 8. HISTORIAL

Consultar:

```bash
git log
```

---

## Versión compacta

```bash
git log --oneline
```

Ejemplo:

```text
7932cd1 feat: add login
214be81 docs: document API
1386d93 chore: initialize project
```

---

## Historial gráfico

```bash
git log --oneline --graph --decorate --all
```

Ejemplo:

```text
*   73ad55a Merge branch 'feat/auth'
|\
| * 50d9013 feat: add authentication
|/
* 78b12ea chore: initialize project
```

---

## Crear alias

```bash
git config --global alias.lg "log --oneline --graph --decorate --all"
```

Después:

```bash
git lg
```

---

# MÓDULO 9. GIT DIFF

Consultar cambios no preparados:

```bash
git diff
```

---

## Cambios preparados

```bash
git diff --staged
```

---

## Comparar commits

```bash
git diff COMMIT1 COMMIT2
```

---

## Comparar ramas

```bash
git diff main..feat/auth
```

---

# MÓDULO 10. `.gitignore`

Permite indicar archivos que Git no debería rastrear.

Ejemplo:

```gitignore
.env
node_modules/
dist/
build/
*.log
.DS_Store
.vscode/
```

Dependiendo del proyecto puede no ser conveniente ignorar toda la configuración de `.vscode`, por lo que debe analizarse caso por caso.

---

## Nunca debería utilizarse Git para almacenar directamente

```text
Passwords
API Keys
Private Keys
Access Tokens
Production credentials
```

El hecho de agregar posteriormente un archivo a `.gitignore` no elimina automáticamente secretos que ya hayan sido introducidos al historial.

---

# PRÁCTICA 1

Crear:

```text
curso-git/
├── README.md
├── src/
│   └── main.go
├── docs/
│   └── architecture.md
└── .gitignore
```

Realizar commits separados:

```text
chore: initialize repository

feat: add application entry point

docs: document initial architecture
```

---

# MÓDULO 11. RAMAS

Las ramas permiten desarrollar cambios independientemente.

Supongamos:

```text
A ─ B ─ C
        │
        └── main
```

Crear:

```bash
git switch -c feat/login
```

La documentación actual de Git utiliza `git switch` específicamente para cambiar de rama y `switch -c` para crear una nueva.

Ahora:

```text
A ─ B ─ C
        │
        ├── main
        │
        └── feat/login
```

Trabajamos:

```text
A ─ B ─ C
        │
        └── main
             \
              D ─ E
                  │
             feat/login
```

---

# Comandos

Listar:

```bash
git branch
```

Crear:

```bash
git branch feat/login
```

Cambiar:

```bash
git switch feat/login
```

Crear y cambiar:

```bash
git switch -c feat/login
```

---

## Regresar

```bash
git switch main
```

---

## Eliminar rama

```bash
git branch -d feat/login
```

Forzar:

```bash
git branch -D feat/login
```

Debe utilizarse `-D` cuidadosamente porque puede eliminar una rama todavía no integrada.

---

# MÓDULO 12. NOMENCLATURA DE RAMAS

Una convención recomendada:

```text
tipo/descripcion
```

Ejemplos:

```text
feat/login
feat/user-profile
fix/session-expiration
docs/api-authentication
refactor/user-service
test/auth-service
chore/update-dependencies
```

---

## Con identificador de tarea

```text
feat/123-user-login
```

```text
fix/248-invalid-token
```

---

## Convención sugerida

| Prefijo     | Finalidad               |
| ----------- | ----------------------- |
| `feat/`     | Nueva funcionalidad     |
| `fix/`      | Corrección              |
| `hotfix/`   | Corrección urgente      |
| `docs/`     | Documentación           |
| `refactor/` | Refactorización         |
| `test/`     | Pruebas                 |
| `chore/`    | Mantenimiento           |
| `ci/`       | CI/CD                   |
| `build/`    | Sistema de construcción |

---

# MÓDULO 13. MERGE

Supongamos:

```text
A ─ B ─ C
        │
        └── main
             \
              D ─ E
                  │
               feat/auth
```

Para integrar:

```bash
git switch main
```

```bash
git merge feat/auth
```

---

# Fast-forward

Cuando `main` no ha avanzado:

```text
Antes:

A ─ B ─ C
         \
          D ─ E
```

Después:

```text
A ─ B ─ C ─ D ─ E
                  │
                 main
```

---

# Merge commit

Si ambas ramas cambiaron:

```text
       D ─ E
      /     \
A ─ B       M
      \     /
       C ─ F
```

`M` representa el merge commit.

---

# MÓDULO 14. CONFLICTOS

Un conflicto puede aparecer cuando Git no puede determinar automáticamente qué cambio debe conservar.

Ejemplo:

Persona A:

```go
const Port = 8080
```

Persona B:

```go
const Port = 3000
```

Git puede generar:

```text
<<<<<<< HEAD
const Port = 8080
=======
const Port = 3000
>>>>>>> feat/config
```

---

# Resolver conflicto

## Paso 1

Identificar:

```bash
git status
```

---

## Paso 2

Editar manualmente.

Por ejemplo:

```go
const Port = 8080
```

---

## Paso 3

Marcar como resuelto:

```bash
git add config.go
```

---

## Paso 4

Continuar:

```bash
git commit
```

---

# Regla importante

Nunca resolver conflictos simplemente aceptando:

```text
Accept Current
```

o:

```text
Accept Incoming
```

sin comprender qué representan ambos cambios.

---

# Cancelar merge

```bash
git merge --abort
```

---

# PRÁCTICA 2 — CONFLICTOS

Dos alumnos modifican la misma línea.

Objetivo:

1. crear ramas;
2. modificar;
3. realizar commits;
4. fusionar;
5. provocar conflicto;
6. analizar;
7. resolver correctamente.

---

# MÓDULO 15. REBASE

`rebase` cambia la base de una serie de commits.

Tenemos:

```text
A ─ B ─ C
     \
      D ─ E
```

Mientras nuestra rama avanzaba:

```text
main:
A ─ B ─ C
```

Queremos colocar nuestros cambios después de `C`.

```bash
git switch feat/login
```

```bash
git rebase main
```

Resultado conceptual:

```text
A ─ B ─ C ─ D' ─ E'
```

Los commits `D'` y `E'` son nuevos commits.

---

# Merge vs Rebase

## Merge

Preserva la topología del historial:

```text
      D ─ E
     /     \
A ─ B ─ C ─ M
```

---

## Rebase

Produce historial lineal:

```text
A ─ B ─ C ─ D' ─ E'
```

---

# Regla crítica

Evitar hacer rebase de commits públicos compartidos cuando otros desarrolladores ya están trabajando a partir de ellos.

¿Por qué?

Porque rebase reescribe historial.

---

# Flujo frecuente

En una rama personal:

```bash
git fetch origin
```

```bash
git rebase origin/main
```

Resolver conflictos:

```bash
git add archivo
```

```bash
git rebase --continue
```

Cancelar:

```bash
git rebase --abort
```

---

# MÓDULO 16. REBASE INTERACTIVO

Permite reorganizar commits.

```bash
git rebase -i HEAD~4
```

Aparece algo similar:

```text
pick 182da4 feat: add login
pick 173af3 fix typo
pick a82911 fix another typo
pick fa183c docs: add login docs
```

Puede cambiarse por:

```text
pick
reword
edit
squash
fixup
drop
```

---

## Ejemplo squash

```text
pick 182da4 feat: add login
fixup 173af3 fix typo
fixup a82911 fix another typo
```

Resultado:

```text
feat: add login
```

con los tres cambios incorporados.

---

# MÓDULO 17. REPOSITORIOS REMOTOS

Consultar:

```bash
git remote -v
```

---

## Agregar remoto

```bash
git remote add origin git@github.com:organizacion/proyecto.git
```

---

## Concepto

```text
Local Repository
      │
      │ push
      ▼
Remote Repository
```

y:

```text
Remote Repository
      │
      │ fetch/pull
      ▼
Local Repository
```

---

# MÓDULO 18. CLONAR REPOSITORIOS

```bash
git clone URL
```

Ejemplo conceptual:

```bash
git clone git@github.com:organizacion/proyecto.git
```

La clonación crea un repositorio local conectado al repositorio remoto. Git también permite opciones especializadas como clonar submodules recursivamente.

---

# MÓDULO 19. FETCH

```bash
git fetch origin
```

`fetch` descarga información del repositorio remoto.

Pero no modifica automáticamente nuestra rama de trabajo.

Conceptualmente:

```text
Remote
   │
   ▼
origin/main

main permanece igual
```

Esto hace que `fetch` sea muy útil para inspeccionar cambios antes de integrarlos.

---

# MÓDULO 20. PULL

Conceptualmente:

```text
git pull
=
fetch
+
integración
```

Dependiendo de la configuración, la integración puede involucrar merge o rebase.

---

## Pull explícito mediante rebase

```bash
git pull --rebase origin main
```

Puede ser útil para mantener limpio el historial de una rama local cuando el equipo ha acordado utilizar esta estrategia.

---

## Pull solo si puede hacerse Fast Forward

```bash
git pull --ff-only origin main
```

Esta alternativa es especialmente segura para una rama `main` local que no debería contener commits propios.

---

# MÓDULO 21. PUSH

Publicar cambios:

```bash
git push origin main
```

---

## Primera publicación de rama

```bash
git push -u origin feat/login
```

Después podrá utilizarse:

```bash
git push
```

---

# MÓDULO 22. TRACKING BRANCHES

Podemos tener:

```text
main
```

asociada con:

```text
origin/main
```

---

Consultar:

```bash
git branch -vv
```

---

# MÓDULO 23. GITHUB Y GITLAB

Estas plataformas agregan funcionalidades alrededor de Git:

```text
Repository hosting
Issues
Pull/Merge Requests
Code Review
Permissions
CI/CD
Releases
Packages
Wikis
Project management
Security
```

---

# Pull Request vs Merge Request

GitHub utiliza principalmente:

```text
Pull Request
```

GitLab utiliza:

```text
Merge Request
```

Ambos mecanismos permiten proponer, revisar y posteriormente integrar cambios.

GitHub documenta los Pull Requests como mecanismo para proponer, discutir y fusionar cambios; GitLab describe los Merge Requests como el espacio central para revisión de código, discusión, pipelines y comprobaciones antes de integrar.

---

# MÓDULO 24. FLUJO PROFESIONAL DE TRABAJO

Una recomendación adecuada para numerosos equipos pequeños y medianos consiste en proteger `main` y trabajar con ramas cortas.

```text
main
 │
 ├── feat/login
 │
 ├── feat/profile
 │
 └── fix/token
```

---

# Inicio del trabajo

Actualizar `main`:

```bash
git switch main
```

```bash
git pull --ff-only origin main
```

Crear rama:

```bash
git switch -c feat/login
```

---

# Durante el desarrollo

```bash
git add .
```

```bash
git commit -m "feat(auth): add login endpoint"
```

Continuar con commits pequeños.

---

# Antes de publicar

```bash
git fetch origin
```

Actualizar nuestra rama:

```bash
git rebase origin/main
```

---

# Publicar

```bash
git push -u origin feat/login
```

---

# Crear Pull/Merge Request

```text
feat/login
    │
    ▼
Pull/Merge Request
    │
    ├── Review
    ├── Automated tests
    ├── CI
    └── Approval
         │
         ▼
        main
```

---

# Después del merge

```bash
git switch main
```

```bash
git pull --ff-only origin main
```

Eliminar rama local:

```bash
git branch -d feat/login
```

---

# MÓDULO 25. RAMAS PROTEGIDAS

En proyectos profesionales conviene evitar:

```bash
git push origin main
```

directamente por parte de los desarrolladores.

En su lugar:

```text
Feature branch
      │
      ▼
Pull Request
      │
      ├── CI
      ├── Review
      └── Approval
           │
           ▼
          main
```

GitHub permite configurar reglas que, entre otras cosas, exigen revisiones y status checks y restringen force pushes o eliminaciones. GitLab permite controlar quién puede hacer push o merge y forzar el paso por Merge Requests.

---

# MÓDULO 26. ESTRATEGIAS DE RAMAS

No existe una estrategia universalmente adecuada.

---

# Estrategia 1 — Feature Branch

```text
main
 │
 ├── feat/a
 ├── feat/b
 └── fix/c
```

Adecuada para numerosos equipos.

---

# Estrategia 2 — Trunk-Based Development

```text
             feat/a
            /
main ──────●────────●────●────
                    \
                     fix/b
```

Las ramas deben vivir poco tiempo.

El objetivo es integrar cambios frecuentemente.

La literatura de Trunk-Based Development enfatiza ramas de funcionalidad de corta duración que regresan rápidamente al trunk, normalmente mediante revisión y CI.

---

# Estrategia 3 — Git Flow

Modelo clásico:

```text
main
 │
 ├── release
 │
develop
 │
 ├── feature/a
 ├── feature/b
 └── feature/c
```

Además:

```text
hotfix/*
release/*
```

Puede ser apropiado para algunos procesos de liberación tradicionales, pero introduce considerablemente más ramas y complejidad.

No debería adoptarse automáticamente.

---

# Recomendación para proyectos modernos pequeños o medianos

```text
main protegida
+
ramas cortas
+
Pull/Merge Request
+
CI
+
Code Review
```

---

# MÓDULO 27. CONVENTIONAL COMMITS

Convención para mensajes de commit.

Formato:

```text
tipo(scope): descripción
```

La especificación estable de Conventional Commits 1.0.0 utiliza una estructura basada en tipo, ámbito opcional, descripción y cuerpo/notas opcionales.

---

# Tipos recomendados

```text
feat
fix
docs
style
refactor
test
build
ci
chore
perf
revert
```

---

# Ejemplos

```text
feat(auth): add JWT authentication
```

```text
fix(api): prevent duplicated requests
```

```text
docs(api): document user endpoints
```

```text
refactor(auth): extract token validation
```

```text
test(auth): add login integration tests
```

```text
ci: add GitHub Actions workflow
```

---

# Qué evitar

```text
changes
```

```text
update
```

```text
final
```

```text
something
```

```text
fix stuff
```

---

# Commit pequeño

Mejor:

```text
feat(auth): add password hashing

feat(auth): add login endpoint

test(auth): add login tests
```

que:

```text
feat: add auth and profile and DB changes and docs
```

---

# MÓDULO 28. RESTORE

La referencia oficial distingue actualmente `restore`, `reset` y `revert`: `restore` recupera contenido del working tree o index; `reset` mueve referencias y puede alterar historial; `revert` crea un nuevo commit que revierte otro cambio.

---

## Descartar cambio en archivo

```bash
git restore archivo.txt
```

Precaución:

los cambios no confirmados pueden perderse.

---

## Sacar archivo del staging

```bash
git restore --staged archivo.txt
```

---

# MÓDULO 29. RESET

`reset` debe comprenderse correctamente.

---

# Soft

```bash
git reset --soft HEAD~1
```

Mueve HEAD pero mantiene cambios en staging.

Conceptualmente:

```text
Commit eliminado
      │
      ▼
Staging Area
```

---

# Mixed

```bash
git reset HEAD~1
```

Mantiene cambios en Working Tree pero los retira de staging.

---

# Hard

```bash
git reset --hard HEAD~1
```

Puede eliminar:

```text
commit
+
staging
+
working tree changes
```

Debe utilizarse con mucha precaución.

---

# Comparación

| Comando   | Commit | Staging  | Working Tree |
| --------- | ------ | -------- | ------------ |
| `--soft`  | mueve  | conserva | conserva     |
| `--mixed` | mueve  | limpia   | conserva     |
| `--hard`  | mueve  | limpia   | modifica     |

---

# MÓDULO 30. REVERT

En historial compartido suele ser preferible:

```bash
git revert COMMIT
```

En lugar de eliminar el commit.

Ejemplo:

```text
A ─ B ─ C
```

Si `C` fue incorrecto:

```bash
git revert C
```

Resultado:

```text
A ─ B ─ C ─ D
```

`D` deshace los cambios de `C`.

El historial permanece intacto.

---

# RESET VS REVERT

## Reset

Puede reescribir historial.

Adecuado principalmente para trabajo local todavía no compartido.

---

## Revert

Genera nuevo historial.

Preferible para cambios ya publicados.

---

# MÓDULO 31. REFLOG

Una de las mejores herramientas para recuperación.

```bash
git reflog
```

Puede mostrar movimientos recientes de HEAD:

```text
7c911da HEAD@{0}: reset
149ead1 HEAD@{1}: commit
a721be4 HEAD@{2}: checkout
```

---

# Caso

Ejecutamos accidentalmente:

```bash
git reset --hard HEAD~3
```

Creemos haber perdido los commits.

Consultar:

```bash
git reflog
```

Encontrar commit:

```text
a19e823
```

Recuperarlo:

```bash
git switch -c recovery a19e823
```

---

# Regla

Antes de asumir:

> "Perdí todo."

consultar:

```bash
git reflog
```

---

# MÓDULO 32. STASH

Permite guardar temporalmente cambios.

Situación:

```text
Estamos desarrollando feat/login.

Aparece una emergencia.

Necesitamos cambiar de rama.
```

Podemos:

```bash
git stash
```

---

## Listar

```bash
git stash list
```

---

## Recuperar

```bash
git stash pop
```

---

## Aplicar sin eliminar

```bash
git stash apply
```

---

## Con descripción

```bash
git stash push -m "WIP authentication"
```

---

# MÓDULO 33. CHERRY-PICK

Permite aplicar un commit determinado en otra rama.

Tenemos:

```text
main
A ─ B ─ C

feature
    \
     D ─ E
```

Queremos solamente `E`.

```bash
git switch main
```

```bash
git cherry-pick HASH_E
```

Resultado:

```text
A ─ B ─ C ─ E'
```

---

# Casos útiles

* corrección específica;
* traslado puntual entre ramas;
* recuperar commit;
* aplicar hotfix.

No debería utilizarse como sustituto habitual de una estrategia correcta de integración.

---

# MÓDULO 34. TAGS

Los tags identifican puntos determinados del historial.

Ejemplo:

```text
v1.0.0
v1.1.0
v2.0.0
```

---

## Crear tag anotado

```bash
git tag -a v1.0.0 -m "Release v1.0.0"
```

---

## Publicar

```bash
git push origin v1.0.0
```

---

## Todos

```bash
git push origin --tags
```

---

# Versionado Semántico

Conceptualmente:

```text
MAJOR.MINOR.PATCH
```

Ejemplo:

```text
2.4.1
```

Puede combinarse con Conventional Commits y herramientas de automatización de releases.

---

# MÓDULO 35. SHOW

Examinar commit:

```bash
git show HASH
```

---

## Examinar tag

```bash
git show v1.0.0
```

---

# MÓDULO 36. BLAME

```bash
git blame archivo.go
```

Permite investigar qué commit introdujo cada línea.

Su uso profesional debería entenderse como:

> "¿Qué contexto histórico existe?"

y no:

> "¿Quién tiene la culpa?"

---

# MÓDULO 37. BISECT

Excelente herramienta para localizar cuándo apareció un error.

Supongamos:

```text
A ─ B ─ C ─ D ─ E ─ F ─ G
```

Sabemos:

```text
A funciona
G falla
```

Iniciar:

```bash
git bisect start
```

Marcar actual:

```bash
git bisect bad
```

Marcar versión conocida como buena:

```bash
git bisect good HASH_A
```

Git seleccionará commits intermedios.

Indicamos:

```bash
git bisect good
```

o:

```bash
git bisect bad
```

hasta localizar el primer commit defectuoso.

Finalizar:

```bash
git bisect reset
```

---

# MÓDULO 38. HOOKS

Git permite ejecutar scripts ante determinados eventos.

Ejemplos:

```text
pre-commit
commit-msg
pre-push
post-merge
```

La instalación de Git incluye plantillas de hooks de ejemplo desactivadas por defecto.

---

# Ejemplo conceptual de pre-commit

```bash
#!/bin/sh

npm test

if [ $? -ne 0 ]; then
    echo "Tests failed"
    exit 1
fi
```

Si las pruebas fallan:

```text
Commit rejected
```

---

# Herramientas relacionadas

Existen herramientas como:

```text
Husky
pre-commit
lefthook
lint-staged
```

que facilitan administrar hooks en proyectos.

---

# Posibles verificaciones

```text
format
lint
tests
security
commit message
secrets
```

---

# MÓDULO 39. WORKTREES

Git puede mantener varias ramas físicamente disponibles al mismo tiempo.

La referencia oficial incluye `git worktree` como mecanismo para administrar múltiples working trees asociados al mismo repositorio.

Ejemplo:

```bash
git worktree add ../proyecto-hotfix hotfix/security
```

Tenemos:

```text
proyecto/
    main o feature

proyecto-hotfix/
    hotfix/security
```

Ambos comparten el mismo repositorio Git.

---

# Caso

Estamos trabajando:

```text
feat/new-dashboard
```

pero aparece una emergencia:

```text
hotfix/auth
```

En lugar de:

```text
stash
switch
trabajar
switch
stash pop
```

podemos utilizar otro worktree.

---

# MÓDULO 40. SUBMODULES

Un repositorio puede referenciar otro repositorio Git.

Ejemplo:

```text
app/
├── frontend/
├── backend/
└── shared-library/
        ↓
      otro repo
```

Agregar:

```bash
git submodule add URL shared-library
```

---

## Clonar proyecto con submodules

```bash
git clone --recurse-submodules URL
```

Git documenta que los submodules quedan vinculados a un commit específico del repositorio incluido, no simplemente a "la última versión" de una rama.

---

## Actualizar

```bash
git submodule update --init --recursive
```

---

# Ventaja

Permite incorporar proyectos independientes.

# Desventaja

Introduce complejidad adicional.

No utilizar submodules simplemente para organizar carpetas.

---

# MÓDULO 41. GIT LFS

Git no está diseñado para manejar eficientemente enormes cantidades de binarios grandes que cambian frecuentemente.

Ejemplos:

```text
video
datasets grandes
modelos
PSD
binarios
assets de gran tamaño
```

Una tecnología relacionada es:

```text
Git LFS
```

Git LFS almacena referencias ligeras en Git y gestiona por separado los objetos grandes.

---

# MÓDULO 42. AUTENTICACIÓN

Los repositorios remotos pueden utilizar:

```text
HTTPS
SSH
```

---

# SSH

Conceptualmente:

```text
Private key
     │
     ▼
Computer
     │
Authentication
     ▼
Git server
     ▲
     │
Public key
```

---

# Regla fundamental

Nunca compartir:

```text
private key
```

---

# MÓDULO 43. SEGURIDAD

## No subir secretos

Nunca realizar:

```bash
git add .env
```

si contiene credenciales reales.

---

## Si un secreto entra en Git

No basta con:

```bash
git rm archivo
```

porque puede permanecer en el historial.

Procedimiento general:

```text
1. Revocar secreto
2. Generar nuevo secreto
3. Eliminarlo del repositorio
4. Si es necesario, limpiar historial
5. Revisar dónde fue expuesto
```

La revocación es prioritaria.

---

# FORCE PUSH

Evitar:

```bash
git push --force
```

especialmente sobre ramas compartidas.

---

## Alternativa más segura

```bash
git push --force-with-lease
```

Sigue reescribiendo historial, pero incorpora una comprobación para reducir el riesgo de sobrescribir trabajo remoto inesperado.

Debe reservarse principalmente para ramas personales donde el equipo permite reescribir historial.

---

# `main`

Idealmente:

```text
NO direct push
NO force push
NO deletion
PR required
CI required
review required
```

Las plataformas modernas permiten imponer buena parte de estas restricciones mediante reglas de protección de ramas.

---

# MÓDULO 44. CODE REVIEW

Un Pull/Merge Request no debería utilizarse únicamente para:

```text
"dar merge"
```

Debe servir para analizar:

```text
correctness
architecture
security
tests
readability
documentation
maintainability
```

---

# Tamaño del Pull Request

Preferible:

```text
200 líneas enfocadas
```

que:

```text
6,000 líneas que modifican 70 archivos sin relación
```

No existe un límite universal, pero los cambios pequeños y coherentes suelen ser más sencillos de revisar.

---

# MÓDULO 45. CI/CD

Flujo moderno:

```text
Developer
    │
    ▼
git push
    │
    ▼
Pull Request
    │
    ▼
CI Pipeline
    │
    ├── Compile
    ├── Format
    ├── Lint
    ├── Tests
    ├── Security
    └── Build
         │
         ▼
       Review
         │
         ▼
        Merge
```

GitLab define CI/CD mediante pipelines con stages y jobs normalmente configurados mediante `.gitlab-ci.yml`; los pipelines pueden integrarse directamente con Merge Requests.

---

# Ejemplo GitHub Actions

```yaml
name: CI

on:
  pull_request:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Test
        run: go test ./...
```

---

# Flujo

```text
feat/auth
   │
   ▼
Pull Request
   │
   ▼
GitHub Actions
   │
   ├── Tests PASS
   └── Tests FAIL
```

Solo cuando:

```text
Tests PASS
+
Review approved
```

se integra.

GitHub permite utilizar branch protection para requerir status checks y revisiones antes del merge.

---

# MÓDULO 46. FORKS

Un fork es una copia del repositorio en otra cuenta o espacio.

Flujo habitual de software libre:

```text
Original Repository
       │
       ▼
      Fork
       │
       ▼
Feature branch
       │
       ▼
Pull Request
       │
       ▼
Original Repository
```

GitLab documenta tanto un flujo con ramas protegidas dentro de un único proyecto como un flujo basado en forks.

---

# MÓDULO 47. MÚLTIPLES REMOTES

Consultar:

```bash
git remote -v
```

Podemos tener:

```text
origin
upstream
```

Ejemplo:

```text
upstream = proyecto original
origin   = nuestro fork
```

---

Agregar:

```bash
git remote add upstream URL
```

Actualizar:

```bash
git fetch upstream
```

---

# MÓDULO 48. HEAD

`HEAD` representa normalmente dónde estamos actualmente.

Ejemplo:

```text
HEAD
 │
 ▼
main
 │
 ▼
Commit C
```

---

# Detached HEAD

Puede ocurrir:

```bash
git switch --detach HASH
```

Tenemos:

```text
HEAD
 │
 ▼
Commit B
```

sin apuntar a una rama.

Si queremos conservar trabajo:

```bash
git switch -c nueva-rama
```

---

# MÓDULO 49. REFERENCIAS

Git trabaja con referencias:

```text
HEAD
main
feat/login
origin/main
tags
```

Estas referencias terminan apuntando a commits.

---

# MÓDULO 50. MODELO INTERNO

Modelo simplificado:

```text
Commit
  │
  ▼
Tree
  │
  ├── Blob
  ├── Blob
  └── Tree
       └── Blob
```

---

# Objetos principales

```text
blob
tree
commit
tag
```

Comprender esto ayuda considerablemente a entender por qué Git funciona como funciona.

---

# MÓDULO 51. ESTRATEGIA RECOMENDADA PARA UN EQUIPO

Una organización práctica puede utilizar:

```text
main
```

como rama protegida.

Desarrolladores crean:

```text
feat/*
fix/*
docs/*
refactor/*
test/*
chore/*
```

---

# Flujo diario

## Antes de comenzar

```bash
git switch main
```

```bash
git pull --ff-only origin main
```

---

## Crear trabajo

```bash
git switch -c feat/modulo
```

---

## Trabajar

```bash
git status
```

```bash
git add .
```

```bash
git commit -m "feat(module): add functionality"
```

---

## Sincronizar antes del PR

```bash
git fetch origin
```

```bash
git rebase origin/main
```

---

## Publicar

```bash
git push -u origin feat/modulo
```

---

## Crear PR

```text
Developer
   │
   ▼
Pull Request
   │
   ├── CI
   ├── Review
   └── Approval
        │
        ▼
       main
```

---

## Después del merge

```bash
git switch main
```

```bash
git pull --ff-only origin main
```

```bash
git branch -d feat/modulo
```

---

# MÓDULO 52. FLUJO PARA REPOSITORIOS DE DOCUMENTACIÓN

Puede utilizarse un flujo todavía más simple.

Actualizar:

```bash
git switch main
```

```bash
git pull --rebase origin main
```

Trabajar normalmente.

Guardar:

```bash
git add .
```

```bash
git commit -m "docs: update research methodology"
```

Sincronizar antes de publicar:

```bash
git pull --rebase origin main
```

Publicar:

```bash
git push origin main
```

Este enfoque puede ser apropiado para repositorios colaborativos de documentación con bajo riesgo y equipos pequeños.

En software productivo es preferible normalmente trabajar mediante ramas y Pull Requests.

---

# MÓDULO 53. AUTOMATIZACIÓN

Los comandos frecuentes pueden automatizarse.

Ejemplo conceptual:

```bash
#!/bin/bash

set -e

git switch main
git pull --ff-only origin main

echo "Repository synchronized."
```

---

# Script para guardar

```bash
#!/bin/bash

set -e

MESSAGE="$1"

if [ -z "$MESSAGE" ]; then
    echo "Commit message required."
    exit 1
fi

git add .

git commit -m "$MESSAGE"

git pull --rebase origin main

git push origin main

echo "Repository synchronized."
```

---

# MÓDULO 54. ALIAS

Configurar:

```bash
git config --global alias.st status
```

```bash
git config --global alias.sw switch
```

```bash
git config --global alias.br branch
```

```bash
git config --global alias.cm commit
```

```bash
git config --global alias.lg "log --oneline --graph --decorate --all"
```

---

Uso:

```bash
git st
```

```bash
git lg
```

---

# MÓDULO 55. TROUBLESHOOTING

## Caso 1

```text
Your branch is behind origin/main
```

Solución habitual:

```bash
git pull --ff-only origin main
```

o analizar primero:

```bash
git fetch origin
```

---

# Caso 2

```text
Your branch has diverged
```

Analizar:

```bash
git log --oneline --graph --all
```

No ejecutar comandos destructivos hasta entender la divergencia.

---

# Caso 3

Commit en rama equivocada.

Supongamos que realizamos:

```text
main
    └── commit equivocado
```

Si todavía no se publicó:

```bash
git switch -c feat/correct-branch
```

La nueva rama conserva el commit.

Posteriormente puede restaurarse `main` según corresponda.

---

# Caso 4

Eliminar commit local.

```bash
git reset --soft HEAD~1
```

si queremos conservar cambios preparados.

---

# Caso 5

Deshacer commit publicado.

```bash
git revert HASH
```

---

# Caso 6

Perdimos commits.

```bash
git reflog
```

---

# Caso 7

Conflicto de merge.

```bash
git status
```

Editar.

```bash
git add archivo
```

Continuar.

---

# Caso 8

Conflicto de rebase.

```bash
git status
```

Resolver.

```bash
git add archivo
```

```bash
git rebase --continue
```

---

# Caso 9

Cancelar rebase.

```bash
git rebase --abort
```

---

# Caso 10

Cancelar merge.

```bash
git merge --abort
```

---

# Caso 11

Rechazo de push

```text
non-fast-forward
```

No responder automáticamente con:

```bash
git push --force
```

Primero:

```bash
git fetch origin
```

Analizar:

```bash
git log --graph --oneline --all
```

y decidir la integración correcta.

---

# MÓDULO 56. COMANDOS PELIGROSOS

Deben comprenderse antes de ejecutarse:

```bash
git reset --hard
```

```bash
git clean -fd
```

```bash
git branch -D
```

```bash
git push --force
```

```bash
git rebase
```

sobre historial público.

---

# Regla profesional

Antes de ejecutar un comando destructivo:

```text
1. git status
2. git log
3. git reflog
4. confirmar rama
5. confirmar remoto
6. ejecutar
```

---

# MÓDULO 57. MALAS PRÁCTICAS

Evitar:

```text
Commits gigantes
Commits sin descripción
Push directo a main
Force push a main
Subir secretos
Ramas viviendo meses
PR gigantes
Mezclar múltiples funcionalidades
Commits "final-final"
Resolver conflictos sin analizar
Usar reset --hard sin entenderlo
Usar Git como almacenamiento de binarios gigantes
```

---

# MÓDULO 58. BUENAS PRÁCTICAS

Preferir:

```text
Commits pequeños
Commits coherentes
Mensajes descriptivos
Ramas cortas
Pull Requests
Code Review
CI
Tests
Main protegida
Tags de versiones
Documentación
Automatización
```

---

# PRÁCTICAS DEL CURSO

## Práctica 1

Crear repositorio.

## Práctica 2

Trabajar con staging.

## Práctica 3

Crear commits.

## Práctica 4

Analizar `diff`.

## Práctica 5

Crear `.gitignore`.

## Práctica 6

Crear ramas.

## Práctica 7

Merge Fast Forward.

## Práctica 8

Merge de tres vías.

## Práctica 9

Provocar conflicto.

## Práctica 10

Resolver conflicto.

## Práctica 11

Configurar remoto.

## Práctica 12

Fetch/Pull/Push.

## Práctica 13

Pull Request.

## Práctica 14

Code Review.

## Práctica 15

Rebase.

## Práctica 16

Rebase interactivo.

## Práctica 17

Stash.

## Práctica 18

Cherry-pick.

## Práctica 19

Reset.

## Práctica 20

Revert.

## Práctica 21

Reflog.

## Práctica 22

Tags.

## Práctica 23

Bisect.

## Práctica 24

Hooks.

## Práctica 25

Worktrees.

## Práctica 26

Submodules.

## Práctica 27

CI/CD.

## Práctica 28

Proyecto colaborativo.

---

# PROYECTO INTEGRADOR

## Desarrollo colaborativo de una aplicación

Equipo:

```text
4 desarrolladores
```

Repositorio:

```text
proyecto/
├── frontend/
├── backend/
├── database/
├── docs/
├── .github/
├── .gitignore
└── README.md
```

---

# Reglas

Rama principal:

```text
main
```

Protegida.

---

# Ramas

```text
feat/*
fix/*
docs/*
refactor/*
test/*
ci/*
```

---

# Commits

Utilizar:

```text
Conventional Commits
```

---

# Integración

Todo cambio deberá utilizar:

```text
Pull Request
```

---

# Requisitos para merge

```text
CI aprobado
Tests aprobados
Code review aprobado
Sin conflictos
```

---

# Flujo

```text
Issue
  │
  ▼
Branch
  │
  ▼
Development
  │
  ▼
Commits
  │
  ▼
Push
  │
  ▼
Pull Request
  │
  ├── CI
  ├── Tests
  └── Review
        │
        ▼
       Merge
        │
        ▼
       main
```

---

# Ejemplo

Issue:

```text
#42 Implement user authentication
```

Rama:

```text
feat/42-user-authentication
```

Commits:

```text
feat(auth): add password hashing

feat(auth): add login endpoint

test(auth): add login tests

docs(auth): document authentication flow
```

Pull Request:

```text
feat/42-user-authentication
        │
        ▼
       main
```

---

# RELEASE

Crear:

```text
v1.0.0
```

mediante:

```bash
git tag -a v1.0.0 -m "Release v1.0.0"
```

```bash
git push origin v1.0.0
```

---

# EVALUACIÓN

| Actividad                    | Porcentaje |
| ---------------------------- | ---------: |
| Prácticas individuales       |       25 % |
| Cuestionarios                |       10 % |
| Conflictos y troubleshooting |       15 % |
| Git colaborativo             |       15 % |
| Pull Request + Code Review   |       10 % |
| Proyecto integrador          |       25 % |

---

# PREGUNTAS DE REPASO

## Fundamentos

1. ¿Qué es Git?
2. ¿Cuál es la diferencia entre Git y GitHub?
3. ¿Qué es un repositorio?
4. ¿Qué contiene `.git`?
5. ¿Qué es Working Tree?
6. ¿Qué es Staging Area?
7. ¿Qué es un commit?
8. ¿Qué representa HEAD?
9. ¿Qué es una rama?
10. ¿Qué es un repositorio remoto?

---

## Comandos

11. ¿Qué hace `git add`?
12. ¿Qué hace `git commit`?
13. ¿Qué hace `git fetch`?
14. ¿Qué hace `git pull`?
15. ¿Qué hace `git push`?
16. ¿Qué hace `git switch`?
17. ¿Qué hace `git merge`?
18. ¿Qué hace `git rebase`?
19. ¿Qué hace `git stash`?
20. ¿Qué hace `git reflog`?

---

## Intermedio

21. ¿Qué diferencia existe entre merge y rebase?
22. ¿Qué diferencia existe entre reset y revert?
23. ¿Qué hace cherry-pick?
24. ¿Qué problema resuelve stash?
25. ¿Qué problema resuelve reflog?
26. ¿Para qué sirven los tags?
27. ¿Qué es un Pull Request?
28. ¿Qué es una rama protegida?
29. ¿Qué es CI?
30. ¿Qué son los Git hooks?

---

# CHEAT SHEET

## Configuración

```bash
git config --global user.name "Nombre"
```

```bash
git config --global user.email "correo@example.com"
```

---

## Crear repositorio

```bash
git init -b main
```

---

## Clonar

```bash
git clone URL
```

---

## Estado

```bash
git status
```

---

## Añadir

```bash
git add .
```

---

## Commit

```bash
git commit -m "feat: add functionality"
```

---

## Historial

```bash
git log --oneline
```

---

## Historial gráfico

```bash
git log --oneline --graph --decorate --all
```

---

## Diferencias

```bash
git diff
```

---

## Ramas

```bash
git branch
```

---

## Crear rama

```bash
git switch -c feat/functionality
```

---

## Cambiar rama

```bash
git switch main
```

---

## Fusionar

```bash
git merge feat/functionality
```

---

## Actualizar remotos

```bash
git fetch origin
```

---

## Descargar e integrar

```bash
git pull
```

---

## Publicar

```bash
git push
```

---

## Publicar nueva rama

```bash
git push -u origin feat/functionality
```

---

## Rebase

```bash
git rebase main
```

---

## Rebase interactivo

```bash
git rebase -i HEAD~4
```

---

## Stash

```bash
git stash
```

---

## Recuperar stash

```bash
git stash pop
```

---

## Revert

```bash
git revert HASH
```

---

## Reflog

```bash
git reflog
```

---

## Cherry-pick

```bash
git cherry-pick HASH
```

---

## Tag

```bash
git tag -a v1.0.0 -m "Release v1.0.0"
```

---

## Worktree

```bash
git worktree list
```

---

# GUÍA RÁPIDA: ¿QUÉ COMANDO DEBO UTILIZAR?

```text
Quiero ver qué cambió
        │
        ▼
     git diff
```

```text
Quiero guardar cambios
        │
        ▼
git add
git commit
```

```text
Quiero cambiar de rama
        │
        ▼
    git switch
```

```text
Quiero integrar ramas
        │
        ▼
     git merge
```

```text
Quiero actualizar información remota sin integrar
        │
        ▼
     git fetch
```

```text
Quiero descargar e integrar
        │
        ▼
     git pull
```

```text
Quiero publicar
        │
        ▼
     git push
```

```text
Quiero guardar trabajo temporal
        │
        ▼
     git stash
```

```text
Quiero deshacer un commit publicado
        │
        ▼
     git revert
```

```text
Creo que perdí commits
        │
        ▼
     git reflog
```

```text
Quiero aplicar un commit concreto
        │
        ▼
     git cherry-pick
```

---

# CRONOGRAMA SUGERIDO — 45 HORAS

| Sesión | Tema                           |    Horas |
| ------ | ------------------------------ | -------: |
| 1      | Control de versiones y Git     |        2 |
| 2      | Arquitectura de Git            |        3 |
| 3      | Add, Commit, Status y Diff     |        3 |
| 4      | Historial y `.gitignore`       |        2 |
| 5      | Ramas                          |        3 |
| 6      | Merge                          |        3 |
| 7      | Conflictos                     |        3 |
| 8      | Git remoto                     |        3 |
| 9      | GitHub/GitLab                  |        2 |
| 10     | Pull/Merge Requests            |        3 |
| 11     | Rebase                         |        3 |
| 12     | Reset, Restore y Revert        |        3 |
| 13     | Stash, Cherry-pick y Reflog    |        3 |
| 14     | Tags y versiones               |        2 |
| 15     | Hooks y herramientas avanzadas |        2 |
| 16     | CI/CD                          |        2 |
| 17     | Proyecto colaborativo          |        3 |
|        | **Total**                      | **45 h** |

---

# RUTA POSTERIOR AL CURSO

Una ruta recomendable sería:

```text
Git Fundamentos
       │
       ▼
Git Intermedio
       │
       ▼
GitHub / GitLab
       │
       ▼
Pull Requests
       │
       ▼
Code Review
       │
       ▼
Conventional Commits
       │
       ▼
CI/CD
       │
       ├── GitHub Actions
       └── GitLab CI
       │
       ▼
Docker
       │
       ▼
Container Registry
       │
       ▼
Kubernetes
       │
       ▼
GitOps
       │
       ├── Argo CD
       └── Flux
```

---

# STACK RECOMENDADO PARA PRACTICAR

Un proyecto didáctico completo:

```text
React / React Native
         │
         ▼
       Go API
         │
         ▼
    PostgreSQL
```

Controlado mediante:

```text
Git
 │
 ▼
GitHub/GitLab
 │
 ├── Issues
 ├── Branches
 ├── Pull Requests
 ├── Reviews
 ├── Actions / CI
 └── Releases
```

y contenerizado mediante:

```text
Docker
+
Docker Compose
```

---

# FLUJO COMPLETO DE DESARROLLO

El objetivo final del curso es que el participante comprenda completamente el siguiente proceso:

```text
Issue
  │
  ▼
git switch main
  │
  ▼
git pull --ff-only origin main
  │
  ▼
git switch -c feat/nueva-funcion
  │
  ▼
Development
  │
  ▼
git add
  │
  ▼
git commit
  │
  ▼
git fetch origin
  │
  ▼
git rebase origin/main
  │
  ▼
git push
  │
  ▼
Pull Request
  │
  ├── CI
  ├── Tests
  ├── Code Review
  └── Approval
        │
        ▼
       Merge
        │
        ▼
       main
        │
        ▼
      Release
```

---

# RESULTADO ESPERADO

Una persona con conocimientos fundamentales de Git sabe:

```text
init
clone
status
add
commit
log
diff
branch
switch
merge
pull
push
```

Una persona con conocimientos intermedios debe comprender además:

```text
Working Tree
Staging Area
HEAD
Refs
Remote tracking branches
Merge conflicts
Merge strategies
Rebase
Interactive rebase
Restore
Reset
Revert
Reflog
Stash
Cherry-pick
Tags
Bisect
Hooks
Worktrees
Submodules
Pull Requests
Branch protection
Code Review
Conventional Commits
CI/CD
```

Pero el verdadero objetivo no consiste en memorizar comandos.

El participante debe ser capaz de recibir una situación como:

> "Cuatro desarrolladores están trabajando simultáneamente en una aplicación y necesitamos integrar sus cambios sin perder información."

y diseñar de manera autónoma:

```text
Repositorio
     │
     ▼
main protegida
     │
     ├── feat/*
     ├── fix/*
     ├── docs/*
     └── refactor/*
            │
            ▼
         Commits
            │
            ▼
      Pull Requests
            │
      ┌─────┼─────┐
      ▼     ▼     ▼
     CI   Tests Review
      └─────┼─────┘
            ▼
           main
            │
            ▼
           Tag
            │
            ▼
         Release
```

Cuando el participante puede **crear este flujo, comprenderlo, diagnosticar sus errores, resolver conflictos y recuperar trabajo perdido**, puede considerarse que posee un **nivel intermedio sólido de Git**.

---

# REFERENCIAS TÉCNICAS RECOMENDADAS

Para continuar el aprendizaje debe priorizarse la documentación oficial.

* Referencia oficial de Git, que organiza los comandos en configuración, creación de proyectos, snapshots, branching/merging, colaboración, inspección, patching y debugging.
* Documentación de GitHub sobre ramas, Pull Requests y protección de ramas.
* Documentación de GitLab sobre Merge Requests, ramas protegidas y CI/CD.
* Especificación Conventional Commits 1.0.0 para estandarización de mensajes.
