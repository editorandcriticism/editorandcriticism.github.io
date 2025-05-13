---
author: By Steve Hoenisch
description: |
    Using the HTML heading tags -- H1 through H6 -- to reveal the
    hierarchical structure of a web page helps foster search engine
    optimization (SEO).
keywords: |
    search engine optimization headings, SEO heading, HTML heading tags, SEO
    tips, HTML headings
title: HTML Heading Tags SEO
---


Heading Sizes Reveal the Hierarchical Structure of Content to Search Engines
----------------------------------------------------------------------------

Using the HTML heading tags -- H1 through H6 -- to reveal the
hierarchical structure of a web page helps foster search engine
optimization (SEO).

A hierarchical structure that includes a main topic and discreet
subsections, all marked off by correctly sized headings, shows readers
and search engines alike what information is important and what
information provides supporting details. Readers can more easily scan
the content for the information they want, and search engines can more
accurately categorize the page's content.

You can break down the structure of a web page in different ways, but it
is, I believe, a best practice to [set the page's first heading in the
HTML H1 tag](h1.html) and then to use the H2 tag for either the
subheading or subsequent sections. If you use H2 for a subheading
directly under the H1 tag (as this page does), then H3 might become the
heading used for the subsequent sections. The point is that you want to
begin with the H1 heading at the top of the page and create a hierarchy
from the top down, with each subsequent section that is at the same
level in the hierarchy being represented by the same size heading. Each
nested subsection is headed by a smaller sized heading. The result is an
outline format that might look something like this:

``` {space="preserve"}
h1 = main page heading
 h2 = subheading under main heading
  h3 = section heading
  h3 = section heading
   h4 = subsection heading
    h5 = nested subsection heading
```

Here's an example from a table of contents that captures the outine
structure of a web page:

``` {space="preserve"}
Interpretative Procedures
in Discourse Analysis
---------------
Table of Contents 
1 Introduction 
2 Methodological Issues 
    2.1 Points of Departure 
    2.2 Methodological Determinism 
3 Pragmatic Interpretations 
    3.1 Speech Act Theory 
    3.2 Interactional Sociolinguistics 
4 Conclusion 
5 Notes 
6 Related Pages 
---------------
1 Introduction
...
```




### Example of Structuring a Web Page with Heading Tags

In the text of the web page, each section shown in the table of contents
above would have a heading level that indicates its topical depth. So,
in the running text of the page (not in the table of contents), the
headings would be marked up like this:

``` {space="preserve"}
<h1>Interpretative Procedures
in Discourse Analysis</h1>
...
<h2>1 Introduction</h2> 
<h2>2 Methodological Issues</h2> 
    <h3>2.1 Points of Departure</h3> 
    <h3>2.2 Methodological Determinism</h3> 
<h2>3 Pragmatic Interpretations</h2> 
    <h3>3.1 Speech Act Theory</h3> 
    <h3>3.2 Interactional Sociolinguistics</h3> 
<h2>4 Conclusion</h2> 
<h2>5 Notes</h2> 
<h2>6 Related Pages</h2> 
```

The sizes of the HTML headings reveals semantic hierarchy to search
engines. The h1 heading marks the highest level in the semantic
hierarchy. The h2 heading marks the second highest level in the semantic
hierarchy. The h3 heading marks the third highest level in the semantic
hierarchy, and so forth.






### Summary

``` {space="preserve"}
<h1>Most important heading, used only once, at top of page</h1> 
<h2>Second Most Important Heading Level</h2> 
<h3>Third Most Important Heading Level</h3> 
<h4>Fourth Most Important Heading Level</h4> 
```

Using the HTML heading tags to make the structure of your information
explicit and reveal the semantic hierarchy of your page's content helps
improve your web page's ranking in search engines such as Google. What's
more: It helps readers navigate through the content of your web
page. ![End Icon](/images/endbox.gif)

*-- Steve Hoenisch*

**Related**

![Document Icon](/images/docblue.gif) [For SEO, Set Your First Heading
in the H1 Tag](/seo/h1.html)

![Document Icon](/images/docblue.gif) [Include a Unique, Accurate Title
in Your HTML Document's Header](/seo/title.html)

![Document Icon](/images/docblue.gif) [Structuring Documents with
XML](/dita/structuring_docs.html)

![Document Icon](/images/docblue.gif) [Tagging DocBook XML Documents for
Search Engine Optimization](/seo/docbook.html)

![Document Icon](/images/docblue.gif) [Search Engine Optimization (SEO)
Techniques](/seo/search-engine-optimization.html)

![External Link Icon](/images/newwin.gif)  [W3C reference on the global
structure of an HTML document: The H1, H2, H3, H4, H5, H6
headings](http://www.w3.org/TR/html401/struct/global.html#h-7.5.5)

First Published: May 27, 2010. Last Updated: May 27, 2010.

