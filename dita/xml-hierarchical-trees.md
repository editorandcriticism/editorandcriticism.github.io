---
title: Hierarchical Trees in XML
---

##### Contents

1 Internet Explorer's Structural View

2 Nodes

3 Trees in Linguistics

4 Related Pages


### 1 Internet Explorer's Structural View

Internet Explorer's old default view for an XML file displayed the document's hierarchical structure. The minus and plus signs allowed the document to be displayed as a collapsible outline -- indeed, as a collapsible tree.

To view an XML document as a collapsible tree in older versions of Internet Explorer, make sure the document does not contain a reference to an XSL stylesheet.

In XML, various concepts, most of which spring from the way we speak about trees or families, are used to express relationships within a document's hierarchical tree structure. At the base of its hierarchy, each tree has a root element, and it can be seen in Internet Explorer by clicking on the first minus sign shown in the document. From the root node stems a hierarchy of other branches and leaves. Leaves are terminal elements: They do not contain child elements.

### 2 Nodes

Each element in a tree structure is called a node. Relationships among nodes are expressed using metaphors borrowed from families: The root node, for instance, is the parent of all the other nodes, called children; together they enter into a parent-child relationship. Although a parent element can have multiple children, each child node has exactly one parent node. XML uses such constructs as parent, child, sibling, ancestor, and descendant in keywords, expressions, and functions.

### 3 Trees in Linguistics

Hierarchical trees are also frequently used to express relationships in linguistics. The following example, marked up in XML, reveals one possible hierarchical structure for the atomic syntactic elements that make up a sample sentence:

    <s>
      <np><det>The</det><n>woman</n></np>   
      <vp><v>saw</v> 
        <np><det>the</det><n>man</n>
          <pp><p>in</p>
            <np><det>the</det><n>park</n></np>
          </pp>
        </np>
      </vp>
    </s>

4 Related Pages

<i class="fa fa-file-o" aria-hidden="true"></i> [XML Page](/dita/index.html)

<i class="fa fa-search-plus" aria-hidden="true"></i> [SEO Page](/seo/index.html)

<i class="fa fa-language" aria-hidden="true"></i> [Linguistics  Page](/linguistics/)








