---
description: Revisa los cambios sin confirmar (código y rigor ML)
context: fork
agent: ds-toolkit:revisor
background: false
allowed-tools: Bash(git diff:*)
---

Cambios sin confirmar:

!`git diff --stat`

!`git diff`

Revisa estos cambios según tus criterios. Foco adicional: $ARGUMENTS
