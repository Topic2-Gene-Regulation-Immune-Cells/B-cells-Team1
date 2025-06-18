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
    Done

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
    Done

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
    Done


2. Determine the relationship between the chromatin landscape and gene expression

    i. Does clustering of the gene expression matrix show the same relationships between cell types as the ATAC-seq data?
    Daten:
      - Gene expression matrix (normalized, logCPM/TPM/etc.)
      - ATAC signal matrix per peak
    Plot:
      - Dendrogramme / Heatmaps (clustering nach Zelltypen)
      - Vergleich ATAC vs. RNA (z. B. UMAP / PCA)

    ii. Can one cluster genes based on their expression profiles?
        a. Can you determine a specific set of genes for your cell lineage?
            Daten:
                - Gene expression matrix
                - Cell type annotation
            Plot:
                - Heatmap oder UMAP (gene clusters)
                - Marker-Gene-Listen für Zelllinie extrahieren

        b. Are there subclusters of special interest?
            Daten:
                - Cluster-Zuordnung der Gene
                - Zelltyp Annotation
            Plot:
                - Heatmap mit hervorgehobenen Subclustern
                - Boxplots: Expression in Subclustern

    iii. Can one use correlation analysis and distance information to associate ATAC-seq regions with gene expression?

        a. Where are associated CREs located with respect to the TSS?
            Daten:
                - ATAC matrix (Signalstärke pro Peak)
                - TSS-Koordinaten (z. B. GENCODE)
                - Korrelationsmatrix ATAC-Peak ↔ Genexpression
                - Genexpression matrix
            Plot:
                - Histogramm: Entfernung assoziierter CREs zum TSS
                - CDF-Plots für verschiedene Zelltypen oder CRE-Typen

        b. Where are the most associated CREs located?
            Daten:
                - Peak-Gen-Korrelationen (z. B. |r| > 0.5, p < 0.05)
                - Gen-Koordinaten (TSS)
                - CRE Annotation (Promoter, Enhancer, Intergenic)
            Plot:
                - Histogramm / Density Plot: Anzahl assoziierter CREs pro Regionstyp
                - Boxplots: Signal nach Gen-Distanz oder Regionstyp

        c. How many CREs are associated with genes?
            Daten:
                - Peak ↔ Gene Assoziationen (nach Korrelation/Distanz gefiltert)
            Plot:
                - Histogramm: Anzahl CREs pro Gen
                - Balkenplot: #Gene mit 0, 1, 2, ... CREs

        d. Is every promoter associated with a gene?
            Daten:
                - Promoter-Regionen (±1 kb um TSS)
                - Peak-Annotation (Promoter zugeordnet?)
            Plot:
                - Anzahl Promoter mit / ohne Genassoziation

         e. Are some promoters associated with other genes?
            Daten:
                - Promoter-Peaks
                - Gen-IDs der assoziierten Gene
            Plot:
                - Histogramm: Promoter → #Gene
                - Netzwerkplot (optional)

        f. What is the closest associated CRE to a gene?
            Daten:
                - Distanzen: Gen-TSS ↔ Peak-Mitte
                - Assoziationen aus Korrelation oder Nähe
            Plot:
                - Histogramm: minimale Entfernung assoziierter CREs zu jedem Gen
                - Scatterplot: Genexpression vs. CRE-Distanz

        g. Are there CREs that control several genes?
            Daten:
                - Peak → Gen Assoziationen
                - Genexpression Matrix
            Plot:
                - Histogramm: #Gene pro CRE
                - Sankey-Plot: CRE → mehrere Gene

    iv. Can one use regression to associate CREs with gene expression?

        a. How much of the variance of gene expression can be explained for each gene with this approach?
            Daten:
                - ATAC matrix (Signalstärke pro Peak)
                - Genexpression matrix
                - Peak ↔ Gene Mapping (z. B. CREs im 100 kb Umkreis vom TSS)
            Plot:
                - Histogramm: R² (Erklärte Varianz) pro Gen
                - Balkenplot: Top-Gene mit höchster erklärter Varianz

        b. How do the coefficients differ when it is performed on your cell lineage alone?
            Daten:
                - ATAC + Expression Daten nur für Zelllinie (z. B. B-Zellen)
                - Regressionsergebnisse (z. B. Ridge/Lasso Coefficients)
            Plot:
                - Boxplot: Verteilung der Regressionskoeffizienten (gesamt vs. Zelllinie)
                - Heatmap: Unterschiede der Gewichtungen zwischen Zelltypen

        c. Which CREs control your cell lineage specific genes?
            Daten:
                - Zelltypspezifische Gene (z. B. aus DE-Analyse oder Clustering)
                - Regressionsergebnisse CRE → Gen (auf Zelltyp gefiltert)
            Plot:
                - Balkenplot: Top-CREs für Zelltypspezifische Gene
                - Netzwerk: CRE → Zelltypspezifische Gene

        d. How do the results of this analysis differ from pure association via correlation?
            Daten:
                - Korrelationsmatrix Peak ↔ Gene
                - Regressionskoeffizienten
            Plot:
                - Scatterplot: Korrelation vs. Regressionskoeffizient
                - Balkenplot: Vergleich #assoziierter CREs (Korrelation vs. Regression)

        e. Are there differences between activating and repressing CREs?
            Daten:
                - Regressionskoeffizienten (Vorzeichen: + aktivierend, – repressiv)
                - Peak-Annotation (z. B. Enhancer, Promoter, Intergenic)
            Plot:
                - Histogramm: Anteil aktivierender vs. repressiver CREs
                - Boxplots: Abstand zum TSS für aktivierend vs. repressiv
                - Sankey: CRE → Gen mit Effekt-Richtung

            
        f. How many genes are mainly regulated by repressing CREs, and can promoters act through repression?
            Daten: 
                - Regressionsergebnisse, CRE-Typen
            Plot: 
                - Balkenplot: #Gene mit negativem Hauptregulator, Anteil Promoter unter Repressoren

        g. Where are repressing CREs located compared to activating CREs?
            Daten: 
                - Koordinaten der CREs mit negativem/positivem Einfluss
            Plot: 
                - Histogramm / Density Plot: Entfernung zum TSS (nach Effektgruppe)

        h. Are there CREs that are repressing for one gene but activating for another gene?
            Daten: 
                - CRE → Gen Mapping + Regressionskoeffizienten
            Plot: 
                - Sankey-Plot oder Netzwerk: CRE mit gemischtem Effekt

        i. Does CRE clustering change if one includes the effect direction on gene expression?
            Daten: 
                - CRE-Correlation / Regressionsmatrix + Effekt-Richtung (Zeichen des Koeffizienten)
            Plot: 
                - Heatmap: CRE-Clustering mit/ohne Effektzeichen


            
        