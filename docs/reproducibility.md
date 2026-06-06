# Reproducibility

This document describes what is currently needed to reproduce the analyses in
this repository. It is written for recruiters, collaborators, and future users
who want to understand what can be rerun, what evidence is available, and what
information is still missing.

The information below is based only on the repository notebooks, reports,
documentation, and current local checkout. Package versions, dataset sources,
and accessions are not invented where they are not documented.

## Current Reproducibility Status

The repository contains analysis notebooks, summary documentation, generated
figures, HTML reports, and a structured `data/` directory. Notebook input paths
now use project-relative locations under `data/`.

The DLBCL cohort 2 file, ESCC expression matrix, and supplementary CNN image
inputs are present under `data/`. The DLBCL cohort 1 external validation files
are intentionally not tracked in GitHub because of file size and/or data
redistribution constraints.

## Required R Packages

The transcriptomics R Markdown notebook
`notebooks/01_dlbcl_escc_transcriptomics_analysis.Rmd` uses the following R
packages:

| Package | Evidence in repository | Purpose |
| --- | --- | --- |
| `Biobase` | Loaded with `library(Biobase)` | Read and manipulate Bioconductor expression objects; extract expression matrices with `exprs()`; combine validation objects. |
| `randomForest` | Loaded with `library(randomForest)` | Train Random Forest classifiers for DLBCL Cell-of-Origin prediction. |
| `caret` | Loaded with `library(caret)` | Generate confusion matrices and performance metrics. |
| `pROC` | Loaded with `library(pROC)` | Calculate and plot ROC curves. |
| `tidyverse` | Loaded with `library(tidyverse)` | Data wrangling, including feature importance sorting and data frame handling. |
| `NMF` | Loaded with `library(NMF)` | Perform Non-negative Matrix Factorization and NMF rank selection for ESCC subtyping. |
| `limma` | Loaded with `library(limma)` | Differential expression analysis for ESCC clusters. |
| `BiocManager` | Installed in notebook with `install.packages("BiocManager")` | Install Bioconductor packages. |
| `clusterProfiler` | Installed with `BiocManager::install("clusterProfiler")` and loaded with `library(clusterProfiler)` | Gene Set Enrichment Analysis. |
| `org.Hs.eg.db` | Installed with `BiocManager::install("org.Hs.eg.db")` and loaded with `library(org.Hs.eg.db)` | Human gene annotation database for enrichment analysis. |
| `enrichplot` | Installed with `BiocManager::install("enrichplot")` | Enrichment plotting support. The notebook installs it but does not clearly show a `library(enrichplot)` call. |
| `DOSE` | Installed with `BiocManager::install("DOSE")` | Dependency/support package for enrichment analysis. The notebook installs it but does not clearly show a `library(DOSE)` call. |
| `ConsensusClusterPlus` | Installed with `BiocManager::install("ConsensusClusterPlus")` and loaded with `library(ConsensusClusterPlus)` | Consensus clustering comparison for ESCC subtypes. |

Package versions are unknown because the repository does not include an R
session info block, `renv.lock`, `DESCRIPTION`, or other R environment lockfile.

## Required Python Packages

The supplementary CNN notebook
`notebooks/02_cnn_image_classification.ipynb` uses the following Python packages:

| Package | Evidence in repository | Purpose |
| --- | --- | --- |
| `opencv-python` / `cv2` | Installed with `pip install opencv-python`; imported as `cv2 as cv` | Read source images and process image tiles. |
| `Pillow` / `PIL` | `from PIL import Image` | Save image tiles. |
| `numpy` | `import numpy as np` | Array operations for image processing. |
| `pandas` | Installed with `pip install pandas`; imported as `pd` | Build data frames containing tile paths and labels. |
| `scikit-learn` | Installed with `pip install scikit-learn`; imports `train_test_split` | Split tile data into train and test sets. |
| `tensorflow` | Installed with `pip install tensorflow`; imports from `tensorflow.keras` | Build, train, and evaluate CNN models. |
| `keras` | Used through `tensorflow.keras` | Model architecture, layers, optimizer, and image data generators. |

The notebook output contains package versions from one previous Windows
environment for some packages, but the repository does not provide a formal
`requirements.txt`, `environment.yml`, or Python lockfile. Required package
versions should therefore be treated as unknown.

## Software Tools Identified

| Tool | Role | Version status |
| --- | --- | --- |
| R | Runs the transcriptomics R Markdown analysis. | Unknown. |
| R Markdown / `rmarkdown` | R notebook/report workflow. | Unknown. |
| Bioconductor | Provides `Biobase`, `limma`, `clusterProfiler`, `org.Hs.eg.db`, `ConsensusClusterPlus`, and related packages. | Unknown. |
| Python | Runs the supplementary CNN notebook. | Unknown. |
| Jupyter Notebook / JupyterLab | Runs `notebooks/02_cnn_image_classification.ipynb`. | Unknown. |
| pip | Installs Python packages inside the CNN notebook. | Unknown. |
| TensorFlow/Keras | CNN model training. | Versions not formally specified. |
| Git/GitHub | Repository version control and portfolio hosting. | Unknown. |

## Expected Input Data Files

The expected input data files are documented in more detail in
`docs/data_sources.md`.

### Transcriptomics Inputs

