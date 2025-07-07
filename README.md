# Uncovering CREs of B-Cells

## Project overview
Differential gene expression and chromatin accessibility jointly define cell identity. By integrating ATAC-seq (chromatin accessibility) with RNA-seq (gene expression), we reconstruct cis-regulatory networks and quantify how promoters and enhancers drive transcription during immune differentiation.

B lymphocytes (B cells), key effectors of adaptive immunity, arise from hematopoietic stem cells in the bone marrow and traverse a well-defined developmental cascade: 
**pro-B → pre-B → immature/transitional B → naïve follicular B → germinal-center B → memory B → plasma cell**. 

Each stage is governed by a distinct constellation of transcription factors and epigenetic modifications, creating unique accessibility and expression signatures that underpin B-cell specification, activation, and long-term immunity.

## Data & Recources
Our coverted tables in csv-format can be found in this Heibox link: https://heibox.uni-heidelberg.de/d/8eb927e475024eb3ae66/

They can also be accesed in '/data':
- '1.ATAC-Seq data.CSV'
- '2.RNA-Seq data.CSV'
- 'ATAC_QCmatric.CSV'
- 'ATAC_QCmatric_ReadStatistics.CSV'

## Overview of our analytical workflow
- **Exploratory Data Analysis**: Correlation heatmaps, distribution plots, outlier detection
- **Dimensionality Reduction and Clustering**: using K-means and hierarchcal clustering of CREs and genes as well as t-SNE/PCA on ATAC and RNA matrices
- **Differentioal and Variance Components analysis**: determining promotor and enhancer regulation
- **Cis-regulatory Mapping**: correlating OCR accesibility with nearby gene expression
- **linear Regression**: lineage specific modeling

## Results:

## How variable is the chromatin signal within cells?

### Is the signal (median, mean, std) dependent on the sequencing depth, number of input cells, or another QC metric?
![ATAC QC vs STAT](figures/heatmap_qc_vs_atac.png)
This heatmap shows the correlation between ATAC statistics and the QC-metric. The signal shows the strongest dependence on InputCellNumber, with correlation coefficients of 0.67 (mean), 0.6 (std), and 0.47 (median). The other OC metrics show only weak correlations. This means that signal strength is most strongly associated with the number of input cells. 

![mean ATAC peaks](figures/mean_ATAC_peaks_with_dendrogramm.png)
Cell types were hierarchically clustered based on their genome-wide ATAC signal. The barplot shows normalized mean accessibility per cell type, colored by lineage. The accompanying dendrogram reflects epigenomic similarity and highlights both lineage-specific patterns and cross-lineage relationships in chromatin accessibility.

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
This scatterplot shows no meaningful relationship between ATAC signal and distance to the TSS. Although the Pearson correlation is statistically significant (r = −0.004, p = 9.23e-03), the effect size is negligible. The data suggest that chromatin accessibility (as measured by ATAC) is not systematically higher or lower depending on proximity to transcription start sites.

### Are intronic enhancers different from enhancers outside the transcript.

![boxplot: intronic vs. non intronic](figures/Boxplot_intronic_vs_non_intronic_enhancer.png)
A two-sample t-test comparing intonic enhancers and non-intronic enhancers showed a highly significant difference in mean ATAC signal (T = T-statistic: 69.853, p = 0.000e+00). These values show a strong distinction between the ATAC mean signal of the two region types.

## Do related cell types cluster together based on their ATAC signal?

### Does the clustering reproduce known relationship between cells?

![Comparison of CRE clusters and lineages one by one, top 2,5%](figures/UMAP_Gini_CREs_cluster_vs_each_lineage_top2,5percent.png)

- Dendrogramm um Verwandheit zu zeigen

The UMAP on the left shows CREs colored by their KMeans cluster assignment, while the 10 UMAPs on the right display CREs associated with each of the 10 analyzed lineages. However, the KMeans clustering does not accurately capture known relationships between lineages, as most lineage-specific CREs — including those from B cells — are dispersed throughout the entire UMAP space.

### Can one quantify the similarity of cell types in a sorted matrix?

