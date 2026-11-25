# 🚀 My Own Swarm - Plugin para Antigravity

Plugin de orquestación autónoma de enjambres de agentes para Google Antigravity, diseñado para elevar el desarrollo con IA a estándares de ingeniería de software rigurosa, desacoplada y escalable.

---

## 🎯 ¿Por qué está diagramado de esta manera?

El desarrollo de software asistido por agentes suele enfrentarse a **cuatro problemas críticos** que impiden delegar tareas complejas con verdadera confianza:

1. **Reinventar la Rueda e Inconsistencia (Falta de Contexto):**  
   Cuando un agente recibe un pedido (por ejemplo, *"haz una tabla con filtros"* o *"crea un popup"*), suele inventar componentes desde cero. El resultado: una tabla que no se parece en nada a las otras del proyecto, duplicación de utilitarios de formateo y estilos desconectados del design system.
2. **La "Erosión de Tests" (Sesgo de Confirmación):**  
   Cuando el mismo agente genera el código y los tests, o cuando tiene permisos para editar las pruebas ante un fallo, el modelo tiende a **modificar o "ablandar" los tests** para que den verde, en lugar de corregir los errores de su propia implementación.
3. **"Código que funciona" vs. "Código mantenible":**  
   Un modelo de lenguaje puede hacer pasar el 100% de los tests unitarios creando una función monolítica de 400 líneas con dependencias acopladas y sin separación de capas. Los tests solo validan *correctitud funcional*, no *salud arquitectónica*.
4. **El humano como cuello de botella o adivinador:**  
   Si el agente asume requerimientos a ciegas, genera código que no responde a lo que el usuario realmente quería. Y si el humano debe revisar cada línea de código manualmente, la fatiga cognitiva destruye la productividad.

---

## 💡 ¿Qué se logra trabajando de esta manera?

Al estructurar el enjambre con **exploración previa de patrones, alineación interactiva ("Grill-Me"), desarrollo Contract-First y bucle de feedback determinista**, se consiguen ventajas operativas claras:

* 🔍 **Inspección de Patrones y Reutilización (DRY):**  
  Antes de escribir una sola línea, el orquestador analiza el repositorio para detectar cómo están hechas las otras tablas, popups, hooks y filtros. Reutiliza componentes y utilitarios existentes en lugar de duplicarlos.
* 🎙️ **Alineación Previa ("Grill-Me"):**  
  El coordinador entrevista al usuario con preguntas breves e incisivas sobre decisiones de arquitectura, diseño y casos límite antes de disparar a los agentes. Cero suposiciones a ciegas.
* 🔒 **Tests Inmutables y Objetivos:**  
  El agente de QA redacta las pruebas basándose **únicamente en la especificación técnica acordada**, antes de que se escriba el código. Los desarrolladores tienen acceso de **solo lectura** a la carpeta de tests: si un test falla, están forzados a reparar su código fuente.
* 🏛️ **SOLID y Diseño Modular por Defecto:**  
  Los desarrolladores aplican principios de responsabilidad única, inversión de dependencias y componentes desacoplados desde la primera línea. Si se crea un nuevo control, se diseña para ser reutilizable en otras vistas de la aplicación.
* 🛡️ **Resiliencia con Checkpoint & Rollback:**  
  En el instante en que los tests pasan por primera vez, el sistema crea un *checkpoint* en Git. Si el refactor arquitectónico posterior se complica o rompe los tests tras 2 intentos, el sistema ejecuta un rollback automático al estado funcional estable y registra la deuda técnica pendiente, **garantizando que el espacio de trabajo nunca quede roto**.
* 📊 **Panel de Control en Vivo (Swarm Board Nativo):**  
  Reutiliza la pantalla nativa de Antigravity sin reinventar la rueda: abre un panel lateral con un clic (`open_board`) donde puedes ver en tiempo real el estado de cada agente (`working`, `waiting`), los mensajes y acuerdos que se dejan entre sí y el avance de la tarea en vivo.

---

## 🔄 El Pipeline de 6 Fases

```
[Usuario] ──► FASE 0: Detección de Patrones & Alineación ("Grill-Me")
                   │  Inspecciona el codebase (tablas, popups, hooks existentes).
                   │  Entrevista al usuario con preguntas clave antes de lanzar agentes.
                   ▼
              FASE 1: Especificación del Contrato (Analista)
                   │  Define 'CONTRACT_SPEC.md' con tipos, interfaces y plan de reutilización.
                   ▼
              FASE 2: Tests Inmutables (QA Adversarial)
                   │  Escribe tests rigurosos contra la spec. Se congelan en Git.
                   ▼
              FASE 3: Implementación Limpia + Checkpoint (Dev Front / Back)
                   │  Desarrollo guiado por tests (TDD) aplicando SOLID y DRY.
                   │  Al dar verde ──► git commit "checkpoint: functional pass"
                   ▼
              FASE 4: Auditoría Arquitectónica y Guardrails (Gatekeeper)
                   │  Audita SOLID, DRY (no duplicar código) y complejidad.
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

> *"Orquesta con **my-own-swarm** la creación del componente de tabla con paginación y filtros"*
>
> *"Usa **my-own-swarm** para implementar el endpoint de reportes y exportación en CSV"*

El Coordinador iniciará la **Fase 0**, analizará tu codebase para ver cómo están implementados otros componentes similares, te hará las preguntas necesarias de diseño/comportamiento (entrevista Grill-Me) y luego lanzará y orquestará de forma autónoma al resto del enjambre.
