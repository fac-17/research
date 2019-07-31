# Streams & Buffers

![](https://media.giphy.com/media/smzfl3E7a4iHK/giphy.gif)

---


## What is a stream?

![](https://media.giphy.com/media/BEk5G9RlOcqA0/giphy.gif)

---

🔍
#### Definition

> A sequence of **data being moved** from one point to the other over time.
> 
> The whole concept is, you have a huge amount of data to process, but you don’t need to wait for all the data to be available before you start processing it.


---


Streams are **collections of data**, just like arrays or strings. Unlike these, however, streams might **not be available all at once**.

📖

**Usual approach:** You tell the program to read a file, then the file is read into memory, from start to finish, and then processed.

**Stream approach:** The file is red it piece by piece, processing its content without keeping it all in memory.

---

⏱
### Time efficiency 

This makes streams really powerful when working with **large amounts of data**, or data that’s coming from an **external source** one chunk at a time.

It takes way less time to **start processing data as soon as you have it**, rather than waiting till the whole data payload is available to start

A stream  lets you handle the data **asynchronously**.

---

🚀
### Spatial efficiency 

Similarly, streams mean you don’t need to load large amounts of data in memory before you are able to process it.

---



🚰 💦 🚿
### Types of streams

**Readable Streams:**
Lets you read data from the source.

**Writable Streams:**
Lets you write data to the destination.

**Duplex Streams:**
Hybrid of Readable and Writable streams.

---


#### Events and functions that can be used with readable and writable streams:

![](https://i.imgur.com/D7T7uNT.png)


--- 


---

🚰
### Piping 

The `pipe()` function lets you pipe the output of a readable stream — the source of data — into a destination. The source has to be a readable stream and the destination has to be a writable one.

---


``` js
const http = require('http')
const fs = require('fs')

const server = http.createServer((req, res) => {
  const stream = fs.createReadStream(__dirname + '/data.txt')
  stream.pipe(res)
})
server.listen(3000)
```
This line:
`stream.pipe(res)`
in pseudo-code is:
`readableSrc.pipe(writableDest)`

It’s generally recommended to either use the pipe method or consume streams with events, but avoid mixing these two.

---



## What is a buffer?

![](https://media.giphy.com/media/l4EoQXbKMlVL60GJO/giphy.gif)


---



### Streams make buffers necessary

> Typically, data is moved with the intention to process it, or read it, and make decisions based on it.
> 
> But there is a minimum and a maximum amount of data a process could take over time.

---


🐇
**If the rate the data arrives is faster than the rate the process consumes the data...** the excess data need to wait somewhere for its turn to be processed.
🐢
**If the process is consuming the data faster than it arrives...** the chunks of data that arrive earlier need to wait for a certain amount of data to arrive before being sent out for processing.
🚦
That waiting area is the **buffer**

---



#### From the node documentation:

> The Buffer class was introduced as part of the Node.js API to make it possible to interact with octet streams in the context of things like TCP streams and file system operations.

= make it possible to **manipulate** or **interact** with streams of **binary data**.


---



- It represents a fixed-size chunk of memory (can’t be resized) allocated outside of the V8 JavaScript engine.

- You can think of a buffer like an array of integers, which each represent a byte of data.

- Node.js automatically creates a buffer during a stream, but there are plenty of ways to create your own.

---



## Buffers can be...

### ...created from scratch

#### Buffer.from()

```js
// Creates a Buffer containing [0x1, 0x2, 0x3].
const buf4 = Buffer.from([1, 2, 3]);
```

#### Buffer.alloc(),

```js
// Creates a zero-filled Buffer of length 10.
const buf1 = Buffer.alloc(10);
```

---


### ...accessed like normal arrays:


```js
const buf = Buffer.from('Hey!')
console.log(buf[0]) //72
console.log(buf[1]) //101
console.log(buf[2]) //121
```

---


### ... modified with write()

```js
const buf = Buffer.from('Hey!')
buf[1] = 111 //o
console.log(buf.toString()) //Hoy!
```


---
### Example: Readable Stream
Reading data with a stream, requires two steps: 
1. Open up a readable stream 
2. Read data from a stream 

--- 
### Step 1


**fs.createReadStream(path[, options])** allows you to open up a readable stream. It returns a readable stream object for file at path. You may then perform stream operations on the returned object, such as pipe().

It takes two arguments:
* path: the **path** of the file to start streaming in
* options: an **object** that can include different values definigt the stream, examples: 
        * encoding:  utf8, ascii, or base64.
        * highWaterMark: 64 * 1024 // Defines size of chunks

---
### Step 2

The best way to read data from a stream is to listen to data event and attach a callback. When a chunk of data is available, the readable stream emits a data event and your callback executes. 

```

var fs = require('fs');
var readableStream = fs.createReadStream('file.txt');
var data = '';

readableStream.on('data', function(chunk) {
    data+=chunk;
});

readableStream.on('end', function() {
    console.log(data);
});

```

--- 

And here is what we didn't figure out: 

*(Bonus) Allow an additional argument to be provided in the command to specify a time interval of how often a chunk of text from the file is streamed to the terminal. E.G node streamFile.js bigtextfile.txt 1s
*

![](https://media.giphy.com/media/26ybwvTX4DTkwst6U/giphy.gif)

---

## References

**Streams:**

https://flaviocopes.com/nodejs-streams/#what-are-streams

https://codeburst.io/nodejs-streams-demystified-e0b583f0005

https://www.freecodecamp.org/news/node-js-streams-everything-you-need-to-know-c9141306be93/

**Buffers:**

https://www.freecodecamp.org/news/do-you-want-a-better-understanding-of-buffer-in-node-js-check-this-out-2e29de2968e8/

https://flaviocopes.com/node-buffers/

**Others**

The Net Ninja intro to Streams and Buffers:
https://www.youtube.com/watch?v=GlybFFMXXmQ
