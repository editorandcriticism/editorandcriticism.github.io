---
author: Steve Hoenisch
description: 'Examples and analysis of linguistic ambiguity in newspaper headlines.'
title: Identifying and Resolving Ambiguity
---



1 Examples of Ambiguity
===========================



Listed below are some headlines that exhibit at least one of three kinds
of ambiguity -- lexical (part-of-speech), syntactic (structural), and
semantic. In some of these examples -- all from actual newspaper
headlines -- the unintended meaning is so strong that, on first reading,
it overshadows the intended one.





drunk gets nine months in violin case





Iraqi head seeks arms





prostitutes appeal to pope





teacher strikes idle kids





squad helps dog bite victim





enraged cow injures farmer with ax





miners refuse to work after death





juvenile court to try shooting defendant





stolen painting found by tree





two Soviet ships collide, one dies





two sisters reunited after 18 years in checkout counter











2 Analysis of Ambiguity
===========================



2.1 Semantic Ambiguity
--------------------------



**Headline:**
``` {.program}
Iraqi head seeks arms
```





**Ambiguity type:** Semantic.





**Identification and explanation:** The homograph "head" can be
interpreted as a noun meaning either chief or the anatomical head of a
body. Likewise, the homograph "arms" can be interpreted as a plural noun
meaning either weapons or body parts.





**What makes headline humorous:** The headline can easily be read as a
disembodied head searching for arms (body parts) or wanting to have them
attached.





**Computational Resolution:** The ambiguity could be resolved for a
computer parser by specifying in the lexical entry for each item its
semantic features.







2.2 Lexical Ambiguity
-------------------------



**Headline:**
``` {.program}
Teacher strikes idle kids
```





**Ambiguity type:** Lexical (part of speech or category ambiguity).





**Identification and explanation:** "strikes" can occur as either an
verb meaning to hit or a noun meaning a refusal to work. Meantime,
"idle" can occur as either an verb or an adjective.





**What makes headline humorous:** The headline can easily be read as
"teacher hits idle kids' even though it was meant to mean that the
walkout of teachers has left pupils idle.







2.3 Structural Ambiguity
----------------------------



**Headline:**
``` {.program}
Stolen painting found by tree
```





**Ambiguity type:** Structural.





**Identification and explanation:** The headline's two alternative
syntactic representations make it structurally ambivalent:





\(1) A tree found a stolen painting.





\(2) A person found a stolen painting near a tree.





**What makes headline humorous:** The headline can easily be read as the
representation in (1): A tree found a painting, which is humorous
because trees, being inanimate, generally don't find things.





**Computational Resolution:** Specifying in the computational lexicon
that the verb "find" usually takes an agent with the property
\[+animate\].








3 Related
=============



<i class="fa fa-file-text"></i> [Abstract: Abney's Memory Requirements and
Lexical Ambiguities of Parsing Strategies](abstract-abney.html)





<i class="fa fa-file-text"></i> [Abstract: Marcus's Computational Account of
Some Constraints on Language](abstract-marcus.html)





<i class="fa fa-file-text"></i> [Abstract: Earley's Efficient Context-Free
Parsing Algorithm](abstract-earley.html)










