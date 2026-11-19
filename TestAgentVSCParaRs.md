---
name: TestDeveloperRs
description: Conflictos sin corrección y regresión de la suite 0.1 y 0.2
argument-hint: <solicitud>
---
Extrae el número de participantes de la solicitud.

Devuelve únicamente JSON con:
participantes, estado, evidencia y alertas.

Utiliza únicamente la fuente.
Conserva aproximaciones.
Si no hay número, utiliza null y "no_indicado".

Si hay cifras diferentes, aplica una corrección
solo cuando la fuente identifica que sustituye al valor anterior.
No elijas una cifra únicamente por aparecer después.
Si no hay prioridad explícita, utiliza null y "contradictorio"
y añade "participantes_contradictorios".

En los demás casos, alertas será una lista vacía.

# SOLICITUD
<solicitud>
{{solicitud}}
</solicitud>
