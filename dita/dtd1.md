---
author: Steve Hoenisch
description: 'A magazine article that explains how to develop a DTD to define the structure of an XML document.'
keywords: | 
    XML, XSL, XSLT, CSS, markup, markup strategies, XML documents, XML structuring, structuring XML documents, XHTML, content, presentation, DTD, formatting XML, XSL:FO, formatting objects 
title: 'Getting into DTD Development Mode'
---

This article appeared in Volume 2, Issue 8 of _XML Journal_ magazine. Last updated on July 10, 2004.


### Introduction

No, the abbreviation DTD is not related to a similar one from medical science: DTs, or delirium tremens, a violent delirium with tremors induced by overconsumption of alcohol. Though in absorbing the intricacies of DTDs and trying to develop your first one, you may begin to wonder whether the two terms are, after all, somehow connected. Even if you've mastered the basic syntax of XML, writing your first document type definition can be brow-ruffling, not in the least because DTD syntax is different from that of XML. This tutorial aims to ease you into DTD development mode without, I hope, giving you a headache, let alone DTs or anything else of the sort.

That said, you will no doubt need to read and study the cited references -- and create a DTD or two on your own -- before fully understanding the many nuances of DTDs. To launch you on the way to a complete understanding of DTDs, this month's column and next month's will explain what document type definitions do and how they do it by guiding you step by step through the development of one for a hypothetical resume. This tutorial, however, is by no means a complete introduction to DTDs; instead, it seeks to get you started, to familiarize you with DTDs, and to point you in the right direction to get more information. After reading and studying this column and the resources to which I refer you, you should be ready to begin creating DTDs for your own XML publishing projects.


<img src="/images/xmlj_v2i8.jpg" align="right"/>





### Constraining Data with Rules

A document type definition lays out the underlying rules that constrain the data in an XML document, much like grammar supplies the tacit rules by which we concatenate words into sentences. To constrain XML data, a DTD combines syntax and operators, all explained below, to form explicit rules that principally do the following:

* Declare the elements that may appear in a document
* Describe the legal content of an element
* Specify the permissable children, if any, of each element
* Set the order in which elements must appear
* Generalize about the number of times each element may occur
* Specify the kind of data a terminal element may contain
* List the attributes that an element may take
* Indicate whether an attribute is required or optional
* Provide an easy way in the form of entities to substitute some characters for others.

Each of these tasks maps to an aspect of DTD syntax or to a DTD operator, which together form the building blocks of a DTD. Next month, I will address attributes, entities, and some of the more advanced aspects of DTDs. This month we'll look at the element-specific tasks and bring them to bear on a hypothetical resume.


### Proconstruction Analysis

Once you've analyzed a representative subset of the documents in your document set, diced them up into a suitable level of structured detail, defined your markup strategy as well as your tags and attributes, and applied them to several documents in your set (see last month's tutorial for more information), you're ready to begin creating your DTD, beginning what will no doubt be an iterative process.

You can create a DTD in one of two ways: Write it from scratch, by hand, as I'll do below, using a text editor like UltraEdit. Or, you can make use of a DTD-creation tool. XML Authority, available from TIBCO Extensibility at http://www.extensibility.com/solutions/trial.htm, simplifies DTD construction. And it checks for errors, too, a few of which you'll probably make in your first DTD. It also has a useful help section on best practices.



### Declaring Elements and their Contents

Let's say we want all the resumes in a set of them to contain the root element resume. To declare an element, you use the `<!ELEMENT>` declaration. Thus, to declare the resume element in the DTD, write

```
<!ELEMENT resume ANY>
```

This statement declares that the element resume may appear with, as the DTD keyword ANY indicates, any combination of text and child nodes. The syntax of the `<!ELEMENT>` declaration is this:

```
<!ELEMENT elementName {rule}>
```

where {rule} may be replaced either by a DTD keyword in all capitals like ANY or EMPTY or by a parentheses-enclosed rule with one or more child elements separated either by commas, indicating that their appearance is required in the order specified, or by a vertical bar, indicating choice. Don't panic; I'll show you examples of all this below.

In our example with the resume element above, the syntactic slot for the rule filled by the keyword ANY is used to describe the legal content -- a content model -- of the resume element: In this case it can by anything from child elements to text. But using the ANY does little to constrain our data, defying the purpose of our DTD, which is to make explicit the permissible relationships and associations among the data in a set of XML documents. Thus, in the rule slot where I've used the keyword ANY, better constraints can and should be put in place. Instead of simply saying that the resume element can take any combination of child elements and text, let's state exactly what children it may contain.



