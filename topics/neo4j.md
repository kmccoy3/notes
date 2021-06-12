
# Neo4j + Cypher Query Language (CQL)

# Nodes 🔴

### Create and View a Node

To create node with ID 'n':
```
CREATE (n);
```
* Semi-colon is only necessary when running multiple queries at once

To fetch node:
```
MATCH (n) RETURN n;
```

### Create and View Multiple Nodes

To create multiple nodes:
```
CREATE (n), (m)
```

To view all nodes:
```
MATCH (n) RETURN n
```

To view *some* nodes:
```
MATCH (n) RETURN n limit 2
```
* will return nodes with IDs 0, 1

### Search Nodes by IDs

```
MATCH (n) WHERE id(n) = 1 RETURN n
```
* can also use >, <, >=, <=, or <> (not equal)

To search multiple nodes:
```
MATCH (n) WHERE id(n) IN [1, 2, 0] RETURN n
```

### Delete Nodes and Database

To delete a node:
```
MATCH (n) WHERE id(n) = 1 DELETE n
```

To delete multiple nodes:
```
MATCH (n) WHERE id(n) IN [2, 3] DELETE n
```

To delete all nodes:
```
MATCH (n) DELETE n
```
* Will only work if there are no relationships in graph

To delete entire database:
in terminal,
```
sudo service neo4j stop
sudo service neo4j status
```
localhost:7474 should stop responding

```
sudo rm - rf /var/lib/neo4j/data/*
sudo service neo4j start
sudo neo4j status
```
* Default password is 'neo4j'

### Create and Search Nodes with Labels

Nodes can have any number of labels

To create node with label:
```
CREATE (n:Person)
```

```
MATCH (n) WHERE n:Person RETURN n
```

To create node with multiple labels:
```
CREATE (n:Person:American)
```

Search node by multiple labels:
```
MATCH (n) WHERE n:Person:American RETURN n
```
* returns nodes with **both** labels

If you want either or:
```
MATCH (n) WHERE n:Person OR n:American RETURN n
```

### Add Labels to Node

```
MATCH (n) SET n:Employee RETURN n
```

Using select ID:
```
MATCH (n) WHERE ID(n) = 0 SET n:Manager RETURN n
```

To add multiple labels to all nodes
```
MATCH (n) SET n:Vacation:Food RETURN n
```

### Remove and Update Labels on Nodes

To remove label from all nodes:
```
MATCH (n) REMOVE n:Person RETURN n
```

To remove label from select nodes:
```
MATCH (n) WHERE ID(n) IN [1, 2] REMOVE n:Person RETURN n
```

To remove multiple labels:
```
MATCH (n)  REMOVE n:Vacation:Food RETURN n
```

To update labels on node:
```
MATCH (n) WHERE ID(n) = 0 REMOVE n:Manager SET n:Director RETURN n
```

### List, count Labels and Delete Nodes Using Label

To list all labels:
```
MATCH (n) RETURN DISTINCT labels(n);
```

To list labels for specific nodes:
```
MATCH (n) WHERE ID(n) = 0 RETURN labels(n);
```

To count number of labels:
```
MATCH (n) RETURN DISTINCT count(labels(n));
MATCH (n) RETURN DISTINCT count(labels(n)), labels(n);
```

To delete nodes by label:
```
MATCH (n) WHERE n:Leader DELETE n;
```

### Create Node with properties

```
CREATE (n:Book{title:"1984"}) RETURN n;
```

Create node with multiple properties:
```
CREATE (x:Book{title:"1984", author:"Orwell", publisher:"Penguin"}) RETURN x
```
* attributes case sensitive!

### Node Property Datatypes

```
CREATE (x:Book{title:"1984", author:"Orwell", publisher:["Penguin", "Pub2"], price:22.50, pages:528, instock:false}) RETURN x;
```

### Search Nodes by Using Properties

To search nodes by properties:
```
MATCH (n:Book{author:"Name"}) RETURN n;
```

Search nodes by array of properties:
```
MATCH (n:Book{Publisher:["pub1", "pub2"]}) RETURN n
```

Using logical operators:
```
MATCH (n:Book) WHERE n.price < 1000 AND (n.author = "author1" OR n.author = "author2") RETURN n
MATCH (n:Book) WHERE toInt(n.pages) = 528 RETURN n;
MATCH (n:Book) WHERE n.author IN ["author1", "author2"] RETURN n;
```

### Update Properties on Node

