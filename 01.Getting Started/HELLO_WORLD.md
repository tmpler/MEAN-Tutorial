# Hello World Express App
Create a folder for our application.
    mkdir app
Enter that folder
    cd app
Run the express command. This is important. You need to choose a template engine that you want to use. Express uses pug (previously known as jade) by default. However, I'm not a fan. I'll be using Handlebars.
The reason for using Handlebars is that the syntax is uncomplicated and we are not wildly modifying the html which pug does do.
    express --hbs
    npm install
    npm start
Go to your browser and type in the server IP address (localhost if its on your machine) followed by `:3000` which denotes the port number.
The page should load with a Welcome to Express.
Lets examine the Express Folder Structure
    ls -l
    -app.js
    -bin
    -node_modules
    -package.json
    -public
    -routes
    -views
## What is all of this?
### app.js
This is the node.js application. Essentially, this is the JavaScript run on the server by the magical node.js.

### bin
In here is a file called www. This is the node server. Using express means we didn't have to write this ourselves.

### node_modules
Is what it says on the tin

### package.json
Very important. When we ran `npm install` earlier, npm ran through this file and installed all of the dependencies. We'll return to this later.

### public
This folder contains pubic files such as stylesheets, images and frontend scripts that we won't be generating. Essentially, they're the static website files.

### routes
This folder contains our routes. Routes are for mapping URL requests to controllers, however, a boilerplate express app puts the controllers inside the routes. We are going to move these later.

### views
This folder contains our views. Views contain our templates for the frontend.

## Make it say hello world
Let's snoop around our folders. If we go to views and open the file index.hbs we will see the following
    ```<h1>{{title}}</h1>
    <p>Welcome to {{title}}</p>```
We should be familiar with the html tags. The double curly braces are part of the Handlebars syntax. It's saying to use the title. Lets go and look in our routes folder at index.js.
    var express = require('express');
    var router = express.Router();

    /* GET home page. */
    router.get('/', function(req, res, next) {
      res.render('index', { title: 'Express' });
    });

    module.exports = router;
Ignoring almost everything here, we can see a JSON object contained within the get method of the router. This has the key `title` and the value `'Express'` which is what replaces the `{{title}}` in our hbs template.
Lets change it to say 'Hello World'.
    var express = require('express');
    var router = express.Router();

    /* GET home page. */
    router.get('/', function(req, res, next) {
      res.render('index', { title: 'Hello World' });
    });

    module.exports = router;
If you didn't stop the application from running press Ctrl+C to stop the node process.
Now rerun npm start and refresh your browser tab with the page open. You'll see that the word 'Express' has been replaced with 'Hello World'. This has also changed in the browser tab. The <title> tag of the html page has also changed. But this wasn't in index.hbs. Lets look at our views folder again. Open the layout.hbs file.
    <!DOCTYPE html>
    <html>
      <head>
        <title>{{title}}</title>
        <link rel='stylesheet' href='/stylesheets/style.css' />
      </head>
      <body>
        {{{body}}}
      </body>
    </html>
You can see 2 handlebars tags. One for `{{title}}` in the <title> tag and one for `{{{body}}}` in the body tag. Notice, the contents of index.hbs has populated the placeholder `{{{body}}}`.
Also, notice that the body placeholder has 3 sets of braces {{{}}}, whereas the title only has 2 {{}}. This tells the handlebars whether to escape string or not. For the body, as we are inputting html, we mustn't escape the html tags. If you would like to see a visual representation of this, delete one set of braces around the body placeholder and rerun your node server.
