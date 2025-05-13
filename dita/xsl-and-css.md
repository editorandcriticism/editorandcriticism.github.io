---
description: 'How to use XSL and CSS to format and style XML documents.'
keywords: |
    XML, XSLT, CSS, markup, markup strategies, XML documents, XML
    structuring, structuring XML documents, XSLT, XHTML, content,
    presentation, DTD, styling, formatting, XSL:FO, formatting objects
title: Using XSL and CSS to Format XML Documents
author: Steve Hoenisch
---


The birth of XSLT breaks down like this: Extensible Stylesheet Language
(XSL) was conceived as an XML application for expressing stylesheets
capable of manipulating XML documents. After its submission to the W3C
in 1997, XSL split into two stylesheet standards: Extensible Stylesheet
Language for Transformations (XSLT) and Extensible Stylesheet Language
Formatting Objects (XSL-FO). XSLT is a language for transforming XML
documents into typically other XML documents, HTML, and WML, but can
also be used to produce documents in plain text and XSL-FO. XSL-FO is
used to describe the layout of XML documents for printing, with the end
product usually being in Portable Document Format (PDF). XSL-FO, a
complex standard that some refer to as simply XSL, may eventually also
be employed to lay out web pages, though this use is unsupported by
current versions of web browsers. You can find more information about
XSLT and XSL-FO, including their specifications, on the World Wide Web
Consortium\'s web site, www.w3c.org. This column focuses on XSLT; later
tutorials will expand on XSLT and delve into
XSL-FO.


The early XSL proposals also gave rise to another breakaway standard,
XPath. It grew out of the location-finding aspects of the XSL and
XPointer specifications, which had been independently using similar
mechanisms to find information in XML documents. XSLT heavily uses XPath
to locate specific nodes or node sets within XML documents. Details
about XPath specification can be found at
http://www.w3c.org.



XSL has another related standard, though unlike XSL it is not based in
XML: Cascading Style Sheets (CSS). In the context of web publishing,
Cascading Style Sheets (CSS) can also be used, at least theoretically,
to statically format XML documents for display, but it cannot be used to
transform them in any meaningful way. For example, XMetal, a tool for
writing and editing in XML, uses CSS to format XML documents for display
in its normal view. But until there is much stronger web browser support
for displaying XML documents with CSS, it is not a practical option for
web publishing.

CSS is not a competitor of XSLT. CSS is a method for statically
formatting an XML document in a way that allows you to separate
formatting and styling information from the document, but it does not
allow you to dynamically transform an XML document into another data
format. With CSS, you cannot manipulate the structure of an XML
document, change the ordering of content, or dynamically generate a
table of contents from a set of headings. Only XSLT can do that.



Using CSS to complement XSLT, however, is a powerful strategy for
building web pages \-- a strategy that splits presentation into what I
call formatting and styling. Formatting can be seen to include basic
HTML markup like headings, horizontal rules, lists and the like.
Styling, meantime, defines the visual properties of markup: Its colors,
sizes, widths, margins, bullet types, and so forth. Although the
distinction between the two is not always clear-cut, formatting
typically appears in the form of elements, styling information in the
form of attribute-value pairs. For example, in
`<h1 style="color: olive;">` the h1 element formats the text as a
first-level heading while the values of the style attribute, used for
specifying inline CSS styles, reflect how the text should be styled.



You can gain a great deal of utility from separating as much styling
information as possible from the formatting and placing it a Cascading
Style Sheet, though until the second major version of CSS, CSS Level 2,
is better supported by browsers, your HTML formatting markup will still
have to retain some styling information, such as that for tables.
Separating visual styling from formatting gives you a way to make
wholesale design changes to a web site without having to change the
formatting code in every HTML document; if you\'ve set up your web pages
properly, with all of them linking to a single CSS, you merely make the
changes in one file, the Cascading Style Sheet.

Cascading Style Sheets: The Definitive
Guide,
published by O\'Reilly, provides a detailed account of how to use CSS.
The W3C CSS specifications are
available at http://www.w3c.org. 


### Related Pages

The tutorials in this series proceed as follows:

1.  [An Introduction to XML](xml_intro.html)
2.  [Structuring Documents in XML](structuring_docs.html)
3.  [Developing a Document Type Definition](dtd1.html)
4.  [Attributes and Entities in DTDs](dtd2.html)
5.  [An Introduction to XSL](xsl1.html)
6.  [Using XSLT to Separate Content from Presentation](xsl2.html)


