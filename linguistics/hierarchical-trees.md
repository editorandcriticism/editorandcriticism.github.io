---
description: 'Examples and analysis of linguistic ambiguity in newspaper headlines.'
title: 'Hierarchical Trees: Relations of Dominance and Dependence'
---


## Trees Can Express Recurrent Feature Groupings 



In generative phonology, the hierarchical feature tree provides a
natural formalism to express recurrent feature groupings. Mentioning a
particular node implies all the information dominated by that node. An
essential property of the feature tree and the segments it generates is
this relation of dominance or dependence, or both.



This relation provides a simple formalism to explain several additional
phonological processes. Here\'s why: As (2) illustrates, two or more
features can be expected to co-occur in rules or constraints only if
they share a common node in the tree. In other words, defining
phonological rules over nodes in the tree graph makes certain feature
groupings simple to express and others more complex. In (2), for
instance, {a} and {b} can be simply isolated by mentioning {f}; on the
other hand, {b} and {c} can be grouped only by also including {a}, {d}
and {e}, which would be an instance of complete assimilation.



By establishing relations of dominance and dependence, the feature tree
depicted in (1) explains why \[high\], \[low\] and \[back\] group
together \-- because they are all daughters of the dorsal node. On the
other hand, \[high\] and \[nasal\] should not join up in a rule or
constraint because there is no single node that dominates only these
features.



Hierarchical trees are also frequently used to express relationships in
syntax. The following example, marked up in [XML](/dita/), reveals the
hierarchical structure of the atomic syntactic elements that make up a
sample sentence:



``` {.program}
<s>
  <np><det>The</det><n>woman</n></np>   
  <vp><v>saw</v> 
    <np><det>the</det><n>man</n>
      <pp><p>in</p>
        <np><det>the</det><n>park</n></np>
      </pp>
    </np>
  </vp>
</s>
```



As a hierarchical tree, the sentence looks like this:



![](/images/tree_representation.gif)





### Related


* [Abstract: Abney\'s Memory Requirements and Lexical Ambiguities of Parsing Strategies](abstract-abney.html) 