**Principal Component Analysis: Lineage and Cluster Mapping**
![PCA for celltypes and clusters with k=5](figures/PCA_k5_ct_clusters.png)
PCA of chromatin accessibility data reveals some lineage-specific structure. Points are colored by cell lineage and shaped by k-means cluster assignment (k = 5). While Cluster 1 aligns strongly with B cells, overall separation between clusters is limited, indicating that chromatin signal alone does not fully resolve cell types.

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

### When and how long is the B-cell specific cluster active?
B-cell specific cluster 6 becomes accessible already in s
Stem and Progenitor cells, indicating that its activation begins early during hematopoiesis. It remains accessible throughout B-cell differentiation, suggesting a long-lasting regulatory role. This sustained activity implies that cluster 6 may be involved in establishing and maintaining B-cell identity over an extended developmental window.


## Does clustering of the gene expression matrix show the same relationships between cell types as the ATAC-seq data?
![RNA vs ATAC dendrogramm 10 Cluster](figures/dendrogram_RNA_ATAC_10_clusters.png)

- Cluster nach lineage anfärben
Gene mit weniger Varianz rauskicken, 10 mit weniger Variabilität score rausnehmen

![confusion matrix heatmap](figures/Cluster_Overlap_Heatmap_RNA_ATAC.png)

Our initial hypothesis was that clustering based on chromatin accessibility (ATAC-seq) and gene expression (RNA-seq) would reveal similar lineage relationships. Specifically, we expected that the major cell lineages would each form distinct and matching clusters in both datasets. We anticipated 10 RNA-seq clusters and 10 ATAC-seq clusters, each reflecting similar regulatory programs.
However, the hierarchical clustering dendrograms do not support this clean one-to-one relationship. Clusters were labeled by assigning them the lineage most proportionally represented within them, since some lineages are assigned to more than one cluster. Looking at the cluster labels, you can see that some lineages appear more than once and some don't appear at all. 
To quantitatively assess the similarity between the two clusterings, we used three metrics:

- Adjusted Rand Index (ARI): 0.534
- Fowlkes-Mallows Index (FMI): 0.592
- Cophenetic distance correlation: r = 0.090, p = 0.0000

While the ARI and FMI suggest moderate agreement, the very low cophenetic distance correlation indicates that the global structure of the dendrograms is poorly conserved between RNA and ATAC.
This interpretation is supported by the cluster overlap heatmap, which shows little overlap: most values are zero, with only a few higher-count entries. This suggests limited consistency in how cell types are grouped across the two modalities. Moreover, RNA-seq clustering resulted in 17 clusters, while ATAC-seq produced only 9, further highlighting the deviation from our expectations.
 
## Can one use correlation analysis and distance information to associate ATAC-seq regions with gene expression?

### Where are associated CREs located with respect to the TSS?
![Histogram CRE-TSS distance](figures/Systematically%20Associated%20CRE-TSS%20distance.png)
This Histogram visualizes the distance of associated CREs with the corresponding TSS. 

### Where are the most associated CREs located?
![Donutplot of CRE Distribution](figures/CRE%20Feature%20Distribution.png)
Here we annotated the B-cell peaks by priority (promoter (±1 kb), exon, intron, intergenic) using pyranges to report the relative frequencies. Most CREs are located in intron (41.8%) and intergenetic regions (40.1%).   

### How many CREs are associated with genes?
![Histogram associated vs orphan CREs](figures/CREs%20within%20100%20kb%20of%20a%20gene%20vs.%20orphan%20CREs.png)
Detection of gene association by checking whether the B cell peaks have ≥1 gene within 100 kb (60.3 %) or none (orphan CREs, 39.7%).

### Is every promoter associated with a gene?
63 of 32241 Promotors are not associated with a gene, see also figure 'figures/Distribution of gene‐counts per promoter'

### Are some promoters associated with other genes?
![Histogram gene counts per promotor](figures/Distribution%20of%20gene‐counts%20per%20promoter.png)
This Histogram depicts the promotor gene overlap distribution.Most promoters overlap exactly one gene, with progressively fewer overlapping two or more.

### What is the closest associated CRE to a gene?
tba 

