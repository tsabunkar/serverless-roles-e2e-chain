<!--
title: 'AWS NodeJS Example'
description: 'This template demonstrates how to deploy a NodeJS function running on AWS Lambda using the traditional Serverless Framework.'
layout: Doc
framework: v3
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
Deploying aws-node-project to stage dev (us-east-1)

✔ Service deployed to stack aws-node-project-dev (112s)

functions:
  hello: aws-node-project-dev-hello (1.5 kB)
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
  "body": "{\n  \"message\": \"Go Serverless v3.0! Your function executed successfully!\",\n  \"input\": {}\n}"
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
    "body": "{\n  \"message\": \"Go Serverless v3.0! Your function executed successfully!\",\n  \"input\": \"\"\n}"
}
```

---

## How to Create User in AWS and let this user login to AWS GUI (Concole)

- IAM > Users
- User name : sita-dev
- Set permissions: Add user to group
  - junior-devs (already created this Group)
- create user
- Goto : IAM > Users > sita-dev
- Security credentials (tab)
  - Enable Console Access
  - Custom password
    - Give a new password
  - Enable Console Access
- Copy the Console password and Console Sing-in URL, username which will be used to login in AWS GUI/Console in different browser

## Assigning users or groups to an existing role

- Created IAM Role with Serverless framework -> ./roles.yml
  - RoleName: serverless-app-test-dev-read-role
    - PolicyName: lambdaCloudWatchBasicExecution (The above role has this policy)
  - Thus role is attached with Policy, A role HAS-A policy (Role--12M-->Policy)
- NOTE: To attach an AWS IAM role to an IAM user using the AWS CLI/Console, **you cannot directly attach a role to a user;** instead, you need to add the user to an IAM group that has permissions granted through a role.
- Add the user: ram-dev > to IAM Group: junior-devs
- NOTE: To attach an IAM role to an IAM group using the AWS CLI, **you typically don't directly attach a role to a group**. Instead, **you attach policies to the group or user**
-

## Command to deploy Serverless Framework application with a custom file name instead of serverless.yml

- \$ serverless deploy --config custom-config.yml
- \$ serverless deploy --config policy-attach-to-exisiting-group.yml

## How to Create IAM Policy Specific to a IAM User Group

- Check serverless --> ./policy-attach-to-exisiting-group.yml
