[README_4.md](https://github.com/user-attachments/files/27214001/README_4.md)
# 🧬 Breast Cancer Stage Classifier via miRNA Expression

> FAU CS Senior Capstone — Group 44 | Spring 2026

An end-to-end ML pipeline for classifying breast cancer stages using miRNA expression data from The Cancer Genome Atlas (TCGA). The project benchmarks three feature selection strategies paired with an SVM classifier to identify the most diagnostically informative miRNA biomarkers across 1,209 patient samples.

---

## 📋 Overview

Breast cancer stage classification from genomic data is a high-dimensional problem — the raw TCGA miRNA dataset contains hundreds of features per patient. This project explores whether intelligent feature selection can narrow that down to a compact, predictive biomarker set without sacrificing classification accuracy.

**Key result:** ~67.9% average classification accuracy across all approaches, with Chi-squared feature selection performing most consistently.

---

## 🔬 Methods

### Feature Selection Approaches
| Method | Description |
|---|---|
| **Chi-Squared** | Statistical test to rank miRNA features by their dependence on cancer stage labels |
| **1D-CNN** | Convolutional neural network used to learn feature importance from sequential miRNA expression profiles |
| **Hierarchical Clustering** | Unsupervised grouping of miRNAs by expression similarity; representative features selected per cluster |

### Classifier
- **Support Vector Machine (SVM)** — trained on the reduced feature sets produced by each selection method
- Multi-class classification across breast cancer stages (I, II, III, IV)

---

## 📊 Dataset

- **Source:** [The Cancer Genome Atlas (TCGA)](https://www.cancer.gov/tcga) via GDC Data Portal
- **Samples:** 1,209 breast cancer patients
- **Features:** miRNA expression profiles (raw counts, normalized)
- **Labels:** Pathological cancer stage

---

## 📁 Repository Structure

```
breast-cancer-mirna-classifier/
├── Deliverables/          # Final reports, presentation slides, ethics essay
├── Progress Reports/      # Weekly task reports and milestone updates
└── .gitignore
```

> Notebooks and source code available upon request / in progress of being uploaded.

---

## 📈 Results Summary

| Feature Selection | Classifier | Avg. Accuracy |
|---|---|---|
| Chi-Squared | SVM | ~67.9% |
| 1D-CNN | SVM | ~67.9% |
| Hierarchical Clustering | SVM | ~67.9% |

Detailed confusion matrices, per-class precision/recall, and cross-validation breakdowns are available in the Deliverables folder.

---

## 🛠️ Tech Stack

- **Python** — pandas, NumPy, scikit-learn, TensorFlow/Keras
- **Feature Selection** — scipy (Chi-squared), custom 1D-CNN, scipy/sklearn (Hierarchical Clustering)
- **Classifier** — scikit-learn SVM (`sklearn.svm.SVC`)
- **Visualization** — matplotlib, seaborn

---

## 👥 Team

**Group 44** — Florida Atlantic University, Department of Computer Science & Engineering

- Nicholas Campos

---

## 📄 License

Academic project — Florida Atlantic University, Spring 2026. Not intended for clinical use.
