---
author: Bidit Sadhukhan
date: "2021-04-03T22:41:10+05:30"
description: "Discover the power of Gremlin in OrientDB. Learn the basics, explore advanced queries, and unlock valuable insights from your graph data."
draft: false
github_link: "https://biditsadhukhan.hashnode.dev/getting-started-with-gremlin-in-orientdb-unleash-the-power-of-graph-databases"
image: /images/blogs-images/orientdb.avif
tags:
- Gremlin
- Orientdb
- demodb
- NoSql
- Graph-traversal
title: "Getting Started with Gremlin in OrientDB: Unleash the Power of Graph Databases"
toc: true
---

# Installation

Are you ready to embark on a graph-filled adventure with OrientDB and Apache TinkerPop? Let's dive into the installation process and unleash the power of graphs in your hands.

### Binary Packages: The Shortcut to Graphland

To get started quickly, you can download the Apache TinkerPop 3-enabled edition of OrientDB. This special edition combines all the fantastic features of the OrientDB Community Edition with seamless integration with the TinkerPop stack. With this binary package, you'll have everything you need to dive headfirst into the world of graphs.

Just imagine the possibilities as you explore the depths of graph databases with the convenience of Gremlin Console, Gremlin Server, and Gremlin Driver at your fingertips. Get ready to unlock the true potential of graph-powered applications.

### Source Code Installation:

Are you feeling adventurous and want to customize your graph experience? Then the source code installation is the perfect option for you. By following a few simple steps and harnessing the power of Git and Apache Maven, you can build the OrientDB Gremlin distribution from scratch.

This process empowers you to have full control over your graph environment. From compiling the code to generating the OrientDB Gremlin distribution, you'll feel like a true graph ninja, ready to conquer any graph-related challenge that comes your way.

So, roll up your sleeves, embrace the command line, and witness the magic of building your very own graph database distribution.

### Building the OrientDB Gremlin Distribution from Source Code

To embark on your graph-building journey, here's a step-by-step guide to building the OrientDB Gremlin distribution from the source code:

1. **Clone the OrientDB Repository**: Start by cloning the OrientDB repository using Git. Navigate to the desired directory and execute the following command:
    
    ```sql
    $ git clone https://github.com/orientechnologies/orientdb
    $ cd orientdb
    ```
    
2. **Switch to the Development Branch**: OrientDB follows a branching system, and to build the TinkerPop-enabled distribution, we need to switch to the `develop` branch. Execute the following command:
    
    ```sql
    $ git checkout develop
    ```
    
3. **Build the Core Distribution**: Before building the OrientDB Gremlin distribution, we need to build the core distribution. This step ensures that the core components are ready for integration. Execute the following command:
    
    ```sql
    $ mvn clean install -DskipTests
    ```
    
    Please note that skipping tests can expedite the build process, but running the tests is recommended for a comprehensive validation of the system.
    
4. **Clone the OrientDB Gremlin Repository**: Now it's time to clone the OrientDB Gremlin repository. Execute the following commands:
    
    ```sql
    $ cd ..
    $ git clone https://github.com/orientechnologies/orientdb-gremlin
    $ cd orientdb-gremlin
    ```
    
5. **Switch to the Development Branch**: Similar to the previous step, switch to the `develop` branch of the OrientDB Gremlin repository:
    
    ```sql
    $ git checkout develop
    ```
    
6. **Build the OrientDB Gremlin Distribution**: It's time to build the OrientDB Gremlin distribution. Execute the following command:
    
    ```sql
    $ mvn clean install
    ```
    
    If you prefer to skip tests, you can use the following command:
    
    ```sql
    $ mvn clean install -DskipTests
    ```
    
7. **Witness the Power of Graphs**: The build process will install all the necessary JAR files in your local Maven repository and generate archives under the distribution module inside the target directory. Now, get ready to unleash the potential of gremlin in orientdb.
    

## How to Open Gremlin:

Now that we have successfully installed OrientDB with the TinkerPop stack, it's time to open the door to the magnificent world of the Gremlin. In this section, we'll explore how to open Gremlin and start unleashing the power of graph queries.

