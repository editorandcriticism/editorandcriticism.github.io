---
author: By Steve Hoenisch
description: |
    How to embed Dublin Core metadata in a web page to provide a
    standards-based approach to search engine optimization (SEO) that
    complements HTML metadata.
keywords: |
    seo dublin core, seo dublin core tips, search engine optimization with
    dublin core
title: SEO with Dublin Core
---


Using Dublin Core Metadata for Search Engine Optimization
---------------------------------------------------------

Embedding Dublin Core metadata elements in your web pages provides a
standards-based approach to search engine optimization that complements
your HTML metadata. The [Dublin Core Metadata
Initiative](http://dublincore.org/) is a set of online metadata
standards for a broad range of purposes, including semantic tagging to
help search engines match requests with relevant results. Because Dublin
Core metadata is based on a standard developed by an open organization,
embedding Dublin Core metadata in every web page is, in my opinion, a
best practice. After briefly discussing the pros and cons of using
Dublin Core, this page shows you how to embed DC metadata elements in
XML, XHTML, and HTML pages.

Although most major search engines probably do not, at present, assign
much weight to Dublin Core metadata, the benefits of using it exceed the
cost. The cost is low: taking the time to add it to every web page -- a
process that you can easily automate by using your HTML metadata to
generate your Dublin Core metadata. Some web developers argue that DC
metadata increases code bloat, but this point is tenuous: Most web pages
have so much junk code in them that the addition of a small DC block is
trivial.

The benefits:

-   Prepares your web pages for a future in which search engines begin
    to use it.
-   Helps prepare your web pages for the evolution of the semantic web
    -- a world in which the semantics of information and services on the
    web is defined, making it possible for the web to recognize and
    fulfill requests for content by people and machines. For more
    information, on the semantic web, see
    <http://en.wikipedia.org/wiki/Semantic_Web>.
-   Used with XML and RDF, helps foster semantic publishing, which may
    be advantageous to scientific publishers; for more information, see
    <http://en.wikipedia.org/wiki/Semantic_publishing>.
-   Lends support to open standards and builds momentum for them.
-   Helps several internal search engines process and
    retrieve information.
-   Might help with your SEO efforts now.

Here's a hypothesis: Given the previous abuse of keywords in HTML
metadata, major search engines such as Google give weight to HTML
keywords only if they represent and categorize, with exacting relevance,
the content of the page. That is, the keywords are parsed as relevant
and used only if they also appear in the page's content, title,
description, and so forth. Perhaps using Dublin Core metadata keywords
that exactly match the HTML keywords and the page's content bolster the
weight given to the HTML keywords because the DC metadata keywords lay a
foundation of *standards-based credibility*. Such a hypothesis must, of
course, be confirmed by empirical testing, which should be the
cornerstone of any approach to search engine optimization.

It's easy to add Dublin Core HTML metadata elements to the HTML header
of your page; you simply place the elements within the `<head>` element
just after your usual HTML metadata. The HTML format of Dublin Core
metadata looks like this:

``` {space="preserve"}
<head>
   <link rel="schema.DC" href="http://purl.org/dc/elements/1.1/">
    <meta name="DC.title" content="SEO with Dublin Core">
    <meta name="DC.description" content="How to embed 
     Dublin Core metadata in a web page to provide a 
     standards-based approach to search engine optimization 
     (SEO) that complements HTML metadata.">
    <meta name="DC.subject" content="seo dublin core, 
     seo dublin core tips, search engine optimization 
     with dublin core">
    <meta name="DC.language" scheme="ISO639-1" content="en">
    </head>
    
```

With XML, you can include Dublin Core metadata in several ways. Here's
an example with a DTD -- <http://www.criticism.com/cc/xc.dtd> -- that I
use for some of the pages on Criticism.com. The structure embeds the
Dublin Core metadata elements in Resource Description Format (RDF) and
extends the `dc:subject` element with Prism Controlled Vocabulary (PCV)
to encapsulate keywords from a taxonomy:

``` {space="preserve"}
<rdf:RDF>
 <rdf:Description>
  <dc:title>SEO with Dublin Core</dc:title>
  <dc:description>
    Embedding Dublin Core metadata elements
    in your web pages provides a standards-based approach
    to search engine optimization that complements 
    HTML metadata. This page shows you how to embed DC 
    metadata elements in XML, XHTML, and HTML pages.
  </dc:description>
  <dc:subject>
   <pcv:Descriptor rdf:about="Taxonomy.xml">
    <pcv:label>search engine optimization</pcv:label>
    <pcv:label>Dublin Core metadata</pcv:label>
    <pcv:synonym>SEO</pcv:synonym>
   </pcv:Descriptor>
  </dc:subject>
 </rdf:Description>
</rdf:RDF>
```

Below is another example in XML, this time using NASA's simple DTD for
an RDF-compliant metadata format. "This format is not an offical NASA
standard," NASA says. "Instead, it is a recommendation from the NASA
Taxonomy Project on what a NASA standard metadata format might look
like." For more information or to download the NASA DTD, see
<http://nasataxonomy.jpl.nasa.gov/fordevelopers/>.

``` {space="preserve"}
<rdf:RDF>
 <ntmr:Item>
  <dc:title>Dublin Core SEO</dc:title>
  <dc:description>How to use Dublin Core 
   metadata to improve search engine rankings.
  </dc:description>
 </ntmr:Item>
</rdf:RDF>
```

The format for XHTML is slightly different, as the following example
demonstrates. As with HTML, you place the XHTML Dublin Core metadata in
the header of your web page just after your usual metadata. This code
snippet was automatically generated with the Dublin Core metadata
generation engine at
<http://webposible.com/utilidades/dublincore-metadata-gen/index.html?lang=en>:

``` {space="preserve"}
<link rel="schema.DC" href="http://purl.org/dc/elements/1.1/" />
    <meta name="DC.title" content="SEO with Dublin Core" />
    <meta name="DC.description" content="How to embed Dublin 
     Core metadata in a web page to provide a standards-based 
     approach to search engine optimization (SEO) that 
     complements HTML metadata." />
    <meta name="DC.subject" content="Dublin Core SEO" />
    <meta name="DC.language" scheme="ISO639-1" content="en" />
```

*--Steve Hoenisch*

**Related**

[Search Engine Optimization Techniques: Tips to Improve Your Search
Engine Rankings](/seo/search-engine-optimization.html)

[XC: A Minimalist, Structural DTD for XML Documents](/cc/about-xc.html)

[Developing a DTD](/dita/dtd2.html)

[Using Data Structure Standards to Foster Efficiency and
Opportunity](/dita/dss.html)

First Published: July 12, 2009. Last Updated: July 12, 2009.