### Specifying Children and Setting their Order

After analyzing and marking up a couple of resumes in the document set, I've settled on a firm high-level structure for the content for all the resumes I'm collecting for publication on a web site. The high-level structure of each resume will be the same and must conform to a set pattern: Every resume will have a root element called resume which will contain the following child elements in the following order: name, contactInfo, experience, education. Thus, in an XML document, I will structure the resume's high-level data like this:

```
<resume>
   <name>...</name>
   <contactInfo>...</contactInfo>
   <experience>...</experience>
   <education>...</education>
</resume>
```

To make this grammar explicit, I specify the child elements and their ordering with the following multiple sequence:

```
<!ELEMENT resume (name, contactInfo, experience, education) >
```

This DTD rule says that the resume element contains the children enclosed in parentheses. The commas in the rule stipulate that the elements must apear in the order in which they are listed. No other child elements or text are permitted directly under the resume node. Such a rule, when related to the XML document in which the elements occur, is called a content model.



### Generalizing About Optionality and Frequency

A set of DTD operators, called occurrence operators, allows authors to generalize about the optionality and frequency with which elements may occur. If no occurrence operator is used, the default is exactly one occurrence. The table titled Occurrence Operators summarizes the occurrence operators and the rule each one implements.


**Occurrence Operators**


_Operator -- Rule_


\* Optional and repeatable -- the element may be used any number of times or not at all.

\+ Nonoptional and repeatable -- the element must be used at least once.

\? Optional but nonrepeatable -- the element may be used once or not at all.


No Operator	Nonoptional and nonrepeatable (default setting) -- the element must appear exactly once.



Now let's say we want the `<experience>` element in our resume to have the following structure:

```
<experience>
     <position></position>
     <company></company>
     <location></location>
     <task></task>
     <note></note>
</experience>
```

`<position>` and `<company>` are both mandatory elements and must appear in each resume in our set once and only once. `<location>`, however, may appear once or not at all but not multiple times. Meantime, `<task>` must appear at least once but may be reused as often as needed. `<note>` is a fully optional element to add any additional information that isn't captured in the other elements: It may be used once, more than once, or not at all. To instill these rules about occurrence into your content model for the element `<experience>`, you append the occurrence operator as a suffix to the appropriate element, as the following example shows:


```
<!ELEMENT experience (position, company, location?, task+, note*) >
```

Since neither `<position>` nor `<company>` are followed by an occurrence operator, they receive the default setting: They must appear in the XML document exactly one time.


### Nesting with Parentheses

You can also use parentheses to nest elements within a rule and then apply any of the occurrence operators to all the elements within the nested set. Examples:

```
<!ELEMENT location ((street, suite)?, city, (state, zip)?)>
```

This rule says that the (street, suite) sequence is optional but may not be repeated (note, though, that if the street element is used, so must be the suite element). Ditto with the (state, zip) sequence. The city element, however, must apear exactly once, and if the other elements are used, they must be positioned according to the order dictated by the comma-separated list.

By the way, you can also nest a choice of elements by placing them in parentheses and separating them by vertical bars instead of commas. For instance, the following rule says that the name element must contain a first name, optionally followed either by a choice of a middle name or a middle initial or by a nickname, followed by a required last name.

```
<!ELEMENT name (firstName, ( (middleName | middleInitial)? | (nickName)? )*, lastName)>
```

Yes, this can get complex quickly. Since I don't want to bore you to death with needless complications, I'll stop with all this nesting balderdash and instead point you to a reference that explains in more detail how to use parentheses to form complex rules: Chapter 3, Document Type Definitions, in XML in a Nutshell, written by Elliotte Rusty Harold and W. Scott Means and published by O'Reilly.


### Mixing Content

The guts of many narrative-oriented XML documents like software manuals, essays, or magazine articles use mixed content -- a choice of either text or elements or a combination of both. For instance, our sample resume has an as-yet undefined element called `<task>`, the contents of which aim to describe what the resume's author did in any given job. Here's an example of the kind of description that would go inside our `<task>` tag, with additional markup:

```
<task>Served as consultant for editing, electronic production, and desktop publishing 
of one financial newsletter, called <cite>Securities Today</cite>, and the organization, 
design, and launch of two others. 
<paragraph>All three became <emphasis>highly successful</emphasis> 
publications.</paragraph></task>
```

