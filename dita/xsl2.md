---
author: Steve Hoenisch
description: 'A magazine article that demonstrates the power and elegance of XSLT stylesheets in separating content from presentation.'
keywords: | 
    XML, XSL, XSLT, CSS, markup, markup strategies, XML documents, XML structuring, structuring XML documents, XHTML, content, presentation, DTD, formatting XML, XSL:FO, formatting objects 
title: XSLT's Power and Elegance Separates Content from Presentation
---


This article appeared in Volume 3, Issue 3 of _XML Journal_ magazine.


### INTRODUCTION

The power and elegance of the Extensible Stylesheet Language for Transformations stems from its ability to transform XML documents into other output formats like HTML, fulfilling one of the original promises of XML: separating content from presentation.

XSLT is particularly powerful because a single stylesheet can format all the XML documents conforming to a DTD into HTML for publication on a web site. The stylesheet can also be used to automatically generate such features as a hyperlinked table of contents, the building of which without XML requires substantial manual work.


<img src="/images/xmlj_v3i3.jpg" align="right"/>


XSLT is also elegant, because if you need to reformat all the pages in your web site, for instance, you need to change the code in only one place, the stylesheet, so long as your source documents are in XML.

Written primarily for content authors, technical writers, web designers, and other nonprogrammers, this tutorial aims demonstrate some of XSLT's power and elegance in separating content from presentation and in automatically generating narrative-oriented HTML documents while showing you how to create progressively more complex template rules -- rules that are at the core of XSLT.


### REVIEW: THE TEMPLATE RULE

In its most basic form, an XSLT stylesheet uses what are called template rules to match nodes in an XML document and transform them into another format. A template rule is an XSL element that matches a node in the XML source document and typically applies an output format, such as HTML, to it. For example, say you have the following simple XML document:

```
<?xml version="1.0"?>
<document>
<body>You've probably heard the propaganda by now: 
XML blesses you with a way to separate content from presentation.</body>
</document>
```

You can use a template rule to find the children of the root element and to format its contents in HTML for presentation. Here's an template rule that does just that:

```
<xsl:template match="/">
     <html>
          <body>
               <p><xsl:apply-templates/></p>
          </body>
     </html>
</xsl:template>
```

In the above rule, the `<xsl:template match="/">` element uses the value of its match attribute to find a node in the XML source. The forward slash operator, an XPath expression, specifies the document's root node. The rule could also match on the same node by specifying it explicitly in the template rule, that is, `<xsl:template match="document">`. By matching on the root node of the document, we're able to build an HTML container that provides the skeleton code (here, just `<html>` and `<body>`) for our document. Below, I will expand on this concept.

The `<xsl:apply-templates>` element invokes a built-in XSLT template rule that processes the children of the matched node, meaning roughly that it outputs the children. Because there is only one child of the `<document>` node in our XML file, `<xsl:apply-templates>` suffices to print the meager contents of the file. If, however, the `<document>` element contained more children, `<xsl:apply-templates>` would print them all out, too, and we would want additional template rules to control how they are formatted.

