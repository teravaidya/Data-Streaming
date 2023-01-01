# Intro to Stream processing

# **Understanding Stream Processing**

In computing, a *stream* is typically thought of as a potentially unbounded sequence.

*Stream Processing* is the act of performing continual calculations on a potentially endless and constantly evolving source of data.

Stream Processing applications perform calculations on *Data Streams*. Data Streams consist of a potentially endless stream of *immutable* data.

Immutable data does not change -- once the data has been placed in the data stream it can never be updated. Another data entry can be placed in the stream that supersedes the previous data entry if necessary.

Data sent to data streams is typically *small, less than 1MB in size*.

The data throughput to data streams is highly variable. Some streams will receive thousands or tens of thousands of records per second, and some will receive one or two records per hour.

## **Stream Processing**

- Stream Processing acts on potentially endless and constantly evolving immutable data contained in data streams.
- Once data have been placed in a data stream, they cannot be modified. We must place a new record in the stream to override the existing data.
- Finally, data in data streams is typically less than 1MB in size and the data volume may vary from a few records an hour to thousands of requests per second.
- **Event** – an immutable fact regarding something that occurred within a system. It can not be changed, once created. Data records in the context of data streaming are events.
- In many SQL databases, it is uncommon to track the history of what values were used for a particular user in the past.
- **Message Queues** – typically communicate commands to perform an action
- **Invented Systems** – react to the facts that are indirectly communicated to them, for example, via user clicks
- **Event** – an immutable fact regarding something that occurred within a system. It can not be changed, once created. Data records in the context of data streaming are events.
- In many SQL databases, it is uncommon to track the history of what values were used for a particular user in the past.
- **Message Queues** – typically communicate commands to perform an action
- **Invented Systems** – react to the facts that are indirectly communicated to them, for example, via user clicks

# **Stream Processing Examples**

## **Log Analysis**

One of the first places many companies use stream processing is in log analysis. Companies often run microservices that constantly produce logs that are full of information that can be mined for:

- User behavior patterns
- Failure prediction
- Debugging

These logs generate a tremendous amount of data on an ongoing basis, which can be difficult to then analyze. To solve this issue, each log produced by a microservice becomes an event in a data stream.

Companies then build programs that can analyze and join on the events in these data streams to find insights into the data.

