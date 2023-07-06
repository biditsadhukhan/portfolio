---
author: Bidit Sadhukhan
date: "2023-07-02T19:53:33+05:30"
description: "Discover the power of Gremlin in OrientDB. Learn the basics, explore advanced queries, and unlock valuable insights from your graph data"
draft: false
image: /images/blogs-images/orientdb.avif
mathjax: true
tags:
- Orientdb
- NoSql
- database
- demodb
title: "Mastering OrientDB Console: Executing Basic to Advanced Queries in the Demodb Database"
toc: true
---

Welcome to our comprehensive guide on executing queries in the OrientDB console. Whether you're new to OrientDB or looking to enhance your querying skills, this blog post is here to help. We'll explore the powerful features of the console and demonstrate how to execute queries ranging from basic to advanced. In particular, we'll focus on leveraging the pre-installed Demodb database, which provides a rich dataset for experimentation and learning. By following along with this guide, you'll gain a solid understanding of the OrientDB console and its querying capabilities. You'll learn how to perform various operations, retrieve data, apply filters, perform aggregations, and more. We'll provide examples and explanations to ensure you grasp the concepts effectively. So, let's dive into the world of OrientDB and unlock its full potential by executing queries in the console!

Stay tuned for upcoming sections where we'll cover everything you need to know to become proficient in executing queries in the OrientDB console. Ready to get started? Let's begin!

## Getting started with the database

Before executing queries in the OrientDB console, ensure that you have both the server and console up and running. Follow these steps:

1. Start the OrientDB server by running the [`server.sh`](http://server.sh) script:
    
    ```bash
    $ ./server.sh
    ```
    
2. Once the server is running, open a new terminal window and start the OrientDB console by executing the [`console.sh`](http://console.sh) script:
    
    ```bash
    $ ./console.sh
    ```
    
    Now that the server and console are running, you can proceed with executing queries and connecting to the database.
    

### **Connecting to an existing database**

To connect to an existing database, use the following commands in the OrientDB console:

1. Connect to the OrientDB server by specifying the remote host and credentials:
    
    ```bash
    orientdb> connect remote:localhost root passwd
    ```
    
2. List the available databases:
    
    ```bash
    orientdb> list databases
    ```
    
3. Open a specific database by providing its name and credentials:
    
    ```bash
    orientdb> open database_name root passwd
    ```
    

### **Creating a new database**

To create a new database, execute the following commands in the OrientDB console:

1. Connect to the OrientDB server:
    
    ```bash
    orientdb> connect remote:localhost root passwd
    ```
    
2. Create a new database by specifying the storage type and path:
    
    ```bash
    orientdb> create database plocal:path/databasename root passwd
    ```
    

> There are other options also for creating a database like memory, so you can explore the [Orientdb documentations](https://orientdb.com/docs/3.1.x/console/Console-Command-Create-Database.html) for learning further.

### **Importing data from a file**

To import data from a file, such as a GraphML file or a file exported from Neo4j or also json, use the following command in the OrientDB console:

```bash
orientdb> import database ~/path/file.graphml -merge=true -keepallclasses
#replace the file.graphml with the name of the file you want to import for.
```

If you want to import a JSON file you can replace the file.format with the file.graphml and keep the remaining same. For knowing more you can refer to this page [Importing Database in OrientDb](https://orientdb.com/docs/3.1.x/console/Console-Command-Import.html)

### Importing CSV Data into OrientDB as a Graph

When working with OrientDB, you may need to import data from CSV files into a graph structure. Importing CSV data into OrientDB allows you to take advantage of its powerful graph capabilities for data analysis and querying.

**The ETL Process**

To import CSV data into OrientDB as a graph, you can follow these steps:

1. Prepare your CSV file in the required format.
    
2. Install and set up OrientDB on your system.
    
3. Refer to the [OrientDB documentation](https://orientdb.com/docs/2.2.x/Import-from-CSV-to-a-Graph.html) for detailed instructions on the Extract, Transform, Load (ETL) process. The documentation provides a step-by-step guide and examples to help you understand and execute the import process.
    

The OrientDB documentation will guide you through the entire process, including how to define the source file, configure the ETL process, and load the graph elements into the OrientDB database.

## Executing Basic Queries in OrientDB Demodb Database

The demodb database focuses on various entities involved in the travel agency's operations, such as users, customers, countries, orders, attractions, services, and reviews. Let's delve into the structure and relationships of these entities.

**Users and Profiles**

The core of the demodb database lies in the "Profiles" class, which stores information about the users registered on the social platform. Users can freely register and create profiles. The connections between users are represented by the "HasFriend" edge, indicating the friendship relationship between them.

**Customers and Countries**

Some users can become customers of the travel agency. When a user becomes a customer, a corresponding vertex is created in the "Customers" class. This vertex is linked to the associated profile using the "HasProfile" edge, establishing the relationship between the customer and their profile.

Customers are also automatically linked to a country through the "IsFromCountry" edge. The "Countries" vertex class stores information about different countries, enabling the association between customers and their respective countries.

**Orders and Services**

Orders made by customers are stored in the "Orders" vertex class. Each customer can have one or more orders, and the "HasCustomer" edge is used to connect orders with customers, representing the relationship between them.

As customers start visiting attractions or using services offered by the travel agency, specific edges are created to establish these connections. The "HasVisited" edge is used to link customers with attractions they have visited, while the "HasStayed" and "HasEaten" edges are used to link customers with services like hotels and restaurants, respectively.

**Reviews and Feedback**

The travel agency values customer feedback and stores reviews in the "Reviews" vertex class. Reviews are linked to customers through the "MadeReview" edge, indicating that a specific customer has made a review. Additionally, the "HasReview" edge connects reviews with the corresponding attractions or services, allowing users to provide feedback on their experiences.

Exploring the demodb database allows you to visualize how data is interconnected and how various entities relate to each other. This knowledge forms a solid foundation for further learning and exploring real-world database scenarios.

In the next sections, we'll dive deeper into executing queries and leveraging the graph section to visualize and analyze the demodb database.

To explore and execute basic queries in the OrientDB Demodb database, you can use the OrientDB console. OrientDB console supports OrientSQL commands, which allow you to interact with the database using SQL-like syntax.

To learn about the OrientSQL syntax and explore a wide range of console commands for querying and manipulating the database, I recommend referring to the [official OrientDB documentation](https://orientdb.com/docs/3.1.x/console/Console-Commands.html). The documentation provides comprehensive information, examples, and guidelines on using the console commands effectively.

By visiting the OrientDB documentation, you'll gain access to detailed resources that will help you understand and leverage the full potential of OrientDB's query capabilities.

Make sure to check out the [OrientDB Console Commands](https://orientdb.com/docs/3.1.x/console/Console-Commands.html) documentation for a deeper dive into executing queries and performing various operations in OrientDB.

## Exporting the `demodb` Database in OrientDB

Sometimes, you may need to export your OrientDB database for various reasons, such as migrating it to a different version of OrientDB or creating a backup. In OrientDB, you can export a database using the `EXPORT DATABASE` command. Let's see how you can export the `demodb` database.

### Export Command Syntax

The syntax for exporting a database in OrientDB is as follows:

```sql
EXPORT DATABASE <output-file>
      [-excludeAll]
      [-includeClass=<class-name>*]
      [-excludeClass=<class-name>*]
      [-includeCluster=<cluster-name>*]
      [-excludeCluster=<cluster-name>*]
      [-includeInfo=<true|false>]
      [-includeClusterDefinitions=<true|false>]
      [-includeSchema=<true|false>]
      [-includeSecurity=<true|false>]
      [-includeRecords=<true|false>]
      [-includeIndexDefinitions=<true|false>]
      [-includeManualIndexes=<true|false>]
      [-compressionLevel=<0-9>]
      [-compressionBuffer=<bufferSize>]
```

### **Exporting the** `demodb` Database

To export the `demodb` database in OrientDB, follow these steps:

1. Open the OrientDB console or use a compatible client.
    
2. Execute the following command to export the `demodb` database:
    
    ```bash
    EXPORT DATABASE <output-file> -includeInfo=true -includeClusterDefinitions=true
    ```
    
    Replace `<output-file>` with the desired path and filename for the export file.
    
    This command exports the full `demodb` database, including database information and cluster definitions.
    
3. Once the command is executed, the database will be exported to the specified `<output-file>`
    

**Additional Considerations:**

By default, the export command uses the JSON-based export format and compresses the file using the GZIP algorithm.

* Exporting a database does not lock it, so concurrent operations can still be performed during the export.
    
* Editing the exported JSON file may cause import failures, as there are constraints on the field order and indentation.
    
* If you need to create an exact snapshot of the database at a specific point in time, it's recommended to use the `BACKUP` command instead.
    

For more advanced options and customization, such as excluding specific classes or clusters, including or excluding schema, security settings, record contents, index definitions, or adjusting compression settings, please refer to the [**OrientDB documentation on exporting databases**](https://orientdb.com/docs/3.1.x/console/Console-Command-Export.html).

Remember to use the appropriate version of OrientDB for exporting and importing the database to ensure compatibility.

---

### Graph Section: Visualizing the Database and Executed Queries

OrientDB provides a dedicated graph section that allows you to visualize the database schema, clusters, records, and the results of executed queries in a graphical format. The graph section offers an intuitive way to explore the relationships and connections within your database.

To access the graph section in OrientDB Studio, follow these steps:

1. Open the OrientDB Studio in your web browser by accessing the URL.
    
    ```bash
    http://localhost:2480/studio/index.html
    ```
    
2. Navigate to the "Graph" or "Graph Section" tab.
    
3. The graph section will display an interactive graph visualization of your database schema.
    
4. You can explore the nodes and edges representing classes and relationships in the graph.
    
5. Additionally, when you execute queries in the OrientDB Console or OrientDB Studio, the results can be displayed in the graph section. This allows you to visualize the query results and the connections between records.
    

Using the graph section can greatly enhance your understanding of the database structure and the impact of the executed queries. It provides a visual representation that makes it easier to analyze complex relationships and identify patterns.

Take advantage of the graph section in OrientDB to gain deeper insights into your data and make informed decisions based on the visual representations.

---

### Understanding the Class Structure

In OrientDB, classes play a crucial role in structuring the data. Think of a class as similar to a table in a relational database but with some unique characteristics. A class allows you to define rules for grouping related records together. For instance, a class called 'Person' can store information about individuals, including properties like Name, Birthdate, and Favorite Number.

To see all the classes in your demodb database, you can execute the following command in the OrientDB console:

```sql
LIST CLASSES
```

This command will provide you with a list of classes in the database along with their details, such as class name, super-classes, clusters, and record count.

### The Power of Classes

Unlike traditional document databases or RDBMS models, OrientDB classes offer efficient storage for schema-less data. They provide flexibility while maintaining the ability to define constraints and schema when needed. This combination of flexibility and structure allows you to effectively manage and query your data.

### **Demodb Class Examples**

The demodb database includes various classes that represent different entities and their relationships. Let's take a look at a few examples:

* The 'Profiles' class stores user information and represents the users of the social platform.
    
* The 'Customers' class represents customers associated with the Travel Agency. When a user becomes a customer, a vertex in the Customers class is created and linked to their profile via the HasProfile edge.
    
* The 'Orders' class stores customer orders. Each customer can make one or more orders, and the HasCustomer edge is used to connect orders to customers.
    
* The 'Attractions' class represents various attractions like castles, monuments, theaters, or archaeological sites. Customers can visit these attractions, and edges like HasVisited are created to establish the connection.
    
* The 'Services' class represents services offered by the Travel Agency, such as hotels or restaurants. Customers can utilize these services, and edges like HasStayed or HasEaten are created to capture the usage.
    

Visit the [**OrientDB Documentation**](https://orientdb.com/docs/) to access the wealth of information available and enhance your understanding of the demodb database and beyond.

### Working with Graphs In OrientDB

Graph databases represent data in network-like structures consisting of vertices and edges. The OrientDB Graph model follows the property graph concept, where a vertex represents an entity connected to other vertices through edges.

**Creating Vertices-** To create a vertex in OrientDB, you can use the `INSERT` command with the `V` class:

```sql
 INSERT INTO V SET name='Jay'
```

Alternatively, you can use the graph-specific command `CREATE VERTEX`:

```sql
CREATE VERTEX V SET name='Jay'
```

Using graph commands ensures the consistency of your graph data. OrientDB provides a set of graph commands that simplify managing graphs from the console.

**Use Case: Social Network for Restaurant Patrons**

Let's explore a use case to understand graph modelling in OrientDB. Imagine creating a social network based on restaurants and their patrons. We'll start by defining classes for individual customers and restaurants.

```sql
CREATE CLASS Person EXTENDS V
CREATE CLASS Restaurant EXTENDS V
```

By extending the `V` class, we create classes specific to our use case. Next, let's populate the graph with some data:

```sql
CREATE VERTEX Person SET name='Luca'
CREATE VERTEX Person SET name='Bill'
CREATE VERTEX Person SET name='Jay'

CREATE VERTEX Restaurant SET name='Dante', type='Pizza'
CREATE VERTEX Restaurant SET name='Charlie', type='French'
```

In this example, we created vertices for individual customers and restaurants. Each vertex represents a unique entity in the graph.

### Creating Edges

To establish connections between vertices, we need to create edges. In this use case, we'll create the `Eat` class to represent the relationship between a customer and a restaurant.

```sql
CREATE CLASS Eat EXTENDS E
```

Now, let's create an edge to represent a customer dining at a specific restaurant:

```sql
CREATE EDGE Eat FROM (SELECT FROM Person WHERE name='Luca')
          TO (SELECT FROM Restaurant WHERE name='Dante')
```

This edge indicates that Luca (a customer) eats at the restaurant Dante. Similarly, we can create edges for other customers and their preferred restaurants.

### Querying Graphs

With the graph data in place, we can perform queries to navigate and explore the relationships in the graph. OrientDB provides special functions to traverse edges, such as `OUT()`, `IN()`, and `BOTH()`, which helps retrieve adjacent vertices.

For example, to find all the people who eat at the restaurant Dante, you can use the `IN()` function:

```sql
SELECT IN() FROM Restaurant WHERE name='Dante'
```

This query returns the record IDs from the `Person` class that is connected to the restaurant Dante. To expand the result set and retrieve detailed information, you can use the `EXPAND()` function:

```sql
SELECT EXPAND(IN()) FROM Restaurant WHERE name='Dante'
```

Now, let's extend the social network by connecting individual users as friends. Create the `Friend` class as an edge:

```sql
CREATE CLASS Friend EXTENDS E
```

Next, create an edge to connect two friends, Luca and Jay:

```sql
CREATE EDGE Friend FROM (SELECT FROM Person WHERE name='Luca')
          TO (SELECT FROM Person WHERE name='Jay')
```

Since friendship is a bidirectional relationship, we can use the `BOTH()` function to retrieve both incoming and outgoing connections:

```sql
SELECT EXPAND(BOTH('Friend')) FROM Person WHERE name='Luca'
```

This query returns the friends of Luca,

including Jay, along with the corresponding edges.

To explore the restaurants patronized by Luca's friends, you can combine the `BOTH()` and `OUT()` functions:

```sql
SELECT EXPAND(BOTH('Friend').OUT('Eat')) FROM Person WHERE name='Luca'
```

This query retrieves the restaurants that Luca's friends have dined at, allowing you to understand the dining preferences within the social network.

**Lightweight Edges**

Starting from version 1.4.x, OrientDB introduces the concept of Lightweight Edges. Lightweight Edges are a performance optimization that eliminates the need for separate records for edges without properties.

To work with Lightweight Edges, you can use graph functions as usual. However, some queries might not return Lightweight Edges. In case you need to query edges directly, including those without properties, you can disable the Lightweight Edge feature:

```sql
ALTER DATABASE CUSTOM useLightweightEdges=FALSE
```

By executing this command, new edges will be created as standard Edges instead of Lightweight Edges. Existing edges are not affected by this change.

For more information on graph modelling in OrientDB and additional details about the Graph API, refer to the [OrientDB Graph API documentation](https://orientdb.com/docs/last/Graph-Database-Tinkerpop.html).

### Conclusions

"Congratulations, intrepid explorer! You've taken your first steps into the mesmerizing world of OrientDB using OrientSQL. But hold on tight, because there's so much more to uncover!

This blog has served as your trusty compass, guiding you through the basics of OrientDB. From creating databases and managing classes to executing queries and unleashing the power of graphs, you've become a savvy adventurer in this thrilling database realm.

But here's the secret: this is just the beginning of your extraordinary journey. OrientDB is like a vast treasure trove, brimming with advanced features and hidden gems. To unravel its full potential, I urge you to embark on your own exploration of the OrientDB documentation.

Within those digital pages, you'll discover the secrets of advanced query techniques, ingenious indexing strategies, distributed architectures, fortifying security measures, and performance optimization wizardry. It's a treasure map to unlock the full might of OrientDB!

Oh, and if you're a thrill-seeker who craves the excitement of traversing the graph, fear not! My blog [Getting Started with Gremlin in OrientDB](https://biditsadhukhan.hashnode.dev/getting-started-with-gremlin-in-orientdb-unleash-the-power-of-graph-databases) awaits your eager eyes. Dive into the world of Gremlin commands, uncovering the awe-inspiring connections and patterns hidden within your OrientDB database.

Remember, this blog may have ignited your passion for OrientDB, but the true adventure lies in your hands. Embrace the joy of continuous exploration, push the boundaries of what you can achieve, and unlock new realms of possibilities with OrientDB.

So, fellow adventurer, keep your compass pointed towards the OrientDB documentation, your sails set for new horizons, and let the thrilling quest continue! Happy coding, and may the OrientDB forces be with you!"