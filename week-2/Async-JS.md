# Asynchronous JavaScript - [Slides](https://hackmd.io/@SjkyAeAyRjSqv_tPCU-41A/rJ5UIzMWr#/)

**Team: Gigi, Tony, Franchie and Reuben :smile:**

---

## What are first class functions, and higher order functions?
JavaScript treats functions as first-class citizens. That’s because in JavaScript or any other functional programming languages functions are objects.

---


### **First class functions** 
These can be treated just like any other object (or data type), which means they can passed or returned as arguments. For example, you can have an array of functions:

---


```javascript
const sum = (x, y) => x + y;
const subtract = (x, y) => x - y;
const multiply = (x, y) => x * y;

const operations = [sum, subtract, multiply];
```
In the browser
```javascript
>operations
<(3)[ƒ, ƒ, ƒ]
0: (x, y) => x + y
1: (x, y) => x - y
2: (x, y) => x * y
```

---


### **Higher order functions** 
A Higher-Order function is a function that receives a function as an argument or returns the function as output. Kind of like nesting one function in another one. For example:
- map()
- filter()
- reduce()

---


For example:
```javascript
const arr1 = [1, 2, 3];
const arr2 = arr1.map(item => item * 2);
console.log(arr2);
```

Returns a new array after each integer has been multiplied by two.
```javascript
(3)[2, 4, 6]
0: 2
1: 4
2: 6

```

---

## What is a callback function? Give an example of a callback function and explain what happens when it is executed

- A callback is a function that is to be executed after another function has finished executing — hence the name ‘call back’. 


---


- Any function that is passed as a function to another function is a call back function.

---

- Callback functions ensure that one function doesn't exceute until a function it is dependant on has executred. 

---


Example:

```javascript=
myCoolFunction() {
 console.log(1);
};
```
```javascript=
anotherCoolerFunction() {
 console.log(2)
}
```
```javascript=

myCoolFunction();
anotherCoolerFunction();
```


---


# 1
# 2

---

```javascript=
function mySlowFunction(){
  setTimeout( =>{
    console.log(1);  }, 500 );
}
```
```javascript=
anotherCoolerFunction() {
 console.log(2)
}
```
```javascript=
mySlowFunction()
anotherCoolerFunction();
```

---


# 2
# 1

---

JS didn't wait for mySlowFunction to do it's thing before moving on myCoolerFunction.

Real world example 
```javascript=
twitter.get('the route of our request i.e. 
search tweets', search parameters i.e. all 
mentions of FAC17, function(err, data, response) 

{
  if(`there isn't an error`){
  `do some cool code we don't understand yet`
  } else {
    console.log(`the error`);
  }
})
```

---


Only when do we have a response from Twitter will our callback be invoked. 

---

## What is the call stack?

* A call stack is a **data structure** that uses the **Last In, First Out (LIFO)** principle to temporarily store and manage function invocation (call).

---

1. **data structure**  is a collection of data values, the relationships among them, and the functions or operations that can be applied to the data principles;

---

2. **LIFO** : When we say that the call stack, operates by the data structure principle of Last In, First Out, it means that the last function that gets pushed into the stack is the first to be pop out, when the function returns.

---

### Why is useful to understand what a call stack is:
An understanding of the call stack will give clarity to how “function hierarchy and execution order” works in the JavaScript engine.

---


### What it is used for?
The call stack is primarily used for function invocation (call). Since the call stack is single, function(s) execution, is done, one at a time, from top to bottom. It means the call stack is synchronous.

---

![img](https://miro.medium.com/max/1050/1*E3zTWtEOiDWw7d0n7Vp-mA.gif)

---

## Asynchronous vs Synchronous programming

---

### Synchronous programming:
- things happen one at a time. 
- When you call a function that performs an action, it returns only when the action has finished. 
- This stops your program from doing other things for the time the action takes.

---


### Asynchronous programming:
- allows multiple things to happen at the same time. 
- When you start an action, your program continues to run. 
- When the action finishes, the program is informed and gets access to the result (for example, the return value).
- other processes are allowed to start, and may even finish before the original task.

---

### Why asynchronous programming:
- synchronous code has the potential to block further execution until it has finished what it’s doing. 
- In English, long-running JavaScript functions can make the UI or server unresponsive until the function has returned. Obviously this can result in a terrible user-experience.

---

**JAVASCRIPT IS SYNCHRONOUS BY NATURE, BUT WE HAVE VARIOUS METHODS TO MAKE IT PERFORM TASKS ASYNCHRONOUSLY**
-these include callbacks, promises, async functions.

---

## References:
[Event loop](https://medium.com/@gaurav.pandvia/understanding-javascript-function-executions-tasks-event-loop-call-stack-more-part-1-5683dea1f5ec)
[First class and higher order functions](https://hackernoon.com/effective-functional-javascript-first-class-and-higher-order-functions-713fde8df50a)
[Higher order Functions](https://blog.bitsrc.io/understanding-higher-order-functions-in-javascript-75461803bad)
[Callbacks](https://codeburst.io/javascript-what-the-heck-is-a-callback-aba4da2deced)

---

That's it! 
![elf](https://media.giphy.com/media/3otPoS81loriI9sO8o/giphy.gif)

