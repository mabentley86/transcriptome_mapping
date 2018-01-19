# Transcriptome mapping
A pipeline for mapping the transcriptome to a reference genome.

## gffutilities [(Manual)](http://ccb.jhu.edu/software/stringtie/gff.shtml)
The gffutilities page contains tools to manipulate GTF and GFF files. It contains two useful programs: 1) [gffreads](https://github.com/gpertea/gffread), which can be used to validate, filter, convert and perform various other operations on GFF files; and 2) [gffcompare](https://github.com/gpertea/gffcompare), which can be used to compare, merge, annotate and estimate accuracy of one or more GFF files.

If we have an annotate reference genome available, it will often be accompanied with a GFF3 file, containing information about specific regions of the genome with respect to CDS, exons, and such like. We can convert this to a GTF file, containing information about CDS, exons and such like with respect to specific regions of the genome. If we want to use hisat2 to perform read mapping, we need to convert from GFF3 to GTF. To do this, we use the command:

```
gffread genome.gff3 -T -o genome.gtf
```

The argument -T specifies output is in GTF format. 


## HISAT2 [(Manual)](https://ccb.jhu.edu/software/hisat2/manual.shtml)
HISAT2 is a fast and sensitive alignment program for mapping next-generation sequencing reads (whole-genome, transcriptome, and exome sequencing data) against the general human population (as well as against a single reference genome). 

### Build hisat2 genome index.

Before mapping reads to the reference genome, we need to build a genome index. If the genome is annotated, we can use a GTF file to extract the locations of exons and introns. We run:

```
hisat2_extract_splice_sites.py genome.gtf > genome_splice_sites.ss
hisat2_extract_exons.py genome.gtf > genome_exons.exon
```

We can then build the index using the files by running:

```
hisat2-build --ss genome_splice_sites.ss --exon genome_exons.exon genome.fasta genome
```

## Appendix
