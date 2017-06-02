* [1.ABC of Programming](#abc-of-programming)
* [2.Basic Javascript](#basic-javascript)
* [3.Functions, methods, and Objects](#functions-methods-and-objects)
* [4.Decisions and Loops](#decisions-and-loops)
* [5.Document Object Model](#document-object-model)
* [6.Events](#events)
* [7.jQuery](#jquery)
* [8.Ajax and JSON](#ajax-and-json)
* [9.APIs](#apis)
* [10.Error Handling and Debugging](#error-handling-and-debugging)
* [11.Content Panels](#content-panels)
* [12.Filtering, Searching and Sorting](#filtering-searching-and-sorting)
* [13.Form Enhancement and Validation](#form-enhancement-and-validation)

# ABC of Programming

## a.What is a script and how to create one? 
A script is a series of instructions like a recipe or manuals. 
To design a script, create tasks, break them down into steps and implement into JavaScript code.

## b.How do computers fit in with the world around them?
Computers create models of the world using data.

### Objects and Properties
each object has its own:
* Properties (name, value)
* Events
* Methods

Properties are characteristics an object have. Programmers choose which event they respond to. 
Methods represent things people need to do with objects.

Web browsers are programs built using objects; Window object, Document object.

### Document
- Properties: URL, lastModified, title
- Methods: perform tasks associated the document loaded in the browser. 
  e.g. getting information from a specified element or adding new content
- Events: you can respond to events. e.g. user clicking or tapping an element

### How a browser sees a web page
JS can be used to change HTML page contents. You need to know how a browser interprets HTML code 
and applies styling to it.

1. Receive a page as HTML code
2. Create a model of the page and store it in memory
3. Use a rendering engine to show the page on screen

## c.How do I write a script for a web page?
html(content layer), css(presentation layer), javascript(behavior layer)

```html
<body>
    <h1>Constructive &amp; Co.</h1>
    <script type="text/javascript" src= "js/add-content.js"></script>
    <p>For all orders and inquiries please call <em>555-3344</em></p>
</body>
</html>
```

```javascript
/*add-content.js*/
var today = new Date();
var hourNow = today.getHours();
var greeting;
if (hourNow > 18) {
    greeting = 'Good evening!';
} else if (hourNow > 12) {
    greeting = 'Good afternoon!';
} else if (hourNow > 0) {
    greeting = 'Good morning!';
} else {
    greeting = 'Welcome!';
}
document.write('<h3>' + greeting + '</h3>');
/*object.method();*/
```

directly put script in html
```html
<script type="text/javascript">document.write('<h3>Welcome!</h3>');</script>
```

# Basic Javascript
variable, data types (number, string, boolean), array
```javascript
var a= "a";
var b = 'b';
var n = 1;
var isTrue = true; //or false
var arr= ['string', 1, false, true];
arr.length // 4
arr[0] = 'String';
```

## Operator
arithmetic operator + - / * ++ -- % boolean < > logical && || 

