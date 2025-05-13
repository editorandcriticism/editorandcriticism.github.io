---
author: Steve Hoenisch
description: 'A magazine article that introduces you to the art and craft of using XSLT stylesheets to separate content from presentation in XML documents.'
keywords: | 
    XML, XSL, XSLT, CSS, markup, markup strategies, XML documents, XML structuring, structuring XML documents, XHTML, content, presentation, DTD, formatting XML, XSL:FO, formatting objects 
title: An Introduction to XSLT -- Using Stylesheets to Separate Content from Presentation
---

This article appeared in Volume 3, Issue 1 of _XML Journal_ magazine.


### INDOCTRINATION 

You've probably heard the propaganda by now: XML blesses you with a way to separate content from presentation. Separation in turn yields productive gains over HTML and other data formats used to manage content: In a process sometimes called single-sourcing, the content of an XML document can be formatted for display in a web browser, reformatted for delivery to such devices as mobile phones and handheld computers, and converted into a PDF file suitable for printing.

A news story, for example, that has been marked up in XML can be transformed into HTML for publication on a web site, converted into Wireless Markup Language (WML) for display on a cell phone's screen, and rendered into a format from which a PDF file can be generated. Meantime, parts of the news story, such as paragraphs that supply background information about a given subject, can be reused in other XML-encoded news stories. What makes all this possible? XSLT.


<img src="/images/xmlj_v3i1.jpg" align="right"/>


Extensible Stylesheet Language for Transformations, or XSLT, is a functional programming language that enables us to bridge the gap between content and presentation by providing a means of specifying how a content-based XML document is transformed into a presentation-oriented document or data format.

This tutorial, written primarily for content authors, technical writers, web designers, and other nonprogrammers, is the first in a short series that aims to introduce you to the basics of XSLT and to help you get started using it to transform XML documents into HTML. The focus is not on data-centric documents but on such narrative-centric documents as reference manuals, help files, essays, stories, instructions, books, and magazine articles.

I'll begin by briefly summarizing the background of XSL and contrasting XSLT with XSL-FO and Cascading Style Sheets (CSS). Along the way I'll discuss what XSLT is, what it can do, and how to use it in conjunction with CSS to separate content from presentation. The next section will introduce you to XSLT's most fundamental component, the template rule, and demonstrate how to write one, culminating in a simple XSLT stylesheet that uses Internet Explorer 5.5's XSLT processor to transform a simple XML document into an HTML document.



### XSLT, XSL-FO, AND CSS

The birth of XSLT breaks down like this: Extensible Stylesheet Language (XSL) was conceived as an XML application for expressing stylesheets capable of manipulating XML documents. After its submission to the W3C in 1997, XSL split into two stylesheet standards: Extensible Stylesheet Language for Transformations (XSLT) and Extensible Stylesheet Language Formatting Objects (XSL-FO). XSLT is a language for transforming XML documents into typically other XML documents, HTML, and WML, but can also be used to produce documents in plain text and XSL-FO. XSL-FO is used to describe the layout of XML documents for printing, with the end product usually being in Portable Document Format (PDF). XSL-FO, a complex standard that some refer to as simply XSL, may eventually also be employed to lay out web pages, though this use is unsupported by current versions of web browsers. You can find more information about XSLT and XSL-FO, including their specifications, on the World Wide Web Consortium's web site, www.w3c.org. This column focuses on XSLT; later tutorials will expand on XSLT and delve into XSL-FO.

The early XSL proposals also gave rise to another breakaway standard, XPath. It grew out of the location-finding aspects of the XSL and XPointer specifications, which had been independently using similar mechanisms to find information in XML documents. XSLT heavily uses XPath to locate specific nodes or node sets within XML documents. Details about XPath specification can be found at http://www.w3c.org/TR/xpath.

XSL has another related standard, though unlike XSL it is not based in XML: Cascading Style Sheets (CSS). In the context of web publishing, Cascading Style Sheets (CSS) can also be used, at least theoretically, to statically format XML documents for display, but it cannot be used to transform them in any meaningful way. For example, XMetal, a tool for writing and editing in XML, uses CSS to format XML documents for display in its normal view. But until there is much stronger web browser support for displaying XML documents with CSS, it is not a practical option for web publishing.

CSS is not a competitor of XSLT. CSS is a method for statically formatting an XML document in a way that allows you to separate formatting and styling information from the document, but it does not allow you to dynamically transform an XML document into another data format. With CSS, you cannot manipulate the structure of an XML document, change the ordering of content, or dynamically generate a table of contents from a set of headings. Only XSLT can do that.

