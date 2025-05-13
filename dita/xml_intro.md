---
author: Steve Hoenisch
description: 'Creating XML documents.'
keywords: | 
    XML, XSL, XSLT, CSS, markup, markup strategies, XML documents, XML structuring, structuring XML documents, XHTML, content, presentation, DTD, formatting XML, XSL:FO, formatting objects 
title: 'An Introduction to XML: Building Your First Document'
---


_This article appeared in Volume 2 Issue 5 of_ XML Journal _magazine in 2001._


# 1 Orientation

XML. And XSLT, DTD, XPath, XSL-FO, XLink, XPointer, SAX, and DOM. To the uninitiated, all the talk about XML quickly dissolves into an alphabet soup of W3C recommendations, abbreviations, and acronyms. This column, with a minimum of technobabble and a good dose of hands-on work, aims to indoctrinate you into the world of XML and to teach you how to use it for web publishing. During the next 12 issues of XML-Journal, I will use tutorials to expand your knowledge of XML and, after the first couple of columns, expose you to a different member of the XML family of technologies or to one of its close relatives.

<img src="/images/xmlj_v2i5.jpg" align="right"/>

Today I'll introduce you to XML and show you how to create your first XML document. Picking up where this column leaves off, the next will discuss fundamentals of structuring and marking up data. Subsequent columns will address such core XML technologies as XSL, DTDs, and XLink. Later in the year, I will turn to more advanced XML ics and related technologies: XSLT, XSL-FO, XML Schema, XPath, DOM, SAX, JSP, and web publishing frameworks like Apache Cocoon. Along the way, I'll also touch on Cascading Style Sheets (CSS), XHTML, and Wireless Markup Language (WML) as well as on XML parsers, XSL processors, and a few handy XML tools.

To help you learn, each month's column will assign some related hands-on work to spur you to begin thinking about and working with the technology. The work will be of two kinds: (i) reading references to which I will point you for additional information and (ii) working with XML code or files. The coding will, at least during the first few columns, center on converting your resume to XML and readying it for publication on the web.

The degree of difficulty of the hands-on work -- and indeed the column itself -- is geared toward new users of XML, though I will assume have some knowledge of HTML. The column's primary target audience is anyone without a formal programming background -- such as content authors, web designers, HTML coders, technical writers, and amateur programmers -- who wants to learn XML. Others are of course welcome, too.

For continuity, each month's column will typically be structured in a similar manner: The column will begin with an introduction that lays out its objectives and scope. The next section will present the background, concepts, and terminology necessary to understand the tutorial and to perform the hands-on work. Then a tutorial will demonstrate how to develop and apply the XML technology in question. The column's final section will assign a new hands-on task, review last week's, and address email from readers. Throughout the column, I will give you plenty of points of departure - that is, references and resources, both online and in books - that you can pursue to find out more about those aspects of XML that interest you. As we proceed in this way, each subsequent column will extend the knowledge gained the previous month.


# 2 What Is XML?

All this talk about XML raises the question: What is it anyway? And what about the jumble of abbreviations that cloaks XML from the curious eyes of an HTML coder or content author? How do XSLT, DTD, XLink and all the rest fit into the XML equation?

Extensible Markup Language is, first and foremost, a metalanguage for describing and structuring data with tags. "Metalanguage" means a language for how to describe other languages. Like HTML, XML uses tags (words bracketed by "`<`" and "`>`"), but unlike HTML, XML has neither a predefined set of tags nor rules for how to use them (though XML does have generic rules governing markup; for instance, tags may not overlap). In XML, tags and the rules for them, or grammar, are defined by the users themselves. XML programmers use tags and their corresponding grammar to describe and structure data in a simple text format like that of HTML (as opposed to a binary format). Because users can define their own tags, XML, as its full name implies, is also extensible, meaning that, unlike HTML, it is capable of being extended. You will begin learning how to create your own XML tags today, in the tutorial section below.

## 2.1 A Family of Technologies

The hodgepodge of abbreviations and acronyms surrounding XML points up another of its characteristics: It is a family of technologies designed to be used over the Internet. Some of XML's family members and their main functions are as follows:

* Extensible Stylesheet Language (XSL), which in turn comprises Extensible Stylesheet Language Transformations (XSLT) and Extensible Stylesheet Language Formatting Objects (XSL-FO). XSL is an XML-based language for expressing stylesheets. XSLT is a language for transforming XML documents into (typically) other XML documents, HTML, and WML. XSL-FO is used to format XML documents for printing. My third column will present a tutorial on XSLT. Later columns will delve into XSL-FO and expand on XSLT.

