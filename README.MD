# Telecom X – Parte 2: Predicción de Cancelación (Churn)

## 1. Preparación de Datos
- Se cargó el archivo CSV tratado previamente (`telecom_tratado.csv`).
- Eliminadas columnas irrelevantes (`customerID`) y extraídas variables útiles de columnas de tipo diccionario (`tenure`, `SeniorCitizen`, `gender`).
- One-hot encoding aplicado a variables categóricas.
- Proporción de churn:
  - 0 (No canceló): 73.46%
  - 1 (Canceló): 26.53%

## 2. Análisis de Correlación
- Correlación con churn:

| Variable      | Correlación |
|---------------|------------|
| tenure        | -0.352     |
| SeniorCitizen | 0.151      |
| gender_Male   | -0.009     |

> Conclusión: `tenure` es la variable más influyente; SeniorCitizen tiene un efecto menor; gender no es relevante.

## 3. Modelado Predictivo

### 3.1 Separación de Datos
- Split 70/30 (estratificado).

### 3.2 Modelos Entrenados
1. Regresión Logística (con normalización)
2. Árbol de Decisión (sin normalización)

### 3.3 Evaluación de los Modelos

###🔹 Regresión Logística
```text
Matriz de Confusión:
[[1489   63]
 [ 470   91]]

Classification Report:
               precision    recall  f1-score   support
           0       0.76      0.96      0.85      1552
           1       0.59      0.16      0.25       561
### Árbol de decisión
Matriz de Confusión:
[[1401  151]
 [ 381  180]]

Classification Report:
               precision    recall  f1-score   support
           0       0.79      0.90      0.84      1552
           1       0.54      0.32      0.40       561
### 3.4 Visualización

### 3.5 Comparación

Exactitud: Árbol de Decisión 0.75 > Regresión Logística 0.74

Regresión logística: mejor para detectar clientes que no cancelan.

Árbol de Decisión: mejor balance general, leve overfitting en clase minoritaria.

### 4. Interpretación e Importancia de Variables

Variables más relevantes: tenure y SeniorCitizen.

Consistentes entre Regresión Logística y Árbol de Decisión.

KNN/SVM/otros no implementados en este desafío.

### 5. Conclusiones

Factores principales de cancelación:

Tenure bajo → mayor riesgo de churn

SeniorCitizen → riesgo ligeramente mayor

Estrategias de retención:

Incentivos y comunicación temprana para clientes nuevos.

Programas de fidelización para adultos mayores.

Árbol de Decisión ligeramente superior; combinación de modelos puede mejorar predicción.
