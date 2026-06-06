# Cancer Transcriptomics and Machine Learning Portfolio

This repository presents an MSc bioinformatics portfolio project focused on cancer transcriptomics, molecular subtyping, and interpretable machine learning. The main work combines supervised classification of Diffuse Large B-Cell Lymphoma (DLBCL) Cell-of-Origin subtypes with unsupervised molecular subtype discovery in Esophageal Squamous Cell Carcinoma (ESCC).

The strongest result is a Random Forest model for DLBCL ABC vs GCB classification that maintained strong performance on an external validation cohort, achieving 0.8283 accuracy, 0.8458 balanced accuracy, and an AUC of approximately 0.88-0.90. A second major analysis identified four ESCC molecular subtypes from 90 transcriptomic samples using NMF, followed by differential expression and pathway-level interpretation.

This is a learning-focused MSc portfolio project, not clinical software. The goal is to demonstrate practical bioinformatics analysis, model validation, biological interpretation, and clear scientific communication using cancer gene expression data.

---

## Project Workflow

```text
Gene Expression Data
        ↓
Random Forest Classification (DLBCL)
        ↓
External Validation

Gene Expression Data
        ↓
NMF Clustering (ESCC)
        ↓
Differential Expression
        ↓
GSEA Pathway Analysis
        ↓
Biological Interpretation
```

---

## Highlights

* Built and externally validated a Random Forest classifier for DLBCL ABC vs GCB Cell-of-Origin classification.
* Achieved external validation performance of 0.8283 accuracy, 0.8458 balanced accuracy, and approximately 0.88-0.90 AUC.
* Identified four molecular subtypes in 90 ESCC samples using Non-negative Matrix Factorization (NMF) on the top 1500 MAD genes.
* Interpreted ESCC subtype biology using limma differential expression analysis and GSEA pathway analysis.
* Included a CNN image classification notebook as an optional supplementary machine learning exercise, with biological label interpretation treated cautiously.

---

## Main Analyses

| Analysis | Dataset / Task | Method | Main Result | Interpretation |
| --- | --- | --- | --- | --- |
| DLBCL Cell-of-Origin classification | ABC vs GCB classification from gene expression profiles | Random Forest with external validation | External validation accuracy 0.8283, balanced accuracy 0.8458, AUC approximately 0.88-0.90 | Demonstrates supervised transcriptomic classification with independent cohort validation |
| ESCC molecular subtyping | 90 ESCC transcriptomic samples | NMF using top 1500 MAD genes | Four molecular subtypes identified | Subtypes were interpreted using limma differential expression and GSEA pathway analysis |
| Supplementary CNN exercise | Image classification notebook | Convolutional Neural Network | Exploratory model-building exercise | Included for machine learning practice; biological label meaning is unclear and not treated as a main biological result |

---

## Project Overview

### 1. DLBCL Cell-of-Origin Classification

The DLBCL analysis focuses on classifying ABC vs GCB Cell-of-Origin subtypes from gene expression data. A Random Forest classifier was trained and evaluated with particular attention to external validation, which is the key strength of this component.

Main workflow:

* Training and testing cohort split
* Random Forest model development
* Hyperparameter tuning
* Feature selection
* ROC curve and AUC evaluation
* Independent external cohort validation

Verified external validation results:

* Accuracy: 0.8283
* Balanced accuracy: 0.8458
* AUC: approximately 0.88-0.90

![DLBCL external validation ROC](figures/dlbcl_external_validation_roc.png)

*External validation ROC curve showing DLBCL classifier performance on an independent cohort.*

### 2. ESCC Molecular Subtyping

The ESCC analysis uses unsupervised transcriptomic profiling to identify molecular structure across 90 Esophageal Squamous Cell Carcinoma samples. NMF was applied using the top 1500 genes ranked by median absolute deviation (MAD), identifying four molecular subtypes.

Main workflow:

* Selection of the top 1500 MAD genes
* Non-negative Matrix Factorization (NMF)
* Consensus clustering assessment
* Four-subtype molecular classification
* Differential expression analysis with limma
* Gene Set Enrichment Analysis (GSEA)
* Biological interpretation of subtype-associated pathways

![ESCC NMF rank selection](figures/escc_nmf_rank_selection.png)

