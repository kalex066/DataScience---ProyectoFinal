# DataScience Bootcamp — Proyecto Final

# 📊 Análisis Inicial y Selección de Problema

## 📝 Descripción

Este proyecto tiene como objetivo realizar un análisis exploratorio de datos (EDA) sobre distintos conjuntos de datos para identificar sus características, calidad y posibles desafíos. A partir de este análisis, se selecciona un conjunto de datos y una problemática específica para desarrollar un modelo de Machine Learning, justificando su relevancia y potencial de aplicación en técnicas de ciencia de datos y aprendizaje automático.

---

## 📂 Conjuntos de Datos Analizados

* 🪄 **Harry Potter Sorting:** Contiene información de 1000 estudiantes de Hogwarts. El objetivo es predecir la casa (Gryffindor, Hufflepuff, Ravenclaw, Slytherin) basándose en rasgos de personalidad y habilidades académicas.
* 📈 **Brecha de Género en STEM (2000 - 2030):** Datos longitudinales (2000-2023) sobre la representación femenina en disciplinas STEM en seis naciones clave, con el objetivo de proyectar la paridad para el 2030.
* 💰 **Salarios en Data Science (2025):** Recopilación de ofertas de empleo que vinculan habilidades técnicas, seniority y modalidad de trabajo con la remuneración salarial anual.
* 🍎 **Clasificación Nutricional (USDA 2026):** Base de datos de alta escala (+40,000 registros) que desglosa macronutrientes y micronutrientes para categorizar la calidad nutricional de los alimentos.

---

## 🔍 Resumen del EDA Inicial

| Dataset | Cantidad de Registros | Estado | Hallazgos Principales |
| :--- | :---: | :--- | :--- |
| **Harry Potter** | 1000 | ✅ Completado | Clases balanceadas y correlaciones claras entre personalidad y casa. |
| **Brecha STEM** | 500 | ✅ Completado | Datos limpios pero alta no-linealidad y volatilidad temporal |
| **Salarios DS** | 944 | ✅ Completado | Sesgo geográfico marcado y distribución salarial exponencial |
| **Nutrición USDA** | 40,000 | ✅ Completado | Alta cardinalidad en nombres y disparidad de calidad según origen del dato. |

---

## 🎯 Problema Seleccionado: Clasificación de Calidad Nutricional (USDA)

### 🚀 Descripción

Implementación de un modelo de clasificación automática para categorizar la calidad nutricional de productos alimenticios (Baja, Media, Alta), transformando perfiles de macronutrientes en una calificación objetiva.

### 💡 Justificación de la Elección

La elección responde a un **alto estándar de complejidad técnica**:

- ⚙️ **Data Wrangling:** Manejo de una cardinalidad de +30,000 elementos y necesidad de agrupación.
- 🧹 **Limpieza Estratégica:** Definición de políticas de limpieza diferenciadas según el origen de los datos (`Branded` vs `Foundation`).
- 🌍 **Impacto:** Aplicación directa en herramientas de salud pública y toma de decisiones del consumidor.

### 📋 Objetivos Específicos

1. 📉 **Reducción de Dimensionalidad:** Consolidar categorías nutricionales para mitigar el *overfitting*.
2. 🛠️ **Implementación de Pipeline:** Crear un flujo de procesamiento escalable.
3. 🤖 **Modelado Predictivo:** Entrenamiento de modelos de ensamble (*Random Forest/XGBoost*).
4. 🧠 **Interpretabilidad:** Identificar qué nutrientes determinan una calificación de "Alta calidad".

---

## 🚀 Instrucciones para Ejecutar

### Prerrequisitos

```bash
pip install pandas numpy matplotlib seaborn plotly scikit-learn lightgbm optuna joblib scipy jupyter
```

### Pasos

1. **Clonar el repositorio:**

```bash
git clone https://github.com/<tu-usuario>/CalidadNutricional.git
cd CalidadNutricional
git checkout main
```

2. **Obtener el dataset:**

- Descargar `comprehensive_foods_usda.csv` desde [USDA FoodData Central](https://fdc.nal.usda.gov/) o desde el dataset de Kaggle referenciado.
- Colocarlo en la ruta `/data/comprehensive_foods_usda.csv`.

3. **Ejecutar el notebook en orden:**

```bash
jupyter notebook CalidadNutricional_CORREGIDO.ipynb
```

Recomendado: `Runtime → Run all` para evitar errores de variables faltantes entre secciones.

4. **Ajustar la ruta del dataset** en la celda de carga (Sección 1, Paso 1.2):

```python
# En Colab
df = pd.read_csv('/content/sample_data/comprehensive_foods_usda.csv')

# En local
df = pd.read_csv('./data/comprehensive_foods_usda.csv')
```

5. **Tiempos esperados de ejecución** (referencia, dataset ~40,000 filas):

| Sección | Contenido | Tiempo aprox. |
|---|---|---|
| 1-3 | Carga, limpieza, EDA | 1-2 min |
| 4 | Preprocesamiento | < 1 min |
| 5.1 | Benchmark inicial (4 modelos, CV-5) | 3-5 min |
| 5.3 | GridSearchCV + RandomizedSearchCV | 5-10 min |
| 5.3 | Optuna (15 trials, cv=3) | 5-15 min |
| 6-7 | Evaluación final + guardado | 1-2 min |

> 💡 Si Optuna tarda demasiado, reducir `n_trials` o `cv` — el resultado converge igual al techo del problema (ver Sección 5.1.1). No es necesario completar los 30 trials para obtener un resultado válido.

### Verificación de reproducibilidad

Todos los splits y modelos usan `random_state=42`. Si los resultados de F1-macro difieren significativamente de los reportados (~0.99-0.999), verificar:

- Que `health_score` y `quality_cat` NO estén incluidas en `cols_num`/`cols_cat` (data leakage).
- Que el `preprocessor.fit()` se haya ejecutado solo sobre `X_train`.
- Que `pd.qcut` se aplicó sobre `health_score` antes del split, no después.

---

## 👥 Autores

| Nombre | Rol |
|---|---|
| Karen Herrera | Data Science Jr |

> Proyecto desarrollado como entrega final del **Bootcamp Data Science de SONDA y Skillnest**. Junio 2026.

---

## 📄 Licencia

Este proyecto se realizó con fines educativos.

### Sobre el dataset

El dataset `comprehensive_foods_usda.csv` deriva de **USDA FoodData Central**, una base de datos pública del Departamento de Agricultura de los Estados Unidos. Su uso está sujeto a los términos de USDA (dominio público para datos generados por el gobierno federal de EE.UU.). Ver [fdc.nal.usda.gov](https://fdc.nal.usda.gov/) para detalles de atribución.


