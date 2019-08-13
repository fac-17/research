# HTTP vs HTTPS

---

![](https://media.giphy.com/media/11fot0YzpQMA0g/giphy.gif)

---

## How does HTTPS work? 

---

HTTP is 'plain text', or a binary file (like an image) anyone can read or see.

---

HTTPS is a standard HTTP protocol with a layer of SSL/TLS encryption added on top.

---

Acronyms:

- HTTP = Hypertext Transfer Protocol 
- HTTPS = Hypertext Transfer Protocol Secure 
- TLS = Transport Layer Security
- SSL = Secure Sockets Layer

---

HTTPS encrypts and decrypts user page requests as well as the pages that are returned by the Web server and protects against eavesdropping and man-in-the-middle attacks. 

---

HTTPS is based on public/private-key cryptography. 

* The public key is used for encryption
* The secret private key is required for decryption.

---

The SSL layer has 2 main purposes:

* Verifying that you are talking directly to the server that you think you are talking to

* Ensuring that only the server can read what you send it and only you can read what it sends back

---

With the SSL layer, someone can intercept the messages you exchange with a server and **still** not be able to read any of the actual data you send.

---

An SSL connection between a client and server is set up by a handshake that establishes: 

* the client is talking to the right server (and visa versa)
* the parties to have agreed on a [“cipher suite”](https://en.wikipedia.org/wiki/Cipher_suite), which includes which encryption algorithm they will use to exchange data
* the parties have agreed on the keys for this algorithm

---

## What are TLS/SSL certificates?

---

SSL means secure socket layer. But that protocol has been deprecated and replaced by Transport Layer Security (TLS). 

Because so many got used to using the SSL acronym we still use it, the two are interchangeable today, but the actual encryption is TLS, not SSL today. 

TLS was introduced in 1999 as a new version of SSL and was based on SSL 3.0.

---

A digital certificate certifies the ownership of a public key by the named subject of the certificate, and indicates certain expected usages of that key. Assertions made by the private key correspond to the certified public key.

---

Here's a legit certificate
![](https://i.imgur.com/KtQF1Ks.png)

---

TLS typically relies on a set of trusted third-party certificate authorities to establish the authenticity of certificates. Trust is usually anchored in a list of certificates distributed with user agent software, and can be modified by the relying party.


 Websites can use TLS to secure all communications between their servers and web browsers. 

---

## Why is this important to implement in your projects?

---

HTTPS provides **critical security** and data integrity for both your websites and your users' personal information. HTTPS is a requirement for many new browser features, particularly those required for progressive web apps.

---

One common misconception about HTTPS is that the only websites that need HTTPS are those that handle sensitive communications. Every unprotected HTTP request can potentially reveal information about the behaviors and identities of your users. 

---

Although a single visit to an unprotected websites may seem benign, some intruders look at the aggregate browsing activities of users to make inferences about their behaviors and intentions, and to de-anonymize their identities. For example, employees might inadvertently disclose sensitive health conditions to their employers just by reading unprotected medical articles.



---

## Demo how to generate certificates and use them in a node project

---

Check this :smile: [TUTORIAL](https://flaviocopes.com/express-https-self-signed-certificate/)

---

Run this command in your project directory to generate certificate and key. If using Ubuntu you will have openssl installed by default. If on MacOS you can install it with: **_brew install openssl_**

---

```
openssl req -nodes -new -x509 -keyout server.key -out server.cert
```

---

The utilitiy will walk you through the process. Just remember to put *localhost* on the common name section.

![](https://i.imgur.com/6t1S9m5.png)

---

Then we can create a simple node server with express.

---

```javascript
const https = require("https");
const express = require("express");
const app = express();
const fs = require("fs");
const port = 3000;

app.get("/", (req, res) => {
  res.send("Hello HTTPS!");
});

https.createServer(
    {
      key: fs.readFileSync("server.key"),
      cert: fs.readFileSync("server.cert")
    },
    app).listen(port, () => {
    console.log(`Example app listening on port ${port}!`);
  });

```

---

![](https://i.imgur.com/XqVa5dh.png)

---

![](https://i.imgur.com/9HcpFId.png)

---

Click on Advanced and proceed to page. You can see that localhost is using the https protocol, although it's a self-signed certificate hence it's not legit but you get the gist.

---

![](https://i.imgur.com/5K18CxZ.png)

---

![](https://i.imgur.com/GVS52aW.png)

---

![](https://i.imgur.com/Lqow97q.png)


---

### Testing your server:

https://www.ssllabs.com/ssltest/

![](https://i.imgur.com/ksWSKFq.png)



---

![](https://media.giphy.com/media/YQitE4YNQNahy/giphy.gif)


---


### Further reading
1. https://www.digicert.com/ssl/
2. https://robertheaton.com/2014/03/27/how-does-https-actually-work/
3. https://love2dev.com/blog/how-https-works/
4. https://developers.google.com/web/fundamentals/security/encrypt-in-transit/why-https
5. https://developers.google.com/web/fundamentals/security/encrypt-in-transit/why-https
6. https://www.smashingmagazine.com/2017/06/guide-switching-http-https/
7. https://en.wikipedia.org/wiki/Transport_Layer_Security#Certificate_authorities
