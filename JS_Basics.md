# JS-Basics

## Day-1

- No relation wiht JAVA
- It has two engine.

       * Rendering Engine : Renders HTML and CSS
       * JavaScript Engine : Converts human readable JS code to Machine code
- JIT(Just In Time) compiler
- JS evaluates expression from left to right. Different sequences can produce different results.


### Adding JS in an HTML Page
* Method-1

``` html
<script type = "text/javascript">
    // Code JS here
</script>
```
* Method-2 (Call an external JS file)
```html
<script src = "script.js"></script>
```
Advantages of using Method-2:
* It separates HTML and Code
* It makes HTML and JS easier to read and maintain
* Cached JS files can speed up page loads

**Note: Scripts can be placed in ```<body>```, or in the ```<head>``` section of an HTML page,or in both.
      But if we place the scripts in head section it will slows down the HTML rendering.
      So, we will always try to place the scripts in the ```<body>``` section.**
      
### Variables

* **```var```** - Can be reassigned and works on global scope. Variables defined with ```var``` move to the top when code is               executed.
* **```const```** - Cannot be reassigned and not accessible before they appear within the code. Works on local scope.

* **```let```** - Similar to const but ``let`` variable can reassigned but not re-declared.


**Data Types**
``` js
var employeeId = 1704093; // Numbers

var x = 'Sourav'; // String.Here, you can use  double quotation also.

let c = true; // Bolean

const PI = 3.14159; // Constant numbers.

let car; // value and type is undefined.
```

- Any variable can be emptied, by setting the value to ```undefined```. The type will also be ```undefined```.
- JS has dynamic types. This means that the same variable can be used to hold different data types.
- You can use quotes inside a string, as long as they don't match the quotes surrounding the string

```js
let answer1 = "It's alright";             // Single quote inside double quotes
let answer2 = "He is called 'Johnny'";    // Single quotes inside double quotes
let answer3 = 'He is called "Johnny"';    // Double quotes inside single quotes
```
- An empty string has both a legal value and a type.
```js
let car = "";    // The value is "", the typeof is "string"
```

- Extra large or extra small numbers can be written with scientific(exponential) notation

```js
let y = 123e5;      // 12300000
let z = 123e-5;     // 0.00123
```

- ```typeof``` : returns the type of a variable or an expression.


## Day-2

**Objects**
```js
// Defining a simple object
var person = {
    firstName:'john',
    lastName: 'Doe',
    age:20,
    nationality:'Bangladeshi'
};
```
**Arrays**
```js
var fruits = ["Banana","Orange","Mango"];
```
**Embedding of Objects (objects inside of an object)**
```js
var employee = {
    employee1:{
        firstName:'john',
        lastName: 'Doe',
        age:20,
        nationality:'German',
        isDrive: function(){return 'Not driving';}
    },
    employee2:{
        firstName:'Saha',
        lastName: 'Sourav',
        age:21,
        nationality:'Bangladeshi',
        isDrive: function(){return 'Driving';}
    }
};
```
**Embedding of Objects and Arrays**

* objects can contain arrays
* arrays can contain objects
```js
let car = {
    brand : 'BMW',
    color : ['red', 'green', 'blue'],
    engine : {
        size : 2.0,
        fuelType : ['Octane','Patrol',
                    noValves = [2,4,6,8]
                ]
    }
};
```
**Member Access**

* Object member access - Dot Operator(.)
* Computed member access
```js
// dot operator
employee.employee1.age = 27;
console.log('Driving status of the employee: ' + employee.employee1.isDrive());

// computed member access
console.log(car.engine.fuelType[0]);
```
### Object Modification

* Member creation 
* Member assignment
* Deletion

```js
car.brand = "Toyota"; // assignment

car.speed = 160; // adding a new key to car object

/*
 adding a new method to car object
*/
car.raiseSpeed = function(){ return 'Speed raise to: ' + car.speed*2 + 'Km/h.'; };

delete car.engine.size; // member deletion. Outputs a bolean value (true/false).
```

### Array Modification