### Are there CREs that control several genes?
![Histogram gene counts per enhancer](figures/Distribution%20of%20gene‐counts%20per%20distal%20ATAC‐seq%20enhancer.png)
Having confirmed that promoters almost invariably overlap exactly one gene (with only a small tail reaching multiple targets; see 'figures/Distribution of gene-counts per promoter'), we next tallied the number of genes associated with enhancers. The resulting enhancer-gene count distribution is strikingly broader: whereas most enhancer still influence only 1 gene, a large fraction of enhancers have no nearby gene at all, and a clear  peak appears at two gene associations—highlighting the more diverse regulatory reach of enhancers compared to promoters.
## Can one use regression to associate CREs with gene expression?
### How much of the variance of gene expression can be explained for each gene with this approach?

![Histogram: regression for all celltypes](figures/Histogram_regression_all_celltypes.png)
This shows how well the ATAC signal explains the RNA signal for all celltypes. For most genes (R² ≈ 0) the  ATAC data explains almost none of their expression levels across cell types. But for the genes with a higher R², the chromatin accessibility seems to have a stronger predictive value.

### How do the coefficients differ when it is performed on B-cells alone?

![Histogram: regression for B-Cells](figures/Histogram_regression_Bcells.png)
This shows how well the ATAC signal explains the RNA signal only for the B-Cells. When regression is performed on B-Cells alone, more coefficients are higher. This indicates, that for B-Cell-specific regression, the chromatin accessibility has a stronger predictive value than for regression over all celltypes. 

![Difference of coefficients for cell-lineage-specific regression](figures/R^2_per_gene.png)
This result can also be seen in this scatter plot. The mean ΔR² (B-cell - all celtype) of 0.0453 indicates that the chromatin accessibility in B-cells explains gene expression better than the global model across all cell types. This suggests that the gene regulation via chromatin structure is (partly) B-cell-specific and that there are lineage-restricted regulatory mechanisms.

### Which CREs control B-cell genes?

![ATAC mean-signal for all CREs controlling B-Cell-specific genes](figures/ATAC_signal_all_CREs_Bcells.png)
This plot shows the ATAC-signal of the genes that have a high ΔR² which means the chromatin accesibility explains the gen expression in B-Cells better than across all celltypes. These genes were labeled as B-Cell-specific genes. 

![delta R^2 for all CREs controlling B-Cell-specific genes](figures/deltaR^2_all_CREs_Bcells.png)
The ΔR²-values of these B-Cell-specific genes can be seen in this plot.

To determine the CREs that control B-Cell-specific genes the peaks associated with these B-Cell-specific genes were identified. The 1845 B-Cell-specific genes can be seen in the dataframe: CREs_for_BCell_specific_genes

### How do the results of this analysis differ from pure association via correlation?

![R^2 vs Pearson correlation](figures/R^2_vs_pearson_correlation.png)
This plot shows the relationship between the R²-values and the correlation. The correlation only measures if there is a relationship between ATAC-signal and RNA-signal, not the direction. R² reflects how well a linear model explains gene expression from accessibility. The plot shows that genes with low correlation (low relationship in general) also have low R²-values (chromatin-accesibility does not explain genexpression well). If the correlation is higher (negative or positive) the R²-values are higher, which means that if there is a stronger relationship in general between ATAC-signal and RNA-signal, the chromatin-accesibility (ATAC-signal) explains the genexpression (RNA-signal) better. 
So this plot shows that the results of the analysis via regression and via correlation do not differ. The regression just gives even more information (about the diretion) than the correlation.

![deltaR^2 vs Pearson correlation](figures/deltaR^2_vs_pearson_correlation.png)
This plot also consideres the cell-type-specific effects by showing the relationship between the ΔR²-values and the correlation. Again it shows that the results of the analysis via regression and via correlation do not differ.

### Are there differences between activating and repressing CREs?

![R^2 by CRE type](figures/boxplot_variance_by_CRE_type.png)
This boxplot shows the R² of activating and repressing CREs in B-Cells. A two-sample t-test showed no statistically significant difference between the two groups (T = –1.64, p = 0.11). This means that for neither activating or repressing CREs the chromatin-accesibility explains the genexpression more than for the other group.

![ATAC mean by CRE type](figures/comparison_of_ATAC_mean_activating_repressing_CREs.png)
This plot compares the ATAC-mean-signals od repression and activating CREs. A two-sample t-test revealed a statistically significant difference between the two groups (T = –3.36, p < 0.001), indicating a strong difference in their means. It indicates that for activating CREs the chromatin-accesibility is lower than for repressing CREs. 

