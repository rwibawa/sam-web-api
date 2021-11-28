# sam-web-api

## 1. Setup
```sh
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

Project name [sam-app]: sam-web-api

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
Template selection: 8

    -----------------------
    Generating application:
    -----------------------
    Name: sam-web-api
    Runtime: nodejs14.x
    Architectures: x86_64
    Dependency Manager: npm
    Application Template: quick-start-web
    Output Directory: .

    Next application steps can be found in the README file at ./sam-web-api/README.md


    Commands you can use next
    =========================
    [*] Create pipeline: cd sam-web-api && sam pipeline init --bootstrap


$ cd sam-web-api/
$ sam.cmd build
Building codeuri: E:\workspace_sam\sam-web-api runtime: nodejs14.x metadata: {} architecture: x86_64 functions: ['getAllItemsFunction', 'getByIdFunction', 'putItemFunction']
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


$ sam.cmd local start-api
```

## 2. Deploy the APIs
```sh
$ sam.cmd deploy --guided

Configuring SAM deploy
======================

        Looking for config file [samconfig.toml] :  Not found

        Setting default arguments for 'sam deploy'
        =========================================
        Stack Name [sam-app]: sam-web-api
        AWS Region [us-west-1]:
        #Shows you resources changes to be deployed and require a 'Y' to initiate deploy
        Confirm changes before deploy [y/N]:
        #SAM needs permission to be able to create roles to connect to the resources in your template
        Allow SAM CLI IAM role creation [Y/n]:
        #Preserves the state of previously provisioned resources when an operation fails
        Disable rollback [y/N]:
        getAllItemsFunction may not have authorization defined, Is this okay? [y/N]: y
        getByIdFunction may not have authorization defined, Is this okay? [y/N]: y
        putItemFunction may not have authorization defined, Is this okay? [y/N]: y
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

Uploading to sam-web-api/486e7fd1544a58b113bc490045dd9d21  9354277 / 9354277  (100.00%)
File with same data already exists at sam-web-api/486e7fd1544a58b113bc490045dd9d21, skipping upload
File with same data already exists at sam-web-api/486e7fd1544a58b113bc490045dd9d21, skipping upload

        Deploying with following values
        ===============================
        Stack name                   : sam-web-api
        Region                       : us-west-1
        Confirm changeset            : False
        Disable rollback             : False
        Deployment s3 bucket         : aws-sam-cli-managed-default-samclisourcebucket-1ht1pd3yeqhsn
        Capabilities                 : ["CAPABILITY_IAM"]
        Parameter overrides          : {}
        Signing Profiles             : {}

Initiating deployment
=====================
Uploading to sam-web-api/85555fa3a397c035fcad8a689e239935.template  2912 / 2912  (100.00%)
Waiting for changeset to be created..

CloudFormation stack changeset
-------------------------------------------------------------------------------------------------
Operation                LogicalResourceId        ResourceType             Replacement
-------------------------------------------------------------------------------------------------
+ Add                    SampleTable              AWS::DynamoDB::Table     N/A
+ Add                    ServerlessRestApiDeplo   AWS::ApiGateway::Deplo   N/A
                         ymenta4d359a69a          yment
+ Add                    ServerlessRestApiProdS   AWS::ApiGateway::Stage   N/A
                         tage
+ Add                    ServerlessRestApi        AWS::ApiGateway::RestA   N/A
                                                  pi
+ Add                    getAllItemsFunctionApi   AWS::Lambda::Permissio   N/A
                         PermissionProd           n
+ Add                    getAllItemsFunctionRol   AWS::IAM::Role           N/A
                         e
+ Add                    getAllItemsFunction      AWS::Lambda::Function    N/A
+ Add                    getByIdFunctionApiPerm   AWS::Lambda::Permissio   N/A
                         issionProd               n
+ Add                    getByIdFunctionRole      AWS::IAM::Role           N/A
+ Add                    getByIdFunction          AWS::Lambda::Function    N/A
+ Add                    putItemFunctionApiPerm   AWS::Lambda::Permissio   N/A
                         issionProd               n
+ Add                    putItemFunctionRole      AWS::IAM::Role           N/A
+ Add                    putItemFunction          AWS::Lambda::Function    N/A
-------------------------------------------------------------------------------------------------

Changeset created successfully. arn:aws:cloudformation:us-west-1:450837389776:changeSet/samcli-deploy1637995578/17705f1c-c27c-4a79-a4b3-262fd12d4a96


2021-11-26 22:46:29 - Waiting for stack create/update to complete

CloudFormation events from stack operations
-------------------------------------------------------------------------------------------------
ResourceStatus           ResourceType             LogicalResourceId        ResourceStatusReason
-------------------------------------------------------------------------------------------------
CREATE_IN_PROGRESS       AWS::DynamoDB::Table     SampleTable              -
CREATE_IN_PROGRESS       AWS::DynamoDB::Table     SampleTable              Resource creation
                                                                           Initiated
CREATE_COMPLETE          AWS::DynamoDB::Table     SampleTable              -
CREATE_IN_PROGRESS       AWS::IAM::Role           getAllItemsFunctionRol   Resource creation
                                                  e                        Initiated
CREATE_IN_PROGRESS       AWS::IAM::Role           putItemFunctionRole      -
CREATE_IN_PROGRESS       AWS::IAM::Role           getByIdFunctionRole      -
CREATE_IN_PROGRESS       AWS::IAM::Role           getAllItemsFunctionRol   -
                                                  e
CREATE_IN_PROGRESS       AWS::IAM::Role           putItemFunctionRole      Resource creation
                                                                           Initiated
CREATE_IN_PROGRESS       AWS::IAM::Role           getByIdFunctionRole      Resource creation
                                                                           Initiated
CREATE_COMPLETE          AWS::IAM::Role           putItemFunctionRole      -
CREATE_COMPLETE          AWS::IAM::Role           getAllItemsFunctionRol   -
                                                  e
CREATE_COMPLETE          AWS::IAM::Role           getByIdFunctionRole      -
CREATE_IN_PROGRESS       AWS::Lambda::Function    getAllItemsFunction      -
CREATE_IN_PROGRESS       AWS::Lambda::Function    putItemFunction          -
CREATE_IN_PROGRESS       AWS::Lambda::Function    getByIdFunction          -
CREATE_IN_PROGRESS       AWS::Lambda::Function    putItemFunction          Resource creation
                                                                           Initiated
CREATE_IN_PROGRESS       AWS::Lambda::Function    getByIdFunction          Resource creation
                                                                           Initiated
CREATE_IN_PROGRESS       AWS::Lambda::Function    getAllItemsFunction      Resource creation
                                                                           Initiated
CREATE_COMPLETE          AWS::Lambda::Function    getByIdFunction          -
CREATE_COMPLETE          AWS::Lambda::Function    putItemFunction          -
CREATE_COMPLETE          AWS::Lambda::Function    getAllItemsFunction      -
CREATE_IN_PROGRESS       AWS::ApiGateway::RestA   ServerlessRestApi        -
                         pi
CREATE_IN_PROGRESS       AWS::ApiGateway::RestA   ServerlessRestApi        Resource creation
                         pi                                                Initiated
CREATE_COMPLETE          AWS::ApiGateway::RestA   ServerlessRestApi        -
                         pi
CREATE_IN_PROGRESS       AWS::Lambda::Permissio   getByIdFunctionApiPerm   Resource creation
                         n                        issionProd               Initiated
CREATE_IN_PROGRESS       AWS::Lambda::Permissio   getAllItemsFunctionApi   Resource creation
                         n                        PermissionProd           Initiated
CREATE_IN_PROGRESS       AWS::Lambda::Permissio   putItemFunctionApiPerm   -
                         n                        issionProd
CREATE_IN_PROGRESS       AWS::ApiGateway::Deplo   ServerlessRestApiDeplo   -
                         yment                    ymenta4d359a69a
CREATE_IN_PROGRESS       AWS::Lambda::Permissio   getByIdFunctionApiPerm   -
                         n                        issionProd
CREATE_IN_PROGRESS       AWS::Lambda::Permissio   getAllItemsFunctionApi   -
                         n                        PermissionProd
CREATE_IN_PROGRESS       AWS::ApiGateway::Deplo   ServerlessRestApiDeplo   Resource creation
                         yment                    ymenta4d359a69a          Initiated
CREATE_IN_PROGRESS       AWS::Lambda::Permissio   putItemFunctionApiPerm   Resource creation
                         n                        issionProd               Initiated
CREATE_COMPLETE          AWS::ApiGateway::Deplo   ServerlessRestApiDeplo   -
                         yment                    ymenta4d359a69a
CREATE_IN_PROGRESS       AWS::ApiGateway::Stage   ServerlessRestApiProdS   -
                                                  tage
CREATE_IN_PROGRESS       AWS::ApiGateway::Stage   ServerlessRestApiProdS   Resource creation
                                                  tage                     Initiated
CREATE_COMPLETE          AWS::ApiGateway::Stage   ServerlessRestApiProdS   -
                                                  tage
CREATE_COMPLETE          AWS::Lambda::Permissio   putItemFunctionApiPerm   -
                         n                        issionProd
CREATE_COMPLETE          AWS::Lambda::Permissio   getByIdFunctionApiPerm   -
                         n                        issionProd
CREATE_COMPLETE          AWS::Lambda::Permissio   getAllItemsFunctionApi   -
                         n                        PermissionProd
CREATE_COMPLETE          AWS::CloudFormation::S   sam-web-api              -
                         tack
-------------------------------------------------------------------------------------------------

CloudFormation outputs from deployed stack
-------------------------------------------------------------------------------------------------
Outputs
-------------------------------------------------------------------------------------------------
Key                 WebEndpoint
Description         API Gateway endpoint URL for Prod stage
Value               https://whosrt5g9k.execute-api.us-west-1.amazonaws.com/Prod/
-------------------------------------------------------------------------------------------------

Successfully created/updated stack - sam-web-api in us-west-1
```

