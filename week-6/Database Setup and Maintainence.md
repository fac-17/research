# Database setup and maintenance

---

## What is a build script and why do you need one? 

---

### Build Script in general :construction_worker: 

A build script is sequence of tasks to be execution in order. This will run all files, methods, functions within the script. A script has a start and finish which can be rerun whenever required.

---

(Kinda like Heroku)

![](https://i.imgur.com/ZXZfcx0.png)


---

### Build Script for databases :construction: 
Build script is a script that creates tables and populates data into those database tables.

A SQL script is a set of SQL commands saved as a file in SQL Scripts. A SQL script can contain one or more SQL statements or SQL blocks. You can use SQL Scripts to create, edit, view, run, and delete script files.

---

> db_build.sql =>  database build script 
> db_buil.js => application build script

---

In other wordes, many databases can be built solely from scripts that create the schemas, database roles, tables, views, procedures, functions and triggers. 

---


### What's the point? :confused: 

* **AUTOMATION**: automates database build process over the whole project lifecycle
* **SPEED**: increase the speed of delivery of database changes
* **SYNCHRONISATION**: teams can synchronize application and database changes


---


--- 


* **TESTING**: allows for easier testing and deployment
* **INTEGRATION**: another thing to help you solve integration issues as they arise
* **REMOTE**: set up remote instances of your database - you may not have access to run SQL commands on a remote server (e.g. Heroku).


---

---

![](https://media.giphy.com/media/4FQMuOKR6zQRO/giphy.gif)



---


## Create a build script for a simple database (one or two tables only), which you can run locally. Check that it works for you and everyone on your team

---


![](https://i.imgur.com/okDCjNW.png)


---

![](https://i.imgur.com/ED3IJPW.png)

---

![](https://i.imgur.com/soFHLBe.png)

--- 

## What is database migration? 

![](https://media.giphy.com/media/dgEtXsuqq2PL2/giphy.gif)

---

![](https://media.giphy.com/media/cnhpl4IeYgU7MCBdV2/giphy.gif)

---

#### Build ?= migrations
In environments such as Production, Staging or User Acceptance Testing (UAT), teams sometimes use the term ‘the build’ more generically, to mean ” the artefact that will establish the required version of the database in that environment“. Unless the database doesn’t already exist, ‘the build’ in these environments is in fact a migration, and will modify the existing database to the required version, while preserve existing data, rather than “tear down and start again”.

### What is a Database Migration?



---


Database migration refers to the management of incremental, reversible changes to relational database schemas. A database migration is performed on a database whenever it is necessary to update or revert that database's schema to some newer or older version.

A schema migration tools modify database schemas while minimizing the impact of schema changes on any existing data in the database and also allowing you to 'roll back' to the previous st"

---

### But WHY do we do database migration? 

A migration can be done for multiple reasons:

* To change our database schema in a reversible way
* to change database vendors
* upgrade the database software
* move a database to the cloud
* update or revert that database to a newer or older version

---

### But HOW do we do data migration? 

To do this, the data itself must be converted to an appropriate structure and form on the target platform.
🔑 Some key tasks in this process include

* assessing the database size to determine how much storage is needed
* testing applications
* guaranteeing data confidentiality

---


## Resources 

[Better Ways to Build a DB](https://www.red-gate.com/simple-talk/sql/database-delivery/better-ways-to-build-a-database/)

[Some other notes... :sweat_smile:](https://github.com/fac-15/Research/blob/master/Week%206/database-setup-maintenance.md)
