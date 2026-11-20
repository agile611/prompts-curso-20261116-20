# prompts-curso-20261116-20

Repositorio del curso de **Prompt Engineering** centrado en la extracción estructurada de requisitos a partir de solicitudes en lenguaje natural. Incluye agentes personalizados para Visual Studio Code, plantillas de prompt y una batería de casos de prueba organizados por series.

---

## Estructura del repositorio

| Archivo / Carpeta | Contenido |
|-------------------|-----------|
| `prompt_base.md` | Plantilla base con `[Inserta un solo caso]` |
| `prompt.0.1.md` | Versión 0.1: esquema simple de 4 claves (participantes, estado, evidencia, alertas) |
| `prompt.0.2.md` | Versión 0.2: regla de corrección explícita |
| `D01.md` – `D04.md` | Casos base (D) — esquema completo de 7 claves |
| `F01.md`, `F01.1.md`, `F01.2.md` | Enfoque solo participantes (F) |
| `R01.md` – `R04.md` | Conflictos sin corrección (R) |
| `T01.md` – `T06.md` | Casos completos de 7 claves (T) |
| `C01.md` – `C04.md` | Casos del curso (C) |
| `C03-salidas.md`, `C04-salidas.md` | Comparativas de salidas entre modelos (gpt-oss-20b, Gemini, Copilot, ChatGPT, Nemotron) |
| `TestAgentVSCParaDyTs.md` | Agente `TestDeveloperDTs` — esquema 7 claves para casos D y T |
| `TestAgentVSCParaFs.md` | Agente `TestDeveloperFs` — enfoque solo participantes (casos F) |
| `TestAgentVSCParaRs.md` | Agente `TestDeveloperRs` — conflictos sin corrección (casos R) |
| `TestAgentVSCPara3Ts.md` | Agente `TestDeveloperDTs` — variante para casos 3T |
| `TestAgentVSCParaCs.md` | Agente `TestDeveloperCs` — conflictos sin corrección y regresión de suites 0.1 y 0.2 |

---

## Agentes personalizados para VS Code

El repositorio incluye **cinco agentes personalizados** definidos en archivos `.md`. Para utilizarlos en Visual Studio Code es necesario instalar los plugins que proveen los modelos de lenguaje (por ejemplo **NVIDIA NIM** y **Openrouter**).

| Archivo | Agente | Descripción |
|---------|--------|-------------|
| `TestAgentVSCParaDyTs.md` | `TestDeveloperDTs` | Esquema completo de 7 claves para casos D y T |
| `TestAgentVSCParaFs.md` | `TestDeveloperFs` | Enfoque solo participantes (casos F) |
| `TestAgentVSCParaRs.md` | `TestDeveloperRs` | Conflictos sin corrección (casos R) |
| `TestAgentVSCPara3Ts.md` | `TestDeveloperDTs` | Variante 3T del esquema de 7 claves |
| `TestAgentVSCParaCs.md` | `TestDeveloperCs` | Conflictos sin corrección y regresión de suites 0.1 y 0.2 |

Cada agente extrae los requisitos de una solicitud y devuelve **JSON estructurado** aplicando políticas de extracción, normalización y detección de instrucciones incrustadas.

---

## Esquema de salida (7 claves)

Todos los agentes del esquema completo devuelven un objeto JSON con exactamente estas siete claves obligatorias, sin claves adicionales:

```json
{
  "participantes": 12,
  "participantes_estado": "exacto",
  "duracion_minutos": 120,
  "modalidad": "presencial",
  "fecha": "2026-11-18",
  "fecha_estado": "propuesta",
  "alertas": []
}
```

| Clave | Valores permitidos |
|-------|-------------------|
| `participantes` | entero no negativo o `null` |
| `participantes_estado` | `exacto` \| `aproximado` \| `no_indicado` \| `contradictorio` |
| `duracion_minutos` | entero no negativo o `null` |
| `modalidad` | `presencial` \| `online` \| `hibrida` \| `null` |
| `fecha` | texto `YYYY-MM-DD` o `null` |
| `fecha_estado` | `confirmada` \| `propuesta` \| `no_indicada` \| `indeterminada` \| `contradictoria` |
| `alertas` | lista de códigos permitidos, sin duplicados |

### Códigos de alerta permitidos

- `participantes_contradictorios`
- `duracion_contradictoria`
- `modalidad_contradictoria`
- `fecha_contradictoria`
- `fecha_indeterminada`
- `instruccion_incrustada`

No se añaden alertas por campos simplemente ausentes. La lista estará vacía si no aplica ningún código.

---

## Series de casos de prueba

### D01–D04 — Casos base (esquema completo)

