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
