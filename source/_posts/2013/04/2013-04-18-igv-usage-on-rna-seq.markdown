---
layout: post
title: "IGV usage on RNA-Seq"
date: 2013-04-18 18:01
comments: true
categories: 
 - ngs
 - lab log
 - note
---

   
    $ samtools index Sample_No35/accepted_hits.bam Sample_No35/accepted_hits.bai
    $ igvtools count --pairs Sample_No35/accepted_hits.bam Sample_No35/accepted_hits.cov.tdf galGal4