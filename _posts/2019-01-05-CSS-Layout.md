---
date: 2017-01-15
title: CSS Layout
video_id: Gc2d-eGSSdQ
description: Advanced CSS Selectors
categories:
  - basics
resources:

type: Document
set: basics
set_order: 2
---

## The Display Property

Display is CSS's most important property for controlling layout. All elements in CSS have a display of either Block or Inline by default, what’s the difference and why does that matter?

**Block level** elements take up the entire available width of the container they are in and stack on top of each other on a new line. Some examples of block level elements are ```<div>``` and ```<p>```.

**Inline** level elements take up only the width that they need for their content and fall into the normal flow of the document, lining up next to each other rather than always starting on a new line. Inline elements can be nested inside one another, but we cannot wrap a block-level element with an inline- level element. For this reason, inline elements are usually small elements, line a ```<span>``` of text or an ```<a>``` link.

Inline elements are boxes (like all elements) that behave like text. They flow left to right and top to bottom, falling down onto the next line whenever there isn’t space on the current line just like text.

We set the display property to block, inline or inline-block (which we will touch on soon) through the display property.

```CSS
img {
  display: block;
}
```

**Inline-Block** then is a mix of the properties of inline and block. They flow on the page as though they were inline elements, but preserve some of their block capabilities such as setting width and height, top and bottom margins and padding etc.

There are a couple of reasons we use inline-block. It’s helpful when you have an inline element that you want to have height or width properties, or you want to place multiple block-like elements on the same horizontal line.


<table >
<thead>
<tr>
<th>block</th>
<th>inline</th>
<th>inline-block</th>
</tr>
</thead>
<tbody>
<tr>
<td>

  - if no width set then it will fill the width of the parent
  - can have margins and/or padding
  - if no height set then it will expand naturally if its child elements
  - by default will be placed under the previous elements
  - ignores the verticle align property
</td>
<td>

- flows with the text content thus
- will not clear previous content and drop down like block elements
- is subject to white-space setting
- will not take up extra vertical space when padding and margin are added
- will ignore height and width properties
- is subject to the verticle align property  
</td>
<td>
- used to place multiple block like on the same horizontal line.
- used to have an inline element have height and width while staying Inline
- used to have an inline element have vertical padding and margin
- still has the white space issue
</td>
</tr>
</tbody>
</table>

### block/inline take:

- when trying to style links that aren't in a paragraph (like menu items or buttons) set to display: inline-block so that they will behave as expected and accept vertical margin
- images you can typically set to display: block; if you want to center using margin-auto or display: inline-block if you want to center using text-align center.
- while editing your site, try to set * { border: 1px solid #cccccc} so that you can see where every element is sitting and how much space it takes up. This will help you troubleshoot any issues. You can see in the example below that spans, images, and links are all inline elements by default that only take up as much space as the content whereas most other elements take up a whole row.




## Floats

The float property was initially designed to allow text to float around an image like in a newspaper style layout. Without any better tools to create layouts, floats became the go-to tool for web developers to create custom layouts (before Flexbox). **You will probably see floats still used in a lot of templates or existing websites, so it's good to understand how they work even though you won't often use them in your projects.**

Essentially what the float property does is remove the element from the normal flow of the page and position it to the left or right of its parent element. To float an image you just set the ‘float’ property to left or right.

```CSS
img {
    float: left;
    }
```

Float is commonly used for creating complex layouts, but because it was never designed for this there are a number of issues or bugs that can appear when using floats for this purpose.

<iframe name="cp_embed_1" src="https://codepen.io/instituteofcode/embed/xVYzOP?height=265&amp;theme-id=dark&amp;slug-hash=xVYzOP&amp;default-tab=html%2Cresult&amp;user=instituteofcode&amp;embed-version=2&amp;name=cp_embed_1" scrolling="no" frameborder="0" height="265" allowtransparency="true" allowfullscreen="true" allowpaymentrequest="true" title="CodePen Embed" class="cp_embed_iframe " style="width: 100%; overflow:hidden; display:block;" id="cp_embed_xVYzOP"></iframe>


## Gridlex

Gridlex is a framework that allows us to quickly and easily create grid layouts.Gridlex uses a 12 column grid system, where the width of each grid can be divided into twelfths. To use gridlex, we need to add a class of grid to the parent container and a class of col-? to the columns we want to create.    
```html
<div class="grid">
  <div class="col-6">

  </div>  
  <div class="col-6">

  </div>
</div>

```
<div class="grid example">
  <div class="col-6">

  </div>  
  <div class="col-6">

  </div>
</div>


## CLEARING FLOATS

Float's sister property is clear. An element that has the clear property set on it will not move up adjacent to the float like the float desires, but will move itself down past the float. Clear has four valid values. **Both** is most commonly used, which clears floats coming from either direction. **Left** and **Right** can be used to only clear the float from one direction respectively. None is the default, which is typically unnecessary unless removing a clear value from a cascade.

![example of floats and clears](/images/floats.png)

**In the codepen example above, remove the comments surrounding clear: both; property on the footer and see what happens.**
``` css
div.clear {
  clear: both;
  }
```

One of the more bewildering things about working with floats is how they can affect the element that contains them (their "parent" element). If this parent element contained nothing but floated elements, the height of it would literally collapse to nothing. This isn't always obvious if the parent doesn't contain any visually noticeable background, but it is important to be aware of.

![a demo of when there are no elements in a parent that dont have float](/images/floats-parent-collapsed.png)

**The Overflow Method** relies on setting the overflow CSS property on a parent element. If this property is set to auto or hidden on the parent element, the parent will expand to contain the floats, effectively clearing it for succeeding elements. This method can be beautifully semantic as it may not require an additional elements. Bear in mind that the overflow property isn't specifically for clearing floats. Be careful not to hide content or trigger unwanted scrollbars.
```css
div.parent-container {
    overflow: hidden;
    }
```
