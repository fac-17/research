# SQL vs NoSQL databases
![](https://media.giphy.com/media/k6hGoGvcDsczHuPHQ3/giphy.gif)


---




**What's the difference?** :cold_sweat: 


* SQL databases are relational (defines relationships in the form of tables.)

* noSQL databases are non-relational/distributed (do not require a fixed schema, avoids joins)

---


**SQL** databases use structured query language (SQL) for defining and manipulating data & are table-based. SQL requires that you use predefined schemas to determine the structure of your data before you work with it. In addition, all of your data must follow the same structure. :nail_care: 



---


**noSQL** database, on the other hand, has dynamic schema for unstructured data, and data is stored in many ways: it can be column-oriented, document-oriented, graph-based or organized as a KeyValue store. Does not require a particular query language. :frowning: 



---



**Examples** 

**SQL** --> Oracle, Postgres, and MS-SQL

**noSQL** --> MongoDB, Redis, Neo4j, Cassandra, Hbase



---




## Examples of the data structure of SQL and NoSQL databases

---

![](https://ottheedge.com/wp-content/uploads/2019/07/NoSQL-Database-Market.png)

---

![](https://miro.medium.com/max/1000/1*6aNDZOYTCkRGNBMJ9tHQkQ.jpeg)

---

### SQL

---

1. Relational database in tabular format (rows and columns)
![](https://docs.microsoft.com/da-dk/azure/architecture/data-guide/images/example-relational2.png)

---

2. Online analytical processing, or OLAP uses multidimensional data ![](https://gccontent.blob.core.windows.net/gccontent/blogs/legacy/c1/2014/11/OLAP_cube-300x257.png)

---

### NoSQL

---

1. A column family containing 3 rows. Each row contains its own set of columns. 
![](https://database.guide/wp-content/uploads/2016/06/wide_column_store_database_example_column_family-1.png)

---

2. A graph database is essentially a collection of nodes and edges. Each node represents an entity (such as a person or business) and each edge represents a connection or relationship between two nodes. 

---

![](https://itknowledgeexchange.techtarget.com/overheard/files/2014/01/Graph-database-sketch.jpg)

---

3. Document database
![](https://docs.mongodb.com/manual/_images/data-model-normalized.bakedsvg.svg)

---

4. Key - Value ![](https://upload.wikimedia.org/wikipedia/commons/5/5b/KeyValue.PNG)

---

 ## Pros and cons of SQL and NoSQL databases
 
 https://www.softwaretestinghelp.com/sql-vs-nosql/

---

|    SQL    | NoSQL    |
| -------- | -------- |
| -/+ fixed data structure     | + flexible data structures     |
| + normalized data | - redundant data |
| + standard and powerful query language | - no standard interface, less powerful queries |

---

|    SQL    | NoSQL    |
| -------- | -------- |
| + commercial and community support due to age of the technology | - less support |
| + code free |  + hierarchical data | 
| + data retrieval speed | + handles big data |

---

## Examples of queries for SQL and NoSQL databases :anguished: 

![](https://miro.medium.com/max/1050/1*O7_3IvmyKdY1yPC23hASQQ.jpeg)

---

This question is the source of a number of jokes, including:
![](https://qph.fs.quoracdn.net/main-qimg-3d6ed6c0ec5f86eb2194df208e8817b0)

---

- The truth is that NoSQL is NOT a standard. It does NOT have a specification. Of any kind.
- All it is is a term that describes a whole bunch of completely-different products.

---

In reality, you have a number of ways to query NoSQL databases, including:

- Ironically, some NoSQL databases now support SQL for querying;
- Most NoSQL databases have unique custom interfaces(eg: MongoDB)
- Many NoSQL databases support (or have plug-ins to e.g. Hadoop that support) Map/Reduce style "querying".

---

## That being said, here are some examples for queries

---

### Selecting everything from a collection:
- SQL
```SELECT * FROM userdetails;```
- NoSQL(MongoDB)
```db.userdetails.find();```

---

### Selecting with a condition
- SQL
```SELECT * FROM userdetails WHERE name = "importantperson"```
- MongoDB
```db.userdetails.find({name:"importantperson"})```

---

## But switch to anything other than MongoDB and you have new syntax 
## (NoSQL is a concept, not a product/language):angry:

---

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQcR9pkggJfftSncQjp0kRoWk1UOFKAvgyqo4-8sryf3ukKATra)
