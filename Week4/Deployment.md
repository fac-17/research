# Deployment 🚀 ☁️

![stupid gif](https://media.giphy.com/media/ObxxxxyDNpWnu/giphy.gif)

---




## PaaS: Platform as a Service

Allows you to host wesbites without having to maintain your own servers. 


---


 ## Why use a PaaS? 🤔☝️👀
 
 - So that it's not hosted locally 
 - Servers are maintained
 - Hardware is handled for you
 - Security is managed for you 
 - Easy scaleability (up and down) as demand dictates
 - Cheaper
 

---


## So that's Github right:question:🙋‍♀️

Wrong... Github stores your code and allows you to preview it using Github pages but you can't actually 'run' a web app as there is no back-end that you can access. 



---




### PAAS providers 🕶
- Heroku
- Windows Azure
- Amazon Web Services (AWS Elastic Beanstalk)



---



### So, how the hell do I use it? 

- Code is stored in Github
- Herkoku project links with Github repo 
- Heroku updates/rebuilds automatically when a change is made 



---



## What is an environment variable?



---




Variables and constants take on values that change the results of a file. 

Containing data the program uses in calculations. 

Variables (let in ES6 notation 😜) may change during execution 🔪, while constant values cannot be reassigned.



---



### So... what's an environment variable?

A variable whose value is set outside the file.

Made up of a name/value pair.
> NAME=value

Environment variables typically aren’t globally accessible across the OS, they're usually session-specific.

At runtime, the reference to the environment variable name is replaced with its current value. 



---




## Why would you want to use them?

At runtime, NodeJS automatically loads environment variables into process.env to make them available to the application. 

Separating infrequently changing data from your code.

Secrets... 🤫



---

## Bad example
```javascript=
var request  = require('request-promise');

var main = function() {

  var myAPIKey = 'ndsvn2g8dnsb9hsg';
  
  var url = 'https://externalapi.service.com/v1/query?key=' + myAPIKey;
  
  return request(url);
};
```


---

## Good example
```javascript=
var request  = require('request-promise');

var main = function() {

  var myAPIKey = process.env.MYAPIKEY;
  
  var url = 'https://externalapi.service.com/v1/query?key=' + myAPIKey;
  
  return request(url);
};
```




---


## Why don't you want them stored in public?

Everyone can see them and abuse them, DB passwords, access tokens, API KEYS 

>"My AWS account was hacked and I have a $50,000 bill, how can I reduce the amount I need to pay?"




---

## How can you manage them?


They come from 'environment', but how do they get to that deployment environment?

Problem: how to populate these environment variables in deployment 
while keeping the code publicly available

---

### By prepending the command

```shell=
PORT=4000 API_KEY=666 npm start
```
```javascript=
server.listen(process.env.PORT||3000);
```

---

### Heroku Config Vars
![Imgur](https://i.imgur.com/Dl6Vuz5.png)

---

### env2
.env file:
```shell=
export DB_PASS=123456
export DB_USER=anon
export API_KEY=666
```
server.js
```javascript=
const env = require('env2')('./secrets/.env');
...
api.makeRequest(`http://legit.com/api/
deleteTheWold&API=${process.env.API_KEY`);
```

---



# Thank You
## Any questions?
