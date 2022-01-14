# GWAS enrichment analysis

# Gene overlap and Spearman s-correlations for GWAS enrichment analysis

FUMA_GWAS <- read.csv("GWAS_magma.genes.out.csv")#file from FUMA analysis using summary statistics from each GWAS

module <- read.csv("pDG_black_network_gene_list.csv") #this file contains the gene list for the WGCNA module and KME for each gene

FUMA_GWAS$GENE

module$hsapiens_homolog_ensembl_gene

module$commonGenes <- gene_Annot[match(module$hsapiens_homolog_ensembl_gene, FUMA_GWAS$GENE),]$P

module2 <- module[complete.cases(module$commonGenes),]

colnames(module2) [7]<- "p_gwas"

cor.test(module2$PValue, module2$p_gwas, method = "spearman", alternative = "less")
