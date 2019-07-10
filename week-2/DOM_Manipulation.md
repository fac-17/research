## DOM Manipulation

---

### How can you use JavaScript to create an HTML element and then add it to your webpage? How would you replace an existing element with it?

---

In an HTML document, the document.createElement() method creates the HTML element specified by tagName 


tagName =
A string that specifies the type of element to be created. 

---

![](https://i.imgur.com/5e5z5kG.png)

---

![](https://i.imgur.com/61cgnvV.png)

---

However this element will not exist within the DOM (on the actual page) until you put it there.

We can then use the Node.appendChild() method, which adds a node to the end of the list of children of a specified parent node.

---

![](https://i.imgur.com/9kvwRQT.png)

---

The Node.replaceChild() method replaces a child node within the given (parent) node.

Syntax
replacedNode = parentNode.replaceChild(newChild, oldChild);

---

### How would you add a li element to the start of a ul?

---

The insertBefore() method inserts a node as a child, right before an existing child, which you specify.

Syntax: node.insertBefore(newnode, existingnode)

---

![](https://i.imgur.com/CEKDJnQ.png)

---

## JavaScript Event

JavaScript Event is an object passed from the browser 
to our handler function when the event is triggered.


---

```
clickableElement.addEventListener("click",handler);

function handler(event){
    event.target // an element an event was fired on
    event.currentTarget // and element that registered the handler
    event.preventDefault();
    // MouseEvent events
    event.clientX  // The X coordinate of the mouse pointer in local (DOM content) coordinates.
    // Keyboard Event
    event.key
}
```

---


#### What does `event.preventDefault()` do? 


You can attach an event handler to an element that has some default action.
This call prevents the default action from being taken.


---

```
submitButton.addEventListener("click",submitHandler);

function submitHandler(event){
    if (!imaginaryValidateFunction()){
        event.preventDefault();
        alert("Bad Input")
    }
}
```

---

Sometimes you might want add some extra functionality
but still trigger the default actions.

Other cancelable actions:
checking a box on a clicked checkbox,
navigating away on clicked links `<a>`


---

### What is a NodeList? 

* In the DOM a NodeList is an object that consists of a list of all the nodes in a document. 

* A node is a single point in the node tree -- for example the document itself, elements, or text.

* NodeLists can usually be returned by properties such as `Node.childNodes` and methods such as `document.querySelectorAll()`

---


### How is a NodeList different from an Array?

* Although NodeList is not an Array, it is possible to iterate over it with: 
`Nodelist.forEach()` 

* A NodeList can also be converted to an Array using: 
`Array.from()`

* However,you cannot use Array Methods on a NodeList like valueOf(), push(), pop(), or join().

---

* NodeLists also differ from Arrays in that they are often live lists (although not always). This means that if elements are removed or added to the DOM, the list updates automatically.

* `querySelector()` and `querySelectorAll()` return a static list that doesn’t update, but properties like `.childNodes` are live lists that will change as you manipulate the DOM.


---

## What are the security concerns around Element.innerHTML and what could you use instead? ##


The innerHTML property provides a really simple and convenient way to create HTML templates and inject them into the DOM.


---


However, DOM manipulations using innerHTML are:

   More prone to attacks (XSS)
    
<iframe src="https://giphy.com/embed/lp3GUtG2waC88" width="480" height="272" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/hack-lp3GUtG2waC88"></a></p>
    

---


### Cross site scripting ###

The idea behind an XSS attack with innerHTML is that malicious code would get injected into your site and then execute. This is possible because innerHTML renders complete markup and not just text.

---

### When is it an Issue? ###

* If you’re inject your own markup into a page, there’s little cause for concern. The danger comes from injecting user and third-party markup into the DOM
 
* If you’re adding content to a page that you didn’t write, you should **sanitize** it to protect yourself from XSS attacks. (remove disallowed markup)

---

<iframe src="https://giphy.com/embed/vuZeED6SoCN8MbLZq8" width="480" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/latenightseth-seth-meyers-lnsm-vuZeED6SoCN8MbLZq8"></a></p>

---

### Safe alternative to innerHTML ###

**Text Content**
The textContent property is great if you’re only adding text.

textContent gets and injects only text content, not markup, from and into a DOM node

```
    EXAMPLE
    Renders a string with escaped characters
    This would show up in the DOM as <img src=x onerror="alert('XSS Attack')"> instead of as an               image element
    div.textContent = '<img src=x onerror="alert(\'XSS Attack\')">';
```


---

**sanitizeHTML.js**
Sanitize and encode all HTML in a user-submitted string to prevent XSS attacks- cleans up HTML fragments.

Works by creating a temporary div and adding the content with textContent. It then returns them using innerHTML to prevent those escaped characters from transforming back into unescaped markup.

![](https://i.imgur.com/IKvGakH.png)


---

**Libaries**
Helper library like DOMPurify - Remove any markup that’s not part of a secure whitelist

https://github.com/cure53/DOMPurify

 ---

