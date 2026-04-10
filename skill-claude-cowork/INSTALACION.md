# Cómo instalar la skill en Claude Cowork

Esta carpeta contiene la skill lista para usar con **Claude en modo Cowork** (app de escritorio de Anthropic). Si usás Claude a través de la web o de otra forma, esta sección no aplica — usá el prompt de la carpeta `/prompt/` directamente.

---

## ¿Qué hace la skill?

Cuando está instalada, Claude detecta automáticamente cuándo querés trabajar con el consultorio y activa el flujo correspondiente. Podés decirle cosas como:

- *"Tuve sesión con MG"* → arranca la entrevista guiada y genera la nota + HC actualizada
- *"Nuevo paciente"* → te pide los datos y crea la historia clínica
- *"Antes de ver a FB"* → lee la HC y te da un resumen de dónde quedaste
- *"Primera entrevista con LR"* → genera la nota de admisión

---

## Pasos para instalar

**1. Descargá esta carpeta completa** (`skill-claude-cowork/`) a tu computadora.

**2. Abrí Claude Cowork** (la app de escritorio).

**3. Instalá la skill:**
- Andá a Configuración → Skills (o Plugins, según la versión)
- Hacé clic en "Instalar skill local" o "Agregar skill"
- Seleccioná la carpeta `skill-claude-cowork/` que descargaste

**4. Conectá tu vault de Obsidian:**
- En la misma sección, conectá la carpeta donde tenés tu vault de Obsidian como carpeta de trabajo
- La skill necesita acceso a esa carpeta para leer y guardar archivos

**5. Listo.** La próxima vez que le digas a Claude algo relacionado con el consultorio, la skill se activa sola.

---

## Estructura de la carpeta

```
skill-claude-cowork/
├── SKILL.md                              ← Instrucciones para Claude
└── references/
    ├── plantilla-paciente.md             ← Plantilla de historia clínica
    ├── plantilla-sesion.md               ← Plantilla de nota de sesión
    ├── plantilla-primera-entrevista.md   ← Plantilla de admisión
    └── prompt-hc.md                      ← Prompt maestro para actualizar HC
```

---

## Importante sobre la ruta del vault

La primera vez que uses la skill, Claude te va a preguntar cuál es la ruta de tu vault en Obsidian. Es algo como:

- Mac: `/Users/tunombre/Documents/MiVault/`
- Windows: `C:\Users\tunombre\Documents\MiVault\`

Guardá esa respuesta para no tener que repetirla cada vez.

---

## ¿Problemas o preguntas?

Abrí un Issue en el repositorio: [github.com/tuusuario/hc-dinamica-obsidian](https://github.com)
