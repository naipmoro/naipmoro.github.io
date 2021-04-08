---
layout: post
title: "Laws of Form in metamath"
date: 2016-12-20
---
Metamath derivations of the primary algebra from G. Spencer-Brown's _Laws
of Form_.
<!--more-->

-----------------------------------------------------------------------------------<br>

### 1. Introduction

[lof.mm][lofmm] presents [metamath][mm] derivations of the Primary Algebra
from Spencer-Brown, G. (1969) _Laws of Form_ (Allen & Unwin, London),
hereafter cited as _LoF_.

The algebra of _LoF_ has a number of models, most significantly Boolean
algebra[^1] and sentential logic, so it may be of some interest to logicians.
From the perspective of metamath, it is a non-trivial example of a system that
requires, indeed is based on, the _empty substitution_.

Access to the empty substitution, in conjunction with metamath's radical
formalism, allows a representation that closely matches _LoF's_ actual
expressions.

_LoF_ is a 2-dimensional notation in which closed curves (boundaries) are
the symbols under investigation, and in which the only property of interest
is whether a given boundary is inside or outside of another boundary,
intersecting boundaries not being allowed. Variables _p q r ..._ will range
over possible arrangements of boundaries (which we call _forms_). It is now
common to call _LoF_ a _boundary algebra_. In _LoF_ all boundaries are
considered equivalent.

The topology of _LoF_ implicitly imposes commutativity on its operations
and transferring this to a linear notation involves compromises. To better
understand the compromises and see the formal cost of linearity was a major
motivation of this exercise.

As has become standard, I use matching parentheses (...) to represent
boundaries. And I need to explicitly state the commutative property.
The ramifications of this last point are felt throughout the ensuing
derivations, as properties that are obvious in the 2D notation have to
be spelled out case by case in auxiliary theorems. The system as formulated
is simply unable to prove general statements of commutativity.

-----------------------------------------------------------------------------------<br>

### 2. Synopsis

Since my derivation of the Primary Algebra (PA) follows Spencer-Brown rather
closely, I spend little time on it here. I do provide a full demonstration
that an alternate basis of **C5** and **C6** is equivalent to PA. I then show
that **C6** alone is adequate. Finally, I show that **C6** is derivable from
the Robbins axiom, implying that a Robbins algebra is a Boolean algebra.[^2]

If metamath is installed on your system, you can confirm
the correctness of the formal derivations in lof.mm by starting the
program, reading in the file, and verifying the steps:

~~~~
$ metamath
Metamath - Version 0.196 31-Dec-2020          Type HELP for help, EXIT to exit.
MM> read lof.mm
Reading source file "lof.mm"... 26646 bytes
26646 bytes were read into the source buffer.
The source has 123 statements; 13 are $a and 52 are $p.
SET EMPTY_SUBSTITUTION was turned ON (allowed) for this database.
No errors were found.  However, proofs were not checked.  Type VERIFY PROOF *
if you want to check them.
MM> verify proof *
0 10%  20%  30%  40%  50%  60%  70%  80%  90% 100%
..................................................
All proofs in the database were verified in 0.01 s.
~~~~

To see the actual steps in the proof of a particular proposition,
for example **c3.0**, execute:
~~~~
MM> show proof c3.0 /lemmon /renumber /no_repeated_steps
~~~~

-----------------------------------------------------------------------------------<br>

### 3. Axioms

In keeping with the spirit of _LoF's_ austerity, I aimed for the most
minimal formalism possible. I start with five constant symbols:

**(** &nbsp;&nbsp; **)** &nbsp;&nbsp; **=** &nbsp;&nbsp; **\|\-** &nbsp;&nbsp;
**form**

and seven basic axioms -- three to provide a recursive definition of 'form',
three common notions (so to speak) to power symbol manipulation, and a
commutativity axiom. Metamath does not distinguish definitions from proper
axioms.

#### _Recursive definition of form_

**void** &nbsp;&nbsp; Empty space is a form.

**encl** &nbsp;&nbsp; If _p_ is a form, enclosing it in parentheses&nbsp; _( p )_
         &nbsp;is a form.

**juxt** &nbsp;&nbsp; If _p_ and _q_ are forms, juxtaposing them as
         &nbsp;_p q_&nbsp; is a form.

#### _Common notions_

**ax-euc** &nbsp;&nbsp; Two things equal to the same thing are equal to each
    other. This is Euclid's first Common Notion and, in an equational logic,
    this and its sibling, transitivity, are the main engine of derivation.
    Formally,&nbsp; _p = q_ &nbsp;and&nbsp; _r = q_
    &nbsp;implies&nbsp; _p = r_.

Euclid's second and third Common Notions are specific to quantity,
so not exactly common. We can rephrase them as: doing the same thing
(e.g., applying the same operation) to equal things leaves equal things.
Applying this to _LoF's_ two operations, enclosure and juxtaposition,
leads to the next two axioms (looked at differently, these can also be
seen as substitution/replacement rules).

**ax-beq** &nbsp;&nbsp; Enclosing equal forms leaves equal forms. We can
    consider this a definition of boundary equality:
    &nbsp; _p = q_ &nbsp;implies&nbsp; _( p ) = ( q )_.

**ax-sub** &nbsp;&nbsp; Juxtaposing the same form with equal forms leaves equal
    forms: &nbsp; _p = q_ &nbsp;implies&nbsp; _p v = q v_.

#### _Commutativity of LoF_

**ax-cmm** &nbsp;&nbsp; _p q = q p_

-----------------------------------------------------------------------------------<br>

### 4. Theorems

The symbol '=' is never defined but it will turn out to obey the expected
laws of an equivalence relation. Specifically, from the common notion
that two things equal to the same thing are equal to each other and from
the commutativity of _LoF_, we derive the reflexivity, symmetry, and
transitivity of '='. Note that such a derivation is not possible in a
traditional formal system without additional axioms -- it is the ability
to reference the empty (or _void_) form that allows it here. For the actual
derivations, see the source file.

**id** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | _p = p_
**sym** &nbsp;&nbsp; | _p = q_ &nbsp;implies&nbsp; _q = p_
**trans** &nbsp;&nbsp; | _p = q_ &nbsp;and&nbsp; _q = r_ &nbsp;implies&nbsp; _p = r_

