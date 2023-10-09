# 2023 Workshop IGS Genome reconstruction - Day 02

## Read trimming lecture
First, we will look into short read raw data quality control.

[Trimming Slides](https://docs.google.com/presentation/d/1BbtS4wJtUuch2fBSip_AH_nyT2bwuv_z3F_qeJTNqSY/edit#slide=id.g288cd11cf66_0_12)

## Read trimming hands-on
### Set up your infrastructure
#### Create folder to work in 
```bash
mkdir /home/igsw/igs_workshop/trimming/
cd /home/igsw/igs_workshop/trimming/
```

#### Install the software
For read trimming, we will use [fastp](https://github.com/OpenGene/fastp).

```bash
# set up a conda environment containing fastp and its dependencies
mamba create -n fastp -c bioconda fastp
conda activate fastp
# familiarize with the tool
fastp -h
```
#### Search your input data

```bash
cd ../raw_data/
ls
# get full path of a file of your choice, e.g. 
readlink -f ERR9964620_1.fastq.gz
# get full path of both read files using a wildcard
readlink -f ERR9964620_*.fastq.gza
```
#### Go back to your working directory

```bash
cd /home/igsw/igs_workshop/trimming/
```

### Run fastp on your data

```bash 
fastp -i /home/igsw/igs_workshop/raw_data/ERR9964620_1.fastq.gz -I /home/igsw/igs_workshop/raw_data/ERR9964620_2.fastq.gz -o ERR9964620_trimmed_1.fastq.gz -O ERR9964620_trimmed_2.fastq.gz
```

### Familiarize yourself with the results

```bash
readlink -f fastp.html
```
Paste the resulting link into your browser and look at the report.


Once you have trimmed reads, you can continue with [read mapping](mapping.md) and other analysis steps.
