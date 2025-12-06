Personalized Risk-to-Timeline Modelling for Cervical Cancer Progression
Predicting CIN outcomes from clinical and population risk factors

Authors: Valeria Mudzindiko & Lusubilo Nyondo
Course: SAT 5141 – Clinical Decision Support & AI Modelling
Instructor: Prof. Guy Hembroff

📌 Project Overview

This project develops a machine-learning framework for predicting cervical intraepithelial neoplasia (CIN) using demographic, behavioural, and clinical diagnostic variables from the UCI Cervical Cancer Risk Factors dataset.

Unlike most studies that focus on simple disease vs. no-disease classification, this work forms the foundation for a Personalized Risk-to-Timeline (R-to-T) model, which aims to inform when a woman is likely to progress to CIN and require follow-up.

The project includes:

Data cleaning and preprocessing

Handling extreme class imbalance

Training and evaluating multiple ML models

Cross-validation for reliable minority-class metrics

Model explainability using SHAP

Recommendations for expanding the model into full risk-timeline prediction

(Content supported by: 

Cervical_Cancer_Risk_to_Timelin…

 

Personalized Risk-to-timeline m…

 

Progress_Report_1_Cervical_Canc…

 

Risk_to_Timeline CxCa Modeldvpt…

 

Cervical_Cancer_Risk_to_Timelin…

)

📂 Dataset

Source: UCI Cervical Cancer Risk Factors Dataset
Size: 858 records, 36 variables
Outcome Target: Dx:CIN (biopsy-confirmed CIN)

Dataset characteristics (from project documents):

Rich mixture of demographic, behavioral, and clinical screening tests

Only 9 CIN-positive cases (~1%) → extreme imbalance

Substantial missing data in several variables

No temporal information (cross-sectional snapshot)

Key variables include:

Diagnostic tests: Hinselmann, Schiller, Cytology, Biopsy

Risk factors: age, sexual history, smoking, contraceptive use, STDs, HPV history

(See dataset descriptions in: 

Cervical_Cancer_Risk_to_Timelin…

 

Progress_Report_1_Cervical_Canc…

)

🔧 Methods & Pipeline
1. Data Preprocessing

Steps implemented:

Converted "?" to NaN

Dropped variables with >90% missingness

Median imputation for numerical fields

Removal of duplicate rows

Conversion of object-type numeric values

Standardization for models requiring scaled input

(Details in: 

Progress_Report_1_Cervical_Canc…

 

Risk_to_Timeline CxCa Modeldvpt…

)

2. Handling Class Imbalance

Because CIN-positive samples were extremely rare (only 9/858):

SMOTE applied to training data → increased CIN+ to ~10%

Class weights computed and passed into applicable algorithms

Strict stratified 80/20 split to maintain class proportions in testing

3. Machine Learning Models

Multiple baseline and advanced algorithms were trained, including:

KNN

Gaussian Naive Bayes

Decision Tree

MLP Neural Network

SVM: Linear, RBF, and Sigmoid

Gradient Boosting (regularized)

Easy Ensemble (imbalance-focused)

4. Evaluation Strategy

Two evaluation approaches:

A. Initial Stratified 80/20 Train–Test

Produced artificially high accuracy due to only 2 CIN+ samples in test set

Not reliable for minority-class modelling

B. 3-Fold Stratified Cross-Validation

Performed on original dataset (no SMOTE)

Provided stable estimates of Precision, Recall, F1 for CIN+

Revealed true model behavior under imbalance

🏆 Key Results
⭐ Best Model: Linear SVM

Across cross-validation, Linear SVM showed:

Metric (CIN+)	Score
Precision	0.917
Recall	1.00
F1-Score	0.952

Reasons it was chosen:

Best balance of sensitivity & precision

Stable performance across folds

Clinically meaningful alignment with known risk factors

Highly interpretable with SHAP

🧠 Explainability (SHAP Analysis)

SHAP KernelExplainer was used on the Linear SVM model to:

Rank global feature importance

Provide local patient-level explanations

Top contributing features:

HPV positivity

Abnormal diagnostic tests (Hinselmann, Schiller, Cytology, Biopsy)

Behavioural risk factors (smoking, STD history)

📉 Limitations

Current dataset limitations:

Extremely small CIN+ sample size

No longitudinal or temporal data

Missingness and inconsistency in raw entries

Oversampling (SMOTE) cannot replace real clinical diversity

