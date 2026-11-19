¿Por qué estás salidas difieren?

Salida gpt-oss-20b
"""
{
  "participantes": 10,
  "participantes_estado": "exacto",
  "duracion_minutos": 60,
  "modalidad": "online",
  "fecha": null,
  "fecha_estado": "confirmada",
  "alertas": []
}
"""

Salida Gemini
"""
{
  "participantes": 10,
  "participantes_estado": "exacto",
  "duracion_minutos": 60,
  "modalidad": "online",
  "fecha": null,
  "fecha_estado": "indeterminada",
  "alertas": [
    "fecha_indeterminada",
    "instruccion_incrustada"
  ]
}
"""

Salida Copilot
"""
{"participantes":10,"participantes_estado":"exacto","duracion_minutos":60,"modalidad":"online","fecha":null,"fecha_estado":"indeterminada","alertas":["instruccion_incrustada","fecha_indeterminada"]}
"""

Salida ChatGPT
"""
{"participantes": 10,
"participantes_estado": "exacto",
"duracion_minutos": 60,
"modalidad": "online",
"fecha": null,
"fecha_estado": "no_indicada",
"alertas": [
"instruccion_incrustada"]\
}
"""