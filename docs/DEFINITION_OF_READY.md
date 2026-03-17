# Definition of Ready (DoR) — Stocky-App

**Proyecto:** Stocky-App  
**Fecha:** 2026-03-16 
**Autor:** Carlos Arenas  

## Propósito
La *Definition of Ready* define los criterios mínimos para que una Historia de Usuario esté **lista para entrar a un Sprint**: planificable, estimable y ejecutable sin bloqueos evitables.

Este documento también establece un estándar **auditable** en GitHub (Issues / Projects / Milestones) para demostrar un flujo profesional de gestión del trabajo.

---

## 1) Criterios para que una Historia esté “Ready”
Una historia se considera **Ready** cuando cumple **todo** lo siguiente:

### 1.1 Claridad del valor
• La historia está redactada en formato **Como / quiero / para**.  
• El objetivo y beneficio son claros (no ambiguos).  
• La historia pertenece a un área/épica definida.

### 1.2 Criterios de aceptación completos
• Tiene criterios de aceptación verificables.  
• Incluye al menos:
  • **Happy path** (flujo correcto).  
  • **Caso inválido** o de error (validación / no encontrado / credenciales, etc.).  
• No hay “etc.” ni criterios demasiado abiertos que permitan interpretaciones.

### 1.3 Alcance controlado
• El alcance está acotado para completarse dentro del Sprint.  
• Si es grande, está dividida en historias más pequeñas.  
• Lo que está **fuera de alcance** está explícito (si aplica).

### 1.4 Dependencias identificadas
• Dependencias técnicas o funcionales están listadas (si aplica).  
• Si existe un bloqueo, la historia **no** pasa a Ready.

### 1.5 Criterios técnicos mínimos
• Se conocen los cambios esperados (API, UI, BD) a nivel general.  
• Se definieron reglas básicas de datos y validaciones principales.  
• Hay claridad suficiente para estimar sin adivinar.

### 1.6 Estimación
• La historia tiene estimación (Story Points o esfuerzo relativo).  
• La estimación se basa en entendimiento real del trabajo.

### 1.7 Definición de pruebas (mínimo)
• Está definido cómo se validará:
  • Prueba manual (pasos mínimos).  
  • Pruebas automatizadas (si aplican).

---

## 2) Señales de que NO está Ready (red flags)
Una historia **no** está lista si:
• Le faltan criterios de aceptación o son ambiguos.  
• Depende de decisiones no tomadas (tecnología, reglas de negocio, UI clave).  
• Mezcla varios objetivos en una sola historia (scope excesivo).  
• No se puede estimar con confianza por falta de información.  
• El verdadero trabajo es investigación/arquitectura no definida.

---

## 3) Flujo oficial en GitHub Project (Milestones por Release)

El proyecto se gestiona con los siguientes estados:

**Backlog** → **Ready** → **In Progress** → **In Review** → **Done**

### Reglas de movimiento (política del proyecto)

**Backlog → Ready** (la historia queda lista para planificarse)  
Una historia solo puede moverse a **Ready** si cumple DoR y:
• Está asignada a un **Milestone de Release** (por ejemplo: `MVP v1`).  
• Está estimada y sin bloqueos activos.

**Ready → In Progress** (trabajo iniciado)  
• La historia fue seleccionada para trabajarse en el Sprint actual (gestionado en GitHub Project).  
• El Issue está asignado.

**In Progress → In Review** (listo para revisión)  
• Existe un Pull Request asociado al Issue (referenciado con “Closes #ID” o equivalente).  
• El PR describe el cambio y evidencia de pruebas realizadas (mínimo: manual).

**In Review → Done** (completado)  
• El PR fue mergeado a `main`.  
• La historia cumple la **Definition of Done (DoD)**.  
• La documentación se actualizó si correspondía.

### Regla de control de alcance
• Si durante el desarrollo aparece información que cambia el alcance o invalida la estimación, la historia se regresa a **Backlog** o **Ready**, se actualizan criterios y se re-estima antes de continuar.

### Regla de Milestones (Release Governance)
• Todo Issue comprometido para entrega debe pertenecer a un **Milestone de Release** (ej. `MVP v1`).  
• Un Milestone se considera completado cuando:
  • Todas las historias planeadas para ese release están en **Done**, o
  • Las historias no completadas se re-planifican explícitamente moviéndolas a otro Milestone, dejando evidencia del cambio.

---

## 4) Relación DoR vs DoD
- **DoR**: “Lista para empezarse”.  
- **DoD**: “Lista para entregarse”.

---

## 5) Estándar auditable en GitHub

Este proyecto se gestiona con:
- **GitHub Issues** como unidad de trabajo (Historias / Bugs / Tech Debt / Docs).
- **GitHub Projects** como tablero de estado.
- **GitHub Milestones** como agrupación por **Release** (ej. `MVP v1`).

La auditoría del proceso se logra con un estándar mínimo de **metadatos + contenido** en cada Issue.

### 5.1 Labels

**Tipo (obligatorio: exactamente 1)**
- `type:feature`
- `type:bug`
- `type:tech-debt`
- `type:docs`

**Área / Épica (obligatorio: exactamente 1)**
- `area:auth`
- `area:inventory`
- `area:customers`
- `area:pos`
- `area:reports`
- `area:ux`

**Prioridad (obligatorio: exactamente 1)**
- `priority:must`
- `priority:should`
- `priority:could`
- `priority:wont`

**Opcional (solo cuando aplique)**
- `blocked` (si hay un bloqueo real)
- `needs-refinement` (si requiere aclaración antes de poder estimarse/planificarse)

### 5.2 Milestones (Release Governance)
- Cada Issue comprometido para entrega debe pertenecer a un **Milestone de Release** (ej. `MVP v1`).  
- Issues sin Milestone se consideran “no comprometidos” (solo backlog).  
- Si el alcance cambia, el Issue se mueve de Milestone dejando evidencia del cambio.

### 5.3 Reglas DoR “auditables” (Ready = verificable desde GitHub)
Un Issue puede moverse a **Ready** en el GitHub Project únicamente si cumple:

**Metadatos**
- Tiene Milestone de Release asignado (ej. `MVP v1`).  
- Tiene labels:
  - 1 `type:*`
  - 1 `area:*`
  - 1 `priority:*`
- No tiene label `blocked`.

**Contenido**
- Historia en formato **Como / quiero / para**.  
- Criterios de aceptación verificables:
  - Happy path
  - Al menos 1 caso inválido/error
- Dependencias identificadas (si aplica)
