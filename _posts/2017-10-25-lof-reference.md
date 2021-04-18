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
\newcommand{\v}[1]{\vphantom{#1}}
\newcommand{\b}[1]{\vphantom{#1}\hphantom{#1}}
$

$$\begin{array}{l l}
\textbf{Axioms} & \\
\CR{\CR{p}\,p} =    & \st{(Position J1)} \\
\CR{\CR{pr}\;\CR{qr}} = \CR{\CR{p}\;\CR{q}}\,r & \st{(Transposition J2)} \\
 & \\
\textbf{Consequences} & \\
\CR{\CR{a}} = a 	  	& \st{(Reflexion C1)} \\
\CR{a b} \,b = \CR{a\v{b}}\, b & \st{(Generation C2)}\\
\CR{\b{a}}\, a = \CR{\b{a}} & \st{(Integration C3)}\\
\CR{\CR{a}\,b}\, a = a & \st{(Occultation C4)}\\
aa = a & \st{(Iteration C5)}\\
\CR{\CR{a\v{b}}\;\CR{b}}\;\CR{\CR{a\v{b}}\,b} = a & \st{(Extension C6)}\\
\CR{\CR{\CR{a}\,b}\,c} = \CR{ac\v{b}}\; \CR{\CR{b}\,c} & \st{(Echelon C7)}\\
\CR{\CR{a\v{b}}\; \CR{b r}\; \CR{c r\v{b}}}
 = \CR{\CR{a\v{b}} \;\CR{b}\; \CR{c\v{b}}}\; \CR{\CR{a\v{b}}\; \CR{r\v{b}}} & \st{(Modified transposition C8)}\\
\CR{\CR{\CR{a\v{b}}\; \CR{r\v{b}}} \;\CR{\CR{b}\; \CR{r\v{b}}} \;\CR{\CR{x\v{b}}\, r} \;\CR{\CR{y\v{b}}\, r}}
= \CR{\CR{r}\, a b}\; \CR{r x y} & \st{(Crosstransposition C9)}\\
 & \\
\textbf{Corollaries} & \\
\CR{a}\, a = \CR{\b{a}} & \st{(J1.1)}\\
\CR{\CR{a}\, a b} = & \st{(J1.2)}\\
\CR{p r}\; \CR{q r} = \CR{\CR{\CR{p}\; \CR{q}}\, r} & \st{(J2.1)}\\
\CR{\CR{\b{a}}}\, a = a & \st{(B2)}\\
\CR{\CR{\b{a}}\, a} = & \st{(C3.1)}\\
\CR{a b} \;\CR{a\v{b}} = \CR{a\v{b}} & \st{(C4.1)}\\
\CR{\CR{a}\, b} \;\CR{a b} = \CR{b} & \st{(C6.1)}\\
\CR{\CR{\CR{a}\, b} \;\CR{a b}} = b & \st{(Robbins C6.2)}\\
\CR{\CR{a\v{b}}\; \CR{b r}} = \CR{\CR{a\v{b}}\; \CR{b}}\; \CR{\CR{a\v{b}}\; \CR{r\v{b}}} & \st{(C8.1)}\\
\CR{\CR{\CR{a}\; \CR{r}} \;\CR{\CR{x} \,r}} = \CR{\CR{r}\, a}\; \CR{r x} & \st{(C9.1)}\\
 & \\
\textbf{General theorems} & \\
\CR{\CR{a_1r}\; \CR{a_2r} \dots \CR{a_n r}} = \CR{\CR{a_1} \;\CR{a_2} \dots \CR{a_n}} \,r & \st{(J2*)}\\
\CR{a_1 r}\; \CR{a_2 r} \dots \CR{a_n r} = \CR{\CR{\CR{a_1}\; \CR{a_2}\dots \CR{a_n}}\, r} & \st{(J2.1*)}\\
\CR{\CR{\CR{\CR{a_n b}\dots }\, a_2}\, a_1}\, b = \CR{\CR{\CR{\CR{a_n}\dots }\, a_2}\, a_1}\, b & \st{(C2*)}\\
\CR{\CR{a\v{b_1}}\;\CR{b_1r}\;\CR{b_2r}\dots \CR{b_nr}} =
\CR{\CR{a\v{b_1}}\;\CR{b_1}\;\CR{b_2}\dots \CR{b_n}}\;\CR{\CR{a\v{b_1}}\;\CR{r\v{b_1}}} & \st{(C8*)}\\
\CR{\CR{\CR{a_1}\; \CR{r}}\; \CR{\CR{a_2}\; \CR{r}}\dots \CR{\CR{a_n} \;\CR{r}} \; \CR{\CR{x_1}\, r}\; \CR{\CR{x_2}\, r}\dots \CR{\CR{x_m}\, r}} & \\
\quad = \CR{\CR{r}\, a_1 a_2\dots a_n}\; \CR{r x_1 x_2 \dots x_m} & \st{(C9*)}\\
\small{\text{For all even $n ≥ 2$,}} & \\
 \CR{\CR{\CR{\CR{a_n}\dots }\, a_2}\, a_1} = \CR{\CR{a_n}\, a_{n-1}\dots a_3 a_1}\dots \CR{\CR{a_4}\, a_3 a_1}\;\CR{\CR{a_2}\, a_1} & \st{(C7.1*)}\\
\small{\text{and,}} & \\
\CR{\CR{\CR{\CR{\CR{a_{n+1}}\, a_n}\dots }\, a_2}\, a_1} & \\
\quad = \CR{a_{n+1} a_{n-1}\dots a_3 \,a_1}\; \CR{\CR{a_n}\, a_{n-1}\dots a_3 a_1}\dots \CR{\CR{a_4}\, a_3 a_1}\;\CR{\CR{a_2}\, a_1} & \st{(C7.2*)}\\
\end{array}$$

<br>
_Note:_ Proofs of the general theorems are given
in [this post]({% post_url 2017-07-28-ch7-lof %}).
