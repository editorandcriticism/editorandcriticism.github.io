---
description: |
    Abney, S. and Johnson, M. 1991. Memory Requirements and Lexical
    Ambiguities of Parsing Strategies, Journal of Psycholinguistics Research
    20:233-250.
title: Abstract of 'Earley\''s Efficient Context-Free Parsing Algorithm'
---


Last updated on Oct. 31, 2012\


Citation
===============================

**From:** Earley, Jay. 1970. An Efficient Context-Free Parsing Algorithm. Reprinted in Readings in Natural Language Processing, Grosz, Jones and Webber, eds. 1986. Los Altos, Calif.: Morgan Kaufmann. 


Top-Down and Bottom-Up Algorithms
=================================================================================

Earley aims to describe what he argues to be the most efficient possible context-free parsing algorithm and to provide empirical evidence for his argument by comparing his top-down algorithm to other familiar parsing algorithms, including those of both the top-down and bottom-up variety. Constructed as a recognizer \-that is, as an algorithm that scans input in the form of a string and either allows or rejects it based on whether the string is a sentence of the grammar \-his algorithm scans a string of input from left to right while looking ahead a fixed number of symbols. At each symbol, the recognizer constructs a set of states that characterize the condition of the recognition process at that point in the scan. The look-ahead feature of Earley\'s algorithm is argued to be especially useful in the parsing of bounded-state LR*(k)* grammars. 

Earley maintains that his algorithm has several strengths over its competitors and demonstrates those strengths by comparing his alorithm to others. The strengths of his algorithm, which uses, a random access model, include an upper bound on time proportional to *n*^3^, with *n* standing for the length of string being parsed. Earley shows that his algorithm can parse at *n*^2^ given unambiguous input. As an example, Earley briefly compares the efficiency of his algorithm to the results that Younger obtained using Cocke\'s algorithm. Earley maintains his is better for two reasons: First, it does not require a special form for the grammar, whereas Cocke\'s required normal form; second, Earley shows his algorithm often performs better than *n*^2^, whereas Cocke\'s requires *n*^2^. 

Earley also compares his algorithm with the backtracking-dependent bottom-up and top-down context-free parsers that have been examined by Griffiths and Petrick, arguing that his is superior because theirs have exponential upper bounds for time. Earley compares the algorithms on seven different grammars and demonstrates that while his algorithm performs similar to the others on simple grammars, it is substantially faster, and thus superior, on very ambiguous grammars. 

Although much of Earley\'s discussion addresses the technicalities of his recognizer and how it compares with other algorithms, he also discusses the practical applications of his algorithm after it is made into a parser. 

Part of Earley\'s discussion assumes a knowledge of basic list processing techniques, making some aspects of his presentation difficult to access for a linguist without a computer science background. 

Related
=============================

<i class="fa fa-file-text" aria-hidden="true"></i> [Abstract: Abney\'s Memory Requirements and
Lexical Ambiguities of Parsing Strategies](abstract-abney.html)


<i class="fa fa-file-text" aria-hidden="true"></i> [Abstract: Marcus\'s Computational Account of
Some Constraints on Language](abstract-marcus.html)




