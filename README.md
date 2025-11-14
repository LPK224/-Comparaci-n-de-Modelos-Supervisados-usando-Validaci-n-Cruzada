# Análisis Predictivo de Cáncer de Mama - Breast Cancer Wisconsin

## 📌 Descripción del Proyecto
Análisis predictivo completo del dataset **Breast Cancer Wisconsin** que contiene 30 características morfológicas de núcleos celulares para 569 muestras. El objetivo es desarrollar un modelo de clasificación robusto para distinguir entre tumores benignos y malignos utilizando validación cruzada y técnicas de machine learning supervisado.

## 🎯 Objetivos del Trabajo
- Comparar el rendimiento de múltiples algoritmos de clasificación
- Validar la robustez de los modelos mediante validación cruzada
- Identificar el modelo con mejor capacidad de generalización
- Establecer un pipeline reproducible para problemas de clasificación médica

## 📊 Dataset y Variables

### Características del Dataset
- **Muestras**: 569 casos (training: 341, validation: 114, test: 114)
- **Características**: 30 variables numéricas de morfología celular
- **Variable objetivo**: `diagnosis` (M = Maligno, B = Benigno)
- **Distribución**: 357 benignos (62.7%) vs 212 malignos (37.3%)

### Variables Principales
Las características incluyen mediciones de:
- `radius_mean`: Radio promedio de los núcleos celulares
- `texture_mean`: Desviación estándar de valores de escala de grises
- `perimeter_mean`, `area_mean`: Dimensiones morfológicas
- `concavity_mean`, `concave points_mean`: Características de contorno
- Mediciones adicionales para error estándar y peores casos

## 🔧 Metodología

### Preprocesamiento
- **Limpieza**: Dataset completo sin valores nulos
- **Codificación**: Variable objetivo codificada (B→0, M→1)
- **Estandarización**: StandardScaler para normalizar características
- **División**: Estratificada 60-20-20 (train-val-test)

### Modelos Evaluados
1. **Logistic Regression** - Regresión logística con regularización
2. **K-Neighbors** - Clasificador por vecinos más cercanos
3. **Decision Tree** - Árbol de decisión
4. **Random Forest** - Ensemble de árboles

### Evaluación
- **Métrica principal**: ROC AUC
- **Validación cruzada**: 5-fold estratificado
- **Comparativa**: Rendimiento en training, validation y test

## 📈 Resultados y Hallazgos

### Rendimiento Comparativo
| Modelo | Train AUC | Val AUC | CV Mean ± Std |
|--------|-----------|---------|----------------|
| Logistic Regression | 0.9979 | 0.9957 | 0.9904 ± 0.0089 |
| K-Neighbors | 0.9965 | 0.9948 | 0.9772 ± 0.0116 |
| Decision Tree | 1.0000 | 0.8972 | 0.9265 ± 0.0257 |
| Random Forest | 1.0000 | 0.9915 | 0.9874 ± 0.0138 |

### Modelo Seleccionado: Logistic Regression
- **ROC AUC en prueba**: 0.9960
- **Accuracy**: 96.49%
- **Precisión**: 96% (benignos), 97% (malignos)
- **Recall**: 99% (benignos), 93% (malignos)

## 🔍 Hallazgos Clave

### 1. Balance de Clases
- **Distribución**: 63% benignos vs 37% malignos
- **Estrategia**: División estratificada exitosa
- **Resultado**: Proporción consistente en todos los conjuntos (37.2%-37.7%)

### 2. Sobreajuste y Generalización
- **Logistic Regression**: Mínimo sobreajuste (diferencia 0.0022)
- **Decision Tree**: Sobreajuste severo (diferencia 0.1028)
- **Consistencia**: Excelente concordancia CV-Test (diferencia 0.0056)

### 3. Robustez del Modelo
- **Alta sensibilidad**: 93% recall en malignos
- **Alta especificidad**: 99% recall en benignos
- **Balance óptimo**: F1-scores equilibrados (0.97 benignos, 0.95 malignos)

## 💡 Conclusiones Principales

1. **Modelo Óptimo**: Logistic Regression demostró el mejor equilibrio entre rendimiento y generalización
2. **Validación Confiable**: La validación cruzada fue efectiva para estimar el rendimiento real
3. **Dataset de Calidad**: Características morfológicas son altamente predictivas
4. **Aplicabilidad Clínica**: Modelo con potencial para apoyo al diagnóstico temprano

## 🚀 Implementación

### Requisitos
```python
pandas>=1.3.0
scikit-learn>=1.0.0
matplotlib>=3.5.0
seaborn>=0.11.0
numpy>=1.21.0
```
