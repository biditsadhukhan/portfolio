---
author: Bidit Sadhukhan
date: "2021-07-04T19:53:33+05:30"
description: "Learn how to install and use SANSA Stack for efficient RDF data processing. Unlock the power of RDF analytics and explore large-scale knowledge graphs."
draft: false
image: "https://pbs.twimg.com/profile_images/806589327434256384/CONouA4k_400x400.jpg"
tags:
- Sansa Stack
- RDF
- sansa-notebook
- sansa-examples
title: "Step-by-Step Guide: Installing and Setting up the SANSA Stack for Scalable RDF Data Processing"
toc: true
---

## **Introducing the SANSA Stack and SANSA Notebook:**

The SANSA (Scalable Semantic Analytics Stack) project, combined with the SANSA Notebook, offers a comprehensive and interactive solution for processing and analyzing RDF (Resource Description Framework) data at scale. In this blog post, we will dive into the SANSA stack and explore how the SANSA Notebook complements it, enabling seamless execution of RDF operations and providing a rich environment for interactive data exploration.

### **SANSA Notebook**

The SANSA Notebook enhances the SANSA stack by providing an interactive environment for exploring and analyzing RDF data. Built on top of popular notebook technologies, such as Zeppelin, the SANSA Notebook allows users to execute RDF operations, visualize data, and iterate on data exploration tasks. Its integration with the SANSA stack enables the seamless execution of SANSA operations and facilitates the interactive exploration of RDF datasets. In this blog post, we will showcase the features and capabilities of the SANSA Notebook, demonstrating how it empowers users to interactively analyze and gain insights from RDF data.

Join us in this blog as we dive into the SANSA stack and SANSA Notebook, uncovering their capabilities, exploring their integration, and demonstrating how they empower scalable RDF data processing and interactive data exploration.

### **Layers of the SANSA Stack: Building Blocks for RDF Data Processing**

The SANSA project is built upon a layered architecture, providing a modular approach to RDF (Resource Description Framework) data processing. The SANSA stack consists of the following layers:

1. RDF Layer
    
2. OWL Layer
    
3. Query Layer
    
4. Inference Layer
    
5. ML Layer
    

Each layer addresses specific aspects of RDF data handling, from modelling and manipulation to ontology handling, query execution, semantic inference, and machine learning. The layered structure of the SANSA stack ensures a comprehensive toolkit for efficient and scalable RDF data processing.

### Requirements for SANSA Stack Installation

To successfully install the SANSA Stack, you will need the following requirements:

1. Spark 3.x.x with Scala 2.12: The SANSA Stack requires a Spark distribution with Scala version 2.12. Ensure that you have Spark 3.x.x installed and configured properly. If you prefer to use Spark 2.x, you can build it from a source based on the [spark2](https://github.com/SANSA-Stack/SANSA-Stack/tree/spark2) branch.
    
2. Java Development Kit (JDK): SANSA Stack relies on Java, so make sure you have a compatible JDK installed on your system. We recommend using OpenJDK version 8 or higher.
    
3. Maven: SANSA Stack uses Maven as a build and dependency management tool. Ensure that you have Maven installed and properly configured.
    
4. Hadoop: Although not mandatory for basic SANSA Stack functionality, having Hadoop installed can be beneficial for advanced features and integration with Hadoop Distributed File System (HDFS). Make sure Hadoop is installed and properly configured if you plan to use Hadoop-specific functionalities.
    

By meeting these requirements, you will be ready to proceed with the installation and utilization of the SANSA Stack.

To check if the prerequisites are installed and their versions, you can use the following code in a Bash script:

```bash
#!/bin/bash

# Check Spark version
spark_version=$(spark-submit --version 2>&1 | grep -o 'version [0-9]\.[0-9]\.[0-9]')
if [[ -z $spark_version ]]; then
  echo "Spark is not installed."
  # Install Spark here (if desired)
else
  echo "Spark is installed. Version: $spark_version"
fi

# Check Java version
java_version=$(java -version 2>&1 | awk -F '"' '/version/ {print $2}')
if [[ -z $java_version ]]; then
  echo "Java is not installed."
  # Install Java here (if desired)
else
  echo "Java is installed. Version: $java_version"
fi

# Check Maven version
maven_version=$(mvn --version | grep -o 'Apache Maven [0-9]\.[0-9]\.[0-9]')
if [[ -z $maven_version ]]; then
  echo "Maven is not installed."
  # Install Maven here (if desired)
else
  echo "Maven is installed. Version: $maven_version"
fi

# Check Hadoop version
hadoop_version=$(hadoop version | grep -o 'Hadoop [0-9]\.[0-9]\.[0-9]')
if [[ -z $hadoop_version ]]; then
  echo "Hadoop is not installed."
  # Install Hadoop here (if desired)
else
  echo "Hadoop is installed. Version: $hadoop_version"
fi
```

You can save the above code in a file, for example, `prerequisites_check.sh`, and execute it in your terminal using the command `bash prerequisites_check.sh`. The script will check the versions of Spark, Java, Maven, and Hadoop (if available) and inform you whether they are installed or not.

Note: The script only checks the presence of the prerequisites and their versions. It does not install them automatically. You will need to install any missing prerequisites manually or implement the installation logic within the script if desired.

> Note: To use the SANSA Notebook, Docker must be installed on your system. If you don't have Docker installed, please follow the instructions below to install Docker before proceeding with the SANSA Notebook setup.

Follow the steps below to install Docker:

1. Install Docker:
    
    ```bash
    sudo apt-get update
    sudo apt-get install docker-ce docker-ce-cli containerd.io
    ```
    
2. Install Docker Compose:
    
    ```bash
    sudo apt-get install docker-compose
    ```
    
3. Verify Docker installation:
    
    ```bash
    sudo docker run hello-world
    ```
    
4. Start Docker service:
    
    ```bash
    sudo service docker start
    ```
    
5. Verify Docker installation again:
    
    ```bash
    sudo docker run hello-world
    ```
    
6. Add user to the `docker` group:
    
    ```bash
    sudo usermod -aG docker sysadm
    ```
    
7. Update apt package list:
    
    ```bash
    sudo apt-get update
    ```
    
8. Verify Docker Compose installation:
    
    ```bash
    docker-compose version
    ```
    
    Once Docker is installed and verified, you can proceed with setting up and running the SANSA Notebook.
    

## Installing SANSA Stack

To install the SANSA Stack, please follow the steps below:

* **Clone the SANSA Stack repository:** - Open your terminal and change to the desired folder where you want to clone the repository:
    

```bash
cd desired_folder 
```

* Run the following command to clone the SANSA Stack repository:
    

```bash
git clone https://github.com/SANSA-Stack/SANSA-Stack.git 
```

* **Navigate to the cloned repository:**
    

* Change your directory to the SANSA-Stack folder:
    
    ```bash
    cd SANSA-Stack 
    ```
    
* Build the SANSA Stack using Maven:
    
    ```bash
    make mcis
    ```
    

### Installation of Sansa Notebook

* After successfully building the SANSA Stack, navigate to the SANSA Notebooks directory:
    
    ```bash
    cd SANSA-Notebooks/sansa-notebooks 
    ```
    
* Build the SANSA Notebook using Maven:
    
    ```bash
    make
    ```
    
    Congratulations! You have successfully installed the SANSA Stack and Sansa Notebook. Enjoy exploring the capabilities of SANSA!
    

### Running SANSA Examples

To run the SANSA examples from the SANSA Notebook, please follow the steps below:

1. **Start the SANSA Notebook:**
    
    * Open your terminal and navigate to the SANSA Notebooks directory:
        
        ```bash
        cd SANSA-Notebooks/sansa-notebooks
        ```
        
    * Start the SANSA Notebook using Docker:
        
        ```bash
        make up
        ```
        
2. **Load the Example Data:**
    
    * After starting the SANSA Notebook, load the example data by running the following command:
        
        ```bash
        make load-data
        ```
        
3. **Run the Examples from CLI:**
    
    * In the SANSA Notebook folder, you will find a [`README.md`](http://README.md) file that contains the code snippets to run the examples from the command line interface (CLI).
        
    * Open the [`README.md`](http://README.md) file and execute the code snippets in the SANSA Notebook's CLI to run the examples.
        
    * The examples cover various aspects of RDF and OWL data processing, querying, inference, and machine learning using the SANSA Stack.
        
    * Some of the codes include:
        
        ```bash
        make cli-triples-reader
        make cli-triple-ops
        make cli-triples-writer
        make cli-pagerank
        make cli-rdf-stats
        make cli-inferencing
        make cli-sparklify
        make cli-owl-reader-manchester
        make cli-owl-reader-functional
        make cli-owl-dataset-reader-manchester
        make cli-owl-dataset-reader-functional
        make cli-clustering
        make cli-rule-mining
        ```
        

By following these steps, you can run the SANSA examples from the SANSA Notebook and explore the different functionalities provided by the SANSA Stack.

> Note: Make sure you have successfully configured and built the SANSA Notebook before running the examples. Refer to the previous instructions for configuring and building the SANSA Notebook.

### Running SANSA Examples with Zeppelin Notebook

If you prefer not to use the command line interface (CLI) and instead want to use the Zeppelin notebook for running the SANSA examples, please follow the steps below:

1. **Start the SANSA Notebook:**
    
    * Open your terminal and navigate to the SANSA Notebooks directory:
        
        ```bash
        cd SANSA-Notebooks/sansa-notebooks
        ```
        
    * Start the SANSA Notebook using Docker:
        
        ```bash
        make up
        ```
        
2. **Access the Interfaces:**
    
    * Once the start-up is complete, you can access the following interfaces: - Spark Master: You can access the Spark Master by opening your web browser and navigating to:
        
        ```bash
         http://localhost:8080/ 
        ```
        
    * Hue HDFS Filebrowser: You can access the Hue HDFS Filebrowser by opening your web browser and navigating to:
        
        ```bash
         http://localhost:8088/home 
        ```
        
    * Zeppelin Notebook: You can access the Zeppelin notebook interface by opening your web browser and navigating to:
        
        ```bash
         http://localhost/ 
        ```
        
3. **Load the Example Data:**
    
    * In the Zeppelin notebook interface, navigate to the "Interpreter" tab.
        
    * Add a new interpreter and configure it to use the SANSA Stack.
        
    * Load the example data to your cluster using the provided code snippets in the Zeppelin notebook.
        
    * The example data can be loaded from various sources such as local files, HDFS, or remote repositories.
        
4. **Run the Examples in the Zeppelin Notebook:**
    
    * In the Zeppelin notebook, create a new notebook or open an existing one.
        
    * Write and execute the code snippets to run the SANSA examples using the Zeppelin notebook interface.
        
    * The examples cover various aspects of RDF and OWL data processing, querying, inference, and machine learning using the SANSA Stack.
        

By following these steps, you can run the SANSA examples using the Zeppelin Notebook interface and leverage its interactive features for data exploration and analysis.

To ensure that the Zeppelin notebook works perfectly, you need to go to each specific note in the notebook folder of the SANSA notebook and update the `note.json` configuration file. Locate the `note.json` file for each note and change the value of the `"isZeppelinNotebook"` property from `false` to `true`.

Here are the steps to make the necessary changes:

1. Navigate to the SANSA notebook folder using the command line:
    
    ```bash
    cd SANSA-Notebooks/sansa-notebooks/notebook
    ```
    
2. Open each note folder and locate the `note.json` file. For example, to edit the first note, you can use the following command:
    
    ```bash
    cd note1
    ```
    
3. Open the `note.json` file in a text editor.
    
4. Locate the `"isZeppelinNotebook"` property and change its value from `"false"` to `"true"`.
    
5. Save the changes and close the file.
    
6. Repeat steps 2-5 for each note in the notebook folder.
    

By modifying the `note.json` configuration file for each note and setting the `"isZeppelinNotebook"` property to `"true"`, you ensure that the Zeppelin notebook functionality is enabled for all the notes in the SANSA notebook.

After making these changes, you can access and use the Zeppelin notebook interface for running the examples and performing data analysis within the SANSA notebook.

### Retrieve the data, output, and code from the SANSA notebook

In order to retrieve the data, output and the code follow the steps mentioned below:

1. Open the Hue HDFS Filebrowser: Go to [http://localhost:8088/home](http://localhost:8088/home) in your web browser to access the Hue HDFS Filebrowser. This interface allows you to interact with the Hadoop Distributed File System (HDFS) and browse its contents.
    
2. Access the Data Folder: In the Hue HDFS Filebrowser, navigate to the root folder, and then find and enter the "data" folder. This is where all the data from the local file in the example folder is copied to the HDFS.
    
3. Retrieve the Data: Inside the "data" folder, you will find the datasets and files used in the examples of the SANSA notebook. You can download these files or use them directly for data processing and analysis within the notebook.
    
4. Access the Output Folder: Similarly, in the Hue HDFS Filebrowser, navigate to the root folder again, and locate the "output" folder. This is where the output of the examples and analyses performed in the SANSA notebook is stored.
    
5. Retrieve the Output: Inside the "output" folder, you will find the results, generated files, or any other output produced by the examples in the SANSA notebook. You can download these outputs for further examination or use them for any post-processing tasks.
    
6. Access the Code: To access the code from the SANSA notebook, you have two options:
    
    a. Zeppelin Notebook: Go to [http://localhost](http://localhost) in your web browser to access the Zeppelin notebook interface. From there, navigate to the specific notebooks or notes in the SANSA notebook. Inside each note, you will find the code used for data analysis, processing, and running the examples.
    
    b. Local File System: Alternatively, you can access the code directly on your local file system in the SANSA notebook folder (the one you cloned from the GitHub repository). Inside the "notebook" subfolder, you will find various notes or notebooks, each containing the code for different examples.
    

By following these steps, you can easily retrieve the data, output, and code used in the SANSA notebook, and explore the results of the examples and analyses performed during your data processing tasks.

### Stopping the Examples and Shutting Down the SANSA Notebook

To stop running the examples and shut down the SANSA notebook, you can use the `make down` command. This command will gracefully stop all the running services and release any allocated resources.

Simply open your terminal, navigate to the SANSA notebook folder, and execute the following command:

```bash
make down
```

This will initiate the shutdown process and ensure that all the components of the SANSA notebook are stopped and cleaned up properly.

Remember to use the `make down` command whenever you are done running the examples or when you no longer need the SANSA notebook running to free up system resources.

## Conclusion

In conclusion, the SANSA Stack provides a powerful platform for processing and analyzing RDF data with a focus on scalability and performance. With its modular architecture and rich set of tools, SANSA enables efficient RDF processing, ontology reasoning, querying, and machine learning on large-scale knowledge graphs.

By following the installation instructions and running the examples in the SANSA notebook, you can experience the capabilities of this stack firsthand. The integration with Apache Spark, along with the provided libraries and utilities, empowers you to tackle complex RDF analytics tasks with ease.

For further exploration and detailed documentation, I encourage you to visit the official SANSA Stack website at [https://sansa-stack.github.io/SANSA-Stack/](https://sansa-stack.github.io/SANSA-Stack/). There, you'll find comprehensive resources, tutorials, and additional information to delve deeper into the world of RDF processing and analysis using SANSA.

Get ready to unlock the full potential of your RDF data with the SANSA Stack! Happy exploring!