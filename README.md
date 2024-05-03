# Stock Market Data Engine Using Apache Kafka
In this project, an end-to-end data engineering pipeline using Apache Kafka is built.

## Description
This pipeline extracts data from a .csv file containing 100,000+ rows and stores it in an Amazon S3 bucket as .json files using Apache Kafka event streaming. After that data is loaded into the AWS Glue Data Catalog using AWS Glue Crawler. Ultimately, data is queried using Amazon Athena and SQL. The following technologies are used to build this data pipeline:
- Programming Language-Python
- Amazon CLI
- Apache Kafka
- Amazon EC2
- Amazon S3
- AWS Glue Crawler
- AWS Glue Data Catalog
- Amazon Athena

## Architecture Diagram
![alt text](https://github.com/rjtkhanna/Kafka_stockMarket_dataEngine/blob/main/20240427_kafka_stock_market_project_diagram.jpg?raw=true)

## Getting Started
### Installing, Configuring And Starting Apache Kafka on EC2
Use the following command to download Apache Kafka: \
`wget https://downloads.apache.org/kafka/3.5.2/kafka_2.12-3.5.2.tgz`

Unzip .tgz file and rename it: \
`tar -xvf kafka_2.12-3.5.2.tgz` \
`mv kafka_2.12-3.5.2 kafka`

Install Java: \
`sudo yum install java-1.8.0-openjdk`

Change ADVERTISED_LISTENERS to public ip of the EC2 instance by executing the following command: \
`cd kafka` \
`sudo nano config/server.properties`

Start Zookeeper: \
`bin/zookeeper-server-start.sh config/zookeeper.properties`

Start Kafka after duplicating the session: \
Use the following command to allot memory to kafka server \
`export KAFKA_HEAP_OPTS="-Xmx256M -Xms128M"` \
`cd kafka` \
`bin/kafka-server-start.sh config/server.properties`

Create the topic: \
Duplicate the session & enter in a new console \
```
cd kafka
bin/kafka-topics.sh --create --topic demo_testing --bootstrap-server Put the Public IP of your EC2 Instance:9092 --replication-factor 1 --partitions 1
```

Start Producer: \
```
bin/kafka-console-producer.sh --topic demo_testing --bootstrap-server Put the Public IP of your EC2 Instance:9092
```

Start Consumer: \
Duplicate the session & enter in a new console \
```
cd kafka
bin/kafka-console-consumer.sh --topic demo_testing --bootstrap-server Put the Public IP of your EC2 Instance:9092
```

### Loading Data into S3 Bucket using Apache Kafka
To load data into S3 Bucket please run the following two files in the order listed:
- [Kafka_Producer.ipynb](https://github.com/rjtkhanna/Kafka_stockMarket_dataEngine/blob/main/Kafka_Producer.ipynb)
- [Kafka_Consumer.ipynb](https://github.com/rjtkhanna/Kafka_stockMarket_dataEngine/blob/main/Kafka_Consumer.ipynb)

### Creating AWS Glue Database
To create an AWS Glue Database in which data would be loaded and from which we can query from Athena:
```
aws glue create-database
--database-input "{\"Name\":\"mytestdatabase-CLI\", \"Description\":\"This dB is created using AWS CLI\"}"
```

### Creating AWS Glue Crawler using CLI
To create a crawler that would load data from the S3 .json files to Glue database, following commands are used on AWS CLI:
```
aws glue create-crawler 
--name "crawler name" 
--role "IAM role" 
--database-name "database name" 
--description "suitable description" 
--targets S3Targets=[{Path="s3 bucket path/"}]
```
Start the crawler using following command in CLI: \
`aws glue start-crawler --name crawler name`







