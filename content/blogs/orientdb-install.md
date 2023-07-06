---
author: Bidit Sadhukhan
date: "2023-06-28T12:03:00"
description: "Install & configure OrientDB in Ubuntu 22.04. Execute Gremlin commands, explore the console, and optimize performance. Unlock OrientDB's power!"
draft: false
github_link: https://github.com/gurusabarish/hugo-profile
image: /images/blogs-images/orientdb.avif
tags:
- Orientdb
- NoSql
- Gremlin
title: Complete Guide to OrientDB Installation, Configuration, and Running Gremlin Commands on Ubuntu 22.04
subtitle: "Orientdb Version 3.2.19"
toc: null
---

# Installing OrientDB from Source on Ubuntu

OrientDB is a powerful, open-source multi-model database management system. This guide will walk you through installing OrientDB from source on Ubuntu.

## Prerequisites

Before proceeding with the installation, ensure that you have the following prerequisites:

* Ubuntu 22.04 operating system
    
* Maven
    
* Git
    
* curl
    
* Java version greater than 8 preferred
    

## Step 1: Set up the Environment

1. Open the terminal and navigate to the desired folder where you want to install OrientDB:
    
    ```bash
    cd desired_folder
    ```
    
2. Install Maven if not installed
    
    ```bash
    sudo apt install maven
    ```
    
3. Install git if not installed
    
    ```bash
    sudo apt install git
    # After this you can wish to configure git to use it for connecting to github or gitlab
    # Although it is not necessary for orientdb installation.
    ```
    
4. Install curl if not installed
    
    ```bash
    sudo apt install curl
    ```
    
5. Check the Java version by running the command
    
    ```bash
    java -version
    ```
    

## Step 2: Download and Build OrientDB

1. Download the OrientDB source code from the official GitHub repository:
    
    ```bash
    curl -o https://github.com/orientechnologies/orientdb orientdb_source
    ```
    
2. Switch to the develop branch to get the latest version:
    
    ```bash
    git checkout develop
    ```
    
3. If you have downloaded the OrientDB ZIP file, extract it:
    
    ```plaintext
    unzip orientdb-tp3-3.3.2.zip  # Check the extracted file (if a zip file is downloaded)
    ```
    

> *Note: Make sure to check the extracted file name.*

1. Navigate to the OrientDB folder:
    
    ```plaintext
    cd orientdb-tp3-3.3.2
    # Rename the file to orientdb
    mv orientdb-tp3-3.3.2 orientdb
    ```
    

Build and install OrientDB (skipping tests to save time):

```bash
mvn clean install -DskipTests
```

> Note: The installation takes some time so do not panic if a lot of things come up in the screen.

## Step 3: Install OrientDB

1. Go to the OrientDB distribution target folder:
    
    In the target folder you will find a lot of files with different extensions here we will choose the tar file for our installation.
    
    ```bash
    cd /orientdb/distribution-tp2/target
    ```
    
2. Copy the OrientDB tarball to the desired location (e.g., `/home/user/`):
    
    ```bash
    cp orientdb-community-tp2-3.2.19-SNAPSHOT.tar.gz /home/user/
    # user is the one the name in which you are logged into your desktop
    ```
    
3. Extract the OrientDB tarball:
    
    ```bash
    tar -xvf orientdb-community-tp2-3.2.19-SNAPSHOT.tar.gz
    ```
    

> *Note: Make sure to check the extracted file name.*

1. Renaming the file to a proper name:
    
    ```bash
    mv orientdb-community-tp2-3.2.19-SNAPSHOT orientdb_install
    ```
    

## Step 4: Start OrientDB

1. Navigate to the OrientDB installation's `bin` directory:
    
    ```bash
    cd orientdb_install/bin
    ```
    
2. Run the Orientdb server using the following command:
    
    ```bash
    ./server.sh 
    # the command is used to start the server.
    # on first time startup it will ask for the password so don't panic give a suitable password and remember it.
    # if there is no error in building the orientdb database then the server will run without any error.
    ```
    
