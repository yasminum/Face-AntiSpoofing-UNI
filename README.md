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
⚙️ Instalación y Dependencias
Asegúrate de tener Python 3.8+ instalado. Luego, instala las dependencias:

bash
pip install -r requirements.txt
Principales dependencias: torch, torchvision, timm, albumentations, scikit-learn, grad-cam.

🚀 Cómo Ejecutar el Código
Abre Jupyter Notebook o JupyterLab.

Lanza el notebook Detection_Spoof.ipynb.

Ejecuta todas las celdas secuencialmente.

📌 Flujo de Ejecución
Fase 1 (Preparación de Datos): El notebook aplica Albumentations (redimensiona a 300x300, evitando desenfoques fuertes para preservar patrones moiré) y configura el WeightedRandomSampler.

Fase 2 (Entrenamiento): EfficientNet-B3 se entrena usando Focal Loss (gamma=2.0) durante 15 épocas. El progreso (Pérdida de Entrenamiento, ACER de Validación) se imprime por época. Los mejores pesos del modelo se guardan como best_liveness_model.pth.

Fase 3 (Evaluación): El notebook calcula y reporta las métricas ISO/IEC 30107-3 (APCER, BPCER, ACER) en el conjunto de evaluación.

Fase 4 (Interpretabilidad): Se generan mapas de calor Grad-CAM para visualizar la atención de la red en artefactos de suplantación (ej., bordes de pantalla, reflejos).

📂 Estructura del Repositorio
text
Face-AntiSpoofing-UNI/
├── Detection_Spoof.ipynb   # Notebook principal con el pipeline completo.
├── requirements.txt        # Dependencias necesarias.
└── results/                # Figuras generadas:
    ├── eda_distribution.png
    ├── training_curves.png
    ├── test_results.png
    └── gradcam_analysis.png
👥 Integrantes del Grupo
Franklin Alegria Barboza

Jose Luis Espinoza Chamaya

Amit Roy Flores Rivera

Raquel Medianero Huari

Yasmin Mariela Urrego Montoya

Profesora: Mg. Elian Raquel Laura Riveros

text

---

### ✨ 2. El "Toque Final" que Marca la Diferencia

Estas acciones adicionales harán que tu proyecto destaque:

*   **Añade un `.gitignore`:** Esto evita que archivos temporales o pesados (como `__pycache__` o el dataset) se suban accidentalmente. Puedes crear un archivo llamado `.gitignore` en la raíz con este contenido básico:
    ```text
    # Byte-compiled / optimized / DLL files
    __pycache__/
    *.py[cod]

    # Jupyter Notebooks
    .ipynb_checkpoints/

    # Dataset (pesado, no se sube)
    data/
    *.pth
    *.h5
Organiza el Notebook: Si en Detection_Spoof.ipynb todavía ves las salidas de las celdas (gráficos, tablas de pérdida), sería ideal limpiarlas antes de la entrega final. En Jupyter, ve a Edit -> Clear All Outputs y guarda de nuevo el archivo. Así el notebook pesará menos y se verá más profesional al abrirlo.

🤔 ¿Qué te parece?
Con estos cambios, tu repositorio pasará de estar "muy bien" a ser impecable. El README mejorado es más atractivo a primera vista, la tabla de resultados es el centro de atención, y el .gitignore demuestra buenas prácticas.

¿Quieres que te ayude con algún otro detalle? ¡Estamos a un paso del 20! 🚀

