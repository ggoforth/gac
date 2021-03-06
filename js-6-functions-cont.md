###Geekwise Academy Cohort JS 1 - Accelerated

**Try for yourself**

Refactor the previous movie example to also prompt the user for a movie title,
and when if it finds a matching title, alert something like "MovieTitle was
released in movieYear" (substituting actual values for MovieTitle and
movieYear).

**`prototype`**

At it's simplest, the `prototype` of a javascript object is a collection of
functions that are "tacked on" to new instances of javascript objects.  At it's
most complicated it's a way for javascript objects to inherit functions and
properties from other objects.  We'll discuss the simple form today as it's most
relevant to how we would likely use `prototype`, and I'll provide some links to
the later scenario.  

Benefits of using prototype:

* More performant - only one version of prototype functions exists for ALL instances of
    the object.
* Enabled inheritence in javascript
* Ability to add methods and properties to already existing object instances.

Drawbacks of using prototype:

* No clousures 

Lets look at an example of how to implement a prototype, and then we'll revisit
the benefits / drawbacks.

Here is an example of creating a prototype for a person:

```javascript
function Person(name, age, gender) {
    this.name = name;
    this.age = age;
    this.gender = gender;
}

Person.prototype = {
    speak: function () {
        console.log('Hi, my name is ' + this.name);
    }
};

```

So, what's going on here?  First, lets look at how we've written the function
definition.  `Person`, note the capitalized `P`.  This signifies that a
function is going to be used as a "constructor" (more on this soon).  Next we
notice that all the function arguments are being assigned to the `this`
property.  Also, note that there is no return value from the `Person` function.

Next, we set the `Person.prototype` equal to an object.  It has a function
called `speak` that all `instances` of the `Person` object with inherit.  

So, lets explore a bit...How do we call the speak function?

```javascript
Person.speak();
```

That's not what we want...maybe we need to call the function off the prototype?

```javascript
Person.prototype.speak();
```

That's closer! We get our console.log, but the name is undefined.  The reason
for this is that we've yet to create a `new` instance of the `Person` function.

**`new` Keyword**

We use the `new` keyword to create a new instance of something. Imagine that...

```javascript
var greg = new Person('greg', 35, 'male');
var christine = new Person('christine', 31, 'female');

console.log(greg);
console.log(christine);
```

Now lets try and call the speak method of our `greg` and `christine` objects.

```javascript
greg.speak();
christine.speak();
```

What do we get?  The end result should be that each person object console logs
their name.  Each person instance has inherited the `speak` function and because
it the `speak` function uses the `this` object to find the name property, we get
the proper name being logged.

So what actually happens when we use the `new` keyword before a function?  The
following is the basic workflow:

* we call `new Person(...)`
* a brand new fresh object is created.
* This new object is set as the `context` of the function
* All prototype functions are added to the new object
* The constructor adds any additional properties to the new object.
* If the constructor function doesn't return a value, the new object is returned
    automatically.

**Try for yourself**

Convert your movie function that returns a normal object literal into a
constructor function.  What are all the steps needed to do that?  

**Try for yourself**

Lets revisit our movie array of arrays.  Lets convert the movie function (the
one that returns a simple object literal) to a constructor function.

* Start with your movie array of arrays.
* Convert each array in the movie array into a movie object using a constructor
    function
* Add a checkIn, checkOut and status functions to your Movie functions prototype
* The checkIn function should set the this.checkedIn property to true
* The checkOut function should set the this.checkedIn property to false
* The status function should look to see if that movie is checked in our out, and
    return a string stating it's status
* Create a loop that will run 5 times
* Inside the loop prompt the user for a movie title they would like to checkout 
    checkin. (remember, you must spell it the same as in your array)
* Find the movie object with that title and call the the appropriate function.
* Finally log out the movie array and lets look at the status of each of those.

**Try for yourself**

* Create a Bank constructor function
* The constructor function should have a balance property equal to 100
* Add a credit function to Banks prototype that will add to balance
* Add a debit function to the Banks prototype that will subtract from the balance
* Create an instance of the bank
* Create a loop that will run three times and prompt the user for a number input
* Parse the values into numbers
* Call the bank.credit(num) function and add that amount to your balance
* Create a new loop that will run twice
* Inside this loop prompt for a number and parse the number
* Run these two numbers with the bank.debit(num) to subtract from the balance
* Finally, log the ending balance after the three credits and two debits. For
    instance, if you start with 100, credit 10 three times, we get 130, then debit
    10 twice, we get 110.
