[Cheat Sheet](https://neo4j.com/docs/cypher-cheat-sheet/5/auradb-enterprise/)

### 1. Database Creation

```cypher
CREATE DATABASE SampleGraphDatabase
```

This creates a database named SampleGraphDatabase

### 2. View data

Currently our database is empty

### 3. Insert data

Data is stored in Neo4j as nodes. Each node has a label and properties.

Think of labels as identifiers for a node. It tells us what type of node it is.

If you are familiar with SQL, you would know about columns. Properties are similar to columns

Let us create a Person node and give it a property called name.

```cypher
CREATE (p: Person {name: "Abhinav", userID: 1})
```

### 4. Fetch data

Let's fetch the data we just inserted

```cypher
MATCH (n:Person) RETURN n
```

![download](https://github.com/blacksmithop/Neo4j_For_Dummies/assets/60320192/9327d05b-11e2-4baa-a805-08ce95036176)
![download](https://github.com/blacksmithop/Neo4j_For_Dummies/assets/60320192/e6eb9deb-bef8-47e3-a83b-545a3e0f4b6e)

Here's the node in detail. As you can see each node columns with an id and elementid property by default.

Think of <id> as the ID field in SQL, we will be using this in a lot of queries.

name is the property we added to that node.

Now that we have a added a node, it will show up under Datatbase Information.
![download](https://github.com/blacksmithop/Neo4j_For_Dummies/assets/60320192/895ba02f-86dc-4c41-ac2e-f9ec34248333)

### 5. Node Relationship

We can create relationships between nodes having different labels.

First, let us create another node.

```cypher
CREATE (AdminProfile: Profile {created_date: datetime("2024-06-30T18:40:32.142+0100"), userID: 0})
```

```cypher
CREATE (ADMIN: Person{name: "Admin User"})
```

Now let us create a relationship called IsOwnerOf

```cypher
MATCH (a:Person),

(b:Profile)

WHERE a.userID = b.userID
```

```cypher
CREATE (a)-[:IsOwnerOf]->(b);
```

Now we have established a relationship between Profile and Person nodes based on their shared userID .

### 6. Fetch data with filters

We can filter our query results with a WHERE clause

```cypher
MATCH (n) WHERE n.userID = 1 RETURN n
```

![download](https://github.com/blacksmithop/Neo4j_For_Dummies/assets/60320192/a7fd0903-7e30-4ef2-bb82-c45976148933)

As you can see these nodes have a relation between them.

Here's the entire database
![download](https://github.com/blacksmithop/Neo4j_For_Dummies/assets/60320192/0506dfa8-6239-4eaf-91f6-16894aded59a)

