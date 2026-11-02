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

- `Absenteeism_data.csv` — course-provided dataset used by the notebook.
- `absenteeism_prediction.ipynb` — preprocessing, modeling,
  evaluation, and model-saving workflow.
- `README.md` — project overview and execution instructions.
- `.gitignore` — exclusions for local and generated files.
- `requirements.txt` — pinned dependencies for running the notebook.

The notebook saves the fitted pipeline to
`models/absenteeism_pipeline.joblib` when the model-saving cells
are executed.

## Data Source and Modifications

This repository includes `Absenteeism_data.csv`, a course-provided
educational adaptation of the Absenteeism at Work dataset.

### Original Source

Martiniano, A., & Ferreira, R. (2012).
Absenteeism at Work. UCI Machine Learning Repository.
https://doi.org/10.24432/C5X882

The original UCI dataset is licensed under
[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

### Course Version

It contains 700 records and 12 columns. Its 11 non-date columns
match the corresponding values in the first 700 records of the
original UCI dataset. Some original columns were omitted and
some column names were changed.

The course version also includes a `Date` column that is not present
in the original UCI CSV. These dates should not be interpreted as
the original observation dates. Calendar features derived from
them are used for educational purposes.

The UCI license statement above refers to the original dataset;
a separate redistribution license for the course-specific
modifications has not been verified.

## Limitations

- This is an educational project, not a production-ready tool
  for evaluating employees or making employment decisions.
- The target threshold was derived from the full dataset's median
  before the training–test split, rather than being set independently.
- Random row-based splitting does not establish performance on
  previously unseen employees or future time periods. Records from
  the same employee may appear in both training and validation data.
- The course-provided dates are not verified original observation
  dates, which limits the interpretation of calendar features.
- The reason for absence may not be available at the time a real-world
  prediction would need to be made.
- Model coefficients describe associations, not causal effects.
- The saved pipeline expects engineered features. It does not perform
  all preprocessing directly from the raw CSV.

## Running the Notebook

Tested with Python 3.13.9.

1. Download or clone this repository.
2. Ensure that `Absenteeism_data.csv` is in the same directory as
   `absenteeism_prediction.ipynb`.
3. Open a terminal in the repository directory and install the
   required packages using this command:

   `pip install -r requirements.txt`

4. Start Jupyter Notebook using this command:

   `jupyter notebook`

5. Open `absenteeism_prediction.ipynb` and run the cells in order.

**Note:** The original UCI CSV has a different structure and cannot
directly replace the included file without preprocessing changes.
`  
