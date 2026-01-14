# Telecom X – Parte 2: Predicción de Cancelación (Churn)

# Descripción del Proyecto

Este repositorio contiene el desarrollo del Desafío Telecom X – Parte 2, enfocado en la construcción y evaluación de modelos predictivos para anticipar la cancelación de clientes (churn) en una empresa de telecomunicaciones.

El proyecto utiliza datos previamente limpiados y transformados en la Parte 1 del desafío, y aplica técnicas de estadística, análisis de correlación y machine learning para identificar los principales factores asociados a la cancelación de servicios.

El objetivo final es generar insights estratégicos que ayuden a la empresa a reducir la pérdida de clientes mediante decisiones basadas en datos.

# Objetivo

Desarrollar un pipeline inicial de modelado predictivo capaz de identificar clientes con alta probabilidad de cancelar su servicio, permitiendo a Telecom X anticiparse al problema del churn y diseñar estrategias de retención más efectivas.

# Contexto del Desafío

Tras un desempeño exitoso en el análisis exploratorio de datos (Parte 1), el rol evoluciona a Analista Junior de Machine Learning, formando parte del equipo encargado de crear soluciones predictivas para un problema real de negocio.

Este desafío simula un entorno empresarial real, donde la ciencia de datos se aplica como herramienta estratégica.

# Desarrollo del proyecto

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
