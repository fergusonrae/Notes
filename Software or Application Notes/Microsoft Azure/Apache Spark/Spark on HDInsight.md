# Spark on HDInsight

Existing data stored in Azure can be easily processed via a Spark cluster.

Spark is the framework, or type, of the cluster. It has some different aspects compared to other kinds of clusters. These include being able to do in-memory calculations and parallel computing.

Data to be processed by the cluster is stored in either Azure Stoage or Azure Data Lake Store.

**CITE/FURTHER INFO:** https://docs.microsoft.com/en-us/azure/hdinsight/spark/apache-spark-overview

## Why Use Spark Service?

* In-memory computing means that it can perform calculations on that data much faster
* Parallel computing means that you can cut the amount of time spent calculating since different calculations are being performed by different systems.

## Why Use Spark Clusters?

| Feature                           | Description                              |
| --------------------------------- | ---------------------------------------- |
| Ease of creating Spark clusters   | You can create a new Spark cluster on HDInsight in minutes using the Azure portal, Azure PowerShell, or the HDInsight .NET SDK. See [Get started with Spark cluster in HDInsight](https://docs.microsoft.com/en-us/azure/hdinsight/spark/apache-spark-jupyter-spark-sql) |
| REST APIs                         | Spark clusters in HDInsight include [Livy](https://github.com/cloudera/hue/tree/master/apps/spark/java#welcome-to-livy-the-rest-spark-server), a REST API-based Spark job server to remotely submit and monitor jobs. |
| Integration with Azure services   | Spark cluster on HDInsight comes with a connector to Azure Event Hubs. Customers can build streaming applications using the Event Hubs, in addition to [Kafka](http://kafka.apache.org/), which is already available as part of Spark. |
| Integration with third-party IDEs | HDInsight provides plugins for IDEs like IntelliJ IDEA and Eclipse that you can use to create and submit applications to an HDInsight Spark cluster. For more information, see [Use Azure Toolkit for IntelliJ IDEA](https://docs.microsoft.com/en-us/azure/hdinsight/spark/apache-spark-intellij-tool-plugin) and [Use Azure Toolkit for Eclipse](https://docs.microsoft.com/en-us/azure/hdinsight/spark/apache-spark-eclipse-tool-plugin). |
| Concurrent Queries                | Spark clusters in HDInsight support concurrent queries. This enables multiple queries from one user or multiple queries from various users and applications to share the same cluster resources. |
| Caching on SSDs                   | You can choose to cache data either in memory or in SSDs attached to the cluster nodes. Caching in memory provides the best query performance but could be expensive; caching in SSDs provides a great option for improving query performance without the need to create a cluster of a size that is required to fit the entire dataset in memory. |
| Integration with BI Tools         | Spark clusters on HDInsight provide connectors for BI tools such as [Power BI](http://www.powerbi.com/) and [Tableau](http://www.tableau.com/products/desktop) for data analytics. |
| Pre-loaded Anaconda libraries     | Spark clusters on HDInsight come with Anaconda libraries pre-installed. [Anaconda](http://docs.continuum.io/anaconda/) provides close to 200 libraries for machine learning, data analysis, visualization, etc. |
| Scalability                       | Although you can specify the number of nodes in your cluster during creation, you may want to grow or shrink the cluster to match workload. All HDInsight clusters allow you to change the number of nodes in the cluster. Also, Spark clusters can be dropped with no loss of data since all the data is stored in Azure Storage or Data Lake Store. |
| 24/7 Support                      | Spark clusters on HDInsight come with enterprise-level 24/7 support and an SLA of 99.9% up-time. |

 

## Schema Showing Spark architecture

![](https://docs.microsoft.com/en-us/azure/hdinsight/spark/media/apache-spark-overview/spark-architecture.png)

The **Head node** has a **cluster manager** that manages the number of applications and what apps are mapped where. Really keeps track of everything going on including how much memory and resources are left. Uses the information to tell the **driver** how to dole out "work" to worker nodes that are light. Once the work is done, the driver collects the results. The driver is a resource the manager uses.

**Worker nodes** take this work and compute it by getting what data pieces they need from a data storage, doing their calculation, and store the **transformed** data in-memory as a **Resilient Distributed Dataset (RDD)**. This RDD is the reason Spark is so fast.

The **HDFS** is the data storage. It stands for Hadoop Distributed File System. This is because Spark is built heavily on Hadoop and stole many of its aspects.



## What Can You Use a Spark Cluster For?

### Data Analysis

HDInsights supports both Power BI and Tableau for creating interactive reports. You can start with unstructured data in a cluster storage, define a schema for the data, and then build data models.

### Machine Learning

**MLib** is the machine learning library Spark comes with, along with various packages from Anaconda.

### Spark streaming (real-time data analysis)

Spark comes with connectors to sources like: Kafka, Flume, Twitter, ZeroMQ, or TCP. You can also choose what data you would like it to connect to using Event Hubs to make an ideal platform for real time analytics pipeline.



## What Comes With a Spark Cluster?

* Spark Core
  * Includes Spark SQL, streaming APIs, GraphX, and MLib
* Anaconda
* Livy
  * A REST interface that can be used to access your cluster even when you're not in it.
* Jupyter notebook
* Zeppelin notebook
* ODBC driver
  * For connecting to BI tools like Power BI and Tableau