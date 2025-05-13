---
author: Steve Hoenisch
description: 'A magazine article that explains how to declare attributes and entities in DTDs to help develop and define XML documents.'
keywords: | 
    XML, XSL, XSLT, CSS, markup, markup strategies, XML documents, XML structuring, structuring XML documents, XHTML, content, presentation, DTD, formatting XML, XSL:FO, formatting objects 
title: Declaring Attributes and Entities in DTDs
---


This article appeared in Volume 2, Issue 10 of _XML Journal_ magazine.


### INTRODUCTION

Introductions to XML all too often ignore the power of the attribute. It gets neglected in favor of the element's ability to capture the structure of a document or the meaning of content. But in developing flexibile, reusable document models and in capturing metainformation about structure or content, the attribute's overlooked utility quickly comes into focus.

Overlooked, too, have been entities, with few introductions to XML freeing them from their shroud of mystery. They are, however, a powerful method for reusing content or code, both in documents and, as we will see, in DTDs. To help you tap the potential of attributes and entities and use them in your XML documents, this tutorial explains how to specify attributes and entities in a document type definition.

<img src="/images/xmlj_v2i10.jpg" align="right"/>



In discussing attributes and entities, this column forms the second installment in a two-column primer on creating DTDs. After a quick review of what my last column covered -- the element-specific aspects of a DTD -- I'll launch into a step-by-step tutorial that guides you through the process of defining attributes and entities, culminating in a sample DTD for resumes.


### DOCUMENT TYPE DEFINITIONS

XML, as you've probably heard before, is a metalanguage, meaning a language used to describe other languages. Examples of XML-based languages, also known as applications of XML, are XHTML, XSL-FO, DITA, and DocBook. These other languages, as it happens, can include one that you create yourself -- and a document type definition is one of the two vehicles (XML Schema being the other) for formulating the language by allowing you to express the rules that make up its grammar. A document type definition, then, lays out the underlying grammar that describes the ways data may be structured in an XML document. Or, to put it more practically, a DTD defines how tags may be applied in a given document. To do so, DTDs combine syntax and operators to form explicit rules that mainly do the following:

* Declare the elements that may appear in a document
* Describe the legal content of an element
* Specify the permissable children, if any, of each element
* Set the order in which elements must appear
* Generalize about the number of times each element may occur
* Specify the kind of data a terminal element may contain
* Declare the attributes that an element may take
* Set the datatype of an attribute's value
* Indicate whether an attribute is required or optional
* Provide an easy way to replace some characters with others or to insert additional content

Each of these tasks maps to an aspect of DTD syntax or to a DTD operator, which together form the building blocks of a DTD. In my last column, I discussed the element-specific aspects of creating a DTD, namely items 1 through 6 in the list. This column will focus on items 7 through 10: writing DTD rules for attributes and creating entities. But first, here's a compact review of what my last column addressed; most of the points in the review are elaborated on in my last column. If you're up to par on writing rules for elements, including those for mixed content, you can skip ahead to the section on attributes.


### REVIEW

Like an XML document, a DTD resides in an ASCII file, but unlike in an XML document it takes a .dtd extension (example: resume.dtd) and does not require as its first line a processing instruction with an XML declaration (`<?xml version="1.0"?>`). The declarations in a DTD may also be placed in an XML file itself, in the `<!DOCTYPE>` document type declaration; such a set of declarations is called an internal DTD subset. I'll discuss how to set up the DTD as either an internal subset or an external file near the end of this tutorial.

In a DTD, the declarations for elements, attributes, and entities are prefaced in the same way, with an opening angle bracket followed by an exclamation mark: `<!`. After the exclamation mark comes one of three keywords written in all capitals -- ELEMENT, ATTLIST, or ENTITY -- that specify the type of declaraction. The declaration keyword is followed by a rule. Let's examine the rule syntax for elements.

Say you want all the XML documents in a set of resumes to contain a root element named resume. To declare an element, you use the `<!ELEMENT>` declaration:

```
<!ELEMENT resume ANY>
```

This statement declares that the element resume may appear with, as the DTD keyword ANY indicates, any combination of text and child nodes.

The syntax of the `<!ELEMENT>` declaration is this:

```
<!ELEMENT elementName {rule}>
```

where {rule} may be replaced either by a DTD keyword in all capitals such as EMPTY or ANY, as I did above, or by a parentheses-enclosed rule with one or more child elements separated either by commas, indicating that their appearance is required in the order specified, or by a vertical bar, indicating choice.

