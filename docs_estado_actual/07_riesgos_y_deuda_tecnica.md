# 07 - Riesgos y deuda técnica

## Riesgos críticos
1. **Reglas hardcodeadas en DAX** (`FechaTomaDeControl`).
   - Evidencia: columna con múltiples fechas fijas por combinación faena/producto.【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L176-L189】
   - Impacto: quiebres funcionales silenciosos ante cambios operacionales.

2. **Dependencia externa con identificadores fijos** (URL + Query ID).
   - Evidencia: `url`, `project`, `team`, `id` fijos en M.【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L474-L493】
   - Impacto: refresh fallido ante cambios en Azure DevOps.

## Riesgos importantes
- Modelo plano/mixto con baja separación de dimensiones.
- Posible duplicidad técnica en `Functions` y `FunctionsNew`.
- Filtros funcionales embebidos en páginas y medidas (consistencia de KPI).

## Riesgos de performance
- `SUMX` sobre tabla completa en medidas de uso probable intensivo.【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L74-L111】
- Alta cantidad de visuales por página.

## Riesgos funcionales
- Mezcla de `Feature`/`User Story` con semántica de incidente.
- Campos descriptivos con nulos relevantes (evidencia CSV: descripción/solución/workaround).

## Riesgos de mantenimiento/gobierno
- Naming inconsistente (ES/EN, sufijos `_`, placeholders).
- No evidenciado en PBIP: data dictionary formal y governance owner.

## Riesgos de datos sensibles/acceso
- `Assigned To` contiene nombre/correo de personas (dato personal laboral). Evidencia de muestra CSV.【QueryDashInc.csv:L1-L4】
- Requiere revisar políticas de acceso y minimización de PII en visuales exportables.
