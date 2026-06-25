# 💊 Drug-Target Interaction Prediction using Machine Learning

> Predicting drug-protein binding interactions using molecular descriptors and ensemble ML — enabling **computational drug discovery** with **91%+ accuracy**

---

## 📌 Overview

This project builds a **computational drug discovery pipeline** to predict whether a drug molecule will bind to a target protein. Using physicochemical molecular descriptors (inspired by ChEMBL database), the pipeline applies Lipinski's Rule of Five, ADMET property analysis, chemical space visualization, and multiple ML models to rank drug candidates.

**Domain:** Cheminformatics / Computational Pharmacology  
**Dataset:** ChEMBL-style molecular descriptor dataset (1,500 drug-target pairs)  
**Target Proteins:** EGFR, VEGFR, BRAF, CDK2, HER2, BCL2, HDAC, PIK3CA, KRAS, TP53  
**Drug Classes:** Kinase Inhibitors, Protease Inhibitors, GPCR Modulators, Ion Channel Blockers, Nuclear Receptor Ligands

---

## 🎯 Key Results

| Model | CV Accuracy | Test Accuracy | AUC-ROC | Avg Precision |
|---|---|---|---|---|
| **Random Forest** | **91.5%** | **91.0%** | **0.972** | **0.968** |
| Gradient Boosting | 90.8% | 90.3% | 0.967 | 0.963 |
| SVM (RBF) | 89.7% | 89.3% | 0.959 | 0.955 |
| Logistic Regression | 85.1% | 84.7% | 0.924 | 0.918 |
| Naive Bayes | 78.4% | 77.9% | 0.871 | 0.862 |

> ✅ Best Model: **Random Forest** — AUC-ROC = **0.972**

---

## 🔬 Biological Context

### Lipinski's Rule of Five (Ro5)
Drug-likeness was evaluated using standard pharmaceutical criteria:
- **Molecular Weight** ≤ 500 Da
- **LogP** ≤ 5 (lipophilicity)
- **H-Bond Donors** ≤ 5
- **H-Bond Acceptors** ≤ 10

### Key Molecular Descriptors for Binding Prediction
Top features identified by Random Forest:
- **log_affinity** — log-transformed binding affinity (nM) — strongest predictor
- **admet_score** — composite ADMET property score
- **drug_efficiency** — selectivity × bioavailability
- **selectivity_score** — target specificity index
- **bioavailability** — oral absorption potential

### ADMET Properties Analyzed
Absorption, Distribution, Metabolism, Excretion, Toxicity indicators including solubility, permeability, half-life, and clearance rate.

---

## 📊 Visualizations

| Figure | Description |
|---|---|
| `01_lipinski_analysis.png` | Ro5 property distributions + violations pie chart |
| `02_eda_analysis.png` | Interaction rates by target, drug class, binding affinity |
| `03_correlation_heatmap.png` | Pearson correlation of all molecular descriptors |
| `04_pca_chemical_space.png` | Chemical space visualization (active vs inactive) |
| `05_model_performance.png` | ROC + Precision-Recall curves + confusion matrix |
| `06_feature_importance.png` | Top 15 molecular descriptors by Random Forest |

---

## 🗂️ Project Structure

```
drug-target-interaction/
│
├── notebooks/
│   └── drug_target_interaction.ipynb     # Full analysis notebook
│
├── src/
│   └── analysis.py                        # Standalone Python script
│
├── data/
│   └── drug_target_interaction.csv        # Generated on first run
│
├── figures/                               # Generated plots
├── results/
│   ├── model_comparison.csv               # Model metrics
│   └── top_drug_candidates.csv            # Top 20 ranked compounds
│
├── requirements.txt
└── README.md
```

---

## ⚙️ How to Run

```bash
git clone https://github.com/yourusername/drug-target-interaction.git
cd drug-target-interaction

pip install -r requirements.txt

# Option 1: Jupyter Notebook
jupyter notebook notebooks/drug_target_interaction.ipynb

# Option 2: Python Script
python src/analysis.py
```

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3.10 |
| ML | scikit-learn (RF, GBM, SVM, LR, NB) |
| Data | NumPy, Pandas |
| Visualization | Matplotlib, Seaborn |
| Dimensionality Reduction | PCA |
| Drug-likeness | Lipinski Ro5 (custom implementation) |
| Evaluation | AUC-ROC, Precision-Recall, 5-fold CV |

---

## 📚 Methods

1. **Data Generation** — 1,500 ChEMBL-inspired drug-target pairs with 16 molecular descriptors
2. **Lipinski Ro5** — Drug-likeness filtering with violation scoring
3. **Feature Engineering** — log_affinity, admet_score, drug_efficiency, mw_logP_ratio, hbd_hba_ratio
4. **Chemical Space PCA** — 3-component visualization of active vs inactive chemical space
5. **Model Training** — 5 ML algorithms with stratified 5-fold cross-validation
6. **Evaluation** — AUC-ROC, Precision-Recall curves, confusion matrix, classification report
7. **Drug Prioritization** — Composite scoring to rank top 20 drug candidates

---

## 💡 Applications

- **Virtual screening** — rapid filtering of large compound libraries
- **Lead optimization** — identifying key molecular properties for binding
- **Target selectivity** — comparing interaction probabilities across proteins
- **Drug repurposing** — finding new targets for existing compounds

---

## 👤 Author

**Mayank Vaishnav**  
M.Sc. Bioinformatics — Graphic Era University, Dehradun  
📧 Mayankva8619@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/your-profile)

---

## 📄 License

MIT License — free to use and adapt with attribution.
