###Geekwise Academy Cohort JS 1 - Accelerated

**History Of Javascript**

* Created around '95 by Brendan Eich.
* Mocha -> Livescript -> Javascript -> ECMAScript
* Programming language that powers the web
* Allows for "handling" user behavior. IE Do "this" if a user does "that".
* Comes with a toolkit for not only running "programs" but also manipulating and interacting with the document object model.
* Ecma International is a non profit with the goal of developing standards for the web. It's because of these guys that you can write (mostly) the same javascript and every browser will understand what you want it to do.

**The DOM**

* Is the HTML you write the DOM?
    * No, that HTML is parsed by the browser and turned into the DOM.
* The DOM is more like a platform.  It's the representation of the page your display **AND** a way to interact with it.  It provides API's to enable this interaction.
* Javascript simply interacts with the dom (to manipulate the page).

**Where does my code go???**

Javascript isn't much fun if you don't know where to start putting your code, so lets start with the most basic example.  

**Inline JS Code**

```html
<html>
<head>
	<title>My page</title>
</head>
<body>
	<span onclick="alert('Hello world!');" class="someclass" id="someid">Click me</span>
</body>
</html>
```

This is one of the most basic ways of injecting javascript into the DOM.  Embedding javascript in the dom like this is largely frowned upon, but it is valid, so we'll discuss it here.  What would you reason that this code would do?

**Inline via script tag**

```html
<html>
<head>
	<title>My page</title>
</head>
<body>
	<h1>Hello World</h1>
	<script>
	    alert('Hello world!');
	</script>
</body>
</html>
```

**Via script tag**

```html
<html>
<head>
	<title>My page</title>
</head>
<body>
	<h1>Hello World</h1>
	<script type="text/javascript" src="myjsfile.js"></script>
</body>
</html>
```

And then create `myjsfile.js` and put it in the same folder as your html file.

```javascript
alert('This is from ann external script tag!');
```

This is usually the best way of adding javascript to your web pages, though sometimes it's unavoidable to use the inline methods described above.
