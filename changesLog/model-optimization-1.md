# Change log Model Optimization 1

## Cambio 1

En lugar de accuracy, debemos usar una métrica que considere el desbalance. Las mejores opciones son:

- f1_weighted: Calcula el F1-score para cada clase y pondera por el número de instancias. Es un buen balance general.
- f1_macro: Calcula el F1-score para cada clase y toma el promedio simple. Trata a ambas clases por igual, sin importar su tamaño.
- recall_macro: Si tu prioridad máxima es encontrar la mayor cantidad de anomalías posible (aceptando más falsos positivos)
  optimizar por el recall.

## Cambio 2
