<!--
title: 'AWS NodeJS Example'
description: 'This template demonstrates how to deploy a NodeJS function running on AWS Lambda using the traditional Serverless Framework.'
layout: Doc
framework: v2
platform: AWS
language: nodeJS
priority: 1
authorLink: 'https://github.com/serverless'
authorName: 'Serverless, inc.'
authorAvatar: 'https://avatars1.githubusercontent.com/u/13742415?s=200&v=4'
-->


# Serverless Framework AWS NodeJS Example

This template demonstrates how to deploy a NodeJS function running on AWS Lambda using the traditional Serverless Framework. The deployed function does not include any event definitions as well as any kind of persistence (database). For more advanced configurations check out the [examples repo](https://github.com/serverless/examples/) which includes integrations with SQS, DynamoDB or examples of functions that are triggered in `cron`-like manner. For details about configuration of specific `events`, please refer to our [documentation](https://www.serverless.com/framework/docs/providers/aws/events/).

## Usage

### Deployment

In order to deploy the example, you need to run the following command:

```
$ serverless deploy
```

After running deploy, you should see output similar to:

```bash
Serverless: Packaging service...
Serverless: Excluding development dependencies...
Serverless: Creating Stack...
Serverless: Checking Stack create progress...
........
Serverless: Stack create finished...
Serverless: Uploading CloudFormation file to S3...
Serverless: Uploading artifacts...
Serverless: Uploading service aws-node.zip file to S3 (711.23 KB)...
Serverless: Validating template...
Serverless: Updating Stack...
Serverless: Checking Stack update progress...
.................................
Serverless: Stack update finished...
Service Information
service: aws-node
stage: dev
region: us-east-1
stack: aws-node-dev
resources: 6
functions:
  api: aws-node-dev-hello
layers:
  None
```

### Invocation

After successful deployment, you can invoke the deployed function by using the following command:

```bash
npm run invoke-trigger
```

Which should result in response similar to the following:

```json
Event*** {
  "Records": [
    {
      "eventID": "0562d66550d50714548c8f1d90015db5",
      "eventName": "INSERT",
      "eventVersion": "1.1",
      "eventSource": "aws:dynamodb",
      "awsRegion": "us-east-1",
      "dynamodb": {
        "ApproximateCreationDateTime": 1640384690,
        "Keys": {
          "nome": {
            "S": "Homem de ferro"
          },
          "id": {
            "S": "4e74e470-6508-11ec-98a8-bb7cb5e357b4"
          }
        },
        "NewImage": {
          "createdAt": {
            "S": "2021-12-24T22:24:49.207Z"
          },
          "nome": {
            "S": "Homem de ferro"
          },
          "id": {
            "S": "4e74e470-6508-11ec-98a8-bb7cb5e357b4"
          },
          "poder": {
            "S": "Rico"
          }
        },
        "SequenceNumber": "1395500000000084768988130",
        "SizeBytes": 154,
        "StreamViewType": "NEW_AND_OLD_IMAGES"
      },
      "eventSourceARN": "arn:aws:dynamodb:us-east-1:009700610486:table/Heroes/stream/2021-12-24T22:06:50.815"
    }
  ]
}
{
    "statusCode": 200
}
```

### Local development

You can invoke your function locally by using the following command:

```bash
npm run invoke-local
```

Which should result in response similar to the following:

```
{
    "statusCode": 200,
    "body": "{\"nome\":\"Homem de ferro\",\"poder\":\"Rico\",\"id\":\"4b81b550-67eb-11ec-aadd-b59e0058699f\",\"createdAt\":\"2021-12-28T14:34:42.341Z\"}" 
}
```
