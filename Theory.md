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
### Scopes
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
However **Whatever is available outside the function, is available inside !**











