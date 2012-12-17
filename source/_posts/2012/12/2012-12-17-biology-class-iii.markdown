---
layout: post
title: "Biology Class - III"
date: 2012-12-17 10:14
comments: true
categories: 
 - bio class
---

## Today's Topic
* Genomics and Proteomics (Chp 21)
    * 蛋白體學不在這本課本上
    
<!-- more -->

## Different approach to study bio question
* Central dogma of molecular biology
    * 生物的中心教條
    * Transcription -> Translation 
* DNA
    * Methylation (甲基化）
    * CNV = Copy Number Variation
    * SNP = Single Nucleotide Polymorphism
* RNA
    * Gene expression
    * ChIP-on-chip
    * microRNA (miRNA)
* Proteins 
    * 2D PAGE
    * LC-Mass-Mass
    * Protein array
    
## Genomics

### Timeline
* 自動DNA定序機，省時省力
* 1st 定序的生物體：流行性感冒間嗜血桿菌
    * 800 genes
* 1st 定序的真核：麵包酵母菌
    * 6000 genes
* 1st 定序的動物：*C. elegans*

### Prokaryotic Genomes (原核基因體）
* 比較小，來練兵
* 感染多從細菌引起
* 演化
* 很多情況只有一個 Choromosome
    * Prokaryotic chromosomes 通常比較小
* Bacterial chromosomes usually circular
    * 高等的真核多半是 linear
* genome 越小， gene 的數量越少
* Prokaryotic genome less complex
    * 缺少很多構造
    * Lack centromeres, telomeres, single origin of replication, relatively little repetitive DNA
* Often have plasmids
    * 基因工程常使用
    
### 流行性感冒 *Haemophilus influenzae* 定序
* by Venter, Smith, et al.
* Venter 之後成立 Celera
    * Auto-Sequencer: ABI(Applied Biosystem Inc.)
    * ABI 提供 300台機器來定序
    * 主要雇用電腦人員來處理資訊
* 2/3 of this genome have predicted function

### Three-Stage Approach to Genome Sequencing
* The project had three stages 
    * Genetic (or linkage) mapping 
    * Physical mapping    * DNA sequencing
* Linkage map
    * 利用限制酶切出的長度片段不同來判斷序列有沒有改變（上次教的）
* Physical map
    * 前後接合

## Human Genome Project（人類基因體解碼）
* 1990 to 2003
    * 以美、英、德、法、日為首,共十八個國家參與序列解讀工作。
* 2000 人類DNA序列草圖完成
* 2003 人類DNA序列完成
    * 因為 Venter Shotgun seq 的技術，進度提前
    * 後 3 年在把 gap 補完
* identify 20,000 - 25,000 genes
    * 一開始預測有超過10萬種 gene (因為有10萬種蛋白質）
    * 一條 gene 可以產生不同種蛋白質


## (Whole-Genome) Shotgun DNA Sequencing (散彈槍定序）
![Shotgun DNA Seq](http://www.genome.gov/dmd/previews/85240_large.jpg)  

* developed by J. Craig Venter in 1992
* This approach skips genetic and physical mapping and sequences random DNA fragments directly
* FISH = Fluorescence In Situ Hybridization
    * 對某個基因有興趣，利用螢光標記，可以看到該基因在染色體的哪個位置
* 傳統的定序方式為一段一段接續的定序
    * 仰賴從前而後的定序
* Shotgun DNA Seq
    * Venter有300台，這樣後面的機器其實不能運作
    * 隨機切斷的片段分開定序
    * 最後再用軟體被片段的dna合在一起
    * 缺點：可能會會gap，再用傳統的方式(Sanger)來接合

## Eukaryotic Genomes（真核基因體）
* Genome size is not the same as the number of genes
* Eukaryotic genomes have repetitive sequences（重覆序列）
    * Moderately repetitive sequences (100 - 1000)
        * rRNA (ribosome RNA) genes
        * multiple origins of replication
    * Highly repetitive sequences (1000 - 1000000)
        * most have no known function
* Coding regions are only 2% of our genome
    * 98% noncoding
        * Intron DNA : 24%  
        * Unique noncoding DNA : 15%  
        * Repetitive DNA : 59% (Transposable elements)
        
### Genome Sizes and Estimated Numbers of Genes
* Genes per Mb is lower in Eukaryotes than in Bacteria
* ￼￼￼￼￼More complex organisms have decreased gene density

### Gene variation
* 各生物間基因的高度相似性
* 人與人之間,差異約0.2%* 人與黑猩猩之間,差異約2%
## Transposable Elements (轉位單元)
* Transposition (轉位作用) – short segment of DNA moves from original site to a new site
* Transposable elements (TEs) – DNA segments that move    * “Jumping genes”* Both ends of many TEs have inverted repeats (IRs)    * identical but run in opposite directions
    * IR ranges from 9 to 40 bp
* may contain a central region that encodes transposase
    * an enzyme that facilitates transposition* may facilitate recombination, or crossing over between different chromosomes
* insertion with TEs
    * within a protein coding seq, block protein production
    * within a regulatory seq, in/decrease protein production
* Ex 費城基因轉位 -> 導致血癌
* TEs may create new sites for alternative splicing in RNA transcript
* TEs 多半是有破壞性的 -> 生物多樣性

## Proteomics (蛋白體學）
* Entire collection of a species’ proteins
* due to gene regulation, cell will only produce a subset of it proteome
    * 基因會根據不同細胞，不同時間，不同環境才會表現，產生不同的蛋白質
    * Ex外在環境 Heat shock, stress response protein, 把細胞放在40度會產生
    * Ex外在環境 輻射線 -> DNA 修補的酵素
    
### 2D Gel Electrophoresis（二維電泳）
* isoelectric focus 
    * 第一維：用帶電量來區分蛋白質, 用pH來排列等電位（帶電會影響泳動速度）
    * separates proteins according to their net charge at a given pH
![](http://1.bp.blogspot.com/-hJMxoQalLxQ/T_hLBMMSTuI/AAAAAAAABf8/Ae2530wP03s/s1600/Isoelectric+Point.gif)
![](http://site.motifolio.com/images/Separation-of-protein-molecules-by-isoelectric-focusing-6111185.png)
* 第二維：泳動的速度由分子大小來決定

### Mass Spectroscopy (質譜儀) 
* LC-Mass-Mass
* Proteins can be identified by their unique amino acid sequence

## Proteomes (蛋白體)
* Relative abundance of proteins    * Abundance in genome    * Abundance in cell
* Ex liver vs muscle
    * liver:
        * metabolic enzymes > 50%
        * structural proteins < 10%
        * motor proteins < 5%
    * muscle:
        * metabolic enzymes < 10%
        * structural proteins 20-30%
        * motor proteins 25-40%
    
### Type of proteins
* Metabolic enzymes
* Structural proteins
* Motor proteins
* Cell-signaling proteins
    * 跟環境影響有關（ex 過氧化氫環境產生大量自由基, oxident）
    * ex p53
* Transport proteins
* Gene expression and regulation proteins
* Protective proteins
    * Help survive environmental stress (heat shock protein, DNA 修補）

## Proteomes are larger than genomes
### Alternative splicing
* exon: 表現序列
* intron: 插入序列
* 出現不同的剪接方式（留下不同組合的exon，產生不同的蛋白質）

![](http://upload.wikimedia.org/wikipedia/commons/7/7a/Alternative_splicing.jpg)

### Post-translational covalent modification
*  Permanent 
    * 增加糖蛋白、脂質
*  Transient 
    * 磷酸化（常為傳遞訊號 kinase, phosphatase)、乙烯化 甲基化
    * Phosphorylation, methylation, acetylation
    
## Systems Biology
* 利用系統的概念（像circuit）來觀察基因間的交互作用與功能性的改變
* Cancer Genome Atlas project
* chips and NGS-seq