Within the task element, then, the resume's author could have any combination of text as well as the `<cite>`, `<paragraph>`, and `<emphasis>` tags. Though not used in the task description, let's also make a line-break element, named `<br>` like in HTML, available.

To declare a rule that allows mixed content like this, you must first declare the text and then list the other elements, all separated by vertical bars to indicate choice and marked as optional and repeatable with the asterisk occurrence operator. Here's the rule:

```
<!ELEMENT task  (#PCDATA | paragraph | cite | emphasis | br )*>
```

`#PCDATA?` PCDATA is XML's name for standard text (though I'm oversimplifying a bit). PCDATA stands for parsed character data, which includes regular text characters except <, &, or the sequence ]]>. PCDATA also includes general entities, which I'll discuss in next month's column.

Because a DTD must declare the content model for each element used in the XML document, our DTD must include declarations for the paragraph, cite, emphasis, and br elements. With the exception of the `<paragraph>` and `<br>` element, they contain only PCDATA, which, used alone, excludes other element tags. Thus:

```
<!ELEMENT paragraph  (#PCDATA | cite | emphasis)*>
<!ELEMENT cite  (#PCDATA )>
<!ELEMENT emphasis  (#PCDATA )>
```

Finally, empty elements, like my HTML-like `<br>` element in the rule for `<task>` above, may be declared using the EMPTY keyword:

```
<!ELEMENT br EMPTY>
```

This ensures that no content, whether other elements or parsed character data, may be placed within it.

Declaring mixed content can get tricky. The key is to remember that if it includes PCDATA, then PCDATA must be declared first. And all the items in the rule must be separated by the vertical bar indicating choice and the rule must be marked as optional and repeatable with an asterisk. For more of the nasty little details about mixed content, see XML in a Nutshell's chapter on DTDs.

If you want to dive straight into a full course on DTDs, David Megginson's book, Structuring XML Documents, published by Prentice Hall, explains all the nuances of building industrial-strength DTDs. For a concise introduction to DTDs, see Robert Eckstein's XML Pocket Reference, published by O'Reilly; I suggest you read its short but potent section on DTDs several times.

#### 8.1 Resume Fragment with Internal DTD Subset

```
<?xml version="1.0" encoding="UTF-8"?>
<!-- DTD AS INTERNAL SUBSET: -->
<!DOCTYPE resume  [
<!ELEMENT resume (name, contactInfo, experience, education) >
<!ELEMENT name (firstName, ( (middleName | middleInitial)? | (nickName)? )*, lastName)>
<!ELEMENT experience (position, company, location?, task+, note*) >
<!ELEMENT location ((street, suite)?, city, (state, zip)?)>
<!ELEMENT task  (#PCDATA | paragraph | cite | emphasis | br )*>
<!ELEMENT paragraph  (#PCDATA | cite | emphasis)*>
<!ELEMENT cite  (#PCDATA )>
<!ELEMENT emphasis  (#PCDATA )>
<!ELEMENT br EMPTY>
]>
<resume>
      <name>
          <firstName>...</firstName>
          <lastName>...</lastName>
      </name>
      <contactInfo>...</contactInfo>
      <experience>
                <position>...</position>
                <company>...</company>
                <location>...</location>
                <task>
                ... <paragraph> ...
                        <cite>...</cite>
                        <emphasis>...</emphasis>
                    </paragraph>
                </task>
                <note>...</note>
      </experience>
      <education>...</education>
</resume>
```

Next month's column will offer the second installment in DTD construction, picking up where this one left off. It'll cover attributes, entities, and the more advanced aspects of working with DTDs. Meantime, begin writing a DTD for your resume by declaring its elements and the rules associated with them. Don't worry about attributes just yet. Remember, though, to declare the content for every element, as I've done above for the child elements of `<task>` (but did not do yet for many of the other elements). Next month, we'll combine all the elements and attributes into a complete DTD. 


### Related Tutorials

The tutorials in this series proceed as follows:

1.  [An Introduction to XML](xml_intro.html)
2.  [Structuring Documents in XML](structuring_docs.html)
3.  [Developing a Document Type Definition](dtd1.html)
4.  [Attributes and Entities in DTDs](dtd2.html)
5.  [An Introduction to XSL](xsl1.html)
6.  [Using XSLT to Separate Content from Presentation](xsl2.html)



