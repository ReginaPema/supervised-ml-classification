# <img src="https://img.icons8.com/?size=50&id=80592&format=png&color=000000" align="center"/> Supervised Machine Learning: Classification
### Aprendizaje Supervisado: Clasificación

> **EN** · Five notebooks covering the core supervised classification algorithms applied to two real-world datasets: employee attrition (HR, 14,999 records) and drug prescription (medical, 200 patients). Each notebook follows the full Machine Learning workflow: preprocessing, training, evaluation with multiple metrics, and interpretation; allowing direct comparison across algorithms on the same data.
>
> **ES** · Cinco notebooks que cubren los algoritmos de clasificación supervisada aplicados a dos datasets reales: rotación de empleados (RRHH, 14,999 registros)y prescripción de medicamentos (médico, 200 pacientes). Cada notebook sigue el flujo completo de Machine Learning: preprocesamiento, entrenamiento, evaluación con múltiples métricas e interpretación; permitiendo comparación directa entre algoritmos sobre los mismos datos.

---

## <img src="https://img.icons8.com/?size=40&id=80454&format=png&color=000000" align="center"/> Notebooks

### 01 · KNN: Employee Attrition Prediction
**Dataset:** `recursos_humanos.csv` | 14,999 employees × 9 features  
**Target:** `left` (0=stayed, 1=left) | Class imbalance: 76.2% / 23.8%

- Applied KNN to predict employee turnover on a moderately imbalanced dataset
- Selected optimal k by evaluating Accuracy and F1 across k=1 to k=20
- Evaluated with Precision, Recall, F1, AUC-ROC and Confusion Matrix
- Analyzed impact of class imbalance on model selection criteria

---

### 02 · SVM: Employee Attrition Prediction
**Dataset:** `recursos_humanos.csv` | 14,999 employees | Same target as notebook 01

- Compared all four SVM kernels: Linear, Polynomial, RBF (Gaussian), Sigmoid
- Full evaluation per kernel: Accuracy, Precision, Recall, F1, AUC-ROC
- Selected optimal kernel with executive summary and ROC curve comparison
- Applied to same dataset as KNN → direct algorithm comparison possible

---

### 03 · Decision Tree: Drug Prescription (5 classes)
**Dataset:** `drugs.csv` | 200 patients × 5 features  
**Target:** drug type: drugA, drugB, drugC, drugX, drugY

- Trained 12 models: 6 depth levels × 2 criteria (GINI, Entropy)
- **Finding:** GINI and Entropy produced identical results at all depths
- **Best model:** depth=4 · Accuracy=98.33% (most parsimonious that achieves maximum)
- Predicted drug for new patient: Age=50, Sex=F, BP=HIGH, Cholesterol=NORMAL, Na/K=15.3

---

### 04 · Ensemble Methods: Drug Prescription (5 classes)
**Dataset:** `drugs.csv` | 200 patients | Same target as notebook 03  
**Baseline:** Decision Tree from notebook 03 (Accuracy=98.33%)

- Compared Random Forest (n_estimators: 10, 50, 100, 200), Gradient Boosting and AdaBoost
- **Finding:** RF matches DT at ≥100 trees. GB peaks at 96.67%; below the DT baseline
- **Conclusion:** The added complexity of ensemble methods was not justified here; parsimony wins
- Validated with 5-fold cross-validation across all configurations

---

### 05 · Logistic Regression: Drug Origin Binary Classification
**Dataset:** `drugs.csv` | 200 patients  
**Target (reformulated):** Nacional (0: drugA/B/C) vs Extranjero (1: drugX/Y)

- Reformulated 5-class problem as binary classification by drug origin
- Evaluated 12 configurations: 5 solvers (lbfgs, liblinear, saga, sag, newton-cg) × L1/L2/ElasticNet
- **Best model:** lbfgs | L2 | C=10 → AUC-ROC=1.0000, Accuracy=0.9833, CV F1=0.9650
- Perfect classification of 17/17 national and 42/43 foreign patients

---

## <img src="https://img.icons8.com/?size=40&id=V7bWlRbkNWas&format=png&color=000000" align="center"/> Algorithm Comparison / Comparación de Algoritmos

| Algorithm | Dataset | Best Accuracy | Key Metric |
|---|---|---|---|
| KNN | HR (14,999) | — | F1 on minority class |
| SVM | HR (14,999) | — | AUC-ROC per kernel |
| Decision Tree | Drugs (200) | 98.33% | depth=4, GINI |
| Random Forest | Drugs (200) | 98.33% | n_estimators≥100 |
| Gradient Boosting | Drugs (200) | 96.67% | below DT baseline |
| Logistic Regression | Drugs (200) | 98.33% | AUC-ROC=1.00 |

> Notebooks 01–02 use the same HR dataset → direct KNN vs SVM comparison.  
> Notebooks 03–05 use the same drugs dataset → DT vs Ensemble vs LogReg comparison.

---

## <img src="https://img.icons8.com/?size=40&id=80431&format=png&color=000000" align="center"/> Tools / Herramientas

![Python](https://img.shields.io/badge/Python-8B9E8B?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-6B7F6B?style=flat&logo=pandas&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-B8A9C9?style=flat&logo=scikit-learn&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=flat)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat)
![Jupyter](https://img.shields.io/badge/Jupyter-C4A882?style=flat&logo=jupyter&logoColor=white)

---

### <img src="https://img.icons8.com/?size=40&id=sM98nozehZSG&format=png&color=000000" align="center"/> Data Sources / Fuentes de Datos

| File | Rows | Features | Source |
|---|---|---|---|
| `recursos_humanos.csv` | 14,999 | 9 | HR dataset: employee attrition |
| `drugs.csv` | 200 | 5 | Medical dataset: drug prescription |

---

## <img src="https://img.icons8.com/?size=40&id=80358&format=png&color=000000" align="center"/> Related Projects / Proyectos Relacionados

| Project | Description |
|---|---|
| [unsupervised-ml-clustering](https://github.com/ReginaPema/unsupervised-ml-clustering) | Hierarchical Clustering · K-Means · PCA · Market Basket |
| [kmeans-vanish-segmentation](https://github.com/ReginaPema/kmeans-vanish-segmentation) | K-Means on 28,377 real retail transactions |

---

## <img src="https://img.icons8.com/?size=40&id=PhymLYNNjf3I&format=png&color=000000" align="center"/> Repository Structure / Estructura

```
supervised-ml-classification/
├── notebook/
│   ├── 01_knn_employee_attrition.ipynb
│   ├── 02_svm_employee_attrition.ipynb
│   ├── 03_decision_tree_drug_prescription.ipynb
│   ├── 04_ensemble_drug_prescription.ipynb
│   └── 05_logistic_regression_drug_origin.ipynb
├── data/
│   ├── recursos_humanos.csv     ← used by notebooks 01 & 02
│   └── drugs.csv                ← used by notebooks 03, 04 & 05
└── README.md
```

---

*Project developed as part of the Data Scientist Certificate · 
Proyecto desarrollado como parte del certificado Científico de Datos — EBAC (2026)* <img src="https://img.icons8.com/?size=35&id=FgMs84V9yrMV&format=png&color=000000" align="center"/>