**Prebuilt Array Methods**
* ```concat()``` - join several arrays into one.
* ```indexOf()``` - returns the first position at which a given element appears in an array.
* ```join()``` - combine elements of an array into a single string and return the string.
* ```lastIndexOf()``` - returns the last position at which a given element appears in an array.
* ```pop()``` - removes the last element of an array.
* ```push()``` - add a new element at the end of an array.
* ```shift()``` - removes the first element of an array.
* ```slice()``` - pulls a copy of portion of an array into a new array.
* ```sort()``` - sorts the element alphabetically.
* ```unshift()``` - inserts new elements to the beginning.
* ```splice(fromPos,noOfElementsToBeDeleted,newElementsToBeAddes)``` - add elements from a specified position.
* ```splice(fromPos,noOfElementsToBeDeleted)``` - remove elements from specified position.
* ```toString()``` - converts elements to string.
 
```js
var array = [
    "Sourav",
    93,
    ['Brain Station',23],
    {
        officeLocation : '2 Mohakhali C/A',
        postCode: 'Dhaka-1212',
    },
    {
        isTrainee: true
    },
    function(){return 'They are in industrial attachment program';}
];

array[0] += ' Saha';
array[5] = 'Changed to String';
// array.isDemo = "Yes";

array.shift(); // delete the first element
array.pop(); // delete the last element

/*
    unshift() insert elements to beginning and
    returns the length of that array.
*/
array.unshift("Sourav","Saha","ID",1704093,[]);

/*
    push(): add elements to end of the array
*/
array.push(20,20.03);

/*
    splice(fromPos,noOfElementsToBeDeleted): remove elements from specified position
*/
array.splice(1,2);

array.splice(1,0,"hello","world",200); // to add element from a specified position

```
### **Functions or Subroutines**
    
Basic Structure
```js
function name(param1,param2,param3){
    // code goes here.
}
```
    
```js
function makeCoffe(milk,sugar){
    let instruction = "boil water";
    instruction += " Pour into cup ,";
    instruction += ' Add coffe,';
    instruction += ' Add '+milk+' spoons of  milk,';
    instruction += ' Add '+sugar+' spoons of sugar.';
    return instruction
};
```
### Callable Objects
    
    Functions are callable objects.
    Callable objects can have callable objects (Nested Callable Objects).
    
* **Subroutine inside a subroutine**
```js
    function demo(){
    var fullName = 'Sourav Saha';

    function concat( name ){
        return "Trainee " + name;
    }
    return concat(fullName); // invoking concat function and return
}
```
* **Objects as a parameter of a subroutine or function** 
```js
function Name( fullName ){
    return fullName.firstName + fullName.lastName;
}
console.log(Name({
    firstName:'Sourav',
    lastName: ' Saha'
}));
```

**Function Invocation**

The code inside the function will execute when "something" invokes (calls) the function:

* When an event occurs (when a user clicks a button)
* When it is invoked (called) from JavaScript code
* Automatically (self invoked)
    
### Memory Hoisting
 
* A feature of JavaScript
* Hoisting means lift-up
* JS only hoists declarations, not initializations.
 
```js
console.log(firstName,printName());
var firstName = 'Sourav';
function printName(){
    console.log(a,embed());
    function embed(){return 'Hello';}
    var a = 100;
    /*
        var a; //created a variable named a which is  undefined
        console.log(a); // returns undefined as a still undefined variable
        a = 100; // set the value of a to 100
    */
    return "Saha-Laxman";
}  
```    
### Strict Mode
* To secure JS.
* Strict mode is declared by adding ```"use strict"```; to the beginning of a script or a function.
* Deleting a function is not allowed.
* Duplicating a parameter name is not allowed.
* Using a variable, Object without declaring it, is not allowed.

```js
"use strict";
x = 3.14;                // This will cause an error
```


### Scope and Closure
* scope -> access
* concept of ```garbage collection```. garbage means variables,subroutines which is not need for this program and taking unnecessary memory.
* uses symbol table

**Inferred Global Scope**
* variables or subroutines defined in global scope can be accessed from anywhere in that program.
* globally declared objects or variable can't be changed from a subroutine.
* variable defined in a function can't be accessed from outside of that function.That means this is explicitly creating this symbol in this scope and none other.

