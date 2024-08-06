# RNASeq-Workflow

# Project Title: Distinct Transcriptomic Profiles of Early-Onset Atopic Dermatitis in Blood of Pediatric Patients
## As a part of Course AS.410.671.01: Gene Expression Data Analysis and Visualization
---

## Introduction & Background

This project focuses on understanding the distinct transcriptomic profiles of early-onset atopic dermatitis (AD) in the blood of pediatric patients. The study leverages gene expression data from the GEO Dataset GSE116486, which examines the differences in gene expression between children with moderate-to-severe AD and healthy controls.

### Key Points:

- **Atopic Dermatitis (AD)**: A common inflammatory skin condition affecting young children.
- **Current Understanding**: Previous studies primarily focus on adult AD using long-standing cases. Recent studies highlight significant Th2 and Th17/Th22 skewing in early pediatric AD, differing from the Th1 up-regulation in adults.
- **Challenge**: Pediatric skin biopsies are difficult to obtain, necessitating alternative methods to understand early AD pathogenesis.

## Objective & Methods

### Objective:

To define the blood gene expression profile and identify biomarkers associated with early moderate-to-severe pediatric AD. This will provide insights into the molecular mechanisms underlying AD in its early stages in children and help quantify systemic inflammation, contributing to developing new treatment targets.

### Methods:

1. **Participants**: Blood cells from 28 children with AD (under 5 years and within 6 months of disease onset) compared to healthy controls.
2. **Sample Collection**: Freshly drawn, unstimulated blood cells.
3. **Analysis**:
   - Microarray-based gene expression analysis.
   - Identification of differentially expressed genes (DEGs) with fold change >1.2 and false discovery rate (FDR) <0.05.
   - Utilized Affymetrix Human Genome U133 Plus 2.0 Array for analysis.

## Data Processing and Analysis

### Normalization:

- **RMA & GCRMA**: Effective normalization methods maintain a data variance balance.
- **MAS**: Narrow peak indicating potential over-normalization, which might suppress critical biological variability.
- **Preferred Method**: RMA, for its balanced approach in normalization without affecting data distribution.

### Outlier Assessment:

- Performed using correlation matrix and clustering of samples.
- No obvious outliers were detected; all samples were considered for analysis.

### Filtering Low Expression Genes:

- Removed genes with minimal variation or low expression to focus on biologically significant DEGs.
- Utilized the coefficient of variation (CV) to eliminate the lowest 25% CV values.

### Feature Selection & Multiple Testing:

- A non-parametric Wilcox test was used for significance testing.
- FDR correction applied to p-values to reduce false positives.
- Identified 234 significant probesets with FDR < 0.05.

### DEG Analysis:

- Criteria for DEGs: p.adjusted (FDR) < 0.05 and absolute fold change > 1.2.
- Identified 204 DEGs (142 upregulated, 62 downregulated).
- Visualized using volcano plots and histograms of adjusted p-values.

### Dimensionality Reduction:

- Principal Component Analysis (PCA) is used to visualize high-dimensional gene expression data.
- Some separation was observed between AD and control groups, with outliers noted in the AD group.

### Clustering:

- Performed using Euclidean distance and Complete Linkage.
- Clustering helps identify closely related gene expressions and potential shared biological pathways.

### Classification:

- Logistic Regression Model (LRM) and Linear Discriminant Analysis (LDA) used for classification.
- LDA achieved perfect classification on the test set.

### Gene Enrichment Analysis:

- Significant probes (top 10 selected) identified and analyzed using NCBI DAVID for gene ontology and biological processes.
- Hits indicate the role of immune response markers and pathways involved in Th2 and Th17 cytokine expression.

## Conclusions

- Identified a limited array of dysregulated genes in the blood of children with AD, contrasting with broader dysregulation seen in the skin.
- The gene expression patterns in blood provide insights into the systemic immune response in early pediatric AD.
- Findings could enhance the understanding of the atopic march progression and aid in developing targeted treatments.

---

## Files and Structure

- **analysis.pdf**: Contains detailed documentation of the study, including methods, analysis, and results.
- **analysis_workflow.Rmd**: The R Markdown file used for the analysis, contains all code, plots, and detailed explanations of the methods and results.

---

## Running the pipeline

1. **Dependencies**: Ensure R and RStudio are installed on your system. Install the necessary R packages by running:
   ```R
   install.packages(c("affy", "limma", "GEOquery", "pheatmap", "ggplot2", "dplyr"))
   ```
3. **Running the Analysis**: Open `Project.Rmd` in RStudio and knit the document to reproduce the analysis and generate the report.
