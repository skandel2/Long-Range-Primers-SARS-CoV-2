# Long-range-primers-SARS-CoV-2

This repository contains primer-schemes, example script (Artic bioinformatics pipeline to process sequencing data), and NCBI Bioproject (SRA) link to raw sequencing data used in the paper 
### [Genomic surveillance of SARS-CoV-2 using long-range PCR primers](https://www.frontiersin.org/journals/microbiology/articles/10.3389/fmicb.2024.1272972/full) https://doi.org/10.3389/fmicb.2024.1272972

We used long range PCR primers in surveillance of SARS-CoV-2. Viral RNA was reverse transcribed using LunaScript SuperMix. cDNA amplification was carried out in two pools of long-range primers with amplicon size of 4500 nucleotides followed by library preparation using rapid barcoding kit SQK-RBK004 from Oxford Nanopore. 

Link to raw sequencing data for four samples sequenced in GridION using long-range primers in fastq format: [PRJNA1189558](https://www.ncbi.nlm.nih.gov/bioproject/?term=PRJNA1189558)

### [Artic bioinformatics pipeline](https://github.com/artic-network/fieldbioinformatics) with medaka was used to process sequencing data from Oxford Nanopore GridION.


### example script:

!artic guppyplex \
--directory /fastq_pass/barcode03 \
--min-length 1800 --max-length 5000 \
--skip-quality-check \
--prefix barcode03 \
--output barcode03-filtered


!artic minion --medaka --medaka-model r941_min_high_g344 --normalise 0 \
--threads 4 \
--scheme-directory /home/artic-ncov2019/primer_schemes/long-range \
--read-file barcode03-filtered --strict nCoV-2019/V1 V05476_barcode03_11.6
