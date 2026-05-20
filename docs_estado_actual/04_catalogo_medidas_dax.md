# 04 - Catálogo de medidas DAX

## Lista completa de medidas
Todas en `DS_Incidencias`: `UltAct`, `MsjBienvenida`, `IncCerradas`, `IncEnProceso`, `IncAbiertas`, `IncTotales`, `IncBloqueadas`, `DuracionINC_Promedio`, `Inactividad`, `Disponible`, `Baja disponibilidad`, `CantProductos`, `Medida`.【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L4-L124】

## Tabla de evaluación
| Medida | Objetivo funcional | Fórmula resumida | Complejidad | Riesgo | Recomendación |
|---|---|---|---|---|---|
| IncAbiertas | Conteo abiertas | DISTINCTCOUNT ID con State=New y tag INCIDENCIA | Media | Filtro textual repetido | Crear medida base de incidencias |
| IncEnProceso | Conteo activas | DISTINCTCOUNT ID con State=Active | Media | Mismo patrón repetido | Consolidar patrón |
| IncCerradas | Conteo cerradas/resueltas | DISTINCTCOUNT ID con State in Closed/Resolved | Media | Dependencia de nomenclatura State | Normalizar estado |
| IncBloqueadas | Conteo bloqueadas | DISTINCTCOUNT ID con State=Blocked | Media | Idem | Normalizar estado |
| IncTotales | Suma de medidas previas | IncAbiertas+... | Baja | Riesgo de doble lógica | Mantener si medidas base robustas |
| DuracionINC_Promedio | Promedio horas | AVERAGE(DuracionINC) redondeado | Baja | Depende de DuracionINC | Revisar outliers |
| Inactividad | Horas inactivas | SUMX con condición Disponible=NO | Media/Alta | Iterador sobre tabla | Evaluar columna precomputada |
| Disponible | Horas disponibles | SUMX(TiempoTotal-DuracionINC) | Media/Alta | Iterador y dependencia NOW() | Definir snapshot |
| Baja disponibilidad | Horas baja disponibilidad | SUMX condición Disponible=SI | Media/Alta | Semántica ambigua | Validar definición funcional |
| CantProductos | Distintos productos | DISTINCTCOUNT no blank | Baja | Baja | Mantener |
| MsjBienvenida | UX | USERPRINCIPALNAME | Baja | Sin impacto KPI | Mantener opcional |
| UltAct | Texto estático | "Última actualización:" | Baja | Requiere concat con fecha | Complementar con medida de fecha |
| Medida | Placeholder | ". " | Baja | Posible ruido técnico | Revisar uso/retirar |

## Medidas principales en lenguaje simple
- `IncAbiertas/IncEnProceso/IncCerradas/IncBloqueadas`: cuentan incidencias por estado usando ID único y tag `INCIDENCIA`.
- `DuracionINC_Promedio`: promedio de horas entre inicio y fin.
- `Disponible/Inactividad`: estimaciones de horas disponibles vs no disponibles.

## Patrones DAX riesgosos
- Uso reiterado de filtros sobre texto (`CONTAINSSTRING`) en medidas de alto uso.
- `SUMX` sobre tabla completa para métricas temporales.

## Oportunidades de optimización
- Medida base `IncidenciasBase` + cálculo por dimensión Estado.
- Precalcular banderas y categorías en Power Query.
