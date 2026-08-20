# QA — Sistema de Gestión PFT-DZ-GRUPO06-2025

## Resumen del Proyecto

Sesión de pruebas de Aseguramiento de Calidad (QA) para el sistema de gestión **PFT-DZ-GRUPO06-2025**, enfocada en la validación de diferentes módulos funcionales de la aplicación.

Se realizaron pruebas funcionales, de validación, reglas de negocio y seguridad, utilizando **MantisBT** para el registro, seguimiento y gestión de los defectos encontrados durante las pruebas.

Los defectos fueron documentados con información de prioridad, gravedad, reproducibilidad, módulo afectado, estado y resolución.

> Los nombres de informadores y responsables fueron omitidos de esta documentación para preservar la privacidad de los integrantes del proyecto.

## Errores Reportados (MantisBT)

* **[[0042693]] - Registro de perfiles con datos inválidos**
  * **Prioridad:** Alta
  * **Gravedad:** Mayor
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema permite crear un perfil utilizando datos inválidos.

* **[[0042694]] - Registro de perfiles con campos obligatorios faltantes**
  * **Prioridad:** Alta
  * **Gravedad:** Mayor
  * **Reproducibilidad:** A veces
  * **Problema:** El sistema permite registrar un perfil sin completar campos obligatorios.

* **[[0043292]] - Filtro por estado incorrecto en listado de perfiles**
  * **Prioridad:** Normal
  * **Gravedad:** Mayor
  * **Reproducibilidad:** Siempre
  * **Problema:** El filtro por estado no aplica correctamente sobre el listado de perfiles.

* **[[0042695]] - Registro de funcionalidades con datos inválidos**
  * **Prioridad:** Normal
  * **Gravedad:** Mayor
  * **Reproducibilidad:** A veces
  * **Problema:** El sistema permite registrar funcionalidades utilizando datos inválidos.

* **[[0042669]] - Generación de reportes de reservas**
  * **Prioridad:** Alta
  * **Gravedad:** Mayor
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema no genera correctamente los reportes correspondientes a las reservas de espacios.

* **[[0042668]] - Validación de reservas consecutivas**
  * **Prioridad:** Alta
  * **Gravedad:** Bloqueo
  * **Reproducibilidad:** Siempre
  * **Problema:** Se produce un bloqueo durante las validaciones de reservas consecutivas.

* **[[0042667]] - Validación de solapamiento de reservas**
  * **Prioridad:** Alta
  * **Gravedad:** Bloqueo
  * **Reproducibilidad:** Siempre
  * **Problema:** Se produce un bloqueo durante la validación de solapamiento al registrar nuevas reservas.

* **[[0042666]] - Registro de nuevas reservas**
  * **Prioridad:** Urgente
  * **Gravedad:** Bloqueo
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema no permite registrar nuevas reservas.

* **[[0042664]] - Reactivación de espacios activos**
  * **Prioridad:** Normal
  * **Gravedad:** Menor
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema permite reactivar espacios que ya se encuentran activos.

* **[[0042663]] - Validación de restricciones de estado**
  * **Prioridad:** Urgente
  * **Gravedad:** Bloqueo
  * **Reproducibilidad:** Siempre
  * **Problema:** No es posible validar las restricciones relacionadas con el estado debido a que el sistema no permite registrar nuevas reservas.

* **[[0042662]] - Modificación de espacios con datos inválidos**
  * **Prioridad:** Alta
  * **Gravedad:** Mayor
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema permite modificar los datos de un espacio utilizando información inválida.

* **[[0042661]] - Registro de espacios con datos inválidos**
  * **Prioridad:** Urgente
  * **Gravedad:** Mayor
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema permite registrar nuevos espacios utilizando datos inválidos.

* **[[0042660]] - Inscripción en actividades canceladas**
  * **Prioridad:** Urgente
  * **Gravedad:** Mayor
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema permite realizar inscripciones en actividades que fueron canceladas.

* **[[0042658]] - Inscripción en actividades finalizadas**
  * **Prioridad:** Urgente
  * **Gravedad:** Mayor
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema permite realizar inscripciones en actividades que ya finalizaron.

* **[[0042657]] - Eliminación de actividades inactivas**
  * **Prioridad:** Normal
  * **Gravedad:** Menor
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema permite eliminar actividades que ya se encuentran inactivas.

* **[[0042656]] - Listado de actividades con filtros**
  * **Prioridad:** Alta
  * **Gravedad:** Mayor
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema no carga o despliega correctamente el listado de actividades cuando se aplican filtros.

* **[[0042655]] - Listado de actividades**
  * **Prioridad:** Alta
  * **Gravedad:** Mayor
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema no carga o despliega correctamente el listado de actividades disponibles.

* **[[0042654]] - Registro de actividades sin solapamiento**
  * **Prioridad:** Urgente
  * **Gravedad:** Mayor
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema no permite registrar una nueva actividad cuando no existe solapamiento con otra actividad.

* **[[0042653]] - Bloqueo de usuario tras intentos fallidos**
  * **Prioridad:** Alta
  * **Gravedad:** Mayor
  * **Reproducibilidad:** Siempre
  * **Problema:** El mecanismo de autenticación no bloquea al usuario después de cinco intentos de inicio de sesión incorrectos.
  * **Tipo:** Seguridad

* **[[0042659]] - Inscripción antes del período habilitado**
  * **Prioridad:** Urgente
  * **Gravedad:** Mayor
  * **Reproducibilidad:** Siempre
  * **Problema:** El sistema permite realizar inscripciones antes de que comience el período de inscripción establecido.
  * **Estado:** Abierta

## Aprendizajes Clave de QA

* **Validación de datos:** Las pruebas con datos inválidos permiten verificar que las reglas de validación sean aplicadas correctamente tanto en registros como en modificaciones.

* **Reglas de negocio:** Las pruebas permitieron detectar problemas relacionados con períodos de inscripción, actividades canceladas o finalizadas y restricciones de reservas.

* **Pruebas de seguridad:** La validación del inicio de sesión permitió identificar un problema relacionado con la ausencia de bloqueo después de múltiples intentos fallidos.

* **Defectos bloqueantes:** Algunos errores impedían continuar con determinadas pruebas, como el registro de nuevas reservas. Estos defectos pueden afectar la ejecución de otros casos relacionados.

* **Reproducibilidad:** Registrar la frecuencia con la que ocurre un defecto permite determinar si el comportamiento es consistente o intermitente.

* **Trazabilidad:** El uso de identificadores únicos de MantisBT permite relacionar cada defecto con las pruebas ejecutadas y realizar seguimiento de su resolución.

## Resumen de Defectos

| Métrica | Resultado |
|---|---:|
| Defectos registrados | 20 |
| Defectos corregidos | 19 |
| Defectos abiertos | 1 |
| Defectos de gravedad Bloqueo | 4 |
| Defectos de gravedad Mayor | 15 |
| Defectos de gravedad Menor | 2 |

## Estado del Proyecto

La mayoría de los defectos identificados durante las pruebas fueron **corregidos y cerrados/resueltos** mediante el seguimiento realizado en MantisBT.

Al momento del registro presentado, permanece **1 defecto abierto**, correspondiente a la validación del período de inscripción de actividades.

## Herramientas Utilizadas

* **MantisBT** — Registro y seguimiento de defectos.
* **TestLink** — Gestión y ejecución de casos de prueba.
* **Pruebas manuales** — Validación funcional y de reglas de negocio.
* **Pruebas de seguridad** — Validación del comportamiento del mecanismo de autenticación.