```js
var engine = {
    piston: '4-Piston',
    titan: '5-Titan'
};

function runExpression(){
    var a  = 10;
    function add(){
        console.log(engine)
    }
    add();
}
runExpression();
```
    
### Context of ```this```
- A keyword.
- By default points to the window object.
- callable object allow us to change the ```this``` context.

```js
var object = {
    prop: this,
    method: function(){ return this; }
};

var array = [
    this,
    function(){ return this;}
];

function global(){
    return this;
}

global.call(object);
new global() // to change the context of this
```

The ```this``` keyword refers to different objects depending on how it is used:

* In object method, ```this``` refers to the object,
* Alone, ```this``` refers to the global object.
* In a function, ```this``` refers to the global object.
* In a function (strict mode) ,```this``` is undefined.
* In an event, ```this``` refers to the element that received the event.
* Methods linek ```call()```, ```apply()```, ```bind()``` can refer ```this``` to any object.


### Constructor
- can be viewed as a blueprint.
- ```instance``` : a copy of the blueprint.
    
**Note:**
- Naming Convention: First letter of the constructor will be capital.
 ```js
 function Apple(x, y, color, score){
    this.x = x;
    this.y = y;
    this.color = color;
    this.score = score;

    /*
        by default return the value of this
        so no need to write return statement again.
    */
}

var apple_1 = new Apple(10,20,'red',160);
var apple_2 = new Apple(10,30,'green',180);
var apple_3 = new Apple(10,40,'brown',20);
 
// Modifying instances
apple_2.score = 190;
```
    
### Prototypes
- Good memory efficiency.
- A shared object.

 **Note:**
 - Everything that unique to that object is on instance level
 - Everything that doesn't unique for instances should be on Prototype.
 - JS treats functions as callable objects.
   
```js
function Fruit(fruitName, color, weight){
    this.fruitName = fruitName;
    this.color = color;
    this.weight = weight;

}

/*
    eat() and throw() method is not unique for each instances
    so, it will be on prototype
*/
Fruit.prototype = {
    eat : function(){ return 'eat the fruit'; },
    throw : function(){ return 'throw the fruit'; }
};

var fruit_1 = new Fruit('apple','red',30);
var fruit_2 = new Fruit('banana','red',40);
var fruit_3 = new Fruit('orange','red',60);  
```

## Day-3

### **Comparsion Operator**
- ```===``` & ```!==``` prevents polymorphism
- '10' == 10 returns ```true```
- '10' === 10 returns ```false```

**If Statement**

Basic Structure:
```js
if (condition){
    // action goes here
}
```
**For Loop**

Basic Structure:
```js
for(initialization;condition,increment/decrement){
   // code goes here
}
```
**for ... in and for ... of** [From w3schools]
```js
// for ... in syntax
var array = [2,4,6];
for(let index in a){
    console.log(array[index]);
}

// for ... of syntax
for (let i of array){
    console.log(i);
}

Output of both:
2
4
6

```
## Day-4

### DOM (Document Object Model)

- Can modify,add, and remove HTML elements and attributes
- Can change CSS

**Node Properties**
* ```attributes``` - returns a live collection of all atrributes registered.
* ```childNodes``` - gives a collection of an element's child nodes.
* ```firstChild``` - returns the first child node of an element.
* ```lastChild``` - returns the last child of an element.

**Node Methods**
* ```appendChild()``` - adds a new child node to an element as the last child node.
* ```insertBefore()``` - inserts a new child before a specified & existing child node.
* ```removeChild()``` - removes a child node from an element.

**Element Methods**
* ```getAttribute()``` - returns the specified attribute value of an element node.
* ```getAttributeNS()``` - returns string value of the attribute with the specified namespace and name.
* ```getElementsByTagName()```



## Resources:
* Udemy: [udemy.com/course/javascript-essentials/](https://www.udemy.com/course/javascript-essentials/)
* w3schools: https://www.w3schools.com/js/
* OOP in JS: https://www.youtube.com/watch?v=4l3bTDlT6ZI&list=PL4cUxeGkcC9i5yvDkJgt60vNVWffpblB7/
