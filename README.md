# B-cells-Team-1

Heibox with tables converted to csv-format: 

https://heibox.uni-heidelberg.de/d/8eb927e475024eb3ae66/

To implement the collective virtual environment: 

cd *project directory*\
conda env create -f environment.yml\
conda activate envBCells1


## How variable is the chromatin signal within cells?

### Is the signal (median, mean, std) dependent on the sequencing depth, number of input cells, or another QC metric?
![ATAC QC vs STAT](figures/heatmap_qc_vs_atac.png)
### Should some cell types be removed from downstream analysis, or should we apply additional normalization?

![mean ATAC peaks](figures/mean_ATAC_peaks_with_dendrogramm.png)

## How variable is the chromatin signal for CREs across cells?
### Should some peaks be removed for downstream analysis due to lack of signal?
![Hexbin: mean vs std](figures/Hexbin_mean_vs_std.png)

![mean per peak](figures/mean_per_peak_id.png)
### Do promoters exibit specific signals that make them differ from enhancers?
![Histogramm: signal vs TSS-distance](figures/Histogramm_mean_per_TSS_distance.png)

![mean signal vs TSS-distance with Annotation](figures/MeanPeakSignal_by_TSS_Distance_per_Annotation.png)

![boxplot: signal of Promotor vs Enhancer scaled](figures/Boxplot_mean_per_Promotor_vs_Enhancer_scaled.png)

![violinplot](figures/violinplot_mean_per_Promotor_vs_Enhancer.png)

### Is there a relationship between the signal and the distance to the TSS?

![mean ATAC-signal vs TSS-distance](figures/scatterplot_peak_vs_TSS_distance.png)

### Are intronic enhancers different from enhancers outside the transcript.

![boxplot: intronic vs. non intronic](figures/Boxplot_intronic_vs_non_intronic_enhancer.png)

## Do related cell types cluster together based on their ATAC signal?

![PCA max. peak - celltype](figures/PCA_peaks_multi.png)

![PCA max. peak - celltype_ PC4](figures/PCA_peaks_multi_2.png)

### Does the clustering reproduce known relationship between cells?

![Comparison of CRE clusters and all lineages together, top 20%](figures/UMAP_Gini_CREs_clusters_vs_lineages_side_by_side.png)

![Comparison of CRE clusters and all lineages together, top 5%](figures/UMAP_Gini_CREs_clusters_vs_lineages_top5percent.png)

![Comparison of CRE clusters and lineages one by one, top 20%](figures/UMAP_Gini_CREs_cluster_vs_each_lineage.png)

![Comparison of CRE clusters and lineages one by one, top 2,5%](figures/UMAP_Gini_CREs_cluster_vs_each_lineage_top2,5percent.png)

### Can one quantify the similarity of cell types in a sorted matrix?

![PCA for celltypes and clusters with k=5](figures/PCA_k5_ct_clusters.png)

![OCR landscape in a UMAP](figures/OCR%20landscape%20-%20UMAP.png)

## Can one define different classes of peaks based on the signal and the signal variation across cells?

### Cre cluster activity per lineage

![Heatmap of Cre cluster activity](figures/Correlation_Peak-Clusters_Lineages_filtered_dataset.png)

### Can one cluster CREs based on their ATAC-signal?

![Gini plot after CRE-Cluster](figures/Top-Gini%20CRE-%20Cluster_%20UMAP.png)

![Gini CRE-Cluster Heatmap](figures/Cluster-specific%20CRE%20accessibility%20patterns.png)

-> hat nur 20% top peaks über Gini index ist es besser als andere Heatmap?

### Can one visualize the behaviour of clustered regions?

![Signal trend across cell types](figures/Line_plot_of_clustered_regions.png)

### Can one define B-cell specific CRE clusters?

![Comparing B-cell signal to others](figures/B-cell_mean_signal_vs_otther_lineages.png)

B-lineage-specific clusters with mean log2FC > 0.85: [4, 8, 9]

### ODER

![Kmeans Bcell specific with 6 clusters](figures/Kmeans_Bcells_6.png)

### Are there differences between the B-cell CRE clusters? When and how long are they active?

![Relative activity per cluster](figures/Relative_activity_per_cluster.png)
->Colors indicate whether the lineage is more or less active relative to that cluster’s average
->Wir das so beantwortet???

### ODER

![Signal trend across Bcells](figures/Line_plot_of_clustered_regions_Bcells.png)
->ATAC-signal means ist verschieden


## Does clustering of the gene expression matrix show the same relationships between cell types as the ATAC-seq data?
![RNA vs ATAC dendrogramm 10 Cluster](figures/dendrogram_RNA_ATAC_10_clusters.png)

Adjusted Rand Index: 0.534
Fowlkes-Mallows Index: 0.592
Cophenetic distance correlation: r = 0.090, p = 0.0000

![confusion matrix heatmap](figures/Cluster_Overlap_Heatmap_RNA_ATAC.png)


## Can one cluster genes based on their expression profiles?

![Heatmap gene expression and lineages](figures/Heatmap_RNAclusters_lineages.png)

![Heatmap mean gene expression and lineages](figures/Heatmap_RNAclusters_lineages_mean.png)

->welches der beiden ist besser??

