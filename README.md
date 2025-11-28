# Proyecto 1 - Modelos de Sistemas  
### Universidad de Antioquia - Ingeniería de Sistemas (Modalidad Virtual)

---

## Descripción  
Este repositorio corresponde al **Proyecto 1** de la asignatura *Modelos de Sistemas*.  

El proyecto consiste en desarrollar un modelo de Machine Learning para predecir el rendimiento académico en las **Pruebas Saber Pro de Colombia**, utilizando variables socioeconómicas y académicas de estudiantes universitarios.

**Competencia Kaggle:** [UDEA AI 4 - Pruebas Saber Pro Colombia](https://www.kaggle.com/competitions/udea-ai-4-eng-20252-pruebas-saber-pro-colombia)

---

## Integrantes del equipo  

| Nombre | Cédula | Programa | Usuario Kaggle |
|--------|--------|----------|----------------|
| **José David Henao Gallego** | 1002205747 | Ingeniería de Sistemas | [josdhenaogallego](https://www.kaggle.com/josdhenaogallego) |
| **Juan Andrés Lema Tamayo** | 1001233264 | Ingeniería de Sistemas | [juanandreslematamayo](https://www.kaggle.com/juanandreslematamayo) |

---

## Contenido del repositorio  
```
Proyecto-1-Modelos-de-Sistemas/
│
├── 01 - exploración.ipynb          # Análisis exploratorio de datos
├── 02 - preprocesado.ipynb          # Preprocesamiento y entrenamiento del modelo
├── 03 - modelo con preprocesado LogisticRegression OneHot SimpleImputer.ipynb
├── 04 - modelo con preprocesado Ensemble GradientBoosting XGBoost LightGBM OneHot.ipynb
├── 05 - modelo con preprocesado Stacking XGB LGBM GB meta LogReg OrdinalEncoder.ipynb
├── 06 - modelo con preprocesado LGBM optimizado OOF FeatEng Ordinal.ipynb
├── 07 - modelo solución.ipynb  # MODELO FINAL
├── README.md                   # Este archivo                 
```

---

## Entregables - Entrega 2

### 1. Video Explicativo (3-4 minutos)

**[Ver video en YouTube](https://youtu.be/jmIibmWRDDE)**

### Opción 2 - Drive:
** [Ver en Drive](https://drive.google.com/file/d/1pVYYp-RLQFH_aEdL70CAZgdKqutwZ4ZT/view?usp=sharing)**

**Contenido del video:**
- Explicación del preprocesamiento de datos
- Transformaciones aplicadas (one-hot encoding, normalización, etc.)
- Demostración del notebook `02 - preprocesado.ipynb`

---

### 2. Notebook de Preprocesamiento

**Archivo:** `02 - preprocesado.ipynb`

**Operaciones realizadas:**

#### **Carga de datos**
- Dataset de entrenamiento: 692,500 registros × 21 columnas
- Dataset de prueba: 296,786 registros × 20 columnas

#### **Limpieza de datos**
- Manejo de valores faltantes (3-4% del dataset)
- Reemplazo de nulos por categoría `'no info'`
- Limpieza de categorías ambiguas (`'No sabe'`, `'No Aplica'`)

#### **Transformaciones aplicadas**

1. **Conversión de rangos numéricos** (`E_VALORMATRICULAUNIVERSIDAD`)
```python
   'Menos de 500 mil' → 0.25
   'Entre 1-2.5 millones' → 1.75
   'Más de 7 millones' → 8.0
```

2. **Codificación One-Hot** (Variables categóricas)
   - `F_EDUCACIONMADRE` → 11 columnas binarias
   - `F_EDUCACIONPADRE` → 11 columnas binarias
   - `E_PAGOMATRICULAPROPIO` → Variable binaria

3. **Codificación ordinal del target** (`RENDIMIENTO_GLOBAL`)
```python
   'bajo' → 0
   'medio-bajo' → 1
   'medio-alto' → 2
   'alto' → 3
```

---

## Entregables - Entrega 3

### 1. Video Explicativo Final (3-4 minutos)

**[Ver video en YouTube](ENLACE_PENDIENTE)**

**Opción 2 - Drive:**
**[Ver en Drive](ENLACE_PENDIENTE)**

**Contenido del video:**
- Evolución de los modelos (del baseline al ensemble final)
- Explicación del ensemble ponderado con LightGBM, XGBoost y CatBoost
- Resultados en Kaggle (Score: 0.44355)
- Demostración del notebook `99_modelo_solucion_ensemble_LGBM_XGB_CatBoost.ipynb`

---

### 2. Evolución de los modelos

#### 📊 **Modelo 3: Baseline - Logistic Regression**
- **Archivo:** `03_baseline_LogisticRegression_OneHot_SimpleImputer.ipynb`
- **Técnicas:** OneHot Encoding, SimpleImputer
- **Accuracy:** ~35-38%
- **Objetivo:** Establecer línea base del rendimiento

#### 📈 **Modelo 4: Ensemble Básico**
- **Archivo:** `04_ensemble_GradientBoosting_XGBoost_LightGBM_OneHot.ipynb`
- **Técnicas:** Promedio de probabilidades de 3 modelos
- **Algoritmos:** GradientBoosting, XGBoost, LightGBM
- **Accuracy:** ~40-42%
- **Mejora:** Primera aproximación a algoritmos de boosting

#### 🎯 **Modelo 5: Stacking Avanzado**
- **Archivo:** `05_stacking_XGB_LGBM_GB_meta_LogReg_OrdinalEncoder.ipynb`
- **Técnicas:** Stacking de dos niveles con OOF predictions
- **Base learners:** XGBoost, LightGBM, GradientBoosting
- **Meta-modelo:** Logistic Regression
- **Encoding:** OrdinalEncoder (más eficiente en memoria)
- **Accuracy:** ~42-44%
- **Diferencia clave:** Meta-aprendizaje para combinar modelos de forma inteligente

#### 🚀 **Modelo 6: LightGBM Optimizado**
- **Archivo:** `06_LightGBM_optimizado_OOF_FeatureEngineering_OrdinalEncoder.ipynb`
- **Técnicas:** 
  - Validación cruzada StratifiedKFold (4-7 folds)
  - Out-of-Fold predictions
  - Early stopping
  - Feature engineering avanzado
- **Hiperparámetros optimizados:**
```python
  learning_rate: 0.02
  n_estimators: 2500
  num_leaves: 128
  feature_fraction: 0.8
  bagging_fraction: 0.8
```
- **Accuracy:** ~44%
- **Diferencia clave:** Pasó de "muchos modelos básicos" a "un solo modelo experto bien optimizado"

#### 🏆 **MODELO 99 (FINAL - Entrega 3)**
- **Archivo:** `99_modelo_solucion_ensemble_LGBM_XGB_CatBoost.ipynb`
- **Estrategia:** Ensemble ponderado (Blending)
- **Algoritmos:**
  - **LightGBM** (peso: 0.55) - n_estimators: 600, learning_rate: 0.03
  - **XGBoost** (peso: 0.20) - n_estimators: 550, learning_rate: 0.035
  - **CatBoost** (peso: 0.25) - iterations: 300, learning_rate: 0.06
- **Preprocesamiento especial:**
  - Manejo de NaN diferenciado por algoritmo
  - Categorical features nativas para CatBoost
  - Sentinel values (-9999) para numéricos
- **Score final en Kaggle:** **0.44355**
- **Diferencia clave:** Combina tres algoritmos complementarios con pesos optimizados basados en su performance individual

---

### 3. Resultados finales

| Métrica | Valor |
|---------|-------|
| **Accuracy (Validation)** | 0.4435 |
| **Score Kaggle** | 0.44355 |
| **Mejora vs Baseline** | +6.5% |

**Estrategia ganadora:**
- Diversidad de algoritmos (LightGBM, XGBoost, CatBoost)
- Pesos optimizados basados en performance
- Blending de probabilidades
- Manejo robusto de datos categóricos

---

## Notas importantes

- El preprocesamiento se mantiene **simple e interpretable**
- Se priorizó la **reproducibilidad** del código
- Todas las transformaciones son **consistentes** entre train y test
- El código está **documentado** para facilitar la comprensión
- La evolución de modelos muestra un proceso de **aprendizaje iterativo**

---

## Licencia

Este proyecto es de carácter académico y pertenece a la Universidad de Antioquia.

---

**Universidad de Antioquia**  
*Ingeniería de Sistemas - Modalidad Virtual*  
*2025-2*