## 3. Invoke APIs
```sh
$ curl --location --request POST 'https://whosrt5g9k.execute-api.us-west-1.amazonaws.com/Prod/' \
 --header 'Content-Type: application/json' \
 --data-raw '{
     "id": "3",
     "name": "XBOX X"
 }'

{"id":"3","name":"XBOX X"}

$ curl --location --request GET 'https://whosrt5g9k.execute-api.us-west-1.amazonaws.com/Prod/'
[{"id":"2","name":"MacBook Pro"},{"id":"1","name":"Google Pixel 6 Pro"},{"id":"3","name":"XBOX X"}]

$ curl --location --request GET 'https://whosrt5g9k.execute-api.us-west-1.amazonaws.com/Prod/2'
{"id":"2","name":"MacBook Pro"}

$ aws dynamodb list-tables
{
    "TableNames": [
        "archived_objects",
        "sam-web-api-SampleTable-PF99XN5AA213"
    ]
}

$ aws dynamodb describe-table --table-name "sam-web-api-SampleTable-PF99XN5AA213"
{
    "Table": {
        "AttributeDefinitions": [
            {
                "AttributeName": "id",
                "AttributeType": "S"
            }
        ],
        "TableName": "sam-web-api-SampleTable-PF99XN5AA213",
        "KeySchema": [
            {
                "AttributeName": "id",
                "KeyType": "HASH"
            }
        ],
        "TableStatus": "ACTIVE",
        "CreationDateTime": "2021-11-26T22:46:34.086000-08:00",
        "ProvisionedThroughput": {
            "NumberOfDecreasesToday": 0,
            "ReadCapacityUnits": 2,
            "WriteCapacityUnits": 2
        },
        "TableSizeBytes": 0,
        "ItemCount": 0,
        "TableArn": "arn:aws:dynamodb:us-west-1:450837389776:table/sam-web-api-SampleTable-PF99XN5AA213",
        "TableId": "3de9302c-f5ef-4fd0-81ec-9179a365e761"
    }
}

```

