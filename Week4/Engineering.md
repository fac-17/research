# Engineering

## Modules
Modular code is code which is separated into independent modules. The idea is that internal details of individual modules should be hidden behind a public interface, making each module easier to understand, test and refactor independently of others.

---

### Core Modules
Node.js has several modules compiled into the binary.
1. http
2. url
3. querystring
4. path 
5. fs (file system)
6. util

---

The core modules are defined within Node.js's source and are located in the lib/ folder. Core modules are always preferentially loaded if their identifier is passed to require(). For instance, require('http') will always return the built in HTTP module, even if there is a file by that name. 
```javascript=
const module = require('module_name');
```

---

In the Node.js module system, each file is treated as a separate module. For example, consider a file named foo.js:
```javascript=
const circle = require('./circle.js');
console.log(`The area of a circle of radius 4 is ${circle.area(4)}`);
```
On the first line, foo.js loads the module circle.js that is in the same directory as foo.js.

---

Here are the contents of circle.js:
```javascript=
const { PI } = Math;

exports.area = (r) => PI * r ** 2;

exports.circumference = (r) => 2 * PI * r;
```
The module circle.js has exported the functions area() and circumference(). Functions and objects are added to the root of a module by specifying additional properties on the special exports object.

Variables local to the module will be private, because the module is wrapped in a function by Node.js. In this example, the variable PI is private to circle.js.

The module.exports property can be assigned a new value (such as a function or object).

---

### The module.exports or exports
is a special object which is included in every JS file in the Node.js application by default. module is a variable that represents current module and exports is an object that will be exposed as a module. So, whatever you assign to module.exports or exports, will be exposed as a module.

---


## Asynchronous

### Why should you use asynchronous forms of functions wherever possible in Node? 
It's our natural desire to be able to think of computer instructions as a step-by-step series of operations. But, on-CPU operations are much cheaper than Input/Output (I/O) operations.

