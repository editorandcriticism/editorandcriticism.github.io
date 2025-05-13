---
author: Steve Hoenisch
description: 'A definition of XML as a metalanguage for describing and structuring data.'
keywords: | 
    XML, XSL, XSLT, CSS, markup, markup strategies, XML documents, XML structuring, structuring XML documents, XHTML, content, presentation, DTD, formatting XML, XSL:FO, formatting objects. metalanguage 
title: |
	What Is XML? A Metalanguage for Describing and Structuring Data
---

All this talk about XML raises the question: What is it anyway? And what about the jumble of abbreviations that cloaks XML from the curious eyes of an HTML coder or content author? How do XSLT, DTD, XLink and all the rest fit into the XML equation?

Extensible Markup Language is, first and foremost, a metalanguage for describing and structuring data with tags. "Metalanguage" means a language for how to describe other languages. Like HTML, XML uses tags (words bracketed by "<" and ">"), but unlike HTML, XML has neither a predefined set of tags nor rules for how to use them (though XML does have generic rules governing markup; for instance, tags may not overlap). 

In XML, tags and the rules for them, or grammar, are defined by the users themselves. XML programmers use tags and their corresponding grammar to describe and structure data in a simple text format like that of HTML (as opposed to a binary format). Because users can define their own tags, XML, as its full name implies, is also extensible, meaning that, unlike HTML, it is capable of being extended. You will begin learning how to create your own XML tags today, in the tutorial section below.

### A Family of Technologies

The hodgepodge of abbreviations and acronyms surrounding XML points up another of its characteristics: It is a family of technologies designed to be used over the Internet. Some of XML's family members and their main functions are as follows:

* Extensible Stylesheet Language (XSL), which in turn comprises Extensible Stylesheet Language Transformations (XSLT) and Extensible Stylesheet Language Formatting Objects (XSL-FO). XSL is an XML-based language for expressing stylesheets. XSLT is a language for transforming XML documents into (typically) other XML documents, HTML, and WML. XSL-FO is used to format XML documents for printing. My third column will present a tutorial on XSLT. Later columns will delve into XSL-FO and expand on XSLT.

* Document Type Definition (DTD). Stemming from Standard Generalized Markup Language, the progenitor of both HTML and XML, a DTD defines the rules that constrain an XML document or a set of XML documents. In my third column, I'll teach you how to construct a DTD.

* XML Schema, for which we've thankfully been spared yet another abbreviation to remember, may eventually supplant DTDs as the primary mechanism for constraining XML data. An XML Schema, which is itself in the format of an XML document, serves the same function as a DTD while correcting some of its limitations. This column will cover XML Schema at a later time.

* XLink, XPath, and XPointer together provide the foundation for creating links and asserting relationships within and among XML documents. XLink describes how to create hyperlinks among XML documents and provides mechanisms for advanced capabilities like multidirectional linking. XPath, widely used by XSLT, allows users to locate specific nodes or node sets within XML documents (you'll learn about nodes next month). XPointer specifies how to describe and point to locations of various kinds within an XML document. My fifth column will address linking in XML. Meantime, for a quick description of it, check out XML Linking: An Introduction at http://www.stg.brown.edu/~sjd/xlinkintro.html.

* Namespaces is a specification that describes how to associate a URL with all the tags in an XML document to ensure that they are unique, thereby eliminating ambiguity when the same tag is used by different XML coders. I'll introduce you to Namespaces after we move through some of the more fundamental aspects of XML.

* The Document Object Model (DOM) and the Simple API for XML (SAX). The Document Object Model, itself an Application Programming Interface, or API, is used to represent the structure and content of XML (and other) documents and provides an interface that allows programs and scripts to manipulate them. SAX, like DOM, also allows applications to get information from an XML document and do something with it. This column will provide an introductory tutorial on DOM and SAX toward the end of the year.

These are just some of the XML-related technologies relevant to a broadly focused XML tutorial. As you may have guessed, there is a plethora of other XML-related specifications and applications, most of which are still evolving: XML Query, XML Base, XML Signature and Canonicalization, XML Protocol, MathML, SMIL, SVG, and FpML, to name a few. You can visit the World Wide Web Consortium's (W3C) web site, http://www.w3c.org, for the rundown on most of these initiatives.

To get a more complete description of what XML is and what its core related technologies are, read two short pieces: an article on the W3C web site called "XML in 10 Points," at http://www.w3.org/XML/1999/XML-in-10-points, and the first half of Chapter 1 in Brett McLaughlin's book, Java and XML, published by O'Reilly.
For a slighly more technical introduction to XML, visit http://www.xml.com/pub/a/98/10/guide0.html.


### Related

The tutorials in this series proceed as follows:

1.  [An Introduction to XML](xml_intro.html)
2.  [Structuring Documents in XML](structuring_docs.html)
3.  [Developing a Document Type Definition](dtd1.html)
4.  [Attributes and Entities in DTDs](dtd2.html)
5.  [An Introduction to XSL](xsl1.html)
6.  [Using XSLT to Separate Content from Presentation](xsl2.html)




