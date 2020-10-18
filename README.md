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
