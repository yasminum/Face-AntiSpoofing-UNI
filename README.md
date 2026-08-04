# Face Anti-Spoofing Detection under Extreme Class Imbalance

This repository contains the official implementation of the Final Project for the **Computer Vision Master's Course** at Universidad Nacional de Ingeniería (UNI). 

The project addresses Presentation Attack Detection (PAD) using a static image approach, classifying faces as *Bona Fide* (real) or *Spoof* (attack). It employs **EfficientNet-B3**, **Focal Loss**, and **Weighted Random Sampling** to handle the severe 8:1 class imbalance present in real-world scenarios.

## 1. Hardware Environment
The code was executed and validated on the UNI JupyterHub AI Lab environment (`ai-lab.pitvirtual.uni.edu.pe`) using the **PyTorch server option**:
- **CPU:** 24 Cores
- **RAM:** 32 GB
- **GPU:** 1 GPU (NVIDIA)
- **Disk:** 100 GB

## 2. Dataset Setup (Important)
To ensure reproducibility without exceeding repository size limits, the dataset is not included in this repository. We utilize the **Large Crowd-Collected Face Anti-Spoofing Dataset (LCC-FASD)**.

1. Download the dataset (~4.84 GB) from Kaggle: 
   👉 [LCC-FASD Dataset Link](https://www.kaggle.com/datasets/faber24/lcc-fasd)
2. Extract the `.zip` file.
3. Place the extracted folder in the root directory of this project and rename it to `data/lcc_fasd/`. The expected structure is:
   ```text
   data/lcc_fasd/LCC_FASD/
   ├── LCC_FASD_training/
   ├── LCC_FASD_development/
   └── LCC_FASD_evaluation/
   ```

## 3. Installation & Dependencies
Ensure you have Python 3.8+ installed. Install the required dependencies by running the following command in your terminal:

```bash
pip install -r requirements.txt
```

*Key dependencies include:* `torch`, `torchvision`, `timm` (for EfficientNet), `albumentations` (for robust PAD augmentations), `scikit-learn` (for ISO metrics), and `grad-cam`.

## 4. How to Run the Code and Reproduce Experiments
The entire pipeline (Data Loading, Preprocessing, Model Initialization, Training, and Evaluation) is encapsulated within a single Jupyter Notebook for ease of execution.

1. Open Jupyter Notebook / JupyterLab.
2. Launch the `Detection_Spoof.ipynb` notebook.
3. **Run All Cells sequentially.** 

### What to expect during execution:
- **Phase 1 (Data Prep):** The notebook automatically applies `Albumentations` (resizing to 300x300, avoiding heavy blur to preserve moiré patterns) and sets up the `WeightedRandomSampler`.
- **Phase 2 (Training):** EfficientNet-B3 is trained using Focal Loss (gamma=2.0) over 15 epochs. Progress (Train Loss, Val ACER) will be printed per epoch. The best model weights will be saved locally as `best_liveness_model.pth`.
- **Phase 3 (Evaluation):** The notebook calculates and reports ISO/IEC 30107-3 metrics (APCER, BPCER, ACER) on the evaluation set.
- **Phase 4 (Interpretability):** Grad-CAM heatmaps are generated to visualize the network's attention on spoofing artifacts (e.g., screen edges, reflections).
- 
## 📁 Estructura del Repositorio

- `Detection_Spoof.ipynb`: Notebook principal con el pipeline completo.
- `requirements.txt`: Dependencias necesarias para ejecutar el código.
- `results/`: Carpeta con todas las figuras generadas:
  - `eda_distribution.png`: Análisis de la distribución de clases.
  - `training_curves.png`: Curvas de entrenamiento y validación.
  - `test_results.png`: Matriz de confusión, curva ROC y DET.
  - `gradcam_analysis.png`: Mapas de activación (Grad-CAM) para interpretabilidad.

