---
title: DITA and DocBook
---

### Presentation: A Terse Overview of DITA and DocBook

_The content in this presentation, which is from circa 2002, may be out of date._



### Contents

What Is DocBook?

What Is DITA?

DITA Details

DITA Demonstration

Resources for further Exploration

### What is DocBook?

DocBook is an OASIS standard that provides a system for writing structured documents in SGML or XML.

It is a large, robust, and easy-to-understand DTD, the main structures of which correspond to a book. There is also a small subset DTD, called simplified DocBook, for articles.

It is especially well-suited to books and papers about computer hardware and software, but not limited to them. Simplified DocBook is well-suited for shorter, article-length material.

DocBook has been widely adopted by a large community of authors and organizations.
It is supported by a number of authoring programs, including XMLMind, which you can install and play with for free (see, for instance, www.xmlmind.com).


### What Is DITA?

DITA stands for Darwin Information Typing Architecture.

Initially developed by IBM, the DITA DTD is now an OASIS standard.

DITA defines: 

* A set of document types for authoring and organizing topic-oriented information in XML.
* A set of mechanisms for combining and extending document types using a process called specialization.

DITA is best suited for writing modular, topic-oriented documents.

### DITA Basics

DITA is an architecture for creating topic-oriented, information-typed content that can be reused and single-sourced in a variety of ways.

It is also an architecture for creating new topic types and describing new information domains based on existing types and domains.

The process for creating new topic types and domains is called specialization. 

### Information Typing

Information typing is the practice of identifying types of topics that contain distinct kinds information, such as concepts, tasks, and reference information.

Information typing is part of the general authoring approach called structured writing, used across the technical writing to improve information quality.

Topics that answer different kinds of questions can be categorized as different information types.

The base topic types provided by DITA ( a generic topic, plus concept, task, and reference ) can be adopted for immediate authoring or extended through specialization. 

### Generic Topic

Concept, Task, Reference

Concept topics answer ″What is...″ questions. They include a body-level element with a basic topic structure, including sections and examples.

Task topics answer ″How do I?″ questions. They have a well-defined structure that describes how to complete a procedure to accomplish a specific goal.

Reference topics describe regular features of a subject or product, such as commands in a programming language.


### Specialization

Specialization allows the creation of specific, targeted document type definitions while still sharing common output transforms and design rules developed for more general types and domains.
For example, elementref is a specialization based on DITA's default reference topic. It is a DTD that describes a structure for documenting a schema or DTD:


Because the elementref DTD shares output transforms developed for the reference type, a new XSLT stylesheet need not necessarily be created to transform it to HTML.

### Domains

A DITA domain defines a set of elements associated with a particular subject area or authoring requirement regardless of topic type.

The elements in a domain are defined in a domain module that can be integrated with a topic type to provide access to the domain elements within the topic type structure.

DITA's default domains:

* Typographic
* Programming
* Software
* User interfaces
* Utilities

You may define your own domains.

### Transclusion Mechanism

DITA includes a transclusion mechanism that is validated under DTD processing rules: an element "can replace itself with the content of a like element elsewhere, either in the current topic or in a separate topic that shares the same content models."


Conref is stricter than XInclude: Only equivalent content can be incorporated.

If there is a mismatch between the reusing and reused element types, the reference is not resolved.
It also goes beyond standard entity reuse: It allows the reused content to be in a valid XML file with a DTD.

The upshot is that reused content gets validated at authoring time, rather than at reuse time, catching problems when they can most easily be fixed. 


### DITA Maps

DITA maps organize references to DITA topics and specify the relationships among them.

They can also serve as outlines or tables of contents for DITA deliverables and as build manifests for DITA projects.

The maps represent the architecture of an information set – the topics that are needed and their relationships to one another.

Maps describe the context in which the topics will be read – the audience, platform, or other requirements of the information set.

Maps provide a mechanism that allows DITA documents to become relatively context-free, enabling them to be more easily reused in different contexts. 


### Basic Map Elements and Attributes

Layer Provides Scalable Reuse

Maps allow scalable reuse of content across multiple contexts, including

* Defining an information architecture or online navigation
* Defining audience-specific document sets
* Defining sets of related links

The map's layer of abstraction provides a central file from which you can build, manage, and publish, with a single command, the content and navigational structures for an entire web site or a section of one.


### Key Metadata Qualification Constructs

audience attribute: The type, job, experience level, and other characteristics of the reader for the topic. The audience element can elaborate values used by audience attributes.

category element: A classification of the topic content, equivalent to both Dublin Core Coverage and 


Dublin Core Subject.

DITA's metadata attributes and elements can be used to create audience- or subject-specific document subsets from a given document set.

### Processing Maps

The DITA package includes XSLT stylesheets that enable you, with a single command, to transform all the documents referenced by a map to HTML and build a table of contents that links to all of them.

The package also includes a stylesheet for merging all the documents referenced by a map into a single DITA file. 


Authoring Software that Supports DITA

* XMetal by Blast Radius
* Epic Editor by Arbortext

### DITA Demonstration

* Specialization example: DTD element reference.
* Example document: Raw XML transformed to HTML.
* Example: DITA map.
* Example: Using map to transform all documents referenced by it and output a table of contents linking to all of them.
* Example: Merge all topics into single XML document and transform to HTML. 

### Resources for Exploration

DITA and DocBook at OASIS: https://www.oasis-open.org/specs/index.php

DITA documentation and downloads at the XML Cover Pages, hosted by OASIS: https://xml.coverpages.org/dita.html

DITA articles at IBM's developerWorks web site: https://www-128.ibm.com/developerworks/xml/library/x-dita1/

DocBook: The Definitive Guide, at https://www.docbook.org/tdg/en/html/docbook.html

DocBook.org


---

### Articles on XML

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

<i class="fa fa-file-text-o" aria-hidden="true"></i> [XC: A Minimalist, Structural DTD for XML Points Toward Markdown Documents](/cc/about-xc.html)


<i class="fa fa-file-text-o" aria-hidden="true"></i> [Review: Using XML to Separate Content from Prensentation](/dita/xsl2_code/simple_doc.html) | [PDF](https://criticism.com/dita/xsl2_code/simple_doc.pdf) <i class="fa fa-moon-o" aria-hidden="true"></i>