### Opening OrientDB: The Gateway to Graphs

Before diving into Gremlin, we need to open OrientDB and establish our connection to the graph database. Follow these steps to open OrientDB:

1. Navigate to your desired location in the terminal. For example, if you have installed OrientDB in the "orientdb-tp3-3.2.19" folder, use the following command:
    
    ```bash
    cd orientdb-tp3-3.2.19/
    ```
    
2. Move to the "bin" directory using the following command:
    
    ```bash
    cd bin
    ```
    
3. To start OrientDB, execute the "[server.sh](http://server.sh)" script using the following command:
    
    ```bash
    ./server.sh
    ```
    
    Congratulations! You have now opened OrientDB, laying the foundation for our graph exploration journey.
    

### Opening Gremlin: Embrace the Power of Graph Queries

Now that OrientDB is up and running, it's time to open Gremlin and harness the true power of graph queries. Follow these steps to open Gremlin:

1. In the terminal, navigate to the "orientdb-tp3-3.2.19" folder (or the folder where you have installed OrientDB) using the following command:
    
    ```bash
    cd orientdb-tp3-3.2.19/
    ```
    
2. Move to the "bin" directory using the following command:
    
    ```bash
    cd bin
    ```
    
3. To start Gremlin, execute the "[gremlin.sh](http://gremlin.sh)" script using the following command:
    
    ```bash
    ./gremlin.sh
    ```
    
    If you are using Windows, use the following command instead:
    
    ```bash
    ./gremlin.bat
    ```
    
    Marvellous! You have successfully opened Gremlin and entered the realm of powerful graph queries.
    

### Embracing the Graph Adventure with Gremlin

Now that you have Gremlin open, you can start exploring the graph database, executing queries, and uncovering valuable insights. Let your imagination run wild as you navigate the vast world of graph structures, relationships, and patterns.

To get started, use the Gremlin console to interact with the graph database. Try executing basic queries, traversing the graph, and discovering the power of Gremlin's expressive query language. The possibilities are endless as you traverse the nodes and edges, uncovering hidden connections and extracting meaningful information.

Remember, you are now equipped with the tools and knowledge to harness the power of Gremlin and unleash the true potential of graph databases. Happy graph querying!

```markdown
// Sample Gremlin code for reference

// Create a graph traversal instance
graph = OrientGraph.open();

// Execute a basic query
graph.V().hasLabel('person').values('name')

// Traverse the graph and find related nodes
graph.V().has('person', 'name', 'John').out('friends').values('name')

// Close the graph when you're done
graph.close()
```

Feel free to experiment with different queries, traverse the graph, and explore the vast possibilities of Gremlin. Enjoy your graph adventure!

### Plugins: Expanding the Capabilities

Before we embark on our graph traversal journey with Gremlin and OrientDB, let's explore the power of plugins. Plugins provide additional functionality and extend the capabilities of the system. In the context of Gremlin and OrientDB, two essential plugins come into play:

* **TinkerPop Server Plugin**: Enables the Gremlin Server functionality, allowing remote connectivity and execution of Gremlin queries.
    
* **OrientDB Plugin**: Integrates OrientDB with the TinkerPop stack, providing seamless integration and access to the graph database.
    

By activating these plugins, we unlock a world of possibilities for graph querying and analysis.

To activate the plugins, follow these steps:

1. Launch the Gremlin Console by executing the [`gremlin.sh`](http://gremlin.sh) script in the `bin` directory of your OrientDB installation.
    
2. Once the Gremlin Console is open, you can activate the plugins using the following commands:
    
    ```sql
    gremlin> :plugin use tinkerpop.server
    gremlin> :plugin use tinkerpop.orientdb
    ```
    
    Marvellous! The plugins are now activated, expanding the capabilities of Gremlin and integrating OrientDB into the TinkerPop ecosystem.
    

## Connect Your Gremlin Server with OrientDB Server

To start traversing the graph within the OrientDB server, establish a connection between your Gremlin server and the OrientDB server. Use the following command:

```sql
gremlin> graph = org.apache.tinkerpop.gremlin.orientdb.OrientGraph.open("remote:localhost/demodb");
```

Now you are connected to the OrientDB server, and you can start traversing the graph and executing powerful Gremlin queries.

## Traversal Within the Graph

With the connection established, we can dive into the exciting world of graph traversal. To perform graph traversals, we'll use the Gremlin traversal API provided by OrientDB.

To create a graph traversal instance, use the following command:

```sql
gremlin> g = graph.traversal();
```

Now you have a `g` object that represents the graph traversal source, allowing you to explore and traverse the graph using Gremlin query syntax.

For example, you can execute basic queries like:

```sql
gremlin> g.V().hasLabel('person').values('name')
```

This query retrieves the names of all vertices labeled as "person" in the graph.

You can also traverse the graph and find related nodes using various graph traversal steps. For example:

```sql
gremlin> g.V().has('person', 'name', 'John').out('friends').values('name')
```

This query finds the vertex labeled as "person" with the name "John" and traverses its outgoing edges labeled as "friends" to retrieve the names of connected vertices.

Remember to close the graph when you have finished your traversal:

```sql
gremlin> graph.close()
```

By leveraging the power of the OrientDB Gremlin plugin and the Gremlin traversal API, you can traverse the graph, discover relationships, perform complex queries, and gain valuable insights from your data.

## Queries with Gremlin: Unleash the Power of Graph Traversal

In this section, we will explore various Gremlin queries that allow you to traverse and analyze your graph data using the OrientDB Gremlin plugin. Get ready to unleash the power of graph traversal!

1. Retrieve all vertices in the graph:
    

```sql
g.V()
```

1. Retrieve all edges in the graph:
    

```sql
g.E()
```

1. Retrieve a specific vertex by ID:
    

```sql
g.V('vertexID')
```

1. Retrieve the outgoing edges of a vertex:
    

```sql
g.V('vertexID').outE()
```

or

```sql
'vertexID'.edges(Direction.OUT)
```

1. Retrieve the incoming edges of a vertex:
    

```sql
g.V('vertexID').inE()
```

or

```sql
'vertexID'.edges(Direction.IN)
```

1. Retrieve the neighbors of a vertex (vertices connected by outgoing/incoming edges):
    

```sql
g.V('vertexID').both()
```

1. Retrieve the value of a specific property of a vertex or edge:
    

```sql
g.V('vertexID').values('propertyName')
g.E('edgeID').values('propertyName')
```

1. Filter vertices based on a specific property value:
    

```sql
g.V().has('propertyName', 'propertyValue')
```

1. Retrieve the number of vertices in the graph:
    

```sql
g.V().count()
```

1. Retrieve the number of outgoing edges for a specific vertex:
    

```sql
g.V('vertexID').outE().count()
```

1. Retrieve the number of incoming edges for a specific vertex:
    

```sql
g.V('vertexID').inE().count()
```

1. Filter vertices based on multiple conditions:
    

```sql
g.V().has('property1', 'value1').has('property2', 'value2')
```

1. Retrieve vertices and their outgoing edges based on a specific property value:
    

```sql
g.V().has('property', 'value').outE()
```

1. Retrieve vertices and their incoming edges based on a specific property value:
    

```sql
g.V().has('property', 'value').inE()
```

1. Retrieve the shortest path between two vertices:
    

```sql
g.V('vertexID1').shortestPath().with(ShortestPath.target, g.V('vertexID2')).path()
```

1. Traverse vertices up to a certain depth:
    

```sql
g.V('vertexID').repeat(out().simplePath()).times(3).path()
```

1. Sort vertices based on a property value:
    

```sql
g.V().order().by('property')
```

1. Group vertices based on a property value:
    

```sql
g.V().group().by('property')
```

1. Retrieve vertices with the highest value of a specific property:
    

```sql
g.V().has('property').order().by('property', decr).limit(1)
```

1. Delete a vertex and its associated edges:
    

```sql
g.V('vertexID').drop()
```

1. Create a new vertex with properties:
    

```sql
g.addV('vertexLabel').property('propertyName1', 'value1').property('propertyName2', 'value2')
```

1. Update the value of a specific property for a vertex:
    

```sql
g.V('vertexID').property('propertyName', 'newValue')
```

1. Calculate the average value of a numeric property across vertices:
    

````sql
g.V().values('numericProperty').mean

24. Retrieve the distinct property values of all vertices:
```groovy
g.V().values('property').dedup()
````

1. Retrieve vertices and their incoming edges with a specific label:
    

```sql
g.V().inE('edgeLabel')
```

1. Retrieve vertices and their outgoing edges with a specific label:
    

```sql
g.V().outE('edgeLabel')
```

1. Retrieve vertices and their properties:
    

```sql
g.V().valueMap()
```

1. Retrieve vertices and their adjacent vertices (outgoing):
    

```sql
g.V().out()
```

1. Retrieve vertices and their adjacent vertices (incoming):
    

```sql
g.V().in()
```

1. Retrieve vertices and their adjacent vertices (both outgoing and incoming):
    

```sql
g.V().both()
```

1. Retrieve the number of outgoing edges for each vertex:
    

```sql
g.V().project('vertex', 'outEdgeCount').by().by(outE().count())
```

1. Retrieve vertices with a specific property that contains a substring:
    

```sql
g.V().has('property', Text.containing('substring'))
```

1. Filter vertices based on a numeric range:
    

```sql
g.V().has('property', between(lowerBound, upperBound))
```

1. Filter vertices based on a property value is null or not null:
    

```sql
g.V().has('property', null)
g.V().has('property', neq(null))
```

1. Filter vertices based on multiple properties and their values:
    

```sql
g.V().has('property1', value1).has('property2', value2)
```

1. Adding a new vertex:
    

```sql
g.addVertex()
```

1. Adding a new edge:
    

```sql
'vertexID1'.addEdge('EdgeID', 'vertexID2')
```

These queries provide a glimpse into the power of Gremlin and the versatility it offers for traversing, querying, and analyzing your OrientDB graph database. Experiment with these queries and explore the vast possibilities that Gremlin brings to your graph data analysis journey. Enjoy the exciting world of graph traversal!

## Conclusion

In this blog post, we have delved into the world of Gremlin, the graph traversal language, and its integration with OrientDB. We have covered various Gremlin queries that allow you to traverse, query, and analyze your graph data using the OrientDB Gremlin plugin. From retrieving vertices and edges to filtering, sorting, and performing complex traversals, Gremlin offers a powerful and flexible way to interact with your OrientDB graph database.

To further explore the capabilities of Gremlin and its integration with OrientDB, we encourage you to visit the [OrientDB Documentation](https://orientdb.org/docs/3.0.x/gremlin/Gremlin.html) for detailed information, examples, and advanced use cases. The documentation provides comprehensive insights into using Gremlin with OrientDB, including supported Gremlin steps, query optimization techniques, and more.

Additionally, if you're interested in using OrientDB with Gremlin Console and TinkerPop, we recommend checking out our blog post ["Getting Started with Orientdb in Gremlin"](link-to-your-blog), where you'll find interesting examples and step-by-step instructions to kickstart your journey.

If you haven't installed OrientDB yet, don't worry! Check out our comprehensive guide on [**OrientDB installation**](https://biditsadhukhan.hashnode.dev/complete-guide-to-orientdb-installation-configuration-and-running-gremlin-commands-on-ubuntu-2204) to get up and running quickly.

To take your OrientDB experience further and master Orient SQL, head over to our blog on [**executing basic to advanced queries in the demodb database**](https://biditsadhukhan.hashnode.dev/mastering-orientdb-console-executing-basic-to-advanced-queries-in-the-demodb-database). There, you'll find a wealth of information and examples to enhance your skills.

So, whether you're a graph enthusiast, a data scientist, or a developer looking to harness the power of graph databases, Gremlin in OrientDB opens up a world of possibilities. Dive into the documentation, explore the blog post, and unleash the full potential of Gremlin for your graph data analysis needs. Happy graph traversing!