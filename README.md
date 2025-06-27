# B-cells-Team1

Heibox with tables converted to csv-format: 

https://heibox.uni-heidelberg.de/d/8eb927e475024eb3ae66/

To implement the collective virtual environment: 

cd *project directory*\
conda env create -f environment.yml\
conda activate envBCells1


## 1. i

### a. ATAC QC vs stats

![ATAC QC vs STAT](figures/heatmap_qc_vs_atac.png)

### mean ATAC peaks colored by lineage

![mean ATAC peaks](figures/mean_ATAC_peaks.png)

-> remove first cell ??

### UMAP of ATAC peaks colored by lineage

![UMAP of ATAC peaks](figures/UMAP_ATAC_peaks_zoomed.png)

![UMAP of B-cell ATAC peaks colored by accessibility](figures/UMAP_B_cells.png)

## 1. ii

### a. remove peaks due to low signal 

![variance per peak](figures/variance_per_peak.png)
![mean per peak](figures/mean_per_peak.png)

### b. Signals of promotors and enhancers

![Histogramm: signal vs TSS-distance](figures/mean_per_TSS_distance_hist.png)
![Lineplot: signal vs TSS-distance](figures/mean_per_TSS_distance.png)

### Distribution of mean ATAC peaks

![Histogramm of mean ATAC peak distribution](figures/Distribution_of_ATAC_peaks.png)

### OCR landscape - UMAP

![OCR landscape in a UMAP](figures/OCR%20landscape%20-%20UMAP.png)

## 1. iii

### PCA

![PCA](figures/PCA.png)

![PCA_clusters](figures/PCA_clusters.png)

### UMAP to determine the overlap between the clusters and the true lineage

![UMAP Overlap of clusters and lineage](figures/UMAP_clusters_lineage.png)

### Correlation of Peak-Clusters and lineages

![Correlation of clusters and lineages](figures/Correlation_Peak-Clusters_Lineages.png)

## 1. iv

### Cre cluster activity per lineage

![Heatmap of Cre cluster activity](figures/CRE_clusters.png)

-> CRE specific data or the same as plot before

### Tried to cluster CREs based on Gini-index 

![Gini plot after CRE-Cluster](figures/Top-Gini%20CRE-%20Cluster_%20UMAP.png)

### CRE-Cluster across lineages

![CRE-Clusters across specific cell types](figures/Cluster-specific%20CRE%20accessibility%20patterns.png)

->does not make sense since i used Gini-index

## 2. i

### RNA vs ATAC

![RNA vs ATAC dendrogramm](figures/dendrogramm_RNA_vs_ATAC.png)

![PCA-Plot RNA vs. ATAC](figures/PCA_RNA_vs_ATAC.png)

## 2. ii
### Mean gene expression per cluster across lineages 

![Heatmap mean gene expression and lineages](figures/Heatmap_RNAclusters_lineages.png)

### Distribution of gene expression in gene clusters across lineages

![Boxplot for expression distribution of gene clusters across lineages](figures/Distribution_geneclusters_lineages.png)

### Mean gene expression per cluster across lineages

![Heatmap mean gene expression](figures/Heatmap_RNAclusters_lineages_mean.png)

### Distribution of gene expression in gene subclusters across lineages

![Boxplot for expression distribution of gene subclusters across lineages](figures/Distribution_geneclusters_lineages_sublucters.png)
