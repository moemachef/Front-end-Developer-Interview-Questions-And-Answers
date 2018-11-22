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
*Answer:* `undefined`, because we didn't pass the text argument to the function after it has been declared outside the function and we console log the text before it was declared inside the function


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

var does not have block scope. Therefore, it can lead to unpredictable behavior if you’re not careful (due to hoisting).
ES6 gave us 2 new ways to define variables, each of which has block scope. The key here is block scope.
We better use let to define the variable i. The expected behavior is that you are declaring the i variable to act as an index or loop counter within the for loop only. Therefore, you’d want that variable to only work within that for code block, meaning within the for curly braces.
It makes our code more readable and predictable. We are declaring that this variable has this specific scope, i.e. where we defined it.



#### *Question: What is the value of `window.foo`?*
```javascript
( window.foo || ( window.foo = "bar" ) );
```

*Answer:* Always `'bar'`

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
