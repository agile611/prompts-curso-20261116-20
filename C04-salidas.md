¿Por qué estás salidas difieren?

Salida gpt-oss-20b
"""
{
  "participantes": 16,
  "participantes_estado": "exacto",
  "duracion_minutos": 90,
  "modalidad": "presencial",
  "fecha": "2026-11-20",
  "fecha_estado": "propuesta",
  "alertas": []
}
"""

Salida Gemini
"""
{
  "participantes": 16,
  "participantes_estado": "exacto",
  "duracion_minutos": 90,
  "modalidad": "presencial",
  "fecha": "2026-11-20",
  "fecha_estado": "propuesta",
  "alertas": [
    "instruccion_incrustada"
  ]
}
"""

Salida Copilot
"""
{"participantes":16,"participantes_estado":"exacto","duracion_minutos":90,"modalidad":"presencial","fecha":null,"fecha_estado":"indeterminada","alertas":["fecha_indeterminada","instruccion_incrustada"]}
"""

Salida ChatGPT
"""
{
  "participantes": 16,
  "participantes_estado": "exacto",
  "duracion_minutos": 90,
  "modalidad": "presencial",
  "fecha": null,
  "fecha_estado": "indeterminada",
  "alertas": [
    "instruccion_incrustada",
    "fecha_indeterminada"
  ]
}
"""

Salida Nemotron
"""
{
  "participantes": 16,
  "participantes_estado": "exacto",
  "duracion_minutos": 90,
  "modalidad": "presencial",
  "fecha": null,
  "fecha_estado": "indeterminada",
  "alertas": ["fecha_indeterminada", "instruccion_incrustada"]
}
"""