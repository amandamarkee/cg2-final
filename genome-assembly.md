# Genome Assembly for _Argiope argentata_ and _Oligotoma nigra_

## Estimating Genome Size from Raw Reads (KMC)
- [K-Mer Counter (KMC)](https://github.com/refresh-bio/KMC) is a quality assessment tool bioinformatics tool designed to efficiently count the occurrences of k-mers (short DNA sequences of length k) within a set of reads from a genome/

First, to run KMC and estimate genome size, create a directory for the output data and script.
```
mkdir kmc
```

I then copied the following script into the new directory that contained the raw Hifi reads:
```
#!/bin/bash
#SBATCH --time=6:00:00   # walltime
#SBATCH --ntasks=24   # number of processor cores (i.e. tasks)
#SBATCH --nodes=1   # number of nodes
#SBATCH --mem-per-cpu=14336M   # memory per CPU core
#SBATCH -J "kmc.sh"   # job name
#SBATCH --mail-user=amarkee@amnh.org   # email address
#SBATCH --mail-type=BEGIN
#SBATCH --mail-type=END
#SBATCH --mail-type=FAIL


# Set the max number of threads to use for programs using OpenMP. Should be <= ppn. Does nothing if the program doesn't use OpenMP.
export OMP_NUM_THREADS=$SLURM_CPUS_ON_NODE

# LOAD MODULES, INSERT CODE, AND RUN YOUR PROGRAMS HERE
module load miniconda3/4.12-pws-472
conda activate kmc
kmc -k21 -t24 -m14 -ci1 -cs10000 @files.txt reads tmp/
kmc_tools transform reads histogram reads.histo -cx10000
```

```
Note: files.txt was generated by creating a list of all fastq.gz files I wanted to run KMC on using the following code:
ls *fastq.gz > files.txt
fastqc m84100_240417_025302_s2_fastq.gz # raw reads for O.nigra in directory
fastqc m84100_240128_044323_s3.hifi_reads.bc1045.fastq.gz # raw reads for A.argentata in directory
```

Once KMC outputs the `reads.histo` file, this can be visualized in the [GenomeScope2 webserver](http://genomescope.org/genomescope2.0/). 
Once there, I set the kmer length is set to `21` and the ploidy to `2` based on each organisms biology. Then, I dragged and dropped each `reads.histo` file into the submission box. 
The output looks as follows:

[_Argiope argentata_](http://genomescope.org/genomescope2.0/analysis.php?code=r0EqXydetoWDM8NgU89F) KMC results can be found here with the following results:

- 1,673,872,525bp in predicted size, in otherwords approximately 1.6 Gbp
- 99.5% homozygosity, and 0.497% heterozygosity across the genome
- ~50x whole genome coverage, with 26.7x heterozygous coverage (kcov), meaning k-mer coverage for heterozygous bases.
  

<img width="791" alt="Screenshot 2024-12-02 at 2 39 01 PM" src="https://github.com/user-attachments/assets/90f8c973-3274-4a3d-ba50-b37d4189eeb5">
<img width="636" alt="Screenshot 2024-12-02 at 2 39 10 PM" src="https://github.com/user-attachments/assets/2052294a-f1b5-433a-8b0a-be44ce94aaf1">

<br>
<br>

[_Oligotoma nigra_](http://genomescope.org/genomescope2.0/analysis.php?code=OUPPsCUp1f63PBTieO1N) KMC results can be found here with the following results:

<img width="804" alt="Screenshot 2024-12-02 at 2 41 38 PM" src="https://github.com/user-attachments/assets/0752523f-d905-4a40-b8c4-5757cba42f9c">
<img width="643" alt="Screenshot 2024-12-02 at 2 41 49 PM" src="https://github.com/user-attachments/assets/21fd8b99-7873-4bcc-846d-67403413862d">

- 2,607,416,052bp in predicted size, in otherwords approximately 2.6 Gbp
- 98.1% homozygosity, and 1.93% heterozygosity across the genome
- ~30x whole genome coverage, with 13.9x whole genome coverage (kcov) meaning k-mer coverage for heterozygous bases.

