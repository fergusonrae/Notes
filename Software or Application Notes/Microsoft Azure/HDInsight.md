# Overview

**DOCUMENTATION:** https://docs.microsoft.com/en-us/azure/hdinsight/

Azure HDInsight is a fully-managed, full-spectrum, open-source analytics service for enterprises. It's a cloud service to process massive amount of data cheaply. It also supports extract, transform, and load; data warehousing; machine learning; and IoT.

It is a cloud distribution of some of the Hadoop components.

With the service you can use open-source frameworks like Hadoop, Spark, Hive, LLAP, R, Spark, and more.

So, HD Insight is the service, and Spark is the framework of the service for the edX course. You can also have an HDInsight service running on an R framework though, or Hadoop.

**Apache Hadoop** - Original open-source framework for big datasets on clusters.

**Apache Spark** - Open-source parallel processing framework that supports in-memory processing to boost performance

## Possible things to use HDInsight for

**Batch processing (ETL) (Extract, transform, and load)** - A process where unstructured or structured data is extracted from heterogeneous data sources, transformed to be structured, and loaded into a data store. This new data can be used for data science or data warehousing.

**Internet of Things (IOT)** - You can process streaming data received at real-time from a variety of devices.

**Data Science** - Can be used to build apps that extract critical insights from data. You can use Azure Machine Learning on top of this to predict future business trends.

**Data warehousing** - Can be used to perform interactive queries at petabyte scales over structured/unstructured data. You can also build models connecting them to BI tools.

**Hybrid** - Can be used to extend existing big data infrastructure to Azure.

## Cluster Types

HDInsight includes specific cluster types and cluster customization capabilities, such as adding components, utilities, and languages.

HDInsight offers the following cluster types:

- **Apache Hadoop**: Uses [HDFS](https://docs.microsoft.com/en-us/azure/hdinsight/hadoop/apache-hadoop-introduction#hdfs), [YARN](https://docs.microsoft.com/en-us/azure/hdinsight/hadoop/apache-hadoop-introduction#yarn) resource management, and a simple [MapReduce](https://docs.microsoft.com/en-us/azure/hdinsight/hadoop/apache-hadoop-introduction#mapreduce) programming model to process and analyze batch data in parallel.
- **Apache Spark**: A parallel processing framework that supports in-memory processing to boost the performance of big-data analysis applications, Spark works for SQL, streaming data, and machine learning. See [What is Apache Spark in HDInsight?](https://docs.microsoft.com/en-us/azure/hdinsight/spark/apache-spark-overview) Or additional markup notebook Under Microsoft Azure
- **Apache HBase**: A NoSQL database built on Hadoop that provides random access and strong consistency for large amounts of unstructured and semi-structured data - potentially billions of rows times millions of columns. See [What is HBase on HDInsight?](https://docs.microsoft.com/en-us/azure/hdinsight/hbase/apache-hbase-overview)
- **Microsoft R Server**: A server for hosting and managing parallel, distributed R processes. It provides data scientists, statisticians, and R programmers with on-demand access to scalable, distributed methods of analytics on HDInsight. See [Overview of R Server on HDInsight](https://docs.microsoft.com/en-us/azure/hdinsight/r-server/r-server-overview).
- **Apache Storm**: A distributed, real-time computation system for processing large streams of data fast. Storm is offered as a managed cluster in HDInsight. See [Analyze real-time sensor data using Storm and Hadoop](https://docs.microsoft.com/en-us/azure/hdinsight/storm/apache-storm-sensor-data-analysis).
- **Apache Interactive Query preview (AKA: Live Long and Process)**: In-memory caching for interactive and faster Hive queries. See [Use Interactive Query in HDInsight](https://docs.microsoft.com/en-us/azure/hdinsight/interactive-query/apache-interactive-query-get-started).
- **Apache Kafka**: An open-source platform used for building streaming data pipelines and applications. Kafka also provides message-queue functionality that allows you to publish and subscribe to data streams. See [Introduction to Apache Kafka on HDInsight](https://docs.microsoft.com/en-us/azure/hdinsight/kafka/apache-kafka-introduction).