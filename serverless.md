# Serverless 

* - [x] Lambda 
    - [x] Version control with Lambda
* - [x] API Gateway
    - [x] API Gateway Import, supports Swagger v2.0
    - [x] API Throttling 
            - 5000 concurrent request or 10,000 request in one second. 
* - [x] Alexa  (Theory)
* - [x] Step Functions (Theory)
* - [x] XRay


* - AWS Lambda Functions (THEORY)

    "It is a compute service where you can upload your code and create a Lambda Function. The Lambda function take care of provisioning and managing the servers that you use to run the code. 
    You don't have to worry about operating systems, patching, scale etc."

    - a) An event-driven compute service where AWS lambda runs your code in response to events. These events could be changes to data in S3 bucket or DynamoDB table. 
    - b) As compute service where Lambda function runs your code in response to HTTP request using Amazon API Gateway or API calls made using AWS SDKs. 

    Languages supported are:
    - Node.js
    - Java
    - Python
    - C#
    - Go 

    Prices 
    - Number of request
        - First 1 million request are free. $0.20 per million request thereafter. 
    - Duration 
        - priced on based on memory used by your function 

    * Advantages 
    - NO SERVERS!
    - Continuous Scaling
    - really cheap 

    - Alexa and Amazon echo use lambda functions. 

    * - Exam Tips 
        - Lambda scales out (not up) automatically.
        - Lambda functions are independent, 1 event = 1 function 
        - Lambda is serverless
        - Lambda is a compute service
        - Know what services are serverless!
            example Lambda, S3, dynamoDB, API Gateway etc
        - Lambda functions can trigger other lambda functions, 1 event can = x functions if functions trigger other functions

        - Architectures can get extremely complicated, AWS x-ray allows you to debug what is happening. 
        - Lambda can do things globally, you can use it to back up S3 buckets to other S3 buckets etc. 
        - Know your triggers 

* - API Gateway (THEORY)

    - "API Gateway is a fully  managed service that makes it easy for developers to publish, maintain, monitor, and secure APIs at any scale."
    - With a few clicks in in the AWS Management Console, you can create an API that acts as a "front door" for applications 
    to access data, business login, or functionality from your back-end services, such as applications running onAmazon Elastic Compute Cloud (EC2) , 
    code running on AWS Lambda, or any web application.

    - RESTful APIs
        - JSON 

    - SOAP APIs
        - XML 

    * What can a API Gateway do?
        - Expose HTTPS endpoints to define a RESTful API
        - Serverless-ly connect to services like Lambda & DynamoDB
        - Send each API end point to a different target
        - Run efficiently with low cost
        - Scale effortlessly
        - Track and control usage by API key
        - Throttle request to prevent attacks
        - Maintain multiple version of API

    * How do I configure API Gateway
        - Define an API (Container)
        - Define Resources and nested Resources (URL paths)
        - For each resource:
            - Select supported HttP methods (verbs)
            - Set security
            - Choose target (such as EC2, Lambda, DynamoDB, etc.) 
            - Set request and response transformations 
        - Deploy API to a stage 
            - Uses API Gateway domain, by default
            - Can use custom domain 
            - Now support AWs Certificate Manager: Free SSL/TLS certs1!

    * What is API Caching?
        lets you cache your endpoints response for a specified time-to-live (TTL) period.

    * Same Origin Policy
        - same-origin policy is an important concept in the web application security model. 
        - Under the policy, a web browser permits scripts contained in a first web page to access data in a second web page, but only if both web pages have the same origin. 
        - This policy is there to prevent XSS attacks. 

        - XSS - Cross Site Scripting 
             - injection type of attacks.
             - Enforced by web browsers. 
             - ignored by Postman and Curl

        * CORS - Cross Origin Resource Sharing (CORS)
            - Enforced by server's end and server can relax the same-origin-policy
            - CORS is a mechanism that allows restricted resources on a web page to be requested from another domain outside the domain from which the first resource was served. 

            - Browser makes an HTTP OPTIONS call for a URL. 
            - Server returns a response that says:
                "These other domains are approved to GET this URL."
            - Error - "Origin policy cannot be ready at the remote resource?"
                You need to enable CORS on API Gateway. 


        * For more details
        - https://dev.to/maleta/cors-xss-and-csrf-with-examples-in-10-minutes-35k3


* - Version control Lambda functions

    * Exam Tips 
    - Can have multiple versions of lambda functions
    - Latest version will use $latest
    - Qualified version will use $latest, unqualified will not have it 
    - Versions are immutable (Cannot be changed).
    - Can split traffic using aliases to different versions
        - Cannot split traffic with $latest, instead create an alias to latest. 


* - XRay 
    - to Debug Lambda functions. 

* - Alexa & Polly Service 

        - Alex is voice service.
        - Amazon Echo is hardware.
        - Polly is text-to-speech service. 

* - Step Functions 

    Step functions allows you to visualize and test your serverless applications. 
    Step Functions provides a graphical console to arrange and visualize the components of your application as a series of steps. 
    This makes it simple to build and run multi-step applications. Step Functions automatically triggers and tracks each step, and retires when there are errors, 
    so your application executes in order and as expected. Step functions logs the state of each step, so when things do go wrong, you cna diagnose and debug problems quickly. 

    - Sequential Steps 
    - Branches of Steps 
    - Parallel Steps 

    - You need to learn Amazon States Language (ASL) to write your own step functions.

* - X-Ray 

    AWS X-Ray is a service that collects data about requests that your application serves, and provides tools you can use to view, filter , and gaining insights into that data to identify issues and opportunities for optimization. Fora any traced request to your application, you can see detailed information not only about the request and response, but also about calls that yours application makes to downstream AWS resources, micro-services, databases and HTTP web APIs.

    X-Ray Deamon --> X-Ray API --> X-Ray Console 
        ^
        |
        |
    X-Ray SDK       Scripts & Tools


    * Exam Tips 

        - The X-Ray SDK provide:
            - 1. Interceptors to add to your code to trace incoming HTTP requests
            - 2. Client handlers to instrument AWS SDK clients that your application uses to call other AWS services
            - 3. An HTTP client to use to instrument calls to other internal and external HTTP web services. 

        - X-Ray integrates with the following AWS Services (FIVE)
            - Elastic Load Balancing 
            - Lambda
            - API Gateway
            - EC2
            - Elastic Beanstalk 

        - Languages 
            - Java
            - Node.js
            - Go
            - Python 
            - Ruby
            - .Net













