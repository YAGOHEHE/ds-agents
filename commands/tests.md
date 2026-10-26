---
description: Ejecuta los tests (todos o una ruta) y diagnostica fallos
argument-hint: "[ruta o args de pytest]"
---

Ejecuta la suite de tests del proyecto con su runner (`pytest`, o `uv run pytest` / `conda run -n <env> pytest` según el proyecto): `pytest $ARGUMENTS` (si no hay argumentos, `pytest`).

Si algo falla, identifica la causa raíz leyendo el código implicado y propón el arreglo mínimo. No lo apliques sin confirmación.
