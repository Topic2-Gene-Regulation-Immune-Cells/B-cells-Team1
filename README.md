# B-cells-Team1

Heibox with tables converted to csv-format: 

https://heibox.uni-heidelberg.de/d/8eb927e475024eb3ae66/

To implement the collective virtual environment: 

cd *project directory*\
conda env create -f environment.yml\
conda activate envBCells1


## 1. i

![ATAC Stats vs QC](figures/ATAC_Stats_vs_QC.png)

### mean ATAC peaks colored by lineage

![mean ATAC peaks](figures/mean_ATAC_peaks.png)

-> remove first cell ??

### UMAP of ATAC peaks colored by lineage

![UMAP of ATAC peaks](figures/UMAP_ATAC_peaks.png)

## 1. ii

### Distribution of mean ATAC peaks

![Histogramm of mean ATAC peak distribution](figures/Distribution_of_ATAC_peaks.png)

## 1. iii

### PCA

![PCA](figures/PCA.png)

![PCA_clusters](figures/PCA_clusters.png)

### UMAP to determine the overlap between the clusters and the true lineage

![UMAP Overlap of clusters and lineage](figures/UMAP_clusters_lineage.png)

### Correlation of Peak-Clusters and cell types 

! [Correlation of clusters and cell types](figures/Correlation_Peak-Clusters_CellTypes.png)

## 1. iv

### Cre cluster activity per lineage

![Heatmap of Cre cluster activity](figures/CRE_clusters.png)

## 2. i

### RNA vs ATAC

![RNA vs ATAC dendrogramm](figures/dendrogramm_RNA_vs_ATAC.png)

![PCA-Plot RNA vs. ATAC](figures/PCA_RNA_vs_ATAC.png)

## 2. ii

### Clustering of genes by expression across all celltypes

![Heatmap Geneclustering](figures/Geneclustering_by_expression.png)

### Mean gene expression per cluster across cell types

![Heatmap mean gene expression](figures/mean_gene_expression.png)

### Distribution of gene expression by cluster in B-cells and other lineages

![Boxplot B-cells vs. other cells](figures/expression_B_vs_others.png)

### Gene cluster vs KMeans cluster

![Heatmap Gene cluster vs. KMeans cluster](figures/Geneclusters_KMeans.png)

### Distribution of gene expression in gene clusters across lineages

![Boxplot for expression distribution of gene clusters across lineages](figures/Distribution_geneclusters_lineages.png)
