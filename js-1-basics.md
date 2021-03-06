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

This is usually the best way of adding javascript to your web pages, though
sometimes it's unavoidable to use the inline methods described above.

**Execution of a javascript file**

Javascript always executes from top to bottom, so, if you include two javascript files:

```html
<script type="text/javascript" src="foo.js"></script>
<script type="text/javascript" src="bar.js"></script>
```

The browser will download `foo.js` first, and execute all the contents line by
line, then it will download `bar.js`, execute that, etc... 

Also, it's often the case that you'll want to use something that `foo.js`
provides inside `bar.js`.  To do this you must ensure that `foo.js` is loaded
first. 

**Key Takeaway**: Order of loading matters.

**Comments**

Comments are notes to your future self.  Code comments are a great way to remind
you or others that will be coming into contact with your code what the code was
intended to do.  Good comments:

* Do **not** explain **how** code works, rather **why** it exists.
    * Good code should be self documenting, a good developer will be able to
	understand what the code is doing, but will often question "why does
	this code exist?"
* Are short, consise and to the point.
* Can be single or multi line depending on what you're trying to explain.
* **Are up to date**
    * All to often we'll alter / change the way code works, but not update the
	comments that already exist.  This is the quickest way to make comments
	not only out of date, but confusing.  If comments don't fit the current
	state of the code, **remove them**, and replace them with new comments
	that reflect the current state of the code.

```javascript
//I'm a single line comment.

/**
I'm a multi line comment.
*/
```

**console.log(...)**

Before we get to much further, you should aquaint yourself with the
`console.log` function.  It's purpose is to log things to the developer console
that you're using.  Be it Chrome dev tools, Firebug for Firefox, etc...  You can
put a `console.log(...)` anywhere in your code and have it log to the console so
you can see what is happening in your code.  Useage is as follows:

```
var name = 'Greg';
console.log(name);
```

**Variables & Datatypes**

Variables are one of the essential building blocks of just about any programming
language.  It's a container that can contain any kind of info, and then used
again later.

* Variables are storage for your data.
* Variables are defined using the `var` keyword.
* Multiple variables can be declared by comma separating multiple variable
    names.

```javascript
//single variable declaration
var name = 'greg goforth';

//multiple variable declaration
var firstName = 'greg',
  lastName = 'goforth';
```

So now we know how to create a variable in javascript, and we know that
variables are simple containers for any kind of data.  That begs the question,
what kinds of data exist in javascript land?

**Primatives** 

A primative data type is one that is immutable.  That is, once it's created it
can not be changed.  Any manipulation of a primative results in another
primative being created.  The primative data types are:

* strings
* numbers
* boolean
* null
* undefined

```javascript
//string example
var name = 'greg';

//number example
var three = 3;

//boolean example, boolean is true or false 
var isAdmin = false,
  isHuman = true;

//null example
var payCheck = null; //representation of no value

//undefined example
var cats = undefined; //representation of a variable that is not yet set
```

**Non-Primatives**

Non-primative values are data types that can be manipulated / changed without
creating a new version of that 'thing'.  There are two types of non-primative
data types in javascript. 

* Objects
* Array

```javascript
//example of an object literal
var person = {
    firstName: 'greg',
    lastName: 'goforth',
    worksAt: 'Bitwise Industries',
    employeeNumber: 9,
    isCEO: false
};

console.log(person.firstName); //logs 'greg'
```

Notice, an object acts as a set of key value pairs, the left side is the key,
the right side is the value.  In this way, `objects` can hold other data types
within them.  `firstName`, `lastName`, and `worksAt` are all `String`s.
`employeeNumber` is a `Number` data type, and `isCEO` is `Boolean`.

Now, for an example of an array.  Visualize array's as lists.  Lists of numbers,
strings, boolean, objects, or other strings.  Any other data type actually, can
be stored in an array.

```javascript
var people = [1, 2, 3, 4];
console.log(people);
```

Before, we mentioned that arrays are lists of things.  You can access those
things via an index.  An index is just a number, essentially it's place in line
inside the array.

The only special thin you need to know about these indexes is that they are zero
based.  IE The first item in an array is stored in index `0`, the second
in index `1`, etc...

```javascript
var people = [1, 2, 3, 4];
console.log(people[0]); //logs 1 
```

**Truthy vs Falsy**

This is an important concept in javascript (and many other languages).  Certain
values when evaluated in javascript are considered "falsy".  The following
values are always falsy:

* false
* 0 (literal number zero)
* "" empty string
* null
* undefined
* NaN (Not A Number, more on this later)

All other values are considered truthy, including "0" (zero in quotes), "false"
(false in quotes), empty functions, empty arrays and empty objects.

Internalize this, as it's a very important concept to understand.  I won't go
into to much detail now about why, just know that it is, and we'll discuss where
we will use this more later.

**Functions**

Functions in javascript are simply some grouped javascript behavior that
performs a specific action.  Javascript ships with some built in functions that
we will explore now.

**alert(...)**

```javascript
var alertString = 'The browser will show this message.';
alert(alertString);
```

The `alert` function will pop up a message that will essentially freeze program
execution until the message is dismissed.

**confirm(...)**

```javascript
var confirmString = 'Are you sure you want to do that?';
var answer = confirm(confirmString);
console.log(answer); //will be true or false
```

The `confirm` function will pop up a message that will essentially freeze program
execution until the message displayed is either confirmed or dismissed. The
function returns boolean depending on if it was dismissed or confirmed.

**prompt(...)**

```javascript
var promptString = 'Enter your first name';
var answer = prompt(promptString); //enter your name 
console.log(answer); //will be your name entered in the previous step 
```

**Try for yourself**

Using [jsbin](http://jsbin.com), create a javascript program that will:

* Ask the user their name
* Ask the user their email
* Ask the user their favorite movie
* Assign all the values prompted for into an object
* Log the object to the console
