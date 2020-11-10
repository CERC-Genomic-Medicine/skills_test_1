# skills_test_1

This repository stores input files, example output files, and description of the problem which is designed to assist in evaluation of skills of job candidates.

## Problem description

Given input genotypes in VCF files (one file per chromosome), implement a workflow (see Figure below) which:

1. Identifies unrelated individuals from genotype data (use existing open source software tools such as KING and/or PLINK).

2. Constructs new VCF files which include only unrelated individuals. For each variant, it computes the following VCF INFO fields:
    - alternate allele count (AC)
    - alternate allele frequency (AF)
    - minor allele frequency (MAF)
    - total number of alleles (AN)
    - average depth (AVG_DP), i.e. average value across FORMAT DP values
    - number of heterozygous alternate allele carriers (N_ALT_HET), i.e. with genotypes 0/1 or 1/0
    - number of homozygous alternate allele carriers (N_ALT_HOM), i.e. with genotype 1/1
  
    **Monomorphic variants (i.e. with AC = 0) must be excluded.**

3. For each variant, computes average depth's percentile value (AVG_DP_P) in VCF INFO field. If variant v<sub>i</sub> has the average depth value AVG_DP<sub>i</sub>, then its average depth's percentile value AVG_DP_P<sub>i</sub> is equal to the percentage of variants across all VCF files with AVG_DP < AVG_DP<sub>i</sub>.

<img src="https://github.com/CERC-Genomic-Medicine/skills_test_1/blob/main/workflow.jpg?raw=true" width="400px">

## Problem solution

To implement this workflow you may:
- use workflow system of your choice, which is compatible with HPC (e.g. Nextflow, Snakemake, Luigi, Cromwell)
- use existing published open source tools to implement workflow steps (e.g. bcftools, vcftools, PLINK, KING, R  and R packages)
- use scripting/programming language (or any combination of them) of your choice

## Evaluation

Depicted sequence of steps in the workflow may not be optimal and any improvements (if such possible) are highly encouraged. Please, leave descriptive comments, which may help us to better understand your choices. Solutions will be evaluated based on the final output files in VCF format, ability to understand and utilize existing open source tools, ability to program/script missing functional parts, and ability to orchestrate everything together.

