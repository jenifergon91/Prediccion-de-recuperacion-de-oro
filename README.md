# Proyecto de Predicción de Recuperación de Oro

## Descripción del Proyecto

Este proyecto tiene como objetivo desarrollar un modelo de machine learning para predecir la cantidad de oro extraído del mineral de oro en las diferentes etapas del proceso de purificación. El modelo ayudará a optimizar la producción y a identificar parámetros no rentables en el proceso.

Se utilizaron datos proporcionados por Zyfra, una empresa que desarrolla soluciones de eficiencia para la industria pesada, que detallan el proceso de extracción y purificación del oro.

## Proceso Tecnológico

El proceso de extracción de oro del mineral se divide en varias etapas clave:

1.  **Flotación (Rougher):** Tratamiento primario para obtener una mezcla de mineral (alimentación rougher) que se utiliza para la flotación. Se obtiene un concentrado de oro rougher y colas rougher.
2.  **Purificación Primaria (Primary Cleaner):** El concentrado rougher se somete a una primera etapa de purificación.
3.  **Purificación Secundaria (Secondary Cleaner):** El material de la purificación primaria pasa por una segunda etapa de purificación.
4.  **Concentrado Final (Final):** El producto final después de las dos etapas de purificación.

Para más detalles sobre las etapas y los parámetros, consulta la descripción en el notebook principal.

## Datos

Los datos utilizados en este proyecto provienen de tres archivos CSV:

*   `gold_recovery_train.csv`: Conjunto de datos de entrenamiento.
*   `gold_recovery_test.csv`: Conjunto de datos de prueba (sin objetivos).
*   `gold_recovery_full.csv`: Conjunto de datos fuente completo.

Los datos están indexados por fecha y hora. Algunas características presentes en el conjunto de entrenamiento no están disponibles en el conjunto de prueba, ya que se miden o calculan en etapas posteriores del proceso.

## Métricas de Evaluación

La evaluación del modelo se realiza utilizando el Error Medio Absoluto Porcentual Simétrico (sMAPE), definido por la fórmula:

$ sMAPE = \frac{1}{N} \sum_{i=1}^{N} \frac{|y_i - \hat{y}_i|}{(|y_i| + |\hat{y}_i|)/2} \times 100\% $

Donde:
*   $y_i$: Valor objetivo real.
*   $\hat{y}_i$: Valor predicho por el modelo.
*   $N$: Número de observaciones.

La métrica final para evaluar el modelo es un sMAPE ponderado que combina las predicciones de recuperación en la etapa rougher y final:

$ sMAPE_{final} = 0.25 \times sMAPE_{rougher} + 0.75 \times sMAPE_{final} $

## Estructura del Proyecto

El núcleo del proyecto se encuentra en el notebook principal. La estructura de archivos es:
├── gold_recovery_train.csv ├── gold_recovery_test.csv ├── gold_recovery_full.csv ├── Prediccion_oro.ipynb └── README.md
