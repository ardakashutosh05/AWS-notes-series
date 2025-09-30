**📘 Amazon DynamoDB – How to Create Table
1. Concept

DynamoDB is AWS’s serverless NoSQL key-value database.
Unlike RDS, it doesn’t use SQL tables, rows, and columns. Instead, it stores items in tables, where each item is a set of key-value pairs.

Table = Collection of items

Item = A row (but flexible schema, each item can have different attributes)

Attributes = Columns (key-value pairs)

Primary Key (Mandatory)

Partition Key (HASH)

Partition + Sort Key (HASH + RANGE)

2. Architecture & Working

When you create a table:

You define Table Name (unique).

You must define Partition Key (mandatory).

Optionally, add a Sort Key (for composite primary key).

Choose capacity mode:

On-demand (pay per request)

Provisioned (RCU/WCU)

💡 Example:

Table: Users

Partition Key: UserId (string)

Sort Key: SignupDate (string)

This design allows you to store multiple items per user, ordered by signup date.

3. Practical Example
✅ Console Steps

Open AWS Management Console → DynamoDB → Tables → Create Table

Enter Table name: Users

Partition Key: UserId (String)

Sort Key: SignupDate (String)

Capacity mode: On-demand

Create

✅ CLI Command
aws dynamodb create-table \
  --table-name Users \
  --attribute-definitions \
    AttributeName=UserId,AttributeType=S \
    AttributeName=SignupDate,AttributeType=S \
  --key-schema \
    AttributeName=UserId,KeyType=HASH \
    AttributeName=SignupDate,KeyType=RANGE \
  --billing-mode PAY_PER_REQUEST

4. Best Practices

Always use On-demand mode for unpredictable workloads.

For production, design partition keys carefully to avoid hot partitions.

Enable Point-in-Time Recovery immediately after creation.

Add tags for cost tracking.

5. Interview Q&A

Q1: What is mandatory when creating a DynamoDB table?
👉 Table name + Partition key.

Q2: What is the difference between Partition Key and Sort Key?
👉 Partition key decides where the item is stored, Sort key allows multiple items under same partition.

Q3: Can DynamoDB have multiple sort keys?
👉 No, only one sort key per table.

Q4: Can you add a sort key after table creation?
👉 No, sort key must be defined at table creation.

Q5: What are the two capacity modes in DynamoDB?
👉 On-demand and Provisioned (RCU/WCU).

Q6: What is schema flexibility in DynamoDB?
👉 Except for primary key, all other attributes are optional and flexible (different items can have different attributes).**
