
# 🧪 Sistema ASUR — Plan de Pruebas API

> Proyecto: `PFT-DZ-GRUPO06-2025` · Suite: **Gestión Institucional de ASUR - API**
> Backend desarrollado con **Spring Boot**, con pruebas funcionales sobre endpoints REST, validaciones, autorización, reglas de negocio y manejo de errores.

![Casos de prueba](https://img.shields.io/badge/Casos%20de%20prueba-193-blue)
![Tiempo estimado](https://img.shields.io/badge/Tiempo%20estimado-7.28h-informational)
![Tiempo real](https://img.shields.io/badge/Tiempo%20real-4.83h-success)
![Ejecución](https://img.shields.io/badge/Tipo-Manual-lightgrey)

Esta es una selección curada de los casos de prueba más representativos del plan completo (193 casos), agrupados por módulo funcional.

Las pruebas fueron diseñadas para validar operaciones CRUD, autenticación, autorización por roles, validaciones de datos, reglas de negocio, restricciones por estado y manejo de errores del backend.

La ejecución se realizó mediante **colecciones de Postman**, utilizando **TestLink** para la gestión y seguimiento de los casos de prueba.

---

## 📑 Índice

* [🔐 Autenticación](#-autenticación)
* [👤 Gestión de Usuarios](#-gestión-de-usuarios)
* [🪪 Gestión de Perfiles](#-gestión-de-perfiles)
* [⚙️ Gestión de Funcionalidades](#️-gestión-de-funcionalidades)
* [🔗 Vinculación de Funcionalidades a Perfiles](#-vinculación-de-funcionalidades-a-perfiles)
* [📅 Gestión de Actividades](#-gestión-de-actividades)
* [🏛️ Gestión de Espacios y Reservas](#️-gestión-de-espacios-y-reservas)
* [🕵️ Gestión de Auditoría](#️-gestión-de-auditoría)
* [🛠️ Stack de pruebas](#️-stack-de-pruebas)

---

## 🔐 Autenticación

**Endpoint base:** `POST /api/auth/login`

### ✅ `PFTDZGR06-266` — Inicio de sesión exitoso

**Prioridad:** 🔴 Alta

Valida el inicio de sesión utilizando credenciales correspondientes a un usuario activo.

**Resultado esperado:** `200 OK` y generación de un **token JWT** válido para acceder a los recursos autorizados.

---

### ❌ `PFTDZGR06-267` — Credenciales inválidas

**Prioridad:** 🔴 Alta

Valida el comportamiento del sistema cuando se proporciona una combinación incorrecta de email y contraseña.

**Resultado esperado:** `400 Bad Request`. El sistema rechaza las credenciales y no genera un token de autenticación.

---

### 🚫 `PFTDZGR06-268` — Login de usuario inactivo

**Prioridad:** 🔴 Alta

Intenta iniciar sesión con un usuario cuyo estado se encuentra **INACTIVO**.

**Resultado esperado:** `401 Unauthorized`. El sistema no permite el acceso.

---

### 🚫 `PFTDZGR06-461` — Login de usuario sin validar

**Prioridad:** 🔴 Alta

Verifica que un usuario registrado pero pendiente de validación no pueda autenticarse en el sistema.

**Resultado esperado:** `401 Unauthorized`.

---

### 🔐 `PFTDZGR06-271` — Fuerza bruta / múltiples intentos fallidos

**Prioridad:** 🔴 Alta

Verifica la respuesta del sistema ante múltiples intentos fallidos consecutivos de inicio de sesión.

**Precondición:** Usuario existente y activo.

**Pasos principales:**

| Nº | Paso                                                       |
| -- | ---------------------------------------------------------- |
| 1  | Enviar una solicitud de login con credenciales incorrectas |
| 2  | Repetir el intento al menos 6 veces                        |
| 3  | Verificar la respuesta del sistema                         |

**Resultado esperado:** El sistema rechaza los intentos y bloquea temporalmente el acceso durante **15 minutos**.

---

## 👤 Gestión de Usuarios

**Endpoint base:** `POST /api/usuarios` · `GET /api/usuarios` · `PUT /api/usuarios/{id}`

### ✅ `PFTDZGR06-216` / `PFTDZGR06-217` / `PFTDZGR06-218` — Registro de Usuario

**Prioridad:** 🔴 Alta

Valida el registro exitoso de usuarios de los diferentes tipos contemplados por el sistema:

* Administrador
* Socio
* No Socio

**Resultado esperado:** `201 Created` y creación correcta del usuario.

---

### ❌ `PFTDZGR06-221` — Registro con datos duplicados

**Prioridad:** 🔴 Alta

Intenta registrar un usuario utilizando información que ya existe en el sistema, como documento, email o teléfono.

**Resultado esperado:** `409 Conflict`. El sistema rechaza el registro y evita la duplicación de datos.

---

### 🔒 `PFTDZGR06-247` — Listado de usuarios por rol no autorizado

**Prioridad:** 🔴 Alta

Verifica que un usuario sin los permisos correspondientes no pueda consultar el listado general de usuarios.

**Resultado esperado:** `403 Forbidden`.

---

### 🔄 `PFTDZGR06-252` — Modificar de No Socio a Socio

**Prioridad:** 🔴 Alta

Valida que un administrador pueda modificar el tipo de usuario de **No Socio a Socio**.

```http
PUT /api/usuarios/{id}
Authorization: Bearer <token>
Content-Type: application/json

{
  "priNombre": "Carlos",
  "priApellido": "Gómez",
  "mail": "carlos.gomez@dominio.com",
  "idPerfil": 2,
  "idCiudad": 15
}
```

**Resultado esperado:** `200 OK`.

El sistema actualiza correctamente el usuario y genera automáticamente el **número de socio (`nroSocio`)** correspondiente.

---

### 🔒 `PFTDZGR06-272` — Administrador intenta modificar contraseña ajena

**Prioridad:** 🔴 Alta

Verifica las restricciones de autorización sobre la modificación de contraseñas de otros usuarios.

**Resultado esperado:** `403 Forbidden`.

---

## 🪪 Gestión de Perfiles

**Endpoint base:** `POST /api/perfiles` · `GET /api/perfiles` · `PUT /api/perfiles/{id}`

### ✅ `PFTDZGR06-303` — Registro de Perfil

**Prioridad:** 🔴 Alta

Valida el alta de un nuevo perfil utilizando datos válidos.

**Resultado esperado:** `201 Created`.

El perfil se crea inicialmente con estado **INACTIVO**.

---

### ❌ `PFTDZGR06-306` — Registro de Perfil con nombre duplicado

**Prioridad:** 🔴 Alta

Intenta registrar un perfil utilizando un nombre que ya existe.

**Resultado esperado:** `409 Conflict`. El sistema no permite perfiles duplicados.

---

### 🔄 `PFTDZGR06-320` / `PFTDZGR06-324` — Baja y Reactivación de Perfil

**Prioridad:** 🟡 Media

Valida la eliminación lógica de un perfil y su posterior reactivación.

**Resultado esperado:** `200 OK` en ambas operaciones y actualización correcta del estado del perfil.

---

### 🚫 `PFTDZGR06-328` — Asignar perfil inactivo a un usuario

**Prioridad:** 🔴 Alta

Verifica que un perfil con estado **INACTIVO** no pueda ser asociado a un usuario nuevo o existente.

```http
POST /api/usuarios
Authorization: Bearer <token>

{
  "idPerfil": 3
}
```

**Resultado esperado:** `422 Unprocessable Entity`.

El sistema rechaza la operación y evita asociar perfiles dados de baja.

---

## ⚙️ Gestión de Funcionalidades

**Endpoint base:** `POST /api/funcionalidades` · `GET /api/funcionalidades` · `PUT /api/funcionalidades/{id}`

### ✅ `PFTDZGR06-419` — Registro de Funcionalidad

**Prioridad:** 🟡 Media

Valida el registro de una funcionalidad utilizando datos válidos.

**Resultado esperado:** `201 Created`.

---

### 🔗 `PFTDZGR06-444` — Vincular funcionalidades a un perfil

**Prioridad:** 🟡 Media

Valida la asociación de una o más funcionalidades con un perfil existente.

**Resultado esperado:** `200 OK` y creación correcta de las relaciones.

---

### 🚫 `PFTDZGR06-447` — Vincular funcionalidad inactiva a un perfil

**Prioridad:** 🔴 Alta

Verifica que una funcionalidad con estado **INACTIVO** no pueda ser vinculada a un perfil.

**Resultado esperado:** `422 Unprocessable Entity`.

---

### 🔗 `PFTDZGR06-451` — Vincular funcionalidades ya vinculadas

**Prioridad:** 🔴 Alta

Verifica que el sistema evite duplicar una relación existente entre un perfil y sus funcionalidades.

```http
POST /api/permisos/acceso-funcionalidad
Authorization: Bearer <token>
Content-Type: application/json

{
  "idPerfil": 1,
  "funcionalidadesIds": [4, 5, 6]
}
```

**Resultado esperado:** `409 Conflict`.

La operación no debe generar relaciones duplicadas ni modificar indebidamente los datos existentes.

---

## 🔗 Vinculación de Funcionalidades a Perfiles

La vinculación entre perfiles y funcionalidades constituye una regla central de autorización del sistema.

### 🔗 `PFTDZGR06-444` — Vinculación de funcionalidades a un Perfil

**Prioridad:** 🟡 Media

Valida la asignación de funcionalidades a un perfil mediante el endpoint de permisos.

**Resultado esperado:** Las funcionalidades quedan correctamente asociadas al perfil y disponibles según los permisos definidos.

---

### 🚫 `PFTDZGR06-447` — Restricción de funcionalidades inactivas

**Prioridad:** 🔴 Alta

Intenta asociar una funcionalidad cuyo estado es **INACTIVO**.

**Resultado esperado:** `422 Unprocessable Entity`. El sistema rechaza la vinculación.

---

### 🔒 `PFTDZGR06-451` — Prevención de vínculos duplicados

**Prioridad:** 🔴 Alta

Verifica que una funcionalidad que ya se encuentra asociada al perfil no pueda volver a vincularse.

**Resultado esperado:** `409 Conflict`.

---

## 📅 Gestión de Actividades

**Endpoint base:** `POST /api/actividades` · `GET /api/actividades` · `PUT /api/actividades/{id}`

### Registro e Inscripción

### ✅ `PFTDZGR06-329` — Registro de Actividad con datos válidos

**Prioridad:** 🟡 Media

Valida la creación de una actividad utilizando fecha, hora, espacio y demás datos requeridos.

**Resultado esperado:** `201 Created`.

---

### 🚫 `PFTDZGR06-370` — Solapamiento de horarios en el mismo espacio

**Prioridad:** 🔴 Alta

Valida una regla crítica de negocio: no se deben registrar dos actividades que ocupen el mismo espacio durante horarios coincidentes.

**Precondición:** Existe una actividad registrada para el `2025-12-22` a las `14:30`.

```http
POST /api/actividades
Authorization: Bearer <token>
Content-Type: application/json

{
  "fecActividad": "2025-12-22",
  "horaActividad": "14:30:00",
  "idEspacio": 1
}
```

**Resultado esperado:** `409 Conflict`.

El sistema rechaza la nueva actividad y no genera un registro duplicado para el espacio y horario ocupado.

---

### ✅ `PFTDZGR06-371` — Actividades consecutivas sin solapamiento

**Prioridad:** 🔴 Alta

Verifica que puedan registrarse actividades consecutivas cuando existe el margen de tiempo definido por la regla de negocio.

**Resultado esperado:** `201 Created`.

---

### 🚫 `PFTDZGR06-359` — Inscripción antes del período habilitado

**Prioridad:** 🔴 Alta

Intenta realizar una inscripción antes de la fecha de apertura configurada para la actividad.

**Resultado esperado:** `422 Unprocessable Entity`.

---

### 🚫 `PFTDZGR06-418` — Baja de actividad con inscripción en curso

**Prioridad:** 🔴 Alta

Verifica que una actividad no pueda darse de baja cuando existen inscripciones activas o el período de inscripción se encuentra en curso.

**Resultado esperado:** `409 Conflict`.

---

## 🏛️ Gestión de Espacios y Reservas

**Endpoint base:** `POST /api/espacios` · `GET /api/espacios` · `PUT /api/espacios/{id}` · `POST /api/reservas/confirmar`

### ✅ `PFTDZGR06-377` — Registro de Espacio

**Prioridad:** 🔴 Alta

Valida el alta de un nuevo espacio utilizando datos válidos.

**Resultado esperado:** `201 Created`.

El espacio se crea inicialmente con estado **INACTIVO**, requiriendo activación posterior.

---

### 🚫 `PFTDZGR06-393` — Reservar un espacio inactivo

**Prioridad:** 🔴 Alta

Verifica que un espacio con estado **INACTIVO** no pueda recibir nuevas reservas.

```http
POST /api/reservas/confirmar
Authorization: Bearer <token>
Content-Type: application/json

{
  "fecReservaActividad": "2025-12-28",
  "horaReservaActividad": "10:00:00",
  "duracion": 60,
  "cantidadPersonas": 300,
  "idUsuario": 2,
  "idEspacio": 1,
  "tipoPago": "EFECTIVO"
}
```

**Resultado esperado:** `422 Unprocessable Entity`.

El sistema rechaza la reserva debido al estado inactivo del espacio.

---

### 🚫 `PFTDZGR06-407` — Reserva con solapamiento de horario

**Prioridad:** 🔴 Alta

Valida que un espacio no pueda reservarse cuando ya existe otra reserva que ocupa el mismo intervalo horario.

**Resultado esperado:** `409 Conflict`.

---

### ✅ `PFTDZGR06-408` — Reservas consecutivas sin solapamiento

**Prioridad:** 🟡 Media

Verifica que dos reservas consecutivas puedan registrarse cuando no existe superposición entre sus horarios.

**Resultado esperado:** `201 Created`.

---

### 🚫 `PFTDZGR06-411` — Cancelación de una reserva ya cancelada

**Prioridad:** 🔴 Alta

Intenta cancelar nuevamente una reserva cuyo estado ya es **CANCELADA**.

**Resultado esperado:** `409 Conflict`.

---

## 🕵️ Gestión de Auditoría

**Endpoint base:** `GET /api/auditorias/{tipoAuditoria}`

Tipos contemplados: `Usuario` · `Actividad` · `Pago`

### 📋 `PFTDZGR06-278` — Consulta de auditoría por tipo

**Prioridad:** 🔴 Alta

Valida que un usuario con permisos administrativos pueda consultar los registros de auditoría correspondientes al tipo solicitado.

**Resultado esperado:** `200 OK`.

---

### 🔒 `PFTDZGR06-282` — Acceso de usuario no autorizado

**Prioridad:** 🔴 Alta

Verifica que usuarios sin permisos administrativos no puedan consultar información de auditoría.

**Resultado esperado:** `403 Forbidden`.

---

### 🔍 `PFTDZGR06-283` — Consulta sin registros encontrados

**Prioridad:** 🟡 Media

Realiza una consulta de auditoría para un tipo que no posee registros disponibles.

**Resultado esperado:** `404 Not Found`.

---

## 🛠️ Stack de pruebas

| Componente       | Herramienta / Tecnología                                     |
| ---------------- | ------------------------------------------------------------ |
| Backend          | Spring Boot                                                  |
| Gestión de casos | TestLink                                                     |
| Ejecución        | Postman                                                      |
| Tipo de prueba   | Manual                                                       |
| API              | REST                                                         |
| Autenticación    | JWT                                                          |
| Cobertura        | Casos positivos, negativos, autorización y reglas de negocio |

### Cobertura de escenarios

Las pruebas contemplan principalmente:

* ✅ Operaciones exitosas.
* ❌ Validaciones de datos inválidos.
* 🔐 Autenticación y autorización.
* 👥 Restricciones según rol.
* 🔄 Cambios de estado y eliminación lógica.
* 🚫 Restricciones sobre entidades inactivas.
* 🔗 Prevención de relaciones duplicadas.
* 📅 Validación de solapamientos de horarios.
* 🏛️ Restricciones sobre espacios y reservas.
* 🕵️ Control y consulta de auditoría.
* ⚠️ Manejo de códigos HTTP y errores de negocio.