3. Once the server is up and running, you can access the OrientDB Studio by opening a web browser and entering the following address:
    
    ```plaintext
    http://localhost:2480/studio/index.html
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688140044545/73eb3b4c-94c3-4479-b41f-b06fa7d50d75.png align="center")

A page like the above will open in your browser tab.

Congratulations! You have successfully installed OrientDB from source on Ubuntu. You can now start working with OrientDB, and access the OrientDB Studio to visually execute and manage your database.

# Accessing OrientDB from the Console

In addition to the OrientDB Studio, you can also access OrientDB directly from the console. This allows you to interact with the database using the powerful Gremlin command language and also the OrientSql commands.

To access OrientDB from the console, follow these steps:

1. Open a terminal window.
    
2. Navigate to the OrientDB installation's `bin` directory:
    
    ```bash
    cd orientdb_install/bin
    ```
    
3. Start the server (if it is not already running):
    
    ```bash
    ./server.sh
    ```
    
4. Once the server is running, open a new terminal window (or tab) to access the console.
    
5. Navigate to the OrientDB installation's `config` folder:
    
    ```bash
    cd orientdb_install/config
    ```
    
6. Open the `orientdb-server-config.xml` file for editing. You can use any text editor of your choice. For example, to use the `vi` editor:
    
    ```bash
    vi orientdb-server-config.xml
    ```
    
7. Locate the `<storages>` and `<users>` tags in the XML file
    
8. Within the `<storages>` tag, add the following code to define the storage:
    
    ```bash
    <storage name="databases" path="/path_to_the_folder/databases/*" userName="root" userPassword="passwd">
        <parameters>
            <parameter name="bufferSize" value="4096"/>
            <parameter name="wal" value="true"/>
            <!-- Add more storage-specific parameters if needed -->
        </parameters>
    </storage>
    ```
    
    Make sure to replace `/path_to_the_folder` it with the actual path to the folder where you want to store the databases. Set the `userName` and `userPassword` attributes according to your preference.
    
9. Within the `<users>` tag, add the following code to define the user:
    
    ```bash
    <user name="root" password="passwd" resources="*"/>
    <!-- Add more user definitions if needed -->
    #Replace passwd with the desired password for the root user.
    ```
    
10. Save the changes and exit the text editor.
    
11. Restart the server:
    
    ```bash
    # cntrl+c to stop the running server if prompted say yes
    ./server.sh
    ```
    
12. Then navigate to the OrientDB installation's `bin` directory in the new terminal window:
    
    ```bash
    cd orientdb_install/bin
    ```
    
13. Connect to the OrientDB server using the [`console.sh`](http://console.sh) command:
    
    ```bash
    ./console.sh
    ```
    

something like this will open up in the terminal

```bash
OrientDB console v.X.X.X (build 0) www.orientdb.com
Type 'HELP' to display all the commands supported.
Installing extensions for GREMLIN language v.X.X.X

