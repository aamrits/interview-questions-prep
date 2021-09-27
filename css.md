🔸Explain CSS pseudo-selectors and pseudo-elements.

🔸What are media queries and explain them in detail?

🔸Explain box-model

🔸What is flexbox and explain their properties?

🔸Difference between transition and transform property in CSS.

🔸What is Mobile-First Approach and Desktop First approach and which one you follow and why?

🔸Units in CSS.Difference between absolute, relative, and fixed?

🔸Write a piece of code to center div.

🔸How we can achieve smooth scrolling

🔸What is specificity in CSS? Explain in detail

🔸What is a responsive web design and how we can achieve that

🔸What do you mean by metatag? And why initial value =1.0 written?

🔸Difference between justify-content vs align-items.

🔸Difference between id and class selectors

🔸How will you decide when to use a button or tag?

🔸Why CSS is important?

🔸What are some of the things you would test while doing accessibility testing?

🔸Make a bouncing ball entirely with help of CSS.

🔸In how many ways can CSS be integrated?

## How many css layouts are there?

There are 4 types of layouts.
* Static: top, left, right and bottom won’t have any effect.
* Relative
* Absolute
* Fixed

## What is box model?

All the HTML elements can be considered as boxes. Box model wraps every HTML elements. A Box model consists of margins, borders, padding and the actual content.

## What is the difference between visibility: hidden and display: none?

<code>visibility: hidden</code> hides the content but the space occupied by the content is there. <code>display: none</code> removes the space as well.

## How to integrate two separate stylesheets together?

You can use the import method or you can put it in as link stylesheet.
```css
<link href="css/bootstrap.min.css" rel="stylesheet">

@import url(“style.css”);

@font-face {
    font-family: myFirstFont;
    src: url(sansation_light.woff);
    Font-weight: bold;
}
```
There are 3 methods as to how we can integrate CSS.
1. Inline CSS
2. Within the <head> tag using <style>.
3. Using an external stylesheet (the right way).
  
## How to make a div center?

```css
.parent-div {
     position: relative;
}
.child-div {
     position: absolute;
     top: 50%;
     left: 50%;
     transform: translate(-50%, -50%);
}
```

## What are pseudo elements and pseudo class?

Pseudo Elements are given to add some special features to elements, like <code>content::before</code>, <code>content::after</code>, <code>p::first-letter</code> etc.

A CSS pseudo-class is a keyword preceded by a colon (:) that is added on to the end of selectors to specify that you want to style the selected elements only when they are in certain state.
Pseudo-elements are very much like pseudo-classes, but they have differences. They are keywords — this time preceded by two colons (::) — that can be added to the end of selectors to select a certain part of an element.


## What is specificity?

Specificity is a set of rules which browser follows to decide when encountered with ambiguous CSS styles.
For example, if 2 divs are same styles, then the style of below div will always work.
<code>id</code> will get preference over class. 
<code>!important</code> will get most preference, above id or class.

## How to make a triangle in css?

```css
.tri {
    height: 0;
    width: 0;
    border-top: 100px solid green;
    border-bottom: 100px solid transparent;
    border-right: 100px solid transparent;
    border-left: 100px solid transparent;
}
```

## What are data attributes?

Data Attributes store data in HTML. When you want to call the data, you can use it by CSS (using <code>attr</code>).

```css
<div class="profile" data-name="amrit" data-youtube-name="rat" data-id="1">Profile</div> 
<style>
.profile:hover:before { 
    content: attr(data-name); 
    color: red; 
} 
</style>
```

## What is the difference between classes and IDs in CSS?

Class can be reused. IDs are unique.
Classes are represented by (.) where IDs by (#).
Normally ID take more preference than class. See specificity.

## What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?

Reset will remove all the default styles applied by the browser to give you a blank canvas.
Normalize will keep the styles of the default elements consistent across the browsers.

## Describe Floats and how they work.

The <code>float</code> property is used for positioning and layout on web pages. Normally it is used to wrap text around images.
But you need <code>clear</code> property after using <code>float</code>.
If an element is taller than the element containing it, and it is floated, it will overflow outside of its container. So, I use the <code>.clearfix</code> class to remove the float.

## Describe z-index and how stacking context is formed.

The z-index property specifies the stack order of an element. An element with greater stack order is always in front of an element with a lower stack order.
<code>z-index: 9999;</code>
Note: z-index only works on positioned elements (position:absolute, position:relative, or position:fixed).

## What are the various clearing techniques and which is appropriate for what context?

You can use clear: both
You can use overflow property like overflow: auto;
.clearfix can also be used

## Box Model
Content, Border, Margin, Padding

## Div property
Syntax | Meaning
------------ | -------------
div p | Selects all <code>p</code> elements that are anywhere inside a <code>div</code> element
div > p | Selects all <code>p</code> elements where the immediate parent is a <code>div</code> element
div + p | Selects all <code>p</code> elements that are placed immediately after a <code>div</code> element
div ~ p | Selects all <code>p</code> elements that are anywhere preceded by a <code>div</code> element