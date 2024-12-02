# Genomic characterization of arthropod silk genes in the silver garden spider _Argiope argentata_ and the black webspinner _Oligotoma nigra_

The silver garden spider (_Argiope argentata_) is an orb-weaving spider in the family Araneidae, with seven distinct types of silk: major ampullate (MaSp), minor ampullate (MiSp), flagelliform (FlAg), aggregate (AgSp), aciniform (AcSp), tubuliform (TuSp) and pyriform (PySp). Each silk type is characterized based on the gland they originate from, and have variation in the properties of silk the produce. Spider fibroins, further referred to as _spidroins_, are a family of silk proteins produced by long, highly repetitive, glycine-rich genes.

</br>
<img width="1448" alt="Screenshot 2024-06-27 at 5 32 20 PM" src="https://github.com/amandamarkee/spidroins/assets/56971761/c0e7bfcb-6dc7-4d2d-8e73-1a88bfe60c22">
<br/><br/>


The black webspinner (_Oligotoma nigra_) is a non-model insect group in the order Embioptera. Webspinners use silk to build protetive encasements for their colonies known as silken galleries. Like other insects, the primary silk gene responsible for producing silk-proteins is the _heavy chain fibroin_, referred to as H-fib in most insect silk literature. 

![O  nigra silk, female](https://github.com/user-attachments/assets/75a4deb8-7055-4f10-94aa-4185ca7ac3f9)

Here, I take a comparative genomics approach to comparing silk genes between these two distantly related arthropod species, to better understand the convergent evolution of the silk system. By characterizing unknown spidroins and fibroins, I hope to glean insight into the diversification and molecular evolution of silk genes in these two species. In order to accomplish this, here I sequence two new long-read genomes using PacBio Revio to produce high-quality referenc genomes for each taxa. I use a combination of bioinformatic tools to perform whole genome feature annotation (also known as structural annotatiot), and through manual annotation of silk genes based on homology and RNAseq mapping.


## Bioinformatic workflow for _Argiope argentata_ and _Oligotoma nigra_ assembly and annotation

1) Raw Read Quality Control with FastQC
2) Whole Genome Assembly with Hifiasm
3) Assembly Quality Control with BUSCO, assemblystats.py & QUAST, and duplicate purging
4) Putitive Spidroin Identification with BLASTx and BioPython
5) Spidroin/Fibroin Extraction with Geneious and Samtools
6) Annotation of Intron/Exon Boundaries _ab initio_ or trained with Augustus
7) Whole Genome Annotation with Braker3

