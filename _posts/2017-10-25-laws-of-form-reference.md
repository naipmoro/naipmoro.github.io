---
layout: post
title: "Laws of Form Reference"
date: 2017-10-25
---
A collection of essential equations from _LoF_.
<!--more-->

A [pdf version]({{ "/assets/pdf/lofref.pdf" | absolute_url }}) 
is available.

{::comment} load enclose.js {:/comment}
$\require{enclose}$
$
\newcommand{\CR}[1]{\enclose{actuarial}{#1}}
\newcommand{\st}[1]{\small\{\text{#1}}}
$

$$\begin{array}{l l}
\textbf{Axioms} & \\
\CR{\CR{p}\,p} =    & \st{(Position J1)} \\
\CR{\CR{p\,r}\;\CR{q\,r}} = \CR{\CR{p}\;\CR{q}}\,r & \st{(Transposition J2)} \\
 & \\
\textbf{Consequences} & \\
\CR{\CR{p}} = p 	  	& \st{(Reflexion C1)} \\
\CR{p\, q} \,q = \CR{p}\, q & \st{(Generation C2)}\\
\CR{\;\,}\, p = \CR{\;\,} & \st{(Integration C3)}\\
\CR{\CR{p}\,q}\, p = p & \st{(Occultation C4)}\\
p\,p = p & \st{(Iteration C5)}\\
\CR{\CR{p}\;\CR{q}}\;\CR{\CR{p}\,q} = p & \st{(Extension C6)}\\
\CR{\CR{\CR{p}\,q}\,r} = \CR{p\,r}\; \CR{\CR{q}\,r} & \st{(Echelon C7)}\\
\CR{\CR{p}\; \CR{q\, x}\; \CR{r \,x}} 
 = \CR{\CR{p} \;\CR{q}\; \CR{r}}\; \CR{\CR{p}\; \CR{x}} & \st{(Modified transposition C8)}\\
\CR{\CR{\CR{p}\; \CR{r}} \;\CR{\CR{q}\; \CR{r}} \;\CR{\CR{x}\, r} \;\CR{\CR{y}\, r}} 
= \CR{\CR{r}\, p \,q}\; \CR{r\, x\, y} & \st{(Crosstransposition C9)}\\
 & \\
\textbf{Corollaries} & \\
\CR{p}\, p = \CR{\;\,} & \st{(J1.1)}\\
\CR{\CR{p}\, p\, q} = & \st{(J1.2)}\\
\CR{p\, r}\; \CR{q\, r} = \CR{\CR{\CR{p}\; \CR{q}}\, r} & \st{(J2.1)}\\
\CR{\CR{\;\,}}\, p = p & \st{(B2)}\\
\CR{\CR{\;\,}\, p} = & \st{(C3.1)}\\
\CR{p\, q} \;\CR{p} = \CR{p} & \st{(C4.1)}\\
\CR{\CR{p}\, q} \;\CR{p \,q} = \CR{q} & \st{(C6.1)}\\
\CR{\CR{\CR{p}\, q} \;\CR{p\, q}} = q & \st{(Robbins C6.2)}\\
\CR{\CR{p}\; \CR{q\, r}} = \CR{\CR{p}\; \CR{q}}\; \CR{\CR{p}\; \CR{r}} & \st{(C8.1)}\\
\CR{\CR{\CR{p}\; \CR{r}} \;\CR{\CR{q} \,r}} = \CR{\CR{r}\, p}\; \CR{r\, q} & \st{(C9.1)}\\
 & \\
\textbf{General theorems} & \\
\CR{\CR{p_1\,r}\; \CR{p_2\,r} \dots \CR{p_n \,r}} = \CR{\CR{p_1} \;\CR{p_2} \dots \CR{p_n}} \,r & \st{(J2*)}\\
\CR{p_1\, r}\; \CR{p_2\, r} \dots \CR{p_n r} = \CR{\CR{\CR{p_1}\; \CR{p_2}\dots \CR{p_n}}\, r} & \st{(J2.1*)}\\
\CR{\CR{\CR{\CR{p_n\, q}\dots }\, p_2}\, p_1}\, q = \CR{\CR{\CR{\CR{p_n}\dots }\, p_2}\, p_1}\, q & \st{(C2*)}\\
\CR{\CR{p}\; \CR{q_1\, x}\; \CR{q_2 \,x}\dots \CR{q_n\, x}} = \CR{\CR{p}\; \CR{q_1}\; \CR{q_2}\dots \CR{q_n}}\; \CR{\CR{p}\; \CR{x}} & \st{(C8*)}\\
\CR{\CR{\CR{p_1}\; \CR{r}}\; \CR{\CR{p_2}\; \CR{r}}\dots \CR{\CR{p_n} \;\CR{r}} \;\;\; \CR{\CR{x_1}\, r}\; \CR{\CR{x_2}\, r}\dots \CR{\CR{x_m}\, r}} & \\
\quad = \CR{\CR{r}\, p_1\, p_2\dots p_n}\; \CR{r\, x_1\, x_2 \dots x_m} & \st{(C9*)}\\
\small{\text{For all even $n ≥ 2$:}} & \\
 \CR{\CR{\CR{\CR{p_n}\dots }\, p_2}\, p_1} = \CR{\CR{p_n}\, p_{n-1}\dots p_3 \,p_1}\dots \CR{\CR{p_4}\, p_3\, p_1}\;\;\; \CR{\CR{p_2}\, p_1} & \st{(C7.1*)}\\
\small{\text{and:}} & \\ 
\CR{\CR{\CR{\CR{\CR{p_{n+1}}\, p_n}\dots }\, p_2}\, p_1} & \\
\quad = \CR{p_{n+1} \,p_{n-1}\dots p_3 \,p_1}\;\;\; \CR{\CR{p_n}\, p_{n-1}\dots p_3 \,p_1}\dots \CR{\CR{p_4}\, p_3 \,p_1}\;\;\; \CR{\CR{p_2}\, p_1} & \st{(C7.2*)}\\
\end{array}$$


