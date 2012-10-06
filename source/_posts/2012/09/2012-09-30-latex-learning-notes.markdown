---
layout: post
title: "LaTeX Learning notes"
date: 2012-09-30 12:35
comments: true
categories: 
 - notes
 - latex
---

## Floating 
Reference:  <http://en.wikibooks.org/wiki/LaTeX/Floats,_Figures_and_Captions>  

* 為了避免 float 的物件移位超過某個範圍，可以使用 `placeins` 此套件

    \usepackage[section]{placeins}
    
## Caption

    \caption[short]{long}
    
short 裡面可以放較短的說明

<!-- more-->

###  Side Captions

{% codeblock lang:latex %}
\begin{SCfigure}
  \centering
  \includegraphics[width=0.5\textwidth]%
    {Giraff_picture}% picture filename
  \caption{ ... caption text ... }
\end{SCfigure}
{% endcodeblock %}

### package `caption`

    \usepackage[font=small,format=plain,labelfont=bf,up,textfont=it,up]{caption}
    \usepackage[hypcap]{caption}

* use `hypercap` to give figures and table a hyperlink inside PDF

### Subfigure

{% codeblock lang:latex %}
\begin{figure}
        \centering
        \begin{subfigure}[b]{0.3\textwidth}
                \centering
                \includegraphics[width=\textwidth]{gull}
                \caption{A gull}
                \label{fig:gull}
        \end{subfigure}%
        ~ %add desired spacing between images, e. g. ~, \quad, \qquad etc. 
          %(or a blank line to force the subfigure onto a new line)
        \begin{subfigure}[b]{0.3\textwidth}
                \centering
                \includegraphics[width=\textwidth]{tiger}
                \caption{A tiger}
                \label{fig:tiger}
        \end{subfigure}
        ~ %add desired spacing between images, e. g. ~, \quad, \qquad etc. 
          %(or a blank line to force the subfigure onto a new line)
        \begin{subfigure}[b]{0.3\textwidth}
                \centering
                \includegraphics[width=\textwidth]{mouse}
                \caption{A mouse}
                \label{fig:mouse}
        \end{subfigure}
        \caption{Pictures of animals}\label{fig:animals}
\end{figure}
{% endcodeblock %}


## Label Reference

    See figure~\ref{fig:test} on page~\pageref{fig:test}.
   
## More xeCJK
<http://www.ptt.cc/bbs/LaTeX/M.1287510009.A.2C1.html>

* 將編號轉成中文 <http://www.cherrot.com/2011/09/lyx2-texlive-xecjk-xetex-chinese-pdf-settings>
 