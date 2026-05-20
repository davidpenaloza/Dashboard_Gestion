# 05 - Columnas calculadas y lógica de negocio

## Columnas calculadas relevantes
- `YYYYMM`, `Mes-anio`, `DuracionINC`, `FechaTomaDeControl`, `TiempoTotal`, `Area_Resolutora_Front`, `TituloINC`, `EstadoHU`, `SemanaDelMes_FechaInicio`, `DescripcionBreve`, `Workaround_`, `Solucion_`.【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L126-L465】

## Lógica incrustada (hechos observados)
- `FechaTomaDeControl` usa `SWITCH(TRUE())` con combinaciones faena/producto y fechas fijas.
- `TiempoTotal` usa `NOW()` (valor dinámico por evaluación).
- `Area_Resolutora_Front` usa `LOOKUPVALUE` contra `De_Para`.

## Reglas hardcodeadas detectadas
- Fechas de toma de control hardcodeadas (ej. 2024-02-15, 2026-01-12, etc.).【Reporte Gestión de Soporte.SemanticModel/definition/tables/DS_Incidencias.tmdl:L180-L188】

## Riesgos funcionales
- Cambios operacionales futuros exigen edición de DAX.
- Ambigüedad semántica en disponibilidad si cambia definición de negocio.

## Qué mover a parametrización
- Tabla de parametrización de vigencias por `Faena`+`Producto` para `FechaTomaDeControl`.
- Catálogo de normalización de estado (`EstadoHU`) y área resolutora.

## Validaciones con negocio requeridas
- Definición oficial de “disponible”, “inactividad” y “baja disponibilidad”.
- Vigencia y responsable real de reglas por faena/producto (actualmente no formalizado).
- Tratamiento de tickets sin `Fecha Fin`.
