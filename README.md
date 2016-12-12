# MarpoDB
An open registry of Marchantia polymorpha genetic parts

# Description
MarpoDB is a gene-centric database developed for genetic engineering and synthetic biology. This is the result of dealing with highly fragmented genomic data (from a non-sequenced organism, Marchantia polymorpha) and compiling it into an accessible resource for sequence exploration and retrieval. The database framework, however, can be used with any type of genetic data and can be set up locally.

In brief, we start off from two "raw" sequence files in FASTA format containing genomic contigs/scaffolds and transcripts. Using these files we will perform several analyses, such as ORF prediction, BLAST homology search, HMMR protein motif prediction, mapping transcripts to the "genome" and interrelating resulting data for loading it into a database.

Then, we shall access the database by means of web server accessible by your browser.

# Overview
To setup a gene-centric database harboring DNA parts we need to install serveral 3rd party software and databases, libraries for running the web server and application, and finally compile and load the data with annotations to the database. 

Full installation instructions can be found in our Wiki (https://github.com/HaseloffLab/MarpoDB/wiki)

Currently, we supply scripts for compiling most libraries for a 64 bit architecture in a linux server, however it may be possible to build the required libraries in a different architecture and perform the corresponding analyses successfully. Also, we are setting up local versions of all the software and libraries, without the need for sudo access since this is the common case for shared servers in academia.

We supply several scripts to split and automate (as much as possible) the setup process. Also, we have packaged most of the dependencies in a virtual environment and defined local variables for the installation. 

Here we provide a list of required dependencies and give an overview of each section.

## Bioinformatics software and required databases

- TransDecoder
- BLAST-2.2.27
- HMMR
- Uniprot
- Pfam-A
- pip python installer and virtualenv
- PostgreSQL
- Psycopg python library from source
- Splign and Compart
- InterproScan

- python libraries
  + biopython
  + Flask
  + Flask-Login
  + Flask-Mail
  + Flask-Session
  + Flask-SQLAlchemy
  + Flask-User
  + Flask-WTF
  + Jinja2
  + pillow
  + requests
  + bcbio-gff

## Data compilation
We have a developed a set of scripts to compile your transcriptome and genome data to a gene-centric database:
First, we will generate ORFs for your transcripts using predicted annotations to support predictions, then map those ORF containing transcripts to the genome (whether is finished or fragmented) and obtain genomic loci for that transcript. Afterwards, we will generate part oriented gene definitions for a promoter region (arbitrarily defined as 3 Kbs upstrem of the TSS of the transcript), 5'UTR, exons, introns and 3'UTR. Finally we will load the genomic region with all gene definitions to the database and generate IDs for each entry.

After loading the database, we will retrieve and perform several analyses (BLAST and all InterproScan comprised analyses) for each entry to provide annotations and load them to the database.

## Server


Well, that's it... I hope everything worked, otherwise, feel free to contact Bernardo Pollak (bp358[at]cam[dot]ac[dot]uk) or Mihails Delmans (md565[at]cam[dot]ac[dot]uk).