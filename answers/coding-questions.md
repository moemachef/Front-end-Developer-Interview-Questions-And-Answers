# Coding Questions

#### *Question: What is the value of `foo`?*
```javascript
var foo = 10 + '20';
```

*Answer:* `'1020'`, because of type coercion from Number to String

#### *Question: What is the value of `foo`?*
```javascript
var foo = 20 + 10 + '30';
```
*Answer:* `'3030'`, because of type coercion from Number to String

#### *Question: If we execute this Javascript, what will the browser's console show??*
```
var text = 'outside';
function logIt(){
console.log(text);
var text = 'inside';
};
logIt();
```
*Answer:* Neither outside, nor inside, the result is`undefined`, It’s because JavaScript initialization is not hoisted. (Why doesn’t it show the global value of outside? The reason is that when the function is executed, it checks that there’s a local x variable present but doesn’t yet declare it, so it won’t look for global one.)




#### *Question: How would you make this work?*
```javascript
add(2, 5); // 7
add(2)(5); // 7
```

*Answer:* A general solution for any number of parameters
```js
function add(x, y) {
  if (y !== undefined) {
    return x + y;
  } else {
    return function(y) { return x + y; };
  }
}

add(2, 5); // 7
add(2)(5); // 7
```

#### *Question: How would you make this work?*
```javascript
sum(3, 5, 7); // 15
sum(3)(5)(7); // 15
```
*Answer:* A general solution for any number of parameters
```js
function sum(x, y, z) {
  if (y !== undefined && z !== undefined) {
    return (x + y + z);
  } else {
    return function(y) { 
      return function(z){
        return (x + y + z)
      }
    };
  }
}
```


#### *Question: Write a sum() function that accepts any number of arguments and returns their sum.*
```javascript
function sum() {
    var s = 0;
    for (var i=0; i < arguments.length; i++) {
        s += arguments[i];
    }
    return s;
}
```
#### *Question: What value is returned from the following statement?*
```javascript
"i'm a lasagna hog".split("").reverse().join("");
```

*Answer:* It's actually a reverse method for a string - `'goh angasal a m\'i'`

#### *Question: The syntax is just fine—the problem is some unexpected behavior, What is it ?*
```
<button id="btn-0">Button 1!</button>
<button id="btn-1">Button 2!</button>
<button id="btn-2">Button 3!</button>
<script type="text/javascript">
  var prizes = ['A Unicorn!', 'A Hug!', 'Fresh Laundry!'];
   for (var btnNum = 0; btnNum < prizes.length; btnNum++) {
      // for each of our buttons, when the user clicks it...
      document.getElementById('btn-' + btnNum).onclick = function() {
        // tell her what she's won!
        alert(prizes[btnNum]);
      };
    }
</script>