orientdb>
```

Well done on completing the configuration process! Your changes to the `orientdb-server-config.xml` file have now been applied and will be utilized when launching the OrientDB server.

## Introduction to Gremlin: A Powerful Graph Traversal Language

In the world of graph databases, Gremlin stands out as a powerful graph traversal language. It provides a flexible and expressive way to query and manipulate graph data. With Gremlin, you can navigate through complex graph structures, perform advanced filtering and mapping operations, and extract valuable insights from your data.

### What is Gremlin?

Gremlin is a graph traversal language that allows you to interact with graph databases using a unified API. It provides a set of graph traversal steps and functions that enable you to traverse and manipulate the graph data. Gremlin is designed to be graph-agnostic, which means it can be used with various graph databases, including OrientDB.

### Why use Gremlin?

Gremlin offers several benefits for working with graph databases:

1. **Expressive and flexible**: Gremlin's syntax and fluent API allow you to express complex graph queries and operations in a concise and readable manner. It provides a wide range of traversal steps and functions to handle different graph scenarios.
    
2. **Graph-agnostic**: Gremlin is not tied to a specific graph database implementation, making it a portable and versatile choice. You can use Gremlin with various graph databases, including OrientDB, without having to learn different query languages.
    
3. **Traversals and transformations**: Gremlin allows you to traverse the graph data and apply transformations at each step. This makes it easy to navigate through the graph, filter nodes and edges based on specific criteria, and perform computations or aggregations on the data.
    
4. **Integration with programming languages**: Gremlin has extensive language bindings for popular programming languages like Java, Python, and JavaScript. This enables you to seamlessly integrate Gremlin queries into your existing applications or workflows.
    

## Getting Started with Gremlin in OrientDB

Now that you have configured the OrientDB server and accessed the console, you are ready to dive into the world of Gremlin. In the next section, we will explore how to execute Gremlin commands in the OrientDB console.

Let's unleash the power of Gremlin and unlock the full potential of your OrientDB database!

* Configuring OrientDB Server for Gremlin in the Console
    

To use Gremlin in the OrientDB console, you need to make some changes in the `orientdb-server-config.xml` file. This configuration file contains settings for the OrientDB server, including enabling Gremlin support. Follow the steps below to configure the OrientDB server for Gremlin:

1. Open the `orientdb-server-config.xml` file located in the config folder of your OrientDB installation.
    
2. In the file, search for the `<network>` tag and uncomment the following parameter to enable the Gremlin Server:
    
    ```xml
    <!-- Uncomment the following line to enable the Gremlin Server -->
    <protocol name="gremlin" implementation="com.orientechnologies.orient.server.network.protocol.binary.ONetworkProtocolBinary" />
    ```
    
    This parameter enables the Gremlin Server protocol for communication.
    
3. Locate the `<handlers>` tag and uncomment the following parameter to enable the Gremlin Server handler:
    
    ```xml
    <!-- Uncomment the following line to enable the Gremlin Server handler -->
    <handler class="com.orientechnologies.orient.graph.gremlin.OGremlinHandler" name="gremlin" />
    ```
    
    This parameter enables the Gremlin Server handler for processing Gremlin queries.
    
4. Save the `orientdb-server-config.xml` file after making the necessary changes.
    
5. Restart the OrientDB server for the changes to take effect.
    

If you are also using the Gremlin Server with OrientDB, you will find the configuration file `gremlin-server.yaml` for Gremlin Server-specific settings. This file is typically located in the config folder of your OrientDB installation. Adjust the configuration in this file according to your requirements.

It's important to note that the approach described above for running Gremlin in the OrientDB console utilizes the [Gremlin API](https://orientdb.org/docs/3.1.x/gremlin/Gremlin.html) rather than the Gremlin plugin. Another way to connect Gremlin with OrientDB is by installing the OrientDB Gremlin plugin. This can be done by following the instructions in the official documentation for [**Apache TinkerPop 3**](https://orientdb.org/docs/3.1.x/tinkerpop3/OrientDB-TinkerPop3.html).

In addition to using the Gremlin API, another way to connect Gremlin with OrientDB is by installing the OrientDB Gremlin plugin. This approach offers additional features and functionalities that enhance your experience with Gremlin and OrientDB. To install the OrientDB Gremlin plugin and learn more about its configuration and usage, you can refer to my blog post on [Getting Started with Gremlin in OrientDB](https://biditsadhukhan.hashnode.dev/getting-started-with-gremlin-in-orientdb-unleash-the-power-of-graph-databases). In this blog post, I have provided step-by-step instructions on how to install and configure the plugin, along with examples of executing basic Gremlin queries in OrientDB. By installing the OrientDB Gremlin plugin, you can unlock the full potential of Gremlin and leverage the power of OrientDB for graph database operations. The plugin provides seamless integration and compatibility between Gremlin and OrientDB, enabling you to execute complex graph traversals and analytics with ease. If you're interested in exploring the OrientDB Gremlin plugin further and gaining practical insights into its usage, be sure to visit my blog post on [Getting Started with Gremlin in OrientDB](https://biditsadhukhan.hashnode.dev/getting-started-with-gremlin-in-orientdb-unleash-the-power-of-graph-databases). By following the instructions and examples in my blog post on [Getting Started with Gremlin in OrientDB](https://biditsadhukhan.hashnode.dev/getting-started-with-gremlin-in-orientdb-unleash-the-power-of-graph-databases), you can configure and utilize the plugin to execute advanced Gremlin queries in OrientDB. Take the next step in your Gremlin and OrientDB journey by exploring the OrientDB Gremlin plugin and harnessing its capabilities. Visit [Getting Started with Gremlin in OrientDB](https://biditsadhukhan.hashnode.dev/getting-started-with-gremlin-in-orientdb-unleash-the-power-of-graph-databases) to dive deeper into the configuration, usage, and execution of Gremlin queries in OrientDB.

Embrace the power of Gremlin and unleash the full potential of your OrientDB database!

If you need further guidance or want to explore more advanced Gremlin concepts, refer to the official [Gremlin Documentation](https://tinkerpop.apache.org/docs/3.6.4/tutorials/getting-started/) and [Practical Gremlin](https://www.kelvinlawrence.net/book/PracticalGremlin.html) for detailed information and examples.

## Conclusion

In this blog post, we have explored the installation and configuration of OrientDB in Ubuntu 22.04. We walked through the steps of installing OrientDB from the source, configuring the server for console usage, and enabling Gremlin support.

Following the installation steps, you now have OrientDB up and running on your Ubuntu system. Additionally, with the Gremlin configuration, you can leverage the power of the Gremlin graph traversal language for querying and manipulating your graph database.

To further enhance your understanding of OrientDB, it is recommended to explore and execute basic to advanced queries in the OrientDB console. You can also take inspiration from the official OrientDB documentation and apply the learnings to your database.

In my blog, [OrientDB Console: Basic to Advanced Queries](https://biditsadhukhan.hashnode.dev/mastering-orientdb-console-executing-basic-to-advanced-queries-in-the-demodb-database), I share my journey of executing basic to advanced queries in OrientDB using the console. You'll find practical examples and insights that can help you master the querying capabilities of OrientDB. By following the examples and exploring the insights shared in the blog, you can strengthen your skills and become proficient in leveraging OrientDB's query language.

Embrace the opportunity to delve into the OrientDB console, execute various queries, and experiment with different scenarios. This hands-on experience will not only expand your knowledge but also enable you to apply OrientDB effectively in your projects.

Additionally, it is highly recommended to familiarize yourself with the [Basic commands](https://orientdb.org/docs/3.0.x/gettingstarted/demodb/DemoDB-Introduction.html) for interacting with the OrientDB Demodb database. This link provides a set of basic commands that you can use to perform operations on the demo database and gain practical experience.

Remember, the OrientDB documentation, my blog, and the Demodb database are valuable resources that complement each other. By leveraging all these resources, you can comprehensively understand OrientDB's querying capabilities and unlock its full potential.

Take the opportunity to experiment with the demo database, execute queries, and explore the rich features of OrientDB. This hands-on experience will strengthen your knowledge and enable you to leverage OrientDB effectively for your projects.

If you have any questions or need further assistance, don't hesitate to ask. Happy graphing with OrientDB!