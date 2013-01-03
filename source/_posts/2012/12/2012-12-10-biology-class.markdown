---
layout: post
title: "Biology Class I"
date: 2012-12-10 10:24
comments: true
categories: 
 - bio class
---

## Today's Topic
* Biotech and Bioinfo (Ch 20)

## Summary
### Gene cloning
* plasmid, cloning vector
* foreign DNA, insert => recombinant plasmid
* transformation

### Genomic lib
* phage clone
* plasmid clone (recombinant vector clone)
* BAC clone

### Screening
* nucleic acid hybridization

### Expressing vector

### DNA sequencing
* dNTP, ddNTP
* Met, Trp only one codon
* homologous sequence, ortholog

### DNA microarray assay
* hybridization
* application
    * gene expression
    * SNP, aCGH
    * MeDNA chip (epigenetic methylation)
    * microRNA
    * Chip-on-chip
<!-- more -->

## Overview: DNA Toolbox
* 人類基因體解碼
    * 利用定序方式(DNA Sequencing)解開DNA密碼，start in 1991, completes in 2003.
    * DNA 重組(recombinant DNA), arise in 1970
        * 把核酸序列（可能不同物種）兩者結合在一起
        * 所謂的遺傳工程(genetic engineering)
        
## Genetic Tech
* Recombinant DNA tech
* electrophoresis，電泳
* Southern/Northern Blotting analysis
* PCR, Polymerase Chain Reaction
* Sanger sequencing (DNA 傳統定序技術)
    * => Nowadays, microarray, Next Generation Sequencing
* Nuclear transplantation
    * 細胞核內置換