Before we can push our source XML and its accompanying stylesheet through an XSLT processor to render the HTML output, we need do a couple more things. First, we need to add an XML processing instruction to the top of the stylesheet. Second, we must wrap the template rule with the `<xsl:stylesheet>` element, which all XSL stylesheets require as their top-level element, and set a namespace for it (note that some versions of Internet Explorer and the MSXML parser may require a different namespace; see http://msdn.microsoft.com/ and the Unofficial MSXML XSLT FAQ at http://www.netcrucible.com/xslt/msxml-faq.htm for details):

```
<?xml version="1.0"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" 
version="1.0">
     <xsl:template match="/">
          <html>
               <body>
                    <p><xsl:apply-templates/></p>
               </body>
          </html>
     </xsl:template>
</xsl:stylesheet>
```

We now have a minimal stylesheet that will convert our XML source to HTML. To view the output in Internet Explorer 5 or greater with version 3 of the MSXML parser, we first need to make a change to the XML source document: It must include a stylesheet processing instruction, appended after the XML processing instruction, that references our new minimal stylesheet, which is in this case located in the same directory as the source file, as the path in the href attribute's value testifies:

```
<?xml version="1.0"?>
<?xml:stylesheet type="text/xsl" href="my_stylesheet.xsl"?>
<document>
<body>You've probably heard the propaganda by now: 
XML blesses you with a way to separate content from presentation.</body>
</document>
```

Let's expand our minimal stylesheet to do a few more things. First, we'll modify our template rule to output the body element specifically (as opposed to all the children of the root element); second, we'll add a link to a Cascading Style Sheet that specifies the visual properties of our HTML formatting:

```
<?xml version="1.0"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" 
version="1.0" >
     <xsl:template match="document">
          <html>
               <head>
                    <link rel="stylesheet" type="text/css" href="doc.css"/>
               </head>
               <body>
                    <p><xsl:value-of select="body"/></p>
               </body>
          </html>
     </xsl:template>
</xsl:stylesheet>
```

This stylesheet first matches the root node explicitly by name (document), builds an HTML container for it as before, and then uses the `<xsl:value-of>` element to select and output the text contents of the message node. The select attribute identifies the element whose contents are to be processed.

Notice that in the stylesheet I also added a link to a sample Cascading Style Sheet in the same directory as the XSLT stylesheet. (The The CSS file contains the code in . In this example, only a few of the CSS rules are used, but the rest of them will be put into play as we expand our rudimentary stylesheet to process a more complex XML document.

Using CSS to complement XSLT is a powerful strategy for building web pages -- a strategy that splits presentation into what I call formatting and styling. Formatting can be seen to include basic HTML markup like headings, horizontal rules, lists and the like. Styling, meantime, defines the visual properties of markup: Its colors, sizes, widths, margins, bullet types, and so forth. Separating visual styling from formatting gives you a way to make wholesale design changes to a web site without having to change the formatting code in every HTML document; if you've set up your web pages properly, with all of them linking to a single CSS, you merely make the stylistic changes in one file, the Cascading Style Sheet.

Cascading Style Sheets: The Definitive Guide, published by O'Reilly, provides a detailed account of how to use CSS. The W3C CSS specifications are available at http://www.w3c.org/Style/CSS/.


### BUILDING A COMPLEX STYLESHEET

This section builds on the review above to create an XSLT stylesheet that transforms any document that conforms to our DTD into an HTML document. We'll create the stylesheet from the top down, step by step, explicating most of the template rules as we go.

Consider the code in the sample XML document that appears in the pop-up window when you click here.

The document is based on a sample DTD. (This DTD is very loosely based on a scaled down version of the TEI Lite DTD with some XHTML and other customizations thrown in; it's been constructed to demonstrate the XSL transformations in this tutorial and, unlike TEI Lite, isn't suitable for other uses; for information about TEI Lite, see http://www.tei-c.org/.)
The XSLT stylesheet is also based on the DTD. Why bring a DTD into this discussion? The answer is that it's best to build the stylesheet based on your DTD to ensure that all elements and attributes are processed fully and according to your requirements. The DTD provides the cues by which you build your stylesheet. That is, to build a suitable stylesheet -- one that processes all the elements and attributes in your XML document fully and appropriately -- you should develop your stylesheet based on your DTD, not on a mere XML document alone. For more information about analyzing DTDs to develop stylesheets, see Chapter 21, DTD Analysis, in The XSL Companion, by Neil Bradley (Addison-Wesley).

Let's start building the stylesheet. Since XSL stylesheets are themselves XML documents, they should generally begin with an XML processing instruction as their first line: `<?xml version="1.0"?>`. The next line contains an optional document type declaration for the stylesheet to specify the stylesheet's root element, xsl:stylesheet. I'm including the document type declaration in our stylesheet because I want to declare several general entities as an internal DTD subset for use in the stylesheet. (Recall that general entities let you replace an entity with its value; that is, wherever the entity pub.date appears in the stylesheet as text, it is replaced by its value as defined in the entity declaration, here June 1, 2002.)

```
<!DOCTYPE xsl:stylesheet [
	<!ENTITY pub.date "June 1, 2002">
	<!ENTITY mdash "--">
	<!ENTITY nbsp "&#160;">
	]>
```

The root element for an XSLT stylesheet must be either xsl:stylesheet or xsl:transform. The xsl: prefix before stylesheet and transform is the customary XSL namespace; all the XSL elements are in the http://www.w3.org/1999/XSL/Transform namespace, which must be referenced as the value of the xmlns:xsl attribute of the xsl:stylesheet root element, as I've done here (see the chapter titled XSL Transformations in O'Reilly's XML in a Nutshell for additional information about the namespace):

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

Next, I set the output method to HTML and include a reference to the HTML version I want to use:


```
<xsl:output method="html" doctype-public="-//W3C//DTD HTML 4.0 Transitional//EN"/>
```


### CREATING AN HTML CONTAINER

Now, bringing a simple template-matching rule into play, we begin building the HTML skeleton for the output file:

```
<xsl:template match="document">
 [...HTML SKELETON CODE...]
</xsl:template>
```

This template rule selects the XML document's root element, `<document>`, and circumfuses it with HTML code, forming a skeleton that will contain the body of the XML document. In the case of this stylesheet, the skeleton is in the form of a header, a content area, and a footer.

In the header, I have used an XSL element -- `<xsl:value-of select="docinfo/title"/>` -- to select the title of the XML document and to output it in the title slot of the HTML document that I'm building.

Notice, too, that between the HTML `<head>` tags I've also created an HTML link to a Cascading Style Sheet, which contains as much as possible of the styling information for my HTML formatting:

```
<link rel="stylesheet" type="text/css" href="doc.css"/>
```

In the next XSL command, I again select the value of the `<title>` tag in the XML document, this time for use as a headline atop the HTML document:

```
<xsl:value-of select="docinfo/title"/>
```

Now skip over the rest of the HTML code in the header and bore into the content area until you find the next command prefaced by the XSL namespace:


```
<xsl:apply-templates select="body"/>
```

This template rule selects the entire contents of the body element in the XML document, processes it according to the other template rules in the stylesheet, and outputs the result at the point of this command inside the HTML container that we built when we matched on the root element earlier.


#### Formatting the Body

To format the body of the XML document, my stylesheet includes a template rule that selects the body element: `<xsl:template match="body">`. This template does three things: It inserts a Table of Contents headline, calls another template that dynamically builds a table of contents, and processes all `<div1>` elements. The `<xsl:call-template name="toc"/>` command calls a macro (located toward the end of the stylesheet in the Macros section) that cycles through the six levels of `<div>` elements, makes a reference to the `<div>` element's heading in the form of a hyperlink, and numbers the section headings using the 1.1 format.

The set of macros that build the table of contents originated in the W3C's XSLT stylesheet for the XML Recommendation. Reverse engineering it is a potent method of teaching yourself some of the advanced capabilities of XSLT. The W3C's stylesheet is available in the download file for Chapter 9 of Michael Kay's book titled XSLT Programmer's Reference at http://www.wrox.com/. In IE5.0 or greater, you can view the XML source code for the W3C's XML Recommendation at http://www.w3.org/TR/2000/REC-xml-20001006.xml; or you can download it and view it using an editor like XML Spy.

The next set of templates in our stylesheet creates headings for the `<div>` elements, mapping the `<head>` element in `<div1>` to the HTML heading element `<h1>` and so forth through `<div6>` and `<h6>`. The template-matching rules for the head elements also call another template, named "head", which inserts an ID attribute in each heading and numbers them with the command mode="number".

#### Processing the Child Nodes

Finally, after building the table of contents and the headings for each `<div>` section, the stylesheet uses the following code to process all the children of the `<div1>` element:

```
<xsl:template match="div1">
     <xsl:apply-templates/>
</xsl:template>
```

In this code, the `<xsl:apply-templates/>` simple tells the XSLT processor to process all the child elements of `<div1>` and to output them according to the template rules for each child element listed further down in the stylesheet. Many of these child elements are processed simply by what I've called the XHTML Quick Print Module. This template rule selects any of the elements listed in the value of the match attribute, makes a copy of the element, makes a copy of all the element's attributes, and simply passes them through to the target output file intact. Because my DTD contains several XHTML elements for low-lying nodes, I can use this template rule instead of writing a separate template rule for each XHTML element.

This sample XSLT stylesheet may be viewed in a pop-up window.


### FURTHER READING

On the heels of this column's brief introduction to XSLT, I suggest you spend a couple of hours in your neighborhood bookstore reading the following chapters in this order:

* Chapter 6, Transformation: Repurposing Documents, in O'Reilly's Learning XML.
* Chapter 8, XSL Transformations, in O'Reilly's XML in a Nutshell.
* Whatever selections you deem useful from Wrox's XSLT Programmer's Reference by Micheal Kay.

Finally, take some time to browse through the resources listed on World Wide Web Consortium's XSL specification page at http://www.w3.org/Style/XSL/. The page includes links to other tutorials, an FAQ, the XSL specifications, and a variety of resources.

I also suggest you start playing around with XSLT a little on your own; it's the best way to learn how to use it. Try playing with the code accompanying this column: Add some elements to the DTD and the XML document and then write template matching rules to process and output them in Internet Explorer. You may have to install the newest version of the MSXML parser to get the code to display correctly; see http://msdn.microsoft.com/downloads/default.asp?url=/downloads/sample.asp?url=/msdn-files/027/001/766/msdncompositedoc.xml for details.

This column has only scratched the surface of XSLT. Its a complex but powerful programming language that, once you learn how to use it, yields the vast gains in productivity that spring from the original promise of XML: separating content from presentation. 


### RELATED TUTORIALS

The tutorials in this series proceed as follows:

1.  [An Introduction to XML](xml_intro.html)
2.  [Structuring Documents in XML](structuring_docs.html)
3.  [Developing a Document Type Definition](dtd1.html)
4.  [Attributes and Entities in DTDs](dtd2.html)
5.  [An Introduction to XSL](xsl1.html)
6.  [Using XSLT to Separate Content from Presentation](xsl2.html)  <i class="fa fa-check-square" aria-hidden="true"></i>





### END OF TUTORIAL SERIES PHOTOGRAPH

<img alt="Sunset over Snoqualmie Pass" src="/photos/snoqualmie-pass-summit-west-sunset.jpg" width="682" height="512" />


A sunset over the Summit West ski area, Snoqualmie Pass, Wash., February 2020. <i class="fa fa-picture-o" aria-hidden="true"></i> Photo Credit: Steve Hoenisch.





