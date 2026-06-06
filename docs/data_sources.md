# Data Sources

This page records the datasets referenced by the analyses in this repository.
It is based only on information present in the repository notebooks, reports,
documentation, and the current local checkout. Missing source metadata are
marked explicitly.

## Current Repository Data Status

The repository now uses a structured `data/` layout. In the current local
checkout, the DLBCL cohort 2 file, ESCC expression matrix, and supplementary CNN
image inputs are present under `data/`. The DLBCL cohort 1 external validation
files are documented but intentionally not tracked.

| Analysis | Expected file path | Purpose | Included in current checkout? | Source/accession/publication |
| --- | --- | --- | --- | --- |
| DLBCL Cell-of-Origin classification | `data/dlbcl/cohort_2/DLBCL.cohort.2.rds` | Main DLBCL gene expression dataset used for ABC vs GCB Cell-of-Origin model training and internal testing. | Yes | Not identified in the repository. |
| DLBCL external validation | `data/dlbcl/cohort_1/DLBCL.eSet.1.rds` | External validation input for the DLBCL Random Forest classifier. | No. Documented only. | Not identified in the repository. |
| DLBCL external validation | `data/dlbcl/cohort_1/DLBCL.eSet.2.rds` | External validation input for the DLBCL Random Forest classifier. | No. Documented only. | Not identified in the repository. |
| DLBCL external validation | `data/dlbcl/cohort_1/DLBCL.eSet.3.rds` | External validation input for the DLBCL Random Forest classifier. | No. Documented only. | Not identified in the repository. |
| DLBCL external validation | `data/dlbcl/cohort_1/DLBCL.eSet.4.rds` | External validation input for the DLBCL Random Forest classifier. | No. Documented only. | Not identified in the repository. |
| ESCC molecular subtyping | `data/escc/exp_data_ESCC_90samples.txt` | ESCC expression matrix used for NMF, consensus clustering, differential expression analysis, and GSEA. | Yes | Not identified in the repository. |
| Supplementary CNN exercise | `data/images/A1.jpg` to `data/images/D2.jpg` | Image inputs for the supplementary CNN image classification notebook. | Yes | Not identified in the repository. |

## DLBCL Datasets Used

The DLBCL analysis uses gene expression data with Cell-of-Origin labels for ABC
vs GCB classification.

### `data/dlbcl/cohort_2/DLBCL.cohort.2.rds`

* File format inferred from code: R serialized object loaded with `readRDS()`.
* Object type inferred from code: Bioconductor expression object compatible with
  `Biobase::exprs()` and phenotype fields such as `COO`.
* Project purpose: training and internal testing for the DLBCL Cell-of-Origin
  Random Forest classifier.
* Repository status: included at this project-relative path.
* Source/accession/publication: missing from repository documentation.

### `data/dlbcl/cohort_1/DLBCL.eSet.1.rds` to `DLBCL.eSet.4.rds`

* File format inferred from code: R serialized objects loaded with `readRDS()`.
* Object type inferred from code: Bioconductor expression objects compatible with
  `Biobase::combine()`, `Biobase::exprs()`, and phenotype fields such as `COO`.
* Project purpose: external validation of the DLBCL Cell-of-Origin Random Forest
  classifier.
* Repository status: not tracked in GitHub. The files are intentionally excluded
  because of file size and/or data redistribution constraints.
* Manual placement for authorized users:

```text
data/dlbcl/cohort_1/DLBCL.eSet.1.rds
data/dlbcl/cohort_1/DLBCL.eSet.2.rds
data/dlbcl/cohort_1/DLBCL.eSet.3.rds
data/dlbcl/cohort_1/DLBCL.eSet.4.rds
```

* Source/accession/publication: missing from repository documentation.
* Git LFS note: Git LFS is not recommended for these files unless redistribution
  permission has been confirmed.

## ESCC Dataset Used

### `data/escc/exp_data_ESCC_90samples.txt`

* File format inferred from code: tabular text file loaded with `read.table()`
  using `header = TRUE` and `row.names = 1`.
* Project purpose: ESCC molecular subtyping by NMF and consensus clustering,
  followed by differential expression analysis and pathway interpretation.
* Repository status: included at this project-relative path.
* Source/accession/publication: missing from repository documentation.

## Supplementary CNN Image Inputs

The CNN notebook expects these project-relative image paths:

```text
data/images/A1.jpg
data/images/A2.jpg
data/images/B1.jpg
data/images/B2.jpg
data/images/C1.jpg
data/images/C2.jpg
data/images/D1.jpg
data/images/D2.jpg
```

These files are included at the project-relative paths above. Their biological
meaning, source, license, and accession information are unknown from the
repository.

## Information Still Missing

The repository does not currently identify:

* Original public database source for the DLBCL datasets.
* Original public database source for the ESCC dataset.
* GEO, SRA, ArrayExpress, TCGA, or other accession numbers.
* Publication titles, journal citations, DOIs, or PMID references.
* Whether the datasets were downloaded directly, processed from raw public data,
  or supplied as teaching/practical materials.
* Dataset-specific licensing, redistribution, or access restrictions.
* Exact redistribution status for the CNN image inputs.
