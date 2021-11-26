# sam-nodejs14-hello
Learn AWS Serverless Application Model.
* [Tutorial](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started-hello-world.html)

## 1. Setup
```sh
$ docker --version
Docker version 20.10.8, build 3967b7d

$ aws --version
aws-cli/2.4.0 Python/3.8.8 Windows/10 exe/AMD64 prompt/off

$ nvm ls
  * 10.15.3 (Currently using 64-bit executable)

$ sam.cmd --version
SAM CLI, version 1.35.0

$ sam.cmd init
Which template source would you like to use?
        1 - AWS Quick Start Templates
        2 - Custom Template Location
Choice: 1
What package type would you like to use?
        1 - Zip (artifact is a zip uploaded to S3)
        2 - Image (artifact is an image uploaded to an ECR image repository)
Package type: 1

Which runtime would you like to use?
        1 - nodejs14.x
        2 - python3.9
        3 - ruby2.7
        4 - go1.x
        5 - java11
        6 - dotnetcore3.1
        7 - nodejs12.x
        8 - nodejs10.x
        9 - python3.8
        10 - python3.7
        11 - python3.6
        12 - python2.7
        13 - ruby2.5
        14 - java8.al2
        15 - java8
        16 - dotnetcore2.1
Runtime: 1

Project name [sam-app]: sam-nodejs14-hello

Cloning from https://github.com/aws/aws-sam-cli-app-templates

AWS quick start application templates:
        1 - Hello World Example
        2 - Step Functions Sample App (Stock Trader)
        3 - Quick Start: From Scratch
        4 - Quick Start: Scheduled Events
        5 - Quick Start: S3
        6 - Quick Start: SNS
        7 - Quick Start: SQS
        8 - Quick Start: Web Backend
Template selection: 1

    -----------------------
    Generating application:
    -----------------------
    Name: sam-nodejs14-hello
    Runtime: nodejs14.x
    Architectures: x86_64
    Dependency Manager: npm
    Application Template: hello-world
    Output Directory: .

    Next application steps can be found in the README file at ./sam-nodejs14-hello/README.md


    Commands you can use next
    =========================
    [*] Create pipeline: cd sam-nodejs14-hello && sam pipeline init --bootstrap


$ cd sam-nodejs14-hello/

$ sam.cmd local start-api
Mounting HelloWorldFunction at http://127.0.0.1:3000/hello [GET]
You can now browse to the above endpoints to invoke your functions. You do not need to restart/reload SAM CLI while working on your functions, changes will be reflected instantly/automatically. You only need to restart SAM CLI if you update your AWS SAM template
2021-11-26 10:57:44  * Running on http://127.0.0.1:3000/ (Press CTRL+C to quit)
Invoking app.lambdaHandler (nodejs14.x)
Image was not found.
Removing rapid images for repo public.ecr.aws/sam/emulation-nodejs14.x
Building image.........................................................................
Skip pulling image and use local one: public.ecr.aws/sam/emulation-nodejs14.x:rapid-1.35.0-x86_64.

Mounting E:\workspace_sam\sam-nodejs14-hello\hello-world as /var/task:ro,delegated inside runtime container
START RequestId: 8cf79e1e-8559-4e5e-8b2a-c9fe1b990569 Version: $LATEST
END RequestId: 8cf79e1e-8559-4e5e-8b2a-c9fe1b990569
REPORT RequestId: 8cf79e1e-8559-4e5e-8b2a-c9fe1b990569  Init Duration: 0.09 ms  Duration: 110.62 ms     Billed Duration: 111 ms Memory Size: 128 MB     Max Memory Used: 128 MB
No Content-Type given. Defaulting to 'application/json'.
2021-11-26 10:58:09 127.0.0.1 - - [26/Nov/2021 10:58:09] "GET /hello HTTP/1.1" 200 -


$ curl --location --request GET 'http://127.0.0.1:3000/hello'

LGS-NET+WRY@GEO-WCND1383YRS MINGW64 /e/workspace_sam/sam-nodejs14-hello
$ sam.cmd local invoke
Invoking app.lambdaHandler (nodejs14.x)
Skip pulling image and use local one: public.ecr.aws/sam/emulation-nodejs14.x:rapid-1.35.0-x86_64.

Mounting E:\workspace_sam\sam-nodejs14-hello\hello-world as /var/task:ro,delegated inside runtime container
START RequestId: 131e8007-c117-47fc-a6b9-dad801b2b6a5 Version: $LATEST
END RequestId: 131e8007-c117-47fc-a6b9-dad801b2b6a5
REPORT RequestId: 131e8007-c117-47fc-a6b9-dad801b2b6a5  Init Duration: 0.08 ms  Duration: 73.93 ms      Billed Duration: 74 ms  Memory Size: 128 MB     Max Memory Used: 128 MB
{"statusCode":200,"body":"{\"message\":\"hello world\"}"}


$ sam.cmd build
Building codeuri: E:\workspace_sam\sam-nodejs14-hello\hello-world runtime: nodejs14.x metadata: {} architecture: x86_64 functions: ['HelloWorldFunction']
Running NodejsNpmBuilder:NpmPack
Running NodejsNpmBuilder:CopyNpmrc
Running NodejsNpmBuilder:CopySource
Running NodejsNpmBuilder:NpmInstall
Running NodejsNpmBuilder:CleanUpNpmrc

Build Succeeded

Built Artifacts  : .aws-sam\build
Built Template   : .aws-sam\build\template.yaml

Commands you can use next
=========================
[*] Invoke Function: sam local invoke
[*] Deploy: sam deploy --guided


LGS-NET+WRY@GEO-WCND1383YRS MINGW64 /e/workspace_sam/sam-nodejs14-hello
$ sam.cmd deploy --guided

Configuring SAM deploy
======================

        Looking for config file [samconfig.toml] :  Not found

        Setting default arguments for 'sam deploy'
        =========================================
        Stack Name [sam-app]: sam-nodejs14-hello
        AWS Region [us-west-1]:
        #Shows you resources changes to be deployed and require a 'Y' to initiate deploy
        Confirm changes before deploy [y/N]:
        #SAM needs permission to be able to create roles to connect to the resources in your template
        Allow SAM CLI IAM role creation [Y/n]:
        #Preserves the state of previously provisioned resources when an operation fails
        Disable rollback [y/N]:
        HelloWorldFunction may not have authorization defined, Is this okay? [y/N]: y
        Save arguments to configuration file [Y/n]:
        SAM configuration file [samconfig.toml]:
        SAM configuration environment [default]:

        Looking for resources needed for deployment:
         Managed S3 bucket: aws-sam-cli-managed-default-samclisourcebucket-1ht1pd3yeqhsn
         A different default S3 bucket can be set in samconfig.toml

        Saved arguments to config file
        Running 'sam deploy' for future deployments will use the parameters saved above.
        The above parameters can be changed by modifying samconfig.toml
        Learn more about samconfig.toml syntax at
        https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-config.html

Uploading to sam-nodejs14-hello/c695d005eb3e6113d9f3a3b47c7e20a1  128802 / 128802  (100.00%)
        Deploying with following values
        ===============================
        Stack name                   : sam-nodejs14-hello
        Region                       : us-west-1
        Confirm changeset            : False
        Disable rollback             : False
        Deployment s3 bucket         : aws-sam-cli-managed-default-samclisourcebucket-1ht1pd3yeqhsn
        Capabilities                 : ["CAPABILITY_IAM"]
        Parameter overrides          : {}
        Signing Profiles             : {}

Initiating deployment
=====================

Uploading to sam-nodejs14-hello/3714c5e8e1732ea0f5b3e4f71025c362.template  1201 / 1201  (100.00%)
Waiting for changeset to be created..

CloudFormation stack changeset
-------------------------------------------------------------------------------------------------
Operation                LogicalResourceId        ResourceType             Replacement
-------------------------------------------------------------------------------------------------
+ Add                    HelloWorldFunctionHell   AWS::Lambda::Permissio   N/A
                         oWorldPermissionProd     n
+ Add                    HelloWorldFunctionRole   AWS::IAM::Role           N/A
+ Add                    HelloWorldFunction       AWS::Lambda::Function    N/A
+ Add                    ServerlessRestApiDeplo   AWS::ApiGateway::Deplo   N/A
                         yment47fc2d5f9d          yment
+ Add                    ServerlessRestApiProdS   AWS::ApiGateway::Stage   N/A
                         tage
+ Add                    ServerlessRestApi        AWS::ApiGateway::RestA   N/A
                                                  pi
-------------------------------------------------------------------------------------------------

Changeset created successfully. arn:aws:cloudformation:us-west-1:450837389776:changeSet/samcli-deploy1637953408/3b55365e-672f-4618-91b2-631408461b34


2021-11-26 11:03:39 - Waiting for stack create/update to complete

CloudFormation events from stack operations
-------------------------------------------------------------------------------------------------
ResourceStatus           ResourceType             LogicalResourceId        ResourceStatusReason
-------------------------------------------------------------------------------------------------
CREATE_IN_PROGRESS       AWS::IAM::Role           HelloWorldFunctionRole   -
CREATE_IN_PROGRESS       AWS::IAM::Role           HelloWorldFunctionRole   Resource creation
                                                                           Initiated
CREATE_COMPLETE          AWS::IAM::Role           HelloWorldFunctionRole   -
CREATE_IN_PROGRESS       AWS::Lambda::Function    HelloWorldFunction       -
CREATE_IN_PROGRESS       AWS::Lambda::Function    HelloWorldFunction       Resource creation
                                                                           Initiated
CREATE_COMPLETE          AWS::Lambda::Function    HelloWorldFunction       -
CREATE_IN_PROGRESS       AWS::ApiGateway::RestA   ServerlessRestApi        -
                         pi
CREATE_IN_PROGRESS       AWS::ApiGateway::RestA   ServerlessRestApi        Resource creation
                         pi                                                Initiated
CREATE_COMPLETE          AWS::ApiGateway::RestA   ServerlessRestApi        -
                         pi
CREATE_IN_PROGRESS       AWS::Lambda::Permissio   HelloWorldFunctionHell   Resource creation
                         n                        oWorldPermissionProd     Initiated
CREATE_IN_PROGRESS       AWS::ApiGateway::Deplo   ServerlessRestApiDeplo   -
                         yment                    yment47fc2d5f9d
CREATE_IN_PROGRESS       AWS::Lambda::Permissio   HelloWorldFunctionHell   -
                         n                        oWorldPermissionProd
CREATE_IN_PROGRESS       AWS::ApiGateway::Deplo   ServerlessRestApiDeplo   Resource creation
                         yment                    yment47fc2d5f9d          Initiated
CREATE_COMPLETE          AWS::ApiGateway::Deplo   ServerlessRestApiDeplo   -
                         yment                    yment47fc2d5f9d
CREATE_IN_PROGRESS       AWS::ApiGateway::Stage   ServerlessRestApiProdS   -
                                                  tage
CREATE_COMPLETE          AWS::ApiGateway::Stage   ServerlessRestApiProdS   -
                                                  tage
CREATE_IN_PROGRESS       AWS::ApiGateway::Stage   ServerlessRestApiProdS   Resource creation
                                                  tage                     Initiated
CREATE_COMPLETE          AWS::Lambda::Permissio   HelloWorldFunctionHell   -
                         n                        oWorldPermissionProd
CREATE_COMPLETE          AWS::CloudFormation::S   sam-nodejs14-hello       -
                         tack
-------------------------------------------------------------------------------------------------

CloudFormation outputs from deployed stack
-------------------------------------------------------------------------------------------------
Outputs
-------------------------------------------------------------------------------------------------
Key                 HelloWorldFunctionIamRole
Description         Implicit IAM Role created for Hello World function
Value               arn:aws:iam::450837389776:role/sam-nodejs14-hello-
HelloWorldFunctionRole-1D3XLJMA0OPCK

Key                 HelloWorldApi
Description         API Gateway endpoint URL for Prod stage for Hello World function
Value               https://1ks2tqmnf4.execute-api.us-west-1.amazonaws.com/Prod/hello/

Key                 HelloWorldFunction
Description         Hello World Lambda Function ARN
Value               arn:aws:lambda:us-west-1:450837389776:function:sam-nodejs14-hello-
HelloWorldFunction-F0PSWHTm0LUA
-------------------------------------------------------------------------------------------------

Successfully created/updated stack - sam-nodejs14-hello in us-west-1



$ curl --request GET 'https://1ks2tqmnf4.execute-api.us-west-1.amazonaws.com/Prod/hello/'
{"message":"hello world"}

$ aws apigateway get-rest-apis
{
    "items": [
        {
            "id": "1ks2tqmnf4",
            "name": "sam-nodejs14-hello",
            "createdDate": "2021-11-26T11:04:12-08:00",
            "version": "1.0",
            "apiKeySource": "HEADER",
            "endpointConfiguration": {
                "types": [
                    "EDGE"
                ]
            },
            "tags": {
                "aws:cloudformation:logical-id": "ServerlessRestApi",
                "aws:cloudformation:stack-id": "arn:aws:cloudformation:us-west-1:450837389776:stack/sam-nodejs14-hello/8a8bedb0-4eeb-11ec-8339-0243f52d94a3",
                "aws:cloudformation:stack-name": "sam-nodejs14-hello"
            },
            "disableExecuteApiEndpoint": false
       }
    ]
}


$ aws cloudformation delete-stack --stack-name sam-nodejs14-hello --region us-west-1

$ aws cloudformation list-stacks
{
    "StackSummaries": [
        {
            "StackId": "arn:aws:cloudformation:us-west-1:450837389776:stack/sam-nodejs14-hello/8a8bedb0-4eeb-11ec-8339-0243f52d94a3",
            "StackName": "sam-nodejs14-hello",
            "TemplateDescription": "sam-nodejs14-hello\nSample SAM Template for sam-nodejs14-hello\n",
            "CreationTime": "2021-11-26T19:03:29.132000+00:00",
            "LastUpdatedTime": "2021-11-26T19:03:39.688000+00:00",
            "DeletionTime": "2021-11-26T19:18:52.065000+00:00",
            "StackStatus": "DELETE_IN_PROGRESS",
            "DriftInformation": {
                "StackDriftStatus": "NOT_CHECKED"
            }
        }
   ]
}


```
