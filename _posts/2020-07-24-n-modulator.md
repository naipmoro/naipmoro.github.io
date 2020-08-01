---
layout: post
title: "The n-modulator"
date: 2020-07-24
---
A brief overview of the _n_-modulator, a generalization of Spencer-Brown's
original modulator circuit.
<!--more--> $\newcommand{\stm}[1]{\small{#1}}$

___________________________________________________________________________
<br>
### Introduction 

Near the end of _Laws of Form_ [1, p. 67], we are presented with a diagram of
the so-called _modulator function_.  Figure 1 pictures it essentially as it
appears in the book (I've labeled the nodes to clarify the underlying
structure).

![orig-mod]({{ "/assets/svg/sb_mod2_orig.svg" | absolute_url }})  
Figure 1. The original modulator

<br>
We interpret each node as a NOR logic gate.[^fn1]
The input is provided via $A$ as a wave of true and false values.  The output
appears at nodes $\mathbf m_5$ and $\mathbf m_7$ as a doubling of the input's
wavelength (or halving of its frequency).  If we use $1$ and $0$ to represent
the true and false values, an input of $1010\ldots$ will produce outputs
such as $11001100\ldots \text{ or  }\,01100110\ldots$,
depending on the phase shift.

Spencer-Brown does not mention, and may not have known, that his modulator
diagram is a tangled version of the symmetric structure in Figure 2.

![mod2]({{ "/assets/svg/mod24a.svg" | absolute_url }})  
Figure 2. The 2-modulator

<br>
In what follows, we omit the source arrows from $A$ and instead distinguish the
input nodes with bold outlines.  It will also prove helpful to distinguish the
output nodes, which we call _modulating nodes_, with dotted outlines
(see Figure 3).

![mod2a]({{ "/assets/svg/mod25.svg" | absolute_url }})  
Figure 3. The 2-modulator with distinguished input and modulating nodes

<br>
The striking symmetry of the 2-modulator immediately enables us to construct a
modulator for any positive integer $n$.  For example, the 3-modulator pictured
in Figure 4 will triple the wavelength of the incoming source.

![mod3]({{ "/assets/svg/mod33.svg" | absolute_url }})  
Figure 4. The 3-modulator

<br>
### Reentry graphs

We can provide a concise definition of the $n$-modulator in terms of
_reentry graphs_.

**Definition 1**  
A _reentry graph_ is a directed cyclic graph composed of a totally ordered set
of vertices (called _nodes_).  By convention we assign integral or alphanumeric
names to the nodes and order them according to the natural order of their
names.  Among the nodes, we distinguish two types in particular:
  - Nodes that are not the target of any other node.  We call them _root
       nodes_.
  - Nodes that target earlier nodes in the order.  We call them _init nodes_.

In practice, we also often distinguish nodes whose output we find
significant.  In an $n$-modulator, these are of course the _modulating nodes_.

**Definition 2**  
For any positive integer $n$, the $n$-modulator is a reentry graph
composed of the $4n$ nodes $m_0, m_1, \ldots, m_{4n-1}$ and a root node
$A$ called the _input wave_.
  - For all $i$, $0\leq i<4n$, $m_i \rightarrow m_{i+1\,(\text{mod}\, 4n)}$.
      This establishes the circular structure of the modulator.
  - The $n$ vertices $m_0, m_4,\ldots, m_{4(n-1)}$ are the _input nodes_.
  - The $n$ vertices $m_{2(n+0)+1}, m_{2(n+1)+1},\ldots, m_{2(2n-1)+1}$
      are the _init nodes_.  Significantly, they are also the _modulating
      nodes_.
  - For each input node $m_k$, $\,A\rightarrow m_k$ and
      $m_k \rightarrow m_{k+2}$. The $m_{k+2}$ are called _skip nodes_.
      Note that the input wave $A$ is injected simultaneously into the $n$
      input nodes.
  - For each init/modulating node $m_j$, $m_j\rightleftarrows m_{j-2n}$.  These
      are the _feedback pairs_, and the $m_{j-2n}$ are the
      _feedback-receptor nodes_ (or simply _receptor nodes_).

A number of results follow immediately from the definition.

**Theorem 1**  
For every $n$-modulator:
  - The input, init, skip, and receptor nodes are mutually disjoint sets, each
      containing $n$ nodes.
  - The even-numbered nodes alternate between input nodes and skip nodes.
  - The first $n$ odd-numbered nodes are the receptor nodes, while the
      remaining $n$ odd nodes are the init nodes.
  - Each node (except $A$) is the target of exactly two source nodes;
      consequently the $n$-modulator is composed of $8n$ total edges.

### Evaluating the n-modulator

Since root nodes are sourceless, they must be assigned values.  In the case of
the $n$-modulator, there is only one root, $A$, to which we assign a boolean
wave such as $11001100\ldots$  This will be the input wave that gets
modulated.

When we turn to evaluating the other (sourced) nodes, the significance of the
graph's total order comes into play.  Nodes are evaluated in sequence,
beginning with $m_0$ and ending with $m_{4n-1}$.  When the source nodes are
earlier than the target node, the evaluation proceeds in the obvious manner.
But when a source is later in the sequence, i.e., when it is an init node, we
use its _previous_ value.  This implies that init nodes must be assigned
initial (time zero) values before the modulator can begin to run.

**Definition 3**  
Let $M_n$ be a $n$-modulator.  The propagation of a new set of
values to all $4n$ nodes will be considered one unit of time.  At time $t$,
the following definitions hold:
  - $A(t)$ is the _value_ of input wave $A$.
  - $m_k(t)$ is the _value_ of node $m_k$.  Let $m_i$ (or $A$) and
      $m_j$ be the two sources of $m_k$.  Then,

$$
  m_k(t) = \left.
  \begin{cases}
    \text{nor}(m_i(t),m_j(t)), & \text{if both } i,j < k \\
    \text{nor}(m_i(t),m_j(t-1)), & \text{if } j > k\\
    \text{nor}(A(t),m_j(t), & \text{if } j < k \\
    \text{nor}(A(t),m_j(t-1), & \text{if } j > k
  \end{cases}
  \right\}.
$$

<br>
To make this concrete, let's briefly run the 2-modulator through the first
tick of the clock.  Assume the input wave $\mathbf A$ is $1010\ldots$
(therefore $\mathbf A(1) = 1$) and let us assign $1$ as the initial value of
the init nodes $\mathbf m_5(0)$ and $\mathbf m_7(0)$. Then,

$$
\begin{alignat*}{3}
\mathbf m_0(1)  \,&=\, \text{nor}(\mathbf A(1), \mathbf m_7(0))    \,&=\, \text{nor}(1, 1) \,&=\, 0 \\
\mathbf m_1(1)  \,&=\, \text{nor}(\mathbf m_0(1), \mathbf m_5(0))  \,&=\, \text{nor}(0, 1) \,&=\, 0 \\
\mathbf m_2(1)  \,&=\, \text{nor}(\mathbf m_0(1), \mathbf m_1(1))  \,&=\, \text{nor}(0, 0) \,&=\, 1 \\
\mathbf m_3(1)  \,&=\, \text{nor}(\mathbf m_2(1), \mathbf m_7(0))  \,&=\, \text{nor}(1, 1) \,&=\, 0 \\
\mathbf m_4(1)  \,&=\, \text{nor}(\mathbf A(1), \mathbf m_3(1))    \,&=\, \text{nor}(1, 0) \,&=\, 0 \\
\mathbf m_5(1)  \,&=\, \text{nor}(\mathbf m_1(1), \mathbf m_4(1))  \,&=\, \text{nor}(0, 0) \,&=\, 1 \\
\mathbf m_6(1)  \,&=\, \text{nor}(\mathbf m_4(1), \mathbf m_5(1))  \,&=\, \text{nor}(0, 1) \,&=\, 0 \\
\mathbf m_7(1)  \,&=\, \text{nor}(\mathbf m_3(1), \mathbf m_6(1))  \,&=\, \text{nor}(0, 0) \,&=\, 1.
\end{alignat*}
$$

If we continue computing values for subsequent time units, we would see
$\mathbf m_5$ emit $1001\ldots$ and $\mathbf m_7$ emit
$1100\ldots$, both double the wavelength of $\mathbf A$ (with $\mathbf
m_5$ being an out-of-phase version).  The reader may verify that an assignment
of initial $\mathbf t_0$ values to other than the init nodes would have no
effect on the computations.

A useful visualization is provided by the following _run-table_.

$$
\begin{array}{c  c |  c | c  c  c  c  c }
\mathrm{id} & \mathrm{sources} & \mathbf{t_{0}} & \mathbf{t_{1}}
& \mathbf{t_{2}} & \mathbf{t_{3}} & \mathbf{t_{4}} & \mathbf{t_{5}}\\
\hline
\hline
\stm{\mathbf{A}} & \mathrm{-} &  & 1 & 0 & 1 & 0 & 1\\
\hline
\stm{\mathbf{m_0}} & \stm{(\mathrm{A}, \mathrm{m_7})}   &   & 0 & 0 & 0 & 1 & 0\\
\stm{\mathbf{m_1}} & \stm{(\mathrm{0}, \mathrm{m_5})}   &   & 0 & 0 & 1 & 0 & 0\\
\stm{\mathbf{m_2}} & \stm{(\mathrm{m_0}, \mathrm{m_1})} &   & 1 & 1 & 0 & 0 & 1\\
\stm{\mathbf{m_3}} & \stm{(\mathrm{m_2}, \mathrm{m_7})} &   & 0 & 0 & 0 & 1 & 0\\
\stm{\mathbf{m_4}} & \stm{(\mathrm{A}, \mathrm{m_3})}   &   & 0 & 1 & 0 & 0 & 0\\
\stm{\mathbf{m_5}} & \stm{(\mathrm{m_1}, \mathrm{m_4})} & 1 & 1 & 0 & 0 & 1 & 1\\
\stm{\mathbf{m_6}} & \stm{(\mathrm{m_4}, \mathrm{m_5})} &   & 0 & 0 & 1 & 0 & 0\\
\stm{\mathbf{m_7}} & \stm{(\mathrm{m_3}, \mathrm{m_6})} & 1 & 1 & 1 & 0 & 0 & 1\\
\end{array}
$$

Notice that column $\mathbf t_5$ is a repetition of column $\mathbf t_1$,
demonstrating that columns $\mathbf t_1 \ldots \mathbf t_4$ will repeat
indefinitely.

(_Note:_ This page is a modified excerpt from a work in progress [2].)

### References
1. G. Spencer-Brown. _Laws of Form_. George Allen and Unwin Ltd, London, 1969.
2. Naip Moro. _Notes on the modulator function from Laws of Form. Work in
Progress_, 2020.

### Footnotes
[^fn1]: NAND logic gates would work equally well, but NOR is more in the spirit
        of _LoF_.