```
*Answer:*
-  The for loop when completed the variable i has a value of 3 each time the loop try to start.

- We can fix it  by using closures with an immediately invoked function expression (IIFE), which creates a closure around our code, capturing the value of i in the IIFE's argument to keep it from changing when the callback is executed.

- We could also have solved the problem using Function#bind to capture the value of i in a new function with that value applied as the first argument.

- We could also replace for loop with forEach method.

- We could also use let insted of var, With the introduction of let and block scoping in ES6, the previously mentioned problem disappears - so long as you declare your for loop initializers using let instead of var. Using let in our loop initializer makes i block scoped to the block of code within the loop. This properly captures the value for our callbacks and keeps us from polluting the global scope with for loop initializers all over the place. Not to mention, it keeps the code more readable and concise - nested IIFE's inside for loops don't really add to code clarity or understanding and can be verbose to type.

https://www.datchley.name/loop-variable-gotcha/

#### *Question: What is the value of `window.foo`?*
```javascript
( window.foo || ( window.foo = "bar" ) );
```

*Answer:* Always `'bar'`

The or (||) operator. In an expression of the form X||Y, X is first evaluated and interpreted as a boolean value. If this boolean value is true, then true is returned and Y is not evaluated, since the “or” condition has already been satisfied. If this boolean value is “false”, though, we still don’t know if X||Y is true or false until we evaluate Y, and interpret it as a boolean value as well.

#### *Question: What is the outcome of the two alerts below?*
```javascript
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```

*Answer:*
- First: `Hello World`
- Second: Throws an exception, `ReferenceError: bar is not defined`

#### *Question: What is the value of `foo.length`?*
```javascript
var foo = [];
foo.push(1);
foo.push(2);
```

*Answer:* `.push` is mutable - `2`

#### *Question: What is the value of `foo.x`?*
```javascript
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
```

*Answer:* `undefined`. Rather, `bar.x` is `{n: 2}`.

`foo.x = foo = {n: 2}` is the same as `foo.x = (foo = {n: 2})`. It is because
a left term is first referenced and then a right term is evaluated when an
assignment is performed in JavaScript. When `foo.x` is referenced, it refers
to an original object, `{n: 1}`. So, when the result of the right term, `{n:
2}`, is evaluated, it will assigned to the original object, which is at the
moment referenced by `bar`.

#### *Question: What does the following code print?*
```javascript
console.log('one');
setTimeout(function() {
  console.log('two');
}, 0);
console.log('three');
```

*Answer:* `one`, `three` and `two`. It's because `console.log('two');` will be
invoked in the next event loop.


#### *Question: What is a potential pitfall with using typeof ```bar === "object"``` to determine if bar is an object? How can this pitfall be avoided?*

*Answer:* 

Although typeof ```bar === "object"``` is a reliable way of checking if ```bar``` is an object, the surprising gotcha in JavaScript is that ```null``` is also considered an object!

Therefore, the following code will, to the surprise of most developers, log ```true``` (not ```false```) to the console:

```
var bar = null;
console.log(typeof bar === "object");  // logs true!
```
As long as one is aware of this, the problem can easily be avoided by also checking if ```bar``` is ```null```:

```
console.log((bar !== null) && (typeof bar === "object"));  // logs false
```
To be entirely thorough in our answer, there are two other things worth noting:

First, the above solution will return ```false``` if ```bar``` is a function. In most cases, this is the desired behavior, but in situations where you want to also return ```true``` for functions, you could amend the above solution to be:

```
console.log((bar !== null) && ((typeof bar === "object") || (typeof bar === "function")));
```
Second, the above solution will return ```true``` if ```bar``` is an array (e.g., if ```var bar = [];```). In most cases, this is the desired behavior, since arrays are indeed objects, but in situations where you want to also ```false``` for arrays, you could amend the above solution to be:

```
console.log((bar !== null) && (typeof bar === "object") && (toString.call(bar) !== "[object Array]"));
```
However, there’s one other alternative that returns ```false``` for nulls, arrays, and functions, but ```true``` for objects:

```
console.log((bar !== null) && (bar.constructor === Object));
```
Or, if you’re using jQuery:

```
console.log((bar !== null) && (typeof bar === "object") && (! $.isArray(bar)));
```
ES5 makes the array case quite simple, including its own null check:

```
console.log(Array.isArray(bar));
```

#### *Question: What will the code below output to the console and why?*

```
(function(){
  var a = b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));
