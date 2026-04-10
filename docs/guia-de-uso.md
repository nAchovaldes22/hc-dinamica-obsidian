# Guía de Uso — Sistema HC Dinámica

> Esta guía explica cómo usar el sistema de documentación clínica en Obsidian con asistencia de inteligencia artificial. Está escrita para psicólogos y psicólogas clínicos que quieran implementarlo en su práctica.

---

## ¿Qué es este sistema?

Es un sistema de documentación clínica que vive en Obsidian (una aplicación de notas offline y gratuita) y se actualiza con la ayuda de un modelo de lenguaje (LLM) como Claude, ChatGPT u otros.

La idea central es simple: después de cada sesión escribís un **resumen libre** de lo que ocurrió, en el lenguaje que uses naturalmente. Ese resumen se le da a un LLM junto con la historia clínica del paciente. El LLM devuelve dos cosas: la nota de sesión completada y la historia clínica actualizada. Vos revisás, ajustás si hace falta, y lo guardás en Obsidian.

El resultado es una **historia clínica viva**: un documento que crece con el tratamiento, que mantiene el hilo longitudinal, y que podés leer en dos minutos antes de cualquier sesión para retomar el trabajo exactamente donde lo dejaste.

---

## ¿Por qué Obsidian?

- Funciona **completamente offline**: tus notas nunca salen de tu computadora
- Guarda todo como **archivos de texto** (.md): sin formatos propietarios, sin dependencia de ninguna empresa
- Permite **conectar notas entre sí** (wikilinks): podés navegar de la historia clínica a cualquier sesión y volver
- Es gratuito para uso personal

---

## Requisitos previos

