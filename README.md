# RNA-Seq Analysis Pipeline: Quality Control

This pipeline provides a series of steps for performing RNA-Seq data quality control (QC) analysis using FastQC. It includes steps to download data, organize files, run FastQC, and generate QC reports for each sample.

## Requirements
Before running the pipeline, ensure you have the following dependencies installed:

FastQC for quality control analysis

wget for downloading files

tar for extracting compressed files

---
## Step 1: Create a working directory

Create a new directory to organize your data and results. This directory will hold the raw data, FastQC results, and final reports.
  ```bash
mkdir RNAseq_analysis
cd RNAseq_analysis
```
---
## Step 2: Download data
```bash
wget ftp://ftp.ccb.jhu.edu/pub/RNAseq_protocol/chrX_data.tar.gz
```
---
## Step 3: Extract data
   ```bash
tar -xzf chrX_data.tar.gz
```
---
## Step 4: Activate your conda env
## Step 5: Quality control with FastQC
### Step 5a : Create an output folder for FastQC reports:
```bash
mkdir qc_output
```
Repeat the process for all the files
---
### Step 5b: Run FastQC on your raw FASTQ files
```bash
fastqc chrX_data/samples/ERR188044_chrX_1.fastq.gz chrX_data/samples/ERR188044_chrX_2.fastq.gz -o qc_output
```
```bash
fastqc chrX_data/samples/ERR188104_chrX_1.fastq.gz chrX_data/samples/ERR188104_chrX_2.fastq.gz -o qc_output
```
```bash
fastqc chrX_data/samples/ERR188234_chrX_1.fastq.gz chrX_data/samples/ERR188234_chrX_2.fastq.gz -o qc_output
```
```bash
fastqc chrX_data/samples/ERR188245_chrX_1.fastq.gz chrX_data/samples/ERR188245_chrX_2.fastq.gz -o qc_output
```
```bash
fastqc chrX_data/samples/ERR188257_chrX_1.fastq.gz chrX_data/samples/ERR188257_chrX_2.fastq.gz -o qc_output
```
```bash
fastqc chrX_data/samples/ERR188273_chrX_1.fastq.gz chrX_data/samples/ERR188273_chrX_2.fastq.gz -o qc_output
```
```bash
fastqc chrX_data/samples/ERR188337_chrX_1.fastq.gz chrX_data/samples/ERR188337_chrX_2.fastq.gz -o qc_output
```
```bash
fastqc chrX_data/samples/ERR188383_chrX_1.fastq.gz chrX_data/samples/ERR188383_chrX_2.fastq.gz -o qc_output
```
```bash
fastqc chrX_data/samples/ERR188401_chrX_1.fastq.gz chrX_data/samples/ERR188401_chrX_2.fastq.gz -o qc_output
```
```bash
fastqc chrX_data/samples/ERR188428_chrX_1.fastq.gz chrX_data/samples/ERR188428_chrX_2.fastq.gz -o qc_output
```
```bash
fastqc chrX_data/samples/ERR188454_chrX_1.fastq.gz chrX_data/samples/ERR188454_chrX_2.fastq.gz -o qc_output
```
```bash
fastqc chrX_data/samples/ERR204916_chrX_1.fastq.gz chrX_data/samples/ERR204916_chrX_2.fastq.gz -o qc_output
```
---
## Step 6: Run Trimmomatic for paired-end data
Trimmomatic processes paired-end FASTQ files and outputs the cleaned, trimmed sequences into paired and unpaired files. The following command demonstrates how to run Trimmomatic with a specific set of parameters to trim the sequences.
Note: This step is optional. Based on the quality control results from FastQC, you may find that trimming is unnecessary for your dataset. If you find that trimming is required, you can follow the steps below.
```bash
trimmomatic PE chrX_data/samples/ERR188044_chrX_1.fastq.gz \
chrX_data/samples/ERR188044_chrX_2.fastq.gz \
paired/ERR188044_chrX_1_paired.fq.gz unpaired/ERR188044_chrX_1_unpaired.fq.gz \
paired/ERR188044_chrX_2_paired.fq.gz unpaired/ERR188044_chrX_2_unpaired.fq.gz \
ILLUMINACLIP:TruSeq3-PE.fa:2:30:10 LEADING:3 TRAILING:3 \
SLIDINGWINDOW:4:15 MINLEN:36
```
---
