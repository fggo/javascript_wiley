* [1. ABC of Programming](#abc-of-programming)
* [2. Basic Javascript](#basic-javascript)
* [3. Functions, methods, and Objects](#functions-methods-and-objects)
* [4. Decisions and Loops](#decisions-and-loops)
* [5. Document Object Model](#document-object-model)
* [6. Events](#events)
* [7. jQuery](#jquery)
* [8. Ajax and JSON](#ajax-and-json)
* [9. APIs](#apis)
* [10. Error Handling and Debugging](#error-handling-and-debugging)
* [11. Content Panels](#content-panels)
* [12. Filtering, Searching and Sorting](#filtering-searching-and-sorting)
* [13. Form Enhancement ad Validation](#form-enhancement-and-validation)

# ABC of Programming

## a. What is a Script and how to create one? 
To design a script : 1. Create tasks 2. Break into steps 3. Implement JavaScript code

## b. How do computers fit in with the world around them?
Computers create models of the world using data - object, property, event, method

### Objects and Properties
Object has
- properties (name-value pairs; characteristics)
- events (programmers choose which event they respond to)
- methods (represent things people need to do with objects)

```
HOTEL Object
1. reservation is made, the book Event fires.
2. it triggers makeBooking(); increases the value of the bookings property
3. value is changed to reflect the number of rooms available.

WINDOW Object has location (property)

DOCUMENT Object has URL, lastModified, title (property)
```

### Web browsers are programs built using objects
Window & Document objects

### Document Object represents an HTML page
- properties : URL, lastModified, title
- methods : perform tasks associated with the document loaded in the browser. (e.g. write(), getElementById())
- events : (e.g. load, click, keypress)

### How a browser sees a web page
JS can be used to change HTML page contents. You need to know how a browser interprets HTML code and applies styling to it. 
1. Receive a page as HTML code
2. Create a model of the page and store it in memory
3. Use a rendering engine to show the page on screen

All major browsers use a JavaScript interpreter to translate your instructions (in JavaScript) into instructions the computer can follow.

## c. How do I write a script for a web page?
HTML (content layer), CSS (presentation layer), JavaScript (behavior layer)

```html
<html>
<head></head>
<body>
	<h1>Constructive &amp; Co.</h1>
	<!--Linking to a JavaScript file from an HTML page-->
	<script src= "js/add-content.js"></script>
	<p>For all orders and inquiries please call <em>555-3344</em></p>
	
	<script type="text/javascript">document.write('<h3>Welcome!</h3>');</script>
</body>
</html>
```

### Creating a basic JavaScript
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
document.write('<h3>' + greeting + '</h3>'); /*object.method();*/
```

# Basic Javascript
Variables to store number or string
```html
<head>
	<title>Document</title>
	<link rel="stylesheet" href="c02/css/c02.css">
</head>
<body>
	<h1>Elderflower</h1>
	<div id="content">
		<h2>Custom Signage</h2>
		<div id="cost">Cost: $5 per tile</div>
		<img src="c02/images/preview.jpg" alt="Sign">
	</div>
	<script>
		var cost = 5;
		var quantity = 14;
		var total = cost * quantity;
		var el = document.getElementById('cost');
		el.textContent = '$' + total;
	</script>
</body>
```

Using quotes inside a string
```html
<body>
<h1>Elderflower</h1>
<div id="content">
	<div id="title">Special Offers</div>
	<div id="note">Sign-up to receive personalized offers!</div>
</div>
<!--<script src="c02/js/string-with-quotes.js"></script>-->
<script>
	var title = "Molly's Special Offers";
	var message = '<a href=\"c02/sales.html\">25% off!</a>';

	var elTitle = document.getElementById('title');
	var elNote = document.getElementById('note');
	elTitle.innerHTML = title;
	elNote.innerHTML = message;
</script>
</body>
```

Variables to store boolean
```html
<body>
<h1>Elderflower</h1>
<div id="content">
	<div class="message">Available:
		<span id="stock"></span>
	</div>
	<div class="message">Shipping:
		<span id="shipping"></span>
	</div>
</div>
<script>
	var inStock = true;
	var shipping = false;

	var elStock = document.getElementById('stock');
	var elShip = document.getElementById('shipping');
	elStock.className = inStock;
	elShip.className = shipping;
</script>
</body>
``` 

Variable Naming Rules
- must begin with ($, _, alphabet)
- dash(-) or period(.), comma(,) cannot be in a variable name
- case sensitive
- no keyword or reserved word can be used

Arrays
```javascript
var colors = ['white', 'green'];
var el = document.getElementById('colors');
el.textContent = colors[colors.length - 1];

colors = new Array('white', 'green');
colors[0] = 'red';
el.innerHTML = colors.item(0);
```

Variable Data Types(number, string, boolean), array(object)
```javascript
var a= "a";
var b = 'b';
var n = 1;
var isTrue = true; //or false
var arr= ['string', 1, false, true]; //new Array('a', 'b', 'c', 'd');
arr.length // 4
arr[0] = 'String';
```

Arithmetic operator + - / * ++ -- %

Boolean operator < > >= <= === !== == !=

Logical operator && || 

## Example
example.html

# Functions, methods, and Objects
```javascript
function updateMessage(myMsg){
	var el = document.getElementById('message');
	el.textContent = myMsg;
}
var msg = 'Sign up to receive our newsletter for 10% off!'
updateMessage(msg); /*call*/

/*Anonymous function (expression) assigned to a variable*/
var area = function(width, height){
	return width * height;
}
var size = area(3, 4);

/*IIFE (Immediately invoked function expressions)*/
// area will hold returned value, rather than storing the function itself
var area = (function(){
	var width =3;
	var height = 2;
	return width * height;
}() //call function immediately
);//to be interpreted as an expression
```

## Object
properties(variables) and methods(functions)
```javascript
/*1. literal notation*/
var hotel = {
	name: 'Quay',
	rooms: 40,
	booked: 25,
	gym: true,
	roomTypes: ['twin', 'double', 'suite'],
	checkAvailability: function(){
		return this.rooms - this.booked;
	}
};
var elName = document.getElementByld('hotelName');
elName.textContent = hotel.name; //Quay
var elRooms = document.getElementByid('rooms'); 
elRooms.textContent = hotel.checkAvailability(); //40

/*Access by dot notation*/
var hotelName = hotel.name;
var roomsFree = hotel.checkAvailability();

/*Access by bracket notation*/
var hotelName = hotel['name'];

/*2-1. constructor notation(creating an object)*/
var hotel = new Object();
hotel.name ='Quay';
hotel.rooms = 40;
hotel.booked = 25;
hotel.checkAvailability = function(){
	return this.rooms - this.booked;
}
var elName = document.getElementById('hotelName');
elName.textContent = hotel.name;
var elRooms = document.getElementById('rooms');
elRooms.textContent = hotel.checkAvailability();

/*updating an object*/
hotel.name = 'Park';
hotel['name'] = 'Park';

/*2-2. constructor notation (creating multiple objects)*/
function Hotel(name, rooms, booked){
	this.name = name;
	this.rooms = rooms;
	this.booked = booked;
	this.checkAvailability = function(){
		return this.rooms - this.booked;
	}
}
var quayHotel = new Hotel('Quay', 40, 25);
var parkHotel = new Hotel('Park', 120, 77);

var details1= quayHotel.name + ' rooms : ';
	details1 += quayHotel.checkAvailability();
var elHotel1 = document.getElementById('hotel1');
	elHotel1.textContent = details1;

var details2 = parkHotel .name+ ' rooms: ';
	details2 += parkHotel.checkAvailability();
var elHotel2 = document.getElementById('hotel2');
	elHotel2.textContent = details2;


/*Adding & Removing properties*/
var hotel = {
	name: 'Park',
	rooms:120,
	booked : 77
}
hotel.gym =true;
hotel.pool = false;
delete hotel.booked;

var elName = document.getElementById('hotelName');
elName.textContent = hotel.name;

var elPool = document.getElementById('pool');
elPool.className = hotel.pool; 

var elGym = document.getElementById('gym');
elGym.className = hotel.gym;
```

## this keyword
```javascript
/*A Function in global scope*/
function windowSize(){
	return [this.innerWidth, this.innerHeight]; //return default window width and height
}

/*Global variables all become properties of the default object (window)*/
var width =600; // global variable; property of the window object
var shape = {width: 300}; //object with a property
var showWidth = function(){
	document.write(this.width); // window.width; window object's width property
}
showWidth();

/*A Method of an object*/
var shape = {
	width: 600,
	height: 400,
	getArea: function(){
		return this.width * this.height; //this = shape object
	}
};

/*Function expression as an object method*/
var width =600;
var shape ={width: 300};
var showWidth = function(){
	document.write(this.width);
}
shape.getWidth = showWidth;
shape.getWidth(); //300; method of an object (shape)
```

## Built-in objects
- Browser Object Model: window -> document history location navigator screen
- Document Object Model: document -> \<html\> \<head\> \<body\>, etc.
- Global JavaScript Objects: string number boolean, date math regex

### Browser Object Model: The Window Object
property
- window.innerHeight
- window.innerWidth
- window.pageXOffset
- window.pageYOffset
- window.screenX
- window.screenY
- window.location
- window.document
- window.history
- window.history.length
- window.screen
- window.screen.width
- window.screen.height

method
- window.alert()
- window.open()
- window.print()

```javascript
/*window-object.js*/
// Create a variable called msg to hold a message that will be shown on the page
// Find the width of the browser window, and put this in the msg variable
var msg = '<h2>browser window</h2><p>width: ' + window.innerWidth + '</p>';
// Find the height of the window and add it to the msg variable
msg += '<p>height: ' + window.innerHeight + '</p>';
// Find the number of items in the browser window's history and add it to the msg variable
msg += '<h2>history</h2><p>items: ' + window.history.length + '</p>';
// Find the width of the computer screen and add it to the msg variable
msg += '<h2>screen</h2><p>width: ' + window.screen.width + '</p>';
// Find the height of the computer screen and add it to the msg variable
msg += '<p>height: ' + window.screen.height + '</p>';

// Create a variable called el to hold the element whose id attribute has a value of info
var el = document.getElementById('info');
// Write the message into that element
el.innerHTML = msg;
// Find the location of the current page and display it in an alert box
alert('Current page: ' + window.location); //window.alert(); default object, window, is implied
```

### Document Object Model: The Document Object
property
- document.title
- document.lastModified
- document.URL
- document.domain

method
- document.write()
- document.getElementById()
- document.querySelectorAll()
- document.createElement()
- document.createTextNode()

```javascript
/* document-object.js */
var msg = '<p><b>page title: </b>' + document.title + '<br />';
msg += '<b>page address: </b>' + document.URL + '<br />';
msg += '<b>last modified : </b>' + document.lastModified + '</p>' ;

var el = document.getElementById('footer');
el.innerHTML = msg;
```

### Global JavaScript Objects
String Object
```javascript
var str = 'Home sweet home ';
```

String Object property
- str.length

String Object method
- str.toUpperCase(); 'HOME SWEET HOME ' 
- str.toLowerCase(); 'home sweet home '
- str.charAt(12); 'o'
- str.indexOf('ee'); 7
- str.lastIndexOf('e'); 14
- str.split(' ') ; ['Home' , 'sweet' , 'home' , '']
- str.substring(8,14); 'et hom'
- str.trim(); 'Home sweet home'
- str.replace('me','w'); 'How sweet home '

```javascript
/* string-object.js */
// Create a variable called saying to hold the string that will be used
var saying = 'Home sweet home ';
// Create a variable called msg to hold a message that will be shown on the page
// Find the length of the string, and put this in the msg variable
var msg = '<h2>length</h2><p>' + saying.length + '</p>';
// Convert the string to uppercase and add it to the msg variable
msg += '<h2>uppercase</h2><p>' + saying.toUpperCase() + '</p>';
// Convert the string to lowercase and add it to the msg variable
msg += '<h2>lowercase</h2><p>' + saying.toLowerCase() + '</p>';
// Find the character with an index of 12 in the string and add it to the msg variable
msg += '<h2>character index: 12</h2><p>' + saying.charAt(12) + '</p>';
// Find the index number of the first instance of 'ee' in the string and add it to the msg variable
msg += '<h2>first ee</h2><p>' + saying.indexOf('ee') + '</p>';
// Find the index number of the last instance of the 'e' character in the string and add it to the msg variable
msg += '<h2>last e</h2><p>' + saying.lastIndexOf('e') + '</p>';
// Find the characters with an index number in the 8-14 range in the string and add it to the msg variable
msg += '<h2>character index: 8-14</h2><p>' + saying.substring(8, 14) + '</p>';
// Find the first instance of 'me' in the string and replace it with a 'w' character and add it to the msg variable
msg += '<h2>replace</h2><p>' + saying.replace('me', 'w') + '</p>';

// Create a variable called el to hold the element whose id attribute has a value of info
var el = document.getElementById('info');
// Write the message into that element
el.innerHTML = msg;
```

### Data Types Revisited
1. String
2. Number
3. Boolean
4. Undefined (declared, not assigned)
5. Null
6. Object (arrays and functions are objects)

Number Object method
- isNaN()
- toFixed()
- toPrecision()
- toExponential()

```javascript
// Create a variable to hold the number that will be used
var originalNumber = 10.23456;
// Create a variable to hold a message that will be shown on the page
var msg = '<h2>original number</h2><p>' + originalNumber + '</p>';
// Round the number to 3 decimal places and add it to the msg variable
msg += '<h2>3 decimal places</h2><p>' + originalNumber.toFixed(3) + '</p>';
// Round the number to a precisely 3 digits and add it to the msg variable
msg += '<h2>3 digits</h2><p>' + originalNumber.toPrecision(3) + '</p>';

// Create a variable called el to hold the element whose id attribute has a value of info
var el = document.getElementById('info');
// Write the message into that element
el.innerHTML = msg;
```

Math Object property
- Math.PI

Math Object method
- Math.round() Rounds number to the nearest integer
- Math.sqrt(n)
- Math.ceil() Rounds number up to the nearest integer
- Math.floor()
- Math.random() Generate a random number n; n>=0 && n<1

```javascript
// Create a variable to hold a random number between 1 and 10
var randomNum = Math.floor((Math.random() * 10) + 1);
// Create a variable called el to hold the element whose id attribute has a value of info
var el = document.getElementById('info');
// Write the number into that element
el.innerHTML = '<h2>random number</h2><p>' + randomNum + '</p>';
```

Date Object method
- getDate() setDate() Returns /sets the day of the month (1-31)
- getDay() Returns the day of the week (0-6)
- getFullYear() setFullYear() Returns I sets the year (4 digits)
- getHours() setHours() Returns I sets the hour (0 -23)
- getMilliseconds()  setMilliseconds() Returns I sets the milliseconds (0 - 999)
- getMinutes() setMinutes() Returns I sets the minutes (0-59)
- getMonth() setMonth() Returns/ sets the month (0-11)
- getSeconds() setSeconds() Returns I sets the seconds (0-59)
- getTime() setTime() Number of milli sec onds si n ce Ja nu ary 1, 1970, 00:00:00 UTC (Coordinated Un iver sa l Time) and a negative number for any time before
- getTimezoneOffset() Returns time zo ne offset in mins for l oca le
- toDateString () Returns "date" as a human-readable string
- toTimeString () Returns "time" as a human-readable string
- toString()

```javascript
/* date-object.js */
// Create a variable to hold a new Date object (defaults to now)
var today = new Date();
// Create a variable to hold the year this year
var year = today.getFullYear();

// Create a variable called el to hold the element whose id attribute has a value of footer
var el = document.getElementById('footer');
// Write the year into that element.
el.innerHTML = '<p>Copyright &copy;' + year + '</p>';
```

```javascript
/* date-object-difference.js */
// Create a variable to hold a new Date object (defaults to now)
var today = new Date();
// Get the year this year
var year = today.getFullYear();
// Set the date that the company was established
var est = new Date('Apr 16, 1996 15:45:55');
// Get difference between then & now in milliseconds
var difference = today.getTime() - est.getTime();
// Divide by number of milliseconds to get years
difference = (difference / 31556900000);

// Create a variable called elMsg to hold the element whose id attribute has a value of message
var elMsg = document.getElementById('message');
// Write the message into that element.
elMsg.textContent = Math.floor(difference) + ' years of online travel advice';
```

## Example
example.js example.html

# Decisions and Loops
comparison operators == != === !== (strictly equals data type and value) > < >= <=

logical operators && || !
```javascript
var score1 = 8;
var score2 = 9;
var pass1, pass2 = 6;

var minPass = (score1 >=pass1) || (score2 >= pass2);
var msg = 'Resit required : ' + !(minPass);

var el = document.getElementById('answer');
el.textContent = msg;
```

if statement
```javascript
var score = 75;
var msg = '';
function congrats() {msg += 'Congratulations you passed!';}
function encourage() {msg += 'next time...';}
if(score >= 50){
	congrats();
	msg += 'Proceed to the next Round!';
}
else{
	encourage();
}
var el = document.getElementById('answer');
el.innerHTML = msg;
```

switch statement
```javascript
var msg;
var level = 2;
switch(level){
case 1:
	msg = 'Good luck';
	break;
case 2:
	msg = 'Second stage... keep going!';
	break;
case 3:
	msg = 'Final Round! almost there!'
	break;
default:
	msg = 'Good luck!'
	break;
}
```

Type coercion & Weak Typing
```javascript
'1' > 0; // true
'ten'/2; // NaN

//weak typing: data types can change without specifying data type
```

Truthy & Falsy values
```javascript
/*Falsy Values*/
var val1 = false; //Boolean false
var val2 = 0; //number zero
var val3 = ''; //Empty Value
var val4 = 10/'score'; //NaN
var val5; //no assigned value 

/*Truthy Values*/
val1 = true; //Boolean true
val2 = 1; //number one
val3 = 'carrot'; //string with content
val4 = 10/5; //Number calculations
val5  = 'true'; //true written as a string
val6  = '0'; //zero written as a string
val7  = 'false'; //falsewritten as a string
```

Checking Equality & Existence
```javascript
//If you use == the following values can be considered equal: false, 0, and ' ' (empty string).However, they are not equivalent when using the str ict operators.
(false == 0) //true
(false === 0) //false
(false == '') //true
(false === '') //false
(0 == '') //true
(O === '') //false

//Although null and undefined are both falsy, they are not equal to anything other than themselves. Again, they are not equivalent when using strict operators.

(undefined ==null) //true
(null == false) //false
(undefined == false) //false
(null == 0) //false
(undefined == O) //false
(undefined === null) //false

//Although NaN is considered falsy, it is not equivalent to anything; it is not even equivalent to itself (since NaN is an undefinable number, two ca nnot be equal).
(Nan == null) //false
(NaN == NaN) //false
```

SCE
```javascript
var artist = 'Rembrandt';
var artistA = (artist || 'Unknown'); //'Rembrandt'

artist = '';
artistA= (artist || 'Unknown'); //'Unknown'

artist = '';
artistA = (artist || {}); //empty object {}

valueA = O;
valueB = 1;
valueC = 2;
if (valueA || valueB || valueC) {
// Do something here
}
```

Loops
```javascript
var scores = [11, 20, 3];
var msg = '';
var roundNum = 0;
for(var i =0; i< scores.length; i++){
	roundNum = i + 1;
	msg = 'Round ' + roundNum + ': scores[i]' + '<br />';
}
document.getElementById('answer').innerHTML = msg;

i =1;
msg = '';
while(i < 10){
	msg += i + ' x 5  = ' + (i*5) + '<br />';
	i++;
}
document.getElementById('answer').innerHTML = msg;

i =1;
msg = '';
do{
	msg += i + ' x 5 = ' + (i*5) + '<br />';
	i++;
}while(i<1);
document.getElementById('answer').innerHTML = msg;
```
## Example

# Document Object Model
THE DOM TREE IS A MODEL OF A WEB PAGE. It consists of four main nodes :document, element, attribute, text

Accessing and updating the DOM tree involves two steps:
1. Locate the node that represents the element you want to work with.
2. Use its text content, child elements, and attributes.

## STEP 1: ACCESS THE ELEMENTS - DOM queries and traversing the DOM.
```javascript
/*DOM Queries : select an individual element node*/
getElementById('id');
querySelector('css selector'); //get first matching element for given css selector

/*DOM Queries : select multiple elements (nodelists)*/
getElementsByClassName('className');
getElementsByTagName('tagName');
querySelectorAll('css selector'); //get list of matching elements

/*Traversing DOM : traverse between element nodes*/
parentNode
previousSibling / nextSibling
firstChild / lastChild
```

## STEP 2: WORK WITH THOSE ELEMENTS
```javascript
/*access or update contents of a text node*/
nodeValue

/*work with HTML content*/
innerHTML
textContent

/*create and remove nodes*/
createElement();
createTextNode();
appendChild();
removeChild();

/*access or update attribute values*/
className
id

hasAttribute();
getAttribute();
setAttribute();
removeAttribute();
```

## Caching DOM Queries
```javascript
/*var to store the result of the query; store reference to where the node elements are in DOM tree*/
var el = document.getElementById('one');
```

## Accessing Elements
```javascript
getElementById('one'); //'id'
querySelector('li.hot'); //'css selector' : returns the first of the matching elements
getElementsByClassName('hot'); //'class name'
getElementsByTagName('li'); //'tagName' : faster method than querySelectorAll()
querySelectorAll('li.hot'); //'css selector'
```

## Methods that select individual elements
```javascript
//returns an individual element with the provided id
var el = document.getElementById('one');
el.className = 'cool';

var el2 = document.querySelector('li.one'); //first element with css selector 'li.one'
```

## NodeLists: DOM Queries that return more than one Element
* NodeList is a type of object called a 'collection'
* length property
* item() method
* Live NodeLists is returned by methods beginning 'getElementsBy_' They are faster to generate than static NodeList. When your script updates the page, the live NodeList is updated at the same time.
* Static NodeLists is returned by new methods that begin 'querySe1ector...' (which use CSS selector syntax). They reflect the document when the query was made. If the script changes the content of the page, the NodeList is not updated to reflect those changes.
```javascript
document.getElementsByTagName('h1');
document.getElementsByClassName('hot');
document.querySelectorA11('li[id]'); //get li elements that have an id attribute (regardless of the values of id attr)
```

## Selecting Elements from a NodeList
```javascript
/*Class Attributes*/
var el1 = document.getElementsByClassName('hot');
if (el1.length > 1){
	var elFirst = el1.item(0);
	var elSecond = el1[1]; //faster
	elSecond.className = 'cool';
}

/*Tag Name*/
var el2 = document.getElementsByTagName('li');
if (el2.length > 1){
	var elFirst = el2.item(0);
	elFirst.className = 'cool';
}

/*CSS Selectors*/
var el3 = document.querySelector('li.hot');
el3.className = 'cool';

var els = document.querySelectorAll('li.hot');
els[1].className = 'cool';
```

```html
<ul>
	<li id="one" class="hot">
	<em>fresh</em> figs </li>
	<li id="two" class="hot">pine nuts</li>
	<li id="three" class="hot"> honey </li>
	<li id="four">balsamic vinegar</li>
</ul>
```
```javascript
var el = document.querySelectorAll('li.hot');
if (el.length > 0){
	for(var i =0; i < el.length; i++){
		el[i].className = 'cool';
	}
}
```

## Traversing the DOM
```javascript
parentNode

previousSibling
nextSibling
firstChild
lastChild
```

## Whitespace Nodes
Most browsers, except IE, treat whitespace between elements (such as spaces or carriage returns) as a text node, so the Sibling and Child properties return different elements in different browsers.
1. remove whitespace (difficult to read codes)
2. avoid using above DOM properties
3. use jQuery(javascript library)

```html
<ul><li id="one" class="hot"><em>fresh</em> figs</li><li id="two" class="hot">pine nuts</li><li id="three" class="hot">honey</li><li id="four">balsamic vinegar</li></ul>
``` 
```javascript
// Select the starting point and find its siblings.
var startItem = document.getElementById('two');
var prevItem = startItem.previousSibling;
var nextItem = startItem.nextSibling;

// Change the values of the siblings' class attributes.
prevItem.className = 'complete';
nextItem.className = 'cool';
```

Avoid whitespaces using tricks
```html
<ul
	><li id="one" class="hot"><em>fresh</em> figs</li
	><li id="two" class="hot">pine nuts</li
	><li id="three" class="hot">honey</li
	><li id="four">balsamic vinegar</li
></ul>
```

Sibling & Child 
```javascript
// Select the starting point and find its siblings.
var startItem = document.getElementById('two');
var prevItem = startItem.previousSibling;
var nextItem = startItem.nextSibling;
// Change the values of the siblings' class attributes.
prevItem.className = 'complete';
nextItem.className = 'cool';

// Select the starting point and find its children.
var startItem = document.getElementsByTagName('ul')[0];
var firstItem = startItem.firstChild;
var lastItem = startItem.lastChild;
// Change the values of the children's class attributes.
firstItem.className = 'complete';
lastItem.className = 'cool';
```

## How to Get / Update Element Content
```javascript
//Text Nodes
nodeValue; //access text from node

//Containing Element
//When you use these properties to update the content of an element, the new content will overwrite the entire contents of the element (both text and markup).
innerHTML
textContent
innerText
```

## Access & Update a Text Node with nodeValue
```html
<div id="page">
	<h1 id="header">List</h1>
	<h2>Buy groceries</h2>
	<ul>
		<li id="one" class="hot"><em>fresh</em> figs</li>
		<li id="two" class="hot">pine nuts</li>
		<li id="three" class="hot">honey</li>
		<li id="four">balsamic vinegar</li>
	</ul>
	<div id="scriptResults"></div>
</div>
<script src="js/inner-text-and-text-content.js"></script>
```
```javascript
/*Accessing & Changing a Text Node with nodeValue*/
/*You must be on a text node (figs), not the element that contains the text (em text fresh).*/
var nodeVal = document.getElementById('one').firstChild.nextSibling.nodeValue; //figs;

var itemTwo = document.getElementById('two');
var elText = itemTwo.firstChild.nodeValue; //'pine nuts'
elText = elText.replace('pine nuts', 'kale'); //1. replace() method
itemTwo.firstChild.nodeValue = 'elText'; //2. nodeValue property also works

/*Access & Update text with textContent (& innerText); access text only from the containing element (and its children)*/
var itemOne = document.getElementById('one').textContent; //'fresh figs'

/*Avoid innerText for three key reasons: support, obeys css rules, performance issue*/
var firstItem = document.getElementById('one');
var showTextContent = firstItem.textContent; //fresh figs
var showInnerText = firstItem.innerText; //figs (fresh is hidden in css rule)

var msg = '<p>textContent: ' + showTextContent + '</p>';
msg += '<p>innerText: ' + showInnerText + '</p>';
var el = document.getElementById('scriptResults');
el.innerHTML = msg;
firstItem.textContent = 'sourdough bread';
```

## Adding or Removing HTML Content
1. innerHTML property : string including markups (or empty string to remove content)
2. DOM manipulation method targets individual nodes

## innerHTML : Update Text & MarkUp with 
```html
<ul>
	<li id="one" class="hot"><em>fresh</em> figs</li>
	<li id="two" class="hot">pine nuts</li>
	<li id="three" class="hot">honey</li>
	<li id="four">balsamic vinegar</li>
</ul>
```
```javascript
var firstItem = document.getElementById('one');
var itemContent = firstItem.innerHTML;
firstItem.innerHTML = '<a href=\"http://example.org\">' + itemContent + '</a>';
```
```html
<!--after script is run-->
<li id="one" class="hot">
	<a href="http://example.org">
		<em>fresh</em> figs
	</a>
</li>
```

## DOM Manipulation : Adding Elements
```javascript
createElement(); // 1. create the element
createTextNode(); // 2. create new text node
appendChild(); // 3. Add it to the DOM
```

```html
<ul id="todo"><li id="one" class="hot"><em>fresh</em> figs</li><li id="two" class="hot">pine nuts</li><li id="three" class="hot">honey</li><li id="four">balsamic vinegar</li></ul>
```
```javascript
var newEl = document.createElement('li');
var newText = document.createTextNode('quinoa');
newEl.appendChild(newText);

var position = document.getElementsByTagName('ul')[0];
position.appendChild(newEl);
```

## DOM Manipulation : Removing Elements
```javascript
var removeEl = document.getElementsByTagName('li')[3];
var containerEl = removeEl.parentNode;
containerEl.removeChild(removeEl);
```

## Comparing Techniques: Updating HTML Content
```javascript
/*1. Rarely used. only works when initially loading. XHTML problem*/
document.write('');

/*2. get/update the entire content of any element, including markup as a string.
Fast and simple to remove contents from an element assigning empty string
Should not be used to add content from a user for security purpose.*/
element.innerHTML;

/*3. DOM Manipulation is suited to changing one element from a DOM,
not good for changing multiple contents and slower*/
var newEl = document.createElement('li');
var newText = document.createTextNode('quinoa');
newEl.appendChild(newText);
var position = document.getElementsByTagName('ul')[0];
position.appendChild(newEl);
```

## Cross-site Scripting (XSS) Attacks

## Defending against XSS

## Attribute Node
```javascript
/*Check for an Attribute and Get its values*/
var firstItem = document.getElementById('one');
if (firstItem.hasAttribute('class'){
	var attr = firstItem.getAttribute('class');
	var el = document.getElementById('scriptResults');
	el.innerHTML = '<p>The first item has a class name: ' + attr + '</p>';
}
/*Creating Attributes & Changing their Values*/
var firstItem = document.getElementById('one');
firstItem.className = 'complete';

var fourthItem = document.getElementsByTagName('li').item(4);
fourthItem.setAttribute('class', 'cool');

/*Removing Attributes*/
var firstItem = document.getElementById('one');
if (firstItem.hasAttribute('class'){
	firstItem.removeAttribute('class');
}
```

## Examining the DOM in Chrome Browser

## Example
```javascript
var list = document.getElementsByTagName('ul')[0];

var newItemLast = document.createElement('li');
var newTextLast = document.createTextNode('cream');
newItemLast.appendChild(newTextLast);

var newItemFirst = document.createElement('li');
var newTextFirst = document.createTextNode('kale');
newItemFirst.appendChild(newTextFirst);
list.insertBefore(newItemFirst, list.firstChild);
```

# Events
- Interactions create Events
- Events trigger Code
- Code responds to Users

## Different Event Types
```javascript
/*UI Events*/
load
unload
error
resize
scroll

/*Keyboard Events*/
keydown
keyup keypress

/*Mouse Events*/
click
dblclick
mousedown
mouseup
mouseover
mouseout

/*Focus Events*/
focus / focusin
blur / focusout

/*Form Events*/
input
change
submit
reset
cut
copy
paste
select

/*Mutation Events*/
DOMSubtreeModified
DOMNodeInserted
DOMNodeRemoved
DOMNodeInsertedIntoDocument
DOMNodeRemovedFromDocument
```

## How Events Trigger JavaScript Code : Event Handling
1. Select Element (Node)
2. Specify Event 
3. Call Code

## Three Ways to Bind an Event to an Element
1. HTML Event Handler(Bad Practice!)
```html
<form method = "post" action="http://www.example.org/register">
	<label for="username">Create a username: </label>
	<input type="text" id="username" onblur="checkUsername()">
	<div id="feedback"></div>
	
	<label for="password">Create a password: </label>
	<input type="password" id="password">
	
	<input type="submit" value="Sign up!">
</form>
<script type="text/javascript" src="js/event-attribute.js"></script>
```
```javascript
function checkUsername(){
	var elMsg = document.getElementById('feedback');
	var elUsername = document.getElementById('username');
	if(elUsername.value.length < 5){
		elMsg.textContent = 'Username must be at least 5 characters';
	} else{
		elMsg.textContent = '';
	}
}
```

2. Traditional DOM Event Handler
You can only attach one function to each event handler
```html
<form method = "post" action="http://www.example.org/register">
	<label for="username">Create a username: </label>
	<input type="text" id="username" >
	<div id="feedback"></div>
	
	<label for="password">Create a password: </label>
	<input type="password" id="password">
	
	<input type="submit" value="Sign up!">
</form>
<script type="text/javascript" src="js/event-attribute.js"></script>
```
```javascript
function checkUsername(){
	var elMsg = document.getElementById('feedback');
	//var elUsername = document.getElementById('username');
	if(this.value.length < 5){ //this refers to the element the event happened on. IE 8 or earlier it would treat this as window object
		elMsg.textContent = 'Username must be at least 5 characters';
	} else{
		elMsg.textContent = '';
	}
}
var elUsername = document.getElementById('username');
elUsername.onblur = checkUsername; //when it loses focus, call checkUsername()
```

## Event Listeners
3. DOM Level 2 Event Listener; allow one event to trigger multiple functions
```javascript
function checkUsername(){
	var elMsg = document.getElementById('feedback');
	if(this.value.length < 5){
		elMsg.textContent = 'Username must be at least 5 characters';
	} else{
		elMsg.textContent = '';
	}
}
var elUsername = document.getElementById('username');
elUsername.addEventListener('blur', checkUsername, false);
//'blur' : the event you want it to listen for
//checkUsername : code to run when the event fires
//false:  
```

## Using Parameters with Event Handlers & Listeners
When the interpreter sees the parentheses after a function call, it runs the code straight away. In an event handler, you want it to wait until the event triggers it. Therefore, if you need to pass arguments to a function that is called by an event handler or listener, you wrap the function call in an anonymous function. Although the anonymous function has parentheses, it only runs when the evenUs triggered.
```javascript
var elUsername = document.getElementById('username');
var elMsg = document.getElementById('feedback');
var checkUsername = function(minLength){
	if (elUsername.value.length < minLength){
		elMsg.textContent = 'Username must be at least ' + minLength + ' characters.';
	} else{
		elMsg.innerHTML = '';
	}
}
elUsername.addEventListener('blur', function(){ checkUsername(5); }, false);
```

## Supporting Older versions of IE
```javascript
var elUsername = document.getElementById('username');
var elMsg = document.getElementById('feedback');
var checkUsername = function(minLength){
	if (elUsername.value.length < minLength){
		elMsg.textContent = 'Username must be at least ' + minLength + ' characters.';
	} else{
		elMsg.innerHTML = '';
	}
}
if(elUsername.addEventListener){
	elUsername.addEventListener('blur', function(){ checkUsername(5); }, false);
} else{
	elUsername.attachEvent('onblur', function(){ checkUsername(5); });
}
```
If you need to support IE8 (or older), instead of writing this fallback code for every event you are responding to, it is better to write your own function (known as a helper function) that creates the appropriate event handler for you. You will see a demonstration of this in Chapter 13, which covers form enhancement and validation.

## Event Flow
The flow of events only really matters when your code has event handlers on an element and one of its ancestor or descendant elements.
- Event Bubbling(false; outward)
- Event Capturing(true; inward; not supported for IE8 or earlier)
```javascript
function showElement() {
	alert(this.innerHTML);
};
/*Event Bubbling*/
el = document.getElementById("list");
el.addEventListener('click', showElement, false);

el = document.getElementById("item");
el.addEventListener('click', showElement, false);

el = document.getElementById("link");
el.addEventListener('click', showElement, false);

/*Event Capturing*/
el = document.getElementById("list2");
el.addEventListener('click', showElement, true);

el = document.getElementById("item2");
el.addEventListener('click', showElement, true);

el = document.getElementById("link2");
el.addEventListener('click', showElement, true);
```

## The Event Object
The event object contains helpful data about the event;
- which element the event happened on
- which key was pressed for a keypress event
- what part of the viewport the user clicked for a click event

The event object is passed to any function that is the event handler or listener. If you need to pass arguments to a named function, the event object will first be passed to the anonymous wrapper function (this happens automatically); then you must specify it as a parameter of the named function as shown on the next page).
```javascript
/*properties*/
target //the target of the event(most specific element interacted with)
type
cancelable

/*method*/
preventDefault();
stopPropagation();
```

## Event Listener with or without parameters
```javascript
function checkUsername(e){
	var target = e.target; //get target of event
}
var el = document.getElementById('username');
el.addEventListener('blur', checkUsername, false);
```

```javascript
function checkUsername(e, minLength){
	var target = e.target;
}
var el = document.getElementById('username');
el.addEventListener('blur', function(e){ checkUsername(e, 5); }, false);
```

## The Event Object in IE5-8
In IE5-8 Event Object is not passed automatically to event handler/listener functions
```javascript
/*the existence of an object is treated as a truthy value*/
function checkUsername(e){
	if(!e){
		e = window.event;
	}
}

/*getting properties*/
var target;
target = e.target || e.srcElement;

/*a function to return the target of an event; possibly to assign event listeners to several elements*/
function getEventTarget(e){
	if(!e){
		e = window.event;
	}
	return e.target || e.srcElement;
}
```

## Using Event Listeners with the Event Object
```html
<!doctype html>
<html lang="en">
<head>
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
<meta http-equiv="X-UA-Compatible" content="ie=edge">
<title>Event Listener and Event Object</title>
</head>
<body>
<div id="page">
	<h1>List King</h1>
	<h2>New Account</h2>
	<form method = "post" action="http://www.example.org/register">
		<label for="username">Create a username: </label>
		<input type="text" id="username"> <div id="feedback"></div>
		
		<label for="password">Create a password: </label>
        <input type="password" id="password"> <div id="feedback"></div>
        
        <input type="submit" value = "sign up">
	</form>
</div>
<script src="js/event-listener-with-event-object.js"></script>
</body>
</html>
```
```javascript
function checkLength(e, minLength){
	var el, elMsg;
	if (!e){
		e = window.event;
	}
	el = e.target || e.srcElement;
	elMsg = el.nextSibling;
	
	if(el.value.legnth < minLength){
		elMsg.innerHTML = 'Username must be at least ' + minLength + ' characters';
	} else {
		elMsg.innerHTML = '';
	}
}

var elUsername = document.getElementById('username');
if (elUsername.addEventListener){
	elUsername.addEventListener('blur', function(e){ checkLength(e, 5); }, 'false');
} else{
	elUsername.attachEvent('onblur', function(e){ checkLength(e, 5); })
}
```

## Event Delegation
By attaching an event listener to a containing element, you are only responding to one element (rather than having an event handler for each child element). You are delegating the job of the event listener to a parent of the elements. In the list shown here, if you place the event listener on the <u1> element rather than on links in each <1i> element , you only need one event listener. This gives better performance.

## Changing Default Behavior
```javascript
/*prevent default browser behavior*/
if (event.preventDefault){
	event.preventDefault();
} else {
	event.returnValue = false;
}

/*stop propagation*/
if (event.stopPropagation){
	event.stopPropagation();
} else {
	event.cancelBubble = true;
}

/*using both methods*/
return false;
```

## Using Event Delegation
```html
<!doctype html>
<html lang="en">
<head>
<title>Event Delegation</title>
<link rel="stylesheet" href="css/c06.css" />
</head>
<body>
<div id="page">
	<h1>List King</h1>
	<h2>Buy groceries</h2>
	<ul id="shoppingList">
		<li class="complete"><a href="itemDone.php?id=1"><em>fresh</em> figs</a></li>
		<li class="complete"><a href="itemDone.php?id=2">pine nuts</a></li>
		<li class="complete"><a href="itemDone.php?id=3">honey</a></li>
		<li class="complete"><a href="itemDone.php?id=4">balsamic vinegar</a></li>
	</ul>
</div>
<script src="js/event-delegation.js"></script>
</body>
</html>
```
```javascript
function getTarget(e) {                          // Declare function
  if (!e) {                                      // If there is no event object
    e = window.event;                            // Use old IE event object
  }
  return e.target || e.srcElement;               // Get the target of event
}

function itemDone(e) {                           // Declare function
  // Remove item from the list
  var target, elParent, elGrandparent;           // Declare variables
  target = getTarget(e);                         // Get the item clicked link

  /*
  The book used the following code - but it had two shortcomings
  - Clicking between list items would remove the whole list
  - Clicking on italic text would remove the link - not the list item

  elParent = target.parentNode;
  elGrandparent = target.parentNode.parentNode;
  elGrandparent.removeChild(elParent);

  The next 10 lines improve that example
  */

  if ( target.nodeName.toLowerCase() == "a" ) {  // If user clicked on an a element
    elListItem = target.parentNode;              // Get its li element
    elList = elListItem.parentNode;              // Get the ul element
    elList.removeChild(elListItem);              // Remove list item from list
  }
  if ( target.nodeName.toLowerCase() == "em" ) { // If the user clicked on an em element
    elListItem = target.parentNode.parentNode;   // Get its li element
    elList = elListItem.parentNode;              // Get the ul element
    elList.removeChild(elListItem);              // Remove list item from list
  }

  // Prevent the link from taking you elsewhere
  if (e.preventDefault) {                        // If preventDefault() works
    e.preventDefault();                          // Use preventDefault() 
  } else {                                       // Otherwise
    e.returnValue = false;                       // Use old IE version
  }
}

// Set up event listeners to call itemDone() on click
var el = document.getElementById('shoppingList');// Get shopping list
if (el.addEventListener) {                       // If event listeners work
  el.addEventListener('click', function(e) {     // Add listener on click
    itemDone(e);                                 // It calls itemDone()
  }, false);                                     // Use bubbling phase for flow
} else {                                         // Otherwise
  el.attachEvent('onclick', function(e) {        // Use old IE model: onclick
    itemDone(e);                                 // Call itemDone()
  });
}
```

## Which Element did an Event Occur On?
Event object's target property is the best way to determine this. Another approach, however, is using 'this' keyword. 'this' refers to the element that the event is on.
```javascript
/*WITHOUT PARAMETERS*/
function checkUsername(){
	var elMsg = document.getElementById('feedback');
	if(this.value.length < 5){
		elMsg.innerHTML = 'Not long Enough';
	} else{
		elMsg.innerHTML = '';
	}
}
var el = document.getElementById('username');
el.addEventListener('blur', checkUsername, false); //no parameter required!

/*WITH PARAMETERS: if you pass parameters 'this' keyword no longer works because the owner
* of the function is no longer the element that the event listener was bound to*/
function checkUsername(el, minLength){
	var elMsg = document.getElementById('feedback');
	if (el.value.length < minLength){
		elMsg.innerHTML = 'Not long enough';
	} else{
		elMsg.innerHTML = '';
	}
}
var el = document.getElementById('username');
el.addEventListener('blur', function(){ checkUsername(el, 5); }, false);
```

## Different Types of Events
- W3C DOM Events
- HTML5 Events (e.g. submit input change readystatechange DOMContentLoaded hashchange)
- BOM Events (e.g. touchstart touchend touchmove orientationchange; events dealing with touchscreen devices)

## User Interface Events
UI Events occur as a result of interaction with the browser window rather than the HTML page contained within it.
```javascript
load
unload
error
resize
scroll
```

