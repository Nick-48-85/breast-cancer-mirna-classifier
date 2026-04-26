# Breast Cancer Stage Classification with miRNA

This repository contains a reproducible, stage-wise pipeline for breast cancer
classification using microRNA (miRNA) expression data. The project compares
multiple feature-selection families and evaluates how well miRNA-only models
can distinguish normal tissue from breast cancer stages I–IV.

## Overview

- **Goal:**  
  Assess how effectively miRNA expression profiles, used in isolation, can distinguish breast cancer
  stages from normal tissue.

- **Main ideas:**
  - Use three feature-selection families:
    - Traditional (SFS, Variance Threshold, Chi-Squared, LASSO)
    - Deep Learning (FNN, DAE, 1D-CNN, LSTMSeq)
    - Clustering (K-Means, Spectral Clustering, Gaussian Mixture Model, Hierarchical)
  - Build stage-wise consensus miRNA panels (intersection + majority).
  - Train standard classifiers on these panels:
    Logistic Regression, SVM (linear kernel), Random Forest, K-Nearest Neighbors.

- **Labels:**  
  Binary problems per stage: **Normal vs Stage I/II/III/IV**.

---

## Data

- **Source:**  
  National Cancer Institute’s **Genomic Data Commons (GDC) portal**,  
  TCGA Breast Cancer (BRCA) cohort.

- **File:**  
  `breast_cancer.csv`

- **Content:**
  - Rows: patient samples (normal + tumor)
  - Columns:
    - 1,881 miRNA features (normalized as `reads_per_million_miRNA_mapped`)
    - `Label` column with stage codes:
      - `0` = Normal  
      - `1` = Stage I  
      - `2` = Stage II  
      - `3` = Stage III  
      - `4` = Stage IV  

---

## Requirements

Recommended environment (or similar):

- Python 3.10+
- numpy
- pandas
- scikit-learn
- tensorflow (for deep learning methods)
- matplotlib

Example installation:

```bash
pip install numpy pandas scikit-learn tensorflow matplotlib
```

---

## Usage

To reproduce the full pipeline and regenerate the results shown in the poster:

1. Make sure `breast_cancer.csv` is in the project root.
2. Open the notebooks in order and run all cells:

   1. `1_miRNA_Traditional_All_Methods.ipynb`  
   2. `2_miRNA_DeepLearning_All_Methods.ipynb`  
   3. `3_miRNA_Clustering_All_Methods.ipynb`  
   4. `4_stagewise_consensus.ipynb`  
   5. `5_stagewise_classification.ipynb`

3. Outputs (ranked miRNA lists, clustering selections, consensus panels,
   classification metrics, and plots) will be written to the corresponding
   output folders (e.g., `TeamsExports/`, `stagewise_consensus/`,
   `stagewise_classification/`).

Running the notebooks in this sequence regenerates the miRNA panels and
classification results used in the analysis and poster.

---

## Repository Structure

```text
.
├── breast_cancer.csv
│
├── 1_miRNA_Traditional_All_Methods.ipynb
├── 2_miRNA_DeepLearning_All_Methods.ipynb
├── 3_miRNA_Clustering_All_Methods.ipynb
├── 4_stagewise_consensus.ipynb
├── 5_stagewise_classification.ipynb
│
├── TeamsExports/                # Method-specific outputs (ranked lists, clusters, etc.)
│   ├── Traditional/
│   ├── DeepLearning/
│   └── Clustering/
│
├── stagewise_consensus/         # Consensus frequency tables and panels
└── stagewise_classification/    # Stage-wise classification results and plots
```

---

## Reproducibility

- Fixed random seeds are used where applicable.
- Preprocessing and splitting strategies are consistent across methods:
  - Stages I–III: 70/30 stratified train–test split.
  - Stage IV: stratified k-fold cross-validation (due to only 15 positives).
- Output filenames follow a consistent naming convention
  (family, method, stage, and top-k where applicable).

This structure is intended to make it straightforward for others to
rerun the notebooks and obtain the same miRNA panels and classification metrics.

---

## Contact

For questions about this codebase or the project, please contact:

- **Joshua Adegboyo** – jadegboyo2023@fau.edu  
- **Anika Baro Villa** – abarovilla2021@fau.edu  
- **Nicholas Campos** – ncampos2022@fau.edu  
- **Brehon Parker** – bparker2012@fau.edu
