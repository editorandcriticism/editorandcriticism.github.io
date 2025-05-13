---
author: Steve Hoenisch
description: 'A magazine article that explains how to structure documents with XML by using three approaches to markup: presentation, structure, and content.'
keywords: | 
    XML, XSL, XSLT, CSS, markup, markup strategies, XML documents, XML structuring, structuring XML documents, XHTML, content, presentation, DTD, formatting XML, XSL:FO, formatting objects 
title: 'Structuring Documents with XML'
---

_This article appeared in Volume 2, Issue 6 of_ XML Journal _magazine_.

### Introduction

This month's tutorial, the second in a series, picks up where last month's left off along the path toward publishing your resume on the Internet as an XML document. Last month I presented an overview of XML, described its basic building blocks, and demonstrated how to create a simple XML document. This month, after reviewing XML's fundamental components, I will guide you through the process of marking up a resume with XML. In doing so, the column will touch on the fundamentals of structuring and marking up data as well as some of the concepts --- like hierarchical trees, nodes, and parent-child relationships --- that underlie XML documents.

<img src="/images/xmlj_v2i6.jpg" align="right"/>

My objective is to help you learn how to structure a document using XML. Toward that end, I will compare three approaches to tagging, those based on presentation, structure, and content. The comparison of these three approaches lays the groundwork for developing a tagging strategy for resumes. Then we'll turn to a quick discussion of hierarchical trees that will supply the terminology needed to address the abstract structure of XML documents. Next, we'll begin the task of reviewing last week's hands-on work and expand on it while marking up a resume in XML. Throughout the column I will introduce you to several new language constructs, again building on last week's tutorial.



### XML's Building Blocks

But first a terse review, peppered with a few new constructs, of the XML fundamentals covered in last month's column:

Remember that a simple XML document must contain at least an XML processing instruction and one or more elements, all encased in angle brackets. Processing instructions start with `<? and end with ?>`. XML documents must begin with an XML processing instruction, which may contain a declaration: `<?xml version="1.0" standalone="yes"?>`. The standalone attribute, which is optional and takes yes or no as its value, specifies whether an external DTD is required. If the value is yes, an external DTD is not required.

The XML processing instruction on the first line of your document may also define the character set used, and its generally a good idea to include it. By default, XML documents use the UTF-8 encoding of Unicode. But you may use the encoding keyword to insert a declaration that specifies that set or another set, as the following example does:



```
<?xml version="1.0" encoding="UTF-16" standalone="yes"?>
```


All the gritty details about the available character sets, including which to use when, can be found in XML in a Nutshell, written by Elliotte Rusty Harold and W. Scott Means and published by O'Reilly. Additional technical details can be found at the W3C's character-encoding page at http://www.w3.org/TR/REC-xml#charencoding.

XML documents also typically include a document type declaration. It begins with `<!DOCTYPE` and performs two main functions: It references a document type definition, or DTD, and identifies the document's root element. The document type declaration may also contain an internal DTD subset, which we'll talk about in a later column. In the following declaration, the root element is the word after `<!DOCTYPE`:


```
<!DOCTYPE resume>
```


The document type declaration, however, is not required for the document to be well formed. A well-formed document is one that adheres to the rules of XML syntax. A valid XML document, in contrast, is one that conforms to the constraints of a DTD.

Even though the root element has been specified in the declaration, it must still appear as the document's first element:


```
<resume>
```


Besides a root element, XML documents typically contain a hierarchy of nested elements. There are, however, a few restrictions on the characters that may be used in element names, especially as their first symbol. In particular, element names must begin with an underscore or a letter in either upper- or lowercase, but never a number. The tag `<2001Resume>` is not permitted. After starting with a letter or underscore, a tag may contain numbers as well as other letters, hyphens, underscores, and periods. The use of colons is illegal unless you are specifying a namespace, which will be addressed in a later column. Also illegal is to begin an element name with the letter combination of xml in any variation of upper- and lowercase. And don't forget that the sequence of symbols used in your opening and closing tags must be exactly the same. For more information about legal and illegal tags in element and attribute names, see Robert Eckstein's XML Pocket Reference, published by O'Reilly. The technical details about valid XML characters are available at http://www.w3.org/TR/REC-xml#charsets.

All elements, including the root, may optionally take one or more attribute-value pairs. XML documents may also contain comments; they begin with `<!-- and end with -->`.

