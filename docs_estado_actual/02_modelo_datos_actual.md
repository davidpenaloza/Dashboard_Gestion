# 02 - Modelo de datos actual

## Tablas existentes y tipo
| Tabla | Tipo inferido | Hecho observado |
|---|---|---|
| DS_Incidencias | Hecho principal | Contiene columnas de negocio y medidas KPI.【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L1-L500】 |
| De_Para | Auxiliar/catálogo | DATATABLE de mapeo de área resolutora.【Reporte Gestión de Soporte.SemanticModel/definition/tables/De_Para.tmdl:L28-L50】 |
| Functions / FunctionsNew | Técnica M | Funciones para conexión y ejecución WIQL.【Reporte Gestión de Soporte.SemanticModel/definition/tables/Functions.tmdl:L1-L120】 |
| Last Refresh Dataset | Técnica | Fecha/hora de última actualización local Chile.【Reporte Gestión de Soporte.SemanticModel/definition/tables/Last Refresh Dataset.tmdl:L20-L46】 |
| LocalDateTable_* + DateTableTemplate_* | Fecha automática | Auto date/time habilitado.【Reporte Gestión de Soporte.SemanticModel/definition/model.tmdl:L11-L24】 |

## Columnas principales (DS_Incidencias)
- Identificadores/estado: `ID`, `Work Item Type`, `State`, `Tags`.
- Contexto: `Torre`, `Fuente`, `Faena`, `DataLake`, `Componente`, `Area Resolutora`, `Producto`.
- Tiempo: `Fecha Inicio`, `Fecha Fin`, `FechaTomaDeControl`, `DuracionINC`, `TiempoTotal`.
- Calidad narrativa: `Descripción Breve`, `Solución`, `Workaround`.

## Relaciones observadas
- 4 relaciones de fecha (no se explicita cardinalidad/dirección en `relationships.tmdl`).【Reporte Gestión de Soporte.SemanticModel/definition/relationships.tmdl:L1-L20】
- No hay relación física DS_Incidencias↔De_Para; se usa `LOOKUPVALUE` en columna calculada `Area_Resolutora_Front`.【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L212-L219】

## Evaluación del modelo
- **Inferencia técnica:** modelo **plano/mixto** (no estrella estricta).

## Riesgos de granularidad
- Mezcla de `Feature` y `User Story` con lógica de “incidencias”.
- Posible coexistencia de registros con `Fecha Fin` nula (abiertos) y cerrados, impactando promedios.

## Riesgos de mantenibilidad
- Lógica hardcodeada en DAX de columnas.
- Dependencia de auto date tables múltiples.

## Recomendaciones de evolución
1. Estrella explícita: FactIncidencias + dimensiones (Estado, Producto, Faena, Fecha, Área).
2. Fecha única (`DimFecha`) y desactivar auto date/time.
3. Reemplazar mapeos DAX por dimensiones parametrizadas.
