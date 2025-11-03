# Proyecto 1 - Modelos de Sistemas  
### Universidad de Antioquia - Ingeniería de Sistemas (Modalidad Virtual)

---

## Descripción  
Este repositorio corresponde al **Proyecto 1** de la asignatura *Modelos de Sistemas*.  

El proyecto consiste en desarrollar un modelo de Machine Learning para predecir el rendimiento académico en las **Pruebas Saber Pro de Colombia**, utilizando variables socioeconómicas y académicas de estudiantes universitarios.

**Competencia Kaggle:** [UDEA AI 4 - Pruebas Saber Pro Colombia](https://www.kaggle.com/competitions/udea-ai-4-eng-20252-pruebas-saber-pro-colombia)

---

## Integrantes del equipo  

| Nombre | Cédula | Programa |
|--------|--------|----------|
| **José David Henao Gallego** | 1002205747 | Ingeniería de Sistemas |
| **Juan Andrés Lema Tamayo** | 1001233264 | Ingeniería de Sistemas |

---

## Contenido del repositorio  

```
Proyecto-1-Modelos-de-Sistemas/
│
├── 01 - exploración.ipynb          # Análisis exploratorio de datos
├── 02 - preprocesado.ipynb          # Preprocesamiento y entrenamiento del modelo
├── README.md                   # Este archivo
└── kaggle.json                 
```

---

## Entregables - Entrega 2

### 1. Video Explicativo (3-4 minutos)

**[Ver video en YouTube](https://youtu.be/ObgS8TdJHQ0)**

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

## Notas importantes

- El preprocesamiento se mantiene **simple e interpretable**
- Se priorizó la **reproducibilidad** del código
- Todas las transformaciones son **consistentes** entre train y test
- El código está **documentado** para facilitar la comprensión

---

## Licencia

Este proyecto es de carácter académico y pertenece a la Universidad de Antioquia.

---

**Universidad de Antioquia**  
*Ingeniería de Sistemas - Modalidad Virtual*  
*2025-2*