# 2023 Workshop IGS Genome reconstruction - Day 04

After having QC'ed, assembled and characterized our data, we will try to put it into context. We will look at different methods for phylogenetic clustering of sequences and do a hands-on session using [chewieSnake](https://gitlab.com/bfr_bioinformatics/chewiesnake) for cgMLST-based clustering as an example.

## Lecture 

Phylogenetic analyses of isolate sequencing data using chewieSnake [Slides](https://docs.google.com/presentation/d/1jrMbTRw470Nc_YrCLnZxZazdkoevCzvAofPe6B0iCfM/edit#slide=id.p1).

## Hands-on

### Set up of chewieSnake (DO NOT RUN!)
```bash
#set up chewiesnake
git clone https://gitlab.com/bfr_bioinformatics/chewieSnake
mamba env create -f /home/igsw/igs_workshop/software/chewieSnake/envs/chewiesnake.yaml
```

### Usage of chewieSnake

```bash
conda activate chewiesnake
/home/igsw/igs_workshop/software/chewieSnake/chewieSnake.py --help 
# or
/home/igsw/igs_workshop/software/chewieSnake/chewieSnake.py --help | less
```

We have assembled a set of *Yersinia pestis* reads from a simulated outbreak scenario at `/home/igsw/igs_workshop/aquamis_results/Assembly/assembly`

To run chewieSnake, you again need a sample sheet of the samples you want to analyze. 

```bash
create_sampleSheet.sh --mode assembly /home/igsw/igs_workshop/aquamis_results/Assembly/assembly
less /home/igsw/igs_workshop/aquamis_results/Assembly/assembly/samples.tsv
```

We can remove data that did not pass our QC from the samplesheet:

```bash
grep -v ERR9964621inter /home/igsw/igs_workshop/aquamis_results/Assembly/assembly/samples.tsv > /home/igsw/igs_workshop/aquamis_results/Assembly/assembly/samples_fixed.tsv
```

Next, we want to run chewieSnake on all of these samples. We again precalculated most of the data for you. Please make sure to work only in the prepared working directory (parameter `-d`)

First, we want to check if our data is correct. To do so, we perform a dry run.
```bash
/home/igsw/igs_workshop/software/chewieSnake/chewieSnake.py -l /home/igsw/igs_workshop/aquamis_results/Assembly/assembly/samples.tsv --scheme /home/igsw/igs_workshop/software/chewieSnake/ypestis --prodigal /home/igsw/igs_workshop/software/chewieSnake/ypestis_data/ypestis_ASM22297v1.trn -n
```

If everything looks good, we start the actual processing.

```bash
/home/igsw/igs_workshop/software/chewieSnake/chewieSnake.py -l /home/igsw/igs_workshop/aquamis_results/Assembly/assembly/samples_fixed.tsv --scheme /home/igsw/igs_workshop/software/chewieSnake/ypestis --prodigal /home/igsw/igs_workshop/software/chewieSnake/ypestis_data/ypestis_ASM22297v1.trn
```

chewieSnake will automatically generate an interactive report for manual curation of your QC results. Open it in the browser:

```
readlink -f /home/igsw/igs_workshop/chewiesnake_results/reports/cgmlst_report.html

```
Copy the resulting line into your browswer to check the results.

chewieSnake will generate a tree file which you can open in e.g. grapetree for further examination.

To start a grapetree session, just type 
```
grapetree
```
This will open a browser window showing a local webserver (`http://localhost:8000/`).

Grapetree is also available as [web service](https://achtman-lab.github.io/GrapeTree/MSTree_holder.html)

You can upload your tree:

`/home/igsw/igs_workshop/chewiesnake_results/cgmlst/exported_trees/clustering_global.tre` 

and the according metadata. The metadata can be downloaded [here](ypestis_data_curated.csv)

`/home/igsw/igs_workshop/raw_data/ypestis_data_curated.csv`

Alternatively, we can vizualize our results in [phandango](jameshadfield.github.io/phandango/).

In the resulting interactive view, you can visualize different metadata fields within the tree. Play around with it and let's try to read someting meaningful from it!
