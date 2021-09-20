## **Serverless 101**
````
Serverless: 
    Enables you to build scalable applications quickly without managing any servers
Low Cost: 
    Serverless applications are event-driven and you are only charged when your code is executed
AWS Handles the Heavy Lifting: 
    You can focus on writing code and building your application instead of configuring servers.
````

## **Lambda** 
````
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
````

## **API Gateway**
````
API Gateway:
    1. An API is like the front door to your application.
    2. API Gateway provides an endpoint to your applications running in AWS.
Serverless:
    1. Low cost and scales automatically.
Throttling:
    1. You can throttle API Gateway to prevent you application from being overloaded by too many requests.
CloudWatch:
    1. Everything is logged to CloudWatch.
    2. For example, API calls, latencies,and erros
````

## **Lambda Versions**
`````
1. $Latest: 
   1. $Latest is always the latest version of code you uploaded to Lambda
   
2. Versioning and Aliases: 
   1. Use Lambda versioning and aliases to point your applications to a specific version of your code if you don't want to use $Latest
   
Special Note: 
   1. If you have an application that is using a alias other than $Latest it will not update when you load new code. So if you upload new Lambda code you will need to change the Alias that program is using
`````

## **Lambda Concurrent Executions Limit**

`````
1. There is a limit of 1,000 concurrent executions per second. If the limit is exceeded it will return 429 error codes.
2. The remedy is to get the limit raised by AWS support
3. Reserved concurrency guarantees a set number of concurrent exections are always available to a crtitcal function.
`````