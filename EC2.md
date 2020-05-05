# Elastic Compute Cloud - EC2

* a virtual machine 

# EC2 Pricing Options
    * On Demand, pay as you use
    * Reserved, a contract - 1 year or 3 year
        - Standard RIs - 75% cheaper than On Demand
        - Convertibles RIs - 54% cheaper than on demand 
        - Scheduled RIs - 
    * Spot, a bid whatever price you want 
        - applications that have flexible start and end times. 
        - apps with very low compute prices
    * Dedicated hosts, good for database like SQL Server
        - good for regulatory requirements
        - can be on demand (hourly) or as a reservation for up to 70% off the On-Demand price. 

# EC2 Instance Types

    - Dr McGiftPx Or Fight Dr Mc Px

    - D for density
    - R for RAM
    - M for main choice for general purpose apps
    - C for Compute
    - G for Graphics
    - I for IOPS
    - F for FPGA
    - T for cheap general purpose (T2 Micro)
    - P for Graphics
    - X for Extreme Memory 
    - H for High Throughput

# What is ECB

* Elastic compute block allows you to create storage volues and attach them to EC2 instances. 
    - Automatically replicated
    - run database or use a a file system

   * ECB Types (2)

    - SSD
        - SSD (GP2)
            - General Purpose 
        - Provisioned IOPS SSD (101)
            - useful for extreme IPOS e.g. Database, RDBMS
            - more that 10,000 IOPS

    - Magnetic 
        - Throughput Optimized HDD (STI)
            - Big Data
            - Data warehouses
            - log processing 
            - cannot be boot volumes 
        - Cold HDD (SC1)
            - Lowest cost storage for infrequent access
            - File server

# Load Balancers 
    - Application LB, operate on Layer 7 and used to load balance of HTTP and HTTPS traffic.
    - Network LB,  Layer 4, TCP traffic where extreme performance is required. Very costly.
    - Classic LB, Legacy LB, it does both Application LB and Network LB, Throws 504 error means that Gateway has timed out. Trouble shot the app or db servers. 

    *  X-Forwarded-For Header:  
        - it is used to get IPv4 address of the end user. 

# Route53 
    * - Register the Domain Name 

# CLI 
 * - to connect to AWS using CLI tool 
 * - ssh into new EC2 instance 
    * 54.172.238.213, EC2 instance public IP
    * chmod 400 MyEC2KP.pem
    * ssh -i "MyEC2KP.pem" ec2-user@ec2-54-172-238-213.compute-1.amazonaws.com



# EC2 with S3 Role Lab
 
  - ** Exam tips ** 

  - Roles allow you not to use Access Key ID's and Secret Access Keys
  - Roles are preferred from a security perspective
  - Roles are controlled by policies
  - You can change a policy on a role and it will take immediate affect
  - You can attach and detach roles to running EC2 instances without having to stop or terminate these instances.

# RDS - Relational Database Server 
 - There are six Relational database that can be provisioned in RDS 

* - RDS - OLTP:
    - SQL Server
    - Oracle
    - MySQL
    - PostgreSQL
    - Aurora
    - MariaDB

* - Non-Relational Database, DynamoDB
    No need to define table structure, for example JSON 
    - Database
        - Collection        Table   
        - Document          Row
        - Key Value Pair    Field

* - Data Warehousing 
    - Used for Business Intelligence. Used to pull in very large and complex data sets and used by management to do queries. 

    * - Online Transaction Processing (OLTP)  vs Online Analytics Analytics Processing (OLAP)
        - Their difference in type of queries you run. 

        * - OLTP: 
            - A online store for example pull a row of data such as Name, Date, Address to deliver to, Delivery Status etc. 
            - Simple Transactions
            - Frequent Transactions 

        * - OLAP 
            - Redshift
            - a complex transactions
            - infrequent transactions 
            - trying to calculate net profit 
            - pulls in large number of records

        * Elasticache 
            - in-memory caching 
            - improves performance of web application 

            Engines (2): 
                - memcached
                - redis






54.166.166.243

