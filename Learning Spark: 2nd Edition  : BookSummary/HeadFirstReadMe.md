## Learning Spark: 2nd Edition
#### Introduction to Apache Spark : (Why and What is)
- **_Why we require spark ?_**
  - Initially when hadoop and MR(Map reduce) framework is used, but it has below problems
    - It was hard to manage and administer
    - Batch-processing MapReduce API was verbose and required a lot of boilerplate setup code, with brittle fault tolerance
    - With large batches of data jobs with many pairs of MR tasks 
      - Each pair’s intermediate computed result is written to the local disk for the subsequent stage of its operation 
        ![](MR_Jobs_Processoring_problem.png) 
      - This repeated performance of disk I/O took its toll: large MR jobs could run for hours on end, or even days.
- **_What is apache spark ?_**
  - Spark provides in-memory storage for intermediate computations, making it much faster than Hadoop MapReduce.
  - Speed : 
    - worked on cheap commodity servers
    - work as DAG which every task can work parallel on different executors
    - Tungsten Engine : make core more compact and execute
  - Ease of Use : 
    - With RDD it provides an abstract layer
    - With Operation like Transformation , Action help in ease of use
- **_Apache spark Architecture?_**
  - Consists of a Driver program that is responsible for orchestrating parallel operations on the Spark cluster
 ![](Spark_Architecture.png)
  - Spark Driver : 
    - It is responsible for instantiating the spark session.
    - it communicates with the cluster manager; 
    - it requests resources (CPU, memory, etc.) from the cluster manager for Spark’s executors (JVMs); 
    - and it transforms all the Spark operations into DAG computations, schedules them, and distributes their execution as tasks across the Spark executors. 
    - Once the resources are allocated, it communicates directly with the executors.
  - Spark Session :
    - It became a unified conduit to all Spark operations
      - Through this define DataFrames and Datasets, read from data sources, access catalog metadata, and issue Spark SQL queries
      - ```scala
           // Build SparkSession
           val spark = SparkSession.builder.appName("LearnSpark").config("spark.sql.shuffle.partitions", 6).getOrCreate()
          // Use the session to read JSON
          val people = spark.read.json("...")
          // Use the session to issue a SQL query
          val resultsDF = spark.sql("SELECT city, pop, state, zip FROM table_name") 
        ```
      - In most deployments modes, only a single executor runs per node.
    - **_Distributed data and partitions_**
      - That is, each executor’s core is assigned its own data partition to work on
        - Spark executor can have multiple core and each core can map to different partition.
        - Each core can process one partition at a time, if you have multiple partition but limited cores per executors , it will take time.
      - Also what happen when partition size is more than executor memory
        - Refer memory structure : https://medium.com/swlh/spark-oom-error-closeup-462c7a01709d
        - If we tried to load big partition , it will be Out of Memory error for Executor
        - Hence, try to assist correct number of partitions while doing the application loading data.
        - ```python 
             # In Python
             log_df = spark.read.text("path_to_large_text_file").repartition(8)
             print(log_df.rdd.getNumPartitions()) 
          ```