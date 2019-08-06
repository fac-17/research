# Script injections / safety issues


## What is a script injection and how do these happen?


### What is a script injection
SQL injection is a code injection technique, used to attack data-driven applications, in which malicious SQL statements are inserted into an entry field for execution. 
SQL injection must exploit 
* a security vulnerability in an application's software => eg: when user input is either incorrectly filtered for string literal escape characters embedded in SQL statements or user input is not strongly typed and unexpectedly executed
* SQL injection is mostly known as an attack vector for websites but can be used to attack any type of SQL database.


### What is a SQL injection attack?
Broadly speaking, it is a malicious user entering data to subvert the nature of your original query. This is almost always through a web interface, and involves an “unescaped” parameter that can be used to change the data returned or perform other database actions. The user “injects” their own SQL into your original SQL statement, changing the query from its original intent.

## Reaction

So you’ve just detected a SQL injection attack. Don’t panic! 

---

![](https://media.giphy.com/media/1FMaabePDEfgk/giphy.gif)

*Okay, perhaps panic a little bit. *


---
The first order of business is to, as quickly as possible:
<!-- ![](https://media.giphy.com/media/xGamRzpBQYlG0/giphy.gif) -->

* disable access => prevent the attacker from doing anything else
* don’t worry about fixing the hole yet!
*  Stop Apache
*  disable all CGI
*  shut down your database
*  => whatever it takes

![](https://media.giphy.com/media/5xaOcLwEvFOizxHVyVy/giphy.gif)

Yes, this will cause a loss of business maybe, but you have to do what it takes! Once things are disabled, start patching up the holes. If it is a well isolated, obvious fix, bring things back up. If not, look for similar code with the same problem, then bring things back up. There are now some important steps to take:

* Double check all similar code for any other problems.
* Check your logs carefully to see if this was an isolated event, or if the hole had been used before. If you are relying on SQL errors for detection, a careful attacker may have already successfully injected some SQL.
* Why this happened in the first place:
    * Didn’t update a driver? 
    * Someone just wrote some bad code? 
    * Something else? 
    * Fix it at both the immediate technical and long-term procedural level


---


## How would you prevent script injections?

Few possibilities! But First, the easy one could be to download TAIL_N_MAIL

The tail_n_mail program at its simplest is a Perl script that greps through :
* log files
* finds items of interest
* mails them out. 
* a little bit more but most important is here 😉 like figuring out which log files to scan, and analyzing the data on the fly.


---



- In a general sense you can prevent JavaScript injection attacks by HTML encoding any data entered by site users.

- When you HTML encode a string, dangerous characters such as `<` and `>` are replaced by HTML entity references such as `&lt`; and `&gt;`. 
 
- So when the string `<script>alert("Boo!")</script>` is HTML encoded, it gets converted to: 
```
&lt;script&gt;alert(&quot;Boo!&quot;)&lt;/script&gt; 
```



---



- The encoded string no longer executes as a JavaScript script when interpreted by a browser.

![converted script](https://docs.microsoft.com/en-us/aspnet/mvc/overview/older-versions-1/security/preventing-javascript-injection-attacks-cs/_static/image8.png)




---



Preventing SQL injection is mostly a matter of following some standard software development practices. 

You want your code to be:
- up to date
- well vetted
- easy to read and revert



---


#### Use version control 
Use git for everything so you can figure out how some bad code (e.g. SQL injections) got into your app, and what safe version you can replace it with. 

#### Code review
Never commit code that hasn’t been looked at by at least one other person not involved in its writing. 



---



#### Limit privileges

- An application should have the minimum rights it needs to do its job. Limit what runs as a superuser. 
- If something really needs to run as a superuser, consider wrapping the data/logic in a SECURITY DEFINER function. 



---


#### Forensics

If you’ve closed an SQL injection hole and audited your code to ensure no other holes exist, you next need to do a forensic examination of what went wrong and what damage was caused.




---


## Good and bad pratices


How not to do it
```javascript=
const sql = `SELECT * FROM table WHERE name = "${userString}"`
```

---

User input - 
> Bobby T"; DROP TABLE table; --

---

- All our tables will get dropped as we are sending 2 queries seperated by ';'

```javascript=
SELECT * FROM table WHERE name = "Bobby T"; DROP TABLE table; --"
```
---

Other examples

### 1 always equals 1 
```javascript=
txtUserId = getRequestString("UserId");
txtSQL = "SELECT * FROM Users WHERE UserId = " + txtUserId;
```
![](https://i.imgur.com/6ArNTXL.png)


---

Our query on the back end now looks like this:
```javascript=
SELECT * FROM Users WHERE UserId = 105 OR 1=1;
```
- 1 is always 1 so the the entire contents of the database will get returned to the user,

---

### '=' is always true
![](https://i.imgur.com/B4N3wtQ.png)

Query result 
```javascript=
SELECT * FROM Users WHERE Name ="" or ""="" AND Pass ="" or ""=""
```
- = is =, it evaluates to true so again this code will run.

---

### Batched statements

![](https://i.imgur.com/hlUkHqQ.png)

---


## Keep your database safe from the SQL Injection Attacks

### 1. Using Prepared Statements

Using Prepared Statements is one of the best ways to prevent SQL injection.

`PREPARE name [ ( data_type [, ...] ) ] AS statement`

It is a feature used to execute the same or similar database statements repeatedly with high efficiency. Used with SQL statements such as queries or updates, it takes the form of a template into which certain constant values are substituted during each execution.

Prepared statements are resilient against SQL injection because values which are transmitted later using a different protocol are not compiled like the statement template. If the statement template is not derived from external input, SQL injection cannot occur.



https://www.postgresql.org/docs/current/sql-prepare.html


### 2. Using Stored Procedures

Stored Procedures adds an extra security layer to our database. When used the app treats input as data to be operated on rather than SQL code to be executed.

A stored procedure is a prepared SQL code that you can save, so the code can be reused over and over again.

So if you have an SQL query that you write over and over again, save it as a stored procedure, and then just call it to execute it.


### 3. Validating user input

Do an input validation first to make sure the value is of the accepted(type, length, format, etc). Only the input which passed the validation can be processed to the database. 

### It’s like checking who is at the door of your house before you open it and let them in.

But remember, this method can only stop the most trivial attacks, it does not fix the underlying vulnerability.

### 4. Limiting privileges

Use an account with **limited privileges** instead using an account with **root access** to limit the scope of damages in case of SQL Injection.


### 5. Hidding info from the error message

Error messages are useful for attackers to learn more about your database architecture, so be sure that you show only the necessary information. 

#### Show a **generic error message** telling something goes wrong and encourage users to contact the technical support team in case the problem persists.

### 6. Updating your system

#### It’s vital to update your system to the most up-to-date version as you can, especially for your SQL Server.

SQL injection vulnerability is a frequent programming error and it’s discovered regularly.

### 7. Keeping database credentials separate and encrypted

If you are considering where to store your database credentials, also consider how much damaging it can be if it falls into the wrong hands. Always 
1. **store** your database credentials in a separate file 
2. **encrypt** it securely to make sure that the attackers can’t benefit much.

Also!!!!
**DO NOT** store sensitive data if you don’t need it and delete information when it’s no longer in use.


### 8. Disabling shell and any other functionalities you don’t need

Turn it off your shell if possible and  remove or disable all functionalities that you don’t need too.

Shell access could be very useful indeed for a hacker. 



### The key to avoiding being the victim of the next SQL Injection Attack is always be cautious and trust nobody. You don’t know when the bad guy is coming so hope for the best and prepare for the worst, validate and sanitize all user interactions... 
from https://tableplus.io/blog/2018/08/sql-injection-attack-explained-with-example.html



## RESOURCES
[script injection attack](https://www.endpoint.com/blog/2012/06/10/detecting-postgres-sql-injection)
[tail_n_mail](https://bucardo.org/tail_n_mail/)
