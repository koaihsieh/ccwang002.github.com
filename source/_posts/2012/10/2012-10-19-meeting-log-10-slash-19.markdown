---
layout: post
title: "Meeting Log - 10/19"
date: 2012-10-19 17:18
comments: true
categories: 
    - lab log
---

## Modification For Presentation

### Workflow
* 做一個簡單版的流程圖
* 現流程圖把 I/O 圖示、DB圖示改掉

### Slides
* move NGS to Supplementary Slides
* move 2<sup>nd</sup> microRNA to Supplementary Slides
* Mark Input and result files on workflow
* Give GSE ID of every dataset
* candidates, clear 'cancer related' remark
* Table2 goes to Supp slides
* add sub fig-2 to Supp slides
* those candidates mapped to intergenic(IGR) (which usually is intragenic, aka intro)

<!-- more -->
## Future Work
* add **rFam** DB into next miRDeep2 run.
* use the 100+ verifying dataset as novel candidates identification
* clipping adapter can allow 1 mismatch. If no adapter is clipped in a read, then the read should be discarded !!
* those miRNA mapped to **exon/mRNA** should consider as well!!
* the count of miRNA identified by the dataset should be logged
    * a program may needed
* cell line verification
    * read the supplementary file
    * 195 MCF7 (Lab has it as well !!)