Remember, too, that an XML document must also adhere to certain markup and syntax rules to be considered well formed. First, XML is case sensitive: The name of an opening tag must match exactly with the name of its closing tag. Second, an empty element --- that is, one which contains no other elements or text --- must have a closing tag, which may be combined with the starting tag. Thus, an empty element can be marked up either as `<phone></phone>` or as `<phone/>`. Third, every non-empty element's opening tag must have a corresponding closing tag: If you open an non-empty element with `<resume>`, it must have a corresponding closing tag of `</resume>` that is properly nested, which brings us to our fourth rule: XML documents may not contain any overlapping tags. Whereas `<h2><i>Headline</h2></i>` might work in HTML, it won't in XML. Finally, all attribute values must be enclosed in either single or double quotation marks.

When we delve into the tutorial below and the review of last week's work, you'll see how the components and rules above are used to create XML documents.

If you missed last month's column and feel you need more information about what I just reviewed, you may want to spend a few minutes reading up on the basics of XML. If you don't have a copy of last month's XML Journal handy, I suggest you read the following references: the first half of Chapter 1 in Brett McLaughlin's book, Java and XML, published by O'Reilly; and Chapter 1 plus pages 11 through 16 of Chapter 2 in XML in a Nutshell, available from www.Amazon.com. More about constructing well-formed XML can be found in the XML Pocket Reference. These readings, taken together, should bring you in line with last month's tutorial.



### Tag Talk

Before beginning to mark up an isolated document with tags, there are several key markup-related decisions to make: One is choosing a convention for tag names, a second is deciding what information to capture in attributes as opposed to child elements, a third is choosing an approach to markup.

Besides the obvious --- consistency --- choosing a convention for tag names should be guided by the following criteria:



