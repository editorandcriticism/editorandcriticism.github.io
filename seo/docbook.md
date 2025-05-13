---
author: By Steve Hoenisch
description: |
    Mark up your DocBook XML to generate HTML metadata for search engine
    optimization (SEO).
keywords: |
    DocBook SEO, DocBook SEO tips, search engine optimization with DocBook,
    tag DocBook

title: DocBook SEO
---


Tagging DocBook Documents for Search Engine Optimization
--------------------------------------------------------

DocBook includes a set of elements to tag documents for search engine
optimization, or SEO. In this article, I'll show you how to set up a
[DocBook](http://www.docbook.org/) document so the DocBook stylesheets
automatically embed metadata in the resulting HTML web page. Metadata --
the encoded information that tells a search engine what your content is
about -- is a fundamental component of optimizing a web page for
indexing by a search engine. Including metadata in the HTML header of a
web page can help improve the page's search engine ranking.

A web page that has been optimized for search engines includes three
important pieces of metadata: a title, a description, and a set of
keywords. The DocBook XSL stylesheets that transform DocBook articles
and books into HTML automatically map the title of a DocBook document to
the title tag in the HTML header of a web page, so you don't have to
worry about the title.

The description and the set of keywords, however, must be explicitly set
by including the `abstract` element and `keywords` element in your
DocBook XML file. To generate a description, the stylesheets map the
content of DocBook's `abstract` element to HTML's meta element for a
description. To generate a list of keywords, the stylesheets add each
keyword enclosed in DocBook's `keywords` element to HTML's meta element
for keywords. Thus, the key to optimizing your HTML output for SEO is to
add the `abstract` and `keywords` elements to your XML.




### Adding the Abstract Element to Your DocBook XML

To include a description in the metadata of the HTML page that you
generate from your DocBook source, you must add the `abstract` element
to your DocBook article or book. The abstract element is a child of the
`articleinfo` element, which can appear near the beginning of your book
or article. Here's an example of how to add the `abstract` element to a
DocBook article:

``` {space="preserve"}
<?xml version="1.0"?>
<!DOCTYPE article SYSTEM "/docbook-xml-4.5/docbookx.dtd">
<article>
<title>Ski Washington on a Budget</title>
<articleinfo>
<abstract>
<para>A concise overview of options available to skiers
traveling to Washington ski areas on a budget.</para>
</abstract>
</articleinfo>
```

After the code snippet above is transformed into HTML with the DocBook
XSL stylesheets, it looks like this:

``` {space="preserve"}
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>Ski Washington on a Budget</title>
<meta name="generator" content="DocBook XSL Stylesheets V1.73.0">
<meta name="description" content="A concise overview of options
available to skiers traveling to Washington ski areas on a budget.">
</head>
```

Tip: To avoid having your description cut off mid-sentence in Google's
search results (when it displays the description), a best practice is to
limit your description to no more than 156 characters and spaces.






### Adding the Keywords Element to Your DocBook XML

To include keywords in the metadata of your HTML page, you use DocBook's
`keywordset` element to encompass several `keyword` elements. Like
abstract, the `keywordset` element is also a child of the `articleinfo`
element. The `keywordset` should include a few highly relevant words
from the page's text -- terms that represent and categorize your
document's content. Here's an example of how to add keywords to a
DocBook article:

``` {space="preserve"}
<?xml version="1.0"?>
<!DOCTYPE article SYSTEM "/docbook-xml-4.5/docbookx.dtd">
<article>
<title>Ski Washington on a Budget</title>
<articleinfo>
<keywordset>
<keyword>skiing</keyword>
<keyword>budget travel</keyword>
<keyword>Washington state</keyword>
</keywordset>
</articleinfo>
```

After the keywords in the code snippet above is transformed into HTML
with the DocBook XSL stylesheets, it looks like this:

``` {space="preserve"}
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>Ski Washington on a Budget</title>
<meta name="generator" content="DocBook XSL Stylesheets V1.73.0">
<meta name="keywords" content="skiing, budget travel, 
Washington state skiing">
</head>
```

Of course, to generate both a description and keywords in the HTML, you
would want to include both an abstract and a set of keywords in your
DocBook XML, like this:

``` {space="preserve"}
<?xml version="1.0"?>
<!DOCTYPE article SYSTEM "/docbook-xml-4.5/docbookx.dtd">
<article>
<title>Ski Washington on a Budget</title>
<articleinfo>
<abstract>
<para>A concise overview of options available to skiers
traveling to Washington ski areas on a budget.</para>
</abstract>
<keywordset>
<keyword>skiing</keyword>
<keyword>budget travel</keyword>
<keyword>Washington state</keyword>
</keywordset>
</articleinfo>
```

When the DocBook stylesheets transform this snippet, both the sentence
in the abstract and the keywords are rendered in their corresponding
metadata fields in the header of the HTML, which helps optimize the web
page for search engines.

*--Steve Hoenisch*

**Related**

[Search Engine Optimization Techniques: Tips to Improve Your Search
Engine Rankings](/seo/search-engine-optimization.html)

[XC: A Minimalist, Structural DTD for XML Documents](/cc/about-xc.html)

[Dublin Core SEO](/seo/dublin-core-metadata.html)

First Published: May 18, 2010. Last Updated: May 18, 2010.

