###Geekwise Academy Cohort JS 1 - Accelerated

**String Concatenation**

The act of joining two things together is called concatenation.  In javascript
we concat __strings__ together using the `+` operator.

```javascript
var password = 'secret',
  salt = 'abc1234',
  saltedPassword = salt + password;

console.log(saltedPassword);
```

Be aware though, javascript has some quirks when dealing with concatenation that
may be confusing.  If you attempt to concat a number and a string, it will
attempt to be "helpful" and and convert the number to a string, so that it can
be concatenated.

```javascript
var num = 1,
  str = "foo";

//cast a number to a string
console.log(num + str); //1foo

//cast a number to a string
console.log(1 + "");
```

The act of converting a number to a string is something called __Type Casting__.
It's essentially saying "Hey, you're trying to concat values of different types,
so I am going to convert one of them for you so the concat will work.

**Arrays**

Arrays are useful for keeping an ordered list of "things".  Arrays don't really
care what you put inside of them, they accept all the data types we've talked
about to date, and a few we haven't.  

To create a new array, you'll use the `[...]` syntax.  Items inside the array
are separated by a `,` (comma).  So, to create an `array` simply:

```javascript
var fruits = ['apple', 'banana', 'cherry', 'grape'];
console.log(fruits);
```

Arrays also have a convenient way to determine how many things are inside them,
via the `length` property.

```javascript
var fruits = ['apple', 'banana', 'cherry', 'grape'];
console.log(fruits.length);
```

**Accessing Array Contents**

This is all very useful, but how do we get our data back out?  Wouldn't be very
useful if we couldn't access the data we are storing in our array.

Array's are index based, so you can use a numbered index to retrieve a specific
value, using the brackets to define which index you want.

```javascript
var a = [1, 2, 3];

console.log(a[N]); //where N would be a numbered index you want to retrieve

//this works too
console.log([1, 2, 3, 4][N]);
```