<br>
The axioms and theorems so far have been transparent, succinct, and
powerful (they embody Boolean algebra, after all), but applying them
would be impractical without further theorems. While this is no different
from any other formal system, here these auxiliary theorems have a
peculiar feeling of inconsequence: they are often tiresome (and sometimes
ugly) commutative elaborations of previous statements, whose only adhoc
utility is to ease the derivation of particular propositions.

I state these below without further comment.

**eucr** &nbsp;&nbsp; | _p = q_ &nbsp;and&nbsp; _p = r_ &nbsp;implies&nbsp; _q = r_
**subr** &nbsp;&nbsp; | _p = q_ &nbsp;implies&nbsp; _u p  =  u q_
**subst** &nbsp;&nbsp; | _p = q_ &nbsp;implies&nbsp; _u p v  =  u q v_
**substr** &nbsp;&nbsp; | _p = q_ &nbsp;implies&nbsp; _u p v  =  v q u_
**subb1** &nbsp;&nbsp; | _p = q_ &nbsp;implies&nbsp; _w ( u p v ) x  =  w ( u q v ) x_
**subb3** &nbsp;&nbsp; | _p = q_ &nbsp;implies&nbsp; _w ( u p v ) x  =  w ( v q u ) x_
**rep** &nbsp;&nbsp; | _p = q_ &nbsp;and&nbsp; _u p v  =  y_ &nbsp;implies&nbsp; _u q v  =  y_
**repbx** &nbsp;&nbsp; | _p = q_ &nbsp;and&nbsp; _w ( u p v ) x  =  y_ &nbsp;implies&nbsp; _w ( u q v ) x  =  y_
**quad** &nbsp;&nbsp; | _p = q_ &nbsp;and&nbsp; _r = s_ &nbsp;implies&nbsp; _p r  =  q s_
**ins** &nbsp;&nbsp; | _p q  =  r s_ &nbsp;implies&nbsp; _p v q  =  r v s_
**cmmx** &nbsp;&nbsp; | _u p v q w  =  u q v p w_
**cmmbx** &nbsp;&nbsp; | _x ( u p v q w ) y  =  x ( u q v p w ) y_
**quadbx** &nbsp;&nbsp; | _p = q_ &nbsp;and&nbsp; _r = s_ &nbsp;implies&nbsp; _x ( u p v r w ) y  =  x ( u q v s w ) y_

<br>
It's hard to know where to stop with auxiliary theorems. Had we chosen
to prove the two additional statements:

&nbsp;&nbsp; _p = q_ &nbsp;and&nbsp; _r = q_ &nbsp;implies&nbsp; _x ( v p u ) w = w ( u r v ) x_  
&nbsp;&nbsp; _p = q_ &nbsp;and&nbsp; _p = r_ &nbsp;implies&nbsp; _x ( v q u ) w = w ( u r v ) x_

we could have reduced significantly the proof of theorem **c9.0**.

-----------------------------------------------------------------------------------<br>

### 5. _Laws of Form_

_LoF_ can be considered a prolonged deduction from two initial 'arithmetic'
equations [_LoF_, p. 12]:

**I1. Number**   &nbsp;&nbsp; | _( )  ( )_ | &nbsp;=&nbsp; | _( )_
**I2. Order**    &nbsp;&nbsp; | _( ( ) )_ | &nbsp;=&nbsp; |

<br>
As mentioned, one of the models of _LoF_ is sentential logic:

| _T_             | &nbsp; &equiv; &nbsp; | _( )_ |
| _F_             | &nbsp; &equiv; &nbsp; | |
| _&not; p_       | &nbsp; &equiv; &nbsp; | _( p )_ |
| _p &or; q_      | &nbsp; &equiv; &nbsp; | _p q_ |
| _p &and; q_     | &nbsp; &equiv; &nbsp; | _( ( p ) ( q ) )_ |
| _p -> q_        | &nbsp; &equiv; &nbsp; | _( p ) q_ |
| _p &harr; q_    | &nbsp; &equiv; &nbsp; | _( ( p ) ( q ) ) ( p q )_ |

<br>
The algebra is self-dual. If we interchange _T_ and _F_, the algebraic laws
continue to hold, with juxtaposition now interpreted as conjunction:

| _T_             | &nbsp; &equiv; &nbsp; | |
| _F_             | &nbsp; &equiv; &nbsp; | _( )_ |
| _&not; p_       | &nbsp; &equiv; &nbsp; | _( p )_ |
| _p &or; q_      | &nbsp; &equiv; &nbsp; | _( ( p ) ( q ) )_ |
| _p &and; q_     | &nbsp; &equiv; &nbsp; | _p q_ |
| _p -> q_        | &nbsp; &equiv; &nbsp; | _( p ( q ) )_ |
| _p &harr; q_    | &nbsp; &equiv; &nbsp; | _( ( ( p ) ( q ) ) ( p q ) )_ |

<br>
In keeping with standard practice, I use the first interpretation
(juxtaposition as disjunction). When refering to the second interpretation,
I call it the 'dual interpretation'.

Spencer-Brown begins with the two axioms:

**J1. Position**      &nbsp;&nbsp; | _( ( p ) p ) =_
**J2. Transposition** &nbsp;&nbsp; | _( ( p r ) ( q r ) ) = ( ( p ) ( q ) ) r_

<br>
and deduces the following consequences [_LoF_, pp. 28-35]:

**C1. Reflexion**         &nbsp;&nbsp; |      _( ( a ) ) = a_
**C2. Generation**        &nbsp;&nbsp; |      _( a b ) b = ( a ) b_
**C3. Integration**       &nbsp;&nbsp; |      _( ) a = ( )_
**C4. Occultation**       &nbsp;&nbsp; |      _( ( a ) b ) a = a_
**C5. Iteration**         &nbsp;&nbsp; |      _a a = a_
**C6. Extension**         &nbsp;&nbsp; |      _( ( a ) ( b ) ) ( ( a ) b ) = a_
**C7. Echelon**           &nbsp;&nbsp; |      _( ( ( a ) b ) c ) = ( a c ) ( ( b ) c )_
**C8. Modified transposition** &nbsp;&nbsp; | _( ( a ) ( b r ) ( c r ) ) = ( ( a ) ( b ) ( c ) ) ( ( a ) ( r ) )_
**C9. Crosstransposition** &nbsp;&nbsp; |     _( ( ( b ) ( r ) ) ( ( a ) ( r ) ) ( ( x ) r ) ( ( y ) r ) ) =_
                                        |     _( ( r ) a b )  (r x y )_

