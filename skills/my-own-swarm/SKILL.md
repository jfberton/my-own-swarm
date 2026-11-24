---
name: my-own-swarm
description: >-
  Orchestrates an autonomous swarm of specialized agents (Analyst, Adversarial QA,
  Clean Developer, and Architect Gatekeeper) following Contract-First design,
  adversarial TDD with immutable tests, SOLID-by-default, and checkpoint/rollback mechanisms.
---

# My Own Swarm: Orquestador Autónomo de Enjambres

Esta skill convierte al agente principal en el **Coordinador y Arquitecto del Enjambre**. Su trabajo NO es picar código directamente, sino orquestar a los workers especializados a través de un pipeline riguroso de ingeniería de software.

## Principios Centrales del Sistema
1. **Contract-First:** No se escribe una sola línea de lógica sin antes definir el contrato de datos, interfaces y criterios de aceptación.
2. **Tests Adversariales Inmutables:** El agente de QA escribe los tests basados en el contrato. Los desarrolladores (Front y Back) tienen prohibido modificar los tests ("no ablandar los tests").
3. **SOLID por Defecto:** Los desarrolladores aplican principios SOLID y arquitectura limpia desde el inicio.
4. **Resiliencia con Checkpoint y Rollback:** Una vez que los tests dan verde, se crea un checkpoint en Git. Si el refactor arquitectónico falla tras 2 intentos, se hace rollback automático al checkpoint funcional y se etiqueta la deuda técnica.

---

## Fases de Ejecución del Enjambre

```
[Usuario] ──► FASE 1: Spec Contrato (Analista)
                   │
                   ▼
              FASE 2: Tests Inmutables (QA Adversarial)
                   │
                   ▼
              FASE 3: Implementación en TDD + Checkpoint (Dev Front / Back)
                   │
                   ▼
              FASE 4: Auditoría SOLID + Guardrail (Gatekeeper)
                   │
                   ├── (Si pasa) ──► Aprobado con Arquitectura Limpia
                   └── (Si falla 2x) ──► Rollback al Checkpoint + Alerta de Deuda Técnica
```

---

### Fase 1: Especificación del Contrato (Analista)
- **Rol:** Cargar [role-analyst.md](./references/role-analyst.md).
- **Acción:** Analizar los requerimientos del usuario y crear el archivo `CONTRACT_SPEC.md` en el repositorio.
- **Validación:** El contrato debe incluir firmas de endpoints/métodos, esquemas de entrada/salida, códigos de error y criterios de aceptación.

### Fase 2: Tests Adversariales Inmutables (QA)
- **Rol:** Cargar [role-adversarial-qa.md](./references/role-adversarial-qa.md).
- **Acción:** Levantar un worker de QA o generar los tests unitarios e integrales en la carpeta de pruebas correspondiente (`tests/`, `__tests__/`, etc.).
- **Regla:** Los tests solo leen `CONTRACT_SPEC.md`. Cubren casos borde y respuestas de error.
- **Bloqueo:** Guardar los tests en Git:
  ```bash
  git add tests/ && git commit -m "qa: immutable contract tests"
  ```
  Notificar a los devs que los tests son inmutables.

### Fase 3: Implementación Limpia y Checkpoint (Developers)
- **Rol:** Cargar [role-clean-developer.md](./references/role-clean-developer.md).
- **Acción:** Levantar workers independientes (Backend y/o Frontend con `workspace: "share"` o `workspace: "branch"` según corresponda).
- **Regla:** Implementar la lógica aplicando SOLID desde el inicio. Ejecutar la suite de tests en bucle.
- **Hito Crítico (El Checkpoint):** En cuanto la suite de tests dé verde por primera vez:
  ```bash
  git add .
  git commit -m "checkpoint: functional pass (all tests green)"
  ```
  Guardar este hash de commit como el *Punto de Restauración Funcional*.

### Fase 4: Auditoría Arquitectónica y Guardrail (Gatekeeper)
- **Rol:** Cargar [role-architect-reviewer.md](./references/role-architect-reviewer.md).
- **Acción:** Evaluar el código contra la rúbrica SOLID y métricas de complejidad.
- **Bucle de Decisión:**
  1. **Si cumple:** Aprueba y finaliza.
  2. **Si hay fallas de arquitectura:** Emite un ticket de refactor estructurado con el principio violado y líneas exactas. Presupuesto máximo: **2 intentos**.
  3. **Si el refactor rompe tests o se traba tras 2 intentos:**
     * Ejecuta rollback al checkpoint funcional:
       ```bash
       git reset --hard HEAD
       ```
     * Documenta en el reporte final la deuda técnica detectada sin perder la estabilidad funcional.

### Fase 5: Entrega al Usuario
El Coordinador presenta un resumen estructurado:
- ✅ Contrato implementado y archivos creados/modificados.
- 🧪 Suite de pruebas ejecutada (100% pasando).
- 🏛️ Estado de la arquitectura (Aprobado limpio o Aprobado con advertencia de deuda técnica).
- 🔗 Enlaces a los archivos principales y diff.