![Kmeans RNA with 9 clusters](figures/KMeans_RNA_9.png)
-> Clustered genes based on their expression level over the cell types

### Can your determine a specific set of genes for B-cells?

![All B-cell specific genese](figures/ATAC_signal_all_CREs_Bcells.png)

### Are there subclusters of special interest?

![Heatmap Subcluster of genes - Accessibility](figures/Heatmap_Subcluster_Bcells_Accessibility.png)

![Line plot Subcluster of genes - Accessibility](figures/Lineplot_Subcluster_Bcells_Accessibility.png)

Cluster 1 mit höchster mean accessibility entsprichte den Top B-cell-specific genes:

![Top B-cell specific genese](figures/ATAC_signal_top_CREs_Bcells.png)

![Hierarchical clustering of genes](figures/Hierarchical_Clustering_Subcluster_Bcells_Accessibility.png)
 
## Can one use correlation analysis and distance information to associate ATAC-seq regions with gene expression?
![Histogram CRE-TSS distance](figures/Systematically%20Associated%20CRE-TSS%20distance.png)

### Where are associated CREs located with respect to the TSS?
![Donutplot of CRE Distribution](figures/CRE%20Feature%20Distribution.png)

### Where are the most associated CREs located?
### How many CREs are associated with genes?
### Is every promoter associated with a gene?
### Are some promoters associated with other genes?
### What is the closest associated CRE to a gene?
### Are there CREs that control several genes?

## Can one use regression to associate CREs with gene expression?
### How much of the variance of gene expression can be explained for each gene with this approach?

![Histogram: regression for all celltypes](figures/Histogram_regression_all_celltypes.png)

### How do the coefficients differ when it is performed on B-cells alone?

![Histogram: regression for B-Cells](figures/Histogram_regression_Bcells.png)

![Difference of coefficients for cell-lineage-specific regression](figures/R^2_per_gene.png)

### Which CREs control B-cell genes?

![ATAC mean-signal for all CREs controlling B-Cell-specific genes](figures/ATAC_signal_all_CREs_Bcells.png)

![delta R^2 for all CREs controlling B-Cell-specific genes](figures/deltaR^2_all_CREs_Bcells.png)

### How do the results of this analysis differ from pure association via correlation?

![R^2 vs Pearson correlation](figures/R^2_vs_pearson_correlation.png)

![deltaR^2 vs Pearson correlation](figures/deltaR^2_vs_pearson_correlation.png)

### Are there differences between activating and repressing CREs?

![R^2 by CRE type](figures/boxplot_variance_by_CRE_type.png)

![ATAC mean by CRE type](figures/comparison_of_ATAC_mean_activating_repressing_CREs.png)

![KDE plot: ATAC mean by CRE type](figures/KDE_plot_ATAC_mean_activating_repressing_CREs.png)

![Histogram: ATAC mean by CRE type](figures/Histogram_ATAC_mean_activating_repressing_CREs.png)

### How many genes are mainly regulated by a repressing CREs, and can promoters act through repression?

![number of genes mainly regulated by activating vs. repressing CREs](figures/number_of_genes_regulated_activating_repressing.png)

### Can promoters act through repression?

![number of activating vs. repressing Promotors](figures/number_of_promoters_activating_repressing.png)

### Where are repressing CREs located compared to activating CREs?

![location of repressing and activating CREs on chromosomes](figures/location_of_activating_repressing_CREs_chromosome.png)

![location of repressing and activating CREs to TSS](figures/location_of_activating_repressing_CREs_TSS.png)

![ECdF: location of repressing and activating CREs to TSS](figures/ECDF_location_of_activating_repressing_CREs_TSS.png)

### Are there CREs that are repressing for one gene but activating for another gene?

![Heatmap: CREs that are both activating and repressing](figures/Heatmap_both_activating_repressing_CREs_TSS.png)
![Network: CREs that are both activating and repressing](figures/Network_both_activating_repressing_CREs_TSS.png)
[interactive Network: CREs that are both activating and repressing](figures/CRE-Gene-Regulatory-Network-Activating-Repressing.html)

### Does CRE clustering change if one includes the effect direction on gene expression?

![Clusering not including the effect direction on gene expression](figures/Clustering_CREs_non_directional.png)
![Clusering including the effect direction on gene expression](figures/Clustering_CREs_directional.png)
![Comparision of Clustering](figures/Cluster_Overlap_Heatmap.png)

-------------------------------------------------------------

### a. ATAC QC vs stats

![ATAC QC vs STAT](figures/heatmap_qc_vs_atac.png)

### mean ATAC peaks colored by lineage

![mean ATAC peaks](figures/mean_ATAC_peaks.png)

### mean ATAC peaks colored by lineage with dendrogramm 

![mean ATAC peaks](figures/mean_ATAC_peaks_with_dendrogramm.png)


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

### g. Where are repressing CREs located compared to activating CREs?

![location of repressing and activating CREs on chromosomes](figures/location_of_activating_repressing_CREs_chromosome.png)
![location of repressing and activating CREs to TSS](figures/location_of_activating_repressing_CREs_TSS.png)
![ECdF: location of repressing and activating CREs to TSS](figures/ECDF_location_of_activating_repressing_CREs_TSS.png)