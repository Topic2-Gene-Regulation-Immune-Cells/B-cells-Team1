1. Determine differences and similarities of the chromatin landscape between immune cells:
    i. How variable is the chromatin signal within cells?
        a. Is the signal dependent on sequencing depth, number of input cells, QC metric?
            Daten: 
                ATAC matrix: Signal pro Peak pro Sample
                QC matrix: columns: InputCellNumber, PF.reads, %fragment_1Kb_TSS, etc.
            Plot: 
                Scatterplot ATAC signal vs InputCellNumber, PF.reads, etc.
                Correlation heatmap between mean ATAC signal and QC metrics

        b. Should some cell types be removed / normalization?
            Plot: 
                Boxplot ATAC signal distributions per cell type (und B-Zellen einzeln anschauen)

    ii. How variable is the chromatin signal for CREs across cells?
        a. Should peaks be removed due to lack of signal?
            Plot: Histogram -> mean signal across samples for each Peak (Peaks mit low mean signal dann evtl. entfernen)

        b. Do promoters exhibit specific signals vs enhancers?
            Daten:
                Annotation file → Peak → Promoter / Enhancer label
                ATAC matrix
            Plot:
                Boxplot (Signal distribution -> Promoter vs Enhancer)

        c. Relationship between signal & distance to TSS
            Daten: 
                ATAC peaks + distance to nearest TSS (rechnen mit Transcript.csv)
                ATAC matrix
            Plot: 
                Scatterplot (Distance to TSS vs Signal intensity)

        d. Intronic enhancers vs others?
            Daten:
                ATAC matrix
                peaks annotieren?
            Plot:
                Boxplot (Signal per category (Intronic / Intergenic / Promoter))

    iii. Do related cell types cluster together based on ATAC signal?
        a. Does clustering reproduce known relationship?
            Daten: 
            Plot: 
                PCA on ATAC signal matrix → scatterplot
                UMAP on ATAC signal matrix
                Hierarchical clustering / dendrogram of cell types.

        b. Quantify similarity of cell types?
            Plot: 
                Heatmap (pairwise correlation matrix between samples)

    iv. Define different classes of peaks based on signal + variation
        a. Cluster CREs based on ATAC-signal
            Plot: 
                K-Means clustering / hierarchical clustering 8Peaks × Cell types9
                -> Cluster heatmap?

        b. Visualize behaviour of clustered regions
            Plot: 
                Lineplot (mean signal per cluster across cell types)

        c. Define cell lineage-specific CRE clusters?
            Plot: 
                For B-cells find clusters where B-cell signal >> others
                -> Violinplot? / heatmap.

        d. Differences between cell-lineage-specific CRE clusters → activity?
            Plot: 
                Cluster?
                über Differenzierung / Lineage?