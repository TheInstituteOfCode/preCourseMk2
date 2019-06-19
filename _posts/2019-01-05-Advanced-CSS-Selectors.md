---
date: 2017-01-15
title: CSS Specificity and Advanced CSS Selectors
video_id: Gc2d-eGSSdQ
description: Advanced CSS Selectors
categories:
  - basics
resources:
  - name: "Layout documentation"
    link: https://jekyllrb.com/docs/frontmatter/
  - name: "Source code"
    link: https://github.com/CloudCannon/bakery-store/tree/layouts
type: Document
set: basics
set_order: 2
---

## Cascading Style Sheet

So far we have looked at how to select elements and apply styles to them, but what if there are conflicting styles? For example if we set the ```<body>```(which includes all elements) to have a color of red, and then set the ```<h1>``` to have a color of blue, what color will the ```<h1>``` be?
Luckily when there is a conflict between instructions, CSS has rules to determine which styles to use and which to ignore. It determines in the following order:

## 1. It cascades based on specificity.

Every selector in CSS has a specificity weight. This, along with the placement in the cascade, identifies how styles will be rendered. The element type selector has the lowest specificity, then the class selector, then the ID selector. So a selector that selects a class will override one that selects an element type, and a selector that selects ID will override a conflicting one that selects based on class even if it comes later in the document.
In mathematical terms, an ID has a specificity of 100, a class / attribute / psuedo-class has a specificity of 10 and an element or pseudo-element has a specificity of 1 . Here are a few examples, the highest specificity will determine the CSS rules that are used.
So a selector that used two classes and an element selector (ie .services .body p) would have a specificity weight of 21.

<table class="editable">
<thead>
<tr>
  <td>selector</td>
  <td>value</td>
  <td>selector</td>
  <td>value</td>
</tr>
</thead>
<tbody>
<tr>
<td>p</td>
<td>1</td>
<td>a:hover</td>
<td>1+1=2</td>
</tr>
<tr>
<td>.alert</td>
<td>10</td>
<td>p::first-line</td>
<td>1+1=</td>2
</tr>
<tr>
<td>.services h1</td>
<td>10 + 1 = 11</td>
<td>div.services.featured</td>
<td>10 + 10 + 1 = 21</td>
</tr>
<tr>
<td>#profile</td>
<td>100</td>
<td>nav.selected</td>
<td>1 + 10 = 11</td>
</tr>
</tbody>
</table>

For some people it's easier to understand specificity by looking at this calculator which will tell you the numerical specificity 'value' of each selector -- <a href="https://specificity.keegan.st/" target="_blank">https://specificity.keegan.st/</a>

## 2. It cascades from top to bottom

Styles declared at the bottom of the stylesheet override styles at the top of the stylesheet.


``` css
p{
  background: orange;
  font-size: 24px;
  }
p{
  background: green;
  }
```

In this example, the paragraph elements would have a background color of green, because it comes below the background of orange and thus takes precedence in the cascade. The font size would remain 24px because there is no new font-size overriding it.


## Advanced CSS Selectors

The most commonly used advanced selectors are the child selector, the multiple selector and the qualifying selector.


<table>
<thead>
<tr>
<th>Explainer</th>
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>div p</td>
<td>Child Selector</td>
<td>looks for all p elements which are inside a div element and applies the stylying to the paragraphs. You search for a child anytime you use two selectors with a space between them</td>
</tr>
<tr>
<td>h1, h2, h3</td>
<td>Multiple Selector</td>
<td>selects all h1s and h2s and h3s</td>
</tr>
<tr>
<td>p.alert</td>
<td>Qualifier selector</td>
<td>Selects all p elements that have a class of alert. Used by having two selects next to each other without a space</td>
</tr>
<tr>
<td>nav &gt; a</td>
<td>direct child selector</td>
<td>This will select only a links that are directly inside a nav. If they were inside a list inside a nav, for example, then they wouldn't be selected.</td>
</tr>
</tbody>
</table>


The most commonly used are the child selector and the multiple selector, both help you reduce the amount of code you write. Take the child selector for example. If you wanted to select every paragraph within certain sections, you could apply a class to every one of those paragraphs. OR you could apply a class to the sections themselves (for example 'featured') and then select every paragraph inside a parent with a class of featured by using the selector ```.featured p { }```

## Psuedo Elements