```
MATCH (n) WHERE n.title = "old" SET n.title = "new" RETURN n;
MATCH (n:Book{title="old"}) SET n.title = "new" RETURN n;
```

To update multiple properties:
```
MATCH (n:Book{title:"title"}) SET n.author = "newAuthor", n.stock = true, n.price = 709 RETURN n;
```

To add property values to node:
```
MATCH (n:Book{title="old"}) SET n += {price: 176.00, pages: 28} RETURN n;
```

To add label to node using property:
```
MATCH (n) WHERE n.title = "title" SET n:Bestseller RETURN n;
```

To copy properties to nodes:
```
MATCH (gp{title:"title"}), (s1{title:"title2"}) SET gp = s1 RETURN gp, s1
```

### Delete Property From Node

```
MATCH (x:Book{author:"Orwell"}) SET x.publisher = NULL RETURN x;
MATCH (s:Book) WHERE s.author = "Orwell" SET s.publisher = NULL RETURN s;
```

Removing a property from all nodes:
```
MATCH (n) REMOVE n.pages RETURN n;
```

Remove property using label:
```
MATCH (n) WHERE n:Bestseller REMOVE n.title RETURN n;
```

Remove property by property:
```
MATCH (n) WHERE n.author = "author1" REMOVE n.instock RETURN n;
```

Remove node by property:
```
MATCH (n) WHERE n.instock = false DELETE n;
```

Remove property from specific nodes:
```
MATCH (n) WHERE id(n) = 17 REMOVE n.price RETURN n;
```

# Relationships →

```
CREATE (node1)-[:RelationshipType]->(node2)
```

# Importing Data with Neo4J
There are a few options for importing data into neo4j:
* LOAD CSV
* neo4j-admin
* neo4j ETL tool
* APOC + Cypher
* APOC + Cypher + jdbc
* programming language + driver

Normalized data represents data as separate files containing IDs, with another file containing the relationships between IDs.
Denormalized data contains all data in one file.

Can transofmr data with
    toInteger()
    toFloat()

If all fields have data, then split() alone will work. If, however, some fields may have no values and you want an empty list created for the property, then you use split() together with coalesce().


CREATE DATABASE name_of_database

:dbs to switch



If the number of rows exceeds 100K, then you have two options.

The first option is to use :auto USING PERIODIC COMMIT LOAD CSV. Placing :auto USING PERIODIC COMMIT enables the load, by default, to commit its transactions every 1000 rows which will enable the entire import of a large file to succeed. However, there are certain types of Cypher constructs that will cause :auto USING PERIODIC COMMIT to be ignored. Cypher statements that use eager operators will prevent you from using :auto USING PERIODIC COMMIT. Some examples of these eager operators include:

    collect()

    count()

    ORDER BY

    DISTINCT

If you cannot use :auto USING PERIODIC COMMIT because your Cypher include some eager operators, then you can use APOC to import the data, which you will learn about in the the next lesson.



:auto USING PERIODIC COMMIT 500
LOAD CSV WITH HEADERS FROM
  'https://data.neo4j.com/v4.0-intro-neo4j/movies1.csv' as row
MERGE (m:Movie {id:toInteger(row.movieId)})
    ON CREATE SET
          m.title = row.title,
          m.avgVote = toFloat(row.avgVote),
          m.releaseYear = toInteger(row.releaseYear),
          m.genres = split(row.genres,":")

APOC better for larger datasets

LOAD CSV WITH HEADERS
FROM 'file:///people.csv'
AS line
RETURN line LIMIT 10  

LOAD CSV WITH HEADERS FROM
'https://data.neo4j.com/v4.0-intro-neo4j/directors.csv' AS row
MATCH (movie:Movie {id:toInteger(row.movieId)})
MATCH (person:Person {id: toInteger(row.personId)})
MERGE (person)-[:DIRECTED]->(movie)
ON CREATE SET person:Director


# Neo4J Bloom


If you need to wipe out everything from the db including indexes (providing you have APOC) CALL apoc.schema.assert({},{},true); MATCH (n) DETACH DELETE n;

  github with good examples: https://dev.neo4j.com/bloom-training-repo

Search Phrases to create new functionality


# Documentation

Sources / Further Reading:
* [neo4j manual](https://neo4j.com/docs/cypher-manual/current/)
* [neo4j course](https://neo4j.com/graphacademy/training-intro-40/00-intro-neo4j-about/)
* [neo4j video tutorials (nodes only)](https://neo4j.com/blog/neo4j-video-tutorials/)
* https://www.javatpoint.com/neo4j-tutorial
