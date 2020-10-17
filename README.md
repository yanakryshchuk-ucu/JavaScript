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
Usage of ```var```:

```
// error occures - declaring variable after statement
showMessage(welcome);
let welcome = 'Welcome';

// no error occures
showMessage(welcome);
var welcome = 'Welcome';
```