![https://video.udacity-data.com/topher/2019/September/5d6ed1b1_screen-shot-2019-09-03-at-1.48.39-pm/screen-shot-2019-09-03-at-1.48.39-pm.png](https://video.udacity-data.com/topher/2019/September/5d6ed1b1_screen-shot-2019-09-03-at-1.48.39-pm/screen-shot-2019-09-03-at-1.48.39-pm.png)

**Log Analysis condenses logs from many servers into a single ordered stream**

## **Web Analytics**

Modern web applications measure almost every action a user takes on their site, for example:

- button clicks
- Page load times
- Session duration

The volume of these actions can quickly overwhelm a traditional **data store** (any place you keep data). Ingesting and analyzing this data can be difficult and companies use stream processing to analyze the data as it is generated.

The benefits of this process are:

- it lessens the long-term processing burden for companies because of the smaller dataset
- provides real-time analysis instead of long-running bath analyses that may only be updated periodically

![https://video.udacity-data.com/topher/2019/September/5d6f1243_screen-shot-2019-09-03-at-6.23.37-pm/screen-shot-2019-09-03-at-6.23.37-pm.png](https://video.udacity-data.com/topher/2019/September/5d6f1243_screen-shot-2019-09-03-at-6.23.37-pm/screen-shot-2019-09-03-at-6.23.37-pm.png)

**Analyzing streaming user events for web analytics**

## **Real-Time Pricing**

Ride-sharing applications are a great example of data streaming for real-time analysis. They use real-time pricing that adjusts with environmental factors and instantaneous demand.

![https://video.udacity-data.com/topher/2019/September/5d6f12a1_screen-shot-2019-09-03-at-6.25.45-pm/screen-shot-2019-09-03-at-6.25.45-pm.png](https://video.udacity-data.com/topher/2019/September/5d6f12a1_screen-shot-2019-09-03-at-6.25.45-pm/screen-shot-2019-09-03-at-6.25.45-pm.png)

**Determining ride-share pricing on streaming real-time event data**

## **Stream Processing Examples Recap**

Stream Processing is a critical component in a number of familiar technology applications:

- Finding patterns and meaningful data in disparate log messages in a microservices architecture
- Tracking user engagement in real-time with streaming website analytics
- Real-time pricing in ride-sharing applications based on demand and environmental conditions
- Stock buying/selling based on price, news, and social media sentiment

****Stream vs. Batch Processing****

## **Batch Processing**

- Runs on a scheduled basis
- May run for a longer period of time and write results to a SQL-like store
- May analyze all historical data at once
- Typically works with mutable data and data stores

## **Stream Processing**

- Runs at whatever frequency events are generated
- Typically runs quickly, updating in-memory aggregates
- Stream Processing applications may simply emit events themselves, rather than write to an event store
- Typically analyzes trends over a limited period of time due to data volume
- Typically analyzes immutable data and data stores

*Batch and Stream processing are not mutually exclusive*. Batch systems can create events to feed into stream processing applications, and similarly, stream processing applications can be part of batch processing analyses.

## **Streaming Data Store**

- May look like a message queue, as is the case with Apache Kafka
- May look like a SQL store, as is the case with Apache Cassandra
- Responsible for holding all of the immutable event data in the system
- Provides guarantee that data is stored ordered according to the time it was produced
- Provides guarantee that data is produced to consumers in the order it was received
- Provides guarantee that the events it stores are immutable and unchangeable

## **Stream Processing Application and Framework**

- Stream Processing applications sit downstream of the data store
- Stream Processing applications ingest real-time event data from one or more data streams
- Stream Processing applications aggregate, join, and find differences in data from these streams
- Common Stream Processing Application Frameworks in use today include:
    - Confluent KSQL
    - Kafka Streams
    - Apache Flink
    - Apache Samza
    - Apache Spark Structure Streaming
    - **Faust Python Library**

### **Further Optional Reading on Message Queues**

- [RabbitMQ](https://www.rabbitmq.com/)
- [ActiveMQ](https://activemq.apache.org/)

## **Benefits of Stream Processing**

- Faster for scenarios where a limited set of recent data is needed
- More scalable due to distributed nature of storage
- Provides a useful abstraction that decouples applications from each other
- Allows one set of data to satisfy many use-cases which may not have been predictable when the dataset was originally created
- Built-in ability to replay events and observe exactly what occurred, and in what order, provides more opportunities to recover from error states or dig into how a particular result was arrived at

## **Key concepts to remember about stream processing**

- Stream processing applications consist of a stream data store and a stream processing application framework
- Stream processing solutions do not operate on a scheduled basis
- Stream processing solutions provide real-time insights based on event data
- Stream processing solutions are built around generic data events, allowing for flexibility in data processing and highly scalable applications
- Batch and stream processing solutions can coexist and feed into each other

## **Append-only logs**

- Append-only logs are text files in which incoming events are written to the end of the log as they are received.
- This simple concept -- of only ever appending, or adding, data to the end of a log file -- is what allows stream processing applications to ensure that events are ordered correctly even at high throughput and scale.
- We can take this idea a step farther, and say that in fact, streams *are* append-only logs.

****Append-Only Logs in SQL Databases****

Append-only logs were not originally created for stream processing. Years ago SQL database developers needed a way to track changes and then synch those changes between primary and secondary nodes.

**Change Data Capture (CDC)** – the process of how SQL databases use append-only logs to track, communicate and synchronize changes in the primary database to replica/secondary nodes.

![Untitled](Intro%20to%20Stream%20processing%2063d3a3f7318745b79def4e84ea75dacf/Untitled.png)

Change Data Capture (CDC) process in a database system using append-only logs

## **Log-Structured Storage**

One of the key innovations over the past decade in computing has been the emergence of log-structured storage as a primary means of storing data.

## **Log-structured streaming**

- Log-structured streams build upon the concept of append-only logs. One of the hallmarks of log-structured storage systems is that at their core they utilize append-only logs.
- Common characteristics of all log-structured storage systems are that they simply append data to log files on disk.
- These log files may store data indefinitely, for a specific time period, or until a specific size is reached.
- There are typically many log files on disk, and these log files are *merged* and *compacted* occasionally.
- When a log file is *merged* it means that two or more log files are joined together into one log file.
- When a log file is *compacted* it means that data from one or more files is deleted. Deletion is typically determined by the age of a record. The oldest records are removed, while the newest stay.
- Examples of real world log-structured data stores: Apache HBase, Apache Cassandra, Apache Kafka

While Apache Cassandra and HBase are not the focus of this course, both:

- are data stores that surface SQ-like interfaces
- are appropriate for working with massive datasets
- use append-only logs to store and coordinate data across nodes
- tend to be used in batch processing systems

On the other hand, Apache Kafka is a message queue system based on the concept of log-structured, append-only storage. It may appear similar to the others but is based on a different storage and scaling mechanism.

## **Apache Kafka as a Stream Processing Tool**

- Kafka is one of the most popular streaming data platforms in the industry today.
- Provides an easy-to-use message queue interface on top of its append-only log-structured storage medium
- Kafka is a log of *events*
- In Kafka, an event describes something that has occurred, as opposed to a request for an action to be performed
- Kafka is distributed by default
- Fault tolerant by design, meaning it is hard to lose data if a node is suddenly lost
- Kafka scales from 1 to thousands of nodes
- Kafka provides ordering guarantees for data stored within it, meaning that the order in which data is received is the order in which data will be produced to consumers
- Commonly used data store for popular streaming tools like Apache Spark, Flink, and Samza

## **Kafka History**

- Created at Linkedin to service internal stream processing needs
- Kafka is one of the Apache Foundation’s most popular projects
- Used widely in production. Some famous users include Uber, Apple, and Airbnb
- Creators of Kafka left LinkedIn to found Confluent, which now acts as the owner and leader of the Kafka project
- Jay Kreps, one of the core authors of Apache Kafka, named the system after Czech author Franz Kafka. Kreps, who enjoys Kafka’s work, thought the name was a good fit because Kafka was built to be a “system optimized for writing.”

## **Kafka in Use in Industry**

- The term *source* is sometimes used to refer to Kafka clients which are producing data into Kafka, typically in reference to another data store
- The term *sink* is sometimes used to refer to Kafka clients which are extracting data from Kafka, typically in reference to another data store

### **Further Optional Reading**

How Uber uses Kafka:

- [The Uber Engineering Tech Stack Part 1](https://eng.uber.com/tech-stack-part-one/)
- [The Uber Engineering Tech Stack Part 2](https://eng.uber.com/tech-stack-part-two/)

## **Kafka Topics**

- Used to organize and segment datasets, similar to SQL database tables
- Unlike SQL database tables, Kafka Topics are not queryable.
- May be created programmatically, from a CLI (Command Line Interface), or automatically
- Consist of key-value data in binary format

## **Kafka Producers**

- Send event data into Kafka topics
- Integrate with client libraries in languages like Java, Python, Go, as well as many other languages

## **Kafka Consumers**

- Pull event data from one or more Kafka Topics
- Integrate with Kafka via a Client Library written in languages like Python, Java, Go, and more
- By default only consume data that was produced after the consumer first connected to the topic. Historical data will not be consumed by default.