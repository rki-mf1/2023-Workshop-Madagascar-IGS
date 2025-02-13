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

### Let's look at the results in the terminal

```bash
# let's go back to our workshop directory
cd ~/igsw/igs_workshop/

# zcat is a cat for gzipped files
zcat raw_data/ERR9964620_1.fastq.gz | less

# Look at the trimmed reads
zcat trimming/ERR9964620_1_trimmed.fastq.gz | less

# Let's search for a specific read using `grep`
zcat trimming/ERR9964620_1_trimmed.fastq.gz | grep "@ERR9964620.8 "  # notice the space after the 8

# If we want to see the read information we can use the -A option (for After)
zcat trimming/ERR9964620_1_trimmed.fastq.gz | grep -A 3 "@ERR9964620.8 "  


```


### Practice: Read the fastp-manual and set some stricter parameters. Rerun the tool and compare the reports.

* We will change the mean Q value filter to 30 to be stricter (which means a proba of error of 1/1000).
* We have to be careful to generate other trimmed fastq files 

```bash
# 
fastp -i raw_data/ERR9964620_1.fastq.gz -I raw_data/ERR9964620_2.fastq.gz -o trimming/ERR9964620_1_trimmed_strict.fastq.gz -O trimming/ERR9964620_2_trimmed_strict.fastq.gz --html fastp_strict.html -q 30 -M 30 

```

### Practice: Write a loop over all *.fastq.gz files in your data folder to trim all reads. 
We will need to loop over the sample names to differenciate between read 1 and read 2. 
To get the sample name, we can use the `basename` command:
```bash
basename /home/igsw/igs_workshop/raw_data/ERR9964620_1.fastq.gz _1.fastq.gz
```



Once you have trimmed reads, you can continue with [read mapping](mapping.md) and other analysis steps.
