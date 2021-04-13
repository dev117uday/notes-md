---
description: express is slow
---

# Express.js : FreeCodeCamp

## Basic Node and Express

### Getting Started

#### Install Express from NPM

```bash
npm i express
```

#### Import Express in .js function file

```javascript
var express = requier("express");
var app = express();
```

#### Simple GET request path

```javascript
app.get("/",(req,res)=>{
    res.send("Hello Express");
})
```

### Methods to send back data

**to send a simple string**

```javascript
res.send("string")
```

**to send a HTML file**

```javascript
let pathToFile = __dirname + "/views/index.html"
res.sendFile(pathToFile)
```

**to send a json response**

```javascript
res.json({"msg":"hello json"})
```

### Serve Static Assets

An HTML server usually has one or more directories that are accessible by the user. You can place there the static assets needed by your application \(stylesheets, scripts, images\). In Express, you can put in place this functionality using the middleware `express.static(path)`, where the `path` parameter is the absolute path of the folder containing the assets. If you don’t know what middleware is... don’t worry, we will discuss in detail later. Basically, middleware are functions that intercept route handlers, adding some kind of information. A middleware needs to be mounted using the method `app.use(path, middlewareFunction)`. The first `path` argument is optional. If you don’t pass it, the middleware will be executed for all requests.

**Serve static assets**

```javascript
app.use(express.static(__dirname + "/public"))
```

### Middleware

**Implement a Root-Level Request Logger Middleware**

Middleware functions are functions that take 3 arguments: the request object, the response object, and the next function in the application’s request-response cycle. These functions execute some code that can have side effects on the app, and usually add information to the request or response objects. They can also end the cycle by sending a response when some condition is met. If they don’t send the response when they are done, they start the execution of the next function in the stack. This triggers calling the 3rd argument, `next()`.

```javascript
app.get("/json",(req,res,next)=>{
  let str = req.method + " " + req.path + " = " + req.id;
  console.log(str);
  next();
})
```

**Chain Middleware**

Middleware can be mounted at a specific route using `app.METHOD(path, middlewareFunction)`. Middleware can also be chained inside route definition.

Example :

```javascript
app.get("/now",(req, res, next) => {
    req.time = new Date().toString();
    next();
  }, (req, res) => {
    res.send({time: req.time});
  }
);
```

### Getting data from GET and POST request

**To get string from GET request**

```javascript
app.get("/:word/echo",(req,res) => {
  let word = req.params.word;
  res.json({ "echo":word })
})
```

**Get input from client - Query parameters**

```javascript
app.get("/name",(req,res) => {
  let firstName = req.query.first;
  let lastName = req.query.last;
  res.json({ "name":`${firstName} ${lastName}` })
})
```

**Extracting data from POST request body**

```javascript
app.post("/name", function(req, res) {
  var string = req.body.first + " " + req.body.last;
  res.json({ name: string });
});
```

### Add body parser to parse POST Request

**Install using NPM**

```text
npm i body-parser
```

**Importing the required dependency**

```javascript
var bodyParser = require("body-parser");
```

All you need to do for this challenge is pass the middleware to `app.use()`. Make sure it comes before the paths it needs to be used on. Remember that body-parser returns with `bodyParser.urlencoded({extended: false})`. Use the following as a template:

```javascript
app.use(bodyParser.urlencoded({ extended: false }));
```

In order to parse JSON data sent in the POST request, use `bodyParser.json()` as the middleware as shown below

```javascript
app.use(bodyParser.json());
```

[Go Back](node-express-fcc.md)

