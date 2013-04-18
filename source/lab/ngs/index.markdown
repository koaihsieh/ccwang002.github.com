---
layout: page
title: "Setup NGS Workflow tool"
date: 2013-03-16
comments: false
footer: true
---

Last updated: 2013-03-16

## Server-wide
### Chinese on Cent OS 5.4
{% codeblock lang:bash %}
$ yum install fonts-chinese
{% endcodeblock %}

### Java 7 JDK
* version 1.7.0_09-icedtea
{% codeblock lang:bash %}
$ yum install java-1.7.0-openjdk*    # install java OpenJDK using yum
{% endcodeblock %}



## Tool

### FastQC
* v0.10.1
* unzip the tar file then run it directly


### seqtk
* <https://github.com/lh3/seqtk>
* Quality trimming and manipulation

### Sickle
* <https://github.com/najoshi/sickle>
* Also for quality trimming

http://www.biostars.org/p/1923/


### Bowtie
* v2.1.0 at `/usr/local/bin`
* compiled from source
* <http://sourceforge.net/projects/bowtie-bio/files/bowtie2/>


### BWA
* 0.6.2 at `/usr/local/bin`
* compiled from source
* <http://sourceforge.net/projects/bio-bwa/files/>


### SAMtools
* 0.1.18 at `/usr/local/bin`
* compiled from source
* <http://sourceforge.net/projects/samtools/files/samtools/>
* code hosted page: <https://github.com/samtools/samtools>


### HTSeq
* 0.5.4p1
* <http://www-huber.embl.de/users/anders/HTSeq/doc/overview.html>
* compiled from source. See [Doc](http://www-huber.embl.de/users/anders/HTSeq/doc/install.html#install)


### IGV
* Integrative Genomics Viewer
* 2.2.4
* zipped binary file from website (need registration)
* run by `./igv.sh`
* <http://www.broadinstitute.org/igv/>


### Rstduio-server

{% codeblock lang:bash %}
$ wget wget http://download2.rstudio.org/rstudio-server-0.97.336-x86_64.rpm
$ rpm -Uvh rstudio-server-0.97.336-x86_64.rpm

{% endcodeblock %}

{% codeblock lang:bash %}

{% endcodeblock %}