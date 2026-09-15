# Limitations and Next Improvements

## Limitations

This study has several limitations.

1. **Single-center retrospective design and lack of external validation**  
   This study was conducted using a single-center retrospective dataset. Model performance may vary across institutions because of differences in patient characteristics, clinical practice, imaging conditions, and laboratory workflows. Therefore, the generalizability of the models to other centers and populations remains uncertain.

2. **Missing sex information**  
   Sex information was missing for a subset of patients. In the Training set, missing sex was strongly associated with in-hospital mortality. To avoid allowing the model to exploit the missingness mechanism directly, missing sex values were imputed with male, the mode in the Training set. However, this does not recover the true sex of those patients and introduces residual uncertainty.

3. **Small final Test set and limited number of mortality events**  
   The final Test set included 128 patients, with only 17 in-hospital deaths. Therefore, estimates of model performance, calibration, and between-model differences remain uncertain.

4. **Uncertain temporal relationship between CXR acquisition and admission**  
   The prediction time point was defined as `visit_start_datetime`. However, for chest radiographs obtained on the same calendar date as admission, it was not possible to determine whether the CXR was acquired before or after the exact admission time.

5. **Unavailable measurement timestamps for clinical variables**  
   Exact timestamps for individual laboratory values and vital signs were not available. Therefore, it could not be confirmed that all clinical variables were measured within a fixed interval relative to the prediction time point.

6. **Limited incremental value of multimodal fusion**  
   Although the Late Fusion model achieved the highest point estimate of ROC-AUC, the improvement over Clinical Logistic Regression was small and not statistically significant. Therefore, the additional value of incorporating CXR information should not be overstated.

## Next Improvements

Future work should focus on the following areas:

1. **External validation**  
   The models should be evaluated using independent datasets from other institutions and populations to assess reproducibility and generalizability.

2. **Larger evaluation cohorts**  
   Validation in larger datasets with more mortality events is needed to obtain more precise estimates of discrimination, calibration, and between-model differences.

3. **Improved temporal alignment of predictors**  
   Future datasets should include exact timestamps for chest radiographs, laboratory measurements, and vital signs so that all predictors can be aligned more precisely to the intended prediction time point.

4. **Further evaluation of multimodal integration**  
   More advanced multimodal fusion approaches should be explored to determine whether imaging information can provide additional predictive value beyond clinical variables alone.

5. **Assessment of clinical utility**  
   Future studies should evaluate whether the use of CXR-derived information meaningfully improves clinical decision-making, risk stratification, or patient management in real-world settings.

6. **Prospective and multicenter evaluation**  
   Prospective and multicenter studies will be important to determine whether the findings are robust across different clinical environments and patient populations.
