# Spatial Transcriptomics & Single Cell RNA Gene Analysis for Lung Cancer

[![R](https://img.shields.io/badge/R-4.0%2B-blue.svg)](https://www.r-project.org/)
[![Shiny](https://img.shields.io/badge/Shiny-1.7%2B-brightgreen.svg)](https://shiny.rstudio.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A comprehensive R Shiny application for analyzing spatial transcriptomics and single-cell RNA sequencing data, specifically designed for understanding the underlying mechanisms of lung cancer including LUAD (Lung Adenocarcinoma), SCC (Squamous Cell Carcinoma), and SCLC (Small Cell Lung Cancer).

## 🔬 Features

### Core Analysis Capabilities
- **Spatial Transcriptomics Analysis**: Comprehensive analysis of 10x Visium spatial data
- **Single Cell RNA Analysis**: Processing and visualization of scRNA-seq data
- **Cell Type Annotation**: Automated cell type prediction using SingleR
- **Pathway Analysis**: Enhanced metabolic pathway scoring with special focus on polyamine metabolism
- **Comparative Analysis**: Tumor vs adjacent tissue comparison
- **Interactive Visualizations**: Multiple plot types including spatial plots, UMAP, heatmaps, and circular plots

### Enhanced Pathway Scoring
- **Polyamine Metabolism**: Simplified scoring with negated PAOX and OAZ1 expression values
- **Metabolic Pathways**: Analysis of fatty acid oxidation, urea cycle, creatine synthesis, pentose phosphate pathway, and purine metabolism
- **Pathway-Level Comparisons**: Aggregated pathway expression analysis across tissue types

### Visualization Tools
- Spatial feature plots and cluster visualization
- Gene expression circular plots
- Cell type distribution analysis
- Pathway expression heatmaps
- Tissue comparison violin plots
- Interactive gene search and selection

## 📊 Data Sources

This application uses publicly available data from:

- **LUAD and SCC Single Cell RNA Sequencing**: [ArrayExpress E-MTAB-13526](https://www.ebi.ac.uk/biostudies/arrayexpress/studies/E-MTAB-13526#processed-data)
- **LUAD and SCC Spatial Transcriptomics**: [ArrayExpress E-MTAB-13530](https://www.ebi.ac.uk/biostudies/arrayexpress/studies/E-MTAB-13530)
- **SCLC Single Cell RNA Sequencing**: https://data.humantumoratlas.org/publications/hta8_2021_cancer-cell_joseph-m-chan?tab=overview

## 🛠 Installation

### Prerequisites
- R (version 4.0 or higher)
- RStudio (recommended)

### Required R Packages
```r
# Core Shiny packages
install.packages(c("shiny", "shinydashboard", "shinycssloaders", 
                   "shinyWidgets", "shinydashboardPlus"))

# Data manipulation and visualization
install.packages(c("DT", "plotly", "ggplot2", "dplyr", "patchwork", 
                   "RColorBrewer", "reshape2", "tidyr", "plyr", "stringr", 
                   "ggpubr", "gridExtra", "grid", "tibble"))

# Bioinformatics packages
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install(c("Seurat", "SingleR", "celldex", 
                       "SummarizedExperiment"))
```

### Clone Repository
```bash
git clone https://github.com/yourusername/spatial-transcriptomics-lung-cancer.git
cd spatial-transcriptomics-lung-cancer
```

## 🚀 Usage

### Data Setup
1. **Update Data Paths**: Modify the data paths in the script to match your system:
```r
BASE_PATH <- "/your/path/to/data/spatial_transcriptomics"
VISIUM_PATH <- file.path(BASE_PATH, "visium")
SCRNA_LUAD_PATH <- file.path(BASE_PATH, "scRNA", "LUAD")
SCRNA_SCLC_PATH <- file.path(BASE_PATH, "scRNA", "SCLC")
```

2. **Data Structure**: Organize your data as follows:
```
data/
├── spatial_transcriptomics/
│   ├── visium/
│   │   ├── P10_T1/
│   │   ├── P11_T1/
│   │   └── ...
│   └── scRNA/
│       ├── LUAD/
│       └── SCLC/
```

### Running the Application
```r
# Load and run the application
source("app.R")
# The app will automatically start in your default browser
```

### Application Workflow
1. **Load Data**: Select cancer type and sample, then click "Load Data"
2. **Gene Selection**: Choose genes by category or add custom genes
3. **Generate Analysis**: Click "Generate Plots" to create visualizations
4. **Explore Results**: Navigate through different tabs to view various analyses

## 📋 Application Tabs

### 1. Spatial Transcriptomics
- Load and analyze 10x Visium spatial data
- Visualize gene expression in tissue context
- Cell type annotation and clustering
- Pathway-level analysis

### 2. Single Cell RNA
- Process scRNA-seq data
- UMAP visualization and cell type identification
- Gene expression analysis by cell type
- Cell type proportion analysis

### 3. Comparative Analysis
- Compare gene expression between spatial and scRNA data
- Cross-platform validation

### 4. Tissue Comparison
- Tumor vs adjacent tissue analysis
- Statistical testing with p-values
- Pathway-level tissue comparison

### 5. Gene Explorer
- Interactive gene search functionality
- Gene availability across datasets
- Pathway information browser

### 6. Data Info
- Complete dataset information
- Sample metadata
- Pathway gene lists

### Cell Type Annotation
- Uses SingleR for automated cell type prediction
- Reference dataset: BlueprintEncodeData
- Fallback to Seurat clustering if annotation fails

### Data Processing Pipeline
1. **Quality Control**: Filter cells/spots based on feature count and mitochondrial percentage
2. **Normalization**: SCTransform normalization
3. **Dimensionality Reduction**: PCA and UMAP
4. **Clustering**: Graph-based clustering
5. **Annotation**: SingleR cell type prediction


**Data Sources:**
- ArrayExpress E-MTAB-13526 (scRNA data LUAD and SCC)
- ArrayExpress E-MTAB-13530 (Spatial data LUAD and SCC)
- The Human Tumor Atlas Network (HTAN) – SCLC

## 👨‍🔬 Author

**Hamid Khoshfekr Rudsari**
- 🏛️ Institution: MD Anderson Cancer Center
- 📧 Email: hkhoshefkr@mdanderson.org
- 📧 Personal: khoshfekr1994@gmail.com
- 📅 Date: July 2025

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

### Development Guidelines
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📝 License

This project is licensed under the MIT License.

## 🐛 Known Issues

- Large datasets may require increased memory allocation
- Some gene annotations may vary between datasets
- Cell type annotation accuracy depends on reference dataset quality

## 📚 Documentation

For detailed documentation on:
- **Data preprocessing**: See comments in `load_visium_data()` and `load_scrna_data()` functions
- **Pathway scoring**: See `calculate_pathway_score()` and related functions
- **Visualization**: See individual plot generation functions



## 🔄 Version History

- **v2.0.0** (October 2025): Second version – minor updates in the README and main.r
- Enhanced pathway analysis capabilities
- Comprehensive visualization tools
- Support for multiple lung cancer types

---

**Keywords**: spatial transcriptomics, single-cell RNA, lung cancer, LUAD, SCC, SCLC, polyamine metabolism, pathway analysis, R Shiny, bioinformatics
