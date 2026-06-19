# Ferroptosis-Cardiac-Project
Integrated Transcriptomic Profiling of Ferroptosis-Related Genes in Myocardial Infarction and Heart Failure

## OVERVIEW
Cardiovascular diseases (CVDs), particularly Myocardial Infarction (MI) and Heart Failure (HF),
remain the leading causes of death worldwide. This project investigates the role of ferroptosis,
an iron-dependent, lipid-peroxidation-driven form of regulated cell death, in these conditions
using integrated transcriptomics and bioinformatics.
 
By combining publicly available gene expression datasets (GEO/NCBI) with the FerrDb ferroptosis
gene database, this study identifies robust ferroptosis-related molecular signatures, hub genes,
and pathways that may serve as biomarkers or therapeutic targets in MI and HF.

## BACKGROUND

Ferroptosis is a distinct programmed cell death pathway characterized by iron-mediated
accumulation of lipid peroxides and oxidative damage to cellular membranes. Its key regulatory
axis involves GPX4, System XC-, NRF2, and the ALOX gene family.
 
Unlike apoptosis or necrosis, ferroptosis has only recently been linked to cardiac injury.
Experimental studies confirm its role in myocardial ischaemia-reperfusion injury, acute MI, and
progressive heart failure. Despite this, the precise molecular landscape of ferroptosis across
MI and HF, and the genes driving it, remains poorly characterized.
 
This project addresses that gap through an integrated, multi-dataset transcriptomic approach.

 ## DATASETS

All transcriptomic data were retrieved from the NCBI Gene Expression Omnibus (GEO):
https://www.ncbi.nlm.nih.gov/geo/
 
  Disease                 | Dataset    | Description
  ------------------------|------------|------------------------------
  Myocardial Infarction   | GSE48060   | MI vs. control cardiac tissue
  Myocardial Infarction   | GSE66360   | MI gene expression profiling
  Myocardial Infarction   | GSE97320   | MI transcriptome dataset
  Heart Failure           | GSE5406    | HF cardiac tissue expression
  Heart Failure           | GSE57338   | Dilated cardiomyopathy / HF
  Heart Failure           | GSE141910  | HF multi-sample dataset
 
Ferroptosis gene reference:
  FerrDb (http://www.zhounan.org/ferrdb/) -- a manually curated resource for ferroptosis
  regulators and markers. 


## METHODOLOGY
 
  GEO Datasets (MI x3, HF x3)
          |
          
  Data Preprocessing & Normalization
          |
          
  Differential Gene Expression Analysis
  (t-test, log2FC > 0.05, p-value < 0.05)
          |
          
  Ferroptosis Gene Overlay (FerrDb)
          |
          |---- MI: Ferroptosis DEGs identified
          |
          +---- HF: Consensus-based integration across 3 datasets
                          |
                          
          Functional Enrichment Analysis
            -- Gene Ontology (GO) via Enrichr
            -- KEGG Pathway Analysis via Enrichr / Reactome
                          |
                          
          Protein-Protein Interaction (PPI) Network
            -- STRING database --> Hub Gene Identification
                          |
                          
          Visualization
            -- Heatmaps
            -- Volcano Plots
## Key Steps
  Preprocessing & Normalization
    Missing value removal, log-transformation, dataset-level normalization.
 
  Differential Expression
    Student's t-test between disease and control groups.
    Threshold: |log2FC| > 0.05, p-value < 0.05.
 
  Ferroptosis Gene Screening
   DEG overlap with FerrDb database to isolate ferroptosis-specific signatures.
 
  Consensus Integration (HF)
    Consensus-based approach across three independent HF datasets to improve reproducibility.
 
  Functional Enrichment
    GO Biological Process, KEGG 2026, Reactome 2024 via the Enrichr platform.
 
  Network Analysis
    PPI network construction using STRING.
    Hub gene identification by node connectivity.
    
## KEY FINDINGS
Myocardial Infarction
  - 38 ferroptosis-associated DEGs identified across MI datasets.
  - Notable genes: IGF2BP3, THBS1, METTL3, HNRNPD, PDK4, YME1L1.
  - Hub genes: IGF2BP3, THBS1, METTL3, HNRNPD, PDK4.
  - Key pathways: NF-kB signaling, arachidonic acid metabolism, calcium signaling,
    ECM-receptor interaction, ROS metabolism, inflammatory response.
 
Heart Failure
  - 6 consensus ferroptosis genes identified: ALOX5, ESR1, SNCA, ATP1A3, FRZB, XIST.
  - Key genes: ALOX5, ESR1, SNCA.
  - Key pathways: Lipid peroxidation, oxidative stress, Wnt signaling (FRZB),
    estrogen signaling (ESR1).
 
Comparative Insights
  Feature              | Myocardial Infarction          | Heart Failure
  ---------------------|--------------------------------|-------------------------------
  Ferroptosis DEGs     | 38                             | 6 (consensus)
  Primary mechanism    | Acute ischaemic injury         | Chronic oxidative stress
  Hub genes            | IGF2BP3, THBS1, METTL3        | ALOX5, ESR1, SNCA
  Network complexity   | High (many interactions)       | Lower, more specific
  Non-coding RNA       | Multiple ncRNAs                | XIST (lncRNA)

## TOOLS AND SOFTWARE

  Tool                          | Purpose
  ------------------------------|------------------------------------------
  Python (pandas, numpy, scipy) | Data preprocessing, DEG analysis
  Enrichr                       | GO and KEGG pathway enrichment
  STRING                        | PPI network construction
  FerrDb                        | Ferroptosis gene reference database
  GEO / NCBI                    | Transcriptomic dataset retrieval
  Matplotlib / Seaborn          | Heatmaps and volcano plots
 
## REPOSITORY STRUCTURE
Repository Structure

data/       > GEO datasets and FerrDb gene lists
scripts/    > Data preprocessing and DEG analysis
results/    > Enrichment analysis and PPI outputs
figures/    > Heatmaps, volcano plots, and network visualizations
README.md   > Project documentation

## RESULTS SUMMARY
  Volcano Plots
  Generated for all six datasets (MI: GSE48060, GSE66360, GSE97320; HF: GSE5406, GSE57338,
  GSE141910), visualizing log2 fold change vs. -log10(p-value) for ferroptosis-related DEGs.
 
Heatmaps
  Expression heatmaps generated for ferroptosis gene signatures across MI and HF sample groups,
  revealing distinct clustering patterns between disease and control.
 
Enrichment Highlights -- Myocardial Infarction
  - Oxidative stress response and ROS metabolism
  - NF-kB signaling pathway
  - Arachidonic acid / lipid metabolism
  - Apoptosis-regulatory pathways (crosstalk with ferroptosis)
  - Calcium signaling
  - ECM-receptor interaction
 
Enrichment Highlights -- Heart Failure
  - Lipid peroxidation and ALOX5-mediated ferroptosis
  - Estrogen receptor signaling (ESR1 downregulation)
  - Wnt signaling pathway (FRZB)
  - Mitochondrial dysfunction (SNCA, ATP1A3)
  - lncRNA-mediated epigenetic regulation (XIST)
