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
* [13. Form Enhancement and Validation](#form-enhancement-and-validation)

# ABC of Programming

## a. What is a script and how to create one? 
A script is a series of instructions like a recipe or manuals. 
To design a script, create tasks, break them down into steps and implement into JavaScript code.

## b. How do computers fit in with the world around them?
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

## c. How do I write a script for a web page?
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

you can directly put script in 'add-content.html'
```html
<body>
    <script type="text/javascript">document.write('<h3>Welcome!</h3>');</script>    
</body>
```

# Basic Javascript
variable data types(number, string, boolean), array(object)
```javascript
var a= "a";
var b = 'b';
var n = 1;
var isTrue = true; //or false
var arr= ['string', 1, false, true]; //new Array('a', 'b', 'c', 'd');
arr.length // 4
arr[0] = 'String';
```

## Operator
arithmetic operator + - / * ++ -- % boolean < > logical && || 

# Functions, methods, and Objects
```javascript
var msg = 'Sign up to receive our newsletter for 10% off!'
/*function declaration*/
function updateMessage(myMsg){
    var el = document.getElementById('message');
    el.textContent = myMsg;
}
updateMessage(msg); /*call*/

/*anonymous function (expression)*/
var area = function(width, height){
    return width * height;
}
var size = area(3, 4);

/*immediately invoked function expressions(IIFE)*/
var area = ( // area will hold returned value, rather than storing the function itself
    function(){
        var width =3;
        var height = 2;
        return width * height;
    } () //call function immediately
);//interprets as an expression
```

## Object
variables in an object are called properties. functions in an object are called method.
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
var elRooms = document.getElementByid('rooms'); //40
elRooms.textContent = hotel.checkAvailability();

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
var elRooms = document.getElementByid('rooms'); //120
elRooms.textContent = hotel.checkAvailability();

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

/*creating objects using constructor syntax*/
var hotel = new Object();
hotel.name= 'Park';
hotel.rooms = 120;
hotel.booked = 77;
hotel.checkAvailability = function(){
    return this.rooms - this.booked;
};
var elName = document.getElementByid('hotelName');
elName.textContent = hotel.name;
var elRooms = document.getElementByid('rooms');
elRooms.textContent = hotel.checkAvailability();

/*creating objects using constructor notation*/
function Hotel (name, rooms, booked) {
    this.name = name;
    this.rooms = rooms;
    this.booked = booked;
    this.checkAvailability = function(){
        return this.rooms - this.booked;
    }
};
var quayHotel = new Hotel('Quay', 40, 25);
var parkHotel = new Hotel( 'Park', 120, 77);
var details1= quayHotel.name + ' rooms : ';
    details1 += quayHotel.checkAvailability();
var elHotel1 = docurnent.getElementByid('hotell');
    elHotel1.textContent =details!;

var details2 = parkHotel .name+ ' rooms: ';
    details2 += parkHotel.checkAvailability();
var elHotel2 = document.getElementByid('hotel2');
    elHotel2.textContent = details2;

/*adding & removing properties*/
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
/*window is the default object*/
function windowSize(){
    return [this.innerWidth, this.innerHeight];
}
/*global variables also become properties of the window object*/
var width =600;
var shape = {width: 300};

var showWidth = function(){
    // global variable, width, is a property of the window object
    doucument.write(this.width); // document.write(window.width); 600
}
showWidth();

/*method of an object*/
var shape = {
    width: 600,
    height: 400,
    getArea: function(){
        return this.width * this.height; //600*400
    }
};

/*function expression as method*/
var width =600;
var shape ={width: 300};
var showWidth = function(){
    document.write(this.width);
}
shape.getWidth = showWidth;
shape.getWidth(); //300
```

## Built-in objects