<br>
To see that **J1** and **J2** constitute a complete set of axioms, refer to
chapter 9 of _LoF_ [pp. 50-52].

One of the goals of lof.mm was to establish different bases (initial
axioms) for the algebra. To do this in one file, I need a way to reference
the same theorems in the different bases. Retaining Spencer-Brown's original
numbering scheme for cross-referencing, I label the theorems as **ck.n** (or **jk.n**),
where **ck** (**jk**) refers to _LoF's_ **Ck** (**Jk**) and **n** refers to the basis under
consideration. In other words, **ck.n = ck.m** (**jk.n = jk.m**) for all **n, m**.
_LoF's_ system is **n = 0**.

-----------------------------------------------------------------------------------<br>

### 6. Summary of results

#### System<sub>0</sub>

This version essentially follows _LoF_, so not
much more needs to be said. There is one difference -- theorem **C5** is derived
before **C4** -- and so for those interested, I show the derivation below, as
expressed by metamath.

First the axioms, i.e., Basis<sub>0</sub>:

**j1.0**  &nbsp;&nbsp; | _( ( p ) p ) =_
**j2.0**  &nbsp;&nbsp; | _( ( p r ) ( q r ) ) = ( ( p ) ( q ) ) r_

<br>
Proof of **c5.0**

1 &nbsp;&nbsp;&nbsp; | ( ( p ) p ) p = ( ( p ) ) p | &nbsp;&nbsp;&nbsp;&nbsp; (c2.0)
2 &nbsp;&nbsp;&nbsp; | ( ( p ) ) = p               | &nbsp;&nbsp;&nbsp;&nbsp; (c1.0)
3 &nbsp;&nbsp;&nbsp; | ( ( p ) ) p = p p           | &nbsp;&nbsp;&nbsp;&nbsp; (2,subst)
4 &nbsp;&nbsp;&nbsp; | ( ( p ) p ) p = p p         | &nbsp;&nbsp;&nbsp;&nbsp; (1,3,trans)
5 &nbsp;&nbsp;&nbsp; | ( ( p ) p ) =               | &nbsp;&nbsp;&nbsp;&nbsp; (j1.0)
6 &nbsp;&nbsp;&nbsp; | ( ( p ) p ) p = p           | &nbsp;&nbsp;&nbsp;&nbsp; (5,subst)
7 &nbsp;&nbsp;&nbsp; | p p = p                     | &nbsp;&nbsp;&nbsp;&nbsp; (4,6,eucr)

<br>
#### System<sub>1</sub>

Although System<sub>0</sub> is the only one demonstrated by
Spencer-Brown, and so can be considered canonical, he mentions in his notes an
alternate basis of **C5** and **C6**, but suggests the derivation is 'both
difficult and tedious' [_LoF_, p.89]. Readers can decide for themselves whether
System<sub>1</sub> is any more complicated than
System<sub>0</sub>. The virtue of this basis, as noted by
Spencer-Brown, is the need for only two distinct variables.

The derivation below ends at the point where both **j1.1** and **j2.1** are
proved, since that establishes **c5.1** and **c6.1** as a complete basis.

#### Basis<sub>1</sub>

**c5.1** &nbsp;&nbsp; | _p p = p_
**c6.1** &nbsp;&nbsp; | _( ( p ) ( q ) ) ( ( p ) q ) = p_

<br>
The following lemma is crucial for the proof of **c1.1** Under the dual
interpretation, it is mildly reminiscent of modus ponens:
(p &and; (p -> q)) &harr; (p &and; q)

**lem1.1** &nbsp;&nbsp; | _p ( ( q ) p ) = p q_

<br>
Proof of **lem1.1**

 1 &nbsp;&nbsp;&nbsp; | ( ( q ) ( p ) ) = ( ( p ) ( q ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (cmmbx)
 2 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) ( ( q ) ( p ) ) ( ( q ) p )
     | = ( ( p ) ( q ) ) ( ( p ) q ) ( ( p ) ( q ) ) ( ( q ) p ) | &nbsp;&nbsp;&nbsp;&nbsp; (1 subst)
 3 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) ( ( p ) ( q ) ) ( ( q ) p )
     | = ( ( p ) ( q ) ) ( ( p ) ( q ) ) ( ( p ) q ) ( ( q ) p ) | &nbsp;&nbsp;&nbsp;&nbsp; (cmmx)
 4 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) ( ( q ) ( p ) ) ( ( q ) p )
     | = ( ( p ) ( q ) ) ( ( p ) ( q ) ) ( ( p ) q ) ( ( q ) p ) | &nbsp;&nbsp;&nbsp;&nbsp; (2,3 trans)
 5 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) ( q ) ) = ( ( p ) ( q ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (c5.1)
 6 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) ( q ) ) ( ( p ) q ) ( ( q ) p )
     | = ( ( p ) ( q ) ) ( ( p ) q ) ( ( q ) p ) | &nbsp;&nbsp;&nbsp;&nbsp; (5 ax-sub)
 7 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) ( ( q ) ( p ) ) ( ( q ) p )
     | = ( ( p ) ( q ) ) ( ( p ) q ) ( ( q ) p ) | &nbsp;&nbsp;&nbsp;&nbsp; (4,6 trans)
 8 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (c6.1)
 9 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) ( ( q ) p ) = p ( ( q ) p ) | &nbsp;&nbsp;&nbsp;&nbsp; (8 ax-sub)
10 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) ( ( q ) ( p ) ) ( ( q ) p )
     | = p ( ( q ) p ) | &nbsp;&nbsp;&nbsp;&nbsp; (7,9 trans)
11 &nbsp;&nbsp;&nbsp; | ( ( q ) ( p ) ) ( ( q ) p ) = q | &nbsp;&nbsp;&nbsp;&nbsp; (c6.1)
12 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) ( ( q ) ( p ) ) ( ( q ) p )
     | = p q | &nbsp;&nbsp;&nbsp;&nbsp; (8,11 quad)
