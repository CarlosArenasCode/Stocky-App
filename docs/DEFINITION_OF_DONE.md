# Definition of Done (DoD): Stocky-App
---
**Proyecto:** Stocky-App  
**Fecha:** 16 de Marzo de 2026  
**Autor:** Carlos Arenas  

---

| Versión | Fecha | Cambio |
|---------|-------|--------|
| 1.0 | 2026-03-16 | Versión inicial |
| 1.1 | 2026-03-16 | DoD Sprint Increment: detalle de Sprint Review/Retro y cierre de Milestone |
| 1.2 | 2026-03-16 | DoD Sprint Increment: añadir git tag por sprint para trazabilidad |
| 1.3 | 2026-03-16 | DoD PR: añadir regla de trazabilidad con ID de historia en título y commits |

---

> La *Definition of Done* define los criterios mínimos para considerar una **Historia de Usuario** como “Terminada”.
> Aplica para trabajo individual, pero con estándar profesional (estilo equipo real).

---

## 1) DoD — Historia de Usuario (User Story)

Una historia se considera **Done** cuando cumple **todo** lo siguiente:

### Funcionalidad
- La historia cumple el objetivo descrito (**Como / quiero / para**).
- Se cumplen **todos** los criterios de aceptación definidos en el backlog.
- Se manejan casos de error comunes (validaciones, recursos inexistentes, credenciales inválidas, etc.).
- No se introducen regresiones visibles en funcionalidades existentes.

### Calidad de código
- El código sigue un estilo consistente (nombres, estructura, arquitectura acordada).
- El linter y/o formatter del proyecto pasan sin errores (ej. ESLint, Prettier, o equivalente según el stack).
- No hay código comentado “temporal”, prints/debugs ni *TODOs* sin registrar en backlog.
- No se exponen secretos (keys, tokens, passwords) en el repositorio.

### Pruebas
- Existen pruebas automatizadas que cubren al menos: el flujo feliz principal y un caso de error o validación de la historia.
- Las pruebas pasan localmente sin errores ni warnings.
- La funcionalidad fue probada manualmente (flujo feliz + al menos 1 caso inválido).

### Revisión (Self-review)
- Se revisó el PR como si fueras un revisor externo: claridad, legibilidad y coherencia.
- El PR incluye descripción clara del cambio (qué y por qué).
- El cambio es lo más pequeño posible (sin mezclar features no relacionadas).

### Documentación
- La documentación se actualiza si el cambio lo requiere (README, docs, endpoints, decisiones).
- Si se agrega/modifica un endpoint, se actualiza la documentación de API correspondiente (ej. OpenAPI/Swagger), si aplica.

### Integración
- El cambio está integrado a `main` mediante Pull Request (no push directo).
- El repositorio compila/arranca correctamente (según el tipo de proyecto: API/UI/monorepo).
- Si existe pipeline de CI (GitHub Actions u otro), todos los checks pasan antes del merge.

---

## 2) DoD — Pull Request (PR)

Un PR se considera **listo para merge** cuando:

- Tiene título y commit(s) claros que incluyen el ID de la historia en el scope (ej. `feat(HU-004): agregar creación de productos`, `fix(HU-012): corregir descuento de stock al confirmar venta`).
- El ID de la historia en título y commits garantiza trazabilidad directa entre el código y el backlog.
- Incluye: descripción, alcance de cambios y checklist.
- No rompe el build/arranque del proyecto.
- Si aplica, incluye capturas o evidencia (ej. endpoint funcionando, UI, logs).

---

## 3) DoD — Incremento de Sprint

Al final del Sprint, el incremento es **Done** si:

- Todas las historias marcadas como Done cumplen el DoD de historia y PR.
- El incremento es potencialmente desplegable (aunque no se despliegue todavía).
- Se ha realizado una Sprint Review y una Retrospectiva, y sus resultados están documentados en:
  - Un Issue de GitHub con las etiquetas `sprint-review` y `sprint-retrospective` (o una Discusión en GitHub, si se prefiere).
  - Dicho issue está vinculado al Milestone correspondiente al sprint (ej. `Sprint-1`, `Sprint-2`...).
  - El contenido incluye: logros, feedback, métricas, acciones de mejora y, en el caso de la retrospectiva, los puntos clave del equipo.
- El Milestone del sprint se ha cerrado, indicando que todos los issues planificados fueron procesados (aceptados o movidos).
- Se ha creado un tag en el repositorio con el formato `sprint-N` (ej. `git tag sprint-1`) apuntando al commit del merge final del sprint.

---

## 4) Excepciones (si aplica)

Si por razones justificadas algo no puede cumplirse (ej. pruebas pendientes por bloqueo técnico), entonces:

- Se documenta explícitamente en el PR.
- Se crea un Issue de “tech debt” con prioridad y plan de resolución.
- La historia **no** se marca Done hasta cumplir DoD (preferido), o se marca como parcial y se re-planifica.

---