<table>
<thead>
<tr>
<th>Selector</th>
<th>Example</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>::after</td>
<td>p::after</td>
<td>Insert something after the content of each <code>&lt;p&gt;</code> element</td>
</tr>
<tr>
<td>::before</td>
<td>p::before</td>
<td>Insert something before the content of each <code>&lt;p&gt;</code> element</td>
</tr>
<tr>
<td>::first-letter</td>
<td>p::first-letter</td>
<td>Selects the first letter of each <code>&lt;p&gt;</code> element</td>
</tr>
<tr>
<td>:active</td>
<td>a:active</td>
<td>Selects the active link</td>
</tr>
<tr>
<td>:empty</td>
<td>p:empty</td>
<td>Selects every <code>&lt;p&gt;</code> element that has no children</td>
</tr>
<tr>
<td>:first-child</td>
<td>p:first-child</td>
<td>Selects every <code>&lt;p&gt;</code> elements that is the first child of its parent</td>
</tr>
<tr>
<td>:first-of-type</td>
<td>p:first-of-type</td>
<td>Selects every <code>&lt;p&gt;</code> element that is the first <code>&lt;p&gt;</code> element of its parent</td>
</tr>
<tr>
<td>:focus</td>
<td>input:focus</td>
<td>Selects the <code>&lt;input&gt;, &lt;textarea&gt;, &lt;a&gt;, &lt;button&gt;</code> element that has focus</td>
</tr>
<tr>
<td>:hover</td>
<td>a:hover</td>
<td>Selects links on mouse over</td>
</tr>
<tr>
<td>:last-child</td>
<td>p:last-child</td>
<td>Selects every <code>&lt;p&gt;</code> elements that is the last child of its parent</td>
</tr>
<tr>
<td>:last-of-type</td>
<td>p:last-of-type</td>
<td>Selects every <code>&lt;p&gt;</code> element that is the last <code>&lt;p&gt;</code> element of its parent</td>
</tr>
<tr>
<td>:link</td>
<td>a:link</td>
<td>Selects all unvisited links</td>
</tr>
<tr>
<td>:not(selector)</td>
<td>:not(p)</td>
<td>Selects every element that is not a <code>&lt;p&gt;</code> element</td>
</tr>
<tr>
<td>:nth-child(n)</td>
<td>p:nth-child(2)</td>
<td>Selects every <code>&lt;p&gt;</code> element that is the second child of its parent</td>
</tr>
<tr>
<td>:nth-last-child(n)</td>
<td>p:nth-last-child(2)</td>
<td>Selects every <code>&lt;p&gt;</code> element that is the second child of its parent, counting from the last child</td>
</tr>
<tr>
<td>:nth-last-of-type(n)</td>
<td>p:nth-last-of-type(2)</td>
<td>Selects every <code>&lt;p&gt;</code> element that is the second <code>&lt;p&gt;</code> element of its parent, counting from the last child</td>
</tr>
<tr>
<td>:nth-of-type(n)</td>
<td>p:nth-of-type(2)</td>
<td>Selects every <code>&lt;p&gt;</code> element that is the second <code>&lt;p&gt;</code> element of its parent</td>
</tr>
<tr>
<td>:visited</td>
<td>a:visited</td>
<td>Selects all visited links</td>
</tr>
</tbody>
</table>

## Advanced Examples

You can also combine the advanced selectors above with the psuedo selectors.

<table>
<thead>
<tr>
<th>Example</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>.alert p:hover</td>
<td>This looks for all paragraphs inside a parent with a class of 'alert' and applies the styles to them when they are in a state of hover</td>
</tr>
<tr>
<td>a:hover, div:hover</td>
<td>This selects all a links and all divs when they are in a state of being hovered</td>
</tr>
<tr>
<td>section &gt; div:not(.featured)</td>
<td>This looks for all divs that are the direct children (not grandchildren) of a section except for those with a class of featured.</td>
</tr>
<tr>
<td>div:hover p</td>
<td>This selects any paragraph inside a div that is being hovered over</td>
</tr>
</tbody>
</table>



## Troubleshooting CSS Issues

One of the most common css issues you will face is where you have two conflicting styles in your css and the one that you want to apply is being overrided by another.

The best way to figure this out is to use the inspector. When you inspect element, in the styles pannel you will see which styles are being applied to your element. Here are the three common issues and their solutions.

## Issue #1: Incorrect Selector
If you haven't used a correct selector (ie spelling mistake, missing a space or a full stop, etc) **then you won't see the style appear in the inspector at all** when inspecting the element. Go back to your code and check that you are using the correct selector.

## Issue #2: Specificity Issue
If you can see the styles in the inspector for that element, but the styles are crossed out then it means that that are being overridden by another style. You can then adjust your selector to be more specific (or make the conflicting style less specific) to prevent the conflict.
This is a very common issue and it's the reason why when you are writing your CSS you should be careful to make sure that you are only as specific as you need to be (and why we generally avoid using ids for selectors).
