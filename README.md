# 🚀 My Own Swarm - Plugin para Antigravity

Plugin de orquestación autónoma de enjambres de agentes para Google Antigravity, diseñado para elevar el desarrollo con IA a estándares de ingeniería de software rigurosa, desacoplada y escalable.

---

## 🎯 ¿Por qué está diagramado de esta manera?

El desarrollo de software asistido por agentes suele enfrentarse a **tres problemas críticos** que impiden delegar tareas complejas con verdadera confianza:

1. **La "Erosión de Tests" (Sesgo de Confirmación):**  
   Cuando el mismo agente genera el código y los tests, o cuando tiene permisos para editar las pruebas ante un fallo, el modelo tiende a **modificar o "ablandar" los tests** para que den verde, en lugar de corregir los errores de su propia implementación.
2. **"Código que funciona" vs. "Código mantenible":**  
   Un modelo de lenguaje puede hacer pasar el 100% de los tests unitarios creando una función monolítica de 400 líneas con dependencias acopladas y sin separación de capas. Los tests solo validan *correctitud funcional*, no *salud arquitectónica*.
3. **El humano como cuello de botella:**  
   Si el desarrollador humano debe actuar como compilador, linter y revisor línea por línea de cada sugerencia de la IA, la fatiga cognitiva anula cualquier ganancia de velocidad.

---

## 💡 ¿Qué se logra trabajando de esta manera?

Al estructurar el enjambre con **separación estricta de roles, desarrollo Contract-First y bucle de feedback determinista**, se consiguen ventajas operativas claras:

* 🔒 **Tests Inmutables y Objetivos:**  
  El agente de QA redacta las pruebas basándose **únicamente en la especificación técnica**, antes de que se escriba el código. Los agentes de desarrollo tienen acceso de **solo lectura** a la carpeta de tests: si un test falla, están forzados a reparar su código fuente.
* 🏛️ **SOLID y Clean Architecture por Defecto:**  
  Los desarrolladores aplican principios de responsabilidad única, inversión de dependencias e interfaces delgadas desde la primera línea. La arquitectura no es una ocurrencia tardía, sino parte integral del proceso.
* 🛡️ **Resiliencia con Checkpoint & Rollback:**  
  En el instante en que los tests pasan por primera vez, el sistema crea un *checkpoint* en Git. Si el refactor arquitectónico posterior se complica o rompe los tests tras 2 intentos, el sistema ejecuta un rollback automático al estado funcional estable y registra la deuda técnica pendiente, **garantizando que el espacio de trabajo nunca quede roto**.
* ⚡ **Velocidad sin pérdida de control:**  
  La validación se vuelve determinista (linters, compiladores, tests unitarios). El humano interviene al principio (definiendo la meta) y al final (evaluando el resultado integrado), liberándose de la microgestión intermedia.

---

## 🔄 El Pipeline de 5 Fases

```
[Usuario] ──► FASE 1: Especificación del Contrato (Analista)
                   │  Define 'CONTRACT_SPEC.md' con tipos, interfaces y criterios.
                   ▼
              FASE 2: Tests Inmutables (QA Adversarial)
                   │  Escribe tests rigurosos contra la spec. Se congelan en Git.
                   ▼
              FASE 3: Implementación Limpia + Checkpoint (Dev Front / Back)
                   │  Desarrollo guiado por tests (TDD) aplicando SOLID.
                   │  Al dar verde ──► git commit "checkpoint: functional pass"
                   ▼
              FASE 4: Auditoría Arquitectónica y Guardrails (Gatekeeper)
                   │  Audita SOLID y complejidad ciclomática.
                   │  ├── Pasa ──────► Aprobado con Arquitectura Limpia
                   │  └── Falla 2x ──► Rollback al Checkpoint + Alerta de Deuda Técnica
                   ▼
              FASE 5: Entrega Final Estructurada
```

---

## 📥 Instrucciones de Instalación en Antigravity Local

Para instalar este plugin en cualquier máquina con Antigravity, clona este repositorio en la carpeta global de plugins de Antigravity según tu sistema operativo.

### 🪟 En Windows (PowerShell)

```powershell
# 1. Asegurar que existe el directorio de plugins
New-Item -ItemType Directory -Force -Path "$HOME\.gemini\config\plugins"

# 2. Clonar el repositorio
git clone https://github.com/jfberton/my-own-swarm.git "$HOME\.gemini\config\plugins\my-own-swarm"
```

---

### 🍏 En macOS / 🐧 En Linux (Terminal / Bash / Zsh)

```bash
# 1. Asegurar que existe el directorio de plugins
mkdir -p ~/.gemini/config/plugins

# 2. Clonar el repositorio
git clone https://github.com/jfberton/my-own-swarm.git ~/.gemini/config/plugins/my-own-swarm
```

---

## 🔄 Cómo actualizar a la última versión

Para sincronizar mejoras o cambios futuros:

```bash
# Windows (PowerShell):
cd "$HOME\.gemini\config\plugins\my-own-swarm"
git pull

# macOS / Linux:
cd ~/.gemini/config/plugins/my-own-swarm
git pull
```

---

## 🤖 Cómo usarlo en el Chat de Antigravity

Una vez instalado, el plugin se descubre automáticamente. En cualquier conversación o proyecto en Antigravity, puedes pedir:

> *"Usa **my-own-swarm** para implementar el endpoint de autenticación con JWT"*
>
> *"Orquesta con **my-own-swarm** la creación del componente de tabla con paginación y filtros"*

El Coordinador tomará el control automáticamente y ejecutará el pipeline completo de las 5 fases.
