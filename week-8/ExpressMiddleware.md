# Express Middleware :electric_plug:

---

## What are express middlewares? :nut_and_bolt:

---

An Express application is essentially a series of middleware function calls.

Middleware functions are functions that have access to the request object (req), the response object (res), and the next middleware function in the application’s request-response cycle. The next middleware function is commonly denoted by a variable named next.

---

![pic](https://miro.medium.com/max/1400/1*wIkLR_9twvmG-LitHYoftw.png)

---

![](https://media.giphy.com/media/V0IdVIIW1y5d6/giphy.gif)

---

If the current middleware function does not end the request-response cycle, it must call next() to pass control to the next middleware function. Otherwise, the request will be left hanging.

---

![pic2](https://miro.medium.com/max/1400/1*ptNjzuT0m2BQ9YpQTVwVLg.png)

---

## What functionality do they provide?:wrench:

---

Middleware functions can perform the following tasks:

* Execute any code.
* Make changes to the request and the response objects.
* End the request-response cycle.
* Call the next middleware function in the stack.

---

An Express application can use the following types of middleware: :clipboard:

1. Application level middleware
```app.use & app.METHOD```
3. Router level middleware
```router.use & router.METHOD```
5. Built-in middleware 
```express.static,express.json,express.urlencoded```
7. Error handling middleware
```app.use(err,req,res,next)```
9. Thirdparty middleware
```bodyparser,cookieparser```

---

 
:construction_worker: These middleware and libraries are officially supported by the Connect/Express team:

---

![](https://i.imgur.com/ILaqMeH.png)



---


![](https://i.imgur.com/OVq53OJ.png)

---

These are some additional popular (third party) middleware modules:

![](https://i.imgur.com/WXi6BQt.png)





---


## What are some examples of useful express middleware and how do you use them 

---

## Third-party middleware :cop:

---

![](https://media.giphy.com/media/iNhZJcINSJVPKeXQ9D/giphy.gif)

---

```javascript
let cp = require('child_process'); 
// Forking a separate Node.js processes
let responseTime = require('response-time'); 
// For code timing checks for performance logging
let assert = require('assert'); 
// assert testing of values
let helmet = require('helmet'); 
// Helmet module for HTTP header hack mitigations
let RateLimit = require('express-rate-limit'); 
// IP based rate limiter
let csp = require('helmet-csp'); 
//Content Security Policy helps prevent unwanted content being injected into your webpages
let cookieParser = require('cookie-parser')

// load the cookie-parsing middleware
app.use(cookieParser())

```

---

```javascript
// Apply limits to all requests 
var limiter = new RateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes 
  max: 100, // limit each IP to 100 requests per windowMs 
  delayMs: 0 // disable delaying - full speed until the max limit is reached 
});
app.use(limiter);
```

---

```javascript

app.use(helmet()); // Take the defaults to start with
app.use(csp({
  // Specify directives for content sources
  directives: {
    defaultSrc: ["'self'"],
    scriptSrc: ["'self'", "'unsafe-inline'", 'ajax.googleapis.com', 'maxcdn.bootstrapcdn.com'],
    styleSrc: ["'self'", "'unsafe-inline'", 'maxcdn.bootstrapcdn.com'],
    fontSrc: ["'self'", 'maxcdn.bootstrapcdn.com'],
    imgSrc: ['*']
    // reportUri: '/report-violation',
  }
}));

```

---

```javascript
// Adds an X-Response-Time header to responses to measure response times
app.use(responseTime());

```

---

```javascript
// Sets up the response object in routes to contain a body property with an object of what is parsed from a JSON body request payload
// There is no need for allowing a huge body, it might be some type of attack, so use the limit option
app.use(bodyParser.json({ limit: '100kb' }));
```

---

```javascript
//
// MongoDB database connection initialization
//
var db = {};
var MongoClient = require('mongodb').MongoClient;

//Use connect method to connect to the Server
MongoClient.connect(process.env.MONGODB_CONNECT_URL, { useNewUrlParser: true }, function (err, client) {
  assert.equal(null, err);
  db.client = client;
  db.collection = client.db('myDBname').collection('myDBcollectionName');
  console.log("Connected to MongoDB server");
});
```

---

### Error Handling

---


Error-handling middleware always takes four arguments. You must provide four arguments to identify it as an error-handling middleware function. Even if you don’t need to use the next object, you must specify it to maintain the sytax. Otherwise, the next object will be interpreted as regular middleware and will fail to handle errors.

---

example:
```javascript
exports.server = (err, req, res, next) => {
  res
    .status(500)
    .sendFile(path.join(__dirname, '..', '..', 'public', '500.html'));
};

```

---

![image alt](https://media.giphy.com/media/UIYxK5He3Z5Sg/giphy.gif)

---


## References:

https://expressjs.com/en/guide/using-middleware.html
