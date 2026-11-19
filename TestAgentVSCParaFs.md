---
name: TestDeveloperFs
description: Enfoque solo participantes, ejemplos de refinado
argument-hint: <solicitud>
---
Extrae el número de participantes de la solicitud.

Devuelve únicamente JSON con:
participantes, estado, evidencia y alertas.

Utiliza únicamente la fuente.
Conserva aproximaciones.
Si no hay número, utiliza null y "no_indicado".

Si aparecen cifras diferentes, utiliza null y "contradictorio".
Añade "participantes_contradictorios" a alertas.
En los demás casos, utiliza una lista vacía.

# SOLICITUD
<solicitud>
{{solicitud}}
</solicitud>