![KDE plot: ATAC mean by CRE type](figures/KDE_plot_ATAC_mean_activating_repressing_CREs.png)
This plot also shows the ATAC-mean-signal for activating and repressing CREs. It shows the same results, that the chromatin-accesibility for repressing CREs is higher than for activating CREs. 

### How many genes are mainly regulated by a repressing CREs, and can promoters act through repression?

![number of genes mainly regulated by activating vs. repressing CREs](figures/number_of_genes_regulated_activating_repressing.png)
This plot shows how many genes are mainly regulated by repressing CREs and which by activating CREs. 

### Can promoters act through repression?

![number of activating vs. repressing Promotors](figures/number_of_promoters_activating_repressing.png)
This plot shows that promoters mainly act activating but still can act through repression (small part).

### Where are repressing CREs located compared to activating CREs?

![location of repressing and activating CREs on chromosomes](figures/location_of_activating_repressing_CREs_chromosome.png)
This plots shows the location of repressing and activating CREs on the different chromosomes. It shows now significant trend although it indicates that on chromosome 19 and 4 there are only activating CREs, while an chromosome 9 there are only repressing CREs. 

![location of repressing and activating CREs to TSS](figures/location_of_activating_repressing_CREs_TSS.png)
The KDE plot considers the location of repressing and activating CREs regarding the distance to the TSS. It shows that repressing CREs are a bit closer to the TSS than activating CREs.


### Are there CREs that are repressing for one gene but activating for another gene?

![Heatmap: CREs that are both activating and repressing](figures/Heatmap_both_activating_repressing_CREs_TSS.png)
This heatmap shows Cres that are both activating (red) for one gene but repressing (blue) for another gene. 

![Network: CREs that are both activating and repressing](figures/Network_both_activating_repressing_CREs_TSS.png)
This is a picture of an interactive network that can be looked at in the notebook (RNA_seq.ipynb). The network shows the connection of the CREs and the associated genes (green lines indicate an activating relationship and red lines a repressing).

### Does CRE clustering change if one includes the effect direction on gene expression?

![Clusering not including the effect direction on gene expression](figures/Clustering_CREs_non_directional.png)
![Clusering including the effect direction on gene expression](figures/Clustering_CREs_directional.png)
![Comparision of Clustering](figures/Cluster_Overlap_Heatmap.png)
This plot shows that the clustering is dependend on the effect direction of gene expression. The same result is obtained by the Adjusted Rand Index with a value of 0.354.

## Can one cluster genes based on their expression profiles?

![Heatmap mean gene expression and lineages](figures/Heatmap_RNAclusters_lineages_mean.png)
Clustering genes based on their expression levels using KMeans does not yield meaningful results. There are no clearly defined lineages within the clusters — genes are either expressed across all lineages or not at all. Expression patterns remain nearly identical between lineages within each cluster.

### Can your determine a specific set of genes for B-cells?

We already generated a list of genes with high chromatin accessibility in B cells, which we labeled as B cell–specific genes. These were identified based on a high ΔR², indicating that chromatin accessibility explains gene expression more strongly in B cells than across all cell types.
![All B-cell specific genese](figures/ATAC_signal_all_CREs_Bcells.png)


### Are there subclusters of special interest?

![Heatmap Subcluster of genes - Accessibility](figures/Heatmap_Subcluster_Bcells_Accessibility.png)

![Line plot Subcluster of genes - Accessibility](figures/Lineplot_Subcluster_Bcells_Accessibility.png)

![Top B-cell specific genese](figures/ATAC_signal_top_CREs_Bcells.png)
Clustering of B cell–specific genes based on their chromatin accessibility revealed three distinct clusters. While the clusters are not clearly separable across all cell types, the mean accessibility profiles allow for a clearer distinction. Cluster 1 contains genes with the highest mean ATAC accessibility. Notably, this cluster shows a strong overlap with the top B cell–specific genes identified based on high ΔR² values, indicating that chromatin accessibility explains gene expression particularly well in B cells. This suggests that genes with both high overall accessibility and strong B cell–specific regulation tend to cluster together.

## Team 
Group 1 (B cells): Liska Großmann, Celine Krogmann, Annalena Kotz, Lilli Schmitt

Supervisor: Dr. Alexander Sasse

Tutor: Aidana Smugalova