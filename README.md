# EEG Seizure Detection | Machine Learning on Multichannel Time Series

**Python · scikit-learn · XGBoost · EEG · supervised classification**

A collaborative academic project evaluating seizure versus non-seizure classification from EEG channel-voltage observations. Developed for **MMD6020 (Fall 2022)** by **Guillermo Martínez Villar, Azadeh Bayani and Anni Wu**.

## At a glance

| Dataset | Methods | Held-out results |
| --- | --- | --- |
| CHB-MIT scalp EEG; ~2.1 million voltage measurements from 23 channels | Logistic regression, AdaBoost, random forest, XGBoost | Tuned XGBoost **ROC-AUC 0.9694**, **macro F1 0.9120**, **accuracy 91.21%** |

**Interpretation:** these metrics describe the original observation-level held-out evaluation. **Patient-independent external generalization was not assessed.** Adjacent EEG observations can be highly correlated, so these metrics must not be interpreted as performance on previously unseen patients.

## Research question

Can nonlinear supervised classifiers distinguish annotated seizure activity from non-seizure EEG observations using multichannel voltage information? What improvement do they provide over a linear logistic-regression baseline?

## Results

| Classifier | Test ROC-AUC |
| --- | ---: |
| Logistic regression | 0.4990 |
| Random forest | 0.9675 |
| Tuned XGBoost | **0.9694** |

Figures and additional experiments are saved in the original notebooks. These numbers are taken from the project outputs; this documentation update does **not** claim new model training.

## Dataset and provenance

- **Original data:** [CHB-MIT Scalp EEG Database, PhysioNet](https://physionet.org/content/chbmit/1.0.0/); 256 Hz recordings with seizure annotations.
- **Project-prepared CSV:** [Google Drive dataset used in the notebooks](https://drive.google.com/file/d/1j--AJ7OEcRLngnt0h_fAlyCHo6sx_FNd/view).
- **License / data access:** Check PhysioNet and the project dataset's permissions before redistribution. The raw data are not duplicated in this repository.

## Reproduce the original analysis

```bash
git clone https://github.com/martinezgtupacamaru/eeg-seizure-detection-ml.git
cd eeg-seizure-detection-ml/eeg_seizure_dectection_ml
python -m pip install -r requirements.txt
jupyter notebook Notebooks/
```

Download the CSV separately and adjust local input paths in the notebooks before running. Notebook dependencies reflect the original project and may need version adjustments in a modern Python environment.

## Repository guide

- [Final version.ipynb](eeg_seizure_dectection_ml/Notebooks/Final%20version.ipynb) — Main comparison and evaluation.
- [Final_xgb.ipynb](eeg_seizure_dectection_ml/Notebooks/Final_xgb.ipynb) — XGBoost training and evaluation.
- [test_xgb.ipynb](eeg_seizure_dectection_ml/Notebooks/test_xgb.ipynb) — Additional model experiments.
- [Original README](eeg_seizure_dectection_ml/README.md) — Detailed methodology, dataset links and project credits.
- [requirements.txt](eeg_seizure_dectection_ml/requirements.txt) — Original dependencies.

The nested directory name is retained to avoid breaking file references or changing the original project history.

## Limitations

1. Patient-independent train/test separation was not established.
2. Observation-level evaluation may overstate deployment-level generalization.
3. Seizure prevalence, clinical false-alarm rate per hour, and calibration must be established before any medical application.
4. This is a research and educational project, **not** a clinical detection system.

## Attribution

Guillermo Martínez Villar, Azadeh Bayani and Anni Wu. Course: MMD6020 (Fall 2022). Dataset: CHB-MIT (PhysioNet). See the [original README](eeg_seizure_dectection_ml/README.md) for references.
