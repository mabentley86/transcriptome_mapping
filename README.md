# Transcriptome mapping
A pipeline for mapping the transcriptome to a reference genome.

## gffutilities [(Manual)](http://ccb.jhu.edu/software/stringtie/gff.shtml)
The gffutilities page contains tools to manipulate GTF and GFF files. It contains two useful programs: 1) [gffreads](https://github.com/gpertea/gffread), which can be used to validate, filter, convert and perform various other operations on GFF files; and 2) [gffcompare](https://github.com/gpertea/gffcompare), which can be used to compare, merge, annotate and estimate accuracy of one or more GFF files.

## HISAT2 [(Manual)](https://ccb.jhu.edu/software/hisat2/manual.shtml)
HISAT2 is a fast and sensitive alignment program for mapping next-generation sequencing reads (whole-genome, transcriptome, and exome sequencing data) against the general human population (as well as against a single reference genome). 

# Build hisat2 genome index.

```
hisat2-build --ss genome_splice_sites.ss --exon genome_exons.exon genome.fasta genome
```

## Appendix
