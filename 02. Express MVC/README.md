# 02. Express MVC
TODO: Introduction

# Checklist
* Understanding Routes
* Restructure express for MVC
* Understanding controllers
* Understanding views

## Understanding Routes
Lets take a look at the code in routes/index.js
```javascript
var express = require('express');
var router = express.Router();

/* GET home page. */
router.get('/', function(req, res, next) {
  res.render('index', { title: 'Hello World' });
});

module.exports = router;
```
There are some key parts to this file however we are focusing on everything after the `/* Get home page*/` comment.
What we have is an object called router using its `get` method. A `get` method does what is says on the tin. It gets what we ask for. This method is taking two parameters, an URL and a Controller in the form of a function.
In simple terms this can be expressed as:
```javascript
router.get(url,controller);
```
If we look back at the start of the file, we can see that router is what's returned from `express.Router()` and express is defined above as `require('express')`. Require is how node knows which modules are needed. By storing this in a nice variable name such as express, we can access the module easily.

The final line is `module.exports = router;`. In node, we use this to put our module into node.js by exporting it.

## Other routes
So that is the route for our homepage explained. However, if we only ever do `get` methods then it severely limits our application to just dishing out web pages. We want uses to be able to make a CRUD application.
* Create - POST
* Request - GET
* Update - PUT
* Delete - DELETE
As you can see, we have only looked at the GET method, and not even in much detail. We'll cover this more later, so just remember the basic structure for a route for now.

### Small note
If you are a self-taught web development type person, you may not have had any formal training in programming. If you know the difference between a method and a function, feel free to move on, else continue reading.
A method is part of an object. Similar to a function, it can take parameters and carry out instructions given to it. However, unlike a function, a method is part of an object and has access to the object itself. Example:
```javascript
/* Function that takes name as a parameter and prints it to the console */
var sayName = function(name){
  console.log(name);
};
/* Person constructor uses a function */
var Person = function(name){
  this.name = name;
};
/* Person method that prints the name property of the object */
Person.prototypesayMyName = function () {
  console.log(this.name);
};
/* a function */
sayName('Leo'); // This prints Leo to the console. The function uses the parameter passed to it.
/* a method */
var person = new Person('Paris');
person.sayMyName(); // prints Paris to the console. The method accesses the name property of the person object.
```
