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
<span color="red">
```bash
[nodemon] app crashed - waiting for file changes before starting...
```
</span>
