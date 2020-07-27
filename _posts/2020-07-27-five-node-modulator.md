---
layout: post
title: "A five-node modulator circuit"
date: 2020-07-27
---
George Spencer-Brown and Luis H. Kauffman
have demonstrated six-node modulators, and the question arises whether that is
the theoretical minimum.  It turns out that five-node modulators do exist.
<!--more-->

The following _reentry diagram_ depicts a logic circuit where each node is a
NOR gate.

![five-node]({{ "/assets/svg/fivenode.svg" | absolute_url }})  
Figure 1. A five-node modulator

<br>
Input **_A_** is a wave of alternating 1s and 0s (true and false values under
the usual interpretation).  The output appears at node $\mathbf{m_3}$ as a doubling
of the input's wavelength (or halving of its frequency), hence the "modulator"
designation.  For example, an input of 1010... will produce outputs such as
11001100... or 10011001..., depending on the phase shift.

### Evaluating the modulator

In a reentry diagram, the nodes are given a specific order and
node values are propagated in sequence from earlier to later nodes,
beginning with $\mathbf{m_0}$.  Where a node's value depends on nodes that are later
in the sequence, we interpret that as requiring the _previous_ values of those
nodes.  Consequently, we need to assign initial values to $\mathbf{m_1}$, $\mathbf{m_2}$,
$\mathbf{m_3}$, and $\mathbf{m_4}$ before the modulator begins to run.

The following _run-table_ shows one such assignment in column $\mathbf t_0$
(time zero). Notice that column $\mathbf t_5$ is a repeat of $\mathbf t_1$,
establishing that columns $\mathbf t_1 \ldots \mathbf t_4$ will
repeat indefinitely.

