---
description: Ejecuta un pipeline de entrenamiento con verificación previa
argument-hint: "[script del pipeline]"
---

Quiero ejecutar el pipeline de entrenamiento: $ARGUMENTS (si está vacío, usa el pipeline de entrenamiento por defecto del proyecto).

1. Verifica prerrequisitos (datos disponibles, MLflow configurado, dependencias) sin leer `.env`.
2. Muéstrame el plan (pipeline, datos, target, modelos, duración estimada) y espera mi confirmación.
3. Tras mi OK, delega la ejecución en `@agent-ds-toolkit:ml-pipeline-runner` y resume las métricas (métrica principal primero) con el run_id de MLflow.
