# Change log Model Optimization 1

## Cambio 1 Cambiar metrica de Optimización

En lugar de accuracy, debemos usar una métrica que considere el desbalance. Las mejores opciones son:

- f1_weighted: Calcula el F1-score para cada clase y pondera por el número de instancias. Es un buen balance general.
- f1_macro: Calcula el F1-score para cada clase y toma el promedio simple. Trata a ambas clases por igual, sin importar su tamaño.
- recall_macro: Si tu prioridad máxima es encontrar la mayor cantidad de anomalías posible (aceptando más falsos positivos)
  optimizar por el recall.

## Cambio 2 Mejorar estrategía de balaceo de datos

Cambiar de estrategía de balanceo a `oversampling` + `undersamplig`

En lugar de aplicar SMOTE (solo oversampling), usaremos técnicas combinadas que limpian el "ruido" después de crear las muestras
sintéticas. Las dos más populares en imblearn son:

1. `SMOTEENN`: Combina SMOTE con Edited Nearest Neighbours. SMOTE crea las muestras y luego ENN elimina las muestras de ambas clases que
   están mal clasificadas, limpiando el espacio de características.
2. `SMOTETomek`: Combina SMOTE con Tomek Links. Después de SMOTE, busca pares de instancias de clases opuestas que son vecinos más
   cercanos (Tomek Links) y elimina la instancia de la clase mayoritaria. Esto ayuda a definir mejor el borde de decisión.