* Document Type Definition (DTD). Stemming from Standard Generalized Markup Language, the progenitor of both HTML and XML, a DTD defines the rules that constrain an XML document or a set of XML documents. In my third column, I'll teach you how to construct a DTD.

* XML Schema, for which we've thankfully been spared yet another abbreviation to remember, may eventually supplant DTDs as the primary mechanism for constraining XML data. An XML Schema, which is itself in the format of an XML document, serves the same function as a DTD while correcting some of its limitations. This column will cover XML Schema at a later time.

* XLink, XPath, and XPointer together provide the foundation for creating links and asserting relationships within and among XML documents. XLink describes how to create hyperlinks among XML documents and provides mechanisms for advanced capabilities like multidirectional linking. XPath, widely used by XSLT, allows users to locate specific nodes or node sets within XML documents (you'll learn about nodes next month). XPointer specifies how to describe and point to locations of various kinds within an XML document. My fifth column will address linking in XML. 

* Namespaces is a specification that describes how to associate a URL with all the tags in an XML document to ensure that they are unique, thereby eliminating ambiguity when the same tag is used by different XML coders. I'll introduce you to Namespaces after we move through some of the more fundamental aspects of XML.

* The Document Object Model (DOM) and the Simple API for XML (SAX). The Document Object Model, itself an Application Programming Interface, or API, is used to represent the structure and content of XML (and other) documents and provides an interface that allows programs and scripts to manipulate them. SAX, like DOM, also allows applications to get information from an XML document and do something with it. This column will provide an introductory tutorial on DOM and SAX toward the end of the year.

These are just some of the XML-related technologies relevant to a broadly focused XML tutorial. As you may have guessed, there is a plethora of other XML-related specifications and applications, most of which are still evolving: XML Query, XML Base, XML Signature and Canonicalization, XML Protocol, MathML, SMIL, SVG, and FpML, to name a few. You can visit the World Wide Web Consortium's (W3C) web site, https://www.w3c.org, for the rundown on most of these initiatives.

To get a more complete description of what XML is and what its core related technologies are, I'd like you to read two short pieces: an article on the W3C web site called "XML in 10 Points," at https://www.w3.org/XML/1999/XML-in-10-points, and the first half of Chapter 1 in Brett McLaughlin's book, Java and XML, published by O'Reilly. For a slighly more technical introduction to XML, visit https://www.xml.com/pub/a/98/10/guide0.html.


# 3 The Ingredients of an XML Document
Now that you have a sense of what XML is, let's jump right into the language and begin working with it by creating a simple XML document from the  down.

An XML document typically comprises several fundamental components, all of which must be enclosed in angle brackets ("`<`" and "`>`"):

* A processing instruction containing an XML declaration. This should be the first line of your XML document.
* A document type declaration
* A root element
* Other elements
* Attributes
* Comments

## 3.1 Processing Instructions

Processing instructions, which identify a task for an application to execute, start with `<?` and end with `?>`. XML documents begin with a processing instruction that contains an XML declaration:

```
<?xml version="1.0" standalone="yes"?>
```

The attribute-value pair version="1.0" signals to the XML processor that the document conforms to version 1.0 of the XML specification, which was developed under the auspices of the W3C and is available at https://www.w3.org/TR/2000/REC-xml-20001006. The standalone attribute, which is optional and takes yes or no in either single or double quotation marks as its value, specifies whether an external DTD is required to parse the XML document. If the value of standalone is yes, then an external DTD is not required.

## 3.2 A Document Type Declaration and a Root Element

Not to be confused with Document Type Definitions, document type declarations, which begin with `<!DOCTYPE`, perform two functions. They provide a list of Document Type Definitions or specify the location of the file's external Document Type Definition, and they identify the document's root element, also called its root node. Since XML documents do not need to have a Document Type Definition to be well formed, I will, for now, skip this aspect of the declaration. A root element, however, is required: All XML documents must have one (though it is not required to be declared with a document type declaration if the document uses neither an internal nor external DTD). In the following declaration, the root element is the word after `<!DOCTYPE`:


```
<!DOCTYPE resume>
```

Remember that since in XML you define your own tags, the root element can be any combination of permitted characters that you choose.

Even though the root element has been specified in the document type declaration, it must still appear as the document's first element:


```
<resume>
```

3.3 Other Elements

Besides a root element, XML documents typically contain a hierarchy of other elements, as this example shows:


```
<contactInfo>
	<name>Steve Hoenisch</name>
	<email>shoenish@rcn.com</email>
	<phone></phone>
	<address type="business">
		<street>10 First Avenue</street>
		<city>New York</city>
		<state>New York</state>
		<zip>10101</zip>
	</address>
</contactInfo>
```

All elements, including the root, may optionally take one or more attribute-value pairs:


```
<resume name="Hoenisch" field="IT" date="February 2001">
```


## 3.4 Attributes and Comments

In XML, the values of attributes, including those in the processing instructions and declarations, must be enclosed in either single or double quotation marks. XML is not forgiving like HTML: No quotation marks around attribute values, no disco.

Comments begin with `<!-- and end with -->`. Nearly anything except a double hyphen ("--") may be placed inside the comment tags and be ignored by the XML processor. Comments may appear anywhere after the XML declaration. They may not, however, be embedded inside an element tag: `<resume <!-- my resume ... -->>` won't work.

Together, here's how these fundamental components can appear in a simple document:

```
<?xml version="1.0" standalone="yes"?>
<!DOCTYPE resume>
<resume name="Hoenisch" field="IT" date="February 2001">
	<contactInfo>
		<name>Steve Hoenisch</name>
		<email>shoenish@rcn.com</email>
		<phone/>
		<address type="business">
			<street>10 First Avenue</street>
			<city>New York</city>
			<state>New York</state>
			<zip>10101</zip>
		</address>
	</contactInfo>
<!-- The closing tag for the root element, resume, must appear at the document's end:  -->
</resume> 
```

# 4 Well-Formedness Constraints

Let's pause for a moment to consider some markup rules to which XML documents must adhere to be considered well formed. A well-formed document is one that conforms to XML syntax rules and contains correctly positioned elements and attributes. A valid XML document, in contrast, is one that conforms to the constraints of its DTD. For more on well-formed and valid documents, see Robert Eckstein's XML Pocket Reference, published by O'Reilly.

First, notice in the above example that some of the elements are in mixed case. Unlike HTML, XML is case sensitive: `<contactinfo>` is, to the XML processor parsing your document, a completely different tag from `<contactInfo>`. Though it doesn't matter what case or combination of cases you use, the name of an opening tag must match exactly with the name of its closing tag; otherwise, your XML document is not well formed and the XML parser will fail to process it.

Second, an empty element -- that is, one which contains no other elements or text, like `<phone/>` in the examples above -- must have a closing tag, which may be combined with the starting tag. Thus, an empty element can be marked up either as `<phone<>/phone>` or as `<phone/>`.

Third, every non-empty element's opening tag must have a corresponding closing tag: If you open an non-empty element with `<resume>`, it must have a corresponding closing tag of `</resume>` that is properly nested, which brings us to our fourth rule: XML documents, again unlike HTML, may not contain any overlapping tags. Whereas `<h2><i>Headline</h2></i>` might work in HTML, it won't in XML.

Finally, as I have already mentioned, all attribute values must be enclosed in either single or double quotes.


# 5 Follow Up with Self Study

Now I would like you to start getting your hands dirty with XML by doing the following work to prepare for next week's column:


* Make sure you have version 5.0 or greater of Microsoft Internet Explorer installed on your computer. You can download it for free from https://www.Microsoft.com/Windows/IE/. Internet Explorer's XML parser allows you to debug and view XML files and we'll be using it to do just that.

* Use Sublime Text, Notepad, UltraEdit (https://www.UltraEdit.com/), or XMetal to mark up your resume or part of it with tags using not only elements but also attributes. As you do so, try to create tags that describe the structure or content of your resume. Also, think about what aspects of your resume's structure should be captured in attributes as opposed to elements. Don't worry about using a Document Type Definition (but remember to set the value of the standalone attribute in the XML declaration to yes: 


```
<?xml version="1.0" standalone="yes"?>)
```

* Edit your marked-up document to make sure it is well formed, according the rules set out above. Save it on your hard drive as a plain-old text file (ASCII, or Unicode on Windows NT) with an .xml file extension.

* Next, open it in Internet Explorer and use the browser to debug any problems with your markup. If you did not craft your tags according to the rules I described above, Explorer will display an error message that usually provides enough information to find and fix the offending code. Continue debugging your file until it displays as an XML page.

* Buy and begin reading Learning XML, a book published by O'Reilly.

* To prepare for the next tutorial, skim the first few pages of David Megginson's book, Structuring XML Documents.

In my next column, Structuring Documents in XML, I will review an example of this hands-on assignment as well as cover the XML hierarchical tree model, examine different approaches to tagging, and discuss the importance of structured data.

### Related Tutorials

The tutorials in this series proceed as follows:

1.  [An Introduction to XML](xml_intro.html)
2.  [Structuring Documents in XML](structuring_docs.html)
3.  [Developing a Document Type Definition](dtd1.html)
4.  [Attributes and Entities in DTDs](dtd2.html)
5.  [An Introduction to XSL](xsl1.html)
6.  [Using XSLT to Separate Content from Presentation](xsl2.html)