13 &nbsp;&nbsp;&nbsp; | p ( ( q ) p ) = p q | &nbsp;&nbsp;&nbsp;&nbsp; (10,12 eucr)

<br>
If we now plug _void_ values into **lem1.1**'s _p_ variable, we
immediately prove:

**c1.1** &nbsp;&nbsp; | ( ( p ) ) = p

<br>
And plugging _void_ values into **c1.1**'s _p_ variable immediately
proves the **I2** arithmetic initial:

**i2.1** &nbsp;&nbsp; | ( ( ) ) =

<br>
**I2** is also directly derivable from the basis by plugging _void_ values
into **c6.1**, followed by two applications of **c5.1**. We now prove one of
the two equations from Basis<sub>0</sub>, **J1**.

**j1.1** &nbsp;&nbsp; | ( ( p ) p ) =

<br>
Proof of **j1.1**

 1 &nbsp;&nbsp;&nbsp; | ( ( p ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (c1.1)
 2 &nbsp;&nbsp;&nbsp; | ( p ) ( ( p ) ) = ( p ) p | &nbsp;&nbsp;&nbsp;&nbsp; (1 subr)
 3 &nbsp;&nbsp;&nbsp; | ( ( p ) ) ( p ) = ( p ) ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (ax-cmm)
 4 &nbsp;&nbsp;&nbsp; | ( ( ) ) = | &nbsp;&nbsp;&nbsp;&nbsp; (i2.1)
 5 &nbsp;&nbsp;&nbsp; | ( ( ( ) ) ( p ) ) = ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (4 subb1)
 6 &nbsp;&nbsp;&nbsp; | ( ( ( ) ) p ) = ( p ) | &nbsp;&nbsp;&nbsp;&nbsp; (4 subb1)
 7 &nbsp;&nbsp;&nbsp; | ( ( ( ) ) ( p ) ) ( ( ( ) ) p ) = ( ( p ) ) ( p ) | &nbsp;&nbsp;&nbsp;&nbsp; (5,6 quad)
 8 &nbsp;&nbsp;&nbsp; | ( ( ( ) ) ( p ) ) ( ( ( ) ) p ) = ( ) | &nbsp;&nbsp;&nbsp;&nbsp; (c6.1)
 9 &nbsp;&nbsp;&nbsp; | ( ( p ) ) ( p ) = ( ) | &nbsp;&nbsp;&nbsp;&nbsp; (7,8 eucr)
10 &nbsp;&nbsp;&nbsp; | ( p ) ( ( p ) ) = ( ) | &nbsp;&nbsp;&nbsp;&nbsp; (3,9 eucr)
11 &nbsp;&nbsp;&nbsp; | ( p ) p = ( ) | &nbsp;&nbsp;&nbsp;&nbsp; (2,10 eucr)
12 &nbsp;&nbsp;&nbsp; | ( ( p ) p ) = ( ( ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (11 ax-beq)
13 &nbsp;&nbsp;&nbsp; | ( ( p ) p ) = | &nbsp;&nbsp;&nbsp;&nbsp; (12,4 trans)

<br>
We now prove **C4**.

**c4.1** &nbsp;&nbsp; | ( ( p ) q ) p = p

<br>
Proof of **c4.1**

1 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (c6.1)
2 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) ( ( p ) q ) = ( ( p ) q ) p | &nbsp;&nbsp;&nbsp;&nbsp; (1 substr)
3 &nbsp;&nbsp;&nbsp; | ( ( p ) q ) ( ( p ) q ) = ( ( p ) q ) | &nbsp;&nbsp;&nbsp;&nbsp; (c5.1)
4 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) ( ( p ) q )
   | = ( ( p ) ( q ) ) ( ( p ) q ) | &nbsp;&nbsp;&nbsp;&nbsp; (3 subr)
5 &nbsp;&nbsp;&nbsp; | ( ( p ) q ) p = ( ( p ) ( q ) ) ( ( p ) q ) | &nbsp;&nbsp;&nbsp;&nbsp; (2,4 eucr)
6 &nbsp;&nbsp;&nbsp; | ( ( p ) q ) p = p | &nbsp;&nbsp;&nbsp;&nbsp; (5,1 trans)

<br>
We will need this corollary of **c4.1**:

**c4cor.1** &nbsp;&nbsp; | ( p q ) ( p ) = ( p )

<br>
Proof of **c4cor.1**

1 &nbsp;&nbsp;&nbsp; | ( ( p ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (c1.1)
2 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) q ) ( p ) = ( p q ) ( p ) | &nbsp;&nbsp;&nbsp;&nbsp; (1 subb1)
3 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) q ) ( p ) = ( p ) | &nbsp;&nbsp;&nbsp;&nbsp; (c4.1)
4 &nbsp;&nbsp;&nbsp; | ( p q ) ( p ) = ( p ) | &nbsp;&nbsp;&nbsp;&nbsp; (2,3 eucr)

<br>
And this corollary of **c6.1**:

**c6cor.1** &nbsp;&nbsp; | ( ( p ) q ) ( p q ) = ( q )

<br>
Proof of **c6cor.1**

1 &nbsp;&nbsp;&nbsp; | q p = p q | &nbsp;&nbsp;&nbsp;&nbsp; (ax-cmm)
2 &nbsp;&nbsp;&nbsp; | q ( p ) = ( p ) q | &nbsp;&nbsp;&nbsp;&nbsp; (ax-cmm)
3 &nbsp;&nbsp;&nbsp; | ( ( q ) ) = q | &nbsp;&nbsp;&nbsp;&nbsp; (c1.1)
4 &nbsp;&nbsp;&nbsp; | ( ( ( q ) ) ( p ) ) ( ( ( q ) ) p ) = ( q ) | &nbsp;&nbsp;&nbsp;&nbsp; (c6.1)
5 &nbsp;&nbsp;&nbsp; | ( q ( p ) ) ( ( ( q ) ) p ) = ( q ) | &nbsp;&nbsp;&nbsp;&nbsp; (3,4 repbx)
6 &nbsp;&nbsp;&nbsp; | ( q ( p ) ) ( q p ) = ( q ) | &nbsp;&nbsp;&nbsp;&nbsp; (3,5 repbx)
7 &nbsp;&nbsp;&nbsp; | ( ( p ) q ) ( q p ) = ( q ) | &nbsp;&nbsp;&nbsp;&nbsp; (2,6 repbx)
8 &nbsp;&nbsp;&nbsp; | ( ( p ) q ) ( p q ) = ( q ) | &nbsp;&nbsp;&nbsp;&nbsp; (1,7 repbx)

