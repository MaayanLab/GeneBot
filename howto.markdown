---
layout: page
title: How To Use
permalink: /howto/
---

## GeneBot Functions

### Gene Summary 
GeneBot enables users to submit a human gene of interest and outputs information pertaining to the searched gene. The **/gene** command provides a summary about the gene and links to various databases. 

The summary outputted is retrieved using the NCBI **Entrez Gene** database API. Links are provided to gene landing pages from various genomic tools that the [Ma'ayan Lab](https://labs.icahn.mssm.edu/maayanlab/) developed, including [**Harmonizome**](https://amp.pharm.mssm.edu/Harmonizome/), [**ARCHS4**](https://amp.pharm.mssm.edu/archs4/), and [**Geneshot**](https://amp.pharm.mssm.edu/geneshot/). 

✦ **Input Format:** `/gene <gene name>`

✦ **Example:** 
- Input: `/gene TP53`
- Output: 
![image](assets/images/summary_output.png)

### Gene Enrichment Analysis
GeneBot enables users to submit a gene set for enrichment analysis. The /geneset command can be used to perform gene enrichment analysis by listing valid Entrez human gene symbols following the command. Alternatively, users can upload a CSV file with the gene set for analysis by calling **@genebot**. Additionally, users can specify which gene-set library they want to be displayed in their results in Slack.

The gene set is analyzed using the [**Enrichr API**](https://amp.pharm.mssm.edu/Enrichr/help#api). The bot will output a link to [**Enrichr**](https://amp.pharm.mssm.edu/Enrichr/) for the gene set entered as well as summary statistics about the gene set. A bar graph displaying the top 10 enriched terms for the user selected gene-set library will be attached as a pdf file. 

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
    - `@genebot geneset *file*` 
    - `@genebot geneset library *file*` 
        - [Here](/samplegenes.csv) is a sample file that is properly formatted with a gene set. 

✦ **Example:** 
- Input: `/geneset MAPK3, STAT1, CREB1`
- Output: 
![image](assets/images/enrichment_output.png)

✦ **Gene Libraries:**
When specifying a library for output, GeneBot will recognize full **Enrichr** library names or predefined short hands. Full Enrichr library names can be found [here](https://amp.pharm.mssm.edu/Enrichr/#stats). Library short hands are available for several widely-used gene set libraries.
- Library short hands include:
    - GO = GO_Biological_Process_2018
    - MGI = MGI_Mammalian_Phenotype_Level_4_2019
    - KEGG = KEGG_2019_Human
    - CHEA = ChEA_2016
    - ENCODE = ENCODE_TF_ChIP-seq_2015
    - GWAS = GWAS_Catalog_2019

### Gene-Gene Network Analysis
GeneBot enables users to submit a gene set for gene-gene network analysis based on **protein-protein interactions** (PPI) and **gene-gene co-expression**. When users enter a gene set, the **/network** command can be used to trigger the constructions of a gene-gene network.

The gene set is analyzed using the [**Genes2Networks**](https://amp.pharm.mssm.edu/G2N/) API to generate a PPI subnetwork that connects the genes and proteins with known protein-protein interactions and gene-gene co-expression associations. Co-expression correlations are determined via a human gene correlation matrix from [**ARCHS4**](https://amp.pharm.mssm.edu/archs4/) to find the top 5 most correlated genes to each input gene. The bot will output summary statistics about the gene set. A network graph displaying the interactions between the input genes will be attached as a PDF file. 

✦ **Input Format:** 
- Input: `/network gene1, gene2, gene3... ` 

✦ **Example:** 
- Input: `/network BRCA1, BRCA2, STAT1, MAPK3`
- Output: 
![image](assets/images/network_output.png)

### Gene Learning Game
GeneBot also contains an interactive game that can be played to learn how to memorize gene names and their known functions. We created the **/learn** command to output a multiple choice question where users can match the correct summary to the gene in question. 

✦ **Example:** 
- Input: `/learn `
- Output: 
![image](assets/images/quiz_output.png)

### Help Commands:
A list of all commands can by accessed by calling: `@genebot help`

✦ **Gene Summary Help:**
If a user needs help with using the **/gene** command to retrieve a summary about a gene, they can call the following command `/gene-help`.

✦ **Enrichment Analysis Help:**
There are several built in help commands for performng enrichment analysis with GeneBot that can be called in Slack to provide concise summaries about different app features and functions. A list of all enrichment analysis help commands can be found by calling: `/geneset-help`

- `/geneset-help ?` → provides summary of how to use GeneBot for enrichment analysis  
- `/geneset-help library?` → provides instructions on how to specify library for output
- `/geneset-help fileupload?` → provides instructions on how to upload file for analysis
- `/geneset-help slashcommand?` → provides instructions on how to navigate /geneset command

If you have any questions about how to use GeneBot, please contact us at <mailto:maayanlabapps@gmail.com>.