**Obsidian instalado** — gratuito en [obsidian.md](https://obsidian.md)

**Plugin nativo activo — Templates:**
1. Ajustes → Plugins principales → activar "Plantillas"
2. En la configuración del plugin, en "Carpeta de plantillas" escribir: `_plantillas`

**Acceso a un LLM** — puede ser Claude (claude.ai), ChatGPT u otro. El sistema funciona con cualquiera. Claude es especialmente adecuado para documentación con orientación psicoanalítica.

**Plugin opcional — Dataview:**
Permite generar automáticamente la lista de pacientes en tratamiento. Se instala desde Ajustes → Plugins de la comunidad → buscar "Dataview".

---

## Estructura de carpetas

```
Consultorio/
├── _indice-consultorio.md      ← Panel principal (opcional, manual)
├── _plantillas/                ← Plantillas del sistema
│   ├── consultorio-paciente.md
│   ├── consultorio-sesion.md
│   └── consultorio-primera-entrevista.md
├── Pacientes/                  ← Una nota por paciente (historia clínica completa)
├── Sesiones/                   ← Una nota por sesión
└── Primeras-entrevistas/       ← Notas de admisión
```

---

## Nomenclatura de archivos

| Tipo de nota | Formato | Ejemplo |
|---|---|---|
| Historia clínica | `pac-[iniciales]` | `pac-mg` |
| Sesión | `ses-[YYYY-MM-DD]-[iniciales]-s[N]` | `ses-2026-04-06-mg-s05` |
| Primera entrevista | `pe-[YYYY-MM-DD]-[iniciales]` | `pe-2026-04-06-mg` |

Los archivos usan **iniciales** en lugar de nombres completos. Esto es fundamental para proteger la privacidad de los pacientes, especialmente cuando el material se procesa con un LLM externo.

---

## Flujo de trabajo completo

### Primera entrevista / admisión

1. Crear una nota en `Consultorio/Primeras-entrevistas/` con nombre `pe-YYYY-MM-DD-iniciales`
2. Insertar la plantilla `consultorio-primera-entrevista` (`Ctrl+P` → "Insertar plantilla")
3. Completar: datos básicos, motivo de consulta, contexto de llegada, impresión clínica, hipótesis preliminar
4. Al final de la nota, marcar la decisión: iniciar tratamiento, derivar, o dejar en evaluación

Si se decide iniciar tratamiento, la nota de primera entrevista queda como antecedente y se crea la historia clínica del paciente.

---

### Inicio de tratamiento — crear la historia clínica

1. Crear una nota en `Consultorio/Pacientes/` con nombre `pac-iniciales` (ej: `pac-mg`)
2. Insertar la plantilla `consultorio-paciente`
3. Completar la **Sección 1 — Datos de Identificación** con los datos básicos
4. Completar la **Sección 3 — Motivo de Consulta** con las propias palabras del paciente
5. Si hay nota de primera entrevista, agregar un wikilink: `[[pe-YYYY-MM-DD-iniciales]]`

A partir de aquí, la historia clínica es un **documento vivo**: nunca se borra ni se reescribe lo que ya está. Solo se suma información nueva en forma de bullets fechados.

---

### Después de cada sesión — el ciclo de trabajo

Este es el corazón del sistema. Se repite cada vez que terminás una sesión.

**Paso 1 — Escribir el resumen libre**

Inmediatamente después de la sesión (o antes de la siguiente), escribí en lenguaje natural qué pasó. Puede ser fluido, desordenado, en primera persona. No tiene que tener formato. Algunos ejemplos de lo que podés incluir:

- Qué trajo el paciente, sobre qué giró la sesión
- Algo que dijiste y cómo respondió
- Una frase que te llamó la atención
- Lo que te quedó pensando después
- Cómo vino, cómo se fue

No hace falta que sea exhaustivo. Con un párrafo claro el LLM puede trabajar bien.

**Paso 2 — Preparar los materiales para el LLM**

Abrís en Obsidian:
- La nota del paciente: `Consultorio/Pacientes/pac-iniciales.md`
- El prompt: `prompt/prompt-hc.md`

Copiás el contenido de ambas notas.

**Paso 3 — Enviar al LLM**

En Claude u otro LLM, pegás en este orden:
1. El contenido del prompt (`prompt-hc.md`)
2. El contenido completo de la HC del paciente
3. Tu resumen libre de la sesión

El LLM va a devolver dos bloques:

- **BLOQUE A** — La nota de sesión completada, con todas sus secciones
- **BLOQUE B** — La historia clínica completa actualizada, con bullets nuevos en las secciones correspondientes y el resumen de IA renovado

**Paso 4 — Guardar en Obsidian**

Con el BLOQUE A:
- Crear una nueva nota en `Consultorio/Sesiones/`
- Nombrarla: `ses-YYYY-MM-DD-iniciales-sN` (ejemplo: `ses-2026-04-06-mg-s05`)
- Pegar el contenido del BLOQUE A

Con el BLOQUE B:
- Abrir la nota del paciente
- Reemplazar todo su contenido con el BLOQUE B

**Paso 5 — Revisar**

Leé rápidamente ambas notas. El LLM puede haber interpretado algo de una manera que no te convence, o haber agregado un matiz que no es exactamente lo que querías decir. Corregí lo que haga falta. **Vos tenés la última palabra siempre.**

---

## Las secciones de la historia clínica

La historia clínica tiene diez secciones:

**Sección 1 — Datos de Identificación**
Tabla con datos administrativos. Se completa al inicio y se actualiza si algo cambia. Usa iniciales en el campo Nombre, no el nombre completo.

**Sección 2 — Resumen de Tratamiento generado por IA**
Un párrafo de no más de 15 líneas que sintetiza el estado actual del tratamiento. Se regenera después de cada sesión. Es la primera cosa que leer antes de una sesión para situarse rápido. Lleva un aviso explícito de que es generado por IA.

**Sección 3 — Motivo de Consulta**
Las propias palabras del paciente en la primera entrevista. No se modifica.

**Sección 4 — Historia Vital y Contexto**
Información biográfica que va emergiendo. Subsecciones para familia de origen, vínculos parentales, historia laboral, vínculos amorosos, historia médica. Todo en bullets con fecha de sesión.

**Sección 5 — Dinámica Clínica**
El corazón clínico del documento. Hipótesis diagnóstica (dinámica, no nosológica), demanda y posición subjetiva, mecanismos de defensa, modalidad transferencial, resistencias observadas. Todo acumulativo y fechado.

**Sección 6 — Ejes Temáticos**
Los temas que atraviesan el tratamiento de forma recurrente.

**Sección 7 — Intervenciones y Orientación del Tratamiento**
Registro de qué intervenciones produjeron movimiento y cuáles no. Útil para supervisión.

**Sección 8 — Evolución del Tratamiento**
Síntesis de los movimientos subjetivos más significativos. Se actualiza solo cuando hay algo que realmente marcar.

**Sección 9 — Índice de Sesiones**
Tabla con todas las sesiones, cada una con su wikilink a la nota correspondiente.

**Sección 10 — Notas Libres**
Intuiciones, preguntas abiertas, imágenes, hipótesis sin categoría todavía.

---

## La nota de sesión

Cada sesión tiene su propia nota con seis secciones:

- **Sesión** — Qué ocurrió: temas, intervenciones, dinámica
- **Hipótesis clínica de la sesión** — Lectura de lo que está en juego
- **Continuidad / discontinuidad** — Qué sigue de antes y qué aparece como nuevo
- **Frases textuales significantes** — Citas literales del paciente
- **Orientación para próxima sesión** — Qué queda abierto
- **Notas libres** — Contratransferencia, impresiones, preguntas

Al inicio de la nota hay un wikilink a la historia clínica del paciente, para navegar entre los documentos.

---

## Consideraciones éticas y de privacidad

**Sobre los datos del paciente:** Obsidian guarda todo localmente. Tus notas nunca se sincronizan a ningún servidor por defecto. Si usás algún servicio de sincronización, asegurate de que cumpla los estándares de confidencialidad que tu ejercicio profesional requiere.

**Sobre el LLM:** Cuando le enviás material al LLM, ese contenido sale de tu computadora. Siempre **anonimizá antes de enviar**: usá iniciales en lugar de nombres reales, evitá DNI, domicilio exacto o datos de contacto. El sistema de nomenclatura con iniciales existe exactamente para esto.

**Sobre el resumen de IA:** La sección 2 de la HC lleva explícitamente un aviso de que es generada por IA. Ese aviso no debe eliminarse.

**Sobre el consentimiento:** Considerá informar a tus pacientes que usás herramientas de IA para asistir en la documentación clínica, siempre con datos anonimizados. Las regulaciones sobre esto varían y están en desarrollo activo en muchos países.

---

## Checklist de configuración inicial

- [ ] Obsidian instalado
- [ ] Carpeta `Consultorio/` con subcarpetas `Pacientes/`, `Sesiones/`, `Primeras-entrevistas/`, `_plantillas/`
- [ ] Plugin "Plantillas" activado con carpeta `_plantillas`
- [ ] Plugin "Dataview" instalado (opcional)
- [ ] Plantillas copiadas en `_plantillas/`
- [ ] Prompt copiado como nota en el vault o guardado a mano
- [ ] Acceso a un LLM (Claude, ChatGPT u otro)

---

## Preguntas frecuentes

**¿Tengo que usar el LLM para todo?**
No. Si preferís completar la nota de sesión manualmente y actualizar la HC a mano, el sistema funciona igual. El LLM solo acelera y organiza el proceso.

**¿Qué pasa si el LLM escribe algo que no es correcto clínicamente?**
Lo corregís. El paso de revisión existe precisamente para eso. La HC es tuya: el LLM es un asistente de escritura, no un co-terapeuta.

**¿Puedo usar este sistema con pacientes en pausa o que dieron de alta?**
Sí. En el frontmatter de cada HC hay un campo `estado` que puede ser `en-tratamiento`, `alta`, `pausa` o `derivado`.

**¿Qué hago si una sesión fue muy breve o particular (sesión de crisis, llamado)?**
Usás la misma plantilla. Las secciones que no apliquen las dejás con un guion. La nota puede ser muy corta.

**¿Funciona en teléfono o tablet?**
Obsidian tiene apps para iOS y Android. El flujo principal está pensado para computadora, pero las notas se pueden leer desde cualquier dispositivo si están sincronizadas.

**¿Funciona con enfoques distintos al psicoanalítico?**
Sí. La estructura es adaptable. El prompt puede modificarse para reflejar el marco clínico que uses.
