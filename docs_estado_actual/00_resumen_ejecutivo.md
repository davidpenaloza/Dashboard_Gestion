# 00 - Resumen ejecutivo

## Objetivo del reporte
- **Hecho observado en archivos:** El reporte consolida elementos de trabajo (Azure DevOps) para seguimiento de gestión de soporte/incidencias, con KPIs de estado, duración y disponibilidad. Evidencia en tabla `DS_Incidencias` y medidas `Inc*`, `DuracionINC_Promedio`, `Disponible`, `Inactividad`.【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L10-L113】
- **Inferencia técnica:** Está orientado a monitoreo operativo y comunicación ejecutiva de incidencias.

## Alcance actual
- Cubre dataset único principal (`DS_Incidencias`) + catálogo `De_Para` + tabla técnica de refresco + páginas operativas/manual/tooltips.【Reporte Gestión de Soporte.SemanticModel/definition/model.tmdl:L15-L24】【Reporte Gestión de Soporte.Report/definition/pages/pages.json:L3-L21】

## Estado general del reporte
- **Hecho observado:** Proyecto PBIP completo y consistente (PBIP + PBIR + TMDL).【Reporte Gestión de Soporte.pbip:L1-L14】【Reporte Gestión de Soporte.Report/definition.pbir:L1-L9】
- **Hecho observado:** 16 páginas, incluyendo páginas de tooltip (`TT-*`) y manual/diseño.【Reporte Gestión de Soporte.Report/definition/pages/pages.json:L3-L21】

## Principales hallazgos
1. Modelo centrado en una tabla principal (diseño plano/mixto, no estrella plena).【Reporte Gestión de Soporte.SemanticModel/definition/model.tmdl:L18-L24】
2. Lógica de negocio incrustada en columnas DAX (ej. `FechaTomaDeControl` hardcodeada por faena/producto).【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L176-L189】
3. Dependencia externa fuerte de Azure DevOps con URL y Query ID fijos.【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L474-L493】
4. Densidad visual alta en páginas clave (ej. `Gestión de incidentes`: 90 visuales).

## Principales riesgos
- **Funcional:** reglas hardcodeadas pueden quedar obsoletas sin control de cambios.
- **Mantenibilidad:** funciones M extensas y duplicadas (`Functions` / `FunctionsNew`).【Reporte Gestión de Soporte.SemanticModel/definition/model.tmdl:L16-L17】
- **Performance/usabilidad:** sobrecarga visual en páginas operativas.
- **Gobierno:** naming mixto y ausencia de diccionario formal en PBIP (No evidenciado en PBIP).

## Nivel de madurez actual
- **Inferencia técnica:** **Madurez media-baja**.
  - Fortalezas: funcional, trazable en texto (TMDL/PBIR), KPIs básicos implementados.
  - Debilidades: deuda técnica de modelado, parametrización y gobierno documental.

## Recomendación ejecutiva
- Priorizar en 90 días: (1) estandarización de modelo lógico (estrella), (2) parametrización de origen, (3) simplificación visual, (4) documentación operativa mínima.

## Mantenibilidad hoy
- **Inferencia técnica:** Moderada a baja. Requiere conocimiento específico de Azure DevOps/WIQL y de lógica DAX embebida.

## Escalabilidad del modelo actual
- **Inferencia técnica:** Limitada. El crecimiento de volumen/uso aumentará costo de cálculos row-by-row y complejidad de soporte.