| Analysis | Expected project-relative path | Included in current checkout? |
| --- | --- | --- |
| DLBCL training/internal testing | `data/dlbcl/cohort_2/DLBCL.cohort.2.rds` | Yes |
| DLBCL external validation | `data/dlbcl/cohort_1/DLBCL.eSet.1.rds` | No. Local-only/manual placement. |
| DLBCL external validation | `data/dlbcl/cohort_1/DLBCL.eSet.2.rds` | No. Local-only/manual placement. |
| DLBCL external validation | `data/dlbcl/cohort_1/DLBCL.eSet.3.rds` | No. Local-only/manual placement. |
| DLBCL external validation | `data/dlbcl/cohort_1/DLBCL.eSet.4.rds` | No. Local-only/manual placement. |
| ESCC molecular subtyping | `data/escc/exp_data_ESCC_90samples.txt` | Yes |

### CNN Image Inputs

| Expected project-relative path | Included in current checkout? |
| --- | --- |
| `data/images/A1.jpg` | Yes |
| `data/images/A2.jpg` | Yes |
| `data/images/B1.jpg` | Yes |
| `data/images/B2.jpg` | Yes |
| `data/images/C1.jpg` | Yes |
| `data/images/C2.jpg` | Yes |
| `data/images/D1.jpg` | Yes |
| `data/images/D2.jpg` | Yes |

## Recommended Directory Structure

```text
bioinformatics-ml-portfolio/
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
    dlbcl_external_validation_roc.png
    escc_nmf_rank_selection.png
    escc_nmf_consensus_map.png
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

The DLBCL cohort 1 `.rds` files should not be committed to GitHub. Authorized
users should manually place them in `data/dlbcl/cohort_1/` before rerunning the
external validation section.

## How to Run the Analyses

These instructions describe the intended workflow after missing input data and
software environments have been supplied.

### 1. Transcriptomics Analysis

1. Install R and the required CRAN/Bioconductor packages listed above.
2. Place `DLBCL.cohort.2.rds` in `data/dlbcl/cohort_2/`.
3. Place `exp_data_ESCC_90samples.txt` in `data/escc/`.
4. If rerunning external validation, place the four authorized local DLBCL cohort
   1 files in `data/dlbcl/cohort_1/`.
5. Open `notebooks/01_dlbcl_escc_transcriptomics_analysis.Rmd` in RStudio or
   another R Markdown-capable environment.
6. Run or knit the notebook.

### 2. Supplementary CNN Image Classification

1. Install Python and the required packages listed above.
2. Place `A1.jpg` to `D2.jpg` in `data/images/`.
3. Open `notebooks/02_cnn_image_classification.ipynb` in Jupyter.
4. Run the notebook.

## Parts Currently Not Reproducible

The following parts are not currently reproducible from a fresh clone:

* DLBCL external validation, because the cohort 1 `.rds` files are intentionally
  excluded from GitHub and must be manually supplied by authorized users.
* Exact package recreation, because no R or Python lockfile is included.
* One-command execution, because there is no script, Makefile, workflow manager,
  or pipeline entry point.

## Git LFS Recommendation

Git LFS is not recommended for the DLBCL cohort 1 external validation files
unless redistribution permission has been confirmed. For this portfolio
repository, documenting the files and requiring authorized manual placement is
safer and clearer than making large binary biological data part of the GitHub
download path.

## Known Limitations

* Dataset provenance is incomplete.
* DLBCL cohort 2, ESCC, and CNN image inputs are present, but their source
  metadata are incomplete.
* Dataset accession numbers, publications, licenses, and redistribution terms
  are unknown.
* The DLBCL cohort 1 external validation files are local-only because of file
  size and/or data redistribution constraints.
* Package versions are not pinned.
* The transcriptomics workflow installs some packages inside the notebook, which
  makes reruns slower and less controlled.
* The CNN notebook installs packages inside notebook cells instead of relying on
  a documented environment file.
* Random seeds are used in some places, but not consistently across all
  stochastic operations. For example, the CNN train/test split does not specify a
  `random_state`.
* The CNN component is supplementary, and the biological meaning of the image
  labels is unclear from the repository.
* No automated tests or validation checks are included.

## Future Reproducibility Improvements

1. Add complete dataset provenance, including source databases, accession
   numbers, publications, download URLs, processing steps, licenses, and access
   restrictions.
2. Add permitted input files to the structured `data/` folders, or provide exact
   manual download/reconstruction instructions where redistribution is not
   allowed.
3. Add `renv.lock` for R and `requirements.txt` or `environment.yml` for Python.
4. Move package installation out of notebooks and into setup documentation.
5. Add a runnable pipeline entry point with scripts, a Makefile, Snakemake, or
   Nextflow.
6. Save generated tables, model metrics, and figures under a consistent
   `outputs/` or `results/` directory.
7. Add `sessionInfo()` for R and `pip freeze` or `conda env export` for Python.

## Practical Reproducibility Assessment

Current reproducibility score: 7 out of 10.

The project now has clearer data organization, relative notebook paths, included
core/supplementary input files, and documentation for local-only external
validation files. It is still not fully reproducible because cohort 1 external
validation requires manual authorized data placement, dataset provenance is
incomplete, and package environments are not pinned.
