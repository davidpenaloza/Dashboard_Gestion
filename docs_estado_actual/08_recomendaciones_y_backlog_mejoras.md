# 08 - Recomendaciones y backlog de mejoras

## Backlog priorizado
| ID | Mejora recomendada | Problema que resuelve | Prioridad | Complejidad | Riesgo impl. | Impacto esperado | Responsable sugerido | Validación funcional | Validación técnica | Horizonte |
|---|---|---|---|---|---|---|---|---|---|---|
| M01 | Parametrizar URL/Project/Team/QueryID en M | Hardcode en origen | Alta | Media | Bajo | Alto | BI Técnico | Sí | Sí | Corto |
| M02 | Crear dimensión Fecha única | Multiplicidad LocalDateTable | Alta | Media | Medio | Alto | BI Modelado | Sí | Sí | Corto |
| M03 | Migrar `FechaTomaDeControl` a tabla de parametrización | Regla hardcodeada | Alta | Media | Medio | Alto | BI + Negocio | Sí | Sí | Corto |
| M04 | Consolidar `Functions` y `FunctionsNew` | Duplicidad técnica | Media | Media | Medio | Medio | BI Técnico | No | Sí | Mediano |
| M05 | Refactor medidas `Inc*` con medida base | Repetición DAX | Media | Baja | Bajo | Medio | BI DAX | Sí | Sí | Corto |
| M06 | Reducción de densidad visual en páginas clave | Lentitud/usabilidad | Alta | Media | Bajo | Alto | BI UX | Sí | Sí | Corto |
| M07 | Catálogo de KPIs y diccionario datos | Falta gobierno documental | Alta | Baja | Bajo | Alto | BI + Funcional | Sí | No | Corto |
| M08 | Separar vistas Operativa / Ejecutiva | Navegación confusa | Media | Media | Bajo | Medio | BI UX | Sí | No | Mediano |
| M09 | Normalizar campos de texto (`Tags`, `EstadoHU`) | Inconsistencias de filtro | Media | Media | Bajo | Medio | BI Datos | Sí | Sí | Mediano |
| M10 | Política PII para `Assigned To` | Riesgo de exposición | Alta | Baja | Bajo | Alto | Data Gov | Sí | Sí | Corto |

## Clasificación
- **Quick wins:** M01, M05, M07, M10.
- **Mejoras importantes:** M02, M06, M08, M09.
- **Cambios estructurales / Refactor modelo:** M03, M04.
- **Mejoras visuales:** M06, M08.
- **Gobierno/documentación:** M07, M10.