*NMF rank-selection metrics used to identify stable ESCC subtype structure.*

![ESCC NMF consensus map](figures/escc_nmf_consensus_map.png)

*NMF consensus map showing four transcriptomic ESCC subtypes.*

### 3. Supplementary CNN Image Classification

The CNN notebook is included as an additional machine learning exercise. It demonstrates basic image classification workflow development, but it is not positioned as a primary biological result because the biological meaning of the image labels is unclear.

---

## Skills Demonstrated

### Bioinformatics

* Cancer transcriptomics
* Gene expression analysis
* Molecular subtype discovery
* Differential expression analysis with limma
* Functional enrichment and pathway interpretation
* Independent validation of transcriptomic classifiers

### Machine Learning and Statistics

* Random Forest classification
* Feature selection
* Hyperparameter optimization
* ROC/AUC evaluation
* Balanced accuracy assessment
* Unsupervised clustering with NMF
* Exploratory CNN image classification

### Programming and Reproducibility

* R and R Markdown
* Bioconductor workflows
* Python notebook-based machine learning
* Data visualization
* Reproducible reporting

---

## Tools and Packages

* randomForest
* caret
* pROC
* limma
* NMF
* clusterProfiler
* Biobase
* org.Hs.eg.db

---

## Repository Structure

```text
README.md

docs/
  01_project_summary.md
  02_code_walkthrough.md
  data_sources.md
  reproducibility.md

notebooks/
  01_dlbcl_escc_transcriptomics_analysis.Rmd
  02_cnn_image_classification.ipynb

reports/
  dlbcl_escc_transcriptomics_report.html.zip
  cnn_image_classification_report.html

figures/

data/
  dlbcl/
    cohort_2/
      DLBCL.cohort.2.rds
    cohort_1/
      README.md
  escc/
    exp_data_ESCC_90samples.txt
  images/
    A1.jpg
    A2.jpg
    B1.jpg
    B2.jpg
    C1.jpg
    C2.jpg
    D1.jpg
    D2.jpg
```

The structured `data/` paths above are the locations used by the notebooks. The
DLBCL cohort 2 file, ESCC expression matrix, and supplementary CNN image inputs
are included in this repository under `data/`.

The DLBCL cohort 1 external validation `.rds` files are not tracked in GitHub
because of file size and/or data redistribution constraints. To rerun the
external validation section, authorized users should manually place
`DLBCL.eSet.1.rds`, `DLBCL.eSet.2.rds`, `DLBCL.eSet.3.rds`, and
`DLBCL.eSet.4.rds` in `data/dlbcl/cohort_1/`.

Git LFS is not recommended for these external validation files unless
redistribution permission has been confirmed.

---

## Limitations

* This repository is an MSc portfolio project and should not be interpreted as a clinically validated diagnostic tool.
* The DLBCL classifier shows promising external validation performance, but further validation across larger, prospectively collected, and platform-diverse cohorts would be required for clinical translation.
* The ESCC subtypes are transcriptomic patterns discovered from 90 samples; their biological and clinical relevance would need confirmation in independent cohorts.
* Pathway interpretations are hypothesis-generating and depend on the quality of differential expression results, gene set annotations, and enrichment methodology.
* The CNN image classification component is supplementary because the biological meaning of the labels is unclear.

---

## Key Learning Outcomes

Through this project, I gained experience in:

* Building predictive models from high-dimensional gene expression datasets
* Evaluating machine learning models using independent validation datasets
* Identifying molecular subtypes from cancer transcriptomic data
* Performing differential expression and pathway enrichment analysis
* Communicating computational biology results in a concise, portfolio-ready format

---

## Future Improvements

* Refactor analyses into modular and reusable scripts
* Add clearer environment and dependency documentation
* Build reproducible bioinformatics workflows
* Containerize analyses using Docker
* Implement workflow management systems such as Nextflow
* Extend validation to additional independent transcriptomic cohorts

---

## Repository Notes

* This is an MSc portfolio project.
* Some data files may not be included due to access, licensing, file size, or redistribution constraints.
* The DLBCL cohort 1 external validation files are documented but intentionally excluded from GitHub.
* The repository prioritizes clear scientific communication and reproducible analysis documentation.