$\newcommand{\st}[1]{\small{\text{#1}}} \newcommand{\stm}[1]{\small{#1}}$
$$
\begin{array}{c  c |  c | c  c  c  c  c }
\mathrm{id} & \mathrm{sources} & \mathbf{t_{0}} & \mathbf{t_{1}} & \mathbf{t_{2}} & \mathbf{t_{3}} & \mathbf{t_{4}} & \mathbf{t_{5}}\\
\hline
\hline
\stm{\mathbf{A}} & \mathrm{-} &  & 1 & 0 & 1 & 0 & 1\\
\hline
\stm{\mathbf{m_0}} & \stm{(\mathrm{A}, \mathrm{m_1}, \mathrm{m_4})} &  & 0 & 0 & 0 & 1 & 0\\
\stm{\mathbf{m_1}} & \stm{(\mathrm{A}, \mathrm{m_0}, \mathrm{m_2})} & 1 & 0 & 1 & 0 & 0 & 0\\
\stm{\mathbf{m_2}} & \stm{(\mathrm{m_0}, \mathrm{m_1}, \mathrm{m_3})} & 1 & 0 & 0 & 1 & 0 & 0\\
\stm{\color{#A05}{\mathbf{m_3}}} & \stm{(\mathrm{m_1}, \mathrm{m_2})} & 1 & \color{#A05}{\mathbf{1}} & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{1}} & \color{#A05}{\mathbf{1}}\\
\stm{\mathbf{m_4}} & \stm{(\mathrm{m_0}, \mathrm{m_1}, \mathrm{m_2})} & 1 & 1 & 0 & 0 & 0 & 1\\
\end{array}
$$

The next example shows an input of 111000..., where $\mathbf t_{13}$ is a repeat
of $\mathbf t_1$ (a valid repeat must occur at the _same point of the input
wave's cycle_).

${}$
$$
\begin{array}{c c | c | c c c c c c c c c c c c c}
\mathrm{id} & \mathrm{sources} & \mathbf{t_{0}} & \mathbf{t_{1}} & \mathbf{t_{2}} & \mathbf{t_{3}} & \mathbf{t_{4}} & \mathbf{t_{5}} & \mathbf{t_{6}} & \mathbf{t_{7}} & \mathbf{t_{8}} & \mathbf{t_{9}} & \mathbf{t_{10}} & \mathbf{t_{11}} & \mathbf{t_{12}} & \mathbf{t_{13}}\\
\hline
\hline
\stm{\mathbf{A}} & \mathrm{-} &  & 1 & 1 & 1 & 0 & 0 & 0 & 1 & 1 & 1 & 0 & 0 & 0 & 1\\
\hline
\stm{\mathbf{m_0}} & \stm{(\mathrm{A}, \mathrm{m_1}, \mathrm{m_4})} &  & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 1 & 0\\
\stm{\mathbf{m_1}} & \stm{(\mathrm{A}, \mathrm{m_0}, \mathrm{m_2})} & 1 & 0 & 0 & 0 & 1 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\
\stm{\mathbf{m_2}} & \stm{(\mathrm{m_0}, \mathrm{m_1}, \mathrm{m_3})} & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 1 & 0 & 0 & 0 & 0\\
\stm{\color{#A05}{\mathbf{m_3}}} & \stm{(\mathrm{m_1}, \mathrm{m_2})} & 1 & \color{#A05}{\mathbf{1}} & \color{#A05}{\mathbf{1}} & \color{#A05}{\mathbf{1}} & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{1}} & \color{#A05}{\mathbf{1}} & \color{#A05}{\mathbf{1}} & \color{#A05}{\mathbf{1}}\\
\stm{\mathbf{m_4}} & \stm{(\mathrm{m_0}, \mathrm{m_1}, \mathrm{m_2})} & 1 & 1 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1\\
\end{array}
$$

By comparison, we can take a quick look at the six-node modulators.

### Spencer-Brown's six-node modulator

Spencer-Brown's stunning picture [1, p. 68] of his six-node modulator (it was
used as the cover of a _LoF_ paperback edition) is frankly incomprehensible,
but encoding it in a reentry diagram (Figure 2) reveals a more tractable
structure.

![spencer-brown]({{ "/assets/svg/sbi.svg" | absolute_url }}){:width="85%"}  
Figure 2. Spencer-Brown's six-node modulator

<br>
Here is a representative run-table:

${}$
$$
\begin{array}{c  c |  c | c  c  c  c  c }
\mathrm{id} & \mathrm{sources} & \mathbf{t_{0}} & \mathbf{t_{1}} & \mathbf{t_{2}} & \mathbf{t_{3}} & \mathbf{t_{4}} & \mathbf{t_{5}} & \mathbf{t_{6}}\\
\hline
\hline
\stm{\mathbf{A}} & \mathrm{-} &  & 1 & 0 & 1 & 0 & 1 & 0\\
\hline
\stm{\mathbf{m_0}} & \stm{(\mathrm{A}, \mathrm{m_1}, \mathrm{m_5})} &  & 0 & 0 & 0 & 1 & 0 & 0\\
\stm{\mathbf{m_1}} & \stm{(\mathrm{A}, \mathrm{m_0}, \mathrm{m_2})} & 1 & 0 & 1 & 0 & 0 & 0 & 1\\
\stm{\mathbf{m_2}} & \stm{(\mathrm{m_0}, \mathrm{m_1}, \mathrm{m_3})} & 1 & 0 & 0 & 1 & 0 & 0 & 0\\
\stm{\color{#A05}{\mathbf{m_3}}} & \stm{(\mathrm{m_1}, \mathrm{m_2}, \mathrm{m_4})} & 1 & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{1}} & \color{#A05}{\mathbf{1}} & \color{#A05}{\mathbf{0}}\\
\stm{\mathbf{m_4}} & \stm{(\mathrm{m_0}, \mathrm{m_2}, \mathrm{m_3})} & 1 & 1 & 1 & 0 & 0 & 0 & 1\\
\stm{\mathbf{m_5}} & \stm{(\mathrm{m_0}, \mathrm{m_1}, \mathrm{m_2})} & 1 & 1 & 0 & 0 & 0 & 1 & 0\\
\end{array}
$$

Columns $\mathbf{t_2} \ldots \mathbf{t_5}$ repeat indefinitely, i.e., column
$\mathbf{t_1}$ can be considered part of the _initialization phase_ but not
part of the circuit's repetition.  Whether initialization phase periods exist
for a modulator is entirely a function of the intial values and the input wave.

### Kauffman's six-node modulator

Unlike Spencer-Brown, Kauffman makes a determined effort to motivate his
modulator [2, pp. 121--123], but the description remains forbidding.  Figure 3
shows a simpler reentry version.

![kauffman]({{ "/assets/svg/kauff.svg" | absolute_url }}){:width="85%"}  
Figure 3. Kauffman's six-node modulator

<br>
Below is a run-table with initial values chosen to replicate the circuit
from Kauffman's paper.

${}$
$$
\begin{array}{c  c |  c | c  c  c  c  c }
\mathrm{id} & \mathrm{sources} & \mathbf{t_{0}} & \mathbf{t_{1}} & \mathbf{t_{2}} & \mathbf{t_{3}} & \mathbf{t_{4}} & \mathbf{t_{5}}\\
\hline
\hline
\stm{\mathbf{A}} & \mathrm{-} &  & 1 & 0 & 1 & 0 & 1\\
\hline
\stm{\mathbf{m_0}} & \stm{(\mathrm{A}, \mathrm{m_1}, \mathrm{m_5})} &  & 0 & 0 & 0 & 1 & 0\\
\stm{\mathbf{m_1}} & \stm{(\mathrm{A}, \mathrm{m_0}, \mathrm{m_3})} & 0 & 0 & 1 & 0 & 0 & 0\\
\stm{\mathbf{m_2}} & \stm{(\mathrm{m_1}, \mathrm{m_4})} &  & 1 & 0 & 0 & 0 & 1\\
\stm{\mathbf{m_3}} & \stm{(\mathrm{m_1}, \mathrm{m_2})} & 0 & 0 & 0 & 1 & 1 & 0\\
\stm{\color{#A05}{\mathbf{m_4}}} & \stm{(\mathrm{m_0}, \mathrm{m_2})} & 0 & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{1}} & \color{#A05}{\mathbf{1}} & \color{#A05}{\mathbf{0}} & \color{#A05}{\mathbf{0}}\\
\stm{\mathbf{m_5}} & \stm{(\mathrm{m_0}, \mathrm{m_4})} & 1 & 1 & 0 & 0 & 0 & 1\\
\end{array}
$$

The reader may notice that node $\mathbf{m_3}$ is also emitting a modulated
wave.  That, however, is a spurious result peculiar to these particular initial
values and input wave.  In general, only $\mathbf{m_4}$ consistently produces
the proper modulation.

A significant property of all modulators is _robustness_: modulation will occur
for _any_ set of intial values and whatever the phase of the input wave.

(_Note:_ This page is a modified excerpt from a work in progress [3])

### References
1. G. Spencer-Brown. _Laws of Form_. George Allen and Unwin Ltd, London, 1969.
2. Luis H. Kauffman. _Laws of Form - An Exploration in Mathematics
and Foundations. Rough Draft_. Unpublished manuscript, c. 2005
(<http://www.math.uic.edu/~kauffman/Laws.pdf>).
3. Naip Moro. _Notes on the modulator function from Laws of Form. Work in
Progress_, 2020.
