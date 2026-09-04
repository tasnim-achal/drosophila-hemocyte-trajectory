# Single-Cell Transcriptional Analysis of Cocaine Response in *Drosophila melanogaster*

This repository contains the computational workflow, custom analysis scripts, and peer review documentation for analyzing single-cell RNA sequencing (scRNA-seq) data of adult *Drosophila melanogaster* brains following acute cocaine exposure.

---

## 📊 Project Overview

This project investigates cell-type-specific transcriptional responses and sex-specific differences across **86,224 single brain cells** in response to psychostimulants.

* **Cell Populations Identified:** 36 distinct clusters representing major neuronal, glial, and neurotransmitter-specific lineages.
* **Primary Affected Cell Types:** Kenyon cells of the mushroom body (C11, C20) and surface glia/astrocytes (C22, C17).
* **Key Findings:** Pronounced sexual dimorphism, with males showing a higher number and magnitude of differentially expressed genes (DEGs) compared to females.

---

## 📈 Quantitative Summary

| Metric / Parameter | Male Flies | Female Flies | Combined / Total |
| :--- | :--- | :--- | :--- |
| **Analyzed Cells** | — | — | 86,224 cells |
| **Identified Clusters** | — | — | 36 clusters |
| **DEGs ($\vert{}log_2\text{FC}\vert{} > 1.0$)** | 133 DEGs | 54 DEGs | 187 DEGs |
| **Top Affected Cell Types** | Surface Glia, Kenyon Cells | Surface Glia, Astrocytes | Glia (C22, C17), MB (C11, C20) |

---

## 📁 Repository Structure

```text
├── data/
│   ├── raw/                 # Raw count matrices (GEO: GSE152495)
│   └── processed/           # Processed Seurat / Scanpy h5ad objects
├── scripts/
│   ├── 01_preprocessing.R   # Quality control, normalization (sctransform)
│   ├── 02_clustering.py     # Graph-based clustering (resolution 0.8)
│   ├── 03_deg_analysis.R    # Differential expression across sex & drug conditions
│   └── 04_pathway_go.R      # Gene Ontology & pathway enrichment analyses
├── docs/
│   ├── peer_review_report.md # Formal peer review analysis & feedback
│   └── reading_guide.md     # Primary paper evaluation & answers
├── figures/                 # UMAP plots, heatmaps, and DEG dotplots
├── requirements.txt         # Python dependencies
└── README.md                # Project documentation

