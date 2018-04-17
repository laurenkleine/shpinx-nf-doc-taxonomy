Pipeline Summary
===============

*:sup:`superscript`*

The main steps in the pipeline are:


1.	Pre-processing quality assessment with FastQC


2.	Trimming or removal of low quality sequences (cutadapt) and collapse of non-unique read pairs (CD-HIT)


3.	Post-processing quality assessment with FastQC


4.	Filtering of host sequences (Bowtie2)


5.	De novo assembly of remaining reads (SPAdes) and taxonomic assessment of contigs, first by nucleotide to nucleotide alignments (BLASTn) and then by translated-nucleotide to protein alignments (DIAMOND)

.. figure:: wf.png
   :align: center

This version of the Stenglein Lab Standard Taxonomic assessment pipeline requires the input of paired FASTQ files. These files are first assessed using FastQC (version) to perform an initial quality control inspection to ensure that the raw data is satisfactory^1. Sequences are then trimmed using Cutadapt (version 1.9.1) to trim low-quality bases and adaptor sequences^2. Default pipeline parameters set quality base to 33 and quality cutoff to 30 for the 50 and 30 ends. The first base of each sequence is also trimmed. The sequence clustering tool CD-HIT is then used to collapse reads with 99% global pairwise identity, leaving only unique reads for further analysis^3. Following these pre-processing steps, a second quality control analysis is run using FastQC.

Host-derived sequences are then filtered using the Bowtie2 alignment tool (version 2.2.5). First, a bowtie index is generated from the host genomic sequence and then sequences aligning with a local mode alignment score greater than 60 are removed^4. SPAdes genome assembler (version 3.5.0) is used to generate contiguous sequences (contigs)^5.

To taxonomically categorize sequences, the NCBI nt database is queried with all contigs using the BLASTn alignment tool (version 2.2.30+)^6,7. Any hit with an expect value less than 〖10〗^8 is assigned taxonomically according to the sequence with the highest alignment score^6,8. To attempt to categorize contigs that are too divergent to produce a high scoring nt–nt alignment, the NCBI nr database is queried in a DIAMOND (version 2.23) search with a minimum length of 20 amino acids and an expect value of 0.01.^9