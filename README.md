# 2023 Madagascar IGS Workshop 

A practical introduction to short-read bioinformatics for bacterial genome reconstruction in the context of the Madagascar IGS workshop 2023.

A set of laptops with linux installed will be provided for the lecture. If you want to work with your own laptop, please see the available options [below](#5)

## Schedule links for the workshop
* [6 October - Friday](#0)
* [9 October - Monday](#1)  
* [10 October - Tuesday](#2)  
* [11 October - Wednesday](#3)  
* [12 October - Thursday](#4)  

## Instructors

* Hugues Richard, Essia Belarbi, Simon Tausch

## Schedule

> All events are held at Le Louvre Hotel,
> Jardin Antaninarenina, 4 Kiana Philibert Tsiranana.

### <a name="0"></a> Friday, 6 October, 2023
| Time        | Linux introduction |
| --          | --               |
| 14:00-15:30 | Welcome & [hands-on with Linux](day00-friday/intro.md) (optional)|
| 15:30-16:00 | Coffee | 
| 16:00-17:00 | Hand-on with Linux (follw'd) | 


### <a name="1"></a> Monday, 9 October, 2023
| Time        | Linux & NGS |
| --          | --               |
| 9:00-10:30 | Welcome & [introduction](day01-monday/general.md) |
| 10:30-11:00 | Coffee break | 
| 10:30-12:00 | [Linux re-cap](day01-monday/linux.md) |
| 12:00-13:00 | Lunch break |
| 13:00-14h30 | [Hands-on & Linux exercises](day01-monday/general.md)
| 14:30-15:00 | Coffee break |
| 15:00-16:00 | [Hands-on (followed)](day01-monday/general.md) |
| 16:00-16:15 | Wrap-up & questions |

### <a name="2"></a> Tuesday, 10 October, 2023

| Time        | Manual Raw data QC and analyses|
| --          | --               |
| 09:00-09:30 | Debriefing Day 1 |
| 09:30-10:00 | [Intro NGS technology](day02-tuesday/README.md) | 
| 10:00-10:45 | [Raw data quality control](day02-tuesday/trimming.md) |
| 10:45-11:00 | Coffee break |
| 11:00-12:00 | [Hands-on & demo trimming](day02-tuesday/trimming.md) |
| 12:00-13:00 | Lunch break |
| 13:00-14:00 | [Read mapping](day02-tuesday/mapping.md) |
| 14:00-14:30 | [Hands-on & demo mapping](day02-tuesday/mapping.md) |
| 14:30-15:00 | Coffee break |
| 15:00-15:45 | Continue practical session |
| 15:45-16:00 | Wrap-up & questions |


### <a name="3"></a> Wednesday, 11 October, 2023

| Time        | Genome reconstruction and characterization |
| --          | --               |
| 09:00-10:00 | Debriefing Day 2 |
| 10:00-10:45 | [QC and Assembly Lecture](day03-wednesday/aquamis.md) |
| 10:45-11:15 | Coffee break |
| 11:15-12:00 | [QC and Assembly Hands-on](day03-wednesday/aquamis.md) |
| 12:00-13:00 | Lunch break |
| 13:00-13:30 | [Functional annotation Lecture](day03-wednesday/functionalannotation.md) |
| 13:30-14:00 | Coffee break |
| 14:00-15:45 | [Functional annotation Hands-on](day03-wednesday/functionalannotation.md) |
| 15:45-16:00 | Wrap-up & questions |

### <a name="4"></a> Thursday, 12 October, 2023

| Time        | Phylogenetic analyses of isolate sequencing data |
| --          | --               |
| 09:00-10:00 | Debriefing Day 3 |
| 10:00-11:00 | [Phylogenetic analyses Lecture](day04-thursday/phylogeny.md) |
| 11:00-12:00 | [Phylogenetic analyses Hands-on & demo](day04-thursday/phylogeny.md) |
| 12:00-13:00 | Lunch break |
| 13:00-15:00 | [Phylogenetic analyses Hands-on & demo](day04-thursday/phylogeny.md) |
| 15:00-15:15 | Coffee break |
| 15:15-16:00 | Wrap up & questions, Thank you and Goodbye! |


### <a name="5"></a> Working with your own laptop

You can either install a linux distribution as a dual boot or just install windows on linux (WSL). This will allow you to run a linux system within your windows environnment and it is recommended. You can check the installation instructions [here](https://learn.microsoft.com/en-us/windows/wsl/install) (page en français [ici(https://learn.microsoft.com/fr-fr/windows/wsl/install)])

You will then need to install the required environnments in mamba/conda. The list of environments used for this tutorial is available on [this page](mamba_commands.md)

## Acknowledgement

This course material is partly based on the following resources and on contributions from great people:

* Carlus Deneke, Federal Institute for Risk Assessment, Germany
* Martin Hölzer, RKI, Germany
* Workshop course template from [the MF1 unit at RKI](https://github.com/rki-mf1/)
* Workshop structure inspired by [https://github.com/cinemaparis/2023](https://github.com/cinemaparis/2023)
