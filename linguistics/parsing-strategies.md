---
description: |
    Parsing strategies in computational linguistics: An outline of Abney and
    Johnson 1991.
keywords: |
    Computational linguistics, linguistics, Abney, parsing strategies,
    parsers, natural language processing, local ambiguity, language
    processing
title: 'Parsing Strategies: Notes on Abney and Johnson'
---



Some Types of Parsing Strategies
===============================================================================



**Note:** The notes on this page are adopted from Abney and Johnson
1991.


**Definition:** A parsing strategy is a method of enumerating the arcs
and nodes of parse [trees](hierarchical-trees.xml).



**Top-down:** Each node is enumerated before any of its descendants.



**Bottom-up:** Each node is enumerated after all its descendants.



**Left-corner:** A node is built immediately after its first child and
that child\'s descendants, but before the remaining children or any of
their descendants.



**Arc-eager:** An arc is enumerated at the earliest point that the two
nodes it connects have been enumerated.



**Arc-standard:** An arc is enumerated at the earliest point such that
(i) both nodes it connects have been enumerated and (ii) either none or
all of the subtree under the child node has been enumerated.


Assumptions about the Parser
=======================================================================


An arc-eager strategy may require less but never more memory than a
corresponding arc-standard strategy. It is thus assumed that the parser
uses arc-eager enumeration, even though an arc-eager strategy may result
in an increase in local ambiguity.



The parser produces only binary branching trees.



The parser has a one word look-ahead.



Each unit of memory is enough space for one node of a parse tree.


The Right-Hand Branching Grammar
===============================================================================


Inspired by the German word-order in such sentences as die Frau kann das
Buch lesen, which translates literally as the woman can the book read,
the phrase-structure grammar is as follows:



``` {.program}

S  > NP IP
NP > Det N
IP > I VP
VP > NP V
```



The final phrase-structure rule shows that, in contrast to typical
declarative English sentences, a verb can be proceeded by its object.



Methodology: Memory Requirements
===============================================================================


The memory usage of a parse tree is the maximum number of incomplete
nodes at any point in the parse.



Recall the assumption that each unit of memory is enough space for one
node of a parse tree. Thus, each incomplete node takes up one unit of
memory.



A node is incomplete if it has been built but either its parent or one
of its children has not been built.



Furthermore, any node is incomplete if its children or parent has been
built but an arc connecting any one of them has not.



Methodology: Local Ambiguity
=======================================================================


Local ambiguities arise when the input to the parser can result in more
than one possible tree.



In particular, such ambiguities occur when the parser is unsure which
set of arcs and nodes to build at a given point in the input string.



The parse increment: Local ambiguities can be determined by examining
what is called the parse increments in the construction of a tree.



More specifically, the ith parse increment comprises those nodes and
arcs enumerated between the terminal nodes for the first word that the
parser sees and the next word of input.



Thus, local ambiguities can occur between those points in the input that
have been read so far and the next word of look-ahead.



The first parse increment, for example, is the set of nodes and arcs
enumerated before the first word (recall that the parser has a one-word
look-ahead).


Related Pages
=========================================


<i class="fa fa-file-text" aria-hidden="true"></i> [Abstract: Abney\'s Memory Requirements and
Lexical Ambiguities of Parsing Strategies](abstract-abney.html)



<i class="fa fa-file-text" aria-hidden="true"></i> [Abstract: Marcus\'s Computational Account of
Some Constraints on Language](abstract-marcus.html)




