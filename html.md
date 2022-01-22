# Questions
- [Major goals of HTML5](#Q1)
- [New features of HTML5](#Q2)
- [If you don’t specify Doctype, what will happen?](#Q3)
- [Deprecated HTML tags in HTML5](#Q4)
- [What are semantic elements and explain a few of them? What are their advantages?](#Q5)
- [What is doctype used for?](#Q6)
- [What is DOM?](#Q7)
- [DOM manipulation.](#Q8)
- [Different types of storage (local storage, session storage, cookies) and which one is the best way to store data?](#Q9)
- [Drag and drop used in HTML5](#Q10)
- [Form input types in HTML5](#Q11)
- [Datalist tag](#Q12)
- [New APIs used in HTML5](#Q13)
- [SVG and canvas](#Q14)
- [What are the different types of script tags? (async,defer)](#Q15)
- [Can a ```<section>``` contains ```<article>``` element? Can a ```<article>``` contain a ```<section>``` element?](#Q16)
- [How the browser renders HTML and CSS? Explain in detail.](#Q17)
- [What are web workers?](#Q18)


# Answers
#### Q1 
### ✍Major goals of HTML5 
- Deliver rich content(movies, graphics, etc) without additional plugins.
- Provides better semantic support for web page structure.
- Provides better cross-browser platform support.

**[⬆](#Questions)**
---
#### Q2
### ✍New features of HTML5 
- Improved support for embedding graphics, audio, and video content via the new <code>canvas</code>,`audio`, and`video` tags.
- Extensions to the JavaScript API such as geolocation and drag-and-drop as well for storage and caching.
- Introduction of “web workers”.
- Several new semantic tags (element clearly describes its meaning to both the browser and the developer) were also added to complement the structural logic of modern web applications. These include the`main`,`nav`,`article`,`section`,`header`,`footer`,  <code>form</code>,  <code>table</code> and <code>aside</code> tags.
- New form controls, such as`calendar`,`date`,`time`,`email`,`url` and`search`.

**[⬆](#Questions)**
---
#### Q3
### ✍If you don’t specify Doctype, what will happen?
New HTML5 tags will not be interpreted by browsers.

**[⬆](#Questions)**
---
#### Q4
### ✍Deprecated HTML tags in HTML5
The tags that are deprecated are the following:
- `basefont`
- `big`
- `center`
- `font`
- `s`
- `strike`
- `tt`
- `u`
- `frame`
- `frameset`
- `noframe`
- `acronym`
- `applet`
- `isindex`
- `dir`

**[⬆](#Questions)**
---
#### Q5
### ✍What are semantic elements and explain a few of them? What are their advantages? 

**[⬆](#Questions)**
---
#### Q6
### ✍What is doctype used for? 


**[⬆](#Questions)**
---
#### Q7
### ✍What is DOM? 


**[⬆](#Questions)**
---
#### Q8
### ✍DOM Manipulation


**[⬆](#Questions)**
---
#### Q9
### ✍Different types of storage (local storage, session storage, cookies)and which one is the best way to store data?
| Cookies                   | Sessions           | Localstorage  |
| ------------------------  |:------------------------:| ------------------------:|
| The storage capacity of local storage is 5MB/10MB      | The storage capacity of session storage is 5MB | The storage capacity of Cookies is 4KB |
| As it is not session-based, it must be deleted via javascript or manually | It’s session-based and works per window or tab. This means that data is stored only for the duration of a session, i.e., until the browser (or tab) is closed | Cookies expire based on the setting and working per tab and window |
| The client  can only read local storage | The client can only read local storage | Both clients and servers can read and write the cookies |
| There is no transfer of data to the server | There is no transfer of data to the server | Data transfer to the server is exist |
| There are fewer old browsers that support it | There are fewer old browsers that support it | It is supported by all the browser including older browser |

**[⬆](#Questions)**
---
#### Q10
### ✍Drag and drop used in HTML5
```js
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

**[⬆](#Questions)**
---
#### Q11
### ✍Form input types in HTML5
The new input types are:
- Time
- Date
- Datetime
- Datetime-local
- Week
- Month
- Email
- Color
- Number
- Range
- Search
- Telephone
- URL

**[⬆](#Questions)**
---
#### Q12
### ✍Datalist tag
A `<datalist>` tag can be used to create a simple auto-complete feature for a web page. 
```js
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

**[⬆](#Questions)**
---
#### Q13
### ✍New APIs used in HTML5
In HTML5 you can use many APIs. Some of them are: 
- Web Workers API
- Server-sent Events API
- WebSocket API
- Cross-document Messaging API
- Drawing
- Audio/Video
- Drag and drop
- Autofocus
- Editable
- Client-side storage
- Geolocation: `navigator.geolocation`

**[⬆](#Questions)**
---
#### Q14
### ✍SVG and canvas
- The <svg> element is a container for SVG graphics. SVG has several methods for drawing paths, boxes, circles, text, and even bitmap images.
- SVG is a language for describing 2D graphics, but <canvas> allows you to draw 2D graphics on the fly using JavaScript.
- In SVG, each drawn shape is remembered as an object. If attributes of an SVG object are changed, the browser can automatically re-render the shape.
- Canvas is rendered pixel by pixel. In canvas, once the graphic is drawn, it is forgotten by the browser. If its position should be changed, the entire scene needs to be redrawn, including any objects that might have been covered by the graphic.

**[⬆](#Questions)**
---
#### Q15
### ✍What are the different types of script tags? (async,defer)


**[⬆](#Questions)**
---
#### Q16
### ✍Can a ```<section>``` contains ```<article>``` element? Can a ```<article>``` contain a ```<section>``` element?
YES

**[⬆](#Questions)**
---
#### Q17
### ✍How the browser renders HTML and CSS? Explain in detail.


**[⬆](#Questions)**
---
#### Q18
### ✍What are web workers?
A web worker is a script that runs in the background (i.e., in another thread) without the page needing to wait for it to complete. The user can continue to interact with the page while the web worker runs in the background. Workers utilize thread-like message passing to achieve parallelism.

**[⬆](#Questions)**
---

##### What is DOM?

##### What are the different types of script tags? (async,defer)

##### DOM manipulation.

##### How the browser renders HTML and CSS? Explain in detail.
