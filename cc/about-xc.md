---
author: Steve Hoenisch
description: |
    This page describes a minimalist, structural document type definition
    for structuring and reusing narrative-oriented XML content. The content
    model of xc.dtd is structural, not semantic. It favors the paragraph.
keywords: |
    XML, extensible markup language, DTD, document type definition, schema,
    structured content, Dublin Core, XSLT, XSL, DITA
title: 'A Compact Document Type Definition (DTD) for Structuring XML Content'
---


**xc.dtd** is a minimalist document type definition for structuring and
reusing narrative-oriented XML content. The content model of xc.dtd is
structural, not semantic, yielding an exceptionally compact yet flexible
grammar. It favors the paragraph.

Although the DTD contains a rich set of metadata based on RDF, Dublin
Core, and Prism, the grammar minimizes and constrains the available
markup to an abstract structural set fortified with a narrow selection
of inline elements from XHTML. If output directly, the html-derived
elements and attribute sets are valid against the XHTML 1.0 Transitional
DTD, and some comply with XHTML 1.0 Strict. When XHTML elements have
been used, however, only part of the attribute sets appear, typically id
and class. For all elements, the class attribute can be mapped directly
to a CSS property in the output or display. The link module is XHTML 1.0
Transitional.

The DTD contains a migration path to DITA, but the path has not been
tested; you're on your own.

The DTD and the XSLT stylesheets are suited for embedding in PHP web
pages. In the PHP layer, you can embed your ads and other code.

Why did I write xc.dtd for my own use when I already have a fully
implemented and customized versions of DITA 1.0 and DITA 3.1.2 ? (See
e.g. http://www.criticism.com/md/crit1.xml, which uses
http://www.criticism.com/dita/dtd/topic.dtd.)

Here's why:

It's simple. Which means it's easy for others to learn easy to use. You
can use it produce large volumes of content quickly and effectively.

It's highly adaptable to different document types because it uses only a
few key abstract structures and places the metainfo about those
structures in attributes (e.g., a key structure is `contentUnit`. You
can use `contentUnit` for all the DITA information types and then just
specify the DITA type (e.g., task) in an attribute).

It uses open standards for metadata (for example: RDF, Dublin Core,
Prism).

The simple structure of the DTD means you can easily process it with
ActionScript for Flash.

It's straightforward to parse documents based on the DTD with PHP. (I
couldn't get Sabletron to parse documents validated with DITA 3.1.2
implementation, but I admittedly didn't spend much time trying to fix
it.

XC is easy to maintain and easy to process with XSLT. DITA can require
too much customization and programming for a small team, especially if
you want to get well-designed documents and web pages.

*--Steve Hoenisch*

![XML DTD icon](../images/xml.JPG) <http://www.Criticism.Com/cc/xc.dtd>


