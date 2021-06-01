
# Neo4j

### Create and View a Node

To create node with ID 'n':
```
CREATE (n)
```

To fetch node:
```SQL
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

```

### Delete Property From Node
