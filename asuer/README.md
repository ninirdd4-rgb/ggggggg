# Sistema de Gestión para ASUR

Proyecto de pruebas realizado sobre una plataforma web desarrollada para ASUR
(Asociación de Sordos del Uruguay), como parte del Proyecto Final de Tecnicatura
de la Licenciatura en Tecnologías de la Información - UTEC.

## Objetivo

Validar la calidad y correcto funcionamiento de una plataforma destinada a la
gestión de usuarios, perfiles, funcionalidades, actividades, espacios,
reservas y auditorías.

## Rol

Participación en las actividades de análisis, diseño, ejecución y seguimiento
de pruebas, así como en la gestión y documentación de defectos.

## Herramientas

- TestLink
- Mantis
- Postman
- DBeaver
- PostgreSQL

## Tipos de pruebas

- Pruebas funcionales
- Pruebas de API
- Pruebas web
- Pruebas de validación
- Pruebas de regresión
- Pruebas de base de datos
- Pruebas de reglas de negocio

## Estructura

- `01-plan-pruebas/` — Plan general de pruebas.
- `02-casos-prueba/` — Casos de prueba y técnicas utilizadas.
- `03-ejecuciones/` — Resultados de ejecución de cada versión.
- `04-defectos/` — Defectos registrados en Mantis.
- `05-metricas/` — Informe final y métricas.
- `06-evidencias/` — Evidencias visuales de las pruebas.

## Ciclos de prueba

Los casos de prueba definidos para API y Web fueron reutilizados en dos
ejecuciones:

- API v1
- API v2
- Web v1
- Web v2

La segunda ejecución permitió realizar una nueva validación sobre la versión
actualizada del sistema y comprobar la corrección de los defectos detectados
durante la primera ejecución.
