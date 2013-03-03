---
layout: post
title: "NGS Workflow - Test Case"
date: 2013-03-02 23:18
comments: true
categories: 
 - lab log
 - ngs
---

### Dataset in use

* Use raw dat set [GSE35178](http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE35178).
* normal, paracancerouse and cancerous human bladder tissues. We obtained a total of 30.0 million read pairs from normal, 33.1 million read pairs from paracancerous and 36.5 million read pairs from cancerous.

* published at Jan 01, 2013
* SRX from [here](http://www.ncbi.nlm.nih.gov/sra?term=SRP010384)
<!-- more -->

### About paired end sequencing
* <http://www.illumina.com/technology/paired_end_sequencing_assay.ilmn>
* Figure 1 of <http://www.biomedcentral.com/content/pdf/1756-0500-5-337.pdf>

The reference above implies no adapter contamination in RNA-seq paired end data.

## Test
* using s3
* fastq-dump from SRA to fastq
* run FastQC in gui mode 12:14
* 





