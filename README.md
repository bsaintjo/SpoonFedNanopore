# SpoonFedNanopore
The world's simplest open-source nanopore alignment and assembly pipeline. This is meant to be an educational tool that Just Works(TM), and walks a user through assembling a genome from nanopore sequencing reads. This pipeline also performs gene annotation using MetaGeneMark and gives the user taxanomic information through Mash.

## Uses
* Educational tool for teaching undergrads or high school students the basics of genome assembly
* WIMP (What's In My Pot) simplified analysis that doesn't require building dependencies
* Citizen scientist that wants to sequence whatever is on their roommate's toothbrush

## Workflow
![SpoonFedNanopore Workflow](./images/diagram.png)

Reads are mapped to each other to give alignment data using `minimap2`. The genome(s) are assembled using `miniasm`. That assembly is then used with `mash` tool to quickly determine the taxa of the sample. Furthermore, we use `MetaGeneMark` in order to perform de novo gene annotation.

This workflow is implemented in a Jupyter Notebook for ease of use as well as embedding educational information so that people that are being introduced to genome assembly can learn about the general principles of the tools and why the commands are used.

This workflow has been optimized for ease of use and speed. The workflow should easily run on a normal laptop computer, and running the entire pipeline should take approximately 5 minutes with our example dataset (~25k nanopore reads, along with 4 small genomes). 

## Requirements
Pipeline must be run on a computer with atleast 4 GB of RAM

## Dependencies
* `docker`
* web browser (Firefox, Chrome, etc.)

## Installation
Install the Docker Community Edition [here](https://www.docker.com/community-edition) for your distribution.

### Mac specific
Run docker application
Preferences -> Advanced
Set Memory slider to the highest settings
Apply changes

### Mac and Linux
```
$ git clone https://github.com/NCBI-Hackathons/SpoonFedNanopore.git
$ cd SpoonFedNanopore/
$ docker build .
$ docker images
# Use the hash given by this command, and replace IMAGEID with the most recent Image ID given
$ docker run -it -p 8888:8888 -v $PWD:/work IMAGEID
```

## TODO
- Instruction for building from docker store
- Script for building a custom Mash sketch database


## References
1. Li, H. (2016). Minimap and miniasm: fast mapping and de novo assembly for noisy long sequences. Bioinformatics 32(14), 2103–2110.
2. Li, H. (2017). Minimap2: pairwise alignment for nucleotide sequences. arXiv.
3. Loman, N. J. and Quinlan, A. R. (2014). Poretools: a toolkit for analyzing nanopore sequence data. Bioinformatics 30(23), 3399–3401.
4. Loman, N. J., Quick, J. and Simpson, J. T. (2015). A complete bacterial genome assembled de novo using only nanopore sequencing data. Nature Methods 12(8), 733–735.
