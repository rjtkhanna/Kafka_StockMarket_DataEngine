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
### Installing Apache Kafka on EC2
Use the following command to download Apache Kafka: \
`wget https://downloads.apache.org/kafka/3.5.2/kafka_2.12-3.5.2.tgz`

Unzip .tgz file and rename it: \
`tar -xvf kafka_2.12-3.5.2.tgz` \
`mv kafka_2.12-3.5.2 kafka`

Install Java: \
`sudo yum install java-1.8.0-openjdk`




