# DataScience Bootcamp---ProyectoFinal

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

| Dataset | Cantidad de Registros |Estado | Hallazgos Principales |
| :--- | :---: | :--- | :--- |
| **Harry Potter** | 1000 | ✅ Completado | Clases balanceadas y correlaciones claras entre personalidad y casa. |
| **Brecha STEM** | 500 | ✅ Completado | Datos limpios pero alta no-linealidad y volatilidad temporal |
| **Salarios DS** | 944 | ✅ Completado | Sesgo geográfico marcado y distribución salarial exponencial |
| **Nutrición USDA** | 40 000| ✅ Completado | Alta cardinalidad en nombres y disparidad de calidad según origen del dato. |

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
