# 🧪 Sistema ASUR — Plan de Pruebas

> Proyecto: `PFT-DZ-GRUPO06-2025` · Suite: **Gestión Institucional de ASUR - WEB**
> Sistema desarrollado en **React**, con pruebas funcionales sobre UI, validaciones y flujos de negocio.

![Casos ejecutados](https://img.shields.io/badge/Casos%20de%20prueba-195-blue)
![Tiempo estimado](https://img.shields.io/badge/Tiempo%20estimado-3.78h-informational)
![Tiempo real](https://img.shields.io/badge/Tiempo%20real-3.52h-success)
![Ejecución](https://img.shields.io/badge/Tipo-Manual-lightgrey)

Esta es una selección curada de los casos de prueba más representativos del plan completo (195 casos), agrupados por módulo funcional. Cada caso incluye precondiciones, pasos clave y el resultado esperado.

---

## 📑 Índice

- [👤 Gestión de Usuarios](#-gestión-de-usuarios)
  - [Registro de Usuario](#registro-de-usuario)
  - [Login](#login)
  - [Baja / Reactivación](#baja--reactivación)
- [🪪 Gestión de Perfiles](#-gestión-de-perfiles)
- [⚙️ Gestión de Funcionalidades](#️-gestión-de-funcionalidades)
- [🔗 Vinculación de Funcionalidades a Perfiles](#-vinculación-de-funcionalidades-a-perfiles)
- [📅 Gestión de Actividades](#-gestión-de-actividades)
  - [Registro e Inscripción](#registro-e-inscripción)
  - [Baja y Reactivación](#baja-y-reactivación)
- [🕵️ Gestión de Auditoría](#️-gestión-de-auditoría)
- [🏛️ Gestión de Espacios y Reservas](#️-gestión-de-espacios-y-reservas)

---

## 👤 Gestión de Usuarios

### Registro de Usuario

#### ✅ `PFTDZGR06-55` — Registro de Usuario con datos válidos
**Prioridad:** 🔴 Alta

| Nº | Paso | Resultado esperado |
|----|------|---------------------|
| 1 | Seleccionar "Registro de nuevo usuario" | — |
| 2 | Completar todos los campos con datos válidos | — |
| 3 | Dar "Aceptar" a la confirmación de registro | El sistema procesa la operación con éxito |

---

#### ❌ `PFTDZGR06-47` — Registro con Número de Documento inválido
**Prioridad:** 🔴 Alta

Verifica el rechazo de una CI con dígito verificador incorrecto (ej. `49839501` vs. la válida `49839507`).

**Resultado esperado:** El sistema no permite continuar. *"El Número de Documento es incorrecto"*.

---

#### ❌ `PFTDZGR06-64` — Registro con Email inválido
**Prioridad:** 🔴 Alta

Ingresa un email con formato incorrecto (`emailinvalido@`).

**Resultado esperado:** *"El formato del email debe ser ejemplo@ejemplo.com"*.

---

#### 🔐 `PFTDZGR06-142` — Contraseña menor al mínimo requerido
**Prioridad:** 🔴 Alta

Ingresa una contraseña alfanumérica válida pero de menos de 8 caracteres (`hola123`).

**Resultado esperado:** *"La Contraseña debe tener como mínimo 8 caracteres"*.

---

#### 👥 `PFTDZGR06-67` — Registro de usuario Socio
**Prioridad:** 🔴 Alta

Valida el flujo completo de alta para el tipo de usuario **Socio**, incluyendo sus campos específicos.

**Resultado esperado:** El sistema procesa la operación con éxito.

---

### Login

#### ✅ `PFTDZGR06-99` — Login con credenciales válidas
**Prioridad:** 🟡 Media

| Nº | Paso |
|----|------|
| 1 | Ingresar al Login |
| 2 | Ingresar email válido |
| 3 | Ingresar contraseña válida |
| 4 | Seleccionar "Ingresar" |

**Resultado esperado:** Se permite el ingreso al sistema.

---

#### ❌ `PFTDZGR06-102` / `PFTDZGR06-103` — Credenciales incorrectas
**Prioridad:** 🟡 Media

Casos que validan que el sistema **no revele** cuál campo es incorrecto (email o contraseña), mostrando siempre el mismo mensaje genérico: *"Contraseña o Email incorrecto"*.

---

### Baja / Reactivación

#### 🔄 `PFTDZGR06-15` / `PFTDZGR06-98` — Baja y Reactivación de Usuario
**Prioridad:** 🟡 Media

Valida la **eliminación lógica** de un usuario y su posterior reactivación desde el listado filtrado por estado inactivo, verificando la actualización correcta del listado en ambos casos.

---

## 🪪 Gestión de Perfiles

#### ✅ `PFTDZGR06-16` — Registro de nuevo Perfil
**Prioridad:** 🔴 Alta

Alta de perfil con nombre y descripción válidos → **registro exitoso**.

#### ❌ `PFTDZGR06-109` — Descripción de Perfil inválida
**Prioridad:** 🔴 Alta

Descripción de más de 300 caracteres → operación rechazada.

#### 🔒 `PFTDZGR06-113` — Restricción de modificación de Nombre
**Prioridad:** 🔴 Alta

Verifica que el sistema **no permita** modificar el nombre de un perfil ya creado (regla de negocio de integridad).

---

## ⚙️ Gestión de Funcionalidades

#### ✅ `PFTDZGR06-115` — Alta de Funcionalidad
**Prioridad:** 🟡 Media

Registro con nombre y descripción válidos → operación exitosa.

#### ❌ `PFTDZGR06-188` — Descripción inválida (>300 caracteres)
**Prioridad:** 🔴 Alta

#### 🔄 `PFTDZGR06-122` / `PFTDZGR06-123` — Baja y Reactivación de Funcionalidad
**Prioridad:** 🟡 Media

---

## 🔗 Vinculación de Funcionalidades a Perfiles

#### 🔗 `PFTDZGR06-189` — Vincular múltiples funcionalidades a un Perfil
**Prioridad:** 🟡 Media

| Nº | Paso |
|----|------|
| 1 | Ingresar a "Gestión de Vinculaciones" |
| 2 | Seleccionar el perfil |
| 3 | Seleccionar la primera funcionalidad |
| 4 | Vincular una segunda funcionalidad |
| 5 | Confirmar la vinculación |

**Resultado esperado:** Operación exitosa, cambios guardados en el sistema.

#### 🔓 `PFTDZGR06-125` — Eliminar vínculo entre Perfil y Funcionalidad
**Prioridad:** 🟡 Media

---

## 📅 Gestión de Actividades

### Registro e Inscripción

#### ✅ `PFTDZGR06-227` — Registro de Actividad con datos válidos
**Prioridad:** 🟡 Media

#### ❌ `PFTDZGR06-237` — Registro con lugar/espacio ocupado
**Prioridad:** 🔴 Alta

Valida una regla clave de negocio: al elegir fecha/hora ya ocupadas, el listado de lugares disponibles **no debe mostrar** los espacios reservados en ese horario.

#### ❌ `PFTDZGR06-241` — Fecha de apertura de inscripción posterior a la actividad
**Prioridad:** 🔴 Alta

**Resultado esperado:** *"La fecha de apertura debe ser anterior a la actividad"*.

#### 📝 `PFTDZGR06-468` — Inscripción a Actividad con datos válidos
**Prioridad:** 🔴 Alta

#### 🚫 `PFTDZGR06-471` — Cancelación de Inscripción
**Prioridad:** 🔴 Alta

---

### Baja y Reactivación

#### 🚫 `PFTDZGR06-464` — No se puede dar de baja una actividad con inscripción abierta
**Prioridad:** 🔴 Alta

Regla de integridad: si el período de inscripción ya comenzó, el sistema bloquea la baja lógica de la actividad.

#### ✅ `PFTDZGR06-465` — Baja de actividad ya finalizada
**Prioridad:** 🔴 Alta

---

## 🕵️ Gestión de Auditoría

#### 📋 `PFTDZGR06-222` — Registro de acciones de usuario
**Prioridad:** 🔴 Alta

Verifica que cada operación (alta, baja, modificación, consulta) quede registrada con **fecha, hora, usuario, terminal y operación**.

#### 🔍 `PFTDZGR06-223` — Reporte de auditoría filtrado por usuario
**Prioridad:** 🔴 Alta

#### 📆 `PFTDZGR06-224` — Reporte de auditoría por rango de fechas
**Prioridad:** 🔴 Alta

---

## 🏛️ Gestión de Espacios y Reservas

#### ✅ `PFTDZGR06-479` — Registro de Espacio con datos válidos
**Prioridad:** 🔴 Alta

El espacio se crea con estado **Inactivo** por defecto, requiriendo activación posterior.

#### 🚫 `PFTDZGR06-496` — Restricción de baja con actividad asociada
**Prioridad:** 🔴 Alta

Un espacio con actividades o eventos vinculados **no puede eliminarse**, protegiendo la integridad referencial del sistema.

#### 💰 `PFTDZGR06-500` — Cálculo automático de vencimiento de seña
**Prioridad:** 🔴 Alta

Verifica que el sistema calcule la fecha límite de pago de seña **5 días hábiles antes** del evento, de forma automática.

#### 💵 `PFTDZGR06-501` / `PFTDZGR06-502` — Tarifas diferenciadas Socio / No Socio
**Prioridad:** 🔴 Alta

Comprueba que el importe mostrado varíe correctamente según el rol del usuario logueado.

#### ⏳ `PFTDZGR06-504` — Cancelación automática de reserva por falta de pago
**Prioridad:** 🔴 Alta

Si no se registra el pago de la seña antes del vencimiento, el sistema cambia automáticamente el estado de la reserva a **"Cancelada"**.