## 4. Install DynamoDB locally.
* [Deploy local DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBLocal.DownloadingAndRunning.html)
```sh
$ docker network create local-dev
$ docker-compose up
Creating network "sam-web-api_default" with the default driver
Pulling dynamodb-local (amazon/dynamodb-local:latest)...
latest: Pulling from amazon/dynamodb-local
Digest: sha256:95358cb2eb7f73fab027d1ec7319c75e2ff1e60830437c01dce772e1e8f2978c
Status: Downloaded newer image for amazon/dynamodb-local:latest
Creating dynamodb-local ...
Creating dynamodb-local ... done
Attaching to dynamodb-local
dynamodb-local    | Initializing DynamoDB Local with the following configuration:
dynamodb-local    | Port:       8000
dynamodb-local    | InMemory:   false
dynamodb-local    | DbPath:     ./data
dynamodb-local    | SharedDb:   true
dynamodb-local    | shouldDelayTransientStatuses:       false
dynamodb-local    | CorsParams: *
dynamodb-local    |

# Or
$ docker-compose up -d
$ docker logs dynamodb-local
```
* [aws-cli to access local db](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Tools.CLI.html)
```sh
$ aws dynamodb list-tables --endpoint-url http://localhost:8000
{
    "TableNames": []
}

# Create SampleTable
$ aws dynamodb create-table --table-name SampleTable --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --provisioned-throughput ReadCapacityUnits=2,WriteCapacityUnits=2 --endpoint-url http://localhost:8000

$ sam.cmd local invoke getAllItemsFunction --event events/event-get-all-items.json --parameter-overrides ParameterKey=Environment,ParameterValue=local ParameterKey=SAMPLE_TABLE,ParameterValue=SampleTable --docker-network local-dev

# Start local API
$ sam.cmd local start-api --parameter-overrides ParameterKey=Environment,ParameterValue=local ParameterKey=DDBTableName,ParameterValue=documentTable --docker-network local-dev

# API calls
$ curl --location --request POST 'http://localhost:3000' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": "1",
    "name": "Google Pixel 6 Pro"
}'

$ curl --location --request GET 'http://localhost:3000'
$ curl --location --request GET 'http://localhost:3000/3'

# Delete SampleTable
$ aws dynamodb delete-table --table-name SampleTable --endpoint-url http://localhost:8000

```

