# 2023 Workshop IGS Genome reconstruction - Day 02

# Reads mapping 

We will align the reads from some of the datasets using the `minimap2` aligner. It is a versatile one that can be used well with short illumina reads as well as long reads.

# Preparing the environment for mapping

```bash 
cd ~/igs_workshop/

# Installing an aligner, samtools for sam files work and igv
mamba create -n mapping -c bioconda minimap2 samtools igv

conda activate mapping 

```

# Preparing the directory 

```bash 
# create a new output folder for mappings
mkdir mapping 

# create a directory for the reference sequence
mkdir references
# download the most common reference for pestis
wget -O references/yersinia_pestis_A1122.fasta https://www.ebi.ac.uk/ena/browser/api/fasta/CP002956.1?download=true


# Aligning the reads from the sample ERRxx to the reference ref.fa
minimap2 -a -x sr references/yersinia_pestis_A1122.fasta raw_data/ERR9964620_1.fastq.gz raw_data/ERR9964620_2.fastq.gz > mapping/ERR9964620.sam  

# We could have also aligned the trimmed reads. Let's do it to compare afterwards
minimap2 -a -x sr references/yersinia_pestis_A1122.fasta trimming/ERR9964620_1_trimmed.fastq.gz trimming/ERR9964620_2_trimmed.fastq.gz > mapping/ERR9964620_trimmed.sam

```
[Publication](https://doi.org/10.1093/bioinformatics/bty191) | [Code](https://github.com/lh3/minimap2)

Inspect the resulting SAM file. Check the [SAM format specification](https://samtools.github.io/hts-specs/SAMv1.pdf).

### Visualization of the mapping (IGV)

```bash
# first, we need to convert the SAM file into a sorted BAM file to load it subsequently in IGV
samtools view -b -S mapping/ERR9964620.sam | samtools sort -@ 4 > mapping/ERR9964620.sorted.bam 
samtools index mapping/ERR9964620.sorted.bam 

# Let's also prepare the trimmed reads
samtools view -b -S mapping/ERR9964620_trimmed.sam | samtools sort -@ 4 > mapping/ERR9964620_trimmed.sorted.bam 
samtools index mapping/ERR9964620_trimmed.sorted.bam 


# start IGV browser and load the reference genome file (the FASTA) and the BAM file, inspect the output
igv &
```

### Practice what you learned

* We will compare with aligning the same read set to an other reference file.

```bash
# download an other reference
wget -o references/yersinia_pestis_SCPM-O-B-5942.fasta https://www.ebi.ac.uk/ena/browser/api/fasta/CP045258.1?download=true

```

* Align the reads to this new reference file `references/yersinia_pestis_SCPM-O-B-5942.fasta`.

* Construct a sorted bam file and visualize it into IGV 


### Alternative: Visualization of mapping (Tablet)

```bash
# open the GUI
tablet &

# load mapping file as 'primary assembly'
# ->  mapping/ERR9964620.sam

# load assembly file as 'Reference/consensus file'
# ->  references/yersinia_pestis_A1122.fasta
```
[Publication](http://dx.doi.org/10.1093/bib/bbs012) | [Code](https://ics.hutton.ac.uk/tablet/)

__Alternative ways to visualize such a mapping are given by (commercial software) such as Geneious or CLC Genomic Workbench.__





