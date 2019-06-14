---
date: 2017-01-15
title: Being Resourceful
video_id: Gc2d-eGSSdQ
description: troubleshooting 101
categories:
  - basics
resources:
  - name: "Layout documentation"
    link: https://jekyllrb.com/docs/frontmatter/
  - name: "Source code"
    link: https://github.com/CloudCannon/bakery-store/tree/layouts
type: Document
set: basics
set_order: 1
---


One of the biggest parts of being a developer is being resourceful and being able to problem solve. In a learning environment it is very easy to put your hand up and just ask a mentor for help, but what happens when the real world comes? Being able to look for solutions on line will not only allow you to learn more, but also will allow you to see into the community that developers have.

## Inspect Element

Introducing the inspector. Google Chrome Inspector is going to be your best friend as a developer, it's a way to troubleshoot issues, test out styles quickly in the browser and check what styles are being applied to each element. once you.

<iframe width="758" height="315" src="https://www.youtube.com/embed/1T4ZIG-7liQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Before you move forward, you should know how to:
 -  identify the HTML & CSS sections of the inspector
 -  how to 'select' an element with the inspector to investigate it's styles
 -  how to test your site responsively
 -  how to test your site on slow connections
 -  how to view the sources of a loaded website to see if external assets and files are being loaded correctly
 -  how to edit styles in the browser and then copy these styles to your website

## Troubleshooting CSS Checklist
  1.  If you can't see your changes at all in the inspection, first check that all your files saved and have you refreshed the page.
  2.  If your styles aren't appearing in the styles tab of the inspector for that particular element, then you probably have a problem with the selector. Check that your selector is accurate and that you aren't missing any curly brackets or semi-colons.
  3.  If styles are there but have a little yellow warning symbol, then there is something wrong with that property. Check the spelling (ie color not colour) and look up your CSS property reference here or in one of the resources below to check the proper format for that property ie you have written border: 1px black;but are missing the a required value and need to say border: 1px solid black;.
  4. If the styles are there but crossed out then you have a specificity problem -- check which other style is overridding it and then either remove the other style / make it less specific, or make the selector you are trying to use more specific. For example, if you had an a { ... } selector that was being overrided by nav a { ... } then you might want to target header nav a { ... }.
## Handy Resources

### HTML references:

**W3 Schools**, one of the classics and very comprehensive -- https://www.w3schools.com/cssref/

**Codecademy Glossary**, a good refresher on html with explanations -- https://www.codecademy.com/articles/glossary-html

### CSS references:

**W3 Schools**, one of the classics and very comprehensive -- https://www.w3schools.com/cssref/

**CSSReference.io**, this is a great visual guide with easy to understand language -- http://cssreference.io/

**CSS Tricks**, this is where you will find articles on how to create certain effects or designs. Handy for a browse -- https://css-tricks.com/

**Unfold the box model** -- is a visual reference that helps you to understand advanced CSS animations and transitions -- Unfold


### Games to practice CSS:

**CSS Diner**, where you move to the next level by learning advanced selectors -- http://flukeout.github.io/

**Flexbox Froggy**, where you learn to properly understand all of the flexbox properties -- http://flexboxfroggy.com/

### Best Practices & Code Standards:
If you want to know that you are writing your code in the best possible way, here's a guide on how to do it -- http://codeguide.co/
**40 best web development blogs** for inspiration -- https://www.keycdn.com/blog/web-development-blogs/
