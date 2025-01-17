# AppSync GraphQL API Acting on DynamoDB

## <!--BEGIN STABILITY BANNER-->

![Stability: Experimental](https://img.shields.io/badge/stability-Experimental-important.svg?style=for-the-badge)

> **This is an experimental example. It may not build out of the box**
>
> This examples does is built on Construct Libraries marked "Experimental" and may not be updated for latest breaking changes.
>
> If build is unsuccessful, please create an [issue](https://github.com/aws-samples/aws-cdk-examples/issues/new) so that we may debug the problem

---

<!--END STABILITY BANNER-->

This an example of an AppSync GraphQL API, pointing to four resolvers doing CRUD operations with a single DynamoDB table.

## Build

To build this app, you need to be in this example's root folder. Then run the following:

```bash
npm install -g aws-cdk
npm install
npm run build
```

This will install the necessary CDK, then this example's dependencies, and then build your TypeScript files and your CloudFormation template.

## Deploy

Run `cdk deploy`. This will deploy / redeploy your Stack to your AWS Account.

After the deployment you will see the API's URL, which represents the url you can then use.

## Synthesize Cloudformation Template

To see the Cloudformation template generated by the CDK, run `cdk synth`, then check the output file in the "cdk.out" directory.

## The Component Structure

This Stack contains:

- a **GraphQL API** with an API Key (Use with caution, each key is only valid for 7 days.)
- a **GraphQL Schema** with Queries to get one and all items and two mutations to save and delete an item
- a **DynamoDB table** `items` that stores the data with a Pay Per Request Billing Mode
- an **IAM Role** that allows AppSync to invoke your DynamoDB table.
- an **AppSync DataSource**, connecting your API to the DynamoDB table with the previously specified role.
- a **AppSync Resolver** for a Query `getOne` to get one item from the DynamoDB table.
- a **AppSync Resolver** for a Query `all` to get all items from the DynamoDB table.
- a **AppSync Resolver** for a Mutation `save` to put an item into the DynamoDB table (the id is autogenerated, you need only name).
- a **AppSync Resolver** for a Mutation `delete` to delete one item from the DynamoDB table.
