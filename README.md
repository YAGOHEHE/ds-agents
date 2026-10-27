# ds-toolkit

Plugin de Claude Code con agentes, comandos y un skill de rigor para proyectos de **ciencia de
datos y machine learning**. Generalizado a partir de un setup real para que sirva en cualquier
proyecto DS.

Este repositorio es a la vez **plugin** (`.claude-plugin/plugin.json`) y **marketplace**
(`.claude-plugin/marketplace.json`, con el plugin en `source: "."`).

## Qué incluye

**Agentes** (`agents/`), namespaced como `ds-toolkit:<nombre>`:

| Agente | Modelo | Rol |
|---|---|---|
| `orchestrator` | opus | Coordina tareas y delega en subagentes |
| `orche_training` | opus | Orquesta el entrenamiento y lo registra en MLflow |
| `ml-researcher` | opus | Investigación (papers, metodologías); usa ARS si está instalado |
| `math-researcher` | opus | Valida matemáticamente los enfoques del ml-researcher (Mathematics for Machine Learning) |
| `stat-researcher` | opus | Valida los enfoques del ml-researcher con enfoque bayesiano (Statistical Rethinking) |
| `task-list-creator` | opus | Listas de tareas de proyecto |
| `meeting-task-list` | opus | Tareas desde actas de reunión |
| `revisor` | opus | Revisión de código y rigor ML (solo lectura) |
| `aed-researcher` | opus | Análisis exploratorio de datos (EDA) antes de modelar |
| `ml-engineer` | sonnet | Implementa y entrena modelos |
| `data-engineer` | sonnet | ETL y calidad de datos |
| `ml-pipeline-runner` | sonnet | Ejecuta el pipeline end-to-end |
| `presentation-creator` | sonnet | Decks a partir de material fuente (skill pptx) |

**Comandos** (`commands/`): `/ds-toolkit:estado`, `/ds-toolkit:revisar`, `/ds-toolkit:tests`,
`/ds-toolkit:pipeline`, `/ds-toolkit:tareas-reunion`.

**Skill** (`skills/rigor-ds`): reglas genéricas de rigor ML (métricas, split temporal, fugas,
MLflow, detección vs predicción).

**Plantillas** (`templates/`): `settings.example.json` (permisos) y `AGENTS.example.md` (contexto
por proyecto). No viajan como componentes activos del plugin (ver más abajo); se copian a cada
proyecto.

## Instalación

Desarrollo local (sin marketplace):

```powershell
claude --plugin-dir C:\Users\<usuario>\Documents\02_Proyectos\ds-toolkit
```

Vía marketplace:

```powershell
claude plugin validate C:\Users\<usuario>\Documents\02_Proyectos\ds-toolkit
claude plugin marketplace add C:\Users\<usuario>\Documents\02_Proyectos\ds-toolkit
claude plugin install ds-toolkit@claude-ds
```

Para el equipo: sube este repo a un git host y cada persona hace
`claude plugin marketplace add <owner>/<repo>` y luego `claude plugin install ds-toolkit@claude-ds`.

## Puesta a punto por proyecto

Dos cosas **no** viajan dentro de un plugin y se configuran en cada proyecto:

1. **Permisos** — el `settings.json` de un plugin descarta todo salvo `agent`/`subagentStatusLine`.
   Copia `templates/settings.example.json` a `.claude/settings.json` del proyecto y ajústalo.
2. **Instrucciones del proyecto** — un `CLAUDE.md` en la raíz del plugin no se carga. Copia
   `templates/AGENTS.example.md` a `AGENTS.md` del proyecto y rellénalo. El rigor genérico lo
   aporta el skill `ds-toolkit:rigor-ds`.

## Uso

- Agente principal: `claude --agent ds-toolkit:orchestrator`.
- Subagente: `@agent-ds-toolkit:revisor revisa src/utils/mi_modulo.py`.
- Comandos: `/ds-toolkit:estado`, `/ds-toolkit:revisar`, etc.

## ARS (companion opcional)

`ds-toolkit:ml-researcher` usa el plugin [academic-research-skills](https://code.claude.com)
(ARS) para revisión de literatura y comprobación de citas **si está instalado**. No es una
dependencia obligatoria: sin ARS, el agente cae a búsqueda web. Para instalar ARS, añade su
marketplace y `claude plugin install academic-research-skills@<su-marketplace>`.
