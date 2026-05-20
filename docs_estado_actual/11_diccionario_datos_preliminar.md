# 11 - Diccionario de datos preliminar

> Si un campo no tiene tipado explícito en TMDL o significado oficial, se marca como inferencia y/o “requiere validación funcional”.

| Tabla | Columna | Tipo dato | Descripción inferida | Uso probable | Riesgo/comentario | Requiere validación funcional |
|---|---|---|---|---|---|---|
| DS_Incidencias | ID | int64 | Identificador work item | Conteos DISTINCT | Clave principal analítica | No |
| DS_Incidencias | Work Item Type | string | Tipo ADO (Feature/User Story) | Segmentación | Mezcla semántica incidencia | Sí |
| DS_Incidencias | State | string | Estado del item | KPIs estado | Catálogo no normalizado | Sí |
| DS_Incidencias | Tags | string | Etiquetas del ítem | Filtro incidencia | `CONTAINSSTRING` costoso | Sí |
| DS_Incidencias | Fecha Inicio | datetime | Inicio evento | Tendencias/duración | Nulos parciales | Sí |
| DS_Incidencias | Fecha Fin | datetime | Fin evento | Duración/cierre | Nulos en abiertos | Sí |
| DS_Incidencias | DuracionINC | calc num | Horas entre inicio-fin | KPI tiempos | Depende de fechas | Sí |
| DS_Incidencias | FechaTomaDeControl | calc date | Fecha de referencia por faena/producto | Disponibilidad | Hardcode crítico | Sí |
| DS_Incidencias | TiempoTotal | calc num | Horas desde toma control a NOW() | Disponibilidad | Valor dinámico | Sí |
| DS_Incidencias | Area Resolutora | string | Área resolutora origen | Segmentación | Calidad origen | Sí |
| DS_Incidencias | Area_Resolutora_Front | calc string | Mapeo abreviado área | Visuales | Sin relación física | Sí |
| DS_Incidencias | Producto | string | Producto asociado | Segmentación | Nulos | Sí |
| DS_Incidencias | Fuente | string | Fuente sistema | Segmentación | Nulos altos | Sí |
| DS_Incidencias | Assigned To | string | Responsable (nombre/correo) | Operación | Dato personal laboral | Sí |
| De_Para | Nombre completo | string | Texto área completa | Lookup/mapeo | Catálogo manual | Sí |
| De_Para | Nombre | string | Abreviatura área | Front visual | Riesgo desactualización | Sí |
| Last Refresh Dataset | Last Refresh Dataset | datetime | Timestamp de última actualización | Tarjeta “última actualización” | Depende de refresh | No |
