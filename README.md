# 🏥 Predicción de Cifosis (Kyphosis)
> Análisis comparativo entre Árboles de Decisión y Random Forest en datos médicos desbalanceados.

![Python](https://img.shields.io/badge/Python-3.12-blue?style=flat&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange?style=flat&logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Finalizado-green)

## 📄 Descripción del Proyecto
La **Cifosis** es una curvatura anormal de la columna vertebral. Este proyecto analiza un conjunto de datos de pacientes sometidos a cirugía de columna para identificar factores de riesgo que predicen la presencia de esta condición post-operatoria.

<img src="images/kyphosis.png" alt="Kyphosis" width="800"/>

El objetivo principal es comparar la eficacia de un modelo interpretable (**Decision Tree**) frente a un modelo de ensamble (**Random Forest**) en un escenario de datos pequeños y desbalanceados.

## 📂 Estructura del Repositorio
*   `data/`: Contiene el dataset `kyphosis.csv`.
*   `notebooks/`: Análisis paso a paso (`Analysis_Kyphosis.ipynb`).
*   `images/`: Gráficos generados y diagrama del árbol.

## 📊 Hallazgos del Análisis Exploratorio (EDA)
*   **Desbalance:** El dataset presenta un fuerte desbalance de clases, con solo un **20.9%** de casos positivos (Cifosis presente).
*   **Edad:** La edad promedio de los pacientes afectados es de ~97 meses (8 años).
*   **Variable Clave:** La visualización mostró que la vértebra superior operada (`Start`) es un discriminador visual importante.

## 🧠 Modelos Implementados

### 1. Árbol de Decisión (Decision Tree)
*   **Resultado:** Sufrió de sobreajuste (*overfitting*).
*   **Accuracy:** 56%
*   **Problema:** Creó reglas demasiado específicas para pacientes individuales (nodos puros de 1 muestra).

### 2. Bosque Aleatorio (Random Forest) - 200 Estimadores
*   **Resultado:** Mejoró significativamente la robustez.
*   **Accuracy:** 76% (Mejora de +20 puntos).
*   **Observación Crítica:** Logró eliminar completamente los **Falsos Positivos** (Especificidad del 100%), pero mantuvo la misma sensibilidad baja para detectar la enfermedad debido a la falta de datos positivos en el entrenamiento.

## 📉 Visualización del Árbol
Aquí se muestra la estructura de decisiones aprendida por el modelo simple:

<img src="/images/arbol_decision.png" alt="Árbol de Decisión" width="800"/>

## 🚀 Conclusiones
El uso de **Random Forest** demostró ser superior para limpiar el "ruido" y evitar falsas alarmas. Sin embargo, para uso clínico real, se recomienda aplicar técnicas de balanceo de datos (SMOTE) para mejorar la detección de casos positivos.

---
*Autor: Alejandro Barrenechea*
*Dataset: Kyphosis Data*