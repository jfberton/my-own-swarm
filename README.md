# 🚀 My Own Swarm - Plugin para Antigravity

Plugin de orquestación autónoma de enjambres de agentes para Google Antigravity, inspirado en las metodologías de desarrollo a escala de SpaceX (Lauren Tan).

Implementa un ciclo de vida riguroso:
* 📋 **Contract-First:** Especificación formal antes de escribir código.
* 🧪 **QA Adversarial & Tests Inmutables:** Los tests se generan contra la especificación y los desarrolladores tienen prohibido modificarlos ("no ablandar tests").
* 💻 **SOLID by Default:** Desarrollo limpio y desacoplado desde el primer token.
* 🛡️ **Checkpoint & Rollback Resiliente:** Si el refactor arquitectónico no pasa tras 2 intentos, el sistema hace rollback automático a la versión funcionalmente estable y documenta la deuda técnica.

---

## 📥 Instrucciones de Instalación en Antigravity Local

Para instalar este plugin en cualquier máquina con Antigravity, simplemente clona este repositorio en la carpeta global de plugins de Antigravity según tu sistema operativo.

### 🪟 En Windows (PowerShell)

Abre PowerShell y ejecuta:

```powershell
# 1. Asegurar que existe el directorio de plugins
New-Item -ItemType Directory -Force -Path "$HOME\.gemini\config\plugins"

# 2. Clonar el repositorio
git clone https://github.com/jfberton/my-own-swarm.git "$HOME\.gemini\config\plugins\my-own-swarm"
```

---

### 🍏 En macOS / 🐧 En Linux (Terminal / Bash / Zsh)

Abre la terminal y ejecuta:

```bash
# 1. Asegurar que existe el directorio de plugins
mkdir -p ~/.gemini/config/plugins

# 2. Clonar el repositorio
git clone https://github.com/jfberton/my-own-swarm.git ~/.gemini/config/plugins/my-own-swarm
```

---

## 🔄 Cómo actualizar a la última versión

Para recibir mejoras o ajustes que hayas subido al repositorio:

```bash
# Windows (PowerShell):
cd "$HOME\.gemini\config\plugins\my-own-swarm"
git pull

# macOS / Linux:
cd ~/.gemini/config/plugins/my-own-swarm
git pull
```

---

## 📤 Cómo publicar este repositorio por primera vez (GitHub / GitLab)

Desde la máquina donde se creó este plugin (`C:\Users\fedeb\.gemini\config\plugins\my-own-swarm`):

1. **Crea un repositorio vacío en GitHub o GitLab** (ej. llamado `my-own-swarm`).
2. **Ejecuta en PowerShell:**

```powershell
cd "$HOME\.gemini\config\plugins\my-own-swarm"

# Inicializar Git
git init
git add .
git commit -m "feat: initial commit of my-own-swarm plugin"

# Renombrar rama a main y vincular tu repo remoto
git branch -M main
git remote add origin https://github.com/jfberton/my-own-swarm.git

# Subir los cambios
git push -u origin main
```

*(Reemplaza `<TU_USUARIO>` por tu usuario real de GitHub).*

---

## 🤖 Cómo usarlo en el Chat de Antigravity

Una vez instalado, no necesitas configurar nada más. En cualquier conversación o proyecto en Antigravity, simplemente pide:

> *"Usa **my-own-swarm** para implementar el endpoint de autenticación con JWT"*
>
> *"Orquesta con **my-own-swarm** la creación del componente de tabla con paginación y filtros"*

El Coordinador tomará el control automáticamente y ejecutará el pipeline completo de 5 fases (Analista $\rightarrow$ QA $\rightarrow$ Dev $\rightarrow$ Reviewer $\rightarrow$ Entrega).
