# DynamoDB
    - a low latency No-SQL Database 
    - serverless 
    - fully managed and scalable 
    - works well with Lambda functions 
    - Stored on SSD storage
    - Spread Across 3 geographically distinct data centers

    * Choice of 2 Consistency models:
        - Eventual Consistent Reads
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