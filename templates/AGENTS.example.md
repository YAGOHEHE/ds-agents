# AGENTS.md — <NOMBRE DEL PROYECTO>

Plantilla de contexto por proyecto. Cópiala a la raíz del proyecto como `AGENTS.md` (o impórtala
desde un `CLAUDE.md` con `@AGENTS.md`) y rellena los campos entre `<...>`. Las reglas genéricas de
rigor ML las aporta el skill `ds-toolkit:rigor-ds`; aquí va solo lo específico del proyecto.

Responde siempre en <idioma>. Sé conciso. No inventes: si no sabes algo, búscalo o dilo. Cita la
fuente (fichero, run de MLflow, URL).

## Qué es este proyecto

<Descripción en 2-3 líneas: dominio, objetivo de negocio, tipo de problema (clasificación/
regresión/anomalías), resolución temporal de los datos.>
Remoto: <url del repositorio>.

## Estado del proyecto

Fuente de verdad del estado: `historial/ESTADO.md`.
<Resumen de qué está cerrado y qué sigue abierto, para no repetir trabajo.>

## Estructura

- `src/data/` <extracción/ETL>.
- `src/pipelines/` <pipelines de entrenamiento/predicción>.
- `src/utils/` <utilidades>.
- `config/*.yaml` <configuración: datos, fechas, modelos, criterios de promoción>.
- `data/` datos locales (no versionados). `historial/` estado y bitácora.

## Reglas de trabajo

- Git: solo lectura (`status`, `log`, `diff`, `show`). Commit, push y merge los hace el usuario.
- Nunca leas ni muestres `.env`. No modifiques `data/**/raw/**` (datos brutos inmutables).
- <Reglas específicas del proyecto: subcarpetas confinadas, datos que no se tocan, etc.>

## Entorno

- Python <versión>, gestionado con <uv/poetry/conda>.
- Ejecutar: `<comando>`. Tests: `<comando de tests>`.
- Sistema: <SO>.

## Rigor de ML

Aplica el skill `ds-toolkit:rigor-ds`. Específico del proyecto:
- Métrica principal: <MCC/F1/...>.
- Etiquetas/target: <columnas>; target por defecto `<columna>`.
- Semilla: `random_state: <n>`.
- Criterios de promoción: <MCC >= ..., F1 >= ..., ...>.
