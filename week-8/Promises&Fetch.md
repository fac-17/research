# Promises and fetch

---

## What is a promise?

![](http://giphygifs.s3.amazonaws.com/media/b44FwP4st6v3G/giphy.gif)

---

Coined by Barbara Liskov 

![](https://i.imgur.com/s5KfOg6.png)

---

and Liuba Shrira in 1988.

![](https://i.imgur.com/cfNfQzG.png)

---

A promise is a **special JavaScript object** that may produce a single value some time in the future: 
- either a resolved value, 
- or a reason that it’s not resolved (e.g., a network error occurred). 


---

A promise links a “producing code” and a “consuming code” together.
- **producing code**: code that takes time and produces a promised result.
- **consuming code**: waits for result of the producing code and does something with it.


---

## constructor syntax  :construction_worker: 
```JavaScript
let promise = new Promise(function(resolve, reject) {
  // executor (the producing code, "singer")
});
```

---


The promise object returned by new Promise constructor has internal properties
- **state** — initially "pending", then changes to either "fulfilled" when resolve is called or "rejected" when reject is called.
- **result** — initially undefined, then changes to value when resolve(value) called or error when reject(error) is called.


---


![](https://i.imgur.com/Zf3VCIw.png)


---

A pending promise may transition into a fulfilled or rejected state. 

Once settled, it must have a value that must not change and cannot be resettled.

Calling resolve() or reject() again will have no effect. 

The immutability of a settled promise is an important feature.

---

Promises are eager... 

---

![](https://media.giphy.com/media/W6G93p1LQZSVufqkAo/giphy.gif)

---

Will start doing whatever task you give it as soon as the promise constructor is invoked.


That means the executor runs automatically once the promise is created. The executor should do a job, then call resolve or reject to change the state of the corresponding promise object.


---

## Promises vs callbacks: Advantages :+1: 


---


**Readability**
- they reduce the amount of nested code
- they allow you to visualize the execution flow easily

---



**Error handling**: let you handle all errors at once at the end of the chain



---


**Simultaneous callbacks**: with Promise.all you can fire off two (or many) promises at the same time if the operations aren’t dependent on each other, but both results are needed to perform a third action.



---

```Javascript
const friesPromise = getFries()
const burgerPromise = getBurger()
const drinksPromise = getDrinks()

const eatMeal = Promise.all([
  friesPromise,
  burgerPromise,
  drinksPromise
])
  .then([fries, burger, drinks] => {
    console.log(`Chomp. Awesome ${burger}! 🍔`)
    console.log(`Chomp. Delicious ${fries}! 🍟`)
    console.log(`Slurp. Ugh, shitty drink ${drink} 🤢 `)
  })
```


---


## Promises vs callbacks: Disadvantages :-1: 


---


There's nothing promises can do that callbacks can't do, but there are things that promises can't do, such as: 

- Synchronous notifications.
- Notifications that may occur more than once (need to call the callback more than once). Promises are one-shot devices and cannot be used on repeat.


---


Running code that contains promises can be slower than running code that is using callbacks, this might improve over time though.


---

## Promises vs (async/await): Disadvantages :-1: 


---


There is a new kid in town: async/await. It's syntactic sugar on top of promises but in some cases it works really well. (There's a lot of debate!)

---

Example using promises:

```javascript=
const makeRequest = () =>
  getJSON()
    .then(data => {
      console.log(data)
      return "done"
    })

makeRequest()
```

---

Same example using async/await: 
```javascript=
const makeRequest = async () => {
  console.log(await getJSON())
  return "done"
}

makeRequest()
```


---



## What is fetch?

![fetch](https://media.giphy.com/media/NBFWQBHEEj1bG/giphy.gif)

---

The Fetch API is a web API that provides an interface for fetching resources asynchronously (API requests). It will seem familiar to anyone who has used XMLHttpRequest, but the new API provides a more powerful and flexible feature set.

---

![](https://i.imgur.com/wqi1YKX.png)

It has good support across the major browsers, except IE.

It's for front end API calls but you can use node-fetch on the backend. 


---

## How do you use it?

* The fetch() method takes one mandatory argument - the path to the resource you want to fetch
* It returns a Promise that resolves to the Response to that request, whether it is successful or not
* You can also optionally pass in an init options object as the second argument (see Request).

---

#### Example 

```javascript=
fetch('http://example.com/movies.json')
  .then(function(response) {
    return response.json();
  })
  .then(function(myJson) {
    console.log(JSON.stringify(myJson));
  });
```

---

## Fetch: advantages and disadvantages

---

#### Advantages:

* Simpler syntax
* Promise based - meaning it's easier to write cleaner asynchronous code.
* It has a neat definition for what a request is, and what a response is.

---

![clean code](https://media.giphy.com/media/uWzDsAsRm2X9qULHLs/giphy.gif "tidying" =x280) ![promise](https://media.giphy.com/media/l2YWC4zX9KXTgcbq8/giphy.gif "promise" =x280)

---


#### Disadvantages: 

* By default, it doesn’t send cookies might be an initial source of confusion to some. Authentication needs to be handled manually. 

![cookies](https://media.giphy.com/media/tCWMUAuZLMvKg/giphy.gif "title" =x140)



---

## Resources

* https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261
* https://www.quora.com/What-are-the-benefits-of-the-Fetch-API-over-AJAX-xmlhttprequest 
* https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch

---

* https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API
* https://flaviocopes.com/fetch-api/
* https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9
* https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch

---
