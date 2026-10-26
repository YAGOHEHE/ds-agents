---
description: Reglas de rigor para ciencia de datos y machine learning. Úsala al entrenar, evaluar o revisar modelos, elegir métricas, hacer splits o registrar experimentos. Cubre métricas en datos desbalanceados, validación temporal, fugas de datos, oversampling, MLflow y la distinción detección vs predicción.
---

# Rigor en ciencia de datos y ML

Aplica estas reglas en cualquier tarea de modelado, evaluación o revisión. No dependen del
dominio del proyecto.

## Métricas

- En clasificación desbalanceada, la métrica principal es el **MCC** (coeficiente de correlación
  de Matthews) o una métrica robusta al desbalance (F1, balanced accuracy). **Nunca** se reporta
  accuracy como métrica principal: es engañosa con clases desbalanceadas.
- El umbral de decisión se elige en **validación**, nunca en el conjunto de test.

## Validación y fugas de datos

- En **series temporales**, el split es temporal (p. ej. `TimeSeriesSplit`) con **embargo** entre
  train y test. Nunca split aleatorio: filtra información futura.
- El **escalado** y el **oversampling/SMOTE** se ajustan **solo sobre train**, después del split.
  Aplicarlos antes del split o sobre test introduce fuga de datos.
- Revisa features que usan información futura: `shift` negativos, ventanas centradas, etiquetas
  propagadas al pasado.

## Experimentos y reproducibilidad

- Registra cada experimento en **MLflow** (o el tracker del proyecto) con parámetros, métricas y
  **semilla** fijada. La configuración vive en ficheros (YAML), no incrustada en el código.

## Detección vs predicción

- Distingue siempre **detección** (mismo instante) de **predicción/anticipación** (horizonte H):
  son preguntas distintas y se evalúan distinto. Comprueba que el resultado responde a la pregunta
  que dice responder.

## Datos y secretos

- Nunca leas ni muestres ficheros `.env` ni credenciales.
- No modifiques datos crudos/inmutables (p. ej. `data/**/raw/**`).

## Verificar antes de afirmar

- No presentes como hecho algo que no has comprobado. Si no ejecutaste los tests o el pipeline,
  dilo. Separa lo verificado de lo que supones. Si algo falla, repórtalo con la salida real.
- Toda cita o referencia externa va con fuente verificable (fichero, run de MLflow, DOI/enlace).
