# 🛡️ Práctica Final — Machine Learning aplicado a Ciberseguridad

> Módulo de Machine Learning · Bootcamp de Ciberseguridad · KeepCoding

---

## 📋 Descripción

Práctica final del módulo de Machine Learning donde se aborda un problema real de **clasificación supervisada**: predecir qué acción se toma ante un ciberataque (**Blocked**, **Ignored** o **Logged**) a partir de un dataset con **40.000 incidencias** y **25 columnas**.

---

## 📂 Estructura del repositorio

```
├── data/
│   └── cybersecurity_attacks.csv        # Dataset de incidencias de ciberataques
├── Practica_Machine_Basica.ipynb        # Notebook básico (2 modelos)
├── Practica_Machine_Avanzada.ipynb      # Notebook avanzado (4 modelos + extras)
└── README.md
```

---

## 🔍 Proceso seguido

### 1. Exploración de datos
- Análisis con `head`, `dtypes`, `describe`, `isnull`, `value_counts`
- Detección de outliers y análisis de correlación con heatmap

### 2. Preprocesamiento
- Eliminación de columnas no útiles (IPs, timestamps, texto libre, columnas con >50% nulos)
- Conversión de nulos a variables binarias (Malware Indicators, Alerts/Warnings)
- Codificación de variables categóricas con `LabelEncoder`

### 3. Análisis visual
- Histogramas por clase para las 14 columnas resultantes

### 4. Modelado

| Notebook | Modelos | Técnicas |
|----------|---------|----------|
| **Básico** | KNN, Regresión Logística | GridSearchCV, StandardScaler, Confusion Matrix |
| **Avanzado** | KNN, Regresión Logística, Árbol de Decisión, Random Forest | GridSearchCV, StandardScaler, Feature Importance, Classification Report, Visualización del árbol, Predicción de Severity Level |

---

## 📊 Resultados

| Modelo | Train | Test |
|--------|-------|------|
| KNN (K=2) | 0.667 | 0.338 |
| Regresión Logística | 0.345 | 0.337 |
| Árbol de Decisión (depth=5) | 0.356 | 0.334 |
| Random Forest (60 est.) | 1.000 | 0.332 |

> Todos los modelos obtienen ~33% en test, equivalente al azar con 3 clases.

---

## 💡 Conclusión

El dataset tiene todas las columnas distribuidas de forma uniforme al 33% entre las tres clases, lo que impide que cualquier modelo aprenda patrones útiles. Los histogramas, las métricas, las confusion matrices y el feature importance confirman que **las características disponibles no contienen información suficiente para predecir la acción tomada**. Se probó también con **Severity Level** como target alternativo y el resultado fue idéntico.

El proceso seguido (exploración → preprocesamiento → modelado → evaluación → conclusión) es correcto. El resultado bajo no refleja un error en la metodología sino una limitación de los datos.

---

## 🛠️ Tecnologías

- Python 3.9+
- Jupyter Lab
- pandas · numpy · matplotlib · seaborn · scikit-learn

---

## 🚀 Cómo ejecutar

```bash
# Instalar uv (gestor de Python)
# macOS/Linux
curl -LsSf https://astral.sh/uv/install.sh | sh
# Windows
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"

# Instalar dependencias
uv sync

# Abrir Jupyter Lab
uv run --with jupyter jupyter lab
```

---

## 👤 Autor

Nico · Bootcamp de Ciberseguridad · KeepCoding 2026
