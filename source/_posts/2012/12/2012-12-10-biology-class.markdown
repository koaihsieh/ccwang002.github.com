---
layout: post
title: "Biology Class - I"
date: 2012-12-10 10:24
comments: true
categories: 
 - bio class
---

## Today's Topic
* Biotech and Bioinfo (Ch 20)

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
* 借助 細菌、質體(Plasmid, 圓形DNA分子 circular DNA)
* 質體會隨細菌的生長而複製
    * 又稱為 cloning vector(選殖載體）
    * 把有興趣的基因放在plasmid上，就會被複製
        * 有純複製、複製+兼基因表現（蛋白質製造）
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
* E Coli Origin of Replication
* Lac Z Gene
* Multiple Cloning Site
* Ampicillin Resistance gene
    * 對抗抗生素的基因（盤尼西林）
* 選殖的壓力  
因為 transformation 的成功率不是100%，使用電擊把外來的dna放入細菌。由於不知道哪個有沒有，利用抗生素來殺細菌。外加的DNA 分子對細菌來說是負擔burden，這些帶有plasmide的細菌在演化上沒有優勢，會被淘汰掉/丟掉plasmid。所以在外加的DNA分子中加入能對抗某抗生素+要表現的基因。在培養皿中加入該抗生素，就會讓這些有plasmid的細菌不會被淘汰掉。並且讓這些沒有plasmid的細菌會被殺死

## Storing Cloned Genes in DNA lib
* Genomic lib
    * use bacteriophage ( phage) is stored as collection of phage clones
    * 可以放入較長的片段
    * can clone entire genome
* BAC(bacterial artificial chromosome) clone
    * large plasmid , can carry large DNA insert
* cDNA lib
    * represent only part of the genome。只有coding region(exon)才會被transcribe成mRNA

### cDNA = complementary DNA
* reverse transcription(反轉錄）of all mRNA(message RNA)
    * reverse transcriptase
    * 因為 DNA 比較穩定
        * RNA 多帶一個氧，活性較大
        * RNA 很容易被破壞
            * 有一個酵素 RNase，會分解 RNA
            * 大約30 min RNA 會被分解
            
![](http://9e.devbio.com/images/ch04/0405fig2.jpg)

## Screening - finding the gene of interest (refer to P.22, 23)
* gene of interest if identified by **nucleic acid probe**

### Nucleic acid hybridization 
* 利用dna互補

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
* 所謂的 Sanger(Traditional) Sequencing

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