# Telco Customer Churn – Machine Learning con Selección de Rasgos vía SHAP

Predicción de **churn (abandono de clientes)** en una empresa de telecomunicaciones, utilizando un pipeline reproducible con: limpieza, imputación, encoding, selección de rasgos con SHAP, y evaluación de modelos de clasificación (KNN, DecisionTree, LogisticRegression).

> **Resultado final (sin fuga):**  
> **Accuracy ≈ 0.843** · **F1 (churn=Yes) ≈ 0.652** con 17 rasgos seleccionados vía SHAP.

## Objetivo del proyecto

- **Negocio:** predecir la probabilidad de que un cliente cancele el servicio, para priorizar acciones de retención.  
- **Analítico:** problema de clasificación binaria sobre la variable `Churn Label` (`Yes`/`No`), optimizando F1 y ROC-AUC.

## Evaluación de desempeño

El **accuracy mostrado en los resultados** no fue el criterio principal para seleccionar el mejor modelo.  
El proyecto se centró en el **F1-score**, que combina *precision* y *recall*, y es más apropiado en contextos con clases desbalanceadas, como el churn.

### Métricas consideradas

Cada modelo fue evaluado con las siguientes métricas, tanto en *train* como en *test*:

- **Precision**: proporción de predicciones positivas que fueron correctas.  
- **Recall (Sensibilidad)**: proporción de churners correctamente detectados.  
- **F1-score**: media armónica entre *precision* y *recall*, priorizando el equilibrio entre ambas.  
- **Accuracy**: proporción total de aciertos (usado solo como referencia general).

> En este proyecto, el valor de “Accuracy” presentado en los resultados corresponde al **F1 ponderado**, que se utilizó como métrica principal para evaluar el rendimiento y comparar los modelos.

### Resultados de los modelos

| Modelo | Accuracy (F1 ponderado) | F1 (Yes) | Recall (Yes) | Comentario |
|:--------|:-----------------------:|:---------:|:--------------:|:------------|
| **Regresión Logística** | 0.84 | 0.68 | 0.65 | Buen equilibrio entre precisión y recall. Sin sobreajuste. |
| **K Vecinos Más Cercanos (KNN)** | 0.83 | 0.66 | 0.63 | Similar al modelo lineal, con ligera sobreajuste en train. |
| **Árbol de Decisión** | 0.84 | 0.66 | 0.61 | Buen rendimiento, aunque algo menos estable. |

> Todos los modelos presentan resultados **coherentes y estables**, sin signos de fuga ni sobreajuste.  
> Las métricas son sólidas para un problema de churn real, donde un **F1 de 0.65–0.70** es considerado competitivo.
