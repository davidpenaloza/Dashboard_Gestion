# 01 - Inventario del proyecto PBIP

## Estructura PBIP observada
- `Reporte Gestión de Soporte.pbip` (orquestador del proyecto).【Reporte Gestión de Soporte.pbip:L1-L14】
- `Reporte Gestión de Soporte.Report/` (definición del reporte y visuales).
- `Reporte Gestión de Soporte.SemanticModel/` (modelo semántico TMDL).
- `README_ANALISIS.md` (contexto de análisis).

## Formatos usados
- **PBIP:** presente.【Reporte Gestión de Soporte.pbip:L1-L14】
- **PBIR:** presente en `definition.pbir`, con referencia por ruta al semantic model.【Reporte Gestión de Soporte.Report/definition.pbir:L4-L8】
- **TMDL:** presente en `model.tmdl`, `relationships.tmdl`, `tables/*.tmdl`.【Reporte Gestión de Soporte.SemanticModel/definition/model.tmdl:L1-L27】

## ¿Qué contiene `.Report`?
- `definition/report.json`, `definition/pages/*`, `definition/bookmarks/*`, `version.json`.
- Define páginas, visuales, filtros de página y navegación.

## ¿Qué contiene `.SemanticModel`?
- Definición de tablas, columnas, medidas, particiones M y relaciones.
- Archivos clave:
  - `definition/model.tmdl`.
  - `definition/relationships.tmdl`.
  - `definition/tables/DS_Incidencias.tmdl`.
  - `definition/tables/Functions.tmdl`, `FunctionsNew.tmdl`.

## Archivos clave revisados
- `Reporte Gestión de Soporte.pbip`.
- `Reporte Gestión de Soporte.Report/definition.pbir`.
- `Reporte Gestión de Soporte.Report/definition/pages/pages.json`.
- `Reporte Gestión de Soporte.SemanticModel/definition/model.tmdl`.
- `Reporte Gestión de Soporte.SemanticModel/definition/relationships.tmdl`.
- `Reporte Gestión de Soporte.SemanticModel/definition/tables/*.tmdl`.
- `QueryDashInc.csv` (muestra materializada de la query origen).

## Observaciones de completitud
- Proyecto **completo para análisis estático** del estado actual.
- No evidenciado en PBIP: políticas de refresh en servicio, RLS en workspace, ownership operativo en Fabric/Service.
