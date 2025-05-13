---
description: 'Some basics of government and binding theory in syntax.'
keywords: |
    linguistics, syntax, government and binding theory, generative
    linguistics
title: Some Basic Concepts in Government and Binding Theory
---

1 Sisterhood
===================================


Here are some syntax review notes from Haegeman, Chapter 2:



``` {.program}
     VP
   /  \
 /      \
V         NP
```



V and NP are in a relationship of *sisterhood*. They are daughters of
the same [parent](hierarchical-trees.html) or mother, VP.





2 Government (1)
===========================================


``` {.program}
A governs B if
(i) A is a governor;
(ii) A and B are sisters.
Governors are heads.
```



When a V governs an element \[its complement or object\] and assigns an
internal theta role to it, we say that it *theta-governs* this element.
Also: If X is a head and it governs Y then X *head-governs* Y.



Recall that a verb *governs* an object, and the head of a phrase governs
the complement.


3 Dominance
=================================


Node A dominates node B if and only if A is higher up in the tree than B
and if you can trace a line from A to B going downwards.


4 Immediate Dominance
=========================================


A node dominates another with no intervening node between them.

5 Precedence
===================================


Node A precedes node B if and only if A is to the left of B and neither
A dominates B nor B dominates A.




6 Immediate Precedence
======================================


If a node A precedes a node B and there is no intervening node, then A
immediately precedes B.

7 C-Command (1)
=========================================


Node A c-commands node B if and only if



\(i) A does not dominate B and B does not dominate A; and



\(ii) the first branching node dominating A also dominates B.



8 Government (2)
===========================================


A governs B if and only if



\(i) A is a governor; and



\(ii) A c-commands B and B c-commands A.



9 C-Command (2)
=========================================


A c-commands B if and only if A does not dominate B and every X that
dominates A also dominates B.



For the choice of X in C-command (2), two options are considered. When X
is equated with the first branching node we obtain the c-command
definition given in C-command (1). This structural relation is sometimes
referred to as strict c-command. Alternatively, X is interpreted as a
*maximal projection*. Under the latter interpretation of (2), A
*m-commands* B.




10 Government (3)
============================================


A governs B if and only if



\(i) A is a governor; and



\(ii) A m-commands B; and



\(iii) no barrier intervenes between A and B.



Maximal projections are barriers to government.



Governors are heads.


11 X-Bar Phrase Structure
===========================================


The following rules express the general format for phrase structure:



``` {.program}
XP  -->  Spec; X'
X'* -->  X'; YP
X'  -->  X; YP.
```


12 Assimilation of S\'
===========================================


The structure of S\' can be assimilated to the X\'-format as follows:



``` {.program}
CP  -->   Spec; C'
C'  -->   C; IP
```


13 A-positions
======================================


A-positions are potential theta positions, positions to which a theta
role can be assigned, i.e. positions such as \[Spec, IP\] \-- that is,
the subject position \-- and the NP dominated by V\'; \[NP, V\'\] \--
that is, the verb\'s complement or object. A-positions are not
necessarily assigned a theta role: The subject position may be occupied
by an expletive element. Still it counts as an A-position. In
traditional terms, we might say that A-positions correspond to positions
associated with grammatical functions.



14 A\'-positions
=========================================


A\'-positions are often defined negatively: They are positions that are
not A-positions. \[Spec, CP\] \-- that is, the complementizer \-- and
adjuncts are standardly considered A\'-positions.



Recall that English\'s four complementizers are *that*, *if*, *whether*,
*for*.