```

*Answer:* 

Since both ```a``` and ```b``` are defined within the enclosing scope of the function, and since the line they are on begins with the var keyword, most JavaScript developers would expect ```typeof a``` and ```typeof b``` to both be undefined in the above example.

However, that is not the case. The issue here is that most developers incorrectly understand the statement ```var a = b = 3;``` to be shorthand for:

```
var b = 3;
var a = b;
```

But in fact, ```var a = b = 3;``` is actually shorthand for:

```
b = 3;
var a = b;
```
As a result (if you are not using strict mode), the output of the code snippet would be:

```
a defined? false
b defined? true
```
But how can ```b``` be defined outside of the scope of the enclosing function? Well, since the statement ```var a = b = 3;``` is shorthand for the statements ```b = 3;``` and ```var a = b;```, ```b``` ends up being a global variable (since it is not preceded by the ```var``` keyword) and is therefore still in scope even outside of the enclosing function.

Note that, in strict mode (i.e., with ```use strict```), the statement ```var a = b = 3;``` will generate a runtime error of ```ReferenceError: b is not defined```, thereby avoiding any headfakes/bugs that might othewise result. (Yet another prime example of why you should use ```use strict``` as a matter of course in your code!)


#### *Question: What will the code below output to the console and why?*

```
var myObject = {
    foo: "bar",
    func: function() {
        var self = this;
        console.log("outer func:  this.foo = " + this.foo);
        console.log("outer func:  self.foo = " + self.foo);
        (function() {
            console.log("inner func:  this.foo = " + this.foo);
            console.log("inner func:  self.foo = " + self.foo);
        }());
    }
};
myObject.func();
```

*Answer:* 

The above code will output the following to the console:

```
outer func:  this.foo = bar
outer func:  self.foo = bar
inner func:  this.foo = undefined
inner func:  self.foo = bar
```

In the outer function, both ```this``` and ```self``` refer to ```myObject``` and therefore both can properly reference and access ```foo```.

In the inner function, though, ```this``` no longer refers to ```myObject```. As a result, ```this.foo``` is ```undefined``` in the inner function, whereas the reference to the local variable ```self``` remains in scope and is accessible there.

#### *Question: What is the significance of, and reason for, wrapping the entire content of a JavaScript source file in a function block?*

*Answer:* 

This is an increasingly common practice, employed by many popular JavaScript libraries (jQuery, Node.js, etc.). This technique creates a closure around the entire contents of the file which, perhaps most importantly, creates a private namespace and thereby helps avoid potential name clashes between different JavaScript modules and libraries.

Another feature of this technique is to allow for an easily referenceable (presumably shorter) alias for a global variable. This is often used, for example, in jQuery plugins. jQuery allows you to disable the ```$``` reference to the jQuery namespace, using ```jQuery.noConflict()```. If this has been done, your code can still use ```$``` employing this closure technique, as follows:

```(function($) { /* jQuery plugin code referencing $ */ } )(jQuery);```

#### *Question: What is the significance, and what are the benefits, of including 'use strict' at the beginning of a JavaScript source file?*

*Answer:* 

The short and most important answer here is that ```use strict``` is a way to voluntarily enforce stricter parsing and error handling on your JavaScript code at runtime. Code errors that would otherwise have been ignored or would have failed silently will now generate errors or throw exceptions. In general, it is a good practice.

Some of the key benefits of strict mode include:

- Makes debugging easier. Code errors that would otherwise have been ignored or would have failed silently will now generate errors or throw exceptions, alerting you sooner to problems in your code and directing you more quickly to their source.

- Prevents accidental globals. Without strict mode, assigning a value to an undeclared variable automatically creates a global variable with that name. This is one of the most common errors in JavaScript. In strict mode, attempting to do so throws an error.
- Eliminates ```this``` coercion. Without strict mode, a reference to a ```this``` value of null or undefined is automatically coerced to the global. This can cause many headfakes and pull-out-your-hair kind of bugs. In strict mode, referencing a a ```this``` value of null or undefined throws an error.

- Disallows duplicate parameter values. Strict mode throws an error when it detects a duplicate named argument for a function (e.g., ```function foo(val1, val2, val1){}```), thereby catching what is almost certainly a bug in your code that you might otherwise have wasted lots of time tracking down.

Note: It used to be (in ECMAScript 5) that strict mode would disallow duplicate property names (e.g. ```var object = {foo: "bar", foo: "baz"};```) but as of ECMAScript 2015 this is no longer the case.

- Makes ```eval()``` safer. There are some differences in the way ```eval()``` behaves in strict mode and in non-strict mode. Most significantly, in strict mode, variables and functions declared inside of an ```eval()``` statement are not created in the containing scope (they are created in the containing scope in non-strict mode, which can also be a common source of problems).

- Throws error on invalid usage of ```delete```. The ```delete``` operator (used to remove properties from objects) cannot be used on non-configurable properties of the object. Non-strict code will fail silently when an attempt is made to delete a non-configurable property, whereas strict mode will throw an error in such a case.


#### *Question: Consider the two functions below. Will they both return the same thing? Why or why not?*

```
function foo1()
{
  return {
      bar: "hello"
  };
}

function foo2()
{
  return
  {
      bar: "hello"
  };
}
```

*Answer:* 

Surprisingly, these two functions will not return the same thing. Rather:

```
console.log("foo1 returns:");
console.log(foo1());
console.log("foo2 returns:");
console.log(foo2());
```
will yield:

```
foo1 returns:
Object {bar: "hello"}
foo2 returns:
undefined 
```

Not only is this surprising, but what makes this particularly gnarly is that ```foo2()``` returns undefined without any error being thrown.

The reason for this has to do with the fact that semicolons are technically optional in JavaScript (although omitting them is generally really bad form). As a result, when the line containing the ```return``` statement (with nothing else on the line) is encountered in ```foo2()```, a semicolon is automatically inserted immediately after the return statement.

No error is thrown since the remainder of the code is perfectly valid, even though it doesn’t ever get invoked or do anything (it is simply an unused code block that defines a property bar which is equal to the string ```"hello"```).

This behavior also argues for following the convention of placing an opening curly brace at the end of a line in JavaScript, rather than on the beginning of a new line. As shown here, this becomes more than just a stylistic preference in JavaScript.


#### *Question: What is NaN? What is its type? How can you reliably test if a value is equal to NaN?*


*Answer:* 

The ```NaN``` property represents a value that is “not a number”. This special value results from an operation that could not be performed either because one of the operands was non-numeric (e.g., ```"abc" / 4```), or because the result of the operation is non-numeric.

While this seems straightforward enough, there are a couple of somewhat surprising characteristics of NaN that can result in hair-pulling bugs if one is not aware of them.

For one thing, although ```NaN``` means “not a number”, its type is, believe it or not, ```Number```:

```console.log(typeof NaN === "number");  // logs "true"```