https://nodesource.com/blog/why-asynchronous/
![(https://i.imgur.com/weYyHkG.png)

In Node.js, I/O is treated differently under the hood and is exposed to the programmer. When working with Node.js, the programmer is rightly forced to see I/O as a separate class of operation. This is what makes Node.js fast - because programmers are forced to write fast programs by not introducing blocking I/O to the program flow

In summary, you should use asynchronous forms of functions because they result in much faster programs. 

*Note: JavaScript is single-threaded, but Node.js is not. By default, a Node.js process will spin up four "worker threads" for performing filesystem I/O. *


### What are error-first callbacks, and why is it important to follow that pattern in your own code?

Node.js is asynchronous so having a dependable callback pattern is crucial.  Without one, developers would be stuck maintaining different styles between different modules. 

The error-first pattern is today’s standard pattern for asynchonous callbacks. 

While every use-case has different requirements and responses, the error-first pattern can accommodate them all.

http://fredkschott.com/post/2014/03/understanding-error-first-callbacks-in-node-js/

#### Two rules for defining an error-first callback:
1. The first argument of the callback is reserved for an error object. If an error occurred, it will be returned by the first err argument.
2. The second argument of the callback is reserved for any successful response data. If no error occurred, err will be set to null and any successful data will be returned in the second argument.

#### Example of error-first callback
```javascript
fs.readFile('/foo.txt', function(err, data) {
  // If an error occurred, handle it (throw, propagate, etc)
  if(err) {
    console.log('Unknown Error');
    return;
  }
  // Otherwise, log the file contents
  console.log(data);
});
```

### Why should you avoid using throw in callbacks?

Asynchronous exception is uncatchable because the intended catch block is not present when the asynchronous code is executed. Instead, the exception will propagate all the way and terminate the program.


https://bytearcher.com/articles/why-asynchronous-exceptions-are-uncatchable/

### When might you use the syncronous form of a function instead?

You use them for writing command-line tools

```javascript
var fs = require('fs');

var handle = fs.openSync('info.txt', 'r');
var buf = new Buffer(100000);
var read = fs.readSync(handle, buf, 0, 10000, null);
console.log(buf.toString('utf8', 0, read));
fs.closeSync(handle);
```

http://www.informit.com/articles/article.aspx?p=2756470&seqNum=6 

---


## Input/Output

Input/output (the fs and path modules): 
- What kind of tasks does the fs module enable you to perform that you wouldn't be able to in the browser? 
- What are some of the issues of working with paths when accessing a file system? 
- How does the path module help, and why should you use it instead of manually writing file paths as strings?

Defn:

The Node.js file system module allows you to work with the file system on your computer.

It provides an API for interacting with the file system in a manner closely modeled around standard POSIX functions.

The Portable Operating System Interface is a family of standards specified by the IEEE Computer Society for maintaining compatibility between operating systems.

To use this module use: 

`const fs = require("fs")`



Common use for the File System module:

- Read files
- Create files
- Update files
- Delete files
- Rename files

### Read Files

Read files such as HTML and host them online

The fs.readFile() method is used to read files on your computer.



### Creating Files 

The File System module has methods for creating new files:

fs.appendFile()
fs.open()
fs.writeFile()

### Update Files

The File System module has methods for updating files:

fs.appendFile()
fs.writeFile()

### Delete Files

To delete a file with the File System module,  use the fs.unlink() method.



### Rename Files

To rename a file with the File System module,  use the fs.rename() method.

---


The Path module provides a way of working with directories and file paths.


--- 

## What are some of the issues of working with paths when accessing a file system? 

---

- names, naming files
- structuring files, keep things out the root, modularise
- not good for modularising, if you change the folder names... uh, oh!

- There are functions available which you'd be hardcoding, i.e. time-wasting!
- The path module provides a lot of very useful functionality to access and interact with the file system.
- No need to install paths, it is part of core modules

---

Most fs operations accept filepaths that may be specified in the form of a string, a Buffer, or a URL object using the file: protocol.

String form paths are interpreted as UTF-8 character sequences identifying the absolute or relative filename. Relative paths will be resolved relative to the current working directory as specified by process.cwd().


---


`var path = require('path');`

![](https://i.imgur.com/sM94eoW.png)

### Some cool ones: 

![ ](https://media.giphy.com/media/3o7abHGYSCrtVws2Os/giphy.gif)

The path.basename() methods returns the last portion of a path.

`path.basename('/foo/bar/baz/asdf/quux.html');`
`// Returns: 'quux.html'`

`path.basename('/foo/bar/baz/asdf/quux.html', '.html');`
`// Returns: 'quux'`


The path.dirname() method returns the directory name of a path.


```javascript=
path.dirname('/foo/bar/baz/asdf/quux');

// Returns: '/foo/bar/baz/asdf'
```


The path.extname() method returns the extension of the path, from the last occurrence of the . (period) character to end of string in the last portion of the path.

```javascript=
path.extname('index.html')

//Returns: .html
```


 ---


## Working with URLS

### What is a urlObject and how is it structured?
    
- A URL like `
```
http://www.example.com/foo?bar=1#main
``` 
consists of several different parts - e.g., the host part 
```
(www.example.com)
``` 
or the search 
```
(?bar=1, often called query string)
```

- When writing Node.js web server software, you regularly need to access or even manipulate those different parts.         splitting this string into its different logical parts manually with substring operations or regular expressions is very cumbersome. A dedicated library makes this very easy.

 --- 
 
#### urlObject: 
- the url module provides a parse() method which converts a url string into a urlObject
- The parsed urlObject has various properties denoting different parts of the url
  ```var url=require('url');
   var address = "http://gremlin:sparks@host.domain.com:4444/somewhere?q=one";
   var my_url=url.parse(address);
  ```
 
  ---
  
   
 my_url will be the following object
```{protocol: "http:"
   host: "gremlin:sparks@host.domain.com:4444"
   hostname:"host.domain.com"
   port: "4444"
   auth: "gremlin:sparks"
   pathname: "/somewhere"
   search:"?q=one"
   query:"q=one"
   }
```
 ---
The urlObject is useful to build functionality that depends on different parts of a url... for example to separate an endpoint from the url, or to separate the query string from the url. basically we have convenient access to the different parts of a url as object properties and values.

Note the query property: anything that comes after the first ? in the url is the 'query string'
http://example.com/path/to/page?name=ferret&color=purple
this can have any number of different properties and values depending on the webpage
node provides another module called querystring to separate these properties into a similar object to urlObject

### Why is it important to be able to turn JavaScript objects into querystrings and back again? 

one of the original use cases for query strings was web forms.
when we submit a form, the text entered in different fields is encoded into the url as 
```
field1=value1&field2=value2&field3=value3
```
the querystring module allows us to convert this to a JSON object using querystring.parse() and back into a string, using querystring.stringify()

querystring.parse() would turn the above string into an object like this:
```{field1: value1,
    field2: value2,
    field3: value3}
```
having these properties as object values makes it much easier to use them in logical expressions like if statements, or to pass these into parts of your program that require these values (taking the CMS example from the nodegirls workshop, to take the form info and populate a blogpost on the page with these values) 
### Why is it a bad idea to build a query string manually from other strings (think about URL encoding and escape characters)?

Take a look at this hypothetical input into a textbox
```chocolate is cool 8628^#^#^#*9@(*& ```
the query string version of that string would look like this
```chocolate+is+cool+8628%5E%23%5E%23%5E%23%2A9%40%28%2A%26+```

this is a process known as url encoding. special characters are 'escaped' so the browser can read them properly.

basically A URL is composed from a limited set of characters belonging to the US-ASCII character set. These characters include digits (0-9), letters(A-Z, a-z), and a few special characters ("-", ".", "_", "~").

there are also some 'reserved' characters that have special meaning within URLs. 
examples include ```?, /, #, : ```
any parts of the url containing data(pathname, querystring etc)must not contain these characters.

So keeping these limitations in mind, other special characters are 'escaped'(converted) to their hex counterparts(these start with a %), and spaces are converted to a '+' in query strings.

if we were to convert something(say form data) manually to a query string, we'd have to painstakingly create functionality to replace all these special characters with their hex keys, and spaces with '+'
using the built in stringify() method is much easier in this case.



## Resources

[W3 Schools File System](https://www.w3schools.com/nodejs/nodejs_filesystem.asp)

[Node JS Documentation](https://nodejs.org/api/fs.html)

[About Path Module](https://nodejs.org/api/path.html)

[URL Encoding](https://www.urlencoder.io/learn/)
