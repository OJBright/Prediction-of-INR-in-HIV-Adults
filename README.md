# Predicting Immunological Non-Response to ART in HIV-Positive 
Adults in Sub-Saharan Africa

## Overview
This repository contains the code, analysis, and results for a 
machine learning study predicting immunological non-response (INR) 
to antiretroviral therapy (ART) among HIV-positive adults in 
Nigeria. The study introduces an exhaustion-informed feature 
engineering framework — constructing clinical surrogates of T-cell 
exhaustion from routine health records — and evaluates four 
supervised classification algorithms with full SHAP explainability 
analysis.

**Course:** Machine Learning in Biomedicine  
**Institution:** Makerere University, Kampala, Uganda  
**Author:** Jerome Bright Ogenrwot  

---

## Research Question
Can routine clinical data from HIV-positive adults on ART in 
Sub-Saharan Africa be used to predict immunological non-response 
using exhaustion-informed machine learning features?

---

## Dataset
**Nigeria Quality of Care HIV Dataset**
- 27,288 HIV-positive patients on ART
- Multiple healthcare facilities across Nigeria, 2006–2018
- Key variables: CD4 counts, viral load, ART regimen, adherence, 
  WHO clinical stage, demographics

> The dataset is not included in this repository due to data 
sharing agreements. To request access, contact the original 
data custodians.

---

## Outcome Definition
Immunological Non-Response (INR) was defined as failure to achieve 
CD4 ≥ 200 cells/µL at most recent follow-up among patients who 
initiated ART with baseline CD4 < 200 cells/µL.

- Total eligible patients: 6,720
- Non-Responders (INR=1): 3,085 (45.9%)
- Responders (INR=0): 3,635 (54.1%)

---

## Features Engineered
12 exhaustion-informed clinical features were constructed:

| Feature | Description |
|---------|-------------|
| BaselineCD4 | CD4 count at ART initiation |
| TreatmentDelayDays | Days from HIV diagnosis to ART start |
| AdvancedDisease | WHO stage III or IV at baseline |
| AdherenceScore | ART adherence level (ordinal) |
| ArtInterruptionBinary | History of ART interruption |
| ArtSwitchBinary | History of ART regimen switch |
| FunctionalStatusScore | Functional status at ART start |
| Age | Patient age |
| SexBinary | Biological sex |
| FacilityLevelScore | Healthcare facility level |
| OpportunisticInfection | Opportunistic infection at last visit |
| WeightAtStart | Body weight at ART initiation |

---

## Models
- Logistic Regression (baseline)
- Random Forest
- XGBoost
- Neural Network (MLP)

---

## Results Summary

| Model | AUC-ROC | F1 | Precision | Recall |
|-------|---------|-----|-----------|--------|
| Logistic Regression | **0.603** | **0.548** | 0.547 | **0.549** |
| Neural Network (MLP) | 0.595 | 0.502 | 0.534 | 0.473 |
| Random Forest | 0.579 | 0.502 | 0.528 | 0.478 |
| XGBoost | 0.556 | 0.491 | 0.509 | 0.475 |

**Best model:** Logistic Regression (AUC-ROC = 0.603)

**Top SHAP predictors:** SexBinary, BaselineCD4, Age, WeightAtStart

---

## Repository Structure
