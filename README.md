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
A series of instructions like a recipe or manuals. To design a script :
1. Create tasks
2. Break into steps
3. Implement JavaScript code

## b. How do computers fit in with the world around them?
Computers create models of the world using data - object, property, event, method

### Objects and Properties
Object has:
- properties (name-value pairs; characteristics)
- events (programmers choose which event they respond to)
- methods (represent things people need to do with objects)

```
HOTEL Object :
1. When a reservation is made, the book event fires.
2. The book event triggers makeBooking(), which increases the value of the bookings property
3. The value of the bookings property is changed to reflect the number of rooms available.

WINDOW Object:
location property

DOCUMENT Object:
URL property, lastModified property, title property
```

### Web browsers are programs built using objects
window & document objects

### document Object represents an HTML page
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
html(content layer), css(presentation layer), javascript(behavior layer)

```html
<body>
	<h1>Constructive &amp; Co.</h1>
	<script src= "js/add-content.js"></script>
	<p>For all orders and inquiries please call <em>555-3344</em></p>
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
document.write('<h3>' + greeting + '</h3>');
/*object.method();*/
```

Linking to a JavaScript file from an HTML page
```html
<body>
	<script type="text/javascript">document.write('<h3>Welcome!</h3>');</script>
	<script src="jss/add-content.js"></script>    
</body>
```

# Basic Javascript
Variables to store number or string
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link rel="stylesheet" href="c02/css/c02.css">
</head>
<body>
    <h1>Elderflower</h1>
    <div id="contnet">
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
- must begin with [$, _, alphabet]
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
var msg = 'Sign up to receive our newsletter for 10% off!'
/*Declare function*/
function updateMessage(myMsg){
	var el = document.getElementById('message');
	el.textContent = myMsg;
}
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
variables in an object are called properties. functions in an object are called methods.
```javascript
/*1. literal notation*/

/*object-literal1.js*/
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

/*object-literal2.js*/
var hotel = {
	name: 'Park',
	rooms: 120,
	booked: 77,
	gym: true,
	roomTypes: ['twin', 'double', 'suite'],
	checkAvailability: function(){
		return this.rooms - this.booked;
	}
};
var elName = document.getElementByld('hotelName');
elName.textContent = hotel.name; //Park
var elRooms = document.getElementByid('rooms');
elRooms.textContent = hotel.checkAvailability(); //120

/*access by dot notation*/
var hotelName = hotel.name;
var roomsFree = hotel.checkAvailability();

/*access by bracket notation*/
var hotelName = hotel['name'];

/*2-1. constructor notation(creating an object)*/
var hotel = new Object();
hotel.name ='Quay';
hotel.rooms = 40;
hotel.booked = 25;
hotel.checkAvailability = function(){
	return this.rooms - this.booked;
}
var elName = document.getElementByid('hotelName');
elName.textContent = hotel.name;
var elRooms = document.getElementByid('rooms');
elRooms.textContent = hotel.checkAvailability();

/*updating an object*/
hotel.name = 'Park';
hotel['name'] = 'Park';

/*2-2. constructor notation(creating multiple objects)*/
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
var elHotel1 = docurnent.getElementByid('hotel1');
	elHotel1.textContent =details!;

var details2 = parkHotel .name+ ' rooms: ';
	details2 += parkHotel.checkAvailability();
var elHotel2 = document.getElementByid('hotel2');
	elHotel2.textContent = details2;


/*Adding & Removing properties*/
var hotel = {
	name: 'Park',
	rooms:120,
	booked : 77;
}
hotel.gym =true;
hotel.pool = false;
delete hotel.booked;

var elName = document.getElementById('hotelName');
elName.textContent = hotel.name;

var elPool = document.getElementById('pool');
elPool.className = 'Pool: ' + hotel.pool; 

var elGym = document.getElementById('gym');
elGym.className = 'Gym: ' + hotel.gym;
```

## this keyword
```javascript
/*A Function in global scope*/
function windowSize(){
	//return default object(window) width and height
	return [this.innerWidth, this.innerHeight];
}

/*Global variables all become properties of the default object (window)*/
var width =600; // global variable; property of the window object
var shape = {width: 300}; //object with a property
var showWidth = function(){
	doucument.write(this.width); // window.width; 600
}
showWidth();

/*A Method of an object*/
var shape = {
	width: 600,
	height: 400,
	getArea: function(){
		return this.width * this.height; //600*400
	}
};

/*Function expression as method*/
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

### Browser Object Model
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

### Document Object Model
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
var msg = '<p><b>page title: </b>' + document.title + '<br />';
msg += '<b>page address: </b>' + document.URL + '<br />';
msg += '<b>last modified : </b>' + document.lastModified + '</p>' ;

var el = document.getElementById('footer');
el.innerHTML = msg;
```

### Global JavaScript Objects
```javascript
var saying = 'Home sweet home ';
```
String Object property
- saying.length

String Object method
- saying.toUpperCase(); 'HOME SWEET HOME '
- saying.tolowerCase(); 'home sweet home '
- saying.charAt(12); 'o'
- saying.indexOf('ee'); 7
- saying.lastlndexOf('e'); 14
- saying.substring(8,14); 'et hom'
- saying.split(' ') ; ['Home' , 'sweet' , 'home' , '']
- saying.trim(); 'Home sweet home'
- saying.replace('me','w'); 'How sweet home '

```javascript
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
- getMilliiseconds()  setMilliseconds() Returns I sets the milliseconds (0 - 999)
- getMinutes() setMinutes() Returns I sets the minutes (0-59)
- getMonth() setMonth() Returns/ sets the month (0-11)
- getSeconds() setSeconds() Returns I sets the seconds (0-59)
- getTime() setTime() Number of milli sec onds si n ce Ja nu ary 1, 1970, 00:00:00 UTC (Coordinated Un iver sa l Time) and a negative number for any time before
- getTimezoneOffset() Returns time zo ne offset in mins for l oca le
- toDateString () Returns "date" as a human-readable string
- toTimeString () Returns "time" as a human-readable string
- toString()

```javascript
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

### Data Types Revisited
1. String
2. Number
3. Boolean
4. Undefined (declared, not assigned)
5. Null
6. Object (arrays and functions are objects)

## Example
```html
```

```javascript
```

# Decisions and Loops


