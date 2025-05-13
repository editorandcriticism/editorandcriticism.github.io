---
description: 'Principles of separating content from presentation with XML, XSLT, CSS'
author: Steve Hoenisch
keywords: |
    XML, XSLT, CSS, markup, markup strategies, XML documents, XML
    structuring, structuring XML documents, XSLT, XHTML, content,
    presentation, DTD
title: Principles of Separating Content from Presentation
---




There are principles of separation that can be immensely useful in
building well-engineered, text-based web pages with XML, XSLT, CSS, and
HTML. An overarching objective is to use XML [to structure
content](structuring_docs.html) and XSLT and CSS to format it in a way
that minimizes redundancy and maximizes flexibility, including the
capability to repurpose content and publish it in various formats. Most
of the principles listed below are best applied to narrative-oriented
documents that will be published as white papers, technical manuals,
help files, essays, and so forth. Keep in mind that these principles are
merely a guide and that the list of exceptions is long: Your data,
purpose, audience, delivery format, and other factors will influence how
you engineer your system's own matrix of structure, metainformation,
parameters, content, and presentation.
<img src="/images/B0000667G4.jpg" align="right" />





-   **XML documents:** Strive to maximize the content that exists as
    text, not as tags, in your XML documents. In other words, content
    that you expect authors or end users to see should usually be set as
    content, not as elements or attributes. Avoid setting content as
    tags, either as elements or attributes, even if doing so comes at
    the cost of some redundancy; it's easier for content authors to work
    with content that is out in the open, not hidden as the value of
    attributes or as elements themselves. Instead, use
    [elements](dtd1.html#section-Declaring-Elements-and-their-Contents)
    to describe the structure or content of your material; use
    [attributes](dtd2.html#section-ATTRIBUTES) to capture
    metainformation about the content or its structure and to encode
    parameters that are used to process the content. Place recurring
    content, especially content that may change, such as the name of a
    product under development, in
    [entities](dtd2.html#section-ENTITIES). Shy away from placing
    formatting or styling information in your XML documents, though it
    may be expedient to include some table and image
    formatting instructions.
-   **XSLT stylesheets:** Place as much formatting information as
    possible in your XSLT stylesheet and eschew using it as a container
    for standard content. Instead, place content out in the open in your
    XML documents even if doing so comes as the expense of a
    little duplication. However, highly variable content, such as the
    date of publication and the version number, may be best placed in
    the XSLT stylesheet as entities. It may also benefit you to make
    exceptions for content that varies by audience, as in the case of
    parameterized settings used in
    internationalization. <img src="/images/0201674874.jpg" align="right" />
-   **Cascading Stylesheets,** as I mentioned above, should complement
    the XSLT stylesheet by containing as many as possible of the
    formatting code's visual styling properties.



In the examples that accompany this and later tutorials in the series,
you'll see some of these principles at work.




#### <i class="fa fa-code"></i> Related Pages



The tutorials in this series proceed as follows:



1.  [An Introduction to XML](xml_intro.html)
2.  [Structuring Documents in XML](structuring_docs.html)
3.  [Developing a Document Type Definition](dtd1.html)
4.  [Attributes and Entities in DTDs](dtd2.html)
5.  [An Introduction to XSL](xsl1.html)
6.  [Using XSLT to Separate Content from Presentation](xsl2.html)