In our example with the resume element above, the syntactic slot for the rule filled by the keyword ANY is used to describe the legal content -- a content model -- of the resume element: In this case, because I used the keyword ANY, it can by anything from child elements to text. But using the ANY does little to constrain our data, defying the purpose of a DTD, which you may recall is to make explicit the permissible relationships and associations among the data in a set of XML documents. Thus, in the rule slot where I've used the keyword ANY, better constraints can and should be put in place.

Instead of simply saying that the resume element can take any combination of child elements and text, the rule should state exactly what children the element may contain and in what order they may appear. For instance, if I determine that every resume in a set must have a root element called resume and contain contain child elements a particular order, I can specify the child elements and their ordering by placing the child elements in parentheses and seperating them by commas:

```
<!ELEMENT resume (name, contactInfo, experience, education) >
```

This DTD rule says that the resume element contains the children enclosed in parentheses. The commas in the rule stipulate that the elements must apear in the sequence in which they are listed. No other child elements or text are permitted directly under the resume node.

Such a rule, though, says little about the frequency with which each child element may appear. A set of DTD operators, called occurrence operators, lets developers generalize about the optionality and frequency of elements. If no occurrence operator is used, as in the rule above, the default is exactly one occurrence. The other occurrence operators are as follows:

* The question mark (?), which makes an element optional but nonrepeatable: the element may be used once or not at all.
* The plus sign (+), which makes an element nonoptional and repeatable: the element must be used at least once.
* The asterisk (\*), which makes an element optional and repeatable: the element may be used any number of times or not at all.

To use occurrence operators in element declarations, you append one of them as a suffix to the element you want to constrain, as I've done for the last three child elements in the following example:


```
<!ELEMENT experience (position, company, location?, task+, note*) >
```


The question mark indicates that the location element may appear once or not at all but not multiple times. The plus sign signals that the task element must appear at least once but may be reused as often as needed. The asterisk on note marks it as a a fully optional element: It may be used once, more than once, or not at all. Meantime, since neither position nor company is accompanied by an occurrence operator, they receive the default setting: They must appear in the XML document exactly once.

You can also use parentheses to nest elements within a rule and then apply any of the occurrence operators to all the elements within the nested set. Example:

```
<!ELEMENT location ((street, suite)?, city, (state, zip)?)>
```

This rule says that the (street, suite) sequence is optional but may not be repeated (note, though, that if the street element is used, so must be the suite element). Ditto with the (state, zip) sequence. The city element, however, must apear exactly once, and if the other elements are used, they must be positioned according to the order dictated by the comma-separated list.

You may also nest a choice of elements by placing them in parentheses and separating them by vertical bars instead of commas. For instance, the following rule says that the name element must contain a first name, optionally followed either by a choice of a middle name or a middle initial or by a nickname, followed by a required last name.


```
<!ELEMENT name (firstName, ( (middleName | middleInitial)? | (nickName)? )*, lastName)>
```

This can get complex quickly. For details on how to use parentheses to form complex rules, see Chapter 3, Document Type Definitions, in XML in a Nutshell, written by Elliotte Rusty Harold and W. Scott Means and published by O'Reilly.

Many narrative-oriented XML documents like books and news stories allow mixed content -- a choice of either text or child elements or a combination of both. For instance, our sample resume has an as-yet undefined element called `<task>`. The purpose of the task element is to describe what the resume's author did in a given job. This job description contains paragraphs, and the paragraphs may contain either text or child elements that themselves contain text.

For instance, within a paragraph, you may want to include tags that mark text for emphasis, set off citations, and allow you to insert a line break. Here's an example of such markup (but without the line break element):


```
<paragraph>Served as consultant for editing, electronic production, 
and desktop publishing of one financial newsletter, called 
<cite>Securities Today</cite>, and the organization, design, 
and launch of two others.</paragraph><paragraph>All three became 
<emphasis>highly successful</emphasis> publications.</paragraph>
```

To declare a rule that allows content to mix text and child elements like in the above example, you must first declare the text and then list the other elements. Each entry in the rule must be separated by vertical bars to indicate choice, and the rule itself must be marked as optional and repeatable with the asterisk occurrence operator, like this:

```
<!ELEMENT paragraph (#PCDATA | cite | emphasis | br )*>
```

PCDATA, you may recall, is XML's name for standard text. PCDATA stands for parsed character data, which includes regular text characters except `<`, &, or the sequence `]]>`. PCDATA also includes general entities, discussed below.