<br>
We prove **C7**.

**c7.1** &nbsp;&nbsp; | ( ( ( p ) q ) r ) = ( p r ) ( ( q ) r )

<br>
Beyond a certain length, proofs become dominated by commutations and
substitutions of equal forms, making them practically unreadable. The full
41-step version of c7.1 is an example (have metamath execute `show proof c7.1
/lemmon /renumber /no_repeated_steps` to see all the steps). Below is a much
condensed version where rearrangement of terms and substitution of equals go
unmentioned.

Condensed proof of **c7.1**

 1 &nbsp;&nbsp;&nbsp; | ( ( ( ( ( p ) q ) r ) ) ( p q ) ) ( ( ( ( ( p ) q ) r ) ) p q )
    | = ( ( ( p ) q ) r ) | &nbsp;&nbsp;&nbsp;&nbsp; (c6.1)
 2 &nbsp;&nbsp;&nbsp; | ( ( ( p ) q ) r ( p q ) ) ( ( ( p ) q ) p r q )
    | = ( ( ( p ) q ) r ) | &nbsp;&nbsp;&nbsp;&nbsp; (c1.1 twice)
 3 &nbsp;&nbsp;&nbsp; | ( ( q ) r ) ( ( ( p ) q ) p r q ) = ( ( ( p ) q ) r ) | &nbsp;&nbsp;&nbsp;&nbsp; (c6cor.1)
 4 &nbsp;&nbsp;&nbsp; | ( ( q ) r ) ( p r q ) = ( ( ( p ) q ) r ) | &nbsp;&nbsp;&nbsp;&nbsp; (c4.1)
 5 &nbsp;&nbsp;&nbsp; | ( ( ( ( ( p ) q ) r ) ) ( ( p ) ( q ) ) ) ( ( ( ( ( p ) q ) r ) ) ( p ) ( q ) )
    | = ( ( ( p ) q ) r ) | &nbsp;&nbsp;&nbsp;&nbsp; (c6.1)
 6 &nbsp;&nbsp;&nbsp; | ( ( ( p ) q ) r ( ( p ) ( q ) ) ) ( ( ( p ) q ) r ( p ) ( q ) )
    | = ( ( ( p ) q ) r ) | &nbsp;&nbsp;&nbsp;&nbsp; (c1.1 twice)
 7 &nbsp;&nbsp;&nbsp; | ( p r ) ( ( ( p ) q ) r ( p ) ( q ) ) = ( ( ( p ) q ) r ) | &nbsp;&nbsp;&nbsp;&nbsp; (c6.1)
 8 &nbsp;&nbsp;&nbsp; | ( p r ) ( ( p ) ( q ) r ) = ( ( ( p ) q ) r ) | &nbsp;&nbsp;&nbsp;&nbsp; (c4cor.1)
 9 &nbsp;&nbsp;&nbsp; | ( p r ) ( p r q ) ( ( q ) r ) ( ( p ) ( q ) r )
    | = ( ( ( p ) q ) r ) ( ( ( p ) q ) r ) | &nbsp;&nbsp;&nbsp;&nbsp; (4,8 quad)
10 &nbsp;&nbsp;&nbsp; | ( p r ) ( p r q ) ( ( q ) r ) ( ( p ) ( q ) r )
    | = ( ( ( p ) q ) r ) | &nbsp;&nbsp;&nbsp;&nbsp; (c5.1)
11 &nbsp;&nbsp;&nbsp; | ( ( ( p ) q ) r ) = ( p r ) ( ( q ) r ) | &nbsp;&nbsp;&nbsp;&nbsp; (c4.1 twice)

<br>
We can now prove the second of the two equations from Basis<sub>0</sub>, **J2**.
This completes the proof that Basis<sub>1</sub> is at least as powerful as
Basis<sub>0</sub>.

**j2.1** &nbsp;&nbsp; | ( ( p ) ( q ) ) r = ( ( p r ) ( q r ) )

<br>
Proof of **j2.1**

1 &nbsp;&nbsp;&nbsp; | ( ( ( ( p ) ( q ) ) r ) ) = ( ( p ) ( q ) ) r | &nbsp;&nbsp;&nbsp;&nbsp; (c1.1)
2 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ( q ) ) r ) = ( p r ) ( ( ( q ) ) r ) | &nbsp;&nbsp;&nbsp;&nbsp; (c7.1)
3 &nbsp;&nbsp;&nbsp; | ( ( q ) ) = q | &nbsp;&nbsp;&nbsp;&nbsp; (c1.1)
4 &nbsp;&nbsp;&nbsp; | ( p r ) ( ( ( q ) ) r ) = ( p r ) ( q r ) | &nbsp;&nbsp;&nbsp;&nbsp; (3 subb1)
5 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ( q ) ) r ) = ( p r ) ( q r ) | &nbsp;&nbsp;&nbsp;&nbsp; (2,4 trans)
6 &nbsp;&nbsp;&nbsp; | ( ( ( ( p ) ( q ) ) r ) ) = ( ( p r ) ( q r ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (5 ax-beq)
7 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) r = ( ( p r ) ( q r ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (1,6 eucr)

<br>
#### System<sub>2</sub>

Having shown that **C5** and **C6** form a basis, I now show that **C6** alone
suffices. The derivation ends at the point where **c5.2** is proved, since
that establishes that Basis<sub>2</sub> is at least as powerful as
Basis<sub>1</sub>.

#### Basis<sub>2</sub>

**c6.2** &nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) = p

<br>
An important lemma used in the proof of **c1.2**:

**lem2.2** &nbsp;&nbsp; | ( p ) p = ( q ) q

<br>
This is a condensed proof of **lem2.2**.

 1 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) ( ( q ) ) ) ( ( ( p ) ) ( q ) ) = ( p ) | &nbsp;&nbsp;&nbsp;&nbsp; (c6.2)
 2 &nbsp;&nbsp;&nbsp; | ( ( p ) ( ( q ) ) ) ( ( p ) ( q ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (c6.2)
 3 &nbsp;&nbsp;&nbsp; | ( ( ( q ) ) ( ( p ) ) ) ( ( ( q ) ) ( p ) ) = ( q ) | &nbsp;&nbsp;&nbsp;&nbsp; (c6.2)
 4 &nbsp;&nbsp;&nbsp; | ( ( q ) ( ( p ) ) ) ( ( q ) ( p ) ) = q | &nbsp;&nbsp;&nbsp;&nbsp; (c6.2)
 5 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) ( ( q ) ) ) ( ( ( p ) ) ( q ) )
    | ( ( p ) ( ( q ) ) ) ( ( p ) ( q ) ) = ( p ) p | &nbsp;&nbsp;&nbsp;&nbsp; (1,2 quad)
 6 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) ( ( q ) ) ) ( ( ( p ) ) ( q ) )
    | ( ( p ) ( ( q ) ) ) ( ( q ) ( p ) ) = ( q ) q | &nbsp;&nbsp;&nbsp;&nbsp; (3,4 quad)
 7 &nbsp;&nbsp;&nbsp; | ( p ) p = ( q ) q | &nbsp;&nbsp;&nbsp;&nbsp; (5,6 euc)

