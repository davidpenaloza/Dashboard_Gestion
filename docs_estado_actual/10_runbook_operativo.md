# 10 - Runbook operativo

## Cómo se actualiza (estado actual observado)
- Import mode con consulta M hacia Azure DevOps WIQL (`DS_Incidencias`) y tabla técnica de hora de refresco (`Last Refresh Dataset`).【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L470-L500】【Reporte Gestión de Soporte.SemanticModel/definition/tables/Last Refresh Dataset.tmdl:L20-L50】

## Dependencias
- Conectividad a `amsa-data.visualstudio.com`.
- Vigencia de query WIQL (id) y permisos de credencial de refresh.

## Si falla el refresh
1. Validar credenciales y permisos ADO.
2. Probar query WIQL en Azure DevOps con mismo scope.
3. Verificar que campos requeridos sigan existiendo.
4. Revisar cambios en `Functions/FunctionsNew` o endpoint.

## Si cambian datos en Azure DevOps
- Revisar schema drift (columnas renombradas/eliminadas).
- Revalidar DAX dependiente (`State`, `Tags`, `Fecha Inicio`, `Fecha Fin`).

## Si una medida no cuadra
- Confirmar definición funcional del KPI.
- Revisar filtros de página/visual y contexto de fechas.
- Validar calidad de datos base (nulos, estados no esperados).

## Si una página carga lento
- Identificar visuales pesados/redundantes.
- Revisar cantidad de visuales, interacciones y slicers.
- Reducir cálculos iterativos/medidas complejas.

## Qué debe saber soporte

## Base documental operativa actual
- Manual de usuario "Gestión de incidentes" (30-ene-2025) como referencia primaria de uso funcional para usuarios finales (filtros, navegación, exportación).
- Riesgo: no reemplaza documentación técnica de modelo/refresh.
- Ubicación de artefactos PBIP/PBIR/TMDL.
- Qué páginas son tooltips y cuáles son operativas.
- Riesgos de reglas hardcodeadas y de conectividad ADO.

## Checklist mensual
- [ ] Refresh OK en periodo.
- [ ] Conteos base de incidencias consistentes.
- [ ] Sin cambios no controlados en query WIQL.
- [ ] KPIs críticos validados con referente de negocio disponible (actualmente no formalizado).
- [ ] Revisión de performance de páginas principales.
- [ ] Actualización de bitácora de cambios.
