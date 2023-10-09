# 2023 Workshop IGS Genome reconstruction - Day 03

To ease analyses and get more reproducible, harmonized results, we can use pipelines. We will look at the [AQUAMIS](https://gitlab.com/bfr_bioinformatics/AQUAMIS) pipeline for Microbial Isolate QC and Assembly as an example. 

## Lecture 

Raw data QC and assembly using AQUAMIS [Slides](https://docs.google.com/presentation/d/1NH_-i5VFoa5Ae0yjDqWhslQkuLy8_o_GJ_JRq_g3Yy0/edit#slide=id.p30).

## Hands-on

### Set up of AQUAMIS (DO NOT RUN!)
```bash
#set up aquamis
mamba create -n aquamis -c conda-forge -c bioconda aquamis
conda activate aquamis
aquamis_setup.sh -b -d -t -s -v

```

### Usage of AQUAMIS

```bash
conda activate aquamis
aquamis --help 
# or
aquamis --help | less
```

We have prepared a set of *Yersinia pestis* reads from a simulated outbreak scenario at `/home/igsw/igs_workshop/raw_data/`

To run aquamis, you need a sample sheet of the samples you want to analyze. 

```bash
create_sampleSheet.sh --mode ncbi /home/igsw/igs_workshop/raw_data/
less /home/igsw/igs_workshop/raw_data/samples.tsv
```

Next, we want to run AQUAMIS on all of these samples. Since assembly is a computationally intensive step, we precalculated most of the data for you. Please make sure to work only in the prepared working directory (parameter `-d`)

First, we want to check if our data is correct. To do so, we perform a dry run.
```bash
aquamis -l /home/igsw/igs_workshop/raw_data/samples.tsv -d /home/igsw/igs_workshop/aquamis_results -t 16 -n
```

If everything looks good, we start the actual processing.

```bash
aquamis -l /home/igsw/igs_workshop/raw_data/samples.tsv -d /home/igsw/igs_workshop/aquamis_results -t 16
```

AQUAMIS will automatically generate an interactive report for manual curation of your QC results. Open it in the browser:

```
readlink -f assembly_report.html 
```
Copy the resulting line into your browser.

AQUAMIS will generate your assembed genomes as .fasta files at `/home/igsw/igs_workshop/aquamis_results/Assembly/assembly`. 

Based on these, we can continue with the [functional annotation](functionalannotation.md) of our data.