A DTD must declare the content model for each element used in the XML document. Since I've included the cite and emphasis elements in my content model for the paragraph element, I must also declare them. They contain only PCDATA, which, used alone, excludes other element tags:

```
<!ELEMENT cite  (#PCDATA )>
<!ELEMENT emphasis  (#PCDATA )>
```

Finally, empty elements, like my HTML-type `<br>` element in the rule for the paragraph element, may be declared using the EMPTY keyword:

```
<!ELEMENT br EMPTY>
```

This ensures that no content, whether other elements or parsed character data, may be placed within it.

Declaring mixed content can get tricky. The key is to remember these three points:

* PCDATA must be declared in the rule first.
* All the items in the rule must be separated by the vertical bar indicating choice.
* The rule must be marked as optional and repeatable with an asterisk placed outside the rule's parentheses.



### ATTRIBUTES

Now let's tackle attributes. They are declared using the ATTLIST keyword. It is followed first by the name of the element for which the attributes are being defined and then by the list of attributes themselves. For instance, here's a partial attribute declaration that specifies an attribute named version for our resume element:

```
<!ATTLIST resume version
```

In this declaration, resume is the name of the target element (the element that we are declaring the attributes for) and version is the name of the attribute. This declaration, however, is incomplete. It needs two other components before it can be completed and closed with an angle bracket. First, it needs a datatype, the simplest and most common of which is CDATA:

```
<!ATTLIST resume version CDATA
```

The CDATA datatype, which is written in all capital letters in DTDs, specifies that any regular text characters except `<`, &, or the sequence `]]>` may be used in the quoted string that makes up the attribute's value in an XML document.

Second, the declaration needs a either a default value or an attribute modifier. For simplicity, I'll complete the attribute declaration with an attribute modifier, which must be prefixed with a number sign (#) and written in capital letters:

```
<!ATTLIST resume version CDATA #REQUIRED>
```

This declaration says that the resume element contains one attribute named version whose value is some combination of regular text characters. A value for the attribute must be present, as stipulated by the #REQUIRED attribute modifier. Thus, the syntax of an attribute declaration goes like this:

```
<!ATTLIST targetElement attributeName attributeDatatype attributeModifierOrDefaultValue>
```

As the ATTLIST keyword suggests, you can define multiple attributes within an attribute declaration. The following declaration, for example, declares all three of the resume element's attributes:

```
<!ATTLIST resume version CDATA #REQUIRED
                          lastUpdated CDATA #IMPLIED
                          field (IT | training | academia) #IMPLIED >
```


In declarations, you can use whitespace to make your rules easier to read. In the above example, I've broken up the three attributes that I'm defining by placing the second two on new lines for legibility. The second line defines an attribute named lastUpdated. Its #IMPLIED attribute modifier leaves the attribute's value unspecified, with the practical implication that the attribute and its value may be either present or absent; attributes with the #IMPLIED modifier are ignored by the XML processor unless they are used as part of an element. The third line defines yet another attribute, this one named field, and uses an enumerated datatype instead of the now-familiar CDATA. An enumerated datatype contains a series of values, listed inside parentheses and separated by vertical bars indicating choice, from which only one may be used as the attribute's value in an XML document.

There are a number of other datatypes that may be used in DTDs, including the ID datatype, which is used to provide a unique element identifier. Although discussing all the attribute datatypes is beyond the scope of this tutorial, you can find out more about them in O'Reilly's XML Pocket Reference, 2nd Edition, and in the chapter on DTDs in XML in a Nutshell. To reinforce this column's introduction to DTDs, I suggest you read Chapter 5, Document Models: A Higher Level of Control, in Learning XML (O'Reilly). For advanced material on how to build industrial-strength DTDs, see David Megginson's book, Structuring XML Documents, published by Prentice Hall.



### ENTITIES

Entities are XML's popular vehicle for replacement text. They allow you to separate content from the inline portion of an XML document, store it either internally or externally, and then call it by placing in the document a reference to the entity defined in a DTD.

Entities come in a number of flavors and have a variety of uses. I will explain how to work with three of them: general entities, external parsed general entities, and parameter entities. General entities let you replace an entity with its value, as defined in an external DTD or an internal DTD subset. External parsed general entities enable you to import the entire contents of an external file into an XML document. Parameter entities, used only in DTDs, permit you to bundle frequently repeated elements forming a content model into a single value for ease of editing and reuse.

