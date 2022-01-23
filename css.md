# Questions
- [Why CSS is important?](#Q1)
- [What do you mean by metatag? And why initial value =1.0 written?](#Q2)
- [Units in CSS. Difference between absolute, relative, and fixed.](#Q3)
- [Explain CSS pseudo-selectors, pseudo-classes and pseudo-elements.](#Q4)
- [What are media queries and explain them in detail.](#Q5)
- [Explain box-model.](#Q6)
- [Difference between transition and transform property in CSS.](#Q7)
- [What is Mobile-First Approach and Desktop First approach and which one you follow and why?](#Q8)
- [Write a piece of code to center div.](#Q9)
- [How we can achieve smooth scrolling?](#Q10)
- [What is specificity in CSS? Explain in detail.](#Q11)
- [What is a responsive web design and adaptive web design.](#Q12)
- [What is flexbox and explain their properties.](#Q13)
- [Difference between justify-content vs align-items.](#Q14)
- [Difference between id and class selectors.](#Q15)
- [How will you decide when to use a button or tag?](#Q16)
- [What are some of the things you would test while doing accessibility testing?](#Q17)
- [Make a bouncing ball entirely with help of CSS.](#Q18)
- [In how many ways can CSS be integrated?](#Q19)
- [What is the difference between `visibility: hidden` and `display: none`.](#Q20)
- [How to make a triangle in css?](#Q21)
- [What are data attributes?](#Q22)
- [What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?](#Q23)
- [Describe Floats and how they work.](#Q24)
- [Describe z-index and how stacking context is formed.](#Q25)
- [What are the various clearing techniques and which is appropriate for what context?](#Q26)
- [Div property: Difference between `div p`, `div > p`, `div + p` and `div ~ p`](#Q27)
- [How font-face is used.](#Q28)

# Answers
#### Q1 
### ✍Why CSS is important? 
- CSS controls all design related aspects of a web page. Without CSS, the webpage is only a skeleton with plain texts, images, etc.
- By CSS, we add typography, styles and layouts. It makes our webpage look pretty.

**[⬆](#Questions)**
---
#### Q2
### ✍What do you mean by `meta` tag? And why initial value =1.0 written?
- The `<meta>` tag defines metadata about an HTML document. Metadata is data (information) about data.
- `<meta>` tags always go inside the <head> element, and are typically used to specify character set, page description, keywords, author of the document, and viewport settings.It is machine parsable.
- Metadata is used by browsers (how to display content or reload page), search engines (keywords), and other web services.

**[⬆](#Questions)**
---
#### Q3
### ✍Units in CSS. Difference between absolute, relative, and fixed.
There are 4 types of layouts.
- `position: static`: HTML elements are positioned static by default. top, left, right and bottom properties won’t have any effect.
- `position: relative`: places an element relative to its current position without changing the layout around it.
- `position: absolute`: places an element relative to its parent’s position and changing the layout around it.
- `position: fixed`: It is positioned relative to the viewport, which means it always stays in the same place even if the page is scrolled.

**[⬆](#Questions)**
---
#### Q4
### ✍Explain CSS pseudo-selectors, pseudo-classes and pseudo-elements.
- Pseudo Selectors are given to add some special features to elements, like `content::before`, `content::after`, `p::first-letter` etc.
- A CSS pseudo-class is a keyword preceded by a colon (:) that is added on to the end of selectors to specify that you want to style the selected elements only when they are in certain state.
e.g. `:active`, `:hover`, `:focus`, `:visited`
- Pseudo-elements are very much like pseudo-classes, but they have differences. They are keywords — this time preceded by two colons (::) — that can be added to the end of selectors to select a certain part of an element.

**[⬆](#Questions)**
---
#### Q5
### ✍What are media queries and explain them in detail.
- Media query is a CSS technique introduced in CSS3. It uses the @media rule to include a block of CSS properties only if a certain condition is true.
```css
@media only screen and (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```
**[⬆](#Questions)**
---
#### Q6
### ✍Explain box-model.
All the HTML elements can be considered as boxes. Box model wraps every HTML elements. A Box model consists of margins, borders, padding and the actual content.

**[⬆](#Questions)**
---
#### Q7
### ✍Difference between transition and transform property in CSS.
- The Transform property in CSS moves or modifies the appearance of an element, whereas the Transition property seamlessly and gently transitions the element from one state to another.
```css
#box4{
    width: 120px;
    height: 120px;
    background-color: red;
    border-radius: 12px;
    transition: all 0.7s ease;
}
#box4:hover{ transform: rotate(25deg); }
```
**[⬆](#Questions)**
---
#### Q8
### ✍What is Mobile-First Approach and Desktop First approach and which one you follow and why?
- The term Mobile-First means that when developing a website, we start writing the CSS for smaller viewport sizes first, and then use CSS media queries to alter the experience for larger ones (e.g: tablets or desktops). For Desktop First, it's the other way around.
- It is easier to simplify a Desktop First Design. But it depends on the requirements of the website whether and the user base. 

**[⬆](#Questions)**
---
#### Q9
### ✍Write a piece of code to center div.
```css
// method 1
.parent-div {
    position: relative;
}
.child-div {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

// method 2: using flex
.parent-div {
    display: flex;
    height: 100vh;
}
.child-div {
    justify-content: center;
    align-items: center;
}
```

**[⬆](#Questions)**
---
#### Q10
### ✍How we can achieve smooth scrolling?
```html
<nav>
    <ul>
        <li><a href="#first-section">First Section</a></li>
        <li><a href="#second-section">Second Section</a></li>
        <li><a href="#third-section">Third Section</a></li>
    </ul>
</nav>

<section id="first-section"></section>
<section id="second-section"></section>
<section id="third-section"></section>

<style>
html {
    scroll-behavior: smooth;
}
</style>
```
**[⬆](#Questions)**
---
#### Q11
### ✍What is specificity in CSS? Explain in detail.
- Specificity is a set of rules which browser follows to decide when encountered with ambiguous CSS styles.
- For example, if 2 divs are same styles, then the style of below div will always work.
- `id` will get preference over class. 
- `!important` will get most preference, above id or class.

**[⬆](#Questions)**
---
#### Q12
### ✍What is a responsive web design and adaptive web design.
- The responsive design will reconfigure all design elements whether it's viewed on a desktop, laptop, tablet, or mobile phone. 
- With adaptive design, different fixed layouts are created that adapt to the users screen size.
- Adaptive design is faster to load.

**[⬆](#Questions)**
---
#### Q13
### ✍What is flexbox and explain their properties.
- Flexbox Layout Model was designed as a one-dimensional layout model.
- It makes it easier to design flexible responsive layout structure without using float or positioning.
- Some of the properties are
    - `justify-content`
    - `align-items`
    - `flex-basis`
    - `flex-direction`
    - `flex-wrap`
    - `flex-grow`
    - `order`

**[⬆](#Questions)**
---
#### Q14
### ✍Difference between justify-content vs align-items.
- `justify-content` — controls alignment of all items on the main axis (horizontal).
- `align-items` — controls alignment of all items on the cross axis (vertical).

**[⬆](#Questions)**
---
#### Q15
### ✍Difference between id and class selectors.
- Class can be reused. IDs are unique.
- Classes are represented by (.) where IDs by (#).
- Normally ID take more preference than class. See specificity.

**[⬆](#Questions)**
---
#### Q16
### ✍How will you decide when to use a button or tag?
- Generally, I use `<a>` for links and navigation between page / views.
- I use `<button>` for actions, for example on the current page : validating/resetting a form, showing a modal, etc.

**[⬆](#Questions)**
---
#### Q17
### ✍What are some of the things you would test while doing accessibility testing?
- Accessibility Testing is defined as a type of Software Testing performed to ensure that the application being tested is usable by people with disabilities like hearing, color blindness, old age and other disadvantaged groups.
- We can screen readers for testing. Some of them are:
    - MAC OS - Voiceover (best with Safari)
    - Windows - JAWS, Narrator, NVDA,
    - LINUX - ORCA
    - Chromevox - Chrome Browser

**[⬆](#Questions)**
---
#### Q18
### ✍Make a bouncing ball entirely with help of CSS.
```html
<div class="bouncingball"></div>
```
```css
.bouncingball {
  width: 140px;
  height: 140px;
  border-radius: 100%;
  background: #CCC;
  animation: bounce 1s;
  transform: translateY(0px);
  animation-iteration-count: infinite;
  position: absolute;
  margin: 50px;
}
@keyframes bounce {
	0% {top: 0;
		-webkit-animation-timing-function: ease-in;
	}
	40% {}
	50% {top: 140px;
		height: 140px;
		-webkit-animation-timing-function: ease-out;
	}
	55% {top: 160px; height: 120px; 
		-webkit-animation-timing-function: ease-in;}
	65% {top: 120px; height: 140px; 
		-webkit-animation-timing-function: ease-out;}
	95% {
		top: 0;		
		-webkit-animation-timing-function: ease-in;
	}
	100% {top: 0;
		-webkit-animation-timing-function: ease-in;
	}
}
```

**[⬆](#Questions)**
---
#### Q19
### ✍In how many ways can CSS be integrated?
You can use the import method or you can put it in as link stylesheet.
```html
<link href="css/bootstrap.min.css" rel="stylesheet">
```
```css
@import url(“style.css”);
```
There are 3 methods as to how we can integrate CSS.
1. Inline CSS
2. Within the `<head>` tag using `<style>`.
3. Using an external stylesheet (the right way).

**[⬆](#Questions)**
---
#### Q20
### ✍What is the difference between `visibility: hidden` and `display: none`.
- `visibility: hidden` hides the content but the space occupied by the content is there. 
- `display: none` removes the space as well.

**[⬆](#Questions)**
---
#### Q21
### ✍How to make a triangle in css?
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

**[⬆](#Questions)**
---
#### Q22
### ✍What are data attributes?
- Data Attributes store data in HTML. When you want to call the data, you can use it by CSS (using `attr`
```html
<div class="profile" data-name="amrit" data-youtube-name="rat" data-id="1">Profile</div> 
<style>
.profile:hover:before { 
    content: attr(data-name); 
    color: red; 
} 
</style>
```

**[⬆](#Questions)**
---
#### Q23
### ✍What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?
- Reset will remove all the default styles applied by the browser to give you a blank canvas.
- Normalize will keep the styles of the default elements consistent across the browsers.

**[⬆](#Questions)**
---
#### Q24
### ✍Describe Floats and how they work.
- The `float` property is used for positioning and layout on web pages. Normally it is used to wrap text around images.
- But you need `clear` property after using `.float`.
- If an element is taller than the element containing it, and it is floated, it will overflow outside of its container. So, I use the `.clearfix` class to remove the float.

**[⬆](#Questions)**
---
#### Q25
### ✍Describe z-index and how stacking context is formed.
- The z-index property specifies the stack order of an element. An element with greater stack order is always in front of an element with a lower stack order.
`z-index: 9999;`
- Note: z-index only works on positioned elements (position:absolute, position:relative, or position:fixed).

**[⬆](#Questions)**
---
#### Q26
### ✍What are the various clearing techniques and which is appropriate for what context?
- You can use `clear: both`
- You can use overflow property like `overflow: auto;`
- `.clearfix` can also be used

**[⬆](#Questions)**
---
#### Q27
### ✍Div property: Difference between `div p`, `div > p`, `div + p` and `div ~ p`
Syntax | Meaning
------------ | -------------
div p | Selects all `p` elements that are anywhere inside a `div` element
div > p | Selects all `p` elements where the immediate parent is a `div` element
div + p | Selects all `p` elements that are placed immediately after a `div` element
div ~ p | Selects all `p` elements that are anywhere preceded by a `div` element

**[⬆](#Questions)**
---
#### Q28
### ✍How font-face is used.
```css
@font-face {
    font-family: myFirstFont;
    src: url(sansation_light.woff);
    Font-weight: bold;
}
```

**[⬆](#Questions)**
---

