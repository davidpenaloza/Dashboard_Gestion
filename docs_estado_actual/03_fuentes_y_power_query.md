# 03 - Fuentes y Power Query / M

## Fuentes identificadas
- **Origen principal:** Azure DevOps (VSTS) vía endpoint `https://amsa-data.visualstudio.com`.【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L474-L477】
- **Mecanismo:** función `WiqlRunFlatWorkItemQueryById` con `id` fijo `e2bdb8c8-624b-4561-ac26-14233cd23865`.【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L478-L493】

## Transformaciones M relevantes
- Obtención de resultados WIQL flat list.
- Rename `Disponible`→`Disponible_SI_NO`.【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L493-L495】
- `Last Refresh Dataset`: cálculo de hora local Chile con ajuste horario estacional.【Reporte Gestión de Soporte.SemanticModel/definition/tables/Last Refresh Dataset.tmdl:L23-L45】

## Funciones M identificadas
- Librería extensa en `Functions` y `FunctionsNew`: batching, manejo de errores HTTP, lectura de fields, query WIQL, armado de link de work item.

## Dependencias externas
- API Azure DevOps, disponibilidad de proyecto/equipo/query, credenciales y permisos del principal de refresh.

## Riesgos
- URL y Query ID hardcodeados.
- Posible duplicidad técnica (`Functions` y `FunctionsNew`) con deuda de mantenimiento.
- Cambios en schema WIQL/fields podrían romper refresh.

## Recomendaciones
- Parametrizar `url`, `project`, `team`, `id`.
- Consolidar librerías M duplicadas.
- Definir contrato de campos requeridos (schema governance).
- Runbook de recuperación ante cambio de query/permiso.
