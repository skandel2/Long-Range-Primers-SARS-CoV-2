# Long-range-primers-SARS-CoV-2

This repositary contains primer-schemes as well as bioinformatics pipeline to process nanopore sequencing data used in the paper 
### Genomic surveillance of SARS-CoV-2 using long-range PCR primers https://doi.org/10.3389/fmicb.2024.1272972


### Artic bioinformatics pipeline (https://github.com/artic-network/fieldbioinformatics) was used to process sequencing data from Oxford Nanopore GridION.


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
