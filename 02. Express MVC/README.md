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
What we have is an object called router using its get method. This method is taking two parameters, an URL and a Controller in the form of a function.
In simple terms this can be expressed as:
```javascript
router.get(url,controller);
```
If we look back at the start of the file, we can see that router is what's returned from `express.Router()` and express is defined above as `require('express')`. Require is how node knows which modules are needed. By storing this in a nice variable name such as express, we can access the module easily.

The final line is `module.exports = router;`. In node, we use this to put our module into node.js by exporting it.
