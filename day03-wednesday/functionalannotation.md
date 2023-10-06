# 2023 Workshop IGS Genome reconstruction - Day 03

To create meaningful insights into our NGS data, we will today use [abricate](https://github.com/tseemann/abricate)


## Lecture 
Find the slides on functional annotation [here](https://docs.google.com/presentation/d/1KSLmUZqPlSHMm0BelPOqufW1w5fnIa00442hGbeujpw/edit#slide=id.g2825e3f29cd_0_72)


## Hands-on 

### Setup of abricate

```bash
conda install -c conda-forge -c bioconda -c defaults abricate
abricate --check
abricate --list
```

### Usage of abricate abricate

```bash
conda activate abricate
mkdir /home/igsw/igs_workshop/abricate_results
# Familiarize yourself with the tool:
abricate --help
```

#### generate sheet with links to files (called fofn by abricate)
```bash
cut -f 2 /home/igsw/igs_workshop/aquamis_results/Assembly/assembly/samples.tsv > /home/igsw/igs_workshop/abricate_results/fofn.txt
```

#### execute abricate on your selected files
```bash
abricate --fofn /home/igsw/igs_workshop/abricate_results/fofn.txt > /home/igsw/igs_workshop/abricate_results/amr_results.csv
```

### Further analysis of results

#### Look at your results
```bash
less home/igsw/igs_workshop/abricate_results/amr_results.csv
```

#### Let's find out where our AMR-Genes are located

1) find on which contigs the AMR-Genes are found from the result file
2) find the sequence of the contig (hint: in the Assembly file)
3) copy the sequence of the contig 
4) go to the [online BLAST website](https://blast.ncbi.nlm.nih.gov/Blast.cgi?PROGRAM=blastn&PAGE_TYPE=BlastSearch&LINK_LOC=blasthome)
5) Paste the sequence into to the mask and BLAST. This will search for possibly matching references and create an alignment of your contig to all sequences in the NCBI Nucleotide collection (nt).

