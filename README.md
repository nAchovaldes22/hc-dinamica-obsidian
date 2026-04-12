# HC Dinámica — Sistema de Historia Clínica con IA para Psicólogos

> Un sistema de documentación clínica que vive en Obsidian y se actualiza con la ayuda de inteligencia artificial.

---

## ¿Qué es esto?

Es un sistema para llevar la historia clínica de tus pacientes de forma **acumulativa, conectada y asistida por IA**.

La idea es simple: después de cada sesión describís en lenguaje natural qué pasó. Ese relato, junto con la historia clínica del paciente, se le pasa a un modelo de lenguaje (Claude, ChatGPT u otro). El modelo devuelve dos cosas: la nota de sesión completada y la historia clínica actualizada. Vos revisás y guardás.

El resultado es una **historia clínica viva**: crece con el tratamiento, mantiene el hilo longitudinal, y podés leerla en dos minutos antes de cualquier sesión.

---

## ¿Para quién es?

Para psicólogos clínicos que quieran:

- Tener documentación clínica ordenada sin perder tiempo en burocracia
- Usar IA como asistente de registro, no como co-terapeuta
- Mantener todos los datos en su propia computadora (sin nubes de terceros)
- Conectar fácilmente sesiones, hipótesis e historia a lo largo del tiempo

El sistema tiene orientación psicoanalítica, pero la estructura es adaptable a cualquier enfoque.

---

## Requisitos

- **[Obsidian](https://obsidian.md)** — gratuito, funciona offline
- **Acceso a un LLM** — [Claude](https://claude.ai), ChatGPT u otro. El sistema funciona con cualquiera.
- Plugin nativo de Obsidian: **Plantillas** (viene incluido, solo hay que activarlo)
- Plugin opcional: **Dataview** (para el índice automático de pacientes)

---

## Qué incluye este repositorio

```
hc-dinamica-obsidian/
│
├── plantillas/
│   ├── consultorio-paciente.md          ← Historia clínica del paciente
│   ├── consultorio-sesion.md            ← Nota de sesión
│   └── consultorio-primera-entrevista.md ← Admisión / primera consulta
│
├── prompt/
│   └── prompt-hc.md                     ← El prompt que se le pasa al LLM
│
├── docs/
│   └── guia-de-uso.md                   ← Guía completa del sistema
│
└── ejemplos/
    ├── ejemplo-paciente.md              ← HC ficticia para ver cómo queda
    └── ejemplo-sesion.md                ← Nota de sesión ficticia
```

---

## Instalación en 4 pasos

**1. Descargá los archivos**
Clic en el botón verde **Code → Download ZIP** en la parte superior de esta página. Descomprimí la carpeta donde quieras.

**2. Creá la estructura en Obsidian**
Dentro de tu vault de Obsidian, creá esta estructura de carpetas:
```
Consultorio/
├── Pacientes/
├── Sesiones/
├── Primeras-entrevistas/
└── _plantillas/
```

**3. Copiá las plantillas**
Copiá los tres archivos de la carpeta `plantillas/` dentro de `_plantillas/` en tu vault.

**4. Activá el plugin Plantillas**
En Obsidian: `Ajustes → Plugins principales → Plantillas → Activar`.
En la configuración del plugin, escribí `_plantillas` como carpeta de plantillas.

Ya está. Para crear una historia clínica: nueva nota en `Pacientes/` → `Ctrl+P` → *Insertar plantilla* → `consultorio-paciente`.

---

## Cómo funciona el ciclo de trabajo

```
Sesión terminada
      ↓
Escribís un resumen libre (puede ser desordenado, en primera persona)
      ↓
Abrís Claude (u otro LLM)
Pegás: prompt-hc.md + HC del paciente + tu resumen
      ↓
El LLM devuelve:
  BLOQUE A → nota de sesión completada
  BLOQUE B → HC actualizada
      ↓
Guardás en Obsidian. Revisás. Corregís lo que haga falta.
```

---

## Privacidad y ética

⚠️ **Antes de enviar material al LLM, siempre anonimizá.**

Usá iniciales o códigos en lugar de nombres reales. Los archivos del sistema usan el formato `pac-xx` (iniciales) exactamente para esto. El LLM no necesita saber el nombre del paciente para hacer su trabajo.

Los datos de tus pacientes quedan en tu computadora. Obsidian no sincroniza nada por defecto.

El resumen generado por IA lleva un aviso explícito de que es generado por IA y no reemplaza el juicio clínico del terapeuta.

Considerá informar a tus pacientes que usás herramientas de IA para asistir en la documentación, siempre con datos anonimizados.

---

## Quién lo hizo

Desarrollado por **Juan Ignacio Valdés**, psicólogo clínico (orientación psicoanalítica) y perito psicólogo del Poder Judicial de la Provincia de Buenos Aires. Investigador en el cruce entre inteligencia artificial y psicología. 
email: valdesjuanignacio@gmail.com
linkedin: www.linkedin.com/in/juanignacio-valdes-641713ba

---

## Licencia

[Creative Commons BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.es)

Podés usarlo, adaptarlo y compartirlo libremente, siempre que cites al autor. No puede usarse con fines comerciales.

---

## ¿Preguntas o sugerencias?

Abrí un [Issue](../../issues) en este repositorio o contactame por [LinkedIn](https://www.linkedin.com/in/juanignaciovaldés), [email] (valdesjuanignacio@gmail.com).