<br>
Axiom **B3** from Meguire[^3] follows immediately from
**lem2.2** by plugging _void_ values into _q_.

**b3.2** &nbsp;&nbsp; | ( p ) p = ( )

<br>
Now we prove **c1.2**.

**c1.2** &nbsp;&nbsp; | ( ( p ) ) = p

<br>
Proof of **c1.2**

 1 &nbsp;&nbsp;&nbsp; | ( ( p ) ) ( p ) = ( p ) ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (ax-cmm)
 2 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) ) ( p ) = ( p ) ( ( ( p ) ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (ax-cmm)
 3 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) ( p ) ) ( ( ( ( p ) ) ) ( p ) )
    | = ( ( ( ( p ) ) ) ( p ) ) ( ( ( p ) ) ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (ax-cmm)
 4 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) ) ( ( p ) ) = ( ( p ) ) ( p ) | &nbsp;&nbsp;&nbsp;&nbsp; (lem2.2)
 5 &nbsp;&nbsp;&nbsp; | ( ( ( ( p ) ) ) ( ( p ) ) ) ( ( ( ( p ) ) ) ( p ) )
    | = ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (c6.2)
 6 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) ( p ) ) ( ( ( ( p ) ) ) ( p ) ) = ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (4,5 repbx)
 7 &nbsp;&nbsp;&nbsp; | ( ( ( ( p ) ) ) ( p ) ) ( ( ( p ) ) ( p ) ) = ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (3,6 rep)
 8 &nbsp;&nbsp;&nbsp; | ( ( p ) ( ( ( p ) ) ) ) ( ( ( p ) ) ( p ) ) = ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (2,7 repbx)
 9 &nbsp;&nbsp;&nbsp; | ( ( p ) ( ( ( p ) ) ) ) ( ( p ) ( ( p ) ) ) = ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (1,8 repbx)