* Ease of reading. One of the W3C's stated goals for XML documents is that they be legible to humans (as opposed to machines) and reasonably clear. Your tagging scheme should reinforce XML's self-documenting capacity and not undermine its legibility. (For more on the goals of XML, see http://www.w3.org/TR/REC-xml#sec-origin-goals.)

* Simplicity and ease of usability and re-creation. In general, the simpler your naming convention, the easier it will be to apply. An easy-to-remember naming format will make writing stylesheets and DTDs easier, too.

* Compatibility with XHTML.

* The potential for reuse with or incorporation into preexisting document type definitions (DTDs), schemas, XSL stylesheets, and tag lists.

* Ease of use of tag content, especially attribute values, in target output.

Since XML does not restrict you to a particular case or format (other than those outlined above), you're free to choose. But in the face of the above criteria, the four main possibilities --- lowercase, uppercase, initial caps, and mixed case --- are not equal. Consider the following possibilities:


```
1. <ELEMENT>

2. <Element>

3. <element>
```


Compatibility with XHTML rules out option 1. In XHTML, all HTML tags must be lowercase. Besides, anything written in all capital letters, even tag names, is hard to read. Option 2 is a bit easier to read, but if you mix your tags with XHTML tags, as is useful to do at lower levels in the hierarchy of traditional documents like software manuals, especially those destined for publication on the web, than [THEN] you'll also find your tags becoming inconsistent: The tags you define begin with an uppercase letter while the XHTML tags begin with a lowercase letter. Option 3 then seems to be the choice that would ensure the greatest consistency, especially if you are considering the use of XHTML in your XML markup. Using lowercase tag names also increases the potential for reusing preexisting tag lists, XSL stylesheets, and DTDs, as most XML programmers seem to prefer lowercase tags. For instance, UltraEdit, a text editor, comes with an XML tag list containing tags in lowercase.

Complex element names and the addition of attributes force us to make more decisions. Consider these tags:


```
4. <elementname property="hard to read">

5. <element_name property="Easy to Read">

6. <elementName property="Easy to Read">
```


Option 4 is difficult to read, ruling it out. Options 5 and 6 are equal in readability and the potential for reuse with existing DTDs and stylesheets: Some XML programmers use option 5 while others use 6. Others use a hyphen instead of the underscore of option 5. For its tag list, UltraEdit uses option 6. Still others use option 4, as can be seen by viewing the XML markup behind the XML specification itself. It's an interesting case study in XML markup; take a moment to study it. In Internet Explorer version 5.0 or greater, go to http://www.w3.org/TR/2000/REC-xml-20001006.xml.

While elements are the principal means for structuring data, attributes are typically used to capture properties of elements, and their values further modify or, well, set a value for the property, as this tag demonstrates: `<desk color="blue">`.

If you choose to set your element names in lowercase, it's best, I believe, to set attribute names in lowercase, too, fostering consistency with the element names. The case of attribute values, however, is a bit trickier. The deciding factor is the use to which they will be put. In narrative-oriented documents, I often use attribute values to contain metacontent about elements names: `<section type="Introduction">`. Besides making the value easier to read amid other coding, capitalizing it fosters its reuse as a headline when the document is outputted through an XSL stylesheet.

Before beginning to code your document, you'll also need to decide what information to capture in attributes as opposed to child elements. The approach I use for traditional documents is to capture metainformation but not content in attributes. XML in a Nutshell addresses the question of using attributes vs. child elements in chapter 2, titled XML Fundamentals. Reading that chapter will reinforce and expand on the concepts discussed in this column.



### Markup Strategies

Choosing an approach to markup is another decision you should make before you begin. There are three principal markup strategies:



* Presentation-based tagging

* Structure- or publication-oriented tagging

* Content or information-based tagging



The three approaches form a dichotomy, with structure-oriented tagging hugging the middle ground, as illustrated by these examples:



```
Presentation         Structure                    Content

<ital>damn</ital>    <emphasis>damn</emphasis>    <expletive>damn</expletive>
```


The markup strategy behind HTML is based almost entirely on presentation: Tags like `<h1>`, `<i>`, and `<b>` indicate how content should be presented through a browser. The motivation behind using XML, however, is that it allows you to separate content from presentation and to structure data based on meaning, resulting in data and documents that are easier to reuse, manipulate, and search. Exclusively using a presentation-oriented approach to tagging defies the purpose of XML. Better is to use either a structure- or content-based approach.

Structure-based tagging is a generic, flexible approach with a wide scope, most useful when exchanging documents within a discipline or across industries. Employing a loosely structured DTD, it emphasizes elements like `<section>`, `<subsection>`, and `<paragraph>`. Additional information about content is often delegated to attributes: `<section type="Introduction">`.

Content-based tagging is a custom, less flexible approach with a narrow scope, most useful when modeling content around clearly defined user needs or a unique class of documents or both. Using a tightly structured DTD, it emphasizes the use of elements like `<introduction>` and `<explanation>`.

In reality, however, most documents intended for publication on the Internet or an intranet combine all three approaches: The higher levels of the hierarchy use content-based tags, the middle levels use structure-oriented tags, and the lower levels, especially at the clausal level, may, for expedience, use some presentational tags from XHTML. Since the focus of this column is primarily on creating XML documents for publication on the Internet, we will use a combination of all three approaches and learn a bit about XHTML as we do so. But as you mark up documents in XML, you will have to evaluate the structure of your documents and the uses to which they will be put before you decide on your own approach. Just be sure you do some planning and design before beginning the markup process. David Megginson's book, Structuring XML Documents, published by Prentice Hall, offers a plethora of information and good advice about choosing an approach to tagging that will work best for your document or project.



### Hierarchical Trees

Last month I asked you to start getting your hands dirty with XML by using a text editor like Notepad or UltraEdit to mark up your resume or part of it. I suggested that you use not only elements but also attributes and that you try to create tags describing the structure or content your resume. I also suggested you think about what aspects of your resume should be captured in attributes as opposed to elements. Marking up part of your resume in XML and debugging it in Microsoft Internet Explorer 5.0 or greater should have resulted in the document being displayed like the hypothetical resume fragment in Figure 1.

Notice how Internet Explorer's default view for an XML document reveals its hierarchical structure: The minus and plus signs allow the document to be displayed as a collapsible outline --- indeed, as a collapsible tree. In XML, various concepts, most of which spring from the way we speak about trees or families, are used to express relationships within an XML document's hierarchical structure. At the base of its hierarchy, each tree has a root element, and it can be seen in Internet Explorer by clicking on the first minus sign of an XML document. From the root node stems a hierarchy of other branches and leaves. Leaves are terminal elements: They do not contain child elements.

Each element in a tree structure is called a node. Relationships among nodes are expressed using metaphors borrowed from families: The root node, for instance, is the parent of all the other nodes, called children; together they enter into a parent-child relationship. Although a parent element can have multiple children, each child node has exactly one parent node. XML and its accompanying specifications like XPointer use such constructs as parent, child, sibling, ancestor, and descendant in keywords, expressions, and functions. For more information on parent-child relationships and related constructs, see XML in a Nutshell and XML Pocket Reference.



### Tutorial

Bringing to bear the XML constructs and strategies discussed above, let's step through the coding of part of an actual resume, which is of course a bit more difficult than the coding behind the hypothetical one shown in Figure 1, which perhaps somewhat naively exclusively uses content-based tagging.

The use to which we intend to put the resume determines, to a certain extent, how we should mark it up. If you're building a web site that collects and presents resumes from job seekers, you would probably want to employ a different markup strategy from one used to code a resume for isolated publication on the web. My primary objective here is to structure the content of the resume in such a way that I can use it as the source for different output formats, including not only HTML but also plain ASCII text, Portable Document Format (PDF), and Wireless Markup Language (WML). I would also like to keep the resume's structure somewhat flexible, in case I decide to add additional material, like a listing of computer skills or references. To mark up the resume, I will blend all three markup approaches, using both content- and structure-oriented tagging complemented by a smattering of presentation-based tagging at the lowest levels. Throughout, I am careful to avoid duplicating information.

I begin with the usual XML processing instruction and include a character encoding declaration. The standalone value of "yes" indicates that an external DTD is not required.


```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
```


Next comes the document type declaration, which specifies that the document's root element is resume.


```
<!DOCTYPE resume>
```


The markup starts with the root element and branches into two high-level structure-oriented elements: header and section. I decide to use a repeatable structure-oriented section element instead of a set of nonrepeatable content-based tags like experience and education to give me the flexibility to add additional sections later. To capture the content of each section, I use the value of the id attribute.


```
<resume>

<header>

	<name>Jane Doe</name>

	<contactInfo>

		<email>janedoe@home.com</email>

		<phone/>

		<addresses>

			<address type="Home">

				<street>10 First Avenue</street>

				<city>New York</city>

				<state>New York</state>

				<zip>10101</zip>

			</address>

		</addresses>

	</contactInfo>	

	<portfolio>Online portfolio available at 

   <a href="http://www.JaneDoePorfolio.com">www.JaneDoePortfolio.com</a>

 </portfolio>

	<objective>To obtain a position as a <emph>content author.</emph></objective>

</header>



<section id="Qualifications">

	<head>Summary of Qualifications</head>
```


Instead of using a content-based tag like qualification for each item in the list of qualifications, I simply borrow HTML's unordered list elements:


```
	<ul>

		<li>In-depth knowledge of multimedia design.</li>

	</ul>

</section>

<section id="Positions">

	<head>Experience</head>

	<position>Content Author</position>

	<employer>XYZ Multimedia Inc.</employer>

	<duration>March 1998 through February 2001</duration>

	<duties>

		<ul>

		<li>Created multimedia content for the company's web site.</li>

		<li>Used Photoshop to refine graphics created by other authors.</li>

		</ul>

	</duties>

</section>



<section id="Training">

	<head>Education</head>

	<education>
```


Because the year of graduation is not always displayed in a resume but may still be useful information to have, it is encoded using an attribute:


```
	<degree year="1997">MA</degree>

	<subject>Photography</subject>

	<school>University of Washington</school>

	</education>

</section>

</resume>
```




### Hands-On Work

This is, of course, just one possible way to mark up a resume, and not necessarily the best way. Deciding on how to build a data structure for a large set of resumes that will be made available on a web site is a complicated task requiring consideration of a number of factors, including the wholesale avoidance of duplicate information; the flexibility to accommodate resumes written in different styles and with different content; and the capability to conduct specialized searches. Mark Wilson and Tracey Wilson, in Chapters 1 and 2 of their book, XML Programming with VB and ASP, published by Manning, provide additional examples about how to mark up a resume or a collection of them in XML, but more importantly they also explain the motivations for wanting to do so. W. Scott Means' article "Converting Unstructured Documents to XML," at http://xml.oreilly.com/news/xmlnut3_ 0301.html, demonstrates how to isolate atomic elements to reveal a document's underlying structure. I highly recommend reading it.

To prepare for next month's column, analyze the way in which I structured the data in this resume and identify what, in your opinion, I should have done differently. Email me with your point of view and the justification for it. But don't s there. First, revisit the way you structured your resume after reading last month's column; finish marking it up and debugging it in Internet Explorer 5.0 or greater if you haven't done so already. Second, I would also like to prod you to conceptualize the rules that should constrain a resume's data. To spur you down this path, I suggest you read pages 89 through 108 of Chapter 4, Constraining XML, in Java and XML, written by Brett McLaughlin and published by O'Reilly.

My next column will dive head first into constraining XML data with document type definitions, or DTDs.



### Related Tutorials

The tutorials in this series proceed as follows:

1.  [An Introduction to XML](xml_intro.html)
2.  [Structuring Documents in XML](structuring_docs.html) <i class="fa fa-check-square" aria-hidden="true"></i>
3.  [Developing a Document Type Definition](dtd1.html)
4.  [Attributes and Entities in DTDs](dtd2.html)
5.  [An Introduction to XSL](xsl1.html)
6.  [Using XSLT to Separate Content from Presentation](xsl2.html)

-------------------------------------------------

<script type="text/javascript" src="https://platform.linkedin.com/badges/js/profile.js" async defer></script>
<div class="LI-profile-badge"  data-version="v1" data-size="medium" data-locale="en_US" data-type="horizontal" data-theme="dark" data-vanity="steve-hoenisch-4092344b"><a class="LI-simple-link" href='https://www.linkedin.com/in/steve-hoenisch-4092344b?trk=profile-badge'>Steve Hoenisch</a></div>





