# Advanced JavaScript
> https://developer.mozilla.org/en-US/docs/Web/JavaScript

> https://github.com/rwaldron/idiomatic.js

Function is compiled "just in time" when it is asked to be executed, otherwise its compilation is just skipped. <br>
At first we look at the local scope - if we don't find our variable there - we go beyond.

```javascript
var foo = "bar";

function bar() {
    var foo = "baz";
    function baz(foo) {
        foo = "bam";
        bam = "yay";
    }
    baz();
}

bar();
foo;    // "bar"
bam;    // "yay"
baz();  // Error
```

Declaration starts from the ```function``` keyword. Otherwise it is expression:
```javascript
var foo = function bar() {
    var foo = "baz";
    function baz(foo) {
        foo = bar;
        foo; // function
    }
    baz();
  }

  foo();
  bar();  // Error! it does not exist outside of its scope (because it was expression, not declaration)
```
```(function(){.....``` is an expression (starts with ```(```)

#### Anonymus function *expression* (without a name) is not okay!
Anonymus functions don't play well in debugging. <br>
Don't use ```eval()```!

#### Immediately-Invoked Function Expression (IIFE)

> http://benalman.com/news/2010/11/immediately-invoked-function-expression/

Immediately executing the value of the expression.
```javascript
(function(){
  var foo = "foo2";
  console.log(foo); // "foo2"
})();

console.log(foo); // "foo"
```
- ```var``` - variable attached to function, available for whole function
- ```let``` - variable attached to the block of code (ie. ```for()``` loop)
<br>
- undefined - currently doesn't have a value
### Hoisting
Declaration of a variable or function are "moved to the top" because at first while compiling, compiler is searching for declarations. <br>
**Mutual recursion** - 2 or more functions are calling each other. It is not possible without hoisting because one function is always declared after another.
> Everything is a *reference*!




