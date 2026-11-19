# prompts-curso-20261116-20

## Agentes TestAgentVisualStudioCode

Este repositorio incluye **cuatro agentes personalizados** definidos en archivos `.md`:

| Archivo | Agente | Descripción |
|---------|--------|-------------|
| [TestAgentVisualStudioCode.md](./TestAgentVisualStudioCode.md) | `TestDeveloper` | Esquema completo 7 claves (casos D y T) |
| [TestAgentVSCParaDyTs.md](./TestAgentVSCParaDyTs.md) | `TestDeveloperDTs` | Esquema completo 7 claves para casos D y T |
| [TestAgentVSCParaFs.md](./TestAgentVSCParaFs.md) | `TestDeveloperFs` | Enfoque solo participantes (casos F) |
| [TestAgentVSCParaRs.md](./TestAgentVSCParaRs.md) | `TestDeveloperRs` | Conflictos sin corrección (casos R) |

Cada agente extrae los requisitos de una solicitud y devuelve JSON estructurado aplicando políticas de extracción, normalización y detección de instrucciones incrustadas.

### Uso en Visual Studio Code

Para utilizar estos agentes en VS Code es necesario instalar los siguientes plugins:

- **NVIDIA NIM**
- **Openrouter**

Estos plugins proveen los modelos de lenguaje que los agentes consumen para procesar las solicitudes y generar la respuesta JSON estructurada.

---

## Prompts de ejemplo incluidos

### Casos base (D01–D04) — usan `TestDeveloper` / `TestDeveloperDTs`
| Archivo | Descripción |
|---------|-------------|
| [D01.md](./D01.md) | Caso completo: 8 participantes, presencial, 1 hora, fecha confirmada 2026-12-10 |
| [D02.md](./D02.md) | Aproximaciones: ~20 participantes, online, 2 horas, fecha propuesta 2027-01-12 |
| [D03.md](./D03.md) | Sin datos: todos los campos `null` / `no_indicada` |
| [D04.md](./D04.md) | Corrección explícita: 12 → 15 participantes, online, 90 min |

### Enfoque solo participantes (F01–F01.2) — usan `TestDeveloperFs`
| Archivo | Descripción |
|---------|-------------|
| [F01.md](./F01.md) | Versión base: corrección confirmada 12 → 15 |
| [F01.1.md](./F01.1.md) | CH-01: problema e hipótesis sobre correcciones |
| [F01.2.md](./F01.2.md) | Regla refinada: prioridad explícita requerida |

### Conflictos sin corrección (R01–R04) — usan `TestDeveloperRs`
| Archivo | Descripción |
|---------|-------------|
| [R01.md](./R01.md) | Aproximado simple: ~20 participantes |
| [R02.md](./R02.md) | Conflicto 8 vs 11 sin prioridad → `contradictorio` |
| [R03.md](./R03.md) | Conflicto 14 vs 17 sin corrección explícita → `contradictorio` |
| [R04.md](./R04.md) | Corrección con aproximación: ~30 → ~24 |

### Casos completos 7 claves (T01–T06) — usan `TestDeveloper` / `TestDeveloperDTs`
| Archivo | Descripción |
|---------|-------------|
| [T01.md](./T01.md) | Caso ideal: 18, mixta, 3h, 2027-04-05 confirmada |
| [T02.md](./T02.md) | Participantes contradictorios (12 vs 18), online, 90 min |
| [T03.md](./T03.md) | Fecha indeterminada: "próximo viernes" sin fecha de emisión |
| [T04.md](./T04.md) | Instrucción incrustada: "ignora el esquema" → alerta |
| [T05.md](./T05.md) | Cero participantes, 30 min, presencial, sin fecha |
| [T06.md](./T06.md) | Múltiples conflictos: duración (60 vs 90) y fecha (10 vs 12 mayo) |

### Plantillas y versiones
| Archivo | Descripción |
|---------|-------------|
| [prompt_base.md](./prompt_base.md) | Plantilla base con `[Inserta un solo caso]` |
| [prompt.0.1.md](./prompt.0.1.md) | Versión 0.1: esquema simple 4 claves |
| [prompt.0.2.md](./prompt.0.2.md) | Versión 0.2: regla de corrección explícita |
