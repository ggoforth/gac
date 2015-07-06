###Geekwise Academy Cohort JS 1 - Accelerated

**Readability**

One of the best things you can do for yourself is making sure that your code is
readable and clean.  Use of white space, proper variable naming, proper
indentation and code organization **go a long way** towards keeping your code
more maintainable and easier to debug.

If you were jumping into a new project, which would you prefer to see?

```javascript
var foo='bar';
  var baz = 'bleep'; var zip ='zop';
  if(this){
then(that);} else { whatevs();}
```

OR

```javascript
var foo='bar',
  baz = 'bleep',
  zip ='zop';

if (this) {
    then(that);
} else { 
    whatevs();
}
```

The second code block is much easier to read, uses whitespace to visually
indicate variable declarations from control flow logic, etc...

**camelCasing variable names**

As a practice, we want to give our variables meaningful names, and that
sometimes means we need more than one word for variable names.  Since we can't
have spaces in names, we use the camelCasing technique for naming our variables.
Camel Casing simply means lower casing the variable name, and then upper casing
all leters that would start a new word.  For instance, for a first name
variable you might write:

```javascript
var firstName = 'greg';
```

**CaSe SeNsItIvItY**

Javascript is case sensitive.  If you write a variable as `fooBar` you must
access / use it as `fooBar`.  `FooBar`, `fOObAR`, or anything else will yield a
value of undefined, so make sure your code always uses case sensitivity.

**Operators**

Operators allow us to take action on variables we may have already created.
Operators enable mathematical operations and comperisons so our code can become
smarter, more elegant, and be capeable of more things.

* Mathmatical Operators
    * `=` (equals)
    * `+` (addition)
    * `-` (subtraction)
    * `*` (multiplication)
    * `/` (division)
    * `%` (modulus)
    * Shorthand Mathmatical operators
        * `+=`
	* `-=`
	* `*=`
	* `/=`
* Comparison Operators
    * `==` (loose comparison)
    * `===` (strict comparison)
    * `!=` (loose not equal)
    * `!==` (strict not equal)
    * `<` (less than)
    * `>` (greater than)
    * `<=` (less than or equal)
    * `>=` (greater than or equal)
* Logical Oporators
    * `&&` (and)
    * `||` (or)

**Try it yourself**

Using [jsbin][jsbin] run a few mathmatical calculations and log the
results in the console.

The shorthand operators noted above exist for quickly operating on existing
variables in a less verbose manner.  Turning this:

```javascript
var a = 0;
a = a + 5; //a now equals 5
```

into this:

```javascript
var a = 0;
a += 5; //a now equals 5
```

Try some of these out in


[jsbin]: http://jsbin.com
