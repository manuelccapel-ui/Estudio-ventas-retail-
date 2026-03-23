## Customer Repurchase Prediction

Proyecto de machine learning para predecir la probabilidad de recompra de clientes a partir del dataset **Online Retail II**.

## Objetivo

El objetivo del proyecto es identificar qué clientes tienen mayor probabilidad de volver a comprar en una tienda retail online. Esta predicción puede utilizarse para:

- aplicar acciones de fidelización sobre clientes con alta probabilidad de recompra,
- aplicar acciones de retención sobre clientes con baja probabilidad de volver a comprar.

## Dataset

Se ha utilizado el dataset **Online Retail II**, que contiene transacciones de una empresa minorista online del Reino Unido entre diciembre de 2009 y diciembre de 2011.

Variables principales:
- `Invoice`
- `StockCode`
- `Description`
- `Quantity`
- `InvoiceDate`
- `Price`
- `Customer ID`
- `Country`

## Flujo del proyecto

El trabajo se ha desarrollado en las siguientes fases:

1. Carga y consolidación de datos desde Excel.
2. Limpieza y control de calidad:
   - eliminación de `customer_id` nulos,
   - eliminación de duplicados exactos,
   - tratamiento de cancelaciones y devoluciones.
3. Análisis exploratorio de datos.
4. Agregación a nivel cliente.
5. Construcción del problema supervisado con validación temporal.
6. Entrenamiento y comparación de múltiples modelos:
   - Regresión logística
   - Árbol de decisión
   - Random Forest
   - Bagging / Pasting
   - Gradient Boosting
   - AdaBoost
   - KNN
   - Naive Bayes
   - SVM
   - XGBoost
   - LightGBM
7. Optimización de modelos candidatos mediante:
   - GridSearchCV
   - RandomizedSearchCV
   - Optuna

## Metodología

El problema se formula a nivel **cliente**. Para evitar fuga de información:

- las variables explicativas se construyen usando únicamente información anterior a una fecha de corte,
- la variable objetivo indica si el cliente realiza al menos una compra válida en los 3 meses posteriores.

La evaluación se realiza mediante **validación temporal**, entrenando siempre con snapshots más antiguos y evaluando en periodos posteriores.

## Modelo final

El modelo finalmente seleccionado fue:

**LightGBM + Optuna**

Resultados principales en el test temporal final:
- Accuracy: 0.7344
- Precision: 0.7443
- Recall: 0.5796
- F1-score: 0.6517
- AUC-ROC: 0.8003

## Estructura del repositorio

```text
.
├─ README.md
├─ .gitignore
├─ requirements.txt
├─ notebooks/
├─ data/
├─ figures/
├─ model_artifacts/
└─ src/
