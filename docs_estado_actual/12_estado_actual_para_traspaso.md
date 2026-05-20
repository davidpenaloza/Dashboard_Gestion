# 12 - Estado actual para traspaso

## Qué debe saber una persona nueva
- El proyecto está en formato PBIP (texto) con separación reporte/modelo.
- La tabla principal es `DS_Incidencias`; la fuente viene de Azure DevOps por WIQL.
- Existen páginas operativas y páginas técnicas (tooltips/diseño/manual).

## Partes críticas
1. Conector/fuente Azure DevOps + query ID fijo.
2. Lógica hardcodeada en `FechaTomaDeControl`.
3. Medidas de disponibilidad basadas en cálculos dinámicos.

## Partes frágiles
- Reglas basadas en `Tags` y nombres de `State`.
- Duplicidad potencial de funciones M.
- Alta densidad visual en páginas operativas.

## Qué no tocar sin validación
- Query ID, filtros de página clave, reglas de disponibilidad, mapeo de áreas.

## Dueño funcional requerido para
- Definiciones KPI, SLA, excepciones, semántica de incidencia.

## Dueño técnico requerido para
- Conectividad/credenciales ADO, modelado semántico, optimización DAX/M, performance visual.

## Checklist de traspaso a soporte
- [ ] Entregar acceso a repo y workspace.
- [ ] Entregar owner funcional y técnico nominados.
- [ ] Entregar catálogo de KPIs acordado.
- [ ] Entregar runbook de fallas de refresh.
- [ ] Entregar backlog priorizado y estado.
- [ ] Validar páginas críticas en sesión de handover.
