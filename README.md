# Serverless CRUD Example

Log in to AWS with your root credentials.  Serverless will invoke the browser to create IAM accounts if needed.

This is completely working code based on the video: https://www.youtube.com/watch?v=LXB2Nv9ygQc

## In a terminal:

```bash
  npm install -g serverless # (as root)
  npm install aws-sdk --save  # (optional)
  serverless create -u https://github.com/mwolfeu/kittenDB.git
    # serverless may create an IAM account if needed and store the secrets in ~/.aws
  cd kittenDB
  sls deploy --stage dev
```
## In the output you should see a section like:
### Note the endpoint urls to use with curl or test-rest.http
```bash
endpoints:
  POST - https://xxx.execute-api.us-east-1.amazonaws.com/dev/hello
  POST - https://xxx.execute-api.us-east-1.amazonaws.com/dev/v1/kitten
  GET - https://xxx.execute-api.us-east-1.amazonaws.com/dev/v1/kitten
  GET - https://xxx.execute-api.us-east-1.amazonaws.com/dev/v1/kitten/{name}
  PUT - https://xxx.execute-api.us-east-1.amazonaws.com/dev/v1/kitten/{name}
  DELETE - https://xxx.execute-api.us-east-1.amazonaws.com/dev/v1/kitten/{name}
```

## To remove the service:

```bash
  serverless remove --dev
```

If you have VSCode with the extension "REST Client" use the .http file to issue the REST calls.  Alternatively, use a tool like curl.


# ----------------------------
# Serverless Boilerplate Below
# ----------------------------

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
serverless invoke --function hello
```

Which should result in response similar to the following:

```json
{
    "statusCode": 200,
    "body": "{\n  \"message\": \"Go Serverless v2.0! Your function executed successfully!\",\n  \"input\": {}\n}"
}
```

### Local development

You can invoke your function locally by using the following command:

```bash
serverless invoke local --function hello
```

Which should result in response similar to the following:

```
{
    "statusCode": 200,
    "body": "{\n  \"message\": \"Go Serverless v2.0! Your function executed successfully!\",\n  \"input\": \"\"\n}"
}
```