**Note To Self:** Array indexes (as well as other indexes we'll discuss later)
all start with 0. So in the example above, index zero would have the value 1,
index 1 has the value 2, index 2 has the value 3, etc...

```javascript
var firstFruit = fruits[0];
console.log(firstFruit); //log the first value in the array

var secondFruit = fruits[1];
console.log(secondFruit);

//etc...

console.log(fruits[4]); //what does a unknown index return?
```

**Adding Items to an array**

Javascript provides a function called `push` that allows for adding items to the
end of an array.  Give it a shot.

```javascript
//add an item to the array
fruits.push('blackberry');
```

When you add items to an array, the `length` property is automatically updated
for you. 

```javascript
var a = [1];
console.log(a.length);

a.push(2);
console.log(a.length);
```

Arrays can also contain other arrays.

```javascript
//create an array to hold multiple arrays
var fruitColors = [];
var cherry = ["cherry", "red"];
var banana = ["banana", "yellow"];
var orange = ["grape", "purple"];

//add all the fruit vars into the fruitColors array
fruitColors.push(cherry);
fruitColors.push(banana);
fruitColors.push(orange);

console.log(fruitColors);
```

Now lets attempt to pull out the color's only for each of the three fruits
in our fruitColors array.

```javascript
//we can access our array's based on index
console.log(fruitColors[0][1]);
console.log(fruitColors[1][1]);
console.log(fruitColors[2][1]);
```

**Removing Items from an array**

So now we can create Arrays, access array properties, and add items to arrays,
how about removing items? 

Items can be removed one at a time **from the end** of the array, using the
`pop` function. NOTE: This modifies the array.  You're not creating a new array
in this case, you're actually changing the original array.  The last item is
removed, and the length property is updated.

```javascript
var lastFruit = fruits.pop();
console.log(lastFruit);
console.log(fruits);
```

Another handy array / string function we'll talk about is the slice function. 
It works on arrays a little differently. The slice function will make a copy 
of the specified indexes and return them in a new array.

The `signature` for the slice function looks like:

`fruits.slice(begin, [end])`

A `signature` is described as the way you call a function.  The order of the
arguments, the name of the function, etc... So, for the slice function the begin
is the zero based starting index, and the end is the index to stop at. NOTE: The
extraction does not include the end index!

```javascript
var fruits = ["apple", "cherry", "plum", "apricot"];
console.log(fruits.slice(1, 3));
console.log(fruits); //note, it's the same as the original array.
```

One point to remember about the slice functions is that it **does not** modify the
original array. But what if we actually did want to modify the original?

**splice** to the rescue! The splice function works in a similar way to the slice
function, however it allows you to modify the original array.

The signature of the splice function looks like:

```javascript
fruits.splice(begin, howManyToRemove, [additional, items, to, add]);
```

So `begin` is our starting index, `howManyToRemove` is how many items to remove from
the starting index, and `additional` `items` `to` `add` are more elements that you want
to add to the array (comma separated values).

```javascript
var fruits = ["cherry", "apple", "banana", "plum"];
fruits.splice(2, 1);
console.log(fruits);
```

There are a lot more things we can do with arrays, for more info, [check out the
MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

**Control Flow Looping**

Looping is the act of repeating blocks of code based on the a given condition.
When the condition ceases to be truthy, the loop stops.

Three kinds of loops we'll discuss are:

1. `while`
2. `for`
3. `do / while`

**while(...)**

First, we'll cover while loops. while loops work by evaluating a condition, if
the condition is true, the loop "fires", executing all code it contains, once
the condition becomes false, the loop stops.

One important concept with while loops is that you must write the code that will
make the condition false, otherwise you get an infinite loop.

```javascript
var a = 0;
while (a < 10) {
    console.log(a);
    a++;
}
```

**for(...)**

With for loops we need to set up 3 things, our starting point, our condition,
and our incrementer.  This type of loop is nice because you do not need to
manage the incrementer in your normal code excecution, because it's built into
the loop structure.

```javascript
for (var i = 0; i < 10; i++) {
    console.log(i);
}
```

Fantastic, so now I can loop, but, what if I want a loop to stop early?
Javascript provides two ways of controlling the flow of a loop, the `continue` and
`break` keywords.

`continue` will immediately reset the loop to the next iteration, and continue on
with the loop. It's basically just saying, disregard the rest of this loop and
go to the next loop.

**do while(...)**

The `do / while` loop is less commonly used however it's a useful tool to have
once you understand how it's used.

The do / while loop will always run at least once, then it evaluates it's
condition. If the condition is still true, it will continue the loop

```javascript
var i = 1;

do {
    console.log(i);
    i++;
} while (i < 10);
```

**Try it yourself**

Create a loop (for or while) that will loop 10 times, and skip the 5th and 7th
loop. All other loops should log the loop number to the console.

The break keyword will, when encountered, immediately stop the loop AND all
subsequent loops.

**Try it yourself**

Create a for loop that will loop ten times, each time logging the current loop
number, but terminate the loop on the seventh loop.

**Looping Arrays**

So all our work with arrays up to this point has been retrieving array indexes
one at a time using a numbered bracket notation, IE `fruits[3]`. This is useful,
but what if your application requirements were such that you needed to do
something to every element in the array?

LOOP ALL THE THINGS! A for loop is a perfect mechanism for iterating over each
element in an array.

**Try it yourself**

How would you create a for loop and log all the items in our fruit array to the
console? Hint...you may find the length property of an array useful here.

**Try it yourself**

Create a program that will:

* Prompt the user for a starting number
* Prompt the user for an ending number
* These numbers will become the start and end points for our loop. If either
    number is not a number, alert to the user that only numbers can be entered. (no
    further action should take place, if / else will be handy here)
* Parse the start and stop points into numbers and store them in variables you can
    use later
* Ensure that the start number is smaller than the stop number, otherwise stop
    execution (if / else)
* Create a loop (for or while, you choose) that will loop starting at the starting
    number, and end on the ending number.
* For each loop, log to the console if the number is even or odd (remember our %
    operator :)

Then, create a program that will:

* Create an array holding the numbers 1 - 500
* Using the array as the basis for a loop, remove one element per loop (pop), with
    the result being an empty array.
* What is the result? Anything surprising happen?  How can we avoid that???




[jsbin]: http://jsbin.com
