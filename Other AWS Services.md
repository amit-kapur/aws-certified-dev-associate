# Other AWS Services

    - [x] SQS - Simple Queue Service 
        - SQS Visibility Timeout 
        - SQL Long Polling
    - [] SNS - Simple Notification Service 
    - [] SES vs SNS - Simple Email Service vs Simple Notification Service
    - [] ElasticBeanStalk
    - [] Kinesis 


# Simple Queue Service (SQS)
    This is the first AWS service developed by Amazon team.

    - SQL is a distributed message queueing system
    - Allows you to decouple the components of an application so that they are independent 


    - [x] SQL is a Pull Based System, not Push based system. 
    - [x] Messages are 256 KB in size 
    - [x] Messages can be kept in the queue from 1 minute to 14 days
    - [x] Default retention period is 4 days
    - [x] SQL Guarantees that your messages will be processed at least once. 

    - A queue is a temporary repository of messages that are awaiting to be processed. 
    - "Amazon Simple Queue Service is a web service that gives you access to a message queue that can be used to store messages while waiting for a computer to process them."

    * Advantages of Simple Queue Service
        - Using Amazon SQS, you can decouple the components of an application so they run independently, easing message management between components. 
        - Any component of a distributed application can stere messages in the queue. Messages can contain up to 256 KB of text in amy format. Any component can later retrieve the messages programmatically using the Amazon SQL API. 
        - The queue acts as a buffer between the component producing and saving data, and the component receiving the data for processing. 
        This means the queue resolves issues that arise if the producer is producing work faster than the consumer can process it, or if the producer or consumer 
        are only intermittently connected to the network. 

    * Queues Types 
        - 1. Standard Queue (default option)
            - Unlimited number of transactions per second. 
            - guarantee that a message is delivered at least once. 
            - may deliver copy of message more than once. 
            - best-effort ordering which ensures that messages are generally delivered in the same order as they are sent. 
        - 2. FIFO Queue 
            - New feature added 
            - the order is preserved and a message is delivered once and remains available until a consumer processes and deleted it; 
            - duplicates are not introduced into the queue.
            -FIFO delivery and exactly once processing
            - limited 300 transactions per seconds (TPS)
            - Good for Banking Transactions etc. which need to happen in strict order  

    * SQS Visibility Timeout parameter
        It is the amount of time that the message is invisible in the SQL Queue after a reader picks up that message. 
        Once message is processed successfully before the visibility timeout expires, then the message is deleted from the queue. 
        Otherwise, the message will become visible again and another reader will process it. This could result in the same message being delivered twice. 

        - Default Visibility timeout is 30 seconds
        - Increase if your takes takes > 30 seconds
        - Max is 12 hours

    * SQS Long Polling 

        Short Polling: returned immediately even if no messages are in the queue. 

        Long Polling: polls the queue periodically and only returns a response when a message is in the queue or the timeout is reached. 
                      It helps saves money as you don't poll empty queues. 


# Simple Notification Service (SNS)

    - Push Based System

    - follows "publish-subscribe" messaging paradigm, with notifications being delivered to clients using a "push" mechanism that eliminates the need to periodically check or "poll" for new information
    and updates. 

    - Formats supported
        - sms
        - email 
        - http endpoints
        - SQL 
        - Lambda functions
        - etc. 

    It is a web service that makes ite easy to setup, operate, and send notifications from the cloud. 
    
    It provides developers with a highly scalable, flexible, and cost-effective capability to publish messages from an application and immediately deliver them to subscribers or other applications. 

    - Pricing:
        - User pays $0.50 per 1 million Amazon SNS Requests
        - $0.06 per 100,000 Notification deliveries over HTTP
        - $0.75 per 100,000 Notification deliveries over SMS
        - $2 per 100,000 Notification deliveries over Email


# SNS vs SQS

    - Both are messaging services 
    - SNS - Push
    - SQL - Pull (Polls)


* Simple Email Service (SES)

    It is a scalable and highly available email service designed to help marketing team and application developers send marketing, 
    notification, and transactional emails to their customers using a pay as you go model. 

    You only need to know email address. 


# Elastic Beanstalk

It is a service for deploying and scaling web applications developed in many popular languages:
Java, .NET, PHP, Node.js, Python, Ruby, Go and Docker on widely used application server platforms like 
Apache Tomcat, Nginx, IIS etc. 

Provides infrastructure needed to run the application (IaaS)
A provisioning service for applications 

You upload your code and Elastic Beanstalk will handle deployment, capacity provisioning, load balancing, auto-scaling and application health.

You retain full control of the underlying AWS resources powering your application and you pay only for the AWS resources required to store and run your applications. 

    # Updating Elastic Beanstalk 

    ** Important for exam **

    * EBS Deployment Policies 

        - 1. All at once
            - Service interruptions while you update the entire environment at one - Outages and Downtime 
            - Not ideal for Mission critical applications
            - Rollback to previous version when update fails.

        - 2. Rolling 
            - Deploys the new version in batches 
            - Each batch of instances is taken out of service while the deployment takes place.
            - Your environment capacity will be reduced by the number of instances in a batch while the deployment takes place
            - Not ideal for Performance sensitive systems 
            - If the update fails, you need to perform an additional rolling update to roll back the changes

            - Reduced capacity during deployment
            - To roll back, perform a further rolling update.

        - 3. Rolling with additional Batch
            - Launches an additional batch of instances
            - Deploys the new version in batches 
            - No Downtime and maintains Full Capacity #

             - Maintains Full capacity during deployment
            - To roll back, perform a further rolling update.

        - 4. Immutable 
            - Deploys the new version to a fresh group of instances in their own new auto-scaling group 
            - When the new instances pass their health checks, then are moved to your existing auto scaling group; finally, old instances are terminated. 
            - Maintains full capacity during the deployment process
            - The impact fo failed update is far leas, and the rollback process requires only terminating the new auto scaling group 
           
            - Preferred option for Mission Critical production systems
            - Maintains Full capacity 
            - To roll back, just delete the new instance and auto-scaling group.


    #  Configuration file for Elastic Beanstalk environment

        - any filename with .config extension 
            - for example myhealthcheckurl.config
        - the config file can have JSON or YAML format
        - It must be saved in .ebextensions folder and this folder should be saved in Top level directory of the application source code bundle. 


# Kinesis 

    - Streaming data? 
        - stock prices
        - gaming data
        - social network data
        - purchases from online stores, think AMAZON 
        - geospatial data , think UBER
        - iOT Sensor data

    Amazon Kinesis is a platform on AWS to send your streaming data too. Kinesis makes it easy to load and analyze streaming data, 
    and also providing the ability for you to build your own custom applications for your business needs. 

    - Services (Three)
        - 1. Kineses Streams (Shards)
            - stores data send by producer in shards for 24 hours. You can increase them to 7 days. 
            Next, EC2 consumes the data and perform calculation 
            Finally, you can store the data in S3, Redshift, DynamoDB, EMR

            You can have multiple shards in a stream. 

        - 2. Kinesis Firehose (Lambda)

            Data Producers --> Kinesis Firehose (Fully Automated, No shards) --> Analysed ny Lambda (maybe) -->  S3, Firehose, Elasticsearch cluster

        - 3. Kinesis Analytics 
            - Run SQL queries on Streams or Firehose and save result in S3. 






            

