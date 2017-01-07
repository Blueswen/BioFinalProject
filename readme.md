# Bioinformatic Final Project
Final Project on 1051.​Theory and Practice of Bioinformatics at NCCU CS

### Goal
Reproduce [Shiao, M.-S. S. et al. Expression Divergence of Chemosensory Genes between Drosophila sechellia and Its Sibling Species and Its Implications for Host Shift. Genome Biol Evol 7, 2843–58 (2015)](https://www.ncbi.nlm.nih.gov/pubmed/26430061)

### Members
1. [Blueswen](https://github.com/Blueswen): Write Nextflow Script

### Data
1. [Sample Data]()
2. [Experiment Data and Results]()

### Dependencies
1. [TopHat](https://ccb.jhu.edu/software/tophat/index.shtml): RNA-Seq reads mapping
2. [Cufflinks](http://cole-trapnell-lab.github.io/cufflinks/): Transcriptome assembly and differential expression analysis for RNA-Seq
3. [CummeRbund](http://compbio.mit.edu/cummeRbund/): R package for data visualiztion
4. [NextFlow](https://www.nextflow.io/)

### Usage
1. Prepare data: fastq files, fasta file, gtf file
2. Prepare Bowtie index
  ```
  $ mkdir sample/genome
  $ bowtie2-build sample/genome.fa sample/genome/genome
  ```
3. Prepare fqlist file and grouplist files
  * fqlist file example:
  ```
  ID001_1.fastq,ID001_2.fastq
  ID002_1.fastq,ID002_2.fastq
  ID003_1.fastq,ID003_2.fastq
  ID004_1.fastq,ID004_2.fastq
  ...
  ```
  * grouplist file example:
  ```
  ID001,ID002,...
  ID003,ID004,...
  ...
  ```
4. Execute Nextflow script
  ```
  $ nextflow main.nf --p 8 --fqlist sample/fqlist.txt\
                      --fqpath sample/fq/GSE67587/\
                      --grouplist sample/grouplist.txt\
                      --genome sample/genome/genome
                      --gtf sample/gene.gtf\
                      --fa sample/genome.fa\
                      --output results/\
  ```
5. Execute R Script
  ```
  $ R plot.r -i results/diff_out -o results/plot/
  ```

### Q&A
1. Install CummeRbund Problems
  1. [Install  CummeRbund](https://bioconductor.org/packages/release/bioc/html/cummeRbund.html)
  2. [Upgrade Bioconductor to the latest version available for this version of R](https://rdrr.io/bioc/BiocInstaller/man/BiocUpgrade.html)
  3. [Question: errors when installing cummeRbund package](https://support.bioconductor.org/p/61555/)

### Reference
1. [Shiao, M.-S. S. et al. Expression Divergence of Chemosensory Genes between Drosophila sechellia and Its Sibling Species and Its Implications for Host Shift. Genome Biol Evol 7, 2843–58 (2015).](https://www.ncbi.nlm.nih.gov/pubmed/26430061)
2. [Trapnell, C. et al. Differential gene and transcript expression analysis of RNA-seq experiments with TopHat and Cufflinks. Nat Protoc 7, 562–578 (2014).](http://www.nature.com/nprot/journal/v7/n3/full/nprot.2012.016.html)
