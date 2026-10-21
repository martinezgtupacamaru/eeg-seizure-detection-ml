# EEG Seizure Detection Using Machine Learning

**MMD6020 — Fall 2022**  
**Project team:** Guillermo Martinez Villar, Azadeh Bayani, and Anni Wu

## Overview

This project investigates binary classification of epileptic seizure versus non-seizure EEG activity using machine-learning models. We analyzed **more than two million time-series samples** (over one million observations) represented by multichannel EEG voltage measurements, comparing several classifiers on the same dataset.

## Dataset and scientific background

**Dataset:** [CHB-MIT Scalp EEG Database (PhysioNet)](https://physionet.org/content/chbmit/1.0.0/)  
**CSV used in this project:** [Download from Google Drive](https://drive.google.com/file/d/1j--AJ7OEcRLngnt0h_fAlyCHo6sx_FNd/view?usp=drive_link)

The CHB-MIT database contains long-duration scalp electroencephalography (EEG) recordings from pediatric patients with epilepsy, including annotations of seizure onset and end times. The original recordings were sampled at **256 Hz**, allowing electrical activity to be followed over time across multiple scalp channels. Our classification inputs were the **EEG channel voltage values directly**.

Seizure detection from continuous EEG is challenging because seizure periods are relatively rare and EEG signals vary between patients. For background on the dataset and methodological issues in seizure detection, see Ali, Angelova, and Karmakar (2024), [*Epileptic seizure detection using CHB-MIT dataset: The overlooked perspectives*](https://doi.org/10.1098/rsos.230601).

## Methods

We compared **logistic regression, AdaBoost, random forests, and XGBoost** for seizure/non-seizure classification. The notebooks document model comparisons, selection of subsets of the original channel variables, hyperparameter tuning, and performance assessment using held-out observations.

## Main results

| Model | Held-out test ROC-AUC |
| --- | ---: |
| Logistic regression | 0.4990 |
| Random forest | 0.9675 |
| Tuned XGBoost | **0.9694** |

Tuned XGBoost also achieved **91.21% test accuracy** and **0.9120 macro F1-score**. Results are taken from saved notebook outputs, without rerunning the experiments.

## Repository contents

- `notebooks/Final version.ipynb` — Model comparison and evaluation.
- `notebooks/Final_xgb.ipynb` — XGBoost experiments and results.
- `notebooks/test_xgb.ipynb` — Additional XGBoost experiments.
- `requirements.txt` — Python dependencies.

## Running the notebooks

1. Install Python and Jupyter.
2. Install the dependencies:

   ```bash
   python -m pip install -r requirements.txt
   ```

3. [Download the CSV dataset from Google Drive](https://drive.google.com/file/d/1j--AJ7OEcRLngnt0h_fAlyCHo6sx_FNd/view?usp=drive_link).
4. Open the notebooks in Jupyter and update their local CSV file paths as necessary.

## References

- CHB-MIT Scalp EEG Database. PhysioNet, version 1.0.0. https://physionet.org/content/chbmit/1.0.0/
- Ali, E., Angelova, M., & Karmakar, C. (2024). *Epileptic seizure detection using CHB-MIT dataset: The overlooked perspectives*. **Royal Society Open Science, 11**, 230601. https://doi.org/10.1098/rsos.230601
