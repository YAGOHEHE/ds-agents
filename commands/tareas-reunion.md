---
description: Extrae tareas de un acta de reunión (y opcionalmente las sube a un task-tracker)
argument-hint: "[acta o ruta]"
---

Analiza el acta: $ARGUMENTS

Genera la lista de tareas en el formato estándar del subagente `meeting-task-list` (puedes delegar con `@agent-ds-toolkit:meeting-task-list`). Después, si el proyecto tiene un MCP de task-tracker configurado (p. ej. ClickUp o Jira), pregúntame si quiero crearlas allí y no crees nada hasta mi confirmación explícita.
