# SparkStream-for-meetup
Spark Streaming of RSVPs from meetup.com API using Kafka
[meetup.com](https://www.meetup.com/) provides a streaming data of RSVPs in JSON Format. The stream is accesible through, 
[http://stream.meetup.com/2/rsvps](http://stream.meetup.com/2/rsvps)

Getting this streaming data into Apache Spark-Streaming is the first step to perform various analytics, recommendations or visualizations on the data.

## Technologies Used

     Kafka 2.13
     Spark 2.4.5


## FEATURES
    1: Real-Time Data is evaluated.
    2: we get to know about kafka producer and consumer apart from SparkStreaming
    3: This Gives the features about the messaging backend Algorithm that how it works.
## PROBLEM STATEMENT

    1: What are the current active cities in India which are scheduling Meetup Events?
    2: What are the trending topics in US Meetup Events?
    
## Execution of the Application

Assuming Kafka and Spark of appropriate version is installed, the following commands are used to run the application.

> Spark Streaming integeration with kafka 2.08 and above, is still in experimental status, Hence using Kafka 2.13 (http://spark.apache.org/docs/latest/streaming-kafka-integration.html)

1. Run Zookeeper to maintain Kafka, command to be run from Kafka root dir
```
bin/zookeeper-server-start.bat config/zookeeper.properties
```

2. Start Kafka server, aditional servers can be added as per requirement.
```
bin/kafka-server-start.bat config/server.properties
```

3. Start Producer.py to start reading data from the meetup stream and store it in '''meetup''' kafka topic.

4. Start Consumer.py to consume the stream from the '''meetup''' topic

5. Submit the spark job spark_meetup.py, to read the data into Spark Streaming from Kafka.
> Spark depends on a external package for kafka integeration [link](https://mvnrepository.com/artifact/org.apache.spark/spark-streaming-kafka-0-8_2.11/2.0.1)
```
bin/spark-submit --packages org.apache.spark:spark-streaming-kafka-0-8_2.11:2.0.1 spark_meetup.py localhost:2181 meetup
```

An analysis of number of RSVPs from various cities in "US" region is performed on the RSVPs Stream.



## REFERENCE
    http://stream.meetup.com/2/rsvps
