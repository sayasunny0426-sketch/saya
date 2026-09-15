# COVID-19 In-Hospital Mortality Prediction

## Overview
This project aims to predict in-hospital mortality in patients with COVID-19 using clinical information and chest radiographs obtained around the time of hospital admission.

The study compares:
- A chest X-ray model using ResNet18
- Clinical models using Logistic Regression, XGBoost, and a Multilayer Perceptron
- A Late Fusion model combining Clinical Logistic Regression and CXR ResNet18 predictions

The main objective was to evaluate whether chest X-ray information provides additional predictive value beyond clinical information alone.

## Dataset
The analysis was performed using the Stony Brook University COVID-19 Positive Cases (COVID-19-NY-SBU) dataset.

A total of 1,277 patients with an eligible frontal chest radiograph obtained from 2 days before the prediction time point through the same calendar date were included in the final analysis.

The fixed dataset split consisted of:
- Training set: 1,021 patients
- Validation set: 128 patients
- Test set: 128 patients

The original patient-level clinical data and chest X-ray images are not included in this repository.

## Repository Structure

- `notebook/`
  - Jupyter notebooks used for data preparation, patient splitting, chest X-ray preprocessing, model development, evaluation, Late Fusion, and Grad-CAM visualization

- `manuscript/`
  - Final manuscript including study methods, results, tables, figures, discussion, limitations, and conclusions

- `presentation/`
  - Final revised presentation slides used for project evaluation

- `limitations_and_next_improvements.md`
  - Summary of the major study limitations and proposed directions for future improvement

## Analysis Workflow

1. Creation of fixed patient-level Training, Validation, and Test sets
2. Chest X-ray eligibility assessment and preprocessing
3. Development and training of the ResNet18 CXR model
4. Clinical variable selection and preprocessing
5. Development of Logistic Regression, XGBoost, and MLP clinical models
6. Construction of the Late Fusion model
7. Evaluation on the fixed Test set
8. Comparison of predictive performance across models
9. Grad-CAM visualization and permutation importance analysis

## Models

### Chest X-ray Model
The CXR-only model used ResNet18 pretrained on ImageNet-1K and was fine-tuned using the selected frontal chest radiograph for each patient.

### Clinical Models
Three clinical models were evaluated:
- Logistic Regression
- XGBoost
- Multilayer Perceptron

The final clinical models used the same selected clinical features.

### Late Fusion Model
Late Fusion combined predicted probabilities from Clinical Logistic Regression and CXR ResNet18.

The final fusion weights were:
- Clinical Logistic Regression: 0.72
- CXR ResNet18: 0.28

## Model Evaluation
Performance was evaluated using:
- ROC-AUC
- PR-AUC
- Brier score
- Expected Calibration Error (ECE)

Paired DeLong tests with Holm correction were used for ROC-AUC comparisons.

Grad-CAM was used to visualize image regions contributing to CXR model predictions.

## Main Results
In the final Test set:
- CXR ResNet18 ROC-AUC: 0.907
- Clinical Logistic Regression ROC-AUC: 0.941
- Clinical XGBoost ROC-AUC: 0.936
- Clinical MLP ROC-AUC: 0.880
- Late Fusion ROC-AUC: 0.944

Although Late Fusion had the highest point estimate of ROC-AUC, the improvement over Clinical Logistic Regression was small and not statistically significant.

Clinical Logistic Regression also showed better PR-AUC, Brier score, and ECE than Late Fusion.

Modality-level permutation importance suggested that Late Fusion relied predominantly on clinical information, while CXR provided complementary prognostic information.

## Limitations
Major study limitations included:
- Single-center retrospective design
- Lack of external validation
- Limited number of mortality events in the Test set
- Missing sex information in a subset of patients
- Uncertain temporal relationship between admission and CXR acquisition on the same calendar date
- Unavailable exact measurement timestamps for individual clinical variables

Additional details are provided in `limitations_and_next_improvements.md`.

## Next Improvements
Future work should include:
- External validation using independent datasets
- Evaluation in larger and more diverse patient populations
- More precise temporal alignment of clinical and imaging predictors
- Further evaluation of multimodal fusion approaches
- Assessment of clinical utility in real-world decision-making
- Prospective and multicenter validation

## Data Availability
The original COVID-19-NY-SBU dataset is publicly available through The Cancer Imaging Archive (TCIA).

Original patient-level clinical data and chest X-ray images are not redistributed in this repository.

## Notes
This repository was prepared as the final portfolio for the COVID-19 mortality prediction project.

It contains analysis notebooks, the final manuscript, presentation materials, and a summary of study limitations and future improvements.
