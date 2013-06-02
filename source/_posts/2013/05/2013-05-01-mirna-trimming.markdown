---
layout: post
title: "miRNA trimming"
date: 2013-05-01 02:35
comments: true
categories: 
 - mirna
 - ngs
 - lab log
---

* using `cutadapt`
* Illumina v1.9, Sanger Phred quality (+64) `--quality-base=64`

    Illumina_DpnII_expression_Sequencing_Primer
    CGACAGGTTCAGAGTTCTACAGTCCGACGATC
    
    RNA_PCR_Primer_Index_1_53p
    CAAGCAGAAGACGGCATACGAGATCGTGATGTGACTGGAGTTCCTTGGCACCCGAGAATTCCA
    
    Illumina_Small_RNA_Sequencing_Primer_35p
    CGACAGGTTCAGAGTTCTACAGTCCGACGATC
    
-b RNA_PCR_Primer_Index_1_53p=CAAGCAGAAGACGGCATACGAGATCGTGATGTGACTGGAGTTCCTTGGCACCCGAGAATTCCA \
-b Illumina_Small_RNA_Sequencing_Primer_35p=CGACAGGTTCAGAGTTCTACAGTCCGACGATC \

### Contamination at Read 1 
Supposedly it may contain:
* Illumina Small RNA Adapter 2
* RNA PCR Primer, Index 1
* TruSeq Adapter, Index 1

/data2/NGS_service/cutadapt-dev/cutadapt/bin/cutadapt \
-a TruSeq_Adapter_Index_1_part=GAACTCCAGTCACATCACGATCTCGTATGCCGTCTTCTGCTTG \
-b RNA_PCR_Primer_Index_1=CAAGCAGAAGACGGCATACGAGATCGTGATGTGACTGGAGTTCCTTGGCACCCGAGAATTCCA \
-a Small_RNA_Adapter_2=TCGTATGCCGTCTTCTGCTTGT \
-a unknown_seq=GCATTGTGGTTCAGTGGTAGAATTCTCGCCTGGAATTC \
65T_ATCACG_L007_R1_001.fastq.gz \
-q 30 -e 0.10 -o 65T_ATCACG_L007_R1.trimmed.fastq -n 3 \
--info-file=65T_ATCACG_L007_R1.trimmed.results.csv


/data2/NGS_service/cutadapt-dev/cutadapt/bin/cutadapt -a TruSeq_Adapter_Index_1_mod=TCGGGTGCCAAGGAACTCCAGTCACATCACGATCTCGTATGCCGTCTTCTGCTTG -a RNA_PCR_Primer_Index_1=CAAGCAGAAGACGGCATACGAGATCGTGATGTGACTGGAGTTCCTTGGCACCCGAGAATTCCA -a Small_RNA_Adapte_2=TCGTATGCCGTCTTCTGCTTGT -a unknown_seq=GCATTGTGGTTCAGTGGTAGAATTCTCGCCTGGAATTC 65T_ATCACG_L007_R1_001.fastq.gz -q 20 -e 0.10 -o 65T_ATCACG_L007_R1.trimmed.fastq -n 2 --info-file=65T_ATCACG_L007_R1.trimmed.results.csv -m 10 --trimmed-only


```
# modified TruSeq Adapter Index 1
        TCGGGTGCCAAG-GAACTCCAGTCACATCACGATCTCGTATGCCGTCTTCTGCTTG
GATCGGAAGAGCACACGTCT-GAACTCCAGTCACATCACGATCTCGTATGCCGTCTTCTGCTTG
# original TruSeq Adapter Index 1
```

## Step 1
RTP_rev_comp_TruSeq_Adapter_Index_1
TGGAATTCTCGGGTGCCAAG-GAACTCCAGTCACATCACGATCTCGTATGCCGTCTTCTGCTTG

/data2/NGS_service/cutadapt-dev/cutadapt/bin/cutadapt \
-a RTP_rev_comp_TruSeq_Adapter_Index_1=TGGAATTCTCGGGTGCCAAGGAACTCCAGTCACATCACGATCTCGTATGCCGTCTTCTGCTTG \
65T_ATCACG_L007_R1_001.fastq.gz \
-q 20 -e 0.10 -o 65T_ATCACG_L007_R1.trimmed.fastq \
--info-file=65T_ATCACG_L007_R1.trimmed.results.csv -m 5 -O 10 --trimmed-only > trim_R1_1st.log \


## Step2
GCATTGGTGGTTCAGTGGTAGAATTCTCGCC -> piRNA

/data2/NGS_service/cutadapt-dev/cutadapt/bin/cutadapt \
-g unknown_hifreq=GCATTGGTGGTTCAGTGGTAGAATTCTCGCC \
65T_ATCACG_L007_R1.trimmed.fastq \
-q 20 -e 0.10 -o 65T_ATCACG_L007_R1.clean.trimmed.fastq \
--info-file=65T_ATCACG_L007_R1.clean.trimmed.results.csv -m 5 > trim_R1_2nd.log \




## Step 1

/data2/NGS_service/cutadapt-dev/cutadapt/bin/cutadapt \
-a TruSeq_Adapter_unknown=TCGTCGGACTGTAGAACTCTGAACGTGTAGATCTCGGTGGTCGCCGTATCATT \
65T_ATCACG_L007_R2_001.fastq.gz \
-q 20 -e 0.1 -o 65T_ATCACG_L007_R2.trimmed.fastq \
--info-file=65T_ATCACG_L007_R2.trimmed.result.csv \
-m 5 > trimmed-only -O 10 --trimmed-only > trim_R2_1st.log \

## Step 2

/data2/NGS_service/cutadapt-dev/cutadapt/bin/cutadapt \
-g unknown_hifreq_comp=GGCGAGAATTCTACCACTGAACCACCAATGCGA \
65T_ATCACG_L007_R2.trimmed.fastq \
-q 20 -e 0.1 -o 65T_ATCACG_L007_R2.clean.trimmed.fastq \
--info-file=65T_ATCACG_L007_R2.clean.trimmed.results.csv -m 5 -O 10 > trim_R2_2nd.log \

