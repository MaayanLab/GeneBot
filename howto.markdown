---
layout: page
title: How To Use
permalink: /howto/
---

## Functions

### Gene Summary 
GeneBot allows users to submit a gene of interest and outputs information pertaining to the gene searched. The **/gene** command provides a summary about the gene and links to various databases. 

The summary outputted is retrieved using the NCBI **Entrez Gene** database API. Links are provided to gene landing pages from various genomic tools that our lab has developed, including **Harmonizome**, **ARCHS4**, and **Geneshot**. 

✦ **Input Format:** `/gene <gene name>`

✦ **Example:** 
- Input: `/gene TP53`
- Output: 
![image](assets/images/summary_output.png)

### Gene Enrichment Analysis
GeneBot allows users to submit a gene set for enrichment analysis. When users enter a gene set, the **/geneset** command can be used to trigger gene enrichment analysis to be performed. Users can upload a csv file with the gene set for analysis by calling **@genebot**. Additionally, users can specify which gene-set library they want to be displayed in their results in Slack.

The gene set is analyzed using the **Enrichr** API. The bot will output a link to **Enrichr** for the gene set entered as well as summary statistics about the gene set. A bar graph displaying the top 10 enriched terms for the user selected gene-set library will attached as a pdf file. 

✦ **Input Format:** 
- Input (no library specified): 
    - `/geneset gene1, gene2, gene3... ` 
    - `/geneset gene1 gene2 gene3... `
- Input (library specified): 
    - `/geneset [library, gene1, gene2, gene3...] ` 
    - `/geneset [ library, gene1 gene2 gene3...] `
        - Gene list can be space or comma separated.
        - Library specified input must be contained by brackets.
- Input (file upload): 
    - `@genebot *file*` 
    - `@genebot library *file*` 

✦ **Example:** 
- Input: `/gene MAPK3, STAT1, CREB1`
- Output: 
![image](assets/images/enrichment_output.png)

✦ **Gene Libraries:**
When specifying a library for output, GeneBot will recognize **Enrichr** names or predefined short hands. Enrichr names for libraries can be found [here](https://amp.pharm.mssm.edu/Enrichr/#stats). Library short hands are available for most recent genesets for each database.
- Library short hands include:
    - GO = GO_Biological_Process_2018
    - MGI = MGI_Mammalian_Phenotype_Level_4_2019
    - KEGG = KEGG_2019_Human
    - CHEA = ChEA_2016
    - ENCODE = ENCODE_TF_ChIP-seq_2015
    - GWAS = GWAS_Catalog_2019

✦ **Help Commands:**
There are several built in help commands for performating enrichment analysis with GeneBot that can be called in Slack that provide concise summaries about different app features and functions. A list of all commands can be found by calling: `/geneset help?`

- `/geneset ?` → provides summary of how to use GeneBot for enrichment analysis  
- `/geneset library?` → provides instructions on how to specify library for output
- `/geneset fileupload?` → provides instructions on how to upload file for analysis
- `/geneset slashcommand?` → provides instructions on how to navigate /geneset command

### Gene Network Analysis
GeneBot allows users to submit a gene set for gene network analysis based on **protein-protein interactions** (PPI) and **gene-gene co-expression**. When users enter a gene set, the **/network** command can be used to trigger gene network analysis to be performed. 

The gene set is analyzed using the **Genes2Networks** API to generate generate a PPI subnetwork that connects the enriched genes and proteins with known protein-protein interactions. Additionally, the gene list is analyzed through a human gene correlation matrix from **ARCHS4** to find the top 5 most correlated genes to each input gene. The bot will output summary statistics about the gene set. A network graph displaying the data generated will attached as a pdf file. 

✦ **Input Format:** 
- Input: `/network gene1, gene2, gene3... ` 

✦ **Example:** 
- Input: `/gene BRCA1, BRCA2, STAT1, MAPK3`
- Output: 
![image](assets/images/network_output.png)

### Gene Learning Game
A major aim of GeneBot was to allow researchers to learn about genes as well. We created the **/learn** command to output a multiple choice question where users can match the correct summary to the gene in question. 

✦ **Example:** 
- Input: `/learn `
- Output: 
![image](assets/images/quiz_output.png)

For more details about workflow and data visualization analysis, check out the detailed user manual. 

Link to paper: 
