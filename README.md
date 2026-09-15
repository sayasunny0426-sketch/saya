# COVID-19 In-Hospital Mortality Prediction

## Overview
This project predicts in-hospital mortality in patients with COVID-19 using admission clinical variables and chest X-ray images.

The project includes:
- Clinical prediction using logistic regression
- Chest X-ray prediction using ResNet18
- Late fusion of clinical and imaging models
- Model evaluation using ROC-AUC, PR-AUC, Brier score, and calibration metrics
- Grad-CAM visualization for chest X-ray interpretation

## Dataset
The analysis was performed using the Stony Brook COVID-19 dataset.

The original patient-level data and chest X-ray images are not included in this repository.

## Repository Structure

- `notebook/`
  - Jupyter notebooks used for data preparation, model training, evaluation, and visualization

- `manuscript/`
  - Final manuscript draft including results tables and figures

## Main Analysis
Patients were divided into fixed training, validation, and test sets.

The clinical model was developed using logistic regression, while the chest X-ray model used ResNet18.

A late fusion model combined the clinical and imaging prediction probabilities.

## Limitations
The main limitations of this study include:
- Single-center dataset
- Limited number of mortality events
- No external validation
- Use of a single frontal chest X-ray per patient
- Potential dataset-specific bias

## Next Improvements
Future work should include:
- External validation using independent datasets
- Evaluation in larger and more diverse patient populations
- Comparison with additional machine-learning and deep-learning models
- Improvement of model calibration
- Further development of multimodal fusion methods

## Notes
This repository is intended for academic and educational purposes.
Patient-level source data and medical images are not distributed in this repository.
