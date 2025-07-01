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

### mean ATAC peaks colored by lineage with dendrogramm 

![mean ATAC peaks](figures/mean_ATAC_peaks_with_dendrogramm.png)

-> remove first cell ??

## 1. ii

### a. remove peaks due to low signal 

![Hexbin: mean vs std](figures/Hexbin_mean_vs_std.png)
![mean per peak](figures/mean_per_peak_id.png)

### b. Signals of promotors and enhancers

![Histogramm: signal vs TSS-distance](figures/Histogramm_mean_per_TSS_distance.png)
![mean signal vs TSS-distance with Annotation](figures/MeanPeakSignal_by_TSS_Distance_per_Annotation.png)

![boxplot: signal of Promotor vs Enhancer scaled](figures/Boxplot_mean_per_Promotor_vs_Enhancer_scaled.png)
![boxplot: signal of Promotor vs Enhancer not scaled](figures/Boxplot_mean_per_Promotor_vs_Enhancer_not_scaled.png)
![violinplot](figures/violinplot_mean_per_Promotor_vs_Enhancer.png)

### c. correlation of peak and distance to TSS

![mean ATAC-signal vs TSS-distance](figures/scatterplot_peak_vs_TSS_distance.png)

### d. intronic vs. non intronic enhancer
![boxplot: intronic vs. non intronic](figures/Boxplot_intronic_vs_non_intronic_enhancer.png)

### Distribution of mean ATAC peaks

![Histogramm of mean ATAC peak distribution](figures/Distribution_of_ATAC_peaks.png)

### OCR landscape - UMAP

![OCR landscape in a UMAP](figures/OCR%20landscape%20-%20UMAP.png)

## 1. iii

### PCA
![PCA max. peak - celltype](figures/PCA_peaks_multi.png)

![PCA max. peak - celltype_ PC4](figures/PCA_peaks_multi_2.png)

![PCA colored by lineage](figures/PCA_peaks_PC2_vs_PC4.png)


## 1. iv

### Cre cluster activity per lineage

![Heatmap of Cre cluster activity](figures/Correlation_Peak-Clusters_Lineages_filtered_dataset.png)

### Visualization of clustered regions

![Signal trend across cell types](figures/Line_plot_of_clustered_regions.png)

### Define cell lineage-specific CRE clusters

![Comparing B-cell signal to others](figures/B-cell_mean_signal_vs_otther_lineages.png)

B-lineage-specific clusters with mean log2FC > 0.85: [4, 8, 9]

### Relative activity per cluster by row-normalizing (z-scoring) the data

![Relative activity per cluster](figures/Relative_activity_per_cluster.png)
->Colors indicate whether the lineage is more or less active relative to that cluster’s average
->Are there differences between these cell-lineage specific CRE clusters? When and how long are they active?  Wir das so beantwortet???

### Tried to cluster CREs based on Gini-index 

![Gini plot after CRE-Cluster](figures/Top-Gini%20CRE-%20Cluster_%20UMAP.png)

### Comparison of clustered CREs and lineages

![Comparison of CRE clusters and all lineages together](figures/UMAP_Gini_CREs_clusters_vs_lineages_side_by_side.png)

![Comparison of CRE clusters and lineages one by one](figures/UMAP_Gini_CREs_cluster_vs_each_lineage.png)

### Tried to link CRE-clusters and lineage based on Gini-index 

![Gini plot after Lineage](figures/Top-Gini%20CRE-%20Lineage_%20UMAP.png)

BUT es macht keinen sinn weil wir ja die UMAP anhand der CREs gemacht haben und nicht anhand der lineages deswegen kann man es nicht vergleichen !

### CRE-Cluster across lineages based on top 20% Gini-number

![CRE-Clusters across specific cell types](figures/Cluster-specific%20CRE%20accessibility%20patterns.png)

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

## 2. iv
### a. regression for all celltypes 

![Histogram: regression for all celltypes](figures/Histogram_regression_all_celltypes.png)

### b. regression for B-Cells

![Histogram: regression for B-Cells](figures/Histogram_regression_Bcells.png)
![Difference of coefficients for cell-lineage-specific regression](figures/R^2_per_gene.png)

### c. cell-lineage specific CREs

![ATAC mean-signal for top CREs controlling B-Cell-specific genes](figures/ATAC_signal_top_CREs_Bcells.png)
![ATAC mean-signal for all CREs controlling B-Cell-specific genes](figures/ATAC_signal_all_CREs_Bcells.png)

![delta R^2 for top CREs controlling B-Cell-specific genes](figures/deltaR^2_top_CREs_Bcells.png)
![delta R^2 for all CREs controlling B-Cell-specific genes](figures/deltaR^2_all_CREs_Bcells.png)

### d. how do the results of R^2 and correlation differ

![R^2 vs Pearson correlation](figures/R^2_vs_pearson_correlation.png)
![deltaR^2 vs Pearson correlation](figures/deltaR^2_vs_pearson_correlation.png)

### e. difference of activating and repressing CREs

![R^2 by CRE type](figures/boxplot_variance_by_CRE_type.png)
![ATAC mean by CRE type](figures/comparison_of_ATAC_mean_activating_repressing_CREs.png)
![KDE plot: ATAC mean by CRE type](figures/KDE_plot_ATAC_mean_activating_repressing_CREs.png)
![Histogram: ATAC mean by CRE type](figures/Histogram_ATAC_mean_activating_repressing_CREs.png)

### f. How many genes are mainly regulated by repressing CREs

![number of genes mainly regulated by activating vs. repressing CREs](figures/number_of_genes_regulated_activating_repressing.png)

### f. Can promotors act through repression 

![number of activating vs. repressing Promotors](figures/number_of_promoters_activating_repressing.png)
