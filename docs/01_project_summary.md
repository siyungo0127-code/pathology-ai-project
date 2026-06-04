# Project Summary

## Project Title

Gene Expression-Based Cancer Subtype Classification and Transcriptomic Profiling

---

## Overview

This project explores machine learning and transcriptomic analysis approaches for cancer subtype identification using gene expression data.

The work consists of two complementary analyses:

1. Building a Random Forest classifier to predict Diffuse Large B-Cell Lymphoma (DLBCL) Cell-of-Origin (COO) subtypes.
2. Identifying molecular subtypes in Esophageal Squamous Cell Carcinoma (ESCC) using unsupervised clustering and pathway analysis.

---

## Objectives

### Part 1: Supervised Learning

Develop a Random Forest model capable of classifying DLBCL samples into Cell-of-Origin (COO) subtypes using gene expression profiles.

Key objectives:

* Train and optimize a Random Forest classifier
* Perform feature selection to identify informative genes
* Evaluate model performance using OOB error and ROC analysis
* Validate the model using an independent testing cohort

### Part 2: Unsupervised Learning

Identify biologically meaningful molecular subtypes within ESCC samples.

Key objectives:

* Discover latent sample groups using Non-negative Matrix Factorization (NMF)
* Compare clustering approaches using Consensus Clustering
* Identify subtype-specific differentially expressed genes (DEGs)
* Characterize biological pathways associated with each subtype using GSEA

---

## Dataset

Gene expression datasets from cancer cohorts:

* Diffuse Large B-Cell Lymphoma (DLBCL)
* Esophageal Squamous Cell Carcinoma (ESCC)

Expression matrices were used as input for both supervised and unsupervised analyses.

---

## Methods

### Machine Learning

* Random Forest Classification
* Hyperparameter Tuning
* Feature Selection
* ROC Curve Analysis
* Independent Cohort Validation

### Transcriptomic Analysis

* Non-negative Matrix Factorization (NMF)
* Consensus Clustering
* Differential Expression Analysis (limma)

### Functional Enrichment

* Gene Set Enrichment Analysis (GSEA)
* Pathway Interpretation using Gene Ontology (GO)

---

## Tools and Packages

### Programming Language

* R

### Major Packages

* randomForest
* caret
* pROC
* limma
* NMF
* clusterProfiler
* Biobase
* org.Hs.eg.db

---

## Key Outcomes

### DLBCL Classification

* Developed a Random Forest classifier for COO prediction
* Performed iterative feature selection to reduce dimensionality
* Evaluated predictive performance using ROC and OOB metrics
* Assessed model generalizability on an external validation cohort

### ESCC Subtyping

* Identified molecular subtypes using NMF clustering
* Compared clustering stability across different algorithms
* Discovered subtype-specific gene signatures
* Identified biological pathways associated with each subtype through GSEA

---

## Skills Demonstrated

### Bioinformatics

* Gene Expression Analysis
* Differential Expression Analysis
* Functional Enrichment Analysis
* Cancer Transcriptomics

### Machine Learning

* Supervised Classification
* Feature Selection
* Model Evaluation
* Hyperparameter Optimization

### Data Analysis

* Statistical Analysis
* Data Visualization
* Biological Interpretation of Results

### Research Skills

* Experimental Design
* Reproducible Analysis
* Scientific Reporting