Using CSS to complement XSLT, however, is a powerful strategy for building web pages -- a strategy that splits presentation into what I call formatting and styling. Formatting can be seen to include basic HTML markup like headings, horizontal rules, lists and the like. Styling, meantime, defines the visual properties of markup: Its colors, sizes, widths, margins, bullet types, and so forth. Although the distinction between the two is not always clear-cut, formatting typically appears in the form of elements, styling information in the form of attribute-value pairs. For example, in `<h1 style="color: olive;">` the h1 element formats the text as a first-level heading while the values of the style attribute, used for specifying inline CSS styles, reflect how the text should be styled.

You can gain a great deal of utility from separating as much styling information as possible from the formatting and placing it a Cascading Style Sheet, though until the second major version of CSS, CSS Level 2, is better supported by browsers, your HTML formatting markup will still have to retain some styling information, such as that for tables. Separating visual styling from formatting gives you a way to make wholesale design changes to a web site without having to change the formatting code in every HTML document; if you've set up your web pages properly, with all of them linking to a single CSS, you merely make the changes in one file, the Cascading Style Sheet. Cascading Style Sheets: The Definitive Guide, published by O'Reilly, provides a detailed account of how to use CSS. The W3C CSS specifications are available at http://www.w3c.org/Style/CSS/. In this tutorial, I will begin demonstrating how to use CSS with XSLT to separate styling from formatting, and I'll expand on the topic in later tutorials.



### PRELIMINARIES: PRINCIPLES OF SEPARATION

There are other principles of separation that can be immensely useful in building well-engineered, text-based web pages with XML, XSLT, CSS, and HTML. An overarching objective is to use XML to structure content and XSLT and CSS to format it in a way that minimizes redundancy and maximizes flexibility, including the capability to repurpose content and publish it in various formats. Most of the principles listed below are best applied to narrative-oriented documents that will be published as white papers, technical manuals, help files, essays, and so forth. Keep in mind that these principles are merely a guide and that the list of exceptions is long: Your data, purpose, audience, delivery format, and other factors will influence how you engineer your system's own matrix of structure, metainformation, parameters, content, and presentation.

* XML documents: Strive to maximize the content that exists as text, not as tags, in your XML documents. In other words, content that you expect end users to see should usually be set as content, not as elements or attributes. Avoid setting content as tags, either as elements or attributes, even if doing so comes at the cost of some redundancy; it's easier for content authors to work with content that is out in the open, not hidden as the value of attributes or as elements themselves. Instead, use elements to describe the structure or content of your material; use attributes to capture metainformation about the content or its structure and to encode parameters that are used to process the content. Place recurring content, especially content that may change, such as the name of a product under development, in entities. Shy away from placing formatting or styling information in your XML documents, though it may be expedient to include some table and image formatting instructions.

* XSLT stylesheets: Place as much formatting information as possible in your XSLT stylesheet and eschew using it as a container for standard content. Instead, place content out in the open in your XML documents even if doing so comes as the expense of a little duplication. However, highly variable content, such as the date of publication and the version number, may be best placed in the XSLT stylesheet as entities. It may also benefit you to make exceptions for content that varies by audience, as in the case of parameterized settings used in internationalization.

* Cascading Stylesheets, as I mentioned above, should complement the XSLT stylesheet by containing as many as possible of the formatting code's visual styling properties.


In the examples that accompany this and later tutorials in the series, you'll see some of these principles at work.


### XSLT'S ATOM: THE TEMPLATE RULE

In its most basic form, an XSLT stylesheet uses what are called template rules to match nodes in an XML document and transform them into another format. (Actually, it is the XSLT processor that takes an XML document, called a source tree, and an XSLT stylesheet as input and uses them to produce a result tree as output, which can then be serialized into a file, but we need not worry about such technicalities just yet.) A template rule is an XSL element that matches a node in the XML source document and typically applies an output format to it. For example, say you have the following simple XML document:

```
<?xml version="1.0"?>
<source>
     <message>Greetings and Salutations.</message>
</source>
```


You can use a template rule to find the children of the `<source>` element and to format its contents in HTML for presentation. Here's an XSLT template rule that does just that:

```
<xsl:template match="/">
     <html>
          <body>
               <h1><xsl:apply-templates/></h1>
          </body>
     </html>
</xsl:template>
```

