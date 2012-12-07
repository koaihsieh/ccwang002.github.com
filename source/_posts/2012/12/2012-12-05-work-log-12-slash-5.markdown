---
layout: post
title: "Work Log - 12/5"
date: 2012-12-05 17:44
comments: true
categories: 
 - lab log
---

## Summary

* recompute the result of dataset verifyB
    * expression in terms of RPKM
    * plot the bar chart
* rerun the result of dataset verifyA
    * not to pool the result

## Slides

<script async class="speakerdeck-embed" data-id="44b3f06020ef0130321a22000a9d04d3" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>

<!-- more -->
## Datatset [GSE29173]

* 3' adapter: TCGTATGCCGTCTTCTGCTTGT
* using Barcoded sequencing shown in its supplementary [file][supp]

[supp]: http://cancerres.aacrjournals.org/content/suppl/2011/05/17/0008-5472.CAN-11-0608.DC1/Tables_Supplement_June2011.xls


[GSE29173]: http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE29173

## Barcode Sequencing
<div class="video-container">
<iframe width="640" height="360" src="http://www.youtube-nocookie.com/embed/hgSoJiOoSQQ?rel=0" frameborder="0" allowfullscreen></iframe>
</div>
<div class="video-container">
<iframe width="640" height="360" src="http://www.youtube-nocookie.com/embed/W5EftJL5XpQ?rel=0" frameborder="0" allowfullscreen></iframe>
</div>

## 接下來要做的事情
* 怎麼篩出最可能的 miRNA
* 怎麼判斷在不同type間表現量的差異是明顯的？（定義？）
* 同一個type的sample，overall的表現量計算方式（Now: Average）？
* Barcoded的sample中expression rate會不會本來就稍微高一點，因為sample size較小？

* 獨立執行過，似乎跟我的code沒有關系
    * ==> 試著自己產生一些test file來檢查（sample size的差別、instrument的差別）
    * ==> 取代fastx clipper的軟體：cutadapt: <http://code.google.com/p/cutadapt/>
    * ==> 
* HWI-EASXXX:1_64:9_25_09:6:1:16:414 的個別意義
* HWI, ILLUMINA差別？

* 關於Galaxy，因為感覺這個東西沒有辦法跟lab其他人的成果合起來，給我們用其實也蠻多餘的，不太確定有沒有必要
    * 如果要做的話，現在的這個要砍掉重練
* 有沒有其他任務可以解