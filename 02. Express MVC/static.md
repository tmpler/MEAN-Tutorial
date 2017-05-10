# Making a static website with Express MVC
We'll be building a social media site that provides different data for the views depending on the user. However, we might want to look at rendering static pages before we stated trying to dynamically add data.

## Checklist
* Feed VC
* Profile VC
* Inbox VC

## Feed VC
Our social media site will need a main page that we go to that gives us all the bits of information that our friends have posted publically. At current, our main view is the first place to be sent to. Let's make it so that our main view is also our feed. This will be entirely cosmetic. Note: I've left out the 'M' from MVC because we are haven't really made any models yet, its just the view and the controller.

### server/controllers/main.js
```javascript
module.exports.index = function(req, res, next) {
  res.render('index', { title: 'New\'s Feed' }); // Change the title to New's Feed. Note: We have to escape the single quote (') using a backslash (\).
}                                                // We could have used double quotes (") around our string instead.
```

For our view, we are going to keep it reasonably simple for now. We'll want a input box for a post (which won't work yet) and a news feed underneath it. We may also want to start using a framework to make the development process faster, so we'll have to modify the layout.hbs as well. We are going to use Twitter's Bootstrap as it is popular and has good documentation. If you would rather use another framework then you can, but this tutorial will continue to assume you are using Bootstrap. For ease, we'll use the CDN's for the stylesheets and JavaScript. Bootstrap also requires jQuery.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>{{title}}</title>
    <!-- Latest compiled and minified CSS -->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
    <!-- Optional theme -->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">
    <!-- jQuery CDN -->
    <script src="https://code.jquery.com/jquery-3.2.1.js" type="text/javascript"></script>
    <!-- Latest compiled and minified JavaScript -->
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>
    <link rel='stylesheet' href='/stylesheets/style.css' />
  </head>
  <body>
    <div class="container">
    {{{body}}}
    </div>
  </body>
</html>
```
I've also added a `div` with class `container` to keep the content of the body limited to a certain width based on screen size.
Now lets add an input box and a feed to index.hbs.
```html

```
