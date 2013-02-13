---
layout: page
title: "近期工作整理 Recent stash for miRNA work"
date: 2012-09-18 09:31
comments: false
sharing: false
footer: true
---
這邊記錄了一些近期工作所需要常用的資訊。
Here collects some useful information for recent work.
### To do next
* 找出在 breast, lung cancer 表現有顯著差異的
* use `cutadapt` and `Flicker` for adapter trimming.
* plot using box plot. (done by R)
* 把 workflow 串起來
* change fortran compiler f77 to gun95

{%codeblock %}
export FC=gfortran
export F77=$FC
{%endcodeblock%}
### Dataset in use
這邊整理了最近在使用的 dataset。( from [Work Log](/blog/2012/11/13/work-log-11-slash-13/) )


Dataset         | Cancer Type        | Sample Size
----------      | -------------      | ------------    
[GSE39162] (A)  | Breast Cancer      |
[GSE33858] (B)  | Lung Cancer        | 32 patients.
[GSE29173] (C)  | Breast Cancer      | 
[GSE37710]      | Pancreatic Cancer  | 352 participants, sample size unknown.

[GSE29173]: http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE29173
[GSE39162]: http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE39162
[GSE33858]: http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE33858
[GSE37710]: http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE37710

* GSE33858
    * 21 adenocarcinoma patients (20 pairs of T+NT and 1 non-pair T)
    * 11 squamous cell carcinoma patients (10 pairs of T+NT and 1 non-pair T).  
    
* GSE29173
    * Metaplastic: 11
    * Apocrine: 4
    * Atypical Medullary: 9
    * Mucinous A: 1
    * Adenoid: 2
    * Cell Line: 7
    * DCIS: 21
    * IDC: 173
    * Normal: 16
    * ILC: 1

### Candidate Type
* [candidates](/blog/2012/10/25/work-log-10-slash-25/) map to exon

<!-- End of work summary -->
## Good Sites
以下的部份大概是一些實用的資訊，但還不知道要怎麼用，以及該怎麼歸類。等自己對這些技術比較熟悉之後，會刪去一些不合宜的資訊，請自行斟著參考。

### Tutorials
* MIT Whitehead Institute short training courses (monthly update)  
<http://jura.wi.mit.edu/bio/education/hot_topics/>  
Contains some pdf slides on topics: Unix, Perl, Python, R, Sequencing  



### GEO dataset search
* GEO dataset search site  
<http://www.ebi.ac.uk/arrayexpress/>