# Packaging

---

## Dependencies



---

#### What is a dependency?

**Modules** are a piece of program that specifies which other pieces it relies on and which functionality it provides for other modules to use.

---

🕸

The relations between modules are called **dependencies**. When a module needs a piece from another module, it is said to depend on that module. 

---

**In short**

📦

Dependencies = Packages required by your program for it to run properly.

---

#### Using a dependency vs. Coding from scratch

Code often deals with common problems.

---

🤯

Authentication. Authorization. Data access. Error handling. Navigation. Logging. Encryption. Validating form inputs. Etc. Etc. Etc.

---

👀

There is very likely an existing solution to the problems you are facing. Dependencies are a way to tap into this existing common knowledge and save time for everyone.

---

🚲

> We can often avoid reinventing a program that 100 people have written before and get a solid, well-tested implementation at the press of a few keys.

---

⏳

> Writing any of this stuff completely from scratch is generally a waste of time. 

---

![](https://i.imgur.com/97I6WHB.jpg)

---

#### What's the problem then? 🚨


What happens if these dependencies (relying on third party code) get removed, break down or are modified.

---

![](https://i.imgur.com/BD7BOA6.jpg)


---

#### What to do, what to do ❓

It is generally recommended to avoid relying too much on dependencies.

Ensure any third party code comes from reliable sources.

---

* have a significant user base
* supported by major companies
* get major new releases regularly
* ...


---

## NPM

#### What is a package manager?

A package manager is a collection of software tools that automates the process of installing, upgrading, configuring, and removing computer programs for a computer's operating system.


NPM (Node Package Manager) is an example of a package manager

---


##### Basic Functions of a package manager
The basic functions of the PM are:

* Extract packages
* Ensure the integrity and authenticity of the package --> verify digital certificates 
* Looking up, downloading, installing or updating existing software
* Group packages by function to reduce user confusion
* Manage dependencies to ensure a package is installed with all packages it requires and prevent **dependency hell**

---

#### How does it help with dependencies? 

Solves Dependecy Hell

---



What is Dependency Hell?

<iframe src="https://giphy.com/embed/Lopx9eUi34rbq" width="480" height="327" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

---


When a package depends on another package as a prerequisite, it will either not install or work as expected if the latter is missing or incorrectly set up. 

A developer then attempts to install the dependency, which in turn may depend on yet more packages. This could quickly become unmanageable if the developer tries to install all these dependencies manually.

---

Package managers solve this problem by resolving dependencies. 
Because every package comes with metadata, the PM knows what are the dependencies and what versions of those dependencies ought to be used.

---

#### What is package.json?? 

The json file contains a lot of meta-data about your project. But mostly it will be used for two things:

* Managing dependencies of your project
* Scripts, that helps in generating builds, running tests and other stuff in regards to your project

---

Example of Package.json file

```

{ "name": "node-js-sample",
  "version": "0.2.0",
  "description": "A sample Node.js app using Express 4",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "express": "^4.13.3"
  },
  "engines": {
    "node": "4.0.0"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/heroku/node-js-sample"
  },
  "keywords": [
    "node",
    "heroku",
    "express"
  ],
  "author": "Mark Pundsack",
  "contributors": [
    "Zeke Sikelianos <zeke@sikelianos.com> (http://zeke.sikelianos.com)"
  ],
  "license": "MIT"
}
```

---



#### NPM init 

```
npm init # This will trigger the initialization

```
npm init is a command that can be used to set up a new or existing npm package. Creates a package.json file


---

## `npm install`

#### What is the difference between installing a package globally, installing it as a dependency, or installing it as a development dependency?

---

> npm is the **package manager** for the Node JavaScript platform. It puts **modules** in place so that **node** can find them, and manages dependency conflicts intelligently.

            `npm install`

installs a package, and any packages that it depends on. 

---

#### 1. NPM as dependency:

This installs your package in the current working directory.


Install all modules listed as dependencies in package.json 

---


#### 2. NPM globally


In global mode it installs the current package context (ie, the current working directory) as a global package.


#### Installing a package globally allows you to use the code in the package as a set of tools on your local computer.

---

#### 3. NPM as development dependencies

Intended as development-only packages that are unneeded in production. 

(example testing packages, webpack or Babel)
When you go in production, if you type npm install and the folder contains a package.json file, they are installed, as npm assumes this is a development deploy. 



 
---

---



### When would you use each? 



If you’re installing something that you want to use in your **program**, using require('whatever'), then install it locally, at the root of your project.

If you’re installing something that you want to use in your **shell**, on the **command line** or something, install it globally, so that its binaries end up in your PATH environment variable.

With NPM, you can add development dependencies to your project called **devDependencies** . These type of dependencies are only required for development purposes, like testing your code or specify the code coverage.

---

### How would you do each in the command line?

As a dependency:

`npm install`

Globally:

`npm install -g or global`

As development dependency:

 `nom install--save-dev`

---

### Why is it normally a bad idea to install a package globally?

Your project depends on them. If your project depends on a package, it should be documented in **package.json** so that you can guarantee that it is installed when someone types npm install. 

Otherwise, you’ll need to add extra steps in your README file to inform anyone else who clones your project that they need to install each of your global dependencies as well.

https://docs.npmjs.com/


---

## Package files

---

#### Where does NPM install packages? 


---



When you install a package using npm you can perform 2 types of installation:

---


* Local install
* Global install

---


By default, when you type an npm install command, like:

![](https://i.imgur.com/cv4gEJ8.png)

The package is installed in your local node_modules folder.

When this happens, npm also adds the package in the dependencies property of the package.json file in the folder.

---


A global installation is performed using the -g flag:

![](https://i.imgur.com/xcvBhUb.png)

When this happens, npm won't install the package under the local folder, but instead, it will use a global location.


---



### But where, exactly?

![](https://media.giphy.com/media/3o7btXJrqLo5bbtQDm/giphy.gif)

---



The npm root -g command will tell you where that exact location is on your machine.

```
npm root -g
```



---


### And in my code?


---



#### To add it:
To use it in your code, you just need to import it into your program using `require`:

![](https://i.imgur.com/Lc7BgaO.png)


---



#### To uninstall it:
To uninstall a package you have previously installed locally (using npm install `package-name` in the node_modules folder, run:

![](https://i.imgur.com/dQCKdiA.png)



---



# Why is it important to make sure that installed packages aren't included in your repositories? 


---



## The problem

![](https://media.giphy.com/media/l0HUjjyZk7vefL5Nm/giphy.gif)

---

Imagine that you have just finished an app and you will have to support it for 3-5 years. 
What's happen next?


---


#### First possibility
> Well, you don't want:

* Depending on someone's npm module 

> Because 

* It can disappear
* You will not be able to update your app anymore



---



#### Second possibility
* You have your private modules which are not accessible from the internet and so you can't build your app on the Internet. 

* Or you just don't want to depend on npm service for some reasons.


---



## How do you prevent Git from including these files in your repository?


---


Create the .gitignore file!!!

![](https://media.giphy.com/media/A9grgCQ0Dm012/giphy.gif)


---


#### What for?

.gitignore - Specifies intentionally untracked files to ignore


```
#dependencies
node_modules/
```



---



#### Why?

* node_module is too big and you already have package.json that helps to install all packages in node_module by npm install command.

* keep small, clean and maintainable 

* There is no need to have them, just refer to the package.json file and install what you need


---


### Create amazing gitignore files!!!
![](https://i.imgur.com/9436sSM.png)


---



![](https://media.giphy.com/media/WUq1cg9K7uzHa/giphy.gif)



---



# Resources

uninstall npm packages : https://nodejs.dev/uninstalling-npm-packages
create gitignore file : https://gitignore.io/

*Eloquent Javascript* great chapter on Modules: https://eloquentjavascript.net/10_modules.html

*Free Code Camp* Dependencies are the devil: https://www.freecodecamp.org/news/code-dependencies-are-the-devil-35ed28b556d/

