# EEG Seizure Detection Using Machine Learning

Machine-learning project for epileptic seizure classification using multichannel EEG data, developed for the MMD6020 course.

## Dataset

[CHB-MIT Scalp EEG Database — PhysioNet](https://physionet.org/content/chbmit/1.0.0/)

## Methods

The project compares logistic regression, AdaBoost, random forests, and XGBoost, with feature selection and hyperparameter tuning. The original analysis and saved results are preserved in the notebooks.

## Main results

| Model | Held-out test ROC-AUC |
| --- | ---: |
| Logistic regression | 0.4990 |
| Random forest | 0.9675 |
| Tuned XGBoost | **0.9694** |

The tuned XGBoost model also achieved **91.21% test accuracy** and **0.9120 macro F1-score**. These numbers are taken from the saved notebook outputs, not from a fresh run.

**Evaluation limitation:** The original evaluation used a random stratified row-level train/test split. Correlated EEG observations may make these results optimistic for new patients or independent recording sessions. Patient-independent generalization was not evaluated.

## Repository contents

- `notebooks/Final version.ipynb` — Original analysis and comparison of classification models.
- `notebooks/Final_xgb.ipynb` — XGBoost modeling and evaluation.
- `notebooks/test_xgb.ipynb` — Additional XGBoost experiments.
- `requirements.txt` — Python packages imported by the notebooks.

## Running the notebooks

1. Install Python and Jupyter Notebook or JupyterLab.
2. Install the dependencies from the repository root:

   ```bash
   python -m pip install -r requirements.txt
   ```

3. Access the dataset using the PhysioNet link above.
4. Open the notebooks in Jupyter. Adjust local file paths and any environment-specific settings as needed.


The notebooks are published with their original modeling methods and saved outputs. **End-to-end reproducibility has not been verified**; package versions are not pinned to the original environment.