10 &nbsp;&nbsp;&nbsp; | ( ( p ) ( ( ( p ) ) ) ) ( ( p ) ( ( p ) ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (c6.2)
11 &nbsp;&nbsp;&nbsp; | ( ( p ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (9,10 eucr)

<br>
Next we prove **J1**.

**j1.2** &nbsp;&nbsp; | ( ( p ) p ) =

<br>
Proof of **j1.2**

 1 &nbsp;&nbsp;&nbsp; | ( p ) p = ( ) | &nbsp;&nbsp;&nbsp;&nbsp; (b3.2)
 2 &nbsp;&nbsp;&nbsp; | ( ( p ) p ) = ( ( ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (1 ax-beq)
 3 &nbsp;&nbsp;&nbsp; | ( ( ) ) = | &nbsp;&nbsp;&nbsp;&nbsp; (c1.2)
 4 &nbsp;&nbsp;&nbsp; | ( ( p ) p ) = | &nbsp;&nbsp;&nbsp;&nbsp; (2,3 trans)

<br>
Another lemma.

**lem3.2** &nbsp;&nbsp; | ( p p ) = ( ( ( p ) ) ( ( p ) )

<br>
Proof of **lem3.2**

 1 &nbsp;&nbsp;&nbsp; | ( ( p ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (c1.2)
 2 &nbsp;&nbsp;&nbsp; | p = ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (1 sym)
 3 &nbsp;&nbsp;&nbsp; | ( p p ) = ( p p ) | &nbsp;&nbsp;&nbsp;&nbsp; (id)
 4 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) p ) = ( p p ) | &nbsp;&nbsp;&nbsp;&nbsp; (2,3 repbx)
 5 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) ( ( p ) ) ) = ( p p ) | &nbsp;&nbsp;&nbsp;&nbsp; (2,4 repbx)
 6 &nbsp;&nbsp;&nbsp; | ( p p ) = ( ( ( p ) ) ( ( p ) ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (5 sym)

<br>
We can finally prove **C5**, which demonstrates that Basis<sub>2</sub> is at least
as strong as Basis<sub>1</sub>.

**c5.2** &nbsp;&nbsp; | p p = p

<br>
Proof of **c5.2**

 1 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) ( ( p ) ) ) ( ( ( p ) ) ( p ) ) = ( p ) | &nbsp;&nbsp;&nbsp;&nbsp; (c6.2)
 2 &nbsp;&nbsp;&nbsp; | ( p p ) = ( ( ( p ) ) ( ( p ) ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (lem3.2)
 3 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) ( p ) ) = | &nbsp;&nbsp;&nbsp;&nbsp; (j1.2)
 4 &nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; = ( ( ( p ) ) ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (3 sym)
 5 &nbsp;&nbsp;&nbsp; | ( ( p p ) ) = p p | &nbsp;&nbsp;&nbsp;&nbsp; (c1.2)
 6 &nbsp;&nbsp;&nbsp; | ( ( p p ) ( ( ( p ) ) ( p ) ) ) = p p | &nbsp;&nbsp;&nbsp;&nbsp; (4,5 repbx)
 7 &nbsp;&nbsp;&nbsp; | ( ( ( ( p ) ) ( ( p ) ) ) ( ( ( p ) ) ( p ) ) ) = p p | &nbsp;&nbsp;&nbsp;&nbsp; (2,6 repbx)
 8 &nbsp;&nbsp;&nbsp; | ( ( p ) ) = p p | &nbsp;&nbsp;&nbsp;&nbsp; (1,7 repbx)
 9 &nbsp;&nbsp;&nbsp; | ( ( p ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (c1.2)
10 &nbsp;&nbsp;&nbsp; | p p = p | &nbsp;&nbsp;&nbsp;&nbsp; (8,9 eucr)

<br>
#### System<sub>3</sub>

Here we derive **C6** from the Robbins equation, demonstrating that a Robbins
algebra is a Boolean algebra. The more familiar form of the Robbins equation
is  _( ( p q ) ( p ( q ) ) ) = p_, but for this exercise I'll be using the
equivalent form:

**robbins** &nbsp;&nbsp; | ( ( ( p ) q ) ( p q ) ) = q

<br>
First we prove **J1**.

**j1.3** &nbsp;&nbsp; | ( ( p ) p ) =

<br>
Proof of **j1.3**

 1 &nbsp;&nbsp;&nbsp; | ( ( ( q ) p ) ( q p ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (robbins)
 2 &nbsp;&nbsp;&nbsp; | p = ( ( ( q ) p ) ( q p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (1 sym)
 3 &nbsp;&nbsp;&nbsp; | ( p ) = ( ( ( ( q ) p ) ( q p ) ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (2 ax-beq)
 4 &nbsp;&nbsp;&nbsp; | ( p ) p
    | = ( ( ( ( q ) p ) ( q p ) ) ) ( ( ( q ) p ) ( q p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (3,2 quad)
 5 &nbsp;&nbsp;&nbsp; | ( ( p ) p )
    | = ( ( ( ( ( q ) p ) ( q p ) ) ) ( ( ( q ) p ) ( q p ) ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (4 ax-beq)
 6 &nbsp;&nbsp;&nbsp; | ( ( ( ( ( q ) p ) ( q p ) ) ) ( ( ( q ) p ) ( q p ) ) ) =  | &nbsp;&nbsp;&nbsp;&nbsp; (robbins)
 7 &nbsp;&nbsp;&nbsp; | ( ( p ) p ) = | &nbsp;&nbsp;&nbsp;&nbsp; (5,6 trans)

<br>
Next we prove **C1**.

**c1.3** &nbsp;&nbsp; | ( ( p ) ) = p

<br>
Proof of **c1.3**

 1 &nbsp;&nbsp;&nbsp; | p ( ( p ) ) = ( ( p ) ) p | &nbsp;&nbsp;&nbsp;&nbsp; (ax-cmm)
 2 &nbsp;&nbsp;&nbsp; | ( p ( ( p ) ) ) = ( ( ( p ) ) p ) | &nbsp;&nbsp;&nbsp;&nbsp; (1 ax-beq)
 3 &nbsp;&nbsp;&nbsp; | ( ( p ( ( p ) ) ) ) = ( ( ( ( p ) ) p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (2 ax-beq)
 4 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ) ( p ) ) = | &nbsp;&nbsp;&nbsp;&nbsp; (robbins)
 5 &nbsp;&nbsp;&nbsp; | ( p ) ( ( p ) ) = ( ( p ) ) ( p ) | &nbsp;&nbsp;&nbsp;&nbsp; (ax-cmm)
 6 &nbsp;&nbsp;&nbsp; | ( ( p ) ( ( p ) ) ) = ( ( ( p ) ) ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (5 ax-beq)
 7 &nbsp;&nbsp;&nbsp; | ( ( ( p ) ( ( p ) ) ) ( p ( ( p ) ) ) ) = ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (robbins)
 8 &nbsp;&nbsp;&nbsp; | ( ( ( ( p ) ) ( p ) ) ( p ( ( p ) ) ) ) = ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (6,7 repbx)
 9 &nbsp;&nbsp;&nbsp; | ( ( p ( ( p ) ) ) ) = ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (4,8 repbx)
10 &nbsp;&nbsp;&nbsp; | ( ( ( ( p ) ) p ) ) = ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (3,9 rep)
11 &nbsp;&nbsp;&nbsp; | ( ( p ) p ) = | &nbsp;&nbsp;&nbsp;&nbsp; (j1.3)
12 &nbsp;&nbsp;&nbsp; | ( ( ( ( p ) ) p ) ( ( p ) p ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (robbins)
13 &nbsp;&nbsp;&nbsp; | ( ( ( ( p ) ) p ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (11,12 repbx)
14 &nbsp;&nbsp;&nbsp; | ( ( p ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (10,13 eucr)

<br>
We now prove **C6**, demonstrating that the Robbins algebra is at least as
powerful as Boolean algebra. The original proof was simplified according to
suggestions by Armahedi Mahzar.

**c6.3** &nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) = p

<br>
Proof of **c6.3**

 1 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( q ( p ) ) = ( ( p ) ( q ) ) ( ( p ) q ) | &nbsp;&nbsp;&nbsp;&nbsp; (cmmbx)
 2 &nbsp;&nbsp;&nbsp; | ( ( q ) ( p ) ) ( q ( p ) ) = ( ( p ) ( q ) ) ( q ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (cmmbx)
 3 &nbsp;&nbsp;&nbsp; | ( ( ( ( q ) ( p ) ) ( q ( p ) ) ) ) = ( ( q ) ( p ) ) ( q ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (c1.3)
 4 &nbsp;&nbsp;&nbsp; | ( ( ( q ) ( p ) ) ( q ( p ) ) ) = ( p ) | &nbsp;&nbsp;&nbsp;&nbsp; (robbins)
 5 &nbsp;&nbsp;&nbsp; | ( ( ( ( q ) ( p ) ) ( q ( p ) ) ) ) = ( ( p ) ) | &nbsp;&nbsp;&nbsp;&nbsp; (4 ax-beq)
 6 &nbsp;&nbsp;&nbsp; | ( ( p ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (c1.3)
 7 &nbsp;&nbsp;&nbsp; | ( ( ( ( q ) ( p ) ) ( q ( p ) ) ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (5,6 trans)
 8 &nbsp;&nbsp;&nbsp; | ( ( q ) ( p ) ) ( q ( p ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (3,7 eucr)
 9 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( q ( p ) ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (2,8 eucr)
10 &nbsp;&nbsp;&nbsp; | ( ( p ) ( q ) ) ( ( p ) q ) = p | &nbsp;&nbsp;&nbsp;&nbsp; (1,9 eucr)

-----------------------------------------------------------------------------------<br>

### 7. Topics in _Laws of Form_

#### Associativity of logical connectives

Although _LoF_ lacks the concept of associativity, proving that a model
of _LoF_ has associative connectives is straightforward. For
example, the proof of
<span style="white-space: nowrap;">(p &or; q) &or; r = p &or; (q &or; r)</span>
corresponds to proving the _LoF_ equation <span style="white-space: nowrap;">p q r = p q r</span> ,
which follows immediately from theorems **quad** or **ins**. Under the dual interpretation this also
proves the associativity of conjunction, but we can prove the latter more
directly. Since  <span style="white-space: nowrap;">p &and; q</span> corresponds to
<span style="white-space: nowrap;">( ( p ) ( q ) )</span>, we
need to show that
<span style="white-space: nowrap;">( ( ( ( p ) ( q ) ) ) ( r ) ) = ( ( p ) ( ( ( q ) ( r ) ) ) ).</span>
Consider the left side of that equation -- it evaluates to a form symmetric in the
three variables:

**conj3** &nbsp;&nbsp; | ( ( ( ( p ) ( q ) ) ) ( r ) ) = ( ( p ) ( q ) ( r ) )

<br>
[This and subsequent proofs will be omitted. See the source file or
utilize metamath's proof-display capabilities.]

This shows that a permutation of variables in the LHS leaves the result
unchanged. Specifically,
<span style="white-space: nowrap;">( ( ( ( q ) ( r ) ) ) ( p ) )</span>, which is equal to
<span style="white-space: nowrap;">( ( p ) ( ( ( q ) ( r ) ) ) )</span>
by commutation, will evaluate to the same form as
<span style="white-space: nowrap;">( ( ( ( p ) ( q ) ) ) ( r ) )</span>
This completes the proof. See the source for a full formal proof.

**conj-assc** &nbsp;&nbsp; | ( ( ( ( p ) ( q ) ) ) ( r ) ) = ( ( p ) ( ( ( q ) ( r ) ) ) )

<br>
Now I turn to proving the associativity of the biconditional,
<span style="white-space: nowrap;">(p &harr; q) &harr; r = p &harr; (q &harr; r)</span>.
I had earlier taken for granted that
<span style="white-space: nowrap;">p &harr; q</span>, transcribed as
<span style="white-space: nowrap;">( ( ( p ) q ) ( ( q ) p ) )</span>,
was equivalent to
<span style="white-space: nowrap;">( ( p ) ( q ) ) ( p q )</span>.
Here I prove it (see the source).

**bicond** &nbsp;&nbsp; | ( ( ( p ) q ) ( ( q ) p ) ) = ( ( p ) ( q ) ) ( p q )

<br>
Let <span style="white-space: nowrap;">A = p &harr; q = ( ( p ) ( q ) ) ( p q )</span>  
and <span style="white-space: nowrap;">B = q &harr; r = ( ( q ) ( r ) ) ( q r )</span>.  
Proving that the biconditional associates amounts to proving:  
<span style="white-space: nowrap;">( ( A ) ( r ) ) ( A r ) = ( ( p ) ( B ) ) ( p B )</span>,  
in other words,  
<span style="white-space: nowrap;">( ( ( ( p ) ( q ) ) ( p q ) ) ( r ) ) ( ( ( p ) ( q ) ) ( p q ) r ) =</span>  
<span style="white-space: nowrap;">( ( p ) ( ( ( q ) ( r ) ) ( q r ) ) ) ( p ( ( q ) ( r ) ) ( q r ) )</span>.  
Consider the left side of that equation -- as in the case of conjunction,
it evaluates to a form symmetric in the three variables:

**bic3** &nbsp;&nbsp; |( ( ( ( p ) ( q ) ) ( p q ) ) ( r ) ) ( ( ( p ) ( q ) ) ( p q ) r )
 | = ( ( p ) ( q ) ( r ) ) ( p q ( r ) ) ( p ( q ) r ) ( ( p ) q r )

<br>
This completes the informal proof that the biconditional associates. See
the source for the full proof.

**bicond-assc** &nbsp;&nbsp; |( ( ( ( p ) ( q ) ) ( p q ) ) ( r ) ) ( ( ( p ) ( q ) ) ( p q ) r )
 | = ( ( p ) ( ( ( q ) ( r ) ) ( q r ) ) ) ( p ( ( q ) ( r ) ) ( q r )

<br>
<br>
**_[Note: this post was updated in April 2021]_**

-----
<br>

[^1]: "...we consider Brown's algebraic axioms and show that they are
      synonymous with the axioms for Boolean algebra." Paul Cull &
      William Frank, "Flaws of Form", International Journal of General
      Systems, 5:4, 201--211 (1979).

[^2]: To be clear, this is not an alternative to the 1996 computer proof
      that Robbins algebras are Boolean (W. McCune, "Solution of the Robbins
      Problem", JAR 19(3), 263--276 (1997)). _LoF_ has a natural identity
      element, the _void_, and Steven Winkler showed in the early 1990s that
      the existence of such an element sufficed to turn a Robbins algebra into
      a Boolean algebra (S. Winker, "Robbins Algebra: Conditions That Make a
      Near-Boolean Algebra Boolean", J. Automated Reasoning 6(4), 465--489
      (1990) and "Absorption and idempotency criteria for a problem in
      near-Boolean algebras", J. Algebra 153(2), 414--423 (1992)). See
      http://homepages.math.uic.edu/~kauffman/Robbins.htm for a _LoF_-inspired
      derivation by Louis Kauffman that does _not_ take the void as given.

[^3]: P. Meguire, "Boundary Algebra: A Simple Notation for Boolean
      Algebra and the Truth Functors" (2007),
      http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.143.8171 .

[lofmm]: https://github.com/naipmoro/lofmm/blob/master/lof.mm
[mm]: http://metamath.org

