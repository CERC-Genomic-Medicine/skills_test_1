# skills_test_1

This repository stores input files, example output files, and description of the problem which is designed to assist in evaluation of skills of job candidates.

## Problem description

Given genotypes saved in compressed Variant Call Format (VCF) files (one file per chromosome) and located inside `input/` directory, implement a workflow (see Figure below) which:

1. **Constructs a list of unrelated individuals.**
   Two individuals are related if kinship coefficient between them is >=0.0442. Use existing published open source software to compute kinship between individuals e.g. [PLINK2](https://www.cog-genomics.org/plink/2.0/) or [KING](http://people.virginia.edu/~wc9c/KING/manual.html).

2. **Builds new VCF files which include only unrelated individuals.**
    For each variant, it computes the following VCF INFO fields:
    - alternate allele count (AC)
    - alternate allele frequency (AF)
    - minor allele frequency (MAF)
    - total number of alleles (AN)
    - average depth (AVG_DP), i.e. average value across FORMAT DP values
    - number of heterozygous alternate allele carriers (N_ALT_HET), i.e. with genotypes 0/1 or 1/0
    - number of homozygous alternate allele carriers (N_ALT_HOM), i.e. with genotype 1/1
  
    **Monomorphic variants (i.e. with AF = 0.0 or AF = 1.0) must be excluded.**

3. **For each variant, computes average depth's percentile value (AVG_DP_P) in VCF INFO field.** If variant v<sub>i</sub> has the average depth value AVG_DP<sub>i</sub>, then its average depth's percentile value AVG_DP_P<sub>i</sub> is equal to the percentage of variants across all VCF files with AVG_DP < AVG_DP<sub>i</sub>.

<img src="https://github.com/CERC-Genomic-Medicine/skills_test_1/blob/main/workflow.jpg?raw=true" width="400px">

## Requirements

To implement this workflow you may:
- use any workflow system of your choice, which is compatible with HPC (e.g. [Nextflow](https://www.nextflow.io), [Snakemake](https://snakemake.readthedocs.io/en/stable/), [Luigi](https://github.com/spotify/luigi), [Cromwell](https://cromwell.readthedocs.io/en/stable/))
- use any existing published open source sowtware tools (e.g. [bcftools](http://samtools.github.io/bcftools/bcftools.html), [vcftools](http://vcftools.sourceforge.net), [PLINK2](https://www.cog-genomics.org/plink/2.0/), [KING](http://people.virginia.edu/~wc9c/KING/manual.html), R and R packages)
- use any scripting/programming language (or any combination of them) of your choice (e.g. Python, C/C++, Java, Perl, R, shell scripting)

## Solution

Please, send us a single compressed archive which includes:
1. **README**. It should provide: (a) a list of all open-source software tools (and their versions) which were used; (b) any additional requirements for the operating system and/or system libraries; (c) any compilation instructions if such exists (d) detailed step-by-step description on how to run the workflow.
2. **Workflow source code**. Include also configuration files if such are needed to run the workflow.
3. **Source of your custom scripts/code**. Please include detailed comments in your source code. This will help us better understand your code.

**Don't send VCF output files!**


## Evaluation

The following will be evaluated:
1. Workflow can be easily installed and run.
2. Selection of unrelated individuals follows best practices.
3. All requested INFO fields are present in the final output VCF files.
4. Values in the requested INFO fields in the final output VCF files are correct for a set of identified unrelated individuals.

**Depicted sequence of steps in the workflow may not be optimal and any improvements (if such possible) are highly encouraged. Please, leave descriptive comments, which may help us to better understand your choices.**

