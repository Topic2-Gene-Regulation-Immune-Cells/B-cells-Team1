1. Determine differences and similarities of the chromatin landscape between immune cells:
    i. How variable is the chromatin signal within cells?
        a. Is the signal dependent on sequencing depth, number of input cells, QC metric?
            Daten: 
                ATAC matrix: Signal pro Peak pro Sample
                QC matrix: columns: InputCellNumber, PF.reads, %fragment_1Kb_TSS, Paired.read.after.removing.PCR.duplication
            Plot: 
                Scatterplot (ATAC signal vs InputCellNumber, PF.reads, etc.)
                Correlation heatmap (mean ATAC signal and QC metrics)

        b. Should some cell types be removed / normalization?
            Daten: 
                ATAC matrix
                QC matrix: Celltype 
            Plot: 
                Boxplot (ATAC signal distribution per CellType -> B-Zellen einzeln anschauen)
                Outlier untersuchen 

    ii. How variable is the chromatin signal for CREs across cells?
        a. Should peaks be removed due to lack of signal?
            Daten: 
                ATAC matrix
            Plot: 
                Histogram -> mean signal across all samples for each Peak (Peaks mit low mean signal dann evtl. entfernen)

        b. Do promoters exhibit specific signals vs enhancers?
            Daten:
                Transcript + Exon + TF motif association (Peak zuordnen -> Promoter/ Enhancer)
                ATAC matrix
            Plot:
                Boxplot (Signal distribution -> Promoter vs Enhancer)

        c. Relationship between signal & distance to TSS
            Daten: 
                Transcript + Exon + TF motif association (ATAC peaks + distance to nearest TSS)
                ATAC matrix 
            Plot: 
                Scatterplot (Distance to TSS vs Signal intensity)

        d. Intronic enhancers vs others?
            Daten:
                ATAC matrix
                Transkripi (peaks annotieren?)
            Plot:
                Boxplot (Signal per category (Intronic / Intergenic / Promoter))

    iii. Do related cell types cluster together based on ATAC signal?
        a. Does clustering reproduce known relationship?
            Daten: 
                ATAC matrix
                CellType 
            Plot: 
                PCA on ATAC signal matrix
                UMAP on ATAC signal matrix
                Hierarchical clustering / dendrogram of cell types

        b. Quantify similarity of cell types?
            Daten: 
                ATAC matrix
                CellType 
            Plot: 
                Heatmap (pairwise correlation matrix between samples/ CellTypes)

    iv. Define different classes of peaks based on signal + variation
        a. Cluster CREs based on ATAC-signal
            Daten: 
                ATAC matrix
            Plot: 
                K-Means clustering / hierarchical clustering (Peaks × Cell types)
                heatmap (of clustered peaks)

        b. Visualize behaviour of clustered regions
            Daten: 
                    ATAC matrix
                    iv, a.
            Plot: 
                Lineplot (mean signal per cluster across cell types)

        c. Define cell lineage-specific CRE clusters?
            Daten:
                ATAC matrix
                iv, a.
            Plot: 
                For B-cells find clusters where B-cell signal >> others
                -> Violinplot? / heatmap (cluster signals and compare across CellTypes)

        d. Differences between cell-lineage-specific CRE clusters → activity?
            Daten: 
                ATAC matrix 
                iv, a.
            Plot: 
                Cluster actibity plot
                über Differenzierung / Lineage?