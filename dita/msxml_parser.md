---
title: Internet Explorer 5 and the MSXML Parser
---


By Steve Hoenisch


Last updated on May 25, 2002.


_Note: The information in this article is likely out of date._ 

Because the example stylesheets in my [XML tutorials](xml_intro.html) conform to the W3C's XSL Recommendation while the MSXML parser with which Internet Explorer 5 is natively equipped does not, you must have installed at least version 3 of the MSXML parser and be running it in replace mode for the code to work. 

Running the parser in replace mode requires manual intervention, so if you don't remember installing and activating it, you're most likely running the old version of the parser, which does not conform to the XSL specification and takes a different XSL namespace. 

You can obtain the latest version of the MSXML parser, which more closely conforms to the XSL specification and uses the correct namespace, from the XML section of the Microsoft Developer's Network (MSDN) at www.Microsoft.com and install it in replace mode in a few minutes.

The W3C's XSL Recommendation uses the following namespace:

`<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`

In contrast, Internet Explorer 5's native XSL processor uses the following namespace, which does not conform to the XSL Recommendation:

`<xsl:stylesheet xmlns:xsl="http://www.w3.org/TR/WD-xsl">`


Michael Kay's XSLT Programmer's Reference, published by Wrox, covers XSLT in full and provides an excellent rundown of how to use XML and XSLT with Internet Explorer as well as an insightful discussion of the different versions of the MSXML parser and the two different namespaces needed for them.



### XSL Resources	

W3C's XSL Recommendation

Microsoft Developer's Network (MSDN)

Wrox books


### Tutorials and Articles on XML

<i class="fa fa-file-text-o" aria-hidden="true"></i> [An Introduction to XML](xml_intro.html)

<i class="fa fa-file-text-o" aria-hidden="true"></i> [Structuring XML Documents](/dita/structuring_docs.html)

<i class="fa fa-file-text-o" aria-hidden="true"></i> [Developing a DTD](/dita/dtd1.html)

<i class="fa fa-file-text-o" aria-hidden="true"></i> [Attributes and Entities in DTDs](/dita/dtd2.html)

<i class="fa fa-file-text-o" aria-hidden="true"></i> [Introduction to XSL: Using Stylesheets to Separate Content from Presentation](/dita/xsl1.html)

<i class="fa fa-file-text-o" aria-hidden="true"></i> [XSLT: Elegance and Power](/dita/xsl2.html)

<i class="fa fa-file-o" aria-hidden="true"></i> [Switching Document Views with XML and Script](/dita/xsl-switch.html)

<i class="fa fa-file-text-o" aria-hidden="true"></i> [XML: A Metalanguage for Describing and Structuring
    Data](/dita/xml-definition.html)

<i class="fa fa-file-o" aria-hidden="true"></i> [Using Data Structure Standards to Foster Efficiency and
    Opportunity](/dita/dss.html)

<i class="fa fa-file-text-o" aria-hidden="true"></i> [Principles of Separating Content from Presentation](/dita/principles-of-separation.html)

<i class="fa fa-file-o" aria-hidden="true"></i> [Hierarchical Trees in XML](/dita/xml-hierarchical-trees.html)

<i class="fa fa-file-text-o" aria-hidden="true"></i> [Using XSL and CSS to Format XML Documents](/dita/xsl-and-css.html)

<i class="fa fa-file-o" aria-hidden="true"></i> [DITA and DocBook: An Overview and
    Demonstration](/dita/dita_docbook.html)

<i class="fa fa-file-text-o" aria-hidden="true"></i> [XML Markup Strategies: Approaches for Structuring
    Documents](/dita/markup_strategies.html)

<i class="fa fa-file-text-o" aria-hidden="true"></i> [DocBook SEO: Tagging DocBook XML Documents for Search Engine
    Optimization](/seo/docbook.html)

<i class="fa fa-file-text-o" aria-hidden="true"></i> [XC: A Minimalist, Structural DTD for XML Points Towards Markdown Documents](/cc/about-xc.html)


<i class="fa fa-file-text-o" aria-hidden="true"></i> [Review: Using XML to Separate Content from Prensentation](/dita/xsl2_code/simple_doc.html) | [PDF](https://criticism.com/dita/xsl2_code/simple_doc.pdf) <i class="fa fa-moon-o" aria-hidden="true"></i>








