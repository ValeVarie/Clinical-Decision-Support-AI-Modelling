# Personalized Risk-to-Timeline Modelling for Cervical Cancer Progression
Predicting CIN outcomes from clinical and population risk factors  
**Authors:** Valeria Mudzindiko & Lusubilo Nyondo  
**Course:** SAT 5141 – Clinical Decision Support & AI Modelling  
**Instructor:** Prof. Guy Hembroff  

## 📌 Project Overview
This project develops a machine-learning foundation for predicting cervical intraepithelial neoplasia (CIN) using demographic, behavioural, and clinical diagnostic variables from the UCI Cervical Cancer Risk Factors dataset.  
It also builds the groundwork for a future Risk-to-Timeline (R-to-T) model that aims to estimate personalized disease progression timelines.

## 📂 Dataset
- **Source:** UCI Cervical Cancer Risk Factors Dataset  
- **Size:** 858 records, 36 variables  
- **Target:** Dx:CIN (biopsy-confirmed CIN)  
- Contains demographic data, sexual/reproductive history, STD history, smoking, contraceptive use, and diagnostic test results (Hinselmann, Schiller, Cytology, Biopsy).

## 🔧 Methods & Pipeline
### 1. Data Preprocessing
- Converted “?” to NaN  
- Removed features with >90% missing values  
- Median imputation  
- Duplicate removal  
- Numeric coercion and standardization

### 2. Handling Class Imbalance
- Extreme imbalance: only **9 CIN+ cases (~1%)**  
- Applied **SMOTE** to training data to increase minority representation  
- Used **class weighting** during model training  
- Applied **stratified 80/20 split**

### 3. Machine Learning Models Evaluated
- KNN  
- Gaussian NB  
- Decision Tree  
- MLP  
- SVM (Linear, RBF, Sigmoid)  
- Gradient Boosting  
- Easy Ensemble  

### 4. Evaluation Approach
- Initial 80/20 split → unstable because only 2 CIN+ cases in test set  
- **3-Fold Stratified Cross-Validation** used for reliable minority-class evaluation  
- Metrics: Precision, Recall, F1-score, Accuracy  

## 🏆 Key Results
### ⭐ Best Model: Linear SVM
- **Precision:** 0.917  
- **Recall:** 1.00  
- **F1-score:** 0.952  
- Most stable across folds and best at detecting CIN+ cases  
- Aligns well with clinical expectations

## 🧠 Explainability (SHAP)
- Used KernelExplainer for global and local interpretability  
- Key features influencing CIN prediction:
  - HPV status  
  - Abnormal diagnostic tests (Hinselmann, Schiller, Cytology, Biopsy)  
  - Smoking and STD history  

## 📉 Dataset Limitations
- Only 9 CIN-positive samples  
- No temporal data  
- Missingness in several features  
- SMOTE cannot replace real clinical variation  

## 🚀 Future Work
- Collect longitudinal dataset with follow-up timelines  
- Apply survival models (Cox PH, AFT, Survival GBM)  
- Use calibrated probability outputs  
- Build a clinical decision-support dashboard  
- External validation across real-world cohorts  
