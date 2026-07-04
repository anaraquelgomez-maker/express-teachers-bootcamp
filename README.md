# Express Teachers Bootcamp

Este repositorio documenta el desarrollo de una API REST construida con **Express** y **Prisma ORM**, como parte del proceso de aprendizaje del bootcamp. A continuación se detalla lo desarrollado en cada etapa del curso.

## 📚 Resumen general

A lo largo del bootcamp se construyó una API para la gestión de estudiantes y materias, incorporando progresivamente:

- Un servidor Express con endpoints CRUD
- Integración de Prisma ORM con modelos de datos (estudiantes y materias)
- Un sistema de autenticación con login y JWT
- Middleware de autenticación para proteger rutas mediante Bearer token

## 🗂️ Bitácora de desarrollo (por clase / avance)

### 1️⃣ Inicialización del servidor Express
**Commit:** `feat: initialize Express server with CRUD endpoints and t...`

- Configuración inicial del proyecto con **Express**
- Creación del servidor base (`app.listen`) corriendo en el puerto `3000`
- Uso de `express.json()` como middleware para parsear cuerpos de petición en formato JSON
- Manejo de datos en memoria mediante un arreglo `students`, simulando una base de datos temporal
- Implementación de un **CRUD completo** de estudiantes:

  | Método | Ruta | Descripción |
  |---|---|---|
  | GET | `/api/estudiantes` | Devuelve el total y la lista completa de estudiantes |
  | GET | `/api/estudiantes/:id` | Devuelve un estudiante por su `id`, o `404` si no existe |
  | POST | `/api/estudiantes` | Crea un nuevo estudiante (valida campos obligatorios: `firstName`, `lastName`, `age`, `email`) |
  | PUT | `/api/estudiantes/:id` | Actualiza un estudiante existente combinando los datos actuales con los nuevos |
  | DELETE | `/api/estudiantes/:id` | Elimina un estudiante por su `id` y devuelve el registro eliminado |

- Cada estudiante contiene los siguientes campos:
  - `id`, `firstName`, `lastName`, `age`, `email`, `phone`
  - `address` (objeto con `country` y `city`)
  - `isActive` (booleano)
  - `courses` (arreglo de materias inscritas)
- Manejo de errores básico con códigos de estado HTTP (`200`, `201`, `400`, `404`)
- Uso de un contador `nextId` para asignar IDs incrementales a nuevos estudiantes

### 2️⃣ Integración de Prisma y modelos de datos
**Commit:** `feat: add Prisma setup with student and subject models, API ...`

- Instalación y configuración de **Prisma ORM**
- Definición del esquema (`schema.prisma`) con los modelos:
  - **Student** (estudiante)
  - **Subject** (materia)
- Conexión a la base de datos mediante `DATABASE_URL`
- Generación del cliente de Prisma
- Endpoints de la API conectados a los modelos definidos

### 3️⃣ Autenticación de usuarios (login + JWT)
**Commit:** `feat: add authentication routes with login functionality and J...`

- Creación de rutas de autenticación (`/auth/login`, etc.)
- Implementación del login con validación de credenciales
- Generación de **JSON Web Tokens (JWT)** al iniciar sesión

### 4️⃣ Middleware de autenticación
**Commit:** `feat: add authentication middleware to validate Bearer token`

- Creación de un middleware para validar el **Bearer token** en las peticiones
- Protección de rutas que requieren autenticación
- Manejo de errores cuando el token es inválido o no está presente

## 🌿 Ramas de trabajo

- **`main`** — Versión estable
- **`develop`** — Rama activa de desarrollo (donde se fueron integrando los avances de cada clase)

## 🛠️ Tecnologías utilizadas

| Tecnología | Uso |
|---|---|
| Express | Framework del servidor / definición de rutas |
| Prisma ORM | Modelado y acceso a la base de datos |
| pnpm | Gestor de paquetes y workspaces |
| JWT | Autenticación basada en tokens |
| Nodemon | Recarga automática en desarrollo |


## 👤 Autor

Proyecto desarrollado como parte del **Desarrollo de Clases**💥​.
