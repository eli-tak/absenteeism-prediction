# Absenteeism Prediction

An educational machine learning project that classifies absence records by duration using logistic regression. The input data and all analysis are included in this repository.

## Project files

- `absenteeism_prediction.ipynb`: data preparation, modeling, evaluation, and model saving.
- `Absenteeism_data.csv`: input data used by the notebook.
- `requirements.txt`: Python packages used in the tested environment.

## Run the notebook

Use Python 3 and install the dependencies from the project directory:

```bash
pip install -r requirements.txt
jupyter notebook
```

Open `absenteeism_prediction.ipynb` and run the cells in order. The CSV must be in the same directory. Execution creates `models/absenteeism_pipeline.joblib`; the model expects the engineered columns described in the notebook, not raw CSV records. Only load model files from trusted sources.

## Method and results

The notebook reserves 20% of rows for testing, then calculates the absence-duration median from the training partition only. A duration above that threshold is class 1. For this split the threshold is 3 hours. A logistic regression pipeline is compared with a majority-class baseline and evaluated with cross-validation and a test set.

In the recorded execution, test accuracy was 78.57% (110 of 140 records); precision and recall for longer absences were approximately 0.75 and 0.72. Mean training cross-validation accuracy was 75.36%. These figures describe this particular split, not a guarantee of future performance. Cross-validation uses a threshold fixed from the whole training partition.

## Limitations

- Random row splitting can place records from the same employee in both partitions and does not evaluate future periods or unseen employees.
- The availability of the reason for absence depends on when predictions are made.
- The test set was inspected during development and is not a fresh independent evaluation.
- This educational model is not suitable for employee assessment or other consequential decisions.

## Data source

The source and license of the supplied CSV have not been verified. Confirm the dataset provenance and redistribution terms before publishing or reusing it.
