# LXG-Net: AI-Powered Digital Twin Framework for Neonatal Risk Prediction

LXG-Net is a proof-of-concept framework that combines temporal sensor anomaly detection, clinical risk classification, explainability, and visualization for neonatal intensive care unit (NICU) monitoring.

> **Important limitation:** The included datasets are constructed/project datasets. The reported model performance should not be interpreted as clinical validation. The framework has not been established as a medical device or validated for clinical decision-making.

## Project overview

The project explores how physiological, environmental, and clinical features can be processed together:

- **LSTM Autoencoder:** models sequences of sensor measurements and flags observations with high reconstruction error as potential anomalies.
- **XGBoost:** classifies risk categories from structured clinical features in the notebook's classification workflow.
- **SHAP:** explains feature contributions to XGBoost predictions.
- **Biological Stress Index (BSI):** a derived feature intended to summarize selected stress-related measurements.
- **Fusion layer:** combines model outputs into a composite risk score in the prototype.
- **Blender Digital Twin:** displays a 3D NICU scene with sensor/status labels and visual status changes.
- **Power BI:** provides a dashboard for exploring dataset measures and risk-related patterns.

## Repository structure

```text
LXG-Net/
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
│   └── LXG_Net_Analysis.ipynb
├── data/
│   ├── README.md
│   ├── nicu_combined_dataset.csv
│   ├── realistic_nicu_sensor_data.csv
│   ├── neonatal_low_burden.csv
│   ├── neonatal_moderate_burden.csv
│   └── neonatal_high_burden.csv
├── results/
│   └── README.md
└── digital-twin/
    ├── README.md
    └── screenshots/
```

## Getting started

1. Clone or download this repository.
2. Install the Python packages listed in `requirements.txt`.
3. Open `notebooks/LXG_Net_Analysis.ipynb` in Google Colab or Jupyter.
4. Ensure the notebook's dataset paths point to the files in `data/` (or upload the required CSV files to the notebook runtime).
5. Run the notebook cells in order and review the metrics/plots produced by the actual run.

The notebook may contain exploratory cells and code iterations. Review execution order and file paths before treating it as a clean, reproducible pipeline.

## Models in simple terms

### LSTM Autoencoder
Uses fixed-length sensor sequences to learn patterns in the training data. Reconstruction error is used as an anomaly signal; a high error indicates a pattern that differs from what the model learned.

### XGBoost
A gradient-boosted decision-tree model used for classification of structured clinical features into the risk labels defined in the dataset.

### SHAP
Provides feature-attribution explanations for XGBoost predictions. SHAP values describe how features contribute to a model output; they do not establish causation or replace clinical judgment.

## Visualizations

See `digital-twin/screenshots/` for screenshots of the Blender scene/script and Power BI dashboard.

## Data and responsible use

The data files are included for project demonstration and experimentation. Check dataset provenance and applicable permissions before redistributing them publicly. The project is for educational/research demonstration only and must not be used to diagnose, monitor, or treat patients.

## Current limitations and future work

- Validate on independent, appropriately governed real-world data before drawing clinical conclusions.
- Verify preprocessing, data splits, and evaluation methodology to prevent data leakage.
- Document the exact BSI formula and ensure it matches the implementation.
- Add a reproducible environment, clean training/evaluation scripts, and automated tests.
- Integrate live hardware/streaming only after validation and safety review.
