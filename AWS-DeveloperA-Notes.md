# AWS Certified Developer Associate Exam Notes

## **Serverless 101**

````text
Serverless: 
    Enables you to build scalable applications quickly without managing any servers

Low Cost: 
    Serverless applications are event-driven and you are only charged when your code is executed

AWS Handles the Heavy Lifting: 
    You can focus on writing code and building your application instead of configuring servers.
````

## **Lambda**

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
````

## **API Gateway**

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

## **Lambda Versions**

`````text
$Latest: 
   - $Latest is always the latest version of code you uploaded to Lambda
   
Versioning and Aliases: 
   - Use Lambda versioning and aliases to point your applications to a specific version of your code if you don't want to use $Latest
   
Special Note: 
   - If you have an application that is using a alias other than $Latest it will not update when you load new code. So if you upload new Lambda code you will need to change the Alias that program is using
`````

## **Lambda Concurrent Executions Limit**

`````text
1. There is a limit of 1,000 concurrent executions per second. If the limit is exceeded it will return 429 error codes.
2. The remedy is to get the limit raised by AWS support
3. Reserved concurrency guarantees a set number of concurrent exections are always available to a crtitcal function.
`````

## **Lambda & VPC's**

`````text
You can enable Lamda to access resources in a private VPC.
   1. Provide VPC Config information to the Function
      1. Private subnet ID, and security group ID
   2. Lambda uses the VPC Information
      1. Lambda configures an ENI, using an IP from the private subnet CIDR range.
   3. Security Group
      1. The security group then allows your function to access resources in VPC.
`````

## **Step Fucntions**

`````text
Visualize and Orchestrate
   - Great way to visualize and orchestrate your serverless applications

Automate
    - Step Functions automatically trigger and track each step of the State Machine or workflow. The output of one step is often the input to the next.
   
Logging
   - Step Functions log the state of each step, so if something goes wrong you can track what went wrong, and where
`````

## **X-Ray**

`````text
Analyze and Debug
    -X-Ray helps developers analyze and debug distributed applications.

Service Map
    -The Servoce Map is a visual representation of your application

X-Ray Agent and X-Ray SDK
    - The X-Ray agent/daemon must be installed on your EC2 instance.
    - Use the X-Ray SDK to instrument your application to send traces to X-Ray.
`````
