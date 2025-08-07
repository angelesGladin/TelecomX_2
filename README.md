# 📉 Telecom X – Predicción de Cancelación de Clientes (Churn Prediction)

Proyecto de análisis y modelado predictivo para anticipar la cancelación de clientes en una empresa de telecomunicaciones. Utiliza técnicas de machine learning, análisis exploratorio y herramientas de interpretabilidad como SHAP, con el objetivo de entender los factores que influyen en el abandono y proponer estrategias de retención efectivas.

---

## 📁 Estructura del Repositorio

📦 TelecomX-Churn
├── data/ # Datos procesados y tratados
├── notebooks/ # Notebooks de análisis y modelado
├── models/ # Modelos entrenados (opcional)
├── outputs/ # Resultados y visualizaciones
├── informe_cancelacion_telecom_x.md # Informe técnico en Markdown
├── requirements.txt # Paquetes necesarios
└── README.md # Este archivo

markdown
Copiar
Editar

---

## 🧠 Objetivo del Proyecto

Desarrollar un modelo capaz de predecir si un cliente cancelará su servicio, con base en sus características de contrato, historial de pagos y uso de servicios. Esto permite a la empresa tomar acciones proactivas y reducir su tasa de cancelación (churn rate).

---

## 🧪 Proceso de Desarrollo

1. **Carga y limpieza de datos**
   - Eliminación de ID único
   - Codificación de variables categóricas con `get_dummies`
   - Balanceo de clases con **SMOTE**
   - Normalización con **StandardScaler**

2. **Análisis Exploratorio (EDA)**
   - Histogramas, boxplots y gráficos de correlación
   - Identificación de variables influyentes
   - Análisis de churn por tipo de contrato, servicios y método de pago

3. **Selección de características**
   - `SelectKBest` con `f_classif`
   - K óptimo = 29 variables seleccionadas por rendimiento

4. **Entrenamiento de modelos**
   - Regresión Logística (`LogisticRegression`)
   - Random Forest (`RandomForestClassifier`)
   - Gradient Boosting (`GradientBoostingClassifier`)
   - K-Nearest Neighbors (`KNN`)
   - Ensemble (VotingClassifier: LR + GB)

5. **Optimización de hiperparámetros**
   - `GridSearchCV` con validación cruzada estratificada

6. **Evaluación**
   - Métricas: Accuracy, Precision, Recall, F1 Score
   - Matrices de confusión
   - Curvas ROC y AUC
   - Interpretación con SHAP y coeficientes logísticos

---

## 🏆 Resultados

| Modelo                  | Accuracy | Precision | Recall | F1 Score | AUC  |
|-------------------------|----------|-----------|--------|----------|------|
| Gradient Boosting       | 0.7887   | 0.5907    | 0.5864 | 0.5886   | 0.850|
| Regresión Logística     | 0.7956   | 0.5997    | 0.6221 | 0.6107   | 0.840|
| Ensemble (LR + GB)      | **0.8025**| **0.6277**| 0.5740 | 0.5996   | **0.851**|

✅ El modelo **Ensemble** combina lo mejor de LR (interpretabilidad) y GB (performance), logrando el mejor AUC.

---

## 🔍 Principales Factores de Cancelación

Según SHAP y análisis de correlación:

- Clientes con contrato **"month to month"**
- **Método de pago:** electronic check
- No contar con **servicios adicionales** como soporte técnico, seguridad o respaldo online
- **Clientes recientes** (pocos meses en la empresa)
- **Altos cargos mensuales** y bajo engagement

---

## 💡 Estrategias de Retención Sugeridas

- Incentivar contratos de **largo plazo** (1–2 años)
- Ofrecer servicios de valor agregado (bundle: soporte + seguridad + respaldo)
- Promocionar **pagos automáticos** con tarjeta o transferencia
- Seguimiento a clientes con **cargos altos**
- Programas de fidelización para clientes con baja antigüedad

---

## ⚙️ Requisitos

+ Python 3.8+
+ pandas
+ numpy
+ matplotlib
+ seaborn
+ scikit-learn
+ imblearn
+ shap

---

Instala las dependencias con:

```bash
pip install -r requirements.txt

```
----

📌 Notas Técnicas

Se utilizó SMOTE para balancear clases antes del entrenamiento

El set de datos fue dividido en 70/30 para entrenamiento y test

Las métricas se evaluaron sobre el set de prueba

Interpretabilidad usando shap.summary_plot y coeficientes logísticos

📚 Archivos Relevantes

informe_cancelacion_telecom_x: Informe técnico detallado del proyecto

notebooks/: Todos los pasos de análisis, modelado y evaluación

---

👨‍💻 Autor