## DNA Cloning(選殖）
* 借助 細菌、質體 (Plasmid, 圓形DNA分子 circular DNA)
* 質體會隨細菌的生長而複製
    * 又稱為 cloning vector (選殖載體）
    * 把有興趣的基因放在plasmid上，就會被複製
        * 有純複製、複製+兼基因表現（蛋白質製造）
    * 細菌染色質以外的遺傳物質
* 最常用的細菌為 E. Coli(大腸桿菌）
* 細菌的doubling time很短（生長成兩倍的時間）

### Restriction Enzyme (限制酶）
* 從不同細菌內取出來，不同的限制酶會認識不同的dna序列。
    * 認識的切位稱之 restriction sites
    * 切出來的片段稱為 restriction fragment
    * 切出來的序列有兩種
        * 兩股不平整，稱之 sticky end
        * 兩股為平整，稱之 blund end
    * 並且用 DNA ligase 來把切掉的 dna 接回來
* dan's backbone 為 sugar phosphate 

![](http://bio1151.nicerweb.com/Locked/media/ch20/20_03RecombinantDNA_3-L.jpg)

### Transformation - Cloning using recombinant plasmids
* Human DNA(insert), E. coli contains plasmid(vector)
    * plasmid contain a gene lac Z(能夠代謝乳酸，產生藍色）
    * 有帶human gene的會呈藍色，就可以知道哪些Ecoli有被成功的transform
* cut with same restriction enzyme
* fragments then are mixed, use DNA ligase to bond fragment sticky ends

![](http://www.biotechspace.site90.com/wp-content/uploads/2012/11/1-3.jpg)

### Plasmid Map
plasmid map 當中包含以下部份：  

* E Coli Origin of Replication (起始複製點）
* Lac Z Gene (代謝乳酸，藍色）
* Multiple Cloning Site (MCS)  
    * insert 插入的位置
* Ampicillin Resistance gene
    * 對抗抗生素的基因（盤尼西林）
* 選殖的壓力  
因為 transformation 的成功率不是100%，使用電擊把外來的dna放入細菌。由於不知道哪個有沒有，利用抗生素來殺細菌。外加的DNA 分子對細菌來說是負擔burden，這些帶有plasmid的細菌在演化上沒有優勢，會被淘汰掉/丟掉plasmid。所以在外加的DNA分子中加入能對抗某抗生素+要表現的基因。在培養皿中加入該抗生素，就會讓這些有plasmid的細菌不會被淘汰掉，這些沒有plasmid的細菌會被殺死。同時如果recombination成功，lacZ這段基因會不見，這時候在培養皿上的菌落，就會是白色的，如果沒有insert的會呈現藍色。   
詳見 [wiki](http://en.wikipedia.org/wiki/PUC19)

## Storing Cloned Genes in DNA lib
* Genomic lib
    * use bacteriophage (phage) is the **collection of phage clones** 
    * use bacteria is the **collection of recombinant vector clones (plasmid clones)** 
    * 可以放入較長的片段
    * can clone entire genome
* BAC(bacterial artificial chromosome) clone
    * large plasmid ,can carry large DNA insert
* cDNA lib
    * cDNA = complementary DNA
    * reverse transcription *in vitro* of all mRNA produced by particular cell
    * represent only part of the genome
    * 只有coding region(exon)才會被transcribe成mRNA

### cDNA = complementary DNA
* reverse transcription(反轉錄）of all mRNA(message RNA) *in vitro*
    * reverse transcriptase
    * 因為 DNA 比較穩定
        * RNA 多帶一個氧，活性較大
        * RNA 很容易被破壞
            * 有一個酵素 RNase，會分解 RNA
            * 大約 30 min RNA 會被分解
            
![](http://9e.devbio.com/images/ch04/0405fig2.jpg)

## Screening - find gene of interest (refer to P.22, 23)
* gene of interest is identified by **nucleic acid probe**
* called **nucleic acid hybridization**

### Nucleic acid hybridization 
* 利用 dna 互補序列來設計 probe
* DNA probe can screen large # of clones at same time
* using radioactively labeled probe molecule (P<sub>32</sub>)
    * probe 序列跟想要的dna互補，就會把它抓起來，洗掉非特異性接合，最後有結合的就會在x光片上留下記錄
    
## Expressing Cloned Genes - 表現載體 expression vector
* plasmid 上帶有 promoter, promoter 會 initiate transcription
* a cloning vector that contains highly active promoter
* 跟一般的plasmid差別在多一個promoter  

![](http://www.bio.davidson.edu/courses/genomics/method/inducepromoter.gif)

* 在細菌中表現人類的蛋白質，通常是沒有功能的
    * 有三級結構，有很多folding（形態上的改變）
    * 細菌沒辦法摺疊人類的蛋白質
    * 會改使用昆蟲/人類細胞來表現
    
    
## DNA sequencing
* dNTP（去氧，2號碳） -> modified nucleotides, ddNTP(雙去氧，2/3號碳）
    * 把3號碳的O去掉，會讓本來5'-3'的連結（需要去氧的步驟）無法進行，dna合成就會終止

![](http://www.rsc.org/images/FEATURE-SEQUENCING-340_tcm18-188568.jpg)
    
* dNTP 95%, ddNTP 5% 並帶螢光
    * 拿到ddntp就會停止，所以表示在隨機長度後會停止
    * 利用毛細管電泳來分離
    * 分子大的游比較慢，先從前面的序列開始讀取螢光
* 所謂的 Sanger (Traditional) Sequencing

![](http://pic.pimg.tw/yourgene/1309618661-09251ce40cf54bf11188879bbeffd8e0.png?v=1309618662)

## Bioinformatics (生物資訊學）
* Computer, huge volumes of data
* genetic codon ( 3 bases DNA -> 1 amino acid )
    * 3 reading frames，看從哪一個開始讀起
    * **Met(Methionine)**, **Trp(W, Tryptophan)** 只有一種codon
    * 從 Met 開始做

### Database
* NIH , NCBI
* EMBL
* BGI in Shenzhen

## Identify homologous sequences (同源序列）
* Ortholog 異物種同源基因
    * homologous genes in different species
* Refer to P. 38
* NCBI Genbank
* BLAST = Basic Local Alignment Search Tool
    * 比對基因序列
    
## DNA microarray (基因晶片) assay
* compare patterns of gene expression in 
    * different tissues
    * at different times
    * under different conditions
    
### procedure
* isolate mRNA
* cDNA by reverse transcription, fluorescently labeled
* cDNA to microarray
    * cDNA **hybridizes** with any complementary DNA on microarray
* rinse(清洗) off excess cDNA
* scan using fluorescence and obtain each gene expression (a spot on array)
* use sample(green) + sample(red) => combined as heat map.

### Application

* Gene expression
* Genotyping-polymorphisms (SNP) and gene copy number (aCGH)  
* Epigenetic methylation chip
    * also called Methylated DNA immunoprecipitation    * 基因後修飾(甲基化、磷酸化)    * 影響基因的表現量      
![](http://ag.arizona.edu/research/xwang/milestones/Rice_Chipchip.jpg)
![MeDIP, MeDIP chip](http://upload.wikimedia.org/wikipedia/commons/3/3f/Medip-final-3.jpg)
* microRNA
* Binding site identification - ChIP-on-chip
    * investigate interactions between proteins and DNA in vivo.
    * chromatin immunoprecipitation ("ChIP") with microarray technology ("chip")  
Chromatin immunoprecipitation (ChIP) assay 這是一種分子生物實驗的方法，其目的在決定某蛋白質(包括轉錄因子)是否會結合在活細胞或組織染色質的某個特定區域的方法。其原理在於活細胞內的DNA結合蛋白(包括transcription factors)，當它們位於適當位置後，能夠與染色質交互連接，此通常是利用甲醛固定來達成。在固定後，接著將細胞lyse並利用超音波使DNA斷成長度約0.2~1 kb的碎片，一旦蛋白質被固定在染色質而且染色質被斷成斷片後，整個蛋白質-DNA複體可利用對蛋白質具專一性的抗體來認知結合而使其發生免疫沈澱。然後再將DNA從蛋白質/DNA中分離純化出來，所分離出之DNA斷片的鑑定可以利用PCR來進行，而PCR所使用的primers則是用當初猜測蛋白質會結合在那個我們所推測之DNA區域而設計的。如此即可判定某蛋白質是否會結合在DNA的某個區域。利用DNA微陣列還可以在衍生出所謂的ChIP on chip或ChIP-chip。  
![ChIP-on-chip (POI = protein of interest)](http://upload.wikimedia.org/wikipedia/en/thumb/8/8d/ChIP-on-chip_wet-lab.png/800px-ChIP-on-chip_wet-lab.png)    