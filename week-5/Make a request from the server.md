# Make a request from the server 


---

### XMLHttp Request -->

Allows you to make a request from the back-end in the same way you would from the front-end

```javascript=
var XMLHttpRequest = require("xmlhttprequest").XMLHttpRequest;
npm install xmlhttprequest --save
```



---



## 1 Request 

Doesn't use promises but is deprecated :confused:


---



## 2 Introduce other ways (using promises)

---

All of the below are using promises which we should not yet get into!

![](https://media.giphy.com/media/tSI5rlnyCM10s/giphy.gif)

---

1. Superagent
>SuperAgent is light-weight progressive ajax API crafted for flexibility, readability, and a low learning curve after being frustrated with many of the existing request APIs. It also works with Node.js!

---


Seems like it's quite easy to use 

``` 
npm install superagent
```
```javascript=
const superagent = require("superagent");
```

---


```javascript=
function handleHome(request, response) {
  superagent.get("https://picsum.photos/v2/list").end((err, res) => {
    console.log(JSON.stringify(res));
  });
}
```

---


Pros: 
- It has a plugin ecosystem where plugins could be built for extra functionality.
- Configurable.
- Nice interface for making HTTP requests.
- Multiple functions chaining to send requests.
- Works in both Browser and Node
- Has support for upload and download progress.
- Has support for chunked transfer encoding.
- Old-style callbacks are supported
- Numerous plugins available for many common features

---

Cons: It’s API doesn’t adhere to any standard.




---




## Fetch 

- native browser API for making requests.

---


Pros
- It’s flexible and easy to use
- Uses promises to avoid callback hell
- Supported by all modern browsers
- Follows request-response approach
- It has a nice and simple syntax

---

Cons
- Doesn’t work in serverside
- Lacks some nice features of developed libraries like canceling requests.
- It doesn’t have built-support for defaults like mode of a request, headers, credentials.

---

The fetch function takes one required parameter: the endpoint URL. It also has other optional parameters as in the example below:

![](https://i.imgur.com/avXT35S.png)

---

within fetch there are other modules and plugins that allow us to send and receive a request to and from the server side, such as axios and nodefetch.


---

## NodeFetch

- a minimal code for a window.fetch compatible API on Node.js runtime.

see code: 
![](https://i.imgur.com/xnLOXIF.png)



---

## Axios 

- Promise-based HTTP client for the browser and node.js
- Using Promises is good when dealing with code that has a complicated / asynchronous chain of events
- Axios also parses JSON responses by default (like SuperAgent)




---



- There are two ways to include Axios in your project.
- You can use npm:
```
$ npm install axios
```
- Or you can include axios using a CDN: 
```
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```



---



- With Axios you can use GET and POST to retrieve and post data from the server. You can see GET here:

![](https://cdn-media-1.freecodecamp.org/images/1*4wmqiPsSN5mdgjJiRaKVZg.png)


---



Pros: 
- It works on both Nodejs and Browser
- Supports Promise API
- Can set or cancel a request
- Can set a response timeout
- Supports protection against Cross-site request forgery, XSRF.
- Can intercept requests or responses before they are carried out.
- Has support for upload progress
- Widely used in React and Vue projects.


---

Cons: 
- Seems to be some debate about whether it is easier or more difficult to use than superagent and fetch


---


## 3 Pro's and Con's / When to use which method / References


Compares pros and cons of JavaScript HTTP Requests Libraries: https://blog.bitsrc.io/comparing-http-request-libraries-for-2019-7bedb1089c83

5 most popular http request libraries according to free code camp:
https://www.freecodecamp.org/news/here-is-the-most-popular-ways-to-make-an-http-request-in-javascript-954ce8c95aaa/

https://attacomsian.com/blog/http-requests-in-nodejs

---


