# Stock market data engine using Apache Kafka
In this project, we built an end-to-end data engineering pipeline using Apache Kafka.

## Introduction
This pipeline extracts data from a .csv file containing 100,000+ rows and stores it in an Amazon S3 bucket using Apache Kafka event streaming. After that data is loaded into the AWS Glue Data Catalog using AWS Glue Crawler. Ultimately, it enables us to query the data using Amazon Athena and SQL. Following technologies are used to build this data pipeline:
- Apache Kafka
- Amazon EC2
- Amazon S3
- AWS Glue Crawler
- AWS Glue Data Catalog
- Amazon Athena
