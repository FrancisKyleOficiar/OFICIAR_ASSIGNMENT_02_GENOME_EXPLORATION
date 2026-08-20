# OFICIAR_ASSIGNMENT_02_GENOME_EXPLORATION
Name: Oficiar, Francis Kyle A.
Activity Title: Basic Genome Structure and Sequence Exploration Using Galaxy
BIO 300 –B Cell and Molecular Biology Laboratory

Species: _Pteropus vampyrus_ (GCF_000151845.1)

# OBJECTIVE
To describe the structure of a genome assembly using basic statistics, sequence-length filtering, and a small-scale open reading frame (ORF) exploration and learning to inspect and interpret an assembled genome.

# *Tools used in Galaxy* 

# Part 1 — Genome Download
Source: NCBI FTP
File: GCF_000151845.1_Pvam_2.0_genomic.fna.gz
Renamed in Galaxy to: *Pteropus_vampyrus*_PGCF_000151845.1_Pvam_2.0_genomic.fna.gz

# Part 2 — Assembly Statistics
Tool: gfastats
Tool mode: Summary statistics generation
Report mode: Genome assembly statistics (--nstar-report)
Input file: 1: *Pteropus_vampyrus*_PGCF_000151845.1_Pvam_2.0_genomic.fna.gz
Output renamed to: gfastats_*Pteropus_vampyrus*

#  Part 3 — Sequence-Length Structure
Tool: Compute sequence length
Input file: 1: *Pteropus_vampyrus*_PGCF_000151845.1_Pvam_2.0_genomic.fna.gz
Setting: "Strip fasta description from header?" = Yes
Output: Compute sequence length on dataset 1
Sorted using Galaxy's Sort tool (column 2, descending) to identify the top 5 longest sequences

# Part 4 — Length-Filtering Experiment
Step 1: Tool: Filter sequences by length
Input file: 1: *Pteropus_vampyrus*_PGCF_000151845.1_Pvam_2.0_genomic.fna.gz
Parameter: minimum length = 10,000 bp (10 kb)
Output renamed to: *Pteropus_vampyrus*_filtered_10kb
Step 2
Re-ran gfastats (same settings as Part 2) using input file: 5: *Pteropus_vampyrus*_filtered_10kb
Output renamed to: gfastats_Pteropus_vampyrus_filtered

# Part 5 — Small ORF Exploration
Step 1: Tool: Filter sequences by ID from a tabular file
Input file: 1: *Pteropus_vampyrus*_PGCF_000151845.1_Pvam_2.0_genomic.fna.gz
Filter using ID list from: "provided list"
My ID: NW_011889338.1
Output: "Positive matches only"
Output renamed to: 7: GCF_000151845.1_Pvam_2.0_genomic.fna uncompressed with matched ID
Step 2: Tool: getorf
Input file: 7: GCF_000151845.1_Pvam_2.0_genomic.fna uncompressed with matched ID
Minimum nucleotide size of ORF to report: 300
What to output: Translation of regions between STOP codons
All START codons to code for Methionine: Yes
Circular sequence: No
Output: getorf_*Pteropus_vampyrus*_fasta

# small interpretation

The genome assembly appears to be relatively contiguous rather than highly fragmented, although it still contains many sequences. The original assembly contains 36,094 sequences, but the maximum sequence length is quite large at 43,245,305 bp, showing that some regions are assembled into long sequences. The N50 of 5,954,017 bp indicates that half of the genome is contained in sequences at least about 5.95 Mb long, while the L50 represents the number of sequences needed to account for half of the total assembly; together, these statistics provide a measure of assembly continuity. After filtering for sequences ≥10 kb, only 2,939 sequences remained while retaining about 1.94 Gb of the original 2.02 Gb genome, showing that the many short sequences contribute relatively little to the total genome size. The genome has a GC content of 39.81%, indicating a moderately GC-rich composition. The ORF exercise showed that the selected sequence contained 40 potential ORFs, with the longest being about 7,410 bp. However, this exercise also demonstrated that finding an ORF does not automatically mean that it is a real gene, because ORFs can occur by chance and require additional evidence to confirm gene function. 
