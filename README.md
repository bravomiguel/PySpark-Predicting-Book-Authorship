# PySpark-Predicting-Book-Authorship

**Aim**: Hands-on lab showing how to use PySpark to predict the authorship of a set of books (either Jane Austen or Shakespeare), by clustering based on book content. 

Note, this notebook has been specifically written to be run on [Google Colab](https://colab.research.google.com/notebooks/welcome.ipynb). You may get errors if using other iPython IDE's (e.g. Jupyter Notebook).

**What you'll learn**: Learn basics of carrying out data pre-processing and ML (in this case k-means clustering) using PySpark. 

**So what**: PySpark is one of the most widely used frameworks for processing and analysing big data, i.e. data with these characteristics;

![alt text](https://www.infodiagram.com/diagram_images/bigdata_toolbox/z/8/four-V-data-chart.png)

When it comes to these kinds of data (which is most data nowadays), traditional tools (e.g. pandas, SQL, etc.) start to fall over, and PySpark really comes into its own.

**PySpark key concepts**:
* *What is it*: PySpark is the Python API for [Apache Spark](https://spark.apache.org), an open-source analytics engine for large-scale data processing.  
* *RDD*: Resilient Distributed Dataset. Basic data object in Spark where data is stored in chunks, allowing for parallel processing over a compute cluster (essential for big data). Can handle structured/unstructured data (also essential).
* *MapReduce*: Key technique for transforming data. First you map data points to values to create (key, value) pairs. Then you reduce data points based on keys. Textbook example is doing word count over large-scale text corpus, e.g.
![alt text](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/11/MapReduce-Way-MapReduce-Tutorial-Edureka.png)
* *DAG*: Directed Acyclic Graph. Link of RDD's mapping out list of tasks performed on RDD's. Allows for lazy evaluation where spark executes tasks only when it has to (by remembering all tasks leading up to this).
* *How it works under the hood*:
![alt text](https://d2h0cx97tjks2p.cloudfront.net/blogs/wp-content/uploads/sites/2/2017/08/Internals-of-job-execution-in-spark.jpg)


**Key Analysis Steps**:
1.   **Setting up PySpark** on Google Colab
2.   **Vectorising books**, by extracting 'stop word' frequency vectors for each book 
3.   **Performing k-means clustering** on vector representations to separate books into two groups (hopefully reflective of authorship)
4.   **Vectorising books again**, this time extracting 'all word' frequency vectors, then performing feature hashing to reduce to fixed width vectors.
5.   **Performing k-means clustering again**, to see if new vector representations allow for more accurate grouping of books by author
