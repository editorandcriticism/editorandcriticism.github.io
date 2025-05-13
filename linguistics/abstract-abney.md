---
description: |
    Abney, S. and Johnson, M. 1991. Memory Requirements and Lexical
    Ambiguities of Parsing Strategies, Journal of Psycholinguistics Research
    20:233-250.
title: Memory Requirements and Lexical Ambiguities of Parsing Strategies
---


#### Abstract


1 Citation
==============





**From:** Abney, S. and Johnson, M. 1991. Memory Requirements and
Lexical Ambiguities of Parsing Strategies, Journal of Psycholinguistics
Research 20:233-250.




2 Optimal Parsing Strategies
================================



Abney and Johnson, maintaining that two properties of parsing strategies
-- space requirements and local ambiguities -- have been subject to
imprecise examination and unrealistic assumptions, investigate the range
of possible parsers, their memory requirements, and the number of local
ambiguities they face. Abney and Johnson lay the foundation for
determining and executing the parsing strategy that, given a grammar,
optimizes the combination of memory requirements and local ambiguities.
In doing so, they provide a method for measuring the local ambiguities
and space requirements of a selected parsing strategy for a particular
grammar. (For Abney and Johnson, a parsing strategy "is a way of
enumerating the nodes and arcs of parse trees" (236).)





Because of the controversy over center-embedded constructions, Abney and
Johnson's method for measuring space requirements is of particular
importance. The method rests on assigning one unit to each node to which
the parser may need to refer, including nodes left incomplete because
their parent or child has yet to be constructed. Given a grammar, a
parsing strategy's required space is the maximum necessitated by an
enumeration that the strategy designates for a parse tree of the
grammar. The measurement's application shows that in languages like
English which branch heavily to the right, a top-down strategy makes
more efficient use of memory than a bottom-up strategy -- because a
top-down strategy keeps the number of incomplete nodes lower.
Conversely, in left-branching structures, a bottom-up parser more
efficiently utilizes space. Meantime, the parsing strategy for center
embedding should require maximal memory requirements if the inability to
parse center-embedded constructions is to be attributed to memory
limitations. However, Abney and Johnson show, neither top-down nor
bottom-up strategies reach their maximum space requirements when applied
to center-embedded structures, a finding that Abney and Johnson make
convincing by providing and comparing clear, concrete enumerations of
the memory requirements for left-branching, right-branching, and
center-embedded structures.





Regarding local ambiguities, Abney and Johnson use calculations to show
that a "less eager" strategy -- that is, one that constructs nonterminal
nodes earlier in the input string -- may reduce the local ambiguities
encountered by the parser. Bottom-up strategies are less eager than
top-down strategies, revealing an efficiency trade off for
right-branching languages like English between reducing local
ambiguities and minimizing memory requirements. Accordingly, Abney and
Johnson maintain that the optimal parsing strategy for English is
probably neither top-down nor bottom-up.





Considered a classic essay in the computational linguistic literature as
well as an important psycholinguistic contribution, the essay is well
organized and highly readable, making it accessible to readers not
initiated into the technical background of computational linguistics.
Abney and Johnson take particular care to define their terms and provide
concrete examples backing up their major points.





3 Related
=============



<i class="fa fa-file-text"></i> **[Abstract: Marcus's Computational Account of
Some Constraints on Language](abstract-marcus.html)**





<i class="fa fa-file-text"></i> **[Abstract: Earley's Efficient Context-Free
Parsing Algorithm](abstract-earley.html)**



