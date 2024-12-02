# Genomic characterization of arthropod silk genes in the silver garden spider _Argiope argentata_ and the black webspinner _Oligotoma nigra_

## Introduction
The ability to produce silk has evolved convergently over millions of years across arthropod lineages, resulting in a diverse array of silk types, uses and displays. Despite the considerable phylogenetic distance, there are striking similarities in the structure and function of silk systems between insects and spiders, both morphologically and genetically. All spiders and approximately 23 lineages of insects produce silk, yet very little is comprehensively known about the genetic variation of this important trait outside of model organisms. This is in part due to challenges in sequencing the genes (fibroins) responsible for diverse phenotypes of silk, due to their length (> 25kb) and high repetition. Long read sequencing platforms have revolutionized silk research in the last decade, providing the first opportunity to capture these repetitive domains, and analyze silk within a comparative framework. For my CG2 final project, I plan to assemble and annotate whole genomes from a non-model insect (Order Embioptera: Oligotoma nigra) and spider (Order: Araneae: Argiope argentata). 

The aim is to compare genome quality, allelic variation, amino acid composition, and silk gene architecture. This project will build upon work I have started for the first chapter of my dissertation by incorporating short read RNA-seq data generated in Comparative Genomics 1 for genome annotation, creating a new genome annotation and assembly for _Oligotoma nigra_, and by characterizing the first ever heavy chain fibroin silk gene for this insect order. I plan to use the long read assembler HiFiasm for assembling my long read genome and haplotype assemblies, QC python scripts and BUSCO for evaluating assembly quality, and either Braker3 for whole genome feature annotation. A combination of BLAST and genome visualization tools will be used to manually annotate the repetitive silk genes, as these often do not get identified in automated feature annotation pipelines.

## Background
The silver garden spider (_Argiope argentata_) is an orb-weaving spider in the family Araneidae, with seven distinct types of silk: major ampullate (MaSp), minor ampullate (MiSp), flagelliform (FlAg), aggregate (AgSp), aciniform (AcSp), tubuliform (TuSp) and pyriform (PySp). Each silk type is characterized based on the gland they originate from, and have variation in the properties of silk the produce. Spider fibroins, further referred to as _spidroins_, are a family of silk proteins produced by long, highly repetitive, glycine-rich genes.

</br>
<img width="1448" alt="Screenshot 2024-06-27 at 5 32 20 PM" src="https://github.com/amandamarkee/spidroins/assets/56971761/c0e7bfcb-6dc7-4d2d-8e73-1a88bfe60c22">
<br/><br/>


The black webspinner (_Oligotoma nigra_) is a non-model insect group in the order Embioptera. Webspinners use silk to build protetive encasements for their colonies known as silken galleries. Like other insects, the primary silk gene responsible for producing silk-proteins is the _heavy chain fibroin_, referred to as H-fib in most insect silk literature. 

![O  nigra silk, female](https://github.com/user-attachments/assets/75a4deb8-7055-4f10-94aa-4185ca7ac3f9)

Here, I take a comparative genomics approach to comparing silk genes between these two distantly related arthropod species, to better understand the convergent evolution of the silk system. By characterizing unknown spidroins and fibroins, I hope to glean insight into the diversification and molecular evolution of silk genes in these two species. In order to accomplish this, here I sequence two new long-read genomes using PacBio Revio to produce high-quality referenc genomes for each taxa. I use a combination of bioinformatic tools to perform whole genome feature annotation (also known as structural annotatiot), and through manual annotation of silk genes based on homology and RNAseq mapping.


## Bioinformatic workflow for _Argiope argentata_ and _Oligotoma nigra_ assembly and annotation

1) Genome Size Prediction with KMC/GenomeScope
2) Whole Genome Assembly with Hifiasm
3) Assembly Quality Control with BUSCO and assemblystats.py 
4) Putitive Spidroin/Fibroin Identification with BLASTx and BioPython
5) Spidroin/Fibroin Extraction with Geneious and Samtools
6) Annotation of Intron/Exon Boundaries _ab initio_ or trained with Augustus
7) Whole Genome Annotation with Braker3

