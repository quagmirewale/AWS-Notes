# AWS Certified Developer Associate Exam Notes

## **Introductions to Serverless Computing**

### **Serverless 101**

````text
Serverless: 
    Enables you to build scalable applications quickly without managing any servers

Low Cost: 
    Serverless applications are event-driven and you are only charged when your code is executed

AWS Handles the Heavy Lifting: 
    You can focus on writing code and building your application instead of configuring servers.
````

### **Lambda**

````text
Extremely Cost Effective: 
    Pay only when your code executes.

Continuous Scaling:
     Lambda scales automatically

Event-Driven: 
    Lambda functions are triggered by an event or action

Independent: 
    Lambda functions are independent. Each event will trigger a single function

Serverless Technology: 
    Lambda, API Gateway, DynamoDB, S3, SNS, SQS

Lambda Triggers: 
    Be aware of the services that can trigger a Lambda function for example:
        1. Dynamo DB
        2. Kinesis
        3. SQS
        4. Application Load Balancer
        5. API Gateway 
        6. Alexa
        7. CloudFront
        8. S3
        9. SNS
        10. SES
        11. CloudFormation
        12. CloudWatch
        13. CodeCommit
        14. CodePipeline

Lambda functions can be set to run up to 15 minutes.
````

### **API Gateway**

````text
API Gateway:
    - An API is like the front door to your application.
    - API Gateway provides an endpoint to your applications running in AWS.

Serverless:
    - Low cost and scales automatically.

Throttling:
    - You can throttle API Gateway to prevent you application from being overloaded by too many requests.

CloudWatch:
    - Everything is logged to CloudWatch.
    - For example, API calls, latencies,and erros
````

### **Lambda Versions**

`````text
$Latest: 
   - $Latest is always the latest version of code you uploaded to Lambda
   
Versioning and Aliases: 
   - Use Lambda versioning and aliases to point your applications to a specific version of your code if you don't want to use $Latest
   
Special Note: 
   - If you have an application that is using a alias other than $Latest it will not update when you load new code. So if you upload new Lambda code you will need to change the Alias that program is using
`````

### **Lambda Concurrent Executions Limit**

`````text
1. There is a limit of 1,000 concurrent executions per second. If the limit is exceeded it will return 429 error codes.
2. The remedy is to get the limit raised by AWS support
3. Reserved concurrency guarantees a set number of concurrent exections are always available to a crtitcal function.
`````

### **Lambda & VPC's**

`````text
You can enable Lamda to access resources in a private VPC.
   1. Provide VPC Config information to the Function
      1. Private subnet ID, and security group ID
   2. Lambda uses the VPC Information
      1. Lambda configures an ENI, using an IP from the private subnet CIDR range.
   3. Security Group
      1. The security group then allows your function to access resources in VPC.
`````

### **Step Fucntions**

`````text
Visualize and Orchestrate
   - Great way to visualize and orchestrate your serverless applications

Automate
    - Step Functions automatically trigger and track each step of the State Machine or workflow. The output of one step is often the input to the next.
   
Logging
   - Step Functions log the state of each step, so if something goes wrong you can track what went wrong, and where
`````

### **X-Ray**

`````text
Analyze and Debug
    -X-Ray helps developers analyze and debug distributed applications.

Service Map
    -The Servoce Map is a visual representation of your application

X-Ray Agent and X-Ray SDK
    - The X-Ray agent/daemon must be installed on your EC2 instance.
    - Use the X-Ray SDK to instrument your application to send traces to X-Ray.

1. Integrated with AWS Services
   1. X-Ray integrates with many AWS services like DynamoDB, Lambda, API Gateway, Elastic Load Balancer, AWS Elastic Beanstalk, Amazon Simple Notification Service, & Amazon Simple Queue service.
2. Your Applications
   1. You can also instrument your own applications to send data to X-Ray. For example, data about incoming HTTP request to you application
3. Supported Platforms
   1. Applications can be running on EC2, Elastic Beanstalk environments, on-premises systems and ECS
4. Running X-Ray IN ECS
   1. For ECS, run the X-Ray daemon in it's own Docker image, running alongside you application.
5. X-Ray Annotations
   1. Add user defined key-value pairs to your X-Ray data, allowing you to filter, index and search, e.g game_name=TicTacToe, game_id=2645
`````

### **API Gateway Caching**

`````text
1. Improves Performance
   1. Improve the performance of your APIs by caching the output of API calls to avoid calling your backend every time.
2. TTL
   1. Responses are cached for a TTL period. The defult TTL is 300 seconds
3. Reduces the Number of API Calls
   1. API Gateway returns the cached response instead of making new request to your application.
`````

### **API Gateway Throttling**

`````text
API Gateway default limits:
    10,000 rps(request per second)
    5,000 (concurrent requests)
            
Special notes:
*These are per region limitis
* These are default limits you can have the increased by AWS support.
* Amazon API Gateway provides Per-client throttling limits. These limits are applied to clients that use API keys associated with your usage policy as client identifier.
`````

### **Advanced API Gateway**

`````text
- You can import APIs using definition files, e.g, OpenAPI, formerly known as Swagger

- When dealing with legacy applications which use SOAP, you can configure API Gateway as a SOAP web service passthrough, or you can use API Gateway to convert XML response to JSON.
`````

## **DynamoDB**

### Into to DynamoDB

`````text
- Dynamo DB is a low latency NoSQL database
- Spports both document and key-value data models. Supported document formats are JSON, HTML, and XML.

- Fast and Flexible NoSQL Database
    - Consistent, single-digit milisecond latency at any scale.
- Full Managed 
    - Supports key-value data models. Supported document formats are JSON, HTML, and XML
- Use Cases
    - A great fit for mobile, web, gaming, ad tech, IoT, and many other applications.

Serverless
    - Integrates well with Lamnda 
    - DynamoDB can be configured to automatically scale.
    - A popular choice for developers and architects who are designing serverless applications

Features
    - Data is stored on SSD Storage
    - Data is spread across 3 geographically distinct data centers
    - Evenutally consistent reads(deafult)
      - Consistency across all copies of data is usually reached within a second. Best for read performance
    - Strongly consistent reads
      - Read always reflects all successful writes. Writes are reflected across all 3 locations at once. Best for read consistency.
    - ACID Transactions
      - (Atomic, Consistent, Isolated, Durable). Read or write multiple items across multiple tables as an all or nothing operation
  
  Transactions
    -DynamoDB data records are called items. Items refer to the row of data in the table. Each item a combination of attributes which is the columns in the table.
`````

### DynamoDB Primary Keys

`````text
- DynamoDB stores and retrieves data basod on a primary key

- There are two types primary keys of keys
    - Partition Key
    - Composite key (partition key + sort key)

- Partition Key
  - Based on a unique attribute
    - For example customer ID, product ID, email address
  - Value of the partition key is input to an internal hash function which determins the partition or physical location on which the data is stored.
  - If you are using the partition key as your primary key, then no two items can have the same partition key.

- Composite Key
  - Partition key + Sort key(Timestamp): Would be used in case the partition key is not unique within your table.
  - Gives you a unique combiniation within the table. Items in the table have the same partition key, but they must have a different sort key.
  - All items with the same partition key are stored together and then sorted according to the sort key value.

`````
