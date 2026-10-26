---
description: Resume el estado del proyecto y lo pendiente
argument-hint: "[foco opcional]"
allowed-tools: Bash(git log:*)
---

Estado reciente del repo (git log):

!`git log -n 15 --oneline`

Lee también el fichero de estado del proyecto si existe (`historial/ESTADO.md`). Resume en menos de
15 líneas: qué está cerrado, qué sigue abierto y cuál es el siguiente paso razonable.

Si no puedes leer el fichero de estado, dilo y resume solo con el git log de arriba y `AGENTS.md`.

Foco adicional: $ARGUMENTS
