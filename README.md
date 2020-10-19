# JavaScript

## Conspects 

Attach js file to index.html file (at the bottom of the file):
```bash 
<script src="./filename.js"></script>
```
Pr simply put js code between
```
<scrip> </script>
```

Utils:

1. Create a function
```bash
function showMessage(message) {
    document.getElementById('message').textContent = message;
}
```
2. Attach both files
```
<script src="./utils.js"></script>
<script src="./home.js"></script>
```
3. Write a message in home
```
showMessage("Title...");
```
4. Ad id to the element in index.html file. "GET A GRIP" will change to "Title..."
```
 <h1 id="message" class="col-sm-12">GET A GRIP</h1>
 ```


JavaScript is Case Sensitive !

Declaring a variable:
```
let total = 144;
```
Declaring multiple variables:
```
let welcome = 'Welcome',
    available = true,
    price = 144;
```

Declaring constant variable - you cannot change its value:
```
const price = 40;
```
Usage of ```var``` - not recommended to use:

```
// error occures - declaring variable after statement
showMessage(welcome);
let welcome = 'Welcome';

// no error occures
showMessage(welcome);
var welcome = 'Welcome';
```

```
let name = 'Yana';
let greeting = `Hello ${name}`;
```

Creating an object:
```
let person = {
    firstName: 'Yana',
    lastName: 'Kryshchuk'
};
// show on web page firstName
showMessage(person.firstName);
```

if() Statement

```
if(5>2){
    console.log('Yes'); // will be written in console
}
```
if() else Statement
```
if(5>25){
   showMessage('true');
}
else if (true){
    showMessage ('now true');
}

else{
    showMessage('check')
}
```


```!==``` - not equal to !
```===``` - equal sign
```
(1 === '1')  // false, use when compare different types
(1 !== '1') // false

(1 == '1') // true - because types are converted
(1 != '1') //false
```
The Ternary Operator
```
// condition ? true-statement : false-statement

let message = (price > 10) ? 'expensive' : 'cheap';
showMessage(message); //expensive
```

It is not possible to access a variable created in a block of code but it is possible with ```var``` - not recommended!

for(Loop)
```
for (let i = 0; i < 3; i++){
    console.log(i);
} 
//0 1 2
```

do ... while() Loop - makes sure the loop executes at least once
```
let count = 1;
do {
    console.log(count);
    count++;
} while (count < 5);
// 1 2 3 4
```

## Functions
Function declaration
```
function showMessage {
    console.log('in a function');
}

showMessage();
```
Function expressions
```
let fn = function(){
}
fn();
```

```
**example 1**
function showMessage(message){
    console.log(message);
}
showMessage('First message');

**example 2**
function showMessage(message1, message2){
    console.log(message1, message2);
}
showMessage('First',  'Second');
```
Return
```
function getSecretCode(value){
    let code = value * 42;
    return code;
}
console.log(getSecretCode(2)); //84
```
## Object properties
```
let mySymbol = Symbol(); // used to createhidden information in an object.

let person = {
    name: "John",
    age: 32,
    pertTime: false,
    [mySymbol]: 'secretInformation'
};
console.log(person.age); // 32

person.age = 44; or
person['age'] = 44;

showMessage(person.age); //44
showMessage(person[mySymbol]); // secretInformation
```
Adding a method to the object:
```
let person = {
    name: "John",
    age: 32,
    pertTime: false,
    showInfo: function(){
        showMessage('in showInfo');
    }
};
person.showInfo(); // in showInfo
```
Use ```this.name``` if you want to access the ```name``` inside of an object.

## Moderating the web-page buttons

```
const button = document.getElementById('see-review');
button.addEventListener('click', function(){
    const review = document.getElementById('review');
    if (review.classList.contains('d-none')){
        review.classList.remove('d-none');
        button.textContent = 'CLOSE REVIEW';
    }
    else {
        review.classList.add('d-none');
        button.textContent = 'SEE REVIEW';
    }
    
});
```
Before that we made some changest in ```index.html```:
```
// add an id
 <a id="see-review" class="btn btn-default">See Review</a>
 
 //add div molule
 
 <div id="review" class="container d-none">
            <h4>Review Title...</h4>
            <p>Review text...</p>
        </div>
```
## Creating and initializing arrays

https://developer.mozilla.org/uk/docs/Web/JavaScript/Reference/Global_Objects/Array
```
let values = [1, 2, 3]; or
let values = Array.of(1, 2, 3);
``` 
```values.push(4 ,5); // 1, 2, 3, 4, 5``` - add element to the end of the array
```values.pop(); // 1, 2``` - remome the last element
```values.shift(); // 2, 3``` - returns the first element of the array and after that the array contains elements without the first one
```values.unshift('lol', 'kek'); // lol, kek, 1, 2, 3``` - puts an element to the zero position in the array
```values.slice(1, 2); // 2``` - slice from... to except of what is in the middle

```values.splice(1, 1); // 1, 3``` - cut from... to

* 1st index - element you want to delete
* 2nd index - number of items you want to delete
* 3rd index - item you want to insert
```
const values = ['a', 'b', 'c'];
values.splice(1, 0, 'foo');
console.log(values); // a foo b c
```
## filter()
```
const values = ['a', 'b', 'c'];
const set = values.filter(function(item){
    return iter > 'b';
});
console.log(set); // c
```
## find() 
Finds *the first* item that matches the criteria, never goes further once it does.
```
const values = ['a', 'bbb', 'c'];
const found = values.find(function(item){
    return item.lenhth > 1;
});
console.log(found); // bbb
```
## forEach()
```
const values = ['a', 'b', 'c'];
values.forEach(function(item) {
    console.log(item);
});
// a b c
```
## Access elements in html code
```
const containers = document.getElementsByClassName('container'); // access all in index.html which class name is "container"
containers[0].classList.add('d-none'); // remove the certain element from view on the web page
console.log(containers);
```
