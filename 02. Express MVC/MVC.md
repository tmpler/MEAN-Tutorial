# MVC
As mentioned before, express by default puts our controllers inside the route. But we don't want that, we want them to be separated. Why? Good practice. No more questions.

## Moving stuff around
Inside out app folder lets make a new folder called server. Lets move our routes folder and views folder here and lets make two new folders, controllers and models.
```bash
mkdir server
mv routes server/
mv views server/
mkdir server/models
mkdir server/controllers
```
Now, this will completely break our application. If you go ahead and npm start you'll have problems as we have moved everything.

This is probably a good time to talk about nodemon which we installed earlier. nodemon is an excellent package for development environments. It keeps node running and detects changes that require node to be restarted. If your node application breaks, it will wait for file changes to occur before attempting to run the server again. Later I'll show you how to run node in production. Make sure you are in the app folder and run:
```bash
nodemon
```
You will see nodemon attempted to run your application but because it is broken you'll get a message like this:
```bash
[nodemon] app crashed - waiting for file changes before starting...
```
## Fix it
Back in the app folder we have a file I alluded to earlier called app.js. Lets take a look in here at line 14
```javascript
app.set('views', path.join(__dirname, 'views'));
```
Lets change this to reflect that we moved views to server.
```javascript
app.set('views', path.join(__dirname, ,'server','views'));
```

Also, line 8 and 9:
```javascript
var index = require('./routes/index');
var users = require('./routes/users');
```
Change this to:
```javascript
var index = require('./server/routes/index');
var users = require('./server/routes/users');
```
Go ahead and check nodemon. The app should now be running.

We're not done yet, we now need to take the controllers out of the routes.

Lets go back to our index.js in server/routes.
```javascript
/* GET home page. */
router.get('/', function(req, res, next) {
  res.render('index', { title: 'Hello World' });
});
```
The second parameter is our controller. We can just take this out and make it a function.
```javascript
var homePageController = function(req, res, next) {
  res.render('index', { title: 'Hello World' });
}
/* GET home page. */
router.get('/', homePageController);
```
So we've taken the controller out of the route, but that doesn't really change much. Really we want the controller in its own folder and file.
Go and make a new file in server/controllers called main.js
```bash
touch server/controllers/main.js
```
In this file input controller:
```javascript
var homePageController = function(req, res, next) {
  res.render('index', { title: 'Hello World' });
}
```

Let's modify the first line to use module.exports.
```javascript
module.exports.index = function(req, res, next) {
  res.render('index', { title: 'Hello World' });
}
```
Here, we have created an index method for our controller. Now lets return to the route in server/routes/index.js and require our controller. And change the `get` method to contain our index controller.

```javascript
var express = require('express');
var router = express.Router();
var mainCtrl = require('../controllers/main');

/* GET home page. */
router.get('/', mainCtrl.index);

module.exports = router;
```
