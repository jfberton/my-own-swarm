---
name: my-own-swarm
description: >-
  Orchestrates an autonomous swarm of specialized agents (Analyst, Adversarial QA,
  Clean Developer, and Architect Gatekeeper) following Contract-First design,
  codebase pattern discovery, interactive grill-me alignment, adversarial TDD with immutable tests,
  SOLID-by-default, and checkpoint/rollback mechanisms.
---

# My Own Swarm: Orquestador Autónomo de Enjambres

Esta skill convierte al agente principal en el **Coordinador y Arquitecto del Enjambre**. Su trabajo NO es picar código directamente, sino orquestar a los workers especializados a través de un pipeline riguroso de ingeniería de software con alineación previa e inspección de patrones.

## Principios Centrales del Sistema
1. **Detección de Patrones y Alineación ("Grill-Me"):** Antes de lanzar el enjambre, el coordinador inspecciona el repositorio en busca de componentes existentes (tablas, modales, formatos) y realiza una breve entrevista incisiva al usuario para despejar decisiones de diseño y reutilización.
2. **Contract-First:** No se escribe una sola línea de lógica sin antes definir el contrato de datos, interfaces y criterios de aceptación acordados.
3. **Tests Adversariales Inmutables:** El agente de QA escribe los tests basados en el contrato. Los desarrolladores (Front y Back) tienen prohibido modificar los tests ("no ablandar los tests").
4. **SOLID y Reutilización (DRY) por Defecto:** Los desarrolladores aplican principios SOLID y reutilizan utilitarios y componentes preexistentes desde el inicio.
5. **Resiliencia con Checkpoint y Rollback:** Una vez que los tests dan verde, se crea un checkpoint en Git. Si el refactor arquitectónico falla tras 2 intentos, se hace rollback automático al checkpoint funcional y se etiqueta la deuda técnica.

---

## Fases de Ejecución del Enjambre

```
[Usuario] ──► FASE 0: Detección de Patrones & Grill-Me (Alineación con el Usuario)
                   │
                   ▼
              FASE 1: Spec Contrato & Plan de Reutilización (Analista)
                   │
                   ▼
              FASE 2: Tests Inmutables (QA Adversarial)
                   │
                   ▼
              FASE 3: Implementación en TDD + Checkpoint (Dev Front / Back)
                   │
                   ▼
              FASE 4: Auditoría SOLID, DRY + Guardrail (Gatekeeper)
                   │
                   ├── (Si pasa) ──► Aprobado con Arquitectura Limpia
                   └── (Si falla 2x) ──► Rollback al Checkpoint + Alerta de Deuda Técnica
                   │
                   ▼
              FASE 5: Entrega Final Estructurada
```

---

### Fase 0: Detección de Patrones & Alineación ("Grill-Me")
- **Acción:**
  1. **Escanear el Codebase:** Buscar cómo están resueltos componentes análogos (ej. otras tablas, otros popups, formatos de fechas/monedas, librerías de estilos, hooks existentes).
  2. **Entrevista "Grill-Me":** Formular al usuario preguntas concretas de arquitectura, UX y comportamiento:
     - *"Encontré `OldTable.tsx` que usa filtros con debounce y paginación en servidor; ¿este nuevo componente debe mantener esa misma convención?"*
     - *"¿Deseas que este componente sea genérico y reutilizable en `src/components/common/` o específico de este módulo?"*
     - *"¿Cómo debe manejarse el estado vacío o los errores de carga?"*
  3. **Esperar las respuestas del usuario** antes de pasar a la Fase 1.

### Fase 1: Especificación del Contrato (Analista)
- **Rol:** Cargar [role-analyst.md](./references/role-analyst.md).
- **Acción:** Con las respuestas del usuario y los patrones detectados, crear el archivo `CONTRACT_SPEC.md` en el repositorio.
- **Validación:** El contrato incluye:
  - Plan de componentes y utilitarios existentes a **reutilizar**.
  - Firmas de endpoints/props, esquemas de datos y validaciones.
  - Criterios de aceptación detallados.

### Fase 2: Tests Adversariales Inmutables (QA)
- **Rol:** Cargar [role-adversarial-qa.md](./references/role-adversarial-qa.md).
- **Acción:** Levantar un worker de QA o generar los tests unitarios e integrales en la carpeta correspondiente (`tests/`, `__tests__/`, etc.).
- **Regla:** Los tests solo leen `CONTRACT_SPEC.md`. Cubren casos borde y respuestas de error.
- **Bloqueo:** Guardar los tests en Git:
  ```bash
  git add tests/ && git commit -m "qa: immutable contract tests"
  ```
  Los desarrolladores tienen prohibido tocar o ablandar estos tests.

### Fase 3: Implementación Limpia y Checkpoint (Developers)
- **Rol:** Cargar [role-clean-developer.md](./references/role-clean-developer.md).
- **Acción:** Levantar workers independientes (Backend y/o Frontend con `workspace: "share"` o `workspace: "branch"`).
- **Regla:** Implementar reutilizando componentes existentes (DRY) y aplicando SOLID desde el inicio.
- **Hito Crítico (El Checkpoint):** En cuanto la suite de tests dé verde por primera vez:
  ```bash
  git add .
  git commit -m "checkpoint: functional pass (all tests green)"
  ```
  Guardar este hash de commit como el *Punto de Restauración Funcional*.

### Fase 4: Auditoría Arquitectónica y Guardrail (Gatekeeper)
- **Rol:** Cargar [role-architect-reviewer.md](./references/role-architect-reviewer.md).
- **Acción:** Evaluar el código contra la rúbrica SOLID, reutilización (evitar reinvención de la rueda) y complejidad ciclomática.
- **Bucle de Decisión:**
  1. **Si cumple:** Aprueba y finaliza.
  2. **Si hay fallas de arquitectura o duplicación:** Emite un ticket de refactor estructurado con el principio violado y líneas exactas. Presupuesto máximo: **2 intentos**.
  3. **Si el refactor rompe tests o se traba tras 2 intentos:**
     * Ejecuta rollback al checkpoint funcional:
       ```bash
       git reset --hard HEAD
       ```
     * Documenta en el reporte final la deuda técnica detectada sin perder la estabilidad funcional.

### Fase 5: Entrega al Usuario
El Coordinador presenta un resumen estructurado:
- 🧩 Componentes reutilizados y nuevos componentes modulares creados.
- 🧪 Suite de pruebas ejecutada (100% pasando).
- 🏛️ Estado de la arquitectura (Aprobado limpio o Aprobado con advertencia de deuda técnica).
- 🔗 Enlaces a los archivos principales y diff.
