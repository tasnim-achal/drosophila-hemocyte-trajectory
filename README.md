# Single-Cell Transcriptional Analysis of Cocaine Response in *Drosophila melanogaster*

This repository contains the single-cell RNA-sequencing (scRNA-seq) computational workflow, custom analysis scripts, and peer review documentation for investigating cell-type-specific transcriptional responses and sex-specific differences in adult *Drosophila melanogaster* brains following acute cocaine exposure[cite: 1].

---

## 🧬 Project Overview

### Scientific Question
Psychostimulants like cocaine induce complex behavioral and physiological alterations, but how these responses are distributed across specific brain cell types and biological sexes remains incompletely understood[cite: 1]. 

This project explores the cell-type-specific transcriptional remodeling triggered by acute cocaine ingestion in *Drosophila melanogaster* and evaluates how pre-existing or drug-induced transcriptional differences vary between male and female flies[cite: 1].

### Key Computational Highlights
* **Dataset Scale:** Single-cell transcriptomic profiles of **86,224 single brain cells** across cocaine-treated and control flies[cite: 1].
* **Cell Populations Identified:** **36 distinct clusters** representing major neuronal, glial, and neurochemical cell lineages[cite: 1].
* **Primary Affected Cell Types:** Kenyon cells of the mushroom body (C11, C20) and glial sub-populations, particularly surface glia (C22) and astrocytes (C17)[cite: 1].
* **Sexual Dimorphism:** Male flies show a substantially higher count and magnitude of differentially expressed genes (DEGs) post-exposure compared to females[cite: 1].

---

## 📊 Key Findings

| Metric / Parameter | Male Flies | Female Flies | Combined / Total |
| :--- | :--- | :--- | :--- |
| **Analyzed Cells** | — | — | 86,224 cells[cite: 1] |
| **Identified Clusters** | — | — | 36 clusters[cite: 1] |
| **DEGs ($\vert{}log_2\text{FC}\vert{} > 1.0$)** | 133 DEGs[cite: 1] | 54 DEGs[cite: 1] | 187 DEGs[cite: 1] |
| **Top Affected Cell Types** | Surface Glia, Kenyon Cells[cite: 1] | Surface Glia, Astrocytes[cite: 1] | Glia (C22, C17), MB (C11, C20)[cite: 1] |

* **Cell-Type Specificity:** Transcriptional response to acute cocaine exposure is highly localized, concentrated primarily in mushroom body Kenyon cells and specific glial sub-types[cite: 1].
* **Sex-Specific Response:** Male flies exhibit a significantly greater transcriptomic response (133 DEGs) compared to females (54 DEGs) under identical drug exposure conditions[cite: 1].
* **Behavioral Correlation:** Transcriptional shifts in memory and support centers align with observed behavioral deficits in geotaxis and motor startle responses[cite: 1].

---

## 🔄 Analysis Workflow

```text
Raw 10x Genomics / GEO Data (GSE152495)
       │
       ▼
01. Quality Control & Filtering
       │ (Filter doublets, low-quality cells, and low-expression genes)
       ▼
02. Normalization & Feature Selection
       │ (sctransform normalization, selection of highly variable genes)
       ▼
03. Dimensionality Reduction & Clustering
       │ (PCA, SNN graph construction, UMAP, Leiden/Seurat clustering res=0.8)
       ▼
04. Cell-Type Annotation & Marker Analysis
       │ (Canonical marker annotation: Kenyon cells, Glia, Monoaminergic neurons)
       ▼
05. Differential Expression & Sexual Dimorphism Analysis
       │ (Male vs. Female DEG comparisons across cocaine vs. control conditions)

```

---

## 📁 Repository Structure

```text
drosophila-cocaine-scrnaseq/
├── data/
│   ├── raw/                 # Raw count matrices (GEO Accession: GSE152495)[cite: 1]
│   └── processed/           # Processed Seurat / Scanpy h5ad objects
├── scripts/
│   ├── 01_preprocessing.R   # Quality control & normalization (sctransform)[cite: 1]
│   ├── 02_clustering.py     # SNN graph clustering (resolution 0.8)[cite: 1]
│   ├── 03_deg_analysis.R    # Differential expression across sex & drug conditions[cite: 1]
│   └── 04_pathway_go.R      # Gene Ontology & pathway enrichment analyses[cite: 1]
├── docs/
│   ├── peer_review_report.md # Comprehensive peer review analysis & evaluation[cite: 1]
│   └── reading_guide.md     # Primary paper evaluation & answers[cite: 1]
├── figures/                 # UMAP plots, heatmaps, and DEG dotplots
├── requirements.txt         # Python dependencies
├── LICENSE
└── README.md

```

---

## 🚀 Quickstart Guide (using `uv`)

### 1. Prerequisites

Ensure you have **Git**, **Python 3.10+**, and **`uv`** installed.

```bash
git --version
python --version
uv --version

```

If `uv` is not installed, install it via terminal:

* **Windows (PowerShell):**
```powershell
powershell -ExecutionPolicy ByPass -c "irm [https://astral.sh/uv/install.ps1](https://astral.sh/uv/install.ps1) | iex"

```


* **Linux / macOS:**
```bash
curl -LsSf [https://astral.sh/uv/install.sh](https://astral.sh/uv/install.sh) | sh

```



### 2. Clone Repository & Setup Environment

```bash
# Clone repository
git clone [https://github.com/your-username/drosophila-cocaine-scrnaseq.git](https://github.com/your-username/drosophila-cocaine-scrnaseq.git)
cd drosophila-cocaine-scrnaseq

# Create and activate virtual environment via uv
uv venv

# Activate (Windows PowerShell)
.venv\Scripts\Activate.ps1
# Activate (Linux/macOS)
source .venv/bin/activate

# Install dependencies
uv pip install -r requirements.txt

```

---

## 📥 Data Access

The raw sequencing data and count matrices for this project are publicly available via the NCBI Gene Expression Omnibus (GEO):

* **GEO Accession:** [GSE152495](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE152495)


---

## 💻 Running the Pipeline

Launch Jupyter Lab within the `uv` environment:

```bash
uv run jupyter lab

```

Execute the notebooks or scripts sequentially:

1. `scripts/01_preprocessing.R` (or corresponding notebook)
2. `scripts/02_clustering.py`
3. `scripts/03_deg_analysis.R`
4. `scripts/04_pathway_go.R`

---

## 🎯 Reproducibility & Environment

* **R Dependencies:** `R v4.2+`, `Seurat v4.0+`, `sctransform`

* **Python Dependencies:** `Python v3.9+`, `scanpy v1.9+`, `anndata`, `leidenalg`

* **Hardware:** Minimum 64 GB RAM recommended for processing the full 86k-cell matrix.



---

## 📝 Peer Review & Citation

For a detailed critical review and analytical feedback on the underlying dataset and methodology, refer to [`docs/peer_review_report.md`](https://www.google.com/search?q=docs/peer_review_report.md).

If you use this codebase or documentation in your research, please cite the primary dataset:

* **GEO Accession:** GSE152495



---

## 📜 License

This project is open-source and distributed under the terms of the [LICENSE](https://www.google.com/search?q=LICENSE) included in this repository.
