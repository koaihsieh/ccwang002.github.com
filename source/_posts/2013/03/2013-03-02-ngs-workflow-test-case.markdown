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
Test case 1

* Use raw dat set [GSE35178](http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE35178).
* normal, paracancerouse and cancerous human bladder tissues. We obtained a total of 30.0 million read pairs from normal, 33.1 million read pairs from paracancerous and 36.5 million read pairs from cancerous.

* published at Jan 01, 2013
* SRX from [here](http://www.ncbi.nlm.nih.gov/sra?term=SRP010384)
<!-- more -->

Test case2  

* search based on [Illumina HiSeq 2000](http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL11154)  

* [GSE43603](http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE43603)

* [GSE37704](http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE37704)

### About paired end sequencing
* <http://www.illumina.com/technology/paired_end_sequencing_assay.ilmn>
* Figure 1 of <http://www.biomedcentral.com/content/pdf/1756-0500-5-337.pdf>

The reference above implies no adapter contamination in RNA-seq paired end data.



### Test2

{% codeblock %}
# SRA to FastQ (2 min)
$ fastq-dump SRR650429.sra
# FastQC (10min)
$ /data/NGSTools/FastQC/fastqc SRR650429.fastq
{% endcodeblock %}

* highest target hit - AAGCAGTGGTATCAACGCAGAGTACTTTTTTTTTTTTTTTTTTTTTTTTT is a 3’-RACE primer

### Test Chou
* Sample No 94