The most common general entities are those defined by the XML specification. They are simple character replacement functions that give you a way to use XML's reserved characters (`<`, `>`, `&`) as text, not markup, inside an XML document without tripping up the XML parser. If, for instance, you want to write the ampersand in a text string, you must use the general entity for it: &. As this example shows, all general entities begin with an ampersand (&) and end with a semicolon (;). The other predefined general entities, sometimes called character references, are as follows:

* Use &lt; for <
* Use &gt; for >
* Use &quot; for " inside attribute values quoted with double quotes. You do not need to use this entity in regular text.
* Use &apos; for ' inside attribute values quoted with single quotes. You do not need to use this entity in regular text.

If these look familar to you, it's because for these four characters and the ampersand, XML uses the same named entities as HTML. Since they are are predefined by XML, you do not need to declare them in your DTD. However, you can create your own character entities by declaring them in your DTD. For instance, if you have been using &nbsp; to insert a nonbreaking space into your HTML documents, you can do the same in your XML documents by declaring it as an entity in your DTD with its replacement text being the Unicode decimal format character for a nonbreaking space surrounded by the entity start and end characters of an ampersand and a semicolon:

```
<!ENTITY nbsp "&#160;">
```

This example reveals the syntax for general entity declarations:

```
<!ENTITY entityName "Replacement text">
```

When you use an entity in your XML document, remember to prefix it with an ampersand and to suffix it with a semicolon:

```
&entityName;
```

The power of the general entity makes itself apparent any time you need to reuse the same bit of content, whether text or code -- especially if it is likely to change. By using a general entity for the content, you can change it in one place, the entity declaration in the DTD, and have that change take effect every place you've used the entity in your XML documents. Say, for instance, that you're writing a software manual for a new product, and the marketing department, fickle folks that they are, have repeatedly changed the name of the product and, you believe, will probably continue to do so right up until the day the product is launched. To get around having to manually change the product name whereever it appears in all your documentation every time the marketing department changes its mind, simply declare an entity called productName (or whatever) and use it in your documentation each time you need to write out the product's name.

The same principle applies to code: General entities may contain XML markup. The markup, however, must be well formed, meaning that it must adhere to the rules of XML syntax, contain properly nested tags that do not overlap, and contain both the start and end tags for any elements used.

The ability to include markup in general entities brings us to another type of entity: external parsed general entities. They allow you to separate a chunk of content, whether code or text, into a file that is external to both the XML document where the entity is referenced and the DTD where the entity is declared. External parsed general entities can be particularly useful in working with XHTML to create XML files that will be published on the Internet. For example, if I have some standard XHTML code that I want to use as the header on every resume that I plan to publish on my XML-driven web site, I can create the XHTML code for it in a separate file, header.xml.

In the DTD, I declare the external parsed general entity as follows, depending on where the resource is located:

```
<!ENTITY header SYSTEM "header.xml">
```

or

```
<!ENTITY header SYSTEM "http://www.criticism.com/code/header.xml">
```

Instead of the replacement text found in a general entity declaration, the external parsed entity declaration uses a SYSTEM keyword and the path to and name of the file to allow the XML parser to locate the resource. It can be either a file on the local system, as in the first example, or a resource on the Internet, as in the second example.

There are a few nuances to using external parsed general entities that I haven't discussed; for more information, I suggest you read the chapter on DTDs in XML in a Nutshell (O'Reilly) by Elliotte Rusty Harold and W. Scott Means, who discuss a similar example in greater detail.


### PARAMETER ENTITIES

You can also use entities to bundle elements commonly used together in the content models of your DTD. Such entities are called parameter entites, they use have a slighly different format from general entities, and they can be used only in DTDs.

Let's return for a moment to the subject of element declarations in DTDs. Recall that in the DTD I'm constructing for resumes, I have a paragraph declaration that includes some low-level, mixed content:

```
<!ELEMENT paragraph (#PCDATA | cite | emphasis | br )*>
```

Now suppose I want to reuse these child elements for a number of other elements, such as `<note>`. Instead of writing out the rule each time for the other elements, I can declare a parameter entity containing the elements I want to group together for reuse:

```
<!ENTITY % inline "cite | emphasis | br">
```

Parameter entity declarations contain a percent sign (%) before the name of the entity. The entity's content is then listed as usual inside quotation marks. To use reuse the cite, emphasis, and br elements within the note element, all I have to do is insert an parameter entity reference in the rule portion of the declaration for the note element:

```
<!ELEMENT note (#PCDATA | %inline; )*>
```

