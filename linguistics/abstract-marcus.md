---
description: |
    Marcus, M. 1986. A Computational Account of Some Constraints on
    Language. In Readings in Natural Language Processing, Grosz, Jones and
    Webber, eds. 1986. Los Altos, Calif.: Morgan Kaufmann.
title: 'Marcus\''s Computational Account of Some Constraints on Language'
---


Abstract last updated on August 11, 2004\


1 Citation
===============================



**From:** Marcus, M. 1986. A Computational Account of Some Constraints
on Language. In Readings in Natural Language Processing, Grosz, Jones
and Webber, eds. 1986. Los Altos, Calif.: Morgan Kaufmann.


2 Determinism Hypothesis
==================================================


The purpose of Marcus\'s paper is to present arguments showing that the
constraints imposed by the structure of the grammar interpreter called
PARSIFAL are such that grammar rules cannot parse sentences violating
either the Specified Subject Constraint or the Subjacency Principle, a
result that stems from a component of the grammar interpreter motivated
by what Marcus calls the Determinism Hypothesis. This hypothesis
\"claims that natural language can be parsed by a computationally simply
mechanism that uses neither backtracking nor pseudo-parallelism, and in
which all grammatical structure created by the parser is \`indelible\'
in that it must all be output as part of the structural analysis of the
parser\'s input\" (89). The structure of PARSIFAL, Marcus says, is based
upon the hypothesis that a parser for natural language does not need to
simulate a nondeterministic machine.



PARSIFAL uses two major data structures, one of which is \"a pushdown
stack of incomplete constituents called *the active node stack*\" (90;
emphasis in original). The other structure, which distinguishes the
parser from others, is \"a small three-place *constituent buffer* which
contains constituents which are complete, but whose higher level
grammatical function is as yet uncertain\" (90; emphasis in original).
The structure and operation of the parser is motivated by several
properties that Marcus maintains a nondeterministic parser should
include and which PARSIFAL embodies: the parser should be partially
data-driven, able to \"reflect expectations that follow from the partial
structures built up during the parsing process\" (91), and have a
constrained look-ahead capacity.



After outlining the grammar interpreter, Marcus, working within the
Chomskian framework that postulates traces, demonstrates how the SSC and
the Subjacency Principle \"fall out\" from the formulation of PASSIVE.
Marcus shows that in the context of a grammar for the parser, a solution
emerges for constructions of passivization and, without adding
complexity to the grammar, raising. Marcus demonstrates these claims by
successfully applying the parser to examples of passivization and
raising. In doing so, he develops a computational account of NP-movement
(but not WH-movement) in accordance with the SSC and Subjacency
Principle.



However, as Marcus himself acknowledges, he does not present strong,
complete evidence for the Determinism Hypothesis. He concludes only that
the NP-movement subcases of the constraints follow from the grammar
interpreter, a result that provides some evidence for the Determinism
Hypothesis but does not confirm it outright. Accordingly, the paper
provides clear evidence for the parser\'s power in handling NP-movement
in accordance with Chomsky\'s constraints but leaves undetermined
whether the parser can also handle cases of, for instance, WH-movement.
The result is a strong contribution to the development of computational
models based on the generative grammar of Chomsky.




3 Related
=============================


* [Abstract: Abney\'s Memory Requirements and
Lexical Ambiguities of Parsing Strategies](abstract-abney.html)

* [Abstract: Earley\'s Efficient Context-Free
Parsing Algorithm](abstract-earley.html)


