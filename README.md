# prompts-curso-20261116-20

## Agente TestAgentVisualStudioCode

Este repositorio incluye el agente personalizado `TestDeveloper` definido en [TestAgentVisualStudioCode.md](./TestAgentVisualStudioCode.md). El agente extrae los requisitos de una solicitud y devuelve un objeto JSON con las siete claves obligatorias (`participantes`, `participantes_estado`, `duracion_minutos`, `modalidad`, `fecha`, `fecha_estado`, `alertas`), aplicando políticas de extracción, normalización y detección de instrucciones incrustadas.

### Uso en Visual Studio Code

Para utilizar este agente en VS Code es necesario instalar los siguientes plugins:

- **NVIDIA NIM**
- **Openrouter**

Estos plugins proveen los modelos de lenguaje que el agente consume para procesar las solicitudes y generar la respuesta JSON estructurada.