* [NoSQL Workbench](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/workbench.settingup.html)

## DynamoDB Queries
```sh

$ aws dynamodb create-table \
    --endpoint-url http://localhost:8000 \
    --table-name Music \
    --attribute-definitions \
        AttributeName=Artist,AttributeType=S \
        AttributeName=SongTitle,AttributeType=S \
    --key-schema AttributeName=Artist,KeyType=HASH AttributeName=SongTitle,KeyType=RANGE \
    --provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1
{
    "TableDescription": {
        "AttributeDefinitions": [
            {
                "AttributeName": "Artist",
                "AttributeType": "S"
            },
            {
                "AttributeName": "SongTitle",
                "AttributeType": "S"
            }
        ],
        "TableName": "Music",
        "KeySchema": [
            {
                "AttributeName": "Artist",
                "KeyType": "HASH"
            },
            {
                "AttributeName": "SongTitle",
                "KeyType": "RANGE"
            }
        ],
        "TableStatus": "ACTIVE",
        "CreationDateTime": "2021-11-27T00:01:45.676000-08:00",
        "ProvisionedThroughput": {
            "LastIncreaseDateTime": "1969-12-31T16:00:00-08:00",
            "LastDecreaseDateTime": "1969-12-31T16:00:00-08:00",
            "NumberOfDecreasesToday": 0,
            "ReadCapacityUnits": 1,
            "WriteCapacityUnits": 1
        },
        "TableSizeBytes": 0,
        "ItemCount": 0,
        "TableArn": "arn:aws:dynamodb:ddblocal:000000000000:table/Music"
    }
}

$ aws dynamodb put-item \
    --endpoint-url http://localhost:8000 \
    --table-name Music \
    --item \
        '{"Artist": {"S": "No One You Know"}, "SongTitle": {"S": "Call Me Today"}, "AlbumTitle": {"S": "Somewhat Famous"}}' \
    --return-consumed-capacity TOTAL  
{
    "ConsumedCapacity": {
        "TableName": "Music",
        "CapacityUnits": 1.0
    }
}

$ aws dynamodb put-item \
    --endpoint-url http://localhost:8000 \
    --table-name Music \
    --item \
      '{
        "Artist": {"S": "Acme Band"},
        "SongTitle": {"S": "Happy Day"},
        "AlbumTitle": {"S": "Songs About Life"} 
      }' \
    --return-consumed-capacity TOTAL
{
    "ConsumedCapacity": {
        "TableName": "Music",
        "CapacityUnits": 1.0
    }
}

$ cat key-conditions.json
{
    "Artist": {
        "AttributeValueList": [
            {
                "S": "No One You Know"
            }
        ],
        "ComparisonOperator": "EQ"
    },
    "SongTitle": {
        "AttributeValueList": [
            {
                "S": "Call Me Today"
            }
        ],
        "ComparisonOperator": "EQ"
    }
}

$ aws dynamodb query --endpoint-url http://localhost:8000 --table-name Music --key-conditions file://key-conditions.json
{
    "Items": [
        {
            "Artist": {
                "S": "No One You Know"
            },
            "SongTitle": {
                "S": "Call Me Today"
            },
            "AlbumTitle": {
                "S": "Somewhat Famous"
            }
        }
    ],
    "Count": 1,
    "ScannedCount": 1,
    "ConsumedCapacity": null
}
```