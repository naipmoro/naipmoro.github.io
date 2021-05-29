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

This is an equation reference for other _Laws of Form_ posts. For axioms
and consequences, we use Spencer-Brown's original labels. For all other
equations, we use variations on the following transformations (where
we simplify every $\CR{\CR{x}}$ to $x$):
  1. Let the _compliment_ of a form result from
     crossing the form. Then the compliment of an equation $E$, denoted
     by $En$, equates the compliments of the LHS and RHS of $E$.
     For example, if $E$ is $p=q$, then $En$ is $\CR{p}=\CR{q}$. Clearly,
     $E \leftrightarrow En$.
  2. The _contradual_ of a form results from crossing every
     variable. For example, the contradual of $\CR{p\,\CR{q}}$ is
     $\CR{\CR{p}\,q}$. The contradual of an equation $E$, denoted by
     $Ec$, equates the contraduals of
     the LHS and RHS of the equation. Since we are effectively substituting
     the same value for each instance of a given variable, $E \leftrightarrow
     Ec$.
  3. The _dual_ of a form results from crossing every variable _and_ the
     entire form (i.e., a combination of contradual and compliment).
     The dual of an equation $E$ is denoted by $Ed$. As above,
     $E \leftrightarrow Ed$.

_Remark._ All three transformations are involutions: whether $t=n,c,$ or $d$,
$Ett=E$. Among the transformations, duals are particularly significant ---
interpreted logically, $Ed$
means the same as $E$ with the truth values reversed. Occasionaly, the same
equation can be the result of more than one transformation. In such cases, we
arbitrarily choose one for the label.

$$\begin{array}{l l}
\textbf{Axioms} & \\[1ex]
\CR{\CR{a}\,a} =    & \st{(Position J1)} \\
\CR{\CR{ac\v{b}}\;\CR{bc}} = \CR{\CR{a\v{b}}\;\CR{b}}\,c & \st{(Transposition J2)} \\
 & \\
\textbf{Consequences} & \\[1ex]
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
\textbf{Corollaries} & \\[1ex]
\CR{a}\, a = \CR{\b{a}} & \st{(J1d)}\\
\CR{\CR{a}\, a b} = & \st{(J1.1 generalization of J1)}\\
\CR{a c\v{b}}\; \CR{b c} = \CR{\CR{\CR{a\v{b}}\; \CR{b}}\, c} & \st{(J2n)}\\
\CR{\CR{\b{a}}}\, a = a & \st{(Meguire B2)}\\
\CR{\CR{\b{a}}\, a} = & \st{(C3n)}\\
\CR{a b} \;\CR{a\v{b}} = \CR{a\v{b}} & \st{(C4c)}\\
\CR{\CR{a}\, b} \;\CR{a b} = \CR{b} & \st{(C6c)}\\
\CR{\CR{\CR{a}\, b} \;\CR{a b}} = b & \st{(Robbins C6d)}\\
\CR{\CR{a\v{b}}\; \CR{b r}} = \CR{\CR{a\v{b}}\; \CR{b}}\; \CR{\CR{a\v{b}}\; \CR{r\v{b}}} & \st{(C8.1 special case of C8)}\\
\CR{\CR{\CR{a}\; \CR{r}} \;\CR{\CR{x} \,r}} = \CR{\CR{r}\, a}\; \CR{r x} & \st{(C9.1 special case of C9)}\\
 & \\
\textbf{General theorems} & \\[1ex]
\CR{\CR{a_1r}\; \CR{a_2r} \dots \CR{a_n r}} = \CR{\CR{a_1} \;\CR{a_2} \dots \CR{a_n}} \,r & \st{(J2*)}\\
\CR{a_1 r}\; \CR{a_2 r} \dots \CR{a_n r} = \CR{\CR{\CR{a_1}\; \CR{a_2}\dots \CR{a_n}}\, r} & \st{(J2n*)}\\
\CR{\CR{\CR{\CR{a_n b}\dots }\, a_2}\, a_1}\, b = \CR{\CR{\CR{\CR{a_n}\dots }\, a_2}\, a_1}\, b & \st{(C2*)}\\
\CR{\CR{a\v{b_1}}\;\CR{b_1r}\;\CR{b_2r}\dots \CR{b_nr}} =
\CR{\CR{a\v{b_1}}\;\CR{b_1}\;\CR{b_2}\dots \CR{b_n}}\;\CR{\CR{a\v{b_1}}\;\CR{r\v{b_1}}} & \st{(C8*)}\\
\CR{\CR{\CR{a_1}\; \CR{r}}\; \CR{\CR{a_2}\; \CR{r}}\dots \CR{\CR{a_n} \;\CR{r}} \; \CR{\CR{x_1}\, r}\; \CR{\CR{x_2}\, r}\dots \CR{\CR{x_m}\, r}} & \\
\quad = \CR{\CR{r}\, a_1 a_2\dots a_n}\; \CR{r x_1 x_2 \dots x_m} & \st{(C9*)}\\[1.5ex]
\small{\text{For all even $n ≥ 2$,}} & \\
 \CR{\CR{\CR{\CR{a_n}\dots }\, a_2}\, a_1} = \CR{\CR{a_n}\, a_{n-1}\dots a_3 a_1}\dots \CR{\CR{a_4}\, a_3 a_1}\;\CR{\CR{a_2}\, a_1} & \st{(C7.1*)}\\[-1ex]
\small{\text{and,}} & \\
\CR{\CR{\CR{\CR{\CR{a_{n+1}}\, a_n}\dots }\, a_2}\, a_1} & \\
\quad = \CR{a_{n+1} a_{n-1}\dots a_3 \,a_1}\; \CR{\CR{a_n}\, a_{n-1}\dots a_3 a_1}\dots \CR{\CR{a_4}\, a_3 a_1}\;\CR{\CR{a_2}\, a_1} & \st{(C7.2*)}\\
\end{array}$$

<br>
_Note:_ Proofs of the general theorems are given
in [this post]({% post_url 2017-07-28-ch7-lof %}).
