# JavaScript REST APIs: Getting Started

## Creating an express responsive server
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

## Retrieve and search for data using REST API Methods
### Create array of data to return

```javascript
// *******NEW******* //
let pies = [
    {"id": 1, "name": "Apple"},
    {"id": 2, "name": "Cherry"},
    {"id": 3, "name": "Peach"}
]; 

router.get('/', function(req, res, next){ // request-response-next objects
    // *******NEW CHANGES******* //
    res.send(pies);
});
```
After we refresh server, we see there new changes in the output.
#### Sending status code to server:
```javascript
 res.status(200).send(pies); // 200 is a code
```
### Adding json envelope and passing that pack from REST API
```javascript
res.status(200).json({ // passing json object
        "status": 200,
        "statusText": "OK",
        "message": "All pies retrieved.",
        "data": pies
    });
});
```
### Create a module for a data
We created a new folser *repos* and *pieRepo.js* inside of it.
```jvascript
let pieRepo = {
    get: function() {
        return [
            {"id": 1, "name": "Apple"},
            {"id": 2, "name": "Cherry"},
            {"id": 3, "name": "Peach"}
        ];
    }
};

module.exports = pieRepo;
```
Then in *index.js* we add line ```let pieRepo = require('./repos/pieRepo');```. Also:
```javascript
// Change this module 
let pies = [
    {"id": 1, "name": "Apple"},
    {"id": 2, "name": "Cherry"},
    {"id": 3, "name": "Peach"}
]; 
// to
let pies = pieRepo.get();
```
**Now the data is in a separate module!** (in pieRepo.js file)

### Read data from a file
We add simple json file to one more new folder *assets*. Then modify the *pieRepo.js* to
```javascript
// fs - built in Node module that knows how to work with reading and writing files
let fs = require('fs');

// create a filename
const FILE_NAME = './assets/pies.json';

let pieRepo = {
    get: function(resolve, reject) {
        fs.readFile(FILE_NAME, function(err, data){
            if(err){
                reject(err);
            }
            else{
                resolve(JSON.parse(data));
            }
        });
    }
};
module.exports = pieRepo;
```
In *index.js* we get rid of ```let pies = pieRepo.get();```. Then we modify blocks:
```
router.get('/', function(req, res, next){ // request-response-next objects
    // *******NEW CHANGES******* //
    pieRepo.get(function(data){
    res.status(200).json({ // passing json object
        "status": 200,
        "statusText": "OK",
        "message": "All pies retrieved.",
        "data": data // PIES -> DATA
    });
    } function(err){
        next(err);
    });
});
```
### Get a single piece of data

