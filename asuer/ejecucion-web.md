# Resultados de Pruebas — Aplicación Web

## Resumen

Se ejecutaron los mismos **195 casos de prueba** sobre dos builds de la aplicación Web:

* **Build v1.0:** primera ejecución.
* **Build v2.0:** segunda ejecución de los mismos casos para verificar los cambios realizados y detectar posibles regresiones.

Los resultados detallados de cada ejecución se encuentran en los archivos correspondientes.

---

## Resultados generales

| Build    | Casos ejecutados | Pasados | Fallados | Tasa de éxito |
| -------- | ---------------: | ------: | -------: | ------------: |
| **v1.0** |              195 |     192 |        3 |        98,46% |
| **v2.0** |              195 |     195 |        0 |      **100%** |

La segunda ejecución alcanzó una tasa de éxito del **100%**, con la totalidad de los casos ejecutados en estado **Pasado [v2]**.

---

## Build v1.0

| Resultado | Cantidad |
| --------- | -------: |
| Pasados   |      192 |
| Fallados  |        3 |
| **Total** |  **195** |

### Casos fallados

| Caso de prueba                                                      | Resultado |
| ------------------------------------------------------------------- | --------- |
| PFTDZGR06-146:029 — Registro de Socio con Subcomisión vacío         | Fallado   |
| PFTDZGR06-111:007 — Listado Filtro por Estado                       | Fallado   |
| PFTDZGR06-237:009 — Registro de Actividad con lugar/espacio ocupado | Fallado   |

### Observaciones

Los casos fallados permitieron identificar problemas relacionados con validaciones y comportamiento funcional de la aplicación.

En algunos casos se identificó una diferencia entre la validación realizada internamente por el sistema y el comportamiento observado en la interfaz gráfica.

---

## Build v2.0

La Build v2.0 fue ejecutada utilizando los mismos **195 casos de prueba** empleados en la Build v1.0.

| Resultado | Cantidad |
| --------- | -------: |
| Pasados   |  **195** |
| Fallados  |    **0** |
| **Total** |  **195** |

La ejecución de la Build v2.0 finalizó con el **100% de los casos de prueba en estado Pasado [v2]**.

---

## Comparación entre builds

La comparación entre ambas ejecuciones permite observar la evolución de los resultados después de los cambios realizados sobre la aplicación.

| Indicador                          |                     Resultado |
| ---------------------------------- | ----------------------------: |
| Casos corregidos: Fallado → Pasado |                         **3** |
| Casos que permanecieron fallados   |                         **0** |
| Regresiones: Pasado → Fallado      |                         **0** |
| Casos que permanecieron pasados    |                       **192** |
| Variación de la tasa de éxito      | **+1,54 puntos porcentuales** |

### Evolución

La primera ejecución obtuvo una tasa de éxito del **98,46%**, mientras que la segunda alcanzó el **100%**.

Los tres casos que habían resultado fallados en la Build v1.0 fueron ejecutados nuevamente en la Build v2.0 y finalizaron correctamente:

* **PFTDZGR06-146:029** — Registro de Socio con Subcomisión vacío.
* **PFTDZGR06-111:007** — Listado Filtro por Estado.
* **PFTDZGR06-237:009** — Registro de Actividad con lugar/espacio ocupado.

No se identificaron regresiones durante la segunda ejecución.

---

## Evidencia detallada

La ejecución completa de cada build se documenta por separado:

* [`WEB-v1.md`](./WEB-v1.md)
* [`WEB-v2.md`](./WEB-v2.md)

Los resultados corresponden a las ejecuciones registradas en **TestLink**.
