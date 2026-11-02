# Employee Absenteeism Prediction

An educational machine learning project that classifies absence
records as **3 hours or less** or **more than 3 hours**, using
logistic regression.

The notebook covers data preprocessing, model training,
cross-validation, baseline comparison, and pipeline persistence.

## Project Overview

The dataset used in this notebook contains 700 absence records.

The target classes are:

- **Class 0:** Absenteeism time of 3 hours or less.
- **Class 1:** Absenteeism time of more than 3 hours.

The 3-hour threshold was derived from the dataset's median.
This is a classification task, not a prediction of the exact
number of absence hours.

## Workflow

1. Inspect the dataset and check for missing values.
2. Group absence reasons into four categories.
3. Extract month and day of the week from dates.
4. Encode education as a binary feature.
5. Define the target and remove absence hours from the input features.
6. Create a stratified 80/20 training–test split.
7. Standardize non-binary features using training data only.
8. Train a logistic regression classifier.
9. Evaluate accuracy, precision, recall, and F1-score.
10. Perform five-fold stratified cross-validation with a pipeline.
11. Compare performance against a majority-class baseline.
12. Save the fitted pipeline and verify predictions after reloading.

## Results

| Metric | Result |
|---|---:|
| Training accuracy | 76.96% |
| Test accuracy | 75.71% |
| Mean cross-validation accuracy | 74.29% |
| Cross-validation accuracy standard deviation | 4.01 percentage points |
| Mean cross-validation F1 for class 1 | 0.702 |
| Majority-class baseline CV accuracy | Approximately 54.5% |

Cross-validation was performed on the training set only.

### Test Confusion Matrix

Rows represent actual classes; columns represent predicted classes.

| Actual / Predicted | 3 hours or less | More than 3 hours |
|---|---:|---:|
| 3 hours or less | 57 | 19 |
| More than 3 hours | 15 | 49 |

The model correctly classified 106 of 140 test records.

For absences longer than 3 hours, test precision was approximately
0.72 and recall was approximately 0.77.

## Tools

- Python
- pandas
- NumPy
- scikit-learn
- joblib
- Jupyter Notebook

## Repository Contents

- `absenteeism_prediction.ipynb` — preprocessing, modeling,
  evaluation, and model-saving workflow.
- `README.md` — project overview and execution instructions.
- `.gitignore` — exclusions for local and generated files.

## Data Availability

The notebook expects a file named `Absenteeism_data.csv` in
the same directory as the notebook.

The CSV is not currently included in this repository.
Dataset source attribution and redistribution permissions
are pending verification.

The notebook cannot be fully executed without the expected
input dataset. A different dataset version may require changes
to preprocessing and may produce different results.

## Running the Notebook

1. Download or clone this repository.
2. Obtain the expected dataset from an authorized source and place
   `Absenteeism_data.csv` beside the notebook.
3. In a Python environment, install the required packages:
```bash
   pip install pandas numpy scikit-learn joblib notebook
   
