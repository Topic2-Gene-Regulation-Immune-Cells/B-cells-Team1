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
This heatmap shows the correlation between ATAC statistics and the QC-metric. The signal shows the strongest dependence on InputCellNumber, with correlation coefficients of 0.67 (mean), 0.6 (std), and 0.47 (median). The other OC metrics show only weak correlations. This means that signal strength is most strongly associated with the number of input cells. 

### Should some cell types be removed from downstream analysis, or should we apply additional normalization?

![mean ATAC peaks](figures/mean_ATAC_peaks_with_dendrogramm.png)
- dendrogramm?

## How variable is the chromatin signal for CREs across cells?
### Should some peaks be removed for downstream analysis due to lack of signal?
![Hexbin: mean vs std](figures/Hexbin_mean_vs_std.png)
Different Hexbin Plots were used to determine peaks that should be removed (peaks with low mean, std, var). The red box shows the peaks that were removed our of the data set due to lack of signal. 

### Do promoters exibit specific signals that make them differ from enhancers?

![Lineplot: mean signal vs TSS-distance](figures/Lineplot_mean_signal_TSS_distance.png)
This plot shows how the mean ATAC-signal depends on the distance to the TSS. The red box shows the peaks that are are labeles as promoters while the other ones are labeled as enhancers. The plot shows that promoters exhibit a lower ATAC-mean-signal than enhancers which means the chromatin in promoters is more closed than in enhancers. 

![boxplot: signal of Promotor vs Enhancer scaled](figures/Boxplot_mean_per_Promotor_vs_Enhancer_not_scaled.png)
A two-sample t-test comparing Promoter and Enhancer regions showed a highly significant difference in mean ATAC signal (T = –34.13, p = 1.05 × 10⁻²³⁹). This result suggest a strong distinction between the ATAC mean signal of the two region types. 

### Is there a relationship between the signal and the distance to the TSS?

![mean ATAC-signal vs TSS-distance](figures/scatterplot_peak_vs_TSS_distance.png)
The Pearson correlation analysis gave the values: r = -0.004, p = 9.23e-03

### Are intronic enhancers different from enhancers outside the transcript.

![boxplot: intronic vs. non intronic](figures/Boxplot_intronic_vs_non_intronic_enhancer.png)
A two-sample t-test comparing Promoter and Enhancer regions showed a highly significant difference in mean ATAC signal (T = T-statistic: 69.853, p = 0.000e+00). These values show a strong distinction between the ATAC mean signal of the two region types.

## Do related cell types cluster together based on their ATAC signal?

### Does the clustering reproduce known relationship between cells?

![Comparison of CRE clusters and lineages one by one, top 2,5%](figures/UMAP_Gini_CREs_cluster_vs_each_lineage_top2,5percent.png)

- Dendrogramm um Verwandheit zu zeigen

### Can one quantify the similarity of cell types in a sorted matrix?

![PCA for celltypes and clusters with k=5](figures/PCA_k5_ct_clusters.png)
-> outlier wegschmeißen

![OCR landscape in a UMAP](figures/OCR%20landscape%20-%20UMAP.png)

## Can one define different classes of peaks based on the signal and the signal variation across cells?

### Can one cluster CREs based on their ATAC-signal?

![Gini plot after CRE-Cluster](figures/Top-Gini%20CRE-%20Cluster_%20UMAP.png)

![Gini CRE-Cluster Heatmap](figures/Cluster-specific%20CRE%20accessibility%20patterns.png)
CREs can be clustered based on their ATAC signal. Clustering into 10 groups yields a clear structure, which supports our initial hypothesis, as we are analyzing 10 distinct lineages.


### Can one visualize the behaviour of clustered regions?

![Signal trend across cell types](figures/Line_plot_of_clustered_regions.png)
Here you can see the average ATAC signal for each cluster, aggregated across all cell types. The clusters clearly differ in their "Mean ATAC singal" ranges.

### Can one define B-cell specific CRE clusters?
As shown in the heatmap in the heatmap of iv. a), only cluster 6 is B cell-specific, as the mean accessibility is high exclusively in B cells. Cluster 9 does not show lineage specificity but B cells, gdT cells, and myeloid cells all exhibit similarly high mean accessibility.

### Are there differences between the B-cell CRE clusters? When and how long are they active?
The UMAP of iii. a) shows that cluster 6 is overlapping in B-cells and Stem&Prog-cells. HELP wie soll man das formulieren?


## Does clustering of the gene expression matrix show the same relationships between cell types as the ATAC-seq data?
![RNA vs ATAC dendrogramm 10 Cluster](figures/dendrogram_RNA_ATAC_10_clusters.png)

- Cluster nach lineage anfärben
Gene mit weniger Varianz rauskicken, 10 mit weniger Variabilität score rausnehmen

Adjusted Rand Index: 0.534
Fowlkes-Mallows Index: 0.592
Cophenetic distance correlation: r = 0.090, p = 0.0000

![confusion matrix heatmap](figures/Cluster_Overlap_Heatmap_RNA_ATAC.png)


## Can one cluster genes based on their expression profiles?

![Heatmap mean gene expression and lineages](figures/Heatmap_RNAclusters_lineages_mean.png)
Clustering genes based on their expression levels using KMeans does not yield meaningful results. There are no clearly defined lineages within the clusters — genes are either expressed across all lineages or not at all. Expression patterns remain nearly identical between lineages within each cluster.

### Can your determine a specific set of genes for B-cells?

![All B-cell specific genese](figures/ATAC_signal_all_CREs_Bcells.png)


### Are there subclusters of special interest?

![Heatmap Subcluster of genes - Accessibility](figures/Heatmap_Subcluster_Bcells_Accessibility.png)

![Line plot Subcluster of genes - Accessibility](figures/Lineplot_Subcluster_Bcells_Accessibility.png)

Cluster 1 mit höchster mean accessibility entsprichte den Top B-cell-specific genes:

![Top B-cell specific genese](figures/ATAC_signal_top_CREs_Bcells.png)
 
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

### How many genes are mainly regulated by a repressing CREs, and can promoters act through repression?

![number of genes mainly regulated by activating vs. repressing CREs](figures/number_of_genes_regulated_activating_repressing.png)

### Can promoters act through repression?

![number of activating vs. repressing Promotors](figures/number_of_promoters_activating_repressing.png)

### Where are repressing CREs located compared to activating CREs?

![location of repressing and activating CREs on chromosomes](figures/location_of_activating_repressing_CREs_chromosome.png)

![location of repressing and activating CREs to TSS](figures/location_of_activating_repressing_CREs_TSS.png)

### Are there CREs that are repressing for one gene but activating for another gene?

![Heatmap: CREs that are both activating and repressing](figures/Heatmap_both_activating_repressing_CREs_TSS.png)
![Network: CREs that are both activating and repressing](figures/Network_both_activating_repressing_CREs_TSS.png)
[interactive Network: CREs that are both activating and repressing](figures/CRE-Gene-Regulatory-Network-Activating-Repressing.html)

### Does CRE clustering change if one includes the effect direction on gene expression?

![Clusering not including the effect direction on gene expression](figures/Clustering_CREs_non_directional.png)
![Clusering including the effect direction on gene expression](figures/Clustering_CREs_directional.png)
![Comparision of Clustering](figures/Cluster_Overlap_Heatmap.png)