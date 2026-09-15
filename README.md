# COVID-19 In-Hospital Mortality Prediction

## Overview
This project aims to predict in-hospital mortality in patients with COVID-19 using admission clinical variables and chest X-ray images.

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
  - Jupyter notebooks used for patient splitting, preprocessing, model training, evaluation, late fusion, and Grad-CAM visualization

- `manuscript/`
  - Final manuscript draft including the study methods, results, tables, figures, discussion, and conclusions

- `presentation/`
  - Final revised presentation slides used for project evaluation

## Analysis Workflow
The overall analysis workflow consisted of the following steps:

1. Creation of fixed patient-level training, validation, and test splits
2. Chest X-ray preprocessing and quality checking
3. Development of the chest X-ray dataset and data loader
4. Training of the ResNet18 chest X-ray model
5. Final test-set evaluation of the chest X-ray model
6. Grad-CAM visualization
7. Clinical variable preprocessing and modeling using logistic regression
8. Construction and validation of the late fusion model
9. Comparison of the final prediction models

## Models

### Clinical Model
A logistic regression model was developed using selected admission clinical variables.

### Chest X-ray Model
A ResNet18 model was trained using frontal chest X-ray images obtained around the time of hospital admission.

### Late Fusion Model
The final multimodal model combined predicted probabilities from the clinical and chest X-ray models.

## Model Evaluation
Model performance was assessed using:
- ROC-AUC
- PR-AUC
- Brier score
- Expected Calibration Error (ECE)

Grad-CAM was also used to visualize image regions contributing to chest X-ray model predictions.

## Presentation
The `presentation/` folder contains the final revised presentation slides summarizing:
- Study background and objectives
- Dataset and cohort selection
- Clinical and imaging model development
- Late fusion strategy
- Model performance
- Grad-CAM results
- Study limitations
- Future improvements

## Limitations
The main limitations of this study include:
- Single-center dataset
- Limited number of mortality events
- No external validation
- Use of a single frontal chest X-ray per patient
- Potential dataset-specific bias
- Limited generalizability to other institutions or patient populations

## Next Improvements
Future work should include:
- External validation using independent datasets
- Evaluation in larger and more diverse patient populations
- Comparison with additional machine-learning and deep-learning models
- Further improvement of model calibration
- Development of more advanced multimodal fusion methods
- Assessment of clinical usefulness and potential implementation in real-world settings

## Data Availability
The original patient-level clinical data and chest X-ray images are not distributed in this repository.

Users interested in reproducing the analysis should obtain the source dataset through the appropriate official data access process.

## Notes
This repository is intended for academic and educational purposes.

The repository contains analysis notebooks, manuscript materials, and presentation materials, but does not contain identifiable patient information or original medical images.
