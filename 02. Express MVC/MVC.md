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
