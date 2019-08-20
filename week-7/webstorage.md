# Web Storage 


Emmanuel, Georgia, Jan, Reuben

---

#### What is local storage?


---

* The Local Storage object stores data with no **expiration data**. 
* The data will not be deleted when the browser is closed
* The data is available until the user manually clears the browser cache or until your web app clears the data

* Example - Logged into Googlemail on Chrome

---

#### What is Session storage?

* The sessionStorage object stores data temporarily for only one session (data  deleted when the browser tab is closed)
* The data is present only until the window or tab is closed
* Example - Google Chrome incognito mode

---

<iframe src="https://giphy.com/embed/BCdhiObre968ElgG0j" width="480" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

---

#### What is the difference?


|Local Storage | Session Storage |
| -------- | -------- |
| Stores data with no expiry date     | Stores data only for the session - stored only until the browser (or tab) is closed    |
| Data is not sent back to the server for every HTTP request - reduces the amount of traffic | Data is never transferred to the server    |

---

|Local Storage | Session Storage |
| -------- | -------- |
| The data persists even when the browser is closed and reopened.    | Changes only available per window   
| Storage limit is 10MB (maximum)    |  Storage limit is larger than a cookie (at least 5MB)    |
| Needs to be manually deleted    | Deleted once you close tab/window    |






---

### Cookies vs local/session storage

---

"Web storage can be viewed simplistically as an improvement on cookies."

---

![](https://media.giphy.com/media/1ngQorBCDcUFy/giphy.gif)

---

Cookies are mainly for reading server-side, whereas local/session storage can only be read by the client-side.

---

Cookies are smaller and send server information back with every HTTP request, while local/session storage is larger and can hold information on the client side.

---

Web storage (session and local) provides much greater storage capacity.

The available size is 5MB, which is more space to work with than a typical 4KB cookie. 

---

![](https://i.imgur.com/HMMgFXa.png)

---


# `Storage` object
 
- Both `window.localStorage` and `window.sessionStorage` return `Storage` object.
 
- It allows reading, adding, modifying, or deleting of stored data items.
 
- Both keys and values are strings so if you need to store more complex data stringify it!

---


- `Storage.length` returns a number of data items in the storage

- `Storage.key(n)` returns the name of `n`th key


- `Storage.getItem(keyName)` returns the value (string) stored at the `keyName` key

---

- `Storage.setItem(keyName,value)` stores value (string) at the key `keyName` (string), creating it if it doesn't exists or updating if it does. 

- `Storage.removeItem(keyName)` removes the keyName key from the Storage

- `Storage.clear()` empties all the keys from the Storage
 

---

# Example of localStorage and sessionStorage

---


![](https://media.giphy.com/media/N35rW3vRNeaDC/giphy.gif)
 

---
 
 
 ![](https://media.giphy.com/media/2sYaePC3iVWYBNxaVj/giphy.gif)
 
Resources

- https://medium.com/datadriveninvestor/cookies-vs-local-storage-2f3732c7d977

- https://developer.mozilla.org/en-US/docs/Web/API/Storage

- https://www.youtube.com/watch?v=AwicscsvGLg