The rule contains the paremeter entity but notice that it is referenced using a percent sign as its prefix instead of the ampersand used for general entities. Because the rule above also includes PCDATA, it must conform to the rules for mixed content discussed above.

Parameter entities, like general entities, provide a way to create a single source of content that can be repeatedly reused, reducing errors, saving keystrokes, and easing maintenance. If, for instance, I decide after creating my DTD that I also need an inline horizontal rule element called hr to be available at the same level as the line break element (br), I can simply insert it once -- in the parameter entity -- and instantly make it available everywhere in the DTD that I have used the %inline; content model. For more information about using parameter entities, see XML in a Nutshell once again.


### COMPLETING THE DTD

Let's bring the element, attribute, and entity declarations together in a sample DTD for a hypothetical set of resumes. The DTD can be placed either in a file external to our resume, which is the best choice if more than one resume will rely on the DTD, or in the XML document itself. A DTD in an XML document is called an internal DTD subset. Placing the DTD in an XML document is especially useful during the early stages of modeling the structure of your documents and making your first pass at creating a DTD for them. Note, however, that in internal DTD subsets, parameter entity references can only be used outside declarations; as such, I have not included any parameter entity references in this DTD. Finally, notice that the internal DTD subset is placed in the `<!DOCTYPE` declaration after the root element (resume) and enclosed with with square brackets ([ and ]).



### RESUME FRAGMENT WITH INTERNAL DTD SUBSET


```
<?xml version="1.0"?>
<!DOCTYPE resume [
	<!ENTITY nbsp "&#160;">
	<!ENTITY header SYSTEM "header.xml">
	<!ELEMENT resume (name, contactInfo, experience, education)>
	<!ATTLIST resume
	version CDATA #REQUIRED
		lastUpdated CDATA #IMPLIED
		field (IT | training | academia) #IMPLIED>
	<!ELEMENT name (firstName, ((middleName | middleInitial)? | (nickName)?)*, lastName)>
	<!ELEMENT firstName (#PCDATA)>
	<!ELEMENT middleName (#PCDATA)>
	<!ELEMENT middleInitial (#PCDATA)>
	<!ELEMENT nickName (#PCDATA)>
	<!ELEMENT lastName (#PCDATA)>
	<!ELEMENT contactInfo (#PCDATA)>
	<!ELEMENT education (#PCDATA)>
	<!ELEMENT experience (position, company, location?, task+, note*)>
	<!ELEMENT position (#PCDATA)>
	<!ELEMENT company (#PCDATA)>
	<!ELEMENT location ((street, suite)?, city, (state, zip)?)>
	<!ELEMENT street (#PCDATA)>
	<!ELEMENT suite (#PCDATA)>
	<!ELEMENT city (#PCDATA)>
	<!ELEMENT state (#PCDATA)>
	<!ELEMENT zip (#PCDATA)>
	<!ELEMENT task (paragraph+)>
	<!ELEMENT note (paragraph+)>
	<!ELEMENT paragraph (#PCDATA | cite | emphasis | br)*>
	<!ELEMENT cite (#PCDATA)>
	<!ELEMENT emphasis (#PCDATA)>
	<!ELEMENT br EMPTY>
]>
<resume version="1.0" lastUpdated="September 2001" field="training">
	<name>
		<firstName>Jane</firstName>
		<lastName>Doe</lastName>
	</name>
	<contactInfo>(212) 123-4567</contactInfo>
	<experience>
		<position>Editor</position>
		<company>Fictitious Financial News</company>
		<location>
			<city>New York</city>
		</location>
		<task>
			<paragraph>Served as consultant for editing, electronic 
    production, and desktop publishing of one financial 
    newsletter, called <cite>Securities Today</cite>, and the 
    organization, design, and launch of two others.</paragraph>
			<paragraph>All three became <emphasis>highly successful</emphasis> 
    publications.</paragraph>
		</task>
		<note>
			<paragraph>This was a part-time job.</paragraph>
		</note>
	</experience>
	<education/>
</resume>
```




### RELATED TUTORIALS

The tutorials in this series proceed as follows:

1.  [An Introduction to XML](xml_intro.html)
2.  [Structuring Documents in XML](structuring_docs.html)
3.  [Developing a Document Type Definition](dtd1.html)
4.  [Attributes and Entities in DTDs](dtd2.html) <i class="fa fa-check-square" aria-hidden="true"></i>
5.  [An Introduction to XSL](xsl1.html)
6.  [Using XSLT to Separate Content from Presentation](xsl2.html)




