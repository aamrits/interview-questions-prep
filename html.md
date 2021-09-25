What are semantic elements and explain a few of them? What are their advantages?

🔸What is doctype used for?

🔸What is DOM?

🔸What are media queries and explain them in detail?

🔸Different types of storage (local storage, session storage, cookies)and which one is the best way to store data?

🔸Create a simple login form and add validations on the password?

🔸What are the different types of script tags? (async,defer)

🔸What is SEO? Explain steps

🔸Explain CSS pseudo-selectors and pseudo-elements.

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

🔸DOM manipulation.

🔸How will you decide when to use a button or tag?

🔸Why CSS is important?

🔸What are some of the things you would test while doing accessibility testing?

🔸Make a bouncing ball entirely with help of CSS.

🔸In how many ways can CSS be integrated?

🔸How the browser renders HTML and CSS? Explain in detail.

## Major goals of HTML5

1. Deliver rich content(movies, graphics, etc) without additional plugins.
2. Provides better semantic support for web page structure.
3. Provides better cross-browser platform support.

## New features of HTML5

* Improved support for embedding graphics, audio, and video content via the new <code>canvas</code>, <code>audio</code>, and <code>video</code> tags.
* Extensions to the JavaScript API such as geolocation and drag-and-drop as well for storage and caching.
* Introduction of “web workers”.
* Several new semantic tags (element clearly describes its meaning to both the browser and the developer) were also added to complement the structural logic of modern web applications. These include the <code>main</code>, <code>nav</code>, <code>article</code>, <code>section</code>, <code>header</code>, <code>footer</code>,  <code>form</code>,  <code>table</code> and <code>aside</code> tags.
* New form controls, such as <code>calendar</code>, <code>date</code>, <code>time</code>, <code>email</code>, <code>url</code> and <code>search</code>.

## What are web workers?

A web worker is a script that runs in the background (i.e., in another thread) without the page needing to wait for it to complete. The user can continue to interact with the page while the web worker runs in the background. Workers utilize thread-like message passing to achieve parallelism.

## Can a <section> contains <article> element? Can a <article> contain a <section> element? 

YES.

## Write the code necessary to create a 300 pixel by 300 pixel <canvas>. Within it, paint a blue 100 pixel by 100 pixel square with the top-left corner of the square located 50 pixels from both the top and left edges of the canvas.
  
```javascript
<canvas id="c" width="300" height="300"></canvas>

<script>
  var canvas = document.getElementById( "c" );
  var drawing_context = canvas.getContext( "2d" );
  drawing_context.fillStyle = "blue";
  drawing_context.fillRect( 50, 50, 100, 100 );
</script>
```
## HTML5 local storage and session storage

With HTML5, web pages can store data locally within the user’s browser.
Earlier, this was done with cookies. However, Web Storage is more secure and faster. The data is stored in name/value pairs, and a web page can only access data stored by itself. Unlike cookies, the storage limit is far larger (at least 5MB) and information is never transferred to the server.

```javascript
<script>
// Check browser support
if (typeof(Storage) !== "undefined") {
    // Store
    localStorage.setItem("lastname", "Smith");
    // Retrieve
    document.getElementById("result").innerHTML = localStorage.getItem("lastname");
} else {
    document.getElementById("result").innerHTML = "Sorry, your browser does not support Web Storage...";
}
</script>
```
The difference between localStorage and sessionStorage involves the lifetime and scope of the storage.
Data stored through localStorage is permanent: it does not expire and remains stored on the user’s computer until a web app deletes it or the user asks the browser to delete it. SessionStorage has the same lifetime as the top-level window or browser tab in which the script that stored it is running. When the window or tab is permanently closed, any data stored through sessionStorage is deleted.
 
## Geolocation API
HTML5’s Geolocation API lets users share their physical location with chosen web sites. JavaScript can capture a user’s latitude and longitude and can send it to the back-end web server to enable location-aware features like finding local businesses or showing their location on a map.

```javascript
var geolocation = navigator.geolocation;
```

## If you don’t specify Doctype, what will happen?

New HTML5 tags will not be interpreted by browsers.

## SVG and canvas

The <svg> element is a container for SVG graphics. SVG has several methods for drawing paths, boxes, circles, text, and even bitmap images.
SVG is a language for describing 2D graphics, but <canvas> allows you to draw 2D graphics on the fly using JavaScript.
n SVG, each drawn shape is remembered as an object. If attributes of an SVG object are changed, the browser can automatically re-render the shape.
Canvas is rendered pixel by pixel. In canvas, once the graphic is drawn, it is forgotten by the browser. If its position should be changed, the entire scene needs to be redrawn, including any objects that might have been covered by the graphic.

## Datalist tag
A <datalist> tag can be used to create a simple auto-complete feature for a web page.
  
```javascript
Please Select Country: <input type="text" list="countries" name="country" />  
<datalist id="countries">   
    <option value="India">India</option>   
    <option value="United States"></option>   
    <option value="United Kingdom"></option>   
    <option value="China"></option>   
    <option value="Nepal"></option>   
    <option value="Afghanistan"></option>   
    <option value="Iceland"></option>   
    <option value="Indonesia"></option>   
    <option value="Iraq"></option>   
    <option value="Ireland"></option>   
    <option value="Israel"></option>   
    <option value="Italy"></option>   
    <option value="Swaziland"></option>   
</datalist>
```

## Form input types in HTML5
The new input types are:
* Time
* Date
* Datetime
* Datetime-local
* Week
* Month
* Email
* Color
* Number
* Range
* Search
* Telephone
* URL

## Deprecated HTML tags in HTML5
The tags that are deprecated are the following:
* <code>basefont</code>
* <code>big</code>
* <code>center</code>
* <code>font</code>
* <code>s</code>
* <code>strike</code>
* <code>tt</code>
* <code>u</code>
* <code>frame</code>
* <code>frameset</code>
* <code>noframe</code>
* <code>acronym</code>
* <code>applet</code>
* <code>isindex</code>
* <code>dir</code>

## New APIs used in HTML5

In HTML5 you can use many APIs. Some of them are: 
* Web Workers API
* Server-sent Events API
* WebSocket API
* Cross-document Messaging API
* Drawing
* Audio/Video
* Drag and drop
* Autofocus
* Editable
* Client-side storage
* Geolocation

## Drag and drop used in HTML5

```javascript
<!DOCTYPE HTML>
<html>
  <head>
    <style>
    #div1 {
        width: 350px;
        height: 70px;
        padding: 10px;
        border: 1px solid #aaaaaa;
    }
    </style>
    <script>
      function allowDrop(ev) {
          ev.preventDefault();
      }

      function drag(ev) {
          ev.dataTransfer.setData("text", ev.target.id);
      }

      function drop(ev) {
          ev.preventDefault();
          var data = ev.dataTransfer.getData("text");
          ev.target.appendChild(document.getElementById(data));
      }
    </script>
  </head>
  <body>

    <p>Drag the W3Schools image into the rectangle:</p>

    <div id="div1" ondrop="drop(event)" ondragover="allowDrop(event)"></div>
    <br>
    <img id="drag1" src="img_logo.gif" draggable="true" ondragstart="drag(event)" width="336" height="69">

  </body>
</html>
```