---
author: By Steve Hoenisch
description: |
    Creating an XML site map for SEO can help improve search engine
    rankings.
keywords: |
    SEO XML, XML site map, search engine optimization, SEO, XML, extensible
    markup language

title: Using XML Site Maps for SEO
---


An XML Site Map Helps Search Engines Index Web Pages
----------------------------------------------------

Creating an XML site map for SEO can contribute to improving your search
engine rankings.

As a URL inclusion protocol, an XML site map notifies search engines
about URLs on your web site that can be crawled. The map includes
information about each page in your site, such as when a page was last
updated, the frequency with which a page typically changes, and how
important a page is relative to other pages on the site. The information
in an XML site map helps optimize the way search engines crawl and index
your site.

Although an XML site map might not affect your search results on its
own, it is a technique that should be employed, among many others, in a
comprehensive SEO program. Together, all the small, detail-oriented
changes that you string together, like adding an XML site map, will have
an effect on your search engine rankings. The map helps ensure that all
the pages you list in the map get crawled.

XML site maps have come under criticism for being an overrated SEO tool.
The criticism, however, becomes valid only when you think of the maps as
being a singular method for boosting results. They are not. Again, an
XML site map is but one small and easy change that you should make to
your web site as part of your [SEO
program](http://www.criticism.com/seo/search-engine-optimization.html) --
it is the totality of all these changes that together can eventually
have a substantial impact on your natural search results.

To automatically generate an XML site map, go to
<http://www.xml-sitemaps.com/>. Here's what one looks like:

``` {space="preserve"}
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" 
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9
http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd">
    <!-- created with Free Online Sitemap Generator
    www.xml-sitemaps.com  -->
    <url>
        <loc>http://www.criticism.com/</loc>
        <priority>1.00</priority>
        <changefreq>daily</changefreq>
    </url>
    <url>
        <loc>http://www.criticism.com/map.html</loc>
        <priority>0.90</priority>
        <changefreq>daily</changefreq>
    </url>
    <url>
        <loc>http://www.criticism.com/map.html</loc>
        <priority>0.90</priority>
        <lastmod>2008-11-25T05:24:10+00:00</lastmod>
        <changefreq>daily</changefreq>
    </url>
    <url>
        <loc>http://www.criticism.com/md/weber1.html</loc>
        <priority>0.80</priority>
        <lastmod>2006-05-09T05:18:20+00:00</lastmod>
        <changefreq>monthly</changefreq>
    </url>
    <url>
        <loc>http://www.criticism.com/da/lw_da.html</loc>
        <priority>0.80</priority>
        <lastmod>2006-05-09T05:22:41+00:00</lastmod>
        <changefreq>monthly</changefreq>
    </url>
```

After the XML site map is created, name it `sitemap.xml`, and place it
in your root public HTML folder so search engines can find it.

Then, submit it to Google by using a Google webmaster account, which you
can set up at <http://www.google.com/services/>.

For more information about XML site maps, see
<http://www.sitemaps.org/>. ![End Icon](/images/endbox.gif)

*-- Steve Hoenisch*




### Related

![Document Icon](/images/docblue.gif) [Search Engine Optimization (SEO)
Techniques](/seo/search-engine-optimization.html)

![Document Icon](/images/docblue.gif) [For SEO, Set Your First Heading
in the H1 Tag](/seo/h1.html)

![Document Icon](/images/docblue.gif) [Include a Unique, Accurate Title
in Your HTML Document's Header](/seo/title.html)

![Document Icon](/images/docblue.gif) [Structuring Documents with
XML](/dita/structuring_docs.html)

![Document Icon](/images/docblue.gif) [Tagging DocBook XML Documents for
Search Engine Optimization](/seo/docbook.html)

![External Link Icon](/images/newwin.gif) <http://www.sitemaps.org/>

First Published: Oct. 7, 2011. Last Updated: Oct. 7, 2011.

