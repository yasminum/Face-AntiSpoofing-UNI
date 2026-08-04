# 🛡️ Face Anti-Spoofing Detection under Extreme Class Imbalance

[![Made with Jupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter)](https://jupyter.org/try)
[![Open In Colab](https://img.shields.io/badge/Open%20in-Colab-blue?style=for-the-badge&logo=googlecolab)](https://colab.research.google.com/github/yasminum/Face-AntiSpoofing-UNI/blob/main/Detection_Spoof.ipynb)

![Python](https://img.shields.io/badge/python-3.8+-blue?style=flat-square&logo=python)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red?style=flat-square&logo=pytorch)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

Repositorio oficial del proyecto final para el curso de **Maestría en Visión por Computador** en la **Universidad Nacional de Ingeniería (UNI)**.

El proyecto aborda la **Detección de Ataques de Presentación (PAD)** mediante un enfoque de imagen estática. Clasifica rostros como *Bona Fide* (reales) o *Spoof* (ataques). Utiliza **EfficientNet-B3**, **Focal Loss** y **Muestreo Aleatorio Ponderado** para manejar el severo desbalance de clases (8:1) presente en escenarios del mundo real.

---

## 📊 Resultados Clave

Nuestro modelo logró un rendimiento robusto en el conjunto de **evaluación** del dataset LCC-FASD:

| Métrica (ISO/IEC 30107-3) | Resultado |
| :--- | :--- |
| **ACER** (Tasa de Error Promedio) | **7.22%** ✅ |
| **APCER** (Error en Ataques) | **2.66%** |
| **BPCER** (Error en Presentaciones Reales) | **11.78%** |
| **Exactitud** | **96.97%** |
| **AUC-ROC** | **0.9866** |

---

## 💻 Entorno de Hardware

El código fue ejecutado y validado en el entorno JupyterHub del laboratorio de IA de la UNI (`ai-lab.pitvirtual.uni.edu.pe`) con la opción **PyTorch**:

- **CPU:** 24 Núcleos
- **RAM:** 32 GB
- **GPU:** 1 GPU (NVIDIA)
- **Disco:** 100 GB

---

## 📁 Configuración del Dataset

Para mantener el repositorio ligero, el dataset **no está incluido**. Utilizamos el **LCC-FASD** (Large Crowd-Collected Face Anti-Spoofing Dataset) [enlace al dataset original] (https://www.kaggle.com/datasets/faber24/lcc-fasd).

1.  Descarga el dataset (~4.84 GB) desde Kaggle.
2.  Extrae el archivo `.zip`.
3.  Coloca la carpeta extraída en la raíz del proyecto y renómbrala a `data/lcc_fasd/`.

La estructura esperada es:

```text
data/lcc_fasd/LCC_FASD/
├── LCC_FASD_training/
├── LCC_FASD_development/
└── LCC_FASD_evaluation/


