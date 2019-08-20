# Session-management in Express

---

## What are sessions?

- By default an **HTTP request cannot remember** or keep track **of** what **requests** came **before** it.


- But sometimes its necessary for both the client and server to **remember the state** when sending requests and returning responses(**eg: when a user is logged in**).

---

#### Stateful and stateless

- Last week we talked about **stateful vs stateless** authentication, and we implemented stateless authentication with JWTs.

- the user's state(in our projects this was logged_in=true) is stored in the JWT on the **CLIENT SIDE** 
    
#### What does the browser do?(stateless)

- It **VERIFIES** that these details have not been tampered with **(the state is never stored on the server)**

---

#### Is there another way to do this?

![](https://media.giphy.com/media/3oz8xRF0v9WMAUVLNK/giphy.gif)


---

### Stateful Authentication
- The other way to do this is by **storing the client's state**(logged_in boolean or anything else really) **on the SERVER**

---

#### Well, Simple explanation(stateful)
1) A **session id**(which is usually a string or a number) is **sent as a cookie** to the client
2) The session id is a **reference to** the state data, remember that this data is **stored on the server**
3) Every time the client makes a request, the session id **is sent as a header**, and the **server looks for** the user state **matching** that session id.

---

### This is what sessions are!
- A way to identify the source of a request
- And provide the corresponding responses.

![](https://media.giphy.com/media/L4LyIV6L8E4Du/giphy.gif)


---


## What are the different ways of managing sessions in express?


---

## Cookie-session 


Cookie-session is a simple / lightweight cookie-based  session implementation.


---

This module stores the session data on the client within a cookie, while a module like express-session stores only a session identifier on the client within a cookie and stores the session data on the server, typically in a database.


---


### Cookie-session

* does not require any database / resources on the server side, though the total session data cannot exceed the browser's max cookie size,
* can simplify certain load-balanced scenarios,

---
 
 #### How do I install it
`
$ npm install cookie-session
`



---


```javascript
var cookieSession = require('cookie-session')
var express = require('express')
 
var app = express()

app.use(cookieSession({
  name: 'session',
  keys: [insert secret keys]
}))
 
app.use(function (req, res, next) {
  var n = req.session.views || 0
  req.session.views = n++
  res.end(n + ' views')
})
 
app.listen(3000)
```
keys refer to secrets to sign your cookie with.
cookieSession automatically generates your sessiondata, signs it with the secret, and stores it in a global session object





---

### Using the `express-session` module

Stateful session management, so only user identifier (session id) is stored in a cookie and actual session data is stored in one of the storage options.

requires a secret, and the sessionid is signed(encrypted) before setting the cookie, and decrypted when the server is checking for a session.

---

```javascript
cont session=require('express-session')
app.use(session({secret:'fac17'}));

```

---

`express-session` middleware inserts another object into `req` object called `session`, that will be available for each request
We can manipulate like any other object

```
req.session.whatever='you want';
```

---

#### Different Stores

by default MemoryStore but there are others include: session-file-store,  express-mysql-session, connect-redis 

```javascript
const session=require('express-session');
const fileStore=require('session-file-store')(session)
app.use(session( { secret:'fac17', store:fileStore( {path:'./sessions'}) }))
```

---

## Create a minimal example of how to set up a session: the counter 

---

#### When a user visits the site:
- It creates a new session for the user  
- Assigns them a cookie 
- Next time the user comes
- The cookie is checked 
- The page_view session variable is updated accordingly


---

```javascript
const express = require('express');
const session = require('express-session');
const app = express();
```

---

```javascript=
// initiate session middleware
app.use(session({secret: "Shh, its a secret!"}));

app.get('/', function(req, res){

   // req.session is preserved between requests
   if(req.session.page_views){
      req.session.page_views++;
      res.send("You visited this page " + req.session.page_views + " times");
   } else {
      req.session.page_views = 1;
      res.send("Welcome to this page for the first time!");
   }
});
app.listen(3000);

```

---

Now if you run the app and go to localhost:3000, the following output will be displayed.

![](https://i.imgur.com/aGaoeWO.png)

---

If you revisit the page, the page counter will increase. The page in the following screenshot was refreshed 42 times.

![](https://i.imgur.com/vqf2lDc.png)

---

## RESOURCES
[manage-session-using-node-js-express](https://codeforgeek.com/manage-session-using-node-js-express-4/)
[express session](https://www.tutorialspoint.com/expressjs/expressjs_sessions.htm)
[The polyglote deveoper](https://www.thepolyglotdeveloper.com/2015/01/session-management-expressjs-web-application/)

https://flaviocopes.com/express-sessions/

https://dzone.com/articles/securing-nodejs-managing-sessions-in-expressjs

https://www.npmjs.com/package/cookie-session
