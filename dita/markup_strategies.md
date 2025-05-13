---
description: 'Strategies for Marking Up XML Documents.'
keywords: |
    XML, DTD, XML Schema, markup, markup strategies, XML documents, XML
    structuring, structuring XML documents, XSLT, XHTML, HTML5
title: XML Markup Strategies
author: Steve Hoenisch
---



### Approaches for Structuring Documents 




Choosing an approach to markup is another decision you should make
before you begin structuring your XML documents. There are three
principal markup strategies:

-   Presentation-based tagging
-   Structure- or publication-oriented tagging
-   Content or information-based tagging, which is also known as semantic markup



The three approaches form a dichotomy, with structure-oriented tagging
hugging the middle ground, as illustrated by these examples:



``` {.program}
Presentation
<ital>damn</ital>

Structure
<emphasis>damn</emphasis>

Content
<expletive>damn</expletive>
```



The markup strategy behind HTML is based largely presentational: Tags
like \<h1\>, \<i\>, and \<b\> indicate how content should be presented
through a browser. The motivation behind using XML, however, is that it
allows you to separate content from presentation and to structure data
based on meaning, resulting in data and documents that are easier to
reuse, manipulate, and search. Exclusively using a presentation-oriented
approach to tagging defies the purpose of XML. Better is to use either a
structure- or content-based approach.



Structure-based tagging is a generic, flexible approach with a wide
scope, most useful when exchanging documents within a discipline or
across industries. Employing a loosely structured DTD or schema, it emphasizes
elements like \<section\>, \<subsection\>, and \<paragraph\>. Additional
information about content is often delegated to attributes: \<section
type=\"Introduction\"\>.



Content-based tagging is a custom, less flexible approach with a narrow
scope, most useful when modeling content around clearly defined user
needs or a unique class of documents or both. Using a tightly structured
DTD, it emphasizes the use of elements like \<introduction\> and
\<explanation\>.



In reality, however, most documents intended for publication on the
Internet or an intranet combine all three approaches: The higher levels
of the hierarchy use content-based tags, the middle levels use
structure-oriented tags, and the lower levels, especially at the clausal
level, may, for expedience, use some presentational tags from XHTML.
Since the focus of this column is primarily on creating XML documents
for publication on the Internet, we will use a combination of all three
approaches and learn a bit about XHTML as we do so. But as you mark up
documents in XML, you will have to evaluate the structure of your
documents and the uses to which they will be put before you decide on
your own approach. Just be sure you do some planning and design before
beginning the markup process. David Megginson\'s book,
_Structuring
XML
Documents_,
published by Prentice Hall, offers a plethora of information and good
advice about choosing an approach to tagging that will work best for
your document or project.

I do, however, suggest not getting bogged down in using too much semantic markup---it's a bit of slippery requirements trap. The more semantic markup that you use, the more you think you require, and the actual return on investment is minimal at best, negative at worst. Less is more. Less is more. <i class="fa fa-fast-forward" aria-hidden="true"></i>




#### Related Pages




The tutorials in this series proceed as follows:


1.  [An Introduction to XML](xml_intro.html)
2.  [Structuring Documents in XML](structuring_docs.html)
3.  [Developing a Document Type Definition](dtd1.html)
4.  [Attributes and Entities in DTDs](dtd2.html)
5.  [An Introduction to XSL](xsl1.html)
6.  [Using XSLT to Separate Content from Presentation](xsl2.html)


