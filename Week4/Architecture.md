Week 4 Research - Topic: Architecture 
===
Much of the Internet is based on the client-server model. In this model, user devices communicate via a network with centrally located servers to get the data they need, instead of communicating with each other.




---

## 1. Separation of concerns: What kind of tasks are normally handled in the back end, and which are more usually handled in the front end? Why?

---

### What is separation of concerns?

Separation of concerns is the idea that each module or layer in an application should only be responsible for one thing and should not contain code that deals with other things.

Repetition should be avoided. Keep code DRY (Don’t Repeat Yourself) instead of WET (Write Everything Twice).

---

### Why does separation of concerns exist?

Separating concerns reduces code complexity by breaking a large application down into smaller units with distinct, readable functions. This is a way of maintaining order.

"If you’re not actively trying to compartmentalize parts of your program it can be very easy to simply write spaghetti code."

When code is well-separated, individual sections can be reused, modified, and debugged with ease and independence. 

---

### What is the difference between front end and back end?

Front end refers to the client-side, whereas back end refers to the server-side of the application.

Front end is what you see and interact with and back end is how all of it works. Front end may refer to the graphical user interface whereas back end is that part of the website you cannot see or interact with.

---

### Which tasks are handled by the front end?

Front end is all about the visual aspects of the website that a user can see and experience.

The front end is composed of HTML, CSS and Javascript.

Examples of tasks handled by the front end include:
- design and visuals
- UI/UX
- accessibility

---

### Which tasks are handled by the back end?

The back end is everything behind the scenes. It is the "brain" of the website.

It generally includes a web server that communicates with a database to serve requests that the front end presents.

Back end development includes languages such as Ruby, Python and Java.

Examples of tasks handled by the back end include:
- integration of user-facing elements
- logic
- data storage
- security
- analytics and statistics

---

## 2. Client side vs server side

Website scripts run in one of two places: 
- the **client side**, also called the front-end
- or the **server side**, also called the back-end.

![image of architecture](https://i.imgur.com/14SMlsc.png)


---


## Client side scripting 
- runs scripts on your computer (in the user’s browser) after you’ve loaded a web page 
- runs its scripts before the HTML is loaded, not after
- Typically reacts to user input & often performs DOM manipulation
- (Usually) can be seen and edited by the user in full e.g. viewing linked scripts in the dev tools
- Cannot read files off of a server directly, must communicate via HTTP requests.
- Does not need interaction with the server


Example: examining the user’s form for the errors before submitting it

---



## Server side scripting 
- scripts are run on the server which hosts the website and sends down the HTML code
- Store persistent data (user profiles, instatweets, mybook pages, etc.).
- Cannot be seen by the user (unless something is terribly wrong).
- Can only respond to HTTP requests for a particular URL, not any kind of user input.
- Responds to GET, POST, PUT, and DELETE requests.

Examples: dynamic change in the website content in response to the user’s queries

---


## Client vs server side
- **Front-end scripting** is good for anything that requires **user interaction**, **back-end scripting** is good for anything that requires **dynamic data** to be loaded. 

- The general rule is to use server-side processing when the client needs to interact with server-side objects like databases, files, etc. 

- Server-side scripting is more secure than client-side scripting as the server side scripts are usually hidden from the client end, while a client-side script is visible to the users.


---



### Example validation
Does the user request require server resources (such as databases) to validate the user input? 
- YES: use Server Side Validation (example: email validation)
- NO: use Client Side Validation (example: password validation)



---


## Pros and Cons

| | Server Side | Client Side |
| -------- | -------- | -------- |
| SEO   | high     | low     |
| Initial Page Load   | Faster     | Slower     |
| Dynamic Page Render   | Slower     | Faster     |
| Security  | Higher    | Lower     |
| Interactivity  | Non-rich     | Rich     |
| Server overhead  | More     | Less     |
| Third Party Libraries | None     | Sometimes required     |


---


## 3. Alternative back-end technologies: Which other technologies (programming languages and servers) might be used instead of Node on the back end? What are some of the pros and cons of using Node in your stack, rather than one of those alternatives?

* PHP 
  * Server side scripting language 
  * Very popular before Node JS 

* Ruby 
  * An object-oriented programming language
  * Ruby on Rails is a server-side web app framework

---

* Python
  * Python is a popular programming langue for the backend
  * Django is a popular server-side web framework, written in Python.

* Java 
  * Has some benefits for large-scale projects
    
---

* Other programming languages that can be used on the server side: 
  * C# 
  * Go
  * Elixir
  * Haskell 
  * Kotlin 
  * Scala 
  * Perl


## What are some of the pros and cons of using Node in your stack, rather than one of those alternatives?

#### Pros

Some benefits of full-stack JS develeopmenrt can be 

* better efficiency and overall developer productivity
* code sharing and reuse
* speed and performance: 

---

  * Node.js is a single threaded language which in background uses multiple threads to execute asynchronous code.
  * This means Node.js is fast and is capable of processing requests without any delays


#### Cons

* Because it is single-threaded, Node JS is not good for processing high-CPU tasks 

* Java, for example, uses multi-threading so is good for large scale projects that involved concurrency

---

## 4. Writing for different environments: Why might you have to write JavaScript differently if it's going to run in the browser, rather than in Node? What tools can help bridge the gap?

---

Both the browser and Node use JavaScript as their programming language.

Building apps that run in the browser is a completely different thing than building a Node.js application.

What changes is the ecosystem.

---

In the browser, most of the time what you are doing is interacting with the DOM, or other Web Platform APIs like Cookies. Those do not exist in Node, of course.

And in the browser, we don’t have all the nice APIs that Node.js provides through its modules, like the filesystem access functionality.

---
Browser compatibility?
Another big difference is that in Node.js you control the environment. Unless you are building an open source application that anyone can deploy anywhere, you know which version of Node you will run the application on.

On Client side the tool bable will help you convert es6 code into es5 https://babeljs.io/ to ensure browser support.

---

Node uses the CommonJS module system, while in the browser we are starting to see the ES Modules standard being implemented.

In practice, this means that for the time being you use require() in Node and import in the browser.

---

Modules:

- encapsulate all sorts of functionality, and expose this functionality to other JavaScript files, as libraries. They let you create clearly separate and reusable snippets of functionality, each testable on its own.


---

Common JS - Server side

-  loaded synchronously, and processed in the order the JavaScript runtime finds them.

---

![](https://i.imgur.com/HyzA5H3.png)

a JavaScript file is a module when it exports one or more of the symbols it defines, being them variables, functions, objects:

![](https://i.imgur.com/twejIVL.png)

---

![](https://i.imgur.com/YeFffqF.png)

---

ES5 Modules - Client side

- the ECMAScript standard for working with modules and are one of the biggest features introduced in modern browsers. They are part of ES6 but the road to implement them has been long.

- remember that having more than a few modules is going to have a performance hit on our pages, as it’s one more step that the browser must perform at runtime.

---

![](https://i.imgur.com/tYJpJWn.png)

![](https://i.imgur.com/bDFT2Qc.png)

---

![](https://i.imgur.com/P2WNfDl.png)