In the above rule, the `<xsl:template match="/">` element uses the value of its match attribute to find a node in the XML source. The forward slash operator, an XPath expression, specifies the document's root node. The rule could also match on the same node by specifying it explicitly in the template rule, that is, `<xsl:template match="source">`. By matching on the root node of the document, we're able to build an HTML container that provides the skeleton code (here, just `<html>` and `<body>`) for our document.

The `<xsl:apply-templates>` element invokes a built-in XSLT template rule that processes the children of the matched node, meaning roughly that it outputs the children. Because there is only one child of the `<source>` node in our XML file, `<xsl:apply-templates>` suffices to print the meager contents of the file. If, however, the `<source>` element contained more children, `<xsl:apply-templates>` would print all of them out, too, and we would want additional template rules to control how they are processed and outputted.

Before we can push our source XML and its accompanying stylesheet through an XSLT processor to render the HTML output, we need do a couple more things. First, we need to add an XML processing instruction to the top of the stylesheet. Second, we must wrap the template rule with the `<xsl:stylesheet>` element, which all XSL stylesheets require as their top-level element, and set a namespace for it (note that some versions of Internet Explorer and the MSXML parser may require a different namespace; see http://msdn.microsoft.com/ for details):

```
<?xml version="1.0"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" 
version="1.0">
     <xsl:template match="/">
          <html>
               <body>
                    <h1><xsl:apply-templates/></h1>
               </body>
          </html>
     </xsl:template>
</xsl:stylesheet>
```

We now have a minimal stylesheet that will convert our XML source to HTML. To view the output in Internet Explorer 5.5 or greater, we first need to make a change to the XML source document: It must include a stylesheet processing instruction, appended after the XML processing instruction, that references our new minimal stylesheet, which is in this case located in the same directory as the source file, as the path in the href attribute's value testifies:

```
<?xml version="1.0"?>
<?xml:stylesheet type="text/xsl" href="my_stylesheet.xsl"?>
<source>
     <message>Greetings and Salutations.</message>
</source>
```

Let's expand our minimal stylesheet to do a few more things. First, we'll modify our template rule to output the message element specifically (as opposed to all the children of the root element); second, we'll add a link to a Cascading Style Sheet that specifies the visual properties of our HTML formatting:

```
<?xml version="1.0"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" 
version="1.0" >
     <xsl:template match="source">
          <html>
               <head>
                    <link rel="stylesheet" type="text/css" href="my_styles.css"/>
               </head>
               <body>
                    <h1><xsl:value-of select="message"/></h1>
               </body>
          </html>
     </xsl:template>
</xsl:stylesheet>
```

This stylesheet first matches the root node explicitly by name (source), builds an HTML container for it as before, and then uses the `<xsl:value-of>` element to select and output the text contents of the message node. The select attribute identifies the element whose contents are to be processed.

Notice that in the stylesheet I also added a link to a CSS file in the same directory as the XSLT stylesheet. The CSS file contains the following code:
h1 { color: olive; }
This simple code selects the `<h1>` element and renders it in olive in Internet Explorer, effectively separating the color aspect of the heading's visual style from its HTML formatting code in the XSLT stylesheet.

Because XSLT is a programming language, there's a great deal more to it than the simple examples shown above. To reinforce this column's brief introduction, I suggest you read Chapter 6, Transformation: Repurposing Documents, in O'Reilly's Learning XML. I also suggest you start playing around with XSLT a little on your own; it's the best way to learn how to use it. Try creating an XML document and write some simple template matching rules like those above to process your source and output it in Internet Explorer. My next column will delve deeper into XSLT to unearth its complexity and accompanying power.


### RELATED TUTORIALS

The tutorials in this series proceed as follows:

1.  [An Introduction to XML](xml_intro.html)
2.  [Structuring Documents in XML](structuring_docs.html)
3.  [Developing a Document Type Definition](dtd1.html)
4.  [Attributes and Entities in DTDs](dtd2.html)
5.  [An Introduction to XSL](xsl1.html) <i class="fa fa-check-square" aria-hidden="true"></i>
6.  [Using XSLT to Separate Content from Presentation](xsl2.html)

---------------------------------------------




<script type="text/javascript" src="https://platform.linkedin.com/badges/js/profile.js" async defer></script>
<div class="LI-profile-badge"  data-version="v1" data-size="medium" data-locale="en_US" data-type="horizontal" data-theme="light" data-vanity="steve-hoenisch-4092344b"><a class="LI-simple-link" href='https://www.linkedin.com/in/steve-hoenisch-4092344b?trk=profile-badge'>Steve Hoenisch</a></div>