Additionally, ```NaN``` compared to anything – even itself! – is false:

```console.log(NaN === NaN);  // logs "false"```

A semi-reliable way to test whether a number is equal to NaN is with the built-in function ```isNaN()```, but even using ```isNaN()``` is an imperfect solution.

A better solution would either be to use ```value !== value```, which would only produce true if the value is equal to NaN. Also, ES6 offers a new ```Number.isNaN()``` function, which is a different and more reliable than the old global ```isNaN()``` function.


#### *Question: What is NaN? What is its type? How can you reliably test if a value is equal to NaN?*

*Answer:* 

The ```NaN``` property represents a value that is “not a number”. This special value results from an operation that could not be performed either because one of the operands was non-numeric (e.g., ```"abc" / 4```), or because the result of the operation is non-numeric.

While this seems straightforward enough, there are a couple of somewhat surprising characteristics of NaN that can result in hair-pulling bugs if one is not aware of them.

For one thing, although ```NaN``` means “not a number”, its type is, believe it or not, ```Number```:

```console.log(typeof NaN === "number");  // logs "true"```

Additionally, ```NaN``` compared to anything – even itself! – is false:

```console.log(NaN === NaN);  // logs "false"```

A semi-reliable way to test whether a number is equal to NaN is with the built-in function ```isNaN()```, but even using ```isNaN()``` is an imperfect solution.

A better solution would either be to use ```value !== value```, which would only produce true if the value is equal to NaN. Also, ES6 offers a new ```Number.isNaN()``` function, which is a different and more reliable than the old global ```isNaN() ``` function.


#### *Question: What will the code below output? Explain your answer.*


```
console.log(0.1 + 0.2);
console.log(0.1 + 0.2 == 0.3);
```

*Answer:* 

An educated answer to this question would simply be: “You can’t be sure. it might print out ```0.3``` and ```true```, or it might not. Numbers in JavaScript are all treated with floating point precision, and as such, may not always yield the expected results.”

The example provided above is classic case that demonstrates this issue. Surprisingly, it will print out:

```
0.30000000000000004
false
```
A typical solution is to compare the absolute difference between two numbers with the special constant ```Number.EPSILON```:

```
function areTheNumbersAlmostEqual(num1, num2) {
	return Math.abs( num1 - num2 ) < Number.EPSILON;
}
console.log(areTheNumbersAlmostEqual(0.1 + 0.2, 0.3));
```

#### *Question: Discuss possible ways to write a function isInteger(x) that determines if x is an integer.*

*Answer:* 

This may sound trivial and, in fact, it is trivial with ECMAscript 6 which introduces a new ```Number.isInteger()``` function for precisely this purpose. However, prior to ECMAScript 6, this is a bit more complicated, since no equivalent of the ```Number.isInteger()``` method is provided.

The issue is that, in the ECMAScript specification, integers only exist conceptually; i.e., numeric values are always stored as floating point values.

With that in mind, the simplest and cleanest pre-ECMAScript-6 solution (which is also sufficiently robust to return false even if a non-numeric value such as a string or null is passed to the function) would be the following use of the bitwise XOR operator:

```function isInteger(x) { return (x ^ 0) === x; } ```

The following solution would also work, although not as elegant as the one above:

```function isInteger(x) { return Math.round(x) === x; }```

Note that ```Math.ceil()``` or ```Math.floor()``` could be used equally well (instead of ```Math.round()```) in the above implementation.

Or alternatively:

```function isInteger(x) { return (typeof x === 'number') && (x % 1 === 0); }```

One fairly common incorrect solution is the following:

```function isInteger(x) { return parseInt(x, 10) === x; }```

While this ```parseInt```-based approach will work well for many values of ```x```, once ```x``` becomes quite large, it will fail to work properly. The problem is that ```parseInt()``` coerces its first parameter to a string before parsing digits. Therefore, once the number becomes sufficiently large, its string representation will be presented in exponential form (e.g., ```1e+21```). Accordingly, ```parseInt()``` will then try to parse ```1e+21```, but will stop parsing when it reaches the ```e ``` character and will therefore return a value of ```1```. 
Observe:

```
> String(1000000000000000000000)
'1e+21'
```

```
> parseInt(1000000000000000000000, 10)
1
```
```
> parseInt(1000000000000000000000, 10) === 1000000000000000000000
false
```
