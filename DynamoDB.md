# DynamoDB
    - a low latency No-SQL Database 
    - serverless 
    - fully managed and scalable 
    - works well with Lambda functions 
    - Stored on SSD storage
    - Spread Across 3 geographically distinct data centers

    * Choice of 2 Consistency models:
        - Eventual Consistent Reads (Default)
        - Strongly Consistent Reads

    * Access is controlled using IAM policy 

    * It consist of Tables Items and Attributes

    * Tables 
    * Items => a record or row
    * Attributes  => a column or field
    * Supports Key-value and document data structures
        - Key => Name of the data
        - Value => the data itself
        - Document => can be written in JSON, XML or HTML. 

    * DynamoDB stores and retrieves data based on a Primary Keys
    * 2 types of Primary keys 
        - 1. Partition Key 
        - 2. Combination of Partition Key + Sort Key (Composite Key)

    * Fine grained access control using IAM condition parameter (DynamoDB:LeadingKeys to allow user to access only the items where the partition key value matches their user ID).

    * DynamoDB Indexes 
        - an index is a data structure which allows you to perform fast queries on a specific column in a table. 
       
        - 2 types of indexes supported by dynamoDb are:
            - 1. Local Secondary Index 
                - Must be created at when you create your table 
                - Same Partition Key as your table
                - Different Sort Key
            - 2. Global Secondary Index 
                - Can create any time - at table creation or after 
                - Different partition Key
                - Different Sort Key

    * Scan vs Query API call

        - Query 
            - Query operation finds items in a table tabled on the Primary Key attribute and a distinct value to search for. 
            - Use an Optional Sort Key name and value to refine the results. 
            - By default, a Query returns all the attributes for the items but you can use the ProjectionExpression parameter. 
            - Results are always sorted by the Sort Key. 
            - ScanIndexForward parameter to false for descending sort - Queries Only. 

        - Scan 
            - A Scan operation examines every item in the table. 
            - By default returns all data attributes 
        
        * Query or Scan? 
            - Query is more efficient than scan. 
            - Scan dumps the entire table, then filters out the values to provide the desired result - removing the unwanted data
            - This adds an extra step of removing the data you don't want. 
            - As the table grows, the scan operation takes longer. 
            - Scan operation on a large table cans use up the provisioned throughput for a large table in just a single operation. 

        * How to improve performance?
            - SMALLER PAGE SIZE: 
                - Your can reduce the impact of a query or scan by setting a smaller page size which used fewer readd operations. 
                - Larger number of smaller operations will allow other request to succeed without throttling. 
            - Avoid using scan operations if you can: design tables in a way that you can use the Query, Get, or BatchGetItem APIs. 
            - PARALLEL SCANS
                - By default, a scan operation processes data sequentially in returning 1 MB increments before moving on to retrieve the next 1 MB of dat. It can only scan one partition at a time. 
                - You can configure DynamoDB to use Parallel Scans instead by logically dividing a table or index into segments and scanning each segment in parallel.
                - Best to avoid paralleled scans if your table or index is already incurring heavy read/write activity from other applications. 

        * EXAM TIPS
            - A Query operation finds items in a table using only Primary Key attribute. 
            - You provide the Primary Key name and a distinct value to search for. 
            - A scan operation examines every item in the table. 
            - By default returns all data attributes. 
            - Use the ProjectionExpression parameter to refine the results. 
            - Query results are always sorted by  the Sort Key if there is one. 
            - Sorted in ascending order. 
            - Set ScanIndexForward parameter to false to reverse the order - queries only. 
            - Query operations is generally more efficient than a scan. 
            - Reduce the impact of a query or scn by setting a smaller page size which uses fewer read operations. 
            - Isolate scan operations to specific table and segregate them from your mission-critical traffic. 
            - Try Parallel scans, rather than the default sequential scan.
            - Avoid using scan operations if you cna: design tables in a way that you can us the Query, Get, or BatchGetItem APIs. 

    * Pricing Model
        - DynamoDB Provisioned Throughput
        - DynamoDB On-Demand Capacity

    * DynamoDB Provisioned Throughput 
            - measured in terms of Read & Write Capacity Unit. 

            - 1 x Write Capacity Unit = 1 x 1KB Write per second
            - 1 x Read Capacity Unit = 1 x Strongly Consistent Read of 4KB per second 
                                                            OR
                                       2 x Eventually Consistent Reads of 4KB per second (Default) 

        * Exam Tips 
            - CALCULATIONS is must to understand

            - You can forecast read and write capacity requirements
            - Predictable application traffic
            - Application traffic is consistent or increases gradually.

            
    * DynamoDB On-Demand Capacity (NEW OPTION)

        - Pay only for what you use, pay per request
        - great for unpredictable workloads
        - scales automatically based on demand
        - you don't need to specify your capacity requirements
        - Charges apply for: Reading, Writing and Storing Data


        - Unknown workloads
        - Unpredictable application traffic
        - You want a Pay-per-use model 
        - Spiky, short lived peaks

        - You can switch between two, once a day. 


    * DynamoDB Accelerator (DAX) 
        - in-memory cache for 10x read performance 
        - microsecond performance, for example Black Friday event
        - Eventually Consistent Read only, not for Strongly Consistent Read 

        TODO notes

    * Elasticache 
        - in-memory cache sits between your application and database.
        - 2 different strategies: Lazy loading and Write Through

        * Types 
            - memcached
            - redis 

        * Caching Strategies (Two)
            - lazy loading 
                - caches data only when it is requested. 
                - Elasticache Node failures not fatal, just lots of cache misses. 
                - Cache miss penalty: Initial request, query database, writing to cache
                - Time-To-Live (TTL) used for expired data.
            - Write-through
                - Writes data whenever data is added or update
                - data never expires 
                - Write Penalty: Each write involves a write to the cache
                - Elasticache node failure means that data is missing until added or updated in the database
                - Wasted resources if most of the data is never used. 

    * DynamoDB Transactions (feature added in 2018)
        - ACID Transactions 
            A Atomic        - Every transaction is treated as a single unit, its all or nothing i.e. it cannot be partially completed. 
            C Consistent    - It must be a valid transaction i.e. it must leave the database in a valid state to prevent any database corruption. (Data Integrity)
            I Isolated      - No dependency between transaction i.e. they can be completed in parallel or sequentially. The effect of each transaction will be same. 
            D Durable       - When a transaction has been committed it must be written to disk and no data loss due to power loss or system failure. 

            for example: 
                Financial Transaction have multiple steps and they must adhere to ACID rules. 

        - Read or write multiple items across multiple tables as an all or nothing operation
        - Check for a pre-requisite condition before writing to a table 


    * DynamoDB TTL (Time-to-live)

        - Coming in Exams

        - Time to live Attribute in table details, set via Items 
        - automatically removes stale data (48 deleted)
        - TTL expressed as epoch time, unix time , Jan 1970
        - filter your data based on epoch time. 

    # DynamoDB Streams / Triggers 

        - Coming in Exams 

        - "Think of Streams as equivalent to  SQL Triggers, good for serverless architecture. You can trigger lambda functions based on a changes in table"

        - Time-ordered sequence of item level modifications (Insert, update, delete)
            - useful for:
                - archiving 
                - auditing 
                - re-playing transactions 

        - Logs are encrypted at rest and stored for 24 hours
        - Accessed using a dedicated endpoint
        - By default, minimum you can store is the Primary Key. 
        - Before and After images can be captured. 

        - Can be used as an event source for Lambda so you can create applicataions which take actions based on nevents in your DynamoDy
    
    
    * Provisioned Throughput Exceeded Exception & Exponential Back-off

        TODO

    * DynamoDB Summary











