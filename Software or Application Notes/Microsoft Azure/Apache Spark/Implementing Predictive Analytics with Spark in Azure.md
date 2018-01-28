# Implementing Predictive Analytics with Spark in Azure

## Welcome

What we're going to learn is how to set up Spark clusters and use them

Will need

* Computer
* MS Azure subscription
* Install Azure Storage Explorer
  * Download
  * Click into folder
  * Double click Microsoft Azure Storage Explorer.pkg to actually download?
  * Drag application to apps folder
  * Open, select add new azure account
  * Sign in, hould have Big Data already there



## Introduction to Spark

### What is it?

Spark is a high-performance general-purpose computation machine. It distributes its workload to different nodes in a cluster. So, like parallel computing.

You typically use a **Resilient Distributed Date Set (RDD)** to work with it. It's the basic unit of data, the core programming model. You can work with RDDs with many languages.

Data frames are like high level RDD's and are going to be used in this course which is AWESOME.

The instructions and code will be read with Jupyter Notebooks which is also great.



### Provisioning a Spark Cluster

1. Search for HD Insights, select, it will create an instance
   1. Basics
      1. Give it a name, must be publically accessible and unique
      2. Cluster type
         1. Will be Spark, choose latest version
      3. Specify username and password
         1. Default is admin
            1. My pass is Alight Redshift pass
         2. Will be used when you connect using http
      4. Define SSH username
         1. Used when you enter on the shell (command prompt or terminal)
         2. Probably the same
      5. Create a resource group
   2. Choose Storage
      1. If you're doing large volumes of data or serious processing, go Data Lake. Otherwise, Azure Storage is easy to work with.
      2. You can also choose to just use an existing or create a new storage, must be unique
         1. If you create new, must also create a container. To make life easy, just give it the same name.
      3. Storing meta data
         1. Can put it into existing database or Azure will just create a private one for you.
   3. Select applications to have available on cluster
      1. Some won't be able to be selected based on versions of Spark chosen
   4. Choose cluster size
      1. Worker nodes and head nodes.
      2. If doing simple, stick with 1 worker nodes, especially when doing tutorials.
      3. Worker node size can also be changed to reduce the amount of price per hour. Have to be careful, some services might not start if nodes are too small.
   5. Specify any additional scripts to run after cluster is done.
      1. Can also specify virtual network to have other procesing connect together
   6. Wait about 20 minutes for a cluster to be created.
2. Select the dashboard and log in with the http credentials
   1. Will open Ambari dashboard
      1. Is an overview of all services that are running in the cluster.
      2. Here is where you can stop, restart, delete services, etc.

## Getting Started with DataFrames

Different methods are called on them in Spark, watch out for that.

Spark SQL can be used to run queries against persistent data frames. Useful if you're more used to SQL. Can also use the %%SQL magic command in Jupyter notebook to call from the data frame.

```sql
SELECT * FROM dataframe
```