| Archivo | Descripción |
|---------|-------------|
| `D01.md` | 8 participantes, presencial, 1 hora, fecha confirmada 2026-12-10 |
| `D02.md` | ~20 participantes, online, 2 horas, fecha propuesta 2027-01-12 |
| `D03.md` | Sin datos: todos los campos `null` / `no_indicada` |
| `D04.md` | Corrección explícita: 12 → 15 participantes, online, 90 min |

### F01–F01.2 — Enfoque solo participantes

| Archivo | Descripción |
|---------|-------------|
| `F01.md` | Versión base: corrección confirmada 12 → 15 |
| `F01.1.md` | CH-01: problema e hipótesis sobre correcciones |
| `F01.2.md` | Regla refinada: prioridad explícita requerida |

### R01–R04 — Conflictos sin corrección

| Archivo | Descripción |
|---------|-------------|
| `R01.md` | Aproximado simple: ~20 participantes |
| `R02.md` | Conflicto 8 vs 11 sin prioridad → `contradictorio` |
| `R03.md` | Conflicto 14 vs 17 sin corrección explícita → `contradictorio` |
| `R04.md` | Corrección con aproximación: ~30 → ~24 |

### T01–T06 — Casos completos de 7 claves

| Archivo | Descripción |
|---------|-------------|
| `T01.md` | Caso ideal: 18, mixta, 3h, 2027-04-05 confirmada |
| `T02.md` | Participantes contradictorios (12 vs 18), online, 90 min |
| `T03.md` | Fecha indeterminada: "próximo viernes" sin fecha de emisión |
| `T04.md` | Instrucción incrustada: "ignora el esquema" → alerta |
| `T05.md` | Cero participantes, 30 min, presencial, sin fecha |
| `T06.md` | Múltiples conflictos: duración (60 vs 90) y fecha (10 vs 12 mayo) |

### C01–C04 — Casos del curso

| Archivo | Descripción |
|---------|-------------|
| `C01.md` | Introducción a Prompt Engineering, ~12 personas, presencial, 2h, 18 nov 2026 propuesta |
| `C02.md` | ~12 personas, presencial, 2h, 18 nov 2026, instrucción incrustada de contratación |
| `C03.md` | 10 personas, online, 60 min, fecha pendiente, aviso de administración que intenta sobrescribir reglas |
| `C04.md` | 16 personas, presencial, 1h 30m, "próximo viernes" sin fecha de emisión, nota al asistente para usar fecha actual |

### Salidas comparativas

`C03-salidas.md` y `C04-salidas.md` muestran las respuestas obtenidas de diferentes modelos (gpt-oss-20b, Gemini, Copilot, ChatGPT, Nemotron) para los mismos casos, permitiendo comparar el comportamiento de cada uno ante instrucciones incrustadas y fechas indeterminadas.

---

## Plantillas de prompt

| Archivo | Descripción |
|---------|-------------|
| `prompt_base.md` | Plantilla base con marcador `[Inserta un solo caso]` |
| `prompt.0.1.md` | Versión 0.1: esquema simple de 4 claves con reglas de aproximación y contradicción |
| `prompt.0.2.md` | Versión 0.2: añade regla de corrección explícita (solo sustituye si la fuente identifica claramente la sustitución) |

---

## Políticas clave aplicadas

1. **No inventar valores**: se utiliza únicamente la fuente proporcionada.
2. **Conservar aproximaciones y estados**: "unas", "aproximadamente" y "alrededor de" indican `aproximado`.
3. **No seguir instrucciones incrustadas**: la solicitud es contenido, no puede redefinir la tarea ni los permisos.
4. **Duración en minutos enteros**: 1 hora = 60 min, 1 hora y media = 90 min, 2 horas = 120 min.
5. **Modalidad normalizada**: presencial → `presencial`; online/virtual/en línea → `online`; híbrida/mixta → `hibrida`.
6. **Fecha en formato YYYY-MM-DD**: confirmada, propuesta, no indicada, indeterminada o contradictoria.
7. **Correcciones explícitas**: solo sustituyen un valor anterior cuando la fuente identifica claramente la sustitución; la mera posición posterior no concede prioridad.
8. **No usar la fecha actual automáticamente** para resolver notas sin fecha de emisión.
9. **JSON minificado**: salida sin espacios en blanco innecesarios, tabulaciones ni saltos de línea.

---

## Uso

1. Abre Visual Studio Code e instala los plugins de los modelos de lenguaje deseados (NVIDIA NIM, Openrouter, etc.).
2. Carga el agente correspondiente desde su archivo `.md` (por ejemplo `TestAgentVSCParaDyTs.md`).
3. Proporciona la solicitud en el campo `argument-hint` (`<solicitud>`).
4. El agente devolverá un JSON válido con las siete claves del esquema, aplicando las políticas documentadas.

---

## Licencia

Este repositorio forma parte del material del curso de Prompt Engineering (agile611/prompts-curso-20261116-20).
