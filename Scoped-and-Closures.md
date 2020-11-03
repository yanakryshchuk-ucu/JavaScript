# Scopes and Closures

Two ways to create a function:
- declaration
```javascript
function foo(){
  console.log("Function foo called");
}
```
- expression
```javascript
var bar = function(){
  console.log("Function foo called");
}

// calling
foo();
bar();
```
## Scopes
A scope dictates a portion of the program where a particular variable is accessible when a particular variable makes sense. 
If the variable in a particular scope is accessed outside the scope, it doesn't exists.

```javascript
var a = 10;

```
If you need to use a variable only in one place, there is no need to make it visible for all components of the code.
After the result is achieved, the variables are no more accessable outside the "box" they were used in.
<br>
**How to create a scope?**

```javascript
{
  // !!! this is not a scope !!!
}
______________________

if(100 == 100){
  // !!! this is not a scope !!!
}
```
Any code you put in that block is going to have the scope which this block extends. Block ends - scope ends.\
However, **The block does not create a scope in JS**! \
In JS scoping is based on functions. 
```javascript
var name = "Yana";

if (name === "Yana") {
  var depatrment = "IT";
}
console.log(name);
console.log(department); // IT
```
If the block created a new scope, then the result of `console.log(department);` would be undefined variable.\
**Now we are going to create an actual scope**
```javascript
function allocateDepartment() {
  if (name === "Yana") {
    var depatrment = "IT";
  }
}

allocateDepartment(); 
console.log(department); // RUNTIME ERROR. It is not available outside the function, 
                         // because the function created the scope.
```
However **Whatever is available outside the function, is available inside !**\
## `"use strict"`
We use strict mode to prevent from being created variables when you do write operation on undeclared variable.\
Example:
```javascript
var myName = "";
myName = "Yana";

// "Yana"
```
```javascript
"use strict";
var myName = "";
myName = "Yana";

// ReferenceError: undeclared variable myName
```
In the example below only the function will be executed in strict mode:
```javascriptode() {
  "use strict";
  var myName = "";
  myName = "Yana";
}
```
**Try using strict mode everywhere!!!**\
### Copy of the variable
The variable created during first execution of a function is different from a variable created during second execution.

### Closures in Callbacks
Execution with timeout
```javascript
var a = 10;
var fn = function() {
  console.log(a);
}
 // wait for 1 second
 setTimeout(fn, 1000); // (parameter we need to execute, time in miliseconds)
 
console.log("Done");

// Done
// 10 (in 1 second after Done)
```
```javascript
var i;
for (i=0;i<10;i++){
  (function(current){
  setTimeout(function(){
  console.log(current);
  }, 2000);
})(i);
}

// 0
// 1
// 2
// 3
// 4
// 5
// 6
// 7
// 8
// 9
```



