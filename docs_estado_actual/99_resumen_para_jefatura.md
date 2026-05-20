# 99 - Resumen para jefatura (ejecutivo)

## Estado actual del dashboard
El dashboard “Reporte Gestión de Soporte” está **operativo y estructuralmente completo en PBIP**, con un modelo semántico basado principalmente en una tabla de incidencias proveniente de Azure DevOps (WIQL). Presenta cobertura de KPIs de estado, tiempos y disponibilidad, y dispone de páginas operativas más páginas técnicas de apoyo (tooltips/diseño/manual).

## Principales riesgos
1. **Reglas de negocio hardcodeadas** en el modelo (fechas por faena/producto).
2. **Dependencia de un query WIQL fijo** (si cambia permisos/esquema, falla refresh).
3. **Complejidad visual** en páginas clave, que afecta usabilidad y potencialmente rendimiento.
4. **Gobierno insuficiente**: falta formalización documental de KPIs y reglas.

## Deuda técnica
- Modelo no estrella (plano/mixto).
- Funciones M técnicas extensas con posible duplicidad.
- Medidas DAX repetitivas y lógica de filtrado sobre texto.

## Decisiones requeridas de jefatura
1. Definir patrocinio de refactor (modelo + gobierno).
2. Asignar referente transitorio para KPI/SLA (hoy no existe owner formal).
3. Asignar referente técnico transitorio para conectividad/refresh (hoy no existe owner formal).
4. Aprobar plan de mejora por fases (quick wins y cambios estructurales).

## Plan recomendado
- **0–30 días (Quick wins):** parametrizar origen, catalogar KPI, limpieza visual inicial, control de acceso PII.
- **30–90 días:** modelo estrella base y tabla calendario única; mover reglas hardcodeadas a parametrización.
- **90+ días:** optimización avanzada, monitoreo continuo, estandarización de documentación y traspaso formal a soporte.

## Mensaje ejecutivo
El dashboard es útil hoy, pero su continuidad y escalabilidad dependen de atender deuda técnica y de gobierno en el corto plazo. Se recomienda intervención controlada con validación funcional y técnica.
