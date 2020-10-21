# JavaScript REST APIs: Getting Started

### Creating a responsive server
```javascript
// bring in the express server and create application
// the require() function resolves libraries and modules in the Node search path (usually \node_modules).
let express = require('express');
// the express() function creates an Express application. Many other objects are created from this application object.
let app = express();

// Use the express Router object
let router = express.Router();

// Create GET to return a list of all pies
router.get('/', function(req, res, next){ // request-response-next objects
    res.send("Cherry Pie");
});

// Confihure router so all routes are prefixed with /api/v1
// all REST APIs in this server are called http://localhost:5000/api/
app.use('/api/', router);

// Create server to listen on port 5000
// The listen() method listens for connections on the host and the port number.
var server = app.listen(5000, function(){
    console.log('Node server is running on http://localhost:5000..');
});
```
Commands for terminal in Visual studio code:
```javascript
$ npm init 
/*
{
  "name": "bethanyspiesapi",
  "version": "1.0.0",
  "description": "REST APIs for Bethanys Pie Shop",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Yana",
  "license": "ISC"
}
*/
$ npm install express nodemon -save
$ npm start
```
In postman we make a GET Request to pur server ie ```http://localhost:5000/api/``` and **Send** it. <br>
Each time after we make changes in our ```index.js``` file and press **Send**, the output on the server will change. 

