# Objects and Prototypes

```javascript
var emp1 = {};
emp1.firstName = "Yana";
emp1.lastName = "Kryshchuk";

function createObject(firstName, lastName) {
  var emp2 = {};
  emp2.firstName = "Mia";
  emp2.laskName = "Candy";
  return emp2;
}
```
### Ways to call a function
```javascript
// 1
function foo(){
  console.log("Hello");
}
foo();

//2
var obj = {};
obj.foo = function(){
  console.log("Hello");
};
obj.foo();

// 3
new foo();